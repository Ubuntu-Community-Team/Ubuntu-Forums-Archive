---
title: "DenyHosts, installation and configuration"
date: 2007-08-28
forum: Server Platforms
---

### Post by kentl on 2007-08-28
Hi!

I'm pretty new to Linux and especially SSH. Still I have installed OpenSSH and tried to make it secure. I am confused about a couple of things and hope you folks can help me. :redface:

**DenyHosts installation**

This is what it looked like when I installed DenyHosts from the package repository:
```

kent@cow:~$ sudo aptitude install denyhosts
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  denyhosts
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/62.4kB of archives. After unpacking 422kB will be used.
Writing extended state information... Done
Selecting previously deselected package denyhosts.
(Reading database ... 19253 files and directories currently installed.)
Unpacking denyhosts (from .../denyhosts_2.6-1_all.deb) ...
Setting up denyhosts (2.6-1) ...
 * Starting DenyHosts denyhosts                                          [ OK ]

```

As DenyHosts can be run as a cron job or as a deamon. Did any of that get set up with the package install? I suspect that the "* Starting DenyHosts denyhosts                                          [ OK ]" message indicates that a deamon was started. Am I right? Will it start up with the computer from now on?

How can you know these things? That is, if deamons or cron jobs were added when you installed packages?

**DenyHosts configuration**

How do you have DenyHosts configured? Do you like all the default settings or do you change them?

Is it hard to get e-mail notification working or is it working from the start? The default settings says:
```
ADMIN_EMAIL = root@localhost
SMTP_HOST = localhost
SMTP_PORT = 25

```
Will this work? Does it mean that I have an SMTP server and some kind of mail application straight from installing Ubuntu Server?

---

### Post by bodhi.zazen on 2007-08-28
Denyhosts is up and running, but not in daemon mode ...

daemon mode is for uploading/downloading restricted hosts from the central server.

Best to read through the config file as there are several options. The config file is very well commented.

```
sudo gedit /etc/denyhosts.conf
```

See this link : [http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)

---

### Post by kentl on 2007-08-28
I now have my config file as I want it to be. For the record I've read the FAQ and all blog posts under "As seen elsewhere" on the DenyHosts site [http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/).

This is what I get if I look for files containing the substring denyhosts in their name:
```

kent@cow:~$ sudo find / -name '*denyhosts*'
/var/log/denyhosts
/var/cache/apt/archives/denyhosts_2.6-1_all.deb
/var/lib/dpkg/info/denyhosts.prerm
/var/lib/dpkg/info/denyhosts.list
/var/lib/dpkg/info/denyhosts.conffiles
/var/lib/dpkg/info/denyhosts.postrm
/var/lib/dpkg/info/denyhosts.md5sums
/var/lib/dpkg/info/denyhosts.postinst
/var/lib/denyhosts
/usr/sbin/denyhosts
/usr/share/man/man8/denyhosts.8.gz
/usr/share/doc/denyhosts
/usr/share/denyhosts
/usr/share/denyhosts/denyhosts_ctl.py
/usr/share/denyhosts/denyhosts_ctl.pyc
/etc/rc6.d/K20denyhosts
/etc/rc2.d/S20denyhosts
/etc/rc1.d/K20denyhosts
/etc/rc3.d/S20denyhosts
/etc/rc5.d/S20denyhosts
/etc/rc4.d/S20denyhosts
/etc/init.d/denyhosts
/etc/rc0.d/K20denyhosts
/etc/logrotate.d/denyhosts
/etc/denyhosts.conf

```
Isn't it being in init.d an indication that it's being started at bootup, as a deamon? Or maybe I'm confusing it and it's being ran once, or perhaps in the background but not as a deamon? I'm new to all this, I apologize for my cluelessness.

What I want to do is run it using a cron job. But if it's starting up by some other means my cron job won't be able to run (as it looks for the lock file for denyhosts, finds it, and terminates).

Can someone shed a bit more light on this please? :confused:

---

### Post by falcon15500 on 2007-08-29
Actually - DenyHosts running in Daemon mode is independant of synching with the master server.  You can set DenyHosts to run as a daemon, checking your syslog at intervals you specify (default being 30 seconds) but NOT do uploading to or downloading from the synch server.
 
Check the config for DenyHosts - as mentioned it is very well commented.  You should quite easily locate the appropriate sections.

And yes, it being in init.d (and rc2.d) shows that it is being started as a daemon.  If you don't want this to happen, remove the entries from init.d and the rcX.d's .  You will still have to change the DenyHosts config file to stop it from becoming a daemon (I think).

falc

---

