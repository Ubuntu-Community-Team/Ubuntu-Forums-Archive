---
title: "Considering Ubuntu or Linux Mint"
date: 2020-10-24
forum: Ubuntu, Linux and OS Chat
---

### Post by waltd on 2020-10-24
Hi all, I'm considering doing a full install of Ubuntu or Linux Mint. I just wanted some opinions and views of why you, in the forum, chose Ubuntu over...say...Linux Mint. Thanks. I welcome an informative conversation.

---

### Post by guiverc on 2020-10-24
**Security**.

Ubuntu has fully documented procedures on how packages are audited for security purposes, how upgraded packages go through the SRU (stable release update) process to enter the repositories.

You can choose what support you want, be it maintained full five years (Canonical supported packages), or community supported (a little lower level of security but less guarantee of maintenance with normally 3 years for a LTS, but can be less).  

Mint uses runtime *adjustments* so they can use upstream (Ubuntu) packages, which adds another attack vector (ie. lowers security).  They also mix the 'main' & 'universe' packages so the security/maintenance of those packages gets hidden unless the user investigates it themselves.

There are benefits with Mint skipping the security aspects, they can make changes faster (no SRU process to complete) resulting in a nicer UI experience often, but that cost is the added security vector that exists in Mint.

Mint has been hacked at least once (twice?) with tainted ISOs discovered (rather quickly), this has not happened with Canonical/Ubuntu because they have a higher level of security (with the added costs to that).

**Support**

