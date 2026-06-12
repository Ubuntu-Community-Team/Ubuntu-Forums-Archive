---
title: "Mail Notification 3.0"
date: 2006-07-05
forum: Ubuntu Backports
---

### Post by uptimebox on 2006-07-05
I have built Mail Notifiaction 3.0 package

[http://rolevikov.net/debian/mail-notification_3.0.uptimebox.1_i386.deb](http://rolevikov.net/debian/mail-notification_3.0.uptimebox.1_i386.deb)

This package has no support for SSL and Evolution (the same as 2.0 version in official repository). Post here if you want me to publish SSLed and/or Evolution version.

Sorry if I posted to wrong forum, but I realy have no idea what place this topic matches better.

---

### Post by loz_hurst on 2006-07-05
Hi there,
I would really appreciate a release with evolution support, if you could.
Thanks
--Laurence

---

### Post by uptimebox on 2006-07-05
[http://rolevikov.net/debian/mail-notification_3.0.uptimebox.2_i386.deb](http://rolevikov.net/debian/mail-notification_3.0.uptimebox.2_i386.deb)

Version with Evolution and SSL support. Unforunately I'm unaware of legal issues related to SSL usage, so it's up to you to decide.

---

### Post by BuffaloX on 2006-07-06
Cool.

Just had to figure out the menu was in system - preferences.

Works like a charm.:)

---

### Post by linuxworld on 2006-07-07
Thanks uptimebox :) 
Works perfect here !!!

---

### Post by rpw on 2006-07-08
Hello,

first I wanna thank you for the deb-file. Unfortunatly it does not work with my [www.gmx.net](www.gmx.net) account. When I configure the mailbox (IMAP) I only get different error messages.

One error message was "the answer >>mailto:name@gmx.de<< could not be analized"

I think there has been an error message about charset iso-8859-1 to, but I can't really remeber (has been too late yesterday evening... ;) )

Maybe there is still a problem with charset?

Regards,

rpw

---

### Post by bikeboy on 2006-07-11
Happy Mail Notification 2.0 user here, what are some reasons for trying the new package?

---

### Post by mthaddon on 2006-07-13
I have installed the version with Evolution support - just wondering how you actually set up an Evolution account in this?

Thanks, Tom

---

### Post by uptimebox on 2006-07-13
> **mthaddon said:**
> I have installed the version with Evolution support - just wondering how you actually set up an Evolution account in this?

Thanks, Tom

You have to restart Evolution after Mail Notification installation.

---

### Post by mthaddon on 2006-07-13
Great, thanks. 

