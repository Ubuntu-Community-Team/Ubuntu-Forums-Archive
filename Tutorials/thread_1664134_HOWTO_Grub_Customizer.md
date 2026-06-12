---
title: "HOWTO: Grub Customizer"
date: 2011-01-10
forum: Tutorials
---

### Post by drs305 on 2011-01-10
[COLOR=MAROON][B][SIZE=4][CENTER]*Grub Customizer*[/CENTER]
[/SIZE][/B][/COLOR]

**[COLOR="DarkRed"]GRUB CUSTOMIZER & GRUB 1.99 ISSUES[/COLOR]**
Daniel Richter has released Grub Customizer 2.2 , which deals with the new submenu structure in Grub 1.99 and later. See post #158 for the announcement. If you are using the default bootloader in Natty or later, please update your version of Grub Customizer to the latest version.


**Images/Fonts**
Grub 1.99 allows placing an image directly in */boot/grub* for use as a background image. Because of the way Grub sets the background image priority, if an image resides in /boot/grub it will be used even if the user selects an image in Grub Customizer. If using Grub Customizer, remove all image files from the */boot/grub* folder, set the image in Grub Customizer, and do not copy the image to the grub folder.

These issues are addressed with a bit more detail starting in Post #108, and the developer, Daniel Richter, responds in Post # 118. (Thanks Daniel).


**[COLOR="Navy"]GRUB CUSTOMIZER[/COLOR]**
Daniel Richter has developed a GUI configuration tool to allow users to change the Grub 2 settings without using the command line. The application allows the user to add, remove, freeze, rename and reorder boot menu items. It will also allow changes to the Grub 2 configuration settings such as background image and menu timeout. For long-time users familiar with StartUp-Manager, this application performs many of the same capabilities with additional options. It also makes convoluted guides such as my "Grub 2 Title Tweaks" unnecessary for all but the most devoted command-line enthusiasts!

The purpose of this guide is to briefly explain how to use Grub Customizer. I am not going 'under the hood' to explain what happens at the file level.  For those interested in how the application actually accomplishes the tasks,  please refer to [Daniel's Grub Customizer FAQ]("https://answers.launchpad.net/grub-customizer/+faq/1355").

I will include thumbnails of the primary screens. While full-scale graphics would be more convenient, thumbnails comply with the Forum's  guidelines for posting images. Eventually I may create an Ubuntu Community documnet with complete graphics and will post a link should I undertake that project.

**[COLOR=Navy][SIZE=3]1. Installation[/SIZE][/COLOR]** 
I've found adding the repository via some of the GUI apps to be a bit troublesome at times, and since Synaptic is no longer included, it's easiest to just open a terminal, add the repository, and install Grub Customizer:
[LIST=A]
[*]Terminal:
Add the repository to your system. The following commands will add the repository, import the security key, update the list of available packages and install Grub Customizer.
[LIST]
[*]Open a terminal
Applications > Accessories > Terminal
[*]Install Grub Customizer
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```
[/LIST]
 
[*]Manual Download from the [Grub Customizer Launchpad site]("https://launchpad.net/grub-customizer"). 
I don't recommend installing it via this method as other methods will properly install and keep the correct version updated. If manually downloading the package please ensure you choose the correct version. 
[LIST]
[*]You can get the latest version from [https://launchpad.net/ubuntu-tweak/+download]("https://launchpad.net/ubuntu-tweak/+download")here. 
[LIST]
[*]The current version requires python 2.7 or later. Maverick uses python 2.6 and Lucid uses python 2.5.5.
[*]If you must or still desire to download the package from the site, Lucid/Maverick users should select an older version to install.
[*]Updates will not be automatically available unless the repository is added.
[/LIST]
[/LIST]
[/LIST]


**[COLOR=Navy][SIZE=3]2. Starting Grub-Customizer[/SIZE][/COLOR]** 
Since this application modifies system files you will be asked to enter your password to gain access.

GUI: Applications > System Tools > Grub Customizer


Terminal: *gksu grub-customizer*


**[COLOR=Navy][SIZE=3]3. Main Menu Interface[/SIZE][/COLOR]** 
[ATTACH]180683[/ATTACH]
**Categories**
Each Grub 2 script in the */etc/grub.d* folder which finds operating systems is depicted in an expanded tree view: linux, memtest86+, os-prober, 40_custom, 41_custom, etc.

[LIST]
[*]**Main:**
[LIST]
[*]Scripts are displayed by their name (in numerical order) in the /etc/grub.d folder.
[*]Only scripts which deal with operating systems are displayed in the tree. There are no entries for 00_header and 05_header in the tree view.
[*]Scripts which are active are displayed with a filled orange tick box.
[*]Scripts which are currently not executable are present but unticked.
[*]If the main category title is unticked, the subsections are not included in the Grub menu, even if selected.
[/LIST]
 
[*]**Sub Sections:**
[LIST]
[*]linux - The 10_linux script. Listings of your primary Ubuntu OS kernels.
[*]memtest86+  - The 20_memtest86+ script.
[*]os-prober - The 30_os-prober script. Finds and displays other operating systems, including Windows and linux systems installed on other partitions.
[*]custom - In a default installation, the first 'custom' refers to 40_custom, and the second 'custom' refers to 41_custom.
[/LIST]
 
[/LIST]

**[COLOR=DarkRed][SIZE=3]4. Making Changes[/SIZE][/COLOR]** (from Main Page)

[LIST]
[*]**Removing / Hiding Entries**
[LIST]
[*]Hide An Entire Section: Untick the main header (*linux, os-prober*, etc)
[LIST]
[*]Example: Unticking *os-prober* will disable the script and remove all entries normally found by it - Windows, other Ubuntu installations, etc. Even if the entries within the subsection are enabled, they will not be displayed.
[/LIST]
[LIST]
[*]Hide Specific Entries: Untick the entry 
[LIST]
[*]Example: Unticking *Ubuntu, with 2.6.35-24-generic* will remove that specific entry in the Grub 2 menu.
[/LIST]
[/LIST]
[/LIST]
 
[*]**Freezing Entries (new Entries) **
[LIST]
[*]Unticking "new Entries" prevents the addition of any new Grub 2 menu entries for that section. New options found during updates may be included in the tree view but will not be selected by default.
[LIST]
[*]If a new item is found by an enabled script, it will *not* be added to the Grub 2 menu.
[/LIST]
 
[*]Example: If 'new Entries' in 'linux' is deselected, when a new kernel is installed on the main system it will not appear in the menu.
[/LIST]
 
[*]**[B]Adding Entries**[/B]
[LIST]
[*]Tick the applicable entry.
[*]Selecting a main category will enable the script.
[*]Selecting an item within a main category will add it to the Grub 2 menu *if it's parent is enabled*.
[/LIST]
 
[*]**[B]Renaming Entries**[/B]
[LIST]
[*]Double-click a menu title to enable the editing mode. Type the new title and click elsewhere on the page to complete the edit.
[/LIST]
 
[*]**[B]Moving Entries**[/B]
[LIST]
[*]To move a main section, highlight the entry and use the Up/Dn arrows on the main menu to change the menu order. Moving a main category will move all its submenus.
[LIST]
[*]Example: If you want Windows to appear before the main Ubuntu entries, move *os-prober* to the top of the list.
[/LIST]
 
[*]To move a title up or down within a subsection, highlight the entry and use the Up/Dn arrows on the main menu to change the menu order.
[LIST]
[*]A titles can only be moved within its own subsection.
[/LIST]
 
[/LIST]
 
[/LIST]

**[COLOR=Navy][SIZE=3]5. Preferences Tabs[/SIZE][/COLOR]** (Edit > Preferences)
[LIST]
[*]**General**
[ATTACH]180691[/ATTACH]
Initial display options such as whether the menu is shown, which menu entry is highlighted, and what kernel options to add to the instructions.
[LIST]
[*]Default entry
[LIST]
[*]**How to Specify the Default Entry by Name:**
[LIST]
[*]'default entry' > 'predefined': Click on "Entry 1", on the expanded selection screen choose the exact title from the right column.
[*]This works for Grub 1.98. Grub 1.99/Natty introduces submenus and using exact titles will change. I don't know if GC has accounted for this change yet. In the meantime, you can refer to this link on how to manually add a default entry from a submenu: [Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316#post10720316")
[/LIST]
[/LIST]
[*]visibility -  Menu display, other OS selections, and timeout.
[*]kernel parameters - Add options such as *nomodeset, noapic, quiet, splash, etc*
[/LIST]
 
[*]**Appearance**
[ATTACH]180689[/ATTACH]
Menu eye candy - resolutions, colors, background images.
[LIST]
[*]custom resolution
[*]menu colors
[*]background image
[/LIST]
 
[*]**Advanced**
[ATTACH]180689[/ATTACH]
Selection of options normally found in the  */etc/default/grub* file. The user can enable/disable individual items and can modify the existing entries by double-clicking the 'value' column and entering the desired value.
[LIST]
[*]The only items listed in this section are those which currently exist in */etc/default/grub*. The user can enable items displayed here, but cannot add items which do not already exist in the file.
[*]Ticked items are included in the Grub 2 configuration file.
[*]Unticked items will not be included in the Grub 2 configuration file. Unticking an entry places a # (comment) symbol at the start of the line in */etc/default/grub*
[/LIST]
 
[/LIST]

**[COLOR=Navy][SIZE=3]6. Partition Selector[/SIZE][/COLOR]**
Accessed via the main menu "File" option, GC allows the user to select a partition on which to perform operations. This allows the user to accomplish tasks on another OS's partition via the *chroot* process. This is useful when you are running one OS but use another OS's Grub run the boot process. 

For instance, running "update-grub" will update the menu on the current OS. If another partition's Grub 2 is controlling things, no change in the boot menu will occur unless the change is made within the controlling Grub's partition. This option allows you to make these changes without booting the controlling OS.

**[COLOR=Navy][SIZE=3]7. Returning to Grub 2 Defaults[/SIZE][/COLOR]**

Daniel Richter describes how to revert to the normal files in his [_Grub Customizer FAQ_]("https://answers.launchpad.net/grub-customizer/+faq/1355"). 
Note: Original files which Grub Customizer will modify are moved to the */etc/grub.d/proxifiedScripts* folder, with the leading numeric designation removed.

The */etc/grub.d/proxifiedScripts* and */etc/grub.d/bin* folders, and any *_proxy files are only created if a Grub 2 script has to be modified. If only changes normally made to */etc/default/grub* are invoked by Grub Customizer, the following won't be necessary.

To restore the normal Grub 2 control of the boot menu:
[LIST]
[*]Remove the */etc/grub.d/bin* folder
[*]Move the contents of */etc/grub.d/proxifiedScritps* back to the  */etc/grub.d* folder.
[LIST]
[*]Any files moved back need to be renamed to the original name.
[*]*linux* back to *10_linux*, *os-prober* back to *30_os-prober*, etc.
[/LIST][*]Remove the */etc/grub.d/proxifiedScipts* folder [COLOR="DarkRed"]once it is empty[/COLOR].
[*]Check the settings in */etc/default/grub* and make any desired changes (default kernel, timeout, etc).
[*]Run "sudo update-grub".
[/LIST]

**[COLOR=Navy][SIZE=3]8. Links[/SIZE][/COLOR] **

[Launchpad Grub-Customizer]("https://launchpad.net/grub-customizer")
[Daniel Richter's Grub Customizer FAQ]("https://answers.launchpad.net/grub-customizer/+faq/1355")
[Grub 2]("https://help.ubuntu.com/community/Grub2") (help.ubuntu.com)
[Grub 2: Introduction]("http://ubuntuforums.org/showthread.php?t=1285897#post8072444")
[Grub 2: Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")
[Grub 2: 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")
[_GNU Grub 2 Manual/Wiki_]("http://grub.enbug.org/Manual")

---

### Post by akha666 on 2011-01-11
Thank you 
it's really simple and easy

---

### Post by Rubi1200 on 2011-01-11
Thank you drs305; very useful and I am sure many users will likely give this a try.

Bookmarked for future reference.

> It also makes convoluted guides such as my "Grub 2 Title Tweaks"  unnecessary for all but the most devoted command-line enthusiasts!Oh no, I hope not! You will still find a few of us out there who love (and use) that guide :)

---

### Post by produnis on 2011-01-17
awsome!!!
thank you very much for this!!

---

### Post by Quackers on 2011-01-19
I'm playing as I type :-) Thanks drs305.
I have one question. It says I'm not using a background image and I am. I'll try a reboot and see if it picks the image up. It has picked up the custom size for menu print though.

---

### Post by drs305 on 2011-01-19
> **Quackers said:**
> I have one question. It says I'm not using a background image and I am. I'll try a reboot and see if it picks the image up. It has picked up the custom size for menu print though.

I'll have to play with it. When I read your post I took a look at the 05_debian_theme file. I happen to have Grub 1.99 on this laptop and the file format has changed quite a bit. Are you using the newest Grub2? Perhaps GC hasn't caught up to it yet.

I'll play with it a bit more. I'm trying not to get too far ahead with G2 in my guides until Natty comes out..

When I return home I can take a look at how it reacts with 1.98

---

### Post by Quackers on 2011-01-19
Actually, drs305, I am using Natty full time now, so I have 1.99 myself. In view of the boot script output problem, it may be that some things are different in this version and the Customizer wouldn't know about it.

---

### Post by Jechem on 2011-01-19
drs305,

Thank you for this GUI. I have been wanting to modify Grub but didn't have the time to do it. This is a time saver.

By the way, I have copied your instructions, if it's okay with you, onto my blog post hoping that more Ubuntu users will be able to benefit from it.

Again thanks for the great work!=D>

---

### Post by Jechem on 2011-01-19
drs305,

Thank you for this GUI. I have been wanting to modify Grub but didn't have the time to do it. This is a time saver.

By the way, I have copied your instructions, if it's okay with you, onto my blog post hoping that more Ubuntu users will be able to benefit from it.

Again thanks for the great work!=D>

---

### Post by Jechem on 2011-01-19
drs305,

Thank you for this GUI. I have been wanting to modify Grub but didn't have the time to do it. This is a time saver.

By the way, I have copied your instructions, if it's okay with you, onto my blog post hoping that more Ubuntu users will be able to benefit from it.

Again thanks for the great work!=D>

---

### Post by Jechem on 2011-01-19
sorry about the multiple posts. don't know how that happened.:confused:

---

### Post by ganesh2k5 on 2011-01-22
I am new to UBUNTU (Linux) and the first thing I wish to change is the customized Menu interface, and the "GRUB CUSTOMIZER" is a breeze. 
Still there is an issue of the colors and the background image chosen under<Preferences>,< appearance>,under "GC"is not displaying. I am getting the same ugly black background and white texts. Some body help me resolve this.

---

### Post by drs305 on 2011-01-22
> **ganesh2k5 said:**
> I am new to UBUNTU (Linux) and the first thing I wish to change is the customized Menu interface, and the "GRUB CUSTOMIZER" is a breeze. 
Still there is an issue of the colors and the background image chosen under<Preferences>,< appearance>,under "GC"is not displaying. I am getting the same ugly black background and white texts. Some body help me resolve this.

Welcome to the Ubuntu forums.

I tried selecting the background in GC and it failed for me as well. However, I had already modified my files and that may be the reason. 

In any case, you can try this. GC may have created it's own files on your system. If it has, 05_debian_theme may not open or you will get an empty file (and this procedure won't work). 

These procedures are for Grub 1.98 (Lucid/Maverick):

```
gksu gedit /etc/grub.d/05_debian_theme
```
Find this section near the top:
> # this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

Replace it with the following:
Change the Wallpaper entry to point to your background image. 
Change the colors to those you wish to use. "black" as the second entry means "transparent" and will allow you to see the background image. Also don't use a color which is the same color as your background image's color, since it will blend in and you may not be able to read it.
New:
> 
# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else  WALLPAPER="path.to.your.background.image/filename.png"
  COLOR_NORMAL="black/**black**"
  COLOR_HIGHLIGHT="magenta/**black**"
Save the file, then run:
```
sudo update-grub
```
As the command runs, see if the image is found (Found background image...) in the terminal output immediately after the "Generating grub.cfg ..." line.

---

### Post by patrickl26 on 2011-01-23
I don't know why but when I try to run Grub Customizer, Ubuntu gets completely freezed and I can do nothing, just pressing the reset button.. :(
Tried to install with all the three possibilities but every time I have the same problem. I have no idea what I'm doing wrong.. please help! ;) Having Ubuntu 10.04

---

### Post by drs305 on 2011-01-23
> **patrickl26 said:**
> I don't know why but when I try to run Grub Customizer, Ubuntu gets completely freezed and I can do nothing, just pressing the reset button.. :(
Tried to install with all the three possibilities but every time I have the same problem. I have no idea what I'm doing wrong.. please help! ;) Having Ubuntu 10.04

Is it freezing when you try to install it or is it when you try to run it? In either case, attempt to do it from a command line and provide us with the error code you get (if possible).

To add the repository:
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
```

To update the repositories:
```
sudo apt-get update
```

To install Grub Customizer:
```
sudo apt-get install grub-customizer

```

To run Grub Customizer:
```
gksu grub-customizer
```

---

### Post by patrickl26 on 2011-01-23
Thanks for that quick reply.
No, the installation works fine, just can't start the application, because it crashes my whole system and I can't do nothing but pressing the restart button. I have this problem just with this application, others work fine for me.

---

### Post by drs305 on 2011-01-23
> **patrickl26 said:**
> Thanks for that quick reply.
No, the installation works fine, just can't start the application, because it crashes my whole system and I can't do nothing but pressing the restart button. I have this problem just with this application, others work fine for me.

Did you try it from the command line using "gksu...."? 
Are there any error messages?

If it crashes, what happens if you try another GUI app such as gedit as root ( gksu gedit )?

---

### Post by patrickl26 on 2011-01-23
when i run gedit using terminal the app is starting without any problem. I have also tried to run Grub Customizer via Teminal and there isn't any error message because the PC freezes just after pressing enter.
Keep reading other freezing problems topics but none of them is a help.
EDIT:
Updated Ubunto to 10.10 and now it works like a charm! ;)
Thanks for the help!

---

### Post by Cpierce on 2011-01-24
drs305, 
First of all, thank you for this program. I am having no issues except the background image. The first computer I installed it on, the image worked fine. The next two computers everything worked except no background image. All three are lucid. For the one that worked, I picked the font colors, and for both backgrounds I picked "transparent". 
I didn't fully understand your earlier explaination concerning image, but should I set both backgrounds to "black" ?

Thank you in advance for any help.

---

### Post by drs305 on 2011-01-24
> **Cpierce said:**
> drs305, 
First of all, thank you for this program. I am having no issues except the background image. The first computer I installed it on, the image worked fine. The next two computers everything worked except no background image. All three are lucid. For the one that worked, I picked the font colors, and for both backgrounds I picked "transparent". 
I didn't fully understand your earlier explaination concerning image, but should I set both backgrounds to "black" ?

Thank you in advance for any help.

First, to be clear, you can thank me for the *guide* but certainly not the program, which was written by Daniel Richter. He deserves all the credit. :-)

I haven't determined what the issue is with the background displays - and why it sometimes works and sometimes doesn't. 

Grub2 doesn't understand the setting "transparent" - Grub Customizer presents that as an option for the second section of the font color since it is more intuitive than "black". GC passes "transparent" to Grub2 as "black", which as a second entry in the font color is what Grub considers transparent. 

If you want to try to manually edit the 05_debian_theme file and not use GC, you would use "black" as the second setting. Here is an example of an entry for /etc/grub.d/05_debian_theme:
 >  
WALLPAPER="/data/backgrounds/earth.png"
COLOR_NORMAL="light-gray/black"
COLOR_HIGHLIGHT="green/black"
The above entry uses the image "earth.png" stored in /data/backgrounds. The highlighted menu entry text is green; unselected entries are light gray. The image is visible behind and around the text.
The background image appears since both have 'black' as the second entry.

If another color was the second entry:
For the highlighted entry, a solid colored bar across the entire screen. The image is hidden by the bar.
If the 'normal' entry also had a (non-black) color as the second value, the entire screen other than the one highlighted would be that color.

---

### Post by Cpierce on 2011-01-24
Thank you very much for the info. I will try this tomorrow and report back. Thanks again !

---

### Post by Cpierce on 2011-01-25
I checked it out, and it still isn't working on those two computers. Nothing under the "appearance" tab works, except resolution. I check under the "advanced" tab and it does list black as the secondary color for both COLOR_NORMAL and COLOR_HIGHLIGHT. The grub boots up as a default and ignores the font colors and background image. The Grub Customizer is version 2.0.8. If I can't get this to work, I will manually change it as you suggested. Just wanted to try everything before I did that. That is what this tool is for, and I would sure like to get it working. 

Any other suggestions to try ?

---

### Post by Cpierce on 2011-01-25
Now I am really confused. I went ahead and manually changed the debian_theme as you described, updated grub, and rebooted. I got the same Black screen with the white font and light gray highlight.

This shouldn't be this difficult. Please help !

---

### Post by drs305 on 2011-01-25
> **Cpierce said:**
> Now I am really confused. I went ahead and manually changed the debian_theme as you described, updated grub, and rebooted. I got the same Black screen with the white font and light gray highlight.

This shouldn't be this difficult. Please help !

If you download and run the boot info script from the following location and attach the RESULTS.txt and your /etc/default/grub contents I can take a look.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Added: I just loaded up Lucid in a VM and GC worked as expected. By looking at your scripts we may be able to find out what is different on your machine.

---

### Post by Cpierce on 2011-01-25
First of all, I would like to thank you again for the help. Sorry for this long post.
```

/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="10"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash vga=769"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="1280x800x24"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

export GRUB_MENU_PICTURE="cool-wallpaper-26.jpg"


export GRUB_COLOR_NORMAL="blue/black"
export GRUB_COLOR_HIGHLIGHT="white/black"




and RESULTS.txt :

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    92,162,047    92,160,000  83 Linux
/dev/sda2          92,162,048   192,446,463   100,284,416   7 HPFS/NTFS
/dev/sda3         192,448,510   195,371,007     2,922,498   5 Extended
/dev/sda5         192,448,512   195,371,007     2,922,496  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        51038582-23a5-4c2b-9ac2-fcd99dfa9a48   ext4                                     
/dev/sda2        17988C1633246A39                       ntfs       c:                            
/dev/sda3: PTTYPE="dos" 
/dev/sda5        746d858d-3f7e-4ee8-9a8c-f9bade226f96   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 51038582-23a5-4c2b-9ac2-fcd99dfa9a48
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x800x24
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 51038582-23a5-4c2b-9ac2-fcd99dfa9a48
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 51038582-23a5-4c2b-9ac2-fcd99dfa9a48
insmod jpeg
if background_image /boot/grub/cool-wallpaper-26.jpg ; then
  set color_normal=blue/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-27-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 51038582-23a5-4c2b-9ac2-fcd99dfa9a48
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=51038582-23a5-4c2b-9ac2-fcd99dfa9a48 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 51038582-23a5-4c2b-9ac2-fcd99dfa9a48
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=51038582-23a5-4c2b-9ac2-fcd99dfa9a48 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 51038582-23a5-4c2b-9ac2-fcd99dfa9a48
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=51038582-23a5-4c2b-9ac2-fcd99dfa9a48 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 51038582-23a5-4c2b-9ac2-fcd99dfa9a48
	linux16	/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+_proxy ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 17988c1633246a39
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=51038582-23a5-4c2b-9ac2-fcd99dfa9a48 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=746d858d-3f7e-4ee8-9a8c-f9bade226f96 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
  21.9GB: boot/grub/grub.cfg
  30.3GB: boot/initrd.img-2.6.32-21-generic
   4.3GB: boot/initrd.img-2.6.32-26-generic
   6.4GB: boot/initrd.img-2.6.32-27-generic
   2.2GB: boot/vmlinuz-2.6.32-21-generic
   2.2GB: boot/vmlinuz-2.6.32-26-generic
   6.5GB: boot/vmlinuz-2.6.32-27-generic
   6.4GB: initrd.img
   4.3GB: initrd.img.old
   6.5GB: vmlinuz
   2.2GB: vmlinuz.old

```

---

### Post by drs305 on 2011-01-25
> **Cpierce said:**
> First of all, I would like to thank you again for the help. Sorry for this long post.


No problem - it's what I asked for. Note you can enclose it in 'code' tags by pressing the # icon in the post's menu and then copying between the generated tags.

I copied and used your first section of grub.cfg, replacing only the UUID and making a copy of an image and placing it in /boot/grub. It worked as it should have.

Do you have a copy of the background image in /boot/grub?
Is it an 8-bit jpeg/jpg image?

If the image doesn't reside in /boot/grub that would explain why it isn't appearing and why your font colors are not changing.

I got called out on a business trip and won't get back to looking at your post until late tomorrow, but check the two items above as a minimum.

---

### Post by Cpierce on 2011-01-26
The image is in /boot/grub. However, I am not sure if it is 8 bit. I looked at the image properties, but didn't see where it specified that. Does the image need to be a certain size, resolution, bit, etc...... in order to work? 
The laptop that works is a Dell D620. The two that are having issues are both Toshiba M115. All three do all the fancy graphics, so I don't believe it is a graphics card problem. 
I am going to take the exact image from the one that works, and try it on the other computers. I also saw the option to "install to MBR", do I need to do that ?

---

### Post by Cpierce on 2011-01-26
The whole issue was the image. I took the same image on the computer that worked, and it worked on the other two computers just fine. Now I just need to know the parameters of images that will work for grub. The image that is working is 1440x900 so resolution must not be critical. It is some other parameter that is causing the issue.

What causes some images to work and others don't ?

---

### Post by Cpierce on 2011-01-30
Does anyone know some pictures won't work ?

---

### Post by drs305 on 2011-01-30
> **Cpierce said:**
> Does anyone know some pictures won't work ?

Yes they do. Remember that Grub 2 is loaded before your system files, so what Grub 2 is able to do is limited. It has the ability to display some images, but not *every* image. It supports tga, png and jpeg (8-bit) images. The RGB color mode is supported but indexed images are not.

You can find the image properties with various graphic software packages. In GIMP, for example, you can use Image > Properties and look at the "Color space" entry to see if the image is RGB. You can also use Image > Mode to see if the image is RGB or Indexed, and from that menu you can change it to RGB if it is not.

---

### Post by Cpierce on 2011-01-30
Thank you very much. That makes sense. The image that would not work was a jpeg with RGB color, but I don't know if it was 8 bit. I will use gimp to convert it to a png format with RGB color and see if that works. 

I really appreciate your help on this.

---

### Post by Cpierce on 2011-01-30
Saving in png worked like a charm. I learned something today. 

Thank you very much.

---

### Post by Objekt on 2011-02-10
I found a new toy.  Jeez, now I'm going to keep rebooting just to play with this.

---

### Post by drs305 on 2011-02-10
> **Objekt said:**
> I found a new toy.  Jeez, now I'm going to keep rebooting just to play with this.

lol. Well, unless it's graphics-related you can see what's going to look like without rebooting:
```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```
I just number them in the command's output for my own purposes - the numbers won't appear in the actual menu.  ;-)

---

### Post by jean noel on 2011-02-11
Absolutely brilliant stuff. Give that man another glass of wine. :D

---

### Post by hariks0 on 2011-02-15
> Sub Sections:
linux - The 10_linux script. Listings of your primary Ubuntu OS kernels.
memtest86+ - The 20_memtest86+ script.
os-prober - The 30_os-prober script. Finds and displays other operating systems, including Windows and linux systems installed on other partitions.
custom - In a default installation, the first 'custom' refers to 40_custom, and the second 'custom' refers to 41_custom...

But I had renamed the 40_custom to 09_custom so that the other OS will be the first entry in grub even after any addition or modification of the kernel entries. 

Will this work OK with this application?

TIA

---

### Post by drs305 on 2011-02-16
> **hariks0 said:**
> But I had renamed the 40_custom to 09_custom so that the other OS will be the first entry in grub even after any addition or modification of the kernel entries. 

Will this work OK with this application?

TIA

You raise an interesting question. I have several custom menus. My preliminary testing of your question suggests that Grub customizer leaves these custom menus alone and, at least for me, doesn't even display them.

So the good news is that your custom menus should not be touched. The downside is that they also don't appear in the Grub Customizer display so you can't edit them from within GC.

I assume that if your custom entries are contained within the 40_custom file they would appear under the "custom" entry in GC.

---

### Post by hariks0 on 2011-02-16
Thank you for your kind reply. However, I had tested this application and found it working without any major issues. The default and topmost item was changed to Ubuntu though. As another surprise, Grub customiser recognised Burg manager and offered a choice to edit the Burg setup instead.:D

Now the topmost and default selection is the other OS in the beautiful Burg menu.

[Check out this link if anybody wants to know how to setup a *Windows entry* that is always on top of the others in grub.]("http://ubuntuforums.org/showpost.php?p=9675846&postcount=9")

---

### Post by drs305 on 2011-02-16
> **hariks0 said:**
> As another surprise, Grub customiser recognised Burg manager and offered a choice to edit the Burg setup instead.:D

I have not used BURG but have noticed when I start GC it states in Help > About that GC is a graphical app to configure grub/burg.

---

### Post by james.euless on 2011-02-17
I cannot get it to run.  I get:

"grub-mkconfig couldn't be executed successfully. You must run this as root!"

I am using LinuxMint 9 (isadora)
Gnome 2.30.2
Kernal 2.6.32-21

Any help is appreciated.

---

### Post by drs305 on 2011-02-17
> **james.euless said:**
> I cannot get it to run. 

When you start GC, you should get a pop-up window asking for your password, just as you would when using any other GUI app requiring root access. 

I get the same message as you report if I try running it from the command line as "grub-customizer". Try "gksu grub-customizer" or start it from Applications > System Tools.

If you continue to have problems, try running any other command as root from the command line and see if it works ("gksu gedit").

---

### Post by geoffree on 2011-02-18
I'm running a 2 os system:  Kubuntu and Ubuntu 10.10.  Installed grub-customizer and was able to invoke it several times.  However, after making a change in the resolution, to 800x640x2(?), the splash screen text which lists the kernels, was very very tiny.  When I next tried to launch customizer, I got: "grub-mkconfig couldn't be executed successfully. You must run this as root!".  I tried from the terminal with gksu and got the same error message.  I re-installed it.  I tried invoking the Great Wamuzygote.  Nothing.  What???

Geoffree

---

### Post by geoffree on 2011-02-18
> **geoffree said:**
> I'm running a 2 os system:  Kubuntu and Ubuntu 10.10.  Installed grub-customizer and was able to invoke it several times.  However, after making a change in the resolution, to 800x640x2(?), the splash screen text which lists the kernels, was very very tiny.  When I next tried to launch customizer, I got: "grub-mkconfig couldn't be executed successfully. You must run this as root!".  I tried from the terminal with gksu and got the same error message.  I re-installed it.  I tried invoking the Great Wamuzygote.  Nothing.  What???

Geoffree

I tried editing the file thus:  sudo gedit /etc/default/grub
There were three characters at the end of the file:  = "" .  I deleted them. Now the splash screen is fine; the resolution is readable. However I'm still unable to launch grub-customizer.  When running update-grub I got an error message that followed the listing of the kernels: 

"glibmm-ERROR **: unhandled exception (type std::exception) in signal handler: what: basic_string::substr"  

What does this signify?

Thank you.

G.

---

### Post by drs305 on 2011-02-19
> **geoffree said:**
> 
"glibmm-ERROR **: unhandled exception (type std::exception) in signal handler: what: basic_string::substr"  

What does this signify?


I'm not sure. I think I would try to restore a normal G2 setup, at least initially. 

Close Grub Customizer, if it is open. 

Open a file browser as root (gksu nautilus /etc/grub.d) and move any file in that folder named "*.proxy" to the Desktop or somewhere else. 

Next move any files in "/etc/grub.d/proxifiedScripts" folder back into /etc/grub.d  These files are the originals which GC used to make the *.proxy files. Restoring them to the /etc/grub.d folder should return G2 to normal.

Once you have no files in /etc/grub.d named *.proxy, try running "sudo update-grub" and see if it now works. You will have lost any GC customizations but at least have restored normal G2 functionality for the time being.

---

### Post by danielrichter on 2011-02-20
> **geoffree said:**
> I tried editing the file thus:  sudo gedit /etc/default/grub
There were three characters at the end of the file:  = "" .  I deleted them. Now the splash screen is fine; the resolution is readable. However I'm still unable to launch grub-customizer.  When running update-grub I got an error message that followed the listing of the kernels: 

