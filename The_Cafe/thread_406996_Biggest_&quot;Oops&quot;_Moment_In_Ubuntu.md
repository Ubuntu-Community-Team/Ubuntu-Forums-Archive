---
title: "Biggest &quot;Oops&quot; Moment In Ubuntu"
date: 2007-04-11
forum: The Cafe
---

### Post by odelay on 2007-04-11
Just wondering what your biggest accidental screw up in Ubuntu was.  It could be either caused by something you didn't understand, or something you just did completely by accident.

I'll share.  Mine happened about an hour ago.  :D

So I have my /home directory on a separate partition and I wanted to install Mathematica on it.  I launch the install script on my desktop and when it asks for an install directory, I select ~/Install/Mathematica.  After the installation, I realized that the path it asked for was relative to its current directory so it actually installed in ~/Install/Desktop/~/Mathematica/.

So I tried dragging this "~" folder it created to the trash, but I didn't have the proper permissions (not sure why).  So I decided to delete it the manly way.

First I:
```
# cd ~/Desktop
```
Then:
```
# sudo rm -rf ~  (please don't paste this for any reason)
```

Note the missing "./".  

OUCH!  It took less than a second to delete my entire home directory (which was what I was using to backup my files...and in turn, wasn't backed up itself).  In my defense, I've gotten about 4 hours of sleep in the last 2 days and was already having a particularly bad day.

Sometimes you just gotta laugh about it.  I'm always complaining about how hard it is to actually remove files in Windows or OS X (graphically)...so I guess I had this one coming.  ](*,) 

So...what about you?

---

### Post by Brunellus on 2007-04-11
same thing happened to me, but back when I was running SuSe.  Some unknown smartasterisk on #suse on freenode had me do it.

---

### Post by ~LoKe on 2007-04-11
Why were you using sudo to remove something in your home directory? =p

---

### Post by gurgle on 2007-04-11
I cant remember what the command was, but I deleted my mp3 folder, about 60 gb worth. OOps!

---

### Post by bobbybobington on 2007-04-11
i couldn't install a new version of openoffice over the older one in suse10. So I tried to find the folder it was in and manually delete it. I think that borked it.

---

### Post by odelay on 2007-04-11
> **Brunellus said:**
> same thing happened to me, but back when I was running SuSe.  Some unknown smartasterisk on #suse on freenode had me do it.

You serious?!  I feel bad even typing the line with the off chance of someone (despite all the disclaimers) copying and pasting it.  I can't believe someone would actually tell you to do it.  Especially in a Linux forum...you think they, out of all people, would understand how much it sucks to lose all your data.


This day apparently is still going down hill.  I made my 2nd "Biggest Screwup" in Ubuntu just moments after the first one.  After reinstalling Kubuntu, I wanted to minimize the number of restarts to speed things up.  I first ran Update Manager and it installed the newest kernel.  Then, without restarting, I tried to remove the ".10" kernel in Adept.  This triggered a terminal prompt, but since it's in Adept, there's no way to select "proceed" or "abort" so I had to force quit and restart.

Now it stalls every time at 99% through the startup loading bar.  In the words of the Boss: I'm on fire.

BTW, if you're interested or know how to help my actual post is over [here]("http://ubuntuforums.org/showthread.php?p=2437715#post2437715").

---

### Post by odelay on 2007-04-11
> **~LoKe said:**
> Why were you using sudo to remove something in your home directory? =p
I guess the Mathematica installer gave special permissions to the install directory.  I wasn't able to remove it with sudo.  Makes no sense to me either.  What a freak accident.

---

### Post by Nikron on 2007-04-11
When installing eclipse/java-6-sun, I managed to screw up /etc/environment, my ~/.bashrc, and my audio by the time I got it working.  I got it all fixed without reinstalling though.

---

### Post by %hMa@?b&lt;C on 2007-04-11
I was reading about log files, and how they would fill up the hard drive (had not got to the part about how the system "rolls the logs")
so I cd'd to the /var/log and did a rm -fr needless to say, the system would not boot :(

---

### Post by mykalreborn on 2007-04-11
once i searched google for "how to be a hacker" and i remember that in the first few results there was a page which said that the best command to be a hacker was:
```
sudo rm -Rf \
``` - note the slash is inclined the other way.
thank god for my 1337 hx8r skills which saved my poor data from being deleted. :lolflag:

---

### Post by jdhore on 2007-04-12
for me, i've never had any major SNAFU's on Ubuntu...i do the rm -rf thing all the time to remove folders and sometimes i type / , but i stop myself before i hit enter.

---

### Post by DoctorMO on 2007-04-12
a couple of snafues, the main way to prevent the problem with rm is to alias it:

```
export rm='/usr/bin/safe_rm'
```

And safe_rm is a handy bash script which will normally move things into ~/.Trash; since you can't move / or ~/ into a sub directory of it's self your mostly safe from breaking your system.

Then you can just clean out your trash folder or have a cron job do it.

---

### Post by thisllub on 2007-04-12
Attempting to install NXServer I unpacked the files into the wrong folder.
Seeing the error of my ways I tried to copy them to the right place (/usr/bin) and overwrote something important. Trashed the whole system.
With a backup of /etc and a separate home partition it was a pretty quick reinstall.

---

### Post by Julolidine on 2007-04-12
I did a similar thing.  I was trying to mount a NAS hard drive via SHFS.  So I made a test mount of it, and put it in a folder called 'test'.  

Then I saw it worked, so I wanted to move it to the appropriate folder, and of course rather than unmounting I did an rm -r on the whole 250gig drive. 

BOOOOOOOOOOoo.   I was able to recover the data though.  It sucked and took hundreds of hours, but the drive was formatted fat32, so it was possible, but I lost all my long file names.  

The best advice I have heard with respect to ever using rm -r is first try the command

ls -r /path/

To check and make sure you're deleting what you really think you're deleting.

---

### Post by RandomJoe on 2007-04-12
Not Ubuntu-specific (in fact, the server was probably running Slackware at the time) but I very nearly managed to trash my RAID array once...  Got lucky...

I was at work, and needed to repartition and reimage a compact flash card for an embedded device.  I did this by inserting the CF card into a PCMCIA card then working with it on my Linux laptop.  Of course, I was also doing something via SSH on my home server.  While coworkers kept stopping by to chat or ask questions.

I got to the point where I needed to modify the partition on the flash card, so I ran fdisk and deleted/recreated the partition.  Saved.  Exited fdisk.  And THEN noticed the original partition type on the drive was 'fd' (Linux RAID)!  Oh _____....  I typed into the wrong shell window...

I spent the rest of the afternoon agonizing about what I would find once I got home, but got lucky.  After lots of HOWTO-reading and searching, I decided to just rerun fdisk, recreate the partition as 'fd', and see what happened.  For whatever reason - because I almost never get this kind of break - everything worked just fine!

---

### Post by stalker145 on 2007-04-12
Not that it's all that bad, but my worst 'oops' came a few days ago. I've been tinkering with Enlightenment and decided to try Entrance as my login. Well, I went and installed it, set it to default and rebooted to check out my beautiful new gateway to Linux. Well, i did *something* wrong and got a blank screen looking at me with my blank stare looking back. Luckily I was able to reboot into recovery mode, reset GDM to default, and get back to playing...

Next time (maybe this weekend) I'll learn a little more and plan a little better.

---

