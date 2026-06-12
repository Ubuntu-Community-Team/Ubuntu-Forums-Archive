---
title: "Usb in Virtualbox 3.1.8 on Lucid host not working"
date: 2010-05-11
forum: Virtualisation
---

### Post by empty_spaces on 2010-05-11
I've tried to research this issue, but haven't turned up anything useful so far.

_My setup_:- **Lucid 64bit host**, **Win XP 32bit guest**
_Issu_e:- Trying to get the Win XP guest to see my usb flash drive.

I know there were issues with getting usb working with Virtualbox **3.1.6** on Lucid.
Supposedly, Virtualbox **3.2 Beta** was supposed to work, but I tried that and usb still did not work for me.

Now, Virtualbox **3.1.8** has been released into the official Lucid repos, so I installed that, and again, no usb. 

So, does anyone have this working? If yes, any settings to make it work?

Note: I am already added to vboxusers group.

---

### Post by nderic77 on 2010-05-12
Are you using the Open Source Edition (OSE) or the full edition? If you installed from the Software Center, you are running OSE. Some people have gotten OSE to work with USB, but as far as I can see, it is only after some significant tweeking. The full edition is proprietary, but provided for personal use for free by Oracle. I am running 3.1.6 full edition on Lucid 64-bit, and have no problem with USB 2.0 devices.

---

### Post by wd5gnr on 2010-05-12
The latest Ubuntu release got rid of hal and current versions of VirtualBox require it for USB. 

Try:

Alt+F2

and then

sudo hald

Press enter and then try launching your VM again.

Hope that helps. And like the previous poster mentioned, you need the "full" version not the one out of the repos. And yes it is not OSS.

---

### Post by empty_spaces on 2010-05-12
Hey guys, thanks for your replies. I guess I had a brain freeze or something, because the issue has been resolved, and it was basically me not paying attention.

Here's what happened. 
I've been using VBox long enough to know the difference between OSE and PUEL.
I guess I forgot that I had added the VBox repos for **Karmic** a while back when playing with **3.1.6(PUEL)**, so when **3.1.8(PUEL)** appeared in the repos and I installed it, it was the one for **Karmic**.

So I updated the correct repos for lucid, and installed **3.1.8(PUEL)** for Lucid. 

Everything works now, including usb. Well, everything except the bridged adapter in networking(NAT is fine). Guess I'll have to start a new thread for that, although if there is a quick solution, I would be nice to get it resolved right here.

---

