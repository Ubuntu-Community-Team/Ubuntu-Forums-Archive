---
title: "Need an advice for a backup server."
date: 2010-09-04
forum: Server Platforms
---

### Post by Rany Albeg on 2010-09-04
Hello , 

I want my old computer to activate as a backup server for the local network.
All other people on my local network use Windows XP,7 and I want them to be able to easily send their files to my server for backup or even to write some bash scripts at the future to do so automatically.

Since I'm a beginner with Ubuntu Server and generally with computer communication, I do not know how to make my computer to function that way.

I read some introduction about Samba software because it sounds like the closest match to what I am looking for, but I want to be sure.

Can you give me a good advice on how to set my computer to function as a backup server?

Thank you,

Rany.

---

### Post by scorp123 on 2010-09-04
> **Rany Albeg said:**
>  Since I'm a beginner with Ubuntu Server and generally with computer communication, I do not know how to make my computer to function that way. [http://www.bacula.org](http://www.bacula.org)

... works tip top for Windows clients too.

---

### Post by Rany Albeg on 2010-09-04
Thank you.
Seems like a good solution.
I'll try it.

Rany.

---

### Post by Medwyyn42 on 2010-09-04
Bacula can be a bit complicated. I've separated my .conf files out into jobs, filesets, and clients. I had to compile 5.03 for my Ubuntu server but downloaded the Vista/Win7 binaries from Sourceforge. I believe that the newest 5.03 binaries properly configure for the monitor function on Vista/Win7 so no need to comment that out of the .conf file and the service should autostart on boot without crashing. One thing I've gotten to partially work is Base jobs - it will work for a small test fileset (c:\temp) but not the entire C:\Windows directory.... not that you'd really need to backup the OS. I've found that Webmin can provide a fairly easy GUI to use for Bacula, but you still need to edit the filesets manually to enable VSS for your Windows clients. Good luck.

---

### Post by HermanAB on 2010-09-05
Hmmm, Windoze - here is an old guide:
[http://www.aeronetworks.ca/windows-backup.html](http://www.aeronetworks.ca/windows-backup.html)

---

### Post by Rany Albeg on 2010-09-05
Thank you guys for all the suggestions.
Eventually I ended up using Samba following [THIS]("http://www.youtube.com/watch?v=p2r0kIB_ItE great tutorial") great tutorial which is explained under 9.04 but still relevant for 10.04 distribution.

Thanks again,

Rany.

---

