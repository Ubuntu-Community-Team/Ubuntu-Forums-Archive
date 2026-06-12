---
title: "serval - cannot disable touchpad tap-click"
date: 2006-12-31
forum: System76 Support
---

### Post by icewater on 2006-12-31
i just received a new serval system and can't seem to affect the touchpad.  i found the thread about the "lock" button, but i don't seem to have a button like this.

running synclient gives:

   Can't access shared memory area. SHMConfig disabled?

Xorg.0.log shows:

(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

the touchpad works, but i really need to turn off the "tap-click" for it to be usable.

thanks

---

### Post by crichell on 2006-12-31
The touchpad is by Elantech (hence the messages in the X log).  We've been looking for a good Elantech config GUI tool but haven't found one yet.

---

### Post by icewater on 2006-12-31
> **crichell said:**
> The touchpad is by Elantech (hence the messages in the X log).  We've been looking for a good Elantech config GUI tool but haven't found one yet.

do you know a non-gui fix for the time being?

thanks

---

### Post by crichell on 2006-12-31
I heard something about "tpconfig" but haven't tested it.  Another guy over here is hacking at it so I'll check with him.

---

### Post by crichell on 2007-01-01
I don't have a method to disable tap-clicking; however, I'm writing a small app to disable and re-enable the touchpad (good for those that use external mice).  Should have it done in a couple of days.

---

### Post by icewater on 2007-01-21
is this utility available yet (disable touchpad on serval)?

thanks

---

### Post by crichell on 2007-01-21
No I've ran out of time.  I hope to get to it in the next couple of weeks.

---

### Post by vanlue on 2007-02-22
Any update on your app or any solutions for this?  I'm having the same issue.

---

### Post by crichell on 2007-02-22
Sorry guys - I haven't had a chance to get to it yet.  As soon as I do I'll post in here.

---

### Post by uttaranduutta on 2007-03-24
Any body has any leads on Writing a Touchpad driver for Elantech Touchpads ? or the Synaptics touchpad could be hacked to work on the Elantech device? Thinking of investing time on it

---

### Post by steveneddy on 2007-03-24
Quick and dirty way to disable the touchpad:

```
sudo rmmod psmouse
```

Which will turn off the mouse and still allow you to use an external USB mouse. Run

```
sudo modprobe psmouse
```

To turn it back on.

This is from [this post]("http://ubuntuforums.org/showthread.php?p=2116637#post2116637"), and the credit goes to Carl.

Cheers - SE

---

### Post by asmiller-ke6seh on 2007-12-20
I'm not saavy enough to figure out how to do this (I'm a Linux noob, and not ashamed to admit it - but I am learning more and more each day) but I would like to find out if there is a way to set up Ubuntu so that when I plug in a mouse to a USB port, the lpatop touchpad is disabled - and when I unplug the mouse from the USB port, the touchpad is re-enabled.

From what I have been able to learn, I deduce that there is a way to monitor the state of the USB port for the presence of a mouse, and then MODPROBE MOUSE to enable or disable the touchpad appropriately.

Anyone interested in doing this, or helping me to figure this out.

May I also suggest that this might be a nice addition to the System 76 driver?

Thanks, in advance.

---

### Post by thomasaaron on 2007-12-20
you can disable the mousepad with:
sudo modprobe -r psmouse

you can enable it again with:
sudo modprobe psmouse

---

### Post by asmiller-ke6seh on 2007-12-20
Thomas,

Yes, I know. But if the system could sense the presence of a pointer device on the USB port, this manua.l process would be unnecessary - don't you think?

So, does anyone know what kind of script would allow:

1) Sensing if the USB port status is MOUSE PRESENT or MOUSE ABSENT,
2) If the state changes, and
3) IF USB MOUSE = PRESENT THEN sudo modprobe -r psmouse, ELSE sudo modprobe psmouse. ENDIF.

Told you I was a noob to LINUX.

---

### Post by thomasaaron on 2007-12-20
You could create a daemon that monitored /var/log/syslog for a changes. When it detected a change, it could grep -i it for "mouse" (which would 
catch most optical mouses (mice??)). If "mouse" was detected, it could modprobe -r psmouse.

The next time it caught a "mouse" change, it could modprobe -i psmouse to re-enable it.