"glibmm-ERROR **: unhandled exception (type std::exception) in signal handler: what: basic_string::substr"  
G.

Hi geoffree,

I'd like to fix this. Please set up a bug report at [https://bugs.launchpad.net/grub-customizer](https://bugs.launchpad.net/grub-customizer) and attach your grub2 configuration files/directories (/etc/grub.d and /etc/default/grub).

Thanks,
Daniel

---

### Post by drs305 on 2011-02-21
Daniel, 

Thanks for stepping up. Welcome to the Ubuntu forums. It gives me another chance to thank you for your excellent work with Grub Customizer.  :-)

---

### Post by jscudder on 2011-02-22
> **james.euless said:**
> I cannot get it to run.  I get:

"grub-mkconfig couldn't be executed successfully. You must run this as root!"


Any help is appreciated.

The following worked for me when I received that message....Create an empty directory called 'locale' in /boot/burg:

'sudo mkdir /boot/burg/locale'



John

---

### Post by james.euless on 2011-02-24
> **drs305 said:**
> When you start GC, you should get a pop-up window asking for your password, just as you would when using any other GUI app requiring root access. 

I get the same message as you report if I try running it from the command line as "grub-customizer". Try "gksu grub-customizer" or start it from Applications > System Tools.

If you continue to have problems, try running any other command as root from the command line and see if it works ("gksu gedit").

It does ask for the password and I can run other commands as root.  When I try Grub Customizer I get this:

james@james-desktop ~ $ gksu grub-customizer
checking for the burg-mkconfig command… 
checking for the grub-mkconfig command… 
/usr/sbin/grub-mkconfig
checking for the update-grub command… 
/usr/sbin/update-grub
checking for the grub-install command… 
/usr/sbin/grub-install
checking for the grub-mkconfig command… 
/usr/sbin/grub-mkconfig
checking for the update-grub command… 
/usr/sbin/update-grub
checking for the grub-install command… 
/usr/sbin/grub-install
running grub-mkconfig
/usr/sbin/grub-probe: error: /boot/grub/device.map:2: No open parenthesis found.

I tried running grub-mkconfig as root just by itself and got this:

/usr/sbin/grub-probe: error: /boot/grub/device.map:2: No open parenthesis found.

If I have not mentioned before, I am running LinuxMint.  I thought being based on Ubuntu this would work, but there may be some unknown difference.

---

### Post by aunicorn on 2011-02-24
**[SIZE=4]Help! Help! Help! How do I start my very own postings? I want  to start a new post of my own to ask questions about problems I am having with ubuntu. Such as:[/SIZE]**
**[SIZE=4][/SIZE]** 
**[SIZE=4]I have windows xp and ubuntu when I choose to use ubuntu I have to choose recovery mode with the ubuntu CD in the drive and then choose "failsafe graphic mode for just one session."[/SIZE]**
**[SIZE=4][/SIZE]** 
**[SIZE=4]Now it seems to me that I should not have to always start with my ubuntu cd in the drive and [/SIZE]**
**[SIZE=4]certainly not have to go to recovery mode, etc. just to start Ubuntu.[/SIZE]**
**[SIZE=4][/SIZE]** 
**[SIZE=4]Help! Please!:)[/SIZE]**

---

### Post by drs305 on 2011-02-24
> **aunicorn said:**
> Help! Help! Help! How do I start my very own postings? I want  to start a new post of my own to ask questions about problems I am having with ubuntu. Such as:
I have windows xp and ubuntu when I choose to use ubuntu I have to choose recovery mode with the ubuntu CD in the drive and then choose "failsafe graphic mode for just one session."
Now it seems to me that I should not have to always start with my ubuntu cd in the drive and certainly not have to go to recovery mode, etc. just to start Ubuntu.

Help! Please!:)

Go to the forum you want to add the entry to ([_Absolute Beginners_]("http://ubuntuforums.org/forumdisplay.php?f=326") might be best for you). Click on "New Thread" near the top left.

Note: We discourage the use of specialized fonts, colors and emphasis on these forums, especially for the entire post. It's covered in the [_Forum Code of Conduct_]("http://ubuntuforums.org/index.php?page=policy").

---

### Post by drs305 on 2011-02-24
> **james.euless said:**
> It does ask for the password and I can run other commands as root.  When I try Grub Customizer I get this ...

I tried running grub-mkconfig as root just by itself and got this:

/usr/sbin/grub-probe: error: /boot/grub/device.map:2: No open parenthesis found.


You might try running "sudo grub-mkdevicemap" which should create a new device.map file for you and possibly resolve your issue (or at least that error message).

---

### Post by GARoss on 2011-03-01
I have a unique siduation & need some help. I'd like to change the grub to default to Vista instead of Ubuntu.

My main problem is the PC that is dual booting Ubuntu 10.04 32-bit & Vista is a company computer & restricts internet connections. I can connect on the Vista side but not while on Ubuntu. Ubuntu was installed with just the install CD &, without internet access, has not been updated to a full install. The goal was to use an open sourse machining program which has been installed & does seem to work but at times crashes. This same software company, EasyDNC, offers a pay version which works very well on Vista.

I cannot download any new software unless it is accessable as a standard internet program from Vista, then install in Ubuntu. Is there a way to change grub order without additional software?

---

### Post by drs305 on 2011-03-01
GARoss,

Assuming you can boot Ubuntu, open a terminal (Applications, Accessories, Terminal) and run these commands:
```
grep menuentry /boot/grub/grub.cfg
gksu gedit /etc/default/grub
```
The first command will display the "menuentries" in your Grub2 menu. Count the menuentries starting from 0 and determine the Vista entry (e.g. if it's the third menuentry, the number would be 2).

Next edit /etc/default/grub and find the "DEFAULT=0" line and replace it with the new number. Save the file, then run:
```
sudo update-grub
```
Reboot.

If you need clarification it's explained in the "Tasks" link in my signature line.

---

### Post by GARoss on 2011-03-01
> **drs305 said:**
> GARoss,

Assuming you can boot Ubuntu, open a terminal (Applications, Accessories, Terminal) and run these commands:
```
grep menuentry /boot/grub/grub.cfg
gksu gedit /etc/default/grub
```
The first command will display the "menuentries" in your Grub2 menu. Count the menuentries starting from 0 and determine the Vista entry (e.g. if it's the third menuentry, the number would be 2).

Next edit /etc/default/grub and find the "DEFAULT=0" line and replace it with the new number. Save the file, then run:
```
sudo update-grub
```
Reboot.

If you need clarification it's explained in the "Tasks" link in my signature line.

Thanks. I'll try this.

---

### Post by -jay- on 2011-03-02
thank you this makes the boot more clean looking

---

### Post by GARoss on 2011-03-02
> **drs305 said:**
> GARoss,

Assuming you can boot Ubuntu, open a terminal (Applications, Accessories, Terminal) and run these commands:
```
grep menuentry /boot/grub/grub.cfg
gksu gedit /etc/default/grub
```
The first command will display the "menuentries" in your Grub2 menu. Count the menuentries starting from 0 and determine the Vista entry (e.g. if it's the third menuentry, the number would be 2).

Next edit /etc/default/grub and find the "DEFAULT=0" line and replace it with the new number. Save the file, then run:
```
sudo update-grub
```
Reboot.

If you need clarification it's explained in the "Tasks" link in my signature line.

Thank you for your help. That did the trick!

---

### Post by Dutch70 on 2011-03-06
Hello drs305, 
 Thank you for this tutorial. However I'm having one problem I haven't been able to get sorted out. I Multiboot several OS's and whenever I install Grub customizer it creates several options for Fedora in the Grub menu at start up. If I go to grub.cfg and delete them, it creates more. Any solution to this???

---

### Post by drs305 on 2011-03-06
> **Dutch70 said:**
> ... whenever I install Grub customizer it creates several options for Fedora in the Grub menu at start up. If I go to grub.cfg and delete them, it creates more. Any solution to this???

Since grub.cfg is actually the 'end' product, any edits you make to it will be erased any time "update-grub" is run. 

Grub Customizer works by replacing the normal menu-generating scripts with modified ones that should be invoked when "update-grub" is run. I don't use Fedora so I don't know much about how it is incorporated into the Grub2 menu.

If you post the contents of RESULTS.txt, which is generated by the boot info script available from the following link, we can see how your menu is structured. Run "sudo update-grub" to get back to the default G2 menu, then run the script.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

 I may not be able to tell you how GC can fix the problem, but perhaps it's creator, *danielrichter*, can. If we can't do it through GC, at the least I should be able to come up with a way outside of GC to  change the menu for you. (You can also look at my signature line's "Tweaks" link to see how I'd probably do it).

---

### Post by Chris.L on 2011-03-06
This sounds great and I'm pretty sure I understand most of it. My question is what needs to be in the loader? I'm dual booting 10.04.1 LTS with Win 7. I have the following on grub 1.98-1ubuntu10
Ubuntu, with Linux 2.6.32-28-generic
Ubuntu, with Linux 2.6.32-28-generic (recovery mode)
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)
Windows Vista (loader) (on /dev/sda3)

what I'm thinking from what I have read is the ...-24generics could be removed and one of the memtests could be, although I don't know which if either it would be. The Windows Vista I think is the recovery partition on windows but I am unsure. I would like to par this list down and rearrange so it boots Win 7, Ubuntu, then recoveries.
Thank you in advance,
Chris

---

### Post by drs305 on 2011-03-06
> **Chris.L said:**
> This sounds great and I'm pretty sure I understand most of it. My question is what needs to be in the loader? 
Chris

These would be the minimum items you would want. You will have to decide which Windows you need. The two non-Vista entries are probably because 7 has 'piggybacked' on the original Vista bootloader. You'll have to try them, but my guess is that you may need to start with the sda1 item:

> 
Ubuntu, with Linux 2.6.32-28-generic
Windows 7 

Now for some explanations.
[LIST]
[*]The memtest86+ entries are probably something you will never use. You can restore the option if you ever need it.
[*]Most people like having an extra older kernel, in case the new one fails for some reason. In that case, keep -24-generic.
[*]It's also convenient to have the current kernel's recovery mode available in case you need it. If you don't want it, you can remove it and if you need recovery mode press "e" to edit the main Ubuntu kernel line and remove "quiet splash" and add "single" to the end of the line. Then press CTRL-x to boot into recovery mode (Wouldn't having the menuentry be easier? ;-) )
[*]Use Grub Customizer to move Windows to the top.
[*]You can do all of these manually as well via the "Tasks" and "Tweaks" links in my signature line, but GC is easier.
[/LIST]

---

### Post by Dutch70 on 2011-03-06
> **drs305 said:**
> Since grub.cfg is actually the 'end' product, any edits you make to it will be erased any time "update-grub" is run. 

Grub Customizer works by replacing the normal menu-generating scripts with modified ones that should be invoked when "update-grub" is run. I don't use Fedora so I don't know much about how it is incorporated into the Grub2 menu.

If you post the contents of RESULTS.txt, which is generated by the boot info script available from the following link, we can see how your menu is structured. Run "sudo update-grub" to get back to the default G2 menu, then run the script.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

 I may not be able to tell you how GC can fix the problem, but perhaps it's creator, *danielrichter*, can. If we can't do it through GC, at the least I should be able to come up with a way outside of GC to  change the menu for you. (You can also look at my signature line's "Tweaks" link to see how I'd probably do it).

 I really do appreciate that drs305, but being that I've got about 8 OS's on my pc, and Fedora is the only one with a problem, I won't trouble you with it right now. 

ps. I'ts not just grub customizer. If I so much as rename the way Fedora is listed, it generates more entries in my grub menu.

Thank you very much though,
Dave

---

### Post by KingLewy on 2011-03-20
Awesome. Thanks for this. My girlfriend's laptop used to have Vista before she upgraded to 7 and today I've had to reinstall GRUB for the THIRD time because her dad keeps trying to boot a Vista recovery partition which wipes the GRUB loader. Unchecked the Vista partition and all is swell. So easy. Thanks! :p

---

### Post by dave_h on 2011-04-03
I just found GC and installed it 2 days ago to my laptop which multiboots into ubuntu 10.10, as well as linux mint, windows vista and 3 puppy linux distros. All went well and I could re-order the grub2 entries and ignore those kernels I wanted to ignore, using GC. Sounds encouraging.

So I installed GC to my test PC which runs about 12 different distros including Win xp, ubuntu 10.10, ubuntu 10.04, mint, slitaz and some puppies. In this case I can't get GC to change any setting or delete any distro from the grub2 list. I have installed it in exactly the same way adding the ppa to software sources then using synaptic to download. 

In both cases (laptop and test PC) Ubuntu 10.10 has the grub2 that does the multiboot and all updates are current. The only difference that may be significant is that for the test PC the distros are spread over 2 HDDs not one as for the laptop.

In both cases (laptop and test PC) I see a bin folder and a proxifiedScripts folder under /etc/grub.d and the 10_linux, 30_os-prober and 40_custom files have proxy after their name.

I also noticed that GC shows Ubuntu 10.04.1 four times in the test pc. 

Anyone any idea what's going on and how I can get it to work.
Thanks

---

### Post by drs305 on 2011-04-03
> **dave_h said:**
> 
Anyone any idea what's going on and how I can get it to work.
Thanks

The first thing that comes to mind is that you have a Grub on another partition controlling your boot. This isn't specific to GC, but often changes are made to the current OS but that Grub isn't providing the menu you see at boot. And while you may think you are using a specific one, the control may change during grub package updates.

Normally you can tell because the first item on the Grub2 menu during boot is from the controlling partition. However, this may not be true if you have reordered things. I use a different background for each partition's Grub so I can tell on boot which one is being used. 

The easiest way to make sure the OS you are using is being controlled by it's G2 is to run: "sudo grub-install /dev/sdX" with X being your boot drive.

---

### Post by dot2kode on 2011-04-04
_Very Nice guide!_ Thanks for sharing with us :D

---

### Post by dave_h on 2011-04-05
Thanks drs305 for your suggestion
> The easiest way to make sure the OS you are using is being controlled by it's G2 is to run: "sudo grub-install /dev/sdX" with X being your boot drive. 

I was pretty sure that I was using the GC and G2 on the Ubuntu 10.10 partition (sda4) as no other /etc/grub.d files had so many entries but I did as you suggested. Unfortunately it made no change.

So I made a name change to an entry in "/etc/grub.d/proxifiedScripts/custom" and then ran GC again. I noticed that the name change was seen in /etc/grub.d/40_custom_proxy but wasn't seen in /boot/grub/grub.cfg

Then I tried the same thing but this time I selected "File>Install to MBR" in GC. The name change was now seen in the grub2 list on reboot.

However since that I have tried to make further deletions to the grub list using GC and whether I do "File>Install to MBR"
or not the changes don't impact /boot/grub/grub.cfg

I have tried ```
sudo update-grub
``` of course after making changes in GC but that doesn't work either.

I did notice however that after running ```
sudo update-grub 
```it ends with > wrong argument count. You have to give the config as parameter 1!

So it seems grub.cfg isn't being updated correctly.

What is "Install to MBR" supposed to do?

Can you suggest a CLI alternative to make this work? In addition the grub list now has 28 entries for Ubuntu 10.04.1 LTS and it grows every time I do GC>Save.

This is a new and updated install of 10.10 by the way.

It all seems very hit and miss.

Any help would be appreciated.

---

### Post by drs305 on 2011-04-05
dave_h,

Since you are getting system-generated error message, I would recommend purging and reinstalling grub-pc and at least temporarily removing GC as well. Once you get G2 working normally you can try GC again if you wish.

Here is how I would do it. You might want to copy your /etc/grub.d folder in case you decide you need something from it later.
```
sudo cp -R /etc/grub.d/ /root/Desktop  # Copy /etc/grub.d to root's Desktop
sudo apt-get update # Make sure you have a working Internet connection
sudo apt-get purge grub-common # Will remove grub-common and grub-pc
# Remove any remaining GC folders in /etc/grub.d, leave memtest alone.
sudo apt-get install grub-pc # Space bar to select drive only, TAB to OK
```
You will now be back at a default Grub2 setup. Update-grub should have run and generated a new menu without any errors. This should have removed the '28 entries' and you can start over with GC if you wish.

As far as the "Install to MBR" question, it runs "sudo grub-install /dev/sdX". I'm assuming if you don't specify anything it will write to your Ubuntu drive's MBR. The command writes instructions to the MBR to look for the boot files in your current OS and ensures the Grub2 files in this OS are controlling things and generating the menu.

---

### Post by MiThRaZoR on 2011-04-05
This is awesome. Thanks!

---

### Post by telovin on 2011-04-10
Hi drs305,

I open GC, it asks for password, I enter my admin password, it runs and again shows me the error message

"grub-mkconfig couldn't be executed successfully. You must run this as root!"

But I had entered my admin password while opening it! How to run GC?
I tried from terminal sudo gksu grub-customizer, it launches GC but same error comes up.
I am using Natty. Today I got a message saying that I am not using genuine ubuntu. Don't know why.

---

### Post by drs305 on 2011-04-10
> **telovin said:**
> Hi drs305,

I open GC, it asks for password, I enter my admin password, it runs and again shows me the error message

"grub-mkconfig couldn't be executed successfully. You must run this as root!"

But I had entered my admin password while opening it! How to run GC?
I tried from terminal [COLOR="Red"][COLOR="Red"]sudo gksu grub-customizer[/COLOR][/COLOR], it launches GC but same error comes up.
I am using Natty. Today I got a message saying that I am not using genuine ubuntu. Don't know why.

From the command line, try "gksu grub-customizer". Don't put 'sudo' at the start since 'gksu' replaces it for graphical apps.

You could try running some other GUI app as root just to see if the problem is with GC or if it is with your system and sudo.

The following should open your fstab file and allow you to edit and save it. If it works the problem isn't with "gksu", "gksudo" or "sudo".
```
gksu gedit /etc/fstab
```

---

### Post by telovin on 2011-04-11
Hi dr s305,
I tried gksu grub-customizer, then also I was getting the error you must run this as root.
I tried sudo grub-mkconfig, It showed all the entries but I couldnt edit it.
gedit command that you gave opened that gedit window. Didn't know what to put it in there. I have saved some entries to put in gedit but before that wanted to consult with someone.

---

### Post by drs305 on 2011-04-11
> **telovin said:**
> Hi dr s305,
I tried gksu grub-customizer, then also I was getting the error you must run this as root.
I tried sudo grub-mkconfig, It showed all the entries but I couldnt edit it.
gedit command that you gave opened that gedit window. Didn't know what to put it in there. I have saved some entries to put in gedit but before that wanted to consult with someone.

The last command with gedit was just to see if you could open an app as root without an error. Apparently you can. The second command you ran also confirms this; the grub-mkconfig command doesn't allow you to input anything as it runs but what you saw looks normal.

So the problem is with grub-customizer. If you haven't already run it successfully, I'd recommend purging and reinstalling to see if that fixes things:
```
sudo apt-get purge grub-customizer
sudo apt-get install grub-customizer
```

---

### Post by telovin on 2011-04-11
Hi drs305,
Yes drs,my problem is with grub customizer. I entered the commands on terminal, it removed customizer but I don't think it reinstalled it.
Copying and pasting the results of the commands here.


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hwinfo libhd16
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-customizer*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 946kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 158266 files and directories currently installed.)
Removing grub-customizer ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for python-support ...
vinu@vinu-desktop:~$ sudo apt-get install grub-customizer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package grub-customizer
vinu@vinu-desktop:~$ 
```

---

### Post by drs305 on 2011-04-11
> **telovin said:**
> Hi drs305,
Yes drs,my problem is with grub customizer. I entered the commands on terminal, it removed customizer but I don't think it reinstalled it.

No, it wasn't reinstalled. Perhaps you don't have Daniel Richter's repository still in your sources.list. 

Just go back to the first post and run the installation steps. It will add the repository and should install properly.

---

### Post by telovin on 2011-04-11
I am unable to install or remove any softwares from any where, not from terminal, not from softwrae sources  and not from synaptic and not from ubuntutweak.Using natty

---

### Post by drs305 on 2011-04-11
> **telovin said:**
> I am unable to install or remove any softwares from any where, not from terminal, not from softwrae sources  and not from synaptic and not from ubuntutweak.Using natty

Your problem running grub-customizer then probably is not with that package but with either sudo or some kind of permission problem.

You might want to make a new thread in the Natty testing forum. Explain what you can and cannot do regarding running commands with "sudo" and "gksudo" as well as your installation problems.

---

### Post by CapeJag on 2011-04-12
I am relatively new to ubuntu although my Unix experience goes back 20+ years!!!  

Had some problems getting Grub Customizer to install.  Finally resorted to command line and probably have bollexed up some stuff in the process.  There seemed to be an error in the 'batch' files supplied by Mr. Richter for Maverick/AMD64 environment [have Maverick version installed on AMD64 machine - so think that's where I was directed].

Package manager continually error-ed out 'on line 3' with what looked like command line residue of something like "omizer maverick ..."
  
Grub Customizer has successfully executed, haven't attempted reboot with changes yet 
:???:  got my fingers crossed.

Have attached some of the command line results (with errors) hope it helps someone.

---

### Post by telovin on 2011-04-16
Hi,
I reinstalled my Grub customizer.
I sometimes get a message saying you are not using genuine Ubuntu. I first downloaded karmic to a CD and installed it on my desktop. Then upgraded to lucid lynx and now using natty. Before using natty, I changed my mother board and processor. After that I get the message you are not using genuine Ubuntu. Is my Grub customizer problem associated with this? I have grub customizer which just disappears and I am discussing the same in launchpad. Just wanted to know if the above said Ubuntu message is messing up with my Grub Customizer. Under Ubuntu tweak-package cleaner-clean kernels does not show anything. Synaptic shows only 2 linux images. My grub manager shows four linux iamges, 2 memtests and 3 windows entries now.

---

### Post by drs305 on 2011-04-16
> **telovin said:**
>  Just wanted to know if the above said Ubuntu message is messing up with my Grub Customizer. Under Ubuntu tweak-package cleaner-clean kernels does not show anything. Synaptic shows only 2 linux images. My grub manager shows four linux iamges, 2 memtests and 3 windows entries now.

I don't know what triggers the "not genuine Ubuntu" message but suspect it has something to do with unofficial repositories. As to whether it is related to your issue I can't say, but if you are using relatively common third-party repositories I wouldn't think it would matter.

As for the 2 vs 4 linux images, perhaps the extra two you are seeing are the recovery mode options. By default, G2 will display both the kernel and the kernel's recovery mode option - essentially doubling the number of displayed kernel entries. 

I don't know why Ubuntu Tweak isn't displaying any extra kernels. It may not display them if they are both the same kernel version and one is "-generic" or "generic-pae".

---

### Post by telovin on 2011-04-16
Hi Drs305,
I backed up the files of grub.d and deleted teh old ones in grub.d added new. Still it was not working out. I backed up my grub.cfg and did ```
sudo update-grub
```. After athat I am able to launch my Grub customizer with ```
gksu grub-customizer
``` command. Now I am able to launch grub customizer, I editted and saved the entries :) I am happy . Thanks a lot drs305 for all your useful suggestions.I did mention the problem in launchpad thinking it was a bug. Then Dan and his people helped me out to do the steps.
I am happy it is working again !;)

---

### Post by stanz on 2011-04-20
> **patrickl26 said:**
> I don't know why but when I try to run Grub Customizer, Ubuntu gets completely freezed and I can do nothing, just pressing the reset button.. :(
Tried to install with all the three possibilities but every time I have the same problem. I have no idea what I'm doing wrong.. please help! ;) Having Ubuntu 10.04
Pretty much the same here...after giving password-system seems to freeze & simply reboots!
I've been trying to run  it using gdb, but can't get anything into the file after entering 'run'.
Only when forgetting to 'sudo gdb...' did I have GC window come up and see it.
It was shaded and I got another window complaining 'needs root privy'.
This is fresh install 10.04.1, and updated as they come in.

GC has worked for me on 10.04-2, so I'm wondering why.
What can I do to collect & offer some info?

---

### Post by drs305 on 2011-04-20
> **stanz said:**
> GC has worked for me on 10.04-2, so I'm wondering why.
What can I do to collect & offer some info?

I'm not sure what is happening but your best option is probably to visit the Launchpad Grub-Customizer page. There are links to recent bug reports, an FAQ, and you can probably contact it's developer, Daniel Richter.
[https://launchpad.net/grub-customizer]("https://launchpad.net/grub-customizer")

---

### Post by amont on 2011-04-29
Thank you again, Daniel, for this nice tool. I have seen the changes I  made with the old method and I have added an image. (First tried jpg, not working, but then png, yes).

By the way, is there a trick to predefine an entry, not by position, but by name? Because, you know, every time a new kernel version is added, the other entries are pushed down, so its position varies.

Thank you again for your time and your guidance.

---

### Post by drs305 on 2011-04-29
> **amont said:**
> By the way, is there a trick to predefine an entry, not by position, but by name? Because, you know, every time a new kernel version is added, the other entries are pushed down, so its position varies.

Things change in Grub 1.99/Natty, as it introduces submenus (where older kernels are stored). But for Lucid, you can specify the *title* rather than the *number* in the "GRUB_DEFAULT=" setting of /etc/default/grub. And it won't matter what position it occupies in the menu.

You would place the exact name as it appears in /boot/grub/grub.cfg (between the quotes). An example might look like:
> 
GRUB_DEFAULT="Ubuntu, with Linux 2.6.35-28-generic-pae"

It appears that you can do the same thing via Grub Customizer: Edit > Preferences: General tab. Click on 'default entry' > predefined. Click on the 'entry 1' selection box. It will expand; select the name from the right column. Click 'Save' to configure Grub 2 according to GC's scripts.

---

### Post by amont on 2011-04-30
> **drs305 said:**
> Things change in Grub 1.99/Natty, as it introduces submenus (where older kernels are stored)...

That's fine, because I'm setting up a netbook for a relative and I have installed 11.04 Natty. (For my own netbook, first entry is OK :) )
Regards.

---

### Post by joemilx on 2011-04-30
An excellent tool!  Accomplished a change in two keystrokes that would have taken 15 minutes previously.  Many, many thanks!

---

### Post by Pro$pect on 2011-05-05
I can't get the background image to work...I changed my resolution to match the image and then clicked copy to grub directory, saved and rebooted but nothing changed.

---

### Post by drs305 on 2011-05-05
> **Pro$pect said:**
> I can't get the background image to work...I changed my resolution to match the image and then clicked copy to grub directory, saved and rebooted but nothing changed.

The first two things I would do to troubleshoot this:

1. Run "sudo update-grub" and watch the terminal to see if it finds the image. There will be a message similar to "Found background image: ..." if it finds the image. If it doesn't, most likely the path is incorrect.

2. The second thing to try would be to install "grub2-splashimages", then copy one of the images from /usr/share/images/grub to where your current image is, and then use that image. If it works, there is a problem with the image you are using.

---

### Post by Pro$pect on 2011-05-05
it found the background image running update-grub.

I installed the splashimages, copied it over to where the image I was trying to use before and unchecked the custom resolution box. still didn't work...

---

### Post by drs305 on 2011-05-05
> **Pro$pect said:**
> it found the background image running update-grub.

I installed the splashimages, copied it over to where the image I was trying to use before and unchecked the custom resolution box. still didn't work...

We might be able to learn something from the boot info script. If you would like to download and run it, then post the RESULTS.txt we can take a look at your boot files. The one caveat is that I don't know how much of the script picks up Grub Customizer modifications, but we can see.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Pro$pect on 2011-05-05
here is the results file:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   482,371,583   482,369,536  83 Linux
/dev/sda2         482,373,630   488,396,799     6,023,170   5 Extended
/dev/sda5         482,373,632   488,396,799     6,023,168  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9ac30183-21d3-4394-939d-e2ed98839da4   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9e22ad1e-a652-46be-bd7f-0ac53b224afa   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 9ac30183-21d3-4394-939d-e2ed98839da4
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 9ac30183-21d3-4394-939d-e2ed98839da4
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 9ac30183-21d3-4394-939d-e2ed98839da4
insmod jpeg
if background_image /boot/grub/94.jpg; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9ac30183-21d3-4394-939d-e2ed98839da4
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=9ac30183-21d3-4394-939d-e2ed98839da4 ro  vga=775  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9ac30183-21d3-4394-939d-e2ed98839da4
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=9ac30183-21d3-4394-939d-e2ed98839da4 ro single  vga=775
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9ac30183-21d3-4394-939d-e2ed98839da4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 9ac30183-21d3-4394-939d-e2ed98839da4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=9ac30183-21d3-4394-939d-e2ed98839da4 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sdb5 during installation
UUID=9e22ad1e-a652-46be-bd7f-0ac53b224afa none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 193.4GB: boot/grub/core.img
  39.5GB: boot/grub/grub.cfg
   4.9GB: boot/initrd.img-2.6.38-8-generic
 193.4GB: boot/vmlinuz-2.6.38-8-generic
   4.9GB: initrd.img
 193.4GB: vmlinuz

```

---

### Post by drs305 on 2011-05-05
Pro$pect,

Thanks for posting. Is the image you are trying to use */boot/grub/94.jpg*?

I will install Grub Customizer and see how it handles images and how it integrates into the boot info script. I see the mention of 94.jpg but will have to experiment with GC myself unless someone else comes along.

---

### Post by Pro$pect on 2011-05-05
yes the image is 94.jpg but the second one I tried using from grub splashimages is Lake_mapourika_NZ.tga

---

### Post by drs305 on 2011-05-05
I installed GC and the grub2-splashimages package. My grub.cfg file looks the same as yours except I see you are still using a jpg image - I assume this is yours unless you converted one of the downloaded images. The package files are all .tga files.

If the one you are using is not one of the downloaded images, make sure the image is RGB (you can tell in Gimp via Image > Mode. Make sure it's RGB and not Indexed). 

If this doesn't solve things, and you haven't tried using one of the /usr/share/images/grub tga files, try one of those.

The only other difference I see is your resolution is set to a specific value while mine is set to auto. You could try manually editing /boot/grub/grub.cfg and changing the gfxmode setting to  "set gfxmode=auto". If you try this, do not update-grub before rebooting.

Edit: Looks like you edited your post as well and have already tried a .tga file...

[COLOR="Red"]Edit 2[/COLOR]
One other thing that may have happened. Grub 1.99 (Natty) uses the first image file it finds in /boot/grub if you haven't specifically designated it in /etc/default/grub with the GRUB_BACKGROUND setting. When you set the image in GC and 'save' it should use the correct file, but to be absolutely sure I'd remove any other images from /boot/grub and leave only the one you really want to use.

[COLOR="Red"]Edit 3[/COLOR]
I've just confirmed my suspicions in Edit 2. Even though I selected the tga file I placed in /boot/grub, with an old .png file in the same folder, grub.cfg used the .png file instead. So if your .jpg file is bad, Grub2 may not have used the .tga file. I'd remove your jpg file and select the tga file once more in Grub Customizer. Don't forget to press SAVE.

---

### Post by Pro$pect on 2011-05-05
I went into the grub folder and deleted all the images I previously tried to use, then in grub customizer I selected a .tga file from grub splashscrens, left the customize resolution button unchecked, hit copy to grub dir, and then save. I restarted and still didn't work...so I edited the grub cfg file to set gfxmode to auto and nothing has changed. :confused:

---

### Post by drs305 on 2011-05-05
](*,)

Does your grub.cfg contain these entries:
> if background_image /boot/grub/<name.of.your.image.tga>; then
  true
else

Perhaps something I wrote in this guide last week might cover what I'm missing:
[Grub 2 Drop-In Backgrounds & Font Selection]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by Pro$pect on 2011-05-05
yes it does right here:
```

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 9ac30183-21d3-4394-939d-e2ed98839da4
insmod tga
if background_image /boot/grub/Lake_mapourika_NZ.tga; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

```

i'll have to look through that guide.

---

### Post by Pro$pect on 2011-05-05
its just weird that update-grub gives me this...

> 

Generating grub.cfg ...
using custom appearance settings
Found background image: Lake_mapourika_NZ.tga
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
 

so it should work

---

### Post by drs305 on 2011-05-05
> **Pro$pect said:**
> its just weird that update-grub gives me this...

I know GC creates some of its own files and moves the originals to a temporary file. Seeing what you just posted, "using custom appearance settings" must be something inserted into the grub.cfg file by GC. It's not a normal Grub2 message. Since anything GC does should make its way into grub.cfg, I haven't asked to see any other files.

About the only suggestion I can offer at this point is to remove GC and revert to a standard G2 setup to see if it will work for you without GC's assistance.

