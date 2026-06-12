---
title: "Secure Samba configuration difficulties"
date: 2013-02-24
forum: Server Platforms
---

### Post by demonskier on 2013-02-24
Hey, so I am running a samba share from ubuntu server 12.04 but can't for the life of me get it to ask for a user and password from my win machine.

My windows user is not named datastore.  Any ideas?

This is my config:

[global]
        security = user
        encrypt passwords = true
        guest ok = no
        username map = /etc/samba/smbusers

[video]
        path = /video
        browseable = yes
        writeable = No
        valid users = datastore

[music]
        path = /music
        browseable = yes
        writeable = No
        valid users = datastore

[downloads]
        path = /downloads
        writeable = yes
        browseable = yes
        valid users = datastore

---

### Post by Morbius1 on 2013-02-24
Any chance the windows user is being converted to datastore because of the contents of smbusers?
```
cat /etc/samba/smbusers
```

---

### Post by demonskier on 2013-02-24
That file is empty

---

### Post by volkswagner on 2013-02-24
I'm not sure "guest ok = needs to be in global.  Normally that would be applied to individual shares.

You have specified "browsable = yes" to all of your shares which should also not be needed.

Are you saying you can access all the shares (read & write)?

---

### Post by Morbius1 on 2013-02-25
Windows remembers how it was able to connect to a share the last time it was successfull. If you connected to the share once using the datastore user name and the corect password it will always use those credentials.

Easy way to test it out - set a new password for datastore:
```
sudo smbpasswd -a datastore
```Then see if you are prompted for credentials on the Windows end. If you are you can set the password back to the way you had it.

---

### Post by demonskier on 2013-02-26
My read write access is correct per the config. (except that I never have to log in of course).

I tried changing the password and still have access so I don't believe that is the problem.

This is my latest config:

[global]
        security = user
        encrypt passwords = true
        username map = /etc/samba/smbusers

[video]
        path = /video
        writeable = No
        valid users = datastore
        guest ok = no

[music]
        path = /music
        writeable = No
        valid users = datastore
        guest ok = no

[downloads]
        path = /downloads
        writeable = yes
        valid users = datastore
        guest ok = no

---

### Post by volkswagner on 2013-02-26
Please post output of testparm.  Perhaps there is something in the global section not listed here.

```
testparm
```

I'm not sure how to interpret "read write access are correct".

You stated you are able to access the shares without a password.  Is the user you are accessing the share with, even a samba user?

How can the read write access be correct, if you are able to access the shares from a user other than "datastore"?

---

### Post by Morbius1 on 2013-02-26
From one of your client machines add a test file to the [downloads] share. Now on the server end go to /downloads and find out who the owner is of that file:
```
ls -al /downloads/test.txt
```

[COLOR=Blue]*BTW, I've been assuming all this time that you are in a home lan type of setup. If this is an enterprise set up with central login servers or some such let us know.*[/COLOR]

---

### Post by demonskier on 2013-02-27
When I said read write access is correct I meant that write access was correct, sorry slip of the tounge... err fingers.  output of testparm:

:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[video]"
Processing section "[music]"
Processing section "[downloads]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        username map = /etc/samba/smbusers
        idmap config * : backend = tdb

[video]
        path = /video
        valid users = datastore

[music]
        path = /music
        valid users = datastore

[downloads]
        path = /downloads
        valid users = datastore


@morbius
I am in a home lan setup.  I will get you that info as soon as I get home.

---

