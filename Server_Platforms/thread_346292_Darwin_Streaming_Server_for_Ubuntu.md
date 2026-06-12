---
title: "Darwin Streaming Server for Ubuntu"
date: 2007-01-25
forum: Server Platforms
---

### Post by amoore on 2007-01-25
I'm looking for documentation about running a Darwin Streaming Server on Ubuntu. DSS is Apple's open source version of the Quicktime streaming server. Can anyone help point me in the right direction of some documentation of DSS for Ubuntu?

---

### Post by amoore on 2007-01-31
Bump...

---

### Post by bitflung on 2007-02-02
i'm looking for the same

Jinzora claimed some video functionality, but i couldn't import videos so i'm confused (the config file lists a lot of video formats as permitted, incl MOV MPG AVI DIVX)

HTTP Explorer is referenced here (with a lot of others):
[http://www.ubuntuforums.org/showthread.php?t=237442](http://www.ubuntuforums.org/showthread.php?t=237442)

if you find a good solution, let me know.
for now, i'm running a brute force method:  i'm converting a bunch of futurama episodes into flash-videos using Picklish ([http://www.picklish.com/](http://www.picklish.com/)) and placing them on my home computer (with dyndns and cable internet).  seems to work well enough, but manually pre-converting the files is a pain as i need two copies of the file (one for local playback on the TV my ubuntu box is hooked up into).

goodluck

---

### Post by amoore on 2007-02-02
Thanks for your reply on my post about the Darwin streaming server. I need a DSS because it supports g3p streaming. g3p is a streaming format that supports video streaming to cell phones that are 3gp compliant.  I have a project that I'm working on that needs this feature. 

If you have any thing that can help me get a DSS up and running on Ubuntu I would be very thankful.

---

### Post by bitflung on 2007-02-03
if found this site earlier, but the server is down right now - i emailed the admin, hopefully they fix the problem.

[http://streaming411.com/wiki/Darwin_Streaming_Server](http://streaming411.com/wiki/Darwin_Streaming_Server)

when i first found the site, i noticed comments that gcc4 will error out on ubuntu (they were using ubuntu server 6.10) - there was something about apt-get'ing gcc3.4 (?) and modifying BuildIt - i dont know what buildit is yet.

their directions included logging into the apple OSS cvs, logging in using a (reg. required) apple account; updating to current DSS sources; modifying the buildit scripts (?)... thats all i recollect.

hopefully the site comes back up.  i have an apple account, but when i tried to follow their directions, i couldn't log into CVS, so i gave up for the night, and when i returned to it tonight the wiki was down...

hope the link helps.

Edit: they also posted about success using Suse and Fedora - perhaps if you know the difference between the build environments of these distros, you'll understand how to make DSS compile on ubuntu.

Edit 2: this is another OSS 3GP compatible streaming server...
          [http://www.catrasoftware.it/Streaming/CatraStreamingServer.htm](http://www.catrasoftware.it/Streaming/CatraStreamingServer.htm)

Edit 3:  i've now tried catra streaming server - i downloaded the linux binaries from sourceforge.  the server is supposed to be all-inclusive (no prerequisite packages to install??) but the binaries fail: something about failing to register as a service.  i'm a noob, more or less, and have little troubleshooting skills at this point - it may be an easy fix, it may not be.

---

### Post by ni4ata on 2007-03-21
Debian Sarge

1. Become root (by using su or any other tool you prefer)

2. Install the libstdc++6 package if not already done:

~$ apt-get install libstdc++6

3. Change to working directory:

~$ cd /usr/local/src/

4. Download the Fedora Core 4 binary from the DSS home page [1]:

/usr/local/src# lynx [http://www.opensource.apple.com/projects/streaming/release/DarwinStreamingSrvr5.5.4-Linux.tar.gz](http://www.opensource.apple.com/projects/streaming/release/DarwinStreamingSrvr5.5.4-Linux.tar.gz)

5. extract it and enter the created directory:

~$ tar xvzf DarwinStreamingSrvr5.5.4-Linux.tar.gz
~$ cd DarwinStreamingSrvr5.5.4-Linux

6. Create the qtss group like this:

~/DarwinStreamingSrvr5.5.4-Linux# groupadd qtss

7. Run the Install script.

~/DarwinStreamingSrvr5.5-Linux# ./Install

8. Enter username for new DSS serveradmin.

9. Enter password for new DSS serveradmin.

10. Repeat password for new DSS serveradmin.

11. Browse to and login at:

[http://ipaddress:1220/](http://ipaddress:1220/)

You're done!

The group must be added manually because the included install script doesn't creates it:

There will be some warnings about ps like this one:

Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)

But the ps output still works for the Install script so don't pay attention to those.



I found this in google cash, and it's works, but i also must add "qtss" user manully.

---

### Post by michwill on 2007-05-08
Well, I've finally got DSS installed and running, but I can't seem to get it to actually stream anything.  All clients simply sit and spin their cursors or hourglasses (depending on platform) and never actually get anything.  Any ideas?

---

### Post by zaziork on 2007-05-12
> **michwill said:**
> Well, I've finally got DSS installed and running, but I can't seem to get it to actually stream anything.  All clients simply sit and spin their cursors or hourglasses (depending on platform) and never actually get anything.  Any ideas?

Have you allowed access through the firewall (IP tables/Firestarter)?

---

### Post by michwill on 2007-05-12
Yeah, I finally got items to play by not using playlists.  I simply provide a list via PHP of the files in "/usr/local/movies" and provide a formatted link to each.  My current problem is encoding properly with the "myth3pg" script.  But that's part of another thread. ;)  Thanks!

---

### Post by pajarraco on 2007-11-12
> **ni4ata said:**
> Debian Sarge

1. Become root (by using su or any other tool you prefer)

2. Install the libstdc++6 package if not already done:

~$ apt-get install libstdc++6

3. Change to working directory:

~$ cd /usr/local/src/

4. Download the Fedora Core 4 binary from the DSS home page [1]:

/usr/local/src# lynx [http://www.opensource.apple.com/projects/streaming/release/DarwinStreamingSrvr5.5.4-Linux.tar.gz](http://www.opensource.apple.com/projects/streaming/release/DarwinStreamingSrvr5.5.4-Linux.tar.gz)

5. extract it and enter the created directory:

~$ tar xvzf DarwinStreamingSrvr5.5.4-Linux.tar.gz
~$ cd DarwinStreamingSrvr5.5.4-Linux

6. Create the qtss group like this:

~/DarwinStreamingSrvr5.5.4-Linux# groupadd qtss

7. Run the Install script.

~/DarwinStreamingSrvr5.5-Linux# ./Install

8. Enter username for new DSS serveradmin.

9. Enter password for new DSS serveradmin.

10. Repeat password for new DSS serveradmin.

11. Browse to and login at:

[http://ipaddress:1220/](http://ipaddress:1220/)

You're done!

The group must be added manually because the included install script doesn't creates it:

There will be some warnings about ps like this one:

Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)

But the ps output still works for the Install script so don't pay attention to those.



I found this in google cash, and it's works, but i also must add "qtss" user manully.

Hi, I did this and I think everything was install fine. but i try to open [http://ipaddress:1220/](http://ipaddress:1220/) like you said and doesn't work
there is another way to see if is working or if there is a error on the install

Edit

I try to install again and i having a invalid user error

chown: 'qtss' : invalid user

any help

---

### Post by pajarraco on 2007-11-12
i fix it.

I create the group, the user and the password

# groupadd qtss
# useradd -g qtss qtss
# passwd qtss

and i put some password

and then i run the ./Install 

now is working

---

