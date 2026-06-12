---
title: "help...installed &quot;untrusted&quot; security updates"
date: 2007-11-17
forum: Server Platforms
---

### Post by LinuxSoundMan on 2007-11-17
i dont know why but when i did a routine security update today i got the message that these cannot be authenticated.

> Upgraded the following packages:
gdm (2.20.0-0ubuntu6) to 2.20.1-0ubuntu1
libsmbclient (3.0.26a-1ubuntu2.1) to 3.0.26a-1ubuntu2.2
samba-common (3.0.26a-1ubuntu2.1) to 3.0.26a-1ubuntu2.2
smbclient (3.0.26a-1ubuntu2.1) to 3.0.26a-1ubuntu2.2  does anyone know why. i havent added any repositories. i am worried here. please help. thanks a lot.

---

### Post by thegnuguru on 2007-11-17
Do you have any third party repos? If not the fix should be

```

sudo apt-get install ubuntu-keyring
sudo apt-get update

```
Maybe your keyring got damaged some how it happens :)

Regards 

Matt Arnold

---

### Post by urvaksh on 2007-11-17
I'm getting the same warning prior to install. In my case its only the samba and smbclient updates though.
I don't have a gdm update
When I tried the sudo install keyring command in the terminal, I got this message
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by thegnuguru on 2007-11-17
Do you have any package managers running if you ABSOLUTELY  sure you don't delete /var/lib/dpkg/lock and try again

EDIT I think something is screwed with samba packages i tried updating and i got 403ed from downloading just those

---

### Post by LinuxSoundMan on 2007-11-17
i sure hope this doesnt put my system at risk. thanks for the replies. i really appreciate it. and i have not added any repositories.

---

### Post by LinuxSoundMan on 2007-11-17
> **thegnuguru said:**
> 
```

sudo apt-get install ubuntu-keyring
sudo apt-get update

```
Maybe your keyring got damaged some how it happens :)

Regards 

Matt Arnold

it said that it was already the latest version. is there anyway i can find out if these untrusted packages are safe? thanks

---

### Post by LinuxSoundMan on 2007-11-17
i just checked and i do have third party repos from [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) and [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) but the conical ones are not checked. thanks

---

### Post by thegnuguru on 2007-11-17
then one of those repo keys is not on your apt keyring

Try removing the third party repos and then updating

---

### Post by LinuxSoundMan on 2007-11-17
im guessing i have to manually add the repos to the key? is there any way i could find out if my system has been compromised? perhaps a program is available to scan the network? sorry i am new to this. im pretty sure WineHQ should be trusted as they are the developers of Wine which runs windows apps on linux. thanks

---

### Post by thegnuguru on 2007-11-17
yes you do need to add that key manually and its very unlikely that your system will be compromised apt warning are a bit more scary then they need to be. This is not to say that you shouldn't be careful about third party repos the package in them don't go thorough as much testing as the Ubuntu ones. But you won't get viruses this ain't windows :) BTW wine is in ubuntu repos already you should only use the ones from wine if you want to test new features and what not

---

### Post by LinuxSoundMan on 2007-11-17
ok then that may be the problem thanks a lot for the info. much appreciated

---

### Post by LinuxSoundMan on 2007-11-17
my keyring daemon is not even running and i have none listed. im not sure exactly how this works.

---

### Post by LinuxSoundMan on 2007-11-17
i see
thanks for the info. and the help. kind regards.

---

### Post by LinuxSoundMan on 2007-11-17
something seems wrong here because when i go to remove samba or anything samba related it says it affects other packages and marks ubuntu-studio-desktop for removal. is this normal behavior. samba allows linux to communicate files to windows if im not mistaken. any help please. thanks

---

### Post by thegnuguru on 2007-11-17
yes that is normal but i don't know why

---

### Post by LinuxSoundMan on 2007-11-17
ok so is samba necessary? it seems like it would allow windows machines to remotely "extract" files from your linux machine based on what it does. perhaps we could get a security expert in on this thread. i installed firestarter for security reasons and it seems buggy because sometimes out of nowhere i will be clicking through menus and it just closes and disappears for no reason. weird stuff goin on today.  thanks for the info by the way.

---

