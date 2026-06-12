---
title: "HOWTO: Wii Remote in Ubuntu Intrepid Ibex (8.10)"
date: 2008-11-25
forum: Tutorials
---

### Post by Toshibawarrior on 2008-11-25
**[SIZE=5]Introduction[/SIZE]**

**_[COLOR="Red"]**UPDATE**[/COLOR]_**: If you want an *_easier_* way to make you wiimote work with Ubuntu go read my newest tip on the "**Tips and Advices**" section.

Hello all! I know that many people liked [_Rhubarb's HOWTO about using the wiimote in Ubuntu_]("http://ubuntuforums.org/showthread.php?t=836231&highlight=wii+remote") but are confused on how to make it possible in other versions of K/Ubuntu. So, I decided to make this guide, to help out Rhubarb and everyone else here in the forums!

(To avoid common mistakes and extra work I'll use some snippets from Rhubarb's original guide.) 

This HOWTO should help you get a Wii remote working as a mouse / keyboard / joystick in 32bit or [COLOR=Red]64bit (still untested in Intrepid)[/COLOR] Ubuntu intrepid Ibex 8.10.
There is no compiling required, you only need to download a few packages, and configure a few text files.

**[SIZE=5]Changelog[/SIZE]**
(Here I'll post minor and important updates made to the guide, make sure you read this first to know what's new on the guide.)

0 - *November 25, 2008* = I started the guide.
1 - *November 27, 2008* = Added the **Special Thanks** and **Conclusion** sections and fixed some text formatting.
2 - *November 30, 2008* = Fixed some typos and changed the instructions for autostarting **uinput** on each boot for a much cleaner and nicer way (Thanks to Rhubarb for the tip!).
3 - *December 11, 2008* = Added the Wiimote Whiteboard section (which is still on BETA state).
4 - *December 14, 2008* = Added a few tips and advices.
5 - *December 15, 2008* = Fixed the Wiimote Whiteboard section of the guide (thanks to Rhubarb for the detailed compiling process).
6 - *January 1, 2009* = Added a link to download a .deb for installing the Whiteboard. (Thanks again to Rhubarb for this ;))
7 - *February 10, 2009* = Added an "IMPORTANT NOTE" (which is just a little reminder) on the Infra Red section.
8 - *February 14, 2009* = Added an alternative to restarting when installing wminput and the necessary packages.
9 - -*July 5, 2009* = Fixed some boo-boos on the HOWTO's grammar and added a new tip [Check the Tips and Advices section to see it!]. I also fixed the command to execute wminput for IR Tracking while using ***gksudo***[It needed to be wrapped in quotes for it to work. Thanks to everyone who noticed this, including zbeekman. I don't use IR tracking mode so to me it was irrelevant in some way].
10 - *June 14, 2010* = Just a quick update: today (after almost a year of absence from this tutorial) I tried it with Ubuntu Lucid Lynx (10.04) and everything works. I still haven't tried the whiteboard part, but as far as I've tested, everything is working. So I'll be renaming this tutorial. I also added a new tip.

**[SIZE=5]Requirements[/SIZE]**

Your computer must have a known working bluetooth adapter, a Wii remote.
An infra-red light source is required if you wish to use your Wii remote to behave like a mouse from an IR light source, such as the Wii sensor bar, some candles, an incandescent light, etc.
An IR LED pen is required if you wish to setup a whiteboard with your Wii remote.

**[SIZE=5]Install the needed packages[/SIZE]**

Open up a terminal (Applications --> Accessories --> Terminal) and paste this in:

```
sudo aptitude install wminput wmgui lswm
```Next, we need to find the bluetooth device address of your Wii remote, this will allow you to connect to your Wii remote faster in future, and will let you know if your system can connect to your Wii remote via bluetooth.

In a terminal type this in:

```
lswm
```And press buttons 1 & 2 on your wiimote to put it in discovery mode.

If you don't see something that looks like 00:2A:34:95:FE:B0 then keep on running lswm / pressing buttons 1 + 2 on your Wii remote until you do.

Please note down the number that lswm returns (that looks similar to 00:2A:34:95:FE:B0), this is your Wii remote bluetooth address (Keep in mind that the number given here is an example).

**[SIZE=5]Check to see if all the capabilities of your Wii Remote (and extra controllers) work:[/SIZE]**

Start up wmgui (Applications --> Accessories --> Wmgui).
wmgui is an easy application that's good to use for simple diagnostics on your wiimote, nunchuk and classic controller.

**[SIZE=5]Allow your Wii remote to be a keyboard / mouse / joystick:[/SIZE]**

Unless you want to run **sudo modprobe uinput** every time you start Ubuntu, it's recommended that you make it automatically run upon Ubuntu start up.

Open a terminal and type:

```
gksudo gedit /etc/modules
```
Insert this line at the end of the file:

```
uinput
```So the whole file should look exactly like this:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
uinput

```You have to restart your computer for the settings to take effect.

Alternately, you can just open a terminal and type:

```
sudo modprobe uinput
```

(This method although accepted is not my favorite way of doing this.)

**[SIZE=5]Using your Wii remote as a mouse using acceleration data:[/SIZE]**

If you want to use your Wii remote as a mouse by tilting your Wii remote, then press buttons 1 + 2 on your Wii remote and from a terminal run this:

```
**gksudo wminput <your wiimote's bluetooth address>**
```Please use your bluetooth device address for your Wii remote (the one that **lswm** returned).

**[SIZE=5]Using your Wii remote as a mouse using an Infra-Red light source:[/SIZE]**

**IMPORTANT NOTE**: *To use the wiimote in Infrea-Red mode you need an Infra-Red source, like: incandescent candles, flashlights or a Wireless Wii Sensor Bar. I personally use the Wireless Sensor Bar and it's pretty cool. You won't need to experiment making your own bars, if you don't want to. You can find "sensor bars" in lots of places, including online stores. Keep in mind that the sensor bar is nothing more than a few LED lights and some plastic to make it look pretty. Ask on this thread for suggestions about where to buy or how to make your own sensor bar.*

There's a configuration file that you must first edit before this is possible.
From a terminal, type this in:

```
gksudo gedit /etc/cwiid/wminput/ir_ptr
```Find these lines:

```
Plugin.ir_ptr.X    = ~ABS_X
Plugin.ir_ptr.Y    = ~ABS_Y
```and replace it with:
```

Plugin.ir_ptr.X    = ABS_X
Plugin.ir_ptr.Y    = ABS_Y
```To get your Wii remote to track IR light sources, press buttons 1 + 2 on your Wii remote and from a terminal run this:

```
gksudo "wminput -c ir_ptr <your wiimote's bluetooth address>"
```Please use your bluetooth device address for your Wii remote.
[B][SIZE=5]
Swapping default left and right mouse buttons:[/SIZE][/B]

If you prefer the left mouse button to be button B (the trigger) on your Wii remote, and the right mouse button to be button A on your Wii remote, then from a terminal run this:
```

gksudo gedit /etc/cwiid/wminput/buttons
```Find these lines:
```

Wiimote.A        = BTN_LEFT
Wiimote.B        = BTN_RIGHT
```and replace it with:
```

Wiimote.A        = BTN_RIGHT
Wiimote.B        = BTN_LEFT
```

[B][SIZE=5]
Using your Wii remote and IR LED pen as a whiteboard:[/SIZE][/B]

This can be done by compiling in Intrepid...because the .deb package for Hardy doesn't work on Intrepid due to an incompatibility in some dependencies.

UPDATE: A .deb package was made! The link is below!

**HARD WAY:** (NOTE:Ubuntu 64-bit users have to compile the whiteboard thmselves because there's no .deb for 64-bit at the moment.)

Open up a terminal (Applications --> Accessories --> Terminal)
To install the needed packages type the following in:

```
sudo aptitude install libcwiid1-dev libsdl1.2-dev libxext-dev libbluetooth-dev libxtst-dev subversion lswm libcwiid1 libbluetooth3 libtool libcwiid1-dev libgtkmm-2.4-dev libglademm-2.4-dev libxtst-dev libcairomm-1.0-dev libsigc++-2.0-dev libgnome2-dev intltool libbluetooth-dev
```

You'll be prompted to enter in your password after entering the above command.

Now download the latest wii whiteboard from subversion:

```
svn checkout http://linux-whiteboard.googlecode.com/svn/branches/cpp/ linux-whiteboard-read-only
```

Change to the newly downloaded sources directory

```
cd ~/linux-whiteboard-read-only/
```

Configure it

```
./autogen.sh
```

Compile it

```
make
```

Install it

```
sudo make install
```

Then you can run it

```
whiteboard
```

This has been tested by Rhubarb in Intrepid and it works. If someone is not able to make it work, simply post your situation here.
[B]
EASY WAY:[/B]

There's a .deb package here - - > [http://code.google.com/p/linux-whiteboard/downloads/list]("http://code.google.com/p/linux-whiteboard/downloads/list") Enjoy!

**[SIZE=5]Using your Wii remote for watching DVDs, Elisa Media Center, Music Players, etc:[/SIZE]**

I've setup on my system 2 icons in my gnome panel that I can click on if I want to connect to my Wii Remote and use it's IR light tracking ability as a mouse, and the other to turn off the wminput daemon that I started on the other icon.

Right click on an empty part of the Gnome panel and select "Add to Panel...", then "Custom Application Launcher" then press the "+Add" button.

Type in a name for it, for the command, use this:
```

