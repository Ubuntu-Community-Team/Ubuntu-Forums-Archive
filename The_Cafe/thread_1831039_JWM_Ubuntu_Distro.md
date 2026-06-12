---
title: "JWM Ubuntu Distro"
date: 2011-08-22
forum: The Cafe
---

### Post by toowoombalinux on 2011-08-22
G'day, {probably posted in wrong section!!!}
I love Puppy Linux - it's a beautiful speed freak!  But there's many things it take's a CLI god to achieve.  So I love Ubuntu as well.
But Puppy does all things well in under 64mbs.  Whereas, Ubuntu uses .... I understand that it's chalk and cheese as Ubu has layers of daemons running to make life easier (which it does).

Why not Lubuntu? ... I run a business and do regular work with a local volunteer charity (a Linux Community) - I need an efficient Desktop ... Lubuntu ain't that - tried it and after many consults to the forum for confiurations gave up!  Puppy's JWM ain't like that.
Looking at Puppy you realise that a well tweaked JWM config and a well teaked ROX file manager can create an easy to use (and efficient) environment to use.

I like pre-configured ... I don't have the time to pre-configure ... I need an efficient and fast workplace/workspace/Desktop ... I like the fire and forget forumula - and many non-computer users do as well.  In my industry I see many computers - and many of them are XP - and many of them would even struggle with Xubuntu (one of the best pre-configured environments for semi-old computers).

I have heard that LXDE is easier to use as it nicely integrates applications (not my experience) and that JWM needs more configuration tweaks to make it run nicely... well Puppy's pre-configured JWM is actually easier than LXDE, and uses less resources.  My mother-in-law (she's 80) uses Puppy JWM - and it was easy to teach her.

But isn't Puppy is now compatible with the Ubuntu repos? .. they call it Puppy Lucid but it ain't fully compatible.  They've incorporated some of the Ubuntu binaries so a number of recently compiled packages for Ubuntu may be transferred over to Puppy ... maybe! (it states that Ubuntu .debs should be left for experimenters).

Minino .... hardware probs! AntiX - nice but I felt that I have to learn to drive again.  Arch ... awesome but time (perhaps patience) and expertise lacking!  And plz don't mention #!...

I experiment with Electronic dance music  - getting Puppy to run Jack-Rack Ardour/Rosegarden, Hydrogen LMMS, tuxguitar and Zynaddsub together with MIDI has been impossible - Ubu does it without thinking!  And installing those apps was a dream in Ubu!

So here's the rub....
Been looking for a JWM Ubuntu distro - can't find one!  So how does one go about finding a group of people who are willing to create this.  As I see an advantage for myself I would contribute 6 years of Puppy Linux experience (however I'm a coding klutz - some bash, wxbasic and xdialog only!  ... plz don't laugh).
I believe that a tweaked JWM Ubuntu would run on a 200MHz 64mbs machine.  I tested JWM on a minCD ubuntu 8.04 install.  The basic setup used around 40mbs - so that goal is possible.

Why this goal?  Cos ppl with that computer spec chuck em out.  I know there's at least 1% of the population is homeless and many of these have families. I've talked to the Salvos and said they would be honoured and relieved if a local group could give reconditioned computers to these families in crisis so at least their kids would have a computer for schooling.  A JWM Ubuntu fits that bill nicely.

Cheer
Martin

PS.  The local Linux Community is not hugely active or has the necessary expertise to achieve an outcome for a project like this ... so I've come here! :P

---

### Post by el_koraco on 2011-08-22
Wouldn't it be easier to take Puppy's config files for JVM, do a minimal Ubuntu install, and add the needed packages to have a Puppy-like setup?

---

### Post by toowoombalinux on 2011-08-22
Tried that - the minimal install requires an internet connection and takes a LONG TIME!  Also, the JWM config files from Puppy cannot be copied directly over - tried it and got a blank unworkable Pinboard - some tweaking needs to be done to make them compatible.
Cheers
Martin

