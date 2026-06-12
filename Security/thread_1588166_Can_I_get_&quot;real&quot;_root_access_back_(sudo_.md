---
title: "Can I get &quot;real&quot; root access back (sudo works fine) after modifying /etc/passwd?"
date: 2010-10-04
forum: Security
---

### Post by rocksockdoc on 2010-10-04
I'm relatively new (1 month) to Ubuntu and I somehow screwed up the root login.
I'm the only user of the laptop, I set up Ubuntu myself a month ago, and it was working fine 'till a couple of days ago when I messed with /etc/passwd somehow.

**All I would like to know is how to set it back up the way it was?**

It's hard to explain as a lot transpired (much of which won't matter to this), but at the moment, here is what is happening:

```

user@donna:~$ **whoami**
user
user@donna:~$** id**
uid=1000(user) gid=1000(user) groups=4(adm),20(dialout),24(cdrom),46(plugdev),105(lpadmin),119(admin),122(sambashare),1000(user)
user@donna:~$ **ecryptfs-mount-private**
Enter your login passphrase: **foobar**
Inserted auth tok with sig [2a1860e7cb545c30] into the user session keyring
[COLOR=DarkRed]**open: Read-only file system**[/COLOR]
[COLOR=DarkRed]**Error locking counteruser@donna:~$ **[/COLOR]
user@donna:~$**su **
Password: **rootfoobar**
**[COLOR=DarkRed]su: Authentication failure[/COLOR]**
user@donna:~$ **rlogin root**
[B][COLOR=DarkRed]/etc/ssh/ssh_config: line 53: Bad configuration option: PermitRootLogin
/etc/ssh/ssh_config: terminating, 1 bad configuration options[/COLOR][/B]
user@donna:~$ **sudo chmod 1777 /tmp**  <--I just did this to prove I had root access
user@donna:~$ 

```

Unfortunately, I don't remember the tweak I did with the password (through the tweakui Ubuntu utility) ... but since all I want to do is get back to default, may I ask:

**Q: How do I get root access back to the way it was by default?**

---

### Post by rocksockdoc on 2010-10-04
Here is what the /etc/passwd looks like.

I highlighted the "root" and "user" account to help you to see if there's something I should fix.

Here it is (in case it helps you to help me):
```

**[COLOR=DarkRed]root:x:0:0:root:/root:/bin/bash[/COLOR]**
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:107::/var/run/dbus:/bin/false
avahi-autoipd:x:103:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:105:113:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
speech-dispatcher:x:106:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
usbmux:x:107:46:usbmux daemon,,,:/home/usbmux:/bin/false
haldaemon:x:108:114:Hardware abstraction layer,,,:/var/run/hald:/bin/false
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:110:115:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:111:117:RealtimeKit,,,:/proc:/bin/false
saned:x:112:118::/home/saned:/bin/false
hplip:x:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:114:120:Gnome Display Manager:/var/lib/gdm:/bin/false
**[COLOR=DarkRed]user:x:1000:1000:user,,,:/home/user:/bin/bash[/COLOR]**
smmta:x:115:123:Mail Transfer Agent,,,:/var/lib/sendmail:/bin/false
smmsp:x:116:124:Mail Submission Program,,,:/var/lib/sendmail:/bin/false

```

---

### Post by andrewthomas on 2010-10-04
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by rocksockdoc on 2010-10-04
BTW, as additional data, a "sudo -s" was suggested here:
- [Manual Data Recovery with Ecryptfs and Ubuntu]("http://cole.mickens.us/2010/08/09/manual-data-recovery-with-ecryptfs-and-ubuntu/"), by  						[Cole Mickens]("http://cole.mickens.us/author/admin/"), on   						[2010/08/09]("http://cole.mickens.us/2010/08/09/manual-data-recovery-with-ecryptfs-and-ubuntu/") 											
  					 
And THAT "**sudo -s**" worked just fine:

```

user@donna:~$ **sudo -s**
[sudo] password for user:** foobar**
root@donna:~# id
uid=0(root) gid=0(root) groups=0(root)

```

**How do I fix the error:**
```

user@donna:~$ rlogin root
/etc/ssh/ssh_config: line 53: Bad configuration option: PermitRootLogin
/etc/ssh/ssh_config: terminating, 1 bad configuration options

```

---

### Post by andrewthomas on 2010-10-04
Here is the default /etc/ssh/ssh_config file

```

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
```

---

### Post by rocksockdoc on 2010-10-05
Thanks Andy,
There's not a whole lott'a help here but when it comes, it's very much appreciated!
Now I can concentrate on the encryption error.

---

### Post by uRock on 2010-10-05
Moved to Security Discussions.

---