I've found the fastest way for me to revert the settings is to quickly purge/reinstall grub-common/grub-pc, but I know exactly what settings to change once I'm back to the defaults. 

sudo apt-get update # Update repositories and make sure Internet is working.
```
sudo apt-get purge grub-common
sudo apt-get install grub-pc # TAB to OK when asked, SPACEBAR to select sda, then TAB to OK
```

The GC has instructions for how to restore things to the defaults, I just find the above easier for me to understand.

---

### Post by Jeff.Smith on 2011-05-08
Really helpful stuff man thanks a lot. :KS

---

### Post by geazzy on 2011-05-09
thanks for this tutorial :D

---

### Post by cyberjar09 on 2011-05-10
I have a question that probably borders 'silly'. 

Whats the difference between what this program achieves and what plymouth does? Upon installing plymouth I still dont see any difference in my boot screen in spite of applying a theme.

---

### Post by drs305 on 2011-05-10
> **cyberjar09 said:**
> I have a question that probably borders 'silly'. 

Whats the difference between what this program achieves and what plymouth does? Upon installing plymouth I still dont see any difference in my boot screen in spite of applying a theme.

This program only affects Grub and the boot sequence. (Well, you could argue that it can add kernel parameters that will influence how the OS runs.)

The graphic images are only for the initial boot screen - what you see *behind* the menu entries on the Grub screen. Grub runs before any OS is loaded; plymouth is loaded and comes into play only after Grub passes control over to the kernel/OS. Splash images you see later on in the boot process aren't controlled by Grub.

---

### Post by cyberjar09 on 2011-05-10
> **drs305 said:**
> This program only affects Grub and the boot sequence. (Well, you could argue that it can add kernel parameters that will influence how the OS runs.)

The graphic images are only for the initial boot screen - what you see *behind* the menu entries on the Grub screen. Grub runs before any OS is loaded; plymouth is loaded and comes into play only after Grub passes control over to the kernel/OS. Splash images you see later on in the boot process aren't controlled by Grub.

That's great. Thanks for breaking it down for me.

---

### Post by dan1981football on 2011-05-11
Hey everybody..!

So made the jump and got 11.04 ubuntu.. I've created a dual boot for Windows 7 and Ubuntu. Wow what a jump!!

Anyways.. all seems okay, i've installed UBUNTU okay updated everything, figured out a little about terminal and just learning how to use synaptic manager..

I'd love to change the GRUB screen to something prettier than the horrible purpley pink thingy,,

I have tried GRUB customizer and downloaded at 1280 x 1024 pic and placed it in the root grub, i've as well changed the colour and the file names to what it reads..

When i restart, the file names have changed but its still the horrible pinky colour like nothing has happened. The background pic is also not there

I'm going despair over it.. i've tried everything, i've read forum posts but its all rather complicated..

Please can somebody help me.. i admit i'm a complete newbie so may need help explained to me in plain easy to understand english please..

Many thanks for taking the time to read this 

Dan

---

### Post by drs305 on 2011-05-11
> **dan1981football said:**
> I'd love to change the GRUB screen to something prettier than the horrible purpley pink thingy,,

I have tried GRUB customizer and downloaded at 1280 x 1024 pic and placed it in the root grub, i've as well changed the colour and the file names to what it reads..Dan

Dan,

First, let's be sure we are talking about the same screen. The Grub Customizer & Grub only change the background of the screen with the menu entries (kernels, Windows, etc). There is another screen later as the system boots that is not controlled by Grub...

If you will post the contents of /boot/grub/grub.cfg we can take a look at what Grub2 is trying to do. 

If you also attach a copy of the image you are trying to use we can make sure it is compatible. Or you can try this test image. Place it in /boot/grub and run 'sudo update-grub'.  (Sorry that it is purple too. ;-)  ).

**Added:**
I wrote guide about using background images in Natty. Here is the link:
[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by dan1981football on 2011-05-11
Hello.. thankyou so much for replying..!

Okies i have placed the picture you provided in my grub folder, i updated the grub using that terminal command thingy and reset my computer whilst crossing my fingers..

Unfortunately still the horrible sickly purpley colour thing with my 2 options of either booting Linux or Win 7

Here is my CFG
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 34a7812d-73f1-4c85-8999-c9ae5cb210c6
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 34a7812d-73f1-4c85-8999-c9ae5cb210c6
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 34a7812d-73f1-4c85-8999-c9ae5cb210c6
insmod jpeg
if background_image /boot/grub/family_guy.jpg; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu Linux 11.04" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34a7812d-73f1-4c85-8999-c9ae5cb210c6
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=34a7812d-73f1-4c85-8999-c9ae5cb210c6 ro  vga=775 splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 7" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root CEDE3F73DE3F52C7
	chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

```

---

### Post by drs305 on 2011-05-11
> **dan1981football said:**
> Hello.. thankyou so much for replying..!

Okies i have placed the picture you provided in my grub folder, i updated the grub using that terminal command thingy and reset my computer whilst crossing my fingers..

Unfortunately still the horrible sickly purpley colour thing with my 2 options of either booting Linux or Win 7

I've looked at the grub.cfg contents. The things I check are that the path and file appear, and that the 'menu_color_normal' has a second setting of 'black', which is the 'transparency setting. Both of these are in the 
*### BEGIN /etc/grub.d/05_debian_theme ###* section.

Things look correct for your image.

I took a shortcut in the explanation in the previous post since I didn't know the name of your image. When G2 sets the image found in /boot/grub, if it finds more than one it uses a set order to pick the image. I didn't explain this and hoped your's would be a .png. It wasn't, and since .jpg are used before .png images, your family_guy image is still in the grub.cfg file.

Move the family_guy.jpg out of /boot/grub, rerun 'sudo update-grub' and then check grub.cfg to make sure it list's a.png (or watch the terminal output when you update-grub - it will show the image being used).

If my attachment works, there is probably a problem with your image. The easiest way to fix it is to change it to a .png image with gimp or another graphics app. If you do this, after confirming my image worked, remove a.png since Grub will use a.png before family_guy.png.

---

### Post by dan1981football on 2011-05-11
IT WORKS!!!

Wow i cant believe it.. finally

Basically i deleted the family guy picture and put your one in there.. i then went update grub and restart..

Initially i thought nothing changed but then i noticed the blob on the bottom left hand corner!!

Hooray..

I then installed the default splash grub2 images and placed them in the grub boot folder.

Using grub customizer i selected which one i wanted, saved it.. updated grub again then rest..

VOILA.. i now have a pretty mountain to look at :)

Thankyou so much for taking the time to help me.. I am definetly going to get my head around Linux one day..

Just another quick question..

Is there anyway to make the font bigger in Grub?

Also,if i want to use my own picture as a Grub background what does it have to be?

Many thanks once again

---

### Post by drs305 on 2011-05-11
> **dan1981football said:**
> IT WORKS!!!
:)
> 
I then installed the default splash grub2 images and placed them in the grub boot folder.

Using grub customizer i selected which one i wanted, saved it.. updated grub again then rest..

You might want to refer to the link at the end of Post #103.  It details exactly how the image is selected in Grub 1.99 (Natty). The only reason I mention it is that Grub has a specific order it uses. GC uses the first option but I think it also employs a slightly different terminology.


> 
Is there anyway to make the font bigger in Grub?
In GC, it's under Preferences, Appearance. Custom Resoltuion.

> 
Also,if i want to use my own picture as a Grub background what does it have to be?
See the link.

Update:
I notice that my GC doesn't show the different custom resolutions available. You can find out which ones Grub can use on your machine by typing "vbeinfo" at the grub prompt (press 'c' to get to the prompt, then ESC back to the menu). 
If you want to set the resolutions manually, you can edit /etc/default/grub and modify this line (and remove the #):
> 
GRUB_GFXMODE=640x480

In Natty, the system defaults to the highest resolution so you might want to try 640x480, 800x600 or 1024x768, depending on what your system supports. It should adjust the image size based on the resolution you select. The smaller the numbers, the larger the text. Don't forget to update-grub after making the changes.

---

### Post by coljohnhannibalsmith on 2011-05-11
[[COLOR=#d40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")  Thank you for the additional information:

I've made a few attempts with GRUB Customizer and I have the following comments:

[I]* While GC allows me to select a splash-image; I must delete the image from /boot/grub before I can use another one.  Just selecting a different splash-image in GC doesn't work.

* Also, GC does not allow me to change the text color.  The text and highlight color defaults to light gray.  I haven't been able to change this, no matter what I've tried.[/I] [I]

* The bottom of some of my images are getting cut off; however the images with this problem have text near the bottom and were not designed as splash-images.  Thery're just images I like that    I got from the web.[/I] 

Is there some other setting that I've failed to change; or will I need to change text/highlight colors with the command line???


[COLOR=Red]Also, I've noticed that the PPA is from 2007.  Does this mean that the app is 'not' being maintained???[/COLOR]




[COLOR=Blue]Thanks, Hannibal[/COLOR]

Staff Note: This post was moved over from the following thread:
[http://ubuntuforums.org/showthread.php?t=1755799]("http://ubuntuforums.org/showthread.php?t=1755799")

---

### Post by coljohnhannibalsmith on 2011-05-12
More Information/Mas Informacion/Mehr Data

Well,

I've had no end of trouble with GRUB Customizer.  I've even run it from the command line with ***root*** permissions; but it 'still' won't change the *[COLOR=Red]font[/COLOR]* or [COLOR=Blue]***highlight***[/COLOR] colors under Natty.  This is either because it cannot find the correct file to modify, or it does not have the correct permissions.  It certainly looks like it doesn't have the correct permissions; as this behavior was noted by someone commenting on his site, prior to the release of Natty.  However, it appears to me that under Natty; GC can not locate the correct file to modify ***either.***  This may be due to the changes in GRUB between GRUB 1.98 & 1.99; so IMHO both issues are currently present under Natty.

**Conclusion:**

This program needs some serious patches to work under Natty.  There are two approaches to this.  Two versions of this app can be released; one to work on apriori GRUB 1.99 distos, and another to work on aposteriori  GRUB 1.99 distros.  The second & cleaner approach would be to add a few lines of code to check for the GRUB version, and then execute the appropriate application code for the appropriate version of GRUB.  The latter approach would initially be more difficult to code; but ultimately much easier to maintain. Also, since the utility of having this program run in a GUI is to relieve the operator of repetitive and often arcane command line tasks; this app defeats itself in this regard.  To be a useful app for the average user, the above mentioned issues need to be resolved ***and ***the app needs to ***ask for root permissions*** when launched or run natively with them.  Also, to be added to ***Ubuntu System Settings,*** as previously suggested, the skins would have to be changed to match the skins present in the parent application.  This means that some of the UI coding would have to be done by our own development staff; and that means adopting this orphan.  However IMO the potential usefulness of this app justifies this.

**In Summary:**

A potentially very useful app, which needs a lot of TLC.

In the meantime, I ***'cannot'*** recommend this app for anyone running ***Natty/GRUB => 1.99.***



[COLOR=Blue]Hannibal[/COLOR]


P.S., ***does anyone know how to get the source for this app?***

---

### Post by drs305 on 2011-05-12
> **coljohnhannibalsmith said:**
> [[COLOR=#d40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")  Thank you for the additional information:

While GC allows me to select a splash-image; I must delete the image from /boot/grub before I can use another one.  Just selecting a different splash-image in GC doesn't work.

[SIZE="3"][COLOR="DarkRed"]Added: **Grub Customizer's developer, Daniel Richter, responds in Post #118, on how to use background images with Grub 1.99.[/COLOR]**[/SIZE]

I was afraid of that. The priority for Grub 1.99 using background images is the following (more detail in Post #1):
[LIST]
[*]GRUB_BACKGROUND=</path/filename> setting in /etc/default/grub
[*]First image found in /boot/grub
[*]Wallpaper designated in /usr/share/desktop-base/grub_backgorund.sh (if desktop-base installed)
[*]/usr/share/images/desktop-base/desktop-grub.png (if desktop-base is installed)
[*]Default theme (no image): Aubergine background, selected item black on light gray background)
[/LIST]
Unfortunately, Grub Customizer uses it's own designation in /etc/default/grub: 
> GRUB_MENU_PICTURESince it is not in the format "GRUB_BACKGROUND", G2 apparently continues to the second priority (in Grub 1.99), finding a file in /boot/grub. It appears that the way GC inputs the background image information results in a lower priority than images still residing in /boot/grub.

You can 1) remove the images in /boot/grub or 2) remove the image from the GC page and then manually edit /etc/default/grub and use the "GRUB_BACKROUND=" convention.

> 
* Also, GC does not allow me to change the text color.  The text and highlight color defaults to light gray.  I haven't been able to change this, no matter what I've tried.I just tried this and get a similar result. Apparently this is another Grub 1.99 change that hasn't been incorporated in GC yet.

The workaround is to manually edit /etc/grub.d/05_debian_theme and make the changes to the following lines (approx line 32/33), 
> echo "${1}set menu_color_normal=white/black"
echo "${1}set menu_color_highlight=black/light-gray"or run the following command(s), changing the **bold** color values from the default. (I'd recommend manually editing so you see the result, but here is the command line version):
> sudo sed "s/set menu_color_normal=white\/black/set menu_color_normal=**green**\/black/g" -i /etc/grub.d/05_debian_theme
sudo sed "s/set menu_color_highlight=black\/light-gray/set menu_color_normal=**yellow\/blue**/g" -i /etc/grub.d/05_debian_theme
sudo update-grub
In either case, you would want to keep 'black' as the second value in the 'menu_normal_color' entry to retain transparency. Don't forget to update grub.

> 
Also, I've noticed that the PPA is from 2007.  Does this mean that the app is 'not' being maintained???That is just the developer's repository name. He only created Grub Customizer within the past year and continues to update it. Apparently he has not incorporated all changes made by Grub 1.99 at this time. 


Staff Note: This post was moved over from the following thread:
[http://ubuntuforums.org/showthread.php?t=1755799](http://ubuntuforums.org/showthread.php?t=1755799)

---

### Post by Cpierce on 2011-05-12
Hey drs305,
You helped with this a while back, and I see you are still at it. Just wanted to take the time to say Thank You for all the hard work. We all appreciate it very much.

---

### Post by drs305 on 2011-05-12
coljohnhannibalsmith,

I was composing my last entry while you posted.

I agree there are some major deficiencies with Grub Customizer and Grub 1.99. I am going to make notes in the original post.

Daniel monitors this thread (at least occasionally) and he has always been very responsive to issues with his app.

If I didn't cover your specific issues on how to get your images/fonts working, continue to post here, or over in your original thread for non-GC solutions.

@ cPierce, thank you.

---

### Post by coljohnhannibalsmith on 2011-05-12
> **drs305 said:**
> That is just the developer's repository name. He only created Grub Customizer within the past year and continues to update it. Apparently he has not incorporated all changes made by Grub 1.99 at this time.

Perhaps I was a bit hasty to refer to this app as an ***orphan***.  I've just had lots of trouble with GC; and I've seen a lot of my favorite apps stop being maintained...

I think my final note before I let the adults take over:

Since this app appears to need a recode; I'd like to see the following options added to the ***appearance*** tab:

*menu_color_normal=white/black
*menu_color_highlight=yellow/black


These options affect the text and background ***'outside'*** of the menu area.  These options are ***'not'*** currently incorporated.




Hannibal

---

### Post by drs305 on 2011-05-12
I've submitted a bug report on the issues we've recently discussed. 
[https://bugs.launchpad.net/grub-customizer/+bug/781683]("https://bugs.launchpad.net/grub-customizer/+bug/781683")

> These options affect the text and background 'outside' of the menu area. These options are 'not' currently incorporated.
Just an elaboration: 
The *menu_color_normal* and *menu_color_highlight* affect the colors *within* the borders. If the *menu_color_normal* is not specified, color_normal is used.

You are correct that GC attempts to set "color_normal" and not "menu_color_normal", so it would be a nice addition.

---

### Post by coljohnhannibalsmith on 2011-05-12
[COLOR=Blue][The workaround is to manually edit /etc/grub.d/05_debian_theme and make the changes to the following lines (approx line 32/33), 

echo "${1}set menu_color_normal=white/black"[/COLOR]    [COLOR=Blue]
echo "${1}set menu_color_highlight=black/light-gray"]
[/COLOR] 
Will this 'mod' allow the colors to be set within GC???

Also, will I have to delete or comment-out the previous edits to lines +98???




Thanks, Hannibal

---

### Post by drs305 on 2011-05-12
> **coljohnhannibalsmith said:**
> The workaround is to manually edit /etc/grub.d/05_debian_theme and make the changes to the following lines (approx line 32/33), 

echo "${1}set menu_color_normal=white/black
echo "${1}set menu_color_highlight=black/light-gray"]

Will this 'mod' allow the colors to be set within GC???

No it won't unfortunately. GC doesn't appear to have that functionality. 

> 
Also, will I have to delete or comment-out the previous edits to lines +98???

You can leave those set if you wish. Those values don't come into play if Grub finds a background image. 

As far as their thinking, the developers just decided to use a default menu setting of white text (over the user's background image), with black text on a solid gray bar for the highlighted menuentry. 

They chose a solid bar for the selected text to prevent a "light-gray text on a light-gray background" scenario, which could have happened if they had made the bar transparent. They would have no idea of what color your image would be.

---

### Post by divlyfein on 2011-05-14
Can you please help with an issue I am having with changing the GRUB background? I have tried everything and read into every solution, but no matter what, it is always the purple background when I log in.

I did try restoring GRUB to its default settings as well as trying many different images. I tried your previously posted a.png as well as the splash image pack you can download. When I run sudo update-grub it displays:

```
Found background image: 050817-N-3488C-028.tga
```

So I'm assuming it should have worked, but it has not. I am using Ubuntu 11.04 installed from Windows 7 "wubi". I am wondering if thats a problem? 
Also when I try to set a background image from the GRUB command line it gives me an error saying unsupported bitmap. 

Here is my results from the boot info script if needed. The image is from the splash images download you recommended in the thread.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   954,488,831   951,414,784   7 HPFS/NTFS
/dev/sda3         954,488,832   976,773,119    22,284,288  17 Hidden HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       15caad1c-ca3d-40f5-89f7-bebff5c49843   ext4                                     
/dev/sda1        A4A056D5A056AE14                       ntfs       System                        
/dev/sda2        32CC7E06CC7DC51F                       ntfs       TI105835W0O                   
/dev/sda3        7AF6A473F6A430F5                       ntfs       HDDRECOVERY                   
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 32CC7E06CC7DC51F
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 32CC7E06CC7DC51F
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 32CC7E06CC7DC51F
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
insmod tga
if background_image /boot/grub/050817-N-3488C-028.tga; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 32CC7E06CC7DC51F
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=32CC7E06CC7DC51F loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 32CC7E06CC7DC51F
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=32CC7E06CC7DC51F loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root A4A056D5A056AE14
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 32CC7E06CC7DC51F
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 7AF6A473F6A430F5
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


  23.8GB: boot/grub/grub.cfg
   1.6GB: boot/initrd.img-2.6.38-8-generic
   5.1GB: boot/vmlinuz-2.6.38-8-generic
   1.6GB: initrd.img
   5.1GB: vmlinuz
```

---

### Post by danielrichter on 2011-05-14
Grub Customizer already sets the background image correctly (using the file /usr/share/desktop_base/grub_background.sh). As far as I know this is still the only way to set image and colors without modifying the script itself (05_debian_theme). But if the new grub script finds an image inside the grub directory it will use this instead of the image defined in grub_background.sh… and in this way, font colors will be ignored too.

So the way around this issue is simple: remove all the images, which are still saved in /boot/grub (sudo rm -i *.jpg *.JPG *.jpeg *.JPEG *.png *.PNG *.tga *.TGA) and set the new image using grub customizer **without clicking copy to grub directory** - also if the device isn't accessible when booting (the grub script find's out if this is the case or not and cache the image, if necessary).

@divlyfein
yes, the new grub seems to be still more selectively according to the image then the old one. I tried the default wallpapers of ubuntu without success. Then I drawed an own image and saved as png - and this one has been loaded/displayed. If grub says "unsupported bitmap" this isn't a config problem - grub itself doesn't support this type of image. Maybe you should contact the grub2 developers.

---

### Post by drs305 on 2011-05-14
Thanks for responding in the thread Daniel. I've updated the first post a bit and referred to your post at the point of the thread where we begin discussing images in Grub 1.99.

---

### Post by drs305 on 2011-05-14
> **divlyfein said:**
> Can you please help with an issue I am having with changing the GRUB background? I have tried everything and read into every solution, but no matter what, it is always the purple background when I log in.

I did try restoring GRUB to its default settings as well as trying many different images. I tried your previously posted a.png as well as the splash image pack you can download. When I run sudo update-grub it displays:

```
Found background image: 050817-N-3488C-028.tga
```

So I'm assuming it should have worked, but it has not. I am using Ubuntu 11.04 installed from Windows 7 "wubi". I am wondering if thats a problem? 
Also when I try to set a background image from the GRUB command line it gives me an error saying unsupported bitmap. 

I am not a frequent user of Wubi but I just uninstalled an old version and installed Wubi's Natty version. 

Upon inspeciting the contents of grub.cfg, the Wubi version does not load the modules necessary for rendering .tga, .png and .jpg images. I next inspected the /boot/grub folder, and the modules are not present.

It appears the developers did not incorporate loading the necessary modules to allow background images in Wubi.

The modules *are* stored in /usr/lib/grub/i386 so it would be possible to modify grub.cfg to load the tga module, and possibly be able to use a background image.

Even though Grub Customizer can be used with Wubi and offers to install a background, now that it has been pointed out I'd prefer not to let this thread get into discussions about Wubi background issues.

I would ask if any Wubi user has been able to use background images to let us know. If I get a definitive answer that it won't work I'll note it in the first post.

I encourage you to post a new thread or search the forums for an answer to the basic question of whether Wubi supports background images for Grub, and I might even try my suggestion above to see if it does work.

---

### Post by coljohnhannibalsmith on 2011-05-15
[I][B][COLOR=Red]You guys are doing such a great job!!!

Please keep up the good work!!! 
[/COLOR] [/B][/I]
[IMG]http://images.sodahead.com/polls/001461285/5554511944_goodjob_answer_5_xlarge.png[/IMG]


[COLOR=Red]***Thanks Hannibal***[/COLOR]

---

### Post by ghostcatzero on 2011-05-18
Just wanted thank telovin for this post:
> **telovin said:**
> ...I backed up the files of grub.d and deleted teh old ones in grub.d added new. Still it was not working out. I backed up my grub.cfg and did ```
sudo update-grub
```. After athat I am able to launch my Grub customizer with ```
gksu grub-customizer
``` command. Now I am able to launch grub customizer...
I had been monkeying around with the Grub file and forgot to sudo update-grub. Once I did it, the error message telling me to run it as root went away. 

Thanks also to the developer of this GUI. I haven't played around with it much, but I'm hopeful that I my dual boot Natty & Peppermint netbook will boot more how I want it. Editing the Grub file didn't work for me, so here's hoping :)

---

### Post by ghostcatzero on 2011-05-18
> **ghostcatzero said:**
> ...I haven't played around with it much, but I'm hopeful that I my dual boot Natty & Peppermint netbook will boot more how I want it. Editing the Grub file didn't work for me, so here's hoping :)
Okay, I spoke too soon. I found the GUI really simple to use, but when I rebooted the changes I saved weren't reflected in the Grub at startup. I successfully ran "sudo update-grub", rebooted again, and Grub's still showing the default menu with none of my edits.

---

### Post by drs305 on 2011-05-18
> **ghostcatzero said:**
> Okay, I spoke too soon. I found the GUI really simple to use, but when I rebooted the changes I saved weren't reflected in the Grub at startup. I successfully ran "sudo update-grub", rebooted again, and Grub's still showing the default menu with none of my edits.

Did you remember to press 'Save' after making the changes in GC? Running update-grub wouldn't incorporate GC's changes unless you had saved it's configuration.

The second thing to check is whether you made the changes on the controlling Grub2 files. It's possible you are making changes to your current system files but the other OS's system files control the boot process.

If you have multiple installations, you can tell which one is controlling Grub by seeing which kernel is listed first (or pressing 'e' and checking the UUID if you have the same kernel). Of course that assumes you haven't reordered the menu.

---

### Post by ghostcatzero on 2011-05-18
I'm pretty sure I saved my changes. I know I clicked save multiple times as I made changes. 

I assume the Ubuntu 11.04 partition controls the Grub, since the Peppermint partition is only 6GB compared to over 100GB for Ubuntu plus Ubuntu is the first distro I installed on this machine. But I'll make sure. The first item in the Grub list at startup is Peppermint so it's possible that's the distro I need to make the changes in. I'll try it from there.

---

### Post by ghostcatzero on 2011-05-18
I downloaded Grub Customizer to my Peppermint partition and it worked perfectly. Thanks!

---

### Post by drs305 on 2011-05-18
> **ghostcatzero said:**
> I assume the Ubuntu 11.04 partition controls the Grub, since the Peppermint partition is only 6GB compared to over 100GB for Ubuntu plus Ubuntu is the first distro I installed on this machine. 

Glad it's working. The size of the OS really won't determine which Grub controls. I suspect the Peppermint installation overwrote the MBR and took control of the boot, which is the normal behavior of most OS's. 

As more and more users play with multiboot systems, especially similar ones like the Ubuntu family, it's easy to lose track of which Grub is controlling things. I use a different splash screen for each OS.

If you ever want to regain Grub control on your current linux OS, it's easy to do. This command assumes sda is the drive BIOS boots.
```
sudo grub-install /dev/sd[COLOR="Red"]a[/COLOR]
```

---

### Post by ghostcatzero on 2011-05-18
It's not really all that important to me which OS controls Grub, unless I were to decide to switch out Peppermint for another lightweight distro. Would that cause more Grub problems, or would the system handle it pretty smoothly?

---

### Post by drs305 on 2011-05-19
> **ghostcatzero said:**
> It's not really all that important to me which OS controls Grub, unless I were to decide to switch out Peppermint for another lightweight distro. Would that cause more Grub problems, or would the system handle it pretty smoothly?

Overall G2 handles most mainstream distros fairly well. If you have problems it's been around long enough that we'll most likely have the correct menuentry if it fails.

It doesn't matter which Grub controls - until you are on the non-controlling one trying to make changes.  ;-)

---

### Post by von Stalhein on 2011-05-19
I see there's been GRUB 1.99 released drs305

