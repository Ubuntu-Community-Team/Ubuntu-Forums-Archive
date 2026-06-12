---
title: "Squirrelmail on Ubuntu 10.04: Problem"
date: 2010-05-04
forum: Server Platforms
---

### Post by satishsood1 on 2010-05-04
Hi,
Firstly I am a beginner to Linux/Ubuntu.

_Background_
I have been installing and using squirrelmail on Ubuntu 9.10 successfully. The steps used were as under:-
        1.  Install Ubuntu Server 9.10  with all options checked. Install ubuntu-desktop.
        2.  Install Webmin for GUI
        3.  Rename /var/www/index.html as /var/www/index1.html
        4.  Create /var/www/mail                folder
        5.  Create /var/local/squirrelmail
        6.  Cteare /var/local/squirrelmail/data
        7.  Create /var/local/squirrelmail/attach
        8.  Change ownership of ..../data    and ..../attach  folder as above to www-data
        9.  Run configuration file of squirrelmail
        10. Set servername  server5.local, Set for dovecot settings (predefined).
        11.  Save configuration
        12.  Access the server through web browser
        13.  Click mail, squirrelmail login page appears and everything is functional. It works without any problem.

 _Problem_
However after installing ubuntu server 10.04 and going through all the above steps, the login page appears. When I login, it gives a message "Error: Error Connection dropped by IMAP server".

I do not know whether there are any specific settings for dovecot, squirrelmail or Ubuntu Server 10.04.
Ubuntu server 10.04 must also work without any problems if 9.10 was working.
I tried with evolution mail also. Sending was OK, but the mail could not be received
Therefore, for email server with evolutionmail/squirrelmail I am back to Ubuntu 9.10 till such time it is resolved.

Any suggestions, please.
Thanks and regards,
Satish

---

### Post by sspence on 2010-05-04
I am not sure if it is related, but since I upgraded to 10.04 a few days ago, my imap is down also.  when I try to start dovecot, I get a message that states

 "Error: Error in configuration file /etc/dovecot/dovecot.conf line 691: Unknown setting: sieve"

Everything worked great until I upgraded.  I am not exactly sure what sieve is, but I seen something on the release notes about sieve, but it does not appear to apply to this.

Thanks,

---

### Post by jmkemp on 2010-05-05
I've got a problem with IMAP since the upgrade, and I'm certain it is down to the upgrade from 9.10 to 10.04. 

It is a dovecot problem and the error message in /var/log/mail.log is as follows:


May  5 19:43:57 localhost dovecot: deliver(james@themself.org): Loading modules from directory: /usr/lib/dovecot/modules/lda
May  5 19:43:57 localhost dovecot: deliver(james@themself.org): Fatal: Plugin cmusieve not found from directory /usr/lib/dovecot/modules/lda
May  5 19:43:57 localhost postfix/pipe[5308]: B9D8025C150: to=<james@themself.org>, relay=dovecot, delay=574, delays=574/0.29/0/0.02, dsn=4.3.0, status=deferred (temporary failure)

I'll go look at launchpad in a minute to see if I can find the solution to the problem. Thought I'd mention it here too given the thread already exists. 

My mail solution is postfix, dovecot and roundcube for webmail. Also got virtual users and mailboxes through MySQL using a variation on the howto.

---

### Post by jmkemp on 2010-05-05
I just spotted some helpful clues over in another thread [http://ubuntuforums.org/showthread.php?t=1465608]("http://ubuntuforums.org/showthread.php?t=1465608")

It seems the upgrade does something odd to the dovecot.conf

---

### Post by timothy_tim on 2010-05-05
I don't know if the default configuration of Squirrelmail uses Sieve, but that could just be the problem.
From the posts of sspence and jmkemp, I concluded that the Sieve plug-in is no longer installed with the default installation of Dovecot. The techspecs page isn't yet updated so I can't validate my assumption.[1] In that matter Postfix would not startup because it's relaying on a plug-in that's missing.
Maybe you could check if the Sieve plug-in is installed on your system.[2]

Hope this helps.

[1] [http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/](http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/)
[2] [http://wiki.dovecot.org/LDA/Sieve](http://wiki.dovecot.org/LDA/Sieve)

---

### Post by jmkemp on 2010-05-06
Having spent a few hours yesterday evening poking about I realised that I had two problems from the upgrade. 

1) dovecot has changed and it isn't adequately documented and/or the installer does odd things. There is some additional info on the [launchpad bug report]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/516040")

The solution is that you need to edit /etc/dovecot/dovecot.conf to move the sieve settings into the plugin{} section. The linked page on the dovecot wiki in the other thread tells you what you need to do, but in summary you also need to change the ssl_disable=no setting to ssl=yes [or your chosen values] and perhaps also change a couple of the other settings that have been re-named or discontinued. 

You also need to remove reference to cmusieve and replace with sieve. In your sieve files you will need to change a few of the require flags, notable imapflags becomes imap4flags and notify becomes enotify. More details are on the dovecot wiki. 

If you get error messages when attempting to re-start  dovecot then they will tell you which settings you need to change (this happens serially, only the first error is reported to stdout).

Once you have edited dovecot.conf you can copy it to conf.d/01-dovecot-postfix.conf (which the installer helpfully turns into a backup version silently). This is ubuntu now using the dovecot-postfix.conf file and moving it to a sub-folder (as it turned out not to be working previously). 

2) my other issue was that the grub upgrade resulted in one of my disks being mounted ro, but a fsck -y sorted that problem out easily enough (but took over an hour to do it). 

Hope this helps others sort out their own issues.

---