gksudo "wminput -d -c ir_ptr <your wiimote's bluetooth address here>"
```For IR mode. If you want to use ACC (accelerometer mode) the command should be:

```
**gksudo wminput <your wiimote's bluetooth address here>**
```

[I]
The **gksudo** is important because if you use **sudo** only, you won't see any prompt to type in your password, and in Intrepid it **IS** necessary to be root to activate **wminput**.[/I]

Select a nice icon for it if you wish, then press close.

To create another icon to kill all running wminput processes, do the same as above, but for the command use this:

```
gksudo killall wminput
```Use **gksudo** here too because you might need to type in your password again.

The advantage of using these two icons to run wminput, is that you can turn off your Wii remote (by pressing and holding the power button on your Wii remote) when you start watching a DVD / listening to music to save battery power, then if you wish to start using your Wii remote again, simply press buttons 1 + 2 on your Wii remote and Ubuntu will automatically connect to your Wii remote again as before without having to pick up a keyboard or mouse to do so.
[B][SIZE=5]
Remapping the buttons / axis on your Wii remote / classic controller / nunchuck:[/SIZE][/B]

All the files you would want to change and experiment with are located in /etc/cwiid/wminput/
A list of all possible axis / keyboard / mouse / joystick / gamepad / steering wheel buttons you can bind your Wiimote to:

[_http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt_]("http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt")

If you don't understand something or have questions just ask! And I'll gladly try to help.

**[SIZE=5]Tips and Advices:[/SIZE]**

- If you're not using your nunchuck or classic controller you must comment (add a **#** before each button entry on  /etc/cwiid/wminput/buttons for the nunchuck and classic controller.

- Make sure you write down your Wiimote's bluetooth address and store it in a safe place to avoid having to use **lswm** each time you have to install wminput and cwiid (as in a fresh install of Ubuntu).

- Make sure you have all the latest updates for Intrepid to avoid corruption and/or bugs.

- Remember to use **gksudo** for **wminput** commands, since Intrepid asks for root privileges while using **wminput**.

- If your bluetooth adapter is not working unplug and re-plug it in different USB ports to see if Ubuntu recognizes it.

- In ACC (accelerometer mode) the wiimote's movement might be erratic. For moving the cursor up and down you tilt the wiimote up and down respectively. But for moving the cursor sideways you have to **twist** your wiimote left or right respectively. In IR (Infra-Red) mode you simply move your wiimote up, down, left , right, just like when playing Wii.

- Keep in mind that if you have a Wii and your Ubuntu computer in the same room and you use the wiimote's power button to turn it off, you'll end up turning on the Wii. And the Wii will automatically take over the wiimote.

- I tested XWii and it works flawlessly with Ubuntu 9.10 and 10.04. [Here's]("http://sourceforge.net/projects/xwii/files/xwii_2.9-3_i386.deb/download") a pre-made (completely safe) .deb package for the newest build of XWii. Just install it and run it on a terminal by typing: "xwii" without quotes and selecting a profile. I'll be adding a little more info on XWii's profiles soon. It's very useful and easy to setup, not to mention that the profiles are a breeze to make and it has some sweet capabilities that CWiiD/wminput doesn't have. Enjoy!

[COLOR="Red"]- If your bluetooth dongle doesn't work with your wiimote but does recognize the wiimote's bluetooth address fine, don't waste time reinstalling and fiddling with **wminput** or any other software. Simply try to find another dongle to test the wiimote. I have received multiple posts of people having non-working dongles and it turns out that there's no way to go around that, they just _*don't work!*_ I have also received notice that Bluesoleil dongles don't work with wiimotes, go figure! They don't even work correctly in Windows, try to stay away from these dongles.[/COLOR]

- If you have multiple Wiimotes and don't want to write down all of their addresses you can use this command:

```
gksudo "wminput -d -c ir_ptr $(lswm)"
```

This way ***lswm*** will search the Wiimote's bluetooth address at the same time as ***wminput*** connects to the Wiimote. Remember to press 1 + 2 on the Wiimote while executing this command!

Thanks to **zbeekman** for this!

[SIZE=5]**Special Thanks**[/SIZE]

To **Rhubarb** for making the original guide for Hardy Heron and giving me advice for this guide.

[SIZE=5]**Conclusion**[/SIZE]

Well, for now that's it. If I wasn't clear enough just let me know and I'll fix anything that needs fixing. And if you have suggestions for my guide simply post them here. Just like Rhubarb I'll do my best to keep this guide up to date with new updates in Ubuntu.

If you want to serve as a tester for using the wiimote in other Linux flavors (Kubuntu, Xubuntu, openSUSE, Fedora, etc) then we'll be very grateful if you post back your feedback on how it works.

;) That's All Folks! But stay tuned! ;)

---

### Post by Coreo on 2008-11-26
AWESOME!!   :popcorn:

I'm totally going to try to make this work this weekend.

I've heard a little bit about it from some friends, but didn't believe that it had actually been done, and that it was this easy.

Thanks for the post!!


/thanks Toshibawarrior

---

### Post by Toshibawarrior on 2008-11-26
Hey Coreo, glad to know you liked it! It's pretty easy as you can see. And the best part is that if you (or anyone else) doesn't understand something you can freely ask for help here and I'll help as fast as I can.

Keep checking frequently for updates! :popcorn:

---

### Post by Coreo on 2008-11-26
Well it's kind of a weird coincidence that I stumbled on this this week...
The past few days/week I've been looking into the LIRC (Linux Infrared Remote Control) project.
My computer doesn't come with a media remote, and I find them kind of restrictive anyway. That project seems to be fairly expandable, just like this one...oh the possibilities. Lol.

I just haven't had much time to look into it more and try it out.
But now that I've found this....I might make a bit more progress with both ideas!   ;)

---

### Post by micha137 on 2008-11-27
Hi all,
sorry for posting this message not in the proper thread primarily. Thanks to toshibawarrior I was reminded to put it here:

Great tutorial. Would have saved me a lot of time if I could have started with your tutorial.

@all
As to the point of having to run wminput as sudo in Intrepid. The following steps fixed that on my system so that it can be called now as non-root in Intrepid:

1.)
create a file in /etc/udev/rules.d
somewhat along the lines suggested by clockware in [http://sudan.ubuntuforums.com/showth...535659&page=12](http://sudan.ubuntuforums.com/showth...535659&page=12)
I named it "50-cwiid.input.rules" and included the single line:

KERNEL=="uinput", MODE="0666"

to make uinput accessible to any user (can alternatively be done a bit safer by assigning access only to a special group).

2.)
Then from a Terminal type: "sudo /etc/init.d/udev restart"

then I could call wminput successfully as normal user.


regards
micha137

---

### Post by Rhubarb on 2008-11-28
Nice work there Toshibawarrior :D

It is possible to get wii whiteboard working easily enough.
To do this it must be compiled.  I can't specify the steps to do this just yet, as I'm moving house this weekend, and I've got myself a job.
So needless to say I'm quite busy.

The main reason why the wii whiteboard can't be installed from the debs here:
[http://code.google.com/p/linux-whiteboard/](http://code.google.com/p/linux-whiteboard/)
Is because they where built for Ubuntu 8.04, and not 8.10.
The main difference between the two is that 8.10 comes with libbluetooth3, and 8.04 comes with libbluetooth2.
Installing with the deb file expects to see libbluetooth2.
When compiling the wii whiteboard source it compiles and works nicely with libbluetooth3.

When I get time I'll post here / let Toshibawarrior know; to update this nice howto here.

---

### Post by Toshibawarrior on 2008-11-28
Thanks a lot Rhubarb! I'll update my guide as soon as I/you find something! As I said on your guide, I'd like to keep Hardy stuff on yours and Intrepid in mine, to keep it more organized :)!

Thanks again!

---

### Post by Rhubarb on 2008-11-29
A more elegant way of making "sudo modprobe uinput" automatically start, is to:-

Edit your /etc/modules file:-
```
gksu gedit /etc/modules
```

The add an extra line to the end of the file:-
```
uinput
```

So /etc/modules should look something like this:-
```
So the whole file should look like this:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
uinput
```

---

### Post by shmish on 2008-11-30
Hi, thanks for this tutorial.

I'm having problems with my wii remote connected to the computer.  I'm using a USB bluetooth dongle. I think it is working because when I plug it in, a bluetooth notification icon appears in the upper right corner.  I've gotten as far as entering lswm in a terminal.  The wii remote is not getting discovered.  I think 1 time it almost worked, this was when I powered on the wii remote at the same time as entering lswm.  The address 00:1B:7A:34:D9:84 was returned and the four lights on the bottom of the remote kept flashing.  Eventually the lights returned to a single blue. I went to wmgui and it says there isn't anything connected.  I haven't been able to have the remote discovered since them.

Any ideas on what I can try?

thanks

---

### Post by shmish on 2008-11-30
Hmm, actually it looks like I have it.  I was trying to power on the remote first then press 1+2.  Instead I had the remote turned off (or at least there were no lights on), then pressing 1 + 2 got the remote connected.

cheers!

---

### Post by shmish on 2008-11-30
Oh man, this is too confusing.
If I do lswm and press 1+2, it brings up the bluetooth address.  If I then open wmgui, it says the remote is not connected.  So I then click File -> Connect in wmgui and press 1+2 again.  The remote connects and wmgui shows that that the controls are working.

My problem is that I don't think the wii remote is actually staying connected when I do the lswm.  The terminal reports the address, the bottom blue lights on the remote flash for a while then they go blank.  Likewise with wmgui: if I connect the wii, close and then re-open wmgui, the remote is no longer connected.

I think I either don't quite understand what is supposed to happen, or maybe I'm doing something wrong.

thanks!

---

### Post by Toshibawarrior on 2008-11-30
Hello shmish, actually **lswm** is for bluetooth address acquisition only, nothing else so the wiimote won't stay and doesn't need to stay connected after you get your bluetooth address. 

Likewise **wmgui** only let's you test the buttons and movements of your wiimote, and as soon as the program closes the wiimote will be disconnected.

What you need to make your wiimote work is typing:

```
gksudo wminput <blueooth address>
```

And then you'll have your wiimote working in accelerometer mode.

So don't worry if lswm and wmgui don't keep your wiimote connected because they're not supposed to. They're just for acquiring your bt address and for diagnostics.

Let me know if it works for you. Remember to read my guide throughly and add all the necessary packages and fixes for it to work. :)

Post back your results. ;)!

:popcorn:

---

### Post by brijizacks on 2008-12-01
even though I followed this tutorial to a tee, every time I try to load wminput it says "unable to open uinput"

I have put the necessary line in the config file
I am using 8.10
Any suggestions?  Can I re-install it?  what could be causing this?

The wiimote IS detected via the bluetooth controller, and wmgui senses it as well, so my only issue is with uinput itself.

Thanks in advance.

---

### Post by Toshibawarrior on 2008-12-01
Try reinstalling the packages and using the "**gksudo**" before wminput in a terminal.

Let me know if it keeps doing that after reinstallation.

:popcorn:

---

### Post by brijizacks on 2008-12-01
I typed in gksudo wminput and low and behold, the accelerated movement does work.

BUT, I want to use the IR as a mouse of course, and when I type in 

gksudo wminput -c ir_ptr, I get this

housetv@HouseTV:~$ gksudo wminput -c ir_ptr
gksudo: invalid option -- 'c'
GKsu version 2.0.0

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of usin

I'm guessing I'm typing it in wrong?  perhaps I need to put the command in  quotes or something?

---

### Post by brijizacks on 2008-12-01
I tried quotes and eureka!  Thanks for your help!

If I type that line in a shortcut it should just autoload it for me right?

You rock!

---

### Post by Toshibawarrior on 2008-12-01
Cool to know it worked for you! and yes, if you add that line to a shortcut or panel applet it should load it when you click on it and then it'll show you a password prompt for you to enter your password and successfully connect your wiimote.

Here's the part of my guide where I explained it. In your case use whatever command worked best for you ;)!

> I've setup on my system 2 icons in my gnome panel that I can click on if I want to connect to my Wii Remote and use it's IR light tracking ability as a mouse, and the other to turn off the wminput daemon that I started on the other icon.

Right click on an empty part of the Gnome panel and select "Add to Panel...", then "Custom Application Launcher" then press the "+Add" button.

Type in a name for it, for the command, use this:
Code:

gksudo wminput -d -c ir_ptr <your wiimote's bluetooth address here>

For IR mode. If you want to use ACC (accelerometer mode) the command should be:

Code:

gksudo wminput <your wiimote's bluetooth address here>


The gksudo is important because if you use sudo only you won't see any prompt to type in your password, and in Intrepid it IS necessary to be root to activate wminput.

Select a nice icon for it if you wish, then press close.

To create another icon to kill all running wminput processes, do the same as above, but for the command use this:

Code:

gksudo killall wminput

Use gksudo here too because you might need to type in your password again.

The advantage of using these two icons to run wminput, is that you can turn off your Wii remote (by pressing and holding the power button on your Wii remote) when you start watching a DVD / listening to music to save battery power, then if you wish to start using your Wii remote again, simply press buttons 1 + 2 on your Wii remote and Ubuntu will automatically connect to your Wii remote again as before without having to pick up a keyboard or mouse to do so.

---

### Post by Stunts on 2008-12-01
Just wanted to say thanks for this excelent tutorial. It works great.
This will impress a lot of people suring presentations, especially combined with compiz-fusion. Can you picture actualy flipping the presentation's pages by waving your arm?
Thanks again!

---

### Post by shmish on 2008-12-01
> **Toshibawarrior said:**
> Hello shmish, actually **lswm** is for bluetooth address acquisition only, nothing else so the wiimote won't stay and doesn't need to stay connected after you get your bluetooth address. 

Likewise **wmgui** only let's you test the buttons and movements of your wiimote, and as soon as the program closes the wiimote will be disconnected.

What you need to make your wiimote work is typing:

```
gksudo wminput <blueooth address>
```

And then you'll have your wiimote working in accelerometer mode.

So don't worry if lswm and wmgui don't keep your wiimote connected because they're not supposed to. They're just for acquiring your bt address and for diagnostics.

Let me know if it works for you. Remember to read my guide throughly and add all the necessary packages and fixes for it to work. :)

Post back your results. ;)!

:popcorn:

Okay, I get it.  Your tutorial was great and I didn't have any problems with it.  I just didn't quite understand what was supposed to happen but now I do.  Next I might try and get the IR working, but we'll see.  I have an IR port on my laptop but I have no idea if it's working in Ubuntu.  That would be the first step.  :)

cheers

---

### Post by Toshibawarrior on 2008-12-01
> **Stunts said:**
> Just wanted to say thanks for this excelent tutorial. It works great.
This will impress a lot of people suring presentations, especially combined with compiz-fusion. Can you picture actualy flipping the presentation's pages by waving your arm?
Thanks again!

You're welcome! Glad to know it worked for you! And that presentation flipping would be awesome! ;)

> **shmish said:**
> Okay, I get it.  Your tutorial was great and I didn't have any problems with it.  I just didn't quite understand what was supposed to happen but now I do.  Next I might try and get the IR working, but we'll see.  I have an IR port on my laptop but I have no idea if it's working in Ubuntu.  That would be the first step.  :)

cheers

Great! Let me know if the IR works or not. And if you have any requests, suggestions or questions for/about my tutorial just ask! ;):)

:popcorn:

---

### Post by tiyakusa on 2008-12-01
Hi all,

I really can't connect to the wiimote!
lswm returns well the MAC address but then, I always get a "Socket error" message in both wmgui and wminput.

Any idea, guys?

Bye

---

### Post by Toshibawarrior on 2008-12-01
Try un and re-plugging your bluetooth device and reinstalling the packages if that doesn't work. Also, did you enable the module **uinput**?

Let me know :)!

---

### Post by jcannonsr on 2008-12-01
> **brijizacks said:**
> I typed in gksudo wminput and low and behold, the accelerated movement does work.

BUT, I want to use the IR as a mouse of course, and when I type in 

gksudo wminput -c ir_ptr, I get this

housetv@HouseTV:~$ gksudo wminput -c ir_ptr
gksudo: invalid option -- 'c'
GKsu version 2.0.0

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of usin

I'm guessing I'm typing it in wrong?  perhaps I need to put the command in  quotes or something?

I used:

sudo wminput -c ir_ptr 00:22:AA:E8:77:09 (use your own code)

and it worked.

---

### Post by tiyakusa on 2008-12-02
> **Toshibawarrior said:**
> Try un and re-plugging your bluetooth device and reinstalling the packages if that doesn't work. Also, did you enable the module **uinput**?

Let me know :)!

Still the same error!
The lswm returns well the MAC address of the wiimote.
But then both wminput and wmgui returns 
"Socket connect error (control channel)
unable to connect"

wminput seems ok as wminput does not complain if i run it as sudo

This is a big mess!

---

### Post by Toshibawarrior on 2008-12-02
I really don't what could be wrong there...

Can you try with a different bluetooth adapter?...Maybe that's the problem.

Try using different USB ports also.

I'm sorry but I really haven't experienced this error ever, so I can't tell you exactly how to fix it. Let me know if what I advised you to do here works, if not post back and I'll dig into it a little more.

---

### Post by tiyakusa on 2008-12-02
> **Toshibawarrior said:**
> I really don't what could be wrong there...

Can you try with a different bluetooth adapter?...Maybe that's the problem.

Try using different USB ports also.

I'm sorry but I really haven't experienced this error ever, so I can't tell you exactly how to fix it. Let me know if what I advised you to do here works, if not post back and I'll dig into it a little more.
Sorry but you will have to dig!
The bluetooth adapter works perfectly with the same wiimote on another PC with ubuntu 08.04.

On the intrepid one, I tried all the USB ports.

Nothing works :(

---

### Post by Toshibawarrior on 2008-12-02
I've been googling and reading around some forums and apparently most people fix that by using the MAC address exactly as it appears in **hciscan** which I truly believe was changed for **lswm**.

Try this on a terminal:

```
sudo aptitude remove --purge wminput wmgui lswm
```

Then restart the computer and type this on a terminal:

```
sudo aptitude install wminput wmgui lswm
```

And try following my guide from the start again. Remember to use sudo or gksudo before wminput commands and also make very sure your bluetooth address MAC is exact. Remember that the correct command to use the wiimote in Accelerometer mode is:

```
gksudo wminput XX:XX:XX:XX:XX:XX
```

Replacing the X's with your address...Tell me if it still doesn't work after doing that and sorry for the inconveniences.

---

### Post by tiyakusa on 2008-12-03
I cannot find how to install the hciscan tool.
It does not work on my computer.

Else I tried the 
> 
gksudo wminput XX:XX:XX:XX:XX:XX
With the MAC address returns by lswm, but I still get the "Socket error" message...

---

### Post by Toshibawarrior on 2008-12-03
Well...apparently hciscan doesn't work anymore...looks like it's an old version of a dead program (in my opinion). I've googled around a lot since yesterday i can't find anything to fix your problem except for the stuff I've mentioned above.

I'm truly sorry about your situation, but I hope some expert comes and helps you. I just made the guide not the programs. Besides I haven't came across such a problem before.

Your best bet is to wait for someone to pop in with a magical solution for this problem.
[I][SIZE="4"]
Did you install** all** of Intrepid's latest updates?...And do you have other input devices besides a mouse?...Or have you messed around with **xorg.conf**?[/I][/SIZE]

---

### Post by tiyakusa on 2008-12-04
I confirm that I installed all Intrepid's updates, I have no other input beside the mouse, and I never touched the xorg.conf file...

I tried to compile the latest version of cwiid, but I still get the error with both wmgui and wminput: "Sockect error".

I figured out that I also get the error message even when I don't touch the wiimote (so the wiimote cannot be found as it is not in sync mode).

What knid of message do you have when you try to find a wiimote but don't press 1+2 buttons?

---

### Post by Toshibawarrior on 2008-12-04
Now that you mentioned it, I tried connecting the wiimote but without putting it in discoverable mode and I get the exact same error as you.

Apparently your wiimote is not being synced with Ubuntu ...

Try pressing 1+2 (putting in discoverable mode) before using the wminput command. Maybe your wiimote is taking longer to be synced than in Hardy.

Try that and let me know what happens. Remember first the wiimote and then the "gksudo wminput XX:XX:XX:XX:XX:XX" command, but don't wait too long to input the command.

Hope it works! :)!

---

### Post by tiyakusa on 2008-12-05
I tried all possible timings, nothing works!

Now I would like to debug directly from the source code. Do you know what debugger/IDE I can use to put breakpoints in source code and go deeper in this issue?

---

### Post by Toshibawarrior on 2008-12-05
I'm very sorry but I've never debugged in my life...especially source code. I can find that out for you, but I'll need time. I can have an answer for you in a few hours.

I'll see what I can find! :popcorn:

---

### Post by Toshibawarrior on 2008-12-05
Ok...I haven't got anything on debugging...as I've never done it before. But Rhubarb gave an idea of what might be wrong.

If you upgraded from Hardy probably your bluetooth stack got screwed in the process. Anyways go to Synaptic and search for **libbluetooth2.** If it's installed uninstall completely it and install **libbluetooth3** which is the one that Intrepid uses. And if libbluetooth3 is installed reinstall it just in case.

Since you said that wmgui nor wminput synced with the wiimote most probably the problem lies in your bluetooth stack. Try that and post back the results!

Hope this works!

---

### Post by tiyakusa on 2008-12-05
Both libbluetooth2 and libbluetooth3 were installed.
I removed the 2 version and reinstalled the 3 version: the erorr is still the same...

---

### Post by Toshibawarrior on 2008-12-05
Ugh...I really don't know what to do next...:(

Try uninstalling the 3 version too and then reinstalling it...and reboot the computer to see if it takes effect.

As a last resort you might have to do a fresh install of Intrepid. Upgrades always end up in disaster...:(

---

### Post by dschie on 2008-12-06
Same problem here. Funny thing is: only on one of two notebooks. On my main notebook(kubuntu intrepid, updated since 7.04) the setup works without any problems, but on my netbook (ubuntu intrepid, updated since 8.04) i get this "Socket connect error (control channel)" error.

---

### Post by Toshibawarrior on 2008-12-06
Apparently upgrading Hardy-->Intrepid messes something up (when it is fresh Hardy-->Intrepid and not Feisty-->Gutsy-->Hardy-->Intrepid). My advice is to backup everything important to you and make a fresh install of Intrepid. 

That way you're almost certain to have success in Wiimoting...At least I haven't had any problems this far, and everyone I know who installed Intrepid from scratch for that matter.

So backup, install, and follow the guide again.

The sad part is that wminput and cwiid use intricate parts of X.org and some libraries that aren't easily reconfigured and/or reinstalled...So the best way is to reformat and install a fresh Intrepid.

I hope this helps!

---

### Post by dschie on 2008-12-06
i've just noticed, that my usb-bt-stick seems to be the problem.

[not working]
Bus 001 Device 002: ID 1131:1001 
Integrated System Solution Corp. KY-BT100 Bluetooth Adapter

My internel bt is working is working fine, while the usb-bt-stick fails on the same machine.

[working]
Bus 005 Device 003: ID 0a5c:2110
Broadcom Corp. Bluetooth Controller

i'm not sure if my usb-stick worked with earlyer kernel version :(

---

### Post by Toshibawarrior on 2008-12-06
Hmmm...that's weird, although some USB Bluetooth dongles are notorious for not working well with wiimotes for some reason.

Some sticks/dongles work fine with other devices but not with wiimotes...I still don't know why.

Anyways, try using your internal bluetooth. Most probably there's an incompatibility between both bluetooth receivers...

Keep posting ;)!

---

### Post by Trebaruna on 2008-12-08
My Wii Remote works absolutely fine with my USB IR thingy, except for one thing:
when the pointer is at the edge of the screen I can (obviously) move the remote further away. However, as soon as I start moving it back the pointer moves, too. As a direct result, the relationship between where I point and where the pointer is is not always the same.

I'd like the remote to work a bit more like on the Wii, itself: i.e. the pointer only moves within the proper region of where I point the remote.
So far, I haven't seen how to fix this up. Any advice?

---

### Post by regebro on 2008-12-08
Anybody have any hints or links on how to talk to the Wii Balance Board?

---

### Post by Toshibawarrior on 2008-12-08
> **Trebaruna said:**
> My Wii Remote works absolutely fine with my USB IR thingy, except for one thing:
when the pointer is at the edge of the screen I can (obviously) move the remote further away. However, as soon as I start moving it back the pointer moves, too. As a direct result, the relationship between where I point and where the pointer is is not always the same.

I'd like the remote to work a bit more like on the Wii, itself: i.e. the pointer only moves within the proper region of where I point the remote.
So far, I haven't seen how to fix this up. Any advice?

I'll look deeper into this! But I haven't seen anything this far.

> **regebro said:**
> Anybody have any hints or links on how to talk to the Wii Balance Board?

As of right now there's no way to do it, just nunchuck, classic controller and wiiguitar are usable via **cwiid**.

I'll keep searching and post back my findings!

:popcorn:

---

### Post by Toshibawarrior on 2008-12-10
*_Trebaruna_*: apparently the "range" of the wiimote on the screen is decided by the IR LEDs you have installed. I recommend you install/put one on each end of your monitor (top left, top right, bottom left, bottom right) and that way you might have more control over how and where it goes. Or you can get a Wireless Wii Sensor Bar for $20 at GameStop and that'll work like a charm, I know 'cause I have one. As far a Wii-like control, well it's pretty hard to nail it down, but with what I told you I think you''ll be fine ;).

_*regebro*_: I found  [an article here on the CWIID project page]("http://abstrakraft.org/cwiid/ticket/63") that is exactly what you wanted, BUT it's still a "demo"...and there's some compiling in need to be done, so only do this is you're comfortable compiling and testing new apps.

I hope I could answer your questions like you wanted/needed.

Keep posting!

---

### Post by Dan23945 on 2008-12-10
> **Toshibawarrior said:**
> Or you can get a Wireless Wii Sensor Bar for $20 at GameStop and that'll work like a charm, I know 'cause I have one. As far a Wii-like control, well it's pretty hard to nail it down, but with what I told you I think you''ll be fine ;).

Do you have a Wii? If not, how are you powering the Sensor Bar?

---

### Post by Toshibawarrior on 2008-12-10
> **Dan23945 said:**
> Do you have a Wii? If not, how are you powering the Sensor Bar?

I have a Wii, but if you turn on a Wii near the wiimote the Wii will take over the wiimote and the computer won't be able to use it.

I have a wired sensor bar (the wii's one) but I just use it for Wii. I bought a NYKO Wireless Sensor Bar which uses 4 AA batteries and it lasts a decent amount of time. 

Anyways, I prefer accelerometer mode.

Keep posting :popcorn:

---

### Post by Dan23945 on 2008-12-10
Is there a way to prevent the Wii from taking over the Wiimote? I would like to test everything with my sisters Wii before I purchase the remote and NYKO Sensor Bar. Thanks!

---

### Post by Toshibawarrior on 2008-12-10
Well, you can un-sync your wiimote from the Wii, or if the controller is brand new then you just program it for Ubuntu and don't sync it with the Wii (by pressing the red button on the front of the console and on the back of the wiimote).

Basically if you hold the SYNC button down on the Wii for 15 seconds, it will clear all synced Wii Remotes from the console. So that way the Wii won't take over the wiimote when on. To sync back just follow the instruction in the manual.

---

### Post by Dan23945 on 2008-12-10
My plan is to use the Wiimote as a remote for [Boxee]("http://boxee.tv/"). In your opinion, is using the Wiimote in Ubuntu similar enough to using it on the Wii, that it will serve my purpose? Thanks for the help.

---

### Post by Toshibawarrior on 2008-12-10
In my opinion they're very different applications...the Wii has a lot more stability and precision, but Ubuntu manages quite well. In accelerometer mode it's kinda weird, bur in InfraRed mode it controls very alike the Wii with some minor differences based on the position of the IR LEDs or IR sources.

I believe it'll serve your purpose quite nicely. I use it with VLC, Amarok, Compiz, Rhythmbox, Secret Maryo Chronicles, FretsOnFire, ZSNES, and many other programs and it works pretty well. I use it as a mouse too and it works nicely.

I hope I answered your question ;)!

---

### Post by Dan23945 on 2008-12-10
Thanks for the help. I'll give it a shot tonight and let you know how it goes. I have a feeling my biggest issue is going to be getting my bluetooth adapter working correctly.

---

### Post by Toshibawarrior on 2008-12-10
> **Dan23945 said:**
> Thanks for the help. I'll give it a shot tonight and let you know how it goes. I have a feeling my biggest issue is going to be getting my bluetooth adapter working correctly.

Sure! Let me know how it goes! ;)

---

### Post by mediamind on 2008-12-10
Toshibawarrior, thanks very much for this tutorial! 

Any progress re using the Wii remote and IR Pen as a Whiteboard in Intrepid? Thanks again!

---

### Post by Toshibawarrior on 2008-12-10
> **mediamind said:**
> Toshibawarrior, thanks very much for this tutorial! 

Any progress re using the Wii remote and IR Pen as a Whiteboard in Intrepid? Thanks again!

Well after some research and asking around the whiteboard can be achieved by compiling it from source, but I don't have the details at the moment. I'll look it up and post it on the guide as soon as I can!

Thanks for posting :popcorn:! :)!

---

### Post by Toshibawarrior on 2008-12-10
I added a section of the wiki for Wiimote Whiteboard to my guide. I haven't been able to test it because I don't have an IR LED pen but if someone wants to test it and post the results and the process they made I'll be very grateful and add it to my guide, obviously thanking whoever does it ;).

I'm not a skilled "compiler" so I won't be of much help right now, but as soon as I find out more info and if someone wants to post what they did and if the section of the wiki I posted worked, I'll update my guide again and write up a cleaner, nicer version of that specific section. ;)

Thanks for your interest! Keep visiting my guide! :)!:popcorn:

---

### Post by Dan23945 on 2008-12-11
> **Toshibawarrior said:**
> Sure! Let me know how it goes! ;)

Worked perfectly! Your guide is wonderful! I wasn't able to get my Kensington bluetooth dongle to detect the Wiimote, luckily I have a Planet bluetooth dongle that worked perfectly. The alpha build of Boxee I'm using has an issue with the IR tracking, but I could navigate the interface easily after remapping the Wiimote buttons.

---

### Post by Toshibawarrior on 2008-12-11
> **Dan23945 said:**
> Worked perfectly! Your guide is wonderful! I wasn't able to get my Kensington bluetooth dongle to detect the Wiimote, luckily I have a Planet bluetooth dongle that worked perfectly. The alpha build of Boxee I'm using has an issue with the IR tracking, but I could navigate the interface easily after remapping the Wiimote buttons.

Awesome! Glad to know it worked for you! ;)! Linux, Ubuntu and Wiimotes are grand! and very customizable :p!

I hope you can keep having a wonderful wiimoting experience! 

:popcorn:!

---

### Post by Rhubarb on 2008-12-11
> **Toshibawarrior said:**
> I added a section of the wiki for Wiimote Whiteboard to my guide. I haven't been able to test it because I don't have an IR LED pen but if someone wants to test it and post the results and the process they made I'll be very grateful and add it to my guide, obviously thanking whoever does it ;).

I'm not a skilled "compiler" so I won't be of much help right now, but as soon as I find out more info and if someone wants to post what they did and if the section of the wiki I posted worked, I'll update my guide again and write up a cleaner, nicer version of that specific section. ;)

Thanks for your interest! Keep visiting my guide! :)!:popcorn:

I'll play around with the wii whiteboard this weekend.
I've made up an IR LED pen myself, and I have gotten the whiteboard working in intrepid from compiling before.

There should be no need to compile from SVN, the tar file should be all that's needed.
I'll post details of all the steps taken to compile it and get it working soon.
And if I can figure out how to make proper deb packages, I may even setup my own PPA repository for it.

-Rhubarb

---

### Post by Maheriano on 2008-12-11
When I plug in my Bluetooth dongle I get a Bluetooth icon on my top taskbar so I click it and choose Setup New Device. I press the 1 and 2 buttons on the Wiimote and it comes up with the code, great! Then I click next to connect to the device and it says the connection failed. So I try it with my Blackberry and the connection failed again. So I go into Wmgui and try to connect there, it says the connection failed there as well. Is there something wrong with my dongle?

It's a BlueSoleil dongle, I hear these are garbage after searching for a bit.

---

### Post by Toshibawarrior on 2008-12-12
> **Maheriano said:**
> When I plug in my Bluetooth dongle I get a Bluetooth icon on my top taskbar so I click it and choose Setup New Device. I press the 1 and 2 buttons on the Wiimote and it comes up with the code, great! Then I click next to connect to the device and it says the connection failed. So I try it with my Blackberry and the connection failed again. So I go into Wmgui and try to connect there, it says the connection failed there as well. Is there something wrong with my dongle?

It's a BlueSoleil dongle, I hear these are garbage after searching for a bit.

Some dongles are ruthless toward wiimotes...besides there's no need to use the bluetooth icon on the taskbar for wiimoting...But if your Blackberry is not recognized either, then the dongle might be faulty. Try using it on another USB port, or using another dongle (maybe a friend's).

Let me know how it goes for you!

---

### Post by Toshibawarrior on 2008-12-12
> **Rhubarb said:**
> I'll play around with the wii whiteboard this weekend.
I've made up an IR LED pen myself, and I have gotten the whiteboard working in intrepid from compiling before.

There should be no need to compile from SVN, the tar file should be all that's needed.
I'll post details of all the steps taken to compile it and get it working soon.
And if I can figure out how to make proper deb packages, I may even setup my own PPA repository for it.

-Rhubarb

Thank you very much for the info! I'll keep my guide as it is right now until you can test it :)! If there's no problem with you of course ;)!

As I said before I have no way to test it right now :(.

See you around! :popcorn:!

---

### Post by pseudolegolas on 2008-12-12
my wiimote is getting detected by using lswm 

$ lswm
Put Wiimotes in discoverable mode now (press 1+2)...
00:1C:BE:F1:7D:28


but is not getting connected by using wmgui or wminput.even kbluetooth bluetooth-wizard is not able to connet to it.

$ wminput                      
Put Wiimote in discoverable mode now (press 1+2)...
Socket connect error (control channel)             
unable to connect

i tried it with sudo as well as wminput 00:1C:BE:F1:7D:28 but nothing seems to work

i have a fresh install of kubuntu 8.10


the remote and dongle works fine with windows and i even tried the whiteboard program sucessfully.

i searched the net for any solution but to no use.

can anyone help!!!!!
SOS SOS SOS.................

---

### Post by Toshibawarrior on 2008-12-12
Ok...I really haven't used the wiimote with Kubuntu/KDE...but I believe you might need to reinstall the programs.

Also try to use the dongle in different USB ports, and if you can, use another bluetooth dongle.

Check these basic steps first and if it doesn't work let me know ;)!

---

### Post by pseudolegolas on 2008-12-13
well i have tried all damn possible options with this dongle.................reinstalled many times................it doesnot work................

the same dongle worked with bluesoleil drivers in windows...............do we have any other driver other than bluez............the problem is in bluez

$ sudo hcitool info 00:1C:BE:F1:7D:28
Requesting information ...                                                   
        BD Address:  00:1C:BE:F1:7D:28                                       
        Device Name: Nintendo RVL-CNT-01                                     
        LMP Version: 1.2 (0x2) LMP Subversion: 0x229                         
        Manufacturer: Broadcom Corporation (15)                              
        Features: 0xbc 0x02 0x04 0x38 0x08 0x00 0x00 0x00                    
                <encryption> <slot offset> <timing accuracy> <role switch>   
                <sniff mode> <RSSI> <power control> <enhanced iscan>         
                <interlaced iscan> <interlaced pscan> <AFH cap. slave>

---

### Post by Toshibawarrior on 2008-12-13
> **pseudolegolas said:**
> well i have tried all damn possible options with this dongle.................reinstalled many times................it doesnot work................

the same dongle worked with bluesoleil drivers in windows...............do we have any other driver other than bluez............the problem is in bluez

$ sudo hcitool info 00:1C:BE:F1:7D:28
Requesting information ...                                                   
        BD Address:  00:1C:BE:F1:7D:28                                       
        Device Name: Nintendo RVL-CNT-01                                     
        LMP Version: 1.2 (0x2) LMP Subversion: 0x229                         
        Manufacturer: Broadcom Corporation (15)                              
        Features: 0xbc 0x02 0x04 0x38 0x08 0x00 0x00 0x00                    
                <encryption> <slot offset> <timing accuracy> <role switch>   
                <sniff mode> <RSSI> <power control> <enhanced iscan>         
                <interlaced iscan> <interlaced pscan> <AFH cap. slave>

I'm sorry, but I haven't seen any other bluetooth driver for Linux. I believe your bluetooth dongle is kinda limited to Windows driver-wise.

Maybe the problem is between a Bluesoleil dongle and Bluez...

Try another dongle if possible.

---

### Post by joe_newbie on 2008-12-13
Thank you for the guide!

I use cwiid and my wiimote with mythtv. I have created a custom /etc/cwiid/wminput/buttons   config file that works very well with mythtv. I though I would share it in case others were looking for these keymappings so here it is:

#buttons

Wiimote.A		= KEY_ENTER
Wiimote.B		= KEY_ESC
Wiimote.Up		= KEY_UP
Wiimote.Down	= KEY_DOWN
Wiimote.Left	= KEY_LEFT
Wiimote.Right	= KEY_RIGHT
Wiimote.Minus	= KEY_9
Wiimote.Plus	= KEY_0
Wiimote.Home	= KEY_SPACE
Wiimote.1		= KEY_KPPLUS
Wiimote.2		= KEY_KPMINUS

all other entries in the standard config file have been commented out (disabled) by adding the # symbol before each line.

In case anyone is wondering, plus and minus are used by mplayer (in the mythvideo plugin) to adjust audio synchronisation.
 
I also have wminput -d run automatically by mythbuntu so that I do not need to use a mouse/keyboard at all with my mythtv frontends :)

Joe

---

### Post by Maheriano on 2008-12-14
BlueSoliel dongles don't work in Linux, I have one as well. It finds the address but won't connect. It barely worked in Windows, they're terrible. I'm just going to dump it and get a new one.

---

### Post by Toshibawarrior on 2008-12-14
> **Maheriano said:**
> BlueSoliel dongles don't work in Linux, I have one as well. It finds the address but won't connect. It barely worked in Windows, they're terrible. I'm just going to dump it and get a new one.

I bought an unbranded Chinese bluetooth dongle from eBay for $5 and it works wonders with my laptop...I can use it for any application imaginable in XP, Vista and Linux (Ubuntu, Kubuntu, openSUSE and PuppyLinux) with no problems whatsoever.

[SIZE="6"]**So my advice for people who have dongles that retrieve the wiimote's address fine but don't do anything else is to get another dongle to test *_first_*.:)**[/SIZE]

This way you won't end up wasting valuable time reinstalling, reconfiguring and fiddling with a non-working bluetooth dongle/transmitter/receiver...

:popcorn:

---

### Post by Rhubarb on 2008-12-15
> **Toshibawarrior said:**
> I bought an unbranded Chinese bluetooth dongle from eBay for $5 and it works wonders with my laptop...I can use it for any application imaginable in XP, Vista and Linux (Ubuntu, Kubuntu, openSUSE and PuppyLinux) with no problems whatsoever.

Indeed toshibawarrior.
I've used really really really cheap usb bluetooth adaptors / integrated bluetooth in laptops, they all work well for me.

In other news:  I haven't had much time this weekend to try compiling the whiteboard stuff.  - Mainly because I've discovered blueproximity.
It's really cool, with any bluetooth device, it  can sense it's distance from the computer, and lock / unlock the screen if you are near / far away.
It also lets you choose which applications / scripts to run on those events.
It's totally cool stuff :P

I'll post sometime soon how to compile the wii whiteboard.

-Rhubarb

---

### Post by Thalarse on 2008-12-15
This is great! It took a while, but I got it working. Now I just have to find the spare wiimote (which was flung across the room, and now the accelerometers don't work.), and some IR LEDs. 

Actually I need my house to be built so I can set up the theatre room with a mythtv frontend box and (if possible) IR laser diodes to put the four dots on the screen (rather than having wiring taped all over the wall). The busted wiimote is perfect for this!

---

### Post by Rhubarb on 2008-12-15
> **Thalarse said:**
> ... IR laser diodes to put the four dots on the screen (rather than having wiring taped all over the wall).

Sounds like a great idea.
Just remember you only need 1 IR source for excellent tracking with the wiimote.  1 IR source is actually better than 2, 3, or 4 IR LEDs.
If you're thinking of using IR Lasers, take care in choosing a suitable power output, and make sure you don't shine it in your eyes (or off reflective surfaces).
A mobile phone camera / wmgui + wiimote would be good to help you "see" the projected IR laser dots.

I've found the IR laser emitted by laser mice (like my logitech G9 mouse), does not have a sufficient power output to be visible to the wiimote.

---

### Post by Rhubarb on 2008-12-15
> **mediamind said:**
> Any progress re using the Wii remote and IR Pen as a Whiteboard in Intrepid? Thanks again!

I've compiled the wii whiteboard successfully in Intrepid 32bit on my netbook.

The following are the steps I took to compile and install it:-



[SIZE="4"][I]Open up a terminal (Applications -->  Accessories --> Terminal)
And type the following in:[/I][/SIZE]

[SIZE="4"]Install all the relevant packages[/SIZE]
```
sudo aptitude install libcwiid1-dev libsdl1.2-dev libxext-dev libbluetooth-dev libxtst-dev subversion lswm libcwiid1 libbluetooth3 libtool libcwiid1-dev libgtkmm-2.4-dev libglademm-2.4-dev libxtst-dev libcairomm-1.0-dev libsigc++-2.0-dev libgnome2-dev intltool libbluetooth-dev
```
You'll be prompted to enter in your password after entering it in.

[SIZE="4"]Now download the latest wii whiteboard from subversion[/SIZE]
```
svn checkout http://linux-whiteboard.googlecode.com/svn/branches/cpp/ linux-whiteboard-read-only
```

[SIZE="4"]Change to the newly download sources directory[/SIZE]
```
cd ~/linux-whiteboard-read-only/
```

[SIZE="4"]Configure it[/SIZE]
```
./autogen.sh
```

[SIZE="4"]Compile it[/SIZE]
```
make
```

[SIZE="4"]Install it[/SIZE]
```
sudo make install
```

[SIZE="4"]Then you can run it[/SIZE]
```
whiteboard
```


I found that it sometimes lags on my netbook.
I'm not sure if it's because it's underpowered, or because it has integrated bluetooth.  It does work nicely other times though.

Another note, if you have blueproximity installed, you'll need to quit out of it if you wish to connect via bluetooth to your wiimote / use other bluetooth devices.  As I think it seems to hold the device you're tracking in blueproximity hostage, disallowing use by cwiid.

-Rhubarb

---

### Post by Maheriano on 2008-12-15
What exactly is the whiteboard? I know what they are in my office but not sure how that translates to Linux + Wii remote.

---

### Post by Toshibawarrior on 2008-12-15
> **Maheriano said:**
> What exactly is the whiteboard? I know what they are in my office but not sure how that translates to Linux + Wii remote.

Here you go. I found a description of the Whiteboard, copied from Softpedia...

> Turn any surface into an interactive whiteboard with your Wiimote

Wiimote Whiteboard allows you to use the Wii Remote (Wiimote) to turn any surface into a Low-Cost Interactive Whiteboard.

It is based on Johnny Lee's original WiimoteWhiteboard program that is written in C# and available for Windows only. My program uses Java to allow for (some) platform-independence.

The developer also provides a Mac-only version of the application which you can use on your Apple computer.

Here are some key features of "Wiimote Whiteboard":

· Runs on Mac OS X, Windows, and Linux
· Simple User Interface available in English, French, German, Portuguese, and Spanish
· Auto-connects up to 2 Wiimotes
· Camera Monitor and Calibration Details for better Wiimote placement
· Right-click support, double-click assistance
· Mouse cursor smoothing
· Screen selection
· Touchpad Mode
· Update notification
· TUIO/OSC support for multi-touch applications

Basically it'll transform any surface of your desktop into an interactive whiteboard...

Have fun!

---

### Post by Maheriano on 2008-12-15
> **Toshibawarrior said:**
> Here you go. I found a description of the Whiteboard, copied from Softpedia...



Basically it'll transform any surface of your desktop into an interactive whiteboard...

Have fun!

Sorry, still don't get it. So it allows you to use the Wiimote as a virtual marker and the lines show up on your screen? And who uses this?

---

### Post by Toshibawarrior on 2008-12-15
> **Maheriano said:**
> Sorry, still don't get it. So it allows you to use the Wiimote as a virtual marker and the lines show up on your screen? And who uses this?

Basically yes. That's exactly what it does. But I might not be the most appropriate person to answer this question since I can't test the whiteboard myself.

As far as I've read it basically turns your wiimote into a marker and your monitor into a big writing board.

---

### Post by mediamind on 2008-12-15
Maheriano,

Check out this video demonstration and all will be revealed: [http://www.youtube.com/watch?v=5s5EvhHy7eQ&eurl=http://www.cs.cmu.edu/~johnny/projects/wii/](http://www.youtube.com/watch?v=5s5EvhHy7eQ&eurl=http://www.cs.cmu.edu/~johnny/projects/wii/)

---

### Post by Maheriano on 2008-12-16
Last question. For using it as an infrared remote, how do you connect the sensor bar to the computer with that weird little connector on it? Are there USB sensors?

---

### Post by Toshibawarrior on 2008-12-16
As stated before any IR source will do...a Wireless Sensor Bar, an incandescent candle...etcetcetc...

I use the NYKO Wireless Sensor Bar and it works just fine, just needs 4 AA batteries...

As far as I've seen there's no way to use the Wii's sensor bar on the computer. Anyways, the sensor bar is nothing more than a few IR LEDs inside a "stylish" plastic casing.

:popcorn:

---

### Post by pmontini on 2008-12-17
I had my wii remote working in Hardy, but when I upgraded to Intrepid, it no longer works.  It does find the address, but will not connect.  When I move the dongle to another computer with hardy it works...

what is new in intrepid that would cause this?

I have been searching and there does not seem to be a solution, other than try another dongle.  With the dongle on another machine with hardy working, I do not believe it is a dongle problem...

I will try the hardy live cd next with the intrepid pc hardware too see if it truely is an intrepid problem...

any other suggestions would be appreciated.

---

### Post by Toshibawarrior on 2008-12-17
> **pmontini said:**
> I had my wii remote working in Hardy, but when I upgraded to Intrepid, it no longer works.  It does find the address, but will not connect.  When I move the dongle to another computer with hardy it works...

what is new in intrepid that would cause this?

I have been searching and there does not seem to be a solution, other than try another dongle.  With the dongle on another machine with hardy working, I do not believe it is a dongle problem...

I will try the hardy live cd next with the intrepid pc hardware too see if it truely is an intrepid problem...

any other suggestions would be appreciated.

Ok, first of all...Welcome!

Second, since you upgraded from Hardy to Intrepid you most likely have a big mess of dependencies and libraries mixed together...

First thing to check here is:

Are you using the **gksudo** before *wminput* commands?

Second thing to check would be:

Do you have **libbluetooth2** and **libbluetooth3** installed? If you have both (most probably you do since you upgraded) get rid of both by Completely Removing them with Synaptic and then installing **libbluetooth3** only.

Most upgrades from Hardy to Intrepid end up in disaster and duplicated libraries...

Try these to steps first...and if it doesn't work, report back and let me know what happened.

As a side note: if these steps don't work, get your important data backed up since there's a 99% chance that a fresh install is in need to be done...most problems that emerge from faulty upgrades are extremely hard to fix...the only "easy" way is to backup, delete, format and install anew...sad but true.

:popcorn:

---

### Post by pmontini on 2008-12-19
Thanks for the help, but no luck.  I did a fresh install of intredid and have the same problems... I get the address, but no connection.  I ran the hardy livecd and it connect no problems.  I am thinking I will rebuild the previous uinput module.  Is it possible to rebuild uinput for intrepid at the hardy level? or has anyone tried this?

or should I look into any other drivers/files?

Thanks!

---

### Post by Toshibawarrior on 2008-12-19
> **pmontini said:**
> Thanks for the help, but no luck.  I did a fresh install of intredid and have the same problems... I get the address, but no connection.  I ran the hardy livecd and it connect no problems.  I am thinking I will rebuild the previous uinput module.  Is it possible to rebuild uinput for intrepid at the hardy level? or has anyone tried this?

or should I look into any other drivers/files?

Thanks!

I really don't know if it'd be possible to build uinput for Hardy in Intrepid...

But...have you used other dongles?...Maybe...just maybe...your current dongle is not recognized by Intrepid...

I'm sorry but I've never tried to build "older" programs/modules in intrepid except for ffmpeg and with no luck...

Maybe someone here has more "building" skills than me ;)!

I really hope you can fix this soon!

---

### Post by Trebaruna on 2008-12-20
Haven't checked in for some time.

Thanks for the advice, I'll consider adjusting the sensors' range, but that isn't the core of the problem. The Wii treats the remote as out of range when the cursor hits the edge of the screen, not when it loses sight of the sensors. It has a bounding box representing the screen. So the remote move back in range when it reenters that box, not as soon as it regains orientation with its sensors. wminput would work better if it also used such a bounding box.

Anyway: I've got my setup working with my homebrew sensor bar and wii mote synced to the computer. The daemon is set to start when I log in. So far, so good. Here's the problem:
when my machine wakes up from stand by, the daemon has died. It reports having caught some signal or other (will get back to you on the exact message).

Clearly, I'd like it to resume its work after waking up. Is there some setting, flag, whatever that I can pass wminput? Can I stick a small script running the daemon somewhere in Ubuntu's bowels so the system will just start it every time..?

---

### Post by Toshibawarrior on 2008-12-22
> **Trebaruna said:**
> Haven't checked in for some time.

Thanks for the advice, I'll consider adjusting the sensors' range, but that isn't the core of the problem. The Wii treats the remote as out of range when the cursor hits the edge of the screen, not when it loses sight of the sensors. It has a bounding box representing the screen. So the remote move back in range when it reenters that box, not as soon as it regains orientation with its sensors. wminput would work better if it also used such a bounding box.

Anyway: I've got my setup working with my homebrew sensor bar and wii mote synced to the computer. The daemon is set to start when I log in. So far, so good. Here's the problem:
when my machine wakes up from stand by, the daemon has died. It reports having caught some signal or other (will get back to you on the exact message).

Clearly, I'd like it to resume its work after waking up. Is there some setting, flag, whatever that I can pass wminput? Can I stick a small script running the daemon somewhere in Ubuntu's bowels so the system will just start it every time..?

Well...apparently Ubuntu always has problems with standby/sleep...

When you say the daemon, you mean the daemon that wminput starts, or the uinput stuff in rc.local?...

Come back with this info and I'll try to help! Sorry for my lateness in responding but I've been playing with openSUSE these days and haven't got around to get wireless working...anyway, let me know! 

:popcorn:

---

### Post by joesnose on 2008-12-23
good guide, i personally upgraded from hardy to intrepid only to find my nice panel icons for my wiimote didn't work anymore. i edited etc/modules and added uinput to the list, still no joy!

 gksudo was not working for me, so i changed the permissions as described in the first page. this worked, although the deamon does not seem to persist, i have to push the panel icon twice to get it to connect, so if i power off the wiimote, it does not get rediscovered when i push the 1 and 2 buttons.

 i can live with this , just happy my wiimote is working again.

an extra note for those building sensor bars, if you want to use the wiimote up close, make your ir leds about 3 inches apart. and if you want to use it further away, 8 inches apart is good.

---

### Post by Rhubarb on 2008-12-24
> **joesnose said:**
> an extra note for those building sensor bars, if you want to use the wiimote up close, make your ir leds about 3 inches apart. and if you want to use it further away, 8 inches apart is good.

I've found that one IR LED is fine for this (rather than having 2).
Or if distance is important, cluster a few IR LEDs together in one spot.

I haven't actually tried out using the daemon, so that I can turn my wiimote off, then on again to test the daemon's persistance.
- I'll test this out for myself during the next few days :)

---

### Post by nattyebola on 2008-12-25
thanks a lot man !

---

### Post by Toshibawarrior on 2008-12-25
> **nattyebola said:**
> thanks a lot man !

You're welcome! Remember to hit the "Thanks" button on the lower right corner of the post you found useful! That way the users can have higher "Thanks stats" and everyone can know what you liked the most! :)

Just a little reminder. :popcorn:!

---

### Post by pmontini on 2008-12-26
Thanks for all the help, but I could not find a way to rebuild modules, so I bought a new micro usb dongle and everything works perfectly!

hardy 8.04 - Cyber-blue Micro Usb Dongle = Works out of box with Wiimote
Intrepid 8.10 - Cyber-blue Micro Usb Dongle = Does not work with Wiimote

Intrepid 8.10 - Kensington Usb Micro Dongle = Works out of box with Wiimote

---

### Post by Toshibawarrior on 2008-12-26
> **pmontini said:**
> Thanks for all the help, but I could not find a way to rebuild modules, so I bought a new micro usb dongle and everything works perfectly!

hardy 8.04 - Cyber-blue Micro Usb Dongle = Works out of box with Wiimote
Intrepid 8.10 - Cyber-blue Micro Usb Dongle = Does not work with Wiimote

Intrepid 8.10 - Kensington Usb Micro Dongle = Works out of box with Wiimote

GREAT! ;)! I'm very glad you managed to work it out! :)

Apparently most problems with incompatibilities between wiimotes and Ubuntus can be solved bu switching dongles...;)! I added this tip/advice to my guide!

Keep wiimoting! :popcorn:

---

### Post by Rhubarb on 2008-12-26
> **joesnose said:**
> ... although the deamon does not seem to persist, i have to push the panel icon twice to get it to connect, so if i power off the wiimote, it does not get rediscovered when i push the 1 and 2 buttons.

Quite true,
I just tested for myself if this is the case.
Running wminput in deamon mode does not act as a daemon too well.
It won't reconnect at all.

Tried using all of these to no avail:-
```
sudo wminput -d 00:1F:32:95:EF:B0
sudo wminput -r 00:1F:32:95:EF:B0
sudo wminput -r 5 00:1F:32:95:EF:B0
```

There's a chance compiling cwiid from source may resolve this.
I haven't checked if this is a known bug or not either.

Thunderstorm coming in, have to go now ---->
-Rhubarb

---

### Post by galgylf on 2008-12-27
Hi, I've just installed ubuntu again. It's a long time since i last used it.
I would really like to try the whiteboard, but i live in the middle of nowhere an it would cost a fortune to get a IR LED sent to me. It would even cost more to drive to a store to buy one. So i wonder, could i use a IR LED from an old remote instead of buying one or is that a bad idea?

Rock on! :guitar: Galgylf

---

### Post by Rhubarb on 2008-12-27
> **galgylf said:**
> ...So i wonder, could i use a IR LED from an old remote instead of buying one or is that a bad idea?

Yes, that should work fine.
A 1.5 volt battery (AAA or AA should be fine to use) and a push button momentary switch is all that you should need to get it to work.

Just remember LEDs are polarised devices, they only work when they're in the circuit in the correct way (I forget which, anode or cathode to +ve), so if it doesn't work one way, try the other way.

Also, you shouldn't use just the remote for your whiteboard, as remotes pulse the IR LED, which causes big problems for the whiteboard app, as it registers double clicks everywhere.

IR LEDs shouldn't need a current limiting resistor in series when they're connected to a 1.5V supply, so it should be safe to connect up without one (which is what I'm currently doing with my IR LED pen).

Have fun wiimote whiteboarding!

---

### Post by Contrast on 2008-12-28
> **Toshibawarrior said:**
> As a side note: if these steps don't work, get your important data backed up since there's a 99% chance that a fresh install is in need to be done...most problems that emerge from faulty upgrades are extremely hard to fix...the only "easy" way is to backup, delete, format and install anew...sad but true.

Great tutorial, much appreciated.

Just FYI, you don't really need to backup or format when reinstalling Ubuntu. Just select "Manual" in the partitioning step of Ubiquity, set the mount point of the partition from your previous install to /, and voila. It will clear out every folder except /home and leave all your personal files in place. I've done this several times and it works perfectly.

---

### Post by Toshibawarrior on 2008-12-28
> **Contrast said:**
> Great tutorial, much appreciated.

Just FYI, you don't really need to backup or format when reinstalling Ubuntu. Just select "Manual" in the partitioning step of Ubiquity, set the mount point of the partition from your previous install to /, and voila. It will clear out every folder except /home and leave all your personal files in place. I've done this several times and it works perfectly.

Cool! Thanks for the tip! ;)...Although i rather do it the hard way...

---

### Post by yeswiican on 2008-12-29
I would just say THANK YOU for this very nice guide. Every thing worked for me (8.10 installation from live cd)
Im not the happy owner of another wii sensor bar so I tried to use 2 ir-led in series with one 100ohm resistor in the usb-port - but until now the to test candel-lighs give the best result.
Thanks again - fantastic job!- And a very nice feeling to control your cursor from the sofa without a mouse...

---

### Post by Trebaruna on 2008-12-29
Toshibawarrior: The problem is clearly with wminput. If I run it from the terminal it will say something like caught signal <some signal> and quit. I think it's a POSIX signal, but unfortunately I forgot to check the exact message, and now I do not have the machine handy.
After resume I can just go and restart wimput without problems and it will continue doing its thing.

joesnose, Rhubarb: curious. if I run wminput -d with a directive to use IR (-c ir_ptr perhaps? can't recall right now) it works like one would expect. Press 1+2 to connect, press the power icon to disconnect. Repeat as often as you'd like.

---

### Post by mmalluck on 2008-12-31
Here's a question on a different tangent:

Any chance we can get one of the wiimote LEDs to blink every couple of seconds so we know its alive? I keep killing batteries with this thing because I forget it's on.

I don't imagine it would be too difficult given that the LED control capability already exist in the wmgui. I'm just not familiar enough with the code to cook up my own solution.

---

### Post by Toshibawarrior on 2008-12-31
> **Trebaruna said:**
> Toshibawarrior: The problem is clearly with wminput. If I run it from the terminal it will say something like caught signal <some signal> and quit. I think it's a POSIX signal, but unfortunately I forgot to check the exact message, and now I do not have the machine handy.
After resume I can just go and restart wimput without problems and it will continue doing its thing.


So, the problem is solved then?...I really don't like either sleep or hibernate...they remind of Window$ somehow...lol!:-D

> **mmalluck said:**
> Here's a question on a different tangent:

Any chance we can get one of the wiimote LEDs to blink every couple of seconds so we know its alive? I keep killing batteries with this thing because I forget it's on.

I don't imagine it would be too difficult given that the LED control capability already exist in the wmgui. I'm just not familiar enough with the code to cook up my own solution.

I was looking to do the same thing...I'm not a programmer and I'm scared to death of breaking my perfectly working wiimoting experience.

What I do is hit the "OFF!" launcher I create don the taskbar ... That way the wiimote will lose it's signal and turn off. Try that. Make a really eye catching icon and add it to the launcher (explained on the tutorial) and that should work...Or you can also issue the commands via Terminal and then close the terminal when done...that should kill wminput too...

Check it out and let me know if that works for you. If not, then we'll need to dig into the code.

---

### Post by Rhubarb on 2009-01-01
Looks like the wii whiteboard is available for download (for intrepid) as a nice deb file from their website now.

[http://code.google.com/p/linux-whiteboard/downloads/list](http://code.google.com/p/linux-whiteboard/downloads/list)

Unfortunately there's no 64bit deb at the moment.
I haven't had a chance to test it out, it should work nicely though.

If you've got 64bit Ubuntu installed, I'd recommend you either wait for a 64bit deb to be released, or to compile it yourself, or you might be able to get away with downloading libbluetooth2 for Ubuntu 8.04 deb file and installing it in intrepid, then installing the wii whiteboard 64bit deb for ubuntu hardy.

---

### Post by ias2 on 2009-01-02
Hi,

   I followed this tutorial on a Ubuntu 8.10 AMD64 box and everything works fine. I have only one problem: after a few minutes of inactivity, the Wiimote get paused and there no way to get it works back. If I restart wminput and press "1+2" on the Wiimote, I get the error message "Socket connect error (control channel)".
Running "hcitool con", I see that the Wiimote is actually connected, but there's way to use it untill reboot ("hcitool dc"  not work).
Is there a way to resume the wiimote and connection after it went into standby? Alternatively, there is a way to avoid the standby?

---

### Post by Toshibawarrior on 2009-01-02
> **ias2 said:**
> Hi,

   I followed this tutorial on a Ubuntu 8.10 AMD64 box and everything works fine. I have only one problem: after a few minutes of inactivity, the Wiimote get paused and there no way to get it works back. If I restart wminput and press "1+2" on the Wiimote, I get the error message "Socket connect error (control channel)".
Running "hcitool con", I see that the Wiimote is actually connected, but there's way to use it untill reboot ("hcitool dc"  not work).
Is there a way to resume the wiimote and connection after it went into standby? Alternatively, there is a way to avoid the standby?

That's weird...It's not supposed to go into standby...

Did you try to remove the batteries on the wiimote and reinserting them? Maybe the wiimote keeps connected while wminput went to sleep and that may be why the error appears...

Try that and come back with the result :)!

---

### Post by ias2 on 2009-01-05
I've performed some other tests and the problem seem to be not related to Wiimote and it's standby state (or wminput), but to an Ubuntu bug or hardware problem... see this:

-----------------------------------------------------------------
root@htpc:~# hcitool con
Connections:
	< ACL 00:1E:35:18:B2:F1 handle 0 state 5 lm MASTER

root@htpc:~# /etc/init.d/bluetooth stop
 * Stopping bluetooth                                       [ OK ] 

root@htpc:~# hcitool con
Connections:
	< ACL 00:1E:35:18:B2:F1 handle 0 state 5 lm MASTER 
-----------------------------------------------------------------

Either there is something weird or I don't know enough about bluetooth technology :)

---

### Post by trottamundo on 2009-01-05
I have installed the whiteboard deb file (0.3.4.2 thanks :)) and get some errors. 

1) The pictures needed for the GTK program are not in the good place. They are in /usr/local/share/pixmaps but whiteboard need them in /usr/local/share/whiteboard/windows/gtk. You can bypass this bug by copy/paste all the file in the right place.

2) ```
(whiteboard:7356): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated. 
``` I don't know if it's critical or not.

3) This deb don't resolved the "socket connect error" i have till the beginnig

Ubuntu intrepid with all update, MSI bluetooth BToes adaptator.

happy new year and thanks for this work.

---

### Post by Toshibawarrior on 2009-01-05
> **ias2 said:**
> I've performed some other tests and the problem seem to be not related to Wiimote and it's standby state (or wminput), but to an Ubuntu bug or hardware problem... see this:

-----------------------------------------------------------------
root@htpc:~# hcitool con
Connections:
	< ACL 00:1E:35:18:B2:F1 handle 0 state 5 lm MASTER

root@htpc:~# /etc/init.d/bluetooth stop
 * Stopping bluetooth                                       [ OK ] 

root@htpc:~# hcitool con
Connections:
	< ACL 00:1E:35:18:B2:F1 handle 0 state 5 lm MASTER 
-----------------------------------------------------------------

Either there is something weird or I don't know enough about bluetooth technology :)

I really don't know what could be wrong. After using that module "stop" command it's supposed to be stopped...and not appear on hcitool again...:(

> **trottamundo said:**
> I have installed the whiteboard deb file (0.3.4.2 thanks :)) and get some errors. 

1) The pictures needed for the GTK program are not in the good place. They are in /usr/local/share/pixmaps but whiteboard need them in /usr/local/share/whiteboard/windows/gtk. You can bypass this bug by copy/paste all the file in the right place.

2) ```
(whiteboard:7356): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated. 
``` I don't know if it's critical or not.

3) This deb don't resolved the "socket connect error" i have till the beginnig

Ubuntu intrepid with all update, MSI bluetooth BToes adaptator.

happy new year and thanks for this work.

1) Your workaround should be enough ;)!

2) I don't think you should worry about that since most "third-party" programs throw those types of errors every now and then, although they shouldn't.

3) This .deb is only for the whiteboard. The "Socket Connect Error" has to do with wminput and cwiid (and most probably with your bluetooth adapter.

I'm very sorry if my answers are not what you expected, but as I stated on my guide, I don't have the resources to use the whiteboard, so I can't test it...I just added that part because i know some people wanted it, but I haven't got around to test and probably won't be able to in a while. :(

---

### Post by Maheriano on 2009-01-05
What have I done wrong? It works with the accelerometer as a mouse perfectly, I just can't get the infrared to work. Here's what I get when I type in the line:

```