[http://lists.gnu.org/archive/html/info-gnu/2011-05/msg00008.html](http://lists.gnu.org/archive/html/info-gnu/2011-05/msg00008.html)

Do you anticipate any changes/improvements that would affect anyone using GC if they upgrade?

---

### Post by drs305 on 2011-05-19
> **von Stalhein said:**
> I see there's been GRUB 1.99 released drs305

[http://lists.gnu.org/archive/html/info-gnu/2011-05/msg00008.html](http://lists.gnu.org/archive/html/info-gnu/2011-05/msg00008.html)

Do you anticipate any changes/improvements that would affect anyone using GC if they upgrade?

The most noticeable change for the normal user is the introduction of submenus. Only the most recent kernel is now displayed on the main menu, with older kernels hidden in a submenu. This will prevent the main display growing as new kernels are introduced.

Mark Richter, Grub Customizer's creator, is busy incorporating the changes into the app. Some were easy and have been accomplished, some are more complex and are still being worked on.

Grub 1.99 also introduces the 'drop-in' Grub background. Here are a few threads I created about G 1.99:

[Grub 1.99 Changes]("http://ubuntuforums.org/showthread.php?p=10720322")

[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316")

[Grub 2 Drop-In Backgrounds & Font Selection]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by von Stalhein on 2011-05-19
^^
Thanks muchly, comprehensive as usual!! :)

---

### Post by nxmehta on 2011-07-04
I'm having problems setting the text colors when using a background image with Grub Customizer.  My root partition is configured as an encrypted lvm, which means that only /boot is accessible when grub starts.  Therefore, I have to copy my background into /boot/grub, which isn't a problem.  What is a problem is /etc/grub.d/05_debian_theme:

```

# First check whether the user has specified a background image explicitly.
# If so, try to use it. Don't try the other possibilities in that case
# (#608263).
if [ -n "${GRUB_BACKGROUND+x}" ]; then
	set_background_image "${GRUB_BACKGROUND}" || set_default_theme
	exit 0
fi

# Next search for pictures the user put into /boot/grub/ and use the first one.
for background in *.jpg *.JPG *.jpeg *.JPEG *.png *.PNG *.tga *.TGA; do
	if set_background_image "${background}"; then
		exit 0
	fi
done

# Next try to use the background image and colors specified by desktop-base.
if set_background_image "${WALLPAPER}" "${COLOR_NORMAL}" "${COLOR_HIGHLIGHT}"; then
	exit 0
fi

```

What crazy person wrote this code?

Here, it's clear that the sequence of steps for checking for a background image is:

1. Check GRUB_BACKGROUND
2. Check /boot/grub for the first image file
3. Use values from /usr/share/desktop-base/grub_background.sh

Only #3 applies menu colors (by passing colors to the set_background_image function).  The first two don't allow you to change colors.  So, if I have an image located in /boot/grub I never change menu colors.

I can certainly just hard code in a workaround, but I figured you might want to know about this and address it in Grub Customizer.

---

### Post by drs305 on 2011-07-04
> **nxmehta said:**
> 
Only #3 applies menu colors (by passing colors to the set_background_image function).  The first two don't allow you to change colors.  So, if I have an image located in /boot/grub I never change menu colors.

I can certainly just hard code in a workaround, but I figured you might want to know about this and address it in Grub Customizer.

I'm sure Daniel will see your post. 

I wrote about fonts/backgrounds in the following thread (and I agree Grub color schemes are not easy to understand). The thread is about Grub 1.99 but the color issues apply to 1.98 as well.
[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by danielrichter on 2011-07-05
> **nxmehta said:**
> I'm having problems setting the text colors when using a background image with Grub Customizer.  My root partition is configured as an encrypted lvm, which means that only /boot is accessible when grub starts.  Therefore, I have to copy my background into /boot/grub, which isn't a problem.

No, generally you don't have to copy your image anyway. In this case 05_debian_theme should detect your image as "not accassible on startup" and copying to /boot/grub by itself.

> **nxmehta said:**
> I can certainly just hard code in a workaround

First try the simple way - simply don't copy your image to /boot/grub and hope 05_debian_theme does it for you.

If this doesn't work, you can do it manually - the trick is to place your image as a hidden file inside /boot/grub (starting with a dot). 05_debian_theme doesn't find files starting with a dot when searching for an image.

> **nxmehta said:**
> but I figured you might want to know about this and address it in Grub Customizer.

My idea was just to remove the button "copy to grub directory" as 05_debian_theme is able to copy the image automatically. If not (please tell me your experiences) I could copy it as a hidden file (adding the dot).

---

### Post by nxmehta on 2011-07-07
> **danielrichter said:**
> No, generally you don't have to copy your image anyway. In this case 05_debian_theme should detect your image as "not accassible on startup" and copying to /boot/grub by itself.

Wow, you're absolutely right, 05_debian_theme copies the file to /boot/grub/.background_cache.png, which works fine.  Cool!  Thanks.

---

### Post by hariks0 on 2011-07-07
After upgrading to 11.04, my Burg went away. Only the GRUP 2 with old background image is there.

Any thoughts?

---

### Post by Gwaro on 2011-07-17
Thanks for being such a help.I successfully did it all but when it comes to using the Grub-customizer, i get the message 'grub-mkconfig couldn't be executed successfully.You must run this root!
How do i go about this?
Thank you.

---

### Post by drs305 on 2011-07-17
> **Gwaro said:**
> Thanks for being such a help.I successfully did it all but when it comes to using the Grub-customizer, i get the message 'grub-mkconfig couldn't be executed successfully.You must run this root!
How do i go about this?
Thank you.

You are altering system files so you could try starting GC from the terminal with:
```
gksu grub-customizer
```

---

### Post by larrivee013 on 2011-07-21
I was wondering if there is a way to put a background and put some big buttons instead of ugly text.

If I was not clear, something that looks like this :

[IMG]http://img13.imageshack.us/img13/7544/tripleboot1.jpg[/IMG][IMG]http://img13.imageshack.us/img13/7544/tripleboot1.jpg[/IMG][http://www.steussy.com/blog/wp-content/uploads/2008/11/triple_boot1.jpg](http://www.steussy.com/blog/wp-content/uploads/2008/11/triple_boot1.jpg)

Thanks

Keven


PS Should I install burg? If yes, where do I download the latest version?

---

### Post by drs305 on 2011-07-21
Hi Kevin. Welcome to the Ubuntu forums.

It's very easy to add a background image to the Grub2 menu, but how it is done depends on which version of Grub2 you are using. You can check on the Grub 2 menu display or run 'grub-install -v'.

For adding buttons you get into 'theming'. Grub 2 is progressing along those lines. There is another bootloader based on GRUB called BURG, which is more advanced on theming and you can search these forums for posts about BURG. (I have no problem with BURG, I just haven't used it or know much about it.)

For Grub 2, here is an excellent, very detailed, PDF file which will tell you what you need to know about Grub 2 theming, if you want to take the time to learn how to do it.
[http://www.4shared.com/file/lFCl6wxL/grub_guidetar.html]("http://www.4shared.com/file/lFCl6wxL/grub_guidetar.html")

---

### Post by drs305 on 2011-07-21
> **drs305 said:**
> Hi Kevin. Welcome to the Ubuntu forums.

It's very easy to add a background image to the Grub2 menu, but how it is done depends on which version of Grub2 you are using. You can check on the Grub 2 menu display or run 'grub-install -v'.

For adding buttons you get into 'theming'. Grub 2 is progressing along those lines. There is another bootloader based on GRUB called BURG, which is more advanced on theming and you can search these forums for posts about BURG. (I have no problem with BURG, I just haven't used it or know much about it.)

For Grub 2, here is an excellent, very detailed, PDF file which will tell you what you need to know about Grub 2 theming, if you want to take the time to learn how to do it.
[http://www.4shared.com/file/lFCl6wxL/grub_guidetar.html]("http://www.4shared.com/file/lFCl6wxL/grub_guidetar.html")

I'll also just mention we prefer to use small images, thumbnails or attachments on the Ubuntu Forums for both screen space and server storage limitations.

---

### Post by larrivee013 on 2011-07-21
Thanks a lot, I'll go read the PDF, but if I don't really understand, I'll install BURG. Another thing, when I try to install BUC, I get this :


> The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath.

:confused:


EDIT : The PDF is way over what I can do. Also, they don't even talk about Ubuntu 11.04 so I don't want to mess my system.

---

### Post by drs305 on 2011-07-21
> **larrivee013 said:**
> Thanks a lot, I'll go read the PDF, but if I don't really understand, I'll install BURG. Another thing, when I try to install BUC, I get this :

EDIT : The PDF is way over what I can do. Also, they don't even talk about Ubuntu 11.04 so I don't want to mess my system.

Yes, it's pretty detailed. For adding a background image in 11.04, Grub2 makes it pretty easy. Here is a guide I wrote about Grub 1.99 and backgrounds:
[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")
It may also look a bit complicated, especially the fonts section, but essentially you just drop an image file into /boot/grub.

As far as the error message - it could mean the package has a serious problem, but it could also be a minor bug. I generally take the advice of what Ubuntu tells me. You could do a search to see if others are having problems installing the package. Depending on your risk tolerance, you could download the .deb file (or it may already be in your /var/cache/apt/archives folder) and install it using:
```
sudo dpkg -i /path/filename.deb
```

---

### Post by larrivee013 on 2011-07-21
Thanks for the fast answer. I downloaded Burg-Manager, but I can't make buc work, I always get the error message. I've downloaded it from 3 places, and always the same thing... Really don't know what to do :(

---

### Post by drs305 on 2011-07-21
> **larrivee013 said:**
> Thanks for the fast answer. I downloaded Burg-Manager, but I can't make buc work, I always get the error message. I've downloaded it from 3 places, and always the same thing... Really don't know what to do :(

If you tried the dpkg method of installing it and it still doesn't work there may be real problems with the package. I don't know what 'buc' is. If you really want to get it installed I'd recommend googling other sites or start a new thread. Not many of our forumites will read this thread as it's a tutorial and most are not too concerned with Grub unless they are having problems. Hope you can get it resolved.

---

### Post by larrivee013 on 2011-07-21
Thanks! I finally got it! I've put a theme and it makes it really awesome! Really starting to love Ubuntu


Ubuntu :guitar:(Rocks!!! )

I've run BUC with GDebi Package Installer and now eveything works fine!

---

### Post by gbrunati on 2011-08-05
I've installed Grub Customizer in my Ubuntu 10.10 with Windows XP previous installed. I run the GC and Ubuntu boots Ok, but when I select the Windows XP boot option in the menu, get the "error: unknown filesystem / grub rescue" prompt.

I've tried several options before (eg. RESCATUX, manual configurations, etc) and always with unsuccessful results.

Any suggestion, please?

Thanks in advance,
GB   :confused:

---

### Post by drs305 on 2011-08-06
> **gbrunati said:**
> I've installed Grub Customizer in my Ubuntu 10.10 with Windows XP previous installed. I run the GC and Ubuntu boots Ok, but when I select the Windows XP boot option in the menu, get the "error: unknown filesystem / grub rescue" prompt.

I've tried several options before (eg. RESCATUX, manual configurations, etc) and always with unsuccessful results.

Any suggestion, please?

Thanks in advance,
GB   :confused:

Are you using a normal Ubuntu installation or Wubi (inside Windows)?

If you are using Wubi, I'd recommend posting in the Wubi megathread. The readers of that thread are very knowledgeable about Wubi issues. Post the contents of RESULTS.txt and describe your problem.

If this is a normal installation, please go to the following link and download/extract/run the boot info script and post the contents of RESULTS.txt.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

It sounds like you installed Grub2 to the Windows partition, in which case you will need to use the Windows disk to repair the boot files. But we will know more once you post RESULTS.txt

---

### Post by cerpin-taxt on 2011-08-12
please help me,my grub customizer dont work .it load but,close when charging sytem tree

---

### Post by drs305 on 2011-08-12
> **cerpin-taxt said:**
> please help me,my grub customizer dont work .it load but,close when charging sytem tree

What error messages, if any, do you get when you try opening it from the command line with:
```
gksu grub-customizer
```
Note: there will be various commands issued in the terminal as the command is executed - look for any that generate error messages.

---

### Post by venkivoice on 2011-09-02
Hi,

I need a help in grub legacy, below is my requirement.

a).Check for a file in windows partition
   a.1) if the file is there boot into linux "else" boot into windows. 

I dont know how to do this, If you have any idea to this without booting into linux and check for the file and then boot in to windows.

Please guide me, it would be a great help.

Thanks & Regards,
Venkat

---

### Post by evets on 2011-09-04
Belated thanks for the info and the tutorial.

---

### Post by drs305 on 2011-09-04
> **venkivoice said:**
> Hi,

I need a help in grub legacy, below is my requirement.

a).Check for a file in windows partition
   a.1) if the file is there boot into linux "else" boot into windows. 

I dont know how to do this, If you have any idea to this without booting into linux and check for the file and then boot in to windows.

Please guide me, it would be a great help.

Thanks & Regards,
Venkat

I am not sure how to do this, but creating a new thread with your request will probably give you the best chance of getting an answer on these forums. I'd include 'Grub Legacy' in the title since the number of users who remember how Grub operates is slowly decreasing.

---

### Post by JKyleOKC on 2011-09-05
> **venkivoice said:**
> Hi,

I need a help in grub legacy, below is my requirement.

a).Check for a file in windows partition
   a.1) if the file is there boot into linux "else" boot into windows. 

I dont know how to do this, If you have any idea to this without booting into linux and check for the file and then boot in to windows.I'm afraid that what you want simply isn't possible with current software. The boot loader, which is what grub is, has very limited capability and that does not include the ability to search additional partitions for files. It merely looks for a specific file on a specified partition, loads that file, and transfers to it to continue the boot process.

To achieve your goal, you would have to rewrite grub itself to add the capability of specifying a second partition and filename, then making the decision of which menu entry to process depending on the outcome of a search.

The whole idea of the free software movement and GPL is to permit you to do just that -- but you need to have the programming capability to do it. That means knowing the C language quite well, and having the necessary tools installed on your system. The grub source code is available, of course, and you're welcome to tackle the task if you like -- but remember that if you do, you will be pretty much on your own so far as detailed help goes, since the grub development team has moved well beyond grub legacy and is working on totally different problems now!

---

### Post by killabee44 on 2011-09-13
Guys,

I installed the Grub Customizer and am getting the following error: "no bootloader found"

Then it gives you an option to select another root partition. 

Has anyone else run into this issue? Thanks.

---

### Post by danielrichter on 2011-09-14
@killabee44:
Grub Customizer does the following checks to find out if Grub2 is installed:
command grub-mkconfig exists
command update-grub exists
command grub-install exists
command "which" to do all the command checks
directory /etc/grub.d exists

make sure this is the case on your system.

---

### Post by danielrichter on 2011-09-14
Hi @all:

I've just released version 2.2 of Grub Customizer which fixes the Grub 1.99 problem (submenu support). Submenus are viewed hierarchical but you can move it's to any location inside its script.

I removed the "copy to grub directory" button now as it shouldn't be clicked when using grub 1.99+ and also isn't required when using older grub revisions in most cases.

---

### Post by drs305 on 2011-09-14
> **danielrichter said:**
> Hi @all:

I've just released version 2.2 of Grub Customizer which fixes the Grub 1.99 problem (submenu support). Submenus are viewed hierarchical but you can move it's to any location inside its script.

I removed the "copy to grub directory" button now as it shouldn't be clicked when using grub 1.99+ and also isn't required when using older grub revisions in most cases.

Thanks Daniel. I've updated the first post to reflect the availability of 2.2 and it's integration with Grub 2's submenus.

---

### Post by Kevrev on 2011-09-19
Hi all,
  Thanks for what appears to be a fantastic Grub too DRS305 ! . 
I am in the process of building a dual boot system with a SATA6 128 GB SDD(Win 7 64) and I intend to move my Win 7 data/user directories to a Sata3 320GB hard drive. On my third Sata3 drive I would like to install Ubuntu Studio 64.
  My question is, will installing Ubuntu last preserve my Windows drives and work with the Grub 2 bootloader? Also I would prefer for Grub to allow Win 7 64 to boot automatically instead of default Ubuntu.
Thanks
Kevin

---

### Post by drs305 on 2011-09-19
> **Kevrev said:**
> My question is, will installing Ubuntu last preserve my Windows drives and work with the Grub 2 bootloader? Also I would prefer for Grub to allow Win 7 64 to boot automatically instead of default Ubuntu.

If installed correctly, Ubuntu should not touch the Windows partition. Make sure when asked where to install Grub 2 that you select the *drive* and not the partition. 

Since you will have Ubuntu on a separate drive, to further ensure you have no problems, I would recommend disconnecting the Windows drive before installing, and changing the BIOS to boot the Ubuntu drive first.

By doing this, you will ensure you do not mistakenly install Ubuntu over the Windows installation. Secondly, it will leave the MBR on your Windows drive intact. This can be helpful if Grub fails, since changing the BIOS boot priority back to the Windows drive will restore Windows even if Grub 2 is still broken.

Once Ubuntu is fully installed, reconnect the Windows drive and run "sudo update-grub" so Grub 2 will add Windows to your Grub menu on boot. At that time, you can make Windows the default OS either by using Grub Customizer to making the change or manually using the procedure in the "Tasks" link in my signature line.

Note: If you already have an Ubuntu installation and don't need another Grub 2, there is an option not to install Grub 2 in the partitioning section of the installation.

---

### Post by huggs on 2011-10-08
I did a thread search for WUBI, and found the cause of why I cannot display a background image in GRUB on a WUBI install.

According to drs305, there are modules necessary for rendering an image, which are not included with WUBI installed GRUB, and some other file editing would also be necessary.

I have asked about this subject in the WUBI megathread before, but it seems that the knowledgeable folks over there don't know which modules it is that are missing.

Could I please get the names of these missing modules, and I suppose a point in the right direction as to what other files would need to be edited? I will take this info over to the WUBI thread and see if it can be sorted out, and maybe a little tut made, maybe the modules could be included in future releases of WUBI?

The black background is so out of place on my mostly blue set-up, I need to rid myself of that and the ugly purple screen too

:PTIA:P

---

### Post by drs305 on 2011-10-08
huggs,

I don't currently have access to a wubi grub.cfg on my system. Here are at least some of the modules loaded by my normal grub.cfg file:
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
  insmod gfxterm
plus any graphic used (png, tga and/or jpg)

I don't think this list is all inclusive and necessarily of any use. I would expect that it is much more complicated. 

Normally I would recommend going to the #grub IRC channel and ask the devs directly, but I don't know how many of them are conversant on Wubi issues. You could also ask in the grub mailing list, which might get a wider audience: 
[http://www.gnu.org/software/grub/grub-mailinglist.en.html]("http://www.gnu.org/software/grub/grub-mailinglist.en.html")

---

### Post by crjackson on 2011-10-09
Nice tool, I used it to remove memtest and to change the resolution. Now I don't get the animated ubuntu screen with the moving dots when booting. I changed the resolution back but still the same. Just a big purple screen.

How do I get my ubuntu loading screen back?

---

### Post by drs305 on 2011-10-09
> **crjackson said:**
> Now I don't get the animated ubuntu screen with the moving dots when booting. I changed the resolution back but still the same. Just a big purple screen.

How do I get my ubuntu loading screen back?

I'd like to be able to tell you how to do it in GC, but I'm still mostly a terminal guy when it comes to making the changes. I haven't spent a lot of time trying to learn how to 'undo' things in GC. 

I don't know what changes were made to your files, but if you use Step 7 in the original post you should be able to restore the original files/settings.

You can then use the following commands to remove the memtest entries.
```
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub
```

I'm not sure why the video acted the way it did, but perhaps the creator will respond.

---

### Post by crjackson on 2011-10-09
> **drs305 said:**
> I'd like to be able to tell you how to do it in GC, but I'm still mostly a terminal guy when it comes to making the changes. I haven't spent a lot of time trying to learn how to 'undo' things in GC. 

I don't know what changes were made to your files, but if you use Step 7 in the original post you should be able to restore the original files/settings.

You can then use the following commands to remove the memtest entries.
```
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub
```

I'm not sure why the video acted the way it did, but perhaps the creator will respond.

Thanks, I usually use the terminal as well, but decided to give this app a shot. I don't want the memtest86 entries back, I just want to fix my loading screen. I've run accross this before when changing grub resolution but it's been so darned long ago I can't remember how I fixed it and I'm having no luck locating the information.

Thanks for you reply.

---

### Post by drs305 on 2011-10-09
> **crjackson said:**
> Thanks, I usually use the terminal as well, but decided to give this app a shot. I don't want the memtest86 entries back, I just want to fix my loading screen. I've run accross this before when changing grub resolution but it's been so darned long ago I can't remember how I fixed it and I'm having no luck locating the information.

Thanks for you reply.

If you return the original files I would suspect it will correct things. If that doesn't work, I'd check the /etc/default/grub file to see if you now have "GRUB_GFXMODE=" enabled with a value. Normally it is 640x480 but there is a comment at the beginning so it's not used. Of course, if you change it make sure you run update-grub.

---

### Post by crjackson on 2011-10-10
> **drs305 said:**
> If you return the original files I would suspect it will correct things. If that doesn't work, I'd check the /etc/default/grub file to see if you now have "GRUB_GFXMODE=" enabled with a value. Normally it is 640x480 but there is a comment at the beginning so it's not used. Of course, if you change it make sure you run update-grub.

I'll check to see about the GFXMODE and comment it out. The other files were returned but still no joy.

---

### Post by crjackson on 2011-10-11
Problem solved...

```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
```

```
sudo update-initramfs -u -k `uname -r`
```

```
sudo update-grub2
```

reboot

---

### Post by drs305 on 2011-10-11
> **crjackson said:**
> Problem solved...


Had you previously added the FRAMEBUFFER line to your system? 
Did GC remove it?
How did you determine this was the issue.

Thanks.

---

### Post by crjackson on 2011-10-11
> **drs305 said:**
> Had you previously added the FRAMEBUFFER line to your system? 
Did GC remove it?
How did you determine this was the issue.

Thanks.

No, it wasn't there before, but it was part of the fix. I have no idea why, I just remember that I had a similar problem after installing 10.04, so I just applied the same fix and it worked.

---

### Post by The Sorrow on 2011-10-12
Great information here. Learned a lot of good stuff.

---

### Post by gtman on 2011-11-03
thank you for this kind of grub customizer...
this is helpfully...

---

### Post by mfox on 2011-12-04
> **woodyg said:**
> I also have a problem with grub customizer... **since installing 11.10.** I have installed three linux OS, so I had a whole bunch of booting options, some of which I wanted to remove and some of which I just wanted to tidy up (e.g. Ubuntu 11.10 rather than linux-image-2.6.32-21-generic or whatever they may be called).

I used grub customizer to do this, some were removed (unticked) and some were re-labeled. I saved it, rebooted... and no change at all. I have done this several times, and it never works, so is it not working with 11.10 or do I have to do something else as well in order to make the changes take place? :confused:

I have a similar problem, but it relates specifically to Mint 12, which I installed a few days ago.  I now have Ubuntu 11.10 as my main OS (grub running from it), but also on my disk I have Windows 7, Bodhi and now Mint 12.  I had some difficulty installing Mint, and I had to wipe its partition and re-install it several times.  After the aborted installs, I used the Mint installer to reinstate my grub2 and then booted into Ubuntu, reinstalled grub2 and ran the update.  The resulting grub menu had Mint 12 listed 4 or 5 times, all identically (i.e. without the usual options like memtest).  I then went into grub-customizer and found the multiple instances of Mint, unchecked all but the first and saved, but there was no change on the grub menu and now even more listings of Mint in the grub-customizer window.  Short of changing the OS from which grub2 is running, I am at a loss as to how to fix this problem.  I'm thinking that the problem is in a configuration file, but can anyone  suggest where to look or how to remedy this?

---

### Post by mfox on 2011-12-04
[COLOR="DarkRed"]Moderator Note: Post moved. Please do not post in multiple threads.[/COLOR]

I have a problem with multiple duplicate listings on my grub menu, and I mean duplicate (not different kernels or boot options). Grub is running from Ubuntu, and the other OSes on my disk are Windows 7, Bodhi and the most recent, Mint 12. I had some difficulty installing Mint, and I had to wipe its partition and re-install it several times. After the aborted installs, I used the Mint installer to reinstate my grub2 and then booted into Ubuntu, reinstalled grub2 and ran the update. The resulting grub menu had Mint 12 listed 4 or 5 times, all identically as previously noted. There were multiple instances of Mint listed in the grub-customizer window, so I unchecked all but the first and saved, but there was no change on the grub menu and now even more listings of Mint in the grub-customizer window. How can I fix this?

---

### Post by drs305 on 2011-12-04
> **mfox said:**
> ... so I unchecked all but the first and saved, but there was no change on the grub menu and now even more listings of Mint in the grub-customizer window. How can I fix this?

Grub 2 imports some of the other OS's menus directly rather than searching their partitions, so I would try running Mint and performing an "update-grub". You could also run the following command after updating to see how many menu items then exist in your Mint OS:
```
grep menuentry /boot/grub/grub.cfg
```
If you are still getting duplicate entries it's the Mint OS that is the problem and not your Ubuntu.

Also note which OS is controlling your boot. Look at the top item in the Grub menu as the system boots. Press 'e' to investigate the entry if it isn't obvious which OS it is.

If you still can't resolve it, run the boot info script and post the contents of RESULTS.txt and we can take a look.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by mfox on 2011-12-04
That got it; thanks drs305. I had to run update-grub from Mint first.  I then restarted and the multiple entries were there, but after running update-grub from Ubuntu, that cleared it up.  It not only cleared it up, it also added the recovery option for Mint.  So you must have been right about Mint having those extra entries there and then Ubuntu importing those entries.  Thanks again!

---

### Post by I2k4 on 2011-12-15
I recently installed Lubuntu 10.10 on an HDD partition, with most of the drive holding  Windows 7.  Before using the Grub Customizer I was getting a six item boot list in this order:

. Ubuntu ... Generic
. Ubuntu ... Recovery Mode
. Memtest 86+
. Memtest 86+ serial console
. Vista (there is no Vista installed)
. Windows 7

When I installed Grub Customizer I did not actually see any entries for either the "Vista" or for the actual Windows 7 choices.  From the instructions here I got the idea that they were included in OS-PROBER somehow.  I thought I could try one simple thing before deciding what to keep from that boot list.

Reading section 4 of the first post here, _I tried to move Windows to the top of the boot order_:

"To move a main section, highlight the entry and use the Up/Dn arrows on the main menu to change the menu order. Moving a main category will move all its submenus.  
. Example: _If you want Windows to appear before the main Ubuntu entries, move os-prober to the top of the list_."

So I moved OS-PROBER up to the top, and saved that and rebooted.  Low and behold _only the first four Ubuntu and Memtest choices appear on the boot list._  I then loaded Lubuntu, opened Grub Customizer again and moved OS-PROBER back down to where it was before, but on restart the list still only includes the Ubuntu and Memtest entries, and both the "Vista" and Windows 7 choices are gone.  

I can't figure out how to boot into Windows 7 from GRUB or any other way now.  _I'm at a complete loss for what to do to either get back to the original configuration, or to add Windows 7 as an entry, and I'm cut off from Windows 7._  Windows applications I need on the netbook are no longer accessible.  Although I can access the Windows partition through Lubuntu and retrieve files, some important files need Windows software.  

I'd appreciate assistance with either:
1) restoring the original GRUB configuration, or
2) adding Windows 7 into the boot order again, possibly as a New Entry.  

Thanks.

---

### Post by drs305 on 2011-12-15
I2k4,

I'd recommend installing and running the Boot Repair tool. It will probably be able to restore your menu in relatively easy fashion. If you are booting into Ubuntu, just install it. If you aren't able to boot into your normal Ubuntu, you can install it in the LiveCD (for that session only to recreate the menu).

It sounds like you have messed up your grub.cfg file but the rest of the files should be intact and you just have to recreate the Grub menu.

There are other ways to do this, but Boot Repair is probably the easiest and most fool-proof. Click the "Boot Repair" link in my signature line for information.

---

### Post by I2k4 on 2011-12-15
Thanks for the quick response - I can boot into Lubuntu and it appears from the file manager that everything in the Windows partition is fine - so it does seem that I somehow fouled up Grub configuration.  I'm very hopeful it can simply be restored and I'll try the Boot Repair tool.  

I won't be able to settle in for a fix it session until tomorrow but will get back on the result.

Best, I2k4

---

### Post by drs305 on 2011-12-15
> **I2k4 said:**
> Thanks for the quick response - I can boot into Lubuntu and it appears from the file manager that everything in the Windows partition is fine - so it does seem that I somehow fouled up Grub configuration.  I'm very hopeful it can simply be restored and I'll try the Boot Repair tool.  

I won't be able to settle in for a fix it session until tomorrow but will get back on the result.

Best, I2k4

If you can boot normally into your Lubuntu and you didn't move or alter the files in the /etc/grub.d folder, you should be able to get Windows back into the grub.cfg file (the Grub menu) by simply running:
```
sudo update-grub
```
As it runs, just watch the terminal and see if you see a reference to Windows. If you do, it most likely added it to the menu. You can also check the existing entries after the update and before booting with:
```
grep menuentry /boot/grub/grub.cfg
```

---

### Post by I2k4 on 2011-12-16
Thanks for the terminal commands - as they looked quick and easy I tried them - I got this result from "update":

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

And this from menuentry:

menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {

_On reboot after this, I only got the same four choices, without Windows._  

I looked into the etc/grub.d folder, not knowing exactly what to expect, and found entries that look like above along with "OS-PROBER" but no specific entry for Windows.

I'm planning to try the Boot Repair as suggested above, later today or on the weekend.  I looked at it quickly, and _there seems to be a one-click try.  I'll do that and report back._  

Apart from that there seemed to be some dialog boxes - if there is any further advice on using Boot Repair or otherwise, in this situation of disappeared Windows, I'd be very glad of it.

Thanks again.

---

### Post by drs305 on 2011-12-16
Grub is not finding Windows when you update grub. There are several reasons this can happen:
1. Critical Windows boot files are missing. Probably not likely in your case.
2. 30_os-prober isn't being run either because the os-prober command isn't available or the script isn't running.

To make sure the script exists and is executable:
```
sudo chmod +x /etc/grub.d/30_os-prober
```
To check that os-prober exists:
```
which os-prober
```

If this still doesn't fix things, run Boot Repair. If it still doesn't work, post the contents of the boot info script, which you can run from within the Boot Repair app.

---

### Post by I2k4 on 2011-12-18
Many thanks for your help here - I got no response from the OS-PROBER commands, but _the Boot Repair tool worked a charm_.  The GRUB boot priority list again includes Windows 7 and it's booting normally.

Since I don't know what went wrong, I can't say if/when I'll try the GRUB Customizer app again, but I'll save this thread forever.

Best wishes for the holidays.

---

### Post by nattyiac on 2011-12-19
*Mod Note: Removed the quoting of the thread's original post in it's entirety.*

I can't get mine to work. When I try to open it says it can't find a bootloader and asks me if I want to choose a partition.
What should I do to solve this?

---

### Post by drs305 on 2011-12-20
> **nattyiac said:**
> *Mod Note: Removed the quoting of the thread's original post in it's entirety.*

I can't get mine to work. When I try to open it says it can't find a bootloader and asks me if I want to choose a partition.
What should I do to solve this?

I'd recommend downloading and running the Boot Repair tool. It can solve a large number of Grub problems. Check out the thread via the "Boot Repair" link in my signature line.

If it doesn't fix it, the app will let you run the boot info script and you can post the RESULTS.txt content if you still need help.

---

### Post by 2CV67 on 2011-12-22
Thanks so much for this HOWTO & even more thanks to Daniel Richter for the vitally-needed app!

I am about to enter the world of Grub2 (trepidations...) & have heard remarks (probably out of date) that Grub Customizer is not yet ready for 1.99.

I know GC 2.2 is out there & is intended for 1.99.

Could you possibly give us a brief status report on that?
As of today, what can GC 2.2 do with 1.99 & are there still shady areas, apart from the images/fonts stuff you helpfully edit in the first post?

Thanks again!

---

### Post by gregzeng on 2011-12-22
> **2CV67 said:**
> Thanks so much for this HOWTO & even more thanks to Daniel Richter for the vitally-needed app!

I am about to enter the world of Grub2 (trepidations...) & have heard remarks (probably out of date) that Grub Customizer is not yet ready for 1.99.

I know GC 2.2 is out there & is intended for 1.99.

Could you possibly give us a brief status report on that?
As of today, what can GC 2.2 do with 1.99 & are there still shady areas, apart from the images/fonts stuff you helpfully edit in the first post?
Thanks again!

Grub Customizer 2.4.1

Just downloaded it now.  
Uncertain what are the changes.  It cannot delete crazy, non-existent 'lines',  so it's still a work in progress.    

Very surprised ... so many Linux 'gurus' * coders around, and this essential fix is still not fixed.  Tried to be more constructive in joining the *buntu community, ... journalistic, writing, documentation skills, .... but after an hour, gave up.  
 
I'm in the 1% of IQ ("unsuitable for Mensa"; Australian Mensa told me, when I explained they have no social responsibilities nor ethics, especially to non-whites like myself.  Seems the Linux obsessives like being 1 per centers as well, to prove that they are not the Ninety-Nine per-centers, in the world's social responsibilities.

So ... back to winning my Nobel Peace Prize for anti-military accomplishments.

---

### Post by bogan on 2011-12-31
[SIZE=2]Hi!, [/SIZE][SIZE=2]**drs305**,
Like others, I add my thanks to danielrichter, and to you; without your detailed help files, I would never have dared to try Grub Customizer, despite having a grub menu with more than 20 confusing entries.

In setting up a new clean install of Ubuntu 11.10, I stumbled on your HowTo:GC. After reading all the posts in that Thread, and again from 1 to 118, I was so impressed that I swallowed my aversion to editing files that start: "Do Not Edit This File."

I installed GC as per your instructions:```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
sudo update-grub 
```[/SIZE][SIZE=2]and ran it from a Root Terminal.Edit: and re-ran[/SIZE][SIZE=2] update-grub [/SIZE][SIZE=2]:[/SIZE]> [SIZE=2]grub-customizer
[/SIZE][SIZE=2] update-grub [/SIZE][SIZE=2] [COLOR=Magenta]Edit2: I did not use "gksu", maybe that caused the errors ??[/COLOR] 
 It ran OK, except for a sea of error messages. { See attachment }. 
My grub menu was edited as I wanted; but no colour change, and no Background image.
 Furthermore, the Debian background Image I had had during boot-up, after the grub menu, since I installed Gnome3, had gone.

I am an Octogenarian Ignoramus and there are some simple things I find difficult to fathom out; please bare with me if they seem obvious to you.

First: how do I "get" your attached image file and "drop" it into /boot/grub/. When I tried with another jpeg it refused to drop.* [** Edit**: I found an answer to the second part of that with 'gksu nautilus /pathname/'. See below.]*

Second: I cannot find any menu item, in Gimp Image Editor, that would change a .jpeg to a .png format, as you describe, nor in Nip2.

Eventually, I found your link in P#103 to "Re: Grub 2 Drop-In Backgrounds & Font Selection"; downloaded the splashimages and used```
 gksu nautilus /imagepathname/
```[/SIZE][SIZE=2] to "drop" it into /boot/grub/.

 That gave an image but the unchanged text colour is illegible against it.

The first image I tried in GC was one with a space in its name and my /boot/grub/grub.cfg then showed:> if background_image /boot/grub/.backgound_cache;[/SIZE][SIZE=2] But no image showed.

Currently my /boot/grub/grub.cfg shows:
```
### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd1,msdos8)'
search --no-floppy --fs-uuid --set=root 2a453a5a-fe73-417b-a61f-8450cf25914b
insmod tga
if background_image /boot/grub/Windbuchencom.tga; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###
```[/SIZE][SIZE=2] "[/SIZE][SIZE=2]Windbuchencom.tga" being the image file I dropped. but[/SIZE][SIZE=2] this did not alter after changing the colours first, and then both image & colours with GC.

Third: I think I remember your Posting that some  lines need to be added to that code, to get the GC colour changes to work; would you please re-post them?.

Fourth 'simple' question: Although I am certain I have grub2 installed since 10.10, the grub menu title still shows:>  GNU Grub version 1.99-12 Ubuntu5[/SIZE][SIZE=2] is that relevant, or important??

Your assistance appreciatively awaited,. Chao!, **bogan**.[/SIZE]

---

### Post by drs305 on 2011-12-31
> **bogan said:**
> Hi!, **drs305**,
Like others, I add my thanks to danielrichter, and to you; without your detailed help files, I would never have dared to try Grub Customizer, despite having a grub menu with more than 20 confusing entries.

Well, I'll get the easy ones first. Grub 2 is officially Grub 1.96 or later - the latest is Grub 1.99. Even Grub legacy, which was around a long time, never got past 0.97. Go figure...

Also, in the attached file I saw a 'pixmaps' error message. You may be able to fix that with this command, which will install a package that might allow the system to use it on the latest version of Ubuntu:
```
sudo apt-get install gtk2-engines-pixbuf
```


> 
First: how do I "get" your attached image file and "drop" it into /boot/grub/. When I tried with another jpeg it refused to drop.[I] [** Edit**: I found an answer to the second part of that with 'gksu nautilus /pathname/'.
Not sure if you still need help with this, but if so one way to move the image into /boot/grub is via a terminal. If the image is on your Desktop, the command would be 
```
sudo cp ~/Desktop/*image-name* /boot/grub/
```
Using nautilus as root would be better, since you can inspect the /boot/grub contents. If the image file isn't specifically designated in /etc/default/grub the bootloader will use the first image file it finds in /boot/grub (which may not be the one you want).

> 
Second: I cannot find any menu item, in Gimp Image Editor, that would change a .jpeg to a .png format, as you describe, nor in Nip2.
It's so simple it's not obvious. In GIMP, open your file and when you are ready to save it as a png image, just select File, Save As and change the extension from .jpg to .png.  When you save it, GIMP may ask you some questions or say it has to modify some of the file characteristics, but it will walk you through any conversion decisions you have to make before it saves the file as a PNG image.

Font colors/background images aren't the easiest things to work with in Grub 2. I'm going to reread the font color part of your post, try to make sure I understand your current problem, experiment in a VM with the Windbuchencom.tga image, and will reply to that part in a separate post.

In the meantime, forum member *towheedm* is our current forum guru on theming and has written an excellent, detailed guide on Grub 2 theming. 
[http://ubuntuforums.org/showthread.php?t=1534689]("http://ubuntuforums.org/showthread.php?t=1534689")

---

### Post by bogan on 2011-12-31
[SIZE=2]Hi!, **drs305**,  Thanks for your very full and prompt reply.
I have just tried out your explanation, about Gimp saving in ,png format[/SIZE], and it worked exactly as you said.
 When I tried before, I was put off by the format button only offering: " All supported formats" and no choices..

That I did on my other computer, my Vista m/c, with Ubuntu11.10, 3.0.0-14 installed via Update Manager: it is subtly different from the one on my Win7 m/c.

Having learned from the problems on the latter, I installed and ran GC, without first dropping an image into /boot/grub  - that seemed such an easy way!!.
It worked first time, with only a couple of Hal errors. 
A single further run, to change to a darker shade of red, and it is AOK.

Which just leaves the remaining problem with the Win7 m/c, of getting the text colours altered for readability.
It would be a pity if I had to take GC out to start over again.

 I have not had time yet to try the "pixmap" patch.


Chao!, **bogan.**

---

### Post by drs305 on 2011-12-31
I just loaded up Grub 1.99 and played with the Windb... file.

I think the code you asked me to find was for the /etc/grub.d/05_debian_theme file at line 98:

Add lines 2 & 3, using the colors you desire.
>         echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
[COLOR="Red"]        echo " set color_normal=red/black"
        echo " set color_highlight=blue/black"
[/COLOR]        if [ -n "${2}" ]; then
   
Save the file, then update Grub.

I've taken this from the "Editing Font Colors" from my thread:
[Grub 2 Drop-In Backgrounds & Font Selection]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by bogan on 2011-12-31
Hi!, **drs305**, Thanks for your Post D >> P#192,

I just entered the pixbuf code in my Vista m/c and it was already installed:> root@alan-MS-7318:~# apt-get install gtk2-engines-pixbuf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**gtk2-engines-pixbuf is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@alan-MS-7318:~# which explains the fewer errors I got.

I also entered the two colour lines in /etc/grub.d/05_debian_theme file, before I remembered I needed it in the other m/c, not this one. I have'nt rebooted yet, I am Posting this first; If there is a conflict I will return and edit this.

I worked out how to "get" the a.png file; like you said: obvious really - when you know how - Double-clicked it, and used Firefox 'Save As:' to save it as a page to Desktop, or wherever.

Fingers crossed,   Chao!, **bogan**.

---

### Post by bogan on 2011-12-31
Hi! **drs305**,
There was no conflict in the display on my Vista m/c, so I have made this separate.
On MY Win7 m/c, I ran:
```
sudo apt-get install gtk2-engines-pixbuf
```and it installed OK. 
Clearly it was not included in the .iso file I used, and Update Manager did not note its absence.

Afterwards, running GC with gksu, still gave 'dbus' and 'Hal' errors, but the first few were no longer there.

Editing the /etc/grub.d/05_debian_theme file, to read:```
echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
       [COLOR=DarkGreen] echo " set color_normal=blue/black"
        echo " set color_highlight=red/black"[/COLOR]
        if [ -n "${2}" ]; then
``` gave the best contrast and readability, in balance for all the Menu images I tried out.

I then found that there were four lines added to the /etc/default/grub file that were relics of a previous setting; bearing no relation to either what was displayed, nor to what I had last set in GC. 

I assume because I had disrupted GC workings by dropping the image file in /boot/grub/.

However, running GC again and removing the image all together, then saving and re-running GC; entering the same appearance settings and image path and name as the other entries, put things right,and now they are all in agreement.
 Those lines are now:>  export GRUB_COLOR_NORMAL="blue/black"
export GRUB_COLOR_HIGHLIGHT="red/black"
export GRUB_MENU_PICTURE="/usr/share/images/grub/Windbuchencom.tga"
GRUB_SAVEDEFAULT="false" So I reckon that, for me at least, you can count that as: "**SOLVED"**!!

Chao! ,**bogan**.:-({|=

---

### Post by drs305 on 2011-12-31
bogan,

Glad it all worked out.

Just a note for others following this thread. I believe the "export" commands entered into /etc/default/grub are specific to the way Grub Customizer works. 

I've rechecked the grub_mkconfig file and it doesn't show those as exportable options. That is why I used manually editing the 05_debian... file. 

Being able to designate/export the colors directly from /etc/default/grub is yet another reason to use GC!

---

### Post by cudayne on 2012-01-03
i searched but i cant find any info on this problem. I installed the grub customizer all went well until l i tried too use it.

It asks for password but it never will accept it. If i try accessing the program through the terminal it just asks for password over an over. If i try it in the desktop i type the password an nothing happens. 

Has anyone else encounterd this problem?

system has kubuntu 64 bit an windows 8 on sda an Linux mint12 installed on sdb. 

I was hoping when i installed mint it would update the boot loader but it didn't so i need too update manually an saw this program an figured it would help me do the trick fast an hopefully easy way.

---

### Post by drs305 on 2012-01-03
> **cudayne said:**
> i searched but i cant find any info on this problem. I installed the grub customizer all went well until l i tried too use it.

It asks for password but it never will accept it. If i try accessing the program through the terminal it just asks for password over an over. If i try it in the desktop i type the password an nothing happens. 

Has anyone else encounterd this problem?

system has kubuntu 64 bit an windows 8 on sda an Linux mint12 installed on sdb. 

I was hoping when i installed mint it would update the boot loader but it didn't so i need too update manually an saw this program an figured it would help me do the trick fast an hopefully easy way.

Are you able to access other GUI applications which require the password?

---

### Post by Thad E Ginathom on 2012-01-13
Grub Customizer 2.5.1 Crashes after loading configuration.
> grub-customizer: /home/nick/src/grub-cust-2.5.0/src/model/grublistCfg.cpp:447: bool GrublistCfg::compare(const GrublistCfg&) const: Assertion `piter->dataSource != __null' failed.Ubuntu 11.04 + KXStudio, 2.6.38-8-lowlatency.

The full output: ```
$  gksu grub-customizer
 *** initializing (w/o specified bootloader type)&#8230;
   * reading partition info&#8230;
   * Loading Framebuffer resolutions (background process)
   * Finding out if this is a live CD
     [running on an installed system]
     [checking the burg-mkconfig command&#8230; ]
     [not found]
     [checking the grub-mkconfig command&#8230; ]
     [found at: /usr/sbin/grub-mkconfig]
     [checking the update-grub command&#8230; ]
     [found at: /usr/sbin/update-grub]
     [checking the grub-install command&#8230; ]
     [found at: /usr/sbin/grub-install]
 *** initializing (w/ specified bootloader type)&#8230;
     [checking the grub-mkconfig command&#8230; ]
     [found at: /usr/sbin/grub-mkconfig]
     [checking the update-grub command&#8230; ]
     [found at: /usr/sbin/update-grub]
     [checking the grub-install command&#8230; ]
     [found at: /usr/sbin/grub-install]
   * Checking if the config directory is clean
 *** loading configuration
 *** loading - preserveConfig: no
   * unsetting saved config
 *** loading settings
 *** loading grub list
   * loading scripts&#8230;
   * loading proxies&#8230;
   * creating proxifiedScript links & chmodding other files&#8230;
   * running grub-mkconfig
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [mkconfig successfull completed]
   * restoring grub configuration
   * loading completed
 *** grub list completely loaded
 *** loading saved grub list
grub-customizer: /home/nick/src/grub-cust-2.5.0/src/model/grublistCfg.cpp:447: bool GrublistCfg::compare(const GrublistCfg&) const: Assertion `piter->dataSource != __null' failed.

```/boot/grub/grub.cfg:
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos8)'
search --no-floppy --fs-uuid --set=root 0bf81110-5908-40aa-978b-1e11a374d2fd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos8)'
search --no-floppy --fs-uuid --set=root 0bf81110-5908-40aa-978b-1e11a374d2fd
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,0,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_linux_proxy ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry "Ubuntu 11.04/KX, with Linux 2.6.38-8-lowlatency NEW" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos8)'
    search --no-floppy --fs-uuid --set=root 0bf81110-5908-40aa-978b-1e11a374d2fd
    linux    /boot/vmlinuz-2.6.38-8-lowlatency root=UUID=0bf81110-5908-40aa-978b-1e11a374d2fd ro   quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-lowlatency
}
menuentry "Ubuntu 11.04/KX, with Linux 2.6.38-8-lowlatency (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos8)'
    search --no-floppy --fs-uuid --set=root 0bf81110-5908-40aa-978b-1e11a374d2fd
    echo    'Loading Linux 2.6.38-8-lowlatency ...'
    linux    /boot/vmlinuz-2.6.38-8-lowlatency root=UUID=0bf81110-5908-40aa-978b-1e11a374d2fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-lowlatency
}
menuentry "Ubuntu, with Linux 2.6.38-13-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos8)'
    search --no-floppy --fs-uuid --set=root 0bf81110-5908-40aa-978b-1e11a374d2fd
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=0bf81110-5908-40aa-978b-1e11a374d2fd ro   quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-13-generic
}
menuentry "Ubuntu, with Linux 2.6.38-13-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos8)'
    search --no-floppy --fs-uuid --set=root 0bf81110-5908-40aa-978b-1e11a374d2fd
    echo    'Loading Linux 2.6.38-13-generic ...'
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=0bf81110-5908-40aa-978b-1e11a374d2fd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-13-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-34-generic (on /dev/sda2) OLD" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root e163c9bc-a031-40fb-a342-017a55cbc3c8
    linux /boot/vmlinuz-2.6.32-34-generic root=UUID=e163c9bc-a031-40fb-a342-017a55cbc3c8 ro quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
    initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, with Linux 2.6.32-34-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root e163c9bc-a031-40fb-a342-017a55cbc3c8
    linux /boot/vmlinuz-2.6.32-34-generic root=UUID=e163c9bc-a031-40fb-a342-017a55cbc3c8 ro single
    initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 843828DD3828CFCA
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```It has been working just fine for me since for-ever, but I can't remember when I last used it, so I don't know what version last worked with this system. Was about to move some stuff around, and it is a vital tool! Probably my favourite.

---

### Post by drs305 on 2012-01-13
Thad E Ginathom,

This may not help you much but when I try to open GC at the moment it also crashes. I tried via the terminal as well but  I get this message:
> libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
led in file ../../dbus/dbus-errors.c line 280.
I don't know what is wrong with the package and haven't checked to see if there is a newer package, but that is what I'd look at first. I don't know if the creator of the package normally monitors these forums or not.

---

### Post by Thad E Ginathom on 2012-01-14
Hmmm... that looks familiar, I think I saw that somewhere along the line too.

I think that problems have come about with a new version, but I don't know which one. Older versions are not available from the PPA. Obviously it's tedious to step back having to compile at each step, and also, one doesn't know if some offending file may not be removed or changed. I tried one step with the same result.

Anyway, at least it is not just me having problems, and as this software has been well maintained, I can be patient and hope for a resolution. Nothing yet from the PPA

---

### Post by drs305 on 2012-01-14
I've updated to 2.51 (using Ubuntu 11.10, 64 bit)  but still get errors. I've contacted Daniel via Launchpad and hopefully we can provide him with the information he needs to investigate this.

---

### Post by Thad E Ginathom on 2012-01-14
Cheers. 

I did take a look around there, as well as some general googling, but didn't come up with anything yet.

---

### Post by drs305 on 2012-01-14
> **Thad E Ginathom said:**
> Cheers. 

I did take a look around there, as well as some general googling, but didn't come up with anything yet.

I have been in contact with Daniel. He suggested removing the proxy scripts in */etc/grub.d*  This didn't work for me but perhaps it might for you. 

In my case, GC works fine in Oneric 32 bit but something in my 64 bit setup is causing problems which prevents it from opening.

---

### Post by 2CV67 on 2012-01-20
Hello & thanks for all the hard work on this thread!

I installed Grub Customizer this morning & am struggling with a strange problem...

Let me spell out the problem simply first, then add messy background afterwards:

Every time I SAVE Grub Customizer & close & re-open it, it adds a new, ticked, instance of my secondary LTS Ubuntu kernel.
The problem must occur on closing, not re-opening, because if I reboot after closing, then the Grub screen shows the extra LTS already.
See screenshot:

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/GrubCustomizer_002.png[/IMG]

Now for the messy background:
Until recently, I had a main Ubuntu 11.04 installation on sda3 & a backup LTS10.04 Ubuntu on sda5. (Also XP on sda1).
Both Ubuntu's had their own Legacy Grub.
Primary Grub stage2 was on sda3 with a chainloader to LTS.

Then an upgrade of 11.04 to 11.10 failed, so I did a clean install of 11.10 on sda3.
That obviously came with Grub2.
I did nothing special & noted that Grub2 seemed to find 11.10 & LTS & XP OK & many attempts at booting to all of them went OK.

This morning, I installed Grub Customizer & initially used it to hide some unwanted old kernels & memtests etc.
It seemed to work OK but I maybe wasn't watching very carefully.
Then I tried to put the OS prober block at the top & started finding I could not "hit" the default entry on reboot.
I slowly noticed that every time I tried, the Grub screen selected one entry out & that I seemed to have too many LTS entries!

A lot of playing around pinned the problem down to "Save+Close G.C. adds new LTS entry" as mentioned above but from there on I am lost...

Maybe this is related to the fact that there is still Legacy Grub alive & kicking on sda5?

I would very much appreciate any help in diagnosis & cure!

Thanks!

---

### Post by drs305 on 2012-01-20
2CV67,

Are the entries you are concerned with the 3.0.12 kernel entries under the "Previous Linux entries" section? If not, which entries are of concern?

I'll await your response before going into things you may not be interested in...

---

### Post by 2CV67 on 2012-01-20
No - the entries under "Previous Linux versions" are legitimate.

The concern is with the 10 identical entries "Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic (on /dev/sda5)" under "os-prober (custom)".
There is really only one such kernel & the 9 copies have been invented by G.C.

---

### Post by drs305 on 2012-01-20
2CV67,

os-prober may be reading the grub.cfg file from your sda5 partition. If a grub.cfg file exists on another partition, Grub 2 will import the contents of the 10_linux section rather than read the partition contents directly. So if the other grub.cfg file contains multiple instances of the same kernel for some reason, they will be imported 'as is' to your current grub.cfg file.

Depending on what it looks like (if it includes all these entries), you may be able to solve the issue by deleting the sda5 grub.cfg file. 

A more conservative approach would be to edit the sda5 grub.cfg file and remove all the extra entries if they exist. 

Here is a way to inspect and edit your additional grub.cfg file and update your current grub to see if it helps:

```
mount | grep sda5 # Check if sda5 is alread mounted
sudo mount /dev/sda5 /mnt # If not already mounted elsewhere
gksudo gedit /mnt/boot/grub/grub.cfg # Substitute path if already mounted

```
Check the entries under the 10_linux section. Are there multiple listings of the 2.6.32-37 kernel? If so, remove all but one and save the file.

Unmount sda5 and then update grub:
```
sudo umount /mnt
sudo update-grub
```

---

### Post by 2CV67 on 2012-01-20
There is no grub.cfg file in sda5 (LTS).
/boot/grub there contains the usual items for Legacy Grub, like menu.lst etc.

I notice that grub.cfg file in sda3 (11.10) has 2 entries for "Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic (on /dev/sda5)" - not including the "recovery" one.
I suppose that is wrong, but don't know how to fix it.
See attached:
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IE
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=796  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset vga=796
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=796  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset vga=796
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_os-prober_proxy ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 2b1b-1302
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 5998da7e-4123-4481-80f0-99a6f3c5e244
	linux /boot/vmlinuz-2.6.32-37-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro splash
	initrd /boot/initrd.img-2.6.32-37-generic
}
menuentry "Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 5998da7e-4123-4481-80f0-99a6f3c5e244
	linux /boot/vmlinuz-2.6.32-37-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro quiet splash
	initrd /boot/initrd.img-2.6.32-37-generic
}
menuentry "Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 5998da7e-4123-4481-80f0-99a6f3c5e244
	linux /boot/vmlinuz-2.6.32-37-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro single
	initrd /boot/initrd.img-2.6.32-37-generic
}
### END /etc/grub.d/20_os-prober_proxy ###

