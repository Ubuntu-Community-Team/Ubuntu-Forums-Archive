---
title: "Question on the philosophy of /home/&lt;username&gt;"
date: 2010-05-16
forum: The Cafe
---

### Post by held7over on 2010-05-16
Why would Linux advocate the user utilize his home directory (/home/<user name>) as his main directory? 

It just seems more logical to me to reserve the home directory (/home/<username>) for behind the scenes stuff like hidden configuration files, sounds (not music) files, collections of potential icons, etc., and then have a main directory (/home/<username>/General) where a user's actual data is stored, such as directories for Music, Video, Documents, Pictures, etc., and have your file manager open up in the /home/<username>/General directory.

The more stuff in a directory, the longer it takes to open, especially on older machines, and the home directory (/home/<username>) which contains all the config files doesn't need to be compounded with the user's actual personal data directories.

It also seems like illogical file structuring to classify "behind the scenes" stuff with personal stuff.

Why doesn't the standard install create "/home/<username>/General" to enforce a more logical structure? (Or /home/<username/Gen for short.)  

What am I not understanding that makes "/home/<username>" the logical choice for a new user and explains why such directories as Pictures and Music are automatically placed there as a seed pattern for the new user to follow?

Thanks for your thinking. :)

---

### Post by ranch hand on 2010-05-16
I am not sure exactly what you think is not logical about the system but I will give it a whack.

Linux is designed to be a multi user platform with all the data and configuration files for each user in in there /home folder.  That way when "Bob" logs in he gets his configuration and data and the some goes for "Virginia" and "Pete".

Most folks do not have enough data in their /home folder to have it be a problem on most boxes.  If they do they are probably capable of creating another partition and editing the /etc/fstab to mount at boot.

This is a safer thing to do anyway just to protect data and also be able to share that data between users with out giving others access to the /home folder.

I have no idea if that is of help to you or not.  I hope so.

---

### Post by Ozymandias_117 on 2010-05-16
You can set it up that way if you want... Just make a /Gen folder and add ```
cd ~/Gen
``` to you're ~/.bashrc file.

---

### Post by oldfred on 2010-05-16
If you multi-boot you may want to have the same data in each. I link in all the data folders from a data partition and only have settings and a few misc things in /home which now is about 1GB.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by held7over on 2010-05-16
I didn't mean to imply it was illogical to have the structure set up so that everyone's customized configurations were applied when they login. I meant it seems illogical to me to have configuration files stored in the same directory fallible humans are going to be playing in with their personal folders and all the splatter that accumulates in such a human main directory of personal stuff. For example--

I am setting up linux machines for people who don't know anything about linux. 

I have found that when they start personalizing their home directory, sometimes they forget the orientation I gave them and delete stuff they don't understand, thinking, I don't need that garbage in "MY PERSONAL STUFF!" Ha Ha Ha

So, I am thinking that I will set them up so that they are one step removed from their home directory when they open their file managers and start to do stuff and add stuff. /home/username/Gen - Which lets them do anything they want out of harms way in Gen.

I was just wondering if it would mess anything up moving the personal files from /home/username into /home/username/Gen and why that wasn't the norm, instead of the exception I am thinking of creating?

And thanks for the .profile suggestion. I will use that!

---

### Post by ranch hand on 2010-05-16
Wouldn't it be better to just educate them a little?  All the config files are .hidden, it they are finding those they ought to be capable of learning.

This could also encourage them to more experimentation with another user just for the purpose of learning.

---

### Post by Windows Nerd on 2010-05-16
The config files are hidden by default for a reason. If they know how to unhide them they probably know what they are for.

---

### Post by held7over on 2010-05-16
Those are valid points too. I've struggled with this for a while, which is why I have brought it to your attention for your thoughts.

And there is also the fact that by me moving the seeded directories like Pictures and Music to a /home/user/Gen, I am probably messing up any future use of some of the additional fancy menus now available, since they show these folders on a hard wired sidebar...should the new user discover how to implement them. -Although I the default menu is far faster anyway...

That just leaves me with the technical excuse of logical separation of classes for the only sake of being anal...but it is true that being hidden is a separation...although the undo is right on their menu. And that speed thing as the directory grows. 

I mention speed of access because my own main directory is pretty sizable and under load, takes a while to open in Nautilus....which makes me ask, why start with a head start on this problem?

