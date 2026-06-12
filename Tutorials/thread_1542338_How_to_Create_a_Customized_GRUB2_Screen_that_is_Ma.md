---
title: "How to: Create a Customized GRUB2 Screen that is Maintenance Free."
date: 2010-07-30
forum: Tutorials
---

### Post by Cavsfan on 2010-07-30
[COLOR="Red"]The information from this thread can be found here

[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)[/COLOR]


Added [COLOR=Green]*Notes[/COLOR] for Ubuntu versions that use Grub2 version 1.99 which started at Natty 11.04 and maybe even late Maverick 10.10.
_Enter **grub-install -v** in terminal and if it says 1.99 pay attention to any line that starts out with [COLOR=Green]Notes[/COLOR] as the changes are critical to this working._
Thanks to** Ranch Hand **for his help and valuable knowledge.
Thanks to **Riskable **for finding a way to make the font larger.
Thanks to **Drs305** for his invaluable help with Grub.
 
I recently installed Ubuntu 12.04 into a separate partition.
So, since I wanted Ubuntu 10.04 to be my main OS, I booted into Lucid and entered in terminal **sudo grub-install /dev/sda** which is where Lucid is.
Then I simply had to replicate the custom entries in **/etc/grub.d/06_custom** and change the menu text, (hd0,3) to (hd0,5) and sda3 to sda5.

 This can be adapted for any version of **Ubuntu** that uses** GRUB2.**
 **Note: **I have not added any quotes around the commands as there may be quotes in the commands themselves.  
 I have just made the commands bold and avoided placing periods after the commands also. Do not modify or add any lines except these mentioned.
 
 This will setup a customized **GRUB2 **menu with a background picture for just **Ubuntu **or** Dual Booting Ubuntu** and **Windows** that is totally maintenance free.
 The only time you may have to modify something is when GRUB files are updated via system update.
 
 **1) **To change the default line number, timeout and the resolution of the GRUB2 screen,bring up a terminal and enter this **gksu gedit /etc/default/grub**
 **GRUB_DEFAULT=4 **means to default on the 5th line from the top. (0 is first). If you only have Ubuntu, set this to 0.
If you dual boot and want Ubuntu as your default set this to 0, if you want Windows as default set it to 2.
I tri-boot so, I have the default set to windows 7 so I set this to 4. If you tri-boot and want your 2nd 'buntu as default, set this to 2.
 **GRUB_TIMEOUT=60** means Grub2 screen displays for 60 seconds before defaulting. You can set this to whatever you want.
 **GRUB_GFXMODE=1920x1200-24** means screen resolution is 1920x1200 and 24 is the color bit depth. The -24 on the end is not absolutely required.
*Specifying the bit depth of 24 is a high quality picture. 

