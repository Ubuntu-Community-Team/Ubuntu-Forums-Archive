---
title: "Citadel sucks"
date: 2008-05-22
forum: Server Platforms
---

### Post by cdenley on 2008-05-22
I have been trying to set up a Citadel mail server, but I'm having problems. First of all, I'm using external accounting so I can use an LDAP server for authentication. However, when a new user logs into webcit, it fails to log them in the first time, and the error is nothing but part or sometimes all of their password! I can work around this, making sure the citadel account is created after I set them up in the LDAP server.

There was no way of disabling the chat or instant messaging features. I was able to work around this with some creative apache configuration.
```

ProxyPass /chat http://127.0.0.1:81/
ProxyPassReverse /chat http://127.0.0.1:81/
ProxyPass /page_user http://127.0.0.1:81/
ProxyPassReverse /page_user http://127.0.0.1:81/
ProxyPass /who http://127.0.0.1:81/
ProxyPassReverse /who http://127.0.0.1:81/
ProxyPass /denied.jpg http://127.0.0.1:81/denied.jpg
ProxyPassReverse /denied.jpg http://127.0.0.1:81/denied.jpg
ProxyPass / http://127.0.0.1:8504/
ProxyPassReverse / http://127.0.0.1:8504/

```
Now I'm trying to use the per-user sieve filter to move spam into a certain folder using webcit. I have spamassassin configured with postfix, so the spam mail goes to the user's inbox flagged as spam in the message header. I can't get the x-spam-flag or x-spam-status conditions to work with the rule-builder. Whenever I create a custom sieve script, it says it saves, but then it isn't listed in the "add or delete" menu. If I try to edit it, it is empty.

Does anyone have any ideas for possible solutions or troubleshooting steps? Does anyone recommend a reliable alternative to citadel? Something that will work with an outlook connector, and preferably something that integrates well with evolution.

I'm using Citadel 7.35.

---

### Post by HermanAB on 2008-05-22
I've been running Citadel reliably for a long time. It works purrrfectly.

I suggest that you go to the Citadel web site and use the Easy Install script to install it.  Once it is working, then you can try to modify it.

Cheers,

Herman

---

### Post by windependence on 2008-05-22
What the heck is Citadel?

-Tim

---

### Post by cdenley on 2008-05-22
> **HermanAB said:**
> I've been running Citadel reliably for a long time. It works purrrfectly.

I suggest that you go to the Citadel web site and use the Easy Install script to install it.  Once it is working, then you can try to modify it.

Cheers,

Herman
It was working, except for the problems I mentioned. I tried purging/reinstalling, but had the same problems. I tried purging, then using the easyinstall script as you suggested, but it's even worse. Not only do I have the same problems, but I can't get external accounting to work. The users get created in citadel, but it keeps telling me it's the wrong password. 

Now I can't get the debian install working either! I reinstalled through apt several times and never had this problem until the easyinstall. Any ideas? The LDAP server and PAM are still working fine.

Do you use external accounting? What version are you running? Have you tried writing then editing sieve filter scripts?

---

### Post by cdenley on 2008-05-22
I got an answer from their BBS uncensored support room.
> 
there was a bug which is fixed now. please hang on for it to be released within the next days. 

I guess my main original issue is in the process of being fixed, but now I still have to get authentication working again.

---

### Post by cdenley on 2008-05-23
I finally got it working again by deleting /etc/pam.d/citadel. Hopefully their upcoming release will fix my sieve filter problems, and maybe it will even stop printing my password in the web browser the first time I try logging in.

---

### Post by quietas on 2008-05-23
I've used Citadel a bit and never liked the nearly ancient web BBS style it still uses. Heck, I remember in 1993 dialing up to better laid out text only BBS's over a 9600 baud modem.

If you want a decent layout, good tech, and easy to use/admin, take a look at Zimbra.

---

### Post by HermanAB on 2008-05-23
> **quietas said:**
> I've used Citadel a bit and never liked the nearly ancient web BBS style it still uses. Heck, I remember in 1993 dialing up to better laid out text only BBS's over a 9600 baud modem.

If you want a decent layout, good tech, and easy to use/admin, take a look at Zimbra.

If your concern is only a matter of looks, try the Blue Citadel theme.  

The nice thing about Citadel, it that it "Just Works" (TM).  It is hard to beat that feature.

---

### Post by cdenley on 2008-06-02
The sieve filter in webcit still doesn't seem to work in 7.36. I upgraded using the debian packages. I still couldn't filter using the x-spam-status or x-spam-flag rules. I couldn't seem to get the script editor to work, either. After I saved a script, if I went back to edit it, it was blank. The script didn't seem to work, either. I thought maybe I needed to start fresh and clear all my data from 7.35.

