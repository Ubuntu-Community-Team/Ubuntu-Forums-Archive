---
title: "Road map for Server"
date: 2006-03-27
forum: Server Platforms
---

### Post by Ongolian on 2006-03-27
I am new to Ubuntu. we are finalising a OS for a server platform to port our applications.  How does Dapper compare with open SUSE or Centos as a Server OS? I read that SUSE is rated as Carrer grade OS and Large corporations moved over to RHEL (Centos). 
Is there a road map to incorporate those enterprise features into Dapper?

---

### Post by Ongolian on 2006-04-02
[QUOTE=Ongolian]I am new to Ubuntu. we are finalising a OS for a server platform to port our applications.  How does Dapper compare with open SUSE or Centos as a Server OS? I read that SUSE is rated as Carrer grade OS and Large corporations moved over to RHEL (Centos). 
Is there a road map to incorporate those enterprise features into Dapper?[/QUOTE]
It is so many days that I have posted this request. 
No one in Ubuntu community advised me on advantages of Ubuntu server. 

It is surprising and discouraging. 

Will any one let me know in which forum  should post this to get a reply???:confused:

---

### Post by gmclachl on 2006-04-02
You may want to have a look at the Ubuntu-Server project and perhaps address your questions to a couple of the dev's on that team. 

 George

---

### Post by gymsmoke on 2006-04-03
Ongolian~
I currently run a CentOS server with SELinux, apache, ftp, ssh, mysql, qmail/vpop, web sites, and a few small corporate apps (custom built).  I am currently testing Ubuntu server (5.10) as an alternative, since my workstation has been successfully moved form M$ to Linux.  So far, I'm impressed! The entire install of the OS, dns, mail (postfix this time... much better performance than qmail), mysql, phpmyadmin, apache, ftp, ssh took less than 4 hours from scratch.  I'm going through some app testing at the moment, but I'd be more than happy to share my experiences as we go.  As somewhat of a novice sysadmin, CentOS cost our company alot in expense to have someone else do all of the setup and config (which still wasn't done entirely the way we wanted).  I went through the install on Ubuntu server, and it's running strong so far. and the only thing it cost me was about a solid week of research/reading and hanging out here in the community...

---

### Post by Ongolian on 2006-04-03
Gymsmoke!

Thanks. I do not mind spending a week to learn if it makes me handle the server on my own. I am waiting for your feedback.

Thanks again:)

---

### Post by jinacio on 2006-04-03
I believe that for the most part, standard apps for a server install (www, email, database, etc...) are really easy to get up and running, and generally there isn't much tweaking involved.

And ofcourse, many howto's arround (for things like getting SSL in apache2) also apply to ubuntu.

By the way, i really hope the official ubuntu [server guide]("http://ubuntuforums.org/showthread.php?t=127112") gets some love before the dapper release...

---

### Post by gymsmoke on 2006-04-04
jinacio~
great.  I need to setup postfix so that it securely performs smtp-forwarding.  Could you tell us how that is accomplished?

---

### Post by jimwillsher on 2006-04-05
You might want to check out the howto at:

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

This is what I have followed, though I've used vsftp instead of proftp. I've subsequently documented the entire process (tweaked to my needs) and can setup an identical config in around 2 hours now.

It's an excellent howto.


Jim

---

