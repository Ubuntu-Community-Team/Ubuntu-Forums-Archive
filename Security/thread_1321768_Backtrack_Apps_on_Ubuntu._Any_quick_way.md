---
title: "Backtrack Apps on Ubuntu. Any quick way?"
date: 2009-11-10
forum: Security
---

### Post by Roasted on 2009-11-10
I was just curious... I've been playing around with Backtrack on LiveCD but I'd really like to install it. I don't know about Backtrack 4, but Backtrack 3 is laughably retarded to try and install, even with the documentation I found on it.

Plus Backtrack is KDE, and I'm a Gnome guy. No biggie but, just a small preference thing.

Is there any way I can add some sort of repository to my listing and just suck down all of the same apps that Backtrack comes with installed by default?

---

### Post by Sarmacid on 2009-11-10
If you copy the /pentest/ directory from backtrack, most of the tools if not all will work.

---

### Post by Roasted on 2009-11-10
> **Sarmacid said:**
> If you copy the /pentest/ directory from backtrack, most of the tools if not all will work.

Where do I put it on Ubuntu?

---

### Post by Sarmacid on 2009-11-10
Just put it anywhere you want.

---

### Post by Roasted on 2009-11-10
Okay. So uh... I pasted it. Now what? Are the applications just supposed to magically show up in my menu?

---

### Post by __p1n__ on 2009-11-10
> **Roasted said:**
> Where do I put it on Ubuntu?

Sounds like you're better off sticking with the livecd.  Go with BT4 instead of BT3 and you'll probably be happiest with the fast track tool (front end to nmap/msf-dbpwn automation.)

---

### Post by Limeni on 2009-11-10
You dont need to copy files from Backtrack CD on Ubuntu to get apps work. You can simply install them inside Ubuntu. 

For example i was playing around with WEP hacking so I installed aircrak-ng through Syntapic Package Manager, or Wireshark through Ubuntu Software Center. Its all there you joust need to install it, and all the apps that work on BackTrack will work on Ubuntu too, they have the same kernel. I thinkg so :D Im still new to Linux, using it for 5 days now, but thats how I installed aircrack.

---

### Post by cariboo on 2009-11-10
Most of the tools should be available in the repositories, use synaptic to search for them.

---

### Post by Sarmacid on 2009-11-10
> **Roasted said:**
> Okay. So uh... I pasted it. Now what? Are the applications just supposed to magically show up in my menu?

Nope, you navigate to the folder of the app and launch it, if you want them to appear on the menu you have to add them yourself using the menu editing tool.

---

### Post by __p1n__ on 2009-11-10
> **Roasted said:**
> Okay. So uh... I pasted it. Now what? Are the applications just supposed to magically show up in my menu?

Seriously, just keep using a livecd version of BT.

---

### Post by Roasted on 2009-11-10
> **__p1n__ said:**
> Seriously, just keep using a livecd version of BT.

I don't want to use the LiveCD. I want to have these applications loaded locally on my computer for quick access. So I really need an actual installation of the OS.

I think I mentioned I tried BT3, which is just... poorly designed to be installed on a computer. I'd just like to have them on my computer to tinker with. If that means BT3/4 in a VM, fine. If I can dump BT's applications on my Ubuntu rig, better yet.

---

### Post by michaelzap on 2009-11-10
> **Roasted said:**
> I don't want to use the LiveCD. I want to have these applications loaded locally on my computer for quick access. So I really need an actual installation of the OS.

I think I mentioned I tried BT3, which is just... poorly designed to be installed on a computer. I'd just like to have them on my computer to tinker with. If that means BT3/4 in a VM, fine. If I can dump BT's applications on my Ubuntu rig, better yet.

AFAIK BackTrack is not really designed to be installed, since it logs you in as root and would therefore be insecure for routine use. Some people do it anyway, of course, and you might want to be one of those people. Here is a tutorial for installing BT4 to your hard drive:
[http://www.itsolutionskb.com/2009/04/how-to-make-a-backtrack-4-hard-drive-installation-step-by-step-guide/](http://www.itsolutionskb.com/2009/04/how-to-make-a-backtrack-4-hard-drive-installation-step-by-step-guide/)

You can also choose the applications that you want to use from BT and install them in Ubuntu, but you may run into roadblocks since the BT folks have made many tweaks to the stock Ubuntu system in order to make a lot of things work. Just copying BT programs to your system and running them with root privileges may work in some instances, but it will depend on what you want to do.

Personally I just stick to the Live CD so as not to muck things up.

---

### Post by Roasted on 2009-11-10
It makes sense as to why it's on a LiveCD. It's just, I like Ubuntu. Ubuntu has Gnome. BackTrack has KDE. It'd just be nice to have my existing Ubuntu install with the tools I need, which BackTrack currently has.

---

### Post by michaelzap on 2009-11-10
> **Roasted said:**
> It makes sense as to why it's on a LiveCD. It's just, I like Ubuntu. Ubuntu has Gnome. BackTrack has KDE. It'd just be nice to have my existing Ubuntu install with the tools I need, which BackTrack currently has.

I hear you. I've had a lot of the same thoughts myself. I would learn how to use BT a lot more if I had the tools in my main Ubuntu installation rather than on a USB stick.

What would really be ideal would be if the BT folks would make a ppa for installation on Debain and Ubuntu systems, but again it might be necessary to make other system changes for many of them to work.

You can try to run your favorite BT tools in Ubuntu, and many of them may work just fine.

---

### Post by Roasted on 2009-11-10
> **michaelzap said:**
> I hear you. I've had a lot of the same thoughts myself. I would learn how to use BT a lot more if I had the tools in my main Ubuntu installation rather than on a USB stick.

What would really be ideal would be if the BT folks would make a ppa for installation on Debain and Ubuntu systems, but again it might be necessary to make other system changes for many of them to work.

You can try to run your favorite BT tools in Ubuntu, and many of them may work just fine.

Yeah, considering there's a repo for them in 8.10, I can't see why they wouldn't work. I understand there may be system-wide changes made to cater to certain applications, but for the most part I don't see where it'd go wrong. Gonna try it in a VM and see where it goes!

---

### Post by linthusiast on 2009-11-18
It would be great if I could abandon using the BT4 live DVD and could have all the tools available and working in Ubuntu 9.10. I understand there are all sorts of kernel patches applied to get wifi cards working in good order. E.g. I have never been able to things like monitor mode, etc using my default ubuntu install. However with the BT4 live DVD it worked out of the box.

Anyway, auditing the security of my Wifi networks along with Web App auditing is my thing, so if I can do this inside Ubuntu 9.10 then fantastic.

Any takers?

---

### Post by jessiebrownjr on 2009-11-18
I patched my own Atheros wifi driver to get it to be able to inject... It was.. a pain, because I was a linux newb. Got aircrack-ng up and operational. It worked.  Once I got that done I installed Backtrack 4 ON my hard drive to see what IT was all about.. it shows up in grub. /twirls fingers.

If I had to do it again, i would just have BT4 on its own partition. I can understand the want to have certain programs on Ubuntu as well, but the kernel they have is optimized I think.

If I remember correctly, alot of people that were injecting got higher sustained injection rates using the BT4 version. im pretty sure that it was 8.04 buntu they base bt4 off of, and gnome at that... 

No offense but when you say, any quick way, you come off as a "script kiddie". Something I found out shortly after I cracked my neighbors wifi, illegaly of course, is.. oh snap, his router logged that, and im too stupid to fix that.. Hope he isn't smart enough to notice! I haven't used aircrack sense that day :-)

