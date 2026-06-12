---
title: "unhappy towards HOWTO writters (Postfix &amp; Dovecot)"
date: 2009-04-04
forum: Testimonials &amp; Experiences
---

### Post by LiQuidAiR on 2009-04-04
I want to post this thread to express my frustration towards the linux community and more directly towards those who write books and howtos on the subject.

I've been trying so hard to learn and read and understand everything I can about server specific things on the Ubuntu operating system and just seem to always run into dead ends.  Or, tutorials I find on the internet are incomplete, poorly written, don't explain enough detail, or don't match the version number of the software I'm working on.  Time and time again, I find, what I thought, was the perfect HOWTO, end up being incomplete.

I figured, hey, go to programmers website and get the installation notes and compability issues straight from the sourcce.  Again, the notes are vague, written so only experienced Linux people can understand (so I think), or there just isn't enough detail.  I'm talking about getting Postfix and Dovecot installed.  I've been to so many websites and so many blogs, or should I say blahs.  The blogs I find for Postfix or Dovecot are regurgitations of previous incomplete howtos.


I have in front of me 30+ pages of how to setup Postfix and Dovecot together.  From the installation notes, they claim getting the two to run is as easy as running apt-get.  The notes tell you step by step what configuration files to open and modify but they don't give you a reason why.  And, getting the separate installations working is not difficult, it's getting them to talk to each other.

And I the only one?  There has to be something I'm missing.  Heck, point me to together Postfix Dovecot HOWTO.

I've been to
WEBSITE postfix.com
WEBSITE wiki.dovecot.com
WEBSITE johnny.chadda.se postfix dovecot mysql 
WEBSITE countless dead end BLOGS (In other words, BLAHS)
BOOK Definitive Guide to Postfix
BOOK Ubuntu Server Administration
BOOK Ubuntu Linux server administrator Novice to Professional


I'm going to revisit the postfix and dovecot website and take better notes. But I have a feeling this isn't going to solve my problem.  

Has anyone else had this issue or has successfully installed the two together?  If you did, How the hell did you do it?  Write a howto, LOL.

---

### Post by albinootje on 2009-04-04
> **LiQuidAiR said:**
>  I'm going to revisit the postfix and dovecot website and take better notes. But I have a feeling this isn't going to solve my problem.  

Has anyone else had this issue or has successfully installed the two together?  If you did, How the hell did you do it?  Write a howto, LOL.

You can write your own howto, and therefore contribute back to the Linux community ;-)

For my work I've used this howto :
[http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL](http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL)
It's for CentOS, but I've "translated" things to Debian, which is what I've used for the mail-server setup.
It was a matter of finding the Debian packages, and back then I had to replace the gid for the group mail working with that howto.

It certainly was not "as easy as apt-get", but I had experience before with postfix and courier-imap and regular (not virtual) email users.

---

### Post by albinootje on 2009-04-04
P.s. I think Postfixadmin rocks, except for it's buggy vacation module a while ago, but perhaps that has been fixed by now.
I've tried Qmail- and vpop-admin, and Vexim in the past, but I like Postfixadmin best!

---

### Post by LiQuidAiR on 2009-04-04
> **albinootje said:**
> You can write your own howto, and therefore contribute back to the Linux community ;-)

For my work I've used this howto :
[http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL](http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL)
It's for CentOS, but I've "translated" things to Debian, which is what I've used for the mail-server setup.
It was a matter of finding the Debian packages, and back then I had to replace the gid for the group mail working with that howto.

It certainly was not "as easy as apt-get", but I had experience before with postfix and courier-imap and regular (not virtual) email users.

I would love to write one.  Or, at least finish one that someone else started.  I'm not going to give up.  When I figure this out and swim thru all the technical writtings, I will post what I discovered and hopefully help out. 

Thank you for your posting.  I'll check that link out.

I'm using:
Ubuntu Server 8.10
Apache2.2
PHP 5
MySQL 5.0+...?
Postfix
PostfixAdmin
Dovecot
BIND9
SSH Server/Client
phpMyAdmin

Hmm..at the point where I can send a test email with Postfix but it can't resolve the receiving MX record.  I can do simple pings to the receiving MX host but Postfix can't.