I kinda doubt, though, that it is a change that would be put into Ubuntu or the System76 Driver. I use an external mouse with my work laptop
all the time. In fact, I don't think I ever disconnect it from my computer. However, I switch back and forth between the mousepad and the USB mouse
fairly frequently. (For example, right now I've got my feet up on my desk and have the laptop where it belongs -- on my lap. The USB mouse is sitting 
on the desk -- where it belongs.)

But it would definitely be a good optional piece of software to throw into the repos for people who have that specific need.
If you don't know how to write shell scripts, I'd recommend this book:
[http://www.amazon.com/Teach-Yourself-Shell-Programming-Hours/dp/0672323583/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1198190559&sr=8-1](http://www.amazon.com/Teach-Yourself-Shell-Programming-Hours/dp/0672323583/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1198190559&sr=8-1)

Personally, if I just wanted something to meet my own needs, I'd write a little script that (en/dis)abled the mousepad and then call that script with
an little launcher icon on the upper toolbar. 

Best,
Tom

---

### Post by asmiller-ke6seh on 2007-12-21
Thanks. That's the kind of thing I was thinking about. I appreciate the recommendation. I have a bit of a way to go - it's been ages since I've done any coding (used to write lots in FORTRAN and PL/1 - to give you an idea - and did some stuff in APL, too; I wrote my first letter merge program in APL for sending out my requests for grad school applications back in 1975).

I think my wife is buying me [this book]("http://www.amazon.com/gp/product/1593270356/ref=wl_it_dp?ie=UTF8&coliid=I294LTM3QIGDTN&colid=25YDR4FAUHAB6") for Christmas. I feel that it is important that I have a better handle on the overall structure of Linux before I start takling things like shell scripts and learning PERL.

Thanks again.

---

### Post by obscenic on 2008-03-25
Any word on this? It's been a year...

---

### Post by obscenic on 2008-03-25
I should add -
I've been attempting to use metacity to bind a key to a shell script to at least disable it.

The shell script is just: modprobe -r psmouse

This works fine when executed from terminal, as it's in /usr/bin..

However, when I bind it with metacity, it does nothing. I've tested the key combo (Alt+F1) bound to firefox in metacity and that works fine. Any ideas why the shell script won't run?

---

### Post by thomasaaron on 2008-03-25
It probably won't run becuase the keybinding is not correctly pointing to the script (or perhaps it needs to run the script as root). I don't know that much about metacity's keybindings, except that it is pretty tough.

HOWEVER, there is a great program called xkeybind. It is in the repos and makes binding keys to various programs/scripts very easy. You might want to give that a try.

This bug report...
[https://bugs.launchpad.net/system76/+bug/114677](https://bugs.launchpad.net/system76/+bug/114677)
...has some useful info about setting up xbindkeys to run a shell script. You could probably use it for... inspiration.

---

### Post by asmiller-ke6seh on 2008-03-26
> **crichell said:**
> I don't have a method to disable tap-clicking; however, I'm writing a small app to disable and re-enable the touchpad (good for those that use external mice).  Should have it done in a couple of days.

It appears that you made a commitment to this effort, and then it went by the wayside. Can you confirm this?

:confused:

---

### Post by boomdiddly on 2008-04-16
Right this is the first thing i'm giving back to the ubuntu community :D

[http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/]("http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/")

I followed these steps and it works a treat

NO more to sensitive tapping or no more tapping at all plus loads of other options for Synaptic's touchpads

Cheers

Paul

---

### Post by thomasaaron on 2008-04-16
Thanks. 

Just a note: The current Servals have an ElanTech touchpad. Not a synaptics touchpad, so this won't work with them.

---

### Post by boomdiddly on 2008-04-16
> **thomasaaron said:**
> Thanks. 

Just a note: The current Servals have an ElanTech touchpad. Not a synaptics touchpad, so this won't work with them.
Oppps sorry

**_Update on Synaptics problems_**

After restarting a couple of times it seams to have lost the settings tap is back :( so i loaded the manager again and it's still turned off.

I remember fixing this before my hard drive crashed and burned because i have it running for months fine and now i remember how to do it so here is is:

first backup you xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

next edit the file:

```
sudo gedit /etc/X11/xorg.conf
```

find the section that looks like this:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

```

and the following to the before the EndSection

```

	Option		"MaxTapTime"		"0"

```

Save and close the file then restart x with Ctrl+Alt+Backspace , log in and enjoy no tapping also here is a list of other things you can add and tinker with!!

type man synaptics in a terminal window for the manual with all the options under the sun

---

