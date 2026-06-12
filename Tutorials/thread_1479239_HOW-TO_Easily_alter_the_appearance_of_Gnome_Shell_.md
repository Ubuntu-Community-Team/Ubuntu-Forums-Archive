---
title: "HOW-TO: Easily alter the appearance of Gnome Shell (Beginners)"
date: 2010-05-10
forum: Tutorials
---

### Post by JustinBenner on 2010-05-10
I spent a few hours figuring out what to edit last night, and I thought  I'd post what I learned for the other noobs like me, that way they can  customize it easily and in less time.

**1. Open gnome-shell.css with gedit**

Open a terminal and type: sudo gedit  /usr/share/gnome-shell/theme/gnome-shell.css

**2. Get comfortable reloading GNOME Shell to test your work.**

To do this, just type this in terminal: gnome-shell --replace

You will need to do this before you can see any of the changes you've  made to the Shell.

Another way of doing this, as mentioned by jjcv, is to press ALT + F2, and enter "restart" into the popup.

A third way of doing this, and probably the most efficient way, was suggested by Ferreter007. Press ALT+F2, then type "rt" to restart your theme, not the entire gnome-shell.

**3. Edit the top panel.**

The top panel can be edited to look however you want. You can use a  gradient or a background image, although the background image has to be  scaled to the appropriate size or it won't display properly. You can also make it variably transparent.

Simply look for panel { in gnome-shell.css, and underneath it, there are  a number of options. The first is the direction of the gradient, if  any. Default is vertical, but it can be done horizontally as well. The  other options are background-gradient-start and background-gradient-end.  Simply alter these colors to reflect how you want the gradient to look.  Go [here]("http://www.computerhope.com/htmcolor.htm")  for some basic HTML color codes.

The other option, as mentioned, is a background image. To set this up,  erase all the code dealing with the gradient, and call a  background-image up. It should now look like this:

#panel {
    color: #ffffff;
    font-size: 12px;
    background-image: url("topbackground.xpm");
}

You can make the top panel transparent by making your panel { look like this:

#panel { 
color: #ffffff; 
font-size: 12px; 
background-color: rgba(0,0,0,0.20); 
} 

"0.20" can be adjusted to increase or decrease transparency. *Thank you to sawrub for pointing that out.*

**4. Change the font used on the panel**

