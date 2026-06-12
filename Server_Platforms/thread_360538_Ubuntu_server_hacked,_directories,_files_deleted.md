---
title: "Ubuntu server hacked, directories, files deleted"
date: 2007-02-13
forum: Server Platforms
---

### Post by jlhughes on 2007-02-13
I have been using Ubuntu for a little more than a year. I am an enthusiastic newbie with more than 10 years experience with building web sites but no previous experience running a web server. 

Please keep that in mind as I try to explain what has happened.

Some time between when I went to bed at 11:30 p.m. on Feb. 12 and when I checked my web site at 6:45 a.m. Feb. 13 (all times Pacific), someone was able to access my web root files and delete entire directories.  

The server is Ubuntu 6.10 (Edgy Eft)

All of the software related to the Apache2 server was installed using Ubuntu's defaults. 

The web root was relocated to /home/www

The first thing I need to know is which log files I should secure in order to preserve the ability to find when and how the access occurred.

Any help would be greatly appreciated.

---

### Post by ninocass on 2007-02-13
If you check /var/log/auth it will tell you anyone thats logged into the system/failed logged in

if you check /var/log/apache2/access it will tell you what pages were served 
-----maybe the attacker surfed the site for a bit?

if you check /var/log/error it will display any errors that have been presented if 
-----maybe the attacker was browsing for admin portals any 404's would be noted here.

A best rule of thumb is to totally format the system.  You cant be sure of where the attacker was on your system or what files they could have put up, ie back doors etc.  The only way to be totaly safe is to format.

Nino

---

### Post by jlhughes on 2007-02-13
Can anyone help explain what's happening with this auth log. 

How do I tell which application is using user gforge and root?

Feb 13 10:48:01 localhost CRON[20582]: (pam_unix) session opened for user gforge by (uid=0)
Feb 13 10:48:01 localhost CRON[20582]: (pam_unix) session closed for user gforge
Feb 13 11:09:01 localhost CRON[21853]: (pam_unix) session opened for user root by (uid=0)
Feb 13 11:09:01 localhost CRON[21855]: (pam_unix) session opened for user root by (uid=0)

[snip]


