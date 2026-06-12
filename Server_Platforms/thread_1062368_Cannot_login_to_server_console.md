---
title: "Cannot login to server console"
date: 2009-02-06
forum: Server Platforms
---

### Post by RickG2 on 2009-02-06
After installing a new printer on Ubuntu 8.10 lamp server I rebooted the server and now I cannot login at the console.  I login and get the following.

Ubuntu 8.10 *severname* tty1

*servername* login: 

I do not get a Login incorrect message, just the login prompt again.  I can no longer access the windows shared folders but I can access the server through webmin and the squid proxy is still working.  I can boot into recovery mode and login as root.  This server has been running without fail since October.  Thanks in advance for any suggestions.

---

### Post by taurus on 2009-02-06
Boot into recovery mode and have a look at your $HOME to make sure you are still the owner of that directory and files in it.

```
ls -la /home/*username*
```
Replace *username* is your login name.

And while you are at it, change the password just to be sure.

---

### Post by albinootje on 2009-02-06
> **taurus said:**
> 
And while you are at it, change the password just to be sure.

In recovery mode that would be :
```

passwd jonathan

```
if your username is jonathan.

---

### Post by RickG2 on 2009-02-06
I logged into recovery as root.  The owner was correct but I changed it anyway.  When I tried to change the password as suggested, I get 'Segmentation fault'.  I tried changing the password through wemin and did not receive any errors, but the issue still exists.

Thanks again

---

### Post by RickG2 on 2009-02-07
I resolved the login problem.  I had to comment out the following from /etc/pam.d/common-auth:

auth   optional      pam_smbpass.so migrate

and from /etc/pam.d/common-password:

  password   optional      pam_smbpass.so nullok use_authtok use_first_pass

I still cannot access the samba shares from windows.

---

### Post by bapoumba on 2009-02-08
Moved to Servers.

---

### Post by mescobal on 2009-02-27
Same problem on a regular Ubuntu 8.10 installation (my wife's). Appeared when trying to enable remote cups administration. Same solution. First time (years using Linux) I can't login using a regular "tty" console. Think this should be filed as a major bug (cups? samba?).
Not sure if it should be filed under "server platforms"
Thanks for the temporal solution (it saved my day / marriage).

---

