---
title: "OpenFire: cannot log into to Admin Console"
date: 2009-06-09
forum: Server Platforms
---

### Post by mfleonhardt on 2009-06-09
Hello all,

Just installed OpenFire on a server running xubuntu 9.0.4.  Setup went smoothly, installing the package and the web-based configuration.  When I try to log into the admin control panel, however, I keep getting:

```
Login failed: make sure your username and password are correct and that you're an admin or moderator.
```

On the browser and

```
2009.06.09 22:45:36 Failed admin console login attempt by admin from 192.168.0.11
```

in /var/log/openfire/warn.log.

I did go through the admin password change in the setup.  I can log in via a chat client as admin, and I've tried replacing both the plain and encrypted passwords in the database (using MySQL for db).

I'm stumped.  Anyone got any suggestions?

Matt

---

### Post by ghen on 2009-06-10
I had this problem with a windows server. The administrator account just got screwed up somehow. I had to reinstall the openfire server.

I suggest asking on the openfire support pages. There are config files that can be edited or deleted to -possibly- get admin access back on track, they didn't work for me but then again I have mine on a windows 2000 server.

But since this is definitely an openfire problem, ask there.
[http://www.igniterealtime.org/community/community/support/openfire_(formerly_wildfire)_support](http://www.igniterealtime.org/community/community/support/openfire_(formerly_wildfire)_support)


I also highly recommend the User Import Export addon for backup/recovery because of this problem ;)

---

### Post by nail.xx on 2009-07-02
Hello,

I know that is a bit late but I got the same problem and it was solved by stupid
```
service openfire restart
```

Thats it :)

---

### Post by nuclear88 on 2009-07-10
It appears to be a permissions issue (possibly with the internal db they're using). If you do a
```
chmod o+r /usr/share/openfire
```
after installing the .deb and going through the online config at [http://servername:9090](http://servername:9090), it should work for you.

---

### Post by go_beep_yourself on 2009-08-07
Is the Administrator account for the user admin? I am assuming so because it never asked me to pick a username, just for my email and password, and I've tried everything to make it work. I'm going to do as one suggested and check the permissions of a file.

---

### Post by papastevez on 2009-11-12
> **nail.xx said:**
> Hello,

I know that is a bit late but I got the same problem and it was solved by stupid
```
service openfire restart
```Thats it :)


Running from Centos I had the same problem. ```
/etc/init.d/openfire restart 
```solved my problem.
This was after my second attempt at installing it btw. the first time stopping and restarting did nothing...though that might be becuase my initial troubleshooting fubar'd it.:P

---

### Post by CCG121 on 2009-12-18
I have tried all the suggestions here and followed [this]("http://library.linode.com/real-time-messaging/xmpp-servers/install-openfire-ubuntu-9.10-karmic") guide i have reinstalled it at least 5 times now and still cannot log in default settings till I get to the "Login failed: make sure your username and password are correct and that you're an admin or moderator."  any other ideas?

---

### Post by urthmover on 2010-01-14
me too  after a fresh install I still get Login failed check your username and password ... very strange

---

### Post by go_beep_yourself on 2010-01-16
Has anyone tried the share.java.net servers listed on the collaboration website to see how well they work? Hopefully, it is not buggy as well.

---

### Post by mazz0 on 2010-03-02
I have this problem in Windows 7.  I gather it's a bug that's been known about for months.  Anyone know of an alternative XMPP server?

---

### Post by go_beep_yourself on 2010-03-07
> **mazz0 said:**
> I have this problem in Windows 7.  I gather it's a bug that's been known about for months.  Anyone know of an alternative XMPP server?

An alternative for what? Were you using openfire for Netbeans developer collaboration plugin?

---

### Post by Neo31 on 2010-06-07
> **papastevez said:**
> Running from Centos I had the same problem. ```
/etc/init.d/openfire restart 
```solved my problem.
This was after my second attempt at installing it btw. the first time stopping and restarting did nothing...though that might be becuase my initial troubleshooting fubar'd it.:PI confirme ```
service openfire restart
``` solved the problem

---

### Post by fallingcow on 2011-08-04
If anyone else runs in to this problem, be aware that the username is *always* "admin", **not** the e-mail address you entered on the last set up screen along side the admin password.

See:

[http://community.igniterealtime.org/thread/42644]("http://community.igniterealtime.org/thread/42644")

---

### Post by Alpinist on 2011-09-18
> **fallingcow said:**
> If anyone else runs in to this problem, be aware that the username is *always* "admin", **not** the e-mail address you entered on the last set up screen along side the admin password.

See:

[http://community.igniterealtime.org/thread/42644]("http://community.igniterealtime.org/thread/42644")

Sheesh. Thanks a lot. That is very poorly documented.

---

