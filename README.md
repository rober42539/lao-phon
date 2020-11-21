# lao-phon
# Lao Latin Phonetic Keyboard Layout

Ever struggled to learn to type Lao? Already comfortable with the standard Latin keys that are already painted on your standard keyboard?

Well, you've come to the right place!

## The Layout
**Note:** *The Linux layout has the zero width joiner as AltGR+Space. For Windows it is AltGR+Minus. The images below are for Windows.*
![Regular Keys](https://raw.githubusercontent.com/rober42539/lao-phon/main/Phonetic.jpg)
![Shift Keys](https://raw.githubusercontent.com/rober42539/lao-phon/main/PhoneticShft.jpg)
![AltGr Keys](https://raw.githubusercontent.com/rober42539/lao-phon/main/PhoneticAltGr.jpg)

## Windows
Clone or [download](https://github.com/rober42539/lao-phon/archive/main.zip) the repo, navigate to the Windows folder.

Run setup.exe.

Add the layout to the Windows 10 onput options. You may need to restart afterwards to see it as an input selection.

## XKB and Linux (Ubuntu)
*This requires some manual installation...*

**Also, the Linux layout has the zero width joiner as AltGR+Space. For Windows it is AltGR+Minus. The images above are for Windows.**

Clone or [download](https://github.com/rober42539/lao-phon/archive/main.zip) the repo.

Navigate to the *la* symbols file in the ./xkb/symbols/ folder of the repo.

Copy the file to the system XKB Symbols for Lao. 

Something like... 

```
sudo cp ~/Downloads/lao-phon/xkb/symbols/la /usr/share/X11/xkb/symbols/la
```

Then open the */usr/share/X11/xkb/rules/evdev.xml* (for Ubuntu, may be a slightly different location for your distribution) file with an editor such as nano...

```
sudo nano /usr/share/X11/xkb/rules/evdev.xml
```

Scroll down until you see something like...

```XML
<layout>
      <configItem>
        <name>la</name>
        <!-- Keyboard indicator for Lao layouts -->
        <shortDescription>lo</shortDescription>
        <description>Lao</description>
        <languageList>
          <iso639Id>lao</iso639Id>
        </languageList>
      </configItem>
      <variantList>
        <variant>  
          <configItem>
            <name>stea</name>
            <description>Lao (STEA proposed standard layout)</description>
            <languageList>
              <iso639Id>lao</iso639Id>
            </languageList>
          </configItem>
        </variant> 
```

After the STEA variant, we will register the *phon* variant. 

```XML
        <!-- Start of Lao Latin Phonetic Layout -->
        <variant>     
          <configItem>
            <name>phon</name>
            <description>Lao Latin Phonetic Layout</description>
            <languageList> 
              <iso639Id>lao</iso639Id>
            </languageList>
          </configItem>
        </variant>  
        <!-- End of Lao Latin Phonetic Layout -->
```

 Before saving, it should look something like...

```XML
    <layout>
      <configItem>
        <name>la</name>
        <!-- Keyboard indicator for Lao layouts -->
        <shortDescription>lo</shortDescription>
        <description>Lao</description>
        <languageList>
          <iso639Id>lao</iso639Id>
        </languageList>
      </configItem>
      <variantList>
        <variant>  
          <configItem>
            <name>stea</name>
            <description>Lao (STEA proposed standard layout)</description>
            <languageList>
              <iso639Id>lao</iso639Id>
            </languageList>
          </configItem>
        </variant> 
        <!-- Start of Lao Latin Phonetic Layout -->
        <variant>     
          <configItem>
            <name>phon</name>
            <description>Lao Latin Phonetic Layout</description>
            <languageList> 
              <iso639Id>lao</iso639Id>
            </languageList>
          </configItem>
        </variant>  
        <!-- End of Lao Latin Phonetic Layout -->
      </variantList> 
    </layout>
```

Save (Control + O, then Control + X to exit).

Then run (on Ubuntu or similar)

```
sudo dpkg-reconfigure xkb-data
```

Or, reboot. Add the layout to your input options.
