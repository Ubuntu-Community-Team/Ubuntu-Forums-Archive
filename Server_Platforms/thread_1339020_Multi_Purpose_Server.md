---
title: "Multi Purpose Server"
date: 2009-11-27
forum: Server Platforms
---

### Post by Ragewerx on 2009-11-27
Forgive my "noobness" I am in process of building a server for multiple uses. I will list everything that this server must be capable of and maybe one of the guru's in here can help me with a few answers.

This server is needed to:

#1. Be a Mail Server   (would like to be able to sync with Outlook)
#2  Be a Web Server   (Intranet as well as Internet)
#3  Be a File Server     (standard file server with mapped drives)
#4  Be a Media Server  (Streaming as well as transferable)
#5  Be a Data Server   (able to do queries and editing remotely as well as local)
#6  Be an FTP or FSTP Server (for media streaming)
#7  Be able to be remotely controlled (windows interface from kavoom)

I know that this is a very tall order but space is limited and after a few q & a routines I am sure that it is possible to do all of these things in one box.
I do have a few older PC's just laying around that could be used for this task as well but my goal is to try to fit everything into one box (1RU x 27" deep). If necessary, I will use the other two PC's I have for this task as well.


The equipment I have so far for this task:

A commercial Silicon Mechanics Server
AMD Opteron 2.2 GHz. (x2)
4GB RAM (expandable to 16GB)
6 x 1TB. SATA II Drives (Variable RAID configs are possible)
3 x 1000 Base-T ethernet cards (built into motherboard)
1 x 40GB IDE drive (for OS layer)

I am not too well versed in ANY of the Buntu's (or Linux for that matter) and most of my time I have setup MS servers. However, I want to escape the security issues and extreme hardware costs as well as the software costs and headaches that a small time guy like me can't afford. And I am really trying to make this a "all in one" solution as it will house my business, personal, & entertainment files. I also plan on using this unit for streaming media thru my home to various other players in different rooms. plus i would like to run my web server off of it and email as well as client database access.

---

### Post by Ragewerx on 2009-11-27
Actually, I am wondering if this is possible to do first of all. And then secondly (if it is possible). What software is needed for this to happen? And lastly, the total users on the system will be roughly about 50 at maximum (all extensions). As in the intranet, internet, and streaming as well as database access.

---

### Post by virtuoosi on 2009-11-27
> **Ragewerx said:**
> 
#1. Be a Mail Server   (would like to be able to sync with Outlook)
#2  Be a Web Server   (Intranet as well as Internet)
#3  Be a File Server     (standard file server with mapped drives)
#4  Be a Media Server  (Streaming as well as transferable)
#5  Be a Data Server   (able to do queries and editing remotely as well as local)
#6  Be an FTP or FSTP Server (for media streaming)
#7  Be able to be remotely controlled (windows interface from kavoom)


#1. [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
#2. Apache2 (Also good for hosting Squirrelmail)
#3. Use Samba to map network drives to Windows machines
#4. There are many options here, my vote goes for Gnump3d
#5. Are you talking about SQL? If so, MySQL
#6. Ubuntu comes with sftp installed, its FTP over SSH. There's also ProFTPd and many others.
#7. You will have to install the desktop environment, and VNC server. This isn't recommended tho, as running X will effect your servers performance.

---

### Post by Lars Noodén on 2009-11-27
Fortunately most of your questions have generic answers and though you will implement them on Ubuntu Linux, the solutions really have nothing to do with Linux distros.  You could do the same on BSD, Solaris or OS X, for example. 

> **Ragewerx said:**
> 
#1. Be a Mail Server   (would like to be able to sync with [expletive delete])


If you mean regular e-mail, then one of these, with IMAPS to get mail to the client.  There are also several webmail clients around, but not listed below.  