I guess the biggest thing is, I want to try to assure their experience to be as smooth as possible for as long as possible, so they are way past their initial judging period of whether or not they like Linux or not. I do not do, dual boot systems. I feel dual booting is the painful way to make the transition as it does not make the person put the effort to make the hump. But, I can see its sales pitch value for the fearful. However, if I do things this way, not having M$ to fall back on seems to me to be more than enough learning curve up front...why tempt pitfalls.

---

### Post by Ozymandias_117 on 2010-05-16
> **held7over said:**
> That just leaves me with the technical excuse of logical separation of classes for the only sake of being anal...but it is true that being hidden is a separation...although the undo is right on their menu. And that speed thing as the directory grows. 

I mention speed of access because my own main directory is pretty sizable and under load, takes a while to open in Nautilus....which makes me ask, why start with a head start on this problem?

Er... How many items do you have? Also, computer specs? I have 137 files/folders in my Home directory and Nautilus opens in > 1 second...

---

### Post by ranch hand on 2010-05-16
When we bought this box it came with Vista on it.  First new computer in 10 years.

As Vista was a down grade from 98, I got another drive and installed 8.04 keeping the old drive as a spare just in case.

Never needed to hook it back in.  I think that you are right in that folks hit a problem and fall back to the known OS.

The problem with the "hardwired" menu, I think, would be no problem if you just put the new folder into the fstab to be mounted.

---

### Post by held7over on 2010-05-16
My personal system is a Dell PIII, 500Mhz, 497MB RAM,  Twin mirrored 250 Gig hard drives with cron calling rsync everyday on 155.4 Gig used.



My main directory is /home/<name>/Documents. I have 377 items there right now, with maybe part of that being 50 to 70 or so splattered (non folder) items that just got dumped in Documents.

If my machine isn't doing anything with maybe a couple of apps just loaded and ready, Nautilus takes about 12 seconds to open my Documents directory (I just timed it). If I have something running with a load, I may be waiting anywhere from 20 to 40 seconds. From there it can get worse as I add things.

---

### Post by ranch hand on 2010-05-16
I bet your ram is getting a lot of use.  I would get more and if it doesn't speed things up it will cut down on swap use (which really should help the speed).

I have a newer faster box but my picture folder, 3.7Gb opens fully in 2 seconds.  I am also running at about 42% ram.

The reason for all that ram usage is that I am running boinc at about full speed (99 to 100% of cpu usage on all 4 cpus).

There is no swap being used though.

My specs are in my sig.

---

### Post by held7over on 2010-05-16
I have 1.8 Gig dedicated to swap space. Right now, I have 9% swap being used with Evolution, Pidgin, Firefox, Gedit, Nautilus, and an open Terminal loaded, but all of them doing nothing except just stilling there. Under 9.10 that would have been closer to 2 to 4%. SO, there is something a bit more busy about 10.04.....so far.

I have another system that I snagged on eBay. I have set it up with a host server using OpenVZ, which when I figure out how to get the firewall up and get it talking to the outside world through my router, I plan to create a bunch of little websites on it plus try to launch a new business idea on web...if I am lucky.  But I must have messed something up, i think, in the networking, as when I try to download the OpenVZ environments, they download a ways, and then just stop downloading. While I can download them just fine on my personal PIII and transfer them via ssh or cd copy. So, I must have done something wrong in creating the host server. At any rate, I sometimes wish this machine was my personal machine! Ha. But I figure I am going to need its speed to do what I want to do... Below are it's spects:

HP Pavilion Media Center TV m8000n PC, AMD Athlon 64x2 Dual Core 5200+, 2.6 Ghz, 1MBx1MB L2 Cache, 2000Mhz System Bus, 2 Gig RAM, 500Gig Hard Drive, Optical DVD Burner, and 128MB Graphic Memory and TV/FM Tuner.

---

### Post by held7over on 2010-05-17
bumped putting SOLVED

---

### Post by nothingspecial on 2010-05-17
You have a valid question/point.

As has been discussed before, it makes sense to have each users config in their own home directory.

The point is, that however much you mess, alter, delete those (your own) configs, the actual programs are unaffected, and will run whatever you do to your /home folder, and in most cases, will generate you a new config should you delete the original one.

Makes perfect sense to me.

---

