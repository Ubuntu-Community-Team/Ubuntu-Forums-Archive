---
title: "CUPS driving me MAD"
date: 2006-01-30
forum: Server Platforms
---

### Post by ]Nbx*cmD[ on 2006-01-30
I need help ](*,) 

I've read almost whole linuxprinting.org and i still can't configure my print server :mad: 

The situation is: three computers, one (mine) using ubuntu breezy badger, other (my father's) using windooze xp and the third running ubuntu warty warthlog as server.
That server holds apache, proftpd, ssh and samba, and it is suposed to hold cups too but it doesn't.
I can print via samba from windooze pc but it lasts about 20 minutes to print a single page, which is **NOT** in **ANY WAY** a reasonable printing time.
So, in an inspirational moment i thought on using IPP, but i couldn't conf¡gure it even following linuxprinting.org howtos :(

My printer is an HP Deskjet 845c, i've downloaded and installed the last hpijs but, damn, it still doesn't work! I can't access localhost:631 anymore.

Please i'd gift my home and bank account who could help me :???: 
Oh btw, the server doesn't have X installed (it's a server) so it has no kde-gnomish "next-next-next-next-finish" gui interface ;)

Thx!

---

### Post by sco01 on 2006-01-30
I did set up a CUPS/Samba print server last week and i ran into the problem you described with slow printing from XP. I solved my problem by removing the HKEY_CURRENT_USER\PrintersConnections\* registry key.

I found the solution on this page: [http://www.edoceo.com/liber/gentoo-samba-cups.php](http://www.edoceo.com/liber/gentoo-samba-cups.php) (see the bottom of the page).

It seems like this is a general problem with Samba and XP SP2. I've noticed that there are a few other solutions out there but i haven't tried any of them since this one worked.

I just have to add that setting up a print server is by far the most anoying thing i've done so far with Ubuntu.

---

### Post by ]Nbx*cmD[ on 2006-01-30
THANKS THANKS THANKS!!
I should have thought it was windows' fault #-o 
Well... about my home and bank account... let's exchange it for a great THANK YOU, is it enough hehe? ;)

---

### Post by sco01 on 2006-01-31
Don't worry. Just glad to help :). I've written a small howto (In Swedish) on setting up an anonymous print server with CUPS and Samba on Breezy. I wrote it since i couldn't find one consistent howto on the topic after googling for one full day. 
I noticed another thread ([http://www.ubuntuforums.org/showthread.php?t=35046](http://www.ubuntuforums.org/showthread.php?t=35046)) where fakier proposed a solution to enabling the web interface without running CUPS as root. I will change that part in my howto, translate it to english and post it in the tips and tricks section within a few days. If anybody is aware of an existing howto for this, please let me know.

//Stefan

---

