---
title: "Distro-shopping, need input."
date: 2010-02-02
forum: The Cafe
---

### Post by Silent Warrior on 2010-02-02
I have two desktops at home - one running Ubuntu/XP, the other a sort of pre-scrap-heap, currently running PCLinuxOS (Gnome). I'm considering moving to a more suitable distribution - I have nothing against PCLOS, besides it installing a ton of drivers and stuff through Mandriva's user-friendly ideals that I just don't need (like 50+ printer-drivers...), and removing them seems to invite full system-wide breakdown. In short, I want to lighten the load a bit. (Not necessarily switching to XFCE/LXDE/other lightweighters, but I can live with that.)

Specs (in flux - I'm somewhat planning a system upgrade of the main machine during the next five years, and the hardware from that will end up in the concerned box):
ASUS P4T-E
Pentium4 2GHz
512 Mb RDRAM
ATI Radeon 9600 Pro (might be 512 Mb - haven't checked in a while, could be 256)
Ages-old TFT screen that isn't detected properly - 15" supposedly capable of 1024x768, though not presently allowed to go there. (Samsung SyncMaster [something]c, integrated speakers)
Creative SoundBlaster Live! 5.1 Platinum (currently no speakers attached - working on that on the side, headphones until further notice)
80 Gb HDD (in other words - space is not an issue)
Realtek 8169

Requirements/preferences:
Graphical package manager (req)
Rolling release model (pref) :) This kind of thing still hasn't caused me any trouble on desktop-PCs. I find it more convenient - and let's not argue about its merits/downsides for now.
More than one or two DEs available (req)
Binary>=source-packages (req - customizable though they are, source-based distributions take too much effort/time to update/maintain to justify use for this purpose, but some compilation is definitely acceptable)
Customizability (req), little extra stuff installed and not traumatizing to remove post-install

Usage-scenarios:
Checking game-FAQs or other light text-processing (gedit/OpenOffice/Firefox/Misc. browser)
Running Wesnoth-SVN, and compiling it ;)
Running a few older DOS-era games through DOSbox - Wing Commander and the like
... Guess that's it. Besides listening to a limited stock of music with Amarok, but I now mean to switch to Audacious on that machine. Or maybe the upcoming Bangarang?

So, what can you recommend? I'm currently testing Arch with VBox - falls flat due to the lack of graphical package management, but the rest of the package-related stuff is absolutely a-OK by me. Nice mix of binary repositories and source-tarballs bagged through AUR. It is rather a lot of trouble to get set up to my liking, though, without browsing through Synaptic and see what's available. (pacman -Ss [*] | less isn't doing it for me...) I'm not sure I want to go through all that bother just to discover I missed something crucial and end up with a brick because I was looking away for ten seconds while updates were applied.
Gentoo and other pure source-distros are out, period, as I outlined above. Sabayon seems to cover some kind of middle-ground though, and I took some liking to it as I was testing it a few months ago. Probable candidate. Thoughts? Opinions? Hate-mail? Mail-bombs?
I have not tried Slackware - well, I tried installing it once, and failed.
PuppyLinux and the like might be an option, though this is DEFINITELY going to be installed to HD - no monkey-business with USB-sticks for this setup, besides for shuffling files between the two boxes.

The by-the-way about future upgrading means that a too specialized configuration would cause a bit of bother in the impending transition, unless I go for the safe option of a reinstall - which makes Arch in my eyes a less-than-optimal choice (unfortunately - would be almost perfect otherwise). Whether I'd carry over the harddrives from the other computer is not decided at the moment, but doing so (and going full SATA - Ubuntu occupies an IDE-drive, and the other drives are pretty darn full, to say the least) would increase the likelyhood of me going for a reinstall rather than just booting post-upgrade and crossing my fingers (improving Arch's outlook, but the package-management is still a factor).

---

### Post by L4U on 2010-02-02
Mint.

For your setup, I'd recommend their Xfce version.  It's what I'm currently using and it rocks.