My god, this has been one hellofah journey.

---

### Post by albinootje on 2009-04-04
> **LiQuidAiR said:**
> I would love to write one.  Or, at least finish one that someone else started.  I'm not going to give up. 

Excellent! :)
> 
Hmm..at the point where I can send a test email with Postfix but it can't resolve the receiving MX record.  I can do simple pings to the receiving MX host but Postfix can't.

Well, but is that host having a proper MX record ?
Try this e.g. :
```

host -t mx www.org  (where www.org is just an example host)

```

For the rest you should know that postfix in Ubuntu or Debian (Postfix in FreeBSD it doesn't do that!) does make a copy of your /etc/resolv.conf and puts it in /var/spool/postfix/etc/ and uses that copy exclusively.

If the resolv.conf in /var/spool/postfix/etc/ is incorrect, then postfix will still suffer from that.
Please verify that also.

---

### Post by LiQuidAiR on 2009-04-04
> **albinootje said:**
> Excellent! :)

Well, but is that host having a proper MX record ?
Try this e.g. :
```

host -t mx www.org  (where www.org is just an example host)

```

For the rest you should know that postfix in Ubuntu or Debian (Postfix in FreeBSD it doesn't do that!) does make a copy of your /etc/resolv.conf and puts it in /var/spool/postfix/etc/ and uses that copy exclusively.

If the resolv.conf in /var/spool/postfix/etc/ is incorrect, then postfix will still suffer from that.
Please verify that also.

You truely are the man!  (right?)  

HAHAHAHA I FIGURED IT OUT!!#~@#~!@#~!

just a few mins ago actually.  I knew it had to do with my BIND9 setup.  I didn't know much about the resolv.conf file as you stated but the way I got it to work was by running sudo apt-get install resolvconf.  That updated the correct files that made the damn thing work!  AHHH.

A successful outbound email test to my gmail account.  THIS IS SICK!

Now to figure out dovecot, :)

---

### Post by LiQuidAiR on 2009-04-05
> **albinootje said:**
> P.s. I think Postfixadmin rocks, except for it's buggy vacation module a while ago, but perhaps that has been fixed by now.
I've tried Qmail- and vpop-admin, and Vexim in the past, but I like Postfixadmin best!

It sure seems to be a good working program.   It's getting the job done.  The interface is simple enough.


I did run into one problem.  When I first ran postfixadmin it returned in invalid domain error.  I found that I had to use MySQL Admin to enter some basic domain information to get it working.  

Then there was a strange headers already sent warning that halted further script execution.  I did a temp fix by just commenting out the lines that were causing the problem :)

I was planning on fixing these errors before I go live.

---

### Post by bodhi.zazen on 2009-04-05
Moved to T&E

---

### Post by hyper_ch on 2009-04-05
Falko's perfect howtos at [http://www.howtoforge.com](http://www.howtoforge.com) --> they just work ;)

---

### Post by LiQuidAiR on 2009-04-05
> **hyper_ch said:**
> Falko's perfect howtos at [http://www.howtoforge.com](http://www.howtoforge.com) --> they just work ;)

Thank you.  I'll take a look.

Have you had any issues with the auth-master directive within the dovecot.conf file?

syslog is returning a file missing or unknown error.

I check /var/run/dovecot/ and the only thing listed is a login file/directory

---

### Post by EnglishSparrow on 2009-04-05
I setup postfix/courier in a few hours...

And I did it from ssh. :)

mail.directoryadmin.info

Now I have my own email w00t!


It's very simple, actually. I can't find the howto again, but google for Debian postfix/courier setup.

---

### Post by albinootje on 2009-04-05
> **LiQuidAiR said:**
>  Have you had any issues with the auth-master directive within the dovecot.conf file?


