---
title: "samba 3.6.3 precise many problems"
date: 2012-06-23
forum: Server Platforms
---

### Post by alfredo.marchini on 2012-06-23
Hi all,
yesterday I installed for a customer samba 3 PDC.
I have installed many of this servers for my customers.
This time I decided to install it on Precise instead of Lucid, always in i386 arch.
I copied samba configuration from Lucid, changed the values that I needed and nothing works.
In Lucid samba is the 3.4.7, in Precise 3.6.3.
I found bug with charset parameter, that cause samba to log many errors and not work correctly, and the worst thing: the windows xp client joined correctly to domain, but after they don't do login.
I searched many forums on web before downgrading every samba package and dependencies to 3.4.7.
Now, with samba 3.4.7 it works, and voilà, no strange log errors.
With samba 3.4.7 on Precise all worked fine.
The question is: how is possible that very important daemon like samba, in a server env, is in this conditions?

The following (corrected) bug is only one example:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/980758](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/980758)

anyway the worst thing is that samba 3.6.3 have other small problems, small that I have to downgrade it.
Or probably I missing something, I'm writing this post for asking you...
Thank you very much
Bye

---

### Post by Morbius1 on 2012-06-23
>  The question is: how is possible that very important daemon like samba, in a server env, is in this conditions?Your example is only one of the problems. As an example here's another one: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410)

Samba has 2 functions is life: A file server and a print server. Right now 50% of Samba's capability is non functional. There's a workaround for this problem but it is to bypass Samba and go directly to CUPS. I'm not smart enough to determine if the problem is with CUPS, Samba, something Ubuntu did, or all of the above but I would feel better if this Confirmed - High Importance bug was actually assigned to someone.

---

