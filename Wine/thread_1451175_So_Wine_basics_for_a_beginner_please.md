---
title: "So Wine basics for a beginner please"
date: 2010-04-10
forum: Wine
---

### Post by bigseb on 2010-04-10
Please can someone help me with the following:

1) How do see what version of wine is in my PC?

2) If I want to upgrade to a newer version what is the best way to do that? I assume the answer will be through the terminal. I, however, am not terminal fluent. Some help would be great. Also, must the current version be uninstalled before I install the new one?

3) My version of Ubuntu is x64. Does that mean the wine is also x64? I ask as the game I wish to install needs a patch to run on a x64 Windows OS, will that be the case in Wine too? The AppDB does not address this.

4) What is Wine Doors? Must I use that to run Wine? 

Thanks

---

### Post by stilling on 2010-04-10
To install wine just open a terminal and 
sudo aptitude install wine

for wine version in terminal " wine --version "

in terminal " wine --help "

Ubuntu as he releases a new version comes with the newest stable wine version in repos so you don`t need to upgrade, Ubuntu does that for you. 

Wine-Doors is a free and open source application-management tool for the GNOME desktop which adds functionality to Wine. Wine-Doors is an alternative to WineTools which aims to improve upon WineTools' features and extend on the original idea with a more modern design approach. Some applications, in order to work properly with wine, require more tweaking than simply installing the application, such as manually configuring Wine to use certain Windows DLLs. The Wine project does not integrate such workarounds into the Wine codebase, instead preferring to focus solely on improving Wine's implementation of the Windows API. While this approach focuses Wine development on long-term compatibility, it makes it difficult for users to run applications which can run using workarounds. Consequently, many third party applications have been created to ease the use of these applications which don't work "out of the box" within Wine itself. Wine-doors is one of them.

If you have 64 bits sytes programs willbe in 64 like your system but that is what repos does as in 32 bits are 32 bits repos in 64 are 64 so you get the idee

i hope this helps you

---

### Post by bigseb on 2010-04-10
> **stilling said:**
> If you have 64 bits sytes programs willbe in 64 like your system but that is what repos does as in 32 bits are 32 bits repos in 64 are 64 so you get the idee

I take then that running a 32bit game in Wine/64bit Ubuntu will present the same problems as running it in 64bit Windows?

---

### Post by asdfoo on 2010-04-10
> **bigseb said:**
> I take then that running a 32bit game in Wine/64bit Ubuntu will present the same problems as running it in 64bit Windows?



what problem is that?  64bit Windows runs 32bit applications just fine, it includes copies of all the 32bit Windows code required to run the applications.

If it's not already clear, everyone who has a 64bit Ubuntu system uses 32bit Wine to run 32bit Windows programs.

---

### Post by bigseb on 2010-04-11
> **asdfoo said:**
> 64bit Windows runs 32bit applications just fine
Not so. Command and Conquer 3 won't run on x64 Windows OS without a patch. Hence I was wondering whether I would need a patch to run the game on my x64 Ubuntu.

---

