---
title: "vfp over samba share"
date: 2009-12-03
forum: Server Platforms
---

### Post by markie83 on 2009-12-03
hello....awesome forum here [IMG]http://e1h7.simplecdn.net/lqcdn/images/questions/images/smilies/smile.gif[/IMG]

anyway my question is this....currently we are using visual foxpro 5 (I know older than dirt but its what works for us) and we have all the programs run off of a mounted nt4 file share (L: )....ok we are wanting to build a faster server with sata drives gigabit-lan etc.

I have built a server using ubuntu 9.04 and have setup samba 3.3.2 with a shared folder under /home/"username"/ldrive (ext3 if you were wondering) I have set the "inherit permissions=yes" in the smb.conf file.

all of my workstations(about 20 pc's) will mount this drive via a batchfile ALL using the same username & password (same credintials as the user under /home/"username").


now I have not implemented this setup yet but have tested it a little....my main concern is that when I take this live do you guys think I will have any of these infamous "file spin lock" problems I have read about with older samba versions? remember ALL users are using the same credentials.

BTW we are using .DBF files not mysql(although we may migrate someday). Also will case sensitivity be an issue since all the client machines are winXP).


....thanks for the advice [IMG]http://e1h7.simplecdn.net/lqcdn/images/questions/images/smilies/smile.gif[/IMG]

---