deemar@Chugger:~$ gksudo wminput -c ir_ptr 00:17:AB:23:A3:49
gksudo: invalid option -- 'c'
GKsu version 2.0.0

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a description name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful for scripts where the
    program accepts receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.

```

---

### Post by Toshibawarrior on 2009-01-05
Somehow "gksudo" gets confused with the "-c" argument in the command. The same thing happened to me and I fixed it by using "sudo" instead of "gksudo"...Try it and report back. ;)!

---

### Post by Maheriano on 2009-01-07
> **Toshibawarrior said:**
> Somehow "gksudo" gets confused with the "-c" argument in the command. The same thing happened to me and I fixed it by using "sudo" instead of "gksudo"...Try it and report back. ;)!

Now what have I done?

```
deemar@Chugger:~$ sudo wminput -c ir_ptr 00:17:AB:23:A3:49
Put Wiimote in discoverable mode now (press 1+2)...
Socket connect error (control channel)
unable to connect

```

---

### Post by Hamm3rh34d on 2009-01-07
Bravo Toshiba! All is well after sorting out the gksudo argument! I have to say it's far more sensitive than I could have hoped for! Excellent guide-well written and precise, I applaud you. Thanks to Rhubarb as well! People like you guys keep the experimentation alive!

---

### Post by Toshibawarrior on 2009-01-07
> **Maheriano said:**
> Now what have I done?

```
deemar@Chugger:~$ sudo wminput -c ir_ptr 00:17:AB:23:A3:49
Put Wiimote in discoverable mode now (press 1+2)...
Socket connect error (control channel)
unable to connect