### Post by alfredo.marchini on 2012-06-23
Hi,
fortunately in this case I didn't use samba as a print server.
But I'm a little bit worried about this situation. :???:
I think that samba is at 1st position about importance in Linux Server env like Apache2, MySQL and networking-related solutions.
Is the first time happens (I started to use Ubuntu Server LTS from 6.06 version)...
This is a very bad start for a new LTS release... :-(

---

### Post by bab1 on 2012-06-23
Right off the bat I have to say that all my printers are network enabled.  I don't use Samba for printing at all.  But, I have always wanted to suppress all those error messages.

It appears that CUPS printing is enabled on my 12.04 Samba server.  You can tell that with this```
sudo ldd `which smbd`|grep libcups
```You should get something like this returned if it is enabled ```
	libcups.so.2 => /usr/lib/i386-linux-gnu/libcups.so.2 (0x001b9000)
```

If you are successful then it should be a matter of configuration in the smb.conf file with something like this```
[global]
load printers = yes
printing = cups
printcap name = cups

[printers]
comment = All Printers
path = /var/spool/samba
browseable = no
guest ok = yes
writable = no
printable = yes
printer admin = root, @ntadmins, @smbprintadm
```

It looks like the parameters in the [global] section are commented out by default. 

All of this came from Samba.org in [**_[COLOR="Blue"]this chapter[/COLOR]_**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html#id2632962") of the Samba-HOWTO-Collection.

In my Googling I also found how to suppress the errors and that helped me.  :-)

---

### Post by bab1 on 2012-06-23
> **alfredo.marchini said:**
> Hi,
fortunately in this case I didn't use samba as a print server.
But I'm a little bit worried about this situation. :???:
I think that samba is at 1st position about importance in Linux Server env like Apache2, MySQL and networking-related solutions.
Is the first time happens (I started to use Ubuntu Server LTS from 6.06 version)...
This is a very bad start for a new LTS release... :-(

What does your /etc/samba/smb.conf file look like.  Post it in the ```
 blocks by clicking on the [SIZE="2"]**#**[/SIZE] icon at the top of the editor.

What do you get from this[CODE]sudo ldd `which smbd`|grep libcups
```

---

### Post by Morbius1 on 2012-06-23
The normal ( previous ) communication between samba and cups is broken. Both a Windows client and a Linux client will confront the same problem regardless of how smb.conf is configured. It's a known problem, one that has been confirmed, one that has been listed as High in importance, but it remains Unassigned ( [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410) )

My first thought is that it's because the Samba-CUPS portion has been rewritten: [http://wiki.samba.org/index.php/Samba_3.6_Features_added/changed](http://wiki.samba.org/index.php/Samba_3.6_Features_added/changed)
Unless Ubuntu added another layer of complexity to this whole thing then it turns into a CUPS vs Samba fight, egos will prevail, and this could turn into a very long wait.

Like I said, the workaround is for Windows and Linux to access a Linux Server printer directly using CUPS but that does not address the problem that the Print Server function of Samba is not working properly.

Me thinks that Samba is making small incremental additions to the 3.6 branch from the Samba4 base so that when it's finally released it's not a monumental change.

---

### Post by alfredo.marchini on 2012-06-23
bab1, 
here my smb.conf.
I had also many cups errors, but I repeat I didn't use cups in this case, also I cannot test ldd command because now my server has smb 3.4.7 not 3.6.3, my problem is that after joining domain, the xp client at login tells me "Domain EXAMPLE not available."

```

[global]
  interfaces = lo, eth1, tun0
  bind interfaces only = yes
  workgroup = EXAMPLE
  server string = PDC %v
  socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

  netbios name = SERVER
  domain logons = yes
  domain master = yes
  preferred master = yes
  wins support = yes
  time server = no
  dns proxy = no
  unix charset = ISO8859-1

  utmp = yes
  map acl inherit = yes
  hide dot files = yes
  veto oplock files = /*.doc/*.xls/*.mdb/
  unix extensions = no
  usershare allow guests = no

  obey pam restrictions = no
  os level = 99
  log file = /var/log/samba/%m.log
  max log size = 1000
  syslog = 0
  log level = 1
  panic action = /usr/share/samba/panic-action %d
  pam password change = yes

  security = user
  unix password sync = yes

  load printers = no
  printing = cups
  printcap name = cups
  show add printer wizard = no

  passdb backend = tdbsam
  username map = /etc/samba/smbusers

  add user script = /usr/sbin/useradd -m '%u'
  delete user script = /usr/sbin/userdel -r '%u'
  add group script = /usr/sbin/groupadd '%g'
  delete group script = /usr/sbin/groupdel '%g'
  add user to group script = /usr/sbin/usermod -G '%g' '%u'
  add machine script = /usr/sbin/useradd -g 501 -s /bin/false -d /tmp '%u'
  passwd program = /usr/bin/passwd %u
  passwd chat = *New*Password* %n\n *Re-enter*new*password*%n\n *Password*changed*

  logon drive = H:
  logon home = \\%L\%U
  logon path = \\%L\profiles\%U
  logon script = %U.bat

  server signing = auto
  server schannel = auto
[homes]
  comment = Home Directory
  valid users = %S
  read only = no
  browsable = no
  create mask = 0700
  directory mask = 0700
  hide dot files = yes
[mail]
  comment = Mail Repository Directory
  valid users = %U
  path = /home/posta/%U
  read only = no
  browsable = yes
  create mask = 0700
  directory mask = 0700
  hide dot files = yes
[netlogon]
  comment = Network Logon Service
  path = /home/netlogon
  guest ok = yes
  locking = no
  browsable = no
[profiles]
  comment = Profile Directory
  path = /home/profiles
  read only = no
  profile acls = yes
  browsable = no
  hide files = /desktop.ini/ntuser.ini/NTUSER.*/
  create mask = 0600
  directory mask = 0700
[printers]
  comment = Printer Spool
  path = /var/spool/samba
  guest ok = yes
  printable = yes
  use client driver = yes
  default devmode = yes
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
   write list = root, @admin
[public]
  comment = Public Directory
  path = /home/public
  valid users = @users
  read only = no
  browsable = yes
  create mask = 0770
  directory mask = 0770
[scanner]
  comment = Scanner Directory
  path = /home/scanner
  read only = no
  browsable = yes
  create mask = 0666
  directory mask = 0777
  guest ok = yes
  public = yes

```

This config running perfectly on samba 3.4.7!!!

---

### Post by alfredo.marchini on 2012-06-28
Have someone news about this situation?
I saw that there are no updates of samba 3.6.3, like it's working like a charm.
You asked me my file configuration.
have u tried it or have u found something wrong?
Usually I kept my systems regularly updated, so this situation is not good for me.
I wait for some days than with aptitude I hold samba packages and dependencies to 3.4.7 and upgrade all other packages.
Thank you.
Bye

---

### Post by bab1 on 2012-06-28
> **alfredo.marchini said:**
> Have someone news about this situation?
I saw that there are no updates of samba 3.6.3, like it's working like a charm.
You asked me my file configuration.
have u tried it or have u found something wrong?
Usually I kept my systems regularly updated, so this situation is not good for me.
I wait for some days than with aptitude I hold samba packages and dependencies to 3.4.7 and upgrade all other packages.
Thank you.
Bye
I was only addressing the printer situation.  I am running Ubuntu 12.04 with Samba 3.6.3 and it works perfectly.

---

### Post by Gyokuro on 2012-06-29
The problem with XP clients joining samba 3.6 DC's (bug 8373) should be fixed in release 3.6.6.

---

### Post by bab1 on 2012-06-29
> **Gyokuro said:**
> The problem with XP clients joining samba 3.6 DC's (bug 8373) should be fixed in release 3.6.6.

I read the bug thread at Samba.org.  Will that Samba update make it to the Ubuntu 12.04 LTS repos?

---

### Post by Gyokuro on 2012-06-29
> **bab1 said:**
> I read the bug thread at Samba.org.  Will that Samba update make it to the Ubuntu 12.04 LTS repos?

If I'm not complete blind I was unable to find a bug report on launchpad.net concerning this problem. I suggest that the OP should fill out a bug report and mention that it should be fixed in release 3.6.6 - so that afterwards people with the same problem can subscribe the bug.

---

### Post by bab1 on 2012-06-29
> **Gyokuro said:**
> If I'm not complete blind I was unable to find a bug report on launchpad.net concerning this problem. I suggest that the OP should fill out a bug report and mention that it should be fixed in release 3.6.6 - so that afterwards people with the same problem can subscribe the bug.

From Ubuntu's (and even Debian's) point of view, this bug is upstream at Samba.org.  

Filing a bug report at launchpad will only bring frustration.  The real question is:  Is the Ubuntu package for Samba frozen at a version below 3.6.6.  I don't see that as a "bug", more as a decision to update the sources of the package when the bug fix is released.

Who manages the Samba package for Ubuntu/Debian?  They are the folks who need to know.

---

### Post by Gyokuro on 2012-06-29
I agree but - if nobody fills a bug report how should canonical/debian know that there is a problem? In my opinion it's better to fill a bug report which maybe get marked later as invalid as people upgrading from 10.04 to 12.04 and get a big surprise. As it's already late for me here is the link for the samba package which is mentioning the samba maintainers ([http://packages.ubuntu.com/precise/samba](http://packages.ubuntu.com/precise/samba)).

---

### Post by alfredo.marchini on 2012-08-07
Hi,
today I come back to my customer with lucid downgraded samba (and dependencies) on precise ubuntu. 
Now the server works well, but is not perfect like on a lucid ubuntu (I have many lucid samba pdc installed and work perfectly).
I think the problems is that I cannot downgrade everything, and the smb is in production.
In addition I discover that something in the tdb db is different between the two versions of samba. So once I update the samba, I cannot go back transparently (I need to backup everything, not a big problem, but is not trasparently).
So I advice that is better to install lucid for samba pdc, don't downgrade packages, it's not a good idea... :(

---

