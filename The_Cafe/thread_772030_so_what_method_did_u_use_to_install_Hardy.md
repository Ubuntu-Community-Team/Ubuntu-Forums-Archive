---
title: "so what method did u use to install Hardy?"
date: 2008-04-28
forum: The Cafe
---

### Post by madjr on 2008-04-28
After a few days everybod upgraded i suppose.

what method did u use?

and how well did it go

First time i used **unetbootin**, really cool, fast and easy. **No CD requiered or windows** like wubi (but u may do so from windows too).

Unetbootin works just like the live-cd, but instead uses your old partition as a virtual CD. You'll need to create a new partition. **Don't format the partition where Unetbootin or desktop iso are.**

you'll also need **libqt4-gui**, look for it in synaptic

---

### Post by PartisanEntity on 2008-04-28
I did a fresh clean install from the Live CD on my MacBook. On my Asus laptop I did an upgrade.

---

### Post by Tundro Walker on 2008-04-28
You need to add the "Update Manager - Distro Upgrade" option to your menu selection.

I did it that way, as I'm sure quite a few other folks did, too.

It was really difficult, too ...

1) Update Manager says there's updates
2) You click "Upgrade to Hardy" (or whatever the button said)
3) You wait 5 hours for your comp to d/l everything
4) You click a random "OK" box to confirm over-writing some setup files (not sure why they can't start off with a "do you want to Auto-Yes to all?" button ... it would make that easier)
5) It runs, cleans up and you're done

Of course, it reinstalls a bunch of stuff, so you have to go through and uninstall that stuff again.  But really, ever since Edgy, I haven't had an issue with using the update/upgrade manager.  (System crashed when I tried it from Dapper to Edgy, but from Edgy to Gutsy, and now to Hardy, haven't had any issues).

I'll probably get flamed for not fresh-installing Hardy, but honestly, I thought Ubuntu was striving to go beyond that annoying MS Windows habit.

---

### Post by billgoldberg on 2008-04-28
I always use the livecd to install a new ubuntu version.

Why?

- you can see if everything works (to some degree)
- you can use it to install ubuntu on multiple pc's
- you can use it as a rescue disk
- I want to start from scratch in the customization process.

You have to back up your data before installing, but making a back-up never hurts anyone.

---

### Post by vishzilla on 2008-04-28
used the alternate cd. mounted the iso from the terminal and upgraded

---

### Post by gn2 on 2008-04-28
Xubuntu Alternate CD for my old laptop.

Ubuntu Live CD for my desktop PC.

---

### Post by LaRoza on 2008-04-28
Alt disk, install next to my 7.10.

I will delete the 7.10 as 8.04 works fine (better) and everything is the way I like it.

---

### Post by schauerlich on 2008-04-28
Upgraded from Distro Upgrade, but I will give it a clean install eventually. I just don't have the time to fix all the little issues I'll inevitably run into with a clean install with everything I have going on now.

---

### Post by FuturePilot on 2008-04-28
I hit the Upgrade button :mrgreen:

---

### Post by Moop on 2008-04-28
I used a live cd of Hardy beta 2 or 3 and never looked back. :)

---

### Post by hessiess on 2008-04-28
running it alongside feisty. might switch when I get everything working again. but im more lickly to switch when feisty is no longer supported.

---

### Post by aaaantoine on 2008-04-28
Burned a Live CD, and then wrote over my / partition.  My intact /home partition saved me a surprising bit of customization work.

---

### Post by venator260 on 2008-04-28
For my laptop, I did the Distro upgrade and hoped that I wouldn't have as much trouble as my Feisty>Gutsy upgrade, which I did not. Only had to sudo init 1 and Rebuild X, and the system seems to be perfect. 

For my desktop, it will be a fresh install, as I no longer have a use for it to be a Mythbuntu/Ubuntu box, and there is alot of stuff I want to clear off of it, so it's just easier to reformat & reinstall.

---

### Post by Corfy on 2008-04-28
I just used the "Upgrade Manager". Nothing fancy, but it worked.

---

### Post by -grubby on 2008-04-28
I used update manager -d to do a distro upgrade

---

### Post by doorknob60 on 2008-04-28
Other, I used Update Manager to upgrade while it was Alpha 6 :)

---

### Post by fedex1993 on 2008-04-28
upgraded from gutsy then reinstalled but looks like i am going to give arch a try.

---

### Post by Fedz on 2008-04-29
When I first installed Ubuntu ages ago (Ubuntu/6.10) I used a burnt live CD.

Decided to install on dual boot with Window$ but, soon found out things ran smoother on Ubuntu than Window$ so, when Window$ decided *not* to boot into I formatted the drive and just installed Ubuntu/6.10 as my sole operating system.

I've been upgrading via SPM to new distos since then with no problems :)

---

### Post by retrow on 2008-04-29
Upgrade from Gutsy to hardy alpha 3 went really well. Things were great until kernel 2.6.24.15 came out during beta testing stage. Several devices stopped working because of HAL errors. It wasn't long before final release came out, and I performed a clean install - and things are fine and dandy once again (and we have kernel 2.6.24.16 now).

---

### Post by Quillz on 2008-04-29
I guess "other," I installed a fresh copy of 8.04 onto a virtual machine on my iMac via a disc image.

---

### Post by amar on 2008-04-29
other again:
freash install from a live USB (ran out of CDs)

---

### Post by samjh on 2008-04-29
Voted "other".

gksu gedit /etc/apt/sources.list (change to Hardy)
sudo apt-get update
sudo apt-get dist-upgrade

Worked very well. :) Only CPU and HDD usage spikes are worrying me.

---

