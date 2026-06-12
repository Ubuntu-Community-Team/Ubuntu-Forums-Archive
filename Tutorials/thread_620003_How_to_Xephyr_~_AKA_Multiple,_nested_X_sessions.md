---
title: "How to Xephyr ~ AKA Multiple, nested X sessions"
date: 2007-11-22
forum: Tutorials
---

### Post by bodhi.zazen on 2007-11-22
[center][size=4]**How to Xephyr**[/size]

[[img]http://cafelinux.org/OptickleArt/albums/userpics/normal_Xephyr.png[/img]](http://cafelinux.org/OptickleArt/albums/userpics/Xephyr.png)

*Click to enlarge*[/center]

What is Xephyr ? 

Xephyr is a X server that runs as a small window within your current X session.

What is it good for ? 

There are multiple potential uses for Xephyr:
[list][*]Development. You can ssh into a chroot and forward X sessions.
[*]Forward X over ssh *without* VNC.[/list]

_Example_: Normally if you ssh -X you can forward x applications. This is not a problem if you are forwarding a single application from a single server. But if you forward multiple applications from multiple servers or a whole desktop, it gets messy (to say the least). You can start a new X session ( [Virtual X](http://ubuntuforums.org/showthread.php?t=271674) ), but then you have to Ctl-Al-F7 and Ctrl-Alt-F8 between them.

1. Install Xephyr 

```
sudo apt-get install xserver-xephyr
```

2. Start Xephyr

```
Xephyr -ac -screen 1280x1024 -br -reset -terminate 2> /dev/null :1 &
```
[list][*]The ":1" = your display (displays are numbered starting with 0)
[*]-ac =  disable access control restrictions= allow you to forward X
[*]-screen 1280x1024 = screen size
[*]-br = black background
[*] -reset -terminate= Xephyr *should* automatically close when the last X client is killed, does not always work.
[*] 2> /dev/null redirects error messages.[/list]

3. Set your display (for X)

```
DISPLAY=:1.0
```

[list][*]Don't forget to set it back after you establish a ssh connection ( DISPLAY=0.0 )[/list]

=========================


4. Forward single apps / separate window for each server.

Start Xephyr

```
Xephyr -ac -screen 1280x1024 -br -reset -terminate 2> /dev/null :1 &
```

Change your $Display

```
DISPLAY=:1.0
```

Forward a xterm:

```
ssh -XfC -c blowfish user@server xterm
```
[list][*]-X = forward X
[*]-f = puts your ssh session into the background
[*]-C = use compression -c blowfish = use blowfish (I am told this is the fastest)[/list]

[[img]http://cafelinux.org/OptickleArt/albums/userpics/normal_xterm.png[/img]](http://cafelinux.org/OptickleArt/albums/userpics/xterm.png)
*Click to enlarge*

[list][*]run "xfwm4" in the terminal for window decorations(substitute your window manager if you are not using xfce).
[*]xterm config file : [http://www.xfce.org/various/Xresources.txt](http://www.xfce.org/various/Xresources.txt)[/list]

Any X apps for that server will start in that window.


=========================


5. Desktop: 

Start Xephyr

```
Xephyr -ac -screen 1280x1024 -br -reset -terminate 2> /dev/null :2 &
```

2. ssh into the chroot/server

```
ssh -XfC -c blowfish user@server xfce4-session
```
[list][*]Substitute your window manager for "xfce4-session"[/list]


=========================


[font=times][size=4][i]Enjoy,[/size][/font]

[img]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/img][size=4] [color=navy][font=times]bodhi.[/color][color=darkgray]zazen[/font][/size][/color][/i]

---

### Post by Dr Small on 2007-11-22
Works good so far. I can't test out ssh yet, since I don't have openssh-server installed on my sisters system yet, but I will try that out soon.

Also, a small fix:
Back where you said:
> Forward a xterm:

```
ssh -Xfc -c blowfish user@server xterm
```

That should be a capital C after -Xfc. Example:
```
ssh -XfC -c blowfish
```

Because I was getting an error with c because of unknown cipher type. :)
Good job, this really makes things simpler yet ;)

Great howto!

Edit:
A screenshot of icewm-session running through Xephyr at 800x600.
[http://ubuntuforums.org/attachment.php?attachmentid=51065&stc=1&d=1195779441](http://ubuntuforums.org/attachment.php?attachmentid=51065&stc=1&d=1195779441)

Dr Small

---

### Post by Dr Small on 2007-11-24
[CENTER][SIZE="4"]Gtk-Xephyr[/SIZE][/CENTER]
Allows you to run Xephyr in a Gtk environment, eliminating the use of starting it all with terminals. You must first download the script below, and give it executable permissions, and copy it to your /usr/bin directory.

Download  from here:
[Dr Small's Blog](http://php.8ez.com/drsmall/blog/wp-content/gtk-xephyr)
Or [Ubuntu Forums](http://ubuntuforums.org/attachment.php?attachmentid=51284&stc=1&d=1195946509) (1)
Chmod it with executable permissions:
```
chmod +x gtk-xephyr
```

Copy it to /usr/bin:
```
sudo cp gtk-xephyr /usr/bin
```

Open it with the Run Dialog (ALT + F2):
```
gtk-xephyr
```

Or make a launcher that points to that command.


I originally wrote this script, after disliking the fact that I needed to open multiple terminals to get this to work, and then Bodhi.Zazen fixed my bugs and made it better :)

You can find the original source of this from here:
[http://php.8ez.com/drsmall/blog/?p=175](http://php.8ez.com/drsmall/blog/?p=175)

(1: If you downloaded the file from the attachment that I uploaded to Ubuntu Forums, please rename it to "gtk-xephyr" instead of "gtk-xephyr.sh". Ubuntu Forums required that I have a file type within their allow list.)


Dr Small

---

### Post by nikoPSK on 2007-12-08
I will have to try this tomorrow.:) thanks bodhi!

---

### Post by adamorjames on 2007-12-08
Looks awesome! Thanks.

---

### Post by jimcooncat on 2008-02-29
I had to add this to the beginning of the script:
```
unset SESSION_MANAGER
```
in order to avoid this error:
```
Another session manager is already running
```

---

### Post by smartboyathome on 2008-07-25
Dr Small, I have modified your script a bit to make it so you can enter your own screen resolution (instead of clicking on pre-defined ones). Here is the new script, in case anyone else wants it. :)

---

### Post by scorp123 on 2008-07-25
> **Dr Small said:**
>  Gtk-Xephyr ... Allows you to run Xephyr in a Gtk environment, eliminating the use of starting it all with terminals. I originally wrote this script, after disliking the fact that I needed to open multiple terminals to get this to work, and then Bodhi.Zazen fixed my bugs and made it better :) Niiiiice!! :grin:

---

### Post by Dratop on 2008-09-22
Thanks for this great script for Xephyr. I still have a (noob?) question though : how do I specify in my xorg.conf file that I want the display associated to Xephyr to be outputted on a outer screen or video projector plugged to my laptop ? I both tried to configure this editing xorg.conf manually and using Nvidia X server settings but did not manage to find a solution.

Thanks in advance for your help.

---

### Post by bodhi.zazen on 2008-09-23
> **Dratop said:**
> Thanks for this great script for Xephyr. I still have a (noob?) question though : how do I specify in my xorg.conf file that I want the display associated to Xephyr to be outputted on a outer screen or video projector plugged to my laptop ? I both tried to configure this editing xorg.conf manually and using Nvidia X server settings but did not manage to find a solution.

Thanks in advance for your help.

I am not sure what you are trying to do exactly, but Xephyr does not run the way you envision. It runs within an existing X session and is not configured through xorg.conf or nvidia-settings.

So you run xephyr on the same screen / x session that is already outputting to your video projector.

---

### Post by mdmcginn on 2008-10-05
On a more popular level, can Xephyr be used to watch ABC.com TV programs, as some have tried to use Xnest to do? See [http://ubuntuforums.org/showpost.php?p=5510093&postcount=12](http://ubuntuforums.org/showpost.php?p=5510093&postcount=12)

---

### Post by kenmiles on 2008-11-02
[QUOTE=

5. Desktop: 

Start Xephyr

```
Xephyr -ac -screen 1280x1024 -br -reset -terminate 2> /dev/null :2 &
```

2. ssh into the chroot/server

```
ssh -XfC -c blowfish user@server xfce4-session
```
[list][*]Substitute your window manager for "xfce4-session"[/list]


=========================


[/QUOTE]

I am using kde 3.5.10 on Ubuntu 8.10.
I am stuck with what to substitute "xfce4-session" with. I have tried kwm-session but I get command not found error.
Thanks in advance for any help, Kenneth.

---

### Post by bodhi.zazen on 2008-11-02
I am a little rusty, but I think KDE usually starts with either 

startx or startkde

You can alternately start the kicker (which is what I have done in the past).

---

### Post by maestrobwh1 on 2008-11-17
I am a bit obtuse... I want to run fluxbox as my nested session on top of kde4:

How do I do this?

brian@brian-laptop:~$ Xephyr -ac -screen 1024x768 -br -reset -terminate 2> /dev/null :1 &
[1] 2439
brian@brian-laptop:~$ DISPLAY=:1.0
brian@brian-laptop:~$ ssh -XfC -c blowfish brian@brian-laptop xterm
ssh: connect to host brian-laptop port 22: Connection refused
**brian@brian-laptop:~$ DISPLAY=0.0** Not sure about this line?
brian@brian-laptop:~$ ssh -XfC -c blowfish brian@brian-laptop xterm
ssh: connect to host brian-laptop port 22: Connection refused
brian@brian-laptop:~$

---

### Post by bodhi.zazen on 2008-11-17
> **maestrobwh1 said:**
> I am a bit obtuse... I want to run fluxbox as my nested session on top of kde4:

How do I do this?

brian@brian-laptop:~$ Xephyr -ac -screen 1024x768 -br -reset -terminate 2> /dev/null :1 &
[1] 2439
brian@brian-laptop:~$ DISPLAY=:1.0
brian@brian-laptop:~$ ssh -XfC -c blowfish brian@brian-laptop xterm
ssh: connect to host brian-laptop port 22: Connection refused
**brian@brian-laptop:~$ DISPLAY=0.0** Not sure about this line?
brian@brian-laptop:~$ ssh -XfC -c blowfish brian@brian-laptop xterm
ssh: connect to host brian-laptop port 22: Connection refused
brian@brian-laptop:~$

Looks like your ssh connection is blocked. Do you have openssh-server installed ? firewall ?

DISPLAY refers to your X session. Your default session is :0. Xephyr is :1 (or whatever you name it). (you do need a colon : before the number).

HTH.

---

### Post by maestrobwh1 on 2008-11-17
I installed openssh-server and got further

brian@brian-laptop:~$ ssh -XfC -c blowfish brian@brian-laptop xterm
brian@brian-laptop's password:
brian@brian-laptop:~$ Xephyr -ac -screen 1152x864 -br -reset -terminate 2> /dev/null :1 &
[1] 22216
brian@brian-laptop:~$ DISPLAY=:1.0
brian@brian-laptop:~$ ssh -XfC -c blowfish brian@brian-laptop xterm
brian@brian-laptop's password:
brian@brian-laptop:~$ [B]Warning: No xauth data; using fake authentication data for X11 forwarding.
connect /tmp/.X11-unix/X1: No such file or directory
Can't open display localhost:10.0
connect /tmp/.X11-unix/X1: No such file or directory
xterm Xt error: Can't open display: localhost:10.0[/B]

---

### Post by bodhi.zazen on 2008-11-17
Is X installed on the machine you are trying to ssh into ?

---

### Post by maestrobwh1 on 2008-11-18
Yes, it is a full blown version of 8.04 Kubuntu. I am launching this from the desktop.  I get bits and pieces but I just can't seem to get something to work.  The only errors I see is what I pasted here.

I am trying to launch fluxbox, but I can't even get xterm to run.  

I don't even think I need to use "ssh" in the command exactly?

**If I am in KDE, what would be the code to run fluxbox, preferably in one line, in Xephyr with a 1024x768 screen (my desktop is 1280x1024)?**

I did this when kde 4 came out a long time ago, and I remember Xephyr being somewhat more cooperative.  It was on a different verision of Ubuntu, and on a different machine.

I found this post
[http://wiki.debian.org/XStrikeForce/FAQ#howtoxnest](http://wiki.debian.org/XStrikeForce/FAQ#howtoxnest) and it mentions something about 
*"Some people find that they can start Xephyr (e.g., with Xephyr :1), but cannot start any clients inside it (e.g., with DISPLAY=:1 xterm or xterm -display :1), because the client connections are rejected by the X server's security mechanism, resulting in error messages like this:"*  The output error listed in the post is similar to mine, but not exactly that same... mine says a directory doesn't exist.

Anyway, the script suggested to run before Xephyr is 

> #!/bin/sh

MCOOKIE=$(mcookie)
xauth add $(hostname)/unix$1 . $MCOOKIE
xauth add localhost/unix$1 . $MCOOKIE
Xephyr "$@"
xauth remove $(hostname)/unix$1 localhost/unix$1

exit 0

But I don't know what to put in for (mcookie), and (hostname) if anything or if this is what the script should look like.

---

### Post by kenmiles on 2008-11-18
> **maestrobwh1 said:**
> I installed openssh-server and got further

brian@brian-laptop:~$ ssh -XfC -c blowfish brian@brian-laptop xterm
brian@brian-laptop's password:
brian@brian-laptop:~$ Xephyr -ac -screen 1152x864 -br -reset -terminate 2> /dev/null :1 &
[1] 22216
brian@brian-laptop:~$ DISPLAY=:1.0
brian@brian-laptop:~$ ssh -XfC -c blowfish brian@brian-laptop xterm
brian@brian-laptop's password:
brian@brian-laptop:~$ [B]Warning: No xauth data; using fake authentication data for X11 forwarding.
connect /tmp/.X11-unix/X1: No such file or directory
Can't open display localhost:10.0
connect /tmp/.X11-unix/X1: No such file or directory
xterm Xt error: Can't open display: localhost:10.0[/B]
Should the DISPLAY not be DISPLAY=:0,1

---

### Post by maestrobwh1 on 2008-11-18
brian@brian-laptop:~$ DISPLAY=:1.0

should be 

brian@brian-laptop:~$ DISPLAY=:1,0

??

I also see posts that use some "export" synatax.

---

### Post by bodhi.zazen on 2008-11-18
Basic steps :

1. Start Xephyr on a new display, say :1.0

2. export display = :1.0. (You can test it is working by entering xeyes and it should appear in Xephyr).

3. SSH into your server. Whey you use the -X, the display in the ssh session is changed to :10.0 (this is normal).

4. Forward X applications. Fluxbox is started with startfluxbox.

---

### Post by maestrobwh1 on 2008-11-18
I am good at some things, but the syntax for getting this kind of thing to work escapes me... So please correct/add/delete what this should look like for me:

> $ Xephyr -ac -screen 1152x864 -br -reset -terminate 2> /dev/null :1 &
$ export=DISPLAY=:1.0
$ xeyes (I should see this in the new 1152x864 "screen" just to test it)
$ ssh -XfC -c blowfish brian@brian-laptop xterm (this should open xterm in the new 1152x864 "screen")  
If xterm opens in the new screen, I can type
-> in xterm 
$ startfluxbox

---

### Post by maestrobwh1 on 2008-11-18
Results
xeyes opens on my kde desktop, not the one created by xephyr

using

> ssh -XfC brian@brian-laptop xterm

with or without the -c blowfish

opens xterm on my kde desktop, not the one created by xephyr

Seriously, I don't "get" how this works...

Even running 
> 
[QUOTE]$ brian@brian-laptop:~/bin$ Xephyr :1 & export DISPLAY=:1; xterm
[1] 12086
xterm Xt error: Can't open display: :1
brian@brian-laptop:~$ _XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/brian-laptop:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc[/QUOTE]

I get a blank xephyr screen (but with little cross hatches) **Screenshot attached** and some errors in konsole.

---

### Post by bodhi.zazen on 2008-11-18
Here is a step-by-step :

> [color=blue]bodhi@hardy:~$ Xephyr -ac -screen 800x600 -br -reset -terminate :1.0 &[/color]
[1] 6389

#This output can be suppressed (re-directed)
bodhi@hardy:~$ expected keysym, got XF86KbdLightOnOff: line 70 of pc08  3:15 PM
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!

# Set the display to :1.0, or Xephyr
[color=blue]bodhi@hardy:~$ export DISPLAY=:1.0[/color]

#Run xeyes
[color=blue]bodhi@hardy:~$ xeyes[/color]

After that last command xeyes is running in the Xephyr window.

---

### Post by maestrobwh1 on 2008-11-19
Thanks... I understand the directions and will try it when I get home... assuming if xeyes shows up in the Xephyr screen... then xterm will:-)

---

### Post by Ape3000 on 2009-01-02
Is it possible to use evdev or something similar to set specified input devices (mice, keyboards) to control specified Xephyr session?

So I'd assign a set of mouse and keyboard so that they always control the Xephyr screen A and another set to control screen B. Then I would put those screens next to each other (both visible) and have multiseat configuration with one physical monitor.

---

### Post by maestrobwh1 on 2009-01-02
Thanks... it works;-)

---

### Post by bodhi.zazen on 2009-01-04
> **Ape3000 said:**
> Is it possible to use evdev or something similar to set specified input devices (mice, keyboards) to control specified Xephyr session?

So I'd assign a set of mouse and keyboard so that they always control the Xephyr screen A and another set to control screen B. Then I would put those screens next to each other (both visible) and have multiseat configuration with one physical monitor.

I have not heard of that but it sounds interesting.

---

### Post by Locke_99GS on 2009-01-05
> **Ape3000 said:**
> Is it possible to use evdev or something similar to set specified input devices (mice, keyboards) to control specified Xephyr session?

So I'd assign a set of mouse and keyboard so that they always control the Xephyr screen A and another set to control screen B. Then I would put those screens next to each other (both visible) and have multiseat configuration with one physical monitor.

The method mentioned here: [https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX) ought to be easily adapted to this article.

---

### Post by boob11 on 2009-01-14
Tnnx

---

### Post by wall0645 on 2009-01-28
Yes!! I figured it out! This is super cool! Thank you bunches bodhi.zazen! METTA :D

---

### Post by sexcopter on 2009-03-10
> **bodhi.zazen said:**
> 
Forward a xterm:

```
ssh -XfC -c blowfish user@server xterm
```
[list][*]-X = forward X
[*]-f = puts your ssh session into the background
[*]-C = use compression -c blowfish = use blowfish (I am told this is the fastest)[/list]

I just saw this an wanted to make this clear. -C gives compression (no choice of method, uses gzip), -c blowfish specifies a particular cipher protocol (nothing to do with compression), and isn't really necessary, since suitable ciphers are invoked anyway.

I got all this from the man page for ssh.

Also, I read somewhere else that while compression is good for low bandwidth situations, on high-speed connections it's actually leads to a performance hit.

Cheers,

James

---

### Post by Dr Small on 2009-03-10
> **smartboyathome said:**
> Dr Small, I have modified your script a bit to make it so you can enter your own screen resolution (instead of clicking on pre-defined ones). Here is the new script, in case anyone else wants it. :)
Instead of using zenity for popups, I've strictly rewritten it for prompts in the terminal. It is much simplier this way, I think :)
```
#!/bin/bash
# 
# GTK-Xephyr
# by Dr Small <drsmall@mycroftserver.homelinux.org>
# Simplifies the process of using Xephyr
#
# Dependencies:
#		Xephyr
	


echo ''
echo 'Select screen resolution'
echo '[1] 640x480'
echo '[2] 800x600'
echo '[3] 1024x768'
echo '[4] USER SPECIFIED'
echo '[5] EXIT'
echo ''
read resolution

case $resolution in
	1)
	resolution='640x480'
	;;

	2)
	resolution='800x600'
	;;

	3)
	resolution='1024x768'
	;;

	4)
	echo 'Please enter a screen resolution:'
	read manualresolution
	resolution=$manualresolution
	;;

	5)
	exit
	;;
esac


echo ''
echo 'Display Number:'
echo '(Please choose a number higher than 0)'
read display


echo ''
echo 'Command:'
echo '(Specify a command to be executed on the nested window)'
read command


echo ''
echo 'Starting Xephyr with resolution of '$resolution
echo 'on display number '$display
Xephyr -ac -screen $resolution -br 2> /dev/null :$display&

echo ''
echo 'Switching to display number '$display
export DISPLAY=:$display

$command&
exit 0
```

---

### Post by Wiebelhaus on 2009-06-02
This is freaking amazing!

Thanks!

---

### Post by shafin on 2009-06-16
I just ran in xephyr into opensolaris (it comes preinstalled) and it looks great.

---

### Post by mk_cafe on 2009-08-02
I just want to ask what's the difference if i set Xephyr on my local computer and then connect to remote computer by ssh with X11 forwarding and when i just set Xephyr by ssh on remote computer? I mean something like this:

1: 
```
Xephyr :1 &
DISPLAY=:1
ssh -X user@hostname
xeyes
```

2:
```
ssh -X user@hostname
Xephyr :1 &
DISPLAY=:1
xeyes
```

If i am thinking right in 1st ex. we are setting Xephyr server to catch any app we start , so when we connect through ssh to remote computer and run any app then it's forwarded to default display on our local comp. which is actually Xypher window?

And in second ex. we just login to remote computer and set Xephyr the same way, but when we  run some application there it's forwarded to Xephyr window on remote comp. and this window is forwarded to our local machine? 

If so, are there any differences like the way data is sending between computers etc.? :P

Sorry if i wrote this unclear but i am just curious and i'm trying to get it ;)

---

### Post by maestrobwh1 on 2009-09-01
This was working in intrepid, but I lost my partition and installed Karmic and re-found my answer in post #24 here to try to get this to work again, as I am getting an error.  Basically I want to run the app XnView in Xephyr on the same machine, as for some reason, the app is transparent on the kde 4 desktop so images are not rendered properly.  No special window settings seem to fix this, but running in Xephyr makes it look proper:

> #!/bin/bash
# xnview.sh to launch xnview in xephyr 
Xephyr -ac -screen 1024x768 -br -reset -terminate :1.0 &
export DISPLAY=:1.0
xnview
exit 0

but I get a 1024x768 black screen and this output:
> $ sh xnview.sh
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 48 requests (46 known processed) with 0 events remaining.
** XnView v1.70 Copyright 1991-2005 Pierre-E Gougelet (Sep  6 2005/15:28:24) **
        Version for Linux x86/Motif (All rights reserved)
** This is freeware software (for non commercial use)

     Type xnview -help, for more information
Error: Can't open display: :1.0
$
The app does open by itself.

---

### Post by bodhi.zazen on 2009-09-01
Karmic is in alpha right now so you may wish to file a bug report.

---

### Post by Snowhog on 2010-01-18
@bodhi.zazen

Back when, like when I was using Intrepid - I used Xephyr to capture the KDM (yes, KDE) Login screen. Then, the command was:

```
Xephyr -query localhost -screen 800x600 :1
```

I'm now using Karmic 9.10 (Kubuntu). The same two files - kdmrc and Xaccess have been properly edited. The command above doesn't work - the syntax for Xephyr has changed - and after Googling, found that this command:

```
Xephyr :1 -query localhost -host-cursor -screen 1024x768

```

should work. It does, but I just get a black screen window of the specified size with a working mouse.

What command syntax do I have to issue in order to get the KDM Login screen? I just want to be able to take a screen shot of my custom KDM Login screen. As stated, back in Intrepid, the 'old' syntax did the trick, but now ...

Thank you.

---

### Post by Snowhog on 2010-01-18
Got it!

```
Xephyr :1 -query 127.0.0.1 -screen 1024x768
```

You have to use the localhost IP address instead of 'localhost' and it works. My KDM Login Screen came up and I was able to take my snapshot of it.

Cool.

---

### Post by schmidtbag on 2010-03-03
anyone know how to get 3d to work in this or is that even possible?

---

### Post by lance bermudez on 2010-03-04
Im lost how do you use this program? I want to be able to connect to a windows xp and a linux box runing ubuntu9.10

---

### Post by schmidtbag on 2010-03-04
> **lance bermudez said:**
> Im lost how do you use this program? I want to be able to connect to a windows xp and a linux box runing ubuntu9.10

...xephyr runs xserver on top of xserver and nothing else.  so basically, run multiple linux graphical interfaces on top of each other.  its not an emulation or virtualization.  look up virtualbox and you'll find your answer

---

### Post by teddyk on 2010-09-30
> **schmidtbag said:**
> anyone know how to get 3d to work in this or is that even possible?

I am wondering this as well... really would like to get  game running in a Xephyr session

---

### Post by bodhi.zazen on 2010-10-01
I do not think Xephyr supports 3d

There is an old blog on this :

[http://dodji.blogspot.com/2007/10/xephyr-xvideo-and-gl-has-landed.html](http://dodji.blogspot.com/2007/10/xephyr-xvideo-and-gl-has-landed.html)

Not sure if that works or not.

---

### Post by xioko on 2011-01-04
Why so difficult?

```
$ echo 'xterm' > .xinitrc
$ xinit -- `which Xephyr` :1
```should do.

---

### Post by devansh.j2007 on 2011-12-12
I am trying to work on a new kdm4 theme.... restarting after a small change is annoying.... so i used Xephyr
i tried both ```
Xephyr :1 -query localhost -host-cursor -screen 1024x768
```

and

```
Xephyr :1 -query 127.0.0.1 -screen 1024x768
```

what i get is a blank screen always
and found out none works in my kde 4.7 i use kubuntu 11.10.. any help guys???

---

### Post by victor0000 on 2012-03-31
```
sudo adduser mo
Xephyr -ac :2 2>/dev/null &
su mo -
DISPLAY=:2
/etc/X11/Xsession
```

---

### Post by leandro666m on 2012-07-31
good work! im trying. will comment.

---