Does Evolution have to be running for this to work? I'm assuming yes, right? The mailbox I'm checking is actually an Exchange folder (so it's using Evolution's Exchange connector, and it tends to stop polling unless you switch folders after a while, so I'm wondering whether this will also be true for the mail notifications...

Also, I'm trying to troubleshoot some IMAP problems - here's the output from with --enable-info:

$ mail-notification --enable-info
mail-notification-INFO: mthaddon@192.168.1.100: resolving 192.168.1.100
mail-notification-INFO: mthaddon@192.168.1.100: connecting to 192.168.1.100 (192.168.1.100) port 993
mail-notification-INFO: mthaddon@192.168.1.100: connected successfully
mail-notification-INFO: mthaddon@192.168.1.100: a SSL/TLS layer is now active (TLSv1, AES256-SHA 256-bit)
mail-notification-INFO: mthaddon@192.168.1.100: < * OK mailhost.example.com Cyrus IMAP4 v2.2.12-Invoca-RPM-2.2.12-1.1.fc3 server ready
mail-notification-INFO: mthaddon@192.168.1.100: > a000 CAPABILITY
mail-notification-INFO: mthaddon@192.168.1.100: < * CAPABILITY IMAP4 IMAP4rev1 ACL QUOTA LITERAL+ MAILBOX-REFERRALS NAMESPACE UIDPLUS ID NO_ATOMIC_RENAME UNSELECT CHILDREN MULTIAPPEND BINARY SORT THREAD=ORDEREDSUBJECT THREAD=REFERENCES ANNOTATEMORE IDLE AUTH=PLAIN SASL-IR LISTEXT LIST-SUBSCRIBED X-NETSCAPE
mail-notification-INFO: mthaddon@192.168.1.100: < a000 OK Completed
mail-notification-INFO: mthaddon@192.168.1.100: > a001 AUTHENTICATE PLAIN
mail-notification-INFO: mthaddon@192.168.1.100: < +
mail-notification-INFO: mthaddon@192.168.1.100: > dGhhZGRvbgB0aGFkZG9uAFVrZXkyNHhSdA==
mail-notification-INFO: mthaddon@192.168.1.100: < a001 NO authentication failure
mail-notification-INFO: mthaddon@192.168.1.100: falling back to IMAP LOGIN authentication
mail-notification-INFO: mthaddon@192.168.1.100: > a002 LOGIN "mthaddon" "my_really_secure_passwd"
mail-notification-INFO: mthaddon@192.168.1.100: < a002 NO Login failed: authentication failure
mail-notification-INFO: mthaddon@192.168.1.100: > a003 LOGOUT
mail-notification-INFO: mthaddon@192.168.1.100: < * BYE LOGOUT received
mail-notification-INFO: mthaddon@192.168.1.100: < a003 OK Completed
mail-notification-INFO: mthaddon@192.168.1.100 reported an error: authentication failed


I have someone else opposite me running Mail-notification 3.0 (compiled from source on Gentoo) that's working fine with this IMAP server... 

Any help appreciated.

Thanks, Tom

---

### Post by cowbud on 2006-07-24
anyone else get a strange corba error when using this? Even when I compile it on my own I get the same error:

A Bonobo exception (Unknown CORBA exception id: 'IDL:omg.org/CORBA/BAD_OPERATION:1.0') has occurred in GNOME:MailNotification:Automation:hasMailboxes().

---

### Post by Hibountu on 2006-07-28
Ok, working well here... just a question... if Evolution must be working for this to do anything, what is the point ?  Is there a way to have Evolution work in the background ?

---

### Post by cowbud on 2006-07-28
Just a quick fyi the reason why it wasn't working for me was because I had an old copy of mail notification still running :)

---

### Post by gunck8 on 2006-08-02
Thanks for the .deb-file. On first startup I got a lot of error messages. Now it however seems to work.

-gunck8

---

### Post by sread on 2006-10-24
Edgy update...
This worked great for me under Dapper but:
When I updated to Edgy, something caused mail-notification to use 100% CPU! Not a good time. If you update to the Edgy mail-notification v3.0 package, problem solved. This was a problem for me because I locked the mail-notification package...not a good idea I guess! Hopefully this will help someone else who's scratching their head like I was.

...package is still locked in synaptic though..can't seem to unlock it, oh well.

---

### Post by dt96hasv on 2006-10-27
Just updated to 6.10 and saw that mail-notification now has IMAP/SSL support and decided to give it a try... However although POP works nicely over SSL, I can not get IMAP to work, it just connects and then does nothing!?

```
hans@hans-desktop:~$mail-notification --enable-info
mail-notification-INFO: hanssv@mail.medic.chalmers.se: resolving mail.medic.chalmers.se
mail-notification-INFO: hanssv@mail.medic.chalmers.se: connecting to mail.medic.chalmers.se (129.16.30.218) port 993
mail-notification-INFO: hanssv@mail.medic.chalmers.se: connected successfully
```

EDIT: Well of course it won't work, SSL/TSL support is disabled...

---

### Post by Lutze on 2006-11-14
What does "is disabled" mean? Is there any way to enable it again, and if not, why is SSL not greyed out anymore?

---

### Post by the_mechanical on 2006-12-04
I have the same problems with IMAP as *dt96hasv*.
Is there anybody who can help us?

```
mail-notification-INFO: *username@server*: resolving *server*
mail-notification-INFO: *username@server*: connecting to *server* (*ip*) port 993
mail-notification-INFO: *username@server*: connected successfully
```
(Note: I've changed the real-adresses with *username@server*, *server* and *ip*)
After that - nothing happens.
Connection: SSL/TSL Port 993 (i also tried the others - with the "server advertised LOGINDISABLED" failure)
POP is working great.

---

### Post by the_mechanical on 2006-12-07
Ok, i found A solution: I installed Mail-Notification4.0RC1
[http://www.nongnu.org/mailnotify/]("http://www.nongnu.org/mailnotify/")
(there has to be installed a lot of *dev -packages)

However: Now it works fine!! (also with IMAP)

---

### Post by dt96hasv on 2006-12-07
As I wrote in the original post the SSL support is disabled in the Mail Notifiaction one gets via the package manager. (The reason for this was some sort of license issue, nothing serious rather technical.) 

The solution for me was to download the source and enable SSL support and build my own version of the Mail Notification package (as explained in the Mail Notification 2.0 thread: [Mail Notification 2.0]("http://ubuntuforums.org/showthread.php?t=55758&page=8"). Note that one also need to install buildscripts to follow the directions there)

Then things worked smothly :)

---

### Post by artelsj on 2006-12-07
I've made a mail-notification [4.0rc2 package](http://packages.artels.org/mail-notification_4.0rc2-artelsj0-1_i386.deb) (checkinstall). SSL is enabled.

---

### Post by ludicrouSpeed on 2007-01-11
hi all, im getting the following problem when i try to install this on my ubuntu 6.10 lappie

error: dependancy is not satisfiable: lidbus-1-2


Any idea whats going on anyone?

Cheers,

Ludi

---

### Post by ludicrouSpeed on 2007-01-11
i downloaded the latest package and it works now, thanks :)

---

### Post by cez801 on 2007-01-19
I got the same problem with lidbus-1-2 as well, which I simply installed to sort it out.

I had already installed mail-notification 3.0 via the package manager, I did have to go an remove that (which also removed mail-notification-evolution at the same time) to get it all working.

The mail notification 4.0RC2 works perfectly, I have 6.10 with IMAP over SSL. 

Thanks.

---

### Post by Freedreamer on 2007-01-20
mail notification 4 is out.
Anyone has a deb package?

thanks in advance

---

### Post by artelsj on 2007-01-20
> **Freedreamer said:**
> mail notification 4 is out.
Anyone has a deb package?

thanks in advance

The developer says that those who have a 4.0 rc installed don't need to upgrade. That being said, I'll probably make a 4.0 final .deb within the next few days.

---

### Post by ls8 on 2007-01-24
> **Freedreamer said:**
> mail notification 4 is out.
Anyone has a deb package?

thanks in advance

Mail Notification 3.0 and 4.0 with SSL, SASL, Evolution support, compiled for Ubuntu 6.10: [http://www.volny.cz/lukas_svoboda/ubuntu/edgy/](http://www.volny.cz/lukas_svoboda/ubuntu/edgy/)

---

### Post by Freedreamer on 2007-01-24
thanks!

---

### Post by ls8 on 2007-01-25
Can anyone please test my packages in dapper?

---

### Post by cez801 on 2007-01-26
I have installed Mail Notification 4.0, but for some reason when I get a notification - it never seems to go to the not notified status.
When I right click on the status icon, I can not do open new message or update status - not sure why.

I'm using IMAP over SSL, any ideas?

---

### Post by jooaakim on 2007-02-03
Any chance of a amd64 package?

---

### Post by marianom on 2007-02-15
Creating your own .deb, configuring and installing it, it's very easy.
I note here the steps required:

1- In case you don't have it, first download and install checkInstall (more about checkInstall [here]("https://help.ubuntu.com/community/CheckInstall")):
```
sudo aptitude install checkinstall
```

2- download the tar.gz mail-notification source code from the site. Unzip it to a directory of your choice and cd into it.

3- run:
```
auto-apt run ./configure
``` 
   3.1- if there are dependencies issues you will be properly notified. Try to get the missing libraries from known sources (synaptic, [http://packages.ubuntu.com/](http://packages.ubuntu.com/), etc).
   3.2- you can run 
```
./configure --help
``` 
to see what configuration options you have. **My advice, explicitly ask for the features you need.**
For example this is the line I executed:
```
auto-apt run ./configure --enable-pop3 --enable-mozilla --enable-ssl --enable-ipv6
```

4- Run make
```
make
``` 

5- The final step:
```
sudo checkinstall
```
 You'll be ask to fill in some info. Do so.

6- Mail-Notification is now installed and you have a .deb file in the directory. e.g.: mail-notification_4.0-1_i386.deb. If you check Synaptic you'll find it there, for easy removal in case you need to do so.

Any doubts please let me know.

---

### Post by jooaakim on 2007-02-19
thanks for that guide but the thing is that i can't configure it as it doesn't find the Gnome libs for some reason. So can't make the deb either as it has to be configed first.

---

### Post by marianom on 2007-02-19
Yeah, I had that problem with several libraries. They're all in Synaptic.
What's exactly the one with problems for you? (Ther errror message for example)

---

### Post by jooaakim on 2007-02-23
Here's what it says:

checking for GTK+ - version >= 2.6.0... yes (version 2.10.6)
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... no
configure: error: unable to find the GNOME libraries

---

### Post by marianom on 2007-02-24
The output usually gives you a line number that, in config.log, tells you exactly what library is missing.
In my config.log (that ran ok, so no errors here), these are the used libs:
```
configure:22846: checking for GNOME
configure:22854: $PKG_CONFIG --exists --print-errors "gthread-2.0 gconf-2.0 >= 2.4.0 libgnomeui-2.0 >= 2.8.0 gnome-vfs-2.0 libglade-2.0 eel-2.0 >= 2.6.0 bonobo-activation-2.0 libxml-2.0 libnotify"

```

As I said I had that problem too and I fixed it downloading the required package. If I recall correctly, one of them was libglade-2.0 which you can find in the repos (you need the -dev version ).
If you can point precisely the missing library (by checking config.log) I can try to help you find it.

---

### Post by JayMan8081 on 2007-03-26
Has anyone had problems with the mail-notification-evolution package from the official ubuntu repos since the evolution update today (today for me, could have been sometime this weekend)?  Ever since I did the evolution update it will not load if I have mail-notification-evolution installed.  Thanks for any help.

---

### Post by desperado666 on 2007-04-11
cant use mail notification with my yahoo email account. can somebody verify this?

---

### Post by buzz.lightyear on 2007-04-24
> **jooaakim said:**
> Here's what it says:

checking for GTK+ - version >= 2.6.0... yes (version 2.10.6)
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... no
configure: error: unable to find the GNOME libraries

Hi,
you probably miss **libeel2-dev**
```
apt-get install libeel2-dev
```

also make sure to install **libgmime2.1-dev** to have support for imap, etc..
```
apt-get install libgmime2.1-dev
```

...and **libedataserverui1.2-dev** is needed for "make" too
```
apt-get install libedataserverui1.2-dev
```

buzz

---

### Post by Mulli on 2007-04-30
Hi,

i've had the same problem with Mail Notification 4.0 :

```
checking for GNOME... no
configure: error: unable to find the GNOME libraries
```


I solved it by installing 'libnotify-bin'. Now it works. 

Greetz
Mulli

---

### Post by moehle on 2007-05-13
Hi,

When I try to make I get this error:

/bin/sh: line 1: -o: command not found
make[2]: *** [bg.gmo] Error 127
make[2]: Leaving directory `/home/david/Desktop/mail-notification-4.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/Desktop/mail-notification-4.0'
make: *** [all] Error 2

Can anyone help with this? I'm running feisty (installed today) and haven't seen this error in previous versions. I tried changing the /bin/sh link to use bash but haven't had any luck.

Thanks

---

### Post by LuisC-SM on 2007-08-18
> **Mulli said:**
> Hi,

i've had the same problem with Mail Notification 4.0 :

```
checking for GNOME... no
configure: error: unable to find the GNOME libraries
```


I solved it by installing 'libnotify-bin'. Now it works. 

Greetz
Mulli

I think you meant to say
```
libnotify-dev
```
Tha's the one that worked for me.

Regards

Luis

---

