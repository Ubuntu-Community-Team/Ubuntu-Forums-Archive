---
title: "Need Help How To Allow AD user Access to internet"
date: 2014-10-22
forum: Server Platforms
---

### Post by izremote on 2014-10-22
Hi All, 
I'm newbie to Ubuntu Server . I configured AD on Ubuntu server which works great,  but when joining the client to AD - client cant access to the WEB.
AD only allows client access LAN . How to allow AD clients  access the Web?

Thank you

---

### Post by oldos2er on 2014-10-22
Moved to Server Platforms. Forum Feedback & Help is for questions and comments about the forum itself, not Ubuntu.

---

### Post by koenn on 2014-10-25
You're gonna have to explain this a lot better.

Are you talking about Active Directory with Samba ? What does internet access have to do with that ? What's the purpose of your server, and who are its clients ? ...

---

### Post by lingpanda on 2014-10-26
> **izremote said:**
> Hi All, 
I'm newbie to Ubuntu Server . I configured AD on Ubuntu server which works great,  but when joining the client to AD - client cant access to the WEB.
AD only allows client access LAN . How to allow AD clients  access the Web?

Thank you

You most likely need to set 'dns forwarder = 8.8.8.8' or another DNS in your smb.conf file.

---

