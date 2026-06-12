---
title: "email doesn't work using postfix/dovecot on Ubuntu 8.04 server"
date: 2008-06-16
forum: Server Platforms
---

### Post by linuxrrules on 2008-06-16
I spent many hours installing/configuring Postfix, Dovecot, and the Mail Filtering packages using the Ubuntu server guides on [http://help.ubuntu.com/8.04/serverguides/](http://help.ubuntu.com/8.04/serverguides/).  I have learned a lot but I still have nothing working.  All tests in the guides that it says to do pass successfully.

My test client is on Thunderbird.  The problem is that I cannot receive or send email from the account. 

This is what /var/log/mail.err (and /var/log/mail.warn) reads -

Jun 15 19:48:12 www amavis[16348]: (16348-01) (!!)ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/amavis-20080615T194812-16348/parts: lstat() failed. ERROR\n
Jun 15 19:48:12 www amavis[16348]: (16348-01) (!!)WARN: all primary virus scanners failed, considering backups
Jun 15 19:48:12 www amavis[16348]: (16348-01) (!!)TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED: 
Jun 15 19:48:39 www amavis[16345]: (16345-02) (!!)ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/amavis-20080615T194839-16345/parts: lstat() failed. ERROR\n
Jun 15 19:48:39 www amavis[16345]: (16345-02) (!!)WARN: all primary virus scanners failed, considering backups
Jun 15 19:48:39 www amavis[16345]: (16345-02) (!!)TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED: 
Jun 15 19:53:40 www amavis[16348]: (16348-02) (!!)ask_av (ClamAV-clamd) FAILED - unexpected result: /var/lib/amavis/tmp/amavis-20080615T195339-16348/parts: lstat() failed. ERROR\n
Jun 15 19:53:40 www amavis[16348]: (16348-02) (!!)WARN: all primary virus scanners failed, considering backups
Jun 15 19:53:40 www amavis[16348]: (16348-02) (!!)TROUBLE in check_mail: virus_scan FAILED: virus_scan: ALL VIRUS SCANNERS FAILED: 

Obviously their is a problem with amavis, ClamAV-clamd, etc. but this only has to do with the Mail filtering portion of the setup.  I can't see how this would be preventing me from sending or receiving email.

included is my /etc/postfix/main.cf file:

included is my /etc/dovecot/dovecot.conf file (in 3 files, because the total size of the file exceeded the 19.5KB limit)

I have Thunderbird setup as follows:

For POP Mail Server
Server name: mail.example.com
User Name: test
Use secure connection: TLS, if available

For Outgoing SMTP Settings
Server Name: mail.example.com
User Name: test

When I try to get mail, it says that there are no new messages on the server.  However, through an external email address I sent an email to my [email]test@example.com[/email] and there was no bounce back email saying that mail could not be delivered to that address.

When I try to send an email from [email]test@example.com[/email] to an external email address I continually get prompted to enter my mail server password.  The prompting never stops despite me entering my password.

Any help would be hugely appreciated.

---

### Post by windependence on 2008-06-16
You need to fix clamav. 

What is the output of:

sudo ps aux | grep clamd

Since your mail cannot be delivered unless it is checked for virii, you will not be able to get mail until this is fixed.

-Tim

---

### Post by linuxrrules on 2008-06-16
Tim, thanks for your response.

> sudo ps aux | grep clamd

user      3141  0.0  0.0   3004   764 pts/0    R+   06:30   0:00 grep clamd
clamav    4773  0.0  2.1  63748 45512 ?        Ss   Jun15   0:22 /usr/sbin/clamd

Something that might be relevant to this is when I tried to install dkim-filter from [https://help.ubuntu.com/8.04/severguide/C/mail-filtering.html](https://help.ubuntu.com/8.04/severguide/C/mail-filtering.html) via the command:

user@www:~$ sudo apt-get install dkim-filter python-policyd-spf 

I got the following output:

user@www:~$ sudo apt-get install dkim-filter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dkim-filter
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/236kB of archives.
After this operation, 594kB of additional disk space will be used.
Selecting previously deselected package dkim-filter.
(Reading database ... 24051 files and directories currently installed.)
Unpacking dkim-filter (from .../dkim-filter_2.5.4.dfsg-0ubuntu2_i386.deb) ...
Setting up dkim-filter (2.5.4.dfsg-0ubuntu2) ...
adduser: Warning: The home directory `/var/run/dkim-filter' does not belong to the user you are currently creating.
Starting DKIM Filter: dkim-filter: /etc/dkim-filter.conf: at least one selector and key required for signing mode
invoke-rc.d: initscript dkim-filter, action "start" failed.
dpkg: error processing dkim-filter (--configure):
 subprocess post-installation script returned error exit status 78
Errors were encountered while processing:
 dkim-filter
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@www:~$

------------------------------------------------------------------------- 

I researched this error on google and discovered that it is a current Ubuntu bug that has not been fixed yet- [https://bugs.launchpad.net/ubuntu/+source/dkim-milter/+bug/228877](https://bugs.launchpad.net/ubuntu/+source/dkim-milter/+bug/228877).  I then did a 'sudo apt-get remove --purge dkim-filter' to remove it.  I am not sure if not having the dkim-filter package installed is causing my clamav problems.

---

### Post by linuxrrules on 2008-06-18
The dkim-filter bug got fixed and I installed it successfully.  It did not fix my clamav errors.  Not surprising.  I am going to continue to search on why I am getting these mysterious errors and will report back.

---

### Post by windependence on 2008-06-18
> **linuxrrules said:**
> The dkim-filter bug got fixed and I installed it successfully.  It did not fix my clamav errors.  Not surprising.  I am going to continue to search on why I am getting these mysterious errors and will report back.

Good deal, let us know what you find out.

-Tim

---

### Post by Fejker on 2008-06-18
I've been fighting with my mail server on Ubuntu 8.04 too. I've followed a bunch of tutorials but had no success.
The farthest I came was that mail sent to the @fejker.net addresses (my mail server address) was kept in a queue in postfix but would not get delivered. I could see the messages in queue in the webmin online interface but they would just remain there even if I clicked the "Flush queue" button.

Is there any other way to get a simple mail server running? I can remember setting up a mail server in Windows with just a couple of clicks. This is costing me too much time.

---

### Post by cviniciusm on 2008-06-21
Hello,

In the main.cf:
"mydestination = [www.example.com](www.example.com), localhost.example.com, example.com (example is our name)"

I think the part " (example is our name)" is a typo. Do you have the process "master" running?

What's the output of "$ postconf | grep -i mydestination" ?


Regards,
cviniciusm.

---

### Post by Fejker on 2008-06-22
```
postconf | grep -i mydestination
mydestination = mail.fejker.net, localhost.fejker.net, localhost.localdomain, localhost
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks
relay_domains = $mydestination
```

---

### Post by cviniciusm on 2008-06-22
Hello,

I think you should include your domain to the list.

It was my early mistake too. I forgot to include my domain to the mydestination.


Regards,
cviniciusm.

---

### Post by Fejker on 2008-06-22
I did that but still nothing. I think my configuration is screwed up from trying so many tutorials. :(

Is there any way to wipe it clean and start from scratch?

---

### Post by kuam on 2008-07-01
I ran into this issue today after following the installation instruction found on [http://help.ubuntu.com](http://help.ubuntu.com).  Here's what I did to resolve the problem:

1)  As stated in the install doc, I issued this from the command line:

   sudo chmod -R 775 /var/lib/amavis/tmp

2)  In /etc/group, make sure that your setup is similar to this:

   clamav:x:120:amavis
   amavis:x:121:clamav

For me, "clamav" was not in the "amavis" group.

Note: the ubuntu forum replaced the colon (:) and "x" as an angry face.

---

### Post by windependence on 2008-07-02
> **kuam said:**
> 

Note: the ubuntu forum replaced the colon (:) and "x" as an angry face.

In the future, you can avoid that by enclosing your code in code tags. [CODE]

-Tim

---

