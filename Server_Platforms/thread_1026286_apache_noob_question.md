---
title: "apache noob question"
date: 2008-12-31
forum: Server Platforms
---

### Post by big-t on 2008-12-31
hello, i got some problems,

i just installed apache2 , php5 , and mysql..
everything work's great!!

even phpmyadmin...

but, always a but..

i can't access my var/www folder :(
i can think this question have been asked a million times, so i am sorry if someone is bored of this question :P

and yeah, i did try to search i didn't find nothing useful for this problem.

and another thing wile i am at it.. 

i did try to set up an ftp, yeah i made that to, but how can i sett dir to var/www, maby that will solve my upload problem there.

i don't remember the name of the ftp server i installed...

you can tell me abaut a easy server client, i and switch gladely :P

thanx for any respond on this threat.

happy new year people <3

---

### Post by TestDummy! on 2008-12-31
Would the FTP daemon be ProFTPd or vsftpd by chance?

---

### Post by big-t on 2008-12-31
vsftpd is the name of it yes, thanx for the reminder.

any tips for setting a user that can access var/www folder :P?

---

### Post by TestDummy! on 2008-12-31
Well, according to their manual ([http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)), you add in something like:

**local_root=/var/www**

> local_root
This option represents a directory which vsftpd will try to change into after a local (i.e. non-anonymous) login. Failure is silently ignored.

Default: (none)

To the **/etc/vsftpd.conf** configuration file.

Don't forget to restart the daemon afterwards: **sudo /etc/init.d/vsftpd restart** (or 'sudo service vsftpd restart', whichever you prefer).

---

### Post by big-t on 2008-12-31
thanx, i will try this now :D

---

### Post by big-t on 2008-12-31
you got a thanks add from my site, it's work.

i am realy realy thankful now, thank for the help :D

---

### Post by TestDummy! on 2008-12-31
I should mention that in trying the daemon myself (my Ubuntu Server box is my testbed), I did run into a big of a snag. vsftpd is configured for anonymous login by default, you have to uncomment a line to make password protected local accounts (like the one you're using on the computer itself) work.

```
# Uncomment this to allow local users to log in.
local_enable=YES
```

---

### Post by big-t on 2008-12-31
omfg, now i got another problem.

my ftp user, can't download or upload or delete any files xD

but i can view them :P

---

### Post by TestDummy! on 2008-12-31
That's covered by other entries listed in the manual.

```
anon_world_readable_only
When enabled, anonymous users will only be allowed to download files which are world readable. This is recognising that the ftp user may own files, especially in the presence of uploads.

Default: YES
```

```
write_enable
This controls whether any FTP commands which change the filesystem are allowed or not. These commands are: STOR, DELE, RNFR, RNTO, MKD, RMD, APPE and SITE.

Default: NO
```

If you'd rather just login using your normal computer username, you can probably disable this one.

```
anonymous_enable
Controls whether anonymous logins are permitted or not. If enabled, both the usernames ftp and anonymous are recognised as anonymous logins.

Default: YES
```

---

### Post by TestDummy! on 2008-12-31
Hm, I'm noticing a problem in my directions. They allow the user to access / without a problem. Perhaps somebody could help correct me so things aren't so insecure.

---

### Post by big-t on 2008-12-31
i tried, now it still don't work :/

is it possible to log in as root? someone know the password for the root user?

is not the password i got for my local user.

---

### Post by windependence on 2008-12-31
You're going to have all kinds of issues with permissions with FTP. I upload all my web files via SCP using WinSCP or from Linux, I use an SFTP client.

-Tim

---

### Post by TestDummy! on 2008-12-31
If it isn't that much trouble for you, I've personally had better luck with proftpd where I've had to use a FTP daemon.

I second the use of SFTP. Since I normally interact with the (headless) testbed over SSH, using SFTP wasn't any trouble and I don't need to have a FTP daemon running otherwise.

---

### Post by Iowan on 2008-12-31
> **big-t said:**
> i tried, now it still don't work :/

is it possible to log in as root? someone know the password for the root user?

is not the password i got for my local user.The servers, like the desktops, come with root account disabled.  It violates forum policy to tell you how to enable the root account (though the information is available on the web).  A couple of other options - change permissions on /var/www, or move Document Root to a more accessible folder.

---

### Post by windependence on 2009-01-01
> **Iowan said:**
> The servers, like the desktops, come with root account disabled.  It violates forum policy to tell you how to enable the root account (though the information is available on the web).  A couple of other options - change permissions on /var/www, or move Document Root to a more accessible folder.

Neither of these options is recommended or necessary to solve his problem. This is more than likely an ownership issue, but without more detail it is not easy to troubleshoot the issue.

-Tim

---

### Post by big-t on 2009-01-01
> **Iowan said:**
> The servers, like the desktops, come with root account disabled.  It violates forum policy to tell you how to enable the root account (though the information is available on the web).  A couple of other options - change permissions on /var/www, or move Document Root to a more accessible folder.

i am reel sorry, i didn't know that.

now i know, tanks for information. :)

---

### Post by big-t on 2009-01-01
well, what's really my problem.

i got a fresh installation of ubuntu hardy 8.4 (i think, i am a bitt blurry after the night, i was out whit my friends xD)

and my webhost whent down, so i need to host my own blog for a little while.

and i got everything installed and working, but i can't access var/www..

is it possible to change apache config file to set another direction for www?

that whould solve it i think :)

i used to run windows server before, and i am not gonna go back to that :P

even if i gonna sit here 1 week before i got everything working :P

---

### Post by Iowan on 2009-01-01
> **windependence said:**
> Neither of these options is recommended or necessary to solve his problem.OK... maybe not necessary...> Change the DocumentRoot to point to the new location. For example, /home/user/public_html/
#

Change the Directory directive, replace <Directory /var/www/> to <Directory /home/user/public_html/>
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by big-t on 2009-01-01
tanks :D

it's working :D

---

