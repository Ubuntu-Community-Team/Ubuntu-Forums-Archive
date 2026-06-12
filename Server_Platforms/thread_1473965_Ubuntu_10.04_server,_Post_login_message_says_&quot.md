---
title: "Ubuntu 10.04 server, Post login message says &quot;133 packages can be updated&quot; - not!"
date: 2010-05-05
forum: Server Platforms
---

### Post by boondocks on 2010-05-05
With:
```
sudo  apt-get  clean  ; sudo  apt-get update ; sudo apt-get upgrade
```
I get:
> Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Looks good, so I log out.
When I log back in:
> Linux this_Ubuntu_10_04_server 2.6.32-22-server #33-Ubuntu SMP Wed Apr 28 14:34:48 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04 LTS

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)


For documentation and useful resources, please visit:
 * [http://ubuntu.com/server/doc](http://ubuntu.com/server/doc)

  System information as of Mon Apr  5 02:41:26 PDT 2010

  System load:  0.05               Swap usage:  0%     Users logged in: 0
  Usage of /:   0.7% of 144.26GB   Temperature: 62 C
  Memory usage: 6%                 Processes:   107

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

[COLOR="Blue"]133 packages can be updated.[/COLOR]
0 updates are security updates.

Checking for a new ubuntu release
No new release found
Last login: Wed May  5 05:15:31 2010 from ....
Ok, I so do:
```
sudo  apt-get  clean  ; sudo  apt-get update ; sudo apt-get upgrade
```
and I get the same results:
> ...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
...

Everytime, I login to this Ubuntu 10.04 LTS server it indicates that:
> ...
[COLOR="Blue"]133 packages can be updated.[/COLOR]
0 updates are security updates.

Checking for a new ubuntu release
No new release found

Yes, occasionally a few packages do get updated but this "[COLOR="Blue"]133 packages can be updated[/COLOR]" does not go away.
What is going on?

---

### Post by MartijnNL on 2011-04-25
I have this same issue (only a different number). It seems the numbers are set once (the updates available after installation) and then no longer updated.

Very annoying. Any solution for this?

---

### Post by KegHead on 2011-04-25
Hi!

Try:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

Advise.

KegHead

---

### Post by MartijnNL on 2011-04-25
Your last option tried to install a generic kernel, which I didn't do (as I'm running a server), but the other options didn't update anything.

I still get:

31 packages can be updated.
17 updates are security updates.

After a new login. Which were the updates I had available when I installed the server last Saturday. They installed fine at that point, but the counts aren't updated anymore.

---

### Post by mp3foley on 2011-04-25
Thanks for posting about this, I was having the same problem.

On my 10.04 server I found that /etc/motd.tail had a copy of the system status with incorrect package update numbers.  It was then I also noticed I was getting double status updates in my motd message.  Cleaning out /etc/motd.tail solved my problem.  After doing this you have to wait about 10 minutes for a cron job to update /etc/motd (which is linked to /var/run/motd).

According to docs I can find (try "man motd" and "man motd.tail") /etc/motd.tail is for static information you want to add to the bottom of the system generated motd.  Looks like a bug that the package numbers and other text got written to it.  Actually, yes it is and has bug file for it, [#659738]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/659738").  May not be the exact bug, but seems to be something like it.

Hope this helps you out as well.

---

### Post by MartijnNL on 2011-04-28
Yep, this solved my issue. Thanks.

---

### Post by eric_1982 on 2011-05-13
Cleaning out the /etc/motd.tail file and doing a quick reboot resolved the issue for me as well. Thank you!

---

