---
title: "Need intranet only mail server"
date: 2010-09-20
forum: Server Platforms
---

### Post by LittleLebowski on 2010-09-20
What is the fastest way to set this up?  I tried using CentOS and Squirrelmail/Dovecot and got lost making Dovecot work.  I'm spinning up an Ubuntu 10.4 server VM right now.  I just need a intranet only email server with a webmail frontend.

---

### Post by perspectoff on 2010-09-20
See:

[https://help.ubuntu.com/10.04/serverguide/C/email-services.html](https://help.ubuntu.com/10.04/serverguide/C/email-services.html)

---

### Post by LittleLebowski on 2010-09-20
So, which one would you recommend?

---

### Post by perspectoff on 2010-09-20
> **LittleLebowski said:**
> So, which one would you recommend?

Postfix with Dovecot seems to be the most popular.

However, I use Drupal, which uses Exim4, so had to switch over.

But you're headed down a road, I suspect, that will end at full Groupware solutions. You will not only want shared email, but shared calendars, and shared data folders, etc.

For e-mail alone, I think the most amount of support comes from the Postfix/Dovecot community (and it is the one Ubuntu seems to enable the most), but take some time and look at some groupware servers, too. Groupware is not trivial to set up, but if you have a SOHO for which you are intending the email server, it might be worth your time to research for a few weeks.

Yahoo bought (and uses) Zimbra which was very popular in colleges prior to its purchase by Yahoo. It is a nice groupware solution. I think Comcast and some other big companies uses Zimbra, too. Zimbra has a community edition (not entirely open-source anymore, but free.)

In Europe, Zarafa is very popular and has a very nice interface.

Kolab, written for the German government, is very, very powerful and probably the most robust groupware, although still a bit of a bear to install (IMO). Still, I think Kolab will eventually be the most powerful and reliably open-source groupware solution with the widest compatibility (with Horde web-based access now integrated).

eGroupware has evolved from what I considered a few years ago to be a very rudimentary groupware solution. It is one of the easier groupware solutions to install, IMO, but I haven't used it lately and don't know how competitive it is with the frontrunners. I think it now has corporate support, which is very useful in fostering development progress.

Of course, Google has a wide range of groupware-type solutions which are extremely popular, but I am somewhat against storing my data on Google servers (or anyone else's servers, for that matter), so I have stayed away from Google solutions for groupware.

My links to some Groupware solutions are at:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Groupware](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Groupware)

and

[http://kubuntuguide.org/Lucid#Groupware](http://kubuntuguide.org/Lucid#Groupware)

---

### Post by LittleLebowski on 2010-09-20
I do appreciate the info but I fear I did not clarify myself enough.  This is intranet only.  Just for developers to test emailing from the apps we build and to check emailed updates.  

  If Zimbra is still free, that seems pretty painless, right?

---

### Post by perspectoff on 2010-09-20
> **LittleLebowski said:**
> I do appreciate the info but I fear I did not clarify myself enough.  This is intranet only.  Just for developers to test emailing from the apps we build and to check emailed updates.  

  If Zimbra is still free, that seems pretty painless, right?

I have an Intranet (at work) with 500+ computers, on several different subnets. To me, it functions like a mini-Internet. I think the difference, depending on your Intranet complexity, is in your network boundaries, not in which server package to use.

All good collaborative development projects grow. You will eventually need Subversion repositories to keep track of software changes and versioning, a wiki to store accumulated experience (that email is too fleeting a medium to record), group calendars to co-ordinate meetings, and perhaps even a Teleconferencing server (like BigBlueButton or Dimdim) with multi-user functionality to foster real-time innovation.

All of these can be used in an Intranet fashion or in an Internet fashion. The only difference is whether you use Intranet IP addressing or Internet IP addressing and the network boundaries enforced by your firewalls, DNS servers, and host files.

---

### Post by LittleLebowski on 2010-09-20
I already have a complete infrastructure in place with email, Sharepoint, and Subversion.  I'm just looking for the easiest solution to give my developers what they've requested which is an email server, limited to the intranet with a webmail GUI.  

  Right now, I'm downloading Zimbra.  Dovecot with Squirrelemail was frustrating for my time limitations (spend a lot of my time without internet access due to security constraints).

---

### Post by perspectoff on 2010-09-20
Dovecot, then, as the server?

[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

Maybe even Courier?

If you want something fast and lean, Zimbra may end up being too big for your needs.

I think Ubuntu has a tasksel to ease the installation:

 sudo tasksel --list-tasks

will give you a list of all the servers Ubuntu can install automatically for you. Perhaps even

 sudo tasksel

I think

 sudo tasksel install mail-server

is the direct command to automatically set up Dovecot (with Postfix).

---

### Post by LittleLebowski on 2010-09-20
Not so much lean and mean as "easy to and painless to configure."

  I couldn't even log into Dovecot using a standard install and got not help at linuxquestions.org on it.  I just want something I can set up quickly.

---

### Post by HermanAB on 2010-09-20
The fastest way?  Citadel of course.  The Easy Install script takes about 20 minutes and apt-get citadel a little less.  Alternateively, you can download a pre-configured VM.

---

### Post by scottuss on 2010-09-20
[http://www.turnkeylinux.org/zimbra](http://www.turnkeylinux.org/zimbra)

Super quick and easy

---