---

### Post by Pogeymanz on 2010-02-02
I know you are leaning against Arch, but there is actually a graphical frontend to pacman called "Shaman." It is very Synaptic-esque. So if that was one of the main reasons for not liking it, Shaman might fix it.

Also, there are Arch packages/scripts around that will save all of your current configs so that you can reinstall in only the time it takes to re-download packages. I haven't used any of them, but I can't imagine it's too hard to even write such a script.

I didn't like Sabayon. Way too much going on for my taste. I much preferred Gentoo, which you don't want.

I say, if Arch isn't your cup of tea, try Sidux. I enjoyed the hell out of Sidux when I used it. It's basically Debian Sid, but with a few compatibility tweaks here and there so that stuff isn't ALWAYS breaking.

Other than those I suggest PCLOS and Debian Testing.

---

### Post by NightwishFan on 2010-02-02
I vote for Debian. As said above, Debian can be a rolling release, and I have run it on some very old computers still using Gnome.

---

### Post by HappinessNow on 2010-02-02
Puppy or any puppy derivative, like MacPup Opera or MacPup Foxy...I wonder if anybody has put together a ChromePup yet?

---

### Post by Tibuda on 2010-02-02
About browsing Arch packages, I browse them from the web ([http://archlinux.org/packages](http://archlinux.org/packages)) and them install using pacman. You could also install gtkpacman or shaman, but it is not really needed.

---

### Post by Psumi on 2010-02-02
wattOS?

---

### Post by Silent Warrior on 2010-02-03
Ah, Shaman looks like JUST the thing to make Arch a very serious contender! A pity I don't get it to work its magic (probably due to unexpected locale-settings - I want to be Swedish, see - compiling gives me all sorts of perl-warnings). I don't have to mess with the locales, I suppose, but I will bloody well want my keyboard outputting the right glyphs... Maybe I'll figure it out if I poke at it enough, but you might like to know it took me days to get a bootsplash - and now there's a warning that suggests I'm trying to load udev twice. :-k
I'll certainly agree with anyone who says that Arch is the way to go to "get what you need", though - as long as you know WHAT that is.

Sidux is looking good (Debian, with rolling releases! OMGWTF!), Puppy with Woof looks "exciting" ;), and I'm running Mint 8 on this very laptop with good experience (though I'd like to try something else this time - I'm just funny like that - but Mint is definitely an option). wattOS... doesn't look bad either. I'm a little apprehensive about switching to a new DE (OpenBox + LXDE?), having used only Gnome and KDE in the past, but I can learn.

danielrmt: Browsing packages online? Never thought of that one... Something to try, absolutely. One of these days.

---

### Post by hhh on 2010-02-03
@Psumi,

Did you end up installing wattOS? I was curious what you thought it's strengths and weaknesses were.

---

### Post by Psumi on 2010-02-03
> **hhh said:**
> @Psumi,

Did you end up installing wattOS? I was curious what you thought it's strengths and weaknesses were.

No I didn't install it. why? It's an RC. I won't install it until it has a final version, sorry.

---

### Post by hhh on 2010-02-03
No problem, I was just curious, like I said. I was very tempted to install it, but I have Karmic running perfectly using standalone Openbox/tint2 and it seems silly to switch one lightweight system for another (actually, wattOS would be way more lightweight in terms of hard drive usage, but that's not an issue for me).

---

### Post by Psumi on 2010-02-03
> **hhh said:**
> No problem, I was just curious, like I said. I was very tempted to install it, but I have Karmic running perfectly using standalone Openbox/tint2 and it seems silly to switch one lightweight system for another (actually, wattOS would be way more lightweight in terms of hard drive usage, but that's not an issue for me).

Could've done what I did here: [http://ubuntuforums.org/showpost.php?p=8768180&postcount=13](http://ubuntuforums.org/showpost.php?p=8768180&postcount=13)

But it's up to you.

---

