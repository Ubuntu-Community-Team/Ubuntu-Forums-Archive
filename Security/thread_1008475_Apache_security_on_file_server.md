---
title: "Apache security on file server"
date: 2008-12-11
forum: Security
---

### Post by technosinner on 2008-12-11
Hi everybody (Hi Dr. Nick).

I once again turn to this community to help my small mind get around technology that surpasses me.  I have a small Ubuntu server at home; it's mostly a file server with a few HDD and Samba shares.  I also have a Apache 2.2 server running on it, which until recently served only for internal testing.

I've been looking into opening this HTTP server to the outside world.  I don't intend to have high traffic on it, but I need a few specific things to be fully accessible thru HTTP.  Of course I'm paranoid because I have my personnal files right next to this abysmal void that is the internet.  (Mind you anything REALLY sensitive is encrypted anyway so that's more or less an issue, but still...)

I know the best thing is to NOT host both services on the same machine but this isn't a solution right now.  So I have a few questions:

- Can a user coming through the Apache service go up root the virtual server?  If so, how can I prevent this?
- What is the www-data user/group actually used for?
- Would having a seperate network interface help?

Note that I follow basic security rules: I don't have a password for root and no user has root priviledge, I installed Apache as a component of Ubuntu and followed default install and the server itself is behind a router (which acts as DHCP).

I tried to rummage through the forums and the net in general but a lot of the topics surpass my knowledge in linux and networking.  I want to learn but I have to start by understanding what I'm doing!

Any help will be greatly appreciated!
Thanks
~ts

---

### Post by cdenley on 2008-12-11
> **technosinner said:**
> 
- Can a user coming through the Apache service go up root the virtual server?  If so, how can I prevent this?
- What is the www-data user/group actually used for?
- Would having a seperate network interface help?

1. What do you mean "up root"? A user shouldn't be able to gain root user access. The most common way for this to happen would probably be if an attacker gained shell access through a vulnerability in your web scripts or apache itself, then managed to escalate privileges with a local vulnerability. If a user gains access to the root directory, either apache is configured improperly, or there is a serious flaw in one of your web scripts.

2. Apache runs as the user/group www-data. This user privilege seperation helps protect your system. This ensures that if a user exploits a vulnerability in your web server, they won't have root user access. This also means that the www-data user/group must have read access to anything you want apache to server.

3. Not really.

---

### Post by technosinner on 2008-12-11
Thanks for the answers!  Let me clarify what I meant in my first one, even if you sorta answered: I meant up in directory level.  Right now I have the default /var as the virtual server, so if I understand correctly, a user can't - unless they gain access to root priviledge - navigate out of there, right?

That's what I'm afraid of... and I won't be using scripts or only very solid and tested ones.

And as for www-data, can I specifically deny it access to any directories?  Call me a noob, but I haven't figured that out yet...

---

### Post by cdenley on 2008-12-11
If your DocumentRoot is set to /var, then it should be impossible to navigate outside of there, unless you create symlinks. It is a very common scripting error to allow the reading of files outside DocumentRoot, but since you're not scripting, I wouldn't worry about it.

You can't specifically deny access to www-data, but you can ensure that sensitive data does not have permissions which allow all users (including www-data) to read it.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by bodhi.zazen on 2008-12-11
Your first line of defense is your router :twisted:

Your second line of defense is to secure apache.

[http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786)

Third, just use iptables, or ufw, on the server to disallow samba connections outside your LAN.

---

### Post by lavinog on 2008-12-11
There are alot of things I am still learning with apache, but here are a couple of things i have learned.
Watch your log files regularly
I used to have a website hosted with yahoo, and there used to be a wordpress blog on it. The version yahoo installs is pretty outdated. I did find a way to update it, but it was a pain to do do with the limited access yahoo gives you. Since then I took it down, and transfered the domain to my personal webserver and just put a blank place holder there. I noticed very quickly that there were alot of bots scanning for "/wp-admin/post.php"

Many of these content management/blog software that makes websites easier to maintain will be your weakest link. If you must use one, make sure it is actively worked on, and that you stay up to date.

Pay attention to permissions. If there is no reason for apache to write to a folder, don't let it write to it.

You can limit control from certain ip addresses:
```
	<Directory "/var/www">
                Options -MultiViews
                AllowOverride None
		Order deny,allow
		deny from all
                allow from 192.168.1
        </Directory>

```
This will only let users from my local network view the site. You can add multiple allow and deny lines. The order statement determines how this behaves. I am pretty sure though this wont protect you from spoofed attacks, and really if you wanted to limit this to your local network you can block port 80 on your router. I was just using this as an example.

```
	<Directory "/var/www">
                Options -MultiViews
                AllowOverride None
		Order allow,deny
		deny from 66.5
                allow from all
        </Directory>

```
This should allow everyone except ip addresses starting with 66.5

There is an option FollowSymLinks that from what I read can be a security risk and could be used to get into areas of your system that you don't want people to be. Some web programs use symlinks to work...if you do need it, make sure it is only enabled in folders that need it, and do a regular check to make sure that it doesn't change the location it points to. (also having the right permissions should help too)

---

### Post by technosinner on 2008-12-14
Super!  Thanks guys I'll look it up and I'll post my probably numerous other questions!

~ts

---