```

Did you use another bluetooth adapter?...Usually those "socket connect errors" come from a faulty dongle/adapter...Weird thing is that you can connect in accelerometer mode...........#-o

Are you sure you're using the correct bluetooth address?...Double-check it just in case. If everything stays the same let me know and I'll dig into those darned "socket connect errors" a little more ;)!

> **Hamm3rh34d said:**
> Bravo Toshiba! All is well after sorting out the gksudo argument! I have to say it's far more sensitive than I could have hoped for! Excellent guide-well written and precise, I applaud you. Thanks to Rhubarb as well! People like you guys keep the experimentation alive!

Thank you very much Hamm3rh34d! It's good to know people have liked my guide! :):):)

I just do all I can to keep helping people! I love Linux and I love experimenting! And I'm sure Rhubarb feels the same ;)!

What attracted me the most about Linux, specifically Ubuntu, is the awesome amount of freedom you get! So I love experimenting and poking files and configurations to see how we can all learn and improve what already is great! ;) And I intend to keep helping others do this as well :p!

Thanks again! And happy wiimoting!

---

### Post by Hamm3rh34d on 2009-01-07
I had the same socket connect error, but it was because I hadn't put the wiimote in discoverable mode BEFORE running the command. On the second time, I went into discoverable mode first and it synced right away. Could possibly be a timing issue?

---

### Post by Maheriano on 2009-01-07
> **Toshibawarrior said:**
> Did you use another bluetooth adapter?...Usually those "socket connect errors" come from a faulty dongle/adapter...Weird thing is that you can connect in accelerometer mode...........#-o

Are you sure you're using the correct bluetooth address?...Double-check it just in case. If everything stays the same let me know and I'll dig into those darned "socket connect errors" a little more ;)!
You're a genius! I wasn't looking at the Wiimote to make sure it was in discoverable, I was just hitting the buttons.....however that wasn't working because I was already connected in accelerometer mode so hitting the 1+2 buttons did nothing. So I held the power button to turn it off, then hit 1+2 again, that put it in discoverable mode, then I ran the command again and it connected! Then I just lit a household candle and used that as the infrared source, worked like butter!

---

### Post by Maheriano on 2009-01-09
After using this for a day, I've decided this is my new permanent mouse for my machine, I love it. It's much easier and user friendly than using a mouse on my sysem. I can see how it wouldn't be ideal for someone sitting in front of a screen but I use a 150 inch projector as my screen and I sit on the couch with a wireless keyboard so the Wiimote eliminates trying to move a mouse around on the cushions of the couch. Plus the ability to turn it on/off via the Wiimote is great. Everyone should give this a try.

I also have an idea: What if you used this for first person shooter games where you look by moving the mouse? If you picked up the plastic Wii Zapper piece ($10) which mounts the Wiimote and Nunchuck to it, then you mapped your movement buttons to the analogue stick on the Nunchuck, you could look around the screen simply by moving your gun to look. Then you move forward, backwards, strafe by moving the analogue stick on the Nunchuck which is at the back of the gun. Wouldn't this be badass?

[IMG]http://images.google.com/url?source=imgres&ct=tbn&q=http://www.wired.com/images/article/full/2007/12/wii_zapper_500px.jpg&usg=AFQjCNGiLFQHRPLIMQSAJSrF1-WZgmKJYQ[/IMG]

---

### Post by NullHead on 2009-01-09
Really nice guide! It's a good reference. I can now controle my mouse with my wii remote! It's not so wonderful with out using an IRC sensor bar ... I still have to make one and try it out, but hay, it works! 

Thanks for writing it :D

---

### Post by Toshibawarrior on 2009-01-10
> **Maheriano said:**
> After using this for a day, I've decided this is my new permanent mouse for my machine, I love it. It's much easier and user friendly than using a mouse on my sysem. I can see how it wouldn't be ideal for someone sitting in front of a screen but I use a 150 inch projector as my screen and I sit on the couch with a wireless keyboard so the Wiimote eliminates trying to move a mouse around on the cushions of the couch. Plus the ability to turn it on/off via the Wiimote is great. Everyone should give this a try.

I also have an idea: What if you used this for first person shooter games where you look by moving the mouse? If you picked up the plastic Wii Zapper piece ($10) which mounts the Wiimote and Nunchuck to it, then you mapped your movement buttons to the analogue stick on the Nunchuck, you could look around the screen simply by moving your gun to look. Then you move forward, backwards, strafe by moving the analogue stick on the Nunchuck which is at the back of the gun. Wouldn't this be badass?

[IMG]http://images.google.com/url?source=imgres&ct=tbn&q=http://www.wired.com/images/article/full/2007/12/wii_zapper_500px.jpg&usg=AFQjCNGiLFQHRPLIMQSAJSrF1-WZgmKJYQ[/IMG]

Great idea! Sadly I use a laptop with a 15.4" monitor and it's virtually impossible to deprecate my mouse...the wiimote is kinda tedious to control on a small monitor.

> **NullHead said:**
> Really nice guide! It's a good reference. I can now controle my mouse with my wii remote! It's not so wonderful with out using an IRC sensor bar ... I still have to make one and try it out, but hay, it works! 

Thanks for writing it :D

Thank you and you're welcome ;)!

---

### Post by Meson on 2009-01-10
Does anyone know of a list of valid keys for the /etc/cwiid/wminput/buttons file?  Also, does it have to be a keyboard or mouse action?  Can I open a program with a specific key?

---

### Post by Toshibawarrior on 2009-01-10
> **Meson said:**
> Does anyone know of a list of valid keys for the /etc/cwiid/wminput/buttons file?  Also, does it have to be a keyboard or mouse action?  Can I open a program with a specific key?

Here you go ---> [http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt]("http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt")

That's the official list of available keys to link to wiimote buttons, pretty cool I might add, because you can also sync "multimedia buttons" (i.e. Play/Pause, Stop, etc) to wiimote buttons! :)

As for opening programs and doing other actions with wiimote buttons, I believe that someone is working on that right now. Apparently they're looking for a way to link scripts (for opening programs and doing specific actions) to wiimote buttons. I believe the only way to do that is using XWii instead of CWiiD...I haven't looked into that stuff for a while though. I'll let you know when I get some info ;)!

Happy wiimoting!

---

### Post by Meson on 2009-01-10
> **Toshibawarrior said:**
> you can also sync "multimedia buttons" (i.e. Play/Pause, Stop, etc) to wiimote buttons! :)


Thanks, that's what I'm trying to do, set up a nice configuration file for VLC.

---

### Post by Snille on 2009-01-10
Hi all,
I've been playing with the WII mote a bit, but I can't seam to be able to compile the whiteboard (Ubuntu 8.10, 64bit system). Has anyone got it to work?

I can download the source from SVN, but the it is not possible to run the ./autogen.sh in the "linux-whiteboard-read-only".
How ever, there is a folder called build and in there there is a "make-deb.sh", that one is possible to run but ends with an error...

Here is the full "log". I think I may have forgotten something, but I don't know what...
Let me know if anyone have any ideas... :)

```

