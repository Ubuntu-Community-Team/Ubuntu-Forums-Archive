---
title: "Need help with VirtualBox..."
date: 2009-08-12
forum: Virtualisation
---

### Post by soulsinner on 2009-08-12
Hi... I have succeeded virtualise my  WinXP that resided in my 1st HDD. I have just install Ubuntu in my 2nd HDD so i have dual-boot and i can run my XP within Ubuntu. 
So the problem that i have after i succeeded virtualize my XP is, non of my keyboard or mouse work.
When i capture my mouse and keyboard, nothing happen. i move my mouse on the XP windows but my mouse don't react. Can anyone help me with this problem. 
Do i need to set anything for my mouse to work??

[[IMG]http://img263.imageshack.us/img263/663/xpvirtualstartup.png[/IMG]]("http://img263.imageshack.us/i/xpvirtualstartup.png/")

At this point my keyboard work well, i can choose XP or Ubuntu.

[[IMG]http://img90.imageshack.us/img90/3923/insidexp.png[/IMG]]("http://img90.imageshack.us/i/insidexp.png/")

When i click capture (right-ctrl) the mouse cursor on ubuntu vanish showing me it was captured, but when i move the mouse the cursor in XP wont budge.
I try filtering my usb (my mouse is usb) when i click capture, my mouse suddenly stop working. Including in ubuntu, after i shut down the virtualXP then my mouse is working again.
Anyone can help me with this, I been googling for a week now but found no answer.

---

### Post by jocampo on 2009-08-12
I like your desktop theme :-)

ok, so let me see if I understand: both, your XP and Ubuntu boxes are virtual? Did you try installing the VirtualBox additions?

---

### Post by soulsinner on 2009-08-13
no... not both on virtualbox..
I use virtualbox on my ubuntu to virtualize my XP on my 1st HDD.
I got some work that have to be done with XP and it's a hassle to reboot and change OS.
The XP was my main OS before i install ubuntu.
The problem is when i want to capture my mouse. Virtualbox show me my mouse is captured but nothing happen on the XP in virtualbox. Why this happen..

By the way... thanx for the compliment on my theme. ^_^

---

### Post by akudewan on 2009-08-13
Ideally, it should just capture your mouse if you click inside the window.

In the main VirtualBox window, (the one from which you boot Windows), go to File > Preferences > Input and make sure "Auto Capture Keyboard" is ticked.

You can also use the Right-Ctrl key to toggle the capture.

---

### Post by adempewolff on 2009-08-13
I don't think your usb mouse would be a problem but just in case it is you could try going through the steps to make the guest OS access USB devices:

1. Install guestadditions
2 [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by soulsinner on 2009-08-13
well..
akudewan : before this I've done everything that u said. It's just that nothing works so i started to post on the forum. anyway thnx for the thought..

adempewolff : i think maybe that is the case... im going to go through that tutorial.. thnx... ^_^

---

### Post by soulsinner on 2009-08-13
adempewolff : -_- i'm stuck with that tutorial. what the hell does it mean... i don't understand any of it...
can we just type like that in the terminal???? im blurred.....

---

### Post by adempewolff on 2009-08-13
yea it's pretty complicated. let me review what I did and I'll get right back to you.

Ok I did some really funky things because I don't know muc about programming.  Looking back and using some common sense I can figure out how to do it manually.

First follow the first command.

```
 if [ "`grep vboxusers /etc/group|grep $USER`" == "" ] ; then sudo usermod -G vboxusers -a $USER ; fi
```

Then type:

```
grep vboxusers /etc/group|cut -d\: -f3
```

it should give you a number for me its "123" remember it.

type:
```
sudo gedit /etc/fstab
```

add the following lines at the end:

```
#USB for Virtualboos
none /proc/bus/usb usbfs devgid=${vGid},devmode=664 0 0
```

Now replace "${vGid}" with the number I had you remember.

Now save the file and restart.

Then go into virtualbox, click settings for the windows xp os, go to the USB menu item.  Enable both checkboxes and add your mouse using the add button on the left side.  Start xp and if it still isn't working check the devices menu then usb devices.

just entering the scripts they give should work as well but for some reason it didn't for me at first and I don't really trust entering script I don't understand.

good luck.

---

### Post by adempewolff on 2009-08-13
i edited the last post then realized that might not notify you depending on the subscription options.

---

### Post by soulsinner on 2009-08-14
hmm... i'll try that... thnx man...
hope it'll work out...

---

### Post by dt.sam on 2009-08-14
&#36825;&#20010;&#23601;&#26159;&#21152;&#36733;&#39537;&#21160;&#30340;&#38382;&#39064;&#65281;

---

### Post by adempewolff on 2009-08-14
&#20160;&#20040;&#39537;&#21160;? &#20320;&#25026;&#19981;&#25026;&#33521;&#25991;&#65311; &#25105;&#26159;&#23398;&#29983;&#12290; &#25105;&#20889;&#27721;&#23383;&#20889;&#24471;&#19981;&#22909;&#12290;

soulsinner-I don't know if you read Chinese but if not he said something along the lines of "This is just a problem of loading the driver".  I don't know what driver he is talking about--maybe guestaddons, maybe the mouse driver.  Or I could have completely misinterpreted it, 4 semesters of Chinese and I still forgot almost everything in just a couple of months over summer break.  Oh well.

---

### Post by soulsinner on 2009-08-18
I think i agree with you on this. Maybe problem with loading the driver inside the XP.
because, at boot up, the keyboard was working.... only when im inside XP the mouse and keyboard doesn't work. anyone got any ideas??
BTW i can't read chinese...

---

### Post by adempewolff on 2009-08-18
the keyboard is USB as well?

---

### Post by soulsinner on 2009-08-25
Nope.. the keyboard is ps/2 & the mouse is USB.
So how can i configure the driver...

---

### Post by adempewolff on 2009-08-25
no idea sorry.  maybe try getting a usb to ps/2 adapter for the mouse and seeing if it will work then.  I think setting it up so windows is directly using the usb mouse with the USB driver would be the hard way.  You should just be able to get the host to feed the mouse input in a generic format to the guest.

---

### Post by soulsinner on 2009-08-25
well. i would try that. i think maybe the usb driver is giving me the problem..
I will go and buy a ps/2 mouse.. (hhhhh... so old) or the converter..
i think i got 1 somewhere..... dunno where it gone...
anyway... thanx a lot wolfy.... u been such a helper...

---

