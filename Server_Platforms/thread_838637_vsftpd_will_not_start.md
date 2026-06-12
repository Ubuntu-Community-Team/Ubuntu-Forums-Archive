---
title: "vsftpd will not start"
date: 2008-06-23
forum: Server Platforms
---

### Post by MarioFromBelgium on 2008-06-23
When I start vsftp my ubuntu 8 returns OK but connecting to the service fails. When I stop the service it says it can't find any running.
I have paste the return for your info.
Does anybody have an idea?

------
administrator@server1:~$ sudo /etc/init.d/vsftpd start
 * Starting FTP server: vsftpd                                           [ OK ]
administrator@server1:~$ ftp localhost
ftp: connect: Connection refused
ftp> exit
administrator@server1:~$ sudo /etc/init.d/vsftpd stop
 * Stopping FTP server: vsftpd                                                  No /usr/sbin/vsftpd found running; none killed.
------

---

### Post by RealPSL on 2008-06-23
Have you changed the default configuration file for vsftpd? If yes can we see it?

---

### Post by windependence on 2008-06-24
After you start vsftp do the following command:


```
ps aux | grep vsftpd
```


Post the output here for us. I don't think the process is starting.


-Tim

---

### Post by MarioFromBelgium on 2008-06-24
This is what I get for the ps command

--
administrator@server1:~$ sudo /etc/init.d/vsftpd start
 * Starting FTP server: vsftpd                                           [ OK ]
administrator@server1:~$ ps aux | grep vsftpd
1000      5005  0.0  0.2   3004   756 pts/0    R+   21:33   0:00 grep vsftpd


--

actually at first I didn't alter the conf. file but since that didn't work I altered it a little bit. I will copy it in a new post immediately!

---

### Post by MarioFromBelgium on 2008-06-24
Boys and girls,

