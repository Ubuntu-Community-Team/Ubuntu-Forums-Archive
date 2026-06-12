---
title: "would i even notice?"
date: 2006-07-26
forum: The Cafe
---

### Post by fuscia on 2006-07-26
i've been looking at a bunch of linux and BSD stuff, but i've got to wonder if an end user like me would even notice the difference between a BSD and a linux (if they both use KDE, for example, there's not much difference for me to see). if i could notice, what would the differences be?

---

### Post by chickengirl on 2006-07-26
I think BSD organizes its filesystem a bit differently, and the package management is different (source-based, a la Gentoo, if I understand correctly)

---

### Post by scxtt on 2006-07-26
i agree - this is what i noticed when i installed FreeBSD 6.0 -- gnome looked the same, but it used "ports" to install software, compiling it from 'scratch' ...

so, it just depends on how you want to 'build' your distro, from scratch (in a gentoo/bsd way) or more 'pre-compiled' (ubuntu way) ...

personally, i just want to be able to 'easily' install any software i need - i'm not all about those extra millisecs a custom compiled program will give me, not that there's anything wrong with being ...

---

### Post by xtacocorex on 2006-07-26
If you decided to cat a file in /proc in BSD you'll get a bunch of binary whereas in Linux, you'll get ASCII text as Linus wanted it that way.

---

### Post by Arisna on 2006-07-26
With BSD, as with a Debian based system, you have the option of using either binary or source packages.  Gentoo's source-based Portage package manager is based on BSD's Ports system.  The commands, of course, are different.

From my experience, FreeBSD is significantly harder to configure for desktop usage than most Linux distros.  There is a FreeBSD-based project called PC-BSD that automatically installs KDE and is fairly user-friendly from what I've read on these forums.  I tried to install an earlier version of it a year ago, but the installation got stuck or something.

More objectively, you'd run into differences in hardware support and subtle differences in command line utilities.  chickengirl is correct about filesystem differences, as well--the most significant I can think of is that user files are by default stored in /usr/home rather than /home.

---

### Post by fuscia on 2006-07-26
it does seem that the hardware support and installation would be a big pain in the butt with the BSDs. i'm sure appreciating the 'user friendliness' of ubuntu, but i was wondering if there were something i was missing out on in the BSDs. i enjoyed playing with puppy and DSL, though the novelty would wear off quickly.

chickengirl, are you still walking on the 'dark side'?

---

### Post by chickengirl on 2006-07-26
> **fuscia said:**
> chickengirl, are you still walking on the 'dark side'?

Alas, no, it got to be too much for my eyes. I'm sure I'll be back, though -- Once you start down the dark path, forever will it dominate your destiny. Consume you it will.

---

### Post by RavenOfOdin on 2006-07-26
> **chickengirl said:**
> I think BSD organizes its filesystem a bit differently, and the package management is different (source-based, a la Gentoo, if I understand correctly)

emerge and kldload are two applications that spring to mind. . .

> **Arisna said:**
> 
From my experience, FreeBSD is significantly harder to configure for desktop usage than most Linux distros.  There is a FreeBSD-based project called PC-BSD that automatically installs KDE and is fairly user-friendly from what I've read on these forums.  I tried to install an earlier version of it a year ago, but the installation got stuck or something.


I think FreeBSD/PPC isn't as far along as Debian/PPC yet. . .something to do with BMAC and usb problems.

I was going to install it from their 700-ish MB .iso but decided against that.

> **chickengirl said:**
> Alas, no, it got to be too much for my eyes. I'm sure I'll be back, though -- Once you start down the dark path, forever will it dominate your destiny. Consume you it will.

*confused*

Yoda?

:D

---

### Post by IYY on 2006-07-26
Once everything is installed and configured, it looks the same.

---

### Post by fuscia on 2006-07-27
> **IYY said:**
> Once everything is installed and configured, it looks the same.

that's what i thought.

---

### Post by G Morgan on 2006-07-27
A big difference is as standard it uses a different shell to BASH (TCSH IIRC) but that can be changed in a few seconds. The documentation is awesome and centralised so you have no problem with getting things running.

As for the comparisons between Portage and Ports. Ports inspired Portage but there is no shared code. Both also allow binary installations. Once you've got your basic enviroment setup (which for me was replacing TCSH with BASH and installing VIM and replacing VI with it) and got your head around Ports (including updates which are done manually though there are simple scripts that can do it for you) its easy enough to use.

Personally I'd run it in VMware Player/Server/Workstation and get your mind around the points I've mentioned then take the plunge. I prefered Gentoo though, it had more housekeeping tools that didn't take away that much power from you.

---

### Post by jonathansizz on 2006-07-30
> From my experience, FreeBSD is significantly harder to configure for desktop usage than most Linux distros. 

Not really. It's harder than Ubuntu, SUSE and Fedora, but no harder than Debian and easier than Slackware and Gentoo.

The installer is curses-based but works fine. You can install multimedia codecs with one command. It has good wireless support. It's got a great package management system, with over 15,000 entries. It's easy to upgrade the whole OS. Excellent documentation.

The downsides compared to linux are that there's no fglrx driver for FreeBSD, so you have to use the radeon one, which gives worse performance (if you're stuck with ATI, that is). Another notable difference is that you have to use an older version of Flash, which is incompatible with many websites. Also, hardware does take a bit longer to be supported.

