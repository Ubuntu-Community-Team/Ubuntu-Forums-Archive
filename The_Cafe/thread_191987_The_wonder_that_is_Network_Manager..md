---
title: "The wonder that is Network Manager."
date: 2006-06-08
forum: The Cafe
---

### Post by prizrak on 2006-06-08
One of the biggest complaints I hear about Linux is how difficult it is to deal with wireless and how it requires alot of work. While it's true if your card happens to be non Linux friendly and was true for a while even for the Atheros and Intel based cards. 

Network Manager changed all that it is awesome. I always thought that while XP's wireless zero was not perfect it was a fairly decent front end. My biggest issue with it was always the fact that that *%*%*% would put things into preferred networks and connect to the last network you connected to. That was a huge pain for me as my local laundromat runs it's own Linksys hot spot, with SSID (you guessed it) Linksys. Someone within the range of my wireless in my building is ALSO running a network with a Linksys SSID. Back on XP (long time ago in an apartment far away) I would have to manually connect to my own network.

I installed Dapper as soon as it came out and went to do laundry the other day. I had Network Manager managing my connections. For one it made connecting to a new network a breeze, it didn't attempt to find my old network (as XP tends to) it simply scanned for w/e is available. There is also nothing like a one click connect. The biggest surprise however was when I got home and powered my laptop. It connected to MY network not the other Linksys it could find. It actually was smart enough to connect to the STRONGER signal as it would likely be the network the user wants to connect to. 

The point of all of this? In about 3 years Ubuntu went from new kid on the block to a system that ALREADY surpasses the competition in things that it was always viewed to be inferior in. If Ubuntu keeps on this path we will be running VR desktops with thought control systems in about 5 years :)

---

### Post by mostwanted on 2006-06-08
Every time I boot up with Network Manager I need to type in my password - not ideal. Network Manager also doesn't support PEAP authentication yet which is what my school uses. These issues won't be resolved until the 0.7 release which I hope makes it into Edgy (but I'm not sure if I'm that lucky).

---

