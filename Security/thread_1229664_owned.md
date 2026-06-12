---
title: "owned?"
date: 2009-08-02
forum: Security
---

### Post by motoperpetuo on 2009-08-02
so, i'm sitting at my computer (dell inspiron 530 running jaunty) yesterday morning surfing the web, and a message pops up saying "your computer is being controlled remotely by another user" or something like that. my initial thought is "whatever, just a glitch." then windows start moving around on their own and whoever or whatever it is starts typing a URL in a browser window. i panic and shut down my computer.

i did have "you must confirm each access to this machine" deselected in remote desktop preferences, since i sometimes use vnc to remote into this desktop from my laptop. i selected it and haven't had whatever happened yesterday morning happen again. 

however, this morning, right when starting up some music in totem, i had a bunch of weird empty windows with the ubuntu help center icon (the little life preserver on the upper-left corner in a standard ubuntu install) start coming up. they rapidly got up to over fifty, so i panicked and shut down again.

i've been (rather naively, i guess) complacent about security in the last two years or so since i moved to linux. i mean, i run all updates, set passwords on things, but that's about it. have i been owned? how would i know? what should i do to prevent whatever is happening, and to fix any security holes i've got now? i've got a base image of this machine that i built in clonezilla...should i reimage in case i've got root kits or back door vulnerablities or something like that now?

---

### Post by TuckLive on 2009-08-02
From what you have described, yes you have been owned.  Any box that is believed to be compromised should be re-imaged is my thinking, because you can never trust that system.  

When you reinstall the system, be sure to set up a password for remote viewing and select the box for you to confirm a remote session.

---

### Post by sasho_zl on 2009-08-02
My suggestion to you is to reinstall the whole system and the next time use better firewall configuration in which only trusted ip's are allowed through the netfilter. You can also try network and host intrusion detection systems. Also before reinstalling copy all the logs from this system so you can better see what has happened. Hopefully the hacker didn't had time to change them.

---

### Post by Dr Small on 2009-08-02
I would reboot while not connected to the network, go into the vino-preferences, disable remoted desktop, shutdown, reconnect network, and continue as normal, and see what happens.

---

### Post by credobyte on 2009-08-02
I would definitely go for a clean install .. compromised system can never be enough secure to leave it as it is.

---

### Post by khelben1979 on 2009-08-02
If you're using an ADSL modem you have the possibility to use an inbuilt firewall in your modem. That's way better security than relying on some software firewall to fix your security.

As what have been suggested already, have proper routines in how you're handling your passwords, never write them up on some paper and never let them appear in any of your e-mails, be a bit paranoid about security and you'll have less trouble on your next Linux system.

---

### Post by motoperpetuo on 2009-08-02
thanks for your advice everyone. i think i'll reimage, as most of you suggested. one quick question, one of you suggested copying my log files. what's the best way to do that?

---

### Post by kg84 on 2009-08-02
Wow, not good mate :(

On this matter, how does one ensure that remote viewing / access is turned off?

---

### Post by hansdown on 2009-08-02
> **kg84 said:**
> Wow, not good mate :(

On this matter, how does one ensure that remote viewing / access is turned off?

Hi kg84.

Click system> administration> login window> remote.

Make sure remote access is disabled.

---

### Post by kg84 on 2009-08-02
> **hansdown said:**
> Hi kg84.

Click system> administration> login window> remote.

Make sure remote access is disabled.


Hiya hansdown.

Sorted.

Thanks (again) :)

---

### Post by hansdown on 2009-08-02
You're welcome kg84.

You do get around. That's a good thing, btw.

---

### Post by motoperpetuo on 2009-08-03
so, i reimaged, forgot to disable remote desktop, and got owned again. it was another remote desktop takeover. no, i'm not proud of this at all.

anyway, i reimaged again, this time while off the internet, and disabled remote desktop before going back online. no remote desktop attempts so far. 

however, i just tried to shut down my laptop (a different computer on the same network) and got a dialog that says "system policy prevents the user from stopping the computer when other users are logged in." i've gotten a few of these, on both computers, over the last few days. i ignored them, figuring it was referring to some process i had running as root or something. now i'd suspect it's whoever's attacking me. is there any good way to tell?

also, does anybody have any good links for security in ubuntu, configuring firewalls, that kind of thing? obviously, i need to learn more.

---

### Post by hansdown on 2009-08-03
Hi motoperpetuo.

bodhi.zazen has a really good thread on intrusion detection.

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

It's a long read, but very worthwhile.

---

### Post by igorzwx on 2009-08-03
try to remove pulseaudio (+purge)

howto is here:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

do you have pulse running with root privileges?

read this too:
[http://www.google.com/search?q=linux%20botnet&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=linux%20botnet&ie=UTF-8&oe=UTF-8)
The paper - *[The Economics of Botnets]("http://www.viruslist.com/en/analysis?pubid=204792068")* 
[http://www.theregister.co.uk/2009/07...net_economics/]("http://www.theregister.co.uk/2009/07/24/botnet_economics/")

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.[/B]

---

### Post by cgb on 2009-08-03
Do you happen to know if you are on a static IP address with your ISP or dynamic?  You may want to force your IP to change if it is setup with a dynamic address so that the hacker would no longer have access to your address.  Some modems you can obtain a new IP address by simply unplugging the modem and waiting a good minute before plugging it back in.  Other modems involve actually changing your MAC address on the Router in order for it to give you a new IP.

---

### Post by Chemical Imbalance on 2009-08-03
> **cgb said:**
> Do you happen to know if you are on a static IP address with your ISP or dynamic?  You may want to force your IP to change if it is setup with a dynamic address so that the hacker would no longer have access to your address.  Some modems you can obtain a new IP address by simply unplugging the modem and waiting a good minute before plugging it back in.  Other modems involve actually changing your MAC address on the Router in order for it to give you a new IP.

+1



Instead of just disabling remote desktop, uninstall it like I do.
Also uninstall telnet, vinagre, and others like it unless you need it fairly often.

If you should ever need it in the future, install it only at that time.

Make sure you have a strong password (no dictionary words in it, use numbers and mixed characters).

Update at least weekly.

Consider buying a hardware firewall or router.

---

### Post by bodhi.zazen on 2009-08-03
VNC connections (remote desktop) are notoriously insecure.

You need to use a stronger password (at a minimum)

[Password Strength Checker]("http://www.passwordmeter.com/") 

and I suggest you use ssh to remote admin your box. You can tunnel vnc over ssh if needed.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

and finally take a look at configuring your firewall, - ufw or gufw or better iptables :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

