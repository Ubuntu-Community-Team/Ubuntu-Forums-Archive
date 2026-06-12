---
title: "How to Switch from Terminal to xfce in Ubuntu Server 16.04?"
date: 2016-06-17
forum: Server Platforms
---

### Post by fahid2 on 2016-06-17
Hello Guys,

I have installed Ubuntu Server 16.04, I want to use it as LAMP server.
normally I wouldn't need a GUI on the machine but at times possibly, since I am no good with Linux.

So after installtion of Ubuntu Server, I installed xfce4 desktop
```
sudo apt-get install xfce4
```
It is installed with ton of supporting packages that are installed with above command.

I restarted the Computer, I came to Terminal as before, from there in order to goto GUI, I tried the following:

[B]Command------------------------Result------------------------------Description
[/B]startx-----------------------------Error-------------------------------I know it is not the command for xfce but tried it anyway
sudo service lightdm start------Error-------------------------------Failed to start lightdm.service: Unit lightdm.service not found

How can I get to GUI/ XFCE environment from Terminal?
I don't want it permanent but I want to be able to load/ unload xfce when I want.

---

### Post by howefield on 2016-06-17
Moved to the "*Server Platforms*" forum.

---

### Post by ajgreeny on 2016-06-17
Having just checked it looks as if xfce4 has no display manager as a dependency so that may be what is missing.

From your terminal command-line run ```
sudo apt-get install lightdm
``` and once installed run command ```
sudo service lightdm start
```
With luck that may get you to a login screen and thus your xfce4 GUI.

---

### Post by steeldriver on 2016-06-17
If you installed the xfce4 package, it should have installed xfce4-session which provides its own session start command

```

startxfce4

```

There's no need to add the overhead of a display manager such as lightdm IMHO

---

### Post by fahid2 on 2016-06-17
> **steeldriver said:**
> If you installed the xfce4 package, it should have installed xfce4-session which provides its own session start command

```

startxfce4

```

There's no need to add the overhead of a display manager such as lightdm IMHO

It Still gives an Erorr


> **ajgreeny said:**
> Having just checked it looks as if xfce4 has no display manager as a dependency so that may be what is missing.

From your terminal command-line run ```
sudo apt-get install lightdm
``` and once installed run command ```
sudo service lightdm start
```
With luck that may get you to a login screen and thus your xfce4 GUI.

It won't help as well,

---

### Post by Bashing-om on 2016-06-17
fahid2; Hello;

A server does not by default have an X-server installed. Installing the desktop and no X-server ?
what returns:
```

dpkg -l xorg

```

I do run xfce4 - as on demand - and in order to use "startx" to start this DE .. one must set the directive up in the .xinitrc file.
My execute line:
```

exec startxfce4 --with-ck-launch > /home/sysop/errors-boot.txt 2>&1

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by fahid2 on 2016-06-17
> **Bashing-om said:**
> fahid2; Hello;

A server does not by default have an X-server installed. Installing the desktop and no X-server ?
what returns:
```

dpkg -l xorg

```

I do run xfce4 - as on demand - and in order to use "startx" to start this DE .. one must set the directive up in the .xinitrc file.
My execute line:
```

exec startxfce4 --with-ck-launch > /home/sysop/errors-boot.txt 2>&1

```[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]

Thanks a lot for trying to help, but either I am not getting it or it isn't working

[PHP]dpkg -l xorg[/PHP]
[IMG]http://i68.tinypic.com/be8t9s.png[/IMG]



[PHP]exec startxfce4 --with-ck-launch > /home/sysop/errors-boot.txt 2>&1[/PHP]
[IMG]http://i68.tinypic.com/14blx7k.png[/IMG]


Then I thought maybe I should create this file at this location, it is complaining about. But turns out there is no **/home/sysop** present

---

### Post by Bashing-om on 2016-06-17
fahid2; K;

xorg is installed .. should support that DE.

Let's backup to starting the DE. As is now .. when you boot, you boot to a terminal, right ?
so, what results with the terminal command:
```

statxfce4