### BEGIN /etc/grub.d/30_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux16	/boot/memtest86+.bin
}
### END /etc/grub.d/30_memtest86+_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

---

### Post by drs305 on 2012-01-20
> **2CV67 said:**
> There is no grub.cfg file in sda5 (LTS).
/boot/grub there contains the usual items for Legacy Grub, like menu.lst etc.

I notice that grub.cfg file in sda3 (11.10) has 2 entries for "Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic (on /dev/sda5)" - not including the "recovery" one.
I suppose that is wrong, but don't know how to fix it.

If you are no longer using Grub legacy on any OS, delete any menu.lst file you find. Just as G2 imports the contents of grub.cfg files, it will 'mine' menu.lst files it discovers as well.

You would edit the sda3 file the same way as I described in the previous post, mounting sda3 instead of sda5. Other than that, the commands would be the same.

Besides editing these entries, there are two other ways of 'cleaning up' your other grub menus.

The first would be to completely remove any menu.cfg or menu.lst file on your other partitions. The advantage is that G2 would be forced to explore the partition directly rather than rely on (and include) entries in existing menus. The disadvantage is that it would be marginally more difficult to boot into other Ubuntu if G2 breaks in your current system.

Another way to clean your menus up would be to boot into those releases, then run "sudo update-grub" within that OS. It should update the Grub menu for that OS (but won't change the G2 menu of your default OS). Once you have updated grub from within the non-default OS, you can edit /boot/grub/grub.cfg to see if it has multiple entries. If it does contain multiple entries, you could manually remove them (but don't run 'update-grub' from within that OS afterward).

---

### Post by 2CV67 on 2012-01-20
OK - thanks!

I looked in the menu.lst in sda5 & there were 2 entries there for the LTS kernel - one with UUID address & one with root/(hd0,x) address (from a previous exercise with GAG & Grub...).

I removed the redundant entry & Grub Customizer is now functioning correctly - it no longer adds unwanted copies of the LTS entry when saved & closed.

Just to tidy things up - is there any way to remove all the existing unwanted entries in G.C. ?

Again - many thanks!

---

### Post by drs305 on 2012-01-20
> **2CV67 said:**
> 
Just to tidy things up - is there any way to remove all the existing unwanted entries in G.C. ?

Again - many thanks!

That's what GC was designed to do. If you untick any of the entries you don't want displayed GC should do that for you.

---

### Post by 2CV67 on 2012-01-20
It has cleared them out of the grub.cfg file & out of the grub screen OK.

But they still show inside G.C. & I don't see how to clear them out of there.

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/GrubCustomizer_002-1.png[/IMG]

They don't actually exist anywhere, do they - unlike all the other unchecked items, which really exist but I choose not to show?

---

### Post by drs305 on 2012-01-20
Not seeing them in the menu is the important thing and at least that part of the issue is resolved. 

Although I too am curious about it, I'll just have to wait to see if what GC's creator thinks. He checks posts in here from time to time and may be able to shed some more/better light on this.

---

### Post by 2CV67 on 2012-01-20
OK & thanks!

As you say - the important part is working OK now. :D

---

### Post by 2CV67 on 2012-02-07
Can I use Grub Customizer (or anything else) to increase the text size on the Grub Screen?

I expected that changing the resolution would do it, but have tried both extremes (320x200x8  &  1280x1024x24) with no visible difference.

All suggestions gratefully received!

---

### Post by drs305 on 2012-02-08
> **2CV67 said:**
> Can I use Grub Customizer (or anything else) to increase the text size on the Grub Screen?

I expected that changing the resolution would do it, but have tried both extremes (320x200x8  &  1280x1024x24) with no visible difference.

All suggestions gratefully received!

Have you checked which resolutions are supported by Grub on your system?

At the Grub menu press 'c' to get to the grub terminal and type:
```
vbeinfo
```
This will show the resolutions available to Grub. If the ones you tried aren't listed, it would have returned to the default and you would not have seen a change. Select one of the first resolutions listed (bigger fonts) and place that value in the /etc/default/grub file (Or try it with Grub Customizer - I can't check at the moment but I believe it should allow you to select on of the available resolutions).

---

### Post by 2CV67 on 2012-02-09
Thanks very much for your suggestions.

I should have mentioned that I had already been round that loop, but I just did it again to be sure.

vbeinfo gives me a screenful of options of which the top few are invisible but the rest go from 400x300x15 to 1280x1024x32.

In Grub Customizer > Preferences > Appearance, the original value was 1280x1024.
There are 50 choices in GC, ranging from 320x200x8 to 1280x1024x24.
All the options in GC are also in vbeinfo (except the invisible first few).
GC doesn't offer the x32 options from vbeinfo.

From the default 1280x1024 setting in GC, I tried the extreme 320x200x8 but then was not sure it was legitimate, so tried 640x480x8 which is in both GC & vbeinfo.
I did not try any   ...x16 or other.
That is how it is set at the moment.

Looking in /etc/default/grub, I see:  GRUB_GFXMODE="640x480x8"
Anything I select in GC & save, appears OK in ../grub.
But the Grub Screen is unchanged.

So I suppose GC is successfully doing all it can in updating ../grub, but something else is not taking over?

---

### Post by drs305 on 2012-02-09
2CV67,

I don't know why your graphics aren't working properly. 

Here is something you can play with if you have the time. It will try to change the resolution from the grub prompt.

At the Grub menu, type 'c' to get to the grub prompt.
Type the following. 
What it will do is set the new resolution. You have to exit the gfxterm and re-enter to have the resolution changed. You should see the txt size change in the menu.

```

set gfxmode=1024x768
terminal_output console
terminal_output gfxterm
ESC to return to menu, which should reflect the new resolution.
set gfxmode=640x480
terminal_output console
terminal_output gfxterm
ESC to the main menu

```
At least we can see if your system responds.

Also, I don't know if we discussed this earlier, but I am assuming you are running in gfxterm mode by default and haven't removed the **#** from the "GRUB_TERMINAL=console" in /etc/default/grub.

---

### Post by 2CV67 on 2012-02-10
Thank you so much for your patience!

No - I haven't removed the # from the "GRUB_TERMINAL=console" in /etc/default/grub.

```
set gfxmode=640x480
terminal_output console
terminal_output gfxterm
ESC to the main menu
```

gave exactly the result I am looking for.
But only for one time.
Next boot it was back to tiny text again.

Not sure where that leads...

---

### Post by 2CV67 on 2012-02-10
Ah! - I found something.

I also have "Startup Manager" installed.
I tried it before installing GC, but never used it as it did not even allow choosing which kernels to display.

I just looked at it & found 2 resolution settings:
1. Under Boot options > Display > Resolution; I saw 1600x1200.
2. Under Advanced > Bootloader resolution; I saw 1024x768.

I tried playing with 1. & can't see any reaction.
Playing with 2. directly influences the Grub Screen display resolution & setting to 640x480 gives the result I want.

Out of curiosity, I put different values in both (1. = 1280x1024  &  2. = 800x600).
This produced an intermediate sized Grub Screen (800x600) but when I look in /etc/default/grub, I still see 640x480x8.

My conclusion so far:
GC controls /etc/default/grub.
The Grub screen is controlled by Startup Manager, but I don't know how or where.

I suppose I can either use SM to set my Grub Screen or uninstall it & hope that hands back control to GC.

Explanations & recommendations?

Thanks!

---

### Post by drs305 on 2012-02-10
> **2CV67 said:**
> 
I suppose I can either use SM to set my Grub Screen or uninstall it & hope that hands back control to GC.

Explanations & recommendations?

Thanks!

I would uninstall StartUp-Manager. SUM was an excellent tool in it's day, but was written before Grub 2. While portions of it still work, many of the settings do not. Removing it and allowing GC take over its duties will probably provide the best results.

Part of the problem may be that GC alters the script files and uses the modified scripts (storing the originals in a subfolder) while SUM directly edits the originals. They are most likely conflicting and thus causing the problem.

Even if GC initially doesn't provide the correct resolution (which I think it will), it will be easier to sort out once SUM is out of the picture.

---

### Post by 2CV67 on 2012-02-10
Thanks for the guidance!

I "completely removed" SUM with Synapt.

Many subsequent reboots with different GC settings leave me with the intermediate-size Grub screen last set by SUM.
GC continues to rewrite /etc/default/grub as soon as it is saved, but that still has no influence on the grub screen...

---

### Post by drs305 on 2012-02-10
2CV67,

So you have the resolution you want but only because of what you previously set in SUM? 

If you want to post another RESULTS.txt and tell me what resolution you want(ed) I can review it once more to see if I can find anything new.

---

### Post by 2CV67 on 2012-02-10
I now have an acceptable resolution but would prefer it bigger.
Really, I would like to not leave this subject without having control over this parameter, if possible.

Results file:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for csyn.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 127730897 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   114,816,554   114,816,492   c W95 FAT32 (LBA)
/dev/sda2         232,396,290   234,436,544     2,040,255  82 Linux swap / Solaris
/dev/sda3    *    135,301,120   232,394,751    97,093,632  83 Linux
/dev/sda4         114,816,679   135,297,023    20,480,345   5 Extended
/dev/sda5         114,816,681   135,297,023    20,480,343  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2B1B-1302                              vfat       XP                            
/dev/sda2        5a626c9d-6484-489b-9a9a-c215110b5952   swap                                     
/dev/sda3        31c1a1b4-1e0e-4e32-a19d-f5e245b285f2   ext4                                     
/dev/sda4: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x5" PART_ENTRY_NUMBER="4" 
/dev/sda5        d561982c-c893-44dc-b06d-b59aa0e7780c   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP dition familiale" /fastdetect /NoExecute=OptIn

=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IE
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry "Ubuntu, with Linux 3.0.0-15-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=775 splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-15-generic
}
submenu "Previous Linux versions"{
menuentry "Ubuntu, with Linux 3.0.0-14-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=775 splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset vga=775 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro vga=775 splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset vga=775 splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_os-prober_proxy ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 2b1b-1302
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-38-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d561982c-c893-44dc-b06d-b59aa0e7780c
	linux /boot/vmlinuz-2.6.32-38-generic root=UUID=d561982c-c893-44dc-b06d-b59aa0e7780c ro quiet splash
	initrd /boot/initrd.img-2.6.32-38-generic
}
### END /etc/grub.d/20_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=5a626c9d-6484-489b-9a9a-c215110b5952 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  88.8GB: boot/grub/core.img
  83.6GB: boot/grub/grub.cfg
  71.0GB: boot/initrd.img-3.0.0-12-generic
  71.9GB: boot/initrd.img-3.0.0-14-generic
  84.0GB: boot/initrd.img-3.0.0-15-generic
  78.0GB: boot/vmlinuz-3.0.0-12-generic
  69.9GB: boot/vmlinuz-3.0.0-14-generic
  75.3GB: boot/vmlinuz-3.0.0-15-generic
  84.0GB: initrd.img
  71.9GB: initrd.img.old
  75.3GB: vmlinuz
  69.9GB: vmlinuz.old

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set d561982c-c893-44dc-b06d-b59aa0e7780c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set d561982c-c893-44dc-b06d-b59aa0e7780c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d561982c-c893-44dc-b06d-b59aa0e7780c
	linux	/boot/vmlinuz-2.6.32-38-generic root=UUID=d561982c-c893-44dc-b06d-b59aa0e7780c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d561982c-c893-44dc-b06d-b59aa0e7780c
	echo	'Loading Linux 2.6.32-38-generic ...'
	linux	/boot/vmlinuz-2.6.32-38-generic root=UUID=d561982c-c893-44dc-b06d-b59aa0e7780c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d561982c-c893-44dc-b06d-b59aa0e7780c
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=d561982c-c893-44dc-b06d-b59aa0e7780c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d561982c-c893-44dc-b06d-b59aa0e7780c
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=d561982c-c893-44dc-b06d-b59aa0e7780c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d561982c-c893-44dc-b06d-b59aa0e7780c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d561982c-c893-44dc-b06d-b59aa0e7780c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2b1b-1302
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-15-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-15-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro splash vga=796 quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-15-generic
}
menuentry "Ubuntu, with Linux 3.0.0-15-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-15-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset splash vga=796
	initrd /boot/initrd.img-3.0.0-15-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-14-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro splash vga=796 quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-14-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-14-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset splash vga=796
	initrd /boot/initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro splash vga=796 quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 31c1a1b4-1e0e-4e32-a19d-f5e245b285f2
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=31c1a1b4-1e0e-4e32-a19d-f5e245b285f2 ro recovery nomodeset splash vga=796
	initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d561982c-c893-44dc-b06d-b59aa0e7780c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=5a626c9d-6484-489b-9a9a-c215110b5952 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  65.3GB: boot/grub/core.img
  61.6GB: boot/grub/grub.cfg
  66.2GB: boot/initrd.img-2.6.32-33-generic
  60.1GB: boot/initrd.img-2.6.32-38-generic
  66.1GB: boot/vmlinuz-2.6.32-33-generic
  66.1GB: boot/vmlinuz-2.6.32-38-generic
  60.1GB: initrd.img
  66.2GB: initrd.img.old
  66.1GB: vmlinuz
  66.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  00 00 00 00 38 c1 cc 3f  00 00 00 00 00 00 00 00  |....8..?........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 90 90 90 90  |................|
00000020  38 0c cd 3f 00 98 00 00  00 00 00 02 00 00 00 00  |8..?............|
00000030  a2 74 1e 29 90 90 90 90  00 00 00 00 38 e6 bd 3f  |.t.)........8..?|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 01 00 00  |................|
00000050  01 00 00 00 00 00 00 00  4d 00 00 00 90 90 90 90  |........M.......|
00000060  78 0c cd 3f 00 f8 3f 00  01 00 00 02 00 00 00 00  |x..?..?.........|
00000070  b1 94 96 5b 90 90 90 90  00 00 00 00 00 00 00 00  |...[............|
00000080  18 30 b9 3f 00 00 00 00  00 00 00 00 00 00 00 00  |.0.?............|
00000090  02 00 00 00 00 00 00 00  29 00 00 00 a8 0c cd 3f  |........)......?|
000000a0  01 00 00 00 90 90 90 90  00 00 00 00 00 00 00 00  |................|
000000b0  bc 0c cd 3f 00 00 00 00  00 00 00 00 e8 0c cd 3f  |...?...........?|
000000c0  03 00 00 00 25 00 00 00  1f 00 00 00 12 00 00 00  |....%...........|
000000d0  01 00 00 00 00 00 00 00  0d 00 00 00 ff 07 00 00  |................|
000000e0  01 00 00 00 45 00 00 00  00 00 00 00 00 00 00 00  |....E...........|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000110  00 00 00 00 00 00 00 00  00 00 00 00 80 0d cd 3f  |...............?|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 4c c1 cc 3f  60 0c cd 3f 00 00 00 00  |....L..?`..?....|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 90 90 90 90  |................|
00000180  94 0d cd 3f 00 f8 00 00  00 00 00 02 00 00 00 00  |...?............|
00000190  a2 74 1e 29 00 00 00 00  38 e6 bd 3f 00 00 00 00  |.t.)....8..?....|
000001a0  00 00 00 00 00 00 00 00  00 01 00 00 01 00 00 00  |................|
000001b0  00 00 00 00 14 00 00 00  90 90 90 90 90 8b 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 57 81 38 01 00 00  |..........W.8...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

Don't know what the last items are about on sda4...

That extended partition was a left-over from a previous setup where I had separate home & root partitions in sda4 - I recently wiped them & did a fresh install of 10.04 without separate home partition, but left it inside an extended, just in case I wanted to change my mind about that.

---

### Post by drs305 on 2012-02-10
2CV67,

Your current Grub menu should display 800x600 according to the sda3 grub.cfg file.

If that is the current resolution and you want to experiment to see if grub.cfg now has control over your display, you could open /boot/grub/grub.cfg and change the 800x600 value on line 46. Then save the file (without running update-grub). The resolution should respond to any change you make to that line on reboot.

If you have used GC for only minor tweaks to grub, I'd remove it completely. I'd like to give you more steps to take from within GC but currently cannot get GC to run on my system for some reason. Step 7 of the original post details how to restore the original files.

---

### Post by 2CV67 on 2012-02-10
The then current dislay was indeed 800x600.

Changing /boot/grub/grub-cfg does change the grub screen OK so I can set it that way for now.

I used GC to set timeout & to only display essential kernels, so I will leave it like that for now.
I think I could get into more trouble trying to follow the "reversion" instructions than by staying with what I have...

If there are any subsequent suggestions, I will be very interested to get  this working properly.

Thank you again, very much, for your help!  :)

---

### Post by drs305 on 2012-02-10
> **2CV67 said:**
> The then current dislay was indeed 800x600.

Changing /boot/grub/grub-cfg does change the grub screen OK so I can set it that way for now.

I used GC to set timeout & to only display essential kernels, so I will leave it like that for now.
I think I could get into more trouble trying to follow the "reversion" instructions than by staying with what I have...

If there are any subsequent suggestions, I will be very interested to get  this working properly.

Thank you again, very much, for your help!  :)

Since there is still a bit of uncertainty about how the resolution was/is set, there is one caveat. The setting in grub.cfg will probably be reset the next time you or the system runs update-grub (automatically for kernel upgrades, for instance).

The setting should be come from the following line in */etc/default/grub*. Make sure the setting there matches what you want, since this is where the resolution setting is imported from when things are running correctly.
> GRUB_GFXMODE=800x600

Note: The */etc/default/grub* file may or may not be used with Grub Customizer installed. Some of the scripts are 'proxified' but I don't think the /etc/default/grub file is so the resolution set in this file should be incorported into the grub.cfg file when update-grub is executed.

---

### Post by 2CV67 on 2012-02-10
Thanks!

I just tested update-grub and it reset grub.cfg to the last value I had set in SUM before uninstalling it.

It does NOT take the current value from /etc/default/grub.

I would like to know where it is storing this old SUM data & how to remove that!

Maybe I will reinstall SUM & set that value to what I want & hope it will stick through update-grub's...

---

### Post by 2CV67 on 2012-02-10
I did reinstall SUM & now I can control Grub screen text size with SUM & all the other stuff with GC.

Messy but it works - for the moment!

---

### Post by Jimmy_r on 2012-02-11
Ok, i havent touched this in ages so barely remember how this stuff works.

First, have this system been upgraded from an earlier ubuntu version which had grub1?
Since there is an option when upgrading to grub2 if you want to keep grub1 in mbr and chainload into grub2, my first thought is that maybe grub1 is still used as your first bootloader, and that causes some odd situation.

If not, i try to explain what SUM could have changed below:

I should have been sane enough to only set the paths used in this file: [http://bazaar.launchpad.net/~jimmy-ronnholm/startup-manager/main/view/head:/bootconfig/grub.py](http://bazaar.launchpad.net/~jimmy-ronnholm/startup-manager/main/view/head:/bootconfig/grub.py)
```

        self.config_file            = '/etc/default/grub'
        self.readonly_config_file   = '/boot/grub/grub.cfg'
        self.update_grub_command    = '/usr/sbin/update-grub'
        self.grub_install_command   = '/usr/sbin/grub-install'
