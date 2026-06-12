---
title: "rpcclient setdriver returns WERR_INVALID_PARAM"
date: 2010-11-03
forum: Server Platforms
---

### Post by bugsduggan on 2010-11-03
I'm trying to build a print server using Ubuntu Server 10.04.1 LTS, Samba 3.4 and CUPS 1.4.3

I have successfully installed my HP DeskJet930C with CUPS and can print from the server (named dibbler). I can also print from my Desktop Ubuntu box across the network with no problems.

I also have a laptop running Windows XP which I would like to be able to print from (hence the samba tomfoolery) and have successfully managed to move the driver files onto the server and run rpcclient adddriver. I have confirmed that everything looks about right and tried to run the setdriver command:

```

bugs@dibbler:~$ rpcclient -U root -c 'setdriver HP_DESKJET_930C HP_DESKJET_930C' localhost

```

This returns WERR_INVALID_PARAM so I ran enumdrivers and enumprinters. enumdrivers returns the driver that I just added :) enumprinters says 'No printers returned.'

I relatively confident that I've missed out something vital along the way (trying to follow several different how-tos at once!) so any help will be gratefully received.

Many thanks.
Bugs

p.s. I did check through the various logs but couldn't find anything glaringly obviously wrong, if they need posting, let me know and I shall do so.

---

### Post by bugsduggan on 2010-11-04
Once again, I have solved my own problem. For those of you having the same issue, you need a section in your smb.conf directly relating to the printer you want to share, so for me:

```

[HP930C]
   comment = Sir Printsalot
   printable = yes
   path = /var/spool/samba
   public = yes
   guest ok = yes

```

Otherwise setdriver doesn't know what you're talking about.

Google is my friend.

---

### Post by agpton on 2012-07-25
To solve this problem, you need to restart the Samba Daemon:
```
sudo service smbd restart
```

I don't why, but it works!

---

