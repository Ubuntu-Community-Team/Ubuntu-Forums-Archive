---
title: "The answer to many telnetd questions.."
date: 2006-06-20
forum: Server Platforms
---

### Post by dhartnet on 2006-06-20
Someone answered it in another thread. I've seen tons of questions about installing telnet, and not being able to connect...

This step is usually forgotten, but its needed or telnetd will not run:


Make sure /etc/inetd exists

if it doesn't do an:
sudo apt-get install netkit-inetd](*,)

---

### Post by francl on 2006-06-26
I was surprised that there was no telenetd, inetd and ftpd installed by default (I am using dapper drake live CD). Usually they are the first things you try when new to a new Unix system and you would expect them to be their by default. It's so much easier to disable something than to have to install it. Its only about 300K for inetd and telnetd. How about making it part of the standard Unbuntu install. It would save a lot of questions and heartache in your forums (just take a look) and make Ubuntu so much more user friendly (thats more important to new users than security).

If your looking for the inetd and telnetd packages for dapper drake you can find them here [http://packages.ubuntu.com/dapper/net/](http://packages.ubuntu.com/dapper/net/) 

I think Ubuntu is a nice version of Linux though.

---

### Post by MJN on 2006-06-27
[quote=francl](thats more important to new users than security).[/quote]
 
Absolute nonsense. Were you educated at the Microsoft School of Thought?
 
Mathew

---

### Post by harisund on 2006-06-27
Come on Mathew, that's just a bit too rude :)

francl, frankly while I am happy that Ubuntu server install comes with no ports open, sometimes that can be a hassle. 

Actually, those shouldn't be the first things when you install a new system. Telnet is an old and outdated protocol thanks to the lack of security. Yes, I understand new users don't care about security as much initially, but new users wouldn't be doing remote logging, don't you think? 

If you are the kind of user who knows how to remote log in and get your work done, or do stuff like X forwards / system administration remotely, you pretty much have more knowledge than "an average new user".

Anyway, for remote access, you can install the package "openssh-server" which immediately opens port 22 for SSH login. inetutils package can get you telnet (after a bit of configuration, opening firewalls if you have any etc...) if you really want ..

---

### Post by houstonbofh on 2006-06-29
This is an example of secure by design.  It is also why the default install (and any other well thought install) does not need a firewall.  No ports are open other than the ones I need.  And I have more than one Ubuntu box out there, and NONE have inetd, telnetd or ftpd running on them.  They have SSH, and other serveices...  FTP is a good example of a bad default program as well.  Which FTP program?  Depending on use, ftpd may be a lesson in frustration, and removing a pre-installed package is a Dell thing. ;)

---