### Post by kentl on 2007-08-29
> Check the config for DenyHosts - as mentioned it is very well commented. You should quite easily locate the appropriate sections.
Yes, I've checked it plenty by now. And it's great! But as far as I know you can't set it to run as a daemon using it. You can only specify the options to use when you run it as a daemon. To support my claim:
```
kent@cow:~$ cat /etc/denyhosts.conf | grep daemon | grep :
# DAEMON_LOG: when DenyHosts is run in daemon mode (--daemon flag)
# DAEMON_LOG_TIME_FORMAT: when DenyHosts is run in daemon mode
# DAEMON_LOG_MESSAGE_FORMAT: when DenyHosts is run in daemon mode
# DAEMON_SLEEP: when DenyHosts is run in daemon mode (--daemon flag)
# DAEMON_PURGE: How often should DenyHosts, when run in daemon mode,
# SYNC_UPLOAD: allow your DenyHosts daemon to transmit hosts that have
# SYNC_DOWNLOAD: allow your DenyHosts daemon to receive hosts that have

```
As you can see there is no option to make it run as a daemon. To run it as a daemon you start it using the --daemon flag.

Apparantly it got added as a daemon which is started during boot up during package installation.

My reason for not wanting to run it as a daemon is that it seems kind of silly to have it constantly reside in memory even when I'm not using it, as it's sleeping most of the time anyway.

Perhaps it's most convenient to run it as a daemon anyway, as the package seems designed for that purpose. If I do not use it as a daemon I guess I'll have trouble after my next update. Also, if I don't run it as a daemon should I move the script?

Another issue regarding DenyHosts.

It has blocked one IP so far. But it did not send any mail even though ADMIN_EMAIL and SMTP_HOST and SMTP_PORT all were set correctly. Is there a way to troubleshoot this issue that you know of?

---

### Post by az on 2007-08-29
> **kentl said:**
> 
My reason for not wanting to run it as a daemon is that it seems kind of silly to have it constantly reside in memory even when I'm not using it, as it's sleeping most of the time anyway.

Perhaps it's most convenient to run it as a daemon anyway, as the package seems designed for that purpose.

It hardly consumes any resources whatsoever.  I can assure you that you won't miss the few k of ram it takes up.

Yes, the package is designed to run out-of-the-box without any fiddling since it has sensible defaults.

---

### Post by kentl on 2007-08-29
I'll keep it as a daemon, to stay out of trouble when updates occur. If it's sensible or not is up for debate, but in this case either way works well I guess.

Got any suggestion to my e-mail problem? If only the script would have had an --mailtest (and perhaps a ---synctest) argument which tested its feature and wrote out some debug information. Then it would have been a bit easier for me, being new to Linux as I am, to solve.

---

### Post by HermanAB on 2007-08-29
Programs like denyhosts is somewhat dangerous since it can potentially lock you out of your own system.

A simpler solution is to change the port that sshd runs on, to something only you know.  This works really well, because the script kiddies are stupid.

Change the port number to for example 2222 in /etc/ssh/sshd_config and restart sshd.  Then remember to specify the port number when you do ssh.

Cheers,

Herman

---

### Post by lhomme on 2007-08-29
About the email, I've had denyhosts running for about a month now and haven't had much luck with the email part.  I've tried all the proper info for my verizon.net account, followed some instructions for setting up gmail as an smtp server (this one for some reason killed denyhosts when the config file is read), and now am on to an account at secureserver.net (this doesn't seem to work either)

using 2.6-1 form the networking universe repository 

I've heard that verizon does weird things to block spam that may be an issue.  The Gmail thing was odd, but I think I followed these steps:
```
smtp.gmail.com (use authentication)
Use Authentication: Yes
Use STARTTLS: Yes (some clients call this SSL)
Port: 465 or 587
```
And after trying to securserver.net account and it not working I'm getting disenchanted 

I hope someone else has had better luck.

---

### Post by kentl on 2007-08-30
HermanAB:

If the script works as it should, and does not contain bugs, then I have to type the wrong passphrase (in my setup using key auth) 10 times during 5 days to get locked out. I don't think it will happen. But of course it's a risk I'm taking.

I have changed the SSH port already. And I'm using RSA2 keys to auth and have disabled keyboard logon and root logon. So I consider my SSH setup to be secure enough now. But thanks for your tip! It's a good tip.

lhomme:

I don't really know what to do. I've entered the (above) relevant entries and I'm still not getting any mails. As I'm a developer myself I might give it a go to check out the DenyHost source, especially the mail part, and have it write to a log file if it errors. But perhaps it already does? (It seems to be a pretty solid script by now) I think we need information about the error which is given to solve this.

In my case the SMTP-server doesn't even require authentication. So it should be really simple. Still, nothing.

---

### Post by kentl on 2007-08-30
I've examined the Python source code for DenyHosts, even though I don't know Python. ;-)

Anyway. It seems like it's using smtplib to do the mail sending. I found an example of sending mail through Python using this library: [http://www.eskimo.com/~jet/python/examples/mail/smtp1.html](http://www.eskimo.com/~jet/python/examples/mail/smtp1.html)

That example contains no error handling. If something goes wrong I guess you'll get a trace of the method calls and some kind of error indicator. It might be sufficient to understand why it doesn't work.

Please beat me to it if you want to. And then tell me. I won't have time to dig into this until perhaps tomorrow. :-)

---

