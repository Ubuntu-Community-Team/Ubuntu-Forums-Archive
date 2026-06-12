---
title: "Grub 2 Drop-In Backgrounds &amp; Font Selection"
date: 2011-04-25
forum: Tutorials
---

### Post by drs305 on 2011-04-25
This page has been migrated to the Ubuntu Community Documentation site. For the most up-to-date information, please visit:
[https://help.ubuntu.com/community/Grub2/Displays]("https://help.ubuntu.com/community/Grub2/Displays")

The above page is a sub-page of the main community documentation regarding [https://help.community/Grub2]("https://help.ubuntu.com/community/Grub2").

Thank you to all the users who posted in these threads and expanded our knowledge of Grub 2 since it's introduction.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?p=12073029](http://ubuntuforums.org/showthread.php?p=12073029)

**Support threads regarding the wiki and it's content should be created in a suitable forum.**

----

First, a disclaimer. Grub 1.99 RC1 will be distributed with Ubuntu 11.04, Natty Narwhal. Dropping a background image into */boot/grub* will not work with Grub 1.98 or earlier, but there are other methods discussed in this guide that will. All Grub 2 users can use this guide to help select font & background colors.

Users looking for information about themes will not find it in this thread. Sorry.

[SIZE=3]**[COLOR="Navy"]GRUB 1.99 Background Images[/COLOR]**[/SIZE]

Copy a .jpg, .png or .tga image to /boot/grub, update Grub, and you now have a Grub menu background. If you haven't previously set up an image or theme, it can be that simple! 

Ubuntu repositories provides a sampling of Grub 2 splashimages suitable for background use. The package is *grub2-splashimages*. Once installed, the images are stored in */usr/share/images/grub*

Note: If the image name includes spaces, the image is copied to a (hidden) file named  *.background_cache.** and an "unexpected operator"  message is generated while running 'update-grub'. The image will still appear during boot, with Grub2 using the file */boot/grub/.background_cache.**. Thanks to forum member *Anduu* for posting this behavior.

Besides the simplicity of activating a background, Grub 2 now should auto-detect video capabilities and provide what it considers the best resolution. It will stretch any image to fill the screen.  It's pretty easy to add a bit of eye candy.

**Procedure:**
[LIST=1]
[*]Copy any image (jpg, png or tga) to the /boot/grub folder.
[*]Run "sudo update-grub".
[*]Done. How easy was that?
[/LIST]

**Additional Info:**

Image Priority:
[LIST=1]
[*]*GRUB_BACKGROUND=</path/filename>* setting in */etc/default/grub*
[LIST]
[*]Available in updated versions of Grub 1.98
[*]Example: GRUB_BACKGROUND=/boot/grub/myimages/eyecandy.png
[/LIST]
[*]First image found in /boot/grub
[LIST]
[*]The first image found, in this order:  jpg, JPG, jpeg, JPEG, png, PNG, tga, TGA
[*]If multiple images of the same extension, alphanumerically.
[/LIST]
[*]Wallpaper designated in /usr/share/desktop-base/grub_backgorund.sh (if desktop-base installed)
[*]/usr/share/images/desktop-base/desktop-grub.png (if desktop-base is installed)
[*]Default theme (no image): Aubergine background, selected item black on light gray background)
[/LIST]

**Gotchas**
[LIST]
[*]Don't forget to run  "sudo update-grub"
[*]If you have multiple distros on your system, remember the change must be made to the controlling Grub
[*]Grub 1.99 RC  or later.
[*]Images should be RGB, i.e. non-indexed (in GIMP, Image > Mode) and jpeg images should be 8-bit.
[/LIST]

When the user specifies a custom background, the Grub developers decided to be conservative and specified a black/white font scheme. They were kind enough to include a comment about it in */etc/grub.d/05_debian_theme* but left it to the user to figure out how to deal with the font colors when using custom backgrounds. Font color selection is discussed in the next section.


[SIZE=3]**[COLOR="Navy"]Font Colors & Backgrounds[/COLOR]**[/SIZE]

First, keep in mind that Grub 2 considers *black* used as the second color entry as *transparent*. You will see the background image wherever *black* is the second entry (e.g. green/black = green text on transparent background).

[LIST]
[*]**[COLOR="DarkRed"]color1/color2[/COLOR]**

Two colors must be designated when assigning colors, separated by a **/**
I'll call them *color1* and *color2* in this guide.

According to the GNU GRUB manual, the colors can be designated as HTML-style (#000000), comma-separated RGB (128,255,255), and SVG 1.0 *lowercase* color names (midnightblue). To date, I have had success using the following designations:
> black blue brown cyan  dark-gray green light-cyan light-blue light-green light-gray light-magenta light-red magenta red  white yellow


[LIST]
[*]*color1* is the text color


[*]*color2* is the background color or transparency (black)
[LIST]
[*]*color2* must be 'black' for a background image to be visible. 
[*]'black' as *color2* is regarded as transparent.
[*]Any other color will hide all or part of any background image being used. 
[/LIST]
[/LIST]


[*]**[COLOR="DarkRed"]Menu Settings[/COLOR]**

There are two conditions (normal & highlight) and two locations (menu or unspecified) possible within the Grub menu: 


[LIST]
[*]**Conditions**


[LIST]
[*]Highlighted or selected text
[LIST]
[*]The selected line is highlighted fully across the entire line, producing a 'bar'.
[*]*color1* determines the font color. *color2* determines the bar color.
[/LIST]

[*]Non-highlighted or unselected text. 
[LIST]
[*]*color1* determines the font color. *color2* determines the background color or transparency of all non-highlighted areas.
[/LIST]
[/LIST]


[*]**Locations**


[LIST]
[*]menu_color_ : The area within the menu border.
[*]color_ : The area outside the menu borders. It will also control items within the menu border if *menu_color_* is not specified.
[/LIST]
[/LIST]


[SIZE=3]The following are the entries which will be added to ***/etc/grub.d/05_debian_theme*** in the next section.[/SIZE]


[LIST]
[*]**Selected Entry within the Grub Menu Border (one line) is controlled by:**
[LIST]
[*]```
menu_color_highlight=color1/color2
```
[*]Colors of selected text & background within the Grub2 menu border.
[*]Defaults to *color_highlight* settings if not specified.
[/LIST]


[*]**Non-selected entries within the Grub Menu Border (the rest) are controlled by:**
[LIST]
[*]```
menu_color_normal=color1/color2
```
[*]Colors of non-selected text & background within the Grub2 menu border.
[*]Defaults to *color_normal* settings if not specified.
[/LIST]


[*]**Highlighted Text Outside the Grub Border (one line) is controlled by:**
[LIST]
[*]```
color_highlight=color1/color2
```
[*]If there is no *menu_color_highlight* entry this setting is used within the Grub2 menu border for the selected entry line.
[/LIST]


[*]**Text/Colors Outside the Grub Border are controlled by:**
[LIST]
[*]```
color_normal=color1/color2
```
[*]Colors of text & background outside the Grub2 menu border.
[*]If there is no *menu_color_normal* entry this setting is used within the Grub2 menu border for the non-selected areas.
[/LIST]
[/LIST]

**[COLOR="DarkRed"]An Example[/COLOR]**
[ATTACH]190038[/ATTACH]

The background image was a black screen with an Ubuntu logo. The image is visible within the menu border since both "menu_color..." entries have black as the second color. The image is not visible outside the menu box since the "color_normal" *color2* is not 'black' (transparent).

> menu_color_normal=white/black
menu_color_highlight=yellow/black
color_normal=green/red
color_highlight=black/white    (Not illustrated)

[/LIST]


**[COLOR="Navy"]Editing Font Colors[/COLOR]**
[LIST]
As root, open */etc/grub.d/05_debian_theme* for editing. The sections to be edited is currently at approximately line 98 (line 105 in Grub 1.99):
```
gksu gedit +98 /etc/grub.d/05_debian_theme
```
[LIST]
[*]Add lines 2 & 3, using the colors you desire, in two places.
> 
echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
[COLOR="DarkRed"]echo "  set color_normal=light-gray/black"
echo "  set color_highlight=green/black"
[/COLOR]
if [ -n "${2}" ]; then

> 
	if [ -z "${2}" ] && [ -z "${3}" ]; then
[COLOR="DarkRed"]echo "  set color_normal=light-gray/black"
echo "  set color_highlight=green/black"
[/COLOR]
		echo "  true"
	fi

[/LIST]
[*]Save the file, then update Grub.
```
sudo update-grub
```
[/LIST]

[SIZE=3]**[COLOR="Navy"]Real-Time Testing Graphics & Font Colors at the Grub2 menu[/COLOR]**[/SIZE]

Font & background changes take effect immediately when editing the Grub 2 menu from the grub prompt, so immediate feedback while testing color combinations is possible.


[LIST=1]
[*]At the Grub2 menu (hold SHIFT during boot if it doesn't display. But hey, if it doesn't display why are you wasting time with a grub background ;-) ).


