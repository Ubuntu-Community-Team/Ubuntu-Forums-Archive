---
title: "Upgrade was interrupted due to lost broadband"
date: 2012-09-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by awam66 on 2012-09-07
Hi,
I decided to do an upgrade from 12.04 to 12.10 on my Dell C521 amd64 computer. I have 12.04 on two partitions so this was the development version. Having done sudo update-manager -d I then started the upgrade. During the download I lost my broadband internet connection and the upgrade aborted itself. I was then inable to do anything more as I got error massages 9sorry can't remember what they were) but it was something to do with errors in /var/lib/apt/lists directory. I renamed this directory and created an empty one then did an apt-get update. All is now OK except when I do a sudo update-mangager -d the upgrade it not offered. AAny ideas please. I am fairly experienced with ubuntu and the terminal.

---

### Post by ventrical on 2012-09-07
This may work.

**sudo dpkg -i --configure -a**

---

### Post by cariboo on 2012-09-07
You more than likely have several missing packages, I'd suggest using:

```
sudo apt-get -f install
```

to download and install the missing packages, then run the upgrade again.

---

### Post by ventrical on 2012-09-07
Thanks for that correction. I was thinking  of a time when I had a power outage and the packages were already downloaded. When I rebooted it told me I had broken packages. So I used --configure -and it worked.

---

### Post by awam66 on 2012-09-07
> **cariboo907 said:**
> You more than likely have several missing packages, I'd suggest using:

```
sudo apt-get -f install
```

to download and install the missing packages, then run the upgrade again.

No that does nothing, just suggests apt-get autoremove but that doesn't help either. Still can't get the upgrade on update manager.

---

### Post by cariboo on 2012-09-07
Have you tried:

```
sudo apt-get update
```

then

```
sudo apt-get dist-upgrade
```

---

### Post by awam66 on 2012-09-08
> **cariboo907 said:**
> Have you tried:

```
sudo apt-get update
```

then

```
sudo apt-get dist-upgrade
```

Yes I have. I have tried all these but still cannot get it to upgrade. Have resorted to change precise to quantal  in the lists file and will see where that takes me.

---

