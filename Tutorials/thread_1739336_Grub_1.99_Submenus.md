---
title: "Grub 1.99 Submenus"
date: 2011-04-25
forum: Tutorials
---

### Post by drs305 on 2011-04-25
EDIT: This page has migrated to the Ubuntu Community Documentation Site and may not be updated. Please refer to the following location for up-to-date information on this subject.
[https://help.ubuntu.com/community/Grub2/Submenus]("https://help.ubuntu.com/community/Grub2/Submenus")


Note: Most users can probably go directly to the **Example** to be able to figure out what the designation for a specific menuentry should be. You've been warned...

One of the changes an Ubuntu user will eventually notice is an entry on the Grub menu called "*Previous Linux versions*". The entry will appear directly below the current kernel (and recovery option if enabled) . It is a new feature of Grub 1.99. I mention Ubuntu users because for now other distros are not turning on the submenu feature by default. Welcome to the world of Grub submenus!

**[COLOR="Navy"]Will It Affect Me?[/COLOR]**
Sooner or later, yes. The *submenu* feature is automatically activated only for the main Ubuntu partition entries; it is only visible when there are two or more kernels present in the boot folder. Submenus are not created for kernels on other partitions or for non-Linux operating systems such as Windows. An Ubuntu user who wishes to always use the latest kernel as the default need take no action, and will always see only the latest kernel on the main Grub screen. 

A user who wishes to always boot a specific kernel, or any older kernel,  will need to understand the submenu feature in order to properly make changes to the Grub configuration files. I expect the third party GUI app, Grub Customizer, will incorporate this feature at some point and I will note it here.

The submenu feature can also be employed by users who wish to create multilevel custom menus, and much of this post details the 'mechanics' of how to identify the kernel when it resides in a submenu.

**[COLOR="Navy"]Why the Change?[/COLOR]**
In Grub legacy and earlier versions of Grub 2, when a new kernel was introduced it was added to the top of the menu. Previous kernels were moved down but still displayed. Over time, without user intervention, the menu could become quite large as kernels and recovery entries grew.

Users had to deal with the growing list of kernels on their own. Hiding the entries with third party apps such as Startup Manager and Grub Customizer was one method; another option was to remove older kernels via Synaptic, Ubuntu Tweak or the terminal. [_Guides_]("http://ubuntuforums.org/showthread.php?t=1587462") were written to help users with this issue.

**[COLOR="Navy"]The Grub 1.99 Solution[/COLOR]**
Grub 1.99 addresses this issue by automatically placing older kernels in the main OS into a submenu named "*Previous Linux versions*". The main menu will display only one kernel from the controlling Ubuntu system, plus its recovery mode if enabled.

**[COLOR="Navy"]Booting Submenu Entries[/COLOR]**

[LIST]
[*]**Selecting a Submenu Entry Manually**

At the GRUB menu during boot the user must select "Previous Linux versions" to access the older kernels. This will open the submenu and the user may choose an older kernel. Clicking the submenu title halts the timer if automatic booting was enabled.

If an entry in the submenu is set as the default entry, the "Previous Linux versions" title is highlighted until the user intervenes or the system boots. The actual entry to be booted will not be displayed unless the user clicks the "Previous Linux versions", at which time the default entry in the submenu will be highlighted.


[*]**Setting the *GRUB_DEFAULT* option in */etc/default/grub***

**[COLOR="Navy"]Setting a Main Page Entry as the Default in */etc/default/grub*[/COLOR]**


[LIST]
[*]As in previous Grub 2 versions, the default boot option is set by the *GRUB_DEFAULT=* setting of the */etc/default/grub* file.


[*]Entries displayed on the main menu can be designated by number or title as with earlier versions of Grub 2.


[LIST]
[*]GRUB_DEFAULT=0
[*]	GRUB_DEFAULT="Ubuntu, with Linux 2.6.38-8-generic"
[/LIST]
[/LIST]

**[COLOR="Navy"]Setting a Submenu Entry as the Default in */etc/default/grub*[/COLOR]**


[LIST]
[*]A submenu entry is composed of two numeric or alphanumeric values separated by a **>** symbol:  "[COLOR="DarkRed"]Submenu Title or Number[/COLOR]**>**[COLOR="Green"]Submenu Menuentry Title or Number[/COLOR]" 


[LIST]


[*]The first part consists of the menuentry number or title;  

[*]The second part, the separator, is a **>** symbol, with no spaces on either side.

[*]The third part, following the **>** symbol, consists of a menuentry title or a number determined by its order within its submenu (counting from 0).

[*]The entire entry should be enclosed by only one set of quotes.
[/LIST]


[*]Titles are easier to use but numbers are also acceptable for either or both the first and second values.


[LIST]
[*]GRUB_DEFAULT="Previous Linux versions>Ubuntu, with Linux 2.6.38-7-generic"
[*]GRUB_DEFAULT="Previous Linux versions>0"
[*]GRUB_DEFAULT="2>0"
[*]GRUB_DEFAULT="2>Ubuntu, with Linux 2.6.38-7-generic"
[*]All of these indicate the first menuentry in the first submenu (with a kernel and recovery mode visible in the main menu).
[/LIST]

If you are going to use numerals in either or both sides of the GRUB_DEFAULT setting, go to the 'Example' below; trust me, it's easier to understand than the following description. 


[*]When determining the first numeral, count each 'menuentry' from the top of grub.cfg (or the top of the Grub menu screen), and include the  associated 'submenu' entry. To determine the second number, count only the menunetries within the respective submenu.


[LIST]
[*]Menuentry counting always starts at zero in either the main or submenu section.
[*]The 'submenu' title counts as a menuentry in the main section.
[*]Menuentries within a submenu do not count for determining the first number of the GRUB_DEFAULT designation. (Only parent level menuentries and submenu titles are counted.)
[*]The second number in the GRUB_DEFAULT designation includes only items within the respective submenu.
[/LIST]
[/LIST]


**[COLOR="DarkRed"]Counting rules to help retain your sanity if you just don't get it and still haven't looked at the Example below:[/COLOR]**


[LIST]
[*]All counting in each section starts at 0.
[*]Reboot and press a key to stop the countdown. Hold down the SHIFT key if the menu doesn't appear at all.
[*]Start counting menu items on the main GRUB menu.
[*]Count down to, and include, the desired entry or submenu title. Write down the number.
[*]If you have to enter a submenu to view the desired entry, count down from the top of the second screen to the item you want to boot. Start counting from 0. Write it down.
[*]Reread this section as necessary or stick to titles as the values.  
[/LIST]

**Example:** 
[LIST]


**Black** numbers are for items seen on the main menu.
[COLOR="Red"]Red[/COLOR] numbers are for items seen only in a submenu.
These numbers are for illustrative purposes and do not appear in the menus or scripts. They are the numbers which would be placed in the *GRUB_DEFAULT=* value in the */etc/default/grub* file.

**0** menuentry *Ubuntu, with Linux 2.6.38-8-generic* 
**1** menuentry *Ubuntu, with Linux 2.6.38-8-generic (Recovery)* 
**2** submenu *[I]Previous Linux versions*[/I]  # This is the first submenu 
[COLOR="Red"]2>0[/COLOR] menuentry *Ubuntu, with Linux 2.6.38-7-generic *
[COLOR="Red"]2>1[/COLOR] menuentry *Ubuntu, with Linux 2.6.38-7-generic (Recovery)* 
[COLOR="Red"]2>2[/COLOR] menuentry *Ubuntu, with Linux 2.6.38-5-generic* 
[COLOR="Red"]2>3[/COLOR] menuentry *Ubuntu, with Linux 2.6.38-5-generic (Recovery)* 
**3** menuentry *[I]Memtest*[/I] 
**4** menuentry *Windows Vista* 
**5** submenu *[I]My ISOs*[/I] # This is the second submenu 
[COLOR="Red"]5>0[/COLOR] menuentry *Natty.iso* 
[COLOR="Red"]5>1[/COLOR] menuentry *Maverick.iso* 
[COLOR="Red"]5>2[/COLOR] menuentry *SystemRescue.iso* 

The *GRUB_DEFAULT=* setting in the */etc/default/grub* file can be either the **black** number or the [COLOR="Red"]red number combination[/COLOR].
[/LIST]#-o
[/LIST]

**[COLOR="Navy"]What Happens When a New Kernel Is Introduced and I Was Using the Most Recent One? *[/COLOR]**

[LIST]
[*]The new kernel menuentry is displayed on the main Grub menu.
[*]The current kernel (and recovery option if enabled) are moved to the top of the "Previous Linux versions" submenu.
[LIST]
[*]If the "Previous Linux versions" submenu does not exist, it is created.
[/LIST]
[*]Other submenu entries are moved lower to accommodate the new submenu entry.
[*]The default is changed to the new kernel if GRUB_DEFAULT=0 or the current default moves into the submenu.
[LIST]
[*]This happens even if the 'title' mode is used in the "GRUB_DEFAULT=" setting. 
[*]This action is not optimum but was determined to allow the most flexibility by the GRUB development team to allow for other capabilities.
[/LIST]
[/LIST]

**[COLOR="Navy"]What Happens If the *GRUB_DEFAULT* Setting Is Wrong?[/COLOR]**

Grub will attempt to boot one additional entry. In most of my experiments it's been the newest kernel.


**[COLOR="Navy"]What Happens When ...[/COLOR]**

There are too many scenarios to cover, but these principals apply in most if not all situations and should provide the basis to help determine the likely outcome.

[LIST]
[*]Except for GRUB package operations, the "GRUB_DEFAULT=" setting in the */etc/default/grub* file never changes automatically. If a kernel is added or removed, the DEFAULT setting does not adjust and is largely responsible for the following results.

[*]If a kernel is introduced or removed and the menuentry or submenu entry is designated exclusively by number(s), a different kernel will become the default.

[*]If a menuentry or submenu is defined by a title:
[LIST]
[*]If the entry remains in its current screen (either remains in the main menu or remains in the submenu), the same kernel will continue to be the default.
[*]If the menuentry (in the main menu or submenu) moves out of its current screen, the DEFAULT will change.
[*]For a submenu entry to remain the DEFAULT, both conditions must remain unchanged.
[/LIST]
When a failure occurs and GRUB is unable to find the DEFAULT entry, it will attempt to boot a different kernel.
[/LIST]

**[COLOR="Navy"]I Have to Boot A Specific Kernel! What Should I Do?[/COLOR]**

You have several options. 
[LIST]


[*]Create a new custom menu. You can design a simple custom menu which never changes unless you manually edit it. If you name it */etc/grub.d/06_custom* it will be at the top of your GRUB menu and it's position will not change (nor be subject to submenu creation).

[*]Turn off the *submenu* feature as described later, and use the title option to set *DEFAULT* in the */etc/default/grub* file.[*]'Lock' and 'hold' your current kernel so that it isn't updated. I'd lock it with Synaptic or another package manager and place a 'hold' via the command line if it was really important to me.
[_https://help.ubuntu.com/community/PinningHowto_]("https://help.ubuntu.com/community/PinningHowto")
[/LIST]


**[COLOR="Navy"]Will My Other Ubuntu Partition Submenus Be Imported?[/COLOR]**
No. For users with multiple Ubuntu installations, Grub will look for other grub.cfg and menu.lst files first. It will import the individual entries but not the submenu structure. If you want your custom menus which include submenus, make sure they, or a link, are in the */etc/grub.d/* folder.


**[COLOR="Navy"]What Else Can I Do With Submenus?[/COLOR]**

One thing I've found useful is that I can combine multiple custom menus into one file. Previously I created a separate custom menu for each category I wanted (ISOs, Other Operating Systems, etc). Now I can place them all in a single custom file, which makes maintaining the entries a bit easier for me.

Here is the format for a submenu and an enclosed menuentry. The submenu contains it's own { }.

> 
[COLOR="Blue"]**submenu "My ISOs" {**[/COLOR]
menuentry "Natty_test.iso
isofile=natty-desktop-amd64.iso		
loopback loop (hd1,6)/iso/$isofile		
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
menuentry 'ISO SystemRescue   sdb5-vm'                     {
isofile=systemrescuecd-x86-2.0.1.iso
loopback loop (hd1,5)/$isofile
linux (loop)/isolinux/rescue64 setkmap=us isoloop=/$isofile
initrd (loop)/isolinux/initram.igz
}
[COLOR="Blue"]**}**[/COLOR]



Provide your tips!


**[COLOR="Navy"]How Can I Turn Off Submenus?[/COLOR]**

Open */etc/grub.d/10_linux* as root:
```
gksu gedit +212 /etc/grub.d/10_linux
```
Near the bottom of the file, find the designated lines and place # symbols at the start of each line:

> **[COLOR="DarkRed"]#[/COLOR]**  if [ "$list" ] && ! $in_submenu; then
**[COLOR="DarkRed"]#[/COLOR]**    echo "submenu \"Previous Linux versions\" {"
**[COLOR="DarkRed"]#[/COLOR]**    in_submenu=:
**[COLOR="DarkRed"]#[/COLOR]**  fi

Run *update-grub* to update the GRUB menu.
```
sudo update-grub
```



**[COLOR="Navy"]Grub Customizer[/COLOR]**
It does not appear that Grub Customizer (see link in my signature line) correctly handles submenus. If the user wishes to use an older kernel, use the naming convention in this guide in the GRUB_DEFAULT entry in /etc/default/grub and leave the "default predefined" section blank in Grub Customizer. GC can be used once this is accomplished, or if the desired menuentry appears on the main Grub 2 menu and not in a submenu.



[COLOR="DarkRed"][B]
Links[/B][/COLOR]

[_[U]GNU GRUB MANUAL_[/U]]("http://www.gnu.org/software/grub/manual/grub.htm")
[Grub 1.99 Changes]("http://ubuntuforums.org/showthread.php?p=10720322")
[Grub 1.99 Drop-In Backgrounds & Fonts]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by axelfoley on 2012-09-23
FYI the above description where its suggests using the ordinal (0,1,2...etc) position in the main and submenu ...... has never worked for me when trying to boot kernels in the "Previous Linux versions" submenu.

numerical only seems to work in the main menu only.

Instead to get submenu's working I have to use the full ascii string e.g.;

vi /etc/default/grub
GRUB_DEFAULT="Previous Linux versions>Ubuntu, with Linux 3.2.0-26-generic"
update-grub

---

### Post by drs305 on 2012-09-23
Thanks for the input. The instructions were taken from the Grub manual for 1.99 and I just tried the numbering format on my Precise VM and it still works as it should. 

I have not tried either method yet on Grub 2.0 but will do some experimenting when I have some time.

---

### Post by drs305 on 2012-09-25
The numerical convention (e.g. "1>0") works for me in Grub 2.0 on my Precise desktop. Even so, I would recommend using the *title* method as it is IMO less prone to user-error during setup and updates.

---