```

as to your file mis-comprehension:
You will not have such a file as shown on your system.
my username on my system is 'sysop' . YOUR username - in the file path - will be different.
as in " /home/fahid/"

The control file .xinitrc does not exist by default . You will create this file to control how you want the DE to behave.
In my created file I am starting xfce and I have a error redirection from this execution to a log file, /home/sysop/errors-boot.txt 2>&1, that I also created .

[INDENT][INDENT]learning
[INDENT][INDENT][INDENT]what does it take to start a desk top
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by fahid2 on 2016-06-17
OK, something Worked.. I used
> sudo apt-get install xubuntu-desktop
now I have xfce desktop, or basically now I have like a Xubuntu installation only built on Ubuntu Server. I think it would have been easier to install Xubuntu in the first place if I was going to end like this.

but anyway, can I make it so that desktop shouldn't load by default. Only if I want to load it explicitly, for how long I need, and then unload it and get back to Terminal and save extra system load due to desktop environment?

---

### Post by fahid2 on 2016-06-17
> **Bashing-om said:**
> fahid2; K;

xorg is installed .. should support that DE.

Let's backup to starting the DE. As is now .. when you boot, you boot to a terminal, right ?
so, what results with the terminal command:
```

statxfce4

```

as to your file mis-comprehension:
You will not have such a file as shown on your system.
my username on my system is 'sysop' . YOUR username - in the file path - will be different.
as in " /home/fahid/"

The control file .xinitrc does not exist by default . You will create this file to control how you want the DE to behave.
In my created file I am starting xfce and I have a error redirection from this execution to a log file, /home/sysop/errors-boot.txt 2>&1, that I also created .[INDENT][INDENT]learning[INDENT][INDENT][INDENT]what does it take to start a desk top
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

Since I am trying it all in Virtualbox, before I do it on real PC.

I have made a copy of VBox Disk (base copy) file after initial installation and am always using the base copy, installing xfce4 (sudo apt-get xfce4) and then trying what you guys are suggesting, but so far have no success except with (sudo apt-get install xubuntu-desktop)

and yes, now I have tried with my username instead of sysop in the given command but still doesn't help

and as I said I don't mind having it done this way or installing Xubuntu in the first place. All I want is that desktop is unneccessary and should not load by default, only when I need to use it. I think my PC will be up 24/7 but I maybe using desktop like 2-3 hours a week. so why have desktop load by default, why let it consume any bit of system resources.

---

### Post by Bashing-om on 2016-06-17
fahid2; Sorry;

I do not know the xubuntu-desktop and can not advise on how it operates.

[INDENT]not a know-it-all
[/INDENT]

---

### Post by ajgreeny on 2016-06-17
You could try removing **lightdm** from your system; it will also remove **xubuntu-desktop** package but don't worry as that is just a metapackage, ie a list of packages, and does not actually contain any of the xubuntu packages or applications.

---

### Post by MAFoElffen on 2016-06-18
I looked at your errors... lets say your were still a few posts back when you were still xfce... and hadn't added the world in overhead to your LAMP server...

The original error when you used startx and startxfce4 was that xorg could not write to your ~/.Xauthority file file in your own user directory. (That is an error if you can't do that) If you had done
```

ls ~/.Xauthority -l

```
You might have found that it either did not exist or was wrongfully owned by root.

What the normal fix for that is
```

rm ~/.Xauthority
#may or may not exist
touch ~/.Xauthority
#creates a new file
chmod 660 ~/.Xauthority
# sets the correct permisions
chown YourUserName ~/.Xauthority
# set the ownership of that file to your own user name

```
Now you installed the world and it will boot directly to the graphical login of xubuntu, and not to the console. That is a lot of overhead and opens up a few vulnerabilities if left on all the time... I see you you now having 2 choices
- uninstall xubuntu-desktop and reinstall xfce as an nstance load / occasionally loaded GUI for maintnance.
- Setup xubuntu as an instance load gui.

The first option is fairly self explanitory. The second... 

Edit /etc/defualt/grub and set "text" as a default kernel boot option. Remeber to run update-grub to update the grub menu with the option.

It will then boot, as a default, into the tty console, without the GUI loading. When and if you need the GUI
```

startxfce4

```
After using the gui, then you need to be able to shut the GUI session down, and get back to the console without interupting the server services... Just shutting down X is now going to go back to the grapphical login manager (not the console).  In a terminal session of your XSession (My past support involved the Linux Graphics Layer, so I know it works for all flavors)
```

