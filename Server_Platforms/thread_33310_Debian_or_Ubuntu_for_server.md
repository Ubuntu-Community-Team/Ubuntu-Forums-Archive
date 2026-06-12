---
title: "Debian or Ubuntu for server"
date: 2005-05-10
forum: Server Platforms
---

### Post by kbdcb on 2005-05-10
Hi,

I was wondering what distro to choose running BIND, postfix and MySQL? Is there a difference between debian and ubuntu in a server environment?

Cheers!

---

### Post by defkewl on 2005-05-10
I'd recommend Debian for server. But if you still insist on using Ubuntu for server then you need to turn off some services that is meant for desktop.

---

### Post by lt_kije on 2005-05-10
[QUOTE=defkewl]I'd recommend Debian for server. But if you still insist on using Ubuntu for server then you need to turn off some services that is meant for desktop.[/QUOTE]

Ubuntu has actually done quite well in my experience as a server install. Make sure to run the install disk as "server" and not the default ("desktop"). I've done two file/web server and router installs using Ubuntu and haven't had problems. Postfix works great; BIND I haven't tried; you shouldn't have any trouble with MySQL.

Good luck!

lt_kije

---

### Post by bazh on 2005-05-10
[QUOTE=defkewl]I'd recommend Debian for server. But if you still insist on using Ubuntu for server then you need to turn off some services that is meant for desktop.[/QUOTE]

what services are meant for the desktop when doing a 'server' install ?

---

### Post by kbdcb on 2005-05-10
Thanks for your answers.

I will then try ubuntu on my server sometime next week.

---

### Post by tncmmngs on 2005-05-10
I used the Ubuntu server install and have been quite happy with it (SSH, LAMP). I'm a little confused by the remark that there may be some unnecessary services running. I'd like to hear more details on this. Right after I installed, I PS'd and NETSTAT'd the system -- very clean (Postfix and another (I think) were running -- gurus, help me here). I read here that the Ubuntu Postfix config only listens to localhost (I haven't confirmed this yet).

I don't have any experience with Debian, but I did my homework on a secure server distribution. Ubuntu scored well for me.

Of course, I went through the [Ubuntu Guide Security](http://www.ubuntuguide.org/#security) suggestions, and implemented those that made sense. Also, added AIDE, LOGWATCH, and ROOTKITHUNTER. I still need to get IPTABLES up before I expose the server to the Internet.

As a Fedora/RedHat refugee, the SUDO takes a little getting used to. There is some discussion about whether the SUDO/disabled-root philosophy is a good security measure. I read through the pros and cons...it makes sense to me. Do the same and make up your own mind.

---

### Post by lathiat on 2005-05-11
[QUOTE=kbdcb]Thanks for your answers.

I will then try ubuntu on my server sometime next week.[/QUOTE]

None, I think the other user was not aware of the 'server' mode to the install.

---

### Post by jdonnell on 2005-05-11
Who is this server for? I.e. is it a live server, a development server, or a server your using at home. If it isn't live and supporting something mission critical or that makes money then I'd use ubuntu and I am for two development servers at my office.

---

### Post by kbdcb on 2005-05-12
[QUOTE=jdonnell]Who is this server for? I.e. is it a live server, a development server, or a server your using at home. If it isn't live and supporting something mission critical or that makes money then I'd use ubuntu and I am for two development servers at my office.[/QUOTE]

It will be stationed at a web hotel. I will use mostly for testing and development. Running BIND, MySQL and Postfix for my mail.

---

### Post by ubuntu_demon on 2005-05-12
[QUOTE=tncmmngs]I used the Ubuntu server install and have been quite happy with it (SSH, LAMP). I'm a little confused by the remark that there may be some unnecessary services running. I'd like to hear more details on this. Right after I installed, I PS'd and NETSTAT'd the system -- very clean (Postfix and another (I think) were running -- gurus, help me here). I read here that the Ubuntu Postfix config only listens to localhost (I haven't confirmed this yet).

[/QUOTE]

gnome comes with things like HAL which is useless for a server.

 if you just do a "server" install(type server at the bootprompt of the cd) you can manually select which packages to install using apt-get ... you won't get unnecessary stuff.

just install everything you need using apt-get (like postfix, openssh,mysql)

I recommend install XFCE if you need a GUI for your server.

I think these packages are enough to get a XFCE4 up :

sudo apt-get install xfce4 x-window-system-core xfwm4 xserver-xorg

try startxfce / startx to get it up
if there are any problems
try sudo dpkg-reconfigure xserver-xorg
or look at your /var/log/Xorg.0.log

---

### Post by LordHunter317 on 2005-05-12
[QUOTE=demon666_nl]gnome comes with things like HAL which is useless for a server.[/quote]HAL has uses on a server as well, or will in the near future at least.  Some portions of Project Utopia that are useful will want it.

---

### Post by ubuntu_demon on 2005-05-12
[QUOTE=LordHunter317]HAL has uses on a server as well, or will in the near future at least.  Some portions of Project Utopia that are useful will want it.[/QUOTE]
 please elaborate

---

### Post by jdonnell on 2005-05-12
[QUOTE=kbdcb]It will be stationed at a web hotel. I will use mostly for testing and development. Running BIND, MySQL and Postfix for my mail.[/QUOTE]

What is the live server running? I try to have the exact same setup for testing because you don't want a surprise problem when your trying to go live. However, I usually develop on a different setup then move to a test server then to the live server. Ubuntu is great for development, but I'd try to mirror the live server for testing. Depending on what you do this may just mean having the same mysql and php versions and config. If that's the case then ubuntu may work great for that as well.

---

### Post by tncmmngs on 2005-05-12
[QUOTE=demon666_nl]gnome comes with things like HAL which is useless for a server.

 if you just do a "server" install(type server at the bootprompt of the cd) you can manually select which packages to install using apt-get ... you won't get unnecessary stuff.

just install everything you need using apt-get (like postfix, openssh,mysql)

I recommend install XFCE if you need a GUI for your server.

I think these packages are enough to get a XFCE4 up :

sudo apt-get install xfce4 x-window-system-core xfwm4 xserver-xorg

try startxfce / startx to get it up
if there are any problems
try sudo dpkg-reconfigure xserver-xorg
or look at your /var/log/Xorg.0.log[/QUOTE]

I should have mentioned that I did use the server install.

---

### Post by WildTangent on 2005-05-12
[QUOTE=demon666_nl]

I recommend install XFCE if you need a GUI for your server.

I think these packages are enough to get a XFCE4 up :

sudo apt-get install xfce4 x-window-system-core xfwm4 xserver-xorg

try startxfce / startx to get it up
if there are any problems
try sudo dpkg-reconfigure xserver-xorg
or look at your /var/log/Xorg.0.log[/QUOTE]

apt told me it couldnt find xfce when i tried a server install on my test box the other night

-Wild

---

### Post by ubuntu_demon on 2005-05-13
I think the choice between debian and Ubuntu is simple :

1) choose Ubuntu (because it has newer packages)

2) If you need a very secure server and Ubuntu doesn't offer some service that you want to use in main repository choose debian. Otherwise still choose Ubuntu.

If you are running a production server or if you are paranoid about security ... all stuff such as : the webserver,programming languages that are used by the webserver, the database that is used .. all those things should be in main. For example if for some reason you need to be running apache 1 .. then debian is probably a more safe bet because in Ubuntu only apache 2 is in main.

---

### Post by nocturn on 2005-05-13
[QUOTE=demon666_nl]I think the choice between debian and Ubuntu is simple :

1) choose Ubuntu (because it has newer packages)

