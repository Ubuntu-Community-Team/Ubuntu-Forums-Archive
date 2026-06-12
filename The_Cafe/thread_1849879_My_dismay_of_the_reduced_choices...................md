---
title: "My dismay of the reduced choices...................."
date: 2011-09-25
forum: The Cafe
---

### Post by MooPi on 2011-09-25
I have been a Linux user and Ubuntu user for many years(10 years approximately). My first steps toward Linux were due to my lack of choices for OS, when Microsoft Windows was almost ubiquitous to a PC. I have been and will continue as a vocal Linux enthusiast. I now have issues with Ubuntu and heard the same complaints from contacts and friends.The direction of Ubuntu dismays me not because of default changes to the OS but to the lack of choice. The minimal install has been my starting point with Ubuntu for some time because the Gnome desktop and the prepackaged Xubuntu,Kubuntu and the like did not fit my taste. It is now broken and attempts to work around those flaws has soured my feelings toward Ubuntu.I do appreciate the package management of Ubuntu though and that is why I have stayed. The wide choice of installed apps and the ease of package management meant I could customize to my hearts content. That has all changed and I'm looking for a new distro. This is not an easy decision to make because I'm so accustomed to all that is available with Ubuntu.To give everyone an idea of how customized my computer is, I shall list some of the core features:
Openbox - window manager
Xterm - terminal
pcmanfm - file manager
mplayer - command line no gui
wicd - network manager
htop - process viewer
wodim CL burning software
feh image viewing and desktop background 
custom scripts to play music , view photos and record media from terminal
There is nothing special about this setup other than it is mine by choice and each application fits well and worked until version 11.04 and beyond. The over all fit and finish of the OS has changed and seems increasingly locked down.
 My statement here is not to flame the community but a call for an inclusion of choice back to Ubuntu and further the discussion among users who have also felt the same as I have. A recent post on the forum about the new default media player sparked the notion for this post.
> **mörgæs said:**
> Why do you people focus so much on what is default? Linux is about choice - there are lots of media players to choose from. VLC for example.

---

### Post by Paqman on 2011-09-25
> **MooPi said:**
> The minimal install has been my starting point with Ubuntu for some time because the Gnome desktop and the prepackaged Xubuntu,Kubuntu and the like did not fit my taste. It is now broken

Really? What's broken about it?

---

### Post by MooPi on 2011-09-25
Desktop won't load without an display manager XDM, GDM etc. I have always started my boxes with "startx" Sound privileges screwed up. I can't list much more because I quit trying to get it to work but have heard from friends and their multiple issues to corroborate mine. This is just a small sampling of problems from my circle of Linux users, I can only assume others that use the minimal install have experienced some problems.

---

### Post by el_koraco on 2011-09-25
> **MooPi said:**
> Desktop won't load without an display manager XDM, GDM etc. I have always started my boxes with "startx" Sound privileges screwed up. I can't list much more because I quit trying to get it to work but have heard from friends and their multiple issues to corroborate mine. This is just a small sampling of problems from my circle of Linux users, I can only assume others that use the minimal install have experienced some problems.

You need this in .xinitrc

```
exec ck-launch-session dbus-launch openbox(-session)
```

The fact that you didn't bother to look up your errors and take three minutes to google does in no way mean that anything is "broken".

---

### Post by MooPi on 2011-09-25
> **el_koraco said:**
> You need this in .xinitrc

```
exec ck-launch-session dbus-launch openbox(-session)
```

The fact that you didn't bother to look up your errors and take three minutes to google does in no way mean that anything is "broken".

I found fixes for both but not all were good fixes and your assumption is incorrect and mildly insulting. If I go to the trouble of setting up a minimal install that utilizes terminal above gui don't you think I looked ?

---

### Post by el_koraco on 2011-09-25
> **MooPi said:**
> I found fixes for both but not all were good fixes and your assumption is incorrect and mildly insulting.

Oh yeah? Well, if you're starting a session via .xinitrc you're gonna have the same privilege issues on any distro out there. Check the Arch and Gentoo wikis if you don't believe me. Hell, I have the same situation on Debian if I get rid of GDM, so...

---

### Post by MooPi on 2011-09-25
> **el_koraco said:**
> Oh yeah? Well, if you're starting a session via .xinitrc you're gonna have the same privilege issues on any distro out there. Check the Arch and Gentoo wikis if you don't believe me. Hell, I have the same situation on Debian if I get rid of GDM, so...

I stated that earlier versions did not have this failing and was the reason I liked and use Ubuntu. My 10.10 systems work flawlessly with the same install base.

---

### Post by el_koraco on 2011-09-25
> **MooPi said:**
> I stated that earlier versions did not have this failing and was the reason I liked and use Ubuntu. My 10.10 systems work flawlessly with the same install base.

I get your dismay, but the only difference is the consolekit-policykit-hal-dbus mess and how and when distros start adopting any of the features. To be true, most of the fault lies with the Gnome people, because they seem to be tying a lot of the basic system functionalities to GDM and the Gnome session, so the ball changes constantly.