pidof xorg && pidof gdm
# or lightdm, kdm, or whatever the dm (gui logon manager is...
# then 
sudo kill 0000 0001 0002
# substituting the numbers there for the returned pid numbers of the previous command, separated by a space.
# an XSession will have one pid. DM's usually have 2 pids associated.

```
That will kill both XSession and the GUI Logon Manager and et you back to the console.But, you will then go black and have a blinking cursor in (0,0) of the console... Do not panic. That will just be tty7 without an active XSession. 

Press <Cntrl><Alt><F1> and you will be back to your original console session that you booted up on.

If you go back to XFCE (without a GUI logon manager installed) when you shutdown/quit, or kill the XSession, it would go back to the console. This is what I do with a minimal X install with OpenBox. But my unstalls of that, without a logon manager, gdo directly back to a console prompt.

Hope that info helps. If you need more detailed instructions, just ask.

My recommends would be option one. (with uninstalling xubuntu-desktop) EDIT--> Which after posting this post, I now see is a plus one to Mr. Greeny

---

### Post by TheFu on 2016-06-21
Another option is to NOT bother installing any GUI on the server and just remote in from a client desktop machine. Then you just need to run X-clients on the remote box. Must lighter and less risky than having a full X-server running.  X/Windows client/server architecture is backwards from almost every other C/S architecture. The "server" runs on the machine you sit behind and the "clients" run on the box in the other room or somewhere else in the world.  Use **ssh -X IP-to-other-machine xterm -sb** to see it working.  On a GigE LAN, X works well.  With key-based authentication, it is relatively easy too.

Plus you can use virtualbox to load a very small "desktop" OS just to connect to servers, if you like. All it needs is a minimal X/server - no DE, no extra apps. IMHO, a linux VM is much better than trying to run an X/Server on some other OS.

Just an option for your consideration.

---

### Post by fahid2 on 2016-06-21
> **TheFu said:**
> Another option is to NOT bother installing any GUI on the server and just remote in from a client desktop machine. Then you just need to run X-clients on the remote box. Must lighter and less risky than having a full X-server running.  X/Windows client/server architecture is backwards from almost every other C/S architecture. The "server" runs on the machine you sit behind and the "clients" run on the box in the other room or somewhere else in the world.  Use **ssh -X IP-to-other-machine xterm -sb** to see it working.  On a GigE LAN, X works well.  With key-based authentication, it is relatively easy too.

Plus you can use virtualbox to load a very small "desktop" OS just to connect to servers, if you like. All it needs is a minimal X/server - no DE, no extra apps. IMHO, a linux VM is much better than trying to run an X/Server on some other OS.

Just an option for your consideration.
Now that seems something real amazing,  can you please tell me more about that how to do it from scratch or even better if you can refer me to some such tutorial.

---

### Post by TheFu on 2016-06-21
Strange that you ask ... [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) .
BTW, running an application on a different machine and "displaying" it locally has been part of X/Windows since the beginning.  In the 90s and 80s, because powerful computers were very expensive, this was the normal way we worked.

I only use remote desktops when coming in over the relatively slow WAN link. On the LAN, I use normal X/Windows with ssh tunneling (which is just *ssh -X*)

---

### Post by MAFoElffen on 2016-06-22
@TheFu

XCP or LTSP? On either, or just to do X forwarding, XServer is still installed on the centralized server that you are connecting to. Translated- ssh -X is forwarding X to the remote node thorough a tunnel. 

But yes, I agree. Even MS Win Server has figured that out and now recommends (for them) using core. My management console is a Gnome Desktop. My only servers that I have minimal X instance loads are severs that also have hardware specific GUI management utils, that I need to run from my console.

<Off-topic: wanted to talk to you about your recent convention... containers.>

---

### Post by TheFu on 2016-06-22
> XCP or LTSP?
Never tried either.  Did use XDCP with a pure X/Terminal (remember those?) in the early 1990s before getting a real workstation on my desk.

PM me about the convention, if you like.

---

### Post by MAFoElffen on 2016-06-22
> **TheFu said:**
> Did use XDCP with a pure X/Terminal (remember those?) in the early 1990s before getting a real workstation on my desk.
Yes, :redface:, while in the Army., Ran some automated battle simulations in the late 80's.

---

### Post by fahid2 on 2016-06-28
> **MAFoElffen said:**
> I looked at your errors... lets say your were still a few posts back when you were still xfce... and hadn't added the world in overhead to your LAMP server...

The original error when you used startx and startxfce4 was that xorg could not write to your ~/.Xauthority file file in your own user directory. (That is an error if you can't do that) If you had done
```

