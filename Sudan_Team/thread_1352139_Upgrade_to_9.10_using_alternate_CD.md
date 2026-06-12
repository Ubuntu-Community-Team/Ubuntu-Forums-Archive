---
title: "Upgrade to 9.10 using alternate CD"
date: 2009-12-11
forum: Sudan Team
---

### Post by zero-n on 2009-12-11
How to upgrade Ubuntu using **[COLOR="Red"]alternate CD[/COLOR]** :


1- Download alternate CD image .

_**Direct link :**_
[**[COLOR="red"]AMD64[/COLOR]**]("http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-amd64.iso")
[**[COLOR="Red"]i386[/COLOR]**]("http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-i386.iso")

**_Torrent:_**
[**[COLOR="Red"]AMD64[/COLOR]**]("http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-amd64.iso.torrent")
[**[COLOR="red"]i386[/COLOR]**]("http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-i386.iso.torrent")



2- Run this command to mount the image.

```
sudo mount -o loop **[COLOR="red"]PATH[/COLOR]**/ubuntu-9.10-alternate-i386.iso /media/cdrom0
```

change **[COLOR="Red"]PATH[/COLOR]** to your CD image path.



3- Run update manager from CD.

```
gksu "sh /cdrom/cdromupgrade"
```

4- Enjoy upgrading.

---

### Post by mhmdfoss on 2009-12-12
thanks alot
this way is more secure than direct update from the internet
as you know our internet is very slow and always interrupt

---

### Post by zero-n on 2009-12-12
yeah.

btw the upgrade manager will ask you if you want to download new updates while upgrading if you choose [COLOR="Red"]**YES**[/COLOR] it will download the new software updates & if you choose **[COLOR="Red"]NO[/COLOR]** you need to run this command after upgrade is done to update you software.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mhmdfoss on 2009-12-12
yep

thank u again:o

---

