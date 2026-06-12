---
title: "URGENT: Why does certain accounts have shell access?"
date: 2006-09-10
forum: Server Platforms
---

### Post by ff2k on 2006-09-10
I was doing some maintenance work and noticed several default accounts have /bin/sh access:

> daemon
bin
sys
games
lp
mail
news
uucp
proxy
www-data
backup
list
irc
gnats
nobody

I thought I was compromised. I checked my other server which isn't accessible online and I noticed these accounts have shell access. 

Why do these accounts need shell access? ](*,)

Someone might exploit something, in say, apache2 and since www-data have shell, they might get in easily.

---

### Post by dickohead on 2006-09-10
They are not actual users, but more like permission levels...

---

### Post by ff2k on 2006-09-11
What are these "permission levels"? I've never heard of them. What are the other levels? :-k 

I've already changed their shell from /bin/sh to /bin/false.

---

### Post by dickohead on 2006-09-12
Well, games for example lets users play games... www-data is the permissions that your /var/www files should have, mail would be the permissions for an smtp/pop server etc etc.

You get the idea, not so much actual users, but users the systems needs for different services, that way not all services are given root access, which is a bad idea.

It's more secure this way. But as to other 'permission levels' or system users and the impact of setting /bin/sh to /bin/false you'd have to either google it or hope someone else replies...

Sorry!

Dickohead.

---

### Post by tribaal on 2006-09-12
The system won't let anyone login with theses accounts, they exist to allow some programs to run as demons and do automatic tasks without giving them root privileges: they are given a user status, so they can only "mess with" the files they have access to, just like any other user.

A good example of why they *need* shell access would be the cron demon. 
Cron, as you may know, is used to issue shell commands at a given time (like a schedule application launcher). Cron needs shell access, since it will actually run a shell command at the time you specified :)

Hope I make sense

- trib'

---

### Post by ff2k on 2006-09-12
dickohead,

Thanks for your reply. I do understand the need for separate users for certain things so that other processes/daemons won't have access or have limited access to their own files. Other Linux/Unix systems have these too, obviously. I'm just wondering why these accounts have their shells configured to /bin/sh while other Linux/Unix distros configured theres as /bin/nologin or /bin/false.

tribaal,

Thanks for your reply as well. But I made some tests and I was able to run a crontab for www-data *without* it having shell access. 

I'm not questioning why cron would need shell access but why the mentioned accounts need shell access. As my test have shown, accounts don't need shell access to be able to do cron jobs. And those accounts don't have cron tabs configured in:

/etc/cron.d
/etc/cron.daily
/etc/cron.hourly
/etc/cron.weekly
/etc/cron.monthly
/etc/crontab

Ironically, I checked a friends Ubuntu server because according to him, he can't connect via ssh. And guess what? There was a program running at /tmp/"/.tmp called sshd. The owner of the folder and files is www-data and the compromised account downloaded this:

[http://212.78.204.20/mwema/cosmin.tar](http://212.78.204.20/mwema/cosmin.tar)

using wget! :mad:

Why Ubuntu? Why? ](*,)

---

### Post by ff2k on 2006-09-18
Dear mods,

Can this thread be moved to Security Issues?

Thanks!

---

### Post by lamego on 2006-09-19
If the accounts are disabled the shell being valid makes no difference. What is the security issue here ?

Regardless of not being important I would also  like to know the reason for this option :)

---

### Post by ff2k on 2006-09-20
The security issue is that someone was able to login to a supposedly "disabled account" called www-data and install some sort of bot.

---

### Post by lipilee on 2007-12-14
Not sure if this ever got closed, but just for the archives (I came across this topic for smth unrelated): having smth run as www-data obviously does not mean someone logged in with the www-data user. Rather using sloppy webservices, such as perl cgi without suexec or php without safe mode, etc., and having /tmp mounted without nodev and noexec... It takes a bad php script to grab and run a little shellbot from there.
So ppl: don't this get you scared, just always take reasonable security measures when running a web server.

---

### Post by stmurray on 2007-12-14
I am new to Ubuntu, but here is general Unix methods to block an id from logging in. 

There are two ways to block an account.  One way is to set the accounts's shell in the entry in /etc/passwd to a non-existent value, such  /bin/false.  (A downside of this is that if someone figures out a way to change /bin/false to an actual shell, then this method fails.  Of course, this would probably be someone with root access, so it is game over anyway, but still....)

The other way a unix-type operating system "blocks" an account is that it puts an invalid password hash into the id's entry in /etc/shadow.  This is where the hash of the password is stored-- an authentication service hashes the password the user enters and looks at the account's entry in /etc/shadow to see if it matches the hash.  If a value is put in the id's /etc/shadow entry, that the hashing algorithm can NEVER compute, then there is no way the id can be authenticated. (The hashing algorithms alway end up a fixed length so any value under that length can never be a valid hash value)  Very often a "*"  or "!" is used.  All the entries in my /etc/shadow, except my personal account, have a "*" or a "!".  

Both ways are valid and many system admins do both.  

I would agree that it would appear in the scenario below that the machine was compromised over a web server....

Sean T Murray

---

### Post by Chayak on 2007-12-17
There are reasons that some accounts have shell access.  They need it as some services use those default accounts to run.

You really don't have to worry as by default they don't allow remote logins under those names.

I'm probably correctly assuming that your friend doesn't use his host.allow and hosts.deny files.  You should really deny any:any and then add the specific hosts and services that you want in the hosts.allow file.

A firewall with access lists is also a good thing to have.  I know some say linux doesn't need a firewall but that's because they don't know any better.  A linux box isn't as easy as a windows machine to crack but it can be done.  Even firewalls can be breached or tricked but every layer of protection you add the safer your systems are.  I shouldn't have to mention strong passwords as well.  If someone can get shell access on a box it's only a matter of time before they root it.

---

