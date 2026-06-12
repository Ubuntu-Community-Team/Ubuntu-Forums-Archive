---
title: "A GRUB2 Theme For Ubuntu 13.04"
date: 2012-11-05
forum: Ubuntu Development Version
---

### Post by dniMretsaM on 2012-11-05
_Update:_ At the suggestion of morgenstond, I'm working on styling the theme in a similar manner to the Unity greeter for LightDM. You can see the progress of that in post [16](http://ubuntuforums.org/showpost.php?p=12342307&postcount=16).

After installing openSUSE a while back and seeing the default GRUB2 theme, I thought that my favorite distribution, Ubuntu, needed it's own. So this is my attempt at theme that lives up to the high standard of the artwork for Ubuntu. It's not finished, but it's getting there. You can find the theme [here]("https://github.com/dniMretsaM/Ubuntu-GRUB2-Theme") on GitHub. I hope to get this theme into the final release of 13.04.

**Todo List:**
[LIST]
[*]Add a drop shodow to the menu and the terminal window.
[/LIST]
**How To Use:**
**1) Clone the GitHub repository:**
```
git clone git://github.com/dniMretsaM/Ubuntu-GRUB2-Theme.git
```**2) Move the theme file:**
```
cd Ubuntu-GRUB2-Theme/
sudo mkdir /usr/share/grub/themes
sudo cp --recursive ubuntu/ /usr/share/grub/themes/
```**3) Add this line to /etc/default/grub:**
```
GRUB_THEME=/usr/share/grub/themes/ubuntu/theme.txt
```**4) Update GRUB's configuration:**
```
sudo update-grub
```**Notes:**
[LIST]
[*]Although I'm making this theme for 13.04, it will work on other versions. I have included a .xcf of the logo ([FONT=Courier New]13.04.xcf[/FONT]), so you can easily change it to be 12.10, or what ever other version you want.
[*]The background image ([FONT=Courier New]background.png[/FONT]) is currently the default wallpaper from 12.10. The theme will use Raring's default when it's available later in the development cycle.
[*]The resolution in the screen shot is 1024x768 (I can't get my  VinrtualBox install to use 1366x76[NOPARSE]8)[/NOPARSE], but the theme  is not resolution dependant. Also, ignore the grey line at the bottom,  as that's from VB.
[/LIST]
So yeah, feel free to try it out. Make suggestions, contribute graphics, whatever.


Enjoy,
dniMretsaM

---

### Post by cecilpierce on 2012-11-05
Thanks for the nice theme, just installed it...:)

---

### Post by elliotn on 2012-11-06
please can u post the logo xcf please

---

### Post by Bucky Ball on 2012-11-06
*Thread moved to **Ubuntu +1 (Raring Ringtail)***


Looking good. Could you spare a thought for those with slow connections remove the screenshot from the body of your post, keeping the attachment? Cheers. :wink:

---

### Post by cecilpierce on 2012-11-06
> **elliotn said:**
> please can u post the logo xcf please

There is a '13.04.xcf' file in the zip file, if that is what your lokking for.

---

### Post by morgenstond on 2012-11-06
Good initiative! I'd definitely like to say goodbye to the old-school look we have now.

I'd just like to suggest styling it in a similar fashion as the lightdm greeter is now. That way, there would be more consistency throughout. 

(If so, then we could start to use the default wallpaper throughout the entire boot, which will look quite professional, especially when Wayland lands and there are no more mode switches during boot).

---

### Post by cecilpierce on 2012-11-06
> **morgenstond said:**
> Good initiative! I'd definitely like to say goodbye to the old-school look we have now.

I'd just like to suggest styling it in a similar fashion as the lightdm greeter is now. That way, there would be more consistency throughout. 

(If so, then we could start to use the default wallpaper throughout the entire boot, which will look quite professional, especially when Wayland lands and there are no more mode switches during boot).

Big +1...:)

---

### Post by dniMretsaM on 2012-11-06
> **elliotn said:**
> please can u post the logo xcf please

I'll add that as an attachment to the first post.

> **Bucky Ball said:**
> *Thread moved to **Ubuntu +1 (Raring Ringtail)***

Thanks. I wasn't sure exactly where it belonged, so I went the safe route and put it in the Cafe.

> **Bucky Ball said:**
> Looking good. Could you spare a thought for those with slow connections remove the screenshot from the body of your post, keeping the attachment? Cheers. :wink:

Done. Didn't think of that, my bad.

> **morgenstond said:**
> I'd just like to suggest styling it in a similar fashion as the lightdm greeter is now. That way, there would be more consistency throughout. 

