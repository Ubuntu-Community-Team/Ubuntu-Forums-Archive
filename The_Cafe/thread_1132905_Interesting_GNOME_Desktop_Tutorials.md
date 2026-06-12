---
title: "Interesting GNOME Desktop Tutorials"
date: 2009-04-22
forum: The Cafe
---

### Post by NightwishFan on 2009-04-22
This is some basic stuff that may interest someone.

Cool GNOME Desktop Tips



Customize the Terminal:

[LIST=1]
[*]Open up GNOME-Terminal
[*]Go to Edit - Profiles, and create a new profile, based on default. Call it what you will. Set that profile to be the default, and then restart GNOME-Terminal.
[*]Open up an image you like in GIMP. For best results it should be something fairly abstract, but any image will do. Small sized images work fairly well, such as 640x480 (or a widescreen like 800x500).
[*]In GIMP, go to Filters - Map - Make Seamless. This should make the image tile correctly.
[*]Save the image (I recommend PNG).
[*]Back in GNOME-Terminal, go to the Background tab under Profile Preferences. Set the background image to the one you saved. Check the box that says "Background Image Scrolls".
[*]In the colors tab, set a color scheme that works with your background. If necessary set the palette as well. (I use "rxvt").
[*]Enjoy! The image will set behind your terminal, and will not have any sharp edges that stick out and make it seem non-continuous. Sometimes the image can look redundant though, it is up to your tastes.
[/LIST]

Save bandwidth when posting images to Ubuntu Forums/Etc:

This will work well with screen shots and the like, which are to be viewed, not downloaded.
[LIST=1]
[*]Take a screen shot using GIMP, under File - Create - Screenshot.
[*]Scale the image to at least 1024x768 (Standard) or 1280x800 (Wide)
[*]Go to: Image - Mode - Indexed. Select "Generate Optimum Palette". If you notice blurring with gradients: At the bottom, under dithering, choose "Floyd-Steinberg (Normal)".
[*]Save the image as PNG.
[*]This will retain most quality of the image, but reduce filesize. Results will vary, for me it is around 40-50% smaller, but is not technically lossless. Generally JPEG will compress better, but this is for those of us who do not like JPEG.
[/LIST] 


Cool Panel:

Did you know that any compatible image can be made the background to the panel with a simple drag and drop?
[LIST=1]
[*]Edit a cool abstract image, and add 75% transparency in GIMP, and then make it the background to your panel.
[*]The only issue is the text color of the panel, which sometimes can be hard to read if you use a black panel color.  It should be able to be customized separate from the other applications font, optionally. (Override option in panel preferences?)
[/LIST]


Use an SVG Wallpaper:

SVG is supported as a GNOME background, but it merely renders it as-is. (No scaling). Not to fear, with GIMP (you can tell I love GIMP), you can easily scale the SVG image to any size, and save as a high quality PNG file!

[LIST=1]
[*]Open a .svg file in GIMP. You will get a dialogue that allows you to choose the size of the image. Pick your screen specifications (1440x900?), and hit ok.
[*]Save the image as is, or edit as you like.
[*]Use the full scale SVG rendered as a PNG image as your wallpaper!
[/LIST]

Under The Sea (which I think is on GNOME-LOOK) is great, I use it as my terminal background though.


Metacity Compositing:

Some of you many not know that metacity can be a compositor. I believe it is still a work in progress though. Be careful what you change in GCONF, as you might alter a feature you like, and not remember how you did it. A graphical way to access is:

[LIST=1]
[*]Press Alt+F2
[*]Type: "gconf-editor" (no quotes) and push enter.
[*]Navigate to: apps - metacity - general
[*]Check the box called: compositing_manager
[*]To reset, either uncheck, or right click and select "Unset Key"
[/LIST]


GNOME Splash Screen:

Ubuntu has the GNOME splash screen disabled by default. To enable, you need to activate it using gconf-editor.

[LIST=1]
[*]Press Alt+F2
[*]Type: "gconf-editor" (no quotes) and push enter.
[*]Navigate to: apps - gnome-session - options
[*]Check the box called: show_splash_screen
[/LIST]


Pulseaudio High Priority:

By default, pulseaudio does not run with an elevated priority. If you so desire, or tend to have jumpy audio, you can enable this in a few easy steps. Note: Using pulseaudio with elevated priority can cause other applications to fall behind it. This is mainly an issue only if pulseaudio causes unwanted behavior. Otherwise, I see no harm.

NOTE: This requires administrative access!

[LIST=1]
[*]Go to: System - Administration - Users And Groups
[*]Click the "Unlock" button and type your password.
[*]Go to "Manage Groups"
[*]Find the group "pulse-rt" and click the "Properties" button.
[*]Check the users in which you want pulseaudio to run with elevated priority
[*]Log out, and then back in
[/LIST]

Pulseaudio should now run with a priority of -11. Perhaps this fixes your problem or adds some performance.


Ripping a DVD using Thoggen:

Do you back up your DVD collection to view? Many people use formats such as DivX or MPEG, however, I prefer to stay within the realm of free software if possible. Those of you that feel the same way will enjoy this application. Thoggen is a DVD ripper that rips to Theora/Vorbis. Theora is perhaps a little iffy for video quality, but not poor. Vorbis sounds excellent, and very high def, yet is small in filesize. Thoggen is also very simple, you simply choose which parts of the DVD to rip, and which language, and then choose the quality or desired size output.

[LIST=1]
[*]Install thoggen using apt or synaptic.
[*]Run it under Applications - Sound And Video - Thoggen
[*]Follow the simple on screen instructions. I usually use a quality of 40, and the full dimensions of the dvd video (by default it is smaller than normal, which I suppose is smaller filesize, but I have space to spare).
[*]Depending on the size of the DVD, it may take quite a while. (3-5 hours is normal).
[*]The result should be to your satisfaction, unless you require subtitles, which I think will be supported soon. There also seems to be an issue with alternate angles.
[/LIST]

Evolution Calendar:

Some people do not use Evolution since they check their email via Firefox. Give Evolution a second chance, as it has some very good organization and reminder features. Simply set an appointment, and it will appear in your GNOME Clock applet, and when the time comes, you can have evolution remind you. I find it useful to remember appointments that are not due for a while, and to remember when to watch TV programs.

---

### Post by suitedaces on 2009-04-22
Thanks, and I've just noticed you, so kudos on the name!

---

### Post by NightwishFan on 2009-04-23
Indeed. Great to see another fan out there.

---