If you are using this CD for a "legit" purpose, you should know how to do it. If you are using it for.. ya know, the other purpose, then it would benefit you to learn how to do things *properly*. It gave me a good boost of cofidence when I taught myself something as simple as patching my own driver.. I had to do it by hand if I remember, I forgot honestly I had to do alot of stuff. 

Does BT4 require you to be in root? Im not sure if it requires it, but alot of programs require you to have root access to be able to do certain things(like play with your wifi card iirc). So it is just handy to be on a root account. You also shouldn't be stupid enough to do someting to wipe your hard drive... if you know, you are a legit pen tester.
I haven't played with bt4 in months so if my memory fails me, sorry!

---

### Post by Logan1985 on 2009-11-19
What about a compromise and running it in a Virtual Machine in Ubuntu via VirtualBox? This is what I do.

---

### Post by EJeanmaire on 2009-11-19
> **jessiebrownjr said:**
> I patched my own Atheros wifi driver to get it to be able to inject... It was.. a pain, because I was a linux newb. Got aircrack-ng up and operational. It worked.  Once I got that done I installed Backtrack 4 ON my hard drive to see what IT was all about.. it shows up in grub. /twirls fingers.


Where did you get the information to do this... Hmm, and I thought you could only use that one usb wifi card they specify with aircrack-ng.  I guess you learn something new every day.

---

### Post by jessiebrownjr on 2009-11-19
> **EJeanmaire said:**
> Where did you get the information to do this... Hmm, and I thought you could only use that one usb wifi card they specify with aircrack-ng. I guess you learn something new every day.
 
You can use *almost* any wifi card with airmon-ng if the drivers are patched accordingly. The benefit of BT, is all the drivers it contains ARE patched for injection.

---

### Post by sefs on 2009-11-20
BT4 is based on Ubuntu 8.10 and it can be installed to your hard disk.

Type startx at the command prompt of the live cd and then run the graphical installer on the desktop.

The window manager is KDE.

---

### Post by kartook on 2009-12-31
you can refer from here . 

i installed Ubuntu on top i added few applications what ever i need .Just i added repo and installed 

its working like a charm refer :  h**p://bit.ly/7WZUlq

---

### Post by cariboo on 2009-12-31
@kartook

You don't have to obfuscate links if they are concerned with Ubuntu or Linux in general. Full links to other sites are welcome.

---

### Post by HH60Gunner on 2010-02-02
> **jessiebrownjr said:**
> You can use *almost* any wifi card with airmon-ng if the drivers are patched accordingly. The benefit of BT, is all the drivers it contains ARE patched for injection.

Mine worked out of the box in ubuntu.  All I had to do was

ifconfig wlan0 down
airmon-ng start wlan0

from there it should output some little thing about wlan0 up or something like that, and mine says below it monitor mode enabled on Mon0

from there I use the rest of the aircrack-ng suite utilizing Mon0 for packet injections.  I'm still new at this and there may be easier ways, but that's what worked for me on my intel wifi card.

---

### Post by mkvnmtr on 2010-02-02
I use Back Track in a virtual box. It is very easy to instal BT4. That said many ot the apps are in the standard repositories. Some are propitory and some appear to be windows only that they have running in wine. Many I have installed in my regular Ubuntu 9.04.As you gain some skill you will find times that you wish to use the distro from a live boot disk. Somestimes in a normal way and sometimes in a way that it does not touch the hard drive you are working on.If like me you are just learning I would recomend you put the whole thing in wirtual box and then find the apps that you cah download from the repositories to install in your regular Ubuntu to practice with.
 BT4 is quite a learning experience for me and I would recomend it to anyone that wishes to learn about security. Be warned it can be tempting to use it in ways that you should not.

---

### Post by teage3 on 2010-02-09
You could just install the apps and menu in yer current ubuntu install. I would rec-amend  using kde though. works so much better in kde. Its really not that hard to do it. just edit yer menu and add the repo. really thats about all there is to it.

---

