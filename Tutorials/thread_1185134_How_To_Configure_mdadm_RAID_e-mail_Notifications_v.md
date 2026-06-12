---
title: "How To Configure mdadm RAID e-mail Notifications via ISP SMTP Using msmtp"
date: 2009-06-11
forum: Tutorials
---

### Post by fermulator on 2009-06-11
This tutorial will assist a home server administrator to configure mdadm e-mail notifications without a full fledged MTA (such as postfix or exim).

Estimated Time: 1 hour

**_My Goals:_**
 * If a drive fails in any of my RAID arrays, I'd like to be notified by e-mail.  The server should tell me, I shouldn't have to go looking for failures.
 * E-mail configuring should be as simple as possible, and should authenticate against my ISP's SMTP server.  I don't want to have to configure a full Mail Transfer Agent (MTA).

**_Disclaimer:_**
 * I take no responsibility if, after following these guidelines, your server fails to notify you by e-mail of a failed drive.  This tutorial is accurate to the best of my knowledge, and has been tested to work, but use at your own risk.  If you have important or critical data, and you're not completely comfortable with linux server administration, please, get a professional to setup your RAID.

**_Caveats:_**
 * I'm obviously running a particular setup and distro, but hopefully one could take this instructions and apply them to their own configuration as needed.

**_System Specs:_**
 * Ubuntu 10.04.4 LTS Server (2.6.32-44-generic-pae)
 * mdadm v2.6.7.1
 * msmtp 1.4.19
 * 3x RAID Arrays : /dev/md250 (3x250GB), /dev/md500 (5x500GB), /dev/md1000 (4x1TB)

**_Preconditions & Assumptions:_**
I assume here that you have a working server, with a working RAID device already configured.  This tutorial does not cover how to setup or configure RAID, but instead how to configure e-mail notifications for an already working mdadm RAID array.

**_Background Information:_**
 * Firstly.  How does e-mail work?  View the operations and diagram from wikipedia [here]("http://en.wikipedia.org/wiki/Email#Operation_overview").
 * Secondly, here's what our pieces of the puzzle are for e-mail:
> MUA (the client): msmtp (a sendmail compatible interface)
MTA (the mail server): your isp or gmail
MSA (smtp middle man): msmtp (a simple MTA that gets mail from your local MTA to your real MTA or mailhub)
 * As you can see, to simplify things, we'll be using msmtp as both the MUA and the MSA.
 * mdadm e-mail notification by default looks for /usr/sbin/sendmail.

_**Process the First - Installing and Configuring the MSA (msmtp)**_

So firstly, we need to install msmtp.  On ubuntu, this is trivial:
```
sudo apt-get install msmtp msmtp-mta
```

Now it's time to configure.  There are two methods for msmtp configuration; system wide, and user base.  We're interested in a system wide configuration which will apply to all users, unless otherwise overrided by a user's own msmtp configuration file.

At the time of writing, the version of msmtp I was using denoted that the system-wide configuration file was **/etc/msmtprc**. It is recommended for you to confirm the same via *msmtp --version*:
> $ msmtp --version | grep "System configuration"
System configuration file name: /etc/msmtprc


Here is a sample system configuration file:

```
sudo nano /etc/msmtprc
```
> # ------------------------------------------------------------------------------
#  msmtp System Wide Configuration file
# ------------------------------------------------------------------------------

# A system wide configuration is optional.
# If it exists, it usually defines a default account.
# This allows msmtp to be used like /usr/sbin/sendmail.

# ------------------------------------------------------------------------------
#  Accounts
# ------------------------------------------------------------------------------

# Sympatico Account
account sympatico
host smtphm.sympatico.ca
from [email]noreply@yourserver.name[/email]
tls on
tls_starttls on
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on
user [email]valid_email@bell.net[/email]
password ********
syslog LOG_MAIL

# Rogers Account
account rogers
host smtp.broadband.rogers.com
port 587
from [email]noreply@yourserver.name[/email]
auth login
user [email]valid_email@rogers.com[/email]
password ********
syslog LOG_MAIL