Excellent idea. I guess I never thought of that because I just have the VM set to auto-login and I never see the DM screen. I'll see what I can do.

---

### Post by morgenstond on 2012-11-06
> **dniMretsaM said:**
> I'll add that as an attachment to the first post.



Thanks. I wasn't sure exactly where it belonged, so I went the safe route and put it in the Cafe.



Done. Didn't think of that, my bad.



Excellent idea. I guess I never thought of that because I just have the VM set to auto-login and I never see the DM screen. I'll see what I can do.

That would be very cool indeed! Thanks!

---

### Post by GrubThemeArtist on 2012-11-06
> **Bucky Ball said:**
> *Thread moved to **Ubuntu +1 (Raring Ringtail)***


Looking good. Could you spare a thought for those with slow connections remove the screenshot from the body of your post, keeping the attachment? Cheers. :wink:

You could merge it with the GRUB Theme thread.

---

### Post by GrubThemeArtist on 2012-11-06
I'm going to help you out a bit. I've attached an installer script, the only thing you have to edit is the theme name. This was written by Towheed Mohammad here about a year ago. I know he has an updated version, but this one works just fine. I assume that you're going for a resolution independent theme, so the tweak I did to Towheed's installer should make it easier for your users to modify the resolution.

I'm also reading through your todo.
-Avoid scrollbars, they're more trouble than they're worth, and don't really add much to the theme. So set scrollbars to false.
-Make your terminal background larger (which is why it's not working). Grub doesn't like images smaller than 2x2.
-For the navigation label, I recommend creating it in Gimp and adding it like an image. You get the benefit of antialiasing.
-Also make your font larger.
-Your progress bar looks messed up because on the center piece you have a one pixel transparent border on the top and bottom.
-My personal preference is for text to not be on the progress bar, to do this you just set text = ""
-I'm not sure what your issue is with the 1024x768 resoluton is or with your selection images (doesn't stretch all the way?).
-If you want to add a drop shadow to the terminal and the menu, just reconstruct the full images in Gimp, combine them all, do a drop shad (Filters -> Light and Shadow -> Drop shadow),then cut them back up (you'll have to change some parameters in your theme.txt).
-When testing it the selection center part is completely missing. I don't know why that is.

---

### Post by funicorn on 2012-11-06
To be clear, are the font and background settings still effective when a grub theme is applied ?

---

### Post by dniMretsaM on 2012-11-06
> **GrubThemeArtist said:**
> I'm going to help you out a bit. I've attached an installer script, the only thing you have to edit is the theme name. This was written by Towheed Mohammad here about a year ago. I know he has an updated version, but this one works just fine. I assume that you're going for a resolution independent theme, so the tweak I did to Towheed's installer should make it easier for your users to modify the resolution.

I looked at the script from his GRUB theme guide, but it didn't work. The one you have attached, however, does. The thing is, the theme doesn't need anything specific for the different resolutions. Also, the script installs to /boot/grub/themes/, but Ubuntu, I believe, uses /usr/share/grub/themes/.

> **GrubThemeArtist said:**
> I'm also reading through your todo.
-Avoid scrollbars, they're more trouble than they're worth, and don't really add much to the theme. So set scrollbars to false.
-Make your terminal background larger (which is why it's not working). Grub doesn't like images smaller than 2x2.
-For the navigation label, I recommend creating it in Gimp and adding it like an image. You get the benefit of antialiasing.
-Also make your font larger.
-Your progress bar looks messed up because on the center piece you have a one pixel transparent border on the top and bottom.
-My personal preference is for text to not be on the progress bar, to do this you just set text = ""
-I'm not sure what your issue is with the 1024x768 resoluton is or with your selection images (doesn't stretch all the way?).
-If you want to add a drop shadow to the terminal and the menu, just reconstruct the full images in Gimp, combine them all, do a drop shad (Filters -> Light and Shadow -> Drop shadow),then cut them back up (you'll have to change some parameters in your theme.txt).
-When testing it the selection center part is completely missing. I don't know why that is.

It appears to me that you're not using the latest commit. The only item in the todo in the current commit is the drop shadow, which I'm probably going to work on tomorrow.

> **funicorn said:**
> To be clear, are the font and background  settings still effective when a grub theme is applied ?

The font is set by the theme. The background image is preempted by  the theme, but the color is still used, but only in the terminal window  (this theme is made to use Ubuntu's default GRUB color.

---

### Post by elliotn on 2012-11-07
> **dniMretsaM said:**
> After installing openSUSE a while back and seeing the default GRUB2 theme, I thought that my favorite distribution, Ubuntu, needed it's own. So this is my attempt at theme that lives up to the high standard of the artwork for Ubuntu. It's not finished, but it's getting there. You can find the theme [here]("https://github.com/dniMretsaM/Ubuntu-GRUB2-Theme") on GitHub. I hope to get this theme into the final release of 13.04.

**Todo List:**
[LIST]
[*]Add a drop shodow to the menu and the terminal window.
[/LIST]
**How To Use:**
**1) Clone the GitHub repository:**
```
git clone git://github.com/dniMretsaM/Ubuntu-GRUB2-Theme.git
```**2) Move the theme file:**
```
cd Ubuntu-GRUB2-Theme/
sudo mkdir /usr/share/grub/themes
sudo cp --recursive ubuntu/ /usr/share/grub/themes/
```**3) Add this line to /etc/default/grub:**
```
GRUB_THEME=/usr/share/grub/themes/ubuntu/theme.txt
```**4) Update GRUB's configuration:**
```
sudo update-grub
```**Notes:**
[LIST]
[*]Although I'm making this theme for 13.04, it will work on other versions. I have included a .xcf of the logo ([FONT=Courier New]13.04.xcf[/FONT]), so you can easily change it to be 12.10, or what ever other version you want.
[*]The background image ([FONT=Courier New]background.png[/FONT]) is currently the default wallpaper from 12.10. The theme will use Raring's default when it's available later in the development cycle.
[*]The resolution in the screen shot is 1024x768 (I can't get my  VinrtualBox install to use 1366x76[NOPARSE]8)[/NOPARSE], but the theme  is not resolution dependant. Also, ignore the grey line at the bottom,  as that's from VB.
[/LIST]
So yeah, feel free to try it out. Make suggestions, contribute graphics, whatever.


Enjoy,
dniMretsaM

thanks m8

---

### Post by GrubThemeArtist on 2012-11-07
> **dniMretsaM said:**
> I looked at the script from his GRUB theme guide, but it didn't work. The one you have attached, however, does. The thing is, the theme doesn't need anything specific for the different resolutions. Also, the script installs to /boot/grub/themes/, but Ubuntu, I believe, uses /usr/share/grub/themes/.

Ubuntu reads from /boot/grub/themes. :)
My tweak just lets the user adjust his resolution or else it would just keep the resolution grub already had. Also, Towheed updated the script last night to reflect some changes for Grub 2.00. We have a grub theme thread and you can find it at the end.