```


So as far as i can tell, the only config file it should touch when it comes to grub2 is /etc/default/grub.

when it comes to resolution, the only lines it should mess with are GRUB_CMDLINE_LINUX_DEFAULT and GRUB_GFXMODE

So if you change those lines to what you want and run update-grub, anything SUM did change should be taken care of.

---

### Post by 2CV67 on 2012-02-11
> **Jimmy_r said:**
> So as far as i can tell, the only config file it should touch when it comes to grub2 is /etc/default/grub.

when it comes to resolution, the only lines it should mess with are GRUB_CMDLINE_LINUX_DEFAULT and GRUB_GFXMODE

So if you change those lines to what you want and run update-grub, anything SUM did change should be taken care of.

Thanks very much for jumping in, Jimmy_r!

This morning, since your post:
I reinstalled SUM & reset the resolution to 640x480 which is what I really want to have.
That put 640x480 into grub.cfg & gives me big text for the Grub screen.
I then used Synapt to completely remove SUM.

For a test, I used GC to set the resolution to 1280x1024 & saved.
/etc/default/grub now has 1280x1024.
After running update-grub, /boot/grub/grub.cfg still shows 640x480 & Grub screen still has big text.

I manually changed grub.cfg (as root) & saved it with 1280x1024.
After update-grub, it is back to 640x480.

So SUM can control grub.cfg which controls the Grub screen.
GC can control /etc/default/grub but information from there never gets to grub.cfg, even after update-grub.

The history is messy.
I originally had partitions with 11.04 & 10.04, both with grub1.
Then I wiped 11.04 & did a clean install of 11.10 with grub2, keeping grub1 in 10.04.
Later I wiped 10.04 & did a clean install of 10.04 again, but with grub2.
The output of boot_info_script with yesterday's values is in post #224, with some shady areas...

What could I check next?

---

### Post by Jimmy_r on 2012-02-11
Really strange.. I have no clue whats happening then

---

### Post by drs305 on 2012-02-11
One way we haven't tried to update the *grub.cfg* file which might make a difference: Rather than run "sudo update-grub" try:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
This is a less user-friendly but more direct way of running update-grub and specifically targets the grub.cfg file. It should import the resolution setting in */etc/default/grub*.

---

### Post by 2CV67 on 2012-02-11
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

That should transfer the /etc/default/grub setting (1280x1024x8) into grub.cfg, right?

Well - no, it doesn't.
grub.cfg still says 640x480.

/etc/grub.d/00_header still includes:
```
if [ "x$gfxterm" = x1 ]; then
    # Make the font accessible
    prepare_grub_to_access_device `${grub_probe} --target=device "${GRUB_FONT_PATH}"`

    cat << EOF
if loadfont `make_system_path_relative_to_its_root "${GRUB_FONT_PATH}"` ; then
set gfxmode=640x480
  load_video
  insmod gfxterm
EOF
```
in case that is significant.

Is there any way I can "trace" the action of update-grub, or grub_mkconfig, to see where it is looking?

If I am the only one with this problem, then I am sorry to be wasting your time.
If others have it too, then maybe it's not a waste...

---

### Post by drs305 on 2012-02-11
> **2CV67 said:**
> 
Is there any way I can "trace" the action of update-grub, or grub_mkconfig, to see where it is looking?

If I am the only one with this problem, then I am sorry to be wasting your time.
If others have it too, then maybe it's not a waste...

I don't know if anyone else is having this problem but I don't mind continuing this investigation (although when it's finally resolved, if ever, as a moderator I may break this off into its own thread). It's become a puzzle. Normally in situations such as this someone pops into the thread and sees something obvious and solves it with a single post. Until that happens....

The first thing I'd confirm after running the grub-mkconfig command is the time/date stamp of grub.cfg to see if it was changed. If it was, then please post your /etc/grub.d/00_header and /etc/default/grub files. And your previous experiments (typos, etc) have confirmed this is the file it is using on boot.

If it's updating the grub.cfg file but not using the resolution, there is something in the settings and script which tells Grub not to import the resolution into grub.cfg. That instruction should be buried in the 00_header script and based on input from the /etc/default/grub settings as far as I know.

I believe SUM is still in control of the resolution? If so, you could also change the SUM resolution setting and then do a search using 'find' to see what file(s) changed after running it. Looking through / might take a while, so you might start with /boot first and expand it to / if no results are found:
```
sudo find /boot -type f -cmin 3
sudo find / -type f -cmin 3
```

I'm off on a business trip but will check back as I can.

---

### Post by 2CV67 on 2012-02-11
I ran update-grub & the time/date stamp of grub.cfg WAS updated.

Here are the /etc/grub.d/header_00 & etc/default/grub files after that update-grub:

```
#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

transform="s,x,x,"

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
locale_dir=`echo ${GRUB_PREFIX}/locale | sed ${transform}`
grub_lang=`echo $LANG | cut -d . -f 1`

. ${libdir}/grub/grub-mkconfig_lib

# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=auto ; fi

if [ "x${GRUB_DEFAULT_BUTTON}" = "x" ] ; then GRUB_DEFAULT_BUTTON="$GRUB_DEFAULT" ; fi
if [ "x${GRUB_DEFAULT_BUTTON}" = "xsaved" ] ; then GRUB_DEFAULT_BUTTON='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT_BUTTON}" = "x" ] ; then GRUB_TIMEOUT_BUTTON="$GRUB_TIMEOUT" ; fi