ls ~/.Xauthority -l

```
You might have found that it either did not exist or was wrongfully owned by root.

What the normal fix for that is
```

rm ~/.Xauthority
#may or may not exist
touch ~/.Xauthority
#creates a new file
chmod 660 ~/.Xauthority
# sets the correct permisions
chown YourUserName ~/.Xauthority
# set the ownership of that file to your own user name

```

OK, following your instruction as I could understand, this is what i did.
Plateform: Windows 10 Pro, Virtualbox
VBox with EFI,  3GB RAM, 32MB Graphic Memory, 60GB HDD

Fresh Clean Installation of Ubuntu Server 16.04
Command Rundown:```
sudo apt-get install xfce4 -y

sudo reboot

startxfce4  // Error

rm .Xauthority

touch .Xauthority

chmod 660 .Xauthority

chown .Xauthority

startxfce4 //still the error


```

Commands
[[IMG]http://i68.tinypic.com/33o0376_thumb.png[/IMG]]("http://i68.tinypic.com/33o0376.png")

startxfce4
[[IMG]http://i68.tinypic.com/2cwwu39_thumb.png[/IMG]]("http://i68.tinypic.com/2cwwu39.png")

Xorg.0.log file screenshot
[[IMG]http://i64.tinypic.com/2946gw1_thumb.png[/IMG]]("http://i64.tinypic.com/2946gw1.png")

What have I misunderstood?

**You can instruct me to go on from here, or you can tell me to start with an image where I will be executing the first command on Ubuntu Server 16.04, just help me get a minimal desktop installed and running (loading and unloading as desired).**

---

### Post by TheFu on 2016-06-28
If you don't have a specific reason to use EFI inside vbox, don't.
3GB of RAM is a bunch for normal Linux needs.  NONE of my servers get 3G of RAM.
If it is a desktop running inside Vbox, please give the video RAM 128MB. Don't know why, but this seems to help GUI performance tremendously.
60G for a VDI seems high.  On a Linux server, it would be strange to need more than 10G for most common uses - unless you have a huge DB (HUGE!!!!) or lots of media files.

Or where those specs for the total machine and not just the VM?

---

### Post by MAFoElffen on 2016-06-29
If you look at your erorrs, it says that the "local machine" XSession init script at /usr/X11/xinitrc does not specifiy a valid TTY so it picked tty0, which does not exist...

startX uses xint, which (itself) takes arguments to work. One of the arguments that startx is supposed to pass is the TTY session. If you are in tty1 (at the command prompt) and pass 1 manully ... try this yourself to verify: 
```

xinit -- :1 -nolisten tcp vt$XDG_VTNR

```
That should work. If it does, then exit back to the command prompt.

Remember there are 3 levels to profiles: user, local, global. Since user does not exist, it went to the global scrpit in /etc/X11/xinit/xinitrc, which does not set a session ID. So if we create a user script ~?.xintirc, that grabs the session ID, it will get precedence over the local machine script...

Copy the following to a file in the base of your home directory to file ~/.xinitrc
```

#!/bin/sh
exec /usr/bin/X -nolisten tcp vt${XDG_VTNR} "${@}"

```
That will end up as being a custom user X profile file that will pass whatever session number back into the ENV. It needs to be made executable: 
```

chmod +x ~/.xinitrc
# Permission should end up as 0700

```
Then when you do 
```

startx