```
dpkg -P citadel-client citadel-common citadel-server citadel-webcit citadel-mta libcitadel1
rm -rf /var/lib/citadel /etc/citadel /usr/share/citadel-webcit /var/run/citadel
apt-get install citadel-client citadel-common citadel-server citadel-webcit libcitadel1
```

In webcit, I entered my username and password, and I assume it created a citadel account (I'm using external accounting). I entered the admin username and password, same thing. I logged in as the admin, and I got an error saying it couldn't connect to the mail server or something. Then I noticed my computer was beeping indefinitely because of the ssh terminal I had connected to the citadel server. The terminal was unusable
```
Message from syslogd@citadel at Mon Jun  2 11:12:44 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:44 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:44 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at M on Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel last message repeated 12 times

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

Message from syslogd@citadel at Mon Jun  2 11:12:46 2008 ...
citadel last message repeated 7 times
```

 I rebooted, and had the same problem immediately. I could probably disable citadel using a rescue cd, purge it, then start fresh, but I'm not going to bother unless someone has some ideas to get filtering to work.

---

### Post by HermanAB on 2008-06-02
I think you need to upgrade to the latest version of Citadel.  I've been using filters for several months, so I don't know how old your version is.

The default install with Easy Install works perfectly good.  The trouble with changing things is that you are then on your own with a unique system that is practically unmaintainable.

If you used Easy Install, then upgrading is as simple as running it again.  If you haven't used Easy Install, then you now know why you should.

---

### Post by cdenley on 2008-06-02
I tried upgrading to 7.36. I think it was just released Friday, and the debian packages compiled over the weekend. I tried 7.35 using the debian packages and the easyinstall. Same problem. I think I'm going to give up on citadel and try zimbra. Based on my experience, citadel is not a good solution for critical business implementation. Apparently I'm not the only one that had the new release get caught in a panic loop. Maybe you're using an older, stable release, or the problem only happens with host-based authentication.

Just to clarify, what kind of filtering are you doing? Can you filter based on spam score? Have you successfully created custom scripts? Can you edit the script after you save it? What version are you running?

---

### Post by windependence on 2008-06-02
> **cdenley said:**
> I tried upgrading to 7.36. I think it was just released Friday, and the debian packages compiled over the weekend. I tried 7.35 using the debian packages and the easyinstall. Same problem. I think I'm going to give up on citadel and try zimbra. Based on my experience, citadel is not a good solution for critical business implementation. Apparently I'm not the only one that had the new release get caught in a panic loop. Maybe you're using an older, stable release, or the problem only happens with host-based authentication.

Just to clarify, what kind of filtering are you doing? Can you filter based on spam score? Have you successfully created custom scripts? Can you edit the script after you save it? What version are you running?

I was going to suggest that. If you need help with Zimbra, before you say it sucks :) please post here and I will help you. Zimbra should be installed on a clean machine, that is nothing else running. Follow the directions to the letter. Oh and 8.04 is not supported so you should load dapper, it works well with that (or CentOS).

-Tim

---

### Post by cdenley on 2008-06-03
> **windependence said:**
> I was going to suggest that. If you need help with Zimbra, before you say it sucks :) please post here and I will help you. Zimbra should be installed on a clean machine, that is nothing else running. Follow the directions to the letter. Oh and 8.04 is not supported so you should load dapper, it works well with that (or CentOS).

-Tim

I figured that title was best to attract the attention of all the citadel fans, because I really wanted it to work. I was hoping to use zimbra with debian etch, but only x86 is supported? I don't want to setup a new server with an OS that is already 2 years old. Since it is still a test server at this point, I'll try the hardy binary.
[https://sourceforge.net/project/showfiles.php?group_id=224243](https://sourceforge.net/project/showfiles.php?group_id=224243)
Hopefully, by the time I want to switch mail servers, it will be supported.

---

### Post by artcancro on 2008-08-31
You'll get better support for Citadel on its own support forum than here.  How quickly that happens depends largely upon the support load at any given time.  Often the developers will release a patch within a day or two if you've actually uncovered a real bug.  The program is built and maintained by a small team that truly believes in open source collaboration.

---

### Post by gtdaqua on 2008-08-31
> **windependence said:**
> 
.......

Oh and 8.04 is not supported so you should load dapper, it works well with that (or CentOS).

-Tim


Zimbra 5.0.9 and above will support Ubuntu 8.04 LTS on both x86 and x64 editions natively. The next best option considering support from these forums will be Debian etch.

---

### Post by cdenley on 2008-09-01
> **artcancro said:**
> You'll get better support for Citadel on its own support forum than here.  How quickly that happens depends largely upon the support load at any given time.  Often the developers will release a patch within a day or two if you've actually uncovered a real bug.  The program is built and maintained by a small team that truly believes in open source collaboration.

I tried their support forum. The most useful reply I got was something like "It is a known bug, be patient". I waited a few weeks, the next release did not fix it. I can't use a server in a production environment that has a serious bug like that go unfixed for at least a month.

Also, when I was trying to write a script to perform some IMAP functions, I accidentally had it authenticate inside a loop. This actually corrupted Citadel's database, and the entire server became unusable. My SSH terminal would give me nothing but beeps, and the local console wouldn't let me log in because it was caught in a infinite loop of errors. Rebooting didn't help. I had to boot to a CD, then purge the corrupt database before I can use my server again. In other words, I accidentally made Citadel completely useless by attacking it remotely with a user account. If I can do this accidentally, I would hate to find out what a malicious user can do intentionally.

> 
Zimbra 5.0.9 and above will support Ubuntu 8.04 LTS on both x86 and x64 editions natively. The next best option considering support from these forums will be Debian etch.

I had been using the community builds, but I recently noticed zimbra was starting to support it. For the network edition, they still emphasize that it is being beta tested.

---

### Post by jamesrfla on 2008-09-02
I have been using citadel and I have had no problems with it. :guitar: I also think it is the easiest mail server to set up for beginners. :)

