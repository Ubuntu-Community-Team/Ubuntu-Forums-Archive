---
title: "Can't login"
date: 2013-06-27
forum: Server Platforms
---

### Post by Ji Ruo on 2013-06-27
I have a server install of 13.04 64bit that I can no longer log into. ssh won't accept a connection. I can't do a physical login from a console either. What happens is: my username and password are accepted, the terminal goes black for a fraction of a second and the login prompt reappears. None of the filesystems are approaching full. A couple of things I was doing or did when this happened may have led to this. Firstly, I installed kubuntu-desktop. (Graphical login displays the same behaviour as above). Secondly, I was getting a samba share working with an internal drive, so I was doing work on /etc/fstab and the acl for this drive. My /etc/fstab has since been restored from the backup I made before starting this work.

auth.log is not showing much information about what's happening with the login, this is what appears when I try to login via console:

```
Jun 27 23:11:54 phenom login[1847]: pam_unix(login:session): session opened for user thelionroars by LOGIN(uid=0)
Jun 27 23:11:55 phenom login[1847]: pam_unix(login:session): session closed for user thelionroars
```

Any advice would be appreciated, please let me know if I can provide further information.

---

### Post by Ji Ruo on 2013-06-30
I ended up installing again on another hard drive, as the extra work was more preferable to me than not having my server available for the forseeable future. I still have this drive and this issue seems imminently solvable, so if anyone can tell me what the problem might be, I would be keen to know and test it out.

---

### Post by Bashing-om on 2013-06-30
Ji Ruo; Hi ! ...
Generally login issues are a result of altered permissions on the /home directory.

Check if ".ICEauthority" is owned by you:
```

ls -al .ICEauthority
## If it isn't (but possibly by root), change it to you:
sudo chown USERNAME:USERNAME .ICEauthority

```
better take a look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.

[INDENT]if not this, will look further[/INDENT]

---

### Post by Ji Ruo on 2013-07-01
Neither .ICEauthority nor .Xauthority exist in any of my home directories on the broken install. However, they aren't present on the new (& working) install either, so I'm wondering if the way logins are handled has changed recently.

---

### Post by steeldriver on 2013-07-01
AFAIK .Xauthority and .ICEauthority are only relevant for desktop (X session) logins

Do you remember what exactly you were doing to get the samba shares working? did that involve installing any pam components (like libpam-krb5, libpam-smbpass, libpam-winbind)?

Since you posted an auth.log fraction I assume you can still log in via recovery mode? are there any other pam_* module messages aside from the pam_unix messages you posted?

Just thinking out loud here, I don't really know where I am going with this line of questioning, just seems like a coincidence that samba things were underway when it went south

---

### Post by Bashing-om on 2013-07-01
et all: 
Not sure either at this time ... but food for thought:
> In a lot of ways it's similar to the xauth program & the .Xauthority file, except that .ICEAuthority is used for client to client, while .Xauthority is for client to server. ... but like steeldriver ... is this only in reference to a desktop system ?

I recently installed this 13.04 as a minimal install ... and had no XAUTHORITY variable set, nor was the file .Xauthority in existence... that initially was a hurdle I had to overcome to get anything done with the system... And I still have small niggly things to deal with.

Is that variable set ?
```
echo $XAUTHORITY
```

[INDENT][INDENT]hey, we be look'n[/INDENT][/INDENT]

---

### Post by trundlenut on 2013-07-01
I had this issue when the permissions got messed up on my home folder.

---