The resolution and bit depth is dependent on your video card/driver. 
 If the last line is incorrect, you will have a black and white or blue grub screen.
 **(Note: **Do not make the **GRUB_GFXMODE **to a higher resolution than your monitor's native resolution.)
 Resolutions available to **GRUB 2 **can be displayed by typing** vbeinfo **in the** GRUB 2 **command line.  
 The command line is accessed by typing "c" when the main** GRUB2 **menu screen is displayed.
 Make sure there is _no_ **#** to the left of these 3 commands.
 Also make sure there is a **#** beside this **#GRUB_HIDDEN_TIMEOUT=0**

[COLOR=Green]*Note[/COLOR] if you are using Grub2 version 1.99, all you need to change in **05_debian_theme** is the colors as shown in step 2 and that is all.
The custom wallpaper must be edited with Gimp (see the green note below).
Then you need to move 1 and only 1 picture to /boot/grub/  e.g. **sudo cp rain.jpg to /boot/grub/** and enter **sudo update-grub**. 
If you change the picture be sure and remove the previous one because it looks for the first one it finds.

 **2)** To add a custom wallpaper background for your **GRUB2** menu, you will need to move at least one picture that is the exact dimensions as your **GRUB_GFXMODE **says to this location:
 **/usr/share/images/desktop-base/  **This is the directory to store your pictures in and you will have to open that directory as root to be able to put them there.  
 If you do not have **Ubuntu Tweak** installed, it can be found in the Ubuntu Software Center (Applications >  Ubuntu Software Center).
 You can open **Ubuntu Tweak** (Applications > System Tools > Ubuntu Tweak. Then click on **Nautilus Settings **and put a check mark beside **Open Folder with root privileges**.  
 This will enable you to right click on the directory **/desktop-base/ **and click on **Open as Administrator.  **Then you can copy and paste your pictures into that directory.  
 When you have moved your picture (mine is called &#8220;rain.tga&#8221;), you should right click on it and go down to the properties tab and put a check mark next to **Execute** (Allow executing file as a program).  
 If you do not make the picture executable, it may not be displayed upon boot. Recently it doesn't seem to matter but, I still make it executable.

[COLOR=Red]Note:[/COLOR] [COLOR=SeaGreen]If you have a high quality picture, the picture _may_ need to be edited with **Gimp**. If it is listed when you enter **sudo update grub** but, does not appear at boot time. 
Edit the picture with **Gimp** and click on **Image** and then **Scale Image** and verify that the picture is the correct size. 
Then if Quality interpolation says "cubic" change it to "linear". 
Then click "scale" at the bottom right.  Then click File and Save and a little box will open. Move the quality slider to 100% and then click on Advanced options. 
Change the Subsampling to "Best Quality" and then click save and it goes though a conversion process. [/COLOR]

This has always made the picture work and it should list your picture when you enter **sudo update-grub**.
 
 And then you will need to edit this file with this command **gksu gedit /etc/grub.d/05_debian_theme ** 
 Any time you wish to change the picture you will have to edit this file and place the 
name of it here:
For grub version 1.98 prior to Natty only:
 **WALLPAPER="/usr/share/images/desktop-base/rain.tga"** They can be **png**, **tga**, **jpg** or **jpeg**.
 You will add this after the first *_**else**_* at the top of the file if there is not one already there and make sure there is no **# **to the left of it.
 Then the colors are right after the above line. Here are my current colors:
 [COLOR=SeaGreen]This is for grub version 1.98 prior to Natty:
```
COLOR_NORMAL="light-cyan/black"  
COLOR_HIGHLIGHT="white/black"
```[/COLOR]
[COLOR=SeaGreen]This is for grub version 1.99 Natty through Precise:[/COLOR]
[COLOR=SeaGreen]At line 98 of 05_debian_theme where you see the 1st line add the two lines after that and save the file:[/COLOR]
```
echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
[COLOR=SeaGreen]echo " set color_normal=[/COLOR][COLOR=SeaGreen]light-cyan/black[/COLOR][COLOR=SeaGreen]"
echo " set color_highlight=[/COLOR][COLOR=SeaGreen]white/black[/COLOR][COLOR=SeaGreen]"[/COLOR]
if [ -n "${2}" ]; then 
```These colors work on my dark background, but they are up to you. 
Just **make sure you do not change the 2nd color of black** to anything else as this will cause the line to be **transparent**.
 [[COLOR=blue]_You can see what colors are available here. Just scroll down several pages._[/COLOR]]("https://help.ubuntu.com/community/Grub2#GRUB%202%20Splash%20Images")

Always enter **sudo update-grub** or **sudo update-grub2** after changing a file.
 

 **3)** To make your GRUB2 screen maintenance free bring up a terminal and enter **sudo grub-mkconfig**.This will Generate a grub config file that tells where everything is coming from.
Then copy this output and paste it into a gedit (or any text file) and save it for future reference.
 
 Each of the grub files involved will be displayed with a beginning and end line that looks like this:
 
 **### BEGIN /etc/grub.d/00_header ###**
 
 **### END /etc/grub.d/00_header ###**
 
 If you just have Ubuntu or are dual booting, open up this file for editing with this command: **gksu gedit /etc/grub.d/40_custom**
 
 You will see this:
 
 [COLOR=#0000ff]#!/bin/sh [/COLOR] 
 [COLOR=#b80047]exec tail[/COLOR] -n +3 [COLOR=#0000ff]$0 [/COLOR] 
 [COLOR=#0000ff]# This file provides an easy way to add custom menu entries.  Simply type the [/COLOR] 
 [COLOR=#0000ff]# menu entries you want to add after this comment.  Be careful not to change [/COLOR] 
 [COLOR=#0000ff]# the 'exec tail' line above.[/COLOR]
 
 Make sure you enter all of the following custom entries _below_ the last line in the file.

[COLOR=Green]*Note[/COLOR] if you are using Grub2 version 1.99, you will need to change the line above to this: [COLOR=#b80047]exec tail[/COLOR] -n +4 [COLOR=#0000ff]$0 [/COLOR] 
 
 The following hard drive and partition that is needed for the Ubuntu entries will be contained between the lines that mention  
 **### BEGIN /etc/grub.d/10_linux ###** and **### END** **/etc/grub.d/10_linux ###**
in the output of the **sudo grub-mkconfig** command above, which should be saved. Simply copy the lines below and change the red to suit your needs.  
 Or you can use the command **sudo blkid **to determine what to put as **sdax** below (where x is a,b,c, etc.).  
 If you are dual windows, this command will also provide the **UUID** (in the red characters after **--set** below in the windows 7 entry). It will be the first line that has **TYPE="ntfs" **beside of it. 
 
 There will be 8 lines for each line for Ubuntu and 9 lines for each Windows entry you wish your GRUB2 to display (starting with echo and ending with EOF).
 
 Keep in mind what is displayed on the echo and menuentry lines can be whatever you want them to be.  
 But, everything else _must be exactly as below_ once you have changed the red part to match your system.
 
[COLOR=Red]However, what is between the quotes should be changed to suit your flavour of Ubuntu (2 lines per entry).
And whatever you put between the quotes is totally up to you as you will be the only one seeing it.[/COLOR] 

[COLOR=Green]*Note[/COLOR] if you are are using Grub2 version 1.99, you will want to use the following with the echo command only at the top:

```
echo "[COLOR=Red]Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04 and Windows 7[/COLOR]" >&2 
menuentry "Lycid Lynx 10.04" {
    set root=([COLOR=Red]hd0,3[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda3[/COLOR] ro quiet splash
        initrd /initrd.img
}

```(Delete the cat << EOF line and the EOF lines)
[COLOR=Green]
*Note [/COLOR]instead of this:

 ```
echo "[COLOR=Red]Ubuntu Lucid Lynx 10.04[/COLOR]" >&2 
cat << EOF
menuentry "[COLOR=Red]Ubuntu Lucid Lynx 10.04[/COLOR]" {
    set root=([COLOR=Red]hd0,3[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda3[/COLOR] ro quiet splash
        initrd /initrd.img
}
EOF
```My Ubuntu Lucid Lynx is on disk 0 partition 3 ([COLOR=#ff0000]hd0,3[/COLOR]). And [COLOR=#ff0000]sda3[/COLOR] is partition 3 of hard drive 0.
 Just change what you see in red above to match wherever yours is and make sure and not change anything else.
 
 Then if you want a recovery mode as a 2nd line, enter this just after the EOF above:
 What goes where the red is will be exactly as above.
 
[COLOR=Green]*Note[/COLOR] if you are are using Grub2 version 1.99, your 2nd entry will look like this:

```

menuentry "[COLOR=Red]Lycid Lynx 10.04[/COLOR][COLOR=Red] (Recovery Mode)[/COLOR]" {
    set root=(hd[COLOR=Red]0,3[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda3[/COLOR] ro single
        initrd /initrd.img
}
```[COLOR=Green]*Note [/COLOR]instead of this:

 ```
echo "[COLOR=Red]Ubuntu Lucid Lynx 10.04 (Recovery Mode)[/COLOR]" >&2 
cat << EOF
menuentry "[COLOR=Red]Ubuntu Lucid Lynx 10.04 (Recovery Mode)[/COLOR]" {
    set root=(hd[COLOR=Red]0,3[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda3[/COLOR] ro single
        initrd /initrd.img
}
EOF
```If you tri-boot enter these entries based on which partition they are on:

[COLOR=Green]*Note[/COLOR] if you are are using Grub2 version 1.99, each subsequent entry will look like this:

```

menuentry "[COLOR=Red]Ubuntu Precise Pangolin 12.04"[/COLOR] {
    set root=([COLOR=Red]hd0,5[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda5[/COLOR] ro quiet splash
        initrd /initrd.img
}
```[COLOR=Green]*Note [/COLOR]instead of this:

```
echo "[COLOR=Red]Ubuntu Precise Pangolin 12.04[/COLOR]" >&2 
cat << EOF
menuentry "[COLOR=Red]Ubuntu Precise Pangolin 12.04"[/COLOR] {
    set root=([COLOR=Red]hd0,5[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda5[/COLOR] ro quiet splash
        initrd /initrd.img
}
EOF
```[COLOR=Green]*Note[/COLOR] and this:

```
menuentry "[COLOR=Red]Ubuntu Precise Pangolin 12.04[/COLOR][COLOR=Red] (Recovery Mode)[/COLOR]" {
    set root=(hd[COLOR=Red]0,5[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda5[/COLOR] ro single
        initrd /initrd.img
}
```[COLOR=Green]*Note [/COLOR]instead of this:

```
echo "[COLOR=Red]Ubuntu Precise Pangolin 12.04[/COLOR][COLOR=Red] (Recovery Mode)[/COLOR]" >&2 
cat << EOF
menuentry "[COLOR=Red]Xbuntu Precise Pangolin 12.04[/COLOR][COLOR=Red] (Recovery Mode)[/COLOR]" {
    set root=(hd[COLOR=Red]0,5[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda5[/COLOR] ro single
        initrd /initrd.img
}
EOF
```Skip this part and go to step 5 below if you just boot into Ubuntu only.
 

 **4)** If you are dual booting **Windows** as I am, you will add this below the above 2 entries after the &#8220;EOF&#8221;:
 
[COLOR=Green]*Note[/COLOR] if you are using Grub2 version 1.99, you will be add this:

```

menuentry "[COLOR=Red]Windows 7[/COLOR]" {
    insmod ntfs
    set root='(hd[COLOR=Red]0,1[/COLOR])'
    search --no-floppy --fs-uuid --set [COLOR=Red]1cfc7a8dfc7a60c6[/COLOR]
    chainloader +1
}
```[FONT=Arial, sans-serif]
[/FONT]
[COLOR=Green]*Note [/COLOR]instead of this:

 ```
echo "[COLOR=Red]Windows 7[/COLOR]" >&2 
cat << EOF
menuentry "[COLOR=Red]Windows 7[/COLOR]" {
    insmod ntfs
    set root='(hd[COLOR=Red]0,1[/COLOR])'
    search --no-floppy --fs-uuid --set [COLOR=Red]1cfc7a8dfc7a60c6[/COLOR]
    chainloader +1
}
EOF
```[FONT=Arial, sans-serif]

[/FONT]The red numbers above will need to be changed to match the drive, partition where you windows install is. 
 And the UUID red characters after **--set** above will need to match the characters contained on a similar line between these 2 lines  in the output of **sudo grub-mkconfig**.
 **### [FONT=Arial, sans-serif]BEGIN[/FONT] /etc/grub.d/30_os-prober ###** 

**### END /etc/grub.d/30_os-prober ###** 
or see the output of the  **sudo blkid **command mentioned in step 3 above.
 

 **5)** Then after all of that is entered below the last line in **/etc/grub.d/40_custom**, save the file as **/etc/grub.d/06_custom**
It is very [COLOR=Red]important[/COLOR] to save the file as **/etc/grub.d/06_custom** and [COLOR=Red]not[/COLOR] **/etc/grub.d/40_custom**, so the custom entries appear first.
Each file is executed in numerical sequence. If you save the custom entries in **/etc/grub.d/40_custom**, you will still need to modify the default line every time a kernel is installed, which defeats the purpose of this tutorial.

Then the last thing is to make **/etc/grub.d/06_custom** executable with this command:
 **sudo chmod +x /etc/grub.d/06_custom**
 
 Then of course **sudo update-grub** to make the changes &#8220;stick&#8221;. If you ever make a change to any of these files and do not remember to enter this command upon reboot, you _will not_ see your changes.
 
Then after you have this setup like you want it, you can make only those 2 or 3 lines appear on your  Grub screen. But, I would recommend waiting a little while and maybe let a kernel update come in and see if the new top option picks the new kernel.  
You can enter **sudo uname -a** to see which version of kernel you are using. When you are confident that all is working as it should you can eliminate the other lines as desired and it will be maintenance free.  
 
 As it is, it will list your custom entries at the top and the other entries for what normally displays below that.
 

 **6)** If and when you are satisfied with the customized screen, you can make the other lines disappear like this:
 (The following are simply suggestions and if you want to see the other lines you do not have to follow the next steps.)  
 But, the default line and the lines you have added at the top will now be maintenance free,
 
 To make the memtest86+ lines so that they do not display enter:
 **sudo chmod -x /etc/grub.d/20_memtest86+**
 
 To make the other Ubuntu kernel lines so that they do not display enter:  
 **sudo chmod -x /etc/grub.d/10_linux**
[COLOR=Red]*Note: It is highly recommended that you keep at least 2 kernels installed.[/COLOR]
If you encounter issues with the latest kernel, enter **sudo chmod +x /etc/grub.d/10_linux && sudo update-grub**
to make all of the kernels selectable. 

If you are dual-booting windows and want to make the duplicate windows entries go away enter this: **sudo chmod -x /etc/grub.d/30_os-prober**
If you are dual booting or triple booting with another OS, you may not want to modify the **30_os-prober** file.
 
 And [COLOR=Red]always remember[/COLOR] to enter **sudo update-grub** [COLOR=Red]after any changes[/COLOR] (**sudo update-grub2 **does the same thing).
 
 Now you will have a GRUB2 screen that does not change or require _any_ modification even when a new kernel is installed.

Example picture [[IMG]http://omploader.org/tNThiaw[/IMG]]("http://omploader.org/vNThiaw")

**7)** Now to make the font larger and more readable. 

[COLOR=Green]*Note [/COLOR]enter **gksu gedit /etc/default/grub** to see if it already contains the **GRUB_FONT= **line. If it is, skip this, if not, continue.

[B]sudo grub-mkfont --output=/boot/grub/DejaVuSansMono.pf2 \
--size=24 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf[/B]

[COLOR=Green]**_*Note if you are using Grub2 version 1.99_**[/COLOR]**[COLOR=Red]- You will probably get errors like the ones below while making the font, but just ignore them[/COLOR]**[COLOR=Red].[/COLOR]

```
Unknown gsub feature 0x63636d70 (ccmp)
Unknown gsub feature 0x646c6967 (dlig)
Unsupported substitution flag: 0x9
Unsupported substitution flag: 0x9
Unknown gsub feature 0x6c6f636c (locl)
Unknown gsub feature 0x6c6f636c (locl)
Unsupported substitution flag: 0x9
```This will copy and resize the font DejaVuSansMono.ttf and put it into a format and location that GRUB will use.

Then edit this file **gksu gedit /etc/default/grub** and add the line below near the top of the file.

**GRUB_FONT=/boot/grub/DejaVuSansMono.pf2**

And enter **sudo update-grub**

Example picture with bigger font  [[IMG]http://omploader.org/tNTlsYg[/IMG]]("http://omploader.org/vNTlsYg")

 The picture above is fairly dark and has cyan/black (normal) and white/black (highlight) for colors in /etc/grub.d/05_debian_theme.

[[IMG]http://ompldr.org/tNjFwZQ[/IMG]]("http://ompldr.org/vNjFwZQ")
Another example with white snow background and blue/black (normal) and magenta/black (highlight) colors in /etc/grub.d/05_debian_theme.

Here is my current tri-boot grub screen:

[[IMG]http://ompldr.org/tZHpnbA[/IMG]]("http://ompldr.org/vZHpnbA")



Last updated: June 25, 2012
Added [COLOR=SeaGreen]*Notes[/COLOR] for Ubuntu versions that use Grub2 version 1.99 which started at Natty 11.04 and possibly late Maverick 10.10.
Added a note above step 2 that simplifies the background for Grub2 version 1.99
More updating for Grub2 version 1.99 starting with note before step 2 through step 2.

---

### Post by SkulblakaSama on 2010-08-02
> **Cavsfan said:**
> In case anyone wants to have a maintenance free GRUB2 screen, check out my tutorial on how to do so.
**Ranch Hand** showed me everything contained in it, I am just sharing it with anyone that wants it.

**drs305**, there will still be plenty of need for your tutorial here as you probably forgot more than I'll ever know about GRUB2!

And I hope you don't mind me posting this here. I am kind of excited! 

_[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)_

Thanks!

After I have done what you said; "Then click on **Nautilus Settings **and put a check mark beside **Open Folder with root privileges**." I keep on getting this... 

andrey@andrey-desktop:~$ update-grub
/usr/sbin/grub-mkconfig: You must run this as root

Is there a fix? What happened that this occurred? :?

---

### Post by Cavsfan on 2010-08-02
> **SkulblakaSama said:**
> After I have done what you said; "Then click on **Nautilus Settings **and put a check mark beside **Open Folder with root privileges**." I keep on getting this... 

andrey@andrey-desktop:~$ update-grub
/usr/sbin/grub-mkconfig: You must run this as root

Is there a fix? What happened that this occurred? :?
If you are referring to my tutorial, which looks like you are, you should post at the bottom of that thread.
Some where in **Ubuntu Tweak** it should have asked you for a password in order to put the check mark in **Nautilus Settings** 
or else it did not take effect. You should put '**sudo**' before either **update-grub** or **grub-mkconfig**. No matter about the checkbox, these have to be run as root.
That is what the error you are getting is.
And please post in the correct thread. If you are working with my tutorial, post questions there.

---

### Post by SkulblakaSama on 2010-08-02
> **Cavsfan said:**
> If you are referring to my tutorial, which looks like you are, you should post at the bottom of that thread.
Some where in **Ubuntu Tweak** it should have asked you for a password in order to put the check mark in **Nautilus Settings** 
or else it did not take effect. You should put '**sudo**' before either **update-grub** or **grub-mkconfig**. No matter about the checkbox, these have to be run as root.
That is what the error you are getting is.
And please post in the correct thread. If you are working with my tutorial, post questions there.

My apologies, I realized that but didn't take action. Thank you for the tutorial and the solution.

---

### Post by Cavsfan on 2010-08-02
> **SkulblakaSama said:**
> My apologies, I realized that but didn't take action. Thank you for the tutorial and the solution.
You are most welcome! I just didn't want to waste **Drs305**'s time on my stuff.
By all means if you have any problems about my tutorial, post questions there.
Thank you

---

### Post by SkulblakaSama on 2010-08-02
> **Cavsfan said:**
> 
The following hard drive and partition that is needed will be contained between the lines that mention  
 **### END /etc/grub.d/10_linux ###** in the output of the **grub-mkconfig** command above, which should be saved. Simply copy the 8 lines below and change the red to suit your needs.  
 

I didn't understand this part, what 8 lines did you mean? 

These are my 10 lines below "**### END /etc/grub.d/10_linux ###"**

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1609e458-e91e-4866-bb71-65e544e681ae
    linux16    /boot/memtest86+.bin
}

Stupid question, do I count the white space, and "### BEGIN /etc/grub.d/20_memtest86+ ###" or just the 8 lines below "### BEGIN /etc/grub.d/20_memtest86+ ###"?

---

### Post by Cavsfan on 2010-08-02
> **SkulblakaSama said:**
> I didn't understand this part, what 8 lines did you mean? 

These are my 10 lines below "**### END /etc/grub.d/10_linux ###"**

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1609e458-e91e-4866-bb71-65e544e681ae
    linux16    /boot/memtest86+.bin
}

Stupid question, do I count the white space, and "### BEGIN /etc/grub.d/20_memtest86+ ###" or just the 8 lines below "### BEGIN /etc/grub.d/20_memtest86+ ###"?


The 8 lines are in the first 2 boxes Starting with **echo** and ending with **EOF** and they must be copied exactly as they are.
If you are dual booting windows, the  3rd box actually is 9 lines long but, starts and ends with the exact same thing.

---

### Post by SkulblakaSama on 2010-08-02
> **Cavsfan said:**
> The 8 lines are in the first 2 boxes Starting with **echo** and ending with **EOF** and they must be copied exactly as they are.
If you are dual booting windows, the  3rd box actually is 9 lines long but, starts and ends with the exact same thing.

Ahh, I see, I had to copy that code that was in the box, then modify the red found in grub-mkconfig.

---

### Post by Cavsfan on 2010-08-02
> **SkulblakaSama said:**
> Ahh, I see, I had to copy that code that was in the box, then modify the red found in grub-mkconfig.
Yes, exactly! Let me know how it comes out! And thanks for doing this!

---

### Post by SkulblakaSama on 2010-08-02
> **Cavsfan said:**
> Yes, exactly! Let me know how it comes out! And thanks for doing this!
One more question, are the numbers the same? This is what I have;

echo "Adding Ubuntu Lucid Lynx 10.04" >&2 
cat << EOF
menuentry "Ubuntu Lucid Lynx 10.04" {
    set root=(hd0,[COLOR=Red]5[/COLOR])
        linux /vmlinuz root=/dev/sda[COLOR=Red]5[/COLOR] ro quiet splash
        initrd /initrd.img
}
EOF

I couldn't find the "sda[COLOR=Red]#[/COLOR]" part, so I assumed both numbers have to be the same. Is that correct?

---

### Post by Cavsfan on 2010-08-02
> **SkulblakaSama said:**
> One more question, are the numbers the same? This is what I have;

echo "Adding Ubuntu Lucid Lynx 10.04" >&2 
cat << EOF
menuentry "Ubuntu Lucid Lynx 10.04" {
    set root=(hd0,[COLOR=Red]5[/COLOR])
        linux /vmlinuz root=/dev/sda[COLOR=Red]5[/COLOR] ro quiet splash
        initrd /initrd.img
}
EOF

I couldn't find the "sda[COLOR=Red]#[/COLOR]" part, so I assumed both numbers have to be the same. Is that correct?

As I mentioned in step 3 above, you can enter this in terminal **sudo blkid **and that will tell you what you need to know. 
Just look for the ext4 beside of it. Yes sda5 would be (hd0,5).

---

### Post by SkulblakaSama on 2010-08-02
> **Cavsfan said:**
> As I mentioned in step 2 above, you can enter this in terminal **sudo blkid **and that will tell you what you need to know. 
Just look for the ext4 beside of it. Yes sda5 would be (hd0,5).
Alright, I've finished your guide, now to reboot...

---

### Post by SkulblakaSama on 2010-08-02
Alright everything seems in order. The background wallpaper, and now there are two new entries. "Linux Lucid" I need to verify the exact name, could you describe what those two entries are?

---

### Post by Cavsfan on 2010-08-02
> **SkulblakaSama said:**
> Alright everything seems in order. The background wallpaper, and now there are two new entries. "Linux Lucid" I need to verify the exact name, could you describe what those two entries are?

They are what ever you put between the quotes, at least what is displayed.
That part is whatever you want it to display, but everything else must be as is.
**Echo** and **menuentry** are what displays and can be whatever you want.
But the first one is Ubuntu (normal mode) and the 2nd one is Ubuntu (recovery mode).
If you did not get the text that displays right, you can change it, just remember to 
enter **sudo update-grub** for the changes to stay. But the rest if you copied right and all went well, just be normal and recovery.
You can test that if you want.
And the next time a kernel is installed you can use **sudo uname -a **to verify that the kernel selected by the top option is the new one.
I have to eat as the wife is calling, but I am glad you got this done.
It is not so much of a hassle for strictly Ubuntu users, but even then the default line would change with every kernel update. 
but what you see now is what you will see 6 months from now. 
And anytime you want to see other kernels or memtest86, just do the opposite of what you did earlier.
Thanks for trying it out and I hope that more people find it useful.
The people that dual boot windows should find it very useful.

---

### Post by SkulblakaSama on 2010-08-02
> **Cavsfan said:**
> They are what ever you put between the quotes, at least what is displayed.
That part is whatever you want it to display, but everything else must be as is.
**Echo** and **menuentry** are what displays and can be whatever you want.
But the first one is Ubuntu (normal mode) and the 2nd one is Ubuntu (recovery mode).
If you did not get the text that displays right, you can change it, just remember to 
enter **sudo update-grub** for the changes to stay. But the rest if you copied right and all went well, just be normal and recovery.
You can test that if you want.
And the next time a kernel is installed you can use **sudo uname -a **to verify that the kernel selected by the top option is the new one.
I have to eat as the wife is calling, but I am glad you got this done.
It is not so much of a hassle for strictly Ubuntu users, but even then the default line would change with every kernel update. 
but what you see now is what you will see 6 months from now. 
And anytime you want to see other kernels or memtest86, just do the opposite of what you did earlier.
Thanks for trying it out and I hope that more people find it useful.
The people that dual boot windows should find it very useful.

Here is a visual for my situation. It's an attachment.

---

### Post by Cavsfan on 2010-08-03
> **SkulblakaSama said:**
> Here is a visual for my situation. It's an attachment.

Do you dual boot Ubuntu with Windows 7 too?
I thought you only had Ubuntu on your machine, but I could be mistaken.
This picture is after you did all of the steps above correct?
The custom entries in the picture show as the last 3 entries, when they are supposed to be the first 3 entries.

Can you enter **sudo grub-mkconfig** in a terminal and post the output here please.
Make sure you wrap the text with CODE (select all of the output and click on the # top right).

Also, could you enter **ls -l /etc/grub.d/**  in a terminal and paste the output here also wrapped in CODE as mentioned above.

This is what I am wanting to see: the 2 custom Ubuntu Entries first and if dual booting Windows 7 like I am that should appear 3rd.

[[IMG]http://omploader.org/tNTRyeA[/IMG]]("http://omploader.org/vNTRyeA")

And I do not suggest starting off with just 2 or 3 entries. As I mentioned in step 6 of the  tutorial, only after some time goes by and you 
are absolutely confident that it works as expected. Then you can make the other files non-executable so that they do not appear.

---

### Post by SkulblakaSama on 2010-08-03
> **Cavsfan said:**
> Do you dual boot Ubuntu with Windows 7 too?
I thought you only had Ubuntu on your machine, but I could be mistaken.
This picture is after you did all of the steps above correct?
The custom entries in the picture show as the last 3 entries, when they are supposed to be the first 3 entries.

Can you enter **sudo grub-mkconfig** in a terminal and post the output here please.
Make sure you wrap the text with CODE (select all of the output and click on the # top right).

Also, could you enter **ls -l /etc/grub.d/**  in a terminal and paste the output here also wrapped in CODE as mentioned above.

This is what I am wanting to see: the 2 custom Ubuntu Entries first and if dual booting Windows 7 like I am that should appear 3rd.

[[IMG]http://omploader.org/tNTRyeA[/IMG]]("http://omploader.org/vNTRyeA")

And I do not suggest starting off with just 2 or 3 entries. As I mentioned in step 6 of the  tutorial, only after some time goes by and you 
are absolutely confident that it works as expected. Then you can make the other files non-executable so that they do not appear.

You're right about me duel booting into Windows 7. I have a reason to believe that I have added something to "**gksu gedit /etc/grub.d/40_custom" ** that wasn't supposed to be there. 

```
Generating grub.cfg ...
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
search --no-floppy --fs-uuid --set 1609e458-e91e-4866-bb71-65e544e681ae
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  set gfxpayload=keep
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
search --no-floppy --fs-uuid --set 1609e458-e91e-4866-bb71-65e544e681ae
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
Found background image: energy-fluke.jpg
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 1609e458-e91e-4866-bb71-65e544e681ae
insmod jpeg
if background_image /usr/share/images/desktop-base/energy-fluke.jpg ; then
  set color_normal=white/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1609e458-e91e-4866-bb71-65e544e681ae
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1609e458-e91e-4866-bb71-65e544e681ae ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1609e458-e91e-4866-bb71-65e544e681ae
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1609e458-e91e-4866-bb71-65e544e681ae ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1609e458-e91e-4866-bb71-65e544e681ae
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1609e458-e91e-4866-bb71-65e544e681ae
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Windows 7 (loader) on /dev/sda1
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01cb2416e6305a00
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Ubuntu Lucid Lynx 10.04" >&2 
cat << EOF
menuentry "Ubuntu Lucid Lynx 10.04" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
EOF
echo "Ubuntu Lucid Lynx 10.04 (Recovery Mode)" >&2 
cat << EOF
menuentry "Ubuntu Lucid Lynx 10.04 (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
}
EOF
echo "Windows 7 (loader)" >&2 
cat << EOF
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01cb2416e6305a00
    chainloader +1
}
EOF
### END /etc/grub.d/40_custom ###
done
```
```
total 40
-rwxr-xr-x 1 root root 4466 2010-08-02 14:48 00_header
-rwxr-xr-x 1 root root 1409 2010-08-02 17:57 05_debian_theme
-rwxr-xr-x 1 root root 4594 2010-04-13 08:59 10_linux
-rwxr-xr-x 1 root root  918 2010-03-23 04:37 20_memtest86+
-rwxr-xr-x 1 root root 6605 2010-04-13 08:59 30_os-prober
-rwxr-xr-x 1 root root  843 2010-08-02 17:34 40_custom
-rw-r--r-- 1 root root  483 2010-04-13 08:59 README

```My apologies for the delay, I had to do something.

---

### Post by Cavsfan on 2010-08-03
> **SkulblakaSama said:**
> My apologies for the delay, I had to do something.

Oh, no problem. We all are busy from time to time. So, you do not have Windows 7 but, you put it into 40_custom as I said in the tut.
No problem and I also know why the custom entries did not appear at the top like they should have. This is a simple fix. 

In the tutorial I mentioned to edit **gksu gedit /etc/grub.d/40_custom** and 
then save it as **06_custom**. You saved **40_custom** and because of the numbering of the files, it made the custom entries appear at the bottom.

Here is a simple fix: enter **gksu gedit /etc/grub.d/40_custom** and take out the third entry about windows 7:

Delete **just** these 8 lines:

```
echo "Windows 7 (loader)" >&2 
cat << EOF
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01cb2416e6305a00
    chainloader +1
}
EOF
```And then click **File** > **Save As** and enter **06_custom**

Then enter (copy and paste) these 3 lines into a terminal
```
sudo chmod +x /etc/grub.d/06_custom  
sudo chmod -x /etc/grub.d/40_custom
sudo chmod -x /etc/grub.d/30_os-prober


```Enter **sudo update-grub** and reboot.

Your 2 custom entries should now appear on top and you should not have to modify it when a kernel is installed as it will default to the top line 
(as long as you have **GRUB_DEFAULT=0** in /etc/default/grub as mentioned in step 1 of the tutorial.

Once you have done that enter **gksu gedit /etc/grub.d/40_custom **again and delete everything you added and save it. It should look exactly like this:
```

[COLOR=Blue]#!/bin/sh[/COLOR]
[COLOR=Red]exec tail[/COLOR] -n +3 [COLOR=Blue]$0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.[/COLOR]
```
And save it.
Like Step 6 says in the tutorial, if you want you can make the memtest86 entries go away and the other kernel entries.
But, I suggest you wait a while before doing this.

Let me know if the first 2 entries are now the custom ones.

---

### Post by SkulblakaSama on 2010-08-03
> **Cavsfan said:**
> 
Your 2 custom entries should now appear on top and you should not have to modify it when a kernel is installed as it will default to the top line 
(as long as you have **GRUB_DEFAULT=0** in /etc/default/grub as mentioned in step 1 of the tutorial.


Instead of "**GRUB_DEFAULT=0" **don't I have to have "**2**"since I duel boot?

---

### Post by SkulblakaSama on 2010-08-03
> **Cavsfan said:**
> 
Here is a simple fix: enter **gksu gedit /etc/grub.d/40_custom** and take out the third entry about windows 7:

Delete **just** these 8 lines:

```
echo "Windows 7 (loader)" >&2 
cat << EOF
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01cb2416e6305a00
    chainloader +1
}
EOF
```And then click **File** > **Save As** and enter **06_custom**

Then enter (copy and paste) these 3 lines into a terminal
```
sudo chmod +x /etc/grub.d/06_custom  
sudo chmod -x /etc/grub.d/40_custom
sudo chmod -x /etc/grub.d/30_os-prober


```Enter **sudo update-grub** and reboot.

Your 2 custom entries should now appear on top and you should not have to modify it when a kernel is installed as it will default to the top line 
(as long as you have **GRUB_DEFAULT=0** in /etc/default/grub as mentioned in step 1 of the tutorial.


Let me know if the first 2 entries are now the custom ones.

The two custom entries are on top, but my Windows 7 entry is gone, I don't think I should have deleted that...

---

### Post by Cavsfan on 2010-08-03
> **SkulblakaSama said:**
> Instead of "**GRUB_DEFAULT=0" **don't I have to have "**2**"since I duel boot?

You have windows too? I thought you didn't. If so, leave the 8 lines in **40_custom** and save it as **06_custom** and yes leave the default as 2.
But do everything else I mentioned.

---

### Post by SkulblakaSama on 2010-08-03
> **Cavsfan said:**
> You have windows too? I thought you didn't. If so, leave the 8 lines in **40_custom** and save it as **06_custom** and yes leave the default as 2.
But do everything else I mentioned.

Hah, that's an interesting misunderstanding. :p

---

### Post by Cavsfan on 2010-08-03
> **SkulblakaSama said:**
> The two custom entries are on top, but my Windows 7 entry is gone, I don't think I should have deleted that...

Yes, sorry I thought you didn't have Windows 7!
Just copy exactly what you have back into the bottom of **06_custom**

```
echo "Windows 7 (loader)" >&2 
cat << EOF
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01cb2416e6305a00
    chainloader +1
}
EOF
```Sorry for the confusion!

Oh, and don't forget** sudo update-grub**

---

### Post by SkulblakaSama on 2010-08-03
It's alright, I'll keep the extra stuff on the bottom, just in case. Everything works just as it should. Thank you for the great tutorial. 

This is off topic, but do you know "Plymouth"? I'm interested in operating it. Can you point me in the correct direction?

---

### Post by Cavsfan on 2010-08-03
> **SkulblakaSama said:**
> It's alright, I'll keep the extra stuff on the bottom, just in case. Everything works just as it should. Thank you for the great tutorial. 

This is off topic, but do you know "Plymouth"? I'm interested in operating it. Can you point me in the correct direction?

You are welcome! Glad we could get by the minor issues. These should get you started.
The 3rd link is where I found the first two.

[[COLOR=blue]_Plymouth article dated May1. 1020_[/COLOR]]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

[[COLOR=blue]_Plymouth themes: Fix, install, create in Ubuntu 10.04 (Lucid Lynx)_[/COLOR]]("http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html")

[[COLOR=blue]_Search for Plymouth stuff._[/COLOR]]("http://www.google.com/webhp?as_q=#hl=en&source=hp&q=ubuntu+10.04+plymouth+tutorial&aq=f&aqi=&aql=&oq=&gs_rfai=CnS0kZ25YTNbAAoPSiAPpocWICQAAAKoEBU_QbsHM&fp=24975515c8815dd")

---

### Post by SkulblakaSama on 2010-08-03
> **Cavsfan said:**
> You are welcome! Glad we could get by the minor issues. These should get you started.
The 3rd link is where I found the first two.

[[COLOR=blue]_Plymouth article dated May1. 1020_[/COLOR]]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

[[COLOR=blue]_Plymouth themes: Fix, install, create in Ubuntu 10.04 (Lucid Lynx)_[/COLOR]]("http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html")

[[COLOR=blue]_Search for Plymouth stuff._[/COLOR]]("http://www.google.com/webhp?as_q=#hl=en&source=hp&q=ubuntu+10.04+plymouth+tutorial&aq=f&aqi=&aql=&oq=&gs_rfai=CnS0kZ25YTNbAAoPSiAPpocWICQAAAKoEBU_QbsHM&fp=24975515c8815dd")

Thank you:popcorn:

---

### Post by Cavsfan on 2010-08-13
Added a sample picture of the finished product after the tutorial.

---

### Post by alaukikyo on 2010-08-17
Is there a way to make the font bigger?

---

### Post by Cavsfan on 2010-08-17
> **alaukikyo said:**
> Is there a way to make the font bigger?

I found this, but have not tried it. I am going to though.

```
grub-mkfont --help
Usage: grub-mkfont [OPTIONS] FONT_FILES

Options:
  -o, --output=FILE_NAME    set output file name
  --ascii-bitmaps           save only the ASCII bitmaps
  -i, --index=N             set face index
  -r, --range=A-B[,C-D]     set font range
  -n, --name=S              set font family name
  -s, --size=N              set font size
  -d, --desc=N              set font descent
  -c, --asce=N              set font ascent
  -b, --bold                convert to bold font
  -a, --force-autohint      force autohint
  --no-hinting              disable hinting
  --no-bitmap               ignore bitmap strikes when loading
  -h, --help                display this message and exit
  -V, --version             print version information and exit
  -v, --verbose             print verbose messages

```

---

### Post by Cavsfan on 2010-08-17
I was able to change the font and the size, but I am still learning about what is the best manner to do this.
I changed the font to Comic_Sans_MS and that didn't work too well.

I didn't really believe there was a way, but now I see how to do it, I just need some more time to perfect it.

This will be added to the bottom of the tutorial as soon as I get it done.

---

### Post by Cavsfan on 2010-08-17
> **alaukikyo said:**
> Is there a way to make the font bigger?

It is now updated with a way to make the font more readable. 
I added step 7 which is all about making the font size much more readable.

---

### Post by Cavsfan on 2010-08-18
The example picture with the bigger font size has now been added at the bottom of the tutorial.

---

### Post by Cavsfan on 2010-08-31
I changed **1920x1200x32** to **1920x1200-32** in **Step 1**. Not sure if that is what made my monitor click 
when booting up or not. This is what I have mine set to now and I have an nVidia GeForce 9800 GT card. 
The monitor was clicking 2 or 3 times at every boot. Now it does not click even once ever.

I also did a clean install 2 days ago from a Lucid Lynx 10.10.1 64 bit Desktop ISO found [[color=blue]_here_[/COLOR]](http://releases.ubuntu.com/). 
So, I am not sure which process fixed the monitor clicking, but I am happy that it no longer does. :D

---

### Post by Cavsfan on 2010-09-24
I changed **1920x1200x32** to **1920x1200-24** in **Step 1.** This is based on your video card/driver.
I have an nVidea card and in NVIDEA X Server Settings, it mentions 24 bit depth.

And my monitor started clicking again soon after I posted the previous comment. But, it is not caused by Ubuntu.
It does it while rebooting with Windows 7 too. I know it is loosing sync, which is what the clicking is, but it has always
done that since I got the PC. I was surprised that it went away temporarily.

---

### Post by saejin on 2010-09-28
It all worked GREAT.... except one little artifact I can not explain...
I used the same values and fonts as the example. In the GRUB2 menu option screen, the fonts of the selected line are chopped off by the top 25% or so.  When I select down to subsequent lines it then chops off the top of each font as it progresses...... It seems to be some problem in the selected font?

Any ideas?

---

### Post by Cavsfan on 2010-09-29
> **saejin said:**
> It all worked GREAT.... except one little artifact I can not explain...
I used the same values and fonts as the example. In the GRUB2 menu option screen, the fonts of the selected line are chopped off by the top 25% or so.  When I select down to subsequent lines it then chops off the top of each font as it progresses...... It seems to be some problem in the selected font?

Any ideas?

You could try changing the font size in step 7 which is currently **--size=24**. The 24 does not correspond to what we normally consider size 24 font though,
I noticed this on one website:
"FYI: I believe the "--size=" indicates point size but I'm not entirely sure (the documentation doesn't say). If it is based on the point scale I don't believe it is 
taking dpi into account since I tried "--size=72" on a 120dpi display and letters were only about half an inch tall (72 points is precisely one inch)."

I guess you could play around with it, but are you sure it is not the picture's size? What size is your resolution and picture size?

---

### Post by Cavsfan on 2010-10-05
For Maverick Meerkat only, added a comment before step 7 that says not to create the font for GRUB2.
And if you have the font listed in **/etc/default/grub**, you will need to comment it out with a **#** in front of it.

I upgraded to Maverick and thought the font was too big, so I tried a few things and then noticed that 
the font line was not even included. When I added it, it made it really look bad. So, I commented it out and it looks great.
So, the default font has been made bigger apparently.

---

### Post by Cavsfan on 2010-10-13
I had upgraded to Maverick from Lucid and apparently things were quite a bit different than doing a clean install, which I did yesterday.
Consequently I had made some errors in the tutorial with notes concerning Maverick which I have just fixed. There are only a couple of subtle 
differences with Maverick and the previous versions. If I caused anyone any harm, I appologize. But, everything should be good to go now 
for any flavour of Ubuntu especially using multiple operating systems, e.g. dual or tri-booting.

---

### Post by Emek on 2010-11-02
Hi guys!

I have migrate from Debian to Ubuntu 10.10 and this is tricky question because I want to know about Grub2 and mouserate in Debian and Ubuntu and Grub1 was something like this:

title           Debian GNU/Linux, kernel 2.6.32-5-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.32-5-686 root=/dev/sda1 ro vga=791** usbhid.mousepoll=2**
initrd          /boot/initrd.img-2.6.32-5-686


And it works for me to have 500Hz mouse rate, now I want to know where to put this little thing:
[B] 
usbhid.mousepoll=2

in Grub2 [/B]

Any suggestions? 

P.S.
Don't tell me please to do it in other way because none of another way works for me even like this [http://ubuntuforums.org/showthread.php?t=215981](http://ubuntuforums.org/showthread.php?t=215981)
So I must edit grub to have 500Hz mouse. 

**Thank you for future answer!**

---

### Post by Cavsfan on 2010-11-02
> **Emek said:**
> Hi guys!

I have migrate from Debian to Ubuntu 10.10 and this is tricky question because I want to know about Grub2 and mouserate in Debian and Ubuntu and Grub1 was something like this:

title           Debian GNU/Linux, kernel 2.6.32-5-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.32-5-686 root=/dev/sda1 ro vga=791** usbhid.mousepoll=2**
initrd          /boot/initrd.img-2.6.32-5-686


And it works for me to have 500Hz mouse rate, now I want to know where to put this little thing:
[B] 
usbhid.mousepoll=2

in Grub2 [/B]

Any suggestions? 

P.S.
Don't tell me please to do it in other way because none of another way works for me even like this [http://ubuntuforums.org/showthread.php?t=215981](http://ubuntuforums.org/showthread.php?t=215981)
So I must edit grub to have 500Hz mouse. 

**Thank you for future answer!**

I see you posted this same question in this thread also:
[[COLOR=blue]_http://ubuntu-ky.ubuntuforums.org/showpost.php?p=10060709&postcount=5_[/COLOR]]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=10060709&postcount=5")
I believe you are more likely to get help on this other thread.

You could also check this out: 
[[color=blue]_drs305 GRUB2 Tutorial_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1195275)

There are also a lot of links in **drs305**'s signature.

I hope this helps! :)

---

### Post by Emek on 2010-11-03
Thanks Cavsfan, but from my experience I want to ask specific questions. I don't want to read all manual to Grub2 or another things, because you see, I do this mistake in Grub1, and now there is Grub2 and my knowledge is for nothing! I don't want to know all Linux configurations before I make simple change that its necessary for my system. I want to learn what is necessary to be learn! I do my migration form Debian in hope to make life simpler! And I expect that from this community. 

We learn all our lives, but we don't learn the same things, so please consider this in future. **Thanks! **

---

### Post by Cavsfan on 2010-11-03
> **Emek said:**
> I want to learn what is necessary to be learn! I do my migration form Debian in hope to make life simpler! And I expect that from this community. 

We learn all our lives, but we don't learn the same things, so please consider this in future. **Thanks! **

I believe expecting things from this community won't get you very far. Asking graciously will get you a lot farther.
And you posted the exact same thing (identical) in 2 different threads, which I believe is inappropriate in this forum. 
This thread is just about how to create a customized GRUB2 screen and that is all.

---

### Post by Emek on 2010-11-04
> **Cavsfan said:**
> I believe expecting things from this community won't get you very far. Asking graciously will get you a lot farther.
And you posted the exact same thing (identical) in 2 different threads, which I believe is inappropriate in this forum. 
This thread is just about how to create a customized GRUB2 screen and that is all.

Let admins decide...

And... Where do you think I should post this mousepoll stuff? Easy to say it is inappropriate, but tell me, where to post this type of question? I am open to guidelines!

---

### Post by alababi on 2010-11-04
With more screenshots, this thread will be nicer.

---

### Post by Cavsfan on 2010-11-04
> **Emek said:**
> Let admins decide...

And... Where do you think I should post this mousepoll stuff? Easy to say it is inappropriate, but tell me, where to post this type of question? I am open to guidelines!

All I meant was that this thread does not have anything to do with mouse polling and I have no idea how to help you with that.
I would suggest you post a new thread in the General Help section. But, you have already posted the identical question on that GRUB and grub-legacy thread.
Not sure what the protocol is.


> **alababi said:**
> With more screenshots, this thread will be nicer.

Feel free to post your screenshot!
I'll post another one myself. Thanks for the suggestion!

---

### Post by Cavsfan on 2010-11-04
Added a lighter background example picture of white snow at the bottom of of the tutorial.
Also added the colors I used in both pictures.
Feel free to post your own GRUB2 screen along with the color combinations you used.

---

### Post by John Little on 2010-11-11
[FONT=Book Antiqua]:PFantastic thread! Thanks!

In your menu entry for Ubuntu

```
cat << EOF
menuentry "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" {
    set root=(hd0,3)
        linux /vmlinuz root=/dev/sda3 ro single
        initrd /initrd.img
}
EOF
```you don't have a [FONT=Arial]search[/FONT] command.  I discovered the hard way what it's for; it sets the root, **overwriting** the set statement the line before, because the "device enumeration" (which drive is [FONT=Arial]hd0[/FONT], which is [FONT=Arial]hd1[/FONT], and so on) can change from boot to boot. People assume, as I had, that [FONT=Arial]hd0[/FONT] is [FONT=Arial]/dev/sda[/FONT], [FONT=Arial]hd1[/FONT] is [FONT=Arial]/dev/sdb[/FONT], and so on, but that can change, indeed it did on my system; [FONT=Arial]hd0[/FONT] became [FONT=Arial]/dev/sdb[/FONT], [FONT=Arial]hd1[/FONT] became [FONT=Arial]/dev/sda[/FONT].

I'm not sure why [FONT=Arial]grub-mkconfig[/FONT] generates the [FONT=Arial]set root[/FONT] statement, since the search overwrites it.  Maybe it's a fallback in case the partition UUID changes.  IMO quite misleading.

The search command doesn't have to use the unwieldy UUID, it can use a label or a file to search for.  

[/FONT]

---

### Post by Cavsfan on 2010-11-12
> **John Little said:**
> [FONT=Book Antiqua]:PFantastic thread! Thanks!

In your menu entry for Ubuntu

```
cat << EOF
menuentry "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" {
    set root=(hd0,3)
        linux /vmlinuz root=/dev/sda3 ro single
        initrd /initrd.img
}
EOF
```you don't have a [FONT=Arial]search[/FONT] command.  I discovered the hard way what it's for; it sets the root, **overwriting** the set statement the line before, because the "device enumeration" (which drive is [FONT=Arial]hd0[/FONT], which is [FONT=Arial]hd1[/FONT], and so on) can change from boot to boot. People assume, as I had, that [FONT=Arial]hd0[/FONT] is [FONT=Arial]/dev/sda[/FONT], [FONT=Arial]hd1[/FONT] is [FONT=Arial]/dev/sdb[/FONT], and so on, but that can change, indeed it did on my system; [FONT=Arial]hd0[/FONT] became [FONT=Arial]/dev/sdb[/FONT], [FONT=Arial]hd1[/FONT] became [FONT=Arial]/dev/sda[/FONT].

I'm not sure why [FONT=Arial]grub-mkconfig[/FONT] generates the [FONT=Arial]set root[/FONT] statement, since the search overwrites it.  Maybe it's a fallback in case the partition UUID changes.  IMO quite misleading.

The search command doesn't have to use the unwieldy UUID, it can use a label or a file to search for.  

[/FONT]
You are welcome!  :)
Adding the **search** command to this will cause problems.
This way you do not need the **search** command or the **UUID**. Everything that is necessary is inside the boxes.
And the drive/partition cannot be changing on every boot. Unless it is because you have the **search** command 
included after the **set root** command. My ext4 Maverick is on (hd0,3) and has been there since installation. 
The UUID (in the Windows 7 entry) will not change unless you reinstall Windows. My Ubuntu installs have 
remained on the same drive/partition (hd0,3) through many installs. 

My 06_custom has remained the same since Karmic and I have never had any problems.

---

### Post by John Little on 2010-11-12
> **Cavsfan said:**
>  My Ubuntu installs have 
remained on the same drive/partition (hd0,3) through many installs. 

My 06_custom has remained the same since Karmic and I have never had any problems.

Well, it happened to me, thought I'd mention it on the thread in case someone else ended up in the same boat.

---

### Post by von Stalhein on 2010-11-14
G'day Cavsfan,
I managed to get past that little issue I was having with grub, and after going through your very easy to follow tute, have started with this one.

Please excuse the crappy cameraphone quality, I'll take another with my camera when it's here later and replace it.

---

### Post by CowzRule on 2010-11-15
Hi,
Just thought I'd show off my customized Grub menu.

---

### Post by Cavsfan on 2010-11-15
> **von Stalhein said:**
> G'day Cavsfan,
I managed to get past that little issue I was having with grub, and after going through your very easy to follow tute, have started with this one.

Please excuse the crappy cameraphone quality, I'll take another with my camera when it's here later and replace it.


Looks good! Thanks for posting! I guess you didn't make up the **06_custom** file?
If you did, the top entry could say "Maverick Meerkat" or what ever you wanted. That is what is maintenance free about it. 
The line never has to be edited and it will always pull the latest kernel. The same with the other entry for recovery; it will 
always pull the latest kernel. And if you leave the other files executable it will show the normal entries below the custom ones.

Looks great and thanks again for posting! :)

---

### Post by Cavsfan on 2010-11-15
> **CowzRule said:**
> Hi,
Just thought I'd show off my customized Grub menu.

Looks great! Thanks for posting!

---

### Post by von Stalhein on 2010-11-16
> **Cavsfan said:**
> Looks good! Thanks for posting! I guess you didn't make up the **06_custom** file?
If you did, the top entry could say "Maverick Meerkat" or what ever you wanted. That is what is maintenance free about it. 
The line never has to be edited and it will always pull the latest kernel. The same with the other entry for recovery; it will 
always pull the latest kernel. And if you leave the other files executable it will show the normal entries below the custom ones.

Looks great and thanks again for posting! :)

he he - not yet - baby steps

I like to stuff up one thing at a time - the next part of your tute may get a run tonight or tomorrow :-)

I've put a few images in that directory, and when I get bored all I need to do is rename the file and I'll have a change.

Later - I've done the second part of the tute, and after some trial and error got to this stage - next is to remove some of the old entries. Your tip to hang on to a couple for a while is a good one!!

---

### Post by Cavsfan on 2010-11-16
> **von Stalhein said:**
> he he - not yet - baby steps

I like to stuff up one thing at a time - the next part of your tute may get a run tonight or tomorrow :-)

I've put a few images in that directory, and when I get bored all I need to do is rename the file and I'll have a change.

Later - I've done the second part of the tute, and after some trial and error got to this stage - next is to remove some of the old entries. Your tip to hang on to a couple for a while is a good one!!

Very good idea to go slow! Looking good so far! I am down to just 3 entries, but the other day I had 
to make 10_linux executable so I could get into recovery mode because I don't know of a key that will do 
it if there is one. I updated my nVidea driver to the latest and needed to get into command prompt to do part of it.

I also have several pictures in the folder and have the colors and the pictures commented out in the file, except the one I am using.
It makes it easier to switch back and forth and the colors that work with dark pictures are there as well as the colors that work well with 
light pictures. It's always nice to mix it up now and then. :)

Thanks for having the interest to post what your menu looks like. :D

EDIT: DO'h! I already had recovery mode!  I just realized that after I posted this. I didn't need to change anything!

---

### Post by von Stalhein on 2010-11-17
Sounds like me - although I'm getting better at NOT pushing the enter key until I have a plan to get back to where I was!!

I'm down to 5 - the current kernel, its recovery version and XP, but I've also left the two previous kernel entries for insurance.

Thanks again for your work and advice :biggrin:

---

### Post by Cavsfan on 2010-11-17
> **von Stalhein said:**
> Sounds like me - although I'm getting better at NOT pushing the enter key until I have a plan to get back to where I was!!

I'm down to 5 - the current kernel, its recovery version and XP, but I've also left the two previous kernel entries for insurance.

Thanks again for your work and advice :biggrin:


I am down to just Maverick, Maverick Recovery and Windows 7 in the **06_custom** file. I never used the memtest and I am 
confident enough that I do not need **10_linux** or **30_os-prober** to be executable. All I see when I enter **sudo update-grub** is 
the image name appear.

**Ranch Hand**, a very knowledgeable guy showed me how to do all of this stuff and he said he has used just the custom file for a long time.

I have also had it this way ever since **Ranch Hand** showed me how to do it. I think since Karmic.
The only time I could see leaving anything executable; displayable is if you have more than just Ubuntu and one version of Windows.

However, even then you could make the other version of windows fit into the custom file.

But, if you have other Linux OSs on there, you would need those to display. But, since we both only have the afore mentioned setup, 
we can get by with just the custom file.

I believe even **drs305**, the GRUB guru around here has his setup this way, but I am not for sure.

Even if something should run amuck, you can always get into recovery mode or at the worst command line mode and all you would 
have to do is maneuver to **/etc/grub.d/** and make 10_linux executable and viola you can access an older kernel and should be good to go.

I have only one kernel since installing Maverick and would not benefit by making **10_linux** executable anyway.

And while this tutorial is intended for you to eventually have just the 3 entries in a simple dual boot system, I 
do realize that caution rules over anything else. So, what your menu displays is entirely up to you and your machine.

I am going to post my newest screen when I get a chance.

---

### Post by Cavsfan on 2010-11-17
Here is my current GRUB2 screen
 
[[IMG]http://ompldr.org/tNjdpYw[/IMG]]("http://ompldr.org/vNjdpYw")



[[IMG]http://ompldr.org/tNjdpZA[/IMG]]("http://ompldr.org/vNjdpZA")

These colors are normal yellow/black and highlighted white/black
And don't forget that instead of rebooting to see your changes, you can simply press "c" to get a grub command line 
and enter different combinations until you have one that suits your taste. 

Enter ```
set color_normal=first-color/black  and/or set color_highlight=first-color/second-color
```Then press Esc to view the changes and you can repeat until you find the colors you like.

The possible colors are [B]black, light-gray, blue, brown, cyan, dark-gray, light-green, green, light-cyan, light-blue, 
light-magenta, magenta, light-red, red, white and yellow[/B].
And remember to leave the second color black or it may become transparent.
There are a few ways you can use the 2nd color - if you wanted the line to be blue and the text to be white, you could
enter white/blue. I would be careful about trying this though. Generally you want the 2nd color to be black.

---

### Post by von Stalhein on 2010-11-19
^^
Cool!!

My next project is to get another hdd and then I'm going to try triple booting with Maverick, XP and Arch.

---

### Post by von Stalhein on 2010-11-24
Hey Cavsfan - [seen this]("http://lifehacker.com/5696245/burg-gives-your-multi+boot-screen-a-big-facelift")??

I haven't had a chance to research it yet - will be interesting to find out the pros and cons.

---

### Post by Cavsfan on 2010-11-24
> **von Stalhein said:**
> Hey Cavsfan - [seen this]("http://lifehacker.com/5696245/burg-gives-your-multi+boot-screen-a-big-facelift")??

I haven't had a chance to research it yet - will be interesting to find out the pros and cons.

I have seen at least one thread on this forum where someone installed burg and there were problems.
They had to get help. Search for this in google  **site:ubuntuforums.org ubuntu burg**
Myself I am content with Grub2.

---

### Post by von Stalhein on 2010-11-24
Yep, after a bit of reading me too!!

---

### Post by Navalio on 2010-12-07
Very good tutorial, but still could not change the font for grub2 boot menu. Found several thread via google, where the grub-mkfont used, but it did not help. Seems, that needed to insert the module "font" and later to load it in grub2. As well understand, that those commands should be outputted to the grub.conf, but where to insert them? in the 40_custom file or in the 00_header something should be changed? Does anyone really made configuration for different fonts, which remains after the "sudo update-grub" command?

---

### Post by Cavsfan on 2010-12-07
> **Navalio said:**
> Very good tutorial, but still could not change the font for grub2 boot menu. Found several thread via google, where the grub-mkfont used, but it did not help. Seems, that needed to insert the module "font" and later to load it in grub2. As well understand, that those commands should be outputted to the grub.conf, but where to insert them? in the 40_custom file or in the 00_header something should be changed? Does anyone really made configuration for different fonts, which remains after the "sudo update-grub" command?

You don't want to put anything in 40_custom, you want to make your custom entries in 40_custom and then save it as 06_custom, 
leaving 40_custom untouched. That way the custom entries will always be first in the menu. Let me do a bit of checking on your 
font problem. I remember when I did an "upgrade" from Lucid to Maverick, I could not get the font to change. I think it changed but, 
not to what I had expected. I messed my kernel up and ended up doing a clean install and then the fonts worked perfectly. I am not 
implying you need to do that. Let me see what I can find out.

---

### Post by Cavsfan on 2010-12-07
> **Navalio said:**
> Very good tutorial, but still could not change the font for grub2 boot menu. Found several thread via google, where the grub-mkfont used, but it did not help. Seems, that needed to insert the module "font" and later to load it in grub2. As well understand, that those commands should be outputted to the grub.conf, but where to insert them? in the 40_custom file or in the 00_header something should be changed? Does anyone really made configuration for different fonts, which remains after the "sudo update-grub" command?

If you created the font from this tutorial, all you should need to do is add this line to /etc/default/grub via **gksu gedit /etc/default/grub**
```
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2

```It is line number 11 in my file. And of course **sudo update-grub2** or **sudo update-grub** (both the same) to make the changes stick. 
Try that first and see if that takes care of it.
I have not seen any other fonts used. But, if this one will not do as expected, it is not the font causing the problem.

---

### Post by Navalio on 2010-12-07
> **Cavsfan said:**
> If you created the font from this tutorial, all you should need to do is add this line to /etc/default/grub via **gksu gedit /etc/default/grub**
```
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2

```It is line number 11 in my file. And of course **sudo update-grub2** or **sudo update-grub** (both the same) to make the changes stick. 
Try that first and see if that takes care of it.
I have not seen any other fonts used. But, if this one will not do as expected, it is not the font causing the problem.

Thanks for quick reply,
Will check a bit later - just came from work.

EDIT:
Cavsfan, so i followed step-by-step the tutorial and eventually the boot font was changed. So, i found mine mistakes: the variable GRUB_FONT was the last one in the /etc/default/grub , thus (seem for me) the font modules were not loaded, but after moving it on the 1st position mine font appeared. And the 2nd bug, which was in mine box, was that the grub-mkfont configured DejavuSansMono font with errors(?), therefore it was not correctly converted to pf2(converting error was somenthing like "Unknown gsub feature 0x73756273 (subs)
", but i will search for that problem additionally), and only the font from the mscorefonts package finally were adopted to the boot screen.

Thanks for your advises.

---

### Post by Cavsfan on 2010-12-08
> **Navalio said:**
> Thanks for quick reply,
Will check a bit later - just came from work.

EDIT:
Cavsfan, so i followed step-by-step the tutorial and eventually the boot font was changed. So, i found mine mistakes: the variable GRUB_FONT was the last one in the /etc/default/grub , thus (seem for me) the font modules were not loaded, but after moving it on the 1st position mine font appeared. And the 2nd bug, which was in mine box, was that the grub-mkfont configured DejavuSansMono font with errors(?), therefore it was not correctly converted to pf2(converting error was somenthing like "Unknown gsub feature 0x73756273 (subs)
", but i will search for that problem additionally), and only the font from the mscorefonts package finally were adopted to the boot screen.

Thanks for your advises.


Don't worry about those errors when converting the font. I had the same thing and I thought I mentioned that in the tutorial. 
I don't know what they meant, but they didn't effect the font, so I didn't worry about it. My fonts and my Grub2 menu look great!
And I had the font command just after the last line in the first few commands in that file. And that apparently does have a big impact.

If all else fails (although I think you are good now). you could always go by **drs305** Grub2 tutorial and reinstall Grub2 and then 
go through my tutorial from scratch.

I upgraded from Lucid to Maverick and lots of things in Grub were not quite right. I did a clean install, but I could have probably just 
re-installed grub and been OK.
Even after I did a clean install I got the errors converting the font. But, all is well.

---

### Post by morbs_gt on 2010-12-16
Hi there.

Thanks for your post OP.

I have a custom grub2 boot with this change in /etc/default/grub
[PHP]GRUB_CMDLINE_LINUX_DEFAULT=""[/PHP]which means I will still have my boot menu with custom entries and background, and have a verbose bootup.

My question is: is it possible to change the black background behind the verbose bootup? Which files should I look into for this? Thanks.

---

### Post by Cavsfan on 2010-12-16
> **morbs_gt said:**
> Hi there.

Thanks for your post OP.

I have a custom grub2 boot with this change in /etc/default/grub
[PHP]GRUB_CMDLINE_LINUX_DEFAULT=""[/PHP]which means I will still have my boot menu with custom entries and background, and have a verbose bootup.

My question is: is it possible to change the black background behind the verbose bootup? Which files should I look into for this? Thanks.

You are welcome.
Here is what I have: [PHP]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""[/PHP]You should be able to go by step 2 on page one via this command:
**gksu gedit /etc/grub.d/05_debian_theme**
That is where you would put the file name of the picture you want for your background.
I say on page one that it has to be in **/usr/share/images/desktop-base/**, but it
can actually be where ever you want it as long as **WALLPAPER=** in **05_debian_theme** file points to your picture's location.

---

### Post by morbs_gt on 2010-12-19
Yeah, I have the following in **/etc/grub.d/05_debian_theme**
[PHP]# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/grub/Grass_1280x1024.tga"
  COLOR_NORMAL="light-gray/black"
  COLOR_HIGHLIGHT="yellow/black"
fi[/PHP]and everything works fine. I have my custom background and and font color for the boot menu.

What I'm wondering though is, is there a way to change the background of the scrolling text of the verbose boot which follows the grub boot menu selection. I do not wish to display the splash, just the text boot, but would like to edit the background of the scrolling text.

This scrolling text is gray on a black background on my end, and wasn't sure which file to look into for that, or if it is at all possible by simply editing a configuration file.

Thanks for your reply though. :)

---

### Post by tech-hero on 2010-12-20
> **SkulblakaSama said:**
> After I have done what you said; "Then click on **Nautilus Settings **and put a check mark beside **Open Folder with root privileges**." I keep on getting this... 
 
andrey@andrey-desktop:~$ update-grub
/usr/sbin/grub-mkconfig: You must run this as root
 
Is there a fix? What happened that this occurred? :?
 
i think you must run it as SUDO
 
example:
 
sudo update-grub

---

### Post by Cavsfan on 2010-12-20
> **morbs_gt said:**
> Yeah, I have the following in **/etc/grub.d/05_debian_theme**
[PHP]# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/grub/Grass_1280x1024.tga"
  COLOR_NORMAL="light-gray/black"
  COLOR_HIGHLIGHT="yellow/black"
fi[/PHP]and everything works fine. I have my custom background and and font color for the boot menu.

What I'm wondering though is, is there a way to change the background of the scrolling text of the verbose boot which follows the grub boot menu selection. I do not wish to display the splash, just the text boot, but would like to edit the background of the scrolling text.

This scrolling text is gray on a black background on my end, and wasn't sure which file to look into for that, or if it is at all possible by simply editing a configuration file.

Thanks for your reply though. :)

That question would probably be better suited for **drs305** the GRUB2 guru around here.
Post the question in his GRUB2 Basics thread: [[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")
I am sure if there is an answer, **drs305** will know what it is.

---

### Post by Cavsfan on 2010-12-20
> **SkulblakaSama said:**
> After I have done what you said; "Then click on **Nautilus Settings **and put a check mark beside **Open Folder with root privileges**." I keep on getting this... 

andrey@andrey-desktop:~$ update-grub
/usr/sbin/grub-mkconfig: You must run this as root

Is there a fix? What happened that this occurred? :?

> **tech-hero said:**
> i think you must run it as SUDO
 
example:
 
sudo update-grub

That question was answered in the subsequent post on August 2, 2010. But, thanks tech-hero.

---

### Post by morbs_gt on 2010-12-20
> **Cavsfan said:**
> That question would probably be better suited for **drs305** the GRUB2 guru around here.
Post the question in his GRUB2 Basics thread: [[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")
I am sure if there is an answer, **drs305** will know what it is.

Thanks for that, I'll give it a shot :)

---

### Post by drs305 on 2010-12-20
You could post it there but I can't answer it.  ;-)

That process is somewhere after Grub2 passes control over to the kernel. The Grub devs are making strides with the gfxmode and retaining settings throughout the entire boot but I haven't seen anything about colors or backgrounds, just text size. 

That's not to say it's not being worked on or that there isn't a way to do it, it's just not something I'm familiar with.  If you find out, please share it with us.

---

### Post by Cavsfan on 2010-12-21
> **drs305 said:**
> You could post it there but I can't answer it.  ;-)

That process is somewhere after Grub2 passes control over to the kernel. The Grub devs are making strides with the gfxmode and retaining settings throughout the entire boot but I haven't seen anything about colors or backgrounds, just text size. 

That's not to say it's not being worked on or that there isn't a way to do it, it's just not something I'm familiar with.  If you find out, please share it with us.

Thanks for clarifying that drs305. I was lost at "scrolling text of the verbose boot which **follows** the grub boot menu selection."
But, I guess I should have recognized that it was after grub. I just knew you would have more of a clue as to what it was about.

And about that part I was right. I don't even know what "That process is somewhere after Grub2 passes control over to the kernel." is.
I'm still clueless! :o That's a bit over my head.

---

### Post by morbs_gt on 2010-12-21
Thanks for the replies, and sorry for the "reposts". If I stumble across anything I'll make sure to let you know. :)

*edit: Ok, so it looks like the messages displayed are due to **decompress_kernel()**.
Also, upon further searching, I've found [this old tutorial]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=177785") and will see it it works for me. It does involve patching and recompiling the kernel.

A little extra to this method seems to be: "One thing to note is if you login  under console mode, you will see the verbose image in the background of  your console.  Kinda neat!"

However this is related to boot eyecandy, sorry for the threadjacking, as patching kernels isn't really a maintenance-free thing.

---

### Post by von Stalhein on 2010-12-23
OK Cavsfan my old fruit - an update came through this evening, and ```
uname -a
``` gives ```
Linux ubuntu 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux
```as the running kernel at present.

However, it should be 2.6.35-24

What's the best way of ensuring that the updated kernel goodness is utilised?

---

### Post by drs305 on 2010-12-23
> **von Stalhein said:**
> What's the best way of ensuring that the updated kernel goodness is utilised?

I'm assuming your custom menu menuentry has "linux /vmlinuz ... " so the latest kernel is used.


Without posting your files, check these commands:
```
ls /boot | grep "vmlinuz-2.6.35"
```
Does the -24 kernel show up?

Next, look at your existing menuentries:
```
grep 'menuentry' /boot/grub/grub.cfg | nl --starting-line-number=0 && grep "GRUB_DEFAULT=" /etc/default/grub
```
Does the GRUB_DEFAULT number match the -24 menuentry number?

---

### Post by Cavsfan on 2010-12-23
Thanks **drs305**! I have also noticed that whatever kernel is installed last becomes the most recent kernel.
```
ls /boot | grep "vmlinuz-2.6.35"
```Yields 
```
[COLOR=Red]vmlinuz-2.6.35[/COLOR]-22-generic
[COLOR=Red]vmlinuz-2.6.35[/COLOR]-23-generic
[COLOR=Red]vmlinuz-2.6.35[/COLOR]-24-generic
```I was having trouble with 23-generic. The coretemp driver for my 3rd CPU core temp was gone when 23-generic was installed.
So, I went through purging and re-installing some kernels. And noticed that if I manually installed 22 last, it became the 
most "recent" kernel. Even though it was not numerically the highest number.

That doesn't sound like **von Stalhein**'s problem though as it sounds like 24 should be the most recent.
And I appreciate your input as you know way more than I do about this stuff. :)

---

### Post by drs305 on 2010-12-23
Cavsfan,

You make an excellent point that the /vmlinuz link points to the most recently-*installed* kernel, not necessarily the most recently-*released* kernel. The /vmlinuz symlink is created in the kernel's post-installation script. It's an important point that I sometimes don't include in posts regarding the use of '/vmlinuz'.

---

### Post by Cavsfan on 2010-12-23
> **drs305 said:**
> Cavsfan,

You make an excellent point that the /vmlinuz link points to the most recently-*installed* kernel, not necessarily the most recently-*released* kernel. The /vmlinuz symlink is created in the kernel's post-installation script. It's an important point that I sometimes don't include in posts regarding the use of '/vmlinuz'.

I learned it by accident, which is my main way - the hard way! Glad I could contribute something. I don't know a whole lot, but I know a little bit. :D

---

### Post by von Stalhein on 2010-12-23
Thanks guys - as below:


```
vmlinuz-2.6.35-22-generic
vmlinuz-2.6.35-23-generic
vmlinuz-2.6.35-24-generic

```

So it is there, but 

```
 0	menuentry "Ubuntu Maverick Meerkat 10.10" {
     1	menuentry "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" {
     2	menuentry "Ubuntu Maverick Meerkat Kernel - 2.6.32-25" {
     3	menuentry "Ubuntu Maverick Meerkat Kernel - 2.6.32-25 (recovery mode)" {
     4	menuentry "Microsoft Windows XP Home (loader) (on /dev/sda1)" {
GRUB_DEFAULT=0

```

shows that I may have been a bit zealous in my customisation.

Do I need to specify the kernel in the GRUB_DEFAULT=0 line better? 
/end obvious question/

---

### Post by Cavsfan on 2010-12-23
> **von Stalhein said:**
> Thanks guys - as below:


```
vmlinuz-2.6.35-22-generic
vmlinuz-2.6.35-23-generic
vmlinuz-2.6.35-24-generic

```So it is there, but 

```

     0    menuentry "Ubuntu Maverick Meerkat 10.10" {
     1    menuentry "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" {
     2    menuentry "Ubuntu Maverick Meerkat Kernel - 2.6.32-25" {
     3    menuentry "Ubuntu Maverick Meerkat Kernel - 2.6.32-25 (recovery mode)" {
     4    menuentry "Microsoft Windows XP Home (loader) (on /dev/sda1)" {
GRUB_DEFAULT=0

```shows that I may have been a bit zealous in my customisation.

Do I need to specify the kernel in the GRUB_DEFAULT=0 line better? 
/end obvious question/

No, you have it setup right. The whole point of my tutorial is that the top entry will always start the last installed kernel.
Or else it would be of no value if you had to edit your menu every time a kernel is installed.
As drs305 stated, is your custom entry in **06_custom** like this?:

```
echo "Adding Ubuntu Maverick Meerkat 10.10" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat 10.10" {
    set root=(hd0,3)
        [COLOR=Red]linux /vmlinuz root=/dev/sda3 ro quiet splash[/COLOR]
        initrd /initrd.img
}
EOF
```Of course with the [COLOR="Red"]sdxx[/COLOR] to match your system.
If so and **2.6.35-24-generic** is the last installed kernel, try **sudo update-grub** and see if that fixes it.
That is not always automatically accomplished when a new kernel is installed.

---

### Post by Cavsfan on 2010-12-23
If all of the above still doesn't get it to boot into the **vmlinuz-2.6.35-24-generic** kernel with the default top line executed at startup
Post the output of **sudo grub-mkconfig** here because I have my **10_linux** unexecutable and if I make it executable, my output looks a lot different than yours.

With it executable to show all installed kernels mine looks like this:

```

     0	menuentry "Ubuntu Maverick Meerkat 10.10" {
     1	menuentry "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" {
     2	menuentry "Windows 7 (loader) (on /dev/sda1)" {
     3	menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
     4	menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
     5	menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
     6	menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
     7	menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
     8	menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
```

With **10_linux** unexecutable (my normal boot), my output looks like this:
```
     0	menuentry "Ubuntu Maverick Meerkat 10.10" {
     1	menuentry "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" {
     2	menuentry "Windows 7 (loader) (on /dev/sda1)" {

```

---

### Post by von Stalhein on 2010-12-24
In the interim I've manually changed the kernel number, and it's booted into it ok - no surprises there.

Obviously I have something in the script wrong as there's no automagic update.

_**06_custom**_
```
echo "Ubuntu Maverick Meerkat 10.10" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat 10.10" {
    recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
```

_**mkconfig**_
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
}

insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768-32
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
Found background image: grubsplash.jpg
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
insmod jpeg
if background_image /usr/share/images/desktop-base/grubsplash.jpg ; then
  set color_normal=white/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Ubuntu Maverick Meerkat 10.10" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat 10.10" {
    recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
EOF
echo "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" {
    recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
EOF
echo "Ubuntu Maverick Meerkat - Kernel 2.6.35-22" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat Kernel - 2.6.35-22" {
    recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
EOF

echo "Ubuntu Maverick Meerkat Kernel - 2.6.35-22(recovery mode)" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat Kernel - 2.6.35-22 (recovery mode)" {
    recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
EOF

echo "Microsoft Windows XP Home (loader)" >&2 
cat << EOF
menuentry "Microsoft Windows XP Home (loader) (on /dev/sda1)" {
    insmod part_msdos    
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01c3d871f965ac80
    chainloader +1
}
EOF
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

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
done

```

edit: And it would be remiss of me not to wish you all a Merry Christmas and Happy New Year -  the bloke in the Red Suit will be hereabouts in around 2 hrs :D Huzzah!!!!

---

### Post by drs305 on 2010-12-24
von Stalhein,

I wasn't sure if you were posting your modified custom entry or not. The custom menuentry to provided an automatic entry for the latest installed kernel would look like this:
> 
menuentry "Ubuntu Maverick Meerkat 10.10" {
    recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	[COLOR="Red"]/vmlinuz[/COLOR] root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	[COLOR="Red"]/initrd.img[/COLOR]
}


---

### Post by Cavsfan on 2010-12-25
I do not even have any UUIDs in my 06_custom file, except for Windows 7, which apparently has to have it.
And mine works just fine. 
von Stalhein, what you posted as your 06_custom file does not match the output of mkconfig.
There it appears to show your 5 entries in 06_custom.

All you really need is what I have below with the UUID for windows XP on the bottom entry.
And of course with the "set root=" and sdxx changed to match your hard drives/partitions.
Then if you want to see the other kernels that are installed (I do this temporarily as needed) simple enter: 
**sudo chmod +x /etc/grub.d/10_linux && sudo update-grub**

That in addition to having your top 2 entries as drs305 stated (to pull the most recently installed kernel).

My **06_custom**

[PHP]#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Ubuntu Maverick Meerkat 10.10" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat 10.10" {
    set root=(hd0,3)
        linux /vmlinuz root=/dev/sda3 ro quiet splash
        initrd /initrd.img
}
EOF
echo "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" {
    set root=(hd0,3)
        linux /vmlinuz root=/dev/sda3 ro single
        initrd /initrd.img
}
EOF
echo "Windows 7 (loader)" >&2 
cat << EOF
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1cfc7a8dfc7a60c6
    chainloader +1
}
EOF[/PHP]

---

### Post by von Stalhein on 2010-12-27
OK guys,
the ```
grep 'menuentry' /boot/grub/grub.cfg | nl --starting-line-number=0 && grep "GRUB_DEFAULT=" /etc/default/grub
``` command (after the update-grub command you suggested above) now gives:
```
0	menuentry "Ubuntu Maverick Meerkat 10.10" {
     1	menuentry "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" {
     2	menuentry "Ubuntu Maverick Meerkat Kernel - 2.6.35-22" {
     3	menuentry "Ubuntu Maverick Meerkat Kernel - 2.6.35-22 (recovery mode)" {
     4	menuentry "Microsoft Windows XP Home (loader) (on /dev/sda1)" {
     5	menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
     6	menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
     7	menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
     8	menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
     9	menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    10	menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    11	menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    12	menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
GRUB_DEFAULT=0

```
and the 06_custom is 
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Ubuntu Maverick Meerkat 10.10" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat 10.10" {
    recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
EOF
echo "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat 10.10 (Recovery Mode)" {
    recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
EOF
echo "Ubuntu Maverick Meerkat - Kernel 2.6.35-22" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat Kernel - 2.6.35-22" {
    recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
EOF

echo "Ubuntu Maverick Meerkat Kernel - 2.6.35-22(recovery mode)" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat Kernel - 2.6.35-22 (recovery mode)" {
    recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set b362ac08-3495-40da-8589-20eb502bca5d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b362ac08-3495-40da-8589-20eb502bca5d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
EOF

echo "Microsoft Windows XP Home (loader)" >&2 
cat << EOF
menuentry "Microsoft Windows XP Home (loader) (on /dev/sda1)" {
    insmod part_msdos    
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01c3d871f965ac80
    chainloader +1
}
EOF
```

I'll see what happens when the next kernel update comes through.

---

### Post by Cavsfan on 2010-12-27
You only need 3 entries in 06_custom: one for Ubuntu, one for Ubuntu Recovery and one for Windows XP.
You have hard coded kernel 22 as your 3rd and 4th custom menu entries. And you do not need the UUID [COLOR=Blue]b362ac08-3495-40da-8589-20eb502bca5d[/COLOR] on the Ubuntu entries.
This is all you need (with the red drive/partition changed to match your system) for the 1st entry:
```
echo "Ubuntu Maverick Meerkat 10.10" >&2 
cat << EOF
menuentry "Ubuntu Maverick Meerkat 10.10" {
    set root=(hd[COLOR="Red"]0,3[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR="Red"]a3[/COLOR] ro quiet splash
        initrd /initrd.img
}
EOF
```

You can pretty much copy and paste from the 1st page of this tutorial into your 06_custom file. 
Changing the red above for the first 2 menu entries and the UUID for your windows XP entry to match your system.
There are 8 lines for the 2 Ubuntu menu entries and 9 lines for the Windows entry.

The output of your grep command shows that the 24 kernel is the latest one, which should be the one running 
from the default top line. It could have been something as simple as **sudo update-grub** was not entered after the 24 kernel was installed.
I try to watch when a new kernel is installed to see if that command is executed. It will list your picture was found if it is.

I don't have **10_linux** executable, so my output of **sudo update-grub** is this:

```
Generating grub.cfg ...
Found background image: family_guy.jpg
done
```

---

### Post by von Stalhein on 2010-12-28
Thanks again Cavsfan and drs305 for your patience and assistance.

I think I have it sorted. I have the current release kernel operating without it being particularly specified, and the  output from sudo update-grub is as as exampled by Cavsfan in the post above.

I've maintained a couple of the older kernels just for a backup if something goes pear shaped.

I tried your version Cavsfan without the UUID etc and kept getting an error - "must load the kernel first" so I've mixed both the suggestions from you and drs305 to get the current working config - and as far as I can see there should be no impediment to it automagically updating when required.

Other than me that is!!!

---

### Post by Cavsfan on 2010-12-28
> **von Stalhein said:**
> Thanks again Cavsfan and drs305 for your patience and assistance.

I think I have it sorted. I have the current release kernel operating without it being particularly specified, and the  output from sudo update-grub is as as exampled by Cavsfan in the post above.

I've maintained a couple of the older kernels just for a backup if something goes pear shaped.

I tried your version Cavsfan without the UUID etc and kept getting an error - "must load the kernel first" so I've mixed both the suggestions from you and drs305 to get the current working config - and as far as I can see there should be no impediment to it automagically updating when required.

Other than me that is!!!

Glad you have it working. I don't understand why it gives you that error without the UUID as that was how I was told to do it 
and it has always worked well for me. :-k But, you can't go wrong with drs305's example.

I have it set up with just the 3 entries, but also keep some extra kernels lying around just in case. 
I just copy and paste this from step 6 on page one to make the other kernels display:
**sudo chmod +x /etc/grub.d/10_linux && sudo update-grub**.
Then when all is OK, I change the **+x** to **-x** and make them not display.

Like I mentioned, after a new kernel gets installed, just make sure **sudo update-grub** gets executed and you should be good. :D

---

### Post by fenario on 2010-12-29
Hi friends

I noticed that in all conf files hd0,1 = sda1

that is not so. when talking hd0,x we start counting at 0
when talking sdax we start counting at 1
hence sda1 = hd0,0 (not hd0,1)
it seems that it doesn't matter as the drive is described as UUID=f7686rnv9877s6 et c. anyway and that won't change even if partitions get deleted and the numbering moves 1 back, say sda7 becomes sda6 if partition sda5 was deleted

now there is a newer system which is:
sda1 = hd0,msdos1
seems to make better sense
I personally use the old grub on it's own partition and tweak it manually
as I don't like the confusion of grub2, like when I installed puppy it just called it 'unknown linux' and that don't look proper to me
by the way grub.config is read only and needs to be made read and write before tweaking and then set to read only again

but just now I found the application Grub Customizer
it may be of help too

happy tweaking

here is my grub menu;

default		0
timeout		7
Pretty colours

color cyan/blue red/green

##on /dev/sda8

title		Ubuntu  10.10,kernel 2.6.35-24 GNOME 

root		(hd0,7)

kernel		/boot/vmlinuz-2.6.35-24-generic root=/dev/sda8 ro  

initrd		/boot/initrd.img-2.6.35-24-generic

savedefault

boot


# on /dev/sda1

title		Microsoft Windows    XP-SP3 Home

rootnoverify	(hd0,0)

savedefault

makeactive

chainloader	+1

# linux installation on /dev/sda7

title           Puppy-Linux 4,kernel 2.6.30-5  XFCE

root            (hd0,6)

kernel          /boot/vmlinuz root=/dev/sda7 pmedia=idehd nosmp acpi=force

savedefault

boot

# linux installation on /dev/sda9

title           Puppy-Linux 5,kernel 2.6.33.2  JWM

root            (hd0,8)

kernel          /boot/vmlinuz root=/dev/sda9 ro vga=normal

savedefault

boot

##on /dev/sda8

title		Ubuntu  10.10,kernel 2.6.35-24 Recovery

root		(hd0,7)

kernel		/boot/vmlinuz-2.6.35-24-generic root=/dev/sda8 ro single 

initrd		/boot/initrd.img-2.6.35-24-generic

savedefault

boot

---

### Post by Cavsfan on 2011-01-26
I recently went back to Lucid from Maverick.
My latest screen with yellow as normal and white as highlighted colors:

[[IMG]http://ompldr.org/tNzV0cQ[/IMG]]("http://ompldr.org/vNzV0cQ")

---

### Post by Cavsfan on 2011-03-29
Decided it was time to change my screen and here it is (12.1MB picture):

[[IMG]http://ompldr.org/tODB1Ng[/IMG]]("http://ompldr.org/vODB1Ng")

While you can see the font size is quite large and readable, here is a closeup of the options:

[[IMG]http://ompldr.org/tODB1YQ[/IMG]]("http://ompldr.org/vODB1YQ")

I left the colors the same (white as highlight and yellow as other), I may jack with those, but for right now they are fine.

And yes I [COLOR="Red"]do[/COLOR] know that there is a [COLOR="Red"]GUI[/COLOR] for doing this. Haven't tried it, don't know if it does exactly the same thing and don't care as long as this method still works.
I think this method is the bees knees...

---

### Post by drs305 on 2011-03-29
Hehe. At first glance I thought I was seeing a skull looking lower left. Then it reminded me of the time someone said one of the earlier release's backgrounds (high altitude desert shot) looked like a skull. I could never look at that screen again without seeing the skull. 

I've played a bit with Customizer and it's a great tool for those not comfortable with editing the scripts, but I'm still a tinkerer too.

---

### Post by Cavsfan on 2011-03-30
LOL! I am not sure what kind of bird it is, but it looks sort of like an eagle. Not too sure about the colors though. I just call it dark blue bird!

I am glad someone came up with a GUI as I guess it appears a bit daunting to some people doing it this way. It did to me at first until I learned more about it.
I still prefer CLI myself.

But, then I was a programmer/analyst for many years. I lost the attention of many a friend trying to explain what I was currently working on at work. LOL!
Some people don't care how things work, they just care that they work. I like tinkering myself too.

---

### Post by seanbw on 2011-04-14
Than you for this tutorial. I used it to have a background picture that actually works even though I have been trying for months now. Not sure I can post it. A bit racy. but it looks lovely. thanks to you and drs305.

---

### Post by Cavsfan on 2011-04-15
> **seanbw said:**
> Than you for this tutorial. I used it to have a background picture that actually works even though I have been trying for months now. Not sure I can post it. A bit racy. but it looks lovely. thanks to you and drs305.

You are very welcome! I am glad you found it useful! :D

---

### Post by Cavsfan on 2011-04-21
Loving it! Today I got the latest kernel for Lucid: linux-headers-2.6.32-31, linux-headers-2.6.32-31-generic and linux-image-2.6.32-31-generic.
And as always the top menu selection pulls in this latest kernel.

I don't have to change my default line number or any of that. Sweet! :popcorn:

---

### Post by Halfling Rogue on 2011-12-27
I had a custom xrandr setup on my original install and making these grub changes lost it. The original grub mkconfig had this in it:

```
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 0e8ef373-799f-4d11-8cca-3d8b4d4b6a94
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
```

Is there a way to add that to the file? I tried repeating my steps from when I first added the drivers, but xrandr isn't behaving the same way for some reason:

```
$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
$ xrandr --newmode "CUSTOM" 85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
$ xrandr --addmode default "CUSTOM"
$ xrandr --output default --mode "CUSTOM"
xrandr: screen cannot be larger than 1024x768 (desired size 1368x768)
```

Before it let me do it thanks to xserver-xorg-video-intel, linux-image-generic-lts-backport-natty, and linux-headers-generic-lts-backport-natty, but those don't seem to be applying any more with the new grub.

---

### Post by Cavsfan on 2011-12-28
> **Halfling Rogue said:**
> I had a custom xrandr setup on my original install and making these grub changes lost it. The original grub mkconfig had this in it:

```
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 0e8ef373-799f-4d11-8cca-3d8b4d4b6a94
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
```Is there a way to add that to the file? I tried repeating my steps from when I first added the drivers, but xrandr isn't behaving the same way for some reason:

```
$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
$ xrandr --newmode "CUSTOM" 85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
$ xrandr --addmode default "CUSTOM"
$ xrandr --output default --mode "CUSTOM"
xrandr: screen cannot be larger than 1024x768 (desired size 1368x768)
```Before it let me do it thanks to xserver-xorg-video-intel, linux-image-generic-lts-backport-natty, and linux-headers-generic-lts-backport-natty, but those don't seem to be applying any more with the new grub.


I don't have any knowledge about xrandr. Perhaps you could ask drs305 on his Grub2 thread:
[[COLOR=blue]_The Grub 2 Guide by drs305_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by drs305 on 2011-12-28
> **Cavsfan said:**
> I don't have any knowledge about xrandr. Perhaps you could ask drs305 on his Grub2 thread:
[[COLOR=blue]_The Grub 2 Guide by drs305_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

Hehe. I was waiting to learn about it in this thread. I don't have an answer. :(

---

### Post by Cavsfan on 2011-12-28
> **cavsfan said:**
> i don't have any knowledge about xrandr. Perhaps you could ask drs305 on his grub2 thread:
[[COLOR=blue]_the grub 2 guide by drs305_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

> **drs305 said:**
> hehe. I was waiting to learn about it in this thread. I don't have an answer. :(

LOL! I did a little research and found this solved thread:

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1724926_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1724926")

Your setup doesn't sound very generic though. Your sig. says Ubuntu 10.04 Lucid Lynx, you added xrandr and you mention Natty in the list of files at the bottom of your post.
I left my setup pretty generic Lucid Lynx with the exception of I have the most current nVidia driver installed.
I also have a script that installs the nVidia driver into a new kernel install (got that from a how to in this forum).

That thread just says that it opened another thread in the  "Multimedia & Video" and "Networking & Wireless" forums.
But, it mentions that xrandr does not work very well with nVidia hardware.
Do you have an ATI card and why is it you feel the need for xrandr? 

I have mixed things up and ended up having to do a clean install every time.
Which is why I went back to the LTS and am leaving it as generic as possible.

Let us know if you find a solution or if you can just get rid of xrandr.  
Good Luck! :)


EDIT: I do not even find xrandr in Synaptic Package Manager on my system.

---

### Post by Cavsfan on 2012-01-07
My latest grub2 screen. They get boring after a while and so I change them.


I guess my latest screen mysteriously came back. Sweet!

[[IMG]http://ompldr.org/tYzRoNg[/IMG]]("http://ompldr.org/vYzRoNg")

---

### Post by Cavsfan on 2012-01-26
If any one wants to post their Grub2 screen on here, feel free. I posted my most current one  "Dread Dog" above.
I know it is a pain because you have to use a camera and upload it.

---

### Post by Cavsfan on 2012-03-22
I just added kernel Linux 2.5.32-40 and rebooted. It came up as the default. No changes necessary. 
Pretty sweet. :guitar:

---

### Post by Roasted on 2012-03-22
Hi there. I'm questioning how user friendly we can make the grub boot screen for Win/Ubu dual booters in our environment. I have the idea of Deja Dup in my head, where the main screen is "BACKUP" and "RESTORE". Two giant buttons.

Is there a way to cut out recovery mode and everything else and get a screen looking like that? Or am I still dreaming? :p

---

### Post by Cavsfan on 2012-03-22
> **Roasted said:**
> Hi there. I'm questioning how user friendly we can make the grub boot screen for Win/Ubu dual booters in our environment. I have the idea of Deja Dup in my head, where the main screen is "BACKUP" and "RESTORE". Two giant buttons.

Is there a way to cut out recovery mode and everything else and get a screen looking like that? Or am I still dreaming? :p

Not sure how you could make it any more simpler than this. 

If you look at my screen on this post, you'll see I have just 3 entries: Lucid Lynx, Lucid Lynx (Recovery) and Windows 7 and nothing else.

[[COLOR=blue]_http://ubuntuforums.org/showpost.php?p=11594281&postcount=105_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11594281&postcount=105")

If this is not what you're looking for, you should look at some of **drs305**'s links. He knows a lot about grub2.
[[COLOR=blue]_The Grub 2 Guide by drs305_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

Item number 20 on that page provides all of the links.

---

### Post by Naruto Man on 2012-04-01
I have 4 questions  :

- How to know my grub resolution (i am Ubuntu 11.10)
- How to customize the top title in the GRUB (see attachments)
- If i want to remove these settings is it safe to remove the 06_custom file
- I  have another Linux distribution (linux-deepin) so how to make the 4 lines-box for it ???

---

### Post by Cavsfan on 2012-04-01
> **Naruto Man said:**
> I have 4 questions  :

- How to know my grub resolution (i am Ubuntu 11.10)
- How to customize the top title in the GRUB (see attachments)
- If i want to remove these settings is it safe to remove the 06_custom file
- I  have another Linux distribution (linux-deepin) so how to make the 4 lines-box for it ???

1) Step 1 page one sets the Grub2 resolution in the **/etc/default/grub** file.
2) I am not aware that there is a way to change the top title.
3) Yes, you could just delete the **06_custom** file. But you want to make sure you have made **/etc/grub.d/10_linux** executable 
first via this command **sudo chmod +x /etc/grub.d/10_linux**
The same would apply to **/etc/grub.d/30_os-prober** and **/etc/grub.d/20_memtest86+** if you want that to be displayed too.
Then of course you want to enter **sudo update-grub** after changing anything in Grub2.
4) As far as adding the other distros; I am not exactly sure.
You could pose that question in **drs305**'s Grub2 Thread. I am sure he would know the answer. He knows quite a bit about Grub.
[[color=blue]_The Grub 2 Guide by drs305_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1195275)

Post #105 in this thread shows my current Grub2 screen.
I have made these changes to Jaunty Jackalope Ubuntu 9.04, Karmic Koala Ubuntu 9.10, Lucid Lynx 10.04 and Maverick Meerkat 10.10, 
but I decided to revert back to Lucid Lynx 10.04 LTS.
I have not heard any complaints that this tutorial will not work on the more recent versions,
I plan on switching to Precise Pangolin 12.04 after it has been out a while.

Good luck and if there is anything about this tutorial I can help you with other than adding other distros, feel free to post here.

---

### Post by drs305 on 2012-04-01
@ Naruto Man,

I read your Question #4 and then downloaded the 11.12 version of linux-deepin. I can't read Chinese so I couldn't review the documentation, but I did mount the ISO and inspect it's contents.

*linux-deepin* is based on Debian and apparently Ubuntu, and the ISO file structure is the same as Ubuntu's. That leads me to believe the installed version will be very similar to Ubuntu.

If that is the case, you can create a custom menu and use the example Cavsfan provides in his first post. Just change the items in red, make the custom file executable (or add the contents to an existing custom menu) and I am fairly confident it will boot.

---

### Post by Naruto Man on 2012-04-02
@[[COLOR=#d40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")
you mean something like that :
```
echo "Linux Deepin 11.12" >&2
cat << EOF
menuentry "Linux Deepin 11.12" {
         set root=(hd0,4
         linux /vmlinuz root=/dev/sda4 ro quiet splash
         initrd /initrd.img }
EOF
```


and i want to know the meaning of these 2 lines :
```
search --no-floppy --fs-uuid --set 1cfc7a8dfc7a60c6
chainloader +1

```[FONT=monospace]and this line from Linux box[/FONT] :
```
initrd /initrd.imgand
```@[Cavsfan]("http://ubuntuforums.org/member.php?u=889820")
i didn't want to set GRUB resolution but i want to know the GRUB resolution from a command line or something else

                                                                                                                                                  Thanks

---

### Post by Cavsfan on 2012-04-02
> **Naruto Man said:**
> @[[COLOR=#d40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")
you mean something like that :
```
echo "Linux Deepin 11.12" >&2
cat << EOF
menuentry "Linux Deepin 11.12" {
         set root=(hd0,4
         linux /vmlinuz root=/dev/sda4 ro quiet splash
         initrd /initrd.img }
EOF
```and i want to know the meaning of these 2 lines :
```
search --no-floppy --fs-uuid --set 1cfc7a8dfc7a60c6
chainloader +1

```[FONT=monospace]and this line from Linux box[/FONT] :
```
initrd /initrd.imgand
```@[Cavsfan]("http://ubuntuforums.org/member.php?u=889820")
i didn't want to set GRUB resolution but i want to know the GRUB resolution from a command line or something else

                                                                                                                                                  Thanks

Thanks **drs305** for providing that information. That makes sense.

**Naruto Man**, if you do not change the resolution and leave that line commented out (default)
the resolution is 640x480.
I don't know of a way at boot up (displaying Grub2 menu) to display the possible resolutions. I don't think 
it is possible.


Here is a bit of information on changing resolutions:
[[COLOR=blue]_Changing resolutions in Grub2._[/COLOR]]("https://help.ubuntu.com/community/Grub2#Changing_Resolutions_w.2BAC8_Splash_Images")

There is a lot of information about Grub2 on that page. Just above that spot is the possible colors that you can change the text to.

---

### Post by Cavsfan on 2012-04-02
> **Naruto Man said:**
> 
and i want to know the meaning of these 2 lines :
```
search --no-floppy --fs-uuid --set 1cfc7a8dfc7a60c6
chainloader +1

```[FONT=monospace]and this line from Linux box[/FONT] :
```
initrd /initrd.imgand
```
Those 2 lines pertain to and are necessary for booting into Windows.

I am not sure about the other line or where you got that from. We'll wait on **drs305** for that answer.

---

### Post by drs305 on 2012-04-02
> **Naruto Man said:**
> @[[COLOR=#d40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")
you mean something like that :
```
echo "Linux Deepin 11.12" >&2
cat << EOF
menuentry "Linux Deepin 11.12" {
         set root=(hd0,4**[COLOR="Red"])[/COLOR]**
         linux /vmlinuz root=/dev/sda4 ro quiet splash
         initrd /initrd.img }
EOF
```


Don't forget the parenthesis I've added in **[COLOR="Red"]bold red[/COLOR]** the second line of the menuentry.

> 
and i want to know the meaning of these 2 lines :
```
search --no-floppy --fs-uuid --set 1cfc7a8dfc7a60c6
chainloader +1

```

The 'chainloader' line is, as CavsFan states, normally used for Windows. It passes control to another bootloader. It can actually be used to pass control to a Grub installation on a partition rather than the MBR, but you don't want to do this.

The 'search' line is used by Grub to look for some of the Grub files, Since you already know where the files are, and are making a custom entry for them, you may not need to add this line but it won't hurt and can help in some situations. If you do add the 'search' line make sure you substitute the UUID of the linux-deepin partition for the one in the example.

> 
[FONT=monospace]and this line from Linux box[/FONT] :
```
initrd /initrd.imgand
```@[Cavsfan]("http://ubuntuforums.org/member.php?u=889820")

That looks like a typo in which an extra "and" was typed on the line. The last line in the menuentry should be:
> initrd /initrd.img
i didn't want to set GRUB resolution but i want to know the GRUB resolution from a command line or something else
                                                                  Thanks[/QUOTE]

If you haven't made any changes in the /etc/default/grub file, the resolution is set automatically by grub. Grub is supposed to set the 'optimum' resolution but I don't know how it determines which is optimum - I don't know if it's the highest supported resolution or something else.

You can check the supported resolutions available to Grub as the computer boots by going to the Grub command line. When you see the Grub menu, press 'c' to go to the command line. Then type "vbeinfo" and all the resolutions available to Grub should be displayed.  Typing "set" shows the current settings.

---

### Post by Cavsfan on 2012-05-28
I just updated it to triple booting Ubuntu Lucid Lynx 10.04, Xubuntu 12.04 and Windows 7.
I'll try to add a picture as soon as I can.

---

### Post by Cavsfan on 2012-05-28
I just added a picture of my latest tri-boot grub2 screen at the bottom of the How to. It will never have to be touched.
The text that is displayed for each menu entry is entirely up to you. I left off the version numbers and just put the names.

---

### Post by Cavsfan on 2012-06-12
Here is my newest grub screen. It never has to be modified.
My grub files are on Lucid Lynx. It defaults to Windows 7 for my wife in case it reboots.

[[img]http://ompldr.org/tZTl2dA[/img]](http://ompldr.org/vZTl2dA)

---

### Post by ChinaJustin on 2012-06-17
Ran into a problem when I ran ¨sudo update-grub¨.  Here´s the output:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 74
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done

```

Here is my current 06_custom file:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Lubuntu Precise Pangolin 12.04" >&2 
cat << EOF
menuentry "Lubuntu Precise Pangolin 12.04" {
    set root=(hd0,msdos2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
EOF
echo "Lubuntu Precise Pangolin 12.04 (Recovery Mode)" >&2 
cat << EOF
menuentry "Lubuntu Precise Pangolin 12.04 (Recovery Mode)" {
    set root=(hd0,msdos2)
        linux /vmlinuz root=/dev/sda2 ro single
        initrd /initrd.img
}
EOF
echo "Windows XP" >&2 
cat << EOF
menuentry "Windows XP" {
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9AB84DC1B84D9C9F
    chainloader +1
}
EOF
```

I haven´t rebooted yet, because I´m afraid of grub not liking the error and having issues. Ideas?

---

### Post by drs305 on 2012-06-17
> **ChinaJustin said:**
> Ran into a problem when I ran ¨sudo update-grub¨.  Here´s the outputHere is my current 06_custom file:

```
#!/bin/sh
[COLOR="Blue"][noparse]echo 1>&2 "Adding My Custom Menu"[/noparse][/COLOR]
exec tail -n +**[COLOR="Blue"]4[/COLOR]** $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
[s]echo "Lubuntu Precise Pangolin 12.04" >&2 [/s]
[s]cat << EOF[/s]
menuentry "Lubuntu Precise Pangolin 12.04" {
    set root=(hd0,msdos2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
[s]EOF[/s]
[s]echo "Lubuntu Precise Pangolin 12.04 (Recovery Mode)" >&2[/s]
[s]cat << EOF[/s]
menuentry "Lubuntu Precise Pangolin 12.04 (Recovery Mode)" {
    set root=(hd0,msdos2)
        linux /vmlinuz root=/dev/sda2 ro single
        initrd /initrd.img
}
[s]EOF[/s]
[s]echo "Windows XP" >&2 [/s]
[s]cat << EOF[/s]
menuentry "Windows XP" {
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9AB84DC1B84D9C9F
    chainloader +1
}
[s]EOF[/s]
```

I haven´t rebooted yet, because I´m afraid of grub not liking the error and having issues. Ideas?

I have edited your file and made the above changes:
[LIST=1]
[*]Only place the '**echo**' command in the top section. Otherwise it's going to be input into the grub.cfg file.
[*]Changed the tail command to **4** since we are adding the 'echo' line to the top.
[*]Remove all **CAT / EOF** references. The way the GRUB scripts are set up, everything is output to grub.cfg so the CAT/EOF entries are not required.
[/LIST]
Here is the new file for you to try:
> 
#!/bin/sh
echo 1>&2 "Adding Lubuntu & Windows XP 06 Custom Menu"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Lubuntu Precise Pangolin 12.04" {
    set root=(hd0,msdos2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}

menuentry "Lubuntu Precise Pangolin 12.04 (Recovery Mode)" {
    set root=(hd0,msdos2)
        linux /vmlinuz root=/dev/sda2 ro single
        initrd /initrd.img
}

menuentry "Windows XP" {
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9AB84DC1B84D9C9F
    chainloader +1
}


---

### Post by Cavsfan on 2012-06-17
> **drs305 said:**
> 
[LIST=1]
[*]Only place the '**echo**' command in the top section. Otherwise it's going to be input into the grub.cfg file.
[*]Changed the tail command to **4** since we are adding the 'echo' line to the top.
[*]Remove all **CAT / EOF** references. The way the GRUB scripts are set up, everything is output to grub.cfg so the CAT/EOF entries are not required.
[/LIST]

Thanks Drs305. So, is this new for Grub version 1.99 on Precise Pangolin 12.04? 
Put only one echo line at the top and drop the 
**cat << EOF** and 
**EOF** lines? 
I know the echo text is not displayed in the menu anyway.

Is the change from +3 to +4 on the exec tail line also for Precise and grub2?
```
exec tail -n +4 $0
``` 
I have not been able to find any documentation on exec tail other than seeing it being used with +4.

---

### Post by drs305 on 2012-06-17
> **Cavsfan said:**
> Thanks Drs305. So, is this new for Grub version 1.99 on Precise Pangolin 12.04? 
Put only one echo line at the top and drop the 
**cat << EOF** and 
**EOF** lines? 
I know the echo text is not displayed in the menu anyway.

Is the change from +3 to +4 on the exec tail line also for Precise and grub2?
```
exec tail -n +4 $0
``` 
I have not been able to find any documentation on exec tail other than seeing it being used with +4.

I don't know if things changed late in 1.98 or later.

The + number simply tells the script to start at that line as far as executing the script. 

*exec* is running the command *tail*, so if you "man tail" you will find the documentation about what is happening.

---

### Post by Cavsfan on 2012-06-17
> **drs305 said:**
> I don't know if things changed late in 1.98 or later.

The + number simply tells the script to start at that line as far as executing the script. 

*exec* is running the command *tail*, so if you "man tail" you will find the documentation about what is happening.

Thanks for the info. I have been only on Lucid and was unaware about this. I'll update the  How to with this info.

---

### Post by Cavsfan on 2012-06-17
Updated this tutorial and added [COLOR=Green]*Notes[/COLOR] for Ubuntu versions that use Grub2 1.99 which started at Natty 11.04.

---

### Post by ChinaJustin on 2012-06-17
@drs305 - Thanks for the update. I plugged that in my 06_custom, run update-grub again, and it worked fine. I´m about to restart my computer, see how it works. Once I get it customized, I´ll try and post a screenshot.

I do have one follow up question, though. Being new to Linux/Ubuntu, and not a programmer (my one stint with programming was an ¨Intro to C++¨ class that was taught by a foreigner whose English was horrid), I do want to try and understand what some of the language is actually doing. I´ll take a look at the ¨man tail¨, but I was wondering about the EOF/CAT parts. I would imagine EOF means ¨End of File¨? What about CAT?  Of course, this may not be the place to go into that, so any reference to another forum/link would be great.

---

### Post by ChinaJustin on 2012-06-18
OK, just found another ¨error¨, but apparently it still worked out fine. When I tried copying the DejaVu font to the /boot/grub/ location, it gave me the following error:

```
Unknown gsub feature 0x63636d70 (ccmp)
Unknown gsub feature 0x646c6967 (dlig)
Unsupported substitution flag: 0x9
Unsupported substitution flag: 0x9
Unknown gsub feature 0x6c6f636c (locl)
Unknown gsub feature 0x6c6f636c (locl)
Unsupported substitution flag: 0x9
```

Found on a Fedora forum, though, that it still should have created the file, and sure enough, it did. (Note: I actually copied the above from that forum, so the error codes aren´t EXACTLY what I got, but close enough) Not sure why it did this, but for anyone else with the problem, you can just

```
ls /boot/grub/DejaVuSansMono.pf2
```

to make sure it worked.

---

### Post by drs305 on 2012-06-18
ChinaJustin,

I'm not a programmer either. CAT merely directly the input to standard output until the EOF (end of file marker) is reached. I believe CAT originates from the word  *concatenate*.

In most GRUB scripts, the CAT/EOF convention is used to send certain portions of the output 'as is' into the grub.cfg file. For the 40_custom file, the GRUB developers designed the update to assume that everything* in the script was to be imported directly into the grub.cfg file. Since so much of the GRUB menu file is dynamically created as the various /etc/grub.d scripts are run, the 40_custom file was designed to bypass this and allow a means which was as close to directly typing into the grub.cfg as possible.

The 'tail' command, the way it is written in 40_custom, merely tells GRUB to start at line X. Everything from line X to the end, excluding commented (#) lines, is sent to grub.cfg

---

### Post by Cavsfan on 2012-06-18
> **ChinaJustin said:**
> OK, just found another ¨error¨, but apparently it still worked out fine. When I tried copying the DejaVu font to the /boot/grub/ location, it gave me the following error:

```
Unknown gsub feature 0x63636d70 (ccmp)
Unknown gsub feature 0x646c6967 (dlig)
Unsupported substitution flag: 0x9
Unsupported substitution flag: 0x9
Unknown gsub feature 0x6c6f636c (locl)
Unknown gsub feature 0x6c6f636c (locl)
Unsupported substitution flag: 0x9
```Found on a Fedora forum, though, that it still should have created the file, and sure enough, it did. (Note: I actually copied the above from that forum, so the error codes aren´t EXACTLY what I got, but close enough) Not sure why it did this, but for anyone else with the problem, you can just

```
ls /boot/grub/DejaVuSansMono.pf2
```to make sure it worked.

ChinaJustin, I used to jump from one version to the next and when I went from Lucid to Maverick I got those same errors when creating the font.
I thought I mentioned that. I'll add it if it is not there.
But, noticed that it still worked. Not quite sure why it does that.
I look forward to seeing your new Grub2 screen! Are you on Precise?
Just curious.
Thanks again drs305!

---

### Post by ChinaJustin on 2012-06-21
OK, so I finally had to reboot my computer, and the font is HUGE! I know it's set at 24 in your instructions, but is that based on a high resolution? I need to go in and see what I can set mine to, and maybe that will help... but right now the menu is just a small rectangle, and I can't see ANY options! I'll try the resolution fix first, but then if I have to resize the font, do I need to delete it first, or will the new font size change overwrite it?

---

### Post by Cavsfan on 2012-06-22
> **ChinaJustin said:**
> OK, so I finally had to reboot my computer, and the font is HUGE! I know it's set at 24 in your instructions, but is that based on a high resolution? I need to go in and see what I can set mine to, and maybe that will help... but right now the menu is just a small rectangle, and I can't see ANY options! I'll try the resolution fix first, but then if I have to resize the font, do I need to delete it first, or will the new font size change overwrite it?

I have a 28" monitor and when I sent it in to be fixed I used a 17" monitor in the mean time.
I had the same problem but, rather than change the font size I changed the resolution in grub.
Enter **gksu gedit /etc/default/grub** in terminal and set this up 

**GRUB_GFXMODE=1366x768-24** (24 is color bit depth)

In my grub file I have this:

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#backup monitor size
#GRUB_GFXMODE=1366x768-24
GRUB_GFXMODE=1920x1200-24
```I added the 1366x768-24 when I was using the 17" monitor and commented it out when I got my big monitor back.
I left it commented out in case I ever have to use the 17' monitor again.
I hope this helps.

Although I don't think you need to change the font size I thought I mention what I have found about grub2 font size:
The size doesn't conform to dpi it is more of a point size. See this link:
[[COLOR=blue]_http://myunster.com/blog/server-administration/18.html_[/COLOR]]("http://myunster.com/blog/server-administration/18.html")

---

### Post by ChinaJustin on 2012-06-23
Slowly but surely getting this figured out!

OK, first, I changed the resolution AND the 'size' value, and it worked great.

Second:

> And then you will need to edit this file with this command gksu gedit /etc/grub.d/05_debian_theme 
Any time you wish to change the picture you will have to edit this file and place the name of it here:
WALLPAPER="/usr/share/images/desktop-base/rain.tga" They can be png, tga, jpg or jpeg.
You will add this after the first else at the top of the file if there is not one already there and make sure there is no # to the left of it.
Then the colors are right after the above line. Here are my current colors:
COLOR_NORMAL="light-cyan/black" 
COLOR_HIGHLIGHT="white/black"

Now, when I go to the 05_debian_theme file, my first 'else' is down in step 5 (not "at the beginning of the file"), but it looks right:

```
# Step #5: Check if GRUB can read the background image directly.
	# If so, we can remove the cache file (if any). Otherwise the backgound
	# image needs to be cached under /boot/grub/.
	if is_path_readable_by_grub "${1}"; then
		rm --force "${BACKGROUND_CACHE}.jpeg" \
			"${BACKGROUND_CACHE}.png" "${BACKGROUND_CACHE}.tga"
	elif cp "${1}" "${BACKGROUND_CACHE}.${reader}"; then
		set -- "${BACKGROUND_CACHE}.${reader}" "${2}" "${3}"
	else
		return 5
	fi

```

Question: do I *replace* 'return 5'? Add it before/after?

And again, thanks for all the help. Really enjoying all this tweaking I can do with Ubuntu... just gotta keep playing with it!

---

### Post by Cavsfan on 2012-06-23
> **ChinaJustin said:**
> And again, thanks for all the help. Really enjoying all this tweaking I can do with Ubuntu... just gotta keep playing with it!

This is sort of embarrassing :redface: but Grub2 v 1.99 is a lot simpler than what I have been using in Lucid.
I guess I should have checked it out before but, look at the comment above step 2 and you will see what you have to do.
All you do to  **/etc/grub.d/05_debian_theme** is change the colors if you want.
You have to edit the picture with Gimp (at least I always have had to) as the green note in step 2 mentions.
Then all you have to do is move your picture to **/boot/grub/** and you only want to have one picture in there.
There is no need for **WALLPAPER="/usr/share/images/desktop-base/rain.tga"**

Edit: I am going to have to investigate further on the text colors because when I added the font line, the colors went white.

---

### Post by Cavsfan on 2012-06-25
**ChinaJustin**, I think I have it all fixed now. It is sort of convoluted as I am trying to maintain version 1.98 of Grub (prior to Natty) 
and version 1.99 Natty up to Precise.
You should just have to start at the green note above step 2 through step 2.

Let me know if you have any problems.

---

### Post by Cavsfan on 2012-06-27
If are using Grub2 version 1.99 on Natty through Precise your **/etc/grub.d/06_custom** file would look like this:
(Except the **(hdx,x)** and **sdax** instances and the UUID for Windows are modified to match your **sudo blkid** output.)
Mine works perfectly except when I select the Windows 7 entry, it displays an error and to press any key but, after a few seconds goes into windows w/o a problem.

```
[COLOR=Blue]#!/bin/sh[/COLOR]
[COLOR=DarkRed]echo 1>&[/COLOR][COLOR=RoyalBlue]2[/COLOR] [COLOR=#ff1493]"Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04 and Windows 7"[/COLOR]
[COLOR=DarkRed]exec tail[/COLOR] -n +4 $0
[COLOR=Blue]# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.[/COLOR]
menuentry "[COLOR=#ff1493]Lycid Lynx 10.04[/COLOR]" [COLOR=DarkRed]{[/COLOR]
    [COLOR=DarkRed]set[/COLOR] root=(hd0,3)
        linux /vmlinuz root=/dev/sda3 ro quiet splash
        initrd /initrd.img
[COLOR=DarkRed]}[/COLOR]
menuentry "[COLOR=#ff1493]Lycid Lynx 10.04 (Recovery Mode)[/COLOR]" [COLOR=DarkRed]{[/COLOR]
    [COLOR=DarkRed]set[/COLOR] root=(hd0,3)
        linux /vmlinuz root=/dev/sda3 ro single
        initrd /initrd.img
[COLOR=DarkRed]}[/COLOR]
menuentry "[COLOR=#ff1493]Ubuntu Precise Pangolin 12.04[/COLOR]" [COLOR=DarkRed]{[/COLOR]
    [COLOR=DarkRed]set[/COLOR] root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
[COLOR=DarkRed]}[/COLOR]
menuentry "[COLOR=#ff1493]Ubuntu Precise Pangolin 12.04 (Recovery Mode)[/COLOR]" [COLOR=DarkRed]{[/COLOR]
    [COLOR=DarkRed]set[/COLOR] root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
[COLOR=DarkRed]}[/COLOR]
menuentry "[COLOR=#ff1493]Debian Squeeze[/COLOR]" [COLOR=DarkRed]{[/COLOR]
    [COLOR=DarkRed]set[/COLOR] root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash
        initrd /initrd.img
[COLOR=DarkRed]}[/COLOR]
menuentry "[COLOR=#ff1493]Debian Squeeze[/COLOR][COLOR=#ff1493] (Recovery Mode)[/COLOR]" [COLOR=DarkRed]{[/COLOR]
    [COLOR=DarkRed]set[/COLOR] root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro single
        initrd /initrd.img
[COLOR=DarkRed]}[/COLOR]
menuentry "[COLOR=#ff1493]Windows 7[/COLOR]" [COLOR=DarkRed]{[/COLOR]
    [COLOR=DarkRed]insmod[/COLOR] ntfs
    [COLOR=DarkRed]set root[/COLOR]='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
[COLOR=DarkRed]}[/COLOR]
```

---

### Post by ChinaJustin on 2012-06-27
I'm glad you mentioned you get an error on your Windows 7 selection, 'cause I get one on the XP selection, too... something about "undefined argument: press any key to continue". Glad to know it wasn't me this time. ;) I do wonder what it's referring to, though; gotta be something from grub, right?

---

### Post by drs305 on 2012-06-27
For Win 7, try replacing "chainloader +1" with:
> 
 ntldr /bootmgr

I'd do it by editing the menuentry live (press 'e' on the Grub menu) first just to see if it makes a difference before committing it permanently.

---

### Post by Cavsfan on 2012-06-27
> **ChinaJustin said:**
> I'm glad you mentioned you get an error on your Windows 7 selection, 'cause I get one on the XP selection, too... something about "undefined argument: press any key to continue". Glad to know it wasn't me this time. ;) I do wonder what it's referring to, though; gotta be something from grub, right?
So, I guess you seen my updates and got it working. Good!
                                                  > **drs305 said:**
> For Win 7, try replacing "chainloader +1" with:
> ntldr /bootmgrI'd do it by editing the menuentry live (press 'e' on the Grub menu) first just to see if it makes a difference before committing it permanently.
Drs305, it did not make any difference. it still said undefined argument. press any key to continue but, without touching anything it went into Windows 7.

I tried editing the line when grub displayed but did not know what to do to get it to accept the changes.
So, I edited 06_custom and sudo update-grub and reboot and nothing changed.
Thanks though!

---

### Post by Cavsfan on 2012-07-01
Here is my latest quad-boot grub2 screen with Lucid, Precise, Debian Squeeze and Windows 7:

[[IMG]http://ompldr.org/tZWt1Mg[/IMG]]("http://ompldr.org/vZWt1Mg")

---

### Post by Cavsfan on 2012-08-01
I just replaced Debian Squeeze with Quantal Quetzal 12.10. This is the contents of my /etc/grub.d/06_custom file.
It still gets an erroneous error when selecting windows but, without touching any key it still boots into windows just like it should. 
Everything else works great.
The (hdx,y) x and y values will depend on the output of **sudo blkid**.
You can also label each partition like this: **sudo tune2fs -L Quantal /dev/sda9**.
```
[COLOR=Blue]#!/bin/sh[/COLOR]
[COLOR=DarkRed]echo 1>&[/COLOR][COLOR=RoyalBlue]2[/COLOR] [COLOR=#ff1493]"Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04, Quantal Quetzal 12.10 and Windows 7"
[/COLOR][COLOR=DarkRed]exec tail[/COLOR] -n +4 $0 [COLOR=Blue]
# This file provides an easy way to add custom menu entries.  Simply type the 
# menu entries you want to add after this comment.  Be careful not to change 
# the 'exec tail' line above (unless on Natty or later then change +3 to +4).[/COLOR]
menuentry "[COLOR=#ff1493]Lycid Lynx 10.04[/COLOR]" [COLOR=DarkRed]{[/COLOR]     [COLOR=DarkRed]
    set[/COLOR] root=(hd0,3)         
           linux /vmlinuz root=/dev/sda3 ro quiet splash         
           initrd /initrd.img 
[COLOR=DarkRed]}[/COLOR] 
menuentry "[COLOR=#ff1493]Lycid Lynx 10.04 (Recovery Mode)[/COLOR]" [COLOR=DarkRed]{[/COLOR]     [COLOR=DarkRed]
    set[/COLOR] root=(hd0,3)         
           linux /vmlinuz root=/dev/sda3 ro single         
           initrd /initrd.img 
[COLOR=DarkRed]}[/COLOR] 
menuentry "[COLOR=#ff1493]Ubuntu Precise Pangolin 12.04[/COLOR]" [COLOR=DarkRed]{[/COLOR]     
[COLOR=DarkRed]    set[/COLOR] root=(hd0,5)         
           linux /vmlinuz root=/dev/sda5 ro quiet splash         
           initrd /initrd.img 
[COLOR=DarkRed]}[/COLOR] 
menuentry "[COLOR=#ff1493]Ubuntu Precise Pangolin 12.04 (Recovery Mode)[/COLOR]" [COLOR=DarkRed]{[/COLOR]     
    [COLOR=DarkRed]set[/COLOR] root=(hd0,5)         
           linux /vmlinuz root=/dev/sda5 ro single         
           initrd /initrd.img 
[COLOR=DarkRed]}[/COLOR] 
menuentry "[COLOR=#ff1493]Quantal Quetzal 12.10[/COLOR]" [COLOR=DarkRed]{[/COLOR]     
[COLOR=DarkRed]    set[/COLOR] root=(hd0,9)         
           linux /vmlinuz root=/dev/sda9 ro quiet splash         
           initrd /initrd.img [COLOR=DarkRed]
}[/COLOR] 
menuentry "[COLOR=#ff1493]Quantal Quetzal 12.10 (Recovery Mode)[/COLOR]" [COLOR=DarkRed]{[/COLOR]     
    [COLOR=DarkRed]set[/COLOR] root=(hd0,9)         
           linux /vmlinuz root=/dev/sda9 ro single         
           initrd /initrd.img 
[COLOR=DarkRed]}
[/COLOR]menuentry "[COLOR=#ff1493]Windows 7[/COLOR]" [COLOR=DarkRed]{
[/COLOR]    [COLOR=DarkRed]insmod[/COLOR] ntfs     [COLOR=DarkRed]
    set root[/COLOR]='(hd0,1)'     
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6     
    chainloader +1
 [COLOR=DarkRed]}[/COLOR]
```

---

### Post by Cavsfan on 2012-08-15
With grub 1.99, which started  on Ubuntu 11.04 (Natty Narwhal), when you select the windows option, you will see an erroneous error that says something like 
"invalid  argument specified
Press any key to continue"

But, whether you wait or press any key it will boot into windows normally.
If you do not have a windows OS, there are no problems what so ever.

---

### Post by Cavsfan on 2012-08-16
My latest Grub2 screen installed on Quantal Quetzal with Lucid 10.04, Precise 12.04, Quantal 12.10 and Windows 7.
It never changes even when new kernels get installed in any Ubuntu.
I get bored and change it from time to time.

[[color=blue]_Grub 2 Screen._[/COLOR]](http://ompldr.org/vZjRreA)

---

### Post by Cavsfan on 2012-08-27
I would not suggest using this How To for Quantal. At least not for the time being.
I could not get it to work myself.
Any other version of Ubuntu is fine though.

In Quantal, I did everything except include Quantal in **06_custom** and I also left **10_lunux** executable so I could get to Quantal.
In my experience if grub is not installed on Quantal, I have no mouse and the video is terrible.
So this is my menu with the other OS' custom at the top above Quantal:
```
     0    Lycid Lynx 10.04
     1    Lycid Lynx 10.04 (Recovery Mode)
     2    Ubuntu Precise Pangolin 12.04
     3    Ubuntu Precise Pangolin 12.04 (Recovery Mode)
     4    Windows 7
     5    Ubuntu, with Linux 3.5.0-11-generic
     6    Ubuntu, with Linux 3.5.0-11-generic (recovery mode)
     7    Ubuntu, with Linux 3.5.0-6-generic
     8    Ubuntu, with Linux 3.5.0-6-generic (recovery mode)
```

---

### Post by Cavsfan on 2012-08-28
This custom grub menu DOES indeed work with Quantal. Not sure if it is the recent addition of the Nvidia 304.43 driver or if I had just made an error.

This is my **/etc/grub.d/06_custom** 7 entries and every option works great.

```
#!/bin/sh
echo 1>&2 "Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04, Quantal Quetzal 12.10 and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Lycid Lynx 10.04" {
    set root=(hd0,3)
        linux /vmlinuz root=/dev/sda3 ro quiet splash
        initrd /initrd.img
}
menuentry "Lycid Lynx 10.04 (Recovery Mode)" {
    set root=(hd0,3)
        linux /vmlinuz root=/dev/sda3 ro single
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro single
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro single
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}
```

---

### Post by ChinaJustin on 2012-09-07
Hey, Cavsfan. Sorry I disappeared as far as posting a screen shot of my set up. Things have been pretty hectic around here, plus I had an issue with the Nvidia driver on my Lubuntu set up, so running it under Wubi for now while trying to figure out the RIGHT way to upgrade the driver. So I'll get that screen shot as soon as I can, but it'll be a while.

FYI: This works for Linux Mint, too. I'm running Maya (Mint 13) 32-bit with the Cinnamon desktop, and works fine. I haven't found a good picture I want to use yet, but I WILL get one and I WILL post a pic when I get it finished. :) Also works dual-booting on my wife's netbook with Windows 7 Starter. I was a bit worried, because Mint has it's own grub files, but they appear to be mainly asthetic things with the actual login screen, not with the grub menu.

FYI #2: Below, you have a mistake. When I was trying to do this again on my fresh install (tonight, actually) of Mint 13, I ran into the previous "syntax error" that I had back over on pages 12 and 13 of this thread. drs305 posted the fix, and you updated the front page tutorial, but not completely. Below, you still have the "echo" line directly above the menuentry line, when actually it should go above the "exec" line at the top. Unless that's what you meant by "the echo command only at the top", but it's a bit misleading when the code you posted has it directly above the menuentry. Make sense? :) Took me a few pages of reading the thread again before I found out the mistake.

> **Cavsfan said:**
>  

[COLOR=Green]*Note[/COLOR] if you are are using Grub2 version 1.99, you will want to use the following with the echo command only at the top:

```
echo "[COLOR=Red]Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04 and Windows 7[/COLOR]" >&2 
menuentry "Lycid Lynx 10.04" {
    set root=([COLOR=Red]hd0,3[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda3[/COLOR] ro quiet splash
        initrd /initrd.img
}

```(Delete the cat << EOF line and the EOF lines)


Any way, screen shots (hopefully) to come soon. Thanks again!

Edit: OK, you have it correct in the post above this, but not on the front page.

---

### Post by Cavsfan on 2012-09-07
> **ChinaJustin said:**
> Edit: OK, you have it correct in the post above this, but not on the front page.

Glad you got it fixed and working well! :D

I was in the process of fixing the first post as you point out and they took away our rights to edit How Tos.
The forum changed their policy for people to use Wiki for their How Tos. 
So, I have been adding stuff to the bottom and hoping people will find it there.

I tried out Mint for a while. This worked on that and even on Debian Squeeze too. Now, I have Lucid Lynx 10.04, Precise Pangolin 12.04, Quantal Quetzal 12.10 and Windows 7. 
I have customized the grub on all 3 Ubuntus.
The only single problem that we have when Windows is selected from the menu it gives an erroneous error with "press any key to continue".
But, if you wait or just press enter it goes right into Windows. 
So, that is not a problem.

Thanks for the post and I look forward to seeing your grub screen. :D

---

### Post by Cavsfan on 2012-09-17
I just wanted to mention that Quantal Quetzal 12.10 just got a grub update to version 2.00 and if you are dual booting with windows, 
you no longer will get any kind of error when selecting any windows OS from this custom menu.

```
cavsfan@cavsfan-MS-7529:~$ grub-install -v
grub-install (GRUB) [COLOR="Red"]2.00[/COLOR]-4ubuntu1
```

This tutorial is going be migrated over to a wiki shortly but, if any one is using Quantal and got the new update,
the custom font colors go after line 108 not 98 in **/etc/grub.d/05_debian_theme**.

---

### Post by Cavsfan on 2012-10-01
The wiki is finished and getting close to being linked to this thread I believe. It is simpler than this How To as it has gotten a bit convoluted over time.

It should be more straight forward and I will let you know when it is available.

This How to is based on the idea that if you dual boot Ubuntu and Windows, want Windows as the default and want a way to keep from having to 
constantly change the default line every time a new kernel is installed so that Windows remains the default (for my wife and son) this is the best way.

Thanks to the Ubuntu users who have used this How To. :grin:

---

### Post by Cavsfan on 2012-10-08
The link to the wiki is going to be added to the top of this thread soon.

But, here is the link. It is broken down into Grub version 1.98 (Lucid) at the top.
Then there is Grub version 1.99 (anything after Lucid and before Quantal) and Grub 2.00 (Quantal). 
There are only minor differences between Grub 1.99 and Grub 2.00.
There is also an example Grub screen for each Grub version.

**grub-install -v**  entered in Terminal will tell you what version of Grub you have.

[[COLOR=blue]_https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen_[/COLOR]]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")

Post any questions here.

---

### Post by von Stalhein on 2012-10-09
Great job Cavsfan!!!

I have bludged since 12.04 and left my Grub screen standard, time to get back on the horse :)

---

### Post by Cavsfan on 2012-10-09
> **von Stalhein said:**
> Great job Cavsfan!!!

I have bludged since 12.04 and left my Grub screen standard, time to get back on the horse :)

Thanks! :D Let me know what you think or if you have any problems or anything.

---

### Post by Cavsfan on 2012-10-24
The Wiki is complete and the link in my signature should be used instead of the first post in this thread.

The Wiki is more accurate and not as convoluted as this How to has become as I can no longer edit it.
There is some incorrect information in this How to but, the Wiki is good to go.

Post any comments, questions or problems here as long as it stays open.

Thanks!
Cavsfan :)

---

### Post by Cavsfan on 2012-10-25
I've created another thread with the Community Wiki in my signature which will give a place to post questions, comments, problems, etc.

[[COLOR=green]_http://ubuntuforums.org/showthread.php?p=12317572#post12317572_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=12317572#post12317572")

This section of the Ubuntu forum will be closed shortly.

Thanks to those who have used this tutorial. :)
I look forward to hearing from you in the new thread.

---

### Post by Cavsfan on 2012-10-29
Check the post in my new thread. I have 7 operating systems installed and doubt I would be able to maneuver the menu if it wasn't custom.

[[COLOR=blue]_http://ubuntuforums.org/showpost.php?p=12324765&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=12324765&postcount=5")

---

### Post by Cavsfan on 2012-11-08
Through experience I have learned that it is best if you restore these custom files to their original state prior to upgrading Ubuntu versions.
So, in the Community Wiki in my signature I have added how to do so and provided a link with the original file contents.
They can be copied and pasted into the files and Grub2 will be back to it's original state.

---

### Post by Elfy on 2012-11-20
This thread is closed. 
 
The information is now held on the community wiki at  
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205) 
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

