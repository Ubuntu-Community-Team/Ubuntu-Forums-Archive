---
title: "Request: Azureus 2.3.0.2"
date: 2005-05-26
forum: Ubuntu Backports
---

### Post by tzutolin on 2005-05-26
A new one was just released.
Can we have it in the backports? :smile:

Changelog: [http://azureus.sourceforge.net/changelog.php?version=2.3.0.2](http://azureus.sourceforge.net/changelog.php?version=2.3.0.2)

---

### Post by ow50 on 2005-05-26
After it appears in [debian unstable](http://packages.debian.org/unstable/net/azureus), I'll build it.

---

### Post by tzutolin on 2005-05-26
[QUOTE=ow50]After it appears in [debian unstable](http://packages.debian.org/unstable/net/azureus), I'll build it.[/QUOTE]
 Thanks, ow50!!! :)

---

### Post by ubuntu_demon on 2005-05-27
in the meantime you can just grab the jar file from sourceforge 

[http://prdownloads.sourceforge.net/azureus/Azureus2.3.0.2.jar?download](http://prdownloads.sourceforge.net/azureus/Azureus2.3.0.2.jar?download)

and copy Azureus2.3.0.2.jar over your old jar. like this :

$ sudo cp Azureus2.3.0.2.jar /usr/share/java/Azureus2.jar

It works like a charm :)

---

### Post by fng on 2005-05-27
aha :)
It's a petty the auto-updater in azureus doesnt do this automaticly

thnx anyway, it now works :)

---

### Post by bnutting on 2005-05-27
The auto-update works in Windows, I wonder why it would not work in Linux? Could it be a permissions thing?

---

### Post by the_clown on 2005-05-27
[QUOTE=bnutting]The auto-update works in Windows, I wonder why it would not work in Linux? Could it be a permissions thing?[/QUOTE]
 The auto-updater worked for me, when I ran Azureus with gksudo

---

### Post by KRavEN on 2005-05-27
[QUOTE=the_clown]The auto-updater worked for me, when I ran Azureus with gksudo[/QUOTE]
 yeah, it is a permissions thing.  I have the same issue and I installed it by hand.  It only gets updated if you start it via gksudo or you can sudo azureus from terminal.

---

### Post by gubuntu on 2005-05-27
Still a newbie, but I think I'm having a similar problem.

When I open azureus and start auto update, I get the message

version 1.3.1 of plugin 'azplugins' failed to install
azplugins_1.3.1.jar permission denied

Untill this morning azureus was working perfectly, now all my indicators went yellow.

I hope this is somthing simple that is just being overlooked by a youngblood.

Thank you in advance for your help.

---

### Post by gubuntu on 2005-05-28
Found a similar problem in a different forum.

Started azureus as sudo. Updated just fine.

Changed user, working great.

---

### Post by Majlo on 2005-06-08
[QUOTE=ow50]After it appears in [debian unstable](http://packages.debian.org/unstable/net/azureus), I'll build it.[/QUOTE]

Azureus 2.3.0.2 is by now in debian unstable

[http://packages.debian.org/unstable/net/azureus](http://packages.debian.org/unstable/net/azureus)

---

### Post by jdong on 2005-06-08
ok, built and uploading to Staging. Required a new library (libseda-java) that's not in Ubuntu's archives at all, so I imported it from Debian Sid.

Since it's not used at all in Ubuntu, there's no chance of conflict :)

---

### Post by ubuntu_demon on 2005-06-08
great!

---

### Post by Majlo on 2005-06-08
[QUOTE=jdong]ok, built and uploading to Staging. Required a new library (libseda-java) that's not in Ubuntu's archives at all, so I imported it from Debian Sid.

Since it's not used at all in Ubuntu, there's no chance of conflict :)[/QUOTE]

Thanks jdong :-)

Lets go testing ....

---

### Post by jdong on 2005-06-08
WOW, 2.3.0.2 is much more RAM-conserving :)

---

### Post by ubuntu_demon on 2005-06-09
[QUOTE=jdong]WOW, 2.3.0.2 is much more RAM-conserving :)[/QUOTE]
 I run azureus from backports (not staging) with the 2.3.0.2 jar "on top"

according to gnome-system-monitor it uses 536 mb (including virtual memory), according to top it uses 57.5 % (of 512 mb -> 294.4 mb) 

I'm very pleased with it because it runs smoothly on my p3 826 mhz with 512 mb ram. But it's still a bit heavy.  Maybe the new backports version behaves a bit better :)

---

### Post by jdong on 2005-06-10
Perhaps. I use Free RAM and Swap monitoring, and daily performance feel to measure its hogginess.

---

### Post by Amaranth on 2005-06-10
I thought you weren't going to 'backport' things that weren't in breezy anymore? After all, it's not really a backport if you build it yourself or get it from somewhere other than the latest ubuntu. :)

---

### Post by jdong on 2005-06-10
It won't have a chance of making it into Breezy because of the no-binary-uploads rule, so I find it fairly safe to do. If you're really gonna complain, I guess I could move it over to Extras, but since it IS a Debian package after all, I rather keep it in Backports for now.

---

### Post by Amaranth on 2005-06-10
[QUOTE=jdong]It won't have a chance of making it into Breezy because of the no-binary-uploads rule, so I find it fairly safe to do. If you're really gonna complain, I guess I could move it over to Extras, but since it IS a Debian package after all, I rather keep it in Backports for now.[/QUOTE]
 I thought Azureus was close to compiling on gcj. Oh well, I don't use backports anyway. :)

---

