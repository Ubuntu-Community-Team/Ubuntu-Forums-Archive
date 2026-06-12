---
title: "Need help with fail2ban and SASL"
date: 2008-12-10
forum: Security
---

### Post by jakev383 on 2008-12-10
I have Postfix all up and running, and installed fail2ban from source (0.8.3) and need some help blocking random intrusion attempts against pop accounts.  It's a botnet, since the IP changes every day, but it will range from 8 attempts to 100 per day from the same IP before it rotates.
Anyway, here's what I get in my logs:
```

Dec 10 10:34:32 mail4 postfix/smtpd[7688]: warning: 114-44-137-9.dynamic.hinet.net[114.44.137.9]: SASL CRAM-MD5 authentication failed: authentication failure

```

Can someone help me block these?
Thanks in advance!

---

### Post by mgmiller on 2008-12-12
First question is why did you install this from source?  It's in the universe repository (version 0.8.3-2) and will do a better job of updating itself with the rest of your system if you use the one there.

Please consider uninstalling the one you have and using the one installable from synaptic.

That being said, this should help......

I just discovered I had multiple intrusion attempts over vsftp and had to configure my fail2ban to block them.  It's easy, here's what you do.

By default, fail2ban only blocks ssh, you need to configure it to block other services.

1) First create the "jail" file from the provided template:
```
sudo cp /etc/fail2ban/jail.conf jail.local
```2) Next, find the section that refers to the service you want fail2ban to protect by editing the file you just created in step 1:
```
sudo gedit /etc/fail2ban/jail.local
```In your case you want the [postfix] section.  Here is what the default will look like:
```
#
# Mail servers
#

[postfix]

enabled  = false
port     = smtp,ssmtp
filter   = postfix
logpath  = /var/log/mail.log
```Simply change the 
```
enabled = false
```to 
```
enabled = true
```There are also a few other mail settings below these, set these as needed as well.

Save the file.

3) Make sure you add the following command to your System > Preferences > Sessions
On the Startup Programs tab, click Add

In the Name field put:  fail 2 ban
In the command field put: ```
fail2ban-client start
```In the Comment field put: what ever you want to remind you what this program does.  Mine says: blocks failed ssh & ftp logins after 5 attempts

4) Log off and log back on to make sure it auto starts.
(You will see an entry in System > Administration > System Monitor in the Processes tab for "fail2ban-server".)

5) verify that you have configured the settings correctly by running the following command:
```
sudo fail2ban-client status
```This should show you the "jails" you have set up.

For example, here is the output I get.  I need to block ssh and vsftpd.....

```
marty@tux:~$ sudo fail2ban-client status
[sudo] password for marty: 
Status
|- Number of jail:    2
`- Jail list:        vsftpd, ssh
  
```This shows that vsftpd and ssh are being monitored.

All should be well.  

The guy from China that has been banging on my ftp server is now blocked. ](*,)

---

### Post by jakev383 on 2008-12-14
Thanks for your post, but that was not what I needed. I know how to install it (and have a reason for using source, thanks) and have it configured and working. The login attempts I'm trying to block are not caught by fail2ban and I need to write a rule to catch them.
Can anyone offer any help?
Thanks.

---

### Post by mgmiller on 2008-12-14
Sorry, I thought I had an easy fix for you.  

I am curious, why did you install from source instead of the repositories?

You may find some help here:
[http://www.the-art-of-web.com/system/fail2ban-sendmail/](http://www.the-art-of-web.com/system/fail2ban-sendmail/)

---

### Post by jakev383 on 2008-12-18
I'm using source instead of the repo because I'm running fail2ban on several machines - some Ubuntu, some Fedora, some Cent.  I used the source to keep the versioning consistent between them all. I've already run into an issue where an older version of a program didn't have the same config syntax as a newer version, so I made fail2ban uniform across the board.
I ended up with this, which seems to work:
```

failregex = : warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed$
            : warning: [[]::ffff:(?P<host>\S*)[]]: SASL CRAM-MD5 authentication failed: authentication failure$
            : warning: [[]::ffff:(?P<host>\S*)[]]: SASL CRAM-MD5 authentication failed: authentication failure
            : warning: [-._\w]+\[<HOST>\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed: authentication failure$

```

All attempts have been banned for the last couple days. I ended up finding an old posting in a Sourceforge forum that helped me get the regex correct.
Thanks for the replies!

---

