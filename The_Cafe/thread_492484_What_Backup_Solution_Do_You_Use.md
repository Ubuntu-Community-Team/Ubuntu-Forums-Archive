---
title: "What Backup Solution Do You Use?"
date: 2007-07-04
forum: The Cafe
---

### Post by andrewsomething on 2007-07-04
I was just wondering what different back up solutions others are using. Do you make a disc image with GParted's live CD? What programs out there offer scheduled back ups?

I just started using Simple Backup. Any one else? Luckily I haven't had to put it to the test yet. Has it worked for you?

How about TimeVault? I haven't tried it, but there's lots of discussion going on in the Gutsy Development thread about it...

---

### Post by reacocard on 2007-07-04
I use rsync with a couple of shell scripts (so I don't have to remember all those options).

If you want to use rsync, this is what I use for /, just adapt it as you need (note that it MUST be run as root, other wise you'll have permissions issues.):
```
rsync -avhxWSDHE --super --delete --progress --delete-after --ignore-errors --exclude /tmp/ --exclude /var/tmp/ --exclude /var/run/ --exclude /lost+found/ --exclude /var/lock/ / /media/Aren\'s\ Drive/backup/root
```
(replace '/media/Aren\'s\ Drive/backup/root' with where you want it to backup to)

 I don't schedule backups because it's a laptop, so the external HD isn't always connected. If you want it scheduled, just link it into cron or something.

---

### Post by djsroknrol on 2007-07-04
Partimage has always worked well for me...

---

### Post by Kujen on 2007-07-04
I backup everything important to a networked harddrive.

---

### Post by wolfen69 on 2007-07-04
i just put all things i want to save on seperate drives. if a major problem arises,(which is rare) reinstalling is no big deal. remember, a fresh install is the cleanest "image". i like fresh things. but that's just me.

---

### Post by FoolsGold_MKII on 2007-07-04
I back up documents, configs, media, program installers, etc. I don't bother backing up the while system though.

DVDs work fine, nothing fancy.

---

### Post by Atomic Dog on 2007-07-04
I use Acronis True Image.  I boot the live cd and make an image on a USB hard drive.  The image can be password protected which is nice.

I have recovered win and linux images and it has worked flawlessly.  It is a great program and only costs $30.  Of course it's a Windows program, but once you install it on a win box and burn the live CD you'll never need the Win version again.

---

### Post by ramjet_1953 on 2007-07-05
I have a laptop, so I bought a second HDD and placed it in one of those small USB enclosures.

I then downloaded [COLOR="Blue"]Ghost for Linux (G4L)[/COLOR] and use it for the ultimate backup, as it makes an exact 1:1 clone of my on-board HDD, including GRUB.

Ghost for Linux is a self-booting stand alone application. You just download the iso and burn it to a CD and then boot from the CD.

If the unthinkable happens, all I have to do is swap the hard drive out with the clone.

Of course, copying an entire HDD using a USB port takes a bit of time. About 3.5 hours for my 120 Gb HDD.

Here's the link for the download:

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

Regards,
Roger :cool:

---

### Post by Papi-KB7VGW on 2007-07-05
I just tar /home and burn that to a cd.  I'm not even bothering to back up windows because it isn't used anymore.  I agree that a fresh install and then adding what I want from the repositories is quick enough.  If I forget to install something then I didn't use it anyway.  ;)

---

### Post by wolfen69 on 2007-07-05
> **Atomic Dog said:**
> I use Acronis True Image.  I boot the live cd and make an image on a USB hard drive.  The image can be password protected which is nice.

I have recovered win and linux images and it has worked flawlessly.  It is a great program and only costs $30.  Of course it's a Windows program, but once you install it on a win box and burn the live CD you'll never need the Win version again.

although i dont do images anymore, i can vouch for acronis true image. it is a great program for imaging.

---

### Post by andrewsomething on 2007-07-05
> **Papi-KB7VGW said:**
> I just tar /home 

That had previously been the way I did it. As someone up thread said, if you can't remember I programs you had installed, you probably don't need them. (Not to mention that most of my data is stored on  another drive anyway). Yet, I'm always interested in new solutions that make the desktop easier for people who don't want to even think about it. 

I haven't tried it yet, but I'd love to tell my Mac using friends that TimeVault can already do what is supposedly one of Leopard's best features... 

Keep the ideas coming!

---

### Post by beercz on 2007-07-05
[http://rsnapshot.org]("http://rsnapshot.org/")

---

### Post by Hallvor on 2007-07-05
I use Acronis True Image too. Just backup everything to an external hard drive using the live-cd.

---

### Post by moredhel on 2007-07-05
my /home is actually a seperate 80gb harddrive :D

---

### Post by reclusivemonkey on 2007-07-05
rsync +1

Backups are one of those things where you are more than happy to rely on simple CLI applications that have been around for eons =]

---

### Post by brim4brim on 2007-07-05
I don't.  I don't have anything too important on my laptop.  I have the important stuff backed up to my parents computer, my external HDD and my memory stick.  I had it on my iPod too but that broke so I might throw them on my new player at some point.

I usually burn a CD of my home folder when a new version of Ubuntu comes out and install the new version by wiping the old partitions as I like having a really clean install to get rid of the junk programs I was trying out as I'm still relatively new to Ubuntu and Linux and whenever I need a program, I install 3 and work out which one is best for me, then uninstall the others.  I've become paranoid about stuff left around since I found my temp folder in Windows had grown to 4GB as Windows only empties it if you run disk cleanup which takes forever because first it works out what files can be compressed which is a stupid thing to do so I never run it.  So run on sentences eh?  Aren't they great?  I'll learn English someday.

---

### Post by AndyCooll on 2007-07-05
I use an rsync to backup certain directories to an external HDD. I've then added that script to the cron so it just runs overnight.

:cool:

---

### Post by graphicgolem on 2007-07-05
I use one that really works and Ive been trying quite a few different methods for about 2 weeks now...simple backup, part image, rsync, tar and g4l all of which may create a 'backup' but in my experience they are unable to restore (and ive played about with grub quite a bit too). With Acronis  i have sucessfully created a full system backup and restored it to a new HD (and I am running off it as I wirte) all within about 1hour! Its not open source or free but it certainly works. Please forgive me if I seem a little disparaging of the other backup methods mentioned, I am still very much a noob as far linux goes but I was becoming a nervous wreck trying to find a a backup method that does what it says on the tin!

---

### Post by starcraft.man on 2007-07-05
> **Hallvor said:**
> I use Acronis True Image too. Just backup everything to an external hard drive using the live-cd.

+1 

Drive imaging is the best back up for a hardrive IMO. You do one on a clean install and can restore at whim. As for data, I have a select few folders in the home, I sync them manually or with a script when its a lot. :)

For those looking for a good free one try partimage.

---

### Post by HermanAB on 2007-07-05
Acronis is for wimps.  Real men use dd, gzip and rsync.
;)

---

### Post by x0as on 2007-07-05
I use dd to create an image from a clean install which is burnt onto dvd, /home is rsync'd onto an external hd.

---

### Post by Quillz on 2007-07-05
I use Acronis True Image on Windows, Time Machine on Mac OS X and just manual copying of my /home directory on Linux to another external hard drive.

---

### Post by Polygon on 2007-07-06
i use sbackup (simple gnome backup) on ubuntu. Works, and after the initial backup, it only makes backups of the differences to save space.

its called sbackup in the ubuntu repos.

---

