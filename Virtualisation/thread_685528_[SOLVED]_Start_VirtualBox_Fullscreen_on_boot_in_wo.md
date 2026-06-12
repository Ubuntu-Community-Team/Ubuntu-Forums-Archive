---
title: "[SOLVED] Start VirtualBox Fullscreen on boot in workspace 2"
date: 2008-02-02
forum: Virtualisation
---

### Post by Twizzle on 2008-02-02
I want to be able to start VirtualBox in full screen mode from Boot but on a second Workspace if possible.

I think I can use:

```
VBoxSDL -vm "Windows XP" -fullscreen 
```

to get it going and I can put this into:

```
System>Sessions>Start Up Programs
```

to get it to start on Boot, but how can I tell it which Workspace to start on.

I would like, in the end, to have the computer Boot and be able to access my programs on XP or Ubuntu just by rotating my Compiz Screen :)

I have tried the Seamless option but do not really like it and am happy to keep the two systems seperate (won't confuse my wife as much either!)

---

### Post by cherva on 2008-02-02
Look at this program [http://live.gnome.org/DevilsPie]("http://live.gnome.org/DevilsPie")
Introduction: A totally crack-ridden program for freaks and weirdos who want precise control over what windows do when they appear. If you want all XChat windows to be on desktop 3, in the lower-left, at 40% transparency, you can do it.

---

### Post by Twizzle on 2008-02-02
That looks perfect!

Thanks :)

---

### Post by Twizzle on 2008-02-03
That works great - The only thing I want to be able to do now is allow Compiz to have control over Virtualbox.

That is I want to have Virtualbox running fullscreen but when I press Ctrl Alt Left or Mouse 1, I want the cube to appear and allow me to switch workspace.

Unfortunately can't find a setting that allows it....

---

### Post by cherva on 2008-02-03
Well thats because virtual box takes these shortcuts to the windows. Can you move the mouse somewhere that it outside of windows. I personally use vmware and for "Ctrl + Alt + Left arrow" I use the space shown on the picture...
In other words move your mouse over linux ground so the shortcuts are send to linux

---

### Post by Twizzle on 2008-02-03
I was hoping to find a way to stop VirtualBox taking the shortcuts as I run it in Fullscreen mode so there is no Linux Space.

I did find a bit of a workaround - either to allow the mouse to flip the screen (but I don't like this much). Or press Right Ctrl then Ctrl Alt and left or right so as to put the focus back to Ubuntu and then rotate the box. :)

---

### Post by cherva on 2008-02-03
I'm not shure about virtualbox but when you  move the mouse of the right part of the screen aren't you over "linux ground" ? Why don't you try it: move the mouse to the right part of your screen so you can't see it and then Ctrl+Alt+left arrow.

---

### Post by rpainter on 2008-02-20
Can you tell me how you got Devils Pie to work with VirtualBox? I tried several different .ds files, and couldn't get the window to move to a new workspace.

---

### Post by Twizzle on 2008-02-20
I did not use Devils Pie in the end. I used a setting in Compiz that sends the program to a specific screen. Unfortunatly I am at work now and can't remember what setting it was! I will check when I get home.

Just remembered - it was the Place Windows plugin. I set VirtualBox to run at startup and for it to open on desktop 3 of my cube.

---

### Post by rpainter on 2008-02-21
Cool. When you get a chance, I would really love to know what setting was used. Thanks.

---

### Post by Twizzle on 2008-02-21
OK it was:

System > Preferences > Advanced Desktop Settings

Tick the 'Place Window' module then go to its 'Fixed Window Placement' tab, and in the second box (Windows with fixed viewpoint) I put:

```
class=Virtualbox
```

And chose an X position of 2 and Y of 0. This meant that it went straight to desktop 2 of my cube.

I then went to System > Preferences > Sessions

and added a new startup program of:

```
VBoxManage startvm "Windows XP"
```

So now when I boot, XP loads in a virtual box on face 2 of the cube. If I want XP, I spin the cube :)

I have a Core 2 Duo 6600, with 2 GB ram and an Nvidia 8600 and am yet to notice any impact on my system in day to day running with the above.

---

### Post by rpainter on 2008-02-21
OK...I tried that, and it does not work for me. It does automatically start, but it does not move to workspace 2. Attached is my configuration. Does it look right?

---

### Post by Twizzle on 2008-02-21
Yep, that looks ok to me.

What are your settings under the general tab?

Have you tried different X and Y settings?

[Here]("http://wiki.compiz-fusion.org/Plugins/Place?highlight=%28place%29") is the WIki page for compiz-fusions place windows module - there may be something there that can help?

---

### Post by dark_phantom on 2008-02-21
I'm going to give it a try. :)

---

### Post by gohanssjn on 2008-02-24
I cannot seem to get this to work, and it's driving my nuts.  I use a differetnt start command for VirtualBox though, seeing st tha one here did not work for me.

I use "VirtualBox startvm "Windows XP"

Do I need to use a different class setting in thatn Virtual Box?

---

### Post by machoo02 on 2008-03-01
Be sure to use the actual name that you gave to your VM in quotes.  For example, my VM is names WindowsXP, so my startup command is ```
VBoxManage startvm "WindowsXP"
```
Note that you can't use "VirtualBox" to start up a VM from the command line...it needs to be VBoxManage, which is one of the command line tools that can manage/control your VM's.

Twizzle:  Thanks for the *awesome* tip!

---

### Post by Jose Catre-Vandis on 2008-03-01
If you are not running compiz and want to do much the same you can use wmctrl. (install with apt)

You will need to identify the name of the Vbox window, this is easy, just start up your vm and note down what it says in the title bar. Then copy this script to a text file, make it executable, and create a launcher. You will get a window for about 10 seconds before it heads off to workspace right. Replace "vmname" with the name of your vm in the script.

```
#! /bin/bash
#open vm in second workspace then switch back to first

VBoxManage startvm vmname
sleep 10 && wmctrl -r "vmname [Running] - innotek VirtualBox" -t1
exit
```

---

### Post by Pence on 2008-11-05
This is exactly what I'm trying to do, but I've hit some problems. I've tried place windows and devil's pie, but I can't get it to open on the second workspcace. also, when it comes up fullscreen (on workspace 1), it's only 1280x960, not 1680x1050. pretty much the only thing I could get to work is assigning rotate cube right to the scroll lock key, which virtualbox doesn't seem to use, so I don't have to press the host key.

my place windows settings are 
class=Virtualbox
X Viewport Positions 2
Y Viewport Positions 0

and my virtualbox.ds file is:

```

; generated_rule Virtualbox
( if 
( and 
( is ( window_name ) "Windows XP [Running] - Sun xVM VirtualBox" )
) 
( begin 
( set_viewport 2 )
( println "match" )
)
)

```

Also, is there a way to execute a script on shutdown? I'd like virtualbox to shut down automatically when I turn off my computer.

Edit:

it seems that there is only one workspace when compiz is installed, which has a greater x and or y dimention, and that you are only looking at part of it at one time.

No Visual Effects:
```

user@user-desktop:~$ wmctrl -d
0  * DG: 1680x1050  VP: 0,0  WA: 0,25 1680x1000  Desk 1
1  - DG: 1680x1050  VP: N/A  WA: 0,25 1680x1000  Desk 2

```

Extra Visual Effects:
```

user@user-desktop:~$ wmctrl -d
0  * DG: 3360x1050  VP: 0,0  WA: 0,25 1680x1000  Desk 1

```

That's why I can't get it to move to the second workspace, there is no second workspace.

---

### Post by kurty_77 on 2009-03-22
can you elaborate on how you used the fixed window placement option?
never mind i missed the post wehere you did this already

thanks

---

### Post by daqron on 2010-05-16
This was annoying the hell out of me because none of the above stuff worked in 10.04. Compiz window placement, wmctrl, and devilspie all ignore VirtualBox VM windows. So, how about just doing it in perl. Make sure wmctrl is installed first.

```
#!/usr/bin/perl
    use strict;
    use warnings;
    system("wmctrl -o [COLOR=Red]1441[/COLOR],0");
    system("VBoxManage startvm [COLOR=Red]Windows[/COLOR]");
```
The first wmctrl value is probably your desktop width + 1. It is where wmctrl considers viewport 2 to begin (1 pixel to the right of viewport 1) on compiz-enabled desktop environments ([more info here]("http://www.bgevolution.com/blog/wmctrl-recap-placing-windows-automatically-on-boot-compiz-viewports/")). Replace "Windows" with whatever your VM's name is. Save the perl file somewhere safe with the .pl extension, i.e., [COLOR="Red"]launcher.pl[/COLOR]. [Make it executable]("http://devdaily.com/blog/post/perl/how-make-perl-program-executable-unix-linux-ftp").

You can also create a launcher for your perl file: right-click on your desktop, select "Create Launcher ...". Configure it as follows:
[INDENT]Type: Application
Name: Whatever You Want
Command: perl [COLOR="Red"]/path/to/launcher.pl[/COLOR]
Comment: Whatever You Want[/INDENT]

Hope this helps!

NB: Sun [recommends deprecation]("http://www.virtualbox.org/manual/ch08.html#vboxmanage-startvm") of the "VBoxManage startvm" command in favor of VBoxHeadless, but that didn't work for me so. YMMV, but I thought I'd warn you.

---

