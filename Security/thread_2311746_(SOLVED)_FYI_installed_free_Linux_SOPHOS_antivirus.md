---
title: "(SOLVED) FYI: installed free Linux SOPHOS antivirus"
date: 2016-01-29
forum: Security
---

### Post by Kris_M on 2016-01-29
spent my life on windows.
one month old on Ubuntu Unity 14.04.3

This is now command line only - no GUI - contrary to some documentation. Changed this past summer.
Download:  [URL="https://www.sophos.com/en-us/products/free-tools/sophos-antivirus-for-linux.aspx"]https://www.sophos.com/en-us/products/free-tools/sophos-antivirus-for-linux.aspx 
Forums:   [/URL][https://community.sophos.com/products/free-antivirus-tools-for-desktops/](https://community.sophos.com/products/free-antivirus-tools-for-desktops/)   you need a login
Documentation pointers at:  [https://www.sophos.com/en-us/support/documentation/sophos-anti-virus-for-linux.aspx#](https://www.sophos.com/en-us/support/documentation/sophos-anti-virus-for-linux.aspx#)
This might also be helpful: [http://www.bleepingcomputer.com/forums/t/578679/sophos-antivirus-for-linux/](http://www.bleepingcomputer.com/forums/t/578679/sophos-antivirus-for-linux/)

Doesn't seem to slow my firefox but reduces game NWN/NWN2 opening to a drag so for that I just shut it off and afterward turn it on.
```
Check status of on-access scanning:
sudo /opt/sophos-av/bin/savdstatus

- Enable on-access scanning:
sudo /opt/sophos-av/bin/savdctl enable

- Disable on-access scanning:
sudo /opt/sophos-av/bin/savdctl disable
```

I tested it with EICAR downloads  [http://www.eicar.org/85-0-Download.html](http://www.eicar.org/85-0-Download.html) - found them fine.

Whether an AV is needed or not in Linus is a discussion for a different thread.  In Win of course I always had one.  I sit behind my router's firewall.

And partially I was bored! LOL  But I will leave it on and update the database occasionally.

```
Install updates
sudo /opt/sophos-av/bin/savupdate

Scan system
sudo savescan /
```
savescan took 17 minutes and found the 3 intentional exploits in my old phone-flash-rom stuff.

Cheers!

---

