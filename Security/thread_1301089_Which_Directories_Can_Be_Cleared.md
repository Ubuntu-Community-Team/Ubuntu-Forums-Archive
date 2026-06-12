---
title: "Which Directories Can Be Cleared?"
date: 2009-10-25
forum: Security
---

### Post by Nuvious on 2009-10-25
I'm writing a script that shreds all the files in certain directories in order to completely clear any tracks at the end of a session.  I'm currently shredding:

/var/log
/tmp
/home (obviously rebuilding the directories afterwards)

Are there other directories that I should be shredding?  Could shredding these directories pose a problem?  Any advice is greatly appreciated!

---

### Post by lensman3 on 2009-10-25
You might look in /root and delete some stuff in there, especially .history.  Make sure the /usr/tmp in a "ln -s" to /tmp ( on my system it is linked to /var/tmp). 

/var "stuff" might be cleaned out too.  It might be better to make /var point to a loop device which is entirely in ram.  So when you reboot that file system mount point would go away.

If you are worried about security, scramble the swap partition.

---

### Post by cariboo on 2009-10-25
If you are that worried about security, why not just use a Live CD all the time.

---

### Post by shaggy999 on 2009-10-26
Better yet, why don't you just mount those directories to tmpfs (i.e. ramdrive) and make sure you have no swap? No need to wipe files if they only existed in RAM....

---

### Post by Lars Noodén on 2009-10-26
> **Nuvious said:**
> 
Are there other directories that I should be shredding?  Could shredding these directories pose a problem?  Any advice is greatly appreciated!

It depends on the session.  What kind of session?

You can look at aide or tripwire or radmind as possible ways to roll back to earlier 'editions'.  Or the live cd suggestion was good.  This might also be one of the few cases that virtualization (see virtualbox or qemu) is useful, mainly for the ability to run from a snapshot.

---

### Post by Nuvious on 2009-10-27
> **cariboo907 said:**
> If you are that worried about security, why not just use a Live CD all the time.

I'm developing a virtual image that will go onto a cloud computing system and ideally any cloud.  The data I'm working with won't fit in memory and is pottentially sensitive to the point where we wouldn't even want the cloud service to be able to read it off the disk when we're done running our system.

> **Lars Noodén said:**
> It depends on the session.  What kind of session?.

Undetermined.  This will be a base system from which other systems are built.  For that reason there needs to be some ammount of consistancy and the ability to install new software (Live CD's not viable here either).

> **Lars Noodén said:**
> You can look at aide or tripwire or radmind as possible ways to roll back to earlier 'editions'.  Or the live cd suggestion was good.  This might also be one of the few cases that virtualization (see virtualbox or qemu) is useful, mainly for the ability to run from a snapshot.

These solutions sound like preventative measure during operation, and it would probably be worth it to look over them.  However, I'm thinking about security post-boot where the user could potentially forget to delete sensitive files, files could be left in swap, or portions of files or sensitive logs could be left in one of the many tmp directories which could later be mined by the cloud service provider.

---

### Post by Lars Noodén on 2009-10-27
Prevention is where it is at.  

Otherwise, you can look around, 

find /var /tmp -user nuvious -print

find /home/nuvious/ -type d -iname '*cache*' -print

find / -type f -user nuvious -name '.~*' -print

find / -type f -user nuvious -name '*#' -print

find / -type f -user nuvious -name '*.swp' -print

---

### Post by Lars Noodén on 2009-10-27
> **Nuvious said:**
> I'm developing a virtual image that will go onto a cloud computing system and ideally any cloud.  The data I'm working with won't fit in memory and is pottentially sensitive to the point where we wouldn't even want the cloud service to be able to read it off the disk when we're done running our system.


Security, or at least that level of privacy, and hosting don't go together.   Cloud is another name for hosting and might be in the same category as 'push' computing was...

What is it about a dedicated server that appears not to meet the requirements here?

---

### Post by Nuvious on 2009-10-27
> **Lars Noodén said:**
> Security, or at least that level of privacy, and hosting don't go together.   Cloud is another name for hosting and might be in the same category as 'push' computing was...

What is it about a dedicated server that appears not to meet the requirements here?

I'm not trying to run a server, just a job on a cloud.  I have a lot of data I need to analyze and it would be nice to run it on a cloud and utilize 10 or more processors for parallelization.  I don't need a 'dedicated server' just a bunch of processors for a few days.

After that I don't need those processors anymore.  Running on a cloud is much more economical and very different from deidcated hosting (would only cost me 40 bucks to run my job on EC2 if it took 1 week to complete and that's way cheaper than buying my own dedicated cluster).

---

### Post by niteshifter on 2009-10-28
> **Nuvious said:**
> I'm developing a virtual image that will go onto a cloud computing system and ideally any cloud.  The data I'm working with won't fit in memory and is pottentially sensitive to the point where we wouldn't even want the cloud service to be able to read it off the disk when we're done running our system.


Sigh. You don't seem to realize that from the instant you hand over your code and data to the service that Mr. Evil Sysadmin they have employed (but don't know about) has access to it. At any time during use or after.

In short, cloud computing is not a magical apparatus that blows away on the wind when you're done, it's just a (group of) computers **that you don't control** and ipso facto **you are sharing with others**.

---

### Post by Nuvious on 2009-10-30
> **niteshifter said:**
> Sigh. You don't seem to realize that from the instant you hand over your code and data to the service that Mr. Evil Sysadmin they have employed (but don't know about) has access to it. At any time during use or after.

In short, cloud computing is not a magical apparatus that blows away on the wind when you're done, it's just a (group of) computers **that you don't control** and ipso facto **you are sharing with others**.

No, it's a group of virtual machines that run on one of many comptures.  The entire virtual machine is held on a server somewhere in its entirety when it's not in use (re-uploading the image is a waste of bandwidth and would increase costs). The virtual machine file is what I'm concerned about especially when it comes to malicious attacks on the cloud server from 3rd parties.  Also pulling data from the machine while it's running would result in a significant slow-down which I could detect (reading RAM images or copying the file system while my process is running would result in paging which would cause my program basically to never finish at which point I could kill the machine and start pressing charges).  It's only when the virtual machine is off and on the cloud's server that I need the data to be securely deleted, thus secure deletion at shutdown is reasonable enough security from my standpoint.

---