simta
    [http://rsug.itd.umich.edu/software/simta/](http://rsug.itd.umich.edu/software/simta/)
Dovecot
    [http://www.dovecot.org/](http://www.dovecot.org/)
Postfix
    [http://www.postfix.org/](http://www.postfix.org/)
Exim
    [http://www.exim.org/](http://www.exim.org/)
Sendmail
    [http://www.sendmail.org/](http://www.sendmail.org/)

If you mean regular e-mail plus calendars and a whole bag of other extra groupware tools, then add one of these to one of the above:

Kolab
    [http://www.kolab.org/](http://www.kolab.org/)
Citadel
    [http://www.citadel.org/](http://www.citadel.org/)
Zimbra
    [http://www.zimbra.com/](http://www.zimbra.com/)
OpenGroupware
    [http://www.opengroupware.org/](http://www.opengroupware.org/)

> **Ragewerx said:**
> 
#2  Be a Web Server   (Intranet as well as Internet)


An 'intranet' server done correctly is a server with access controls set.  Set up a virtual host on [Apache](http://httpd.apache.org/docs/2.2/vhosts/), [Lighttpd](http://www.cyberciti.biz/tips/howto-lighttpd-web-server-setting-up-virtual-hosting.html), or [nginx](http://articles.slicehost.com/2008/5/16/ubuntu-hardy-nginx-virtual-hosts), using SSL (to get https).  Then set up access controls (e.g. htpasswd)  

> **Ragewerx said:**
> 
#3  Be a File Server     (standard file server with mapped drives)


Three common choices are [Samba](https://help.ubuntu.com/community/SettingUpSamba), WebDAV+https, SSHFS.  If you have multiple servers for multiple groups in different physical locations, then some cases might warrant use of OpenAFS.  

> **Ragewerx said:**
> 
#4  Be a Media Server  (Streaming as well as transferable)


Streaming can be done using [Icecast2](http://www.icecast.org/), [VLC](http://www.videolan.org/vlc/streaming.html), or [FFMPEG](http://ubuntuforums.org/showthread.php?t=665607).  For audio, use Ogg Vorbis for music when possible and Ogg Speex for speech.  For video, use Ogg Theora, MPEG (h.264) or Quicktime.  

> **Ragewerx said:**
> 
#5  Be a Data Server   (able to do queries and editing remotely as well as local)


Can you elaborate?  Do you mean a database?  If so, then you have MySQL, Postgresql, and Sqlite to choose from for the sql databases.  For non-sql databases you have BerkeleyDB and GT.M, to name two.  

> **Ragewerx said:**
> 
#6  Be an FTP or FSTP Server (for media streaming)


No FTP, please.  FTPS is not much better and rather difficult to set up. SFTP is very easy and secure and comes as part of openssh-server and you already have that installed.  

> **Ragewerx said:**
> 
#7  Be able to be remotely controlled [snip]


ssh does that for you but maybe you want to run vnc tunneled over ssh.

---

### Post by HermanAB on 2009-11-27
Howdy,

One physical server can do everything, but you may find that it eventually devolves into a maintenance problem.  Complex servers (e.g. email) is usually best installed on a separate machine, which could be a virtual machine using virtualbox or vmware, so that when you update one service, you don't break another.

---

### Post by Ragewerx on 2009-11-27
@ Everyone that responded to my questions,
I thank you incredibly for such speedy and insightful help. This is the reason why I choose Ubuntu in the first place. I have to say that the people in this forum are top-notch and really do care about computing and where it is going. I myself am a fellow compu-nut that has fallen from the old age days of working on a sun with a dos prompt writing a file in edlin one line at a time for a frontdoor to use to access the internet (over Telnet). From those days (back in 91-93) to working on a GUI system (windows) that would soon ruin my brilliant mind and make me forget most of the programming languages I have ever learned. After all of these years of learning all the nooks and crannies of winders I now have to relearn all of the stuff that I so easily shunned for a pretty screen and a animated cursor.

@ Lars,
Yes, I meant for databasing. IE: kinda like setting up a virtual client list with details and contact info (a sort of PIM if you will). I do believe that MySQL is probably the best way to go about that since the information will be accessable to both sides (intranet/internet) Also, it is needed to be used for a calendar and periodic updates to events and listings (as like MS does in outlook) I know that outlook is not a great schedule/personal manager package but however, it is the only one I have to use (my cell phone is stuck with it) so I might have to go the whole "echange" route (EWWWWWWWW!) I would much rather use something that will allow me to use the MS side of these features and that same software can be changed over to the newer cell phones (IE: HTC and such). Yes, there are a million ways to do this and it is very generic but the areas that make this unique are the facts that I am trying to build a small version of a commercial business system without the MS hook inserted into me all the while having to use certain MS software because of legacy hardware issues.

@ Herman,
I agree, a mail server is best left to be a standalone unit. If needed, I do have something that would be perfect for that job. It is an old P-II 400MHz. (I think??) however, it is an outdated PC that would have ample room for mail and mail services. But the fact remains that it would be headless and I would have to remotely control it over IP there is a proggie called "Kavoom" that does that well and yes, it does *nix as well!

---

### Post by Lars Noodén on 2009-11-29
> **Ragewerx said:**
> 
...Also, it is needed to be used for a calendar and periodic updates to events and listings  ...

Then Kolab or Citadel is the place to start.  Remember that anything you build or see or buy or outsource is going to be built of many small pieces.  So, for example, Kolab or Citadel will sit on top of a mail server (aka MTA) and work with a database (perhaps MySQL or Postgresql) and maybe make use of a web server (perhaps Apache2 or Lighttpd).

As far as 'intranet' goes, just make sure that you use an encrypted connection and require login for access.  Intranets are about *who* can access, not about *where* they happen to sit.  It's entirely probably that a legitimate user has a legitimate reason to access the intranet for his or her work while off site, say visiting a client or working at the branch office.

---

