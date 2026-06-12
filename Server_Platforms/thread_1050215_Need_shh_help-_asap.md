---
title: "Need shh help- asap"
date: 2009-01-25
forum: Server Platforms
---

### Post by Lori700698 on 2009-01-25
I can't log in!!! Now I'm assuming this in a SHH issue, but I could be completely wrong.  Using Ubuntu Intrepid, using only Webmin and Putty.  Here's where the problem started, I'm trying to get our new printer on the server, I've logged into CUPS I swear 200 times then everything stops working.  I've restarted cups, shh (I'm still in Webmin at the moment) I had this all happen last night and when I logged out of Webmin it was all over, I couldn't get in anywhere, so I did a re-install of everything.  All was good today until I started with CUPS again, printer was there, working fine, and I was fine tuning, and bam, locked out...Please help, it takes HOURS to re-install!

---

### Post by bgerlich on 2009-01-25
Your description is way to vague. Try to login using ssh -vvv user@0.0.0.0 to see where exactly ssh fails.

---

### Post by Lori700698 on 2009-01-25
and what would the pass word be for this???

---

### Post by bgerlich on 2009-01-25
Well "user" is your username, 0.0.0.0 is your server's ip and the password is login password for "user"

---

### Post by Lori700698 on 2009-01-25
seems to be a password issue, I can't putty in with any user's name or pass words, nor the root.  Just says access denied, and when I try as root it just cuts off the connection.

---

### Post by bgerlich on 2009-01-25
Don't use putty, use ssh (openssh client) in command line to login in verbose mode (-vvv) and post the output.

---

### Post by Lori700698 on 2009-01-25
Ok, I truly don't know what to do here, I carried all my stuff back to the terminal and re-hooked up the monitor and keyboard.  I can't even log in there, I got a /etc/postfix/main.cf no such file or directory error.  So I guess it's more than a SHH problem?

---

### Post by Lori700698 on 2009-01-25
Oh my gosh, it's the whole mail thing on the server!  I haven't even touched this yet and it appears to be missing files and has reset my main/root password.  Sometimes I just hate computers, and that would be today!  I'm attempting to delete this from webmin at the moment, who knows what that will do, if anything!

---

### Post by Lori700698 on 2009-01-25
THIS WORKED!!!!  I was still in Webmin when the issue started, last night I was logged out so I thought I was screwed and re-installed whole darn thing.  Happened again today so I didn't log out of Webmin, changed this /var/lib/samba/secrets.tdb to this /var/lib/samba/secrets.tdb.old in file manager, went to command shell and ran dpkg --purge libpam-smbpass  then sudo apt-get install libpam-smbpass
AND I'm back!!!!

Directions from
[http://ubuntuforums.org/showthread.php?p=6615896#post6615896](http://ubuntuforums.org/showthread.php?p=6615896#post6615896)

---

