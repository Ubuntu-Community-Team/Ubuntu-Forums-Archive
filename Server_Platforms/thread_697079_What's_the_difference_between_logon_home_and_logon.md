---
title: "What's the difference between logon home and logon path in samba?"
date: 2008-02-14
forum: Server Platforms
---

### Post by cpthk on 2008-02-14
Hi:

I am trying to understand what's the difference between logon home and logon path in samba. I searched the internet, but I get even more confusing right now. Any clue? 

Here is what I found: [http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html) Anyone understand what is it saying?

Thanks.

---

### Post by lnx4me on 2008-02-14
Hmmm. Logon Home I believe would be the home directory on the samba server of the user connecting. the logon path would be were the cmd or logon.bat file used typically when you set up samba as domain logon server. I would suggest reading over the default smb.conf file.

---

### Post by cpthk on 2008-02-15
I read already, but I just don't understand what's the difference.

---

