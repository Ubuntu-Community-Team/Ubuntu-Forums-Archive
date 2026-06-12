---
title: "Tiger Interpertation"
date: 2010-07-26
forum: Security
---

### Post by andthewicked on 2010-07-26
Hi, I need some help again, I just installed tiger and ran it for the first time and was wondering if you could help tell me what is going on with this. I don't know if I even ran this right. also it didn't finish running all the way if that means anything I had to crl-c to exit. 

--WARN-- [boot02] The configuration file /boot/grub/menu.lst has group 
         permissions. Should be 0600 
--FAIL-- [boot02] The configuration file /boot/grub/menu.lst has world 
         permissions. Should be 0600 
--WARN-- [boot06] The Grub bootloader does not have a password configured. 


# Performing check of system file permissions...
--ALERT-- [perm023a] /bin/su is setuid to `root'. 
--ALERT-- [perm023a] /usr/bin/at is setuid to `daemon'. 
--ALERT-- [perm024a] /usr/bin/at is setgid to `daemon'. 
--WARN-- [perm001w] The owner of /usr/bin/at should be root (owned by daemon). 
--WARN-- [perm002w] The group owner of /usr/bin/at should be root. 
--ALERT-- [perm023a] /usr/bin/passwd is setuid to `root'. 
--ALERT-- [perm024a] /usr/bin/wall is setgid to `tty'. 





Security scripts *** 3.2.2, 2007.08.28.00.00 ***
Sun Jul 25 21:43:15 EDT 2010
21:43> Beginning security report for kyle-desktop (i686 Linux 2.6.31-20-generic).

# Performing check of passwd files...
# Checking entries from /etc/passwd.
--WARN-- [pass014w] Login (backup) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (bin) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (couchdb) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (daemon) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (games) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (gnats) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (guest) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (irc) is disabled, but has a valid shell. 
--WARN-- [pass016w] User kernoops has / as home directory 
--WARN-- [pass014w] Login (kyle) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (libuuid) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (list) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (lp) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (mail) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (man) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (news) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (nobody) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (proxy) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (root) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (speech-dispatcher) is disabled, but has a valid 
         shell. 
--WARN-- [pass015w] Login ID sync does not have a valid shell (/bin/sync). 
--WARN-- [pass014w] Login (sys) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (uucp) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (www-data) is disabled, but has a valid shell. 
--WARN-- [pass012w] Home directory /var/lib/sendmail exists multiple times (2) 
         in /etc/passwd. 
--WARN-- [pass006w] Integrity of password files questionable (/usr/sbin/pwck 
         -r). 

# Performing check of group files...

# Performing check of user accounts...
# Checking accounts from /etc/passwd.
--WARN-- [acc021w] Login ID avahi-autoipd appears to be a dormant account. 
--WARN-- [acc021w] Login ID libuuid appears to be a dormant account. 
--WARN-- [acc006w] Login ID mail's home directory (/var/mail) has group `mail' 
         and world write access. 
--WARN-- [acc022w] Login ID nobody home directory (/nonexistent) is not 
         accessible. 
--WARN-- [acc006w] Login ID polkituser's home directory (/var/run/PolicyKit) 
         has group `polkituser' write access. 
--WARN-- [acc021w] Login ID timidity appears to be a dormant account. 

# Performing check of /etc/hosts.equiv and .rhosts files...

# Checking accounts from /etc/passwd...

# Performing check of .netrc files...

# Checking accounts from /etc/passwd...
security.report.kyle-desktop.tmp.4926

---

### Post by sisco311 on 2010-07-26
Yep, tiger is kinda useless if you don't know how to interpret its output. :)

Start reading its documentation/man page, learn a few things about unix/linux user accounts, file permissions, sutuid/setgid applications...

[http://www.nongnu.org/tiger/](http://www.nongnu.org/tiger/)
[http://www.linuxhaxor.net/?p=529](http://www.linuxhaxor.net/?p=529)

Also check out:
[thread=510812]Ubuntu Security[/thread]
[thread=919472]Intrusion Detection[/thread]

---