cat << EOF
if [ -s \$prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
EOF
if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
   set default="${GRUB_DEFAULT_BUTTON}"
else
   set default="${GRUB_DEFAULT}"
fi
EOF
else
    cat <<EOF
set default="${GRUB_DEFAULT}"
EOF
fi
cat <<EOF
if [ "\${prev_saved_entry}" ]; then
  set saved_entry="\${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "\${boot_once}" ]; then
    saved_entry="\${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "\${have_grubenv}" ]; then if [ -z "\${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
EOF
if [ -n "${GRUB_VIDEO_BACKEND}" ]; then
    cat <<EOF
  insmod ${GRUB_VIDEO_BACKEND}
EOF
else
    # Insert all available backends; GRUB will use the most appropriate.
    have_video=0;
    for backend in $(cat "${GRUB_PREFIX}/video.lst"); do
	have_video=1;
	cat <<EOF
  insmod ${backend}
EOF
    done
    if [ x$have_video = x0 ]; then
	echo "true"
    fi
fi
cat <<EOF
}

EOF

serial=0;
gfxterm=0;
for x in ${GRUB_TERMINAL_INPUT} ${GRUB_TERMINAL_OUTPUT}; do
    if [ xserial = "x$x" ]; then
	serial=1;
    fi
    if [ xgfxterm = "x$x" ]; then
	gfxterm=1;
    fi
done

if [ "x$serial" = x1 ]; then
    if ! test -e ${GRUB_PREFIX}/serial.mod ; then
	echo "Serial terminal not available on this platform." >&2 ; exit 1
    fi

    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
	grub_warn "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used."
	GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
fi

if [ "x$gfxterm" = x1 ]; then
    # Make the font accessible
    prepare_grub_to_access_device `${grub_probe} --target=device "${GRUB_FONT_PATH}"`

    cat << EOF
if loadfont `make_system_path_relative_to_its_root "${GRUB_FONT_PATH}"` ; then
set gfxmode=640x480
  load_video
  insmod gfxterm
EOF

# Gettext variables and module
if [ "x${LANG}" != "xC" ] && [ -d "${locale_dir}" ] ; then
    prepare_grub_to_access_device $(${grub_probe} --target=device ${locale_dir}) | sed -e "s/^/  /"
  cat << EOF
  set locale_dir=(\$root)$(make_system_path_relative_to_its_root ${locale_dir})
  set lang=${grub_lang}
  insmod gettext
EOF
fi

cat <<EOF
fi
EOF
fi

case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
terminal_input ${GRUB_TERMINAL_INPUT}
EOF
  ;;
esac

case x${GRUB_TERMINAL_OUTPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
terminal_output ${GRUB_TERMINAL_OUTPUT}
EOF
  ;;
esac

if [ "x$gfxterm" = x1 ]; then
    if [ "x$GRUB_THEME" != x ] && [ -f "$GRUB_THEME" ] \
	&& is_path_readable_by_grub "$GRUB_THEME"; then
	echo "Found theme: $GRUB_THEME" >&2
	prepare_grub_to_access_device `${grub_probe} --target=device "$GRUB_THEME"`
	cat << EOF
insmod gfxmenu
EOF
	themedir="`dirname "$GRUB_THEME"`"
	for x in "$themedir"/*.pf2 "$themedir"/f/*.pf2; do
	    if [ -f "$x" ]; then
		cat << EOF
loadfont (\$root)`make_system_path_relative_to_its_root $x`
EOF
	    fi
	done
	if [ x"`echo "$themedir"/*.jpg`" != x"$themedir/*.jpg" ] || [ x"`echo "$themedir"/*.jpeg`" != x"$themedir/*.jpeg" ]; then
	    cat << EOF
insmod jpeg
EOF
	fi
	if [ x"`echo "$themedir"/*.png`" != x"$themedir/*.png" ]; then
	    cat << EOF
insmod png
EOF
	fi
	if [ x"`echo "$themedir"/*.tga`" != x"$themedir/*.tga" ]; then
	    cat << EOF
insmod tga
EOF
	fi
	    
	cat << EOF
set theme=(\$root)`make_system_path_relative_to_its_root $GRUB_THEME`
EOF
    elif [ "x$GRUB_BACKGROUND" != x ] && [ -f "$GRUB_BACKGROUND" ] \
	    && is_path_readable_by_grub "$GRUB_BACKGROUND"; then
	echo "Found background: $GRUB_BACKGROUND" >&2
	case "$GRUB_BACKGROUND" in 
	    *.png)         reader=png ;;
	    *.tga)         reader=tga ;;
	    *.jpg|*.jpeg)  reader=jpeg ;;
	    *)             echo "Unsupported image format" >&2; exit 1 ;;
	esac
	prepare_grub_to_access_device `${grub_probe} --target=device "$GRUB_BACKGROUND"`
	cat << EOF
insmod $reader
background_image -m stretch `make_system_path_relative_to_its_root "$GRUB_BACKGROUND"`
EOF
    fi
fi

make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=${2}
fi
EOF
}

if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
echo else
make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
echo fi
else
make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
fi

if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ] && [ "x$GRUB_BUTTON_CMOS_CLEAN" = "xyes" ]; then
    cat <<EOF
cmosclean $GRUB_BUTTON_CMOS_ADDRESS
EOF
fi

# Play an initial tune
if [ "x${GRUB_INIT_TUNE}" != "x" ] ; then
  echo "play ${GRUB_INIT_TUNE}"
fi

if [ "x${GRUB_BADRAM}" != "x" ] ; then
  echo "badram ${GRUB_BADRAM}"
fi

```

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="3"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="vga=775 splash"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="1280x1024x8"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_SAVEDEFAULT="false"
```

I reinstalled SUM (again!) & changed the resolution there, then ran the 2 searches you suggested.
The results don't show anything I can recognise as useful.
What is surprising is they don't find grub.cfg even though it IS updated by SUM to the latest setting.
Confirmed twice more.

Terminal output for searches:

```
chris@Acer-desk:~$ sudo find /boot -type f -cmin 3
[sudo] password for chris: 
chris@Acer-desk:~$ sudo find / -type f -cmin 3
find: ‘/proc/7474/task/7474/fd/5’: No such file or directory
find: ‘/proc/7474/task/7474/fdinfo/5’: No such file or directory
find: ‘/proc/7474/fd/5’: No such file or directory
find: ‘/proc/7474/fdinfo/5’: No such file or directory
find: ‘/home/chris/.gvfs’: Permission denied
chris@Acer-desk:~$ 
```

---

### Post by Jimmy_r on 2012-02-11
Aha. Seems the version of sum in repositories does not have the same version of code as on the launchpad page i was referring to.

A few versions ago, ubuntu did not have support for setting gfxmode through the config file, it was done directly in the 00_header file. The startupmanager that is in ubuntu repositories does still live by that rule and edits that file directly.

This is how to solve your problem:
Edit /etc/grub.d/00_header

Change the line that looks like this
```
set gfxmode=640x480
```
to instead look like this
```
  set gfxmode=${GRUB_GFXMODE}
```

Save the file, run update-grub and dont use SUM again.. gonna see if i can have it removed from ubuntu repositories ^^

---

### Post by 2CV67 on 2012-02-11
> **Jimmy_r said:**
> 
This is how to solve your problem:
Edit /etc/grub.d/00_header

Change the line that looks like this
```
set gfxmode=640x480
```
to instead look like this
```
  set gfxmode=${GRUB_GFXMODE}
```

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/bulls-eye.jpg[/IMG]

Very grateful thanks for all the help on this thread!   :D   :D

---

### Post by drs305 on 2012-02-11
I have an old guide on StartUp-Manager and will add a note about this when I return home from my business trip. SUM was good in it's day but as we see it hasn't kept up with the times.

Thanks Jimmy_r

EDIT:
I have updated the official community documentation on _[https://help.ubuntu.com/community/StartUpManager]("https://help.ubuntu.com/community/StartUpManager")_ as well as the Ubuntu Forum _[StartUp Manager]("http://ubuntuforums.org/showthread.php?t=818177")_ thread.

---

### Post by overkill22 on 2012-03-07
hi !
i want to know something:

1) when i start and stop the pc how can i see the therminal with all the list of the operation that the pc is doing ?
now when i start i have a black screen for 20 seconds then i'm on my desktop.
when i stop the pc now i have the quiet  splash...

2) how can i set correctly the quiet splash when i start the pc ?

i need to do this with the correct relolution (in my case is 1366x768 )

thankyou

---

### Post by drs305 on 2012-03-07
> **overkill22 said:**
> hi !
i want to know something:

1) when i start and stop the pc how can i see the therminal with all the list of the operation that the pc is doing ?
now when i start i have a black screen for 20 seconds then i'm on my desktop.
when i stop the pc now i have the quiet  splash...

2) how can i set correctly the quiet splash when i start the pc ?

i need to do this with the correct relolution (in my case is 1366x768 )

thankyou

The 'quiet' setting is the one that hides the text - try removing 'quiet splash' and see if that is the result you are looking for.

In GC, the setting can be changed via the Edit, Preferences, Advanced: Untick the GRUB_CMDLINE_LINUX_DEFAULT setting if all it contains are the "quiet splash" listings. If you have other entries on that line that you want to keep, you can click the line and delete the individual entries.

You can also directly edit the /etc/default/grub file as root and remove only the "quiet splash" entries from the same line.

If you manually edit the file, don't forget to run "sudo update-grub" after saving the file.

The GRUB resolution is also in the same tab in the GRUB_GFXMODE. However, this setting affects only the Grub menu and after it passes control to the kernel your text size may not be the same as it was in Grub.

---

### Post by overkill22 on 2012-03-07
> **drs305 said:**
> The 'quiet' setting is the one that hides the text - try removing 'quiet splash' and see if that is the result you are looking for.

In GC, the setting can be changed via the Edit, Preferences, Advanced: Untick the GRUB_CMDLINE_LINUX_DEFAULT setting if all it contains are the "quiet splash" listings. If you have other entries on that line that you want to keep, you can click the line and delete the individual entries.

You can also directly edit the /etc/default/grub file as root and remove only the "quiet splash" entries from the same line.

If you manually edit the file, don't forget to run "sudo update-grub" after saving the file.

The GRUB resolution is also in the same tab in the GRUB_GFXMODE. However, this setting affects only the Grub menu and after it passes control to the kernel your text size may not be the same as it was in Grub.

thank you for your answer.

i tried to remove "quite splash" in the advanced settings of GC but nothing to do...
i tried to remove "quite splash" + the mark in GRUB_CMDLINE_LINUX_DEFAULT but nothing to do...

1) is possible to set resolution for the kernel like we can do with grub ?

2) what does GRUB_GFXMODE do ?

thank you.

---

### Post by drs305 on 2012-03-07
The GRUB_GFXMODE setting sets the resolution of the Grub gfx terminal (this is the default Grub terminal which allows graphics to be displayed in the menu). The normal use is to change the size of the text in the menu. You can use any setting Grub can detect (search "vbeinfo") or leave it set to "auto" and let Grub determine the highest available resolution.

You can also use the Grub 'console', which is more like a regular terminal. You use this by enabling "GRUB_TERMINAL=console" in Grub Customizer.

Grub has the capability of transferring the resolution from the Grub menu to the kernel - it seems to work with varying rates of success. 

You can use the Add feature in the GC Preferences tab to add a new line:
> GRUB_GFXPAYLOAD_LINUX=keep

For more information, take a look at the [GNU GRUB Manual]("http://www.gnu.org/software/grub/manual/grub.html#gfxpayload"). Section 13.1.8 and 13.1.9

One other way to see the text as the computer boots is to use the "text" option, but it has some drawbacks. You can include the "text" option where I had you look for "quiet splash". This should display the boot messages (although they will scroll by quickly) but it will leave you at a text login screen. You can get to the Desktop by logging in and then running "sudo lightdm".

You can test this without making the change permanent by pressing 'e' at the grub menu. Cursor to the end of the 'linux' line, type "text" without the quotes, and then press CTRL-x to boot.

---

### Post by overkill22 on 2012-03-08
i've read the documentation...
i've understand how to do the text boot.

now my grub is set like the picture grub.png, but when i start i see only black screen... i've try to do some change but nothing happened.

why?
i don't see any grub menu because i have only lubuntu on this computer. (see grub2.png)

---

### Post by drs305 on 2012-03-09
> **overkill22 said:**
> ...when i start i see only black screen... i've try to do some change but nothing happened.

why?
i don't see any grub menu because i have only lubuntu on this computer. (see grub2.png)

Are you asking how to see the Grub menu at boot? If so, try holding down the SHIFT key while the system starts to boot. That should display the Grub menu if you only have one OS. This will check the 'keystatus' function.

If that doesn't work, try pressing ESC repeatedly during the boot to see if it appears.

If that doesn't work, try booting and then CTRL-ALT-DEL about midway through the boot. Since the system didn't fully boot Grub is supposed to display the menu the next time the system starts. Trying this will check to see if the 'recordfail' check is present and working.

---

### Post by overkill22 on 2012-03-09
> **drs305 said:**
> Are you asking how to see the Grub menu at boot? If so, try holding down the SHIFT key while the system starts to boot. That should display the Grub menu if you only have one OS. This will check the 'keystatus' function.

If that doesn't work, try pressing ESC repeatedly during the boot to see if it appears.

If that doesn't work, try booting and then CTRL-ALT-DEL about midway through the boot. Since the system didn't fully boot Grub is supposed to display the menu the next time the system starts. Trying this will check to see if the 'recordfail' check is present and working.

no, it is correct that i don't see the grub menu, i want so.

i want to see the "quiet splash" like i see when i shutdown the pc. the same i want to see when i startup. now at startup i see black screen with a white cursor on top left...

---

### Post by drs305 on 2012-03-09
Ok, I think we are back to the start. Your system boots to the Desktop but you want to be able to see what messages are displayed during boot?

Perhaps running the Boot Info Script and posting the contents of RESULTS.txt will show us something. You can run the script from within Grub Customizer.

---

### Post by overkill22 on 2012-03-10
> **drs305 said:**
> Ok, I think we are back to the start. Your system boots to the Desktop but you want to be able to see what messages are displayed during boot?

Perhaps running the Boot Info Script and posting the contents of RESULTS.txt will show us something. You can run the script from within Grub Customizer.

hi!
hi want to be able to do 2 different things:

1) in the first case i want to see the messages displayed during boot. (like a terminal console)

2) in the second case i don't want to see the message but i want to see only the pretty screen with the logo "lubuntu" that i see when i shut down the pc. 

now i don't see the picture and don't see the boot's messages.

how can i save the boot info script ?

---

### Post by drs305 on 2012-03-10
> **overkill22 said:**
> hi!
hi want to be able to do 2 different things:

1) in the first case i want to see the messages displayed during boot. (like a terminal console)

2) in the second case i don't want to see the message but i want to see only the pretty screen with the logo "lubuntu" that i see when i shut down the pc. 

now i don't see the picture and don't see the boot's messages.

how can i save the boot info script ?

Do you see the Grub menu at all when you boot?

You can run the script from within Grub Customizer. It will run and provide a link to the location of the RESULTS.txt. This will be enough, but if you want to be nice and post it for us:
Go to the link, open the file and copy the contents. Then start a new post here, click the **#** icon in the post's menu. This will create "Code" tags. Copy the RESULTS.txt content between the 'code' tags to help with formatting.


If you can't get the script to run from Grub Customizer, you can download the script and follow the instructions from:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by overkill22 on 2012-03-11
> **drs305 said:**
> Do you see the Grub menu at all when you boot?

You can run the script from within Grub Customizer. It will run and provide a link to the location of the RESULTS.txt. This will be enough, but if you want to be nice and post it for us:
Go to the link, open the file and copy the contents. Then start a new post here, click the **#** icon in the post's menu. This will create "Code" tags. Copy the RESULTS.txt content between the 'code' tags to help with formatting.


If you can't get the script to run from Grub Customizer, you can download the script and follow the instructions from:
[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

i didn't find how to run the script from GC, i used bootinfoscript:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   619,378,687   619,376,640  83 Linux
/dev/sda2         619,380,734   625,141,759     5,761,026   5 Extended
/dev/sda5         619,380,736   625,141,759     5,761,024  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disco /dev/sdb: 2021 MB, 2021654528 byte
63 testine, 62 settori/tracce, 1010 cilindri, totale 3948544 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,945,059     3,944,998   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        fa1311a1-925a-4a8a-a760-30cb1a2fa5b8   ext4       
/dev/sda5        f36b0fed-84fc-4f08-a41d-eca2c7a4d50a   swap       
/dev/sdb1        54DB-9058                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/54DB-9058         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root fa1311a1-925a-4a8a-a760-30cb1a2fa5b8
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root fa1311a1-925a-4a8a-a760-30cb1a2fa5b8
  set locale_dir=($root)/boot/grub/locale
  set lang=it_IT
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, con Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root fa1311a1-925a-4a8a-a760-30cb1a2fa5b8
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=fa1311a1-925a-4a8a-a760-30cb1a2fa5b8 ro vga=795  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, con Linux 3.0.0-16-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root fa1311a1-925a-4a8a-a760-30cb1a2fa5b8
    echo    'Caricamento Linux 3.0.0-16-generic...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=fa1311a1-925a-4a8a-a760-30cb1a2fa5b8 ro recovery nomodeset vga=795
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, con Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root fa1311a1-925a-4a8a-a760-30cb1a2fa5b8
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=fa1311a1-925a-4a8a-a760-30cb1a2fa5b8 ro vga=795  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, con Linux 3.0.0-12-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root fa1311a1-925a-4a8a-a760-30cb1a2fa5b8
    echo    'Caricamento Linux 3.0.0-12-generic...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=fa1311a1-925a-4a8a-a760-30cb1a2fa5b8 ro recovery nomodeset vga=795
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fa1311a1-925a-4a8a-a760-30cb1a2fa5b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f36b0fed-84fc-4f08-a41d-eca2c7a4d50a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-16-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  48 fa 7c 6d 64 9d 4c 68  c5 15 31 11 bc 6b c5 de  |H.|md.Lh..1..k..|
00000010  2d dc cf 61 95 f3 2d 44  b8 a6 91 68 6f a0 1a 46  |-..a..-D...ho..F|
00000020  27 fe 97 c7 33 28 8a ea  e2 54 78 92 21 89 cb c8  |'...3(...Tx.!...|
00000030  4a 16 f7 e3 f0 e5 30 7c  68 c2 8a 94 6c 82 75 28  |J.....0|h...l.u(|
00000040  c0 3a 14 fb b9 24 fd 92  e7 ce eb 0d 75 7e 93 f7  |.:...$......u~..|
00000050  84 9d 4b 16 a7 b4 67 9d  61 a0 46 1e ea 32 e0 06  |..K...g.a.F..2..|
00000060  9b 75 a1 72 9e b1 37 c1  c1 bb 76 f2 b4 b3 11 93  |.u.r..7...v.....|
00000070  dc 68 97 a5 09 1c 46 7e  15 b7 11 65 ef 42 da 86  |.h....F~...e.B..|
00000080  82 20 97 fb 91 23 2e f9  e4 d0 e2 4b 7a db 2a 5a  |. ...#.....Kz.*Z|
00000090  e3 a1 a1 5c 39 d4 01 d7  82 85 ed c8 b3 b5 fa e2  |...\9...........|
000000a0  68 6f e7 35 be 9a f6 55  57 88 a6 96 59 a5 8f 39  |ho.5...UW...Y..9|
000000b0  bb a7 12 75 aa 20 4a f9  c7 58 5b 73 83 b8 d7 1e  |...u. J..X[s....|
000000c0  3d b1 6a 82 56 fe 76 8e  45 fb 0a 7d 84 f4 d8 ed  |=.j.V.v.E..}....|
000000d0  56 60 db 03 61 2b d2 f4  a8 a5 3f 8c bc ab ab 2f  |V`..a+....?..../|
000000e0  71 f6 bc 97 9e 35 32 4b  3e c5 c2 d0 c6 f7 79 4f  |q....52K>.....yO|
000000f0  9c 16 0f 9f 8c 55 9e 2c  39 ec 7b 4f a9 9d d5 ec  |.....U.,9.{O....|
00000100  88 f9 1d ab 2e 9d b5 68  68 d5 04 e9 19 f2 4c eb  |.......hh.....L.|
00000110  90 ae 2e 3a 2d d6 a1 f9  32 35 6f f0 2a f1 ee 18  |...:-...25o.*...|
00000120  07 8a 84 ed 7e 76 ec e1  76 62 e3 51 d9 b9 ef 3d  |....~v..vb.Q...=|
00000130  d9 fd 98 5d df 62 74 cd  8d 97 a9 17 7d 66 d7 dc  |...].bt.....}f..|
00000140  e9 46 ed 73 74 fd fb 25  46 d7 da e7 ec 9a 3b 95  |.F.st..%F.....;.|
00000150  29 9a 3e a3 eb f5 66 d7  68 fc 79 ba b6 24 b6 6b  |).>...f.h.y..$.k|
00000160  52 d7 77 1a 5d 5f 99 d4  75 11 75 bd 84 fb fe 90  |R.w.]_..u.u.....|
00000170  e9 2d f5 0e 77 3d ea fd  fa 54 27 85 a4 de d1 72  |.-..w=...T'....r|
00000180  49 9b 74 89 64 4f 1d 89  39 1e ec 13 07 a1 cf 22  |I.t.dO..9......"|
00000190  5f 75 fb aa 7a d1 d8 32  ab fc 31 65 02 50 e7 4f  |_u..z..2..1e.P.O|
000001a0  ac f9 51 c3 98 df ea 3b  b0 a6 ac 70 d7 1d d0 e2  |..Q....;...p....|
000001b0  5a 62 b6 c7 fa fe 3b 23  10 f3 93 60 a8 1d 00 fe  |Zb....;#...`....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 57 00 00 00  |............W...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by drs305 on 2012-03-11
> **overkill22 said:**
> 
hi want to be able to do 2 different things:

1) in the first case i want to see the messages displayed during boot. (like a terminal console)

Currently your default selection still contains the "quiet splash" entries

> menuentry 'Ubuntu, con Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root fa1311a1-925a-4a8a-a760-30cb1a2fa5b8
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=fa1311a1-925a-4a8a-a760-30cb1a2fa5b8 ro [COLOR="Blue"]vga=795[/COLOR]  [COLOR="Red"]quiet splash vt.handoff=7[/COLOR]
    initrd    /boot/initrd.img-3.0.0-16-generic
}

I think we tried to 'fix' this before, but in case you didn't or perhaps didn't complete it correctly:
It appears you should see the Grub menu for 10 seconds. Press 'e' at the Grub menu and you should see the above menuentry. Use the cursors and DEL key to remove the text in [COLOR="Red"]red[/COLOR]. Then CTRL-x to boot and you *should* see the messages as it boots. This doesn't change things permanently - only for the current boot.
> 
2) in the second case i don't want to see the message but i want to see only the pretty screen with the logo "lubuntu" that i see when i shut down the pc. 

now i don't see the picture and don't see the boot's messages.

I have Lubuntu LTS in a virtual machine and I get the Lubuntu screen during boot. One reason may be that you have a 'vga' setting in your options. Although 'vga' settings are deprecated, they should still work. But you can see if that makes a difference by removing the 'vga' information in [COLOR="Blue"]blue[/COLOR] in the same manner as above.

I can't do any more testing with Lubuntu as it broke when I tried to update it while writing this post. Rather than reinstall it I'm going to wait for the next LTS next month.

---

### Post by overkill22 on 2012-03-12
> **drs305 said:**
> Currently your default selection still contains the "quiet splash" entries



I think we tried to 'fix' this before, but in case you didn't or perhaps didn't complete it correctly:
It appears you should see the Grub menu for 10 seconds. Press 'e' at the Grub menu and you should see the above menuentry. Use the cursors and DEL key to remove the text in [COLOR=Red]red[/COLOR]. Then CTRL-x to boot and you *should* see the messages as it boots. This doesn't change things permanently - only for the current boot.

I have Lubuntu LTS in a virtual machine and I get the Lubuntu screen during boot. One reason may be that you have a 'vga' setting in your options. Although 'vga' settings are deprecated, they should still work. But you can see if that makes a difference by removing the 'vga' information in [COLOR=Blue]blue[/COLOR] in the same manner as above.

I can't do any more testing with Lubuntu as it broke when I tried to update it while writing this post. Rather than reinstall it I'm going to wait for the next LTS next month.

i tried to remove the red one and i see the text boot.
if i remove the blue one the screen is black....
how can i set the text resolution during the text boot ?

and can you tell me why the part in red is in different resolution (mine is 1266*768 )

```
insmod part_msdos insmod ext2 set root='(hd0,msdos1)' search --no-floppy --fs-uuid --set=root fa1311a1-925a-4a8a-a760-30cb1a2fa5b8 if loadfont /usr/share/grub/unicode.pf2 ; then set [COLOR=Red]gfxmode=1280x1024[/COLOR]   load_video   insmod gfxterm   insmod part_msdos   insmod ext2   set root='(hd0,msdos1)'   search --no-floppy --fs-uuid --set=root fa1311a1-925a-4a8a-a760-30cb1a2fa5b8   set locale_dir=($root)/boot/grub/locale   set lang=it_IT   insmod gettext
```

---

### Post by drs305 on 2012-03-14
> **overkill22 said:**
> i tried to remove the red one and i see the text boot.
if i remove the blue one the screen is black....
how can i set the text resolution during the text boot ?

and can you tell me why the part in red is in different resolution (mine is 1266*768 )


Your "GRUB" resolution appears to be set to 1280x1024. This is the resolution for your Grub menu and is set by Grub automatically or via the setting in /etc/default/grub.  Grub will attempt to use the 'best' resolution if none is specified. This is what is contained in your grub.cfg file:

> set gfxmode=1280x1024

Note that this resolution isn't the one necessarily used by your OS once the system is booted. This is only the Grub resolution.

Grub's instructions tell the kernel to boot at the resolution equivalent of "vga 795", which is the equivalent of 1280×1024. I don't know the equivalent of 1266x768.

One more tweak you could try at the Grub menu is to edit the entry, removing the "vga=795" AND also change 
> set gfxpayload=$linux_gfx_mode
to 
set gfxpayload=keep


I'm not on the forums much at present and don't have the time to thoroughly investigate your video issues (which is not one of my strong points). That's why I'm mostly offering you temporary fixes, hoping one of them might work but not sure they will.

---

### Post by overkill22 on 2012-03-19
nothing to do...
i'm afraid because i think that it is a very simple action to do because two years ago i had the same problem on my notebook with ubuntu 10.04 LTS...
the only problem is that i don't see the quiet splash when i start the netbook but only when i shutdown...

however thank you for your time, it was precious for me, so i knew something new ... hope with lubuntu 12.04 this problem will disappear..

---

### Post by Chutney3k on 2012-04-01
This is Fantastic!!

Thank you SO MUCH!, you're efforts are very much appreciated.

I have previously attempted to edit GRUB after some googling and it was a nightmare and ultimately unsuccessful. 

This was a breeze! it did everything I wanted.

I feel this should come bundled with GRUB and BURG

I would like to also be able to hide recovery entries, but be able to press a hot key to show the recovery entry when I need it. but that is a request for BURG probably.

10/10!

---

### Post by Chutney3k on 2012-04-01
Oh, forgot to mention,

the only issue I did have was that Grub Customizer did not appear in the Ubuntu Software centre even after adding the repository, nor did it appear in the menus when I installed it using apt-get grub-customizer. I could only find it using the terminal command to run the customizer as per your terminal instructions

---

### Post by drs305 on 2012-04-01
> **Chutney3k said:**
> 
I would like to also be able to hide recovery entries, but be able to press a hot key to show the recovery entry when I need it. but that is a request for BURG probably.

10/10!

This won't do exactly what you want but it's what I have done on my wife's computer...

I created a custom menu entry (41_custom) for the recovery mode option using default settings so it would always boot the latest kernel's recovery mode. I made an empty title, so it doesn't show on the menu but if you scroll to the bottom of the menu ( a blank line) and press ENTER the recovery mode boots. Something along these lines (I've omitted the 'search' line in this example since it contains a specific UUID for my system but you can leave it in your copy):
> 
menuentry '   ' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos[COLOR="Red"]11[/COLOR])'
	linux	/vmlinuz ro single
	initrd	/initrd.img
}


---

### Post by Chutney3k on 2012-04-01
Ah, Very cool idea. Only problem with that (if im reading you right) is that I like to use Icon's without text in my theme so I would still have additional icons right?

---

### Post by drs305 on 2012-04-01
> **Chutney3k said:**
> Ah, Very cool idea. Only problem with that (if im reading you right) is that I like to use Icon's without text in my theme so I would still have additional icons right?

Themes would certainly add additional 'problems'. I haven't played with themes for quite some time. I suspect the answer would be to create an invisible or transparent icon but would have to leave that to someone else to play with.  ;-)

---

### Post by bogan on 2012-04-29
Hi!,** drs305**,

With your help, and this very instructive Thread, I got the grub menus in my set-up exactly as I wanted, with a different arrangement and background for each installation: 10.04LTS, 11.10 on HDD & 11.10 on USB, according to which I booted, from.
Thus I was never in doubt as to which boot was selected.

Now I have up-graded [with Update Manager] 11.10 to 12.04LTS and things went better than I expected, other than having to reset the Themes for GTK & Windows, to avoid unreadable text [White on White], and an error message "Could not write bytes: Broken pipe" at login and shut down.

However, after three days I am finding problems, the most annoying of which, apart from frequent uninformative: "Sorry, 12.04 has encountered an internal error" messages, is that I cannot get Grub Menu to change its background; it remains a bright 'Aubergine' with white text.

I have tried removing and reinstalling Grub Customizer and grub itself; using different images that work with other installations, and even dropping one into /boot/grub, as well as re-organising GC settings when booted into each.
Edit: In my 11.10, 10.04 and a LiveUsb with full install of 11.10, all the backgrounds are just as I wanted.

With 12.04, 'Update-grub' finds the different images I have tried, they show in /etc/default/grub, and there are no other .png or jpeg files in /boot/grub. I also tried running```
 sudo grub-mkconfig
```The text is exactly as I wanted, but the background stays stubbornly plain Aubergine.
Grub menu title shows: > GNU GRUB version 1.99-21ubuntu3Is there some difference with 12.04LTS, or Grub/grub2 ?? that prevents a change of background, or have I missed something?. I cannot see any similar reports in all the threads I have searched through.

Is it possible that the "Broken pipe" error message could be a clue??

Edit, Fri 4th May: I have just upgraded to a 23-inch Monitor as I suspected some of my Unity crash problems were something to do with the older monitor; but it has made no difference to the Grub background not changing.

Chao!, **bogan.**

---

### Post by drs305 on 2012-05-06
bogan,

Are you trying to use a background image or just trying to change to a different colored (no image) background?

I haven't tried using a background image in 12.04 yet but I am not aware of any changes that should have caused problems.

If it's a background image that is failing, attach it to a post and I'll try to use it on my system.

---

### Post by bogan on 2012-05-07
Hi!, **drs305**,

Thanks for your response.

It is mainly the background image that I cannot get to change, but the text, highlighted or not, does not change either.

I have tried four different images, all of which work in 10.04 and 11.10, but will not in 12.04. Attached is the one I last tried: greencove16_9.jpg.

Edit: Apologies, I picked the .jpg images because they were smaller, I forgot about changing them to .png format. I used Gimp to convert this one to greencove16_9.png and it worked.

Not only that, but the text colors changed also.

So: Solved.  Chao!, **bogan**.

---

### Post by mmesantos1 on 2012-05-07
Very helpful how to, thank you for posting. :)

---

### Post by aquarius18 on 2012-05-20
Strange things seem to happen sometimes - such as this:

On a Mint12 install I had grub customizer working without problems. Same on my other 2 Ubuntu installs (11.04 and on another partition 12.04).

Since a couple of days grub customizer takes about 2 minutes to load (?????) - the authentication window pops up immediately after selecting grub customizer from the menu / shortcut and then - silence .....

I have googled the problem and searched this thread from go to woe - to no avail.

What could have gone wrong?

Linux Mint 12
Cinnamon 1.4
Kernel 3.2.0-xxxx (the problem also happens with standard 3.0.0 - xxx and latest 3.3.4 - xxx kernels)
grub customizer 2.5.5

Thanks all

---

### Post by bogan on 2012-05-20
Hi!, **aquarius18,**

Since updating to 12.04, Grub-Customizer - always slow to load - has seemed much slower.

I just re-ran it and the progress bar crawled, stalling several times, and finally completed loading in one minute 15 seconds from entering my password in the Authentication box.

So you are not alone.

Chao!,** bogan.**

---

### Post by aquarius18 on 2012-05-20
> **bogan said:**
> Hi!, **aquarius18,**

Since updating to 12.04, Grub-Customizer - always slow to load - has seemed much slower.

I just re-ran it and the progress bar crawled, stalling several times, and finally completed loading in one minute 15 seconds from entering my password in the Authentication box.

So you are not alone.

Chao!,** bogan.**

Thanks bogan

What buggers me is that Grub Customizer loaded quick-smart until a few day ago on my Linux Mint 12 (based on Ubuntu 11.10) and now it takes an eternity to fire up. It's just like a delay of 2 minutes has crept into some file ...... all the other OS's are loading Grub Customizer in a flash.

If I would know where to look for the faulty (??) file then I could probably fix it.

Thanks again / Frank

---

### Post by drs305 on 2012-05-21
> **aquarius18 said:**
> Strange things seem to happen sometimes - such as this:
...

Since a couple of days grub customizer takes about 2 minutes to load (?????) - the authentication window pops up immediately after selecting grub customizer from the menu / shortcut and then - silence ...

What could have gone wrong?


1, I've had GC hang a few times for me. In my case once it was due to disk issues. For you I would think that wouldn't be the problem if GC ran correctly from another OS.

2. The second time it was due to a modified script I had in my /etc/grub.d folder. Even though the script wasn't executable GC still tried to run it.

3. I would suggest trying to 'turn off' os-prober by removing the executable flag to see if it still hangs, but based on #2 it may run the script anyway. It looks like GC will look at everything regardless of the flag setting, which makes sense since it wants to allow you to select (or not select) everything from within GC.

4. Does "sudo update-grub" run normally?

---

### Post by aquarius18 on 2012-05-21
> **drs305 said:**
> 1, I've had GC hang a few times for me. In my case once it was due to disk issues. For you I would think that wouldn't be the problem if GC ran correctly from another OS.

No, that is unlikely as the disk o/wise is working w/out problem.

> **drs305 said:**
> 2. The second time it was due to a modified script I had in my /etc/grub.d folder. Even though the script wasn't executable GC still tried to run it.

Hmmmm....

> **drs305 said:**
> 3. I would suggest trying to 'turn off' os-prober by removing the executable flag to see if it still hangs, but based on #2 it may run the script anyway. It looks like GC will look at everything regardless of the flag setting, which makes sense since it wants to allow you to select (or not select) everything from within GC.

I will try that tomorrow (it's close to midnight here and time for a horizontal position...)

> **drs305 said:**
> 4. Does "sudo update-grub" run normally?

Runs normally, quick as usual.

Thanks again - I'll report back tomorrow after work

Frank

---

### Post by aquarius18 on 2012-05-22
Well, I can't see anything in the /etc/grub.d folder that may cause the problem. Then again, I am not a Linux coder, so my capabilities are limited indeed.

Did a reinstall of Grub Customizer but the result is still the same.

Would it make sense to completely remove GC and then do a fresh install? 

As an aside, this drive (sdc1) is (at least at this point in time) not the controlling OS. The actual grub loader is generated / controlled by a Ubuntu 11.04 install on sda6.

Thanks again

---

### Post by bogan on 2012-05-22
Hi!, **aquarious18,**

You Posted:>  As an aside, this drive (sdc1) is (at least at this point in time) not  the controlling OS. The actual grub loader is generated / controlled by a  Ubuntu 11.04 install on sda6.In that case, I would suggest that is where you should be looking.  

Chao!,** bogan**.

---

### Post by PcMojo on 2012-05-22
@Drs305 I just did a clean install of 12.04 and am using GnomeClassic. I followed your instructions at the beginning of this thread (not realizing how old the thread was at the time) and had difficulty.   I started by trying to use Synaptic, but couldn't find Synaptic (gone in 12.04? Sniff, sniff) I was able to install grub customizer via terminal because for some reason using Ubuntu Software Center (USC) didn't work. I could add the ppa, and could see two of them that were added in USC, but the searches never brought up the grub customizer program. I restarted USC and did multiple searches and unhid technical files, but no joy.   I just wanted to let others know in case they are having the same problem. Your terminal commands at the beginning of the thread worked just fine!  Cheers!

---

### Post by aquarius18 on 2012-05-22
> **PcMojo said:**
> @Drs305 I just did a clean install of 12.04 and am using GnomeClassic. I followed your instructions at the beginning of this thread (not realizing how old the thread was at the time) and had difficulty.   I started by trying to use Synaptic, but couldn't find Synaptic (gone in 12.04? Sniff, sniff) I was able to install grub customizer via terminal because for some reason using Ubuntu Software Center (USC) didn't work. I could add the ppa, and could see two of them that were added in USC, but the searches never brought up the grub customizer program. I restarted USC and did multiple searches and unhid technical files, but no joy.   I just wanted to let others know in case they are having the same problem. Your terminal commands at the beginning of the thread worked just fine!  Cheers!

The first post has been edited/updated several times so should still be relevant.

You can still use synaptic by installing it yourself

```
sudo apt-get install synaptic
```

that worked for me

---

### Post by aquarius18 on 2012-05-22
thanks bogan

> **bogan said:**
> Hi!, **aquarious18,**

You Posted:In that case, I would suggest that is where you should be looking.  

Chao!,** bogan**.

GC loaded normally until a few days ago (see my first post on this issue) - no changes have been made to the disks/partitions.

---

### Post by drs305 on 2012-05-22
> **PcMojo said:**
> @Drs305 I just did a clean install of 12.04 and am using GnomeClassic. I followed your instructions at the beginning of this thread (not realizing how old the thread was at the time) and had difficulty.   I started by trying to use Synaptic, but couldn't find Synaptic (gone in 12.04? Sniff, sniff) I was able to install grub customizer via terminal because for some reason using Ubuntu Software Center (USC) didn't work. I could add the ppa, and could see two of them that were added in USC, but the searches never brought up the grub customizer program. I restarted USC and did multiple searches and unhid technical files, but no joy.   I just wanted to let others know in case they are having the same problem. Your terminal commands at the beginning of the thread worked just fine!  Cheers!

Thanks for the feedback. I'll recheck the main page and make the necessary changes as soon as I have a bit of time.

---

### Post by drs305 on 2012-05-22
> **aquarius18 said:**
> 
As an aside, this drive (sdc1) is (at least at this point in time) not the controlling OS. The actual grub loader is generated / controlled by a Ubuntu 11.04 install on sda6.


That is the key, not an aside. GC would be making changes to the GRUB you have on the release you are currently running. Any changes would be make to the GRUB files *on that partition* but would not be reflected on the GRUB menu if it is being controlled by another OS/release.

Boot into that release, then make it's GRUB the controlling one by running the following commands (only the first is required to do it but you should update your menu as well). The first command will instruct the system to look for the correct bootloader by writing that location into the MBR (or equivalent). It's now looking at your other OS for the boot instructions. If you want sdb, just change the command if your BIOS looks at sdb first.
```
sudo grub-install /dev/sda
sudo update-grub

```

---

### Post by aquarius18 on 2012-05-22
> **drs305 said:**
> That is the key, not an aside. GC would be making changes to the GRUB you have on the release you are currently running. Any changes would be make to the GRUB files *on that partition* but would not be reflected on the GRUB menu if it is being controlled by another OS/release.

Boot into that release, then make it's GRUB the controlling one by running the following commands (only the first is required to do it but you should update your menu as well). The first command will instruct the system to look for the correct bootloader by writing that location into the MBR (or equivalent). It's now looking at your other OS for the boot instructions. If you want sdb, just change the command if your BIOS looks at sdb first.
```
sudo grub-install /dev/sda
sudo update-grub

```

Did just that:

```
sudo grub-install /dev/sdc 
sudo update-grub
```
[FONT=monospace]
and changed boot order to sdc in BIOS. OS loads fine but [/FONT][FONT=monospace]it didn't fix the problem[/FONT][FONT=monospace], GC still takes 2min 30sec to load.

I am stumped ](*,)

[/FONT]

---

### Post by drs305 on 2012-05-23
> **aquarius18 said:**
> ... but it didn't fix the problem, GC still takes 2min 30sec to load.

I am stumped ](*,)


Don't really know what is happening. I'm sure GC runs a system search. If it uses the unaltered os-prober command, you could try running that one yourself just to see how long it takes outside of GC. If it hangs at any point it might indicate which partition or drive it was trying to read at the time. The command would be 
```
sudo os-prober
```

---

### Post by aquarius18 on 2012-05-24
> **drs305 said:**
> Don't really know what is happening. I'm sure GC runs a system search. If it uses the unaltered os-prober command, you could try running that one yourself just to see how long it takes outside of GC. If it hangs at any point it might indicate which partition or drive it was trying to read at the time. The command would be 
```
sudo os-prober
```

Thanks again.

Running sudo os-prober revealed nothing at all, loads fine and does not hang.

Frank

---

### Post by drs305 on 2012-05-24
Under preferences there is a timeout option. If it is set perhaps shortening it will help. You can also disable the system search and I assume GC would 'honor' what was already in the menu as a result of update-grub. Other than that, I'm afraid I don't have any new ideas.

---

### Post by aquarius18 on 2012-05-25
> **drs305 said:**
> Under preferences there is a timeout option. If it is set perhaps shortening it will help. You can also disable the system search and I assume GC would 'honor' what was already in the menu as a result of update-grub. Other than that, I'm afraid I don't have any new ideas.

Thanks again - I really appreciate your time and efforts.

I have done a complete purge and reinstall:

```
sudo apt-get remove --purge grub-customizer

sudo apt-get clean

sudo apt-get install grub-customizer
```

rebooted but to no avail. 

Guess I have to live with it for the time being.

Cheers / Frank

---

### Post by chome4 on 2012-05-30
How do I get Grub Customizer to transfer its screen resolution settings to the Ubuntu 'Displays' area? 

Grub Customizer shows a long list of resolutions and after selecting the one I want and saving/updating, the resolutions list is still showing the default ones I had straight after install.

---

### Post by drs305 on 2012-05-30
> **chome4 said:**
> How do I get Grub Customizer to transfer its screen resolution settings to the Ubuntu 'Displays' area? 

Grub Customizer shows a long list of resolutions and after selecting the one I want and saving/updating, the resolutions list is still showing the default ones I had straight after install.

Adding this line to /etc/default/grub, or through GC, is *supposed* to transfer the setting in GRUB_GFXMODE to the kernel. I know early on it had troubles doing so.  Make sure you have GRUB_GFXMODE set to the resolution you want and then add or enable this line:

> GRUB_GFXPAYLOAD_LINUX=keep

I'm curious if this setting works for you, so please let us know

You should note this from the man page:
> Depending on your kernel, your distribution, your graphics card,
     and the phase of the moon, note that using this option may cause
     GNU/Linux to suffer from various display problems, particularly
     during the early part of the boot sequence.  If you have problems,
     set this option to `text' and GRUB will tell Linux to boot in
     normal text mode.


---

### Post by chome4 on 2012-05-30
> **drs305 said:**
> Adding this line to /etc/default/grub, or through GC, is *supposed* to transfer the setting in GRUB_GFXMODE to the kernel. I know early on it had troubles doing so.  Make sure you have GRUB_GFXMODE set to the resolution you want and then add or enable this line:



I'm curious if this setting works for you, so please let us know

You should note this from the man page:

Did a fresh install and installed GC. Made the amendment to the file 'grub' but nothing changed.

Here's my grub file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="1280x1024x15"
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
===================================================================


lspci | grep VGA gives:

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5430 Series]

---

### Post by bogan on 2012-05-30
Hi!, chome4,

In your Gruib file the : GRUB_GFXMODE="1280x1024x[COLOR=Red]15[/COLOR]" entry should either be: > GRUB_GFXMODE="1280x1024x**[COLOR=Blue]16[/COLOR]**" or > GRUB_GFXMODE="1280x1024x**[COLOR=Blue]24[/COLOR]**"Though if that would affect its operation or not, I have no idea.

Chao!, **bogan**.

---

### Post by ohmysql on 2012-05-30
By the way if you want grub to play the theme song from Inspector Gadget when you boot up, here's the script:

GRUB_INIT_TUNE="1000 220 3 247 1 262 3 294 1 330 2 0 2 262 2 0 2 311 4 247 3 0 1 294 2 0 2 262 3"

Yeah, that might be nerdiest thing I've done in a while is look up the pitches and sound that out...

My musical education is totally going to waste, and PS I am underpaid!

---

### Post by chome4 on 2012-05-31
> **bogan said:**
> Hi!, chome4,

In your Gruib file the : GRUB_GFXMODE="1280x1024x[COLOR=Red]15[/COLOR]" entry should either be:  or Though if that would affect its operation or not, I have no idea.

Chao!, **bogan**.

Doesn't work!

I can't believe those muppets at Canonical have released an operating system without the easy ability to choose from a list of resolutions.

Just like Microsoft when they released the rubbish Windows Vista!!!

---

### Post by jringoot on 2012-05-31
I find this quite complex to use.
I could not resolve my issue with this.

Issue was: 
I have multiboot: windows7+ubuntu 12.04+ fedora 17
got an update of ubuntu -> fedora got lost in the grub menu.

Reason was: ubuntu was installed on regular logical drives but fedora created an LVM on install.
Solution: 
-sudo apt-get install lvm2
-activate the volumegroup where fedora was installed (lvmtools or simply with palimpsest a gui disk-manager, is gnome-disk-utility as a package see [http://en.wikipedia.org/wiki/Palimpsest_Disk_Utility](http://en.wikipedia.org/wiki/Palimpsest_Disk_Utility))
-mount the volumes needed (/boot and /) (can be done easily with palimpsest as well)
-sudo grub-update

Now I have fedora choice back in grub, the menu entry is a bit ugly but it works

---

### Post by chome4 on 2012-05-31
> **jringoot said:**
> Thanks this is really usefull now.
Since I have a triple boot: win7, ubuntu, fedora (I need them all for my job).

And now ubuntu update has updated grub and kicked out the fedora entries, not even present in older linux installs.

I think that's really ugly from the Ubuntu development team/staff.


Found this:
  
In a terminal: sudo gedit /etc/default/grub    Search for the line with  "quiet splash", and change it to "quiet splash nomodeset". Save the  file.  Then sudo update-grub.  And reboot your computer. In most of the  cases this will help.
  
....you guessed it....didn't work either....
  
    [LEFT]I'm trying to find a way to contact Canonical to let them know that this is one of the major issues people have with Ubuntu.

UPDATE:

The link below contains a correspondence I had with the producer of Grub Customizer.

[http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html/comment-page-1#comment-125381](http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html/comment-page-1#comment-125381)
[/LEFT]

---

### Post by flaviops on 2012-06-30
Hi, I change the preferences on the grub customizer but when I reboot none of the changes are made(the grub customizer still have the options changed). What can I do about it?


Thanks.

Edit: It keeps with the purple background and white font color.

---

### Post by drs305 on 2012-07-01
> **flaviops said:**
> Hi, I change the preferences on the grub customizer but when I reboot none of the changes are made(the grub customizer still have the options changed). What can I do about it?

Thanks.

Edit: It keeps with the purple background and white font color.

flaviops,

Welcome to the Ubuntu Forums.  :-)

Do you have more than one Ubuntu installed on your computer? It's possible you are making changes to one set of Grub files while the system is booting off another set.

If you give me some examples of what you are trying to do it might help so we could look at specific settings.

In the meantime, you might download and install Boot Repair. It contains a script which we may need you to run to see what is happening. Also BR has the ability to change some basic settings, although not as many as GC does. 

The link to BR is in my signature line.

I'm logging out now but will check back tomorrow.

---

### Post by flaviops on 2012-07-01
> **drs305 said:**
> flaviops,

Welcome to the Ubuntu Forums.  :-)

Do you have more than one Ubuntu installed on your computer? It's possible you are making changes to one set of Grub files while the system is booting off another set.

If you give me some examples of what you are trying to do it might help so we could look at specific settings.

In the meantime, you might download and install Boot Repair. It contains a script which we may need you to run to see what is happening. Also BR has the ability to change some basic settings, although not as many as GC does. 

The link to BR is in my signature line.

I'm logging out now but will check back tomorrow.

Thanks. I am trying to change the background of the grub. I can change the fonts(modified only once) and the resolution on the grub customizer. But when I change the background and the colors, it keeps on the default.

Edit: I have only Ubuntu and windows in my notebook. I also tried to use boot repair using the recommended repair.

---

### Post by drs305 on 2012-07-01
> **flaviops said:**
> Thanks. I am trying to change the background of the grub. I can change the fonts(modified only once) and the resolution on the grub customizer. But when I change the background and the colors, it keeps on the default.

Edit: I have only Ubuntu and windows in my notebook. I also tried to use boot repair using the recommended repair.

Here are two threads you can take a look at. The first discusses adding a background image and changing font colors.
[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")

The second one is from yesterday and deals with font colors not changing even after editing /etc/grub.d/05_debian. I finally figured out what was happening, and it might be what is causing you problems as well.
[http://ubuntuforums.org/showthread.php?t=2012327]("http://ubuntuforums.org/showthread.php?t=2012327")

---

### Post by flaviops on 2012-07-02
> **drs305 said:**
> Here are two threads you can take a look at. The first discusses adding a background image and changing font colors.
[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")

The second one is from yesterday and deals with font colors not changing even after editing /etc/grub.d/05_debian. I finally figured out what was happening, and it might be what is causing you problems as well.
[http://ubuntuforums.org/showthread.php?t=2012327]("http://ubuntuforums.org/showthread.php?t=2012327")

Thanks, the problem was solved making the modifications contained on the second link.

---

### Post by Balthazar54 on 2012-07-14
Great program!

I've been stressing on how to change the boot default for a couple of weeks now. As a noobie, all the various posts on how to do this were just confusing me.

I found the the 'previously booted entry' option in preferences gave me an even better result than I was looking for. Having grub default to the last used os is perfect for me.

---

### Post by drs305 on 2012-07-14
> **Balthazar54 said:**
> Great program!

I've been stressing on how to change the boot default for a couple of weeks now. As a noobie, all the various posts on how to do this were just confusing me.

I found the the 'previously booted entry' option in preferences gave me an even better result than I was looking for. Having grub default to the last used os is perfect for me.

Yes, Grub Customizer doesn't get a lot of attention on these forums but it's a great tool.

Welcome to the forums and Happy Ubuntu-ing !

---

### Post by vexorian on 2012-07-21
grub-customizer is just great. Thanks.

---

### Post by bohemian9485 on 2012-07-25
Having used Grub Customizer to a great extent and witnessed its usability firsthand, I wonder why it was not included as a default package in Ubuntu.

---

### Post by beebelo on 2012-08-01
Grub Customizer is very nice. And thank you for this informative thread. I hope you can assist with my Grub2 issue. 

I'm running Ubuntu Studio 12.04. Fresh install. I let the installer wipe the hard drive with the automatic method. It's the only OS on the drive. 

Like many others, I want the old small font scrolling text boot-up messages like it used to be. I don't care about splash or color. 

What I get is a 1024x768x32 (I assume) Grub menu followed by the same black screen that others have reported, until a half-second before the LightDM login screen. 

So far neither GC nor manual editing of /etc/grub.d/00_header and /etc/default/grub -- followed by sudo update-grub -- has solved the problem. 

According to vbeinfo, I should be able to set 1024x768x32. (My monitor's native resolution is 1440x900 but that is not on the vbeinfo list.)

My video card is a Radeon 9550. I am not using the proprietary driver. 

Here is the result of my bootinfoscript: 
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    76,081,151    76,079,104  83 Linux
/dev/sda2          76,083,198    78,176,255     2,093,058   5 Extended
/dev/sda5          76,083,200    78,176,255     2,093,056  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2cf31bd7-8346-4b7e-81c2-12aff54a7499   ext4       
/dev/sda5        610c8587-4317-45a5-9756-1b180b50f7e0   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 2cf31bd7-8346-4b7e-81c2-12aff54a7499
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768x32
  set gfxpayload=keep
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 2cf31bd7-8346-4b7e-81c2-12aff54a7499
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-23-lowlatency-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 2cf31bd7-8346-4b7e-81c2-12aff54a7499
	linux	/boot/vmlinuz-3.2.0-23-lowlatency-pae root=UUID=2cf31bd7-8346-4b7e-81c2-12aff54a7499 ro   
	initrd	/boot/initrd.img-3.2.0-23-lowlatency-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-lowlatency-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 2cf31bd7-8346-4b7e-81c2-12aff54a7499
	echo	'Loading Linux 3.2.0-23-lowlatency-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-lowlatency-pae root=UUID=2cf31bd7-8346-4b7e-81c2-12aff54a7499 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-lowlatency-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 2cf31bd7-8346-4b7e-81c2-12aff54a7499
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 2cf31bd7-8346-4b7e-81c2-12aff54a7499
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2cf31bd7-8346-4b7e-81c2-12aff54a7499 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=610c8587-4317-45a5-9756-1b180b50f7e0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  26.143779755 = 28.071669760   boot/grub/core.img                             1
  26.143741608 = 28.071628800   boot/grub/grub.cfg                             1
   1.881286621 = 2.020016128    boot/initrd.img-3.2.0-23-lowlatency-pae        2
   6.326442719 = 6.792966144    boot/vmlinuz-3.2.0-23-lowlatency-pae           1
   1.881286621 = 2.020016128    initrd.img                                     2
   6.326442719 = 6.792966144    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  c9 c4 42 00 ca c4 42 00  cb c4 42 00 cc c4 42 00  |..B...B...B...B.|
00000010  cd c4 42 00 ce c4 42 00  cf c4 42 00 d0 c4 42 00  |..B...B...B...B.|
00000020  d1 c4 42 00 d2 c4 42 00  d3 c4 42 00 d4 c4 42 00  |..B...B...B...B.|
00000030  d5 c4 42 00 d6 c4 42 00  d7 c4 42 00 d8 c4 42 00  |..B...B...B...B.|
00000040  d9 c4 42 00 da c4 42 00  db c4 42 00 dc c4 42 00  |..B...B...B...B.|
00000050  dd c4 42 00 de c4 42 00  df c4 42 00 e0 c4 42 00  |..B...B...B...B.|
00000060  e1 c4 42 00 e2 c4 42 00  e3 c4 42 00 e4 c4 42 00  |..B...B...B...B.|
00000070  e5 c4 42 00 e6 c4 42 00  e7 c4 42 00 e8 c4 42 00  |..B...B...B...B.|
00000080  e9 c4 42 00 ea c4 42 00  eb c4 42 00 ec c4 42 00  |..B...B...B...B.|
00000090  ed c4 42 00 ee c4 42 00  ef c4 42 00 f0 c4 42 00  |..B...B...B...B.|
000000a0  f1 c4 42 00 f2 c4 42 00  f3 c4 42 00 f4 c4 42 00  |..B...B...B...B.|
000000b0  f5 c4 42 00 f6 c4 42 00  f7 c4 42 00 f8 c4 42 00  |..B...B...B...B.|
000000c0  f9 c4 42 00 fa c4 42 00  fb c4 42 00 fc c4 42 00  |..B...B...B...B.|
000000d0  fd c4 42 00 fe c4 42 00  ff c4 42 00 00 c5 42 00  |..B...B...B...B.|
000000e0  01 c5 42 00 02 c5 42 00  03 c5 42 00 04 c5 42 00  |..B...B...B...B.|
000000f0  05 c5 42 00 06 c5 42 00  07 c5 42 00 08 c5 42 00  |..B...B...B...B.|
00000100  09 c5 42 00 0a c5 42 00  0b c5 42 00 0c c5 42 00  |..B...B...B...B.|
00000110  0d c5 42 00 0e c5 42 00  0f c5 42 00 10 c5 42 00  |..B...B...B...B.|
00000120  11 c5 42 00 12 c5 42 00  13 c5 42 00 14 c5 42 00  |..B...B...B...B.|
00000130  15 c5 42 00 16 c5 42 00  17 c5 42 00 18 c5 42 00  |..B...B...B...B.|
00000140  19 c5 42 00 1a c5 42 00  1b c5 42 00 1c c5 42 00  |..B...B...B...B.|
00000150  1d c5 42 00 1e c5 42 00  1f c5 42 00 20 c5 42 00  |..B...B...B. .B.|
00000160  21 c5 42 00 22 c5 42 00  23 c5 42 00 24 c5 42 00  |!.B.".B.#.B.$.B.|
00000170  25 c5 42 00 26 c5 42 00  27 c5 42 00 28 c5 42 00  |%.B.&.B.'.B.(.B.|
00000180  29 c5 42 00 2a c5 42 00  2b c5 42 00 2c c5 42 00  |).B.*.B.+.B.,.B.|
00000190  2d c5 42 00 2e c5 42 00  2f c5 42 00 30 c5 42 00  |-.B...B./.B.0.B.|
000001a0  31 c5 42 00 32 c5 42 00  33 c5 42 00 34 c5 42 00  |1.B.2.B.3.B.4.B.|
000001b0  35 c5 42 00 36 c5 42 00  37 c5 42 00 38 c5 00 fe  |5.B.6.B.7.B.8...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 1f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

Thanks for any assistance.

---

### Post by drs305 on 2012-08-01
*beebelo*,

The scrolling text as the system boots is normally enabled by a setting in /etc/default/grub. Open this file as root:
```
gksu gedit /etc/default/grub
```

Change this line to allow scrolling system text messages during boot:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to:
> GRUB_CMDLINE_LINUX_DEFAULT=""

Then run "sudo update-grub" to update the menu. 

If this doesn't provide what you want, the next time you boot press highlight your boot selection and press 'e'.
Cursor to the end of the linux line and delete "quiet splash" with the backspace key. Press ctrl-x or F10 to boot, see if the text appears, and let us know.

---

### Post by beebelo on 2012-08-02
Hi drs305, 

I had looked for 'quiet splash', by way of GC and gedit as well, but maybe I was looking in the wrong place...  I will do this tonight and report back.

Thanks.

---

### Post by beebelo on 2012-08-02
Unfortunately I was correct. I had already gone down that path, and removed "quiet splash". 

Here is my /etc/default/grub : 
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
#GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="1024x768x32"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_DISABLE_OS_PROBER="true"

``` 
Is there anything else that you see which I should do?  I suppose this is not a Grub Customizer issue, so if you want me to post in a new thread, just let me know...

Thank you.

---

### Post by drs305 on 2012-08-02
> **beebelo said:**
> Unfortunately I was correct. I had already gone down that path, and removed "quiet splash". 
Is there anything else that you see which I should do?  I suppose this is not a Grub Customizer issue, so if you want me to post in a new thread, just let me know...

Thank you.

Grub Customizer can alter and move certain Grub configuration files, so making the change to /etc/default/grub may not be the file that GC uses to configure the menu. (It may be, I just don't know.)

So the next thing would be to look at the Grub menu during boot by the method I described in the last paragraph of my earlier post. See if "quiet splash" exists on the 'linux' line or not. If it is there, try removing it and boot.

If the 'quiet splash' is in the menu and you ran update-grub earlier, then another GC file may be creating the menu and we'll have to deal with it. If 'quiet splash' is not in the actual Grub menu I'll have to give this more consideration.

---

### Post by beebelo on 2012-08-02
> **drs305 said:**
> If 'quiet splash' is not in the actual Grub menu I'll have to give this more consideration.

... it's not there in the actual Grub menu:(

I also searched the files in /etc/grub.d/ .  I found this in 10_linux :
```
  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_RECOVERY}" != "xtrue" ]; then
    if [ -x /lib/recovery-mode/recovery-menu ]; then
      linux_entry "${OS}" "${version}" true \
        "recovery nomodeset ${GRUB_CMDLINE_LINUX}"
    else
      linux_entry "${OS}" "${version}" true \
        "single nomodeset ${GRUB_CMDLINE_LINUX}"
    fi
  fi
```
Don't know what is happening there exactly... or what the \ means in the line above 'quiet'. Does the \ just mean continued on the next line, like _ in visual basic?

---

### Post by drs305 on 2012-08-03
> **beebelo said:**
> ... it's not there in the actual Grub menu:(

Don't know what is happening there exactly... or what the \ means in the line above 'quiet'. Does the \ just mean continued on the next line, like _ in visual basic?

Yes, that is exactly what it means in this case. 

I always combine "quiet splash" and you said it wasn't in the menu, which is what I asked. Is "quiet" there? From the line in 10_linux it looks like it should be.

Since Grub Customizer can use some 'proxified' files/folders rather than the default ones, it might be helpful to see your entire setup by running the boot info script. You can run it (see the BIS link in my signature) from within Boot Repair, after installing that useful app.

---

### Post by beebelo on 2012-08-04
'Morning - 

1) The word "quiet" is not shown anywhere in my Grub menu when I press "e"
2) So I installed BIS as you recommended. The output it gave me is: [http://paste.ubuntu.com/1129244/](http://paste.ubuntu.com/1129244/)

---

### Post by drs305 on 2012-08-04
beebelo,

Thanks for posting the information. I really can't see why you can't get the scrolling text to appear. I can think of two things you can try, but these really shouldn't be necessary and may still not display the messages.

Both involve editing the GRUB preferences file and changing default settings.```

gksu gedit /etc/default/grub
```

Uncommenting this line would eliminate graphics from Grub (at least until later):
> # Uncomment to disable graphical terminal (grub-pc only)
**[COLOR="Red"]#[/COLOR]**GRUB_TERMINAL="console"

The other thing you could try would be to use the basic graphics resolution:
> 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[s]GRUB_GFXMODE="auto"[/s]
GRUB_GFXMODE=640x480

Make one of the changes, update-grub, and see what happens. If the first one doesn't work, restore the original setting and try the other.

Background: Not seeing the scrolling text during the boot process really is controlled by the kernel and not by GRUB. The messages are system messages from the OS you are using, not Grub - Grub merely provides a way to pass the parameter (quiet) to the system boot so that the messages are displayed. For some reason it isn't happening on your system. It may have something to do with the kernel you are using but I really don't know.

The two ideas above take the graphics out of the GRUB process. In theory I don't think this should affect what the kernel does, but let's see.

The only other thing I can think of at the moment would be to add "text" to the end of the linux options. This boots Ubuntu to the terminal login prompt. It isn't something that you would want to do often, but if you were trying to view the boot messages for troubleshooting purposes it might work.

---

### Post by bogan on 2012-08-05
Hi!, **drs305** &** beebelo**.
Edit: In one of MAFoElffen's 'Blank screen Sticky' Posts he suggested that in some kernal versions 'text' in the linux options did not work. I have found that setting the Grub background in GC can have the same result.

I do not know if this is relevant to your current 'no text messages' problem, but you may find it interesting.

On one of my desktops I have two 12.04 installations; A is a direct install of 12.04 -pae, B is an updated version  of 12.04 LTS -generic [not -pae] - originally 9.10.

Both are fully updated to 3.2.0-27 #43 with grub2 & GC controlled from B, so when I boot A to 12.04 pae the Grub background screen only shows for a second or so after pressing 'Enter'.
Hence If I edit its grub script and put " --verbose text " in place of " quiet splash " I get the full display of system messages before the TTY login prompt. If I then press 'Crtl+Alt+F7' the last messages are displayed with a hanging cursor, ending with "Checking Battery State [OK]".

With " --verbose text " in place in B, the Grub background screen continues to display for about 30 seconds, goes to a blank black screen for a moment, and then shows the TTY login prompt, but no messages. Pressing 'Crtl+Alt+F7' gives a blank black screen with a flashing cursor top left.

In other words, in some way Grub Customizer is preventing the 'text' option from giving a display, or it  is 'hidden' behind the background.
Presumably, if the grub background was set to a blank screen, it could have the same effect.

Chao!, **bogan**.

---

### Post by beebelo on 2012-08-05
> **drs305 said:**
>  Uncommenting this line would eliminate graphics from Grub (at least until later): 

Right, and that does in fact work. I've done it both from GC and by way of manual edit. It displays all the messages I wanted to see, albeit in a most ugly way (huge text that wraps around, and scrolls too fast to see because of its size). But the important point is that yes, it works.


> **drs305 said:**
> The other thing you could try would be to use the basic graphics resolution:  

I will try it with the 640x480 res as soon as I get a chance (late tonight). The setting "auto" is a recent change I made for trial purposes. Previously I had tried 800x600 and 1024x768, with and without the color depth setting, "x32"

Thanks for the information about the process itself and where GRUB ends and the kernel picks up. That may be useful. I'm using the low-latency pae stock kernel provided with Ubuntu Studio 12.04. I don't understand how the old framebuffer thing relates to booting with GRUB2 and a modern kernel. It used to be so easy in GRUB-legacy. lol

So it just occurred to me: The vbeinfo script that I ran previously, is that information just related to the GRUB menu? Not for after the kernel takes over?  

Anyway, I'll try these later tonight and post back ...

> **drs305 said:**
> The only other thing I can think of at the moment would be to add "text" to the end of the linux options. This boots Ubuntu to the terminal login prompt. It isn't something that you would want to do often, but if you were trying to view the boot messages for troubleshooting purposes it might work.

Right. Well I'm not troubleshooting anything yet, just set in my ways. Going back to my first *nix experiences in the early 2000s, I've always thought watching a workstation boot up is just really cool. And I especially liked the Linux distros that did the colored messages with the green "OK" and the red "FAIL".

Thanks again. More to come.

---

### Post by beebelo on 2012-08-05
> **bogan said:**
> 
In other words, in some way Grub Customizer is preventing the 'text' option from giving a display, or it  is 'hidden' behind the background.
Presumably, if the grub background was set to a blank screen, it could have the same effect.

bogan,

Thanks very much for that information. I will digest it and see how I can relate it to my problem.  Certainly looks to be valuable info!  

beeb

---

### Post by drs305 on 2012-08-05
> **beebelo said:**
> So it just occurred to me: The vbeinfo script that I ran previously, is that information just related to the GRUB menu? Not for after the kernel takes over?  

Anyway, I'll try these later tonight and post back ...


The vbeinfo command displays what resolutions are available before the OS boots, so it actually applies only to BIOS and GRUB and not to what resolutions are available after the OS boots.

"gfxpayload=keep"  is *supposed* to try to keep the same resolution between Grub and the OS, but results are mixed on its implementation.

---

### Post by beebelo on 2012-08-09
Just a quick reply to say that I have surrendered. Nothing has the desired effect. Some setting did cause slight differences in where the black screen began and ended, but that is all. I also tried adding "verbose" at the GRUB menu. 

Based on what you (drs305) were saying about GRUB handing over to the kernel, I'm guessing that some particular graphics module is not compiled into this kernel, since GRUB_TERMINAL="console" does work (though it's too large & fast to read).

Thanks for all you help--I do appreciate it very much!

---

### Post by newb85 on 2012-08-13
I'm having a few problems.

I tried to change the font to "Ubuntu".  Unfortunately, now all the symbols are rendered as ?'s.  Is there a default font I should put it on to revert this?

Also, my grub is now displayed with the Debian splash screen as the background.  I haven't selected a background, so I'm not sure why.  How do I get rid of this?

Thanks!

---

### Post by Jakin on 2012-08-13
Pretty sure the "default" font is Sans.

To remove the image goto settings, and hit the X, or just change it to whatever you wish.

and dont forget to save :)

---

### Post by newb85 on 2012-08-13
> **Jakin said:**
> Pretty sure the "default" font is Sans.

To remove the image goto settings, and hit the X, or just change it to whatever you wish.

and dont forget to save :)

Switching to Sans took care of the symbol issue.  Thanks!

I should have been more clear: I didn't select a background image, and no image is selected in the Preferences dialogue.  Therefore, the "X" (which the Ambiance theme renders as a "-") button isn't available.  But the Debian background image shows up anyways.

---

### Post by Jakin on 2012-08-13
Thats strange.. and i have no anwser for it. 
I know its not really a solution; If you can apply images, and just want like a plain black (or whatever color) image you can find that anywhere and apply.

---

### Post by drs305 on 2012-08-14
> **newb85 said:**
> I'm having a few problems.
...
Also, my grub is now displayed with the Debian splash screen as the background.  I haven't selected a background, so I'm not sure why.  How do I get rid of this?

Thanks!

You probably have the package "desktop-base" installed. It really isn't necessary unless you purposefully installed it.

Grub searches for desktop-base when building the Grub menu. The files are located in /usr/share/images/desktop-base. 

There are a couple of ways to get rid of the background:
1. Uninstall desktop-base
2. Rename the /usr/share/images/desktop-base folder
3. Edit the 05_debian_theme script
4. Use a different image which has a higher priority than desktop-base.

You can check your /boot/grub/grub.cfg file to confirm where the background image is being pulled from. Most likely it is from desktop-base, but it could also be an image file located in /boot/grub or from a setting in /etc/default/grub. 

However you hide or remove the image file, run "sudo update-grub" to remove the information from the grub.cfg file.

If this post didn't help, find the section of grub.cfg which references the background image being used and copy it in a post.

---

### Post by newb85 on 2012-08-14
@drs305 - Thanks, option 2 worked wonderfully.

@Jakin - Actually, Sans isn't the default font.  The default is not to have a font set.  There's a button next to the font in the Preferences dialogue ("X" or "-" or whatever your theme represents it as) that clears out the font selection.

---

### Post by Jakin on 2012-08-14
> **newb85 said:**
> 
@Jakin - Actually, Sans isn't the default font.  The default is not to have a font set.  There's a button next to the font in the Preferences dialogue ("X" or "-" or whatever your theme represents it as) that clears out the font selection.

On my setup there is actually no X or whatever to remove font, i have to actually choose one, So when you asked i checked what mine was (as i had never changed it)

Glad you figured the splash thing out :D

---

### Post by 2CV67 on 2012-08-19
**Grub Customizer Locks Me Out!**

I just upgraded from 11.10 to 12.04.

Mostly, things went pretty smoothly, leaving me with only a few details to sort out.

One detail was that my Grub menu had a lot of duplicates (wish I had noted exactly), instead of just 12.04 & 10.04LTS & XP which should show.

I used Grub Customizer to "fold up" some of these duplicates, assuming I would then not see them on the Grub screen.
At least one of each OS was still showing.

But when I came to reboot, ALL the 12.04 references had disappeared from Grub screen, so I can no longer boot my main Ubuntu!

I can still get to 10.04LTS & to XP & can also boot 10.04 & 12.04 from live USB sticks.

In 10.04, I tried installing Grub Customizer there too and it sees all the variants quite correctly (12.04 under os-prober) but that doesn't affect the Grub screen, which still does not show 12.04.

How can I regain access to my 12.04?

Of course I can dig into 12.04 files from 10.04, but which file(s) do I need to modify & how?

Thanks for any clues!

---

### Post by danielrichter on 2012-08-19
> **2CV67 said:**
> **Grub Customizer Locks Me Out!**

How can I regain access to my 12.04?


There are two solutions:

a) you can install the bootloader of 10.04 to mbr (on the files menu).
b) you can switch grub customizer to the 12.04 partition (also on the files menu)

---

### Post by 2CV67 on 2012-08-19
> **danielrichter said:**
> There are two solutions:

a) you can install the bootloader of 10.04 to mbr (on the files menu).
b) you can switch grub customizer to the 12.04 partition (also on the files menu)

Well, that's a whole lot better than zero solutions - Thanks!

I located the 2 options under 'Files' but am just hesitating before plunging in.

Is either option preferable?
What are the implications?

Thanks again!

---

### Post by danielrichter on 2012-08-19
> **2CV67 said:**
> Well, that's a whole lot better than zero solutions - Thanks!

I located the 2 options under 'Files' but am just hesitating before plunging in.

Is either option preferable?
What are the implications?

Thanks again!

The second is preferable as it's your main grub installation (I guess your primary system is 12.04). However Grub has the problem that the currenty running system (you're on 10.04) won't be found. But this is easy to fix simply by re-saving the config (or running update-grub) on 12.04.

---

### Post by 2CV67 on 2012-08-19
OK!

12.04 is back in business - thank you so much for your prompt assistance!

Thanks!

---

### Post by 2CV67 on 2012-08-19
Still not sure why I have duplicate os-prober & custom entries though.

Nor what to do about them...

[ATTACH]222898[/ATTACH]

---

### Post by bogan on 2012-08-19
Hi!, **Daniel Ricte**r,

Glad of the chance to say thank-you directly, for a great Program and continued support.

I have had a similar strange duplicate effect in Grub Customizer, to that mentioned by 2CV67.

I have two 12.04 versions, a pae kernal directly installed on sde11 and a generic updated version, originally 9.10, on sde8. GC on the later controlling Grub Menu.

Currently, GC on sde11 shows, in 'os-prober (custom)>(new entries)', no less than eleven copies of:> Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)all with a tick although I previously unticked all but one.

[COLOR=Blue]**Update:**[/COLOR]
I just rebooted to sde8 to check out my memory, and back again to sde11;  whereupon GC has added another four copies of the same sde8 entries, in  addition to the previous eleven.!!

NB. there is no entry for the recovery version of 12.04-generic and the originals had no way to identify which version 12.04 was referred to.[ I added the '12.04.1'.]

It also shows two copies of the 'custom' script, though there is nothing in them. [ I know I could delete one of them, but have not found a way to prevent or delete the duplicates.]

All the other entries in 'os-prober (custom)' are correct, Windows, 11.10 on USB & 10.04 on sde6, except that Windows does not have a recovery mode listed.

The entries in 'linux (custom)' for 12.04-pae, are also correct:> Ubuntu, with 12.04 LTS Linux 3.2.0-29-generic-pae (on sde11)
Ubuntu, with 12.04 LTS Linux 3.2.0-29-generic-pae (recovery mode)(on sde11This is not new, I first noticed it about the end of May when the recovery entry went missing but as it is not an operational problem, I have not bothered to report it. That is because the Grub Menu is controlled by the GC on sde8.

In that version all is as I would expect. > Ubuntu, with 12.04 LTS Linux 3.2.0-29-generic (on /dev/sde8) That also applies to the GC on the USB, which is operative when I boot from it via the Bios boot menu. Though the sde8 entries, including recovery versions, are shown under 'linux (custom)> (new entries)'.
[ There is also an empty entry for "header.dpkg-old> (new entries)", which does not exist in the sde11 version.}

I should perhaps add that I have not directly. edited any of the Grub or Grub Customizer files,.

Any Suggestions??  Sorry it is so long, it is complex to describe. 
Is it possible to remove and re-install Grub Customizer, without all the procedure in the 'How To'? or would that not work.??

Chao!, **bogan**.

---

### Post by bogan on 2012-08-19
Hi!, **2CV67**,

Your problem seems to be more simple than mine, and easier to correct, as it duplicates whole scripts, which GC can delete.

Which is, of course to treat the symptoms, and the error, cause untreated, may repeat itself.

Highlight the script header, eg.: 'custom' or 'os-prober', and select the negative symbol: '**-**', in the toolbar: that will delete it, then 'Save'.

Chao!, **bogan**.

---

### Post by bogan on 2012-08-26
**Re: Duplicate Grub Menu Entries after saving GC config.**

Hi!, **All,**  

Further to my Post #325, things have got more complicated:

I re-installed the 12.04.1 pae in sde11 [ with its /Home in sde10 ] with a newly downloaded live CD of 12.04.1, The installation went OK with only some minor problems.

I formated the root partition; hence it has a new copy of Grub-Customizer and it now controls the Grub menu.

However, it is still showing 11 duplicate incomplete copies of the sde8 Ubuntu 12.04-generic entry, though no recovery entry, and after un-ticking them and Saving the configuration, GC adds a further four entries, and they are now displayed in Grub Menu.

What is worse. the GC in sde8 is now doing the same thing with the sde11 entries, though, of course they do not show in the Grub Menu. The sde8 entries there, are correct.

Running: ```
grob menuentry /boot/grub/grub.cfg 
```shows four sde8 entries above the others [windows,usb,10.04 & 11.10] and one below them, in the /etc/grub.d/30-so-prober_proxy entries.

Displaying the /etc/grub.d/30-os-prober_proxy file, shows 12 sde8 entries before the others & 11 afterwards. [ The ID's{? addresses?} are not the same for all of them.]

Like the /boot/grub/grub.cfg entries, in the Grub Menu, highlighting an sde8 entry and pressing 'e', the last two lines have only:> linux /vmlinuz root=/dev/sde8
initrd /initrd.img  but selecting one, boots OK with a tty login showing for a few seconds before going to a full GUI login and normal Ubuntu desktop.

How can I correct this mix-up, and stop GC creating duplicate entries.?? EDit: Runniong 'update-grub', before GC, made no difference.

As it is a clean install I assume the error must be in files in the Home Partition which did not get renewed; or is that not possible?

Chao!, **bogan**.

---

### Post by bogan on 2012-08-29
**Re: Duplicate Grub Menu Entries after saving GC config.**  Update:

Hi!, **All,**

  I installed Gnome-shell and that replaced the Grub Customer grub menu background with the star-screen Debian logo. To get rid of it I edited /etc/default/grub, by adding "GRUB_BACKGROUND=<imagepath>", where <imagepath> was the same as set by GC.

This returned the chosen background, but unfortunately left the default text colours, which do not show up well against that background.

I am posting the contents of the: '/etc/grub.d/30-os-prober_proxy' file, in the hope someone can advise me as to what action to take.

It seems worth noting that the batch of four entries containing 3 X 'c8138...' & '39f2...', are the four entries repeated each time Grub Customizer configuration is Saved, or when it is rescanned; whilst in the original 11 entries, below the sde6 entries, are several additional entries with quite different digits.

```
#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/os-prober' | /etc/grub.d/bin/grubcfg_proxy "+*
+'Windows Vista (loader) (on /dev/sde1)'~e925706bb8401d20e0cc07cd00453cab~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~39f2bea9ceda40a0256e3780972bdd21~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~39f2bea9ceda40a0256e3780972bdd21~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~39f2bea9ceda40a0256e3780972bdd21~
+'Ubuntu, with 11.10 Linux 3.0.0-24-generic ( on USB) (on /dev/sda2)'~06326763671374ea76fa1965999b4863~
+'Ubuntu, with 11.10 Linux 3.0.0-24-generic (recovery mode) ( on USB) (on /dev/sda2)'~0f452f935f90913f7954c85f82021486~
+'Ubuntu, with 10.04 LTS Linux 2.6.32-42-generic (on sda6) (on /dev/sde6)'~b7a70d5132f6b78b0bb8855b9b218d26~
+'Ubuntu, with 10.04 Linux 2.6.32-42-generic (recovery mode) (on sda6) (on /dev/sde6)'~45b8ba42a6db1f408deb15f1bdeb8868~
+'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~39f2bea9ceda40a0256e3780972bdd21~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~30aa6e2264f526362a779e2cc7102729~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~36ddee63368b2e11f49be8f46017a123~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~cbbe1f6232a7c7e4599aab2078970ebe~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~ecc239d74178a4e281cc816e3424d1de~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~c8138359f6a4e43a84c3e32ef602e0a7~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~39f2bea9ceda40a0256e3780972bdd21~
-'Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)'~7638b89af8c75109af48766ecffa6f04~
"
```Is there any point, or possible harm, in just directly deleting the false entries from the Grub Customer display? - just leaving one -- but which one ??

Chao!, **bogan. **

---

### Post by drs305 on 2012-09-04
> **bogan said:**
> Is there any point, or possible harm, in just directly deleting the false entries from the Grub Customer display? - just leaving one -- but which one ??

Chao!, **bogan. **

For the moment, I'll address GRUB generally rather than GC specifically since I don't know how GC's prober treats GC entries in another partition.

Under normal circumstances, Grub's os-prober will take the entries in another partitions 10_linux section to help build the menu. I think I'd try directly editing the sda8 grub.cfg file and manually remove any extraneous entries from that menu.

I'd also look in your current OS's /etc/grub.d folder to make sure there is only one executable script looking at the other partitions. Although I don't suspect it in this case that is often the reason for duplicate entries.

I haven't used GC in a long time, and I don't recall how the proxified scripts work - I don't know how the script you posted was created. If needed I might install GC and see what the script looks like on my machine.

---

### Post by bogan on 2012-09-04
Hi!, **drs305**,

Thanks for the response, I had just finished re-reading all the Posts in this thread, and had just about concluded the only course was to remove Grub Customizer from all the partitions, rename the GC proxy files and revert the 'proxifiedScripts' to their original status in grub.d.

Then to remove and reinstall grub-pc and start again from scratch.

In those earlier Posts, I notice that **2CV67**, who reported duplicate scripts in his Grub menu - Posts #319>#326 - had previously Posted - #204>#207, back in Jan 20th 2012 - duplicate entries almost exactly the same as my stage 2 problem, except that his include some recovery entries, whereas mine had none. His problems - according to the later Posts, to which Daniel Ricter also responded, do not seem to have been resolved.

I put "stage 2" because my problem has spread to all the partitions; using your: ```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
``` in each of the OS's shows duplicate entries for sde8, but no recovery entry. For example from sde11:```
 0    Ubuntu, with 12.04.1 LTS Linux 3.2.0-29-generic-pae (on /dev/sde11)
     1    Ubuntu, with 12.04.1 LTS Linux 3.2.0-29-generic-pae (recovery mode) (on /dev/sde11)
     2    Memory test (memtest86+)
     3    Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)
     4    Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)
     5    Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)
     6    Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)
     7    Windows Vista (loader) (on /dev/sde1)
     8    Ubuntu, with 11.10 Linux 3.0.0-24-generic ( on USB) (on /dev/sda2)
     9    Ubuntu, with 11.10 Linux 3.0.0-24-generic (recovery mode) ( on USB) (on /dev/sda2)
    10    Ubuntu, with 10.04 LTS Linux 2.6.32-42-generic (on sda6) (on /dev/sde6)
    11    Ubuntu, with 10.04 Linux 2.6.32-42-generic (recovery mode) (on sda6) (on /dev/sde6)
    12    Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)
alan@alan-MS-7318:~$ # There were another 7 sde8 entries, but I unticked them in GC.
```10.04 on sde6 has a single false sde8 entry & no recovery, 12.04.1 on sde8 has the correct entries for itself, including recovery, but four false entries for sde11, whilst 10.10 on sda2/USB has five false entries for sde8 but no recovery entry.

Regarding your comment about being sure there is only one executable script in grub.d, the only file that appears to have false entries is 30-os-prober_proxy, which I posted in #328 - if you can call that an executable script?? { that is in sde11, in sde8 it is similar but is 20-os-prober_proxy and the first file it lists is os-prober~1}

But the first line of that file: > '/etc/grub.d/proxifiedScripts/os-prober' | /etc/grub.d/bin/grubcfg_proxy "+* Presumably means it uses those scripts which do address other OS's. { the second is not accessible to me, so I have no idea what it does. Though the syntax of that line looks a bit suspect to me, with "+* at the end.} 

I hope I am not overwhelming you with too much info.

Chao!, **bogan**.

---

### Post by drs305 on 2012-09-04
bogan,

I had another thought regarding sde8. Perhaps the multiple entries your current menu is 'harvesting' are the older sde8 kernels which have been moved to the submenu of sde8. So although it shows just one item repeated several times, perhaps it is generating multiple kernel version entries but listing them all the same way. I would expect that a clean install of 12.04.1 wouldn't have many kernel versions, but upgrades from 12.04 would most likely have quite a few older kernels accumulated on the system.

There are a couple of ways you could check. One would be to boot into that OS and remove all additional kernels and update-grub. Then return to your default OS and update-grub and see if it changes the menu.

You could also manually edit the sde8 grub.cfg, removing not only any extra kernels that might be in the main menu but also those listed in the 'submenu' section.

---

### Post by bogan on 2012-09-05
Hi!, **drs30**5,

Yeah, the same had occurred to me, but after clearing out all the old headers and images, with Ubuntu Tweak, from both 12.04 installs, the problem actually got worse, not better.

The only install that has several back versions still in it, is 10.04 in sde6, and they do not appear in any of the menus, having been unticked.

I do not know if this is relevant but booting the first three sde8 menu entries, successfully get to GUI after a text boot to a tty prompt, which only stays a few seconds, and after a black screen 20 secs, shows the greeter login screen.

The fourth hangs at a BusyBox/initramfs prompt, after a lot of messages saying /dev/sde8 does not exist & libsomething 3.2.0.29 can not be found.

Checking the menu entry scripts, the only difference is that the last line of the first three is: "initrd /initrd.img",  whereas the fourth is: "initrd /initrd.img.old".  { Edit: corrected from "/initrd.img~1" .

Update manager has announced a kernal update, so what I have done is to remove all the false entries, except the first, form the /boot/grub/grub.cfg files of both sde11 & sde8, but left all the other files unaltered, and not run update-grub: though of course the update will run it anyway.

We will see what we will see.

Chao & Thanks,** bogan.**

---

### Post by bogan on 2012-09-05
Hi!, drs305,

I am now more confused than ever.

The last few days I have had a spate of 'System Fault Detected' & 'Program XXX has stopped unexpectedly' messages, and I got several in the middle of Update Manager. configuring the kernal update Download in 12.04 on sde11. Finally UM crashed completely.

From Root I ran: ```
apt-get update
apt-get upgrade
apt-get dist-upgrade
dpkg --configure -a  # none of which seemed to do anything.
dpkg-reconfigure -a  # which took 12 minutes but showed nothing.
```I then rebooted without running either update-grub or Grub Customizer.

To my surprise the Boot menu showed 12.04 -30 & 12.04-29, both with recovery entries; but the four false sde8 entries were all back:  the /boot/grub/grub.cfg file also had the four false sde8 entries  back, Your code shows it correctly as it displays:```
alan@alan-MS-7318:~$ grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
     0    Ubuntu, with Linux 3.2.0-30-generic-pae
     1    Ubuntu, with Linux 3.2.0-30-generic-pae (recovery mode)
     2    Ubuntu, with 12.04.1 LTS Linux 3.2.0-29-generic-pae (on /dev/sde11)
     3    Ubuntu, with 12.04.1 LTS Linux 3.2.0-29-generic-pae (recovery mode) (on /dev/sde11)
     4    Memory test (memtest86+)
     5    Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)
     6    Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)
     7    Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)
     8    Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)
     9    Windows Vista (loader) (on /dev/sde1)
    10    Ubuntu, with 11.10 Linux 3.0.0-24-generic ( on USB) (on /dev/sda2)
    11    Ubuntu, with 11.10 Linux 3.0.0-24-generic (recovery mode) ( on USB) (on /dev/sda2)
    12    Ubuntu, with 10.04 LTS Linux 2.6.32-42-generic (on sda6) (on /dev/sde6)
    13    Ubuntu, with 10.04 Linux 2.6.32-42-generic (recovery mode) (on sda6) (on /dev/sde6)
    14    Ubuntu 12.04.1 LTS (12.04) (on /dev/sde8)
alan@alan-MS-7318:~$ 

```Update Manager is now running again and now claims there are no updates, and I have to decide whether to update sde8 as well. 
Edit: It would seem that deleting menu entries from the grub.cfg file has no effect.

{ *There was an error in my last post I have edited: the second initrd entry was: "initrd.img.old", not: "initrd-img~1"*}.
Chao!, **bogan.**

---

### Post by drs305 on 2012-09-05
> **bogan said:**
> 
We will see what we will see.

Chao & Thanks,** bogan.**

Yes, let us know. I plan on closing this thread once you get this figured out as I haven't followed the developments of GC sufficiently to offer current advice. Hopefully we can get this figured out.

I think if the menu edit didn't help I would probably purge everything GC related, including all the GC files/folders in /etc/grub.d. Then see what Grub does with menus on it's own.

---

### Post by bogan on 2012-09-05
Hi!, **drs30**5,

YES, BUT!

I updated the 12.04 kernal on sde8 successfully and this got rid of the false sde11 entries, substituting the correct ones. So I then booted sde11 and ran 'update-grub' - not GC - and that - according to your code - has got rid of the false sde8 entries and put in the correct ones.:lolflag:

It remains to be seen what happens when I reboot a few times, and examine the relevant files. For the time being at least I do not intend to run Grub Customizer. 

I will let you know how it goes, but I have other urgent commitments  *I can not delay.*. Many Thanks for all your Support and Help.

I hope " closing this Thread " only means one will not be able to Post to it, and that what is a very valuable resource to many forum visitors will still be available as a 'How To GC'.:guitar:

Chao!, bogan.

---

### Post by drs305 on 2012-09-05
Due to my pending semi-retirement and lack of recent experience with Grub Customizer, I am closing this thread. It will remain in the archives until such time as the forum admin folks decide to purge the tutorial section of out-of-date threads. If you have a GC question please start a new thread. Link to this thread if desired.

I encourage either the Grub Customizer developer or someone with recent in-depth experience to create a wiki for this app in the Ubuntu documentation site. Anyone doing so is more than welcome to use all or part of my posts in this thread to help create such a page.

Many thanks to Daniel Richter for seeing the need for such an application and providing one to the Ubuntu community.

Happy Ubuntu-ing !

Thread closed.

---

