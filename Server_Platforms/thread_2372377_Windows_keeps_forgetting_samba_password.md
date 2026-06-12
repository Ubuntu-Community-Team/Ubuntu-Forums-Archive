---
title: "Windows keeps forgetting samba password"
date: 2017-09-24
forum: Server Platforms
---

### Post by derekdoesit on 2017-09-24
My 1st POST!
i spend a lot of time creeping through the forums finding all kinds of information and most are perfect for what i need. So for all those who helped me without knowing it...THANK YOU!

So my problem now is with windows and my samba password on windows and sometimes on my other linux servers consisting of pihole/openvpn,samba file server, and plex.

I rarely have problems on on the linux servers because of the .smbcredentials file, but windows not only forgets the password, but states that it doesn't work until i log onto the samba server and run:
```
smbpasswd -a %username%
``` 
I use the same password and boom, its good for like 2 days.

Any idea why it's doing this? My wife gets a little annoyed when i have to vpn home from work just to "update" the password.

---

### Post by Morbius1 on 2017-09-24
Once upon a time there was a package called libpam-smbpass. What that package did was force the samba password for a user to be the same as the local login password for that user. It would do this at boot time.

So if you have a user that has a login password of XXX and a samba password of YYY the samba password would stay at YYY until the server was rebooted. Then libpam-smbpass would reset the samba password to XXX. It was maddening. I think they removed it from the repositories in more recent releases of Ubuntu so I don't know if this is the problem for you but it's the only thing that seems to fit your symptoms.

Either keep libpam-smbpass but change the login password to match your samba password. Or just remove libpam-smbpass:
```
sudo apt-get remove libpam-smbpass
```
The package has no other function in life then to do what I described.

---

### Post by derekdoesit on 2017-09-24
I actually read a post this morning about removing libpam-smbpass. So i guess im going to work with it until a problem occurs. Thank you for confirming my choice in removing libpam-smbpass.

---

