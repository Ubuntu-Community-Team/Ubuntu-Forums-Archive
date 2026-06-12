---
title: "Whats your favorite way to hose an Ubuntu install?"
date: 2008-11-06
forum: The Cafe
---

### Post by meg23 on 2008-11-06
These are a few of my favorite ways:

1. configuring grub manually and screwing up the whole thing
2. bad partial kernel upgrade
3. installing virtualbox on a hardy from apt
4. accidentally deleting filesystem using rm -rf by mistyping file location

---

### Post by earthpigg on 2008-11-06
1

---

### Post by beno1990 on 2008-11-06
> **meg23 said:**
> These are a few of my favorite ways:

1. configuring grub manually and screwing up the whole thing
2. bad partial kernel upgrade
3. installing virtualbox on a hardy from apt
4. accidentally deleting filesystem using rm -rf by mistyping file location

Way to avoid #2:

Always keep a secondary kernel installed as a backup.

Way to avoid #4:

Never delete anything from within /.

---

### Post by billgoldberg on 2008-11-06
I've hosed a few installs.

My favorite was installing ATI drivers manually when I first started using Linux.

I printed out the instructions and they didn't work.

I rebooted and the desktop was unusable.

30 minutes later I looked at the brown default gnome layout.

---

### Post by JohnFH on 2008-11-06
Don't quite know what you mean by favourite, but #4 is the most effective although #2 would frighten me as well.  Grub can easily be restored and I've never had or even heard of a serious problem with #3.

Early on in my Linux life, although I'm still very young (in terms of my Linux years), I wanted to delete a partition to reorganise my disk space.  When asked for the sudo password, I just thought to myself "Yeah, I know what I'm doing - I know it all!" so entered the password and then deleted the wrong partition.  I didn't have a clue what I was doing.  

Biggest threat to my Ubuntu install is ME!  Idiot.

---

### Post by kevdog on 2008-11-06
Install Ubuntu on old crappy hardware -- That usually really confuses the alternate install disk.

---

### Post by Barrucadu on 2008-11-06
> **JohnFH said:**
> Early on in my Linux life, although I'm still very young (in terms of my Linux years), I wanted to delete a partition to reorganise my disk space.  When asked for the sudo password, I just thought to myself "Yeah, I know what I'm doing - I know it all!" so entered the password and then deleted the wrong partition.  I didn't have a clue what I was doing.

I did that once! The thing is, it was my data partition with schoolwork and suchlike on. I was panicking. Then I relaxed, took a deep breath, and recreated the partition with sfdisk. I have fixed *so* many partition problems, I should really double check these things.

---

### Post by Thelasko on 2008-11-06
None of the above, 1-3 are totally fixable.  Not installing software from the repositories is my preferred method.

---

### Post by Ozor Mox on 2008-11-06
I can't remember the command exactly but it's something like

dd if=/dev/urandom of=/dev/sda

---

### Post by meg23 on 2008-11-06
The virtualbox install was definitely the most unexpected. That is definitely my favorite totally unexpected way to hose an install.

---

### Post by aaaantoine on 2008-11-06
> **meg23 said:**
> The virtualbox install was definitely the most unexpected. That is definitely my favorite totally unexpected way to hose an install.

I guess I should consider myself lucky this didn't happen to me.

Here's one: recompiling a kernel, without really knowing what the hell it is you're doing.

I guess this could apply to any Linux install.  The above is the only time I can recall actually hosing a Linux OS.  I did it when I was experimenting with Mandrake back in 2005.

---

### Post by Thelasko on 2008-11-06
> **aaaantoine said:**
> Here's one: recompiling a kernel, without really knowing what the hell it is you're doing.
That falls under, "Not installing software from the repositories" in my opinion.

---

### Post by Keith Hedger on 2008-11-06
Accidentally using truecrypt to create an encrypted drive but got the partition number wrong...now where did I put that install disk?

---