this will probably look very stupid but since the conf file is larger than my terminal-window (I'm connacting from my portable through putty) I can't copy it.

I just decided to autoremove and install again vsftp so that I can be 100% surten that the conf file is not changed.
Again the same result :

--
root@server1:~# sudo /etc/init.d/vsftpd start
 * Starting FTP server: vsftpd                                           [ OK ]
root@server1:~# ps aux | grep vsftpd
root      5282  0.0  0.2   3004   760 pts/2    S+   22:19   0:00 grep vsftpd
--

---

### Post by RealPSL on 2008-06-24
Does anything get written to the log file /var/log/vsftpd.log?

---

### Post by windependence on 2008-06-25
Looks like it's trying to start but I don't see any process ID so I can only conclude it did not start.

Like RealIPSL said, we should be looking at the log files.

-Tim

---

### Post by MarioFromBelgium on 2008-06-25
Guys,

I will check this evening the log-files. (I'm at work now administering more than a few win-servers, my UBUNTU is at home)

Yesterday,late in the evening I decided again to remove vsftpd and install proftpd...guess what... no problems!!

I'm doing this as a hobby with the intention to(one day soon) introduce the first UBUNTU-server at work; So I'm doing this primarily to learn. Therefor, this evening, I will again instal vsftpd and see what happens, I will post you the log-files!

---

### Post by DSmidgy on 2010-06-12
Hi,
in my case, the problem was in "ssl_enable=YES".

/var/log/syslog states:
server init: vsftpd main process (23493) terminated with status 1
server init: vsftpd main process ended, respawning

---

### Post by DSmidgy on 2010-06-13
I found out, that the certificate does not exist:
/etc/ssl/private/vsftpd.pem

---

### Post by Fliegelflagel on 2010-07-25
Try this:
[FONT="Fixedsys"]sudo vsftpd[/FONT]
and look at what vsftpd tells about its problems. For example:
[FONT="Fixedsys"]500 OOPS: SSL: cannot load RSA certificate[/FONT]
shows that it has problems reading the RSA certificate mentioned in the config file.

---

### Post by duceduc on 2010-08-06
> **DSmidgy said:**
> Hi,
in my case, the problem was in "ssl_enable=YES".

/var/log/syslog states:
server init: vsftpd main process (23493) terminated with status 1
server init: vsftpd main process ended, respawning

Thank you!!! That was the answer to my problem.

---

### Post by nucleuskore on 2011-02-09
On my server I had the same error message of server respawning too quickly and status 1, and the server dying.

So I tried starting it by typing **sudo vsftpd** and got a message telling me that there was a problem with the boolean value of **anonymous_enable**

In my default vsftpd config file it was as follows:

# Allow anonymous FTP? (Disabled by default)
**anonymous_enable=YES** 

Now this is **correct** as I wanted anonymous read-only access, but is wasn't working. Even deleting the line, typing it again and restarting the server did not work. So I simply commented it out so that it now looked like this

# Allow anonymous FTP? (Disabled by default)
#anonymous_enable=YES 

and my server is now working ! I tried to delete the files as an anonymous user and it wont allow me, just as I wanted it. This is insane.

---

### Post by pabloguevara on 2012-06-26
Same problem here...

```
Jun 26 01:41:20 pablo-sony kernel: [  763.714373] init: vsftpd main process ended, respawning
Jun 26 01:41:20 pablo-sony kernel: [  763.726605] init: vsftpd main process (3715) terminated with status 1
Jun 26 01:41:20 pablo-sony kernel: [  763.726666] init: vsftpd main process ended, respawning
Jun 26 01:41:20 pablo-sony kernel: [  763.738945] init: vsftpd main process (3718) terminated with status 1
Jun 26 01:41:20 pablo-sony kernel: [  763.739015] init: vsftpd main process ended, respawning
Jun 26 01:41:20 pablo-sony kernel: [  763.751046] init: vsftpd main process (3721) terminated with status 1
Jun 26 01:41:20 pablo-sony kernel: [  763.751108] init: vsftpd main process ended, respawning
Jun 26 01:41:20 pablo-sony kernel: [  763.763270] init: vsftpd main process (3724) terminated with status 1
Jun 26 01:41:20 pablo-sony kernel: [  763.763330] init: vsftpd respawning too fast, stopped

```


This is my vsftpd config file:

```
# /etc/vsftpd/vsftpd.conf - Dec 3, 2010
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_std_format=YES
nopriv_user=ftpuser
ascii_upload_enable=YES
ascii_download_enable=YES
ftpd_banner=pablo FTP
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd/chroot_list
listen=YES
pam_service_name=vsftpd
userlist_enable=YES
tcp_wrappers=YES
userlist_deny=NO
chmod_enable=NO
pasv_max_port=1024
userlist_file=/etc/vsftpd/user_list

# After upgrading vsftpd to 2.3.5 you may be getting the following message when trying to log in.
# 500 OOPS: vsftpd: refusing to run with writable root inside chroot ()
# This is due to the following update:
#
# - Add stronger checks for the configuration error of running with a writeable
# root directory inside a chroot(). This may bite people who carelessly turned
# on chroot_local_user but such is life.
#
# workaround is:
#
# sudo chmod a-w /home/ftpuser
#
# or add:
allow_writeable_chroot=YES

```

```
pablo@pablo-sony:~$ uname -a
Linux pablo-sony 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by pabloguevara on 2012-06-26
I did try what nucleuskore sugests, but It did not work for me, I till get:

```
Jun 26 01:52:30 pablo-sony kernel: [ 1434.136995] init: vsftpd main process (3884) terminated with status 1
Jun 26 01:52:30 pablo-sony kernel: [ 1434.137063] init: vsftpd main process ended, respawning
Jun 26 01:52:30 pablo-sony kernel: [ 1434.145912] init: vsftpd main process (3887) terminated with status 1
Jun 26 01:52:30 pablo-sony kernel: [ 1434.145940] init: vsftpd main process ended, respawning
Jun 26 01:52:30 pablo-sony kernel: [ 1434.155155] init: vsftpd main process (3890) terminated with status 1
Jun 26 01:52:30 pablo-sony kernel: [ 1434.155218] init: vsftpd main process ended, respawning
Jun 26 01:52:31 pablo-sony kernel: [ 1434.166012] init: vsftpd main process (3893) terminated with status 1
Jun 26 01:52:31 pablo-sony kernel: [ 1434.166074] init: vsftpd main process ended, respawning
Jun 26 01:52:31 pablo-sony kernel: [ 1434.177605] init: vsftpd main process (3896) terminated with status 1
Jun 26 01:52:31 pablo-sony kernel: [ 1434.177687] init: vsftpd main process ended, respawning
Jun 26 01:52:31 pablo-sony kernel: [ 1434.186504] init: vsftpd main process (3899) terminated with status 1
Jun 26 01:52:31 pablo-sony kernel: [ 1434.186568] init: vsftpd main process ended, respawning
Jun 26 01:52:31 pablo-sony kernel: [ 1434.197124] init: vsftpd main process (3902) terminated with status 1
Jun 26 01:52:31 pablo-sony kernel: [ 1434.197186] init: vsftpd main process ended, respawning
Jun 26 01:52:31 pablo-sony kernel: [ 1434.206209] init: vsftpd main process (3905) terminated with status 1
Jun 26 01:52:31 pablo-sony kernel: [ 1434.206282] init: vsftpd main process ended, respawning
Jun 26 01:52:31 pablo-sony kernel: [ 1434.218096] init: vsftpd main process (3908) terminated with status 1
Jun 26 01:52:31 pablo-sony kernel: [ 1434.218192] init: vsftpd main process ended, respawning
Jun 26 01:52:31 pablo-sony kernel: [ 1434.230363] init: vsftpd main process (3911) terminated with status 1
Jun 26 01:52:31 pablo-sony kernel: [ 1434.230426] init: vsftpd main process ended, respawning
Jun 26 01:52:31 pablo-sony kernel: [ 1434.242397] init: vsftpd main process (3914) terminated with status 1
Jun 26 01:52:31 pablo-sony kernel: [ 1434.242460] init: vsftpd respawning too fast, stopped

```

---

