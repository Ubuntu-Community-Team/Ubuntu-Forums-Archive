---
title: "Is Ubuntu Server Edition the right choice for me"
date: 2008-03-30
forum: Server Platforms
---

### Post by sunny7day on 2008-03-30
I'm new to Linux and I want to run a web server. The Ubuntu server edition has LAMP, but should I choose Ubuntu as Web server? It has no GUI.

I understand a server shouldn't have a GUI. But for a starter like me,  I think it's too hard to learn from command line. There are lots of command you have to remember. And if I have to run the server without the GUI, I will use Webmin to do settings on the server.

So here I have another question: How powerful Webmin is? Can it cover most of the configuration on a system just by using a web browser?

I'm lost...:(

---

### Post by WearZeeP on 2008-03-30
You should absolutely use the server edition for servers, and as you said webmin is a pretty good and powerful tool.
If you don't always have a screen and keyboard connected to it, you could set up ssh and use the tty exactly as if you has direct physical access to it.

Other things you can do is to temporarily install X and a lightweight WM like fluxbox and do stuff that you cant really do with a tty (though I think that you can achieve anything with a tty ;) ), and then remove it when you are done.

And regarding webmins powerfullness, it was a while since I used it so I don't rally know, but you can always install it and try it out.

---

### Post by freebeer on 2008-03-30
I guess you really need to look at your needs.  How much traffic are you going to get vs the performance hit you take by running a GUI on top of the server.  But that's rather hard to gauge - especially if you're new to the OS. :wink:

Personally, I run a web site (very little traffic and really only intended as a play/learning experience) on a desktop version.  (6.06 to be precise)  I found it very helpful to run a full-blown GUI on it as it provided me with additional tools to help me learn.  The web sever serves just fine with a GUI on it (perhaps not optimally, but so what?).  You can always optimize later if you find the need to do so later.

---

### Post by WearZeeP on 2008-03-30
Yeah I did that too a while ago, but I used that computer as my normal desktop computer too.
And yeah, not to be off topic, but why do you run such an old version of Ubuntu? (desktop version especially)
I mean even the 6.10 (desktop) version is reaching end-of-life april 25th
You should really upgrade, considering security vulnerabilities and such.

---

### Post by HermanAB on 2008-03-30
"Don't fix it if it ain't broke"

My last mail server ran for 4 years, with zero updates, before I finally replaced the machine when a disk drive failed.

However, don't try that with Windows...

---

### Post by edm1 on 2008-03-30
it may be best to get to know linux using the desktop versions first. Once you have learnt a bit of CLI and how the filesystem is organised you should then move to the server edition.

---

### Post by freebeer on 2008-03-30
It's a little off-topic, but maybe I can answer and still be on-topic...  :D

6.06 isn't broken (as another has said) and since it's a Long Term Support version, it's a perfectly viable platform to run as a server (even if it is a desktop edition).  (See?  Back on topic again. :D)

I also run 7.10 as a PDC and backup server and I'm currently evaluating/playing with 8.04 beta.  Once 8.04 is released, I'll certainly be considering the 6.04 for an upgrade to 8.04, but I'm in no rush.  It's solid, and if it weren't for power failures, it'd probably have an uptime measured in years.

---

### Post by hyper_ch on 2008-03-31
> **freebeer said:**
> I found it very helpful to run a full-blown GUI on it as it provided me with additional tools to help me learn.
What tools for learning how to operate a server?

---

### Post by freebeer on 2008-03-31
Tools?  Well a graphical file manager helps (such as nautilus) as it gave me a visual means of viewing the file structure.  Being (at the time) unfamiliar with the Linux file structure and where stuff is traditionally stored, having that helped me orient myself to the Brave New World.  Command Line is great but reams of scrolling names (when you don't know what a file vs a folder is supposed to look like) is quite a bit to absorb all at once.  I still use graphical tools depending on what I'm attempting to do - sometimes graphical is the best/easiest tool, sometimes the command line is.

---

### Post by BillGod on 2008-03-31
I have been running linux for a long time now.  But if I were going to learn how to run a web server.  I would install server edition.  Desktop edition is only going to teach you a few things.  I am assuming you want to learn how to setup a web server.  If you are just looking to setup a simple website with family and friends accessing it.. heck yeah use desktop.  But if you really want to learn how everything works.  Go for server.  If you don't know how to use ssh start there.  Make sure you setup your lamp server and include ssh (secure shell server)  That will give you access to the computer with no keyboard and monitor.  With text editors like nano editing files is not as hard as it was back in my day with vi.  learn the basics and I am sure you will be pleased.  I run a few websites on a dual 600mhz proc pentium 3 with 256 mb of ram.  It also runs my asterisk server and runs like a champ.  You will get better performance from server edition but like I said its if you want to learn or are you just wanting to set it up and get it working.

ps..  ubuntu forums are the best forums out there.  so many people willing to help.  It should not take long to figure out how to do something.

---

### Post by jda487 on 2008-03-31
I am actually wondering the same thing... I recently picked up a PC to set up as a server for my house.  I'd like to get a remote X server running so I can VNC to it for remote desktop access to the box.  Samba and apache are straight forward enough to setup but my issue has been getting the desktop running.

I installed 7.10 server but I am thinking that it might be easier to install the desktop edition then add the server functions than to install the server edition and add desktopping to it.


Any advice?  I'm sure there are good guides out there for this stuff but I've been looking for a day or so and not found exactly what I wanted.

---

### Post by Poleh on 2008-03-31
> **edm1 said:**
> it may be best to get to know linux using the desktop versions first. Once you have learnt a bit of CLI and how the filesystem is organised you should then move to the server edition.

Sound advice, this is exactly what I did. I ran Gutsy on my laptop for 6 months before I tried the server edition. Not that the server edition was that hard, as I was already familiar with Apache, Mysql and PHP ...

---

