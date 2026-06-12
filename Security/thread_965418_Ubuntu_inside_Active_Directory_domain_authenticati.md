---
title: "Ubuntu inside Active Directory domain authentication problems"
date: 2008-10-31
forum: Security
---

### Post by gkaragoulis on 2008-10-31
I have three servers (Server A,B,C), all running fully updated Ubuntu with the latest kernel, and they are all members of my company's existing AD domain.  Until recently everything has worked great, but in the past couple weeks there has been very strange behavior:

When I try to login to server A, it won't authenticate anymore and never lets me in (more details below).  When I try server B, I can login, but other domain users can't.  And when I try server C, everyone can login; everything seems fine on that one.

The errors I'm getting on servers A and B are exactly identical, except they happen to different users.  When logging into the desktop, my auth.log shows this:

```
Oct 31 14:55:52 XF2 gdm[25986]: pam_winbind(gdm:auth): getting password (0x00000010)
Oct 31 14:55:52 XF2 gdm[25986]: pam_winbind(gdm:auth): pam_get_item returned a password
Oct 31 14:55:52 XF2 gdm[25986]: pam_winbind(gdm:auth): user 'CORP.gkaragoulis' granted access
Oct 31 14:55:52 XF2 gdm[25986]: pam_unix(gdm:account): could not identify user (from getpwnam(CORP.gkaragoulis))
```

Normally when "getpwnam()" fails I just restart 'nscd' and everything is fine, but this time not even that works.  Restarting samba, winbind and nscd in varying orders does nothing as well.

Some strange things happen when I try to telnet into server A.  If I get the password right, then it says:

```
Oct 31 15:11:43 XF2 login[26604]: pam_winbind(login:auth): getting password (0x00000010)
Oct 31 15:11:43 XF2 login[26604]: pam_winbind(login:auth): pam_get_item returned a password
Oct 31 15:11:43 XF2 login[26604]: pam_winbind(login:auth): user 'corp.gkaragoulis' granted access
Oct 31 15:11:43 XF2 login[26604]: pam_unix(login:account): could not identify user (from getpwnam(CORP.gkaragoulis))
Oct 31 15:11:43 XF2 login[26604]: User not known to the underlying authentication module

```

So it appears as if it successfully gets and recognizes my password, but then getpwnam fails for some reason and it won't let me login.  Some other situations that may give more information is when I try to 'su' into 'CORP.gkaragoulis' I get this:

```
rootinc@XF2:~$ su CORP.gkaragoulis
Unknown id: CORP.gkaragoulis
rootinc@XF2:~$ su CORP.backupuser
Password: 
CORP.backupuser@XF2:/home/rootinc$ 
CORP.backupuser@XF2:/home/rootinc$ wbinfo -u | grep CORP.gkaragoulis
CORP.gkaragoulis

```

Any help out there for me?

---

### Post by gkaragoulis on 2008-11-11
So I wasn't able to fine the root cause of this issue, but I was able to resolve it.  I simply rejoined all the servers to the AD domain and everyone's authentication worked fine again.  But I'm still mystified as to why it got screwed up in the first place...

Is it possible that the Linux machine's configuration inside the domain got corrupted so that some accounts fail while others don't?  How else are those symptoms possible?

---

### Post by HermanAB on 2008-11-11
I have see problems like that.  Gawd knows what goes wrong.  Usually it can be resolved by rejoining.  Sometimes I have to restart Win2003 ADS.

---

### Post by gkaragoulis on 2008-11-11
...and rejoining every time this happened wouldn't be a problem if I wasn't the IT administrator for a company that wants their environment to remain stable all the time.  I guess that's what we have to live with though; it doesn't seem like anyone out there has a solution for this...or even knows what is going on...

---

### Post by HermanAB on 2008-11-11
I have found Samba Winbind to be very stable with Win2003 ADS.  Problems only arise when I make changes to ADS.  If I leave it alone, it keeps working for months on end.

---