[*]Press 'c' to get the grub prompt.


[LIST]
[*]**Change the background image:**

[*]```
background_image <path/filename>
```
[LIST]
[*]Example: background_image /boot/grub/natty.png  # Assumes prefix is set to (hdX,Y)/boot/grub
[/LIST]


[*]**Change the font & background colors:**
[*]```
set <selection>=color1/color2
```
[LIST]
[*]Example: set menu_color_highlight=yellow/blue
[/LIST]
[/LIST]


[*]To see all current settings type *set* at the grub prompt.


[*]Changes to *color_normal* are seen immediately at the grub prompt. To see the menu changes press ESC to return to the Grub2 menu.
[/LIST]


**[COLOR="DarkRed"]Don't forget[/COLOR]** 

[LIST]
[*]You are just testing the settings at the Grub prompt/menu. Once you have settled on your color combinations, boot, make the changes to */etc/grub.d/05_debian_theme*, save the file.
[*]*update-grub* for the changes to be incorporated in *grub.cfg*.
[/LIST]

This guide is a compilation of several threads/posts originally in the Natty Testing Forum.


**[COLOR="Navy"]Other Grub 1.99 Links:[/COLOR]**
[Grub 1.99 Changes]("http://ubuntuforums.org/showthread.php?p=10720322#post10720322")
[_Grub 1.99 Submenus_]("http://ubuntuforums.org/showthread.php?t=1739336")

