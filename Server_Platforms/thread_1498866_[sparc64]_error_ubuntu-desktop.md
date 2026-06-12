---
title: "[sparc64] error ubuntu-desktop"
date: 2010-06-01
forum: Server Platforms
---

### Post by philo_71 on 2010-06-01
hi,
i was intalled ubuntu 6.06 lts on Ultra 5, after i do an upgrading to 8.04  lts,
with synapthic manager and cdrom 8.04.1 for sparc64, the system 8.04 work
but i have losted ubuntu-desktop.

i do :
sudo apt-get remove ubuntu-desktop

>>  ubuntu-desktop not installed

then i do :

sudo apt-get install ubuntu-desktop

>> E : packets errors ??

can i do ?


best regards
philo

---

### Post by thebigob on 2010-06-01
I have a Sunfire v120 running Ubuntu 8.04 LTS also

I have not installed Ubuntu desktop however hopefully have some suggestions.

Firstly ensure universe and multiverse repository's are enabled.

can you then post the output of the following:

```

sudo apt-cache search ubuntu desktop

```

---

### Post by philo_71 on 2010-06-01
hi,

i do :
sudo apt-cache search ubuntu desktop
and after

sudo apt-get install ubuntu-desktop

same error !!
>> packets error !

>> my files desktop are damaged..
>> and ask me the cdrom 6.06 lts , can y parametre source.list i think !

best regards
Philo

---

### Post by thebigob on 2010-06-01
can you post the output from this command specifically:
```

sudo apt-cache search ubuntu desktop

```
Also if you do:

```

sudo apt-get update

```does that have any errors?

---

### Post by philo_71 on 2010-06-01
hi

i do :
apt-get update 

>> i have errors >> the file /etc/apt/sources.list are not corretly !
>> because the url are indexed at 6.06 lts , i replace by dapper to hardy into sources.list.
>> but there are mistakes, for example at security packets !
>> can y tell me the essenciel deb are déclared !




best regards
philo

---

### Post by thebigob on 2010-06-01
Ok looks like your sources.list has been corrupted.

I will find a proper link for the sources.list and post it here

---

### Post by thebigob on 2010-06-01
Ok I have found some links to the default hardy sources.list however I am not sure if this is the same for sparc of when this moved to ports.

If someone can post a default sparc hardy sources.list that would really help as I cant get to my server right now.

However what I would recommend if the machine has just been set up is to do a distribution upgrade from 6.06lts using the update-manager-core. As this will upgrade the machine fully.

Steps:

install 6.06LTS and ensure you have a working apt

from there 

```

sudo apt-get install update-manager-core

```

once this is installed do:

```

do-release-upgrade

```This will take your server to 8.04LTS and set up all your packages and sources correctly.

Sorry for the rubbish solution

---

### Post by philo_71 on 2010-06-01
hi,
can i do :
wget -q [http://xxxxxxxx]("http://packages.medibuntu.org/medibuntu-key.gpg")hardyxxxxxsources.listxxxxx

because a can't copy your sources.list file i don't have samba and
not usb devices !!

best regards 
philo

---

### Post by thebigob on 2010-06-03
> **philo_71 said:**
> hi,
can i do :
wget -q [http://xxxxxxxx]("http://packages.medibuntu.org/medibuntu-key.gpg")hardyxxxxxsources.listxxxxx

because a can't copy your sources.list file i don't have samba and
not usb devices !!

best regards 
philo

I would seriously recommend restarting with 6.06 and using the upgrade method I mentioned in my previous post

---