# gmail account
# Configuring for gmail is beyond the scope of this tutorial
# Googling for "gmail msmtp" should help
account gmail
host smtp.gmail.com
port 587
from [email]noreply@yourserver.name[/email]
tls on
tls_starttls on
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on
user <username>
password ********
syslog LOG_MAIL


# Other ISP Account
# Configuring for other ISPs is beyond the scope of this tutorial
# Googling for "myisp outlook smtp" should help

# ------------------------------------------------------------------------------
#  Configurations
# ------------------------------------------------------------------------------

# Construct envelope-from addresses of the form "user@oursite.example".
#auto_from on
#maildomain fermmy.server

# Use TLS.
#tls on
#tls_trust_file /etc/ssl/certs/ca-certificates.crt

# Syslog logging with facility LOG_MAIL instead of the default LOG_USER.
# Must be done within "account" sub-section above
#syslog LOG_MAIL

# Set a default account
account default : rogers

# ------------------------------------------------------------------------------

Save and close this file.

See [http://msmtp.sourceforge.net/doc/msmtp.html#Configuration-files](http://msmtp.sourceforge.net/doc/msmtp.html#Configuration-files) for additional details.

Now it's time to test that e-mail works!  First, we'll run a "pretend test" to make sure the settings we've just configured have taken affect.

```
msmtp --pretend
```

Verify the output is correct as best as you know it to be.

Now, we'll try an actual test.

```
echo "This is a test e-mail from my server using msmtp" | msmtp -d youremail@domain.com
```

If all went well, you should receive an e-mail very shortly!

If things didn't go well, you can check the mail log files (/var/log/mail.log) for hints as to what went wrong, or perhaps even the msmtp executable will spit out some useful errors.

**_Step the Second - Installing and Configuring our MUA ("sendmail")_**

Now, as per the [homepage of msmtp]("http://http://msmtp.sourceforge.net/"), msmtp is a "Sendmail compatible interface (command line options and exit codes)."

This is exciting because it means that if msmtp is compatible with sendmail commands and exit codes, we can simply use msmtp as our e-mail command line executable.

*NEW*
[LIST]
[*]Feedback from other users, and I personally tested on Ubuntu 10.04 LTS, has yielded that installing *msmtp-mta* performs the proper sendmail linkage automatically for us. Since this was part of the installation instructions above, we can proceed *without* this next code block.
[*]Should something go wrong with mdadm sending e-mail via "sendmail", please consider manually over-riding the sendmail symlink to msmtp as follows:
[/LIST]
```
sudo mv /usr/sbin/sendmail /usr/sbin/sendmail.bak
sudo ln -s /usr/bin/msmtp /usr/sbin/sendmail
```

*FEEDBACK REQUESTED*
[LIST]
[*]If you performed this how to, and *did not* require the manual sendmail symlink, please reply to this thread confirming. Thanks.
[/LIST]

**_Step the Third - Configuring MDADM for e-mail notifications_**

Edit the mdadm configuration file:
```
sudo nano /etc/mdadm/mdadm.conf
```
NOTE:  Most distributions expect the mdadm.conf file in /etc/, not /etc/mdadm.  I believe this is a "ubuntu-ism" to have it as /etc/mdadm/mdadm.conf.

I'll avoid details about the DEVICE declarations and such that might already exist in this configuration file, and instead we'll focus on the MAIL options.  If you're interested in more details on the mdadm.conf, check the man page here: [http://man-wiki.net/index.php/5:mdadm.conf](http://man-wiki.net/index.php/5:mdadm.conf).

> # instruct the monitoring daemon where to send mail alerts
MAILADDR [email]youremail@domain.com[/email]
MAILFROM my-server-name - mdadm


Save and close this file.

That's it!

Let's run a simple test from mdadm to ensure e-mail notifications are working.  If you have DEVICE declarations in your mdadm.conf file, use the following command:
```
sudo mdadm --monitor --scan --test --oneshot
```
This should deliver an e-mail, scanning all devices found in mdadm.conf.

If you rely on mdadm scanning your partitions for RAID devices, you'll want to specify the devices (usually found as /dev/md###):

```
sudo mdadm --monitor --scan --test --oneshot /dev/md[[:digit:]]*
```
This should deliver an e-mail, with the results from /proc/mdstat.  The "/dev/md[[:digit:]]*" portion of the command should match all RAID devices starting with "md" for you automatically.

I then received the following e-mail (actually x3, one for each of my arrays because I have 3):
> -------- Original Message --------
From: my-server-name - mdadm
Sent: Sat 18 May 2013 09:39:59 PM EDT
To: [email]myemail@domain.com[/email]
Cc: Subject: TestMessage event on /dev/md640:my-server-name

This is an automatically generated mail message from mdadm
running on fermmy-server

A TestMessage event had been detected on md device /dev/md640.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2000 : active raid6 sdl1[1] sdn1[3] sdk1[0] sdm1[2] sdj1[5] sdi1[4]
      7814053632 blocks super 1.1 level 6, 64k chunk, algorithm 2 [6/6] [UUUUUU]
      
md1001 : active raid1 sda1[1] sdb1[0]
      9764800 blocks [2/2] [UU]
      
md250 : active raid1 sdb3[0] sda3[1]
      233392960 blocks [2/2] [UU]
      
md1002 : active raid1 sda2[1] sdb2[0]
      1952704 blocks [2/2] [UU]
      
md1000 : active raid5 sdd1[0] sde1[1] sdc1[3] sdf1[2]
      2930279808 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
md640 : active raid1 sdh1[0] sdg1[1]
      625130708 blocks super 1.1 [2/2] [UU]
      
unused devices: <none>

**_Step the Fourth - Configuring MDADM for Monitoring_**

At this stage of the game, you're (hopefully) almost done!  The only part left is to ensure that your linux distribution is already monitoring your RAID array, and if it's not, configure it yourself.

In short, a "monitor" mdadm process must always be running which periodically checks the status of your array(s).  This is typical of any RAID system.  It's my understanding that the mdadm monitor will send out e-mail alerts on the following events:
> Fail, FailSpare, DegradedArray, and TestMessage
These events really are the only things we would typically care to receive an e-mail about.  Good.

Now, a typical mdadm monitoring mode process command might like like:
```
mdadm --monitor --scan --daemonize --test --syslog (/dev/md[[:digit:]]*)
```

Let's break down the above command:
 * --monitor --> Sets the mdadm process to "Monitor Mode".
 * --scan --> Scans the mdadm.conf file for RAID DEVICES.
 * --daemonize --> This process should be treated as a daemon.
 * --test --> On system startup, send out test e-mail(s).
 * --syslog --> Log to the system log (/var/logs/syslog)
 * The last portion is optional(?) for those who don't have devices defined in the RAID configuration file.

For addition details on mdadm monitor mode, try **mdadm --monitor --help** or review the man file for monitor mode at [http://man-wiki.net/index.php/8:mdadm#For_Monitor_mode:](http://man-wiki.net/index.php/8:mdadm#For_Monitor_mode:).

For my case in particular, Ubuntu 10.04, the monitoring of all RAID arrays had already been implemented, and started on system startup.  This was realized by the file */etc/init.d/mdadm*, and it's debian configuration options defined in */etc/default/mdadm*.

I prefer to have a test e-mail on startup, so in the /etc/default/mdadm option file, I changed
> DAEMON_OPTIONS="--syslog"
to
> DAEMON_OPTIONS="--syslog --test"
or (OPTIONAL)
> DAEMON_OPTIONS="--syslog --test (/dev/md[[:digit:]]*)"

NOTE:  As per the beginning of "Step the Fourth", if you don't have any devices defined in your mdadm.conf configuration file, you need to suffix the DAEMON_OPTIONS with "(/dev/md[[:digit:]]*)"

To verify that the mdadm monitor process is actually running, try:
```
ps aux | grep mdadm
```
Result in my case, showing the monitor process is already running:
> root      6230  0.0  0.0   2160   600 ?        Ss   May29   0:04 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog --test
or (OPTIONAL)
> root     21021  0.0  0.0   2160   584 ?        Ss   20:12   0:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog --test /dev/md1000 /dev/md250 /dev/md500

If your linux distribution doesn't already have the mdadm monitoring daemon, you'll have to configure this yourself, but I'm afraid this is beyond the scope of this tutorial.  I suggest Googling "mdadm monitor daemon" for help, and in particular, this is useful: [http://linux-raid.osdl.org/index.php/Detecting,_querying_and_testing#Monitoring_RAID_arrays](http://linux-raid.osdl.org/index.php/Detecting,_querying_and_testing#Monitoring_RAID_arrays).

Good luck!  Once you know a mdadm monitor daemon is running, you can simulate a failure to verify that the system *will indeed* e-mail you, which is what we're after right?
 * I found this website very useful: [http://linux-raid.osdl.org/index.php/Detecting,_querying_and_testing#Simulating_a_drive_failure](http://linux-raid.osdl.org/index.php/Detecting,_querying_and_testing#Simulating_a_drive_failure)

[SIZE="5"]By this point, you should find comfort in the knowledge that your server will tell YOU when a drive fails! :-)[/SIZE]

**_Credits:_**

This tutorial was created from me conducting research, trial and error, and from some specific content from a few different pages, so I want to give credit where credit is due!
 * [http://www.novell.com/support/viewContent.do?externalId=7001034&sliceId=1](http://www.novell.com/support/viewContent.do?externalId=7001034&sliceId=1)
 * [http://ubuntuforums.org/showthread.php?t=780509&highlight=msmtp](http://ubuntuforums.org/showthread.php?t=780509&highlight=msmtp)

---

### Post by iBurger on 2009-10-14
Thank you! This is exactly what I was looking for.!! :)

---

### Post by tjhart85 on 2009-10-15
Thanks for this!  This is exactly what I needed!

---

### Post by danger89 on 2010-07-12
Everything works OK, also send e-mail using msmtp until...


root@server:~# sudo mdadm --monitor --scan --test --oneshot
**sendmail: fatal: open /etc/postfix/main.cf: No such file or directory**

I will get that error message, I think the symlink link didn't work, what to do?

**EDIT:**
I just installed postfix again, could be via:
sudo apt-get install --reinstall postfix

Or first --remove & --purge, then --install

---

### Post by fermulator on 2010-07-14
> **danger89 said:**
> Everything works OK, also send e-mail using msmtp until...


root@server:~# sudo mdadm --monitor --scan --test --oneshot
**sendmail: fatal: open /etc/postfix/main.cf: No such file or directory**

I will get that error message, I think the symlink link didn't work, what to do?

**EDIT:**
I just installed postfix again, could be via:
sudo apt-get install --reinstall postfix

Or first --remove & --purge, then --install

Did that resolve your issue?

---

### Post by lunix- on 2010-07-18
Thanks a lot for sharing your knowledge!  :D

This was a fun howto to complete and it worked like a breeze on my Debian Lenny server.    

This is great stuff for us semi-newbies!!

---

### Post by braincookie on 2010-08-25
Wow, that was a nice one, it worked like a charm on ubuntu Jaunty. I want to point out one minor mistake you made: you estimated it would take one hour to complete this, but with those great explanations, it took me less than 15 minutes ;)

Thanks a lot!

---

### Post by Evil Dax on 2010-09-23
Nice, clean how-to, exacly what I need.
However, somebody's not happy:

> 
dax@fileserver:/$ echo "This is a test." | msmtp -d my@isp

--
*bunch of stuff*
--


<-- 501 5.6.0 Data format error: we do not accept messages without any headers
msmtp: the server did not accept the mail
msmtp: server message: 501 5.6.0 Data format error: we do not accept messages without any headers
msmtp: could not send mail (account default from /etc/msmtprc)



So, can I add a bunch of headers somewhere?

---

### Post by Carlbc18 on 2010-10-12
Works great, exactly what i needed.

---

### Post by joachim.buechse on 2011-01-28
I think the "kosher" way to get the /usr/sbin/sendmail link is to install the package msmtp-mta (which depends on msmtp).

> **fermulator said:**
> 

**_Step the Second - Installing and Configuring our MUA ("sendmail")_**

Now, as per the [homepage of msmtp]("http://http://msmtp.sourceforge.net/"), msmtp is a "Sendmail compatible interface (command line options and exit codes)."

This is exciting because it means that if msmtp is compatible with sendmail commands and exit codes, we can simply use msmtp as our e-mail command line executable.

Create a symlink for sendmail to msmtp:
```
sudo ln -s /usr/bin/msmtp /usr/sbin/sendmail
```

Caveat:  I'm not sure if this is "kosher" in general with the Linux community.  This method worked for me, but if someone has a "proper" solution, I'd be more than happy to hear it.



---

### Post by Rickolati on 2011-03-07
Hi

Thanks for your response, it has been useful so far!!

I do however have one issue...

I think my issue is linked with your statement:
"* mdadm e-mail notification by default looks for /usr/sbin/sendmail."

I can send emails successfully using msmtp but it seems that mdadm still uses sendmail because I can see changes to /etc/postfix/main.cf refelct in /var/log/mail.log.

My mails get bounced back and I think it is because the from field is incorrect. With msmtp I set my from field to [email]myemail@gmail.com[/email] but i cannot do that with main.cf as it sends it as the user I am logged in with i.e. [email]root@myhostname.com[/email]

I have edited the /etc/aliases file with root: [email]myemail@gmail.com[/email] as well.

I am out of ideas now and any help would be appreciated!!

Can I set mdadm so it uses msmtp instead of postfix? I am not sure if I even udnerstand all this correctly, so if I am talking trash, please correct me :)

---

### Post by jacekk015 on 2011-09-15
Instead of install msmtp package, please all of you install msmtp-mta package.
Better do this with sudo aptitude, because you have to remove broken dependency between postfix.
If you do this correct aptitude will install msmtp package and automatically will link sendmail to msmtp.

jk@ubuntu1:/usr/sbin$ ll sendmail
lrwxrwxrwx 1 root root 12 2011-09-15 23:06 sendmail -> ../bin/msmtp*

---

### Post by njparton on 2011-10-28
> **jacekk015 said:**
> Instead of install msmtp package, please all of you install msmtp-mta package.
Better do this with sudo aptitude, because you have to remove broken dependency between postfix.
If you do this correct aptitude will install msmtp package and automatically will link sendmail to msmtp.

jk@ubuntu1:/usr/sbin$ ll sendmail
lrwxrwxrwx 1 root root 12 2011-09-15 23:06 sendmail -> ../bin/msmtp*

I set up my first mdadm array yesterday so would like to set up monitoring and email notifications this evening.  Can anyone verify that the last bit of advice above works (so that I can ignore the symbolic link bit in the original post)?  Thanks

---

### Post by RocKKer on 2012-04-19
> **njparton said:**
> Can anyone verify that the last bit of advice above works (so that I can ignore the symbolic link bit in the original post)?  Thanks

...I know this is an old post, but yes, I can verify it works as described on 11.10.

---

### Post by njparton on 2012-04-20
Great, I have it working in Debian Squeeze too.

---

### Post by martinlindhe on 2012-08-28
Thanks for your great guide. I made this journey on Ubuntu 12.04 LTS, here is my shortened version;

Ubuntu 12.04 does autostart "mdadm" daemon, so i just added a service restart command at the end. I also excluded the "configure a Mail Transfer Agent (MTA)" part.


instructions:

```
sudo nano /etc/mdadm/mdadm.conf
```edit &#8220;MAILADDR&#8221;, be sure to have a sendmail MTA configured (i use ssmtp, orginal poster suggested msmtp. both is used for relaying the mail to a external SMTP server, like gmail)

verify config is working, by running and then check your inbox:

```
sudo mdadm --monitor --scan --test --oneshot
```by default, Ubuntu will auto-start mdadm in daemon mode, see /etc/default/mdadm

To make the changes to  /etc/mdadm/mdadm.conf take place, restart the deamon:

```
sudo service mdadm restart
```

---

### Post by JoeSabido on 2012-12-21
Hello,

Thanks for writing this guide, I found it quite detailed and easy to follow, and it works (Using Ubuntu 12.04.1 64b) except for one thing.

I installed everything as described, performed the mdadm notification tests (which worked), and then proceded to perform a test. I turned the computer off, then I unplugged one of the hard drives and booted up.

I can confirm (using Webmin) that mdadm has detected the degraded array, but I received no notification.

If I restart the service (sudo service mdadm restart), then I get a notification on the degraded array. Or if I stop the service, I will get the notification upon service start.

So, if the notifications are being sent on mdadm start, why are they NOT being sent on system boot, when mdadm starts?

Thanks

---

### Post by RobertKH on 2013-03-24
I know this post is old and probably no one really monitors it however I keep getting this error when trying to test my email as described in the first post. msmtp: /etc/msmtprc: line 49: account Gmail not (yet) defined

I did change my password to the app specific password as described earlier as well. When I go into the mail logs, I see this
Mar 24 02:53:38 server-box postfix/sendmail[4354]: fatal: open /etc/postfix/main.cf: No such file or directory
Mar 24 08:25:57 server-box postfix/sendmail[1132]: fatal: open /etc/postfix/main.cf: No such file or directory

Could this be because I have postfix installed? I could remove it as I haven't yet gotten it set up for anything. 
Any ideas?

---

### Post by fermulator on 2013-05-18
Thanks everyone for the feedback!

Since I originally wrote this how-to on Ubuntu 8.04, I have since built a new server, and reconfiguring my RAID monitoring has been long over-due.  I finally got around to it, and edited this how-to accordingly to be updated for Ubuntu 10.04 LTS.  In addition, I have noted the feedback regarding the *proper* way to have msmtp be sendmail (msmtp-mta).

Further feedback on the edited instructions is appreciated.

---

### Post by kb5won on 2014-01-05
Thanks for this write-up!  Worked great, sendmail worked without having to make the links manually.

---

### Post by fermulator on 2014-01-10
> **RobertKH said:**
> I know this post is old and probably no one really monitors it however I keep getting this error when trying to test my email as described in the first post. msmtp: /etc/msmtprc: line 49: account Gmail not (yet) defined

I did change my password to the app specific password as described earlier as well. When I go into the mail logs, I see this
Mar 24 02:53:38 server-box postfix/sendmail[4354]: fatal: open /etc/postfix/main.cf: No such file or directory
Mar 24 08:25:57 server-box postfix/sendmail[1132]: fatal: open /etc/postfix/main.cf: No such file or directory

Could this be because I have postfix installed? I could remove it as I haven't yet gotten it set up for anything. 
Any ideas?

Sorry never tested w/ postfix ... did you miss the "sendmail symlink" trick I noted in the tutorial?

---

### Post by buffy^ on 2014-11-13
When postfix is missing the main.cf it means that the config has not yet been run. Don't bother re-installing it simply run

```

sudo postfix dpkg-reconfigure

```

---

### Post by RobertKH on 2014-11-14
I actually ended up using another SMTP mail sender. It worked pretty well. If I can find the link again I will post it here. Postfix seemed to be harder to set up. I have already gotten emails on changing file sizes as well as a crap line in fstab. Fixed fstab and haven't gotten any other emails since. Apparently it gives me what I was looking for. Thank you for taking the time to answer this old question thought. I appreciate it. Maybe I will give it some time and work with postfix.

---

