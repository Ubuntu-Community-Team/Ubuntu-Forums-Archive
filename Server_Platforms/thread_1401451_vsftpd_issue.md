---
title: "vsftpd issue"
date: 2010-02-08
forum: Server Platforms
---

### Post by kapilajayanath on 2010-02-08
Hi,

I'm getting the following message when I install vsftpd on my ubuntu(9.10).

update-rc.d: warning: vsftpd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)

What does this mean? I'm unable to locate vsftpd.conf file in /etc and I'm unable to start the vsftpd.

I tried removing and reinstalling vsftpd through apt-get and dpkg and I got the above message all the times.

Please advice.

---

### Post by kiranmurari on 2010-02-08
Hi,
The "Default-Stop" in INIT INFO section of /etc/init.d/vsftpd is defined only for runlevel "1". As the other runlevels (0 & 6) in which vsftpd has to be stopped are not defined, this results in the update-rc.d warning.
See: [http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts)
```
Default-Start: run_level_1 [run_level_2...],Default-Stop: run_level_1 [run_level_2...]
defines the run levels where the script should be started (stopped) by default.
For example, if a service should run in runlevels 3, 4, and 5 only, specify 
"Default-Start: 3 4 5" and "Default-Stop: 0 1 2 6".
```I did not face any issues in starting vsftpd. Also, I do see the vsftpd.conf in /etc directory. I'm using Ubuntu-9.10 32 bit server and the version of vsftpd installed was 2.2.0
As far as application execution is concerned, you can safely ignore this warning.

However, I managed to fix the warning by editing /etc/init.d/vsftpd. Changed the line
```
# Default-Stop: 1
```to```
# Default-Stop: 0 1 6
```Now issued the following commands:
```
$ sudo update-rc.d -f vsftpd remove
$ sudo update-rc.d vsftpd defaults
```The warning doesn't occur anymore. But this will only fix the current installation of vsftpd and may not survive re-installation/upgrade.

To make sure that you do a complete uninstall (including configuration files), issue the following command:
```
$ sudo apt-get purge vsftpd
```Now install vsftpd again.
```
$ sudo apt-get install vsftpd
```A few things to look at during/after installation:

[LIST]
[*]Do you see the following message after the update-rc.d warning```
Starting FTP server: vsftpd                         [OK]
```
[*]The vsftpd.conf file should be present by default in /etc folder.
[/LIST]
Hope this helps.

---

### Post by kapilajayanath on 2010-02-10
Hi Kiran,

Thanks a lot for the advice. Anyway before seeing your reply, I did the following.
1. sudo apt-get remove vsftpd
2. Manually located and removed all the vsftpd related directories.
3. sudo apt-get install vsftpd

It worked and still got that warning message. As long as my ftp server was working i didn't worry about the message. Thanks once again for your instructions and I learnt a lot through that.

Kapila

---

### Post by Satoru-san on 2010-02-10
> **kapilajayanath said:**
> It worked and still got that warning message. As long as my ftp server was working i didn't worry about the message.
Where here to help, what was the warning message?

I use vsftpd, it took a while to get the configuration working right, are you sure you can upload files and download them?

---