> **dniMretsaM said:**
> 
It appears to me that you're not using the latest commit. The only item in the todo in the current commit is the drop shadow, which I'm probably going to work on tomorrow.


I was tired last night and was reading your Completed list like it was part of the todo. :P

I was still having some odd behavior though.

---

### Post by dniMretsaM on 2012-11-07
Ok, so in the [FONT=Courier New]unity-greeter-style[/FONT] branch, there is the *beginning* of a theme that will hopefully look like the Unity Greeter for LightDM (screen shot attached). A few things to note. Due to the limitations on GRUB theming, I don't think it's possible to do have the boot menu stay in place while the options scroll though it like the login window does in the greeter. I'm also not sure if I can do the dots on the wallpaper. I could put it on the wallpaper directly, but then it would be resolution dependent, which I don't want. If anybody knows how I could accomplish this, let me know.

> **GrubThemeArtist said:**
> Ubuntu reads from /boot/grub/themes. :)
My tweak just lets the user adjust his resolution or else it would just keep the resolution grub already had. Also, Towheed updated the script last night to reflect some changes for Grub 2.00. We have a grub theme thread and you can find it at the end.

I guess it can technically read from anywhere that you point GRUB_THEME. And I'll take a look at the updated script, though the one you posted seems to work just fine.

> **GrubThemeArtist said:**
> I was tired last night and was reading your Completed list like it was part of the todo. :P

I was still having some odd behavior though.

What issues are you having? Still a problem with the selection center image?

---

### Post by morgenstond on 2012-11-08
> **dniMretsaM said:**
> Ok, so in the [FONT=Courier New]unity-greeter-style[/FONT] branch, there is the *beginning* of a theme that will hopefully look like the Unity Greeter for LightDM (screen shot attached). A few things to note. Due to the limitations on GRUB theming, I don't think it's possible to do have the boot menu stay in place while the options scroll though it like the login window does in the greeter. I'm also not sure if I can do the dots on the wallpaper. I could put it on the wallpaper directly, but then it would be resolution dependent, which I don't want. If anybody knows how I could accomplish this, let me know.



I guess it can technically read from anywhere that you point GRUB_THEME. And I'll take a look at the updated script, though the one you posted seems to work just fine.