### Post by Engnome on 2006-06-08
I dont understand all this hype about network manager. My network admin has been looking the same since warty. So I checked with google and is [http://images.google.com/images?client=opera&rls=en&q=ubuntu%20network%20manager&sourceid=opera&oe=UTF-8&ie=UTF-8&sa=N&tab=wi]("http://images.google.com/images?client=opera&rls=en&q=ubuntu%20network%20manager&sourceid=opera&oe=UTF-8&ie=UTF-8&sa=N&tab=wi") this it? I checked synaptic but i have it installed so what is going on here? what am I missing:confused:

---

### Post by ComplexNumber on 2006-06-08
> Every time I boot up with Network Manager I need to type in my password - not ideal that happens with me too. personally, i don't see any problem with that. perhaps one of the reasons why it needs the password is because network manager writes to files in the /etc directory. 

despite having wifi radar up and running, and the fact that i hadn't even set my wireless card up at all in network manager (ie there is nowhere in network manager's GUI that knows what wireless card i have...because i haven't entered any info in there), network manager seems to have configured everything itself. this can be noted from some of the files such as names.conf, resolv.conf, etc in the /etc directory.

---

### Post by prizrak on 2006-06-12
[QUOTE=mostwanted]Every time I boot up with Network Manager I need to type in my password - not ideal. Network Manager also doesn't support PEAP authentication yet which is what my school uses. These issues won't be resolved until the 0.7 release which I hope makes it into Edgy (but I'm not sure if I'm that lucky).[/QUOTE]
Can't say anything about PEAP support, one thing though is that you can install network manager yourself outside of the repos. 

The reason it asks for a password is because it stores network keys in the keyring, which is encrypted. I dunno if I would call it a design flaw, it's nice to not have your secret keys not out in the open and keyring could easily just use user for authentication (the way Windows does with encrypting drives). On the other hand however unecrypted keys are only a concern with physical access to the system (at which point the least of your worries is a WPA/WEP key).
>  	I dont understand all this hype about network manager. My network admin has been looking the same since warty. So I checked with google and is [http://images.google.com/images?client=opera&rls=en&q=ubuntu%20network%20ma](http://images.google.com/images?client=opera&rls=en&q=ubuntu%20network%20ma) nager&sourceid=opera&oe=UTF-8&ie=UTF-8&sa=N&tab=wi this it? I checked synaptic but i have it installed so what is going on here? what am I missing

Network Manager is installed but not activated by default. In order to get it you need to get rid of the default icon in the tray. Hit Alt+F2 and type in nm-applet. That will start the network manager applet. You also need to go to /etc/network/interfaces and comment out all of the entries (put a # in front of the lines). For some reason NM doesn't like that file.

---

### Post by grsing on 2006-06-12
I haven't really been all that impressed with Network Manager.  Well, actually, the applet itself is fine, but wireless in Ubuntu is still not that great.  I'm using a very common config (pretty standard Dell laptop, D600), and it doesn't work out of the box, and I still haven't gotten WPA working.  I understand the reasons behind why it can't work out of the box (freedom stuff), but a newbie wouldn't, and I don't even know why WPA doesn't work.  So, it's an improvement, but still not up to Windows level, for me (I hate to say that, but wireless and games are about the only 2 things that Windows is still better for, for me).

---

### Post by nalmeth on 2006-06-12
I would use this if I could. My wireless situation is still up in the air on my laptop.
Every 'authority' I talk to has a different story.

I have to figure out if its a Cardbus vs PCICMA issue, or a 32-bit vs 16-bit issue (this tip from my local computer store guy).

Anyway, it looks very impressive, can't wait to try it out eventually.

---

### Post by prizrak on 2006-06-12
[QUOTE=grsing]I haven't really been all that impressed with Network Manager.  Well, actually, the applet itself is fine, but wireless in Ubuntu is still not that great.  I'm using a very common config (pretty standard Dell laptop, D600), and it doesn't work out of the box, and I still haven't gotten WPA working.  I understand the reasons behind why it can't work out of the box (freedom stuff), but a newbie wouldn't, and I don't even know why WPA doesn't work.  So, it's an improvement, but still not up to Windows level, for me (I hate to say that, but wireless and games are about the only 2 things that Windows is still better for, for me).[/QUOTE]
The issue is not freedom in this case and it's not in the place you are looking at. The problem is in the drivers. To be fair Windows can't run my WNIC unless I install drivers first, at all. No out of the box support whatsoever. Ubuntu has it up and running, this isn't really something that has to do with the application itself. So far from what I have seen it is superior to XP's wireless zero.

---

### Post by Engnome on 2006-06-13
[QUOTE=prizrak]
Network Manager is installed but not activated by default. In order to get it you need to get rid of the default icon in the tray. Hit Alt+F2 and type in nm-applet. That will start the network manager applet. You also need to go to /etc/network/interfaces and comment out all of the entries (put a # in front of the lines). For some reason NM doesn't like that file.[/QUOTE]

It says:

Could not open location 'file:///nm-applet'

Details: The location or file could not be found.

When I try nm-applet.

---

### Post by ????? on 2006-06-13
NetworkManager always shows the signal strength as 100% no matter how strong the signal really is... and I saw a topic in the HOWTO forum that tells you how to stop networkmanager fromasking you for keyring password

---

### Post by vvlist on 2006-06-13
I like network manager. The only problem I have with it (and maybe I can fix this) is that it does not auto connect on boot, I have to select the network first and this messes up liferea from auto starting on boot because it thinks there is no network. Any ideas on how to fix this? Oh, and by the way, this is still in beta, so people shouldn't have high expectations for it... yet.

---

### Post by prizrak on 2006-06-13
[QUOTE=vvlist]I like network manager. The only problem I have with it (and maybe I can fix this) is that it does not auto connect on boot, I have to select the network first and this messes up liferea from auto starting on boot because it thinks there is no network. Any ideas on how to fix this? Oh, and by the way, this is still in beta, so people shouldn't have high expectations for it... yet.[/QUOTE]
It auto connects to a network on boot if it were connected to it at some point before. It auto-connects to my home network even if I was on a different one before. I'm not too sure if it would connect to more than one like that though. 
> NetworkManager always shows the signal strength as 100% no matter how strong the signal really is...
I have the opposite sorta I got 83% right now and I'm like 3 feet from the router. I think it might have to do with the drivers or the hardware itself rather than NM. It is still in development so things should get better. 
> and I saw a topic in the HOWTO forum that tells you how to stop networkmanager fromasking you for keyring password
Thanks that's fairly useful to know I think I will try it out.
> It says:

Could not open location 'file:///nm-applet'

Details: The location or file could not be found.

When I try nm-applet.
Hmm, it is a possibility that it is not installed by default, I was sure it was. In that case attempt this 
```
sudo apt-get install network-manager network-manager-gnome
```
The rest is the same.

---

