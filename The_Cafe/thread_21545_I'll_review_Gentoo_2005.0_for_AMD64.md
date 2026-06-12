---
title: "I'll review Gentoo 2005.0 for AMD64"
date: 2005-03-22
forum: The Cafe
---

### Post by jdong on 2005-03-22
Spring break is coming up soon. If Gentoo 2005.0 for AMD64 gets released during this timeframe, I'll certainly give it a test  -- from what I've read, 2005.0 changes the way multilib/mixed 32/64-bit is handled on Gentoo. For example, WINE's ebuild has 'ABI=x86' set, which will build a 32-bit WINE binary.

This is certainly well worth my time to review.

---

### Post by BWF89 on 2005-03-22
I thought Gentoo didn't have any version numbers. You just updated it.

---

### Post by TravisNewman on 2005-03-22
It's mostly in the way the default initial bootstrap and initial installation changes things. There are definitely differences between versions that you don't automatically get when updating.

---

### Post by akurashy on 2005-03-22
I heard that gentoo 2005.0 going to have a installer *dunno if it true*

---

### Post by TravisNewman on 2005-03-22
Whoa! That's strange! Now, if there's an installer that does all the compiling, guides you through setting the cflags and the use flags, and guides you through kernel compiling and initial software selection, AND DOES IT WELL, then I'll be all for it. Though there are plenty of people who will still prefer to do it manually-- since the same work is being done, it probably wont' change much in the way of time to install, but newer users who want a distro compiled for their system will love this.

---

### Post by Thief- on 2005-03-22
Gentoo users are so **goshdarn** pretentious that I wouldn't want to use it even if it was possible to install it.

---

### Post by HungSquirrel on 2005-03-22
It's possible to install it...it's just not possible to install it without running into dependency problems or mirrors being down.  Emerge is highly overrated.

---

### Post by Thief- on 2005-03-22
[QUOTE=Thief-]Gentoo users are so **goshdarn** pretentious that I wouldn't want to use it even if it was possible to install it.[/QUOTE]
 Of course you can install it. I was using hyperbole.

Still, the whole "no installer" thing is ridiculous.

---

### Post by jdong on 2005-03-22
2005.0 adds a number of profile updates, such as udev+2.6 by default. On AMD64, it also drastically changes how multilib (32-bit+64-bit mixing) is handled through Portage (for the better).

I'd like to see if this actually makes using 64-bit Linux practical for me, or if it's just a hype.

---

### Post by TravisNewman on 2005-03-22
hmm. I used it for 2 years or so-- never ran into my mirrors being down, ran into less dependency issues there than I do with apt. 

I don't think it's pretentious. It's customizable! Gentoo USERS can get pretty pretentious, but it's quite a versatile distro.

---

### Post by poofyhairguy on 2005-03-23
[QUOTE=jdong]2005.0 adds a number of profile updates, such as udev+2.6 by default. On AMD64, it also drastically changes how multilib (32-bit+64-bit mixing) is handled through Portage (for the better).

I'd like to see if this actually makes using 64-bit Linux practical for me, or if it's just a hype.[/QUOTE]

I look forward to your reviews nowadays. I can't wait for the Suse 9.3 one sometime.

---

### Post by jdong on 2005-03-23
I'm happy to announce that I got my hands on 2005.0 AMD64 stage3 tarballs + minimal livecd's.

I'll proceed to install it today after school, around 3:00 PM....  I'll blog about it, like usual, probably under a brand-new thread, since this one is tainted already.

---

### Post by jdodson on 2005-03-23
[QUOTE=jdong]I'll proceed to install it today after school, around 3:00 PM....  I'll blog about it, like usual, probably under a brand-new thread, since this one is tainted already.[/QUOTE]

what was your take on fedora core 3?

-1 Offtopic :twisted:

---

### Post by jdong on 2005-03-23
Emerged a quick X11+fluxbox system just for reviewing purposes... It feels like the same old Gentoo.

WINE emerges properly now, but other outstanding issues, like Flash, are still not resolved. Gentoo-dev-sources newer than 2.6.9 all have compilation problems... As I said, same old Gentoo!

I certainly won't be relying on this OS... Back to Ubuntu.

---

### Post by dillweed on 2005-03-23
I'm not here to defend Gentoo, as I've been using Ubuntu for awhile now and like what I see.  The only beef that I have with ubuntu is that sometimes I'm not really sure what is going on with my system.  I love the fact that with gentoo I know exactly what is being installed and where it is going, I know what services are being started and why, and the documentation for gentoo is outstanding, at least in my opinion.  (Boy long sentence) Not to say that ubuntu doesn't also have good documentation and the #ubuntu in freenode is helpful, albeit busy, but the documentation here seems somewhat disorganized for me.  

At any rate, I've never had a problem with mirrors being down or slow in gentoo.  Ubuntu is a great desktop distro, but needs some work in the server area, though I don't think it is targeting the server market.  I don't mind tweaking system files and others like to have their desktop setup right away.  But as the Poles say "Kazdy po swojemu."  Use the operating system that you like and works for you and makes your belly button turn green.  :-P 

So there you have it folks my 2 bucks.

PS remember these are my opinions

Dillweed

---

### Post by defkewl on 2005-03-24
[QUOTE=Thief-]Of course you can install it. I was using hyperbole.

Still, the whole "no installer" thing is ridiculous.[/QUOTE]

Do you always have to say ridiculous for everything that does not meet your preference/criteria? For you perhaps it is, but for others they say it's a lifesaver.

---