---

### Post by drs305 on 2011-04-25
> **drs305 said:**
> First, a disclaimer. Grub 1.99 RC1 will be distributed with Ubuntu 11.04, Natty Narwhal. Dropping a background image into */boot/grub* will not work with Grub 1.98 or earlier, but there are other methods discussed in this guide that will. All Grub 2 users can use this guide to help select font & background colors.

Users looking for information about themes will not find it in this thread. Sorry.

[SIZE=3]**[COLOR="Navy"]GRUB 1.99 Background Images[/COLOR]**[/SIZE]

Copy a .jpg, .png or .tga image to /boot/grub, update Grub, and you now have a Grub menu background. If you haven't previously set up an image or theme, it can be that simple! 

Ubuntu repositories provides a sampling of Grub 2 splashimages suitable for background use. The package is *grub2-splashimages*. Once installed, the images are stored in */usr/share/images/grub*

Note: If the image name includes spaces, the image is copied to a (hidden) file named  *.background_cache.** and an "unexpected operator"  message is generated while running 'update-grub'. The image will still appear during boot, with Grub2 using the file */boot/grub/.background_cache.**. Thanks to forum member *Anduu* for posting this behavior.

Besides the simplicity of activating a background, Grub 2 now should auto-detect video capabilities and provide what it considers the best resolution. It will stretch any image to fill the screen.  It's pretty easy to add a bit of eye candy.

**Procedure:**
[LIST=1]
[*]Copy any image (jpg, png or tga) to the /boot/grub folder.
[*]Run "sudo update-grub".
[*]Done. How easy was that?
[/LIST]

