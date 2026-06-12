---
title: "What is the worst error you did in Ubuntu if any?"
date: 2010-04-15
forum: The Cafe
---

### Post by TheNerdAL on 2010-04-15
Mine was that I used Computer Janitor and might have deleted something important now I have to do a fresh install. D: What about you?

---

### Post by undecim on 2010-04-16
In class once with my laptop trying to wipe a flash drive (it had sensitive data on it), I used sda instead of sdb with the dd command.

Lost 3 days of non-backed work.

---

### Post by ThePinkPoo on 2010-04-16
My netbook likes to black screen with the blinking cursor.  That's a pain in the ***.

---

### Post by Firestem4 on 2010-04-16
One time I accidentally deleted /tmp. Recreating this file normally is a no-no because /tmp has some special file attributes and I believe a specific sticky-bit. I didn't know this at the time and when I accidentally remove /tmp and tried to recreate it, I couldn't log into my desktop session anymore :(

---

### Post by NightwishFan on 2010-04-16
Ran a binary package without an uninstall script and couldn't track down where all the pieces went, so I reformatted my root drive to ensure it was gone.

---

### Post by benmoran on 2010-04-16
This was when I first started using Linux. I got tired of not being able to access system files due to permissions. I when about changing the permissions on every single file on the machine to myself. Needless to say, after a long process, the system was unbootable.

---

### Post by Random_Dude on 2010-04-16
Accidentally deleted the shut down button.8-[

---

### Post by Khakilang on 2010-04-16
Try to install software through Synaptic and he next thing I know it has broken dependencies error. I have to re install the whole computer again and use only Software centre for software I need.

---

### Post by gemmakaru on 2010-04-16
I removed all the compiz files to "fix" an issue I was having, without switching to metacity.  This resulted in windows with no borders.  Reinstalling compiz fixed it.

Many years ago I had a suse server with a raid 1 and all my files on it.  I had a faulty IDE channel on the card which corrupted one of the disks.  I rebuilt the raid using a different IDE channel but copied the corrupted disk over the good one, loosing all the data.  Not sure if that was me or the system at fault though.  I could have prevented it.  Ok that wasn't ubuntu but could happen with any distro.

---

### Post by nothingspecial on 2010-04-16
When I got my first computer, I couldn`t get the sound to work.

So I asked Mr Google.

And I learned all kinds of cool linuxy stuff like editing /etc/modprobe.d/alsa-base and recompiling alsa. I messed about that much I even reinstalled a couple of times.

It turned out that you have to plug the speakers into the green hole...

---

### Post by fromthehill on 2010-04-16
chmod 777 on on every single file in the filesystem

---

### Post by NightwishFan on 2010-04-16
> **fromthehill said:**
> chmod 777 on on every single file in the filesystem

Owned.

---

### Post by idef1x on 2010-04-16
Not particulary in Ubuntu...it was my first encounter with Linux a year of 15 back..

I decided once to clean up some stuff on my brand new installed Slackware system and the files /etc/mtab and /etc/fstab looked the same to me, so deleted mtab. If i remember correclty the whole system hung at that time and rebooting didn't solve it so reinstalling was the only thing i could think of at that time..

I kept on saying to myself that at least it's the best way to learn a system ;)

---

### Post by Mustard on 2010-04-16
Running a windows virus in Wine, that I had found in an email attachment, just to see what it would do.  Then realising it was actually working and downloading things to my .wine folder. I wasn't too keen to use that Wine install anymore.

---

### Post by Daisuke_Aramaki on 2010-04-16
Not in Ubuntu, but I did something stupid on a FreeBSD box once. Wanted to deinstall a program, but instead of deinstalling from the program directory, issued the deinstall command from the top ports directory. Came back after three hours and realized all programs that I had installed had gone! Wasted another five hours installing everything again.

---

### Post by Doctor Mike on 2010-04-16
When I first started using Ubuntu I was using a wubi install. I tried to compile a custom kernel. I'm not completely sure, but I don't think you can do that with a wubi install.

---

### Post by tadcan on 2010-04-16
While backing up my home folder to an external drive, I deleted my actual home folder on Ubuntu and lost about two months of documents. Luckily some of it was recovered with software.

---

### Post by eriktheblu on 2010-04-16
I deleted /boot once on my wife's machine.

She only runs MS Windows now :(.

---

### Post by undecim on 2010-04-16
> **nothingspecial said:**
> It turned out that you have to plug the speakers into the green hole...

I can't count high enough to enumerate all the times that kind of thing has happened to me.

---

### Post by rafita on 2010-04-16
I got 1GB mixed up with 1TB in gparted, and formatted my external HD instead of my USB strick.

---

### Post by doas777 on 2010-04-16
> **rafita said:**
> I got 1GB mixed up with 1TB in gparted, and formatted my external HD instead of my USB strick.

yeah, that is one of mine as well. thank god for testdisk. they really need to right align the numbers so that longer ones stick out.

---

### Post by scouser73 on 2010-04-16
> **TheNerdAL said:**
> Mine was that I used Computer Janitor and might have deleted something important now I have to do a fresh install. D: What about you?

Same here when I used Computer Janitor, I thought it would only get rid of the crap...little did I realise, lol.

---

### Post by Penguin Guy on 2010-04-16
> **nothingspecial said:**
> It turned out that you have to plug the speakers into the green hole...
The first time I made a computer, it didn't work when I turned it on. After opening it up and checking for any loose wires, short circuits, etc I finally found that I'd forgot to turn the PSU on ](*,)

Also, when I was new to Linux, I opened up the group list as root and deleted all these groups I've never heard of ('bin', 'sys', 'tty', etc). It was only once I'd got halfway down the list that it occurred to me that they might be there for a reason...

> **NightwishFan said:**
> [QUOTE=fromthehill;9129928]chmod 777 on on every single file in the filesystem

Owned.[/QUOTE]
:lolflag:

---

### Post by DM was on fire! on 2010-04-16
> **nothingspecial said:**
> When I got my first computer, I couldn`t get the sound to work.

So I asked Mr Google.

And I learned all kinds of cool linuxy stuff like editing /etc/modprobe.d/alsa-base and recompiling alsa. I messed about that much I even reinstalled a couple of times.

It turned out that you have to plug the speakers into the green hole...

Oh god, I would've died had I ever done that! :c

I think my worst mistake was messing up xorg in an attempt to get my ATI video card to work better (and it turned out I had the worst video card for any Ubuntu user to ever own. Niiice...) 
I input the wrong info and ended up killing xorg (Linux actually *does* have BSODs. It's called "XORG IS BROKEN"). I wasn't aware of the whole sudo dpkg-reconfigure *-phigh* xserver-xorg command, so I ended up having to reinstall. n.n

---

### Post by Frogs Hair on 2010-04-16
Tried to update a Wubi install to 10.04 , I was in the cleanup stage before restart and the computer froze. 12 minutes remaining turned into an hour and I tried to boot. ( NO WAY ) I reinstalled Wubi and made a cd a week later.

---

### Post by murderslastcrow on 2010-04-16
Umm... I installed from a CD that didn't finish burning, so there was no xserver package. Also, once I tried to install Ubuntu with Gnome on a computer with 112 MB of RAM and a 400 Mhz processor.

---

### Post by dFlyer on 2010-04-16
It wasn't with ubuntu, but Red Hat many, many years ago, when I first started using linux. I did a rm -rf / as the super user.

---

