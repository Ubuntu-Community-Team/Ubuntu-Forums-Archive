---
title: "boot Ubuntu Server without monitor"
date: 2010-06-24
forum: Server Platforms
---

### Post by bigboa on 2010-06-24
Good day to every one!!
 
I'm traing to boot Ubuntu without monitor, but when i disconnect monitor and power on server i can't connect to server, over ssh, even after 5 min. When monitor connected to server all works fine.
 
Can anybody help...

---

### Post by _Mark_ on 2010-06-24
So to recap, with monitor can SSH to server, without monitor can't SSH
Sounds like it is not booting fully and without a monitor you won't be able to see any errors. Can you ping the server when no monitor is connected? if again no I would say definitely not booting correctly

you could look at any logs in /var/log to see if you can see any boot errors apart from that don't really know what to suggest

---

### Post by Bachstelze on 2010-06-24
Maybe you have a weird BIOS that won't boot without a monitor. Look in it and see if it is modifiable.

---

### Post by DavePlummer on 2010-06-24
It's probably not an Ubuntu problem. I run a headless server with no problems. Some machines, by default, will refuse to boot anything when a monitor and/or keyboard is missing. You can usually override that behavior by changing a setting in the BIOS setup. The location/name of the setting varies. You may have to poke around a bit to find it. Hope this helps.

---

### Post by bigboa on 2010-06-24
> **_Mark_ said:**
> So to recap, with monitor can SSH to server, without monitor can't SSH
Sounds like it is not booting fully and without a monitor you won't be able to see any errors. Can you ping the server when no monitor is connected? if again no I would say definitely not booting correctly
 
you could look at any logs in /var/log to see if you can see any boot errors apart from that don't really know what to suggest
 
Yes, i can ping when monitor is connecting and SSH to server.
 
About BIOS i don't find anything like boot without monitor, in settings, but i will try to find it again.

---

### Post by bigboa on 2010-06-24
don't find anything in BIOS, can it be Grub problem?

---

### Post by koenn on 2010-06-24
grub doesn't need a monitor.

Look in your BIOS for something  like "HALT on all errors" and set that to something that sounds like "ignore errors re. monitor"

---

### Post by CharlesA on 2010-06-24
It sounds like it's a BIOS thing, yes. I've run a few machines headless without problems.

---

### Post by dragos2 on 2010-06-24
How do you connect: by hostname or by ip? Your server has a static ip ? Maybe there is a HDCP router on the network and your server gets a different ip every time it boots.

What is the firewall state on it ? Can you ping it ?

---

### Post by EmanresuusernamE on 2010-06-24
I concur, I have a desktop machine that I turned into a server, and I don't have a monitor, keyboard or mouse on it.  Just a power cord and a LAN cable, and it works just fine if I send it a remote reboot request too.

When you say that the server works fine with the monitor, are you connecting the monitor and then going to a different computer to connect, or do you only have one monitor and start using the server after you put the monitor on it?

How long are you waiting before attempting to connect to the server?  Do you have SSH installed an enabled?  Did you install a firewall that is blocking your SSH port?

When you're on the server, can it SSH into itself? Use this command to see if you can:
ssh localhost

---

### Post by bigboa on 2010-06-25
It seems i have problem with hardware (WANLIDA PC-8001H-2). Can't find anything in BIOS (InsydeH20). I have win7 and ubuntu 10.04 installed. Whithout monitor win7 cant't boot, like ubuntu. When i connect monitor - averything works just fine, ping, SSH ...

---

### Post by EmanresuusernamE on 2010-06-28
Can you try booting up your computer with the monitor, then after it boots remove the monitor to see if it still works?

---

### Post by Groodles on 2010-06-28
When you boot with a monitor attached, and it's finished the boot sequence..... what is the monitor displaying?

---

### Post by WinstonChurchill on 2010-06-28
A friend of mine had a headless "server" that he had 9.04 Desktop installed on, and he wanted to use VNC remotely to make it download torrents and such. The Desktop version wouldn't boot without a monitor plugged in, so I just plugged a VGA cable in and stuffed aluminum foil in the other end of the cable (shorting all the pins) - and it worked. Maybe try that?

---

### Post by EmanresuusernamE on 2010-06-28
:confused: :confused: :confused:

I should think that shorting out all of the pins would be a bad idea.  If the system is not properly grounded and there was some feedback from say the power supply, then it's possible that you could damage your video card.  And if you don't have a video card and something goes wrong with the system, you won't be able to access it until you move the hard drive to another system.

---

### Post by koenn on 2010-06-28
I agree, shorting the pins sounds like a bad idea.

What could be interesting, is boot the machine **without** a monitor, give it ample time to fail (5 minutes ?), then attach a scrren and see what it displays. 
You *might* see the thing display an error, which would be a clue as to why it stops if no monitor is present

---

### Post by WinstonChurchill on 2010-06-28
> **koenn said:**
> I agree, shorting the pins sounds like a bad idea.
All I'm saying is that I encountered this same issue, and the aluminum foil worked. And that video card still functions just fine. BUt, this success could be specific to certain video hardware - this one was a very old Intel AGP card.

---

### Post by CharlesA on 2010-06-28
> **koenn said:**
> I agree, shorting the pins sounds like a bad idea.

What could be interesting, is boot the machine **without** a monitor, give it ample time to fail (5 minutes ?), then attach a scrren and see what it displays. 
You *might* see the thing display an error, which would be a clue as to why it stops if no monitor is present

From what I've seen when trying to run my machine headless, it won't display anything if it doesn't detect the monitor, even if you hook one up after booting.

Maybe I have mine set up incorrectly, but idk.

---

### Post by cariboo on 2010-06-28
I think the op needs to answer a couple of questions first.

[list=1]
[*] Which version are you running? Desktop or server
[*] If you are running the server version did you install a desktop?
[*] Why in the world are you dual booting Win 7 and a server?
[/list]

---

### Post by theshowmecanuck on 2012-10-17
"Works for me" is not a response. If all you have to tell people is that it works for you, then don't bother, it obviously doesn't work for the original poster. If you have nothing constructive to say then don't say anything. 

If somehow X11 software is installed, Ubuntu will not start without a monitor unless you configure it. The idiots at Ubuntu have put in ridiculous checks to stop successful booting without a monitor. Another case of unchecked "good ideas." That's sarcasm, that "feature" is a horrible idea.

And the packaging retards have ensured that you can't install ia32 compatibility package without it installing X11. What a load of bullocks.

Here's how to fix this issue.

[http://askubuntu.com/questions/196603/how-to-remove-the-graphical-user-interface/196613#196613](http://askubuntu.com/questions/196603/how-to-remove-the-graphical-user-interface/196613#196613)

And in case you think it's isolated here are a couple more you might try to answer with a little more than "works for me"

[http://askubuntu.com/questions/166009/use-ubuntu-graphical-desktop-without-monitor-at-boot](http://askubuntu.com/questions/166009/use-ubuntu-graphical-desktop-without-monitor-at-boot)

Search for similar questions and you'll see.

In the meantime, I'll post a useful answer for those people.

---

### Post by CharlesA on 2012-10-18
Keep in mind this thread is from 2010, and lightdm didn't exist in 10.04.

---

