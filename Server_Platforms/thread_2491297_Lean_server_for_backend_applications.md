---
title: "Lean server for backend applications?"
date: 2023-10-03
forum: Server Platforms
---

### Post by monkey-learns-linux on 2023-10-03
[COLOR=#232629][FONT=-apple-system]I am new to Linux. I want to set up the** leanest possible Ubuntu LTS server **but one that is just as secure as the bulky versions. 
Why LTS? In my understanding LTS is better than others. Correct me if I am wrong.
I came across flavors like minimal Ubuntu, Ubuntu server & Alpine but I don't know how to proceed. In my understanding ubuntu server just lacks a GUI but is there a way to make it even more leaner by deleting some things that will not be useful in a backend server running Node/Java & relational db like MySQL?

TLDR: How to set up a secure networking capable Ubuntu LTS server that can run JavaScript, Java & MySQL without having even one extra line of code than it truly needs.[/FONT][/COLOR]

---

### Post by monkey-learns-linux on 2023-10-03
How can I make "ubuntu server" LTS version even leaner such that it is specific for backend apps like Java JavaScrpt & relational DB like MySQL? Just point me in the direction of knowledge.

---

### Post by grahammechanical on 2023-10-03
> [COLOR=#232629][FONT=-apple-system]Why LTS? In my understanding LTS is better than others.[/FONT][/COLOR]

I would not sat that. LTS = Long Term Support. With LTS we get 5 years support which can be extended for an additional 5 years the Extended Security Maintenance (ESM) which comes with sonething called Ubuntu Pro.

[https://ubuntu.com/pro](https://ubuntu.com/pro)

Ubuntu LTS releases come out every two years in the April. So, 20.04 LTS (April 2020); 22.04 LTS (April 2022). The next Ubuntu LTS will be 24.04 LTS (April 2024).

The Ubuntu releases that come out every six months in between those dates are only supported for nine months. I would not describe them as of lesser quality than an LTS release. Or, less stable. These standard support releases come with update drivers and upgraded applications. Over the life support time (5 years) of an LTS release it also is upgraded to the latest set of Linux drivers (called Linux firmware). We call these upgrades point releases. Right now I am running Ubuntu Desktop 20.04.6 which reaches end of support life in April 2025. I have signed up for Ubuntu Pro so I will get an additional 5 years support for 20.04. It is free for up to 5 machines. 

Oh, by the way, I do not think that Alpine Linux is classed as a flavour of Ubuntu even though it may be based upon Ubuntu code.

Regards

---

### Post by TheFu on 2023-10-03
> **monkey-learns-linux said:**
> How can I make "ubuntu server" LTS version even leaner such that it is specific for backend apps like Java JavaScrpt & relational DB like MySQL? Just point me in the direction of knowledge.

If you want a light server, there are better distros, like alpine [https://www.alpinelinux.org/](https://www.alpinelinux.org/) which is well under 50MB, not 2GB.  Pick the right tool for the right job.  Alpine comes with nothing extra. You have to install what you want/need.

---

### Post by MAFoElffen on 2023-10-03
<<duplicate thread to: https://ubuntuforums.org/showthread.php?t=2491297>>
As in nothing extra... Alpine is stripped of many of what I would consider basic Linux Utilities. I install what I need, when I need it.

In his other thread with the same title in the "New To Ubuntu Section", you say you are a new user to Linux and are asking for recommendations on a what to do there also... 
[QUOTE=monkey-learns-linux][COLOR=#232629][FONT=-apple-system]I am new to Linux. I want to set up the** leanest possible Ubuntu LTS server **but one that is just as secure as the bulky versions. 
Why LTS? In my understanding LTS is better than others. Correct me if I am wrong.
I came across flavors like minimal Ubuntu, Ubuntu server & Alpine  but I don't know how to proceed. In my understanding ubuntu server just  lacks a GUI but is there a way to make it even more leaner by deleting  some things that will not be useful in a backend server running  Node/Java & relational db like MySQL?

TLDR: How to set up a secure networking capable Ubuntu LTS server that  can run JavaScript, Java & MySQL without having even one extra line  of code than it truly needs.[/FONT][/COLOR][/QUOTE]
I do not think you have the knowledge or experience to choose Alpine and make it a success. I would recommend Ubuntu Server, installed as minimal.

---

### Post by MAFoElffen on 2023-10-03
<<>duplicate thread of: https://ubuntuforums.org/showthread.php?t=2491299>

---

### Post by TheFu on 2023-10-03
> **MAFoElffen said:**
>  
I do not think you have the knowledge or expereince to choose Alpine and make it a success. I would recommend Ubuntu Server, installed as minimal.

Ah.  If someone doesn't have a few years of Server experience, then alpine would be a challenge.  But desire and passion can make up for all sorts of deficiencies.
The learning curve on Ubuntu Server is steep enough for someone without at least a year experience at a terminal.  

There's a reason many of us here use Ubuntu Server - it tends to have slightly newer, but stable packages compared to Debian Stable.  There are many nice packages installed to make life comfortable and it still provides the customization we need/want in a server.  There are a few things in Ubuntu Server that I don't want installed too, so I remove them.  What to remove is a matter of taste.  

If you remove too much, and break the system, you'll learn a bunch, so be certain you have snapshots or backups or better, both before heading that direction.  If you don't have the skills do accomplish those things ... back up and learn those first.  Then you can worry about removing packages and looking for negative impacts.

My leanest ubuntu server 
```
$ df -h
Filesystem                  Size  Used Avail Use% Mounted on
lxd/containers/back18        30G  531M   30G   2% /
```
So it is using 531MB of storage. That's an LXC container.  LXC containers aren't a sparse as a Docker container. They have a different philosophy and use more storage.  But once you care that much, it is time to move to something like alpine, IMHO.

A stock Ubuntu 22.04 server, with snapd removed:
```
$ df -h
Filesystem                Size  Used Avail Use% Mounted on
/dev/mapper/vg--00-lv--0  9.8G  4.5G  4.8G  49% /
/dev/vda2                 739M  400M  286M  59% /boot

```
seems to use 5G of storage.

So, if you want lean, use containers, not full installs.

---

### Post by oldfred on 2023-10-03
Threads merged since reply in both threads.

Do not post duplicate threads. We all are volunteers and need to know what has already been suggested.

---

### Post by monkey-learns-linux on 2023-10-04
> **TheFu said:**
> If you want a light server, there are better distros, like alpine [https://www.alpinelinux.org/](https://www.alpinelinux.org/) which is well under 50MB, not 2GB.  Pick the right tool for the right job.  Alpine comes with nothing extra. You have to install what you want/need.

Is alpine linux less secure than "ubuntu server LTS" ? Will it have networking & backend applications capabilities? How can I learn about this? I dont even know how to go about learning this.

> **MAFoElffen said:**
> <<duplicate thread to: https://ubuntuforums.org/showthread.php?t=2491297>>
As in nothing extra... Alpine is stripped of many of what I would consider basic Linux Utilities. I install what I need, when I need it.

In his other thread with the same title in the "New To Ubuntu Section", you say you are a new user to Linux and are asking for recommendations on a what to do there also... 
QUOTE=monkey-learns-linux;14159831][COLOR=#232629][FONT=-apple-system]I am new to Linux. I want to set up the** leanest possible Ubuntu LTS server **but one that is just as secure as the bulky versions. 
Why LTS? In my understanding LTS is better than others. Correct me if I am wrong.
I came across flavors like minimal Ubuntu, Ubuntu server & Alpine  but I don't know how to proceed. In my understanding ubuntu server just  lacks a GUI but is there a way to make it even more leaner by deleting  some things that will not be useful in a backend server running  Node/Java & relational db like MySQL?

TLDR: How to set up a secure networking capable Ubuntu LTS server that  can run JavaScript, Java & MySQL without having even one extra line  of code than it truly needs.[/FONT][/COLOR]
I do not think you have the knowledge or expereince to choose Alpine and make it a success. I would recommend Ubuntu Server, installed as minimal.[/QUOTE]

I dont think I have the experience to make alpine a success either because like you assumed correctly, i dont know what I am doing. However, I want to know. So how can I know? Is there a way to cut Ubuntu server beyond minimal so that its specific for backend applications and relational db?

> **TheFu said:**
> Ah.  If someone doesn't have a few years of Server experience, then alpine would be a challenge.  But desire and passion can make up for all sorts of deficiencies.
The learning curve on Ubuntu Server is steep enough for someone without at least a year experience at a terminal.  

There's a reason many of us here use Ubuntu Server - it tends to have slightly newer, but stable packages compared to Debian Stable.  There are many nice packages installed to make life comfortable and it still provides the customization we need/want in a server.  There are a few things in Ubuntu Server that I don't want installed too, so I remove them.  What to remove is a matter of taste.  

If you remove too much, and break the system, you'll learn a bunch, so be certain you have snapshots or backups or better, both before heading that direction.  If you don't have the skills do accomplish those things ... back up and learn those first.  Then you can worry about removing packages and looking for negative impacts.

My leanest ubuntu server 
```
$ df -h
Filesystem                  Size  Used Avail Use% Mounted on
lxd/containers/back18        30G  531M   30G   2% /
```
So it is using 531MB of storage. That's an LXC container.  LXC containers aren't a sparse as a Docker container. They have a different philosophy and use more storage.  But once you care that much, it is time to move to something like alpine, IMHO.

A stock Ubuntu 22.04 server, with snapd removed:
```
$ df -h
Filesystem                Size  Used Avail Use% Mounted on
/dev/mapper/vg--00-lv--0  9.8G  4.5G  4.8G  49% /
/dev/vda2                 739M  400M  286M  59% /boot

```
seems to use 5G of storage.

So, if you want lean, use containers, not full installs.


Great reply. I think I want to start from alpine because it will help me understand the things I will install. Like building legos. My question is how can I learn about what comes in alpine linux in-depth? I am starting my journey with linuxfromscratch.org so that should help me understand linux to some extent. My question is what do I do after that? Because my end goal is to make the leanest possible _**secure **_server.

> **oldfred said:**
> Threads merged since reply in both threads.

Do not post duplicate threads. We all are volunteers and need to know what has already been suggested.

ok, i will not do that again. Thanks for merging it this time.

One thing that is stuck in my head is "will alpine linux be as secure as Ubuntu?" Because Ubuntu has a corporation behind it that maintains it, it seems to be that it may be more secure because of faster updates. Do Ubuntu and alpine linux have the same security packages? Can I install ubuntu packages on alpine linux? 

I do not wish to trade security for size.

---

### Post by ian-weisser on 2023-10-04
[FONT=arial]> **monkey-learns-linux said:**
> [COLOR=#232629]
I am new to Linux.
I want to set up the** leanest possible Ubuntu LTS server **but one that is just as secure as the bulky versions.
[/COLOR][COLOR=#232629]

Those are opposites.

If you are truly "new", then it is unlikely that you have the skills to accomplish a "leanest possible" install.
And if you are experienced enough to accomplish "leanest possible", then you already know how much work that requires.

[/COLOR]> **monkey-learns-linux said:**
> [COLOR=#232629]In my understanding LTS is better than others. Correct me if I am wrong.[/COLOR][COLOR=#232629]

Okay: You might be wrong. Keep an open mind. LTS and non-LTS each have different advantages and disadvantages. Neither is objectively "better" or "worse."

Many "new" folks wipe and reinstall, sometimes several times as they[/COLOR][COLOR=#232629] learn. Your first install is unlikely to be your last.

[/COLOR]> **monkey-learns-linux said:**
> [COLOR=#232629]TLDR: How to set up a secure networking capable Ubuntu LTS server that can run JavaScript, Java & MySQL without having even one extra line of code than it truly needs.[/COLOR]

It will take you several weeks, perhaps months, to learn the skills required. There is no single path for everybody.

General advice for new users: Make your install *successful* rather than *perfect*. Increment toward perfection as your skills improve. Re-evaluate what perfection should look like based upon your learning and experience.
[/FONT]

---

### Post by TheFu on 2023-10-04
About LTS - it is all about support periods.  If you spend a month setting a a server (and when you are new, it could be a year to setup, easily, then you don't want support to end without 3+ yrs of support still remaining.  

When I was new to Linux, I wanted to know everything too.  IT IS NOT POSSIBLE, so get that idea out of your mind.  I've been doing Unix/Linux since around 1993 and I guess I know 10%.  Things are always changing so answers usually have history behind them.  

If you want to learn Linux as a server + light developer, then start with the basics that end users need to know. [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) . Work through the first 12 chapters of that to get the basic understanding.  Around pg 250, things that seem disconnected should start to click together and you'll gain insights that just aren't possible memorizing commands.  That alone will take 6-12 weeks, depending on your commitment.  The goal is true knowledge, not finishing each chapter and all the exercises.  Only you can know if you truly understand users, groups, permissions.  Even after getting an "A" in a Unix course because I could memorize those things, the elegance of Unix permissions wasn't clear until I sat down and played with 3 different userids, mixing and matching groups, then seeing what every single possible permission did on the files AND on the directories.  I literally did this:
```
chmod 007 file
chmod 006 file
chmod 005 file
chmod 004 file
chmod 003 file
chmod 002 file
chmod 001 file
chmod 000 file

```and between each of those changes, saw what the owner, group member and outsider could see and do with the file. Then I moved onto 
```
chmod 100 file
chmod 200 file
chmod 300 file
....
chmod 777 file

```You need time to "sleep on it."  Lots of time as you learn more and add the new points of knowledge into your overall Unix understanding.
For example, 711 is very useful for programs and directories in ways not intuitively obvious, but not ok for interpreted scripts.

Also learn what is meant when people say that in Unix "everything is a file".

These things are base knowledge and feed into EVERYTHING ELSE on the system.

As for security, it is a process, not a program.  In general, the larger a program or set of installed programs are on any computer, the less secure it will be.  Alpine is small, so more secure than Ubuntu, but there are many assumptions around that statement - like "all other things being equal".  Any computing device can be non-secure, if the admin and users make foolish choices.  Out of the box, alpine is more secure because it has nothing enabled. If you want something to work beyond a minimal shell, then you'll need to set it up. OTOH, post install Ubuntu Server does lots of things, some over the internet. Is that more or less secure?  It certainly can be handy. That's also certain.

I've decided that Ubuntu Server is secure enough by my needs, with a few caveats.  Ask again in 3 yrs and we can chat deeply about that. That this point, you don't have the background and I don't have the time to type it all.

If you want to learn how to setup a Linux system, get comfortable with an Ubuntu desktop flavor suitable for your hardware.  Run that for 3 months. Everything you can do on a "server" is possible on desktops too.  Getting to the point faster is usually a good thing so people aren't overwhelmed with things that are nearly automatic on the desktop releases.  Do you really want to struggle with setting up network access via text config files that nobody except Canonical uses? Is that an efficient use of your time?

Next, install something that shows more of the details like Arch or Slackware.  Run one of those for 3 months.  

Then come back and load Ubuntu Server.  Run that for 3 months.  Or Debian. Your choice.  They are different, but not completely different.

Then decide if you might want to switch to a RHEL-based server or a SuSE-based server to get their take on it.  They come with SELinux installed, which can be a pain, but has lots of features not in Debian/Ubuntu.

For end-users, Linux is Linux is Linux.  Over 90% is the same.  It is the administrative aspects that are different, but the underlying system is the same.  Alpine, debian, ubuntu, rhel, SuSE, arch, gentoo ... are 90% the same.  They all get their kernels from kernel.org (that Linus runs).  Of course, kernel versions can matter greatly, depending on your hardware and specific uses.  For a while, ZFS didn't work with the v6.x kernel.  If you don't use ZFS, it doesn't matter, but if you do ... you'd either know this or be bitten.

Oh ... learn about volume managers and file systems sometime around 8 months of daily use.  Beginners aren't used to thinking that there are 10 popular, but different, file systems. If you don't know anything, choose ext4 on Debian/Ubuntu. Some other distros will push some other file systems, which is great.  Just beware that data loss can happen in some non-standard uses.

Did I mention backups?  You need those.

You may notice I didn't say much about being lean, since that's really low on the things someone new should worry about. There are bigger issues to solve.

---

### Post by MAFoElffen on 2023-10-04
TheFu had a lot of valuable things, that I would have said if given a change, that I wholly agree on. I'll add to that.

I've been testing for Ubuntu Server since 10.04... From the release versions, in Server Edition of Ubuntu, there is not as many major changes, like you have with the Desktop Edition. We had a few, such as Kernel, the move from Init to SystemD, the move to Netplan, the move from debian-installer to the live installer... to name a few. They were big changes, but not game changers like with Desktop Edition. From the interim releases to LTS releases, there are not usually major changes that you see right off on the surface, with each release. The main focus is on making it stable, secure and applying CVE's (security). This last is where you you say your focus is (security), in Ubuntu, that is just done. 

Most users of Server Edition, there is no reason for them to go with an interim release, because their focus is stability, support, and security. They are not looking for the latest and greatest (within reason). (Unless it supports new hardware.) Once they get their server setup and configured, those can be left static until another LTS release comes around that they can migrate to it.

I think it's time to mention about the building blocks... If you install via debootstrap using the sources.list of Ubuntu, that is 'Ubuntu Base'. If you want to learn 'lean', then i suggest you learn how to install using this method. That is Ubuntu, stripped down to it's minimum infrastructure base. I often will start out an install from this, onto the file manager/file system I have setup, and install what I need onto this. Warning: This is an advanced installation method, where you need to understand how things should work, and how the pieces should work together. 

If you go with the method of installing packages to get to the next step in a build; From there the steps up from that (in order) are 'ubuntu-server-minimal', the 'ubuntu-server'.

Within this post, are tidbits that should keep you busy for months; Googling, reading, learning how to do... All the while learning about Linux commands and how to use them, until you feel comfortable working in Console. There is a learning curve, that I feel is worth the time to learn. 

It's your decision on what you choose and what paths you take to get there. Sometimes "the best path" for the long-run, is not the fastest. It's your decision how you interpret what "the best path" means... You can get there in the same place in a few commands, but what you learn with that is not the same.

---

### Post by MAFoElffen on 2023-10-04
A plan, that will facilitate you getting there quicker, and learning faster, if you have only one computer... Is to install Ubuntu Desktop on your host, and install KVM as a virtual host system. 

That way you can learn to install Ubuntu Server VM's in a safe and friendly environment. You can connect to the machines from a graphical terminal, where you can cut-and-paste commands into, and see what they do.

When I am testing and evaluating VM's, I can allocate the resources it should have, on the target platform, then quickly see would it is doing from the Virt-manager console to see if it needs more resources. that way, you can evaluate what 'lean" means. and if what you do has effects on that.

I think, overall, that will force you to learn Linux, in a way that will speed up the learning curve... In an test (learning) environment. Long ago, I consolidated my 14 physical servers into one Physical Virtual Host... And use that same VM Host to test things that have problems, or should not work... To see if they can make them work if done a different way.

I think this is your best option to start out learning.

Once you decide on, and setup the foundation, then you can investigate and decide on the further: an SQL database, whether you want to go with TomCat Server for JAVA app's, etc. (I have a note on that below.)

I have to admit, I know JAVA, but have moved away from that in favor of just doing Python instead. JAVA is not the same it was about 10 years ago. Before that, JAVA had it's heyday, and was supposed to be the thing to do. With every version of JAVA, there then were security issues that had to be corrected in the next release layer, that couldn't just be applied, because there were things that were deprecated. So they required code changes just to keep them running. It became a very large maintenance consideration. Then JAVA demand itself fell from favor. It was not a hard decision. I even wrote a college course proposal, that included lectures and code examples, converting their existing "Object Oriented Programming" course from using JAVA to Python... I even included writing a their (sample) final project in Python. That was in early 2017. Curious in what you see differently on that nowadays?

---