[ I assume what's going on here is a jerk probing for ssh access -- unsuccessfully ]

Feb 13 12:58:51 localhost sshd[28593]: Did not receive identification string from 211.99.156.152
Feb 13 13:01:01 localhost sshd[28724]: Invalid user test from 211.99.156.152
Feb 13 13:01:01 localhost sshd[28724]: (pam_unix) check pass; user unknown
Feb 13 13:01:02 localhost sshd[28724]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:01:04 localhost sshd[28724]: Failed password for invalid user test from 211.99.156.152 port 51258 ssh2
Feb 13 13:01:06 localhost sshd[28733]: Invalid user test from 211.99.156.152
Feb 13 13:01:07 localhost sshd[28733]: (pam_unix) check pass; user unknown
Feb 13 13:01:07 localhost sshd[28733]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:01:09 localhost sshd[28733]: Failed password for invalid user test from 211.99.156.152 port 53160 ssh2
Feb 13 13:01:11 localhost sshd[28740]: Invalid user test from 211.99.156.152
Feb 13 13:01:12 localhost sshd[28740]: (pam_unix) check pass; user unknown
Feb 13 13:01:12 localhost sshd[28740]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:01:14 localhost sshd[28740]: Failed password for invalid user test from 211.99.156.152 port 54979 ssh2
Feb 13 13:01:16 localhost sshd[28747]: Invalid user test from 211.99.156.152
Feb 13 13:01:17 localhost sshd[28747]: (pam_unix) check pass; user unknown
Feb 13 13:01:17 localhost sshd[28747]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:01:19 localhost sshd[28747]: Failed password for invalid user test from 211.99.156.152 port 57563 ssh2
Feb 13 13:01:21 localhost sshd[28754]: Invalid user test from 211.99.156.152
Feb 13 13:01:21 localhost sshd[28754]: (pam_unix) check pass; user unknown
Feb 13 13:01:21 localhost sshd[28754]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:01:23 localhost sshd[28754]: Failed password for invalid user test from 211.99.156.152 port 60948 ssh2
Feb 13 13:01:25 localhost sshd[28761]: Invalid user test from 211.99.156.152
Feb 13 13:01:25 localhost sshd[28761]: (pam_unix) check pass; user unknown
Feb 13 13:01:25 localhost sshd[28761]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:01:28 localhost sshd[28761]: Failed password for invalid user test from 211.99.156.152 port 35332 ssh2
Feb 13 13:01:30 localhost sshd[28768]: Invalid user test from 211.99.156.152
Feb 13 13:01:30 localhost sshd[28768]: (pam_unix) check pass; user unknown
Feb 13 13:01:30 localhost sshd[28768]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:01:32 localhost sshd[28768]: Failed password for invalid user test from 211.99.156.152 port 38722 ssh2
Feb 13 13:01:34 localhost sshd[28775]: Invalid user test from 211.99.156.152
Feb 13 13:01:35 localhost sshd[28775]: (pam_unix) check pass; user unknown
Feb 13 13:01:35 localhost sshd[28775]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:01:37 localhost sshd[28775]: Failed password for invalid user test from 211.99.156.152 port 41459 ssh2
Feb 13 13:01:39 localhost sshd[28782]: Invalid user test from 211.99.156.152
Feb 13 13:01:39 localhost sshd[28782]: (pam_unix) check pass; user unknown
Feb 13 13:01:39 localhost sshd[28782]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:01:41 localhost sshd[28782]: Failed password for invalid user test from 211.99.156.152 port 43997 ssh2
Feb 13 13:01:43 localhost sshd[28789]: Invalid user test from 211.99.156.152
Feb 13 13:01:44 localhost sshd[28789]: (pam_unix) check pass; user unknown
Feb 13 13:01:44 localhost sshd[28789]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:01:46 localhost sshd[28789]: Failed password for invalid user test from 211.99.156.152 port 47341 ssh2
Feb 13 13:01:48 localhost sshd[28796]: Invalid user test from 211.99.156.152
Feb 13 13:01:49 localhost sshd[28796]: (pam_unix) check pass; user unknown
Feb 13 13:01:49 localhost sshd[28796]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:01:51 localhost sshd[28796]: Failed password for invalid user test from 211.99.156.152 port 50536 ssh2
Feb 13 13:01:53 localhost sshd[28803]: Invalid user test from 211.99.156.152
Feb 13 13:01:54 localhost sshd[28803]: (pam_unix) check pass; user unknown
Feb 13 13:01:54 localhost sshd[28803]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:01:55 localhost sshd[28803]: Failed password for invalid user test from 211.99.156.152 port 54037 ssh2
Feb 13 13:02:00 localhost sshd[28810]: Invalid user test from 211.99.156.152
Feb 13 13:02:01 localhost sshd[28810]: (pam_unix) check pass; user unknown
Feb 13 13:02:01 localhost sshd[28810]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:02:03 localhost sshd[28810]: Failed password for invalid user test from 211.99.156.152 port 56969 ssh2
Feb 13 13:02:05 localhost sshd[28817]: Invalid user test from 211.99.156.152
Feb 13 13:02:09 localhost sshd[28817]: (pam_unix) check pass; user unknown
Feb 13 13:02:09 localhost sshd[28817]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:02:11 localhost sshd[28817]: Failed password for invalid user test from 211.99.156.152 port 33693 ssh2
Feb 13 13:02:16 localhost sshd[28830]: Invalid user test from 211.99.156.152
Feb 13 13:02:17 localhost sshd[28830]: (pam_unix) check pass; user unknown
Feb 13 13:02:17 localhost sshd[28830]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:02:18 localhost sshd[28830]: Failed password for invalid user test from 211.99.156.152 port 38659 ssh2
Feb 13 13:02:20 localhost sshd[28837]: Invalid user tester from 211.99.156.152
Feb 13 13:02:21 localhost sshd[28837]: (pam_unix) check pass; user unknown
Feb 13 13:02:21 localhost sshd[28837]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:02:23 localhost sshd[28837]: Failed password for invalid user tester from 211.99.156.152 port 42706 ssh2
Feb 13 13:02:25 localhost sshd[28846]: Invalid user tester from 211.99.156.152
Feb 13 13:02:25 localhost sshd[28846]: (pam_unix) check pass; user unknown
Feb 13 13:02:26 localhost sshd[28846]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:02:28 localhost sshd[28846]: Failed password for invalid user tester from 211.99.156.152 port 45241 ssh2
Feb 13 13:02:30 localhost sshd[28853]: Invalid user tester from 211.99.156.152
Feb 13 13:02:31 localhost sshd[28853]: (pam_unix) check pass; user unknown
Feb 13 13:02:31 localhost sshd[28853]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:02:32 localhost sshd[28853]: Failed password for invalid user tester from 211.99.156.152 port 48653 ssh2
Feb 13 13:02:34 localhost sshd[28860]: Invalid user tester from 211.99.156.152
Feb 13 13:02:35 localhost sshd[28860]: (pam_unix) check pass; user unknown
Feb 13 13:02:35 localhost sshd[28860]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:02:37 localhost sshd[28860]: Failed password for invalid user tester from 211.99.156.152 port 51284 ssh2
Feb 13 13:02:39 localhost sshd[28867]: Invalid user tester from 211.99.156.152
Feb 13 13:02:39 localhost sshd[28867]: (pam_unix) check pass; user unknown
Feb 13 13:02:39 localhost sshd[28867]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:02:41 localhost sshd[28867]: Failed password for invalid user tester from 211.99.156.152 port 53822 ssh2
Feb 13 13:02:43 localhost sshd[28874]: Invalid user tester from 211.99.156.152
Feb 13 13:02:44 localhost sshd[28874]: (pam_unix) check pass; user unknown
Feb 13 13:02:44 localhost sshd[28874]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:02:46 localhost sshd[28874]: Failed password for invalid user tester from 211.99.156.152 port 57249 ssh2
Feb 13 13:02:48 localhost sshd[28881]: Invalid user tester from 211.99.156.152
Feb 13 13:02:48 localhost sshd[28881]: (pam_unix) check pass; user unknown
Feb 13 13:02:48 localhost sshd[28881]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:02:50 localhost sshd[28881]: Failed password for invalid user tester from 211.99.156.152 port 59775 ssh2
Feb 13 13:02:52 localhost sshd[28883]: Invalid user tester from 211.99.156.152
Feb 13 13:02:53 localhost sshd[28883]: (pam_unix) check pass; user unknown
Feb 13 13:02:53 localhost sshd[28883]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:02:55 localhost sshd[28883]: Failed password for invalid user tester from 211.99.156.152 port 34719 ssh2
Feb 13 13:02:56 localhost sshd[28890]: Invalid user tester from 211.99.156.152
Feb 13 13:02:57 localhost sshd[28890]: (pam_unix) check pass; user unknown
Feb 13 13:02:57 localhost sshd[28890]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:02:59 localhost sshd[28890]: Failed password for invalid user tester from 211.99.156.152 port 37213 ssh2
Feb 13 13:03:01 localhost sshd[28897]: Invalid user tester from 211.99.156.152
Feb 13 13:03:01 localhost sshd[28897]: (pam_unix) check pass; user unknown
Feb 13 13:03:01 localhost sshd[28897]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:03:04 localhost sshd[28897]: Failed password for invalid user tester from 211.99.156.152 port 40619 ssh2
Feb 13 13:03:06 localhost sshd[28904]: Invalid user tester from 211.99.156.152
Feb 13 13:03:07 localhost sshd[28904]: (pam_unix) check pass; user unknown
Feb 13 13:03:07 localhost sshd[28904]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:03:09 localhost sshd[28904]: Failed password for invalid user tester from 211.99.156.152 port 43140 ssh2
Feb 13 13:03:11 localhost sshd[28911]: Invalid user tester from 211.99.156.152
Feb 13 13:03:12 localhost sshd[28911]: (pam_unix) check pass; user unknown
Feb 13 13:03:12 localhost sshd[28911]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:03:14 localhost sshd[28911]: Failed password for invalid user tester from 211.99.156.152 port 46668 ssh2
Feb 13 13:03:16 localhost sshd[28918]: Invalid user tester from 211.99.156.152
Feb 13 13:03:17 localhost sshd[28918]: (pam_unix) check pass; user unknown
Feb 13 13:03:17 localhost sshd[28918]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:03:19 localhost sshd[28918]: Failed password for invalid user tester from 211.99.156.152 port 49164 ssh2
Feb 13 13:03:20 localhost sshd[28925]: Invalid user tester from 211.99.156.152
Feb 13 13:03:21 localhost sshd[28925]: (pam_unix) check pass; user unknown
Feb 13 13:03:21 localhost sshd[28925]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:03:23 localhost sshd[28925]: Failed password for invalid user tester from 211.99.156.152 port 52151 ssh2
Feb 13 13:03:25 localhost sshd[28932]: Invalid user tester from 211.99.156.152
Feb 13 13:03:26 localhost sshd[28932]: (pam_unix) check pass; user unknown
Feb 13 13:03:26 localhost sshd[28932]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:03:28 localhost sshd[28932]: Failed password for invalid user tester from 211.99.156.152 port 55663 ssh2
Feb 13 13:03:29 localhost sshd[28939]: Invalid user testing from 211.99.156.152
Feb 13 13:03:30 localhost sshd[28939]: (pam_unix) check pass; user unknown
Feb 13 13:03:30 localhost sshd[28939]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 
Feb 13 13:03:32 localhost sshd[28939]: Failed password for invalid user testing from 211.99.156.152 port 58152 ssh2
Feb 13 13:03:34 localhost sshd[28946]: Invalid user testing from 211.99.156.152
Feb 13 13:03:35 localhost sshd[28946]: (pam_unix) check pass; user unknown
Feb 13 13:03:35 localhost sshd[28946]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.99.156.152 

[ snip ]

---

### Post by tbasten on 2007-02-14
i have got a few linux servers running live these days and every single on of them experiences ssh brute force attack. There are a couple of ways around it. the first is the most obvious, make sure your passwords are strong, i mean strong. Secondly there is no way to completely stop SSH brute force attacks but you can limit the ammount of times they can try with this 

/sbin/iptables -A INPUT -p tcp –dport 22 –syn -m limit –limit 1/m –limit-burst 2 -j ACCEPT
/sbin/iptables -A INPUT -p tcp –dport 22 –syn -j DROP


or 


iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j LOG --log-prefix "SSH_brute_force "
iptables -A INPUT -p tcp --dport 22 -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP

Either of which works.

If you did get hacked, find out which account they logged in with (looking @ succesful loggins @ /var/log/auth, if not in ther try /var/log/auth.x [x being a different number]) once you know which account they logged in with look at the accounts /$home/.bash_history to find out what commands were executed

Hope this might help

Regards Tim

---

### Post by jlhughes on 2007-02-14
OK. Now I think I have a virus.

Here's what just happened.

As I posted earlier, all directories in the web root associated with different domains disappeared. Other directories in the web root tree were left alone.

So, I decided to copy over the remaining files to a dvd-rw disk on a laptop.  The laptop mounts the server home directory with a nfs mount.

When I dragged over the www directory to the DVD Creator window on the laptop and opened the www directory, ALL OF THE MISSING DIRECTORIES WERE VISIBLE!!!

I made a copy of the "missing" files on the dvd. I checked and the files appear to be "OK" and undamaged ON THE DVD.

HOWEVER,  this trick NO LONGER WORKS. The nfs share on the laptop no longer sees the missing files and trying to create a second dvd of the files doesn't work the magic. Now both computers agree that the missing files are missing.

I have tried rebooting the server in rescue mode as a root user, but I still don't see these directories.

What should I do now? (Beside the obvious re-format and reinstall)

---

### Post by tbasten on 2007-02-14
sounds like there is a bot running. Get the bash_history of the account which was hacked and find out what commands were exicuted

---

### Post by jlhughes on 2007-02-14
There is nothing in ~.bash_history that I don't recognize as work I have done.

Any other ideas on how I can reveal these directories and files that are being hidden from me?

---

### Post by tbasten on 2007-02-14
updatedb

locate $filename

---

### Post by gradedcheese on 2007-02-14
> 
Feb 13 10:48:01 localhost CRON[20582]: (pam_unix) session opened for user gforge by (uid=0)
Feb 13 10:48:01 localhost CRON[20582]: (pam_unix) session closed for user gforge


gforge is a sourceforge-like web-based project management software that I assume you've been hosting?  Go to their site right away and read about any security vulnerabilities or other problems that may have been associated with this.  It's very difficult to break in to a standard-issue Apache web server, but it's a bit easier if there's some security vulnerability on some hosted software to exploit.  I suspect that's what happened here :(  Since they seem to have managed to get root, I'd disconnect that box from the network and ssh in to it via a crossover cable or something when you do your diagnostics.

---

### Post by jlhughes on 2007-02-14
More "fun" things:

open terminal window
sudo updatedb (wait for awhile ... when finished)
cd www
ls 

NOW everything shows up HERE in the terminal window

BUT wait a minute! cd www shouldn't exist!  The web root is /home/www not /home/john/www

And yet, there it is -- /home/john/www and inside are all of the original web root folders PLUS the folders that are still in the /home/www/ directory.

So the files were not deleted. They were moved from /home/www to /home/john/www

-----

And now about the gforge user.

I have an application installed called gforge-db-postgresql  (I don't recall having installed this, but I can't be certain I didn't.)

When I attempt to remove app I get this error:

Removing gforge-db-postgresql ...
head: cannot open `/var/lib/postgres/data/postmaster.pid' for reading: No such file or directory
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
dpkg: error processing gforge-db-postgresql (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gforge-db-postgresql
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried reinstalling the app and that failed as well.

This postgresql is installed with an added /7.4/ directory and the removal script can't find what it is looking for because it doesn't know about /7.4/

Any ideas?

---

### Post by gradedcheese on 2007-02-14
you can do a --force-remove instead to have it remove while ignoring the pid file.  

sudo dpkg --force-remove gforge-db-postgresql 

I wonder what happened here... did they port scan until they found something to connect to and then found some way to get in as 'gforge'?  How did they get root?  This might be a stupid question, but by default the root user is not usable on ubuntu (as far as logging in).  Did you or they set a root password?  If you've never touched the root account, can you try setting its password? ("sudo passwd root")

---

### Post by jlhughes on 2007-02-14
> **gradedcheese said:**
> 
sudo dpkg --force-remove gforge-db-postgresql 


When I try this I get this message:

john@ubuntu:~$ sudo dpkg --force-remove gforge-db-postgresql
dpkg: unknown force/refuse option `remove'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
john@ubuntu:~$ 

>  This might be a stupid question, but by default the root user is not usable on ubuntu (as far as logging in).  Did you or they set a root password?  If you've never touched the root account, can you try setting its password? ("sudo passwd root")

I did sudo passwd root and was able to set the password.   Since I was able to create a root password, does that mean someone else had already created the root account?

---

### Post by gradedcheese on 2007-02-14
hmm... maybe use "dkpg --purge" instead then.  I could have sworn it's --force-remove

> I did sudo passwd root and was able to set the password. Since I was able to create a root password, does that mean someone else had already created the root account?

Someone might need to correct me on this but as I understand it:
- out of the box, no root password is set in ubuntu.  this means that the root account, though it exists, cannot be logged in to until a password gets set
- if they had done this, you wouldn't be able to set the password (you'd need to know the one they set it to first)
- therefore, since it was still unset, I would assume that they did not actually gain root, at least not in the sense that they could log in as root

In fact, I wonder if anything was really 'hacked'... the files being moved is strange, but could you have done that somehow?  I'd poke around the logs and see if there's maybe another explanation.

---

### Post by jlhughes on 2007-02-14
> **gradedcheese said:**
> 
In fact, I wonder if anything was really 'hacked'... the files being moved is strange, but could you have done that somehow?  I'd poke around the logs and see if there's maybe another explanation.

I would be more than happy to blame myself for having inadvertently moved the web root files from /home/www to /home/john/www. However, that seems like it would take some real effort. And it doesn't answer why the move took place when I was asleep. (Wife claims I never got up.)

> maybe use "dkpg --purge" instead then.

john@ubuntu:~$ sudo dpkg --purge gforge-db-postgresql
Password:
(Reading database ... 148212 files and directories currently installed.)
Removing gforge-db-postgresql ...
head: cannot open `/var/lib/postgres/data/postmaster.pid' for reading: No such file or directory
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
dpkg: error processing gforge-db-postgresql (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gforge-db-postgresql
john@ubuntu:~$

---

### Post by ninocass on 2007-02-14
Heh id still format just to be on the safe site, working in the IT security area i know only to well what happens when someone gets root on a box, we advise all our clients to format ASAP

As mentioned the SSH brute force attempts are very common.  If you set up SSH with Private Key Authentication and turn off the authenticate wit h leyboard feature it means you can only connect via SSH if you have that Key which will stop any brute force attempts.  Theres a few nice guides on the forums for settings this up, 5 minutes does it :)

---

### Post by LaLLi on 2007-02-14
What kind of Internet connection does your server have? Does your network hardware have a "firewall" to stop Bruteforce before thety even reach the server?

---

### Post by jlhughes on 2007-02-14
> **LaLLi said:**
> What kind of Internet connection does your server have? Does your network hardware have a "firewall" to stop Bruteforce before thety even reach the server?

This server is in my home office. I have a broadband connection, fixed IP address and a Linksys router that directs WAN requests to this server on the LAN.  I have a full Ubuntu Apache2 web server running with ssh active. Behind the Linksys router I use Samba to connect the Windows machines on the LAN and NFS for the Linux boxes.

Obviously, I don't know enough about security to expose myself like that, but I am the only person relying on this server and therefore the only one hurt when it is attacked. It also represents my learning tool.

---

### Post by MJN on 2007-02-15
> **jlhughes said:**
> ... but I am the only person relying on this server and therefore the only one hurt when it is attacked.

On the contrary; the rest of us suffer when your machine is compromised given the inevitable nefarious uses it's likely to be put to once hijacked.

Mathew

---

### Post by thomaso on 2007-02-17
> **MJN said:**
> On the contrary; the rest of us suffer when your machine is compromised given the inevitable nefarious uses it's likely to be put to once hijacked.

Mathew

maybe but with basic security a linux box is so much harder than windows its not worth it to 95% of hackers to attack one... so haveing one linux box hacked while sad really only hurts the user hacked

---

### Post by MJN on 2007-02-17
What nonsense. I take it you've never heard of Kaigent.C? (here's a link in case not: [http://www.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=ELF%5FKAIGENT%2EC](http://www.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=ELF%5FKAIGENT%2EC))

If a hacker breaks into your box they are unlikely to call it a day - there's only so much 'useful' info on somebody's home PC. More likely they'll utilise your SMTP connection to send spam and utilise other income-generating techniques.

Don't bring the Windows/Linux battle into this - it's irrelevent. A compromised machine is a compromised machine.

Mathew

---

### Post by GoBieN on 2007-02-17
After reading this whole story, i don't think you were hacked. But i beliece that a security issue in the PHP or CGI scripts or perhaps the gforce software, allowed someone to mess around on your system using by moving or deleting files. Nothing really serious.

---

### Post by homli on 2007-03-04
> **tbasten said:**
> ...you can limit the amount of times they can try with this 

/sbin/iptables -A INPUT -p tcp &#8211;dport 22 &#8211;syn -m limit &#8211;limit 1/m &#8211;limit-burst 2 -j ACCEPT
/sbin/iptables -A INPUT -p tcp &#8211;dport 22 &#8211;syn -j DROP

or 

iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j LOG --log-prefix "SSH_brute_force "
iptables -A INPUT -p tcp --dport 22 -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP

The ipt_limit rules would also prevent *you* from SSHing into the box if someone is brute forcing, wouldn't they?

The ipt_recent rules get around that issue.  However, you'll want to make sure your kernel doesn't suffer from [[COLOR="Blue"]_this bug_[/COLOR]]("http://www.oreillynet.com/linux/blog/2006/05/iptables_recent_module_bug.html") before using ipt_recent.

---

### Post by Slychilde on 2007-03-04
If you haven't yet, definitely read all the info you can about OpenSSH on these boards and in the wiki.  I would make a RSA encryption key, and set it so ssh will only accept that; turn off normal passwords.  You can SSH from windows machines via putty, and it supports RSA keys, although it will require one extra step.

Most brute force attempts are dictionary log-ins.  When I was messing around with a LAMP server, I had script kiddies brute forcing me 24/7.  So, make sure you have a lengthy, complicated password.  It sucks to type that stuff, I know, but it's worth it.

In the end, I got sick of the silliness of getting brute forced, so I redirected my ssh port to a very obscure port (2k+, I think).  I think this would be perfect for you, since the ssh server is for personal use only.  After I set my port to something very 'non-standard' the attempts flat out stopped.  I guess what someone said on this forum holds true, "Security through obscurity."

Tbasten, would you mind explaining what those commands do exactly?  That sounds interesting.

---

### Post by GoBieN on 2007-03-04
Just set your SSHD server on a different port then the standard 22 and you don't have to be concerned about brute force ! Use a port only you know !

---

### Post by esaym on 2007-03-05
> **GoBieN said:**
> Just set your SSHD server on a different port then the standard 22 and you don't have to be concerned about brute force ! Use a port only you know !

Yea thats what I do

---

