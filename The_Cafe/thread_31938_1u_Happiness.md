---
title: "1u Happiness"
date: 2005-05-05
forum: The Cafe
---

### Post by kvidell on 2005-05-05
I just remembered!!
I have two dual proc P4 1u servers in my garage :-D
Hawtness.

Does Ubuntu make for a good webserver environment? I've only used it as a laptop OS so far.

Time to find a spare CDrom drive to plug in to them and install Hoary! (They don't have cdrom drives :-\ stupid Transmeta buying weird hardware)
- Kev

---

### Post by WildTangent on 2005-05-05
how does one just forget about dual CPU servers?! :? 

-Wild

---

### Post by jimcooncat on 2005-05-05
If adding hardware's a pain, and there's some kind of operating system on there, maybe the following article will help. Haven't used it yet myself, just saw it today while avoiding work^W^W researching online.

Install GNU/Linux without any CD, floppy, USB-key, nor any other removable media
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

---

### Post by TravisNewman on 2005-05-05
Seriously. Person-With-Creepy-Avatar makes a point (that avatar rocks dude). I know that I certainly couldn't forget about that.

But Ubuntu is easy to set up as a server, but for production level servers I'd suggest Debian or FreeBSD, or if you're feeling adventurous, Gentoo. Since these were forgotten servers, they're obviously not production servers, so you should give Ubuntu a shot.

---

### Post by kvidell on 2005-05-05
Haha... Well...
I got them two days before I went on vacation for two weeks, and when I got back my family had moved them from where I left them to our garagey thing, so I kinda forgot they were there.

Also, I'd gotten frusturated with them when I did play with them because as it turns out, they were set to boot with video forwarded to a serial device, and I've no null modem cables handy.

But yea... by no means are these for anything fancier than letting my friends and colleagues have a place to get comfy with a gui-less environment, and a simple personal webserver.

And don't tell me to go back to debian right now for any reason :-\ I'm still feeling angsty about it after it trashed my T30. (well... I trashed the T30 because of Debian not wanting to work and me not knowing exactly how to fix what was wrong.)

---

### Post by TravisNewman on 2005-05-05
Well, if Debian is intimidating, FreeBSD may be as well.

So yeah, give Ubuntu a shot on those babies.

---

### Post by poofyhairguy on 2005-05-05
[QUOTE=kvidell]
Time to find a spare CDrom drive to plug in to them and install Hoary! (They don't have cdrom drives :-\ stupid Transmeta buying weird hardware)
- Kev[/QUOTE]

They don't have cdrom drives? No wonder you forgot about it.

---

### Post by kvidell on 2005-06-30
So..
I _finally_ got around to doing something with these damn things.
One of them is completely dead, so I harvested it's ram (two twigs of ECC 512mb Kingston) and added it to the one that works just fine... cept then none of the interfaces work so I guess that ram's crap too.

Back down to a gig in that one, oh pity :-P hehe.

Found a spare CD drive and IDE cable (The one I harvested off the hd from the dead server ;)) and installed Ubuntu in "Server" mode.
Which turned out to suck because I wanted X and just installing xserver-xorg didn't do exactly what I wanted, so I ended up apt-get'ing ubuntu-desktop.. Ah well.

Now all I need to know is what ubuntu defines the default runlevels as, and how do I change the one that's booted in to by default.

I'd like to boot in to the runlevel that starts all services but the X server. Is that 2 or 3? How do I set it?

Thanks!
BTW: Blazing nice as a dual proc :-D Godbless the repo's having an smp kernel.
- Kev

---

### Post by nocturn on 2005-06-30
[QUOTE=panickedthumb]Well, if Debian is intimidating, FreeBSD may be as well.

So yeah, give Ubuntu a shot on those babies.[/QUOTE]

I used to have a FreeBSD server, and it is very good.  But it lacks binary security updates and 'rebuilding world' is intimidating as well as time consuming.

---

### Post by WildTangent on 2005-06-30
nice job getting at least one working. can i have it?  ;-)  O:) 

-Wild

---

### Post by kvidell on 2005-07-01
I just upgraded it to Breezy... oh my does that run nice :-D
Since, ya know, I don't need X to actually work on it... just forwarding the display to my ssh clients (Like my laptops).

This is kind of cool... It only has a 30 gig drive though so it can't be my little samba file server. I'll need to figure out how to get my other drive in it.

---

### Post by WildTangent on 2005-07-01
[QUOTE=kvidell]This is kind of cool... It only has a 30 gig drive though so it can't be my little samba file server. I'll need to figure out how to get my other drive in it.[/QUOTE]
stuff it in the floppy drive bay if it has one

-Wild

---

