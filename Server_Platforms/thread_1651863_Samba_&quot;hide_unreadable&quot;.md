---
title: "Samba &quot;hide unreadable&quot;"
date: 2010-12-23
forum: Server Platforms
---

### Post by PierreRobiquet on 2010-12-23
Hello,

I currently have two shares which I have set up within my smb.conf file, one of which is called "music" and the other of which is called "music_public". I intend to make Music public face the internet, however be restricted to read only access should my password somehow be compromised as this will prevent the evil doer from performing any damage. However, I can still see the shares even though I can't access them, for example I can see "music_public" even though I have "hosts_deny = 192.168." set along with "hide unreadable = yes". Here is a small snippet of the relevant sections of my smb.conf file

```

[global]
guest ok = no
hide unreadable = yes

[Music]
path = /home/testuser/music
comment = Music Files
browseable = no
writeable = yes
valid users = testuser
hosts allow = 192.168.

[Music_public]
path = /home/testuser/music
comment = Public Music Files
browseable = no
writeable = no
valid users = testuser
hosts deny = 192.168.

```At the moment when I login as "testuser" I can see both music and "music_public" shares however as I have denied LAN access to "music_public" I receive an access denied error when attempting to connect. As such I would like to know if I'm using "hide unreadable" correctly or if there is a error in my configuration.

---

### Post by PierreRobiquet on 2010-12-24
I've Google'd around and it appears as though that is what "hide unreadable" is supposed to do, however I still can't seem to get this to work properly. It's not a major issue however I will have a large number of repeat shares e.g. music, music_public, pictures, pictures_public and I would rather the browser window wasn't full of unusable shares.

---

### Post by luvshines on 2010-12-25
> **ConcreteDonkey said:**
> I've Google'd around and it appears as though that is what "hide unreadable" is supposed to do, however I still can't seem to get this to work properly. It's not a major issue however I will have a large number of repeat shares e.g. music, music_public, pictures, pictures_public and I would rather the browser window wasn't full of unusable shares.

Can't understand what your concern is. Are you facing any issues in accessing the shares ?

---

### Post by PierreRobiquet on 2010-12-27
The permissions on my shares are completely fine, however I want to hide shares which are unacessable to the current account or location. I have the "music" folder restricted to my LAN only and "music_public" is write protected and accessible to the world however if I log in from outside my LAN I can see the "music" folder but I can't access it, I thought "hide unreadable" was supposed to hide the folder if it is inaccessible.

---