**Additional Info:**

Image Priority:
[LIST=1]
[*]*GRUB_BACKGROUND=</path/filename>* setting in */etc/default/grub*
[LIST]
[*]Available in updated versions of Grub 1.98
[*]Example: GRUB_BACKGROUND=/boot/grub/myimages/eyecandy.png
[/LIST]
[*]First image found in /boot/grub
[LIST]
[*]The first image found, in this order:  jpg, JPG, jpeg, JPEG, png, PNG, tga, TGA
[*]If multiple images of the same extension, alphanumerically.
[/LIST]
[*]Wallpaper designated in /usr/share/desktop-base/grub_backgorund.sh (if desktop-base installed)
[*]/usr/share/images/desktop-base/desktop-grub.png (if desktop-base is installed)
[*]Default theme (no image): Aubergine background, selected item black on light gray background)
[/LIST]

**Gotchas**
[LIST]
[*]Don't forget to run  "sudo update-grub"
[*]If you have multiple distros on your system, remember the change must be made to the controlling Grub
[*]Grub 1.99 RC  or later.
[*]Images should be RGB, i.e. non-indexed (in GIMP, Image > Mode) and jpeg images should be 8-bit.
[/LIST]

When the user specifies a custom background, the Grub developers decided to be conservative and specified a black/white font scheme. They were kind enough to include a comment about it in */etc/grub.d/05_debian_theme* but left it to the user to figure out how to deal with the font colors when using custom backgrounds. Font color selection is discussed in the next section.


[SIZE=3]**[COLOR="Navy"]Font Colors & Backgrounds[/COLOR]**[/SIZE]

First, keep in mind that Grub 2 considers *black* used as the second color entry as *transparent*. You will see the background image wherever *black* is the second entry (e.g. green/black = green text on transparent background).

[LIST]
[*]**[COLOR="DarkRed"]color1/color2[/COLOR]**

Two colors must be designated when assigning colors, separated by a **/**
I'll call them *color1* and *color2* in this guide.

The colors can be designated as HTML-style (#000000), comma-separated RGB (128,255,255), and SVG 1.0 color names (MidnightBlue)


[LIST]
[*]*color1* is the text color


[*]*color2* is the background color or transparency (black)
[LIST]
[*]*color2* must be 'black' for a background image to be visible. 
[*]'black' as *color2* is regarded as transparent.
[*]Any other color will hide all or part of any background image being used. 
[/LIST]
[/LIST]


[*]**[COLOR="DarkRed"]Menu Settings[/COLOR]**

There are two conditions (normal & highlight) and two locations (menu or unspecified) possible within the Grub menu: 


[LIST]
[*]**Conditions**


[LIST]
[*]Highlighted or selected text
[LIST]
[*]The selected line is highlighted fully across the entire line, producing a 'bar'.
[*]*color1* determines the font color. *color2* determines the bar color.
[/LIST]

[*]Non-highlighted or unselected text. 
[LIST]
[*]*color1* determines the font color. *color2* determines the background color or transparency of all non-highlighted areas.
[/LIST]
[/LIST]


[*]**Locations**


[LIST]
[*]menu_color_ : The area within the menu border.
[*]color_ : The area outside the menu borders. It will also control items within the menu border if *menu_color_* is not specified.
[/LIST]
[/LIST]


The following are the entries which will be added to */etc/grub.d/05_debian_theme* in the next section.


[LIST]
[*]**Selected Entry within the Grub Menu Border (one line) is controlled by:**
[LIST]
[*]```
menu_color_highlight=color1/color2
```
[*]Colors of selected text & background within the Grub2 menu border.
[*]Defaults to *color_highlight* settings if not specified.
[/LIST]


[*]**Non-selected entries within the Grub Menu Border (the rest) are controlled by:**
[LIST]
[*]```
menu_color_normal=color1/color2
```
[*]Colors of non-selected text & background within the Grub2 menu border.
[*]Defaults to *color_normal* settings if not specified.
[/LIST]


