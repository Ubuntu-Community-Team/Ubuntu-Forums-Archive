---
title: "Recommended place to store and organize web app / virtual environment / ... files on"
date: 2022-08-30
forum: Ubuntu, Linux and OS Chat
---

### Post by abthory on 2022-08-30
Hello,

I have a Ubuntu VM with my web app, virtual environment, git files, etc...


I was storing my web app files under: 
/var/www/website

My virtual environment under: 
/usr/local/venvs/myvenv

My git bare repo under: 
/home/anthony/git/mybaregit

I am a bit OCD and also I felt like /var/ or /usr/ were only for storing Linux files, etc, not my personal folder (I am new at Unix-like system so I don't know). Thus I moved everything under my /home/anthony/:
```
anthony@server:~$ ls
website  git  venvs

```
Look pretty, looks clean. But how is it, security-wise? I feel like 1 mistake on my /home/anthony/ folder could be painful for the entire project, versus the previous storage way that was spread across multiple folders.


What do you think? 
Do people usually store project files, virtual environments, etc., outside or their home directory? 
Apparently /var/ is a good place. Would it be wiser to store everything in /var/ rather than /home/, as someone suggested that home is personal, and a website is supposed to be visited by strangers (but as it's a VM, I'm not sure it applied here). 
Also while looking at uWSGI doc, they talked about storing the virtual environment under /usr/, so I am a bit confused. 

Is there a convention that people usually follow when setting up their project on a Unix-like server?

Thank you very much for your opinion.

---

### Post by TheFu on 2022-09-02
"virtual environment" can mean many different things. Please explain your usage clearly.

There are file system hierarchy standards for Unix and Linux systems.  Follow those.  Google will find the document - I think 2015 is the current version. There's a wikipedia article too.

In general, things that are system-wide do not belong under a user's $HOME.  A website definitely does not.  Whether /var/ is a good place is completely debatable, since /var/ was for system files (like logs, caches), not data to be used off the system as DBMS and web apps do these days.  I fight that battle by adding separate LVs and mounting separate storage under /var/.... for the different, non-system, stuff.

I use /usr/local/ for system-wide stuff that needs to be shared with all users AND is built manually.  This is also were I place AppImages (/usr/local/appimages/).

If by virtual environments, you mean different versions of specific programming languages, then I keep those under my $HOME.  When it is time to deploy that specific web-app with that specific version of the language files and modules, I use a tool which is part of the language which places all the dependences into a deployment file, to make deployment to a different system easier.  My production systems don't have regular users on them.

But with most things on Unix, the admin is who sets the standards for systems and has to live with good and bad choices.  Over time, I've learned from mentors and my own mistakes mainly what NOT to do. OTOH, almost all my current systems have less than ideal setups, since I learn about the mistakes well after the deployment and just need to address it for the next deployment.

And sometimes little things aren't worth worrying about at all.  For example:
```
$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/vda1      ext4      7.1G  3.1G  3.7G  46% /
/dev/vda2      ext4      2.3G  974M  1.2G  46% /var/www

```
That's a web app server.  I was forced to create the 2nd mount when the first ran out of inodes.  That system has been upgraded and upgraded probably since 2008-ish.  Someday, I might fix it based on my current standard practices.  Actually, it will probably be moved into a linux container instead of being a full VM, so overhead will be lower and performance significantly higher.  We all learn from each mistake, right?

---

### Post by abthory on 2022-09-02
Thanks a lot for all those information. I guess I think too much and I just have to try and see sometimes. Many concepts will become clearer and obvious with time.

By virtual environment, yes, I talked about programming language. 

I read articles about the file system hierarchy but I was sill confused where to put my stuff because I felt like except the /home/ folder, everything is for the system. But I guess I just don't have enough grasp on Unix yet.

Thanks for your help

---

### Post by TheFu on 2022-09-03
There is nothing special about /home/ and home directories don't actually need to be placed there.  Inside enterprises, where user credentials are shared across multiple systems, it is common for a persons HOME to be provided over an NFS mount to some other location, say /u1/{username}.  This is so their thousands and thousands of users can be mounted only as needed to specific systems.

/home/ is typically for end-users who do not have any other accounts on any other systems. They are local-only, which is very odd.  It just isn't done, at least not in any of the 10 companies where I've worked over the decades.  The location for any specific HOME is part of the password entry.  That can be in /etc/passwd or LDAP or x.500 directories or NIS or NIS+.   For fun, create a new userid and place the HOME somewhere else.  See what works and what doesn't.  Some Canonical specific choices they are pushing the last few years break.

---

### Post by SeijiSensei on 2022-09-03
I have an account for websites that is independent of my home directory. All my sites live under /home/[username]/sites. Makes it easier to manage things like permissions.

---

### Post by abthory on 2022-09-05
I see, I guess it's more a matter of convention than rule. I thought there was like a very specific place where people MUST do things. Or at least highly recommended (I guess there is for other stuffs, like I don't think people would put a .service in a /usr/ directory (don't even know if that's possible, Linux probably wouldn't read it? Anyway.)). I think I will do like you SeijiSensei. I only need 1 sudo user account beside root, as it's a VM just for prodution.

Thank you

---

### Post by TheFu on 2022-09-05
> **abthory said:**
> I see, I guess it's more a matter of convention than rule. I thought there was like a very specific place where people MUST do things. Or at least highly recommended (I guess there is for other stuffs, like I don't think people would put a .service in a /usr/ directory (don't even know if that's possible, Linux probably wouldn't read it? Anyway.)). I think I will do like you SeijiSensei. I only need 1 sudo user account beside root, as it's a VM just for prodution.

Thank you

It is only a convention if everyone follows.  There are a number of things where Ubuntu distros do not follow the convention used by other distros.
I don't know what a .service file is, but systemd unit files can be put anywhere - the tools that use them just need to be told about the other location(s).  Systemd isn't Linux. It is an init program and is optional. There are multiple different init programs - systemd is the youngest and doesn't appear to follow the Unix Philosophy, so many people dislike it.  It is extremely tightly integrated into the boot process and hard to remove, unlike the other choices. I miss init scripts.  Later solutions, like systemd and upstart, fixed problems I've never had and just made the way a system starts more obtuse. Prone to error due to the added complexity.  Others might have different opinions.  init was elegant and simple.  Sigh.  OTOH, Fedora, Debian and a number of other popular distros also picked systemd, so Ubuntu following along isn't exactly going off into a far off land.  If I disliked it that much, I'd have switched distros by now.  Some people have.

---

### Post by abthory on 2022-09-05
Interesting, thank you for your opinion. I am really new to Unix-like OS so I really don't know much about it yet. I didn't know that there was such deep differences between distributions (Well, obviously there must be, otherwise there wouldn't be different distributions). I picked Ubuntu because it is often the one recommended to beginners and used in many tutorials. With time I will probably know better about these differences, but that's still really interesting to read.

---

