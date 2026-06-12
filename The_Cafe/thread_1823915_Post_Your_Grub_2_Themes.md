---
title: "Post Your Grub 2 Themes"
date: 2011-08-12
forum: The Cafe
---

### Post by drs305 on 2011-08-12
Inspired by *Dylan103's* popular [Conky thread]("http://ubuntuforums.org/showthread.php?t=281865"), and various "Screenshot of the Month" threads, this thread is for posting Grub 2 themes. 

**[COLOR="DarkRed"][COLOR="DarkRed"]NEW[/COLOR][/COLOR]**
GRUB 2.0 has just been released and includes it's own theme: starcraft

Grub 2.0 is not in the Ubuntu repositories nor in use on any current release of Ubuntu, but if you want to compile it you can get the files from the following location:
[http://ftp.gnu.org/gnu/grub/grub-2.00.tar.gz]("http://ftp.gnu.org/gnu/grub/grub-2.00.tar.gz")

**This is not designed to be a support thread.** It's posted in the Community Cafe forum for a reason - it is not designed to be a "How To" on building a theme. It's purpose is to provide a pre-built theme that can be used without a great deal of editing. The user will need to add icons, backgrounds, and additional fonts if necessary by the theme. 

The latter portion of this post will provide some general information about fonts, icons, and backgrounds. That will be the extent of general support information.

**Rules for posting:**
I can't improve on KiwiNZ's rules on _[another thread]("http://ubuntuforums.org/showthread.php?t=1794152")_, so here they are:
[list=1]
[*]Stay within the board rules, no matter how hot you may believe the wallpaper/screen shot to be.
[*]If you are going to quote, there isn't a need to quote an img-embeded picture - Just don't do it. Please just reference the post by page number/page link/etc.
[*]Off Topic Posts will be edited or removed.
[*]The desktops thread is not to be used as a means to post explicit or suggestive, and provocative images (they must be safe for your kids and/or boss to see). Please help to keep the thread relevant and safe to browse for everyone.
[*]The moderators of this forum reserve the right to edit or remove your posts as necessary so they may comply with our Community Rule set.
[*][COLOR="Red"]Please use reduced-size thumbnails[/COLOR], out of respect for people running on lower bandwidth or screen resolutions. Any large image (as determined by me) will be removed! If you can't post a thumbnail, please use a text link to your image. ImageShack causes problems for users in some countries. Please use another image hosting service. If your image is removed, reread this section. 
[*]Themes posted to this thread may be used and modified without attribution.
[/list]

**Additional information to include in your post:**
[LIST=1]
[*]If you have to install special files/fonts, please specify how to do it.
[*]Provide the paths if images or files are not located in the same folder as the theme file.
[*]Background Image: Name/where you got it (with link would be nice).
[*]Icons: Name/where you got it (with link would be nice).
[/LIST]

**Limited Support Information:** (Remember this is not a support forum)
This post provides some general information on background images, icons, and fonts. It is not meant to be a comprehensive guide to creating Grub 2 themes.

For complete information on how to build themes, I refer you to forum member *towheedm*'s excellent theming guide, which can be found from information in this link:
_[http://ubuntuforums.org/showthread.php?t=1534689]("http://ubuntuforums.org/showthread.php?t=1534689")_

[LIST=1]
[*]**Background Images**
Background images referenced in a theme file will override the background images listed in *05_debian_theme* and */etc/default/grub* and, in Grub 1.99 and later, image files placed in the */boot/grub* folder.


[*]**Fonts**
The default Grub 2 font is based on */usr/share/grub/unicode.pf2* and is identified as "Unknown Regular 16" when "lsfonts" is run from the Grub command prompt. This font is scaled based on the resolution set by Grub during boot (the higher the resolution, the smaller the font). Grub 2 in later versions uses the highest resolution (smallest font) available to it unless the user specifies a different resolution in the "GRUB_GFXMODE=" entry of the */etc/default/grub* file.

To see the fonts loaded by Grub 2, at the grub command prompt, run the following command. (To get to the grub command line, press 'c' while viewing the Grub 2 menu.)
```
lsfonts
```

Grub 2 uses '.pf2' fonts. Other fonts can be converted to this format with the 'grub-mkfont' command (demonstrated later).

To create additional .pf2 fonts:
[LIST]
[*]The fonts used by Ubuntu are generally stored in */usr/share/fonts* and its subfolders.
[*]To find a specific font, you can use the *locate* command. ( Example: *locate DejaVuSans.ttf* )
[*]Fonts can be placed directly in the same folder as the theme file (e.g. theme.txt) or in a universal folder such as */boot/grub/fonts* and linked to the folder containing the theme file.
[*]To import a font to a 'universal' grub font folder (which must be created first):
```

sudo mkdir /boot/grub/fonts
sudo grub-mkfont --verbose --range=0x0-0x7F --size=18 --output=/boot/grub/fonts/DejaVuSans-18.pf2  $(locate DejaViewSans.ttf)
```
[/LIST]
[LIST]
[*]To link a font in the */boot/grub/fonts* folder to the folder containing theme.txt (/boot/grub/themes/ubuntu/ :
```
sudo ln -s /boot/grub/fonts/DejaVuSans-Bold-18.pf2  /boot/grub/themes/ubuntu/
```
[/LIST]

[*]**Icons**
[LIST]
[*]Icons are called based on a "--class xxxx" entry in a menuentry. The xxxx references a .png file in the *icons* folder. Do not include the extension (.png) in the class designation.
[LIST]
[*]Example:  menuentry 'Ubuntu, with Linux 3.0.0-7-generic' **--class ubuntu**  {
[/LIST]
[*]Icons should be stored in an "icons" folder in the same folder as the theme.txt. Grub 2 will automatically look in the *icons* folder for referenced icons.
[*]Icons will be scaled according to the information in the theme.txt
[*]Grub 2 automatically uses the icon image in the *icons* folder with the same name as the "--class" designation in the menuentry.
[*]Default *classes* may include:
[LIST]
[*]10_linux: ubuntu, gnu-linux, gnu, os
[*]30_os-prober: gnu-linux, gnu, os, windows (if found)
[*]Icons for many popular OS's can be found in *towheedm's* Grub 2 Theming Guide (see Links section).
[LIST]
[*]For example, if the menuentry contains "--class ubuntu", Grub 2 will look for an icon in the *icons* folder named "ubuntu.png"  Do not use the ".png" extension if creating a custom "--class" entry.
[/LIST]
[/LIST]
[*]The user may create his own "--class" and place the .png file in the *icons* folder. 
[LIST]
[*]Example: "--class myclass"  with "myclass.png" placed in the *icons* folder.
[/LIST]
[/LIST]
[/LIST]

**LINKS:**
[_A Beginner's Guide to Theming GRUB2_]("http://ubuntuforums.org/showthread.php?t=1534689") by forum member *towheedm*
[_GNU GRUB 1.99 Manual_]("http://www.gnu.org/software/grub/manual/grub.html")

A sample Grub 2 Theme created using *towheedm's* guide:

---

### Post by drs305 on 2011-08-12
This is a very simple theme to get you started. It was created with the help of the Grub Theming Guide by forum member *towheedm* referenced in the following thread.
_[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)_

I have removed a lot of the commented lines of the example theme to make it short and simple.

Theme Path/Name: /boot/grub/themes/ubuntu/theme-drs305.txt
Font Folder: None. Only the default Grub 2 font is used. (unicode.pf2, reported as "Unknown Regular 16" by the *lsfonts* command at the grub prompt)
Icons Location: /boot/grub/themes/ubuntu/icons
Background Image: /boot/grub/themes/ubuntu/drs305.png
[list]
[*]GIMP used to make the background of the icon images transparent.
[/list]
Special instructions:
[LIST]
[*]*/etc/default/grub* entry: GRUB_THEME=/boot/grub/themes/ubuntu/drs305-theme.txt
[*]Icons are determined by a "--class" entry in */boot/grub/grub.cfg* The default "--class" is "ubuntu" for entries located in the *10_linux* section of *grub.cfg*. 
[/LIST]

Notes:
[LIST]
[*]The menuentries are from a custom file, which accounts for the non-standard names and order.
[*]The background image and most icons are hand-made. The 'ubuntu' and 'windows' icons are available via the Grub Theming Guide referenced earlier.
[/LIST]

Theme Content (drs305-theme.txt):

> 
# Global Property
title-text: "GRUB 1.99RC Oneiric"
title-font: "Unknown Regular 16"
title-color: "green"
desktop-image: "/boot/grub/drs305.png"
#desktop-color: "#000000"
# Show the boot menu
+ boot_menu {
left = 10%
top = 15%
width = 85%
height = 75%
item_font = "Unknown Regular 16"
item_color = "lightgrey"
selected_item_color = "yellow"
item_height = 20
item_padding = 10 # Vertical spacing between menuentries.
item_spacing = 10
item_icon_space = 20 # Horizontal spacing between the icon and it's menuentry.
icon_width = 20
icon_height = 20
icon_spacing = 10
}

---

### Post by drs305 on 2011-08-16
Here's an expanded version of Post # 2, with a circular timer added. The additional entries are listed in **bold**.

The screenshot actually includes 3 different images - take your pick (just remove the other two sections in the theme) and adjust the "left" and "top" variables to place it where you wish it to appear.

To add the center image:
Add a center image to the theme folder (/boot/grub/themes/ubuntu).
The three examples I copied from Ubuntu system folders are
[LIST]
[*]/usr/share/app-install/icons/xfce4-clock.png
[*]/usr/share/app-install/icons/alarm-clock.png 
[*]/usr/share/app-install/icons/gworldclock.png
[/LIST]

Add a tick image.
I extracted the *tick.png* image from the Grub 2 Theming Guide's *demo* folder.
The number of 'ticks' is set by the "tick_num" setting. In this example, the number was 10, several of which have already disappeared as the timer counted down.

Geometry:
[LIST]
[*]Placement is set by the variables in the "+ circular progress" section.
[LIST]
[*]The center image will be the size of the icon. Adjust the icon image with an image editor such as GIMP if you wish to change the center image size.
[*]The ticks will be displaced around a circle whose diameter is set by the pixel distance designated in the "width" line. 
[LIST]
While the examples all have the tick marks outside the center image, you can set the 'width' smaller and have the tick marks actually appear *inside* the clock face with some experimentation. See the far right clock image.
[/LIST]
[*]The distance from the left border is set by the "left" variable. It can be designated by pixels, percentage, or both.
[*]The distance from the top is set by the "top" variable (% or pixels from the top of the screen).
[^]The "'start angle = -56"  sets the first tick to disappear as the one at approximately 1 o'clock.
[/LIST]
[/LIST]

In posting this theme, I've used 'code' tags rather than 'quote' tags to save space.
```

# GRUB2 gfxmenu Ubuntu Demo theme
# The Definitive Guide to Theming GRUB2,
# using the ubuntu1 demo theme from [http://www.gibibit.com](http://www.gibibit.com)
# Designed for 640x480 resolution
# Global Property
title-text: "GRUB 1.99RC Oneiric 11"
title-font: "Unknown Bold 16"
title-color: "green"
message-font: "Unknown Regular 16"
message-color: "white"
message-bg-color: "black"
desktop-image: "/boot/grub/themes/ubuntu/drs305.png" 	# overrides any other background image setting
desktop-color: "#000000" 								# desktop-color only used if desktop-image is not found

# Show the boot menu
+ boot_menu {
left = 10%
top = 15%
width = 85%
height = 55%
item_font = "Unknown Regular 16"
item_color = "lightgrey"
selected_item_color = "yellow"
item_height = 20
item_padding = 10
item_spacing = 10
item_icon_space = 20
icon_width = 20
icon_height = 20
icon_spacing = 10
}

[B]# Show a circular progress bar
+ circular_progress {
id = "__timeout__"
left = 10%
top = 80%
width = 50
height = 50
num_ticks = 10
start_angle = -56
ticks_disappear = true
# /usr/share/app-install/icons/xfce4-clock.png   /usr/share/app-install/icons/alarm-clock.png
center_bitmap = "xfce4-clock.png"
tick_bitmap = "tick.png"
}

# Show a circular progress bar
+ circular_progress {
id = "__timeout__"
left = 40%
top = 80%
width = 70
height = 50
num_ticks = 10
start_angle = -56
ticks_disappear = true
center_bitmap = "alarm-clock.png"
tick_bitmap = "tick.png"
}

# Show a circular progress bar
+ circular_progress {
id = "__timeout__"
left = 70%
top = 80%
width = 55  # Reduced so ticks are within the clock face
height = 70
num_ticks = 11
start_angle = -56
ticks_disappear = true
# /usr/share/app-install/icons/xfce4-clock.png   /usr/share/app-install/icons/alarm-clock.png
center_bitmap = "gworldclock-lg.png" # Modified image (enlarged)
tick_bitmap = "tick-sm-blk.png"  # Modified image (black and reduced size)
}[/B]

```

---

### Post by towheedm on 2011-10-27
I'd have expected at least a few GRUB themes posted by now.  Oh well ...

Here's a theme I created from the metacity/gtk+-2.0 theme 'Azenis' which can be found [here]("http://gnome-look.org/content/show.php/Azenis?content=106608").

The GRUB theme shows best at 1024x768.

To install the theme, first extract the archive, cd to the directory where the archive was extracted to and run the 'install.sh' script.

I forgot to include the Fixed Regular 13 font in the archive.  It is now included nd the archive updated.  Sorry for that.

---

### Post by drs305 on 2011-10-27
> **towheedm said:**
> I'd have expected at least a few GRUB themes posted by now.  Oh well ...

Here's a theme I created from the metacity/gtk+-2.0 theme 'Azenis' which can be found [here]("http://gnome-look.org/content/show.php/Azenis?content=106608").

The GRUB theme shows best at 1024x768.

To install the theme, first extract the archive, cd to the directory where the archive was extracted to and run the 'install.sh' script.

Thanks towheedm!

I've actually used your guide to create numerous themes but none are significantly different from what you have in your guide. I'd hoped there would be some more postings here as well, as using your tools and Grub 2's capabilities one can make some pretty interesting boot menus.

---

### Post by towheedm on 2011-10-28
So true.

I'm not an artist or graphics designer, so I will create themes based on other's images.

Let's hope we see some more theme soon.

I created this theme quickly in between what I hope would be my tutorial on creating Metacity/GTK+ themes.

I'll update the pdf file this weekend and put a link to this thread in it, so all new downloads should see it.

I was also contemplating requesting a GRUB theme section on gnome-llook.  What's your opinion on that?

---

### Post by Legendary_Bibo on 2011-10-28
I'm contemplating on making a NyanCat Grub2 theme.

---

### Post by Legendary_Bibo on 2011-10-28
Well I made one to fit to my desktop theme. I just took everything out of Axiom's Metacity theme and resized stuff and converted them to .png, and went through and changed the colors in towheedm's theme.txt file. I was confused about the install.sh script in there. It didn't seem to do anything, I had to manually link and copy stuff for it to work (which I could turn it into a script I guess).

Edit: Finally added a screenshot.

---

### Post by MG&amp;TL on 2011-10-28
Your themes look awesome. I had problems with serious lag on my machine though...how d'you get around that?

---

### Post by Legendary_Bibo on 2011-10-28
> **MG&TL said:**
> Your themes look awesome. I had problems with serious lag on my machine though...how d'you get around that?

I'm getting that as well, and trying to figure out why that's happening. My guess would be that there's too much being loaded in. I might reduce the size of the distributor logos and see if that helps.

I'll hit the down arrow then like half a second later it moves.

---

### Post by cecilpierce on 2011-10-28
I had that happen to with grub but for some reason burg works fine ?
:confused:

---

### Post by MG&amp;TL on 2011-10-28
Hey, cecil! ;)

---

### Post by Legendary_Bibo on 2011-10-28
I've been googling around, and the Grub2 theming department is really untapped, besides the themes in this thread I've come across like 3 others and 1 of them were another demo.

---

### Post by MG&amp;TL on 2011-10-28
I am writing a script to make the themes, but it's kinda stuttered to halt because there's no other devs, and even devs have off days. Anyone like to help?

I can take all programming languages, as I'd quite like to ditch the original.

---

### Post by Legendary_Bibo on 2011-10-28
> **MG&TL said:**
> I am writing a script to make the themes, but it's kinda stuttered to halt because there's no other devs, and even devs have off days. Anyone like to help?

I can take all programming languages, as I'd quite like to ditch the original.

Like converting Metacity themes to Grub2 themes?

I wonder if it's possible to make a gui to build the themes, and have a preview of what's going on.

---

### Post by MG&amp;TL on 2011-10-28
Well...Not really. More like (at the moment):


```
Enter a background image:  /home/michael/Background.jpg
Enter fonts to use(use "done" when finished): /home/michael/Myfont.ttf
etc. 


```


A GUI would be awesome. :D

preview....not sure. maybe we could have a set of files it could open (.grb, maybe?) and have themes distributed on gnome-art or whatever. With previews.

---

### Post by Legendary_Bibo on 2011-10-28
> **MG&TL said:**
> Well...Not really. More like (at the moment):


```
Enter a background image:  /home/michael/Background.jpg
Enter fonts to use(use "done" when finished): /home/michael/Myfont.ttf
etc. 


```
A GUI would be awesome. :D

preview....not sure. maybe we could have a set of files it could open (.grb, maybe?) and have themes distributed on gnome-art or whatever. With previews.

I'm writing out an installation script (seriously what did that install script do? :confused:), and I'll change some things so it's universal.

---

### Post by MG&amp;TL on 2011-10-28
....my script allows you to make your own and specify the values. If that's the question...?

Anyways, not the thread. PM me if you want to help.

And good idea, drs. Shame not many people use it.

---

### Post by Legendary_Bibo on 2011-10-28
haha sorry, I was just informing you of what I was up to. I'm almost done with the simple installation script.

I was thinking that we could set them up as tar archives that you can just install in some menu, kind of like how the gnome2 theme installer was, and then just have it execute the installation script within the tar file to move the contents over. That's if someone is up to making a simple GUI for it, other wise just extracting the tar balls with a folder containing everything, and executing an installation script will work.

---

### Post by MG&amp;TL on 2011-10-28
Yeah. 

So you're saying an application that can open and deploy pre-packaged GRUB themes?

Yeah. Can do that. I'll make a launchpad page, if I'm getting you straight. I'll PM you. presumably you can code? I can do basic stuff, but my major failing is the GUI stuff. Cannot do it. :(

---

### Post by Legendary_Bibo on 2011-10-28
> **MG&TL said:**
> Yeah. 

So you're saying an application that can open and deploy pre-packaged GRUB themes?

Yeah. Can do that. I'll make a launchpad page, if I'm getting you straight. I'll PM you. presumably you can code? I can do basic stuff, but my major failing is the GUI stuff. Cannot do it. :(

I'm still noobish at coding, most of my experience has been on .NET. I'm trying to learn Mono Sharp as well, the way gtk works is weird to me.

But I'll learn some more tonight and see if I can get something.

---

### Post by MG&amp;TL on 2011-10-28
> **Legendary_Bibo said:**
> I'm still noobish at coding, most of my experience has been on .NET. I'm trying to learn Mono Sharp as well, the way gtk works is weird to me.

But I'll learn some more tonight and see if I can get something.

I started all of six months ago. :D Noobish then, noobish now. I still google everything.

Would you prefer to have a C-based language or a fresher, newer one?

---

### Post by towheedm on 2011-10-28
> **Legendary_Bibo said:**
> I was confused about the install.sh script in there. It didn't seem to do anything, I had to manually link and copy stuff for it to work (which I could turn it into a script I guess).

You must change the variables in the script for proper installation.  Please see my GRUB guide.  Ah, but it's also a heavily commented script.

Next time, I'll look first.  Saw they were changed.

Ran the install script and it successfully installed the theme to /boot/grub/themes/Axiom.

---

### Post by towheedm on 2011-10-28
> **Legendary_Bibo said:**
> I'm getting that as well, and trying to figure out why that's happening. My guess would be that there's too much being loaded in. I might reduce the size of the distributor logos and see if that helps.

I'll hit the down arrow then like half a second later it moves.

It's not a problem with the theme.  It's a bug in GRUB.  Apparently the poll rate is too long.  There was a patch for it somewhere around.

Anyway, since the mod has stated that this thread is not for support ...

---

### Post by drs305 on 2011-10-28
> **towheedm said:**
> 
Anyway, since the mod has stated that this thread is not for support ...
Hehe. Well, I guess I did say that...

If one of you would start a new thread and put the link here we can all follow along.  :-)

---

### Post by Legendary_Bibo on 2011-10-28
> **towheedm said:**
> You must change the variables in the script for proper installation.  Please see my GRUB guide.  Ah, but it's also a heavily commented script.

Yeah I looked at your script in more detail d'oh! Well I stopped writing up my script and I'm working on the GUI installer, and I'll figure a way on how to incorporate MG&TL's stuff like changing Fonts and background images.

---

### Post by MG&amp;TL on 2011-10-28
Keep us informed, legendary_bibo! :)

---

### Post by Legendary_Bibo on 2011-10-29
Worked on the GUI when I could (this takes longer to do in Mono Develop than Visual Stuido btw).

I kept it simple, and this will give us something usable. It would be nice to have some advanced design options, but I'm not sure if Grub stretches the images and what not. So that may be a bit difficult. I do have one question, if you use a wallpaper that's not 1024x768 or just doesn't match grub's resolution, does it throw a fit?

I'll either start coding stuff tonight, or tomorrow.

---

### Post by MG&amp;TL on 2011-10-29
Nothing bad happens, I think it just stretches the wallpaper. Or compresses it.

---

### Post by MG&amp;TL on 2011-10-29
That is VERY cool btw. How did you get it done so fast?

---

### Post by Legendary_Bibo on 2011-10-29
> **MG&TL said:**
> That is VERY cool btw. How did you get it done so fast?

I haven't coded much yet, it's just the gui, but I used the graphical designer in Mono Develop which is just glade's gui designer (drag and drop stuff).

---

### Post by MG&amp;TL on 2011-10-29
Oh. Cool, okay. Put it up on launchpad so that we can all get at it. :D

---

### Post by Legendary_Bibo on 2011-10-29
> **MG&TL said:**
> Oh. Cool, okay. Put it up on launchpad so that we can all get at it. :D

I'll do that in the morning, it's a bit late right now. :popcorn:

I'll let you guys know when I get the launchpad up.

---

### Post by MG&amp;TL on 2011-10-29
Oh, sorry. V.early in morning here. Time issues....:D I keep forgetting.

---

### Post by Legendary_Bibo on 2011-10-29
> **MG&TL said:**
> Oh, sorry. V.early in morning here. Time issues....:D I keep forgetting.

It's up.

[https://launchpad.net/earlybird](https://launchpad.net/earlybird)

Launchpad is confusing though.

---

### Post by MG&amp;TL on 2011-10-29
> **Legendary_Bibo said:**
> It's up.

[https://launchpad.net/earlybird](https://launchpad.net/earlybird)

Launchpad is confusing though.


It is. Your best bet is here:

[http://doc.bazaar.canonical.com/latest/en/mini-tutorial/]("http://doc.bazaar.canonical.com/latest/en/mini-tutorial/")

Which I find is really helpful. Make a branch, add your code, commit, then push.

---

### Post by Legendary_Bibo on 2011-10-29
Well I got as far as figuring out how to filter stuff, but a lot of what we need to do will involve some bash, which I don't know how I would pass parameters to a bash script, but with towheedm's install script, much of the leg work is done for basic functionality.

I'm used to Windows, so gtk stuff is weird to me :P
Also, I'm spoiled from MSDN :D
Also, I'm noobish at C#.

We'll definitely need to set guidelines once it's done.

---

### Post by MG&amp;TL on 2011-10-29
Perhaps somebody could write a script to check that all componements are there? Like debian packaging, but on a smaller scale.

---

### Post by MG&amp;TL on 2011-10-29
Parameters: probably not exactly what you want, but helpful nonetheless:

[http://floppix.ccai.com/scripts1.html]("http://floppix.ccai.com/scripts1.html")

Would you like me to start setting up the launchpad bzr branch?

---

### Post by StephanG on 2011-10-30
Well, it's not exactly Grub, I use Burg.  But this is what it looks like:

---

### Post by MG&amp;TL on 2011-10-30
> **StephanG said:**
> Well, it's not exactly Grub, I use Burg.  But this is what it looks like:

Yeah, I looked at this- the only problem seems to be that it's no longer maintained.

---

### Post by Legendary_Bibo on 2011-11-04
Grub theme #2 for me. Oxygen. :D

I've got a few minor tweaks left to do before I release it, but this is what it looks like so far.

How do you guys get the progress bar to show up in your VMs by the way? I don't want to have to setup a dual boot VM to get it to show, so when I do the pounding the shift key thing to get to my grub menu on my VM the progress bar never shows up, but it does on my laptop which is a dual boot setup.

A couple things I've noticed also, setting progress bar text to false doesn't seem to work, and I don't think the scrollbars are working so I set them to false. On my last theme I had them true and setup some dummy entries in the grub menu, and the scroll bars wouldn't show up, and I couldn't go past the fourth entry. It might have been working, but I couldn't see the selection.

Also does anyone know if there's Oxygen distro icons? Faenza has them.

---

### Post by drs305 on 2011-11-04
In my VM theme, I just have the following code and it displays fine:
```
+ progress_bar {
   id = "__timeout__"
   left = 6%
   top = 60%	
   width = 83%
   height = 15	
#   bg_color = "lightgrey"
#   bg_color = "201, 0, 22"
#   fg_color = "255, 99,9"
   bg_color = "red"
   fg_color = "green"
   border_color = "255, 181, 21"
   show_text = true
   font = "Unknown Regular 16"
   text_color = "white"
   text = "@TIMEOUT_NOTIFICATION_LONG@"
}
```

---

### Post by Legendary_Bibo on 2011-11-04
Done with the Oxygen theme.

[http://gnome-look.org/content/show.php/Oxygen+Grub+2+Theme?content=146508](http://gnome-look.org/content/show.php/Oxygen+Grub+2+Theme?content=146508)

---

### Post by towheedm on 2011-11-04
> **Legendary_Bibo said:**
> when I do the pounding the shift key thing to get to my grub menu on my VM the progress bar never shows up, but it does on my laptop which is a dual boot setup.

If you need to do this then GRUB_HDDEN_TIMEOUT_QUIET is set.  When you press the key combo to get to the GRUB menu, the timeout is automatically set to -1 (timeout has expired), so the progressbar will not show.  This is what happens when you press a key during the timeout period and the progressbar disappears.

To show the menu you must comment out the GRUB_HIDDEN_TIMEOUT and GRUB_HDDEN_TIMEOUT_QUIET variables and also uncomment the GRUB_TIMEOUT variable in [COLOR=Blue]/etc/default/grub[/COLOR]:

```
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=20

```Of course make sure you update GRUB's configuration file after:
```
sudo update-grub
```For a multi OS setup, this is automatically done by GRUB so that the menu shows to allow you to select an OS.  The progressbar should now show and countdown from the value set by GRUB_TIMEOUT.


> On my last theme I had them true and setup some dummy entries in the  grub menu, and the scroll bars wouldn't show up, and I couldn't go past  the fourth entry. It might have been working, but I couldn't see the  selection.The scrollbars are automatically hidden when the menu items fit within the viewport set by the menu background ( the center slice).

Did you set these additional entries in 40_custom?  The entries should be at least:

```
menuentry 'Some OS' --class someOS {
    set root='(hd1,0)'
}

```I've found that the additional menu entries will never show if at least one GRUB command is not included within the menuentry block.

[COLOR=Red]As stated in the guide, the progressbar is mapped unto the east slice and must be exactly the same width as the east slice.  If the east slice has a width smaller than the width of the progressbar, the progressbar's image is cropped to the width of the east slice.  This also means that if you do not have an east slice image, the progressbar will never be shown.
[/COLOR]
Hope this helps.

---

### Post by Legendary_Bibo on 2011-11-05
> **towheedm said:**
> If you need to do this then GRUB_HDDEN_TIMEOUT_QUIET is set.  When you press the key combo to get to the GRUB menu, the timeout is automatically set to -1 (timeout has expired), so the progressbar will not show.  This is what happens when you press a key during the timeout period and the progressbar disappears.

To show the menu you must comment out the GRUB_HIDDEN_TIMEOUT and GRUB_HDDEN_TIMEOUT_QUIET variables and also uncomment the GRUB_TIMEOUT variable in [COLOR=Blue]/etc/default/grub[/COLOR]:

```
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=20

```Of course make sure you update GRUB's configuration file after:
```
sudo update-grub
```For a multi OS setup, this is automatically done by GRUB so that the menu shows to allow you to select an OS.  The progressbar should now show and countdown from the value set by GRUB_TIMEOUT.


Sweet thanks. Now I can actually include the progress bar in my screenshots

> **towheedm said:**
> 
[COLOR=Red]As stated in the guide, the progressbar is mapped unto the east slice and must be exactly the same width as the east slice.  If the east slice has a width smaller than the width of the progressbar, the progressbar's image is cropped to the width of the east slice.  This also means that if you do not have an east slice image, the progressbar will never be shown.
[/COLOR]
Hope this helps.

I tried that, it looked pretty bad. I tried all sorts of voodoo to get the east side of the progress bar to behave correctly, but to no avail.

---

### Post by towheedm on 2011-11-05
> As stated in the guide, the progressbar is mapped unto  the east slice and must be exactly the same width as the east slice.   If the east slice has a width smaller than the width of the progressbar,  the progressbar's image is cropped to the width of the east slice.   This also means that if you do not have an east slice image, the  progressbar will never be shown.What a dumb mistake on my part.  That should be scrollbar and not progressbar. my apologies.

Now, is your problem with the progressbar or scrollbar?  Include a screenshot of the problem please.

Your screenshot shows a basic progressbar and not a styled progressbar.

Have a look at the Azenis theme in Post #4.

---

### Post by Legendary_Bibo on 2011-11-05
> **towheedm said:**
> What a dumb mistake on my part.  That should be scrollbar and not progressbar. my apologies.

Now, is your problem with the progressbar or scrollbar?  Include a screenshot of the problem please.

Your screenshot shows a basic progressbar and not a styled progressbar.

Have a look at the Azenis theme in Post #4.

Oh I'm not using the scrollbar on this theme. I made the area bigger and I figured there's no way anyone would have more OS's then what would fill the space with.

I did have one slight problem with the progress bar which was that the highlight would over lap the east side by a couple of pixels.

---

### Post by towheedm on 2011-11-05
The Oxygen theme looks pretty good.  I see one problem why the scrollbars don't show well.  I'll look at the theme in more depth a bit later and start a new thread for support.  I'll post the link. Or, you start the thread and post the link.

BTW:  Always take into account that the user may have tons of menu items.  I have at 4 custom built kernels, a stock kernel, 2 XP, F14 and F15, Natty, Sabayon, plus a few more!

---

### Post by Legendary_Bibo on 2011-11-05
> **towheedm said:**
> The Oxygen theme looks pretty good.  I see one problem why the scrollbars don't show well.  I'll look at the theme in more depth a bit later and start a new thread for support.  I'll post the link. Or, you start the thread and post the link.

BTW:  Always take into account that the user may have tons of menu items.  I have at 4 custom built kernels, a stock kernel, 2 XP, F14 and F15, Natty, Sabayon, plus a few more!

Well in this one I reduced the size of the east side parts and had stretched the center, but I can change them back to accommodate a scrollbar.

haha, dang, I guess I there are some cases that need a scrollbar.

---

### Post by _uli_ on 2012-03-24
A very simple Grub2 theme is part of my artwork proposal for Debian and can be found here:

[http://wiki.debian.org/DebianArt/Themes/journey#Grub_2_-_Theme](http://wiki.debian.org/DebianArt/Themes/journey#Grub_2_-_Theme)

It is supposed to look similar to the default GDM3 login screen. It is based on an Ubuntu theme 
created by Jo Shields at [http://retro.apebox.org/grubthemes/]("http://retro.apebox.org/grubthemes/") 

The guide at [http://www.4shared.com/file/lFCl6wxL/grub_guidetar.html]("http://www.4shared.com/file/lFCl6wxL/grub_guidetar.html")
was very helpful. Thanks a lot!

regards
Ulrich

---

### Post by TREESofRIGHTEOUSNESS on 2012-04-16
I would really like to see a themed GRUB for Ubuntu... this sounds excellent!!

---

### Post by towheedm on 2012-04-16
> **TREESofRIGHTEOUSNESS said:**
> I would really like to see a themed GRUB for Ubuntu... this sounds excellent!!

Have patient my friend, a default theme will be included in GRUB 2.00 and is already included in the bzr branch of GRUB, presently at GRUB 2.00~Beta3.  But I'm guessing, this will never be upgraded in Oneiric or releases prior to it.

---

### Post by TREESofRIGHTEOUSNESS on 2012-04-17
Well, I just finished a temporary theme based on the definitive guide, and using the demo theme included...  I am really surprised this hasn't gotten more attention...  a nice GUI should be made to do all this stuff....  But, anyway... at least it can be done!!

---

### Post by drs305 on 2012-04-17
> **TREESofRIGHTEOUSNESS said:**
> Well, I just finished a temporary theme based on the definitive guide, and using the demo theme included...  I am really surprised this hasn't gotten more attention...  a nice GUI should be made to do all this stuff....  But, anyway... at least it can be done!!

An Ubuntu Grub theme is being worked on by the devs for the release of Grub 2.0 (as opposed to the current Grub 1.99).

---

### Post by Mopar1973Man on 2012-04-17
I got to admit there is a some killer looking GRUB themes here. I'm still a noob but just sitting here droolin' over what some of you guys have put together... All I can say is WOW!

---

### Post by cecilpierce on 2012-04-18
> **_uli_ said:**
> A very simple Grub2 theme is part of my artwork proposal for Debian and can be found here:

[http://wiki.debian.org/DebianArt/Themes/journey#Grub_2_-_Theme](http://wiki.debian.org/DebianArt/Themes/journey#Grub_2_-_Theme)

It is supposed to look similar to the default GDM3 login screen. It is based on an Ubuntu theme 
created by Jo Shields at [http://retro.apebox.org/grubthemes/]("http://retro.apebox.org/grubthemes/") 

The guide at [http://www.4shared.com/file/lFCl6wxL/grub_guidetar.html]("http://www.4shared.com/file/lFCl6wxL/grub_guidetar.html")
was very helpful. Thanks a lot!

regards
Ulrich

Thats real nice looking, I tried to add a couple icons but some didnt work and some did,
Thanks.

---

### Post by TREESofRIGHTEOUSNESS on 2012-04-18
When I choose an option on the menu it goes to the terminal screen, but I have "quiet splash" as kernel options, so it really looks like something went wrong (as a black screen in a box pops up)....  what are some alternatives?  Can, I just have a fullscreen intermediate image?  can I just bypass the terminal displaying?  Can an "icon" pop up that says something like "Loading (os name)"
though I like having a nicer GRUB SCREEN than just a background and colored fonts....

---

### Post by _uli_ on 2012-05-03
Hi cecilpierce!
Thanks for the feedback! :-)

I just like to add that the artwork has changed a bit in the recent weeks.

First of all, the Grub2 theme I was writing about in my original message is this one:
[http://wiki.debian.org/DebianArt/Themes/journey_v1#Grub_2_-_Theme](http://wiki.debian.org/DebianArt/Themes/journey_v1#Grub_2_-_Theme)

[IMG]http://lazybrowndog.net/debian/wheezy/_grub-theme/journey-grub-theme-screenshot-small.png[/IMG]

I stopped working on this theme because it was trying to look like the old GDM of Gnome <3.4. Debian Wheezy plans to come with Gnome 3.4, so this wasn't really a good choice. Of course this version is still available under the above link and free for anyone to use or tweak.

My new Grub2 theme tries to fit in better with Gnome >= 3.4.
[http://lazybrowndog.net/debian/wheezy/journey/grub.html](http://lazybrowndog.net/debian/wheezy/journey/grub.html)

After you downloaded it, I have changed the background from the dark texture (shown in your screenshot) to the lighter hexagon one shown here: 

[IMG]http://lazybrowndog.net//debian/wheezy/journey/_grub-theme/journey-grub-theme-screenshot-preview.png[/IMG]

Please download the package again to get that background.

> **cecilpierce said:**
> I tried to add a couple icons but some didnt work and some did,
Thanks.

Yes. I did not implement the workaround mentioned on page 80 of the great documentation by Towheed Mohammed:
[http://forums.debian.net/viewtopic.php?f=16&t=78121](http://forums.debian.net/viewtopic.php?f=16&t=78121)

So the icon is chosen by grub according to the class that is registered in the menuentry in /boot/grub/grub.cfg (see the guide at page 51). It seems that not all operating systems are registered correctly by Grub2.

best wishes
Ulrich

---

### Post by cecilpierce on 2012-05-03
Thanks Ulrich for the update, I have two hard drives so sda has Grub and sdb has Burg, burg is a lot easier to change things on the fly, maybe some day grub will have all that fancy stuff.
:p

Cecil

---

### Post by GrubThemeArtist on 2012-05-14
Aero
[http://db.tt/oJeOe2Uk]("http://db.tt/oJeOe2Uk")

[IMG]http://dl.dropbox.com/u/40152532/GrubThemes/SmallPhotos/Aero.png[/IMG]

Tropical
[http://db.tt/o1sGXqwB]("http://db.tt/o1sGXqwB")

[IMG]http://dl.dropbox.com/u/40152532/GrubThemes/SmallPhotos/Tropical.png[/IMG]

Autumn
[http://db.tt/8JQg6Ibv]("http://db.tt/8JQg6Ibv")

[IMG]http://dl.dropbox.com/u/40152532/GrubThemes/SmallPhotos/Autumn.png[/IMG]

---

### Post by GrubThemeArtist on 2012-05-14
MLP GRUB Themes.

Applejack:
[http://db.tt/NPGMHtwt](http://db.tt/NPGMHtwt)

Fluttershy:
[http://db.tt/keZpk6jV](http://db.tt/keZpk6jV)

Pinkie Pie:
[http://db.tt/A9syCgjY](http://db.tt/A9syCgjY)

Rainbow Dash:
[http://db.tt/ps4RB0pF](http://db.tt/ps4RB0pF)

Rarity:
[http://db.tt/BAdoGZj9](http://db.tt/BAdoGZj9)

Twilight Sparkle:
[http://db.tt/VlcSg0Qj](http://db.tt/VlcSg0Qj)

They all have this form

[IMG]http://dl.dropbox.com/u/40152532/GrubThemes/SmallPhotos/Rarity.png[/IMG]

Also, Early Bird, a simple GRUB theme installer and manager (will be updated regularly).

Download link: [http://db.tt/f4odUpwQ]("http://db.tt/f4odUpwQ")

Needs mono runtime.

---

### Post by cecilpierce on 2012-05-14
@ GrubThemeArtist

Thanks for all the themes and info, looks real nice,

Cecil

---

### Post by towheedm on 2012-05-14
Really cool themes.  I don't fancy the Windows look on Linux though, but the theme is very well done.

Could you right align the text on Tropical theme?  It will look more complete.

Dark themes are my thing, so of course my favorite would have to be Autumn.

I will certainly install these sometime soon.  Keep 'em coming.

---

### Post by cecilpierce on 2012-05-15
I like dark themes more to.
Is there suppose to be a time out bar on the bottom, i dont see it ?

---

### Post by towheedm on 2012-05-15
> **cecilpierce said:**
> I like dark themes more to.
Is there suppose to be a time out bar on the bottom, i dont see it ?

The theme is using the circular_progress indicator.  That's the circle with the three dots in it.

There are two types of progress indicators: the horizontal progress indicator and the circular progress indicator.  Also, progress indicators are optional.  The theme designer may or may not decide to use one or even both.

---

### Post by cecilpierce on 2012-05-15
@towheedm

I dont see the circle around the 3 dots ?

---

### Post by GrubThemeArtist on 2012-05-15
> **cecilpierce said:**
> @towheedm

I dont see the circle around the 3 dots ?

The pony themes have no form of progress indication. I wanted them as smooth and clean as possible. The Autumn theme uses a circular progress bar though.

Also what are you using to test them in that Window? I've been using VMs to test them.

---

### Post by cecilpierce on 2012-05-15
> **GrubThemeArtist said:**
> The pony themes have no form of progress indication. I wanted them as smooth and clean as possible. The Autumn theme uses a circular progress bar though.

Also what are you using to test them in that Window? I've been using VMs to test them.

I use sudo grub-emu in a terminal.

---

### Post by GrubThemeArtist on 2012-05-15
> **cecilpierce said:**
> I use sudo grub-emu in a terminal.

Thanks. I wish I knew that before.

---

### Post by cecilpierce on 2012-05-15
> **GrubThemeArtist said:**
> Thanks. I wish I knew that before.

Your welcome, keep up the good work.

---

### Post by towheedm on 2012-05-16
> **cecilpierce said:**
> @towheedm

I dont see the circle around the 3 dots ?

My mistake, I thought you were referring to the Autumn theme.

---

### Post by cecilpierce on 2012-05-16
Sorry, Autumn timer works fine.

---

### Post by xalaros330 on 2012-05-20
[_[SIZE="3"]Matrix[/SIZE]_]("http://kde-look.org/content/show.php/matrix+theme+for+grub?content=151010") designed for 1366x768 screens.

[IMG]http://dl.dropbox.com/u/80562560/grub%20matrix%20theme/preview.jpg[/IMG]

---

### Post by GrubThemeArtist on 2012-05-21
You might want to redo your zipping. You packaged a tar file as a tar.gz which gives an error with an archive manager.

---

### Post by cecilpierce on 2012-05-21
> **GrubThemeArtist said:**
> You might want to redo your zipping. You packaged a tar file as a tar.gz which gives an error with an archive manager.

I just opened it with midnight commander and it looked ok, maybe he fixed it ?

---

### Post by xalaros330 on 2012-05-22
> **cecilpierce said:**
> I just opened it with midnight commander and it looked ok, maybe he fixed it ?

No, I did not change it, it worked fine with Ark as it was, but GrubThemeArtist was right, it was a tar file with .tar.gz ending.

I've fixed it now, thanks.

---

### Post by cecilpierce on 2012-06-18
Any new themes cookin ?

):P

---

### Post by GrubThemeArtist on 2012-06-21
> **cecilpierce said:**
> Any new themes cookin ?

):P

I just finished a multi resolution theme for a team. I'll be back to original creations soon. I've still got some ideas of what I want to do.

I think from now on I'll be making the themes in multiple resolutions. :D

---

### Post by cecilpierce on 2012-06-21
> **GrubThemeArtist said:**
> I just finished a multi resolution theme for a team. I'll be back to original creations soon. I've still got some ideas of what I want to do.

I think from now on I'll be making the themes in multiple resolutions. :D

Very good GTA, having fun with themes  :D

Question:
Do you know why grub-emu hangs up and won't let you get out of it except kill the terminal ?

p.s. and you can't move around while in it ?

---

### Post by GrubThemeArtist on 2012-06-21
> **cecilpierce said:**
> Very good GTA, having fun with themes  :D

Question:
Do you know why grub-emu hangs up and won't let you get out of it except kill the terminal ?

p.s. and you can't move around while in it ?

Yes, I was wondering the same thing. It doesn't hang up, click on the terminal window you used to open it up and then press the arrow keys while it's focused then your selection will move around, and escape closes it. The terminal captures the input.

---

### Post by cecilpierce on 2012-06-21
> **GrubThemeArtist said:**
> Yes, I was wondering the same thing. It doesn't hang up, click on the terminal window you used to open it up and then press the arrow keys while it's focused then your selection will move around, and escape closes it. The terminal captures the input.

OK thanks, I'll try that.

---

### Post by cecilpierce on 2012-06-22
Thanks GTA, it took me awhile to figure that out. It works for looking at the list.
But...I wish someone would fix it like the one in BURG  ):P

---

### Post by drs305 on 2012-06-28
GRUB 2.0 has just been released and includes it's own theme: starcraft

Grub 2.0 is not in the Ubuntu repositories nor in use on any current release of Ubuntu, but if you want to compile it you can get the files from the following location:
[http://ftp.gnu.org/gnu/grub/grub-2.00.tar.gz]("http://ftp.gnu.org/gnu/grub/grub-2.00.tar.gz")

---

### Post by cecilpierce on 2012-06-28
Well I gave it a shot! It didnt come out so good, just a plain black and white menu with alot of extra junk ):P

Good thing I have other grubs on here   :lolflag:

p.s.

drs305, did you try it ?

---

### Post by drs305 on 2012-06-29
> **cecilpierce said:**
> 
drs305, did you try it ?

No I haven't. I decided I didn't want to compile it so I'm hoping it may be incorporated into Quantal, which I'm currently testing.

---

### Post by cecilpierce on 2012-06-29
@drs305

Im in QQ to, my compile didnt go to smooth so I'll wait and see if it makes it in the updates, thanks

---

### Post by towheedm on 2012-06-29
I built it on Squeeze when it was at beta 3.  Built went smoothly and I got the default theme.  The theme is not too shabby, but not as good as some of the more recent ones posted here.

---

### Post by GrubThemeArtist on 2012-07-05
I just ripped the theme from the source and installed it on a VM with Ubuntu 11.10. I thought it was meh. The corners didn't have any antialiasing, and the text is dark on a dark background.

Anyways, I should have a new one by tomorrow (got distracted with irl stuff). My next one will have a minimalistic look to it, support for multiple resolutions, and have a dark and light version.

---

### Post by szymon_g on 2012-07-05
Hm... what's the point of doing themes of something that- in "perfect situation" would not being seen? I mean: seriously, how long (and often) are you watching grub?

---

### Post by GrubThemeArtist on 2012-07-06
> **szymon_g said:**
> Hm... what's the point of doing themes of something that- in "perfect situation" would not being seen? I mean: seriously, how long (and often) are you watching grub?

Because we can (and it's enjoyable when you've got the right set up to where you're only "creating" and you're not working (font conversions and installation for testing)). If you're a dual booter, you see it often. Also, it's interesting to do. I'm also learning how to make plymouth themes, and after that I'm going to move to gdm or lightdm theming. It'd be nice to have an aesthetically consistent boot to run process.

Anyways here's a preview of my next one. I wanted to go with something simple since I'm making this in 4 different resolutions and making a dark version of each of those resolutions. I think it was Towheed who said he liked dark themes.

[IMG]http://i.imgur.com/eW7yD.png[/IMG]

---

### Post by cecilpierce on 2012-07-06
I see it alot since I have 8 disrto's on this pc and testing QQ and another 64bit pc with 4 on it, better then seeing a plain old text based bla screen all the time
:p

GTA, I also like the dark themes, still waiting for the new one   ):P

---

### Post by cecilpierce on 2012-07-07
> **GrubThemeArtist said:**
> 
Anyways here's a preview of my next one. I wanted to go with something simple since I'm making this in 4 different resolutions and making a dark version of each of those resolutions. I think it was Towheed who said he liked dark themes.

[IMG]http://i.imgur.com/eW7yD.png[/IMG]

That looks really great ):P

---

### Post by GrubThemeArtist on 2012-07-07
Ran into an issue with recoloring stuff for the dark version, so I'll have to come back to it tomorrow. Anyways, here's the light version. I made it for 3 different resolutions. I was going to do 800x600 but got lazy. :D

[1600x1200]("http://dl.dropbox.com/u/40152532/GrubThemes/Monochrome-Light_1600x1200.tar.gz")
[1280x1024]("http://dl.dropbox.com/u/40152532/GrubThemes/Monochrome-Light_1280x1024.tar.gz")
[1024x768]("http://dl.dropbox.com/u/40152532/GrubThemes/Monochrome-Light_1024x768.tar.gz")

---

### Post by karmila on 2012-07-07
> **GrubThemeArtist said:**
> Ran into an issue with recoloring stuff for the dark version, so I'll have to come back to it tomorrow. Anyways, here's the light version. I made it for 3 different resolutions. I was going to do 800x600 but got lazy. :D

[1600x1200]("http://dl.dropbox.com/u/40152532/GrubThemes/Monochrome-Light_1600x1200.tar.gz")
[1280x1024]("http://dl.dropbox.com/u/40152532/GrubThemes/Monochrome-Light_1280x1024.tar.gz")
[1024x768]("http://dl.dropbox.com/u/40152532/GrubThemes/Monochrome-Light_1024x768.tar.gz")
Hi GTA,

I downloaded the theme. There is two installation scripts (EarlyBirdInstall.sh and install.sh) inside the folder.
Which one should i use?

---

### Post by GrubThemeArtist on 2012-07-08
> **karmila said:**
> Hi GTA,

I downloaded the theme. There is two installation scripts (EarlyBirdInstall.sh and install.sh) inside the folder.
Which one should i use?

The install.sh script. The Early Bird script is used by Early Bird, a graphical application I wrote that lets you install themes graphically and lets you switch between installed themes. I think I posted a link to it a couple pages back (I think it's the post with a bunch of screenshots). You'll need Mono to run it though.

---

### Post by karmila on 2012-07-08
> **GrubThemeArtist said:**
> The install.sh script. The Early Bird script is used by Early Bird, a graphical application I wrote that lets you install themes graphically and lets you switch between installed themes. I think I posted a link to it a couple pages back (I think it's the post with a bunch of screenshots). You'll need Mono to run it though.

Thanks. I don't have mono installed right now, so install.sh then :D

I ran the install script, got this:
```
newb@homePC:~/Monochrome-Light_1024x768$ sudo sh install.sh 
install.sh: 27: install.sh: let: not found
```

Ubuntu 12.04
Grub Version: 1.99-21ubuntu3.1

---

### Post by GrubThemeArtist on 2012-07-08
I always use 

```
sudo ./install.sh
```

without issue.

---

### Post by karmila on 2012-07-08
> **GrubThemeArtist said:**
> I always use 

```
sudo ./install.sh
```without issue.

Ah yes. No problem with the script. 
Seems not working with the previous command.

Going to reboot to see how it looks... 

And... thank you it looks really nice :p

---

### Post by GrubThemeArtist on 2012-07-08
> **karmila said:**
> Ah yes. No problem with the script. 
Seems not working with the previous command.

Going to reboot to see how it looks... 

And... thank you it looks really nice :p

Glad you like it. :D

---

### Post by GrubThemeArtist on 2012-07-08
Dark version:

[IMG]http://i.imgur.com/ASSDN.png[/IMG]

Links:
[1600x1200](http://db.tt/2MCBUr0H)
[1280x1024](http://db.tt/PfVKJqxn)
[1024x768](http://db.tt/ZGGCXKHn)

---

### Post by GrubThemeArtist on 2012-07-13
Hey Towheed, I'm thinking about converting your pdf to a web page and I figured drs305 could link to it from here to get people more involved.

---

### Post by cecilpierce on 2012-08-22
> **GrubThemeArtist said:**
> Hey Towheed, I'm thinking about converting your pdf to a web page and I figured drs305 could link to it from here to get people more involved.

Where did every body go ?

Nothing new ?

---

### Post by Jakin on 2012-08-22
I don't really theme it- but i slap an image on there.




[http://browse.deviantart.com/?qh=&section=&q=chip+pack#/d3kd8ar](http://browse.deviantart.com/?qh=&section=&q=chip+pack#/d3kd8ar)
(AMD version)

---

### Post by cecilpierce on 2012-08-26
Whats going on with GRUB 2.00 ?

---

### Post by towheedm on 2012-08-26
> **cecilpierce said:**
> Whats going on with GRUB 2.00 ?

What do you mean?  GRUB v2.00 was released some time ago.

---

### Post by cecilpierce on 2012-08-27
> **towheedm said:**
> What do you mean?  GRUB v2.00 was released some time ago.

Synaptic still 1.99.... but I tried 2 from the ppa and it was a mess for me, I stll use burg on the main HD and experiment with grub on thr secondary HD.

---

### Post by GrubThemeArtist on 2012-11-03
I just finished another one (I made a Gnome Shell GRUB theme a while ago, I guess I forgot to post it here).

I call it simpleBlue :D

[IMG]http://i.imgur.com/Pm4R4.png[/IMG]

_Download link:_
[http://db.tt/s5FjyOcq]("http://db.tt/s5FjyOcq")

_XCF Files:_
[http://db.tt/01smR6et]("http://db.tt/01smR6et")

---

### Post by cecilpierce on 2012-11-04
Thats nice...:)  Just DL it, thanks

What are the XCF files for ?

---

### Post by GrubThemeArtist on 2012-11-04
Oh those are the files for the menu and the little info pane in case you want to change the background color like to green or red or pink or something.

---

### Post by GrubThemeArtist on 2012-11-04
This is the Gnome Shell like theme I made. The tar file also has a version of it with the Beefy-Miracle wallpaper (and you can change out the distributor logo if you would like). I also made a Plymouth theme of each one as well. I need to make the animations smoother though.

Download link:
[http://db.tt/j5FfQk1G]("http://db.tt/j5FfQk1G")

Screenshot:
[IMG]http://i.imgur.com/g8c3P.png[/IMG]

If you use Fedora, or a distro that uses the GDM login screen, it makes a really consistent looking boot up.

---

### Post by towheedm on 2012-11-06
Someone recently reported that the install.sh script did not work with GRUB 2.00.  While the guide is for 1.99, themes should still work un-modified on 2.00, so I've patch the install.sh script to also work on 2.00.

You can get it from post # 28 here:[http://ubuntuforums.org/showthread.php?t=1534689&page=3](http://ubuntuforums.org/showthread.php?t=1534689&page=3)

I've also included it in the main download archive.

---

### Post by GrubThemeArtist on 2012-11-06
What were the changes made?

---

### Post by towheedm on 2012-11-06
OP, please allow me to post this here as I believe more GRUB2 themers will see it here than if I created a new thread.  Thanks.

There are now quite a few themes created in this thread for GRUB2.  It would be nice to package them for distribution and keep them all in one archive.

For this, I'm thinking about creating a grub2-themes.deb package.  If there's enough interest, I'll certainly persue it.

There are however, certain requirements imposed by the **Debian Policy Manual** before a package is accepted for inclusion in it's repos.  Since Ubuntu is based on Debian and uses it's packaging system, I'm guessing they would also be required by Ubuntu.

If you are interested in having your theme included in the package, please e-mail me (please do not PM me) with the subject line **Request to include GRUB2 theme in DEB package**.  If you have the guide, then my e-mail address is in it.  I'll then reply with the requirements.

Hmm, probably I should create a small text file with the requirements and attach it here.

Thanks.

---

### Post by GrubThemeArtist on 2012-11-06
You have my permission. I wish I got into the habit of making themes for other resolutions besides 1024x768 early on, but what can you do.

I've made 20 myself so that should be a good starting point.

---

### Post by towheedm on 2012-11-06
> **GrubThemeArtist said:**
> What were the changes made?

Two main changes that affected the install.sh script were:

[LIST]
[*] Prefixes are now quoted, ie: sysconfdir=/etc is now sysconfdir="/etc".
[*] The variable GRUB_PREFIX is no longer set in grub-mkconfig.  Previously, it was: GRUB_PREFIX=`echo '/boot/grub' | sed "s,//*,/,g"`
[/LIST]

There are several other changes, but they do not affect the install.sh script.

Here a diff:
```
--- /usr/sbin/grub-mkconfig (1.99)    2011-11-13 01:13:56.000000000 -0400
+++ grub-mkconfig (2.00)   2012-11-06 23:41:04.995693225 -0400
@@ -18,43 +18,47 @@
 # along with GRUB.  If not, see <http://www.gnu.org/licenses/>.
 
 transform="s,x,x,"
-
-prefix=/usr
-exec_prefix=${prefix}
-sbindir=${exec_prefix}/sbin
-bindir=${exec_prefix}/bin
-libdir=${exec_prefix}/lib
-sysconfdir=/etc
+prefix="/usr"
+exec_prefix="${prefix}"
+datarootdir="${prefix}/share"
+
+prefix="/usr"
+exec_prefix="${prefix}"
+sbindir="${exec_prefix}/sbin"
+bindir="${exec_prefix}/bin"
+sysconfdir="/etc"
 PACKAGE_NAME=GRUB
-PACKAGE_VERSION=1.99-14
+PACKAGE_VERSION=2.00
 host_os=linux-gnu
-datarootdir=${prefix}/share
-datadir=${datarootdir}
-pkgdatadir=${datadir}/`echo grub | sed "${transform}"`
+datadir="${datarootdir}"
+if [ "x$pkgdatadir" = x ]; then
+    pkgdatadir="${datadir}/grub"
+fi
 grub_cfg=""
-grub_mkconfig_dir=${sysconfdir}/grub.d
+grub_mkconfig_dir="${sysconfdir}"/grub.d
 
 self=`basename $0`
 
-grub_mkdevicemap=${sbindir}/`echo grub-mkdevicemap | sed "${transform}"`
-grub_probe=${sbindir}/`echo grub-probe | sed "${transform}"`
+grub_probe="${sbindir}/`echo grub-probe | sed "${transform}"`"
+grub_editenv="${bindir}/`echo grub-editenv | sed "${transform}"`"
 grub_script_check="${bindir}/`echo grub-script-check | sed "${transform}"`"
 
-GRUB_PREFIX=`echo '/boot/grub' | sed "s,//*,/,g"`
+export TEXTDOMAIN=grub
+export TEXTDOMAINDIR="${datarootdir}/locale"
+
+. "${pkgdatadir}/grub-mkconfig_lib"
 
 # Usage: usage
 # Print the usage.
 usage () {
-    cat <<EOF
-Usage: $self [OPTION]
-Generate a grub config file
-
-  -o, --output=FILE       output generated config to FILE [default=stdout]
-  -h, --help              print this message and exit
-  -v, --version           print the version information and exit
-
-Report bugs to <bug-grub@gnu.org>.
-EOF
+    gettext_printf "Usage: %s [OPTION]\n" "$self"
+    gettext "Generate a grub config file"; echo
+    echo
+    print_option_help "-o, --output=$(gettext FILE)" "$(gettext "output generated config to FILE [default=stdout]")"
+    print_option_help "-h, --help" "$(gettext "print this message and exit")"
+    print_option_help "-v, --version" "$(gettext "print the version information and exit")"
+    echo
+    gettext "Report bugs to <bug-grub@gnu.org>."; echo
 }
 
 argument () {
@@ -62,7 +66,7 @@
   shift
 
   if test $# -eq 0; then
-      echo "$0: option requires an argument -- '$opt'" 1>&2
+      gettext_printf "%s: option requires an argument -- \`%s'\n" "$0" "$opt" 1>&2
       exit 1
   fi
   echo $1
@@ -87,7 +91,7 @@
     grub_cfg=`echo "$option" | sed 's/--output=//'`
     ;;
     -*)
-    echo "Unrecognized option \`$option'" 1>&2
+    gettext_printf "Unrecognized option \`%s'\n" "$option" 1>&2
     usage
     exit 1
     ;;
@@ -95,8 +99,6 @@
     esac
 done
 
-. ${libdir}/grub/grub-mkconfig_lib
-
 if [ "x$EUID" = "x" ] ; then
   EUID=`id -u`
 fi
@@ -113,33 +115,19 @@
       done ;;
   esac
   if [ $root != t ] ; then
-    echo "$self: You must run this as root" >&2
+    gettext_printf "%s: You must run this as root\n" "$self" >&2
     exit 1
   fi
 fi
 
-set $grub_mkdevicemap dummy
-if test -f "$1"; then
-    :
-else
-    echo "$1: Not found." 1>&2
-    exit 1
-fi
-
 set $grub_probe dummy
 if test -f "$1"; then
     :
 else
-    echo "$1: Not found." 1>&2
+    gettext_print "%s: Not found.\n" "$1" 1>&2
     exit 1
 fi
 
-mkdir -p ${GRUB_PREFIX}
-
-if test -e ${GRUB_PREFIX}/device.map ; then : ; else
-  ${grub_mkdevicemap}
-fi
-
 # Device containing our userland.  Typically used for root= parameter.
 GRUB_DEVICE="`${grub_probe} --target=device /`"
 GRUB_DEVICE_UUID="`${grub_probe} --device ${GRUB_DEVICE} --target=fs_uuid 2> /dev/null`" || true
@@ -169,41 +157,6 @@
 fi
 
 for x in ${GRUB_TERMINAL_OUTPUT}; do
-    if [ "x${x}" = "xgfxterm" ]; then
-    if [ -n "$GRUB_FONT" ] ; then
-        if is_path_readable_by_grub ${GRUB_FONT} > /dev/null ; then
-        GRUB_FONT_PATH=${GRUB_FONT}
-        else
-        echo "No such font or not readable by grub: ${GRUB_FONT}" >&2
-        exit 1
-        fi
-    else
-        for dir in ${pkgdatadir} ${GRUB_PREFIX} /usr/share/grub ; do
-        for basename in unicode unifont ascii; do
-            path="${dir}/${basename}.pf2"
-            if is_path_readable_by_grub ${path} > /dev/null ; then
-            GRUB_FONT_PATH=${path}
-            else
-            continue
-            fi
-            if [ "${basename}" = "ascii" ] ; then
-                    # make sure all our children behave in conformance with ascii..
-            export LANG=C
-            fi
-            break 2
-        done
-        done
-    fi
-    if [ -z "${GRUB_FONT_PATH}" ] ; then
-        if [ "x$termoutdefault" != "x1" ]; then
-        echo "No font for gfxterm found." >&2 ; exit 1
-        fi
-        GRUB_TERMINAL_OUTPUT=
-    fi
-    fi
-done
-
-for x in ${GRUB_TERMINAL_OUTPUT}; do
     case "x${x}" in
     xgfxterm) ;;
     xconsole | xserial | xofconsole)
@@ -213,6 +166,11 @@
     esac
 done
 
+GRUB_ACTUAL_DEFAULT="$GRUB_DEFAULT"
+
+if [ "x${GRUB_ACTUAL_DEFAULT}" = "xsaved" ] ; then GRUB_ACTUAL_DEFAULT="`"${grub_editenv}" - list | sed -n '/^saved_entry=/ s,^saved_entry=,,p'`" ; fi
+
+
 # These are defined in this script, export them here so that user can
 # override them.
 export GRUB_DEVICE \
@@ -220,9 +178,9 @@
   GRUB_DEVICE_BOOT \
   GRUB_DEVICE_BOOT_UUID \
   GRUB_FS \
-  GRUB_FONT_PATH \
+  GRUB_FONT \
   GRUB_PRELOAD_MODULES \
-  GRUB_PREFIX
+  GRUB_ACTUAL_DEFAULT
 
 # These are optional, user-defined variables.
 export GRUB_DEFAULT \
@@ -243,6 +201,7 @@
   GRUB_CMDLINE_LINUX_XEN_REPLACE_DEFAULT \
   GRUB_CMDLINE_NETBSD \
   GRUB_CMDLINE_NETBSD_DEFAULT \
+  GRUB_CMDLINE_GNUMACH \
   GRUB_TERMINAL_INPUT \
   GRUB_TERMINAL_OUTPUT \
   GRUB_SERIAL_COMMAND \
@@ -256,18 +215,17 @@
   GRUB_DISABLE_OS_PROBER \
   GRUB_INIT_TUNE \
   GRUB_SAVEDEFAULT \
+  GRUB_ENABLE_CRYPTODISK \
   GRUB_BADRAM
 
 if test "x${grub_cfg}" != "x"; then
-  rm -f ${grub_cfg}.new
-  exec > ${grub_cfg}.new
-
-  # Allow this to fail, since /boot/grub/ might need to be fatfs to support some
-  # firmware implementations (e.g. OFW or EFI).
-  chmod 400 ${grub_cfg}.new || grub_warn "Could not make ${grub_cfg}.new readable by only root.\
-  This means that if the generated config contains a password it is readable by everyone"
+  rm -f "${grub_cfg}.new"
+  oldumask=$(umask); umask 077
+  exec > "${grub_cfg}.new"
+  umask $oldumask
 fi
-echo "Generating grub.cfg ..." >&2
+gettext "Generating grub.cfg ..." >&2
+echo >&2
 
 cat << EOF
 #
@@ -295,20 +253,18 @@
   esac
 done
 
-if [ "x${grub_cfg}" != "x" ] && ! grep -q "^password " ${grub_cfg}.new ; then
-  chmod 444 ${grub_cfg}.new || true
-fi
-
 if test "x${grub_cfg}" != "x" ; then
   if ! ${grub_script_check} ${grub_cfg}.new; then
-    echo "Syntax errors are detected in generated GRUB config file." >&2
-    echo "Ensure that there are no errors in /etc/default/grub" >&2
-    echo "and /etc/grub.d/* files or please file a bug report with" >&2
-    echo "${grub_cfg}.new file attached." >&2
+    # TRANSLATORS: %s is replaced by filename
+    gettext_printf "Syntax errors are detected in generated GRUB config file.
+Ensure that there are no errors in /etc/default/grub
+and /etc/grub.d/* files or please file a bug report with
+%s file attached." "${grub_cfg}.new" >&2
   else
     # none of the children aborted with error, install the new grub.cfg
     mv -f ${grub_cfg}.new ${grub_cfg}
   fi
 fi
 
-echo "done" >&2
+gettext "done" >&2
+echo >&2
```

---

### Post by GrubThemeArtist on 2012-11-06
Thanks. So what does this mean for people running an older version? Do I have to include two scripts now?

---

### Post by towheedm on 2012-11-06
No you don't.  The new script will work for 1.98, 1.99 and 2.00.

---

### Post by GrubThemeArtist on 2012-11-06
> **towheedm said:**
> No you don't.  The new script will work for 1.98, 1.99 and 2.00.

Okay cool, now I just need to update all 20 of my themes.

That sounds fun.

---

### Post by dniMretsaM on 2012-11-08
I'm currently working on a theme that I hope to get into the final release of 13.04. There is a thread about it [here](http://ubuntuforums.org/showthread.php?t=2081013). I'm always looking for suggestions on how to improve the theme.

---

### Post by GrubThemeArtist on 2012-11-09
> **dniMretsaM said:**
> I'm currently working on a theme that I hope to get into the final release of 13.04. There is a thread about it [here](http://ubuntuforums.org/showthread.php?t=2081013). I'm always looking for suggestions on how to improve the theme.

Make a new set of icons, and make it consistent. Get creative!

And that's another thing I want to bring up, using the pieces of Ubuntu's GUI isn't very creative. Sure it'll fit right in, but it doesn't add a lot of pizzazz. Don't think about trying to get the theme into Ubuntu 13.04 (not to be mean, but it's not going to happen, Canonical is probably just going to have one of their employees make it if they decide to make their own Grub theme), just go nuts with trying to come up with a cool or beautiful design.

Grub theming has a lot of little paper cut issues, learn what they are and learn your way around them (e.g. Grub has a 2 pixel error when stretching the selection image across the menu).

---

### Post by GrubThemeArtist on 2012-11-29
I wanted to redo my Autumn theme using Elementary OS Luna's autumn wallpaper.

I have everything set up right I'm sure of it, but no matter what I do GRUB gives me an "invalid argument" error. I'm trying to figure it out. Here's a mockup at least (I think it's time to make new icons though).

I'll be figuring out later though.

---

### Post by GrubThemeArtist on 2012-11-29
Turns out the wallpaper was giving me issues. Just need to tweak some settings. :)

---

### Post by GrubThemeArtist on 2012-12-02
I bring you my newest creation, Solstice!

Download link:
[http://db.tt/MUquJDFz](http://db.tt/MUquJDFz)

Enjoy :)

---

### Post by cecilpierce on 2012-12-03
> **GrubThemeArtist said:**
> I bring you my newest creation, Solstice!

Download link:
[http://db.tt/MUquJDFz](http://db.tt/MUquJDFz)

Enjoy :)

Nice!

---

### Post by mtguy on 2012-12-11
Hi all,

Many thanks for the excellent themes in this thread.  I've downloaded and installed several, altering some with different bg's and such, but I seem to have run into a problem...even with unmodified themes.  I have 3 entries in my grub menu...ubuntu 12.04, ubuntu recovery, windows 7.  

When I choose one, the grub menu is immediately replaced by a large black box.  This happens regardless of the theme I use (modified or not).  Is there some way to get rid of this large black box?  It's only a couple of seconds, but it's still annoying.  Ideally, I'd like for the grub menu to disappear and just leave my bg pic for those couple of seconds, but I'd rather have the grub menu for those seconds than a big ugly black box.  Any help would be appreciated.

---

### Post by towheedm on 2012-12-11
Yeah, unfortunately you cannot get rid if it, but you can theme it just as with the other elements of the GRUB menu.

That black box is called the terminal window and the fact that it appears black may indicate that the theme does not set the slices or background for the terminal.

For more on this and on GRUB theming you can check out my guide, the link is in the my sigs and post any support questions in this thread: [http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

---

### Post by GrubThemeArtist on 2012-12-11
I've been tossing in the same terminal box for several of my themes. If you've changed your terminal colors (which oddly enough is in a plymouth configuration file) you can change the terminal color. However, as Towheedm has said, we can't have it where that box doesn't appear. I think Towheedm has even asked the Grub devs to change this, but I don't think they want to.

Oh yeah Towheed, there was a recent patch to Grub upstream that lets you design unselected menu items. That opens up some new possibilities. :)

---

### Post by towheedm on 2012-12-12
Yeah but my tutorials cannot be based on commits to the trunk branch, simply because 99.99% of users will not be using GRUB from the trunk branch.

The tutorial must be based on at least what the distros will be packaging, which is from the packaged release from the devs.

And yeah, the devs do not (for some reason) consider my recommendations.  I remember asking why we don't just place themes in /usr/share/themes and got a whole technical explanation about where and when /usr is mounted.  If you have installed GRUB 2.00, you'll notice that the default theme is in fact placed in /usr/share/grub/themes/starfield, with a copy in /boot/grub to overcome the /usr where and when mount issue.

It's a good workaround, but now my install script must take this into consideration when working with 2.00.  I'm also working on a grub-set-theme script that will be included in the next edition.  I'll also ask the devs to include it in upstream.

---

### Post by GrubThemeArtist on 2013-03-09
Whoa, this place got updated. Anyways, here's my newest creation Raindrops

Download link:
[http://dl.dropbox.com/u/40152532/GrubThemes/Raindrops.tar.gz](http://dl.dropbox.com/u/40152532/GrubThemes/Raindrops.tar.gz)

---

### Post by JFDsouza on 2013-04-02
should I install mono-runtime or what?

---

### Post by carla2013 on 2013-04-02
I think Raindrops is awesome! Great job, [**[COLOR=#000000]GrubThemeArtist[/COLOR]**]("http://ubuntuforums.org/member.php?u=1641597")!

---

### Post by cecilpierce on 2013-09-03
What happen to everybody into the themes, anything cooking ???)   :P

---

### Post by woohoomoo2u on 2013-11-15
Kinda new here, I'm trying to get something like [HTML]http://f.cl.ly/items/3s3C1T213D0M1D0d040P/MainSS%20Preview.png[/HTML] going but with a ubuntu icon like [ATTACH=CONFIG]247858[/ATTACH] and replacing the apple with a logo of the pc's manufacture (hp for me). I am still having trouble lining them up horizotinal, everything else is looks nice.

---

### Post by cecilpierce on 2014-01-20
Will the new grub have any new themes with it ?

---

### Post by JFDsouza on 2014-03-27
Will this script work on fedora too or is this only for ubuntu?

---

### Post by cecilpierce on 2014-04-11
> **JFDsouza said:**
> Will this script work on fedora too or is this only for ubuntu?

Themes work with grub and fedora uses grub.

Should work ok.

---

### Post by john.hupp on 2014-05-23
I attach the latest shots of a work-in-progress that I'm aiming to use for Lubuntu dual-booting with Windows.

From this point in development, I tried to tame the terminal box using Towheed's Guide information (Workarounds for Known Bugs - Applying a background image to the terminal window), but that information seems no longer to be current for the beta version of Grub2 installed by Lubuntu (and probably Ubuntu also).  For instance, the term box is supposed to be centered and cover 70% of the screen.  So with the boot menu top = 20%, I would have expected the top of the menu to be covered (with 5% to spare), but the first menu item was still visible.  And since my boot menu and progress bar both have left = 14% and width = 72%, I would have expected the term box NOT to cover the sides of those, but it did.  The scaling and cropping information likewise seems not to apply to the installed grub2 beta.  For instance, even after explicitly setting grub_gfxmode='1024x768', the resulting terminal box is not 70% of that size (e.g. 717x538), but something much less.

So for the time being, I have switched to a plain-color desktop-image and GRUB_BACKGROUND (a single 1-px file serving for both).  With this I can set it up so that the term box and its decorations cleanly paint the entire screen (at least up to a resolution of around 2560x1600).  See my second-to-next post below.

---

### Post by john.hupp on 2014-05-26
I've been trying to make the theme in the post above completely resolution-independent.

Grub responded well to % values for the numeric values in the progress  bar and labels.  Also OK with %'s for boot_menu properties top, left,  height, width.

But I'm getting bad behavior with item_height and the other properties.   For a 1024x768 grub display and an original setting of item_height =  26, I can't get equivalent output unless I set item_height = 27%

So item_height seems to be referencing a parent with a height of about 96, rather than 768.

This is in a VMWare Player environment running Lubuntu 14.04.

Is this a known problem, or is there an explanation/workaround?

(I also realized as I got into this that I will run into a problem with  different aspect ratios, so other than creating at least two themes for  the commonest aspect ratios, I'd be interested in a tip there as well if  there is a solution.)

---

### Post by john.hupp on 2014-05-29
In accord with post second-above, this theme uses a plain-color desktop-image and GRUB_BACKGROUND for the sake of being able to arrange for a whole-screen splash by the terminal box and its decorations.

I include in the archive Towheed's install.sh script, edited per the Guide instructions, but I did not test it. If you don't see the menu at all, edit /etc/default/grub and comment out the GRUB_HIDDEN_TIMEOUT line before running sudo update-grub.  (In a dual-boot setup the *buntu installer has probably already done this.)

**Refinements**: My own results, as seen in the screenshots, also include mods to the scripts in the /etc/grub.d directory.  1) If you want the memtest menu items to display icons and also not appear until after Windows and other distros, then as root delete /etc/grub.d/20_memtest86+ and copy in my 50_memtest86+ from the archive.  2) If you have Lubuntu installed and would like the menu to refer to that as Lubuntu and use a Lubuntu icon (instead of using the Ubuntu name and icon), then as root overwrite /etc/grub.d/10_linux with my version from the archive.  Then run sudo update-grub.

I wish I were savvy enough to edit install.sh instead of just giving the above manual instructions for further changes, but that would currently be a long and painful exercise.  I would welcome another hand at that job.  It would be a trivial job for many people.

Note that you will not see the scrollbar unless the number of menu items requires it.  If you don't see the scrollbar and want to, you can add some dummy entries to /etc/grub.d/40_custom per the instructions in Towheed's Guide.  Then run sudo update-grub.

I expect the theme to be *rather* independent of resolution and aspect ratio, but as I note in post #139, the item-related boot_menu properties do not currently support relative numeric values (and for numeric values in general, absolute or relative, only integers are supported).  I also realized that it would introduce certain problems if it were otherwise.  Most notably, it would be difficult to achieve square-dimensioned icons under all resolutions and aspect ratios.  But as it stands, the boot menu size and location will scale, but the item-related dimensions and the scrollbar width will not.  I would be interested in hearing/see how this looks on a high-res widescreen monitor.  (I've been working on this with the older hardware I use with Lubuntu, and additionally, in a VMWare Player playground under Windows I couldn't see a way to set up a widescreen environment.)

---

### Post by vuester on 2014-09-01
> **GrubThemeArtist said:**
> I just finished another one (I made a Gnome Shell GRUB theme a while ago, I guess I forgot to post it here).

I call it simpleBlue :D

[IMG]http://i.imgur.com/Pm4R4.png[/IMG]

_Download link:_
[http://db.tt/s5FjyOcq](http://db.tt/s5FjyOcq)

_XCF Files:_
[http://db.tt/01smR6et](http://db.tt/01smR6et)


hello,
this splash screen include icon for Linux Mint also? 
Thank you

---

### Post by cecilpierce on 2015-05-07
Just thought I'd ask , anyone making themes lately ?

---

### Post by john.hupp on 2015-05-07
> **cecilpierce said:**
> Just thought I'd ask , anyone making themes lately ?

I haven't made anything new, but the one I was posting about in #140 is my go-to if I'm building a dual-boot machine.  Though I'm pretty happy with it (it's 100% better than default behavior), I wish grub2 supported automatic scaling.  The theme has to be manually retooled a bit for different screen sizes.

---

### Post by cecilpierce on 2015-05-07
Thanks, that looks nice and clean. I have been using burg on one drive and grub on the second drive.

I was trying to get a circle progress timer to work with some of the old themes but no luck so I went to Autumn for now.

Grub is a pain in the neck for me !

---

### Post by cecilpierce on 2015-05-11
I guess no ones interested in themes any more, strange !

---

### Post by primitive1 on 2015-10-08
I am interested in theming grub.  May i get someone to send me links or the manual itself for grub and if there are any pointers for solid newbie users to adjust the theming.

I get tired of the boring monotone screen and would like to spice up the grub please.  Thank you!

---

### Post by towheedm on 2015-10-08
Here's a link on Google Drive.  Again, the guide is no longer maintained.  Hopefully it works well with the latest version of GRUB.

I've updated my sig to reflect the new link.

[https://drive.google.com/file/d/0B4ryPDYMqL_MNDgzNjYzMWEtMTIxZC00MzRkLTg1NWUtMmQzNTE0NTBjNDQ5/view?usp=sharing](https://drive.google.com/file/d/0B4ryPDYMqL_MNDgzNjYzMWEtMTIxZC00MzRkLTg1NWUtMmQzNTE0NTBjNDQ5/view?usp=sharing)

Towheed Mohammed

---

### Post by cecilpierce on 2015-10-09
> **primitive1 said:**
> I am interested in theming grub.  May i get someone to send me links or the manual itself for grub and if there are any pointers for solid newbie users to adjust the theming.

I get tired of the boring monotone screen and would like to spice up the grub please.  Thank you!

Here is a link to install burg boot loader:
[http://www.unixmen.com/how-to-install-burg-boot-loader-in-ubuntu-1304-and-linuxmint/](http://www.unixmen.com/how-to-install-burg-boot-loader-in-ubuntu-1304-and-linuxmint/)

Antergos OS has a nice grub theme is you want to install it, looks like burg.

p.s. you can click on the paper clip on the Cafe menu and see pics.

---

### Post by Kpenguin on 2015-10-11
> **towheedm said:**
> I'd have expected at least a few GRUB themes posted by now.  Oh well ...

Here's a theme I created from the metacity/gtk+-2.0 theme 'Azenis' which can be found [here]("http://gnome-look.org/content/show.php/Azenis?content=106608").

The GRUB theme shows best at 1024x768.

To install the theme, first extract the archive, cd to the directory where the archive was extracted to and run the 'install.sh' script.

I forgot to include the Fixed Regular 13 font in the archive.  It is now included nd the archive updated.  Sorry for that.

Hey, tried your theme! Looks great except for the fact that the aspect ratio is way off and the whole thing's skewed up. How do I fix this? I have a 1366x768 display (16/9 ratio)
Thanks!

Kpenguin

---