[*]**Highlighted Text Outside the Grub Border (one line) is controlled by:**
[LIST]
[*]```
color_highlight=color1/color2
```
[*]If there is no *menu_color_highlight* entry this setting is used within the Grub2 menu border for the selected entry line.
[/LIST]


[*]**Text/Colors Outside the Grub Border are controlled by:**
[LIST]
[*]```
color_normal=color1/color2
```
[*]Colors of text & background outside the Grub2 menu border.
[*]If there is no *menu_color_normal* entry this setting is used within the Grub2 menu border for the non-selected areas.
[/LIST]
[/LIST]

**[COLOR="DarkRed"]An Example[/COLOR]**
[ATTACH]190038[/ATTACH]

The background image was a black screen with an Ubuntu logo. The image is visible within the menu border since both "menu_color..." entries have black as the second color. The image is not visible outside the menu box since the "color_normal" *color2* is not 'black' (transparent).


[/LIST]


**[COLOR="Navy"]Editing Font Colors[/COLOR]**
[LIST]
As root, open */etc/grub.d/05_debian_theme* for editing. The section to be edited is currently at approximately line 98:
```
gksu gedit +98 /etc/grub.d/05_debian_theme
```
[LIST]
[*]Add lines 2 & 3, using the colors you desire.

[/LIST]
[*]Save the file, then update Grub.
```
sudo update-grub
```
[/LIST]

[SIZE=3]**[COLOR="Navy"]Real-Time Testing Graphics & Font Colors at the Grub2 menu[/COLOR]**[/SIZE]

Font & background changes take effect immediately when editing the Grub 2 menu from the grub prompt, so immediate feedback while testing color combinations is possible.


[LIST=1]
[*]At the Grub2 menu (hold SHIFT during boot if it doesn't display. But hey, if it doesn't display why are you wasting time with a grub background ;-) ).


[*]Press 'c' to get the grub prompt.


[LIST]
[*]**Change the background image:**

[*]```
background_image <path/filename>
```
[LIST]
[*]Example: background_image /boot/grub/natty.png  # Assumes prefix is set to (hdX,Y)/boot/grub
[/LIST]


[*]**Change the font & background colors:**
[*]```
set <selection>=color1/color2
```
[LIST]
[*]Example: set menu_color_highlight=yellow/blue
[/LIST]
[/LIST]


[*]To see all current settings type *set* at the grub prompt.


[*]Changes to *color_normal* are seen immediately at the grub prompt. To see the menu changes press ESC to return to the Grub2 menu.
[/LIST]


**[COLOR="DarkRed"]Don't forget[/COLOR]** 

[LIST]
[*]You are just testing the settings at the Grub prompt/menu. Once you have settled on your color combinations, boot, make the changes to */etc/grub.d/05_debian_theme*, save the file.
[*]*update-grub* for the changes to be incorporated in *grub.cfg*.
[/LIST]

This guide is a compilation of several threads/posts originally in the Natty Testing Forum.

**[COLOR="Navy"]Other Grub 1.99 Links:[/COLOR]**
[_Grub 1.99 Submenus_]("http://ubuntuforums.org/showthread.php?t=1739336")

---

### Post by Pjotr123 on 2011-05-20
Well, it appears that the devs have succeeded in making this operation both easier and more difficult at the same time. Without communicating the change to us common users, as usual. :-(

Firstly, thanks for this guide. :)
Secondly: how can I add a colour change of the menu font, to 05_debian_theme? In other words, how can I specify color1/color2? Which code lines do I add, and where do I add them?

---

### Post by drs305 on 2011-05-21
> **Pjotr123 said:**
> Firstly, thanks for this guide. :)
Secondly: how can I add a colour change of the menu font, to 05_debian_theme? In other words, how can I specify color1/color2? Which code lines do I add, and where do I add them?

First. you are welcome. 

Secondly, I just about jumped when I started looking in the first post. It's there, but even the author (that would be me ;-) ) had to look twice. I'll make the text stand out, but the operative line is (emphasis added):

> 
The following are the entries which will be added to **/etc/grub.d/05_debian_theme** in the next section.