snille@edge:~/linux-whiteboard-read-only/build$ sudo ./make-deb.sh 
[sudo] password for snille: 
Merging translations into ../src/whiteboard.desktop.
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package whiteboard
dpkg-buildpackage: source version 0.3.4.2-0ubuntu1
dpkg-buildpackage: source changed by VAnhTu1987 <VAnhTu1987@gmail.com>
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp 
# Add here commands to clean up after the build process.
#/usr/bin/make clean
dh_clean 
 debian/rules build
dh_testdir
cmake .. -DCMAKE_INSTALL_PREFIX=/usr
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- checking for module 'gtkmm-2.4'
--   found gtkmm-2.4, version 2.14.1
-- checking for module 'libglademm-2.4'
--   found libglademm-2.4, version 2.6.6
-- Configuring done
-- Generating done
-- Build files have been written to: /home/snille/linux-whiteboard-read-only/build
dh_testdir
# Add here commands to compile the package.
/usr/bin/make -j2
make[1]: Entering directory `/home/snille/linux-whiteboard-read-only/build'
make[2]: Entering directory `/home/snille/linux-whiteboard-read-only/build'
make[3]: Entering directory `/home/snille/linux-whiteboard-read-only/build'
make[3]: Entering directory `/home/snille/linux-whiteboard-read-only/build'
Scanning dependencies of target translations
make[3]: Leaving directory `/home/snille/linux-whiteboard-read-only/build'
Scanning dependencies of target whiteboard
make[3]: Entering directory `/home/snille/linux-whiteboard-read-only/build'
make[3]: *** No rule to make target `../ALL', needed by `ALL.gmo'.  Stop.
make[3]: Leaving directory `/home/snille/linux-whiteboard-read-only/build'
make[2]: *** [CMakeFiles/translations.dir/all] Error 2
make[2]: *** Waiting for unfinished jobs....
make[3]: Leaving directory `/home/snille/linux-whiteboard-read-only/build'
make[3]: Entering directory `/home/snille/linux-whiteboard-read-only/build'
[ 10%] [ 10%] Building CXX object src/CMakeFiles/whiteboard.dir/common.cpp.o
Building CXX object src/CMakeFiles/whiteboard.dir/main.cpp.o
[ 15%] Building CXX object src/CMakeFiles/whiteboard.dir/auxiliary.cpp.o
[ 21%] Building CXX object src/CMakeFiles/whiteboard.dir/events.cpp.o
[ 26%] Building CXX object src/CMakeFiles/whiteboard.dir/ConfigFileParser.cpp.o
[ 31%] Building CXX object src/CMakeFiles/whiteboard.dir/configurator.cpp.o
[ 36%] Building CXX object src/CMakeFiles/whiteboard.dir/irfilter.cpp.o
[ 42%] Building CXX object src/CMakeFiles/whiteboard.dir/calibration.cpp.o
[ 47%] Building CXX object src/CMakeFiles/whiteboard.dir/wiicontrol.cpp.o
/home/snille/linux-whiteboard-read-only/src/wiicontrol.cpp: In function ‘cwiid_wiimote_t* wii_connect(char*)’:
/home/snille/linux-whiteboard-read-only/src/wiicontrol.cpp:45: warning: taking address of temporary
[ 52%] Building CXX object src/CMakeFiles/whiteboard.dir/wiicursor.cpp.o
[ 57%] Building CXX object src/CMakeFiles/whiteboard.dir/gtk-gui.cpp.o
[ 63%] Building CXX object src/CMakeFiles/whiteboard.dir/wiicursormanager.cpp.o
Linking CXX executable ../bin/whiteboard
make[3]: Leaving directory `/home/snille/linux-whiteboard-read-only/build'
[ 63%] Built target whiteboard
make[2]: Leaving directory `/home/snille/linux-whiteboard-read-only/build'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/snille/linux-whiteboard-read-only/build'
make: *** [build-stamp] Error 2
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
snille@edge:~/linux-whiteboard-read-only/build$

```

Any ideas?

---

### Post by Toshibawarrior on 2009-01-10
> **Snille said:**
> Hi all,
I've been playing with the WII mote a bit, but I can't seam to be able to compile the whiteboard (Ubuntu 8.10, 64bit system). Has anyone got it to work?

I can download the source from SVN, but the it is not possible to run the ./autogen.sh in the "linux-whiteboard-read-only".
How ever, there is a folder called build and in there there is a "make-deb.sh", that one is possible to run but ends with an error...

Here is the full "log". I think I may have forgotten something, but I don't know what...
Let me know if anyone have any ideas... :)

```

snille@edge:~/linux-whiteboard-read-only/build$ sudo ./make-deb.sh 
[sudo] password for snille: 
Merging translations into ../src/whiteboard.desktop.
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package whiteboard
dpkg-buildpackage: source version 0.3.4.2-0ubuntu1
dpkg-buildpackage: source changed by VAnhTu1987 <VAnhTu1987@gmail.com>
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp 
# Add here commands to clean up after the build process.
#/usr/bin/make clean
dh_clean 
 debian/rules build
dh_testdir
cmake .. -DCMAKE_INSTALL_PREFIX=/usr
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- checking for module 'gtkmm-2.4'
--   found gtkmm-2.4, version 2.14.1
-- checking for module 'libglademm-2.4'
--   found libglademm-2.4, version 2.6.6
-- Configuring done
-- Generating done
-- Build files have been written to: /home/snille/linux-whiteboard-read-only/build
dh_testdir
# Add here commands to compile the package.
/usr/bin/make -j2
make[1]: Entering directory `/home/snille/linux-whiteboard-read-only/build'
make[2]: Entering directory `/home/snille/linux-whiteboard-read-only/build'
make[3]: Entering directory `/home/snille/linux-whiteboard-read-only/build'
make[3]: Entering directory `/home/snille/linux-whiteboard-read-only/build'
Scanning dependencies of target translations
make[3]: Leaving directory `/home/snille/linux-whiteboard-read-only/build'
Scanning dependencies of target whiteboard
make[3]: Entering directory `/home/snille/linux-whiteboard-read-only/build'
make[3]: *** No rule to make target `../ALL', needed by `ALL.gmo'.  Stop.
make[3]: Leaving directory `/home/snille/linux-whiteboard-read-only/build'
make[2]: *** [CMakeFiles/translations.dir/all] Error 2
make[2]: *** Waiting for unfinished jobs....
make[3]: Leaving directory `/home/snille/linux-whiteboard-read-only/build'
make[3]: Entering directory `/home/snille/linux-whiteboard-read-only/build'
[ 10%] [ 10%] Building CXX object src/CMakeFiles/whiteboard.dir/common.cpp.o
Building CXX object src/CMakeFiles/whiteboard.dir/main.cpp.o
[ 15%] Building CXX object src/CMakeFiles/whiteboard.dir/auxiliary.cpp.o
[ 21%] Building CXX object src/CMakeFiles/whiteboard.dir/events.cpp.o
[ 26%] Building CXX object src/CMakeFiles/whiteboard.dir/ConfigFileParser.cpp.o
[ 31%] Building CXX object src/CMakeFiles/whiteboard.dir/configurator.cpp.o
[ 36%] Building CXX object src/CMakeFiles/whiteboard.dir/irfilter.cpp.o
[ 42%] Building CXX object src/CMakeFiles/whiteboard.dir/calibration.cpp.o
[ 47%] Building CXX object src/CMakeFiles/whiteboard.dir/wiicontrol.cpp.o
/home/snille/linux-whiteboard-read-only/src/wiicontrol.cpp: In function &#8216;cwiid_wiimote_t* wii_connect(char*)&#8217;:
/home/snille/linux-whiteboard-read-only/src/wiicontrol.cpp:45: warning: taking address of temporary
[ 52%] Building CXX object src/CMakeFiles/whiteboard.dir/wiicursor.cpp.o
[ 57%] Building CXX object src/CMakeFiles/whiteboard.dir/gtk-gui.cpp.o
[ 63%] Building CXX object src/CMakeFiles/whiteboard.dir/wiicursormanager.cpp.o
Linking CXX executable ../bin/whiteboard
make[3]: Leaving directory `/home/snille/linux-whiteboard-read-only/build'
[ 63%] Built target whiteboard
make[2]: Leaving directory `/home/snille/linux-whiteboard-read-only/build'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/snille/linux-whiteboard-read-only/build'
make: *** [build-stamp] Error 2
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
snille@edge:~/linux-whiteboard-read-only/build$

```

Any ideas?

As I stated before, I'm not familiar with the whiteboard, but looking at your log.....Have you installed the package called: build-essential ?...

```
sudo apt-get install build-essential
```

I'm really not sure if the whiteboard is working on Intrepid 64...I'm sorry. But you might want to check if you have that package installed. Report back if it worked :)!

---

### Post by Snille on 2009-01-10
Hi again,
I read in the thread that you where not "in" to the whiteboard things... :)
Thank you for your replay anyway, and yes I had/have the essentials packet installed and also the "cmake" packet that is needed for the "make-deb.sh" to get as far as it gets. How ever I noticed that I get the same error on my 32bit machine. So maybe it's something else that's broke?

On the 32bit machine however the .deb worked without problems anyway. So the software works. :)

Just wanted to check if someone knew some trix... :)

---

### Post by Meson on 2009-01-10
Does anyone know if a configuration file can specify multiple buttons, like KEY_CTRL+KEY_UP or KEY_CTRL,KEY_UP

---

### Post by Toshibawarrior on 2009-01-10
> **Meson said:**
> Does anyone know if a configuration file can specify multiple buttons, like KEY_CTRL+KEY_UP or KEY_CTRL,KEY_UP

As far as I've tested no...Only XWii does that...I haven't been able to test XWii because it gives me a 1,000 errors...ugh! I need to go deeper into the process of compiling it...

Anyways, it is the only way to sync multiple buttons to a single wiimote button. As I said, it also let's you launch programs and scripts...Check it out! ;)!

---

### Post by vulcanfk on 2009-01-14
Thanks for this howto.

I have the WiiMote up and working, and the Classic Controller working also.  Is there a way to map the analog joysticks on the classic controller?  Even digitally?

Thanks.

---

### Post by Rhubarb on 2009-01-15
> **vulcanfk said:**
> Thanks for this howto.

I have the WiiMote up and working, and the Classic Controller working also.  Is there a way to map the analog joysticks on the classic controller?  Even digitally?

Thanks.

I'm really sleepy at the moment, so I won't say much, as it may just be wrong or misleading.

But from memory it is possible to map one of the analog joysticks to be a mouse / standard joystick.
It may be possible to map the other to be similar to a D pad I think.

I'll add this to the list of things to try out with my wiimote + classic controller this weekend (I'm trying out XWii in 8.10 too).

Keep your eyes on this thread vulcanfk ;)

---

### Post by Maheriano on 2009-01-15
2 more questions from me:

1. Will this work with programs running in WINE? More specifically, Day Of Defeat from Steam which runs on the Halflife 2 engine.
2. Can I map the joystick on the nunchuck to work like the left, right, up, down keys on the keyboard?

---

### Post by vulcanfk on 2009-01-15
> **Rhubarb said:**
> I'm really sleepy at the moment, so I won't say much, as it may just be wrong or misleading.

But from memory it is possible to map one of the analog joysticks to be a mouse / standard joystick.
It may be possible to map the other to be similar to a D pad I think.

I'll add this to the list of things to try out with my wiimote + classic controller this weekend (I'm trying out XWii in 8.10 too).

Keep your eyes on this thread vulcanfk ;)

Thanks Rhubarb.  I'll also poke around some more and see if I can find anything.  I'm subscribed to this thread so I don't miss any updates ;)

---

### Post by Maheriano on 2009-01-16
I just installed 64 bit 8.1 on a new hard drive and had to set this up again....with a problem. I type the infrared command into the Terminal and it connects, then my Wiimote works as an infrared mouse perfectly. Then it exits for some reason 5 seconds later and I have to do it again. It won't stay connected for more than 5 seconds. Here's the Terminal output:

> deemar@Chugger:~$ sudo wminput -c ir_ptr 00:17:AB:23:A3:49
Put Wiimote in discoverable mode now (press 1+2)...
Ready.
Exiting.
deemar@Chugger:~$ 

---

### Post by Maheriano on 2009-01-16
> **Maheriano said:**
> I just installed 64 bit 8.1 on a new hard drive and had to set this up again....with a problem. I type the infrared command into the Terminal and it connects, then my Wiimote works as an infrared mouse perfectly. Then it exits for some reason 5 seconds later and I have to do it again. It won't stay connected for more than 5 seconds. Here's the Terminal output:

Nevermind, the batteries got weak from not turning the Wiimote off between uses. Should add that to the troubleshooting guide.

---

### Post by xjgnsdof on 2009-01-17
This guide didn't work for me. I press 1+2, but wminput doesn't recognize the Wiimote. I'm not reinstalling Intrepid from scratch just for this; in Hardy, it worked.

---

### Post by Toshibawarrior on 2009-01-17
> **elgilicious said:**
> This guide didn't work for me. I press 1+2, but wminput doesn't recognize the Wiimote. I'm not reinstalling Intrepid from scratch just for this; in Hardy, it worked.

If you upgraded from Hardy forget about it...98% of Hardy->Intrepid upgrades end up in wiimote disaster...

You could check two things:

1. Go to Synaptic and search for **libbluetooth** if you have versions 2 and 3 (most probably) uninstall both and reinstall **libbluetooth3** only...

2. Double-check your wiimote's bluetooth address and make SURE you're root when using wminput commands...

Report back!

---

### Post by xjgnsdof on 2009-01-17
I'll accept that an upgrade sometimes leads to functions being left behind, but there has to be a way to reverse it. I hope somebody finds out how, especially given that many of us upgrade rather than clean install.

---

### Post by Toshibawarrior on 2009-01-17
> **elgilicious said:**
> I'll accept that an upgrade sometimes leads to functions being left behind, but there has to be a way to reverse it. I hope somebody finds out how, especially given that many of us upgrade rather than clean install.

Well, did you try what I told you?...

I've been wiimoting in ubuntu for months now and everytime I see/hear someone upgrade 9specially from Hardy to Intrepid) the wiimote's libraries go berserk and problems start arising everywhere...sad but true...

If the **libbluetooth3** is not your problem you might need to interact with intrinsic x.org files and that won't be pretty. Remember that Intrepid's X.org is different than the one on Hardy, so many input devices need to be configured differently...including wiimotes sometimes...