To change the font used on the panel, look for .panel-button {

Underneath it is your options. I left the padding and border-radius  alone, but I did change the font. Now the function looks like this:

.panel-button {
    padding: 4px 12px 3px;
    border-radius: 5px;
    font: 12px trebuchet ms;
}

Since I found the font on the default theme to be a little too large in  general, I took a look through the rest of the panel functions, and  changed text sizes down to 12 or 10 px, when they were 14 or 16 px  before.

**5. Edit the appearance of the Application, Recent Document and Places  buttons in Overview**

To edit the appearance of these buttons, look for: .section-header {

You can set the gradient that appears on the buttons in this function.  Mine looks like this:

.section-header {
    border: 1px solid #AAABBA;
    background-gradient-direction: vertical;
    background-gradient-start: rgba(29,40,59,0.9:cool:;
    background-gradient-end: #000000;
    font-weight: bold;
    font-size: 12px;
}

**6. Change the background of the menu area (behind Places, Recent  Documents, etc.)**

Find #dash {

You can either change the gradient around, or make your own custom image  (just like you did for the top panel). Mine looks like this:

#dash {
    color: #FFFFFF;
    background-image: url("background.jpg");
    padding: 0px 14px;
}

**7. Change the appearance of the Applications and Recent Documents  menu...**

Find .dash-pane {

Alter the background-color, or put in your own image. I personally use a  nice dark color, then give it transparency for that sexy look. Here is  what mine looks like:

.dash-pane {
    background-color: rgba(52,56,106,0.45);
    border: 1px solid #FFFFFF;
    padding: 4px;
    spacing: 4px;
}

**8. Alter the size of the icons...**

You can change the size of the icons by altering the following:

.app-menu-icon {
    width: 24px;
    height: 24px;
}

[B]9. Comments/Suggestions

[/B] I realize this is a very basic guide, so feel free to correct me if  I'm wrong or throw out any suggestions. Just thought this would make it  a bit easier.

**10. Updates**

1. Updated info about restarting Gnome Shell.

2. Added method to make top panel transparent, given by sawrub.

---

### Post by bapoumba on 2010-05-11
Approved to T&T.

---

### Post by JustinBenner on 2010-05-14
Has anyone found to make the panel and dash totally transparent, even when you are in Activities mode?

---

### Post by plun on 2010-05-16
Thanks for the howto, very helpful !

How do I change icon sizes  ??

---

### Post by jjcv on 2010-05-16
When in gnome-shell you can type:

Alt-F2 and enter restart

which will restart your shell (re-reading your gnome-shell.css)

---

### Post by JustinBenner on 2010-05-17
> **plun said:**
> Thanks for the howto, very helpful !

How do I change icon sizes  ??

No problem, I am excited to get back into the Linux community a bit more, help out on what I can.

You can change the icon sizes by altering the following:

.app-menu-icon {
    width: 24px;
    height: 24px;
}

---

### Post by JustinBenner on 2010-05-17
> **jjcv said:**
> When in gnome-shell you can type:

Alt-F2 and enter restart

which will restart your shell (re-reading your gnome-shell.css)

Thanks, I've added this to the Tutorial :KS

---

### Post by labinnsw on 2010-09-26
This is good. I was about to do something like this but not as complete. This still leaves a black background in the desktop selection view. I was trying to find out how to change that when I came across this.

I have viewed some other solutions, [(see link in my signature)]("http://ubuntuforums.org/group.php?do=discuss&group=&discussionid=1063") but they don't work for me. When I follow those instructions, gnome-shell won't start.

I am on a 64bit Lucid. I uninstalled xulrunner and installed older .debs of xulrunner and libgjs0.

---

### Post by herbie643 on 2011-01-24
Well I have changed a theme, Ambiance GNOME Shell Theme, I believe from half-left, and the only thing left is, How do you change the text color of APPLICATIONS, PLACES & DEVICES and RECENT ITEMS.  Now by that I mean, the actual text, not the buttons.
I have looked high and low in the gnome-shell.css and was unable to make that change.
Any ideas?

---

### Post by JustinBenner on 2011-03-31
> **labinnsw said:**
> This is good. I was about to do something like this but not as complete. This still leaves a black background in the desktop selection view. I was trying to find out how to change that when I came across this.

I have viewed some other solutions, [(see link in my signature)]("http://ubuntuforums.org/group.php?do=discuss&group=&discussionid=1063") but they don't work for me. When I follow those instructions, gnome-shell won't start.

I am on a 64bit Lucid. I uninstalled xulrunner and installed older .debs of xulrunner and libgjs0.

Are you running the latest gnome-shell, or the one from the official Ubuntu repository? If you are running the latest one, I changed the color of that area by altering .overview { in gnome-shell.css. Mine is now transparent, and it looks like this:

.overview {
    background-color: rgba(0,0,0,0.20);
}

Let me know if this solves your problem, and if so, I'll add it to the tutorial.

---

### Post by JustinBenner on 2011-03-31
> **herbie643 said:**
> Well I have changed a theme, Ambiance GNOME Shell Theme, I believe from half-left, and the only thing left is, How do you change the text color of APPLICATIONS, PLACES & DEVICES and RECENT ITEMS.  Now by that I mean, the actual text, not the buttons.
I have looked high and low in the gnome-shell.css and was unable to make that change.
Any ideas?

Looking at this briefly, I couldn't see an easy fix. I'll get back to you on this... It may be as simple as defining the font in whatever section is applicable, I'll play around and see.

---

### Post by labinnsw on 2011-03-31
> **JustinBenner said:**
> Are you running the latest gnome-shell, or the one from the official Ubuntu repository? If you are running the latest one, I changed the color of that area by altering .overview { in gnome-shell.css. Mine is now transparent, and it looks like this:

.overview {
    background-color: rgba(0,0,0,0.20);
}

Let me know if this solves your problem, and if so, I'll add it to the tutorial.

Although I still love Gnome, I decided to switch. My desktop needs to run conky. I did get it to work though, on a later version.

---

### Post by sirius329 on 2011-04-14
hi,I've modified the gnome-shell.css and restart the gnome-shell,but it dosn't work,I just want a smaller icon....my path is /home/username/gnome-shell/source/gnome-shell/data/theme/gnome-shell.css  is that ok?

---

### Post by ferreter007 on 2011-05-01
Hey everybody.

I'm a big ubuntu fan and been using it for years but haven't given nearly as much back as I want to have helped so hopefully this tip may save some of you designers a little time. 

I've been redesigning templates for gnomeshell and rather than totally restart your full shell try this;

Press Alt+F2 and type 'rt' as this reloads only the Gnome Shell *Theme*. Not the full gnome-shell.

Hope this helps in the productivity.

---

### Post by JustinBenner on 2011-05-07
> **ferreter007 said:**
> Hey everybody.

I'm a big ubuntu fan and been using it for years but haven't given nearly as much back as I want to have helped so hopefully this tip may save some of you designers a little time. 

I've been redesigning templates for gnomeshell and rather than totally restart your full shell try this;

Press Alt+F2 and type 'rt' as this reloads only the Gnome Shell *Theme*. Not the full gnome-shell.

Hope this helps in the productivity.

Thanks ferreter, I've added this to the first post...

---

### Post by sawrub on 2011-05-19
Here are 2 changes done from my side.

1. Changed the top panel color to transparent

#panel { 
    color: #ffffff; 
    font-size: 12px; 
    background-color: black; 
} 

to 

#panel { 
    color: #ffffff; 
    font-size: 12px; 
    background-color: rgba(0,0,0,0.20); 
} 


2. Made the days of other months appear distinctively.

.calendar-other-month-day { 
    color: #cccccc; 
} 

to 

.calendar-other-month-day { 
    color: #ffff00; 
}

---

### Post by geazzy on 2011-05-19
nice tutorials :)

---

### Post by airtonix on 2011-10-13
I'm looking for the css selector path that lets me style the hyperlinks in the chat message popup.

If you're not sure what I'm referring to then have a look at this image that I found on the gnome website.

[IMG]http://blogs.gnome.org/marina/files/2011/01/notification-chat-clipped2.png[/IMG]

I didn't want to upload a screenshot of my own chat sessions for privacy reasons.

I'm currently using the [Nord]("http://0rax0.deviantart.com/art/GNOME-Shell-Nord-214295138") theme from deviant art and the hyperlinks are white text on a white background... so fairly difficult to read before clicking.

---

### Post by kedmond on 2011-11-11
Hey guys, thanks for all of the useful tips.  I was wondering if anyone knew how to change the color of the text in the shell's calendar so that each event matches the color of their respective calendar.  Thanks!

---

### Post by apostl3pol on 2013-02-10
One extra tip to add to this thread: you can use LookingGlass to get some "inspect element" functionality like that found in Firebug.

[https://live.gnome.org/GnomeShell/LookingGlass]("https://live.gnome.org/GnomeShell/LookingGlass")

---

