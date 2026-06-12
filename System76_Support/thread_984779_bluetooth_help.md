---
title: "bluetooth help"
date: 2008-11-17
forum: System76 Support
---

### Post by Lee_Machine on 2008-11-17
So I started a thread about this issue and I had thought that I had fixed it but I guess not.

[http://ubuntuforums.org/showthread.php?t=982688](http://ubuntuforums.org/showthread.php?t=982688)

The symptoms are this:

I cannot connect or see any bluetooth devices. When I go to the bluetooth menu in Preferences all I can see is the General Information, not the hardware information, or where it would be called by my computer name1 by default and you can set options like what devices to trust and if to always connect.

I am thinking that this is an issue where it is not talking to the hardare correctly, as it has worked before at random times.

It still says in the Device Manager under USB bluetooth "Inusfficiant power to operate USB device" 

Not sure what this is about.

In the daemon.log for bluetoothd it says "unable to get on D-Bus"
along with "Failed to find Bluetooth netlink family"

The system is panp4n Ubuntu 8.10 64bit

Thanks in Advance,

Update:

I found this with my exact hardware information per Device Manager:

[https://bugs.launchpad.net/ubuntu/+bug/289836](https://bugs.launchpad.net/ubuntu/+bug/289836)

No known workarounds.

---

### Post by Lee_Machine on 2008-11-17
Update:

So I plugged in one of my bluetooth dongles that I use for my TVs media box and it worked right away on the laptop. Didn't have to install or reload anything works like it should.

Dont know if this fix is needed to be done upstream by the vendor, or if S76 can do it.

Until I find a fix I'll just have to use the external dongle when I want to use my mouse. As I have tried more things that I should on a machine that needs to be stable, and not tested on.

---

### Post by thomasaaron on 2008-11-17
Fn-F12 turns the bluetooth on and off. Whenever you reboot the machine it defaults to 'off', so you have to manually turn it back on.

Also, if you left-click the bluetooth icon, it should show you a list of available devices. Does that work.

It could also be that there is some remnant of your KDE install that is hosing your bluetooth.

---

### Post by Lee_Machine on 2008-11-17
> **thomasaaron said:**
> Fn-F12 turns the bluetooth on and off. Whenever you reboot the machine it defaults to 'off', so you have to manually turn it back on.

Also, if you left-click the bluetooth icon, it should show you a list of available devices. Does that work.

It could also be that there is some remnant of your KDE install that is hosing your bluetooth.

I read about fn-F12 on another thread that you responded to. I tried it but with no luck. 

So I dont have to mess with it being default to off I just went to etc/default/bluetooth/main.conf "i think that is the path im at work and on a Windows machine."

Anyways I changed it to always on.

This way to when I come back from a reboot or suspend my mouse will work. It works just fine with another external dongle.

Also when I click the bluetooth icon it doesnt find any devices nor even see that there is hardware "when I don't have the external dongle in"

tried searching with the command hci --search and that doesn't work, nor does any other CL program.

The internal does not always show up in Device Manager either at random times.

The external does and it still comes with the error about insufficient power for USB device.

Do you think it is the bug report that put a link to?

---

### Post by thomasaaron on 2008-11-17
Probably not.

Please try it from a live CD. You will have to push the Fn-F12 once your in the live session. See if it sees anything then. This will give us a better idea of if it is a hardware issue or a hosed configuration somewhere.

---

### Post by Lee_Machine on 2008-11-17
Ok, 

I'll try that later on tonight. It didn't work though when I put in a livd-cd of Linux Mint which I considered installing but I read that the S76 driver do not work in Mint. 

Thanks for the help.

---

### Post by Lee_Machine on 2008-11-17
So I tried using the Ubuntu 8.10 64bit live-CD, the same one I used to install my current install and bluetooth still did not work. Same issues as last time.

I then put in the external one and it recognized it right away and worked.

Any suggestions?

---

### Post by Lee_Machine on 2008-11-17
I also forgot to mention that I have tried installing the bluez3 stack and removing the bluez4 stack, along with tring to use blueman.

Intrepid doesn't like bluez3 very much. it broke 2 bluetooth dependencies and didn't work for me even with the external dongle.

So I just removed that and reinstalled bluez4.

This was listed as a work around on launchpad.

---

### Post by thomasaaron on 2008-11-18
Let's take this issue to support email. If it doesn't work from a live CD, it's probably hardware.

Please fill out this form, and I'll email you with further information...
[http://system76.com/article_info.php?articles_id=39](http://system76.com/article_info.php?articles_id=39)

---

