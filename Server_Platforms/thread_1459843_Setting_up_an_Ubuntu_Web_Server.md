---
title: "Setting up an Ubuntu Web Server"
date: 2010-04-22
forum: Server Platforms
---

### Post by mariolopezjr on 2010-04-22
Hi, I wanted to dabble with Ubuntu server. I am under the impression that Ubuntu Server should be less susceptible to web attacks than Windows Server 2008 R2 so I am thinking of possibly using Ubuntu Server instead, even though I already have Windows Server 2008 R2.

I was wondering if Ubuntu Linux can satisfy the various needs I require out of a server:

Share access:
[LIST]
Standard shares, ie a share with all my music, another with photos, one for backups, etc. Needs read/write access.
[/LIST]
[LIST]
A CD/DVD share, where I can mount CDs/DVDs/BDs in order to access from my machines.
[/LIST]
An ADUC like tool (Active Directory).
Web server (I know I can do it on Ubuntu)
Setting up RAID 5.


I cannot remember more than that at the moment. This is also a request for information. I have a simplified guide for setting up a web server in Ubuntu, but maybe a guide for more advanced users would be nice. I am familiar with Ubuntu and Linux in general, so the command line doesn't scare me.

If someone can point me to guides for the above things, I would be eternally grateful. For your information, I will be using Ubuntu Server 8.04 LTS and will upgrade to 10.04 LTS when it is release.

Thank you for your time,

Mario Lopez

---

### Post by qixil on 2010-04-22
The obvious route would be to use Apache.

Here you'll be messing with conf files - unless you install something like Webmin. Not much call for the command line (shell). Although there's prolly a much better way.

IMO RAID5 should be done in hardware - be it Windows or Linux.

Just some initial thoughts from a non-hardcore Ubuntu guy.

---

### Post by mariolopezjr on 2010-04-22
> **qixil said:**
> The obvious route would be to use Apache.

Here you'll be messing with conf files - unless you install something like Webmin. Not much call for the command line (shell). Although there's prolly a much better way.

IMO RAID5 should be done in hardware - be it Windows or Linux.

Just some initial thoughts from a non-hardcore Ubuntu guy.
Thanks for the thoughts, I'll definitely look into it. Though fakeRAID is said to not be as good as software RAID. And I definitely cannot afford a real RAID card.

Anybody else can offer some help? I have been tinkering around, but until I finish my build I cannot for sure do anything, so I am testing in a virtual machine.

---

### Post by arrrghhh on 2010-04-22
If you're doing RAID5 as I understand it you're going to want a RAID card.  They're not extremely expensive, unless your needs are great.

Trust me, you don't want to do software RAID or fakeRAID.

After reading your requirements in the first post, everything you listed is possible - but you may run into issues with the ADUC like tool... not sure what that is, and I'm not sure what AD tools are available in Linux.  Samba4 is supposed to allow servers to act as domain controllers and a lot of other promising things, but it's been in development for quite some time and it may never arise with all of the amazing things they're planning on doing.

---

### Post by mariolopezjr on 2010-04-22
> **arrrghhh said:**
> If you're doing RAID5 as I understand it you're going to want a RAID card.  They're not extremely expensive, unless your needs are great.

Trust me, you don't want to do software RAID or fakeRAID.

After reading your requirements in the first post, everything you listed is possible - but you may run into issues with the ADUC like tool... not sure what that is, and I'm not sure what AD tools are available in Linux.  Samba4 is supposed to allow servers to act as domain controllers and a lot of other promising things, but it's been in development for quite some time and it may never arise with all of the amazing things they're planning on doing.
From what I have been researching, and I have been researching a lot, LDAP is kind of like ADUC. I'll have to read more documentation on it and see if I can massage it into something I like.

I understand it is all possible really, but I'm also looking for guides, tutorials, documentation, etc. I want to know and learn how to do this stuff, and I am reading documentation, but tutorials are nice to use to actually experience it, albeit in a virtual machine.

So, you have any opinions on that? I have found some web server tutorials, but they all seem way to over simplified. I don't want somebody telling me to do this and that and then giving a brief explanation, I want a technical tutorial that is on the verge of a documentation but still a bit better. Kind of like a Dummies book or something.

I am familiar with Ubuntu and Linux, but not with the server variant and some heavy Terminal stuff. :)

---

### Post by Vegan on 2010-04-22
First do not use a software RAID you are simply askling for trouble.

To setup a web server, its easy, from a fresh install of Linux

sudo tasksel LAMP

then edit the /etc/apache2 file to add vhosts if needed.

If only one site, use /var/www and change the permissions to 755 so that Apache can use it without problems.

---

### Post by mariolopezjr on 2010-04-22
> **Vegan said:**
> First do not use a software RAID you are simply askling for trouble.

To setup a web server, its easy, from a fresh install of Linux

sudo tasksel LAMP

then edit the /etc/apache2 file to add vhosts if needed.

If only one site, use /var/www and change the permissions to 755 so that Apache can use it without problems.
Yeah, it is going to be only one site. Is it recommended to do tasksel as opposed to installing it in the Ubuntu Server installation? I didn't read which is preferred in the Ubuntu docs.

Do you happen to have experience with Samba and have some tips to share?

---

### Post by arrrghhh on 2010-04-22
For LAMP, I prefer to do it from the initial install, and I would assume Ubuntu would recommend that as well.

For samba, the only way to manage it (by default) is with a conf file.  My preferred method is kinda lazy, but it works really well - install a package called "webmin" - it allows you to monitor and manage pretty much all aspects of your server.

As for detailed tuts... that's kinda hit-or-miss.  Obviously there's MAN pages, that would be the first place to start with any topic.

---

### Post by mariolopezjr on 2010-04-22
> **arrrghhh said:**
> For LAMP, I prefer to do it from the initial install, and I would assume Ubuntu would recommend that as well.

For samba, the only way to manage it (by default) is with a conf file.  My preferred method is kinda lazy, but it works really well - install a package called "webmin" - it allows you to monitor and manage pretty much all aspects of your server.

As for detailed tuts... that's kinda hit-or-miss.  Obviously there's MAN pages, that would be the first place to start with any topic.
You've been very helpful haha thanks. Would webmin be better than eBox?

---

### Post by arrrghhh on 2010-04-22
> **mariolopezjr said:**
> You've been very helpful haha thanks. Would webmin be better than eBox?

I've used webmin previously, and still do... but it seems they don't comply with how Ubuntu packages are built, and most will recommend eBox because it's in the repo's and apparently obey the rules as far as Ubuntu goes for packaging.

Some will tell you Webmin will screw up your system... I highly doubt it, and it's never happened to me.  I've only had good experience with Webmin.

---

### Post by Tommetje on 2010-04-29
I'm also planning on setting up an Ubuntu Linux webserver and have a few more questions about RAID.

First of all, I hear you speak about "fakeRAID", a term I'm not familiar with. I know software RAID, which is configurable from within the OS. Thus the OS handles the RAID-stuff. Hardware RAID uses a RAID-controller and how does fakeRAID work? I bought myself a HP DL380 server with a Smart Array 5i controller in it. This is hardware RAID, right?

Secondly, I have 6 SCSI disks in this HP server, all of them are 36.4 GB in size. How would I best configure these disks with RAID? I was thinking of using 2 disks in a RAID1 configuration for the root partition, the /usr partition etcetera and the other 4 disks in a RAID5 configuration with 1 hot spare for the /var and /home partition.

Any thought about how best to configure RAID with 6 SCSI disks (and feel free to elaborate on which parts of the file system to use different partitions for).

Tom

---