2) If you need a very secure server and Ubuntu doesn't offer some service that you want to use in main repository choose debian. Otherwise still choose Ubuntu.

If you are running a production server or if you are paranoid about security ... all stuff such as : the webserver,programming languages that are used by the webserver, the database that is used .. all those things should be in main. For example if for some reason you need to be running apache 1 .. then debian is probably a more safe bet because in Ubuntu only apache 2 is in main.[/QUOTE]

How would you go about suggesting packages for inclusion in main?
I want to run a Hoary server, but I user Kerberos (KDC and Kadmin).

Another question, for other packages in main (like Cyrus sasl), is there a way to find out with what options/support they were build?

---

### Post by ubuntu_demon on 2005-05-13
[QUOTE=nocturn]How would you go about suggesting packages for inclusion in main?
I want to run a Hoary server, but I user Kerberos (KDC and Kadmin).[/QUOTE]

I don't know the official request procedure to get something in main. But in order to move something to main it has to be already in universe and it has to have MOTU maintainers on it. Read about it here : [http://www.ubuntulinux.org/wiki/MOTU](http://www.ubuntulinux.org/wiki/MOTU) You can also make universe requests there.



[QUOTE=nocturn]
Another question, for other packages in main (like Cyrus sasl), is there a way to find out with what options/support they were build?[/QUOTE]


They might put something in /usr/share/doc if there is something special.

But you can also compile a package yourself. Just get the source package using apt-get / synaptic.

---

### Post by RicardapBR on 2005-05-13
Hi!
I installed Ubuntu for a webserver at my university.
But a problem insist to happen:
The files on the server can only be accessed for people inside this domain (mat.ufrgs.br) or by ip (143.54.*.*)

I've configured many settings on the server and don't know why people outside the university can't access the services of this server (SSH, FTP, HTTPD, ...)

Please Help!

---

