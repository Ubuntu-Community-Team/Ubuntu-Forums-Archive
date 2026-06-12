---
title: "Ubuntu or Red Hat Enterprise"
date: 2005-09-06
forum: Server Platforms
---

### Post by locque on 2005-09-06
I am building a new server for my private business. We only have ~10 users but need a good file, mail, web, database server for our company. I wanted to get any opinions about Ubuntu as such a server. I am using at my house for my development server with Apache MySQL and PHP, but how does it rank as a server for use in my small business environment? I was considering Red Hat simply because they have made that their main focus as of lately... Any ideas???

---

### Post by KingBahamut on 2005-09-06
Ubuntu. 

I ran a Fedora box for a long time, but then switch to Ubuntu, and while it took me awhile to get used to Apache2, once I did I was very happy.

---

### Post by lao_V on 2005-09-08
sudo apt-get upgrade has broken my linux-kernel a few times now so I'm a bit hesitant to use it in production.

---

### Post by deuce868 on 2005-09-08
I agree that while I love Ubuntu on my laptop/deskop with several important server packages basically in a "no promises" mode with the universe repository it's very hard to recommend as a server os. I would definitely say though to check out Debian stable instead of RH. I use debian on my servers and because of it a lot of my experience on the desktop translates since they share a lot of details.

---

### Post by relix42 on 2005-09-08
[QUOTE=locque]I am building a new server for my private business. We only have ~10 users but need a good file, mail, web, database server for our company. I wanted to get any opinions about Ubuntu as such a server. I am using at my house for my development server with Apache MySQL and PHP, but how does it rank as a server for use in my small business environment? I was considering Red Hat simply because they have made that their main focus as of lately... Any ideas???[/QUOTE]

You need to consider what you as an administrator are comfortable with.  Each of the distributions has their strengths and weaknesses - as do administrators.

I run RH boxes and Debian boxes in production server environments without problem.  I use Ubuntu as the Dev/Test boxes.  There are problems that plague each one.  RH has a tendency to release some things before their time.  Debian is behind the curve as far as new releases of some software (as follows their philosophy).  Ubuntu, as a mix of Debian and Ubuntu, poses some problems on certain situations.

So, pick your poision (Not quite perfect but later versions, much more stable with some bells and whistles you may want, or a bit of both).  

Also, unless your usage is rather heavy or specific, you may not fund much of a difference between any of the above.

So, make your first pick based on your comfort level as an administrator.

---

### Post by drogoh on 2005-09-10
[QUOTE=locque]I am building a new server for my private business. We only have ~10 users but need a good file, mail, web, database server for our company. I wanted to get any opinions about Ubuntu as such a server. I am using at my house for my development server with Apache MySQL and PHP, but how does it rank as a server for use in my small business environment? I was considering Red Hat simply because they have made that their main focus as of lately... Any ideas???[/QUOTE]


Unless you've got money to burn, shy away from RHEL; it's only good if you need the paid support.  If you absolutely want to use an RPM based distro, go with CentOS.  You may also want to look into FreeBSD but BSD is a different animal from Linux (and is quite suited for a server out of the box (look at Yahoo :p)) but it's all down to you and what you're most comfortable with.  Personally, I've always been a fan of FreeBSD because of its massive ports collection and not being bolted to a single version of Apache, PHP, MySQL, etc. without compiling your own and having stray files everywhere, but we can only show you the available paths, you must choose which one to take.

---

### Post by amohanty on 2005-09-10
> Unless you've got money to burn, shy away from RHEL; it's only good if you need the paid support.  

I second that. Managed 10 servers with RHEL, some packages are released before time, but without paid support its not worth it. If you want some really stable server stuff I have had good experience with Intel Solaris (dunno what the status is right now). In general I have had quite a decent experience with RH9, Suse and Ubuntu server install, so take your pick. After all thats what FOSS is all about.

AM

---