---

### Post by toowoombalinux on 2011-08-22
BTW.  Interested peeps can contact me at: <snip> or on Facebook - Toowoomba Linux
Cheers
Martin

---

### Post by toowoombalinux on 2011-08-25
<bump> in the hope that at least one person may show a little interest in a worthwhile project....

---

### Post by boydrice on 2011-08-25
I think you are in a tough spot.  Getting something to run decently on 64mb of ram is no easy feat (I have an old laptop with 64mb of ram).  There will always be a sacrifice in user-friendliness for a minimum of resources.  Have you looked a Vector Linux Light, it always seemed to strike the right balance between easy to use and light as hell.  Good luck.

---

### Post by VOT Productions on 2011-08-25
Xubuntu?

---

### Post by smellyman on 2011-08-25
You might give [AnitX]("http://antix.mepis.org/index.php?title=Main_Page") a try.

It is fluxbox/icewm and can run (supposedly) on 64 megs.  I have run it easily on 128 so I can see it being capable on 64 although probably not ideal

It's a Mepis spin so is Debian based.  Might be what you are looking for.

EDIT:  Oops  I see you mention AnitX and it's like learning to drive.  I think it's hard to be more straight forward than a Debian based distro.  Icewm is pretty similar to Jwm and fluxbox is another nice alternative.

---

### Post by toowoombalinux on 2011-09-10
G'day,
AntiX is good - I tried it when it first came out and my notes read "like learning to drive" - forgotten why ... yes it's debian based so it should be familiar....

Anyway, where's there's a will there's a way - I will be trying to do a local flavoured JWM Ubuntu distro.  AntiX would be preferable but being able to carry all the repositories with you on a portable HD (as in Ubuntu) is very handy; especially for install-fests.

Keep ya updated..
Cheers

---

### Post by alexan on 2011-09-10
With the good 'ol Karmic all you need was


sudo apt-get install jwm menu pcmanfm
(then you could choose to use pcman of nautilus to draw the desktop).
Now, not sure if it still work

---

### Post by ddnev45 on 2011-09-10
Check this out:

[http://crunchbanglinux.org/forums/topic/12751/jwm-config/](http://crunchbanglinux.org/forums/topic/12751/jwm-config/)

---

### Post by keithpeter on 2011-09-11
> **toowoombalinux said:**
> I experiment with Electronic dance music  - getting Puppy to run Jack-Rack Ardour/Rosegarden, Hydrogen LMMS, tuxguitar and Zynaddsub together with MIDI has been impossible - Ubu does it without thinking!  And installing those apps was a dream in Ubu!

Hello toowoombalinux and all

[http://puredyne.org/](http://puredyne.org/)

Their [minimum target spec]("http://puredyne.466513.n3.nabble.com/puredyne-Ubuntu-Studio-will-use-XFCE-for-11-10-collaboration-tc2832886.html#a2973070") is P3, 800MHz, 384Mb which is a bit over yours but jack + a huge range of audio / performance software (including supercollider, fluxus and PD) is configured to work out of the box.

I've simulated 128Mb ram by using a modeline and AntiX will run all major web/ office functions on 128Mb, P4ish including printing a large openoffice/libreoffice doc. I got Audacity running as well, but the ability to record to hard drive without glitches is going to depend on processor speed...

---

### Post by toowoombalinux on 2011-09-13
Checking out Puredyne - looks interesting....
Cheers
Martin

PS. From the Ubuntu MiniCD I have got JWM/ROX working fine - but very ugly and not a productive workspace.  Integrating Puppy config files into it is a challenge indeed as Puppy works on the basis that your the root user (Puppy has configured JWM into a nicely productive workspace).  And changing that useless menu ... very difficult to find anything of worth - a challenge indeed!

PPS. The Crunchbang .jwmrc config looks nice but it's still a manual configuration - Puppy configures automatically which is what I'm after

---

