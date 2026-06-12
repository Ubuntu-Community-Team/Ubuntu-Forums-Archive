---
title: "mandriva 2006's interactive firewall"
date: 2005-11-21
forum: The Cafe
---

### Post by uberlinux on 2005-11-21
Why dosent ubuntu have it? it is slick! [IMG]http://madpenguin.org/images/reviews/mandriva2006/portscan.jpg[/IMG]

---

### Post by ssam on 2005-11-21
have you tried firestarter?

---

### Post by uberlinux on 2005-11-21
[QUOTE=ssam]have you tried firestarter?[/QUOTE]
firestarter is what I currently use, and it is wack compared to the firewall in mandriva.

---

### Post by GeneralZod on 2005-11-21
Do you know if it is a GTK app? If not, it is unfortunately unlikely to be adopted in Ubuntu, but Kubuntu is a possibility.

Also, sadly, there seems to be a strong [NIH](http://en.wikipedia.org/wiki/Not_invented_here) ethic between distros that seems to stop a lot of distro's own tools being re-badged and adopted by others.

---

### Post by sal on 2005-11-21
yes, i saw this on the OSDir screenshots when it came it. i think it is a good idea. i think it help people that are coming from windows out because, although, when the system is secure, all you really need to do is read your logs, the windows user would have a hard time picking up on this concept. maybe i should say the "mom and pop" windows user, because there are a lot of security minded windows users.

but the fact that it is interactive and tells the user what is going on is good because the beginer need these things till they get better at handling the os on there own.

---

### Post by stimpack on 2005-11-21
Not just the beginner, I am assuming it is also interactive for outbound traffic?, this is sorely missed at the moment, no way to stop applications 'phoning home'.

---

### Post by sal on 2005-11-21
yes, this is why i say it is a good thing, makes the day a little easyer.

i like it, and i would love them to implament it into dapper.

the thing is so many windows users i try and get to switch to ubuntu/kubuntu don't like the idea that they don't know whats going on well they are on the internet. they are used to the windows based firewalls that show them alerts.
so, when they don't see alerts they think it's not working. this would help to easy there minds out.

---

### Post by uberlinux on 2005-11-21
well, do any of you wizards know what the app is called, where it is found, maybe?  I could always try to make a .deb of it and install, share it that way.

---

### Post by uberlinux on 2005-11-21
[http://rpm.pbone.net/index.php3/stat/4/idpl/2252905/com/mandi-ifw-0.7.4-1mdk.i586.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/2252905/com/mandi-ifw-0.7.4-1mdk.i586.rpm.html)
this seems to be part of it.  anyone want to help me unravel this???

---

### Post by uberlinux on 2005-11-21
[http://rpm.pbone.net/index.php3/stat/4/idpl/2364592/com/mandi-0.7.4-1mdk.i586.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/2364592/com/mandi-0.7.4-1mdk.i586.rpm.html) I think this is the daemon.
anyone any good at making debs???

---

### Post by uberlinux on 2005-11-21
Well, I tried alien to no avail.  Next step is to compile the two components from scratch, but this will probably have to be ported somehow, and I'm no coder, so hopefully someone that knows what they are doing will give it a try.

---

### Post by uberlinux on 2005-11-21
dammit!  I cant find the code anywhere!

---

### Post by sapo on 2005-11-21
I hate windows poping up in my desktop.. Firestarter for great justice :D

---

### Post by uberlinux on 2005-11-21
[QUOTE=sapo]I hate windows poping up in my desktop.. Firestarter for great justice :D[/QUOTE]
I love having the option of windows poping up on my desktop.  Firestarter dosent suffice as something that is reassuring to people who are leaving the windows/zonealarm world, if you don't believe me, ask my skiddish family members who want reassurance that they are actively being saved from certain doom:lol:

---

### Post by jdong on 2005-11-21
It appears to be dbus based... pretty neat for the interactive freaks, but for most of us regular firewall rules would work just as well with a nice viewer like Firestarter.

I hope to see this at least in Universe.

---

### Post by uberlinux on 2005-11-21
For real, I think it looks very 'proffessional' and people coming from windows will certainly find it reassuring. Kudo's to the Mandrake people on this one!
Jdong, your the backports leader, you should get this one on there!

---

### Post by jdong on 2005-11-22
Backports means that it has to be in **Dapper** before I can do anything about it... MOTU's who you're looking to bug ;)

---

### Post by rpaller on 2005-11-22
Have you tried fwbuilder to piece together your iptables and then frontend it with Firestarter?

I grabbed fwbuilder so I can improve my iptables setup for my WRT54G router running openwrt firmware. I have yet to see what I can do with it on Ubuntu yet.

---

### Post by uberlinux on 2005-11-22
[QUOTE=rpaller]Have you tried fwbuilder to piece together your iptables and then frontend it with Firestarter?

I grabbed fwbuilder so I can improve my iptables setup for my WRT54G router running openwrt firmware. I have yet to see what I can do with it on Ubuntu yet.[/QUOTE]
The whole reason I want Mandriva's interactive firewall is because it seems a lot like zonealarm, and windows users like that type of reassurance.

---

### Post by Burgundavia on 2005-11-22
I would not want anything like that on any desktop I give to my parents. It is lovely for us becuase we know what to do, but they don't.

Case in point, my father removed Zonealarm because of the annoying pop-up messages.

Corey

---

### Post by uberlinux on 2005-11-22
everyone I've dragged over has wanted something like it, I don't know...

---

