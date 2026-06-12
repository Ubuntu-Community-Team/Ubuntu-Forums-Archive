---
title: "Easy samba printing question... (I think)"
date: 2006-05-01
forum: Server Platforms
---

### Post by fizgig on 2006-05-01
So I've got breezy server installed on my server and it works great.  I've also installed an HP printer to it directly and shared it using samba.

I can print from my ubuntu laptop just fine through the samba connection.

My wife's xp laptop refuses to print to the printer until I manually browse (using file explorer) to the server using my name and password to see all the samba shares.  After that I'm able to print during that windows session.

Clearly, xp isn't giving my name and password to the samba server when it tries to print so samba isn't letting it through until I type in the name and password in file explorer which I guess samba remembers for awhile and then lets xp through.

So, to solve this issue I want to either tell windows xp to send my credentials when it tries to print (which I don't know how to do) or, even better, I'd like everyone to have access to my samba-shared printer.  Can anyone tell me how to do this?  (Preferrably the latter)

---

### Post by Koybe on 2006-05-01
It think you need to make samba a PDC and join the WinXP machine to the domain. Otherwise it'll always ask you for username/password.

Or maybe the other solution : create her user the same both on her windows machine and on the samba server. Just like an old workgroup. It should work.

---

### Post by Iowan on 2006-05-01
Since I don't know the specifics, I'll have to speak in generalities:  You *should* be able to set up the printer share for guest access - not requiring a username/password.

---

### Post by fizgig on 2006-05-01
@Iowan: Any tips on how to do that?  My first post can be boiled down to asking how to do just that.

---

### Post by Iowan on 2006-05-01
Well... no, I haven't gotten to the shared-printer stage yet.  You might post (at least) the printer share portion of your smb.conf file.  Perhaps someone will come along who knows what they're doing and point you (us) in the right direction.

Koybe: That wasn't intended to suggest that you don't know what you're doing...

Borrowed from another thread:
```
[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   browsable = no
```

---

