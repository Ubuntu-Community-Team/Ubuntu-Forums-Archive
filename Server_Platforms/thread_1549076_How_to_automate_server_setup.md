---
title: "How to automate server setup"
date: 2010-08-09
forum: Server Platforms
---

### Post by allspiritseve on 2010-08-09
Hello all,

I reinstall Ubuntu twice a year after each release. Every time I do, I have to spend a good amount of time setting up my system the way I had it before, especially my LAMP stack for web development. 

Additionally, I would like to move from using shared hosting for my clients to using a VPS, but this involved a lot of repetitive work getting everything set up right.

I'm wondering if there is any information available on how to automate setting up a server?

For example: the default Ubuntu desktop with LAMP installed will not send email. I have to hunt down the right documentation every 6 months to figure out how to get this working. Yes, I could just bookmark the solution I find, but I'm looking for a way to take me out of the picture altogether.

Any ideas?

---

### Post by Bachstelze on 2010-08-09
I don't think there's a good way to do what you want.  You could just archive /etc, but your old config files might not work with the newer versions of all software.

Why for heaven's sake do you reinstall every 6 months anyway? Especially on a server...

---

### Post by Joe of loath on 2010-08-09
Just out of interest, why does your server need to be updated so regularly? Most servers seem to be installed with something stable (CentOS, Debian), and left for years before updating.

---

### Post by allspiritseve on 2010-08-09
Just to clarify: I'm using Ubuntu Desktop on my laptop, running a LAMP stack for development. It's not 'only' a server and I like to keep the latest version of Ubuntu running on it. I've not had much luck with upgrades, so I prefer to start over from scratch every 6 months.

---

### Post by Bachstelze on 2010-08-09
> **allspiritseve said:**
> Just to clarify: I'm using Ubuntu Desktop on my laptop, running a LAMP stack for development. It's not 'only' a server and I like to keep the latest version of Ubuntu running on it. I've not had much luck with upgrades, so I prefer to start over from scratch every 6 months.

That's one case where it would make sense to use XAMPP (or whatever the hell it's called) instead of the LAMP packages from the repos.  You have all your config files in the same place, and you don't have to worry about version incompatibilities since you would just install the same XAMPP version again.

Basicaly, keep your LAMP installation separate from your Ubuntu installation, so that you can upgrade one independently from the other. You coud even have a separate /opt partition, that would eliminate the need to reinstall XAMPP altogether.

[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by rubylaser on 2010-08-09
Well, the only way to do this would be to document the steps that it takes to setup your server properly, and then write a setup shell script to do the updates, install the necessary packages, setup passwords, and web directories as necessary.

I just document the procedure in and can copy / paste most of the info into a new system.  Frankly, I never re-install though.  I just do a dist-upgrade, and I'm ready to go.

---

### Post by CharlesA on 2010-08-09
> **rubylaser said:**
> Well, the only way to do this would be to document the steps that it takes to setup your server properly, and then write a setup shell script to do the updates, install the necessary packages, setup passwords, and web directories as necessary.

I just document the procedure in and can copy / paste most of the info into a new system.  Frankly, I never re-install though.  I just do a dist-upgrade, and I'm ready to go.

I do this. I've got a shell script that'll install the services I use, backups the original configuration files then copy the preconfigured ones over them. If anything doesn't work I compare the original config file and the old one and see what is different.

---

### Post by oldfred on 2010-08-09
When I converted to Karmic I went from 32bit to 64 bit so I knew I had to do a full install. I planned on converting my portable to Karmic and wanted it to be like my desktop. I was also planning to install Lucid alpha or beta soon so I wanted a standard way to update.

I tried to do as much from command line as I could. I then copied history to a bash file and cleaned it up from my typos and removed sudos. Since then I have continued to update and now have two updates. One sets up my /data and links in home. Another updates system &  installs all my apps.

---