Which howto(s) are you following ?
I think I've used these in the past :
[http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL](http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL)
[http://www.postfix.org/SASL_README.html#server_dovecot](http://www.postfix.org/SASL_README.html#server_dovecot)

And I think (iirc) the file you're missing is a socket, which really needs the right permissions, and the right permissions on the directory it lives in.

---

### Post by albinootje on 2009-04-05
> **EnglishSparrow said:**
>  It's very simple, actually. I can't find the howto again, but google for Debian postfix/courier setup.
Congrats!
Here's a howto on that on this forum in a long thread :
[http://ubuntuforums.org/showthread.php?t=185913](http://ubuntuforums.org/showthread.php?t=185913)

(But ... I love dovecot+postfix!) :)

---

### Post by LiQuidAiR on 2009-04-05
> **albinootje said:**
> Which howto(s) are you following ?
I think I've used these in the past :
[http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL](http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL)
[http://www.postfix.org/SASL_README.html#server_dovecot](http://www.postfix.org/SASL_README.html#server_dovecot)

And I think (iirc) the file you're missing is a socket, which really needs the right permissions, and the right permissions on the directory it lives in.

I started with a brand new install of Ubuntu server 8.10.  I apt-get installed everything except postfixadmin.  Running apt-get install resolvconf solved one problem (Postfix couldn't resolve MX records).  

after going thru several HOWTO's that were incomplete and didn't seem to offer enough detail I continued to look and found

[http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/](http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/)

The followed this tutorial all the way to till it was time to run a test to see if Postfix and dovecot are working together.

Strangely, I haven't seen anything about auth-master except that it is a socket.  The /var/run/dovecot/ directory is empty.

Could it be that because of user permissions within dovecot.conf are incorrect the socket isn't loaded?  I wouldn't think so.  At least, I just tried running a sudo find / -name auth-mas* command and it returned nothing.

You guys freaking rock!  Now I have the responsibility of giving back to the community just as you are and have.

---

### Post by LiQuidAiR on 2009-04-05
> **EnglishSparrow said:**
> I setup postfix/courier in a few hours...

And I did it from ssh. :)

mail.directoryadmin.info

Now I have my own email w00t!


It's very simple, actually. I can't find the howto again, but google for Debian postfix/courier setup.


That's kewl.  The funny thing about courier and dovecot is I first thought about trying to find the easiest and most widely available MDA and found a few write ups about Dovecot.  So the choice was easy.  Come to find out there is more courier and postfix howto's than the prior.  Oh well.  I choose Dovecot so I want see this project through.

---

### Post by albinootje on 2009-04-05
> **LiQuidAiR said:**
> 
Strangely, I haven't seen anything about auth-master except that it is a socket.  The /var/run/dovecot/ directory is empty.


Here's the relevant part of a mail-server that I run with dovecot+postfixadmin :

```

# relevant part of dovecot.conf

auth default {
  mechanisms = plain
  passdb sql {
    args = /etc/dovecot/dovecot-sql.conf
  }
  userdb sql {
    args = /etc/dovecot/dovecot-sql.conf
  }
  userdb prefetch {
  }
  user = nobody  
  socket listen {
    master {
      path = /var/run/dovecot/auth-master
      mode = 0600 
      user = vmail
      group = mail
    }
    client {
      path = /var/spool/postfix/auth/dovecot
      mode = 0660   
      user = postfix
      group = mail

```
```

 ls -la /var/run/dovecot/auth-master 
srw------- 1 vmail mail 0 Apr  1 05:46 /var/run/dovecot/auth-master

``` 
```

ls -la /var/spool/postfix/
drwxr-xr-x  2 postfix mail      4096 Apr  1 05:46 auth

```
```

ls -la /var/spool/postfix/auth/dovecot 
srw-rw---- 1 postfix mail 0 Apr  1 05:46 /var/spool/postfix/auth/dovecot

```
And.. did I forget something ?

---

### Post by LiQuidAiR on 2009-04-05
> **albinootje said:**
> 
And.. did I forget something ?

Mean man.  So mean!  HAHA...

I'm going to change the User and Group ID to what you have..  It looks like you have the exact same setup as me.

let's see

---

### Post by albinootje on 2009-04-05
> **LiQuidAiR said:**
> Mean man.  So mean!  HAHA...

:) I only asked because I was in a hurry, multi-tasking cooking and reading emails and forums increases.. the internal "system load" here.

I'm going to change the User and Group ID to what you have..  It looks like you have the exact same setup as me.

Okay, I'm curious, perhaps it's a good idea to restart both postfix and dovecot after making those changes.

---

### Post by LiQuidAiR on 2009-04-05
No dice.

Apr  5 16:01:57 web01 deliver(joshua@joshdesignonline.com): Can't connect to auth server at /var/run/dovecot/auth-master: No such file or directory
Apr  5 16:01:57 web01 postfix/pipe[9905]: 255B52CE287: to=<joshua@joshdesignonline.com>, relay=dovecot, delay=0.07, delays=0.03/0.01/0/0.03, dsn=4.3.0, status=deferred (temporary failure)

---

### Post by albinootje on 2009-04-05
Yes, I forgot something very important..., see also here :
[http://ubuntuforums.org/archive/index.php/t-763533.html](http://ubuntuforums.org/archive/index.php/t-763533.html)

What do you have for sasl settings in postfix's main.cf ?

More here :
[http://ubuntuforums.org/showthread.php?p=7014041](http://ubuntuforums.org/showthread.php?p=7014041)

---

### Post by LiQuidAiR on 2009-04-05
I'm going to do a full reboot and then a full postfix and dovecot reload

---

### Post by albinootje on 2009-04-05
```

# relevant part of my postfix/main.cf
smtpd_sasl_auth_enable          = yes
smtpd_sasl_exceptions_networks  = $mynetworks
smtpd_sasl_security_options     = noanonymous
broken_sasl_auth_clients        = yes
smtpd_sasl_type                 = dovecot
smtpd_sasl_path = auth/dovecot

```

---

### Post by LiQuidAiR on 2009-04-05
Same syslog message.

---

### Post by albinootje on 2009-04-05
> **LiQuidAiR said:**
> Same syslog message.

Can you post the output of the following :
```

postconf -n|grep -i sasl
postconf -n|grep -i auth

```
And post the permissions of the relevant files and directories that I've posted before ? 
Thanks in advance.

---

### Post by LiQuidAiR on 2009-04-05
> **albinootje said:**
> Can you post the output of the following :
```

postconf -n|grep -i sasl
postconf -n|grep -i auth

```
And post the permissions of the relevant files and directories that I've posted before ? 
Thanks in advance.

joshua@web01:/etc/postfix$ postconf -n|grep -i sasl
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_exceptions_networks = $mynetworks
smtpd_sasl_local_domain = 
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot


joshua@web01:/etc/postfix$ postconf -n|grep -i auth
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_path = private/auth



joshua@web01:/etc/postfix$ ls -la /var/spool/postfix/
total 76
drwxr-xr-x 19 root    root     4096 2009-04-02 20:45 .
drwxr-xr-x  5 root    root     4096 2009-04-02 21:11 ..
drwx------  2 postfix root     4096 2009-04-05 16:18 active
drwx------  2 postfix root     4096 2009-04-05 00:14 bounce
drwx------  2 postfix root     4096 2009-04-02 20:45 corrupt
drwx------ 17 postfix root     4096 2009-04-05 12:19 defer
drwx------ 17 postfix root     4096 2009-04-05 12:19 deferred
drwxr-xr-x  3 root    root     4096 2009-04-05 16:04 etc
drwx------  2 postfix root     4096 2009-04-02 20:45 flush
drwx------  2 postfix root     4096 2009-04-02 20:45 hold
drwx------  2 postfix root     4096 2009-04-05 16:16 incoming
drwxr-xr-x  2 root    root     4096 2009-04-05 16:04 lib
drwx-wx--T  2 postfix postdrop 4096 2009-04-05 16:16 maildrop
drwxr-xr-x  2 postfix root     4096 2009-04-04 21:32 pid
drwx------  2 postfix root     4096 2009-04-05 16:04 private
drwx--s---  2 postfix postdrop 4096 2009-04-05 16:04 public
drwx------  2 postfix root     4096 2009-04-02 20:45 saved
drwx------  2 postfix root     4096 2009-04-02 20:45 trace
drwxr-xr-x  3 root    root     4096 2009-04-02 20:44 usr



joshua@web01:/etc/postfix$ ls -la /var/spool/postfix/auth/dovecot 
ls: cannot access /var/spool/postfix/auth/dovecot: No such file or directory

joshua@web01:/etc/postfix$ ls -la /var/run/dovecot/auth-master
ls: cannot access /var/run/dovecot/auth-master: No such file or directory



Okay.  Is an interesting this.  I just tried sending a test email to my gmail account and it worked.  It returned no error.

the @joshdesignonline.com is my domain and is forwarding to my ubuntu server on a private/local network.  Basically,  it only cares about the auth-master socket if it's a local email test.

---

### Post by albinootje on 2009-04-05
> **LiQuidAiR said:**
> 
joshua@web01:/etc/postfix$ ls -la /var/spool/postfix/auth/dovecot 
ls: cannot access /var/spool/postfix/auth/dovecot: No such file or directory

Okay, good. 
You are missing the directory /var/spool/postfix/auth
Create it and give it the proper permissions. Afair I've posted my permissions for that directory.

---

### Post by LiQuidAiR on 2009-04-05
Okay it's created and has the same permissions.  I choose 770 permissions instead.  but the user and the group are setup correctly.  I restarted both services. 

I ran a quick test to send myself an email but it returned the same error.
I can still send a email to my gmail.com account.

---

### Post by albinootje on 2009-04-05
> **LiQuidAiR said:**
>  Have you had any issues with the auth-master directive within the dovecot.conf file?

syslog is returning a file missing or unknown error.

I check /var/run/dovecot/ and the only thing listed is a login file/directory

Is the complaint still about /var/run/dovecot/auth-master ?
These are my permissions for the /var/run/dovecot directory :
```

drwxr-xr-x  3 root     root     4096 Apr  1 05:46 dovecot

```

---

### Post by albinootje on 2009-04-05
See also this thread :
[http://start.ubuntuforums.org/showthread.php?t=1024866](http://start.ubuntuforums.org/showthread.php?t=1024866)

---

### Post by LiQuidAiR on 2009-04-05
I think I figured it out. All of the howto's were saying to uncomment out

```

#   protocol imap {
#     listen = *:143
#     ssl_listen = *:10943
#   }
#   protocol pop3 {
#     listen = *:110
#   }
#   protocol managesieve {
#     listen = *:12000
#     ..
#   }

```

I put the comments back on because I ran sudo dovecot and dovecot said FATAL: same ip/port listening for imap imaps.  

BOOM.  the auth-master sockets are now in the /var/run/dovecot/


I need to go back and see why the howto's were saying to uncomment those lines.. I wonder if it was my mistake or theirs.

Now to test it.

---

### Post by LiQuidAiR on 2009-04-05
Now evolution is actually talking to my server.  This is so kewl!

Thank you albinootje.  I wouldn't have had such a fun time working on this if you didn't provide me the support of asking me questions about my config and making sure the basics were setup.  Thank you very much.

EVERYONE GIVE THIS GUY AN AWARD!@~#!@


Now I have an error in my sql syntax I have to figure out.  LOL.....  That should be easy...compared.

YOU DA MAN albinootje!!

---

### Post by albinootje on 2009-04-05
> **LiQuidAiR said:**
> 
BOOM.  the auth-master sockets are now in the /var/run/dovecot/

cool! :)
> 
I need to go back and see why the howto's were saying to uncomment those lines.. I wonder if it was my mistake or theirs.

Some howtos are pretty old. For example the one you mentioned earlier on, the comment about "Dspam, later, sorry" is there since at least a year, and dovecot configuration did change between some different dovecot versions.
I'm using Debian Etch, and I will need to test before I will jump to Debian Lenny because Dovecot has made quite a jump in version differences there afaik.

---

### Post by albinootje on 2009-04-05
> **LiQuidAiR said:**
> Now evolution is actually talking to my server.  This is so kewl!

Thank you albinootje.  I wouldn't have had such a fun time working on this if you didn't provide me the support of asking me questions about my config and making sure the basics were setup.  Thank you very much.

You're welcome. Great that you got it working! :)

---

### Post by LiQuidAiR on 2009-04-05
I would like to add you to my friends list.  Never know when I might be able to help you.

Thank you again.

---

### Post by albinootje on 2009-04-05
> **LiQuidAiR said:**
> I would like to add you to my friends list.  Never know when I might be able to help you.

Sure, go ahead.
> 
Thank you again.
No problem.

---

