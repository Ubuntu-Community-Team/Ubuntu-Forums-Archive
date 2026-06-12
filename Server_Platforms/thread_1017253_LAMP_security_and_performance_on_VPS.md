---
title: "LAMP security and performance on VPS"
date: 2008-12-20
forum: Server Platforms
---

### Post by Eagleon on 2008-12-20
Hi everyone,

One of my clients are planning on deploying a PHP project that I am currently building for them. Since they have a low budget, they want me to set up the system on a VPS server they have rented. Of course, I am choosing ubuntu server as the distro of choice, but here is the thing.... although I have set up ubuntu servers in the past for personal use on many occasions and secured them, I have never done it before for an actual site that would be online. I was hoping I could get a little guidance from the gurus on this forum. I have several questions, and I would really appreciate the help:

1) Security

2) Performance

Do you have any advise or good reference material you can guide me to in regards to the two topics mentioned above? 

3) Cost

If a professional charged my client to set this up, how much would it cost?

4) Maintenance and Administration

The primary application will be a dynamic PHP site running on MYSLQ. Any advice on tools I could use to maintain and administrate the server? Other than ssh I mean... 

5) Automated Backups 

What is the best solution for automated, timed backups for MYSQL? I was thinking of writing a custom dump script and running a cron job on it to upload to a mirror, but if there is a better solution out there, it would be nice to know. 

I think that is it, but if you have any other suggestions I'd really appreciate it. Thanks a lot!

EDIT: Actually, I have one more question... how about pointing the domain to DNS? I know how to do this, but are there any security and/or other things I should be aware of? If you know a standard guide to set this up, please let me know. Thanks.

EDIT: Also, wanted to mention... I am looking for information that I need to know that may not be found here: [https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html)

---

### Post by windependence on 2008-12-21
> **Eagleon said:**
> Hi everyone,

One of my clients are planning on deploying a PHP project that I am currently building for them. Since they have a low budget, they want me to set up the system on a VPS server they have rented. Of course, I am choosing ubuntu server as the distro of choice, but here is the thing.... although I have set up ubuntu servers in the past for personal use on many occasions and secured them, I have never done it before for an actual site that would be online. I was hoping I could get a little guidance from the gurus on this forum. I have several questions, and I would really appreciate the help:

1) Security

I would use OpenBSD, just MHO

> **Eagleon said:**
> 2) Performance

Again, OpenBSD or FreeBSD or if you are stuck on Ubuntu, use another file system such as ZFS.

> **Eagleon said:**
> Do you have any advise or good reference material you can guide me to in regards to the two topics mentioned above? 

Book - Absolute BSD or ask on the forum at [www.daemonforums.org]("http://www.daemonforums.org")

> **Eagleon said:**
> 3) Cost

If a professional charged my client to set this up, how much would it cost?

This is what I do for a living. I charge $95 an hour. I am cheap for my area though (Phoenix) most charge $125.

> **Eagleon said:**
> 4) Maintenance and Administration

The primary application will be a dynamic PHP site running on MYSLQ. Any advice on tools I could use to maintain and administrate the server? Other than ssh I mean... 

phpMyadmin

[MySQL GUI Tools Bundle for 5.0]("http://dev.mysql.com/downloads/gui-tools/5.0.html")

Webmin or eBox

I would highly recommend if you are going to do this professionally, you learn the CLI. You WILL need it at some point.

> **Eagleon said:**
> 5) Automated Backups 

What is the best solution for automated, timed backups for MYSQL? I was thinking of writing a custom dump script and running a cron job on it to upload to a mirror, but if there is a better solution out there, it would be nice to know. 

I think that is it, but if you have any other suggestions I'd really appreciate it. Thanks a lot!

Amanda or Bacula

A simple rsync script would work here too and is a nice light solution. 
[http://sunsite.dk/info/guides/rsync/rsync-mirroring.html](http://sunsite.dk/info/guides/rsync/rsync-mirroring.html)

> **Eagleon said:**
> EDIT: Actually, I have one more question... how about pointing the domain to DNS? I know how to do this, but are there any security and/or other things I should be aware of? If you know a standard guide to set this up, please let me know. Thanks.

Just use your registrar's DNS control panel to create your 'A' record and 'Cname' records. You do NOT have to set up your own DNS server, use theirs.

> **Eagleon said:**
> EDIT: Also, wanted to mention... I am looking for information that I need to know that may not be found here: [https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html)

I do this stuff everyday for a living and their are many many free tools out there for you to use. I know some people won't like my advocating *BSD here but as far as security and performance goes, it's hard to beat and been around since the 60s. It's also rock solid.

You need to remember that if you are doing this professionally, you don't have time to learn on a customer's machine. They want it up all the time and if it goes down, you better know some CLI or you're pretty much screwed. Set yourself up a small lab using some really old hardware. If you don't have any, I'll send you some if you cover shipping. Set up a real network and a few nodes on it and if you can get a static IP from your ISP, set yourself up a real web server to play with. That way you can test your stuff before you go out to the client so you don't look stupid :)

-Tim

---

### Post by Eagleon on 2008-12-22
Hi Windependance,

Thank you for the advice. I do know CLI fortunately, but will certainly use this advice. 

Thanks

---

### Post by vpsville on 2008-12-23
> **Eagleon said:**
> 
1) Security
2) Performance
3) Cost
4) Maintenance and Administration

The primary application will be a dynamic PHP site running on MYSLQ. Any advice on tools I could use to maintain and administrate the server? Other than ssh I mean... 

5) Automated Backups 


First of all, as someone who has wasted many hours patching and administering a lot of BSD servers in the past, I'd have to say Ubuntu is a good server distribution choice but Debian is better (IMHO).  They are almost identical though, with Ubuntu being a bit less conservative.

1 - Install a firewall and disable unneeded services.  Ubuntu doesn't have any specific security issues very often, but the software you're running will.  Look at resources for securing Apache and PHP.  Run apt-get update and apt-get upgrade frequently.  99.9% of security problems you will run into on a website are with the PHP code your client writes/purchases/installs, not the binaries you're running.

2 - If you have a performance problem, look into this.  Otherwise defaults will be fine for now.  Worry about this last and after you have relevant usage data.

3 - The VPS provider will likely have a LAMP template ready to go, just install that. 

4 - Ubuntu/Debian is a breeze to maintain, apt-get update && apt-get upgrade.  Sometimes the Ubuntu packages are a bit ambitious and break things (which is why I suggested Debian for production use) but its rare nowadays.  

5 - Rsync to another VPS is a cheap solution.  Try rsyncpalace.com for some ideas.

---