:(

---

### Post by xjgnsdof on 2009-01-17
I did all of that, and none of it worked. All Intrepid upgraders should file a bug report.

---

### Post by wizgrav on 2009-01-18
Hello, I recently wrote a python script for IWBs based on Lee's concept.
[[COLOR="SandyBrown"]Source, win32 exe, a deb and docs are here [/COLOR]]("http://code.google.com/p/infrael/downloads/list"). Please post your feedback.
I haven't really tested on MacOSX so if anyone dual boots I'd be grateful.

---

### Post by R2D2! on 2009-01-19
Is &#305;t poss&#305;ble to g&#305;ve a command that when I tw&#305;st the Wiimote, the screen changes (xrandr -o left, right, etc), l&#305;ke &#305;n an iPod?

—Ilhu&#305;temoc &#948;

---

### Post by Toshibawarrior on 2009-01-20
That would be awesome! But sadly not possible as far as I know of...

As far as I've read/seen accelerometer/IR tracking/movement is only for mouse cursor movement, I haven't seen any way to link commands to movements...

I'll keep you posted if I find anything. :popcorn:

---

### Post by bioshake on 2009-01-21
Hey guys - I keep reading that its possible to get the  wiimote working as a joystick (for say emulator programs such as GFCE UltraX).

But I'm at a loss as to where you make that happen in any of these guides.

I have no problems getting the bluetooth adapter address and getting the wiimote working in the gui tool as well..

Anyone have a step by step guide to getting the wiimote working as a joystick?

Thanks.

---

### Post by Rhubarb on 2009-01-21
> **bioshake said:**
> ...Anyone have a step by step guide to getting the wiimote working as a joystick?
I didn't get around to doing some wiimote research last weekend. - Where I was going to post about this.

As the upcoming weekend is longer for me than most weekends, I should have some more time to play around with my wiimote, and note my discoveries.

I have gotten it to work as a joystick before, and from memory it wasn't too hard to get going.

For now, you may learn how to do it from reading through this thread:-
[http://ubuntuforums.org/showthread.php?p=5232024](http://ubuntuforums.org/showthread.php?p=5232024)
- There's a lot of pages there, and a lot to wade through, and you'll need to experiment as well.
... Or you can just wait a week, and I'll hopefully have the answers you seek.

- Rhubarb.

---

### Post by bioshake on 2009-01-21
> **Rhubarb said:**
> I didn't get around to doing some wiimote research last weekend. - Where I was going to post about this.

As the upcoming weekend is longer for me than most weekends, I should have some more time to play around with my wiimote, and note my discoveries.

I have gotten it to work as a joystick before, and from memory it wasn't too hard to get going.

For now, you may learn how to do it from reading through this thread:-
[http://ubuntuforums.org/showthread.php?p=5232024](http://ubuntuforums.org/showthread.php?p=5232024)
- There's a lot of pages there, and a lot to wade through, and you'll need to experiment as well.
... Or you can just wait a week, and I'll hopefully have the answers you seek.

- Rhubarb.

Thanks.  I'll poke in and snif around as well as check back.

That was the guide I was following - all it says under the first section:

> 
Allow your Wii remote to be a keyboard / mouse / joystick:-
Unless you want to run sudo modprobe uinput every time you start Ubuntu, it's recommend you make it automatically run upon Ubuntu start up.
Code:

gksudo gedit /etc/modules

Add this line at the end of the file:
Code:

uinput

So the whole file should look exactly like this:
Code:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
uinput

You may restart your computer for the settings to take effect, or if you're impatient and want to play with your Wii remote now (without having to restart your computer) you can run this:
Code:

sudo modprobe uinput



I've done all that and I'm obviously missing something to make it work as an input  device other than a mouse.   Do I need to add the xorg.conf info as well?

---

### Post by Rhubarb on 2009-01-26
> **bioshake said:**
> ... I've done all that and I'm obviously missing something to make it work as an input  device other than a mouse.   Do I need to add the xorg.conf info as well?

Ok, I've just played around a little, and managed to get my wiimote working as a joystick quite easily.

Make up a file named:  /etc/cwiid/wminput/joystick
And put this into it:
```
#joystick

include joystick_buttons

Plugin.acc.X	= ABS_X
Plugin.acc.Y	= ABS_Y
```

Then make up another file named:  /etc/cwiid/wminput/joystick_buttons
And put this into it:
```
#joystick_buttons

Wiimote.A	= BTN_A
Wiimote.B	= BTN_B
Wiimote.Minus	= BTN_X
Wiimote.Plus	= BTN_Y
```

You can probably reference /etc/cwiid/wminput/gamepad too

The trick to getting your wiimote to appear as a joystick, and not just a keyboard / mouse, is to make sure you **don't** bind any mouse buttons to your wiimote.

I have discovered something rather odd, this worked fine in Ubuntu 8.04, but in Ubuntu 8.10 it seems binding keyboard buttons mostly doesn't work.
- I haven't researched this enough, it may well be because I use a dvorak keyboard layout rather than qwerty.

If you wish to test your wiimote working as a joystick, it's probably best to have nothing in your /etc/cwiid/wminput/joystick_buttons.

Once all setup, you can get your wiimote running as a joystick like so:
```
sudo wminput -c joystick 00:1F:32:95:EF:B0
```

The 00:1F:32:95:EF:B0 address is obtained by running lswm to obtain your wiimote address.


Now hopefully I have some time to test out XWii ... ;)

---

### Post by DarkN00b on 2009-01-28
First I'd like to say thanks for this tutorial. I had it working in less than 5 minutes. I have one minor question though...

I want to use my WiiMote with Boxee, but the accelerometer based cursor movement is a real pain in that environment. It works much better with the D-pad only. Is there a way for me to disable the accelerometers? 

Any help is as always greatly appreciated.

---

### Post by Rhubarb on 2009-01-28
> **DarkN00b said:**
> First I'd like to say thanks for this tutorial. I had it working in less than 5 minutes. I have one minor question though...

I want to use my WiiMote with Boxee, but the accelerometer based cursor movement is a real pain in that environment. It works much better with the D-pad only. Is there a way for me to disable the accelerometers? 

Any help is as always greatly appreciated.

Ok, it's really quite easy to disable the accelerometers, you just need to remove the following 2 lines from your /etc/cwiid/wminput/ir_ptr file:
```
Plugin.ir_ptr.X	= ABS_X
Plugin.ir_ptr.Y	= ABS_Y
```

If you want to use your D-Pad to control the mouse (if you haven't already got this working yet), I've quickly got this mostly working:
```
Wiimote.Dpad.X	= REL_X
Wiimote.Dpad.Y	= -REL_Y
```
It's really quite crap, but it's promising.
I do know somehow it's possible to adjust the scale, so rather than jumping only 1 pixel, it can jump 4 pixels at a time.
Also I'm not sure if it's possible to push + hold the D-Pad down to constantly move the cursor in your desired direction.
But it's a good start anyway, I know it's possible to do the scale thing, I just need to do a bit of a search on the net to find out the correct syntax for it.

Let me know if this works for you, and how you get on with it ;)
-Rhubarb

---

### Post by DarkN00b on 2009-01-28
> **Rhubarb said:**
> Ok, it's really quite easy to disable the accelerometers, you just need to remove the following 2 lines from your /etc/cwiid/wminput/ir_ptr file:
```
Plugin.ir_ptr.X	= ABS_X
Plugin.ir_ptr.Y	= ABS_Y
```

OK, that worked (mostly). I made the changes to ir_ptr and started wminput with ```
wminput -q -c ir_ptr NN:NN:NN:NN:NN:NN
```

The problem is that when I press the "A" button the cursor jumps to the middle of the screen and executes a left mouse button press. If I need to I can use Xmodmap to remap the "A" button to the Enter key.

[COLOR="Red"]EDIT: This was an easy fix. In my case all I needed to do was open /etc/cwiid/wminput/buttons and change the second line so it reads ```
Wiimote.A		= KEY_ENTER
```
Now everything works perfectly. Thanks a lot![/COLOR]

> **Rhubarb said:**
> If you want to use your D-Pad to control the mouse (if you haven't already got this working yet), I've quickly got this mostly working:
```
Wiimote.Dpad.X	= REL_X
Wiimote.Dpad.Y	= -REL_Y
```
It's really quite crap, but it's promising.
I do know somehow it's possible to adjust the scale, so rather than jumping only 1 pixel, it can jump 4 pixels at a time.
Also I'm not sure if it's possible to push + hold the D-Pad down to constantly move the cursor in your desired direction.
But it's a good start anyway, I know it's possible to do the scale thing, I just need to do a bit of a search on the net to find out the correct syntax for it.

Let me know if this works for you, and how you get on with it ;)
-Rhubarb

I don't want to use the D-pad to control the mouse in this situation. The keyboard arrow keys can be used for navigation in Boxee and the D-pad is great for that because it simulates perfectly the behaviour of a television remote.

I also have it set up so that no admin privileges are needed to connect, so no "gksudo".

Thanks for the reply!

---

### Post by meist3r on 2009-01-29
I don't know how useful this is to anybody but I had set up my Wiimote/Bluetooth just like in Hardy and couldn't get it to work despite several package purges etc. 

Then I played around with it and found a way to connect to my Wiimote anyway. Wminput and Wmgui wouldn't do the authorization for some reason so I had to employ a third party so to speak.

Simply start WMgui or WMinput and start the polling for your Wiimote (where you would get an error). While the Wiimote is blinking away and the program polling open another terminal and run:

```
sudo hcitool cc <MAC of Wiimote>
```

This does the trick for me and my Wiimote is then found correctly by wminput AND wmgui. I guess something in the app code for the two was screwed up so you have to make hcitool do the authentication/connection for you so the wminput/gui can then take over. I wish they'd work that out but so far this is my solution and the only one that works for me.

---

### Post by Rhubarb on 2009-01-30
Wow, that's quite a nice trick there meist3r.

May I ask if you're running Intrepid or Hardy there?
If you're running Intrepid, did you do a clean install, or did you upgrade from Hardy?

The reason why I'm asking is because it seems there are many problems with wiimote based applications in Intrepid if the system has been upgraded from Hardy.
- This is because of the libbluetooth package:-
Hardy comes with libbluetooth2
Intrepid comes with libbluetooth3
But when Intrepid has been upgraded from Hardy, it keeps libbluetooth2 rather than replacing it with libbluetooth3.

Perhaps the workaround you've found overcomes this problem.

Anyway, thanks for sharing this meist3r to all of us, much appreciated.
-Rhubarb

---

### Post by meist3r on 2009-01-30
I do actually run an 8.10 system upgraded from Hardy. Are there any accounts of people with fresh Ibex installs not havin these problems? I certainly know that on Hardy I didn't have to jump through any of these hoops.

Hope someone will get their Wiimote to work. I certainly did. I didn't even think about it again but then I came across Cave Story and wanted to play that with a gamepad (my dvorak keyboard has the keys in all the wrong places). Then I thought about wminput and after some hours of trying here I am. Still got some problems with the keymapping because of my layout but I can steer, jump, switch weapons and shoot. That's all I need directly on the gamepad.

I sure hope this will be fixed in Jaunty.

---

### Post by Toshibawarrior on 2009-01-30
As Rhubarb said (so did I) upgrades from Hardy to Intrepid end up in wiimote disaster...I'd say that 99.9% of upgrades break wiimote usage due to the libbluetooth issue.

I always recommend installing Ubuntus from scratch...you'll waste less time that way. 

You could fix ALL of your wiimote-problems by simply making a fresh install of Intrepid. I did and I'm 1005 problem free.

See ya around! :popcorn:

---

### Post by Jose Hevia on 2009-01-31
> **Toshibawarrior said:**
> As Rhubarb said (so did I) upgrades from Hardy to Intrepid end up in wiimote disaster...I'd say that 99.9% of upgrades break wiimote usage due to the libbluetooth issue.

I always recommend installing Ubuntus from scratch...you'll waste less time that way. 

You could fix ALL of your wiimote-problems by simply making a fresh install of Intrepid. I did and I'm 1005 problem free.

See ya around! :popcorn:

I installed intrepid from scratch on an acer one. It doesn't work without meist3r trick, it works with it.

I have another machine with updated intrepid, works with the trick, doesn't work without it.

And another machine with updated hardy works fine without the trick, same usb bluethooth dongle that with the other two.

---

### Post by magicman5421 on 2009-02-08
Hey I have a problem
Everything works up until installing the whiteboard. I am able to download the source through svn, and cd into the newly created directory, but when i run ./autogen.sh it says "bash: ./autogen.sh: No such file or directory"
Where is this file?
By the way, I'm on 8.10 x86_64

---

### Post by Rhubarb on 2009-02-09
> **magicman5421 said:**
> Hey I have a problem
Everything works up until installing the whiteboard. I am able to download the source through svn, and cd into the newly created directory, but when i run ./autogen.sh it says "bash: ./autogen.sh: No such file or directory"
Where is this file?
By the way, I'm on 8.10 x86_64

From memory I didn't use autogen.sh when compiling the whiteboard.
Instead I used make and make install.
I'm not sure if I ran ./configure first.

So, I *think* I ran something like this:

CD into the directory
make sure you've got all the dependencies
```
./configure
make
sudo make install
```

I haven't confirmed this, so I could be quite wrong.
Also, I haven't tried with 64bit, but it should be ok at a guess.

---

### Post by jtsop on 2009-02-10
I managed to make this work but without the infrared it is unusable. Maybe there should be a comment on the first post that there are sensor bars available at most online shops? I found many of those at amazon and ebay.

---

### Post by Toshibawarrior on 2009-02-10
I think it could be possible to add that. I'm not going to advertise any shop in particular though...Thanks for the tip! It completely skipped my mind.

@ Rhubarb: Thanks for helping me out here. When it comes down to compiling I'm as lost a Gilligan! :popcorn:

---

### Post by rsmallri on 2009-02-10
> **Toshibawarrior said:**
> You could fix ALL of your wiimote-problems by simply making a fresh install of Intrepid. I did and I'm 1005 problem free.I just wanted to say that I have a fresh i386 Intrepid installation (not upgraded from Hardy) and I am having issues with my wiimotes - the only way I can get them to sync is using meist3r's method.

---

### Post by Nickedynick on 2009-02-11
Hi, this may have been covered before in this thread but I seem to have a problem...

I had all of this set up perfectly on my desktop with Compiz effects assigned to buttons, IR working, etc. but after I did a fresh install the other day and tried it again the cursor doesn't want to move outside a certain boxed area. I assume there's some resolution issue with X or something like this, but I can't seem to fix it.

Any ideas?

EDIT: I've worked out that it's approximately a 916x674 box on my 1680x1050 screen...

---

### Post by grs on 2009-02-11
Just some questions about the light source.

I've never used the Wii or even managed to look at one, I'm not really a fan of consoles.
The remote seems reasonable priced to for me to give this project a go but I'm wondering about the light source needed for it, can the light bar for the Wii be bought separately and what sort of interface does it connect to a PC/laptop with?

---

### Post by rsmallri on 2009-02-11
There are stacks of them on ebay or you can easily make one yourself. All they are is a pair of IR LED clusters which the remote's camera senses - they have no intelligence in them. The connector is not standard however you can buy wireless or usb ones off ebay, or alternatively chop the connector off the end of the OEM one and put a USB connector on it.

---

### Post by meist3r on 2009-02-12
> **magicman5421 said:**
> Hey I have a problem
Everything works up until installing the whiteboard. I am able to download the source through svn, and cd into the newly created directory, but when i run ./autogen.sh it says "bash: ./autogen.sh: No such file or directory"
Where is this file?
By the way, I'm on 8.10 x86_64

Sounds to me like you didn't set execution permission on the file. Bash doesn't tell you it can't find the file it can't file the "executable" file. Run

```
sudo chmod +x autogen.sh
```

and then try again.

---

### Post by Maheriano on 2009-02-13
The wireless sensor bar I just bought takes 4 AA batteries, is this the standard for the ones everyone else has? I thought there were some that took 2 AA instead of 4. Almost makes me want to go buy another one. I don't want to have to use 4 in the sensor and then 2 in the Wiimote.

---

### Post by Rhubarb on 2009-02-13
> **Maheriano said:**
> The wireless sensor bar I just bought takes 4 AA batteries, is this the standard for the ones everyone else has? I thought there were some that took 2 AA instead of 4. Almost makes me want to go buy another one. I don't want to have to use 4 in the sensor and then 2 in the Wiimote.

Well, I made up my own IR LED, and attached only the 1 AAA battery.
It works fine, and you certainly don't need to have 2 IR LEDs to make it work - Just the one will do quite nicely.

---

### Post by jtsop on 2009-02-14
> You have to restart your computer for the settings to take effect.

There is no such need. You can just: 
      sudo modprobe uinput


PS: There are some usb sensor bars at ebay and they have the advantage that do not need batteries and also it shutdowns with the computer since it is usb powered ;)

---

### Post by jtsop on 2009-02-14
Here is a list of commands to run in a terminal in order to install all needed packages for wiimote and whiteboard in ubuntu 8.10. It creates to profiles multimedia and presentation. 
Multimedia is the default and has volume up/down/mute, next, previous. forward,backward, play/pause and
Presentation is for presentations it supports Slide show (F5), Stop (Esc), white (w) and volume. You can enable this by running :
sudo ln -fs /etc/cwiid/wminput/presentation /etc/cwiid/wminput/default

```

sudo su
wget -O /tmp/whiteboard_0.3.4.2-0ubuntu2automated_i386.deb http://linux-whiteboard.googlecode.com/files/whiteboard_0.3.4.2-0ubuntu2automated_i386.deb
apt-get install wminput wmgui lswm
apt-get install libgtkmm-2.4-1c2a libglademm-2.4-1c2a libcairomm-1.0-1 libglibmm-2.4-1c2a libpangomm-1.4-1
dpkg -i /tmp/whiteboard_0.3.4.2-0ubuntu2automated_i386.deb
rm /tmp/whiteboard_0.3.4.2-0ubuntu2automated_i386.deb
#lswm
grep uinput /etc/modules || echo uinput >> /etc/modules
modprobe uinput
file=/etc/cwiid/wminput/mmedia
echo "Wiimote.A       = BTN_LEFT" > $file
echo "Wiimote.B       = BTN_RIGHT" >> $file
echo "Wiimote.Up      = KEY_PREVIOUSSONG" >> $file
echo "Wiimote.Down    = KEY_NEXTSONG" >> $file
echo "Wiimote.Left    = KEY_BACK " >> $file
echo "Wiimote.Right   = KEY_FORWARD" >> $file
echo "Wiimote.Minus   = KEY_VOLUMEDOWN" >> $file
echo "Wiimote.Plus    = KEY_VOLUMEUP" >> $file
echo "Wiimote.Home    = KEY_MUTE" >> $file
echo "Wiimote.1       = KEY_PROG1" >> $file
echo "Wiimote.2       = KEY_PAUSE" >> $file
echo "Plugin.ir_ptr.X = ABS_X" >> $file
echo "Plugin.ir_ptr.Y = ABS_Y" >> $file
file=/etc/cwiid/wminput/presentation
echo "Wiimote.A       = BTN_LEFT" > $file
echo "Wiimote.B       = BTN_RIGHT" >> $file
echo "Wiimote.Up      = KEY_UP" >> $file
echo "Wiimote.Down    = KEY_DOWN" >> $file
echo "Wiimote.Left    = KEY_LEFT" >> $file
echo "Wiimote.Right   = KEY_RIGHT" >> $file
echo "Wiimote.Minus   = KEY_VOLUMEDOWN" >> $file
echo "Wiimote.Plus    = KEY_VOLUMEUP" >> $file
echo "Wiimote.Home    = KEY_ESC" >> $file
#echo "Wiimote.Home    = KEY_MUTE" >> $file
echo "Wiimote.1       = KEY_F5" >> $file
echo "Wiimote.2       = KEY_COMMA" >> $file
#echo "Wiimote.2       = KEY_DOT" >> $file
echo "Plugin.ir_ptr.X = ABS_X" >> $file
echo "Plugin.ir_ptr.Y = ABS_Y" >> $file
ln -fs /etc/cwiid/wminput/mmedia /etc/cwiid/wminput/default
echo "case \"\$1\" in" > /etc/init.d/wiimote
echo "  start)" >> /etc/init.d/wiimote
echo "        wminput -d &" >> /etc/init.d/wiimote
echo "        ;;" >> /etc/init.d/wiimote
echo "  stop)" >> /etc/init.d/wiimote
echo "	pkill wminput" >> /etc/init.d/wiimote
echo "	;;" >> /etc/init.d/wiimote
echo "esac" >> /etc/init.d/wiimote
chmod +x /etc/init.d/wiimote
update-rc.d wiimote defaults 99

```


Is automated and you dont need to do anything but press 1&2 on wiimote to start using it. It also enables it after each restart.




Depending on your favorite player you have to change shortcuts in order to work with it:

--Amarok
Amarok -> Settings -> Configure Shortcuts
Play/Pause -> Click Custom -> Click on Button -> Click on Alternate Shortcut Button -> Press Wii Button 2  (It should Add "Pause")
Seek Backward -> Click Custom -> Click on Button -> Click on Alternate Shortcut Button -> Press Wii Left Arrow  (It should Add "XF86Back")
Seek Forward -> Click Custom -> Click on Button -> Click on Alternate Shortcut Button -> Press Wii Right Arrow  (It should Add "XF86Forward")

--VLC
--some keys do not work :(
VLC -> Tools -> Preferences -> HotKeys
Next -> Click in Editbox -> Press Wii Down Arrow (It should Add "Media Next Track") -> Click Set
Previous -> Click in Editbox -> Press Wii Up Arrow (It should Add "Media Prev Track") -> Click Set
Click Save

---

### Post by Maheriano on 2009-02-14
I have a question. How hard is it to program the + and - buttons to slide between desktops?

---

### Post by jtsop on 2009-02-15
it is very easy change these lines and put the keys you want instead, then go to system settings, keyboard & mouse, Global shortcuts, Component: KWin and change shortcut for Walk through desktop list (and reverse).


echo "Wiimote.Left    = KEY_BACK " >> $file
echo "Wiimote.Right   = KEY_FORWARD" >> $file

---

### Post by eyeonus on 2009-02-17
Okay, so we have [a list of what can be bound to the WiiMote & accessories]("http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt"), is there somewhere where I can get a list of the names of the things that can be bound? (ex.: What is the name for the positive Y axis on the nunchuck joystick so that I can bind to it, as in "Nunchuck.JoyYPos = KEY_END" or similar.)

Is there a way to make an a button, etc., auto repeat, so that if I held it whatever it was bound to would continue to be "pressed"?

Is there some way to make it so that pressing a button/button combination will "switch modes", so that multiple bind configurations can be switched between via keyboard and/or WiiMote?

Is it possible to bind a key combo to a single button, as in "alt+tab" and "alt+shift+tab"?

Could the answers to these questions please be included as an edit to the top post so that it will be easier for people to find? (I honestly don't know if any of these questions have been asked or answered already- after looking through 19 pages of the "HOWTO: Wii remote in Ubuntu 8.04" thread and 3 of this one I got tired of all the reading.)

---

### Post by Toshibawarrior on 2009-02-17
> **eyeonus said:**
> Okay, so we have [a list of what can be bound to the WiiMote & accessories]("http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt"), is there somewhere where I can get a list of the names of the things that can be bound? (ex.: What is the name for the positive Y axis on the nunchuck joystick so that I can bind to it, as in "Nunchuck.JoyYPos = KEY_END" or similar.)


Right now the Nunchuk's joystick is not usable in CWiiD...There are other apps to use it though, but I've never used them. Maybe someone has and is willing to share his/her experiences(?)

> 
Is there a way to make an a button, etc., auto repeat, so that if I held it whatever it was bound to would continue to be "pressed"?

I'll have to look into it since I really haven't had a need for it.

> 
Is there some way to make it so that pressing a button/button combination will "switch modes", so that multiple bind configurations can be switched between via keyboard and/or WiiMote?


I remember someone saying something about this, but I really can't remember where...

> 
Is it possible to bind a key combo to a single button, as in "alt+tab" and "alt+shift+tab"?


Right now CWiiD is not able to do it, XWii does, but as of this moment I believe XWii is useless in Intrepid Ibex...I've tried to compile it multiple times and I get tons of errors and bugs...I'll let you know if this changes.

> 
Could the answers to these questions please be included as an edit to the top post so that it will be easier for people to find? (I honestly don't know if any of these questions have been asked or answered already- after looking through 19 pages of the "HOWTO: Wii remote in Ubuntu 8.04" thread and 3 of this one I got tired of all the reading.)

Yes they can be added to the HOWTO, as Tips. I'm sorry about my lacking answers, but right now I'm exhausted. I worked all day on a shoe store fixing shows and purses and then I went to church...so now I'm seeing double...lol! I'll try to look further into these issues and then add them to the Tips section.

Keep checking back here on this HOWTO for updates!

:popcorn:

---

### Post by planemanx15 on 2009-02-23
First off, thanks for the howto, It is really great.

I used it back in 8.04 and this work great.  I performed a fresh build on my Toshiba (same laptop as Toshibawarrior lol) but this doesnt work.  I can see the wiimote with lswm but when I try to connect with  gksudo wminput 00:1B:7A:16:DE:11 I fail to connect, same issue with Wmgui.  

Is there a fix yet? How about a second program? I would like to use this with XBMC but need to have it work first.  I tried but my wiimote (changing the MAC addresses of course) but nothing.  I haven't tried buying another bluetooth dongle yet, just wanted to check in for any updates

---

### Post by Toshibawarrior on 2009-02-24
Well...my first advice is switching bluetooth dongles...Some dongles don't support wiimotes, but do support other pointing devices...very weird indeed.

When you say you made a *fresh build* you mean a fresh install of Intrepid?...If you did make a fresh install there's one way to go. If you upgraded from Hardy there's a whole other way to go.

Let me know if this helps and if you upgraded or not. Then maybe I can help you.;)

---

### Post by Danno2468 on 2009-03-05
Very Good how too! thanks alot, all my friends are impressed with the remotes:D

---

### Post by Toshibawarrior on 2009-03-06
Heh heh, you're welcome!

This thread has been a little slow lately, but I've been into things, and besides right now I'm in Kubuntu and I'm so lazy/busy that I haven't even tried to use the wiimote with KDE...

Anyway, keep posting! :popcorn:

---

### Post by Rohan Kapoor on 2009-03-13
I personally have been able to use my Wii-Remote thanks to this guide but have had issues using it with gksudo. I found out a way to make it so that the sudo command is not needed to run the wiimote and it is able to be run by a normal user in the correct group.

I ran this command:

```
sudo sh -c 'echo "KERNEL==\"uinput\", GROUP=\"username\"" > /etc/udev/rules.d/50-cwiid-input.rules' /etc/init.d/udev restart
```

Replace username with username or groupname and it works then without sudo or gksudo!

---

### Post by kashell on 2009-04-08
Hi.

I'm trying to get my joysticks on the classic controller and nunchuck to work correctly.

I played around a little in the buttons config file and ended up with:

```
Nunchuk.Stick.X = ABS_X
Nunchuk.Stick.Y = -ABS_Y

Classic.LStick.X = ABS_X
Classic.LStick.Y = -ABS_Y
Classic.RStick.X = ABS_X
Classic.RStick.Y = -ABS_Y
```

The problem is, if I move the joystick it only moves from a fixed position on the screen and doesn't move very far. For example, the classic controller will automatically move to the top left of the screen and I can only move it a little bit (and after that it will snap back to the original position).

In addition, when I try to configure my controllers on any emulator, it is unable to register the joystick data.

I tested it in wmgui and both the classic controller and nunchuck seem to work fine, although if I have the IR data turned on it will make them go nutty.

Any ideas?

---

### Post by hebeallrusty on 2009-04-09
on the upgrade to Jaunty, I had to ```
sudo chmod 0660 /dev/input/uinput
``` to get wminput running as user as well as darth-vaders udev rule

---

### Post by Toshibawarrior on 2009-04-09
Sorry guys...I've been hit hard by real-life and I haven't been able to actually post here that often, nor have I tested anything wiimote-related...I'm very sorry.

I've been testing Kubuntu jaunty and due to some absolutely necessary reasons I had to reinstall Vista on my laptop...

I'll try to post back here if I find anything.:popcorn:

---

### Post by ub0fan on 2009-04-09
Hello all,I just wanted to introduce myself,I am new here and I hope to have a very nice time on this forum.

---

### Post by Toshibawarrior on 2009-04-09
Welcome ub0fan! We hope you have a very nice time here too! Remember that we're here to help, and be helped! See you around! :popcorn:

---

### Post by kashell on 2009-04-09
On a side note Toshiba, you may want to update the original thread with a suggestion to use

```
sudo wminput -d -c ir_ptr 00:1F:32:A0:1E:16
```

if

```
gksudo wminput -d -c ir_ptr 00:1F:32:A0:1E:16
```

doesn't work correctly. This is what I had to do in order to correctly connect the Wiimote.

Since sudo doesn't prompt for the password, I simply hit the shortcut for gksudo killall wminput first, which prompts for the password. From there I click sudo wminput -d -c ir_ptr and it works like a gem.

I wonder: Is there a way to put two commands together on a shortcut on the panel? I tried using (command1&);(command2&) as suggested [here]("http://ubuntuforums.org/showthread.php?t=531589") but that didn't work.
Despite this being more convenient than the command line, I'd like to see an automatic way of connecting the wiimote, instead of having to manually click the command every time for each individual controller.

---

### Post by asg31 on 2009-04-11
ivee got 64 im noob i made already a pen but cant get bluetooth and software to work

[[IMG]http://img26.imageshack.us/img26/6415/screenshotkyr.th.png[/IMG]](http://img26.imageshack.us/my.php?image=screenshotkyr.png)

---

### Post by -nat- on 2009-04-12
> **asg31 said:**
> ivee got 64 im noob i made already a pen but cant get bluetooth and software to work

[[IMG]http://img26.imageshack.us/img26/6415/screenshotkyr.th.png[/IMG]](http://img26.imageshack.us/my.php?image=screenshotkyr.png)

Same thing happened to me, for (what I assume to be) the same reason.
It looks as if you are running "BlueProximity" which uses bluetooth non-stop. Try quiting BlueProximity (right click its icon in the taskbar and choose quit) and then run the whiteboard command/program again :)


P.S. Thanks for the tutorial Toshibawarrior! using the WiiRemote with games is heaps of fun! :-D

I do have a problem though...
One thing I can't seem to do is use the Guitar Hero:World Tour Wii guitar controller with my computer (for Frets on Fire :guitar:). I've tried a few different programs, but they either don't support Guitars at all, or only work with GH:3 ones. :(
Does anyone know if there's anyway to get it to work?

---

### Post by Toshibawarrior on 2009-04-12
> **-nat- said:**
> Same thing happened to me, for (what I assume to be) the same reason.
It looks as if you are running "BlueProximity" which uses bluetooth non-stop. Try quiting BlueProximity (right click its icon in the taskbar and choose quit) and then run the whiteboard command/program again :)

+1 great tip there! I believe it's happening for the same reason.


> P.S. Thanks for the tutorial Toshibawarrior! using the WiiRemote with games is heaps of fun! :-D

You're welcome!

> I do have a problem though...
One thing I can't seem to do is use the Guitar Hero:World Tour Wii guitar controller with my computer (for Frets on Fire :guitar:). I've tried a few different programs, but they either don't support Guitars at all, or only work with GH:3 ones. :(
Does anyone know if there's anyway to get it to work?
[/QUOTE]

Hmmm...I've never read of anyone using a GHWT Guitar...just GH3's...But then again, I don't own one...so I can't test it...I'm very sorry...:( Try searching the forums and see if someone found out anything...

---

### Post by paulflook on 2009-04-16
Hi all,
I have finally got my wiiremote to work brilliantly in ubuntu 8.10, with all buttons mapped to what i need, my only question is, when x11 changes resolutions the mouse cursor goes very sensitive,probably due to how x11 handles the scaling, is there anyway i can solve this? I'm a big scummvm fan and have to resort to playing in a small window to get the cursor to move right.

Any help would be greatly appreciated!

---

### Post by spaznrq on 2009-04-17
Hello!  Thank you for this great HOWTO post, which enabled me to get the entire thing working within less than 5 minutes, literally!  I remembered a year ago when I was trying to set the Wiimote to be used as a mouse through IR, and I tried for an entire day fruitlessly.

I've tried to scour the past posts on this thread for some more help on configuring the mouse, but haven't found the answers to these questions:

1) Holding a button.  When pressing and HOLDING the directional pad to be used as arrows, it doesn't actually repeatedly send the directional command continuously for me, i.e. holding the down on the d-pad to scroll down on a website only scrolls it one notch, but not all the way down.  Can this be fixed somehow?

2) Multi-button mapping.  I've already read that it is not possible with CWiid yet, but I'm just posting this here in case anyone is interested in using Gromit in combination with the Wiimote presentation mode together.  I'm using Gromit to draw things on my presentation (after configuring the mouse to be used in presentation mode).  I need to press "Pause" to start the drawing and "Shift+Pause" to clear the screen.  It was mentioned that Xwii can do it, but I don't want to venture there since my current setup is nearly perfect for me.  In anycase, I would like to know if I can do a "Shift+Pause" mapping with CWiid in the future.

3) Sensitivity.  I've figured that using this further away from the screen/IR bar helps with having a shaky cursor, but is there a way to configure this?  

