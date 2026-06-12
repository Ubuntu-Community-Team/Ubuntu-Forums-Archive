---
title: "Re-branding ubuntu?"
date: 2008-09-21
forum: Ubuntu Dev Link Forum
---

### Post by Dub Throatflex on 2008-09-21
Hello,
I don't know I'm posting in right forum, or not.
I'm creating customized LiveCD and I want to fully rebrand ubuntu, how to do this? I know how to change GNOME themes, etc., but distribution name in system monitor, and other apps, how to do this?
Thanks, and sorry for my poor english:)

---

### Post by Dub Throatflex on 2008-09-24
Anyone? :(

---

### Post by Dub Throatflex on 2008-10-12
Sorry for bumping, but i REALLY need it, please, anyone...

---

### Post by inxygnuu on 2008-10-12
I would check out the distro editor thingss, they might help you.

I feel your pain of not getting responded to. that has happened to me too.:(

---

### Post by Dub Throatflex on 2008-10-14
> **inxygnuu said:**
> I would check out the distro editor thingss, they might help you.

I feel your pain of not getting responded to. that has happened to me too.:(
Tried Reconstructor, it just changes GDM, GTK themes, etc.:(
Any other solutions?

---

### Post by UbuWu on 2008-10-14
Look at the kubuntu-, ubuntustudio- and ichtux-default-settings packages and make something similar for your distro.

---

### Post by forger on 2008-10-15
remastersys ?
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by Dub Throatflex on 2008-10-18
Found nothing helpful in kubuntu- and similar packages.
Remastersys doesn't rebrand distro, it just compresses it to iso

---

### Post by ankursethi on 2008-10-19
Are you sure you want to use Ubuntu? I ask this because PCLinuxOS has a very nice tool you can use to remaster the CD.

It works like this. You boot the LiveCD, install/remove all the software you want, change themes, delete stuff, change system settings etc. Then you just run the tool to produce an ISO of your newly remastered system. Alternatively, you can install PCLOS to disk and then follow the same procedure.

---

### Post by Dub Throatflex on 2008-10-19
You don't understand, I know how to remaster CD, but I don't know how to rebrand (change distribution's name).

---

### Post by bretcolin on 2009-04-25
I've been experimenting with reconstructor with the ubuntu 9.04 cd and first it needed a script mod that fixed the chksum problem now it works. I was successful in getting alot of the branding off by uninstalling ubuntu-desktop metapackage reverting it to gnome and applying the oxegen icon theme. I also had to dig into the reconstructor file system in my home folder under sudo nautilus /home/username/reconstructor/root/usr/share. Most of the files to change are in there. Ubiquity icons, ubuntu-art,gconf, witch is how to change the desktop settings. Replace that gconf folder with your current one. Thats were I'm at. I hope that helps.    bret:)

---

### Post by mdgrech on 2009-05-25
Honestly man rebrand?  Seriously your going to release Ubuntu and the only difference your going to make is changing the themes and removing anything that says Ubuntu on it?  I mean you can do that but do you honestly expect it go anywhere?  You obviously like Ubuntu so instead of trying to make a quick buck off it why don't you give back to the community.

---

### Post by bretcolin on 2009-05-25
I'm not trying to take any credit or make a buck. I'm an artist and this is how I can give to the community. Ubuntu rebranded Debian lenny, so I'm not sure what you mean. Is there anything wrong with having a little fun. What's wrong with people. After awile we won't know what correct is anymore. Pretty soon there will be no freedom to customise. The first thing I do when Ubuntu's gnome gets on my computer is change it. Isn't that the point. I don't want to live in a world were everything is the same. Everything is not the same. I'm not trying to rebrand Ubuntu anyway, I'm trying to get the anoying branding off because I simply don't like it personally, I think it's ugly.

---

### Post by grndslm on 2009-06-26
> **bretcolin said:**
> i'm not trying to take any credit or make a buck. I'm an artist and this is how i can give to the community. **ubuntu rebranded debian lenny, so i'm not sure what you mean.**Burn!!

---

### Post by durand on 2009-06-26
Ubuntu did not rebrand debian lenny, it changed the default packages, the themes, patched programs and many other things. Ubuntu still syncs its repos at the start of a development cycle. There is a difference between rebranding where you just change the name of the product and what ubuntu and other linux distros do. I'm not saying that this is what you're doing, however.

---

### Post by brucewagner on 2010-01-29
I want to do the same thing as the originator of this thread. 

I want to remove the branding - logos and such. 

It's not about disrespecting the sources. I would always give full credit where credit is due.  

It's about aesthetics.  It's about style.  It's about looks. 

I actually want to re-brand (really UN-brand) Linux Mint 8.  Personally, I think the LM logo is very ugly and the color choices would Not be mine. 

I want to make it look cool.... with no LM logos everywhere...

I want to install some nice apps that are missing, tweak the theme, the launch icons, etc., and create my own ISO of a Live CD.... for my new custom configured system. ... so I can easily install it for all my friends (without spending hours at their house!)

(1)  Which is the best / easiest tool to remaster your own live CD?

(2)  What's the easiest way to remove all the Logos from Ubuntu / Linux Mint?

---

### Post by mamad_fexar on 2010-02-07
Remastering & Reconstructing is Gnu's Philosophy:

[COLOR="Red"]> [COLOR="Red"][http://www.gnu.org/philosophy/pragmatic.html](http://www.gnu.org/philosophy/pragmatic.html)[/COLOR][/COLOR]

---