Ubuntu has many more support options, a far larger user base, and many sites available. Beyond here, there are many IRC rooms (Ubuntu flavors, eg. I"m using Lubuntu) can also ask questions in #ubuntu, but with all the extra users, you'll get answers a lot faster, also more qualified answers usually as more enterprise/employed people will be answering (will apply in Mint too, just on a lower level).  Mint can't use Ubuntu sites (askubuntu, IRC etc)


I used Mint briefly, I liked how it looked, however it was using Mint that made me fully aware of the difference in security between (in my view *cloudy*) Mint and Ubuntu. Yes if you're fully aware of the differences, you can **almost** have the same security level [on Mint] as Ubuntu (ignoring *adjustments* of course) but you have to choose that as it's not the Mint default (not recommended either by Mint as it can result in a less stable system due *adjustments*).  I upgraded my Mint system to the higher levels of security, and it wasn't as stable as they warned, and switched back to Ubuntu.

**Cinnamon**

If you love the Cinnamon desktop, Mint maybe the best place for you, as they're the main platform where it is created, so that's one area where Mint will be best.


[B]Adjustment[I]s
[/I][/B]
I perfectly understand Mint's use of adjustments, to build & maintain all packages themselves would cost resources, and thusthe *hack* of *adjustments* is a quick & somewhat dirty solution. It makes perfect sense, but it's adding another attack vector. For Mint is makes perfect sense, for a user though, the negatives of *adjustments* should be considered  differently.


In the end it's your choice.  There are pro's & con's for both.

There will be other pro's of Mint; but I'm writing as a Ubuntu (and Debian) user, and I'm mainly writing about LMUE (the main Linux Mint) as I've followed the LMDE version less closely (I'd just use Debian in that case, and I'm unsure if *adjustments* are used in LMDE).

---

### Post by pantazi on 2020-10-25
Cracking reply guiverc, nice concise overview.

I took up Ubuntu a few years ago, fairly light use and recently began exploring other distros' in Virtualbox. Tried Mint first, but it didn't have the same appeal and yesterday began exploring Kubuntu.
Overall though, I feel that Ubuntu will win out. 20.04.1 has a great look and is user friendly particularly for one who is coming late to Linux, plus there is a lot of help out there.
Linux beats Windows hands down. Just my thoughts.

---

### Post by jeremy31 on 2020-10-25
Moved to Ubuntu/Linux/OS chat

---

### Post by kc1di on 2020-10-25
I will say they both are good distros.  I think the preference for me is the desktop. I like Cinnamon but prefer Ubuntu's implementation of Gnome. Other than that if your using Ubuntu LTS and Mint they are very similar and it comes down to personal choice.  Mint has some nice tools and so does Ubuntu.  

Good luck in your search, best way to tell is to use them both for awhile and see which is the most comfortable for you.

---

### Post by exploder on 2020-10-25
Both are great choices! It all comes down to personal preferences. I relied on Windows 10 and Chrome OS for about a year after my divorce. I really did not care for either very much, lol. I wanted something with style that in no way reminded me of Windows. Ubuntu 20.04 turned out to be everything I was hoping for. I have used Mint many times, the out of the box tools are outstanding. I highly recommend Linux Mint to people that want a traditional desktop. I tried the Plasma desktop, Cinnamon, Budgie, they are all pretty nice but Ubuntu for me just had the right combination of everything. Try both from a live USB or DVD and see which one you enjoy more.

---

### Post by ayesc0tty89 on 2020-10-25
Use a virtual machine, try out both then decide which you like more.
I personally don't like MINT but love Ubuntu.

---

### Post by grahammechanical on 2020-10-25
I did not choose Ubuntu over Linux Mint because Linux Mint did not exist when I chose Ubuntu. Nor would I today choose Linux Mint over Ubuntu. I have no problem with people using other Linux distributions. Even other computer operating systems. Most people use what they paid for when they purchased a machine or device. 

I seem to have become indoctrinated by the Ubuntu Code of Conduct, the Ubuntu Policy and the Ubuntu Forums Code of Conduct. I do not apologize for that.

You have chosen Free and Open Source Software. It is free but not as in free beer. Try to give something back.

Regards

---

### Post by T6&amp;sfpER35% on 2020-10-25
while back when i decided i'm done with windows , i installed mint ,cause everyone said that's the easiest coming from windows.
i liked it , it worked good and it looked nice and all that , just one problem i had i couldn't solve , and that is every once in awhile my keyboard and mouse would freeze to the point i have to reboot.the longer i used mint the more frequent it became, when it got to like 3 times a week i decided to look around for other distros.
hence i'm on ubuntu now ,(and loving it btw.) ,and the freezing stuff never happened again.
otherwise both are great distros

---

### Post by ajgreeny on 2020-10-25
You may find that Mint with cinnamon in VBox is pretty slow running but using Xfce it is very good.

I started with Ubuntu 5.04 some 15 years ago, using gnome 2, which I loved.  When gnome 3 appeared it left me befuddled and I then moved to Xubuntu (Xfce), which I have been with ever since.
I also try many other distros including Mint as VMs, though I now use KVM instead of VBox as it runs everything much better, and faster in my experience, though I have not tried Mint-cinnamon in KVM as I am now a die-hard Xfce user.

There are several things GUI related which I did not like about Mint, the update manager, or whatever it was called, being one of them.  In those far off days I used synaptic for updating the Ubuntu or Xubuntu I was using but in Mint that was not possible as Mint's version of synaptic did not show any update options.  By default that is still the case nowadays, though it is now possible to add the standard ubuntu-repos version of synaptic in Mint and use it for updating the system just as you do in Ubuntu itself.  This no longer a matter of any importance to me as I nearly always use terminal for update and upgrade operations.

One other advantage of Mint originally was its inclusion of restricted codecs at installation, probably very useful for new Linux users, but Ubuntu had none and they had to be installed after installation of the OS.  I have now been using this OS for so long I find it hard to remember the difficulties I must have had trying to play, for example, commercial DVDs, but once you follow instructions easily found with a search, codecs are so easy to install now that I do not give it a second thought.

---

### Post by T6&amp;sfpER35% on 2020-10-25
> [COLOR=#000000]One other advantage of Mint originally was its inclusion of restricted codecs at installation,[/COLOR]

i'm pretty sure ubuntu installation nowadays also ask if you want to install 3rd party codecs

---

### Post by mastablasta on 2020-10-26
i started with Ubuntu (at the time Gnome now that interface is called Mate). at the time i had issues with panels staying on screen with some games. KDE on the other hand offered to automatically turn off special effects for full screen applications (such as games) and had no other issues. so i moved to KDE Mint, but at some point it after install it started acting a bit strange. for example windows won't always show on mouse over in panel. so i went and installed Kubuntu and that was 8 or 9 years ago. i am still on Kubuntu. and it is just getting better and better. all the things i missed before are coming to the OS. DE is snappy and uses less resources that it did before. which makes me think that this KDE follows the same philosophy in OS that i would.

on the main PC i was still using windows XP but at the same time i explored Xubuntu a lot and i have to say it is also a good option if you need something light and easy to configure to your liking. 

if you wan tot go to linux i would say  - download a few distros you like how they look use a USB (maybe with multiboot installer like Yumi) and just try them out. the one you like the most get's an install. and then you can continue from there. if there is something you don't like you can always change 

another option (if you have good machine and plenty of ram) is to use virtualbox and boot the ISOs there or even do the install there.

---

### Post by pantazi on 2020-10-26
> **ajgreeny said:**
> You may find that Mint with cinnamon in VBox is pretty slow running but using Xfce it is very good.




I found that too.

---

### Post by ajgreeny on 2020-10-26
> **3nd said:**
> i'm pretty sure ubuntu installation nowadays also ask if you want to install 3rd party codecs
Indeed it does but I never use that when I install the OS preferring to get the installation done , then a&#271;d what's  needed afterwards.

---

### Post by pantazi on 2020-10-28
> **waltd said:**
> Hi all, I'm considering doing a full install of Ubuntu or Linux Mint. I just wanted some opinions and views of why you, in the forum, chose Ubuntu over...say...Linux Mint. Thanks. I welcome an informative conversation.

Perhaps the OP would now like to reply?

---

### Post by Shibblet on 2020-10-29
I am a bit of a minimalist when it comes to Operating Systems.  This is why Kubuntu's "Minimal Install" is a great thing for me.  If there is a program that I do not want, or need to use, I want it gone off of my computer entirely.  And dependency that does not work with other programs need to be removed as well.  This can turn into a bit of a problem when I try to erase "everything" that comes with a package install.

I feel a bit like Al Capone in the Untouchables...  "I want him dead!  I want his family dead!  I want his house burned to the ground!"  ;-)

My PC needs are very minimal as well.  So, when it comes to Ubuntu vs. Linux Mint, it's not about which one is better, it's about which one works best for my needs.

KDE Desktop + Ubuntu Software Repositories + APT Package Management + PPA System + Minimal Software Environment = Kubuntu

---