What issues are you having? Still a problem with the selection center image?

Wow, you work fast! That's looking quite nice already! I'm very curious to see how closely you'll be able to mimic the unity greeter in the end. 
Have you thought about contacting the designers to try and get their feedback on this undertaking? They may have some invaluable ideas, and I guess that would be the first step in eventually getting this in as default.

---

### Post by dniMretsaM on 2012-11-08
> **morgenstond said:**
> Wow, you work fast! That's looking quite nice already! I'm very curious to see how closely you'll be able to mimic the unity greeter in the end. 
Have you thought about contacting the designers to try and get their feedback on this undertaking? They may have some invaluable ideas, and I guess that would be the first step in eventually getting this in as default.

Thanks! And I plan on contacting them, I just wanted to make sure I could get something that is at least fairly similar so as to not waste their valuable time.

---

### Post by serdotlinecho on 2012-11-08
I totally want this. Even though i'm not dual booting...beautiful and sleek!

---

### Post by dniMretsaM on 2012-11-21
The theme now uses Raring's default wallpaper. I'll update the thread with a screenshot soon.

---

### Post by cecilpierce on 2012-11-21
Just installed the new theme, looks nice.
Wish someone would make icons for all distros, I made a few but its a pain when your not an expert..:P

---

### Post by TREESofRIGHTEOUSNESS on 2012-12-11
#ubuntu-design

I posted this webpage on there, This really needs to occur in ringtail.  With as smooth as unity is running, it would be great to have a complete beautiful experience

---

### Post by AestheticArson on 2013-03-05
Thank you very much for this theme! It looks good. I'm running Ubuntu 12.10, and was able to install quick without any problems.

My first suggestion for you is to either increase the terminal window's width and height, it seemed very small especially with the default font for the terminal window.
The second suggestion would be to change the default font that you have for the terminal window, I noticed that the underscore "_" doesn't show up after being input.

Besides that it's awesome! Thank you very much.

---

### Post by morgenstond on 2013-03-06
Has there been any word on getting this in by default from the powers that be?

---

### Post by pqwoerituytrueiwoq on 2013-03-07
Now that is a nice theme, any chance of a xubuntu version? (just change the background and change 'Ubuntu' to 'xubuntu')
almost makes me want to change the timeout on my menu just to see it

---

