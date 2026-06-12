---
title: "Breezy installed like a Breeze!"
date: 2005-07-02
forum: The Cafe
---

### Post by XDevHald on 2005-07-02
I cannot tell you how easy breezy installed with NO errors. The last time I tried to move over to Breezy, my gdm.conf screwed up and I couldn't get my postfix to run right with my localdomain, now it works like a charm and breezy is actually running with no bugs :shock:

Amazingly enough, I am able to boot into Gnome and actually enjoy a faster desktop, now that's a shocker to get from Breezy. Now I know a lot of people have been getting so many errors, but maybe the new release really brought out some good packages that aren't filled with bugs, (Not Bad)

Anyone else enjoying a fresh move from Hoary to Breezy besides me tonight? :D

---

### Post by sapo on 2005-07-02
is there any preview release out? what about the X problem that almost everybody who installed wasnt able to get X up?

i wanna try it out... but i have work to finish.. and i dont know if i should upgrade my hoary  :|

---

### Post by mohaham on 2005-07-02
thats exciting... lemme take a try too..

---

### Post by sapo on 2005-07-03
I m downloading.. hope it doesnt break everything.. if just my gedit, mysql and apache work out.. its enought for me to work  :grin:

---

### Post by jerome bettis on 2005-07-03
yeah i got brave a week or so back and gave it a try.  x wouldn't start, i tried messing with it a little bit but it wasn't working out.  then i changed my apt sources file back to hoary and ran update & upgrade but that doesn't downgrade.  

is there a way to undo an upgrading from apt?  if there is i'll give it a go right now.  if not i'd rather not bother with the live cd & restore thing.  unless it is actually _that_ good and i wouldn't need to get back to hoary.

---

### Post by bored2k on 2005-07-03
[QUOTE=jerome bettis]yeah i got brave a week or so back and gave it a try.  x wouldn't start, i tried messing with it a little bit but it wasn't working out.  then i changed my apt sources file back to hoary and ran update & upgrade but that doesn't downgrade.  

is there a way to undo an upgrading from apt?  if there is i'll give it a go right now.  if not i'd rather not bother with the live cd & restore thing.  unless it is actually _that_ good and i wouldn't need to get back to hoary.[/QUOTE]
 With the current flawless state of my Hoary, I don't think I'll be --dist-upgrading anytime soon.

---

### Post by sapo on 2005-07-03
[QUOTE=jerome bettis]yeah i got brave a week or so back and gave it a try.  x wouldn't start, i tried messing with it a little bit but it wasn't working out.  then i changed my apt sources file back to hoary and ran update & upgrade but that doesn't downgrade.  

is there a way to undo an upgrading from apt?  if there is i'll give it a go right now.  if not i'd rather not bother with the live cd & restore thing.  unless it is actually _that_ good and i wouldn't need to get back to hoary.[/QUOTE]

i still have 3 hours downloading stuff... somebody can say if my x is going to work or not? i didnt see any X upgrades in the upgrade list.. ](*,)

---

### Post by Skel on 2005-07-03
i have gotten brave and am trying now first time i had to reinstall ubuntu maybe this will be better or els ei will be a idiot :razz:

---

### Post by bored2k on 2005-07-03
[QUOTE=Skel]i have gotten brave and am trying now first time i had to reinstall ubuntu maybe this will be better or els ei will be a idiot :razz:[/QUOTE]
 One word: **backup**.
Second word: Knoppix.

---

### Post by WildTangent on 2005-07-03
i just tried it half an hour ago, x wouldnt start :( i also took the second HD out of the computer i tried it on, and restored the windows boot loader, my parents are pissed because they dont understand GRUB, i have to explain it to them everytime they start the computer :(

-Wild

---

### Post by bored2k on 2005-07-03
[QUOTE=WildTangent]i just tried it half an hour ago, x wouldnt start :( i also took the second HD out of the computer i tried it on, and restored the windows boot loader, my parents are pissed because they dont understand GRUB, i have to explain it to them everytime they start the computer :(

-Wild[/QUOTE]
 Make their OS the default option, then hide Grub. This way, it will only boot if you press certain key before the 3 second time limit expires. 

If you don't know how, save yourself some trouble, get grubconf, then follow the GUI. [http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb](http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb)

---

### Post by Skel on 2005-07-03
nope i fucked it up again i get weird errors when doing dist-upgrade on a fresh install now... dont know whatever maybe i will get it whne its more stable..(sigh) now i got ta put another 57904 hours of work into this thing...STupid ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ]

---

### Post by benplaut on 2005-07-03
mmm... i can't wait to try out the live CD

burning as i type  :grin:

---

### Post by WildTangent on 2005-07-03
[QUOTE=benplaut]mmm... i can't wait to try out the live CD

burning as i type  :grin:[/QUOTE]
breezy is out on livecd already?

-Wild

---

### Post by UbuWu on 2005-07-03
The live cd doesn't have the proprietary drivers, so no luck with my nvidia graphics card...

---

### Post by jeremy on 2005-07-03
[QUOTE=bored2k]One word: **backup**.
Second word: Knoppix.[/QUOTE]
 Third word: Partimage

---

### Post by XDevHald on 2005-07-03
Hmm, I must be the only one in the world actually running it correctly :shock: what am I doing right? O.o

---

### Post by WildTangent on 2005-07-03
one thing ill add that ive wanted to do for a while. i used reiserfs instead of EXT3 when i installed hoary (and subsequently upgraded to breezy) i noticed a slight decrease in bootup time, but nothing major. i do hear reiser is great for small files as it doesnt allocate a small file to one sector of a hard drive, even though 2 or 3 such files could fit in said sector. interesting stuff if you ask me :) my next installation will be reiser

-Wild

---

### Post by sapo on 2005-07-03
[QUOTE=WildTangent]one thing ill add that ive wanted to do for a while. i used reiserfs instead of EXT3 when i installed hoary (and subsequently upgraded to breezy) i noticed a slight decrease in bootup time, but nothing major. i do hear reiser is great for small files as it doesnt allocate a small file to one sector of a hard drive, even though 2 or 3 such files could fit in said sector. interesting stuff if you ask me :) my next installation will be reiser

-Wild[/QUOTE]

i ve been using reiser since my first ubuntu install.. Hoary Preview Release, never had problems  :grin:

---

### Post by benplaut on 2005-07-04
[QUOTE=WildTangent]breezy is out on livecd already?

-Wild[/QUOTE]

yup, colony 2  :)

