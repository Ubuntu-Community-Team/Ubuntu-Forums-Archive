---
title: "Tripwire /var/run changes?"
date: 2009-08-27
forum: Security
---

### Post by PadawanGeek on 2009-08-27
Every time I run a check on tripwire on my server, I comes up with added, removed, and modified files under /var/run, even if I just updated the database.

Here is the section in the file:

```
-------------------------------------------------------------------------------
Rule Name: System boot changes (/var/run)
Severity Level: 100
-------------------------------------------------------------------------------
  ----------------------------------------
  Added Objects: 3
  ----------------------------------------

Added object name:  /var/run/iptraf
Added object name:  /var/run/iptraf/iptraf-itrafmoncount.dat
Added object name:  /var/run/iptraf/iptraf-processcount.dat

  ----------------------------------------
  Removed Objects: 2
  ----------------------------------------

Removed object name:  /var/run/console/root
Removed object name:  /var/run/motd.new

  ----------------------------------------
  Modified Objects: 4
  ----------------------------------------

Modified object name:  /var/run

  Property:            Expected                    Observed                    
  -------------        -----------                 -----------                 
* Num Links            16                          17                          


Modified object name:  /var/run/ConsoleKit/database

  Property:            Expected                    Observed                    
  -------------        -----------                 -----------                 
* Inode Number         11894                       12637                       


Modified object name:  /var/run/console/pete

  Property:            Expected                    Observed                    
  -------------        -----------                 -----------                 
* Inode Number         11800                       12634                       


Modified object name:  /var/run/motd

  Property:            Expected                    Observed                    
  -------------        -----------                 -----------                 
* Inode Number         11384                       11899                       

```

Is this okay? I'm sort of a noob at this stuff.

---

### Post by cariboo on 2009-08-27
> Added object name:  /var/run/iptraf
Added object name:  /var/run/iptraf/iptraf-itrafmoncount.dat
Added object name:  /var/run/iptraf/iptraf-processcount.dat



That is perfectly normal, when ever a service starts a pid is created in /var/run.

---

### Post by PadawanGeek on 2009-08-28
> **cariboo907 said:**
> That is perfectly normal, when ever a service starts a pid is created in /var/run.

Thanks!

---