```
... then it should start up normally, using the session you started from, which is most often tty1.

A ballooned desktop package sets thisse ENV variables from within their desktop package, previous just to tty7, which you notice with 16.04 and systemd, has changed to tty1. What that will do is put the session ID as an ENV variable into the call to the local machine XSession script. 

Try this and see how it works for you.

---

### Post by fahid2 on 2016-06-29
> **TheFu said:**
> If you don't have a specific reason to use EFI inside vbox, don't.
3GB of RAM is a bunch for normal Linux needs.  NONE of my servers get 3G of RAM.
If it is a desktop running inside Vbox, please give the video RAM 128MB. Don't know why, but this seems to help GUI performance tremendously.
60G for a VDI seems high.  On a Linux server, it would be strange to need more than 10G for most common uses - unless you have a huge DB (HUGE!!!!) or lots of media files.

Or where those specs for the total machine and not just the VM?
[B]Specs are for Vbox not the Host
[/B]
No EFI, if necessary - Got It, Thanks
I was just playing around trying to Imitate a scenario with a real machine

RAM: 3GB, thought it will help run the VM better

128MB G-RAM - OK
I gave 32MB as I basically wanted to use it as CLI most of the time. But 128MB it is.

60G? you are right, I maybe won't, because I basically want to attach/ mount some network shares to be used for multimedia data etc.
Next time I will make it 32G

---

### Post by fahid2 on 2016-06-29
> **MAFoElffen said:**
> If you look at your erorrs, it says that the "local machine" XSession init script at /usr/X11/xinitrc does not specifiy a valid TTY so it picked tty0, which does not exist...

startX uses xint, which (itself) takes arguments to work. One of the arguments that startx is supposed to pass is the TTY session. If you are in tty1 (at the command prompt) and pass 1 manully ... try this yourself to verify: 
```

xinit -- :1 -nolisten tcp vt$XDG_VTNR

```
That should work. If it does, then exit back to the command prompt.

Remember there are 3 levels to profiles: user, local, global. Since user does not exist, it went to the global scrpit in /etc/X11/xinit/xinitrc, which does not set a session ID. So if we create a user script ~?.xintirc, that grabs the session ID, it will get precedence over the local machine script...

Copy the following to a file in the base of your home directory to file ~/.xinitrc
```

#!/bin/sh
exec /usr/bin/X -nolisten tcp vt${XDG_VTNR} "${@}"

```
That will end up as being a custom user X profile file that will pass whatever session number back into the ENV. It needs to be made executable: 
```

chmod +x ~/.xinitrc
# Permission should end up as 0700

```
Then when you do 
```

startx

```
... then it should start up normally, using the session you started from, which is most often tty1.

A ballooned desktop package sets thisse ENV variables from within their desktop package, previous just to tty7, which you notice with 16.04 and systemd, has changed to tty1. What that will do is put the session ID as an ENV variable into the call to the local machine XSession script. 

Try this and see how it works for you.

First Through Putty, in .xinitrc copy/ pasted your script: 
#!/bin/sh exec
/usr/bin/X -nolisten tcp vt${XDG_VTNR} "${@}"

[[IMG]http://i63.tinypic.com/24xie7o_thumb.png[/IMG]]("http://i63.tinypic.com/24xie7o.png")

Then directly on the VM: I entered the Command: startx
[[IMG]http://i65.tinypic.com/14bthdf_thumb.png[/IMG]]("http://i65.tinypic.com/14bthdf.png")

tried startxfce4 // error
tried startx by switching ttyx by ALT+ArrowKey // error

---

### Post by MAFoElffen on 2016-06-29
Okay... here is what I do.

if you open ~/.profile, go to the last section of that file. It looks similar to this (from memory, so may be slightly different):
```

...
# If the user has a bin directory add it to the path
if [ -d "$HOME/bin" ] ; then
     PATH=$HOME/bin:$PATH
fi

```
That, translated from BASH to English, look for a directory in the user's home directory called Bin. If it exists, add it to the path, so the user can execute his own scripts and binarys.

I now I could put scripts into that directrory (if I created it) but choose to call it ~/Scripts. I just append the same logic to the end of my ~/.profile file:
```

...
# If the user has a Scripts directory add it to the path
if [ -d "$HOME/Scripts" ] ; then
     PATH=$HOME/Scripts:$PATH
fi

```

My naming conventions for my scripts are now a combination of systemd and powershell (I do integrated environements) so for something like starting something, I use a name like "start.something". So, create either a user bin directory or your own Script directory:
```

mkdir ~/Scripts
mv ~/.xinitrc ~/Scripts/start.X
ls -l ~/Scripts/start.X
vim ~/Scripts/start.X

```
Edit your script to just use the command that worked. (You went on above so I assume the previous test commandline argument worked...)
```

#!/bin/bash
xinit -- :1 -nolisten tcp vt$XDG_VTNR

```

---