### Post by xArv3nx on 2008-11-06
> Whats your favorite way to hose an Ubuntu install? 
Update Manager. :mad:

---

### Post by malleus74 on 2008-11-06
Installing updates without a backup ;)

---

### Post by earthpigg on 2008-11-06
so what is the deal with virtualbox...?

---

### Post by meg23 on 2008-11-06
There is some bug with the updates that royally screws up hardy heron. I lost internet and has lots of freezes. After a reboot, nothing would boot up, not even in recovery mode.

---

### Post by lukjad on 2008-11-06
Use Automatix. ;)

---

### Post by bodhi.zazen on 2008-11-06
None of the above,

Install Arch over the top :twisted:

---

### Post by bodhi.zazen on 2008-11-06
> **lukjad007 said:**
> Use Automatix. ;)

:lolflag:

---

### Post by compiledkernel on 2008-11-06
> **lukjad007 said:**
> Use Automatix. ;)

Dont you mean Ultamatix? :)

---

### Post by snova on 2008-11-06
> **aaaantoine said:**
> Here's one: recompiling a kernel, without really knowing what the hell it is you're doing.

I once tried that. The trouble was, the build system generated about half a dozen files. I couldn't tell which one was supposed to be booted and which ones weren't, or which ones were temporary...

Fortunately I didn't screw anything up, it just refused to boot. (I think I had gotten the right one, though.)

---

### Post by chucky chuckaluck on 2008-11-06
when i still used ubuntu, i was a bit fanatical about stripping off stuff i didn't need. i once really screwed up by opening synaptic and checking everything for removal that i never heard of and was sure i didn't need.

---

### Post by lukjad on 2008-11-06
> **compiledkernel said:**
> Dont you mean Ultamatix? :)
I mean Automatix in all its forms. :p

---

### Post by forrestcupp on 2008-11-06
Favorite way to hose Ubuntu:

Just start it up. :)  joking

My favorite was when I had an ATI card installed and I replaced it with an nvidia card and X didn't work anymore without a lot of tears and work.  Even after taking precautions so that wouldn't happen.

---

### Post by init1 on 2008-11-06
Yeah, I rm'd / on a Mandriva install once, since I was going to delete the partition anyway. It was kinda cool seeing the entire system slowly die :twisted:

---

### Post by jimi_hendrix on 2008-11-06
this isnt ubuntu but...when i tried to install arch i connected to the internet, installed xorg, messed up my xorg configuring, rebooted, fixed problem, got error when trying to connect to internet...wasting a friday afternoon

---

### Post by aaaantoine on 2008-11-11
> **Thelasko said:**
> That falls under, "Not installing software from the repositories" in my opinion.

Ah, I missed that.  Yes, installing software using any other method than directly from the Ubuntu repositories is pretty much asking for trouble if you're a newbie.

---

### Post by tuxsheadache on 2008-11-11
Let's see...
1st time: I changed the drivers for my graphics card, next thing I knew the screen was one big flicker.
2nd time: I did exactly the same thing hoping I wasn't dumb enough to click wrong one again, I was.
3rd time: deleting the wrong partition
4th time: deleting the right partition, but set everything the wrong format or something :S (I love partitions xD)
5th time: Switching it off when it was trying to come out of hibernate, it didn't like that.
6th time: I guess sometime within the next week, just watch me.

---

### Post by malleus74 on 2008-11-17
:lolflag:

---

### Post by Sorivenul on 2008-11-17
> **chucky chuckaluck said:**
> when i still used ubuntu, i was a bit fanatical about stripping off stuff i didn't need. i once really screwed up by opening synaptic and checking everything for removal that i never heard of and was sure i didn't need.

I've done that, more or less.  Stripped out things I didn't need and didn't think I needed, then changed my sources.list to the development release.  Nightmare.  This was back with Edgy I believe.  Haven't borked an Ubuntu install since unless I had a bad update from the development branch on my testing machine.

---

### Post by Grant A. on 2008-11-17
"Tinkering" with system files.

---

