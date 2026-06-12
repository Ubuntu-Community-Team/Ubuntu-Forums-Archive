---
title: "Setup Server for automated emails (help)"
date: 2009-04-07
forum: Server Platforms
---

### Post by starr0stealer on 2009-04-07
I have recently installed Ubuntu 8.04, then directly upgraded to Ubuntu 8.10 (8.10 wouldnt install correctly, but upgrade worked)

Now I am wanting to setup a few things to be automated. The first is I would like to set a script to email me when ever the server boots up. So I know that the server is back online after maintenace retuines. I'd also like to setup a script to email me when ever someone logs into SSH. A few other things, but once i get the email working it think i can take it from there.

So my issue, I can't seem to get sendmail to work, I also tried ssmtp. I removed both packages, then just instealled sendmail. Tried running the commands manually. ( sendmail -f "from name" "recipient" ) then type the message, (TO: From etc) but ctrl D wouldnt do anything at all.

I also tried using the mail command, but bash just keeps saying its not known.

I don't want to install a full fledge email server, I dont need to get replies just send out the messages.


I mainly use the server through putty, since its more of a hassle to go into the server room.

---

### Post by Cheesemill on 2009-04-08
Do you already have a mail server set up on a different machine?
If so you can route emails through that, for example we have an Exchange server where I work and the following method works fine for me:

First install the required packages:
```
sudo aptitude install mailutils
```

Then configure exim to relay mails through your existing server:
```
sudo dpkg-reconfigure exim4-config
```

Using the following settings:

General type of mail configuration - Mail sent by smarthost; No local mail
System mail name - Accept default
Listening IP address - 127.0.0.1
Other destinations - Accept default
Visible domain name - Accept default
Host name of outgoing smart host - Enter IP or hostname of your existing mail server
Keep number of DNS queries minimal - No
Split configuration into small files - No


You should now be able to use the mail command to send email.

Cheesemill

---

### Post by wkulecz on 2009-04-08
Install postfix and mailx with apt or synaptic.  Lots of good info about setting up postfix will be found with a google or forum search.

How I set mine up is discussed a bit here:
[http://ubuntuforums.org/showthread.php?t=1097249](http://ubuntuforums.org/showthread.php?t=1097249)

--wally.

---

### Post by starr0stealer on 2009-04-08
i was under the impression that exim4 and postfix were full fledge email servers. Which isnt what I want for this server.

Last night on my VM install of Ubuntu Deskto 8.10, I installed just (heirloom-mailx && sendmail) default configuration, and I was able to get an email to be sent out.

---

### Post by GeeZor on 2009-04-08
Have tried creating a script that just sends out the email?
And after that, creating an entry in /etc/rcX.d to run the script at startup (at whatever runlevel you desire, prob. 2 and up)?

This folder is originally meant to start service but you could abuse it for just causes as well...

Good luck.

---

### Post by starr0stealer on 2009-04-08
That is just the problem. I can't get the server install to send out emails.

---

### Post by starr0stealer on 2009-04-08
This is strange. Since I just installed the server OS last night, I figured I might of messed up some configuration since I was installing and removing mail apps like a mad man. So I reinstalled the server today. First thing I upgraded, then checked for updates. once that was done, I directly ran the following...

```

sudo -i
apt-get install heirloom-mailx
apt-get install sendmail
sendmailconfig

```

Then the send the mail, i typed

```

mail -s "Test Email" myemail@domain.com
Test email content.
This is a second line
.

```

email was sent to be queued up. after about 2 mins. I check the logs.
All it ever says on the server is

```

Apr  8 19:02:01 COMPNAME sm-mta[6468]: n38Mw1a2006466: to=<myemail@domain.com>, ctladdr=<root@COMPNAME> (0/0), delay=00:04:00, xdelay=00:04:00, mailer=esmtp, pri=120499, relay=inbound10.mxlogic.net. [208.65.144.1], dsn=4.0.0, stat=Deferred: Connection timed out with inbound10.mxlogic.net.

```



Now i've done the exact same commands on both my VM install on Windows XP, and my dual boot OS. Both are direct installs of Ubuntu 8.10.
The server was installed 8.04, then upgraded to 8.10.. 



What am I missing? ? ?

---