---

### Post by cdenley on 2008-09-02
> **jamesrfla said:**
> I have been using citadel and I have had no problems with it. :guitar: I also think it is the easiest mail server to set up for beginners. :)

It was pretty easy to set up, but so was zimbra. If you want to give me your IP address, I can see if I can recreate the problem I experienced.

---

### Post by jamesrfla on 2008-09-02
> **cdenley said:**
> It was pretty easy to set up, but so was zimbra. If you want to give me your IP address, I can see if I can recreate the problem I experienced.

Zimbra and citadel have the only best looking web mail interface out there for Linux. I went hear [http://en.wikipedia.org/wiki/Comparison_of_mail_servers](http://en.wikipedia.org/wiki/Comparison_of_mail_servers) and went through all the different mail servers. I would of used zmail but I have to use that for my @embarqmail.com address and I don't want to use the same thing on my mail server at home. So I got citadel instead. :guitar:

---

### Post by windependence on 2008-09-02
> **cdenley said:**
> I tried their support forum. The most useful reply I got was something like "It is a known bug, be patient". I waited a few weeks, the next release did not fix it. I can't use a server in a production environment that has a serious bug like that go unfixed for at least a month.

Also, when I was trying to write a script to perform some IMAP functions, I accidentally had it authenticate inside a loop. This actually corrupted Citadel's database, and the entire server became unusable. My SSH terminal would give me nothing but beeps, and the local console wouldn't let me log in because it was caught in a infinite loop of errors. Rebooting didn't help. I had to boot to a CD, then purge the corrupt database before I can use my server again. In other words, I accidentally made Citadel completely useless by attacking it remotely with a user account. If I can do this accidentally, I would hate to find out what a malicious user can do intentionally.


I had been using the community builds, but I recently noticed zimbra was starting to support it. For the network edition, they still emphasize that it is being beta tested.

Hmmmm.... that is kinda scary. I have been on the fence although I am much more familiar with Zimbra since I have several client installs and they just run, virtually no problems. The only downside is that Zimbra likes to be the only thing on the machine. In my case that isn't a big problem because I run almost everything in a VM, so I just give it it's own VM. I have to say I DO like the Zimbra interface better though.

-Tim

---

### Post by artcancro on 2009-04-16
> **cdenley said:**
> 
Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: 22

Message from syslogd@citadel at Mon Jun  2 11:12:45 2008 ...
citadel citadel: cdb_*: Berkeley DB panic: -30977

As a follow-up to this issue (already discussed on the Citadel support forum but it bears repeating here in case someone lands on this thread after a web search) ... "Berkeley DB panic" errors in Citadel almost always mean that something happened in the underlying system -- either the db got corrupted because the host system ran out of disk space, or files were accidentally deleted, or the system's Berkeley DB library was accidentally downgraded (perhaps because someone installed a bunch of other packages).

In newer versions of Citadel, that last condition is explicitly checked for, and a more helpful error message will be logged.

---

### Post by quietas on 2009-04-16
Give Zimbra a try. I've been running two Zimbra servers now for a year and I will keep using it for years to come. Either that or screw it and get Google Apps for Your Domain. =)

---

### Post by mathman54 on 2009-04-16
> **HermanAB said:**
> If your concern is only a matter of looks, try the Blue Citadel theme.  

The nice thing about Citadel, it that it "Just Works" (TM).  It is hard to beat that feature.

Unfortunately for me it is not working. I just installed it after getting tired of trying to get postfix/whatever working. I get a relay not open message. How can I fix this without spending the next two months trying to get email setup. 
Also I went to a web site called [www.mxtoolbox.com](www.mxtoolbox.com). It says that MXLookup is OK and diagnostics show that everything is good.

---

