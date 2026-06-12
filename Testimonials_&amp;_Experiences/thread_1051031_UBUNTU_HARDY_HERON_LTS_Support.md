---
title: "UBUNTU HARDY HERON LTS Support"
date: 2009-01-26
forum: Testimonials &amp; Experiences
---

### Post by trixman on 2009-01-26
i have a question on Hardy Heron 8.04. i am a new user and love the         os i understand that it will have support for 3 years.  What happens after 3 years can you still use Hardy Heron.

thanks 

:KS

---

### Post by snowpine on 2009-01-26
Hi Trixman,

Yes, you can keep using Hardy Heron after 3 years, if you want to. What will happen is you will no longer get any updates/security patches/bug fixes, and the repositories will be closed, so it won't be as easy to install new applications. Hope that helps clear things up.

[http://www.ubuntu.com/products/whatIsubuntu/releases](http://www.ubuntu.com/products/whatIsubuntu/releases)

(edit) I should probably also add that, when the next LTS release comes out, you should be able to upgrade to it with one or two mouse clicks, and be good for another 3 years. :)

---

### Post by albinootje on 2009-01-26
> **trixman said:**
> i have a question on Hardy Heron 8.04. i am a new user and love the         os i understand that it will have support for 3 years.  What happens after 3 years can you still use Hardy Heron.


After the "end of life" you can still use it, but there will be no security updates for it anymore, and the repositories will eventually disappear.
When that moment arrives you can test the new LTS from the installation cdrom, and if it works fine, install that.

---

### Post by trixman on 2009-01-26
so i can update from within Hardy Heron and not lose any information.

thanks for the help

:KS

---

### Post by overlord.gaurav on 2009-01-26
> so i can update from within Hardy Heron and not lose any information.

Yes, you can. Your 'Update Manager' will prompt you to upgrade to the newer version.

---

### Post by trixman on 2009-01-26
thanks for the help. these forums are such a big help.

:popcorn:

---

### Post by albinootje on 2009-01-26
> **trixman said:**
> so i can update from within Hardy Heron and not lose any information.


It makes much more sense to make backups and reinstall from scratch if the new LTS release is there.
Because upgrading from one LTS to another means more than one upgrade, and one upgrade can already take between 1 and 2 hours, depending on your hardware, and which packages you have installed.
It's also not a 2 mouse click procedure, it's much more than that.
Also in the middle of the upgrade you can expect questions, it's not like a normal installation, where you can have a break when the initial installation starts.

---

### Post by trixman on 2009-01-26
ok, how do you make a backup. and then restore it when installing

:KS

---

### Post by snowpine on 2009-01-26
> **albinootje said:**
> It makes much more sense to make backups and reinstall from scratch if the new LTS release is there.
Because upgrading from one LTS to another means more than one upgrade, and one upgrade can already take between 1 and 2 hours, depending on your hardware, and which packages you have installed.
It's also not a 2 mouse click procedure, it's much more than that.
Also in the middle of the upgrade you can expect questions, it's not like a normal installation, where you can have a break when the initial installation starts.

Actually you can upgrade directly from one LTS to the next LTS (for example 6.06->8.04) without going step-by-step. And the next LTS doesn't even exist yet (it's coming in 2010) so we don't know exactly what the upgrade procedure will be--why worry about it at this point? ;)

---

### Post by albinootje on 2009-01-26
Here's a howto for having a separate /home partition :
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Making the backup would be about /home and perhaps also /etc

If you have a web server and mysql server running, then you need also backups from /var/www and /var/lib/mysql.

Note: making backups onto usb devices with FAT32 or NTFS will mess up your Linux permissions on your files and directories.
I recommend using archiving software like tar or zip to make archives from all the dot files and dot directories (e.g. .mozilla/) in your /home, and copy those archives to the usb drive.
For data files like audio and video it's not such a problem as you can easily revert the permissions of those if you like.

---

### Post by trixman on 2009-01-26
thanks for the help. i was just curious .

thanks to all
;)

---

### Post by albinootje on 2009-01-26
> **snowpine said:**
> Actually you can upgrade directly from one LTS to the next LTS (for example 6.06->8.04) without going step-by-step. 

Good to know, thanks. (... hits invisible Thanks button)
> 
And the next LTS doesn't even exist yet (it's coming in 2010) so we don't know exactly what the upgrade procedure will be--why worry about it at this point? ;)

Agreed :)

---

### Post by waspbr on 2009-01-26
you are right, you don't have to worry about that yet. But it is wise to back up your files on a regular basis, say once a month, it may happen that one day your hard drive may go belly up (yes I am looking at you western digital, hellooo maxtor). 

there are several ways to back up your files, such as pictures, documents, etc. A USB drive would probably be the easiest way to back up your files just in case. 

Note, you should always back up your files regardless of the OS you use

---

### Post by wolfen69 on 2009-01-26
> **trixman said:**
> ok, how do you make a backup. and then restore it when installing

:KS

i just keep my personal files backed up and do a clean install. no big deal.

---

### Post by SpenceMakesSense on 2009-01-26
I know some else mentioned this but making your home directory can be easy and to do and saves a lot of time. All youd have to do is reinstall the programs you previously had and all the settings you had for that program are saved in the home directory so it will practically be the same thing after reinstalling the programs. And also it keeps your theme too. Which I found really cool first time I seperated my home partition and upgraded.

---

### Post by wolfen69 on 2009-01-26
you can also backup your home directory without having a seperate home partition. open home and do ctrl-H. then copy and paste.

in my case, the only config files worth saving is my .mozilla and .mozilla-thunderbird

everything else only takes a couple extra minutes to get it back where i had it. the important things are my personal data files which i backup once a week.

---

### Post by solwic on 2009-01-26
> **wolfen69 said:**
> you can also backup your home directory without having a seperate home partition. open home and do ctrl-H. then copy and paste.

in my case, the only config files worth saving is my .mozilla and .mozilla-thunderbird

everything else only takes a couple extra minutes to get it back where i had it. the important things are my personal data files which i backup once a week.

I used to back up my /home directory...but I've got about 80GB of media, and that can take a while, even if you only have to do it once.  

I reinstalled Ubuntu this week when I added Windows XP back to the system (easier to start over with Windows, then add Ubuntu, than it is the other way around), and for the first time put my /home on its own partition.  I'll still update my backups, of course, but as long as I dont bork the partition table, it should save me two hours of copying files back over.  :)

---

### Post by lswb on 2009-01-26
> **trixman said:**
> so i can update from within Hardy Heron and not lose any information.

thanks for the help

:KS

Don't count on trouble free updates. Back up your data before doing a version upgrade. Jst read the forums anytime after a new version is released and you'll see why backups are a good idea.

---

### Post by cariboo on 2009-01-26
If  you use rsync or some of the other backup programs available through ther repositories, only the first backup takes a while, after that only changed files get backed up. I complete backup of my home directory takes about an hour, incremental daily backups take less than 3 minutes, unless I've downloaded something big, then it may take a little longer. 

The backup off my home partition on the my server also gets backed up to an external hard drive daily. I hate loosing personal data.

Jim

---