Here is a link that explains some of the major changes for Grub 1.99, and it includes a link to the developer's message detailing all the changes. I've only highlighted the major ones noticeable by a normal user; many of the changes expand the filesystems with which Grub 1.99 will work and do things behind the scene.
[Grub 1.99 Changes]("http://ubuntuforums.org/showthread.php?p=10720322#post10720322")

---

### Post by Pjotr123 on 2011-05-21
Thanks a lot! That worked just fine (see the attached picture).

A tip: if you would add to your excellent guide that the font colour entries have to be applied in "# Step #7" in 05_debian_theme, somewhere in the middle of that text file, then this would make it even easier.

Enjoy your Saturday (beautiful sunny day over here in Noord-Brabant, I'm off on my bicycle in half an hour, to make a trip through the woods). :)

Regards, Pjotr.

---

### Post by dmalloch on 2011-07-27
Good morning!

Just getting into an old thread.

I am having a slight problem with my changes to the Grub menu.  I have tried putting my background image directly into the /boot/grub folder, or as a GRUB_BACKGROUND=</path/filename> setting in /etc/default/grub (not at the same time).  Both ways work perfectly.  The problem comes when I try to modify the menu colours in the 05_debian_theme folder.  My modified colours are not used and I am left with the default ones.  If I remove the background image then my modified colours are used.  Is there something  else I should do?

Dave

---

### Post by drs305 on 2011-07-27
> **dmalloch said:**
> I am having a slight problem with my changes to the Grub menu.  I have tried putting my background image directly into the /boot/grub folder, or as a GRUB_BACKGROUND=</path/filename> setting in /etc/default/grub (not at the same time).  Both ways work perfectly.  The problem comes when I try to modify the menu colours in the 05_debian_theme folder.  My modified colours are not used and I am left with the default ones.  If I remove the background image then my modified colours are used.  Is there something  else I should do?

Dave

You are probably having the problem because the grub menu is using a different part of a conditional statement when it finds an image. If you look at /boot/grub/grub.cfg, there is a section that initially might look like
```
if background_image /boot/grub/drs.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray

```
If that is what your file looks like, you have to edit 05_debian_theme to include some instructions *within* the "if background_image" section and before the *else* section.

Take a look at the "Editing font colors" in the first post to see the extra lines which must be added to 05....

---

### Post by dmalloch on 2011-07-27
Thanks very much, that did the trick.  I should have paid closer attention to your excellent explanation.

---

### Post by Chakoo on 2011-10-29
Not working...

I put an image in /boot/grub/ and ran update-grub. When I restarted, the background was black instead of the usual aubergine.

When I enter into console mode in grub and try to set the image using the [ background_image <path/filename> ] method it gives me "Error: Unsupported Bitmap Format."

Wasn't this supposed to be simple?

Shadi

---

### Post by drs305 on 2011-10-29
> **Chakoo said:**
> Not working...

I put an image in /boot/grub/ and ran update-grub. When I restarted, the background was black instead of the usual aubergine.

When I enter into console mode in grub and try to set the image using the [ background_image <path/filename> ] method it gives me "Error: Unsupported Bitmap Format."

Wasn't this supposed to be simple?

Shadi

Looking at the Grub 1.99 manual, it appears that bitmap images are no longer supported for background images. I will update the Grub 2 guides dealing with this.

Attached is a PNG file which works.

---

### Post by drs305 on 2011-10-29
> **Chakoo said:**
> Not working...

I put an image in /boot/grub/ and ran update-grub. When I restarted, the background was black instead of the usual aubergine.

When I enter into console mode in grub and try to set the image using the [ background_image <path/filename> ] method it gives me "Error: Unsupported Bitmap Format."

Wasn't this supposed to be simple?

Shadi

Looking at the Grub 1.99 manual,bitmap images are not supported for background images. Use a jpg, tga or png image.

Attached is a PNG file which works.

---

### Post by Chakoo on 2011-10-29
I didn't even use a bitmap image... I was trying a JPG image that I made myself, and then I tried one from the grub2-splashimages and still didn't work.

Plus when I removed them all and ran update-grub, the background was still black not the ubuntu purple.

---

### Post by Chakoo on 2011-10-29
Also your image didn't work... (thanks for trying) And I'm using Oneiric not Natty (but I can't fix my information 'cause i have less than 50 posts -_-) Don't know if that helps.

Shadi

---

### Post by drs305 on 2011-10-29
> **Chakoo said:**
> Also your image didn't work... (thanks for trying) And I'm using Oneiric not Natty (but I can't fix my information 'cause i have less than 50 posts -_-) Don't know if that helps.

Shadi

If you run the boot info script and post the contents of RESULTS.txt I can take a look at grub.cfg. Make sure you have it set up to try to use whatever your image is. You can get to the script page via the 'BIS' link in my signature line or you can install '[_Boot-Repair_]("https://help.ubuntu.com/community/Boot-Repair")', which contains the script.

When you post again, please include whether the entire screen was black or just the middle section where you would expect the image to be.

---

### Post by Chakoo on 2011-10-29
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   419,432,447   419,430,400  83 Linux
/dev/sda2         419,432,448   613,481,582   194,049,135   7 NTFS / exFAT / HPFS
/dev/sda3         613,482,494   625,141,759    11,659,266   5 Extended
/dev/sda5         613,482,496   625,141,759    11,659,264  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        59312ec6-a40d-4168-a0f2-b80c7be247eb   ext2       
/dev/sda2        4B84C43146DE0326                       ntfs       Windows
/dev/sda5        38bf76e9-b849-4449-a5fe-29b9654a0166   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext2       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set=root 59312ec6-a40d-4168-a0f2-b80c7be247eb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 59312ec6-a40d-4168-a0f2-b80c7be247eb
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 59312ec6-a40d-4168-a0f2-b80c7be247eb
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=59312ec6-a40d-4168-a0f2-b80c7be247eb ro quiet splash acpi_backlight=vendor  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 59312ec6-a40d-4168-a0f2-b80c7be247eb
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=59312ec6-a40d-4168-a0f2-b80c7be247eb ro recovery nomodeset quiet splash acpi_backlight=vendor
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 4B84C43146DE0326
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
UUID=59312ec6-a40d-4168-a0f2-b80c7be247eb /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=38bf76e9-b849-4449-a5fe-29b9654a0166 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               5
               =                boot/vmlinuz-3.0.0-12-generic                  3
               =                initrd.img                                     5
               =                vmlinuz                                        3

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

The whole screen is black. Text is white, highlighted text is black on white background.

---

### Post by drs305 on 2011-10-29
> **Chakoo said:**
> 
The whole screen is black. Text is white, highlighted text is black on white background.

I don't see a theme setting and there is no 05_debian_theme section of your /boot/grub/grub.cfg file. The file */etc/grub.d/05_debian_theme* is the script which incorporates non-default images/fonts into the Grub menu if no theme is set elsewhere (/etc/default/grub).

Perhaps you removed the executable bit or removed the file. You can see if the file exists with the first command, and set it to be executable with the second.


```
ls /etc/grub.d/05_debian_theme 
sudo chmod +x /etc/grub.d/05_debian_theme 
sudo update-grub

```

---

### Post by Chakoo on 2011-10-29
drs305 you are my god! :D thanks dude, worked like a charm.

Shadi

---

### Post by drs305 on 2012-07-03
This page has been migrated to the Ubuntu Community Documentation site. For the most up-to-date information, please visit:
[https://help.ubuntu.com/community/Grub2/Displays]("https://help.ubuntu.com/community/Grub2/Displays")

The above page is a sub-page of the main community documentation regarding [https://help.community/Grub2]("https://help.ubuntu.com/community/Grub2").

Thank you to all the users who posted in these threads and expanded our knowledge of Grub 2 since it's introduction.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?p=12073029](http://ubuntuforums.org/showthread.php?p=12073029)

**Support threads regarding the wiki and it's content should be created in a suitable forum.**

---