I might have missed any posts that answer these questions... sorry if that happens.  But I am really excited about this and really love the work done here.  Thanks a lot!

---

### Post by Dritz on 2009-04-24
How can I get the wii remote LEDs to light up when connecting the remote with wminput? It shouldn't be hard to remember to turn wminput off when I'm not using it without a light to remind me but I can't seem to master this concept.

---

### Post by Danno2468 on 2009-05-08
I know it says for 8.10, but i am using 9.04.  Anyways I am trying to set up the 2 icons for the ir wiimote.  I have the sudo killall wminput comand working fine.  But the other command isn't how I would like.  Putting the gksudo doesn't let anything work.

sudo wminput -d -c ir_ptr 00:1F:32:9A:38:6D
I have to set the launcher to in terminal or it won't work.  It opens up a terminal window and works.  But that window stays open.  When it is closed the wii mote stops working.  What would i have to do to make it so that nothing opens it just works, and then when i hit the other button it stops it?

Also i was just wondering what do "-c" and "-d" do for the comand?

---

### Post by slaeyer on 2009-05-28
> **Danno2468 said:**
> I know it says for 8.10, but i am using 9.04.  Anyways I am trying to set up the 2 icons for the ir wiimote.  I have the sudo killall wminput comand working fine.  But the other command isn't how I would like.  Putting the gksudo doesn't let anything work.

Been lurking here for a day, reading the posts when I found one I thought I could answer.

Just a thought, but try putting the entire command after gksudo in quote marks "", i.e.  gksudo "wminput -d -c ir_ptr <your wiimote's bluetooth address here>"

I've noticed myself when running gksudo commands using alt-f2 that any command operations tend to be incorrectly sent to gksudo rather than program blahblah.  Placing the entire command inside quotes allows it to be sent through gksudo properly in my experience.

---

### Post by greyfox1 on 2009-05-30
slaeyer, you're a lifesaver.  When running ```
gksudo wminput -c ir_ptr <address>
``` in Terminal, I was getting a response of:

```
gksudo: invalid option -- 'c'
```

Putting quotes around everything after gksudo did the trick and I'm up and running now in IR mode (or at least the command worked properly, I haven't set up an IR sensor yet).

Thanks!

P.S. I'm using Jaunty, FWIW.

---

### Post by Contrast on 2009-06-02
Has anyone here been able to run wminput as a user rather than root in Jaunty? I use the Wiimote for controlling my media center and it's kind of a pain to have to put in my password every time I open and close XBMC.

---

### Post by Meson on 2009-06-02
> **Contrast said:**
> Has anyone here been able to run wminput as a user rather than root in Jaunty? I use the Wiimote for controlling my media center and it's kind of a pain to have to put in my password every time I open and close XBMC.

Make sure uinput is in /etc/modules

check out the wminput man page for what to put in /etc/udev/rules.d

---

### Post by Gusk on 2009-06-09
Woah! this thing rocks!
Thanks ToshibaWarrior!

Now I'm looking for a list of all usable buttons, axes, etc. from wiimotes/extensions and respective modifications you can do to them, but it seems there's nothing like it on the CWiid's website or anywhere else. What I mean by modifications can be something like, for example, I've been trying to use the wiimote's Y accelerometer to simulate a wheel to use it with Mario Kart 64 inside Mupen64Plus, but I want to limit it's range, or change its sensitivity, etc.

I actually managed to kind of do so by using a piece of code I found inside the "neverball" file inside /etc/cwiid/wminput, which looks like this:

Plugin.acc.Pitch = -ABS_Y
Plugin.acc.Pitch_Scale = 2.0

But that's way too limited; there must be something else I could apply to this to make it more malleable/usable hhmm...
You have to tilt the wiimote way too much to get response, regardless of the value. It isn't as smooth as I'd like it to work. I tried changing the Pitch_Scale value, but that doesn't really help.

Any help would be appreciated
Thanks!

BTW, my first post! :D

---

### Post by bkbilly on 2009-06-12
The problem I have has already been posted here but there was no answer...
I am using ubuntu 8.10 64 bit and I can't install the **Whiteboard**
when i type this command: svn checkout **http://linux-whiteboard.googlecode.com/svn/branches/cpp/ linux-whiteboard-read-only** it downloads me a folder
when I continue typing the commands and go to **./autogen.sh** it shows me
> bash: ./autogen.sh: No such file or directoryIf I ignore it it says to the **make** command this:
> make: *** No targets specified and no makefile found.  Stop.If I ignore and that one and type the **make** **install** it shows me:
> make: *** No rule to make target `install'.  Stop.When I open the folder that it has downloaded, there isn't the file **autogen.sh** neither any **config** file

Is there a chance that it didn't download the correct file?
[SIZE=3][COLOR=Red]**can somebody help me?:popcorn:**[/COLOR][/SIZE]

---