---

### Post by mips on 2011-09-25
MooPi, 

Arch or Debian (Stable or Testing) seems like it would suite your needs.

---

### Post by MooPi on 2011-09-26
> **mips said:**
> MooPi, 

Arch or Debian (Stable or Testing) seems like it would suite your needs.

Thanks mips, I've taken your advice and installed Debian Squeeze stable. This is a revisit after many years using Ubuntu and all seems to be going well. No hiccups or deal breakers as yet. I will have to enable some Ubuntu repositories to get some of the multimedia codecs I depend on though. This feels like what I'm used to and is giving me the control I desire.

---

### Post by Paqman on 2011-09-26
> **MooPi said:**
> Desktop won't load without an display manager XDM, GDM etc.

That's a pretty harsh definition of "broken". Choosing to not use a display manager is a very unusual choice of system setup.

---

### Post by ninjaaron on 2011-09-26
I'm glad we had this conversation.  I feel as if we've all come to special place regarding GDM and console kit.

P.S.  I still have issues with permissions in Arch sans gdm that make me want to cut people, but it mostly has to do with mounted volumes.  Be sure you profile is in all the right groups (with the cool kids).

---

### Post by el_koraco on 2011-09-26
> **MooPi said:**
> I will have to enable some Ubuntu repositories to get some of the multimedia codecs I depend on though. This feels like what I'm used to and is giving me the control I desire.

No need, add the Debian Multimedia (that's the father to Medibuntu) repo to your sources.list, and you probably don't need much more than the win32 codecs.

---

### Post by earthpigg on 2011-09-26
MooPi's already made the plunge, but I'll leave what I was going to suggest anyways:

LTS Ubuntu Server Edition, with PPAs of that software that you want the most recent of added as you see fit.

---

### Post by mips on 2011-09-27
> **MooPi said:**
> Thanks mips, I've taken your advice and installed Debian Squeeze stable. This is a revisit after many years using Ubuntu and all seems to be going well. No hiccups or deal breakers as yet. I will have to enable some Ubuntu repositories to get some of the multimedia codecs I depend on though. This feels like what I'm used to and is giving me the control I desire.

For codecs enable the Debian Multimedia repo.

I forgot to mention Crunchbang linux. It's based on Debian Squeeze and they have a Openbox & XFCE version. I'm using the XFCE version. It's pure Debian with some configs done for you. Very nice distro and they have an excellent friendly community I must add.

If you already have squeeze installed you can add their small repo and 'update' (dunno what else to call it) to crunchbang.

---

### Post by el_koraco on 2011-09-27
> **mips said:**
> If you already have squeeze installed you can add their small repo and 'update' (dunno what else to call it) to crunchbang.

We call it "crunchify Squeeze/Wheezy/(apto)sid".

---

### Post by red_Marvin on 2011-09-27
> **Paqman said:**
> That's a pretty harsh definition of "broken". Choosing to not use a display manager is a very unusual choice of system setup.

Only if you consider running anything else than gnome/kde as very unusual.
It is pretty common on more minimal setups.
...Then again, I haven't been using ubuntu for a while, perhaps it is
very unusual in an ubuntu context.

Edit: Also, in my opinion, if the running of graphical applications depends on
the login process being graphical then the system *is* broken.
If not in implementation then in design.

---

### Post by MooPi on 2011-09-28
> **el_koraco said:**
> No need, add the Debian Multimedia (that's the father to Medibuntu) repo to your sources.list, and you probably don't need much more than the win32 codecs.

Done. Thanks again for the heads up on Debian Multimedia. Watching my first dvd on Debian right now.

---

### Post by wolfen69 on 2011-09-28
> **el_koraco said:**
> No need, add the Debian Multimedia (that's the father to Medibuntu) repo to your sources.list, and you probably don't need much more than the win32 codecs.

What a revelation! Kidding aside, you can do this for every distro and get all the codecs you need. Believe it or not, even Slackware users listen to music and watch youtube vids! ;)

---

### Post by wolfen69 on 2011-09-28
> **MooPi said:**
> Watching my first dvd on Debian right now.

Congrats on getting a dvd to play on something else besides ubuntu. ):P

---

### Post by mips on 2011-09-28
> **MooPi said:**
> Thanks mips, I've taken your advice and installed Debian Squeeze stable.

Don't be shy of Wheezy/testing either, it's pretty stable (this is Debian after all) and it give you access to newer versions of software. A lot of people run testing for their desktops.

I won't mix the two though (like I did) as it can lead to dependency issues and apt-pinning is such a schlep.

---

### Post by del_diablo on 2011-09-28
You can also google "debian pinning".
Meaning you setup a system where it prefferes packages from 1 repo, you can also seamlessy install packages for another version, lets say "Testing kernel" instead of "Unstable kernel".

---

