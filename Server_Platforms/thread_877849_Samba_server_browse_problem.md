---
title: "Samba server browse problem"
date: 2008-08-02
forum: Server Platforms
---

### Post by pevma on 2008-08-02
Hi guys,
m fairly new to ubuntu.
got my Samba server running fine for a couple of days...now all of a sudden I can't browse in it any more from any pc or any other/got 2 more in d net/
d only way to get to the shared folder is when i use Nautilus and go to "Server Connect" and write my IP and the name of the shared folder...thats d only way any other way its just not there...from the other pc-s there is no way i can see the shared folder.

anybody got an idea what could it be? or how can i fix it?

thanks

---

### Post by redraiderbum on 2008-08-02
If you are trying to see the share from windows sometimes the network discovery just messes up.  If you set a NetBIOS id for the share (that is the name of the share on the network), open a windows explorer window by right-clicking on the start menu and choosing 'explore', then in the url bar type:

\\your_share_name

---

### Post by pevma on 2008-08-03
Thanks, 
tried it again in the morning the next day and its fine.

Its true that sometimes the network services get messed up....saw it with my own eyes...now everything is working fine...
had the same problem with KDE from the other pc/couldn't see me/, but i know its there and its working.
I know it has nothing to do with restarting the smbd process, because i did it several times with no effect and as i said...the next day everything is ok...just bizzare...or i missed/messed something with the smbd.conf file , by the way i did the configuration through SWAT.

but thank you!!

---