### Post by nmjcman101 on 2009-06-14
Hey guys, I read through the whole thread, and was going to try and get things like openarena working with the nunchuck joystick mapped to WASD, and I DID find a plugin for it, but can't figure out how to get it to compile.
[http://dodekane.free.fr/index.php?post/2008/08/15/Wiimote-with-FPS-TCE-under-Linux](http://dodekane.free.fr/index.php?post/2008/08/15/Wiimote-with-FPS-TCE-under-Linux)
(plugin package)
but after placing into the cwiid-0.6.00/wminput/plugins directory I can't compile cwiid with the error:
```
douglas@douglas-laptop:~/Desktop/Wii/cwiid-0.6.00$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for gawk... no
checking for mawk... mawk
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... -lfl
checking whether yytext is a pointer... yes
checking for bison... bison -y
checking for python... python
checking for pthread_create in -lpthread... yes
checking for hci_devid in -lbluetooth... no
configure: error: bluetooth library not found
```I would really like to get openarena working with this, any ideas?

EDIT: Sorry, didn't realize how old this thread was.

---

### Post by R2D2! on 2009-06-14
Do you have libbluetooth3 and libbluetooth-dev packages installed?

This, however, has nothing to do with the new plugin. You need to compile before you add the plugin.

—Ilhu&#305;temoc &#948;

---

### Post by Rhubarb on 2009-06-15
> **nmjcman101 said:**
> Hey guys, I read through the whole thread, and was going to try and get things like openarena working with the nunchuck joystick mapped to WASD, and I DID find a plugin for it, but can't figure out how to get it to compile.
[http://dodekane.free.fr/index.php?post/2008/08/15/Wiimote-with-FPS-TCE-under-Linux](http://dodekane.free.fr/index.php?post/2008/08/15/Wiimote-with-FPS-TCE-under-Linux)
(plugin package)
but after placing into the cwiid-0.6.00/wminput/plugins directory I can't compile cwiid with the error:
...
I would really like to get openarena working with this, any ideas?

EDIT: Sorry, didn't realize how old this thread was.

Hi there nmjcman101, I did manage to compile that last year in Ubuntu Hardy, it worked quite well.

As R2D2! has said, you need to install all the dev packages for bluetooth and cwiid, then compile it all.  From memory I did have to change a few bits in cwiid to recognise the new plugin before compiling it.
I could probably get it going in Ubuntu Jaunty with a few hours spare time - I'm not a programmer.

A better idea would be to try and get the plugin included with wminput by default upstream.  That way we could all benefit from it nicely.

Have fun!

PS, I still haven't attempted to get my wiimote + other controllers working with Jaunty yet, I've been too obsessed with contributing to [http://www.openstreetmap.org](http://www.openstreetmap.org) :P

---

### Post by Xero Xenith on 2009-06-25
Excellent! Wiimote working fine as a mouse in Linux Mint 7 (based off Jaunty). Only modification I made was that this returned an error:

```
chris@chris-desktop ~ $ gksudo wminput -c ir_ptr 00:19:1D:82:36:41
gksudo: invalid option -- 'c'
GKsu version 2.0.2

Usage: gksudo [-u <user>] [options] <command>

<snip>
```

...so I used quotes as so:

```
gksudo 'wminput -c ir_ptr 00:19:1D:82:36:41'

```

And that worked perfectly. Can't thank you enough :)

---

### Post by Toshibawarrior on 2009-06-25
You're welcome Xero, nice to know that people are still enjoying my guide! It's been a while since I last updated the guide and it's been months since I last used my wiimote as a mouse/remote...I've been busy with other things, but I'll jump back in here soon...[SIZE="1"]hopefully![/SIZE]

---

### Post by philcamlin on 2009-06-25
cool!!!!!!:popcorn:

---

### Post by Toshibawarrior on 2009-06-27
Well, last night I fiddled around with the wiimote and cwiid and I got it working with no problems on Jaunty...So I believe the Intrepid guide should remain the same for Jaunty.

I also got XWii working, and let me say the first word that came through my mind: "DAAAANG!". It's great and the profile switching capabilities are awesome! I even made a drum machine using Hydrogen and XWii; with some button mapping and getting used to the way of doing things that XWii has it becomes a great companion to any Linux-WiiMoter!

I may add the compiling steps for XWii later on to my guide. It doesn't conflict with CWiiD as long as they'r enot running at the same time. :popcorn:

---

### Post by Danno2468 on 2009-06-28
Thank you slaeyr! that did exactly what i wanted it to do!!!

---

### Post by zbeekman on 2009-07-05
So i didn't want to wade through all of the comments but I have  a few notes and suggestions for improvements.  First off these install instructions seem to work fine for jaunty as well as Ibex (i.e. 9.04).  Also I would ******HIGHLY****** recommend putting double quotes around the command you pass to gksudo.  For some reason if I use your commands as is gksudo complanes about -c not being a valid option.  Also, I have added a small piece of code which makes it so that your wii-mote's blue tooth address is automatically picked up and inserted.  This is what my wii-mote launching icon runs:

```
gksudo "wminput -d -c ir_ptr $(lswm)"
```

Also don't forget to hold buttons 1 & 2 while doing this!

It would appear that the only thing that lswm writes to std out is the hardware address so you can just use command substitution/shell expansion to get this address.  This is nice if you have multiple wiimotes, then you can just grab one and use it.

Hope people find this usefull.

---

### Post by Jeezus on 2009-07-13
I don't know if anyone has done so yet, but I just got the wiimote working in Ubuntu 8.10 64 bit. The only problem I had was that the AC kept blowing out one of my tea candles... :p I need to go get a wireless sensor bar...

---

### Post by Maheriano on 2009-07-15
> **Jeezus said:**
> I don't know if anyone has done so yet, but I just got the wiimote working in Ubuntu 8.10 64 bit. The only problem I had was that the AC kept blowing out one of my tea candles... :p I need to go get a wireless sensor bar...

I've had it going in 8.1 and 9.04.
And you don't want a wireless sensor bar, they go through batteries like a mofo unless you want to keep turning it on/off every time you want to use it. I bought a wireless one for $5 and ended up cutting up an old USB cable and soldering it to the battery terminals inside it to make it wired. That way it just sits on my computer and is always on.

---

### Post by Thalarse on 2009-07-25
I just got the wiimote working with 9.04, as a joystick using the neverball thing. It's great! But one thing I'm unsure of: How do I offset the axis so that I hold the wiimote vertically in the null position, rather than horizontally? I looked through this thread and tried my google-fu, but I couldn't find anything relevant. 


Also: Has anyone managed to get the wii motion plus thing working? I bought one for the wii, but I was wondering if it could be useful for more subtle input on a pc.

---

### Post by Maheriano on 2009-08-04
I use gksudo but it still asks me for the password when I run it. Is there another way to make it stop asking for the password? I use BlueProximity to fire the command when I turn on the remote so I don't want to have to use a keyboard to put the password in.

---

### Post by Jexel on 2009-08-17
Hi guys, has anyone been able to bind the wiimote to the keyboard? For some reason I can't seem to bind any of the buttons to the keyboard, only mouse.

---

### Post by Jeahavee on 2009-09-06
:( WOW 21 pages. Maybe it was asked, but I have it working as an ACC mouse but I want to change the button to do custom task like Play/Pause Mouse Scroll up/down Volume up/down.

gksudo gedit /etc/cwiid/wminput/buttons

I see all the BTN_Left and right

AND

[http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt](http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt)

I see all the commands I hope

How do I change it so that it works so far changing them hasn't done a thing? (Please show me)

It would be nice to turn off the acc and ir and just use the buttons. how would I alter my command? (Please show me)

Would I need to make 2 command for each Wiimote?

---

### Post by Jeahavee on 2009-09-06
OKAy so changing the WII mote things also changes the MOUSE things... somehow

How do I make it so I can use it as a remote not a mouse?

---

### Post by Cardcaptor Stacey on 2009-09-09
I've got a bluetooth adapter and the Wiimote works, but I would like to use it as a mouse. If I bought a wireless sensor bar, would it work?

---

### Post by Rohan Kapoor on 2009-09-12
It would work, yes.

---

### Post by d0b33 on 2009-10-30
Thanks for this, got my wii remote working with karmic but can I configure it to work with mythtv?

---

### Post by BeastlyKings on 2009-11-03
I would also like to know how to turn off the IR and ACC functions and run the wiimote as a remote using the buttons only. I'm using it for mythtv and I want to save battery power because I don't NEED the mouse function.


@d0b33
Yes it can very easily be made to work with Mythtv, thats how I use it, when I get home I will show you my configuration file so you can copy it and change it to your needs.
The problem comes in that the wiimote only has 11 buttons, and to get full functionality you need a lot more than that. For live tv you need about 19 to get full functionality, but I've found I'm quite satisfied with the 11 I've selected, I seldom need any more, but I keep a wireless keyboard nearby just in case.
The basic button layout I've chosen for live tv, as far as I can remember seeing how as I don't have it in my hand atm, is this:

B = Go Back
A = Select
UP/DOWN/LEFT/RIGHT = Navigation
Minus button = Volume Down
Plus button = Volume up
Home button = Mute
1 = Play/Pause
2 = Menu


I'll get that config file to you asap.



@Maheriano
You don't need to set it up that way, you don't need BlueProximity to start your wiimote.
What you want to do is turn all of that BlueProximity stuff off, and just change your command from ```
gksudo "wminput -c ir_ptr <your wiimote's bluetooth address>"
``` to ```
gksudo "wminput -d -c ir_ptr <your wiimote's bluetooth address>"
```

Or better yet, the way I do it, I fire it from the command line everytime so I don't use the app launcher buttons or the gksu command, it always gives me problems, so I do this for both my remotes ```
sudo wminput -d -c ir_ptr <your wiimote's bluetooth address>
```

Either way you do it, by using the "-d" option you make it so that once wminput is started the wiimotes will automatically resync. So now you can turn them off by holding the power button for a second or two, and resync them by pressing the  1 and 2 button at the same time.



Hope this helps!
-BK

---

### Post by BeastlyKings on 2009-11-03
@d0b33
This is how I have set mine up, hope it helps!
```
Wiimote.A               = KEY_ENTER
Wiimote.B               = KEY_ESC
Wiimote.Up              = KEY_UP
Wiimote.Down    = KEY_DOWN
Wiimote.Left    = KEY_LEFT
Wiimote.Right   = KEY_RIGHT
Wiimote.Minus   = KEY_VOLUMEDOWN
Wiimote.Plus    = KEY_VOLUMEUP
Wiimote.Home    = KEY_BACKSLASH
Wiimote.1               = KEY_P
Wiimote.2               = KEY_M
```

---

### Post by Rhubarb on 2009-11-03
I wonder if there's any difference for getting wiimotes to work in Karmic?

I guess there's only one way to find out :D

---

### Post by HighFrictionZone on 2009-11-07
Somewhat related, I have it working, but I was curious if it was possible to map the up/down/left/right on the right analog stick on the classic controller to keyboard buttons. Can it be done?
Edit: Nevermind, it cannot. Doesn't matter though, I solved the problem I was trying to work around. In the default configs, it is set up as a HAT but that doesn't make sense so I configured the X and Y axis on the right stick to refer to RX and RY. Problem solved. New issue though, can I set something in the config to make the LEDs at least blink? If not, no problem.

---

### Post by NotKeith on 2009-11-15
> **Rhubarb said:**
> I wonder if there's any difference for getting wiimotes to work in Karmic?

I guess there's only one way to find out :D

Just upgraded and tried it out, so far, so good.

---

### Post by Cal27 on 2009-11-28
Great tutorial, but I want to use the thumbstick on the nunchuk as the mouse. I've tried several different bindings but none have worked so far. Has anyone else had success with this?

---

### Post by R2D2! on 2009-12-22
> **Cal27 said:**
> Great tutorial, but I want to use the thumbstick on the nunchuk as the mouse. I've tried several different bindings but none have worked so far. Has anyone else had success with this?

See [this plugin]("http://abstrakraft.org/cwiid/ticket/87"). You have to apply the patch and rebuild the source.

—Ilhu&#305;temoc

---

### Post by greyfox1 on 2009-12-23
For anyone having issues getting wminput to run without root privileges (i.e. gksudo), I got this working in Karmic by doing the following after confirming that it worked using gksudo once I had followed this tutorial:

1. I created the file: /etc/udev/rules.d/80-wminput.rules. This file contains only the text:
```
KERNEL=="uinput", MODE="0666"
```

2. At this point, I confirmed that I could get my wiimote working without root privileges by opening a Terminal and issuing the command:

```
wminput -c ir_ptr [wiimote MAC address]
```


3. Once I knew I could get this working without root privileges, I went to System->Preferences->Startup Applications and created a new item with the command I confirmed was working in Terminal in step 2 above. Wminput now starts when I log in, which is perfect since I use XBMC on this particular machine, which also starts up when I log in. The only tricky part is I have to press 1+2 on the wiimote at the right time during login, or else wminput won't grab it.

NOTE: There are various instructions out there that recommend configuring the file in step 1 by user group rather than by mode 0666. I tried and tried but couldn't get it working using the group method. Try this at your own risk as the "mode" method is slightly less secure, but at least it works. HTH!

---

### Post by jorrieboy on 2009-12-26
I have a question about this...

Is there a way i can use the nunchuck "thumbstick" as a joystick or the left/right/up/down buttons?

And is it possible to set a shortcut to a button (like: super + space, control + alt + right-key, alt + tab, ect.)?

(sorry if my English is not so good)

---

### Post by bapoumba on 2009-12-26
Moved to Tutorials & Tips.

---

### Post by BinaryMn on 2009-12-27
I currently have one Wiimote controlling my HTPC as a mouse using IR. My HTPC is just a desktop that I built from boneyard parts running Jaunty and a 160GB hard drive with all of my DVDs ripped to ISO images on a 1TB external hard drive. I just use nautilus to browse the hard drive and then use VLC to load the ISO and play back the movies. When MythTV bumps up to .23 so MythVideo supports ISO DVD playback, I'll switch to using MythTV (might even have something better than an impressive POS desktop for a HTPC).

Anyway, this is my problem. There are times where using the accelerometer is preferable over the IR input. I set up an init.d script that runs wminput in daemon mode at boot right after the bluetooth loads. Is there a way, or what is the best way to set up some kind of way to either switch between IR and accelerometer without having to physically go to the computer? Something I was thinking about is making wminput recognize the Wiimote as a second controller some how on command, so it loads an entire different button and mouse control layout. Mind you, switching between IR and accelerometer inputs or controller settings from the wiimote is required.

---

### Post by Ubuntiac on 2010-01-11
Has anyone tried the IR part of this guide on Lucid yet? Does it work?

---

### Post by Statik on 2010-01-26
I just tried this tutorial. Works great for the wmgui, everything recognized. Tried the whiteboard portion and, like everyone else, I did not get an autogen.sh file in the svn checkout. Not sure why, but there isn't one available, nor can you ./configure or make.

Anyone have a solution yet?

Statik

---

### Post by bodusb on 2010-02-07
On Kubuntu 9.10, works fine...

---

### Post by tjk on 2010-02-09
error please ignore this message...

---

### Post by nenico on 2010-02-24
hi, i have tried to get all butons, axis as gamepad and ir pointer as mouse pointer working together and have no succes. can anyone help me?
here is my actual config file:
```
http://pastebin.com/tYyPUr8v
```

---

### Post by Tinfoilpain on 2010-11-04
I know that this is quite an old forum, but I was wondering what were the specific key symbols "KEY_" Next song and previous song. Also Play/pause Any help would be useful because I cant seem to get them to work

---

### Post by emoguitarist06 on 2010-11-04
Has anyone figured out Xwii?

I'm running Ubuntu 10.10 64bit and Xwii installed perfectly and the only option that works though is emulating the mouse but every other profile is not detected by any emulator I have, Mupen64Plus, Dolphin, Gens/gs, or PCSX

---

### Post by Mgiacchetti on 2010-11-24
So does anyone know how to connect this thing WITHOUT  the ir and accelerometer??

I WISH TO USE AS CONTROLLER FOR AN EMULATOR AND DON'T WANNA WASTE BATTERIES 


please just answer this ONE SIMPLE QUESTION.

---

### Post by anirudh215 on 2011-01-17
Do you know if I can run the whiteboard feature on Ubuntu 10.04?

---

### Post by antti64 on 2011-01-24
Hi!

I have been trying to use Wiimote as a mouse or joystick in Ubuntu 10.04. It seems doesn't to work. 

I have problems with modprobe and uinput. 

```
>>lswm
Put Wiimotes in discoverable mode now (press 1+2)...
00:22:4C:8D:FF:F7
>>wm2js -c 00:22:4C:8D:FF:F7
Searching Wiimotes ; press 1+2 or the red SYNC button...
Connection established! 0x7fffc4026df0
Warning: Unable to open uinput device ; hint: 'modprobe uinput' ?!
Error: Registering the uinput device failed, aborting!
```

modprobe uinput doesn't help. wmgui and lswm works fine.

Has anyone managed to fix this in Ubuntu 10.04?

Antti

---

### Post by antti64 on 2011-01-24
> **greyfox1 said:**
> For anyone having issues getting wminput to run without root privileges (i.e. gksudo), I got this working in Karmic by doing the following after confirming that it worked using gksudo once I had followed this tutorial:

1. I created the file: /etc/udev/rules.d/80-wminput.rules. This file contains only the text:
```
KERNEL=="uinput", MODE="0666"
```

2. At this point, I confirmed that I could get my wiimote working without root privileges by opening a Terminal and issuing the command:

```
wminput -c ir_ptr [wiimote MAC address]
```


3. Once I knew I could get this working without root privileges, I went to System->Preferences->Startup Applications and created a new item with the command I confirmed was working in Terminal in step 2 above. Wminput now starts when I log in, which is perfect since I use XBMC on this particular machine, which also starts up when I log in. The only tricky part is I have to press 1+2 on the wiimote at the right time during login, or else wminput won't grab it.

NOTE: There are various instructions out there that recommend configuring the file in step 1 by user group rather than by mode 0666. I tried and tried but couldn't get it working using the group method. Try this at your own risk as the "mode" method is slightly less secure, but at least it works. HTH!

Have you managed to get this working under 10.04?

Antti

---

### Post by racie on 2011-02-08
Sorry for the bump... but is there anyone who knows how I can successfully reverse everything in the tutorial?  I have removed wminput, wmgui, and lswm, but I am still having an issue that I believe was caused by this tutorial.

---

### Post by Rebelli0us on 2011-02-25
Thank you, this was very helpful! It seems to work better than GlovePIE and it's ON all the time, you don't have to press B to move the pointer. Nice!


- How do you get wiimote to auto-start at boot up?

- How do you get wiimote to auto-start on resume from S3? I noticed sometimes it's still alive.

- Why do you have to keep login into a mouse?!! Is there a way to create a shortcut that starts wii and auto-logs in?



What does this mean? It's a quote form the OP:


> 
To create another icon to kill all running wminput processes, do the same as above, but for the command use this

  ```
  gksudo killall wminput
```

Use gksudo here too because you might need to type in your password again.

The advantage of using these two icons to run wminput, is that you can turn off your Wii remote (by pressing and holding the power button on your Wii remote) when you start watching a DVD / listening to music to save battery power, then if you wish to start using your Wii remote again, simply press buttons 1 + 2 on your Wii remote and Ubuntu will automatically connect to your Wii remote again as before without having to pick up a keyboard or mouse to do so.


A good idea if this works. We're talking multimedia here, you don't want a keyboard at your living room couch, or another mouse to start the first mouse.


//

---

### Post by Rebelli0us on 2011-03-09
I get this message box when machine resumes from suspend S3. It does it in the Root account and regular accounts as well. Any ideas how to fix this?

---

### Post by KiaZ on 2011-04-29
Hello, 
sorry for bringing up an old post. 
I have a wiimote (accelerometer mode, I just need to use the buttons) correctly running with wmimput both in ubuntu 9.10 and 10.10 . 
However i have a problem : I would like to automatically pair the wiimote at boot , without pressing 1+2 to put wiimote in discovery mode. 
Actually I just run 
$ sudo wminput -c /etc/my-wiimote-conf.conf 
and i have to press 1+2 to connect wiimote. 

I would like to keep permantly paired my wiimote with my all-in-one pc. 

Is there a way to do that ? 
if i run : 
$ sudo wminput -c /etc/my-wiimote-conf.conf my:wiimote:mac:address
doesn't change anything, wmimput is still asking me to press 1+2 

Can anyone help me ? 
thanks in advance. 
KiaZ

---

### Post by Toshibawarrior on 2011-04-29
Hello KiaZ,

As far as I know, there's no way to do that. As soon as the bluetooth connection with your PC is lost or terminated (either by turning off the PC or manually killing the process) the Wiimote turns off. 

But then again I've been away from this post for a long time and I don't even use Ubuntu anymore (Bought an iMac 6 months ago). I'm sorry I can't help you further with this issue. Last time I tested this guide was with Intrepid Ibex, I don't what could have changed over the years.

---

### Post by KiaZ on 2011-04-30
> **Toshibawarrior said:**
> Hello KiaZ,

As far as I know, there's no way to do that. As soon as the bluetooth connection with your PC is lost or terminated (either by turning off the PC or manually killing the process) the Wiimote turns off. 

But then again I've been away from this post for a long time and I don't even use Ubuntu anymore (Bought an iMac 6 months ago). I'm sorry I can't help you further with this issue. Last time I tested this guide was with Intrepid Ibex, I don't what could have changed over the years.

Hello, thanks for answering... 
So there's no way to avoid putting wiimote in discovery mode every time you reboot ... 
I will find temporary workaround, but I read on many wminput guides that you have to specify wiimote mac address to use wmimput. Well, my wminput version works without mac address, always asking to press 1+2 to pair. 
If there would be a way to permantly add my wiimote mac address to wminput or whatever other program ... would be extremly helpful ....

---

### Post by Rebelli0us on 2011-05-01
wminput works with or without the MAC address on the command line.

When you suspend S3 wiimote usually disconnects, so on resume you have to press 1+2 to reconnect, it's just how the wiimote is designed to work.

Using the -d daemon option works without requiring a keyboard or another mouse to restart the wiimote, BUT -d option causes intermittent OS crashes on both my machines, so I've stopped using it.

---

### Post by Mickafromparis on 2011-06-07
Hi, I've been using wiiremote with Maverick and it worked fine. I can't make it work anymore with natty (nor wmgui, nothing happens...) Does anyone have a clue?

---

### Post by -ijk- on 2011-06-09
> **KiaZ said:**
>  I would like to automatically pair the wiimote at boot , without pressing 1+2 to put wiimote in discovery mode. 

The problem is the pin for pairing a wiimote is a binary string rather than just numbers - this isn't supported.

There's a guy called David Herrmann who [takes an interest in this and has submitted patches which didn't get accepted]("http://thread.gmane.org/gmane.linux.bluez.kernel/13380")

However he has been writing a [wiimote driver]("https://github.com/dvdhrm/xwiimote") as a GSOC project
([Announcment]("http://thread.gmane.org/gmane.linux.bluez.kernel/12872"))

---

### Post by Zvlwab on 2011-09-26
I'd like to use a wii mote + nunchuk as a controller for Mupen64.

This is my config file:
```
# Wiimote
Wiimote.Up = BTN_0
Wiimote.Down = BTN_1
Wiimote.Left = BTN_2
Wiimote.Right = BTN_3
Wiimote.A = BTN_A
Wiimote.B = BTN_B
Wiimote.Minus = BTN_SELECT
Wiimote.Plus = BTN_START
Wiimote.Home = BTN_MODE
Wiimote.1 = BTN_X
Wiimote.2 = BTN_Y

# Nunchuk Buttons
Nunchuk.C = BTN_C
Nunchuk.Z = BTN_Z

# Nunchuk Axes
Nunchuk.Stick.X = ABS_X
Nunchuk.Stick.Y = -ABS_Y
```Everything works fine, except that the  nunchuk's stick gives a too low input so that I'm unable to run in  several games. I googled it, but I was unable to find any good answers.
Also I tried this:
```

Nunchuk.Stick.X_Scale = 2.0
Nunchuk.Stick.Y_Scale = 3.0
```But it just gives some errors when trying to connect

Could anyone tell me how to fix this?

I also read something about wm2js, but this only gives an error

---

### Post by jjpcexpert on 2012-04-17
How may I calibrate a Wiimote using my Philips TV remote? Don't have an IR pen :(

---