### Post by pqwoerituytrueiwoq on 2013-04-20
Why can't i get the partedmagic icon to work? all of my other icons work???
```
~$ ls -l /media/chad/10A9-AFCE/boot/grub/themes/ubuntu/icons/
total 1440
-rw-r--r-- 1 chad chad  65909 Mar 13 20:27 arch.png
-rw-r--r-- 1 chad chad  17205 Mar 13 21:53 dban.png
-rw-r--r-- 1 chad chad  65909 Mar 13 20:27 debian.png
-rw-r--r-- 1 chad chad   4283 Mar 13 20:27 fedora.png
-rw-r--r-- 1 chad chad  65909 Mar 13 20:27 gentoo.png
-rw-r--r-- 1 chad chad  29156 Mar 13 21:49 gnomeubuntu.png
-rw-r--r-- 1 chad chad 395473 Mar 13 20:27 gnu-linux.png
-rw-r--r-- 1 chad chad  37643 Mar 13 20:27 kubuntu.png
-rw-r--r-- 1 chad chad  65946 Mar 13 20:27 linuxmint.png
-rw-r--r-- 1 chad chad   7380 Mar 13 20:27 lubuntu.png
-rw-r--r-- 1 chad chad  16087 Mar 13 20:27 mandrivalinux.png
-rw-r--r-- 1 chad chad 141927 Mar 13 20:27 opensuse.png
-rw-r--r-- 1 chad chad   7777 Mar 13 20:27 osx.png
-rw-r--r-- 1 chad chad   4449 Apr 20 23:21 partedmagic.png
-rw-r--r-- 1 chad chad   8631 Mar 13 20:27 recovery.png
-rw-r--r-- 1 chad chad  23422 Mar 13 20:27 sabayon.png
-rw-r--r-- 1 chad chad 214373 Mar 13 20:27 slackware.png
-rw-r--r-- 1 chad chad  40292 Mar 13 20:27 submenu.png
-rw-r--r-- 1 chad chad   8852 Mar 13 20:27 ubuntu.png
-rw-r--r-- 1 chad chad  17049 Mar 13 20:27 windows.png
-rw-r--r-- 1 chad chad  11882 Mar 13 20:27 xubuntu.png
```
[http://pastebin.com/YVXSdkbN](http://pastebin.com/YVXSdkbN) - partedmagic's entry is on line 66

to make my partedmagic.png
```
wget [http://partedmagic.com/lib/exe/fetch.php?media=logo.gif](http://partedmagic.com/lib/exe/fetch.php?media=logo.gif) -O /tmp/logo.gif
convert /tmp/logo.gif /tmp/partedmagic.png
echo "open /tmp and get you will see the png file"
```

---

### Post by Baldrick_NZ on 2013-04-21
> **dniMretsaM said:**
> _Update:_ At the suggestion of morgenstond, I'm working on styling the theme in a similar manner to the Unity greeter for LightDM. You can see the progress of that in post [16](http://ubuntuforums.org/showpost.php?p=12342307&postcount=16).

After installing openSUSE a while back and seeing the default GRUB2 theme, I thought that my favorite distribution, Ubuntu, needed it's own. So this is my attempt at theme that lives up to the high standard of the artwork for Ubuntu. It's not finished, but it's getting there. You can find the theme [here]("https://github.com/dniMretsaM/Ubuntu-GRUB2-Theme") on GitHub. I hope to get this theme into the final release of 13.04.

**Todo List:**
[LIST]
[*]Add a drop shodow to the menu and the terminal window.
[/LIST]
**How To Use:**
**1) Clone the GitHub repository:**
```
git clone git://github.com/dniMretsaM/Ubuntu-GRUB2-Theme.git
```**2) Move the theme file:**
```
cd Ubuntu-GRUB2-Theme/
sudo mkdir /usr/share/grub/themes
sudo cp --recursive ubuntu/ /usr/share/grub/themes/
```**3) Add this line to /etc/default/grub:**
```
GRUB_THEME=/usr/share/grub/themes/ubuntu/theme.txt
```**4) Update GRUB's configuration:**
```
sudo update-grub
```**Notes:**
[LIST]
[*]Although I'm making this theme for 13.04, it will work on other versions. I have included a .xcf of the logo ([FONT=Courier New]13.04.xcf[/FONT]), so you can easily change it to be 12.10, or what ever other version you want.
[*]The background image ([FONT=Courier New]background.png[/FONT]) is currently the default wallpaper from 12.10. The theme will use Raring's default when it's available later in the development cycle.
[*]The resolution in the screen shot is 1024x768 (I can't get my  VinrtualBox install to use 1366x76[NOPARSE]8)[/NOPARSE], but the theme  is not resolution dependant. Also, ignore the grey line at the bottom,  as that's from VB.
[/LIST]
So yeah, feel free to try it out. Make suggestions, contribute graphics, whatever.


Enjoy,
dniMretsaM

I really love the concept of this! Looks totally professional.

The only thing, which I think is a bug, is once I've timed out (or made my selection and entered enter), I get a large terminal-like box which centres itself in the middle of my screen pretty much blocking out your excellent work! It actually looks like some sort of splash screen, but entirely blue, with no writing on it.

Removing the 'terminal.png' and associated font from the theme.txt file helps, but doesn't remove it altogether.

Is there anyway to remove this completely?

Keep up the awesome work!!
heers.
C

---

### Post by edkmho on 2013-04-27
Great theme. Thanks.

I am experiencing the same issue with the big square poping up after selecting the OS. Would appreciate if you could help.

Many thanks.

---

### Post by disPlay on 2013-04-27
The theme looks great. Thanks

---

### Post by ruffxl on 2013-05-29
Great work, Keep it up 
And Thanks! :D

---

### Post by Cavsfan on 2013-05-29
Not intending to steal anyone's thunder but, the green link in my signature does this.
I change the picture and the font colors once in a while. Other than that it _never_ has to be touched unless you install or delete an OS.
Here is a picture of my current Grub2 screen in Raring:

[ATTACH=CONFIG]243240[/ATTACH]

You pretty much just have to point each entry to the correct partition e.g. sda2 for each OS.

```
cavsfan@cavsfan-MS-7529:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0    menuentry "Precise Pangolin 12.04" {
     1    menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
     2    menuentry "Quantal Quetzal 12.10" {
     3    menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
     4    menuentry "Raring Ringtail 13.04" {
     5    menuentry "Raring Ringtail 13.04 (Recovery Mode)" {
     6    menuentry "Saucy Salamander 13.10" {
     7    menuentry "Saucy Salamander 13.10 (Recovery Mode)" {
     8    menuentry "Linux Mint 14 Nadia" {
     9    menuentry "Linux Mint 14 Nadia (Recovery Mode)" {
    10    menuentry "Windows 7" {

```

---