---

### Post by WildTangent on 2005-07-04
give me a link! please! :D

-Wild

---

### Post by christooss on 2005-07-04
[QUOTE=WildTangent]give me a link! please! :D

-Wild[/QUOTE]
 [http://cdimage.ubuntu.com/releases/breezy/colony-2/](http://cdimage.ubuntu.com/releases/breezy/colony-2/)

---

### Post by oddabe19 on 2005-07-04
all you guys with X problems, there are plenty of threads in the Breezy forums that explain how to fix it.

just to let you know.

---

### Post by ubuntu_demon on 2005-07-04
I'm upgrading right now!

updated :
couldn't get xserver-xorg working. So I decided to do a fresh install of hoary and breezy and install a triple boot on my desktop (hoary,breezy,windows XP).

I did a fresh server install of breezy colony 2 after that I installed ubuntu-desktop and reconfigured my xserver. Now the basic installation seems to work fine. Except that gnome-system-tools couldn't be configured.

every seems to be working fine. I don't think I'll update until colony 2 (except for hoary-extras). The only minor irritation is that gnome-system-tools didn't configure properly (so I will update that package).

I've decided not do do any sound configuration files editting unless absolutely necessary.

---

### Post by christooss on 2005-07-04
I am upgrading my system right this momnt. Only 1 h an 30 min left :)

---

### Post by UbuWu on 2005-07-04
Today's update (which for me is probably all updates from the last 2 weeks, a long list of packages) is the first since may that has really screwed up my system, or at least X/Gnome.

---

### Post by XDevHald on 2005-07-05
[QUOTE=UbuWu]Today's update (which for me is probably all updates from the last 2 weeks, a long list of packages) is the first since may that has really screwed up my system, or at least X/Gnome.[/QUOTE]
 Only issue I am having is that the sound doesn't work, pfft, that's easy to fix, but I'm to lazy this morning to take the time to do it. *YAWNS*

I'll be checking the breezy forum out on other known bugs to see what else I might be missing.

---

### Post by XDevHald on 2005-07-05
For those looking on how to fix X on startup, or other issues related to boot up or hard freezes with Gnome 2.11 on Breezy Badger, see: [http://www.ubuntuforums.org/showthread.php?t=46349](http://www.ubuntuforums.org/showthread.php?t=46349)

---

### Post by jerome bettis on 2005-07-07
[QUOTE=sapo]i ve been using reiser since my first ubuntu install.. Hoary Preview Release, never had problems  :grin:[/QUOTE]
 reiser**4** is much better.  been using it for a few months here with 0 problems.  it really saves disk space well.  i can't really give too many solid numbers but on my / partition (everything except usr var & home) i have only 68 megs used and when i used ext3 it was almost 300!! same exact files just a lot of block mismanagement, most likely due to lots of small files..  the long check ext had to do every 30 or so mounts (or after an bad unmount) are gone as well.  and it's faster too!

what's the catch?  well it's very new but it's close to being stable.  the main problem is that most live cds or distros don't have it in their kernel which can be a big deal sometimes.  the kanotix live cd has it though and has saved me some aggrvation.

as for breezy, it looks like i should wait a little longer still.  hopefully this thread floats around the top of this forum so we can stay updated etc.

---

### Post by XDevHald on 2005-07-07
> as for breezy, it looks like i should wait a little longer still. hopefully this thread floats around the top of this forum so we can stay updated etc.

That won't be an issue :) As for breezy, it's running probably on 10-15% of desktops right now if not more. Now the security on breezy is at minimum but it will increase before October for X.org

I'm running Breezy as we speak and currently running VERY well, and shocked as well, but I won't get my hopes up if they do something a little on edge with breezy ;)

We'll keep this thread going and up to date for everyone :D

---

### Post by MetalMusicAddict on 2005-07-07
After reading this I decided to try breezy on my laptop. It went fine for the most part. Im getting a error when "dist-upgrade"ing but Ill work it out.

I was hapy to see that the "i810" driver for my laptop was fixed. Im wondering though is it possable to take the driver/file from Breezy and move it to Hoary?

---

### Post by arunsub on 2005-07-07
Can anyone tell me what's new in Breezy from end-user (non-technical) point of view?

---

### Post by bored2k on 2005-07-07
Everyone please continue this conversation here:
[http://ubuntuforums.org/showthread.php?t=47014&page=2](http://ubuntuforums.org/showthread.php?t=47014&page=2)

---

