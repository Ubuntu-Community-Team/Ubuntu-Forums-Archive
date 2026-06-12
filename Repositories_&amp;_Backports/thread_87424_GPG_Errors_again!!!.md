---
title: "GPG Errors again!!!"
date: 2005-11-08
forum: Repositories &amp; Backports
---

### Post by kudu on 2005-11-08
This just showed up again out of the blue. Been working just fine for several days if not weeks now but all of a sudden...BAM...broken again.


W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Must be the server side since I haven't changed anything in my sources.list lately and it was working fine.

kudu

---

### Post by pstudier on 2005-11-08
Exactly the same with me.  I reloaded for several days in a row and all was OK.  Starting yesterday I get the exact same message.  I haven't changed repositories or anything.

---

### Post by stacktracer on 2005-11-08
Same for me on dapper.

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

If I change my sources.list to say "archive.ubuntu.com" instead of "us.archive.ubuntu.com", I don't get the error. But this makes me nervous.

---

### Post by stacktracer on 2005-11-08
This works, but still makes me nervous:

[http://www.ubuntuforums.org/showthread.php?t=87123&highlight=gpg+error](http://www.ubuntuforums.org/showthread.php?t=87123&highlight=gpg+error)

---

### Post by bctechnzl on 2005-11-09
I am getting problems with my nz repositories

 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) is giving me W: Couldn't stat source package list  errors, (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Can anyone tell me whats going on?

---

### Post by towsonu2003 on 2005-11-09
may be they close servers from time to time for maintenance??

here is my error:

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Fetched 191B in 3s (57B/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems [did that 6 times]

---

### Post by rcmn on 2005-11-09
same here

---

### Post by towsonu2003 on 2005-11-10
still have this problem

can someone help? repository problems jeopardize security!

and why does this work??
[http://www.ubuntuforums.org/showthread.php?t=87123&highlight=gpg+error](http://www.ubuntuforums.org/showthread.php?t=87123&highlight=gpg+error)

---

### Post by verzonnen on 2005-11-11
Changing the repositories to archive.ubuntu.com, as a previous poster suggested takes care of the error message.

However, Can some one assure us that ububtu has not been compromised?

In the mean time It might be wise not to do ANY updates.....

PS I notice there are a few threads on this subject, maybe they could be merged.

---

### Post by public_void on 2005-11-11
Same here. Can't remember when it started.

---

### Post by Jussi Kukkonen on 2005-11-14
There are at least four bugs on this subject in bugzilla.ubuntu.com, all resolved with NOTABUG. 
I agree with towsonu2003 though, this is a serious security issue even if it's a repository problem and not a software bug -- Telling people that GPG errors are normal and they should just keep doing what they used to, makes the whole idea of GPG signing moot...

---

### Post by neohunt on 2005-11-14
I have exactly the same problem

W: GPG error: [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Bye!!

---

### Post by towsonu2003 on 2005-11-14
maybe a ubuntu person (?) could reply to this to describe what's going on and why this happens from time to time? just saying...

is reply #6 at [http://www.ubuntuforums.org/showthread.php?t=87123](http://www.ubuntuforums.org/showthread.php?t=87123) the answer we are looking for?

---

### Post by aysiu on 2005-11-14
If you're experiencing GPG errors, you have the wrong repositories. See the first link in my sig.

---

### Post by dog.breath on 2005-11-16
Here's what worked for me:

[LIST]
[*]Used [source-o-matic]("http://www.ubuntulinux.nl/source-o-matic") to generate my */etc/apt/sources.list* text
[*]Created a backup of *sources.list* and touched a new one: *sudo cp sources.list sources.list.0; sudo touch sources.list*
[*]Pasted the output from source-o-matic into my new *sources.list* file
[*]Ran *sudo apt-get update*
[/LIST]

---