There are desktop-specific spin-offs being developed - PC-BSD and DesktopBSD, which are worth trying out if you have a spare partition. These take care of all the configuration chores for you.

---

### Post by mips on 2006-07-30
Heard comments that BSD seems much faster, cannot confirm this 'yet' as I still have to do an install.

---

### Post by G Morgan on 2006-07-30
> **mips said:**
> Heard comments that BSD seems much faster, cannot confirm this 'yet' as I still have to do an install.

I think BSD was more stable but comparing stability between Linux and BSD is like comparing tap water with bottled water (on anything bar health risks, bottled water is horrendous here) in that their both the same bloody thing (at least where I come from).

I didn't find it any faster than Gentoo and I do prefer portage to ports.


//edit - by the way there is a Gentoo/BSD project out there.//

---

### Post by Engnome on 2006-07-30
> **mips said:**
> Heard comments that BSD seems much faster, cannot confirm this 'yet' as I still have to do an install.

I've tried PC-BSD and DesktopBSD and can confirm speed gain, however I couldn't stand kde so it was soon overwritten by some other linux dist I wanted to try.

Any easy BSD that uses gnome or has it easyily installable? How is gnome supported? I get the feeling *BSD is only KDE.

---

### Post by scxtt on 2006-07-30
FreeBSD uses Gnome, by default, but i think KDE is an option (can't remember) ... it's not the *latest* Gnome, but it's certainly stable ...

---

### Post by Engnome on 2006-07-30
> **scxtt said:**
> FreeBSD uses Gnome, by default, but i think KDE is an option (can't remember) ... it's not the *latest* Gnome, but it's certainly stable ...

I thought FreeBSD came without a DE and you had to install it yourself?

---

### Post by scxtt on 2006-07-30
when you're installing it, you can choose which DE you want to install -- i know for a fact that after install, i was greeted by gnome (which is what i prefer), but i vaguely remember being able to choose KDE (don't hold me to that :p) ...

i'd still be using FreeBSD if it had better ATI support, tho i'm definitely guilty of not putting enough effort into it ...

---

### Post by jonathansizz on 2006-07-30
As regards the DE - you can install GNOME, KDE or whichever other window managers you like off the CD during install. FreeBSD usually releases a new version every 4 or 5 months, so doing it this way won't leave you *too* out-of-date. 

Alternatively, you can install the latest version over the internet after you have installed the OS. Right now, we have KDE 3.5.3, GNOME 2.14.2, Fluxbox 1.0 rc2, etc.

Software management is really easy:

# portinstall x11/gnome2

would do the trick


Say you want to upgrade Firefox:
# portsnap fetch update

updates the database. Then

# portupgrade firefox

upgrades firefox


You can see what's available [here]("http://www.freebsd.org/ports/index.html")

---

