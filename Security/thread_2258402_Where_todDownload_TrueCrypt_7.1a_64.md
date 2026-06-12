---
title: "Where todDownload TrueCrypt 7.1a 64"
date: 2014-12-27
forum: Security
---

### Post by dreamquartz on 2014-12-27
Looking for a location where to safely download TrueCrypt 7.1a 64 bit.
Have the 32, but not the 64.

John

---

### Post by open2reason on 2014-12-27
dreamquarts,
Truecrypt may well be dead;

 [http://ubuntuforums.org/showthread.php?t=2226748&highlight=truecrypt](http://ubuntuforums.org/showthread.php?t=2226748&highlight=truecrypt) [https://en.wikipedia.org/wiki/TrueCrypt](https://en.wikipedia.org/wiki/TrueCrypt) [http://truecrypt.sourceforge.net/](http://truecrypt.sourceforge.net/) [https://truecrypt.ch/](https://truecrypt.ch/)  [http://istruecryptauditedyet.com/](http://istruecryptauditedyet.com/)  [https://opencryptoaudit.org/](https://opencryptoaudit.org/)

I for one have decrypt my Truecrypt data and encrypt again using the options within the Disk app. Not much of a solution for cross platform work buy OK of Linux work.

Not too sure where a safe copy may be found.

---

### Post by markodd on 2014-12-27
You can download the 7.1a version in truecrypt.ch.

---

### Post by hojat2 on 2014-12-27
you can use cryptsetup instead truecrypt ! 
trueceypt is a Dead Project
install it 
```
sudo apt-get install cryptsetup
```
then make a virtual drive (for example 500 mb)
```
dd if=/dev/zero of=MyDrive.img bs=1M count=500
```
then configure and Enter pass
```
cryptsetup -y -v luksFormat MyDrive.img
```
then map it
```
 cryptsetup luksOpen MyDrive.img MyDrive
```
then format it
```
mkfs -t ext3 /dev/mapper/MyDrive
```
then mount it
sudo mkdir /media/MyDrive```

sudo mount /dev/mapper/MyDrive /media/MyDrive
```
then change permission for "user" user to can write file for no root user
```
sudo chown user:user MyDrive/
 sudo chmod 0700 /media/MyDrive
```
for unmout
```

sudo umount /dev/mapper/MyDrive 
sudo cryptsetup luksClose MyDrive
```

---

### Post by uRock on 2014-12-27
I still use Truecrypt. Here's how I installed it. ```
sudo add-apt-repository ppa:stefansundin/truecrypt
sudo apt-get update
sudo apt-get install truecrypt
```

---

