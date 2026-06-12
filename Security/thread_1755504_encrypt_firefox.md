---
title: "encrypt firefox"
date: 2011-05-11
forum: Security
---

### Post by Saeen on 2011-05-11
Hi,
I was wondering how can i secure my firefox data. There are some extensions for that but i want to know how can i manually do that. Should i have a small disk space as a separate drive and mount it when firefox starts ? What encryption should i use on that fs. Some more information that might be useful plus any links you can share.

Thank You


***EDIT i found one link on ubuntuforums [http://ubuntuforums.org/showthread.php?t=148600&highlight=encfs]("http://ubuntuforums.org/showthread.php?t=148600&highlight=encfs"). If you have more information please share.

---

### Post by bodhi.zazen on 2011-05-11
When you install, select to encrypt home.

---

### Post by lmn. on 2011-05-11
If ubuntu is 100% secure, why would you need to encrypt its data?

just posted this in one of my own threads, but I think its relevant.

```
https://www.eff.org/https-everywhere
```

---

### Post by FuturePilot on 2011-05-11
> **lmn. said:**
> If ubuntu is 100% secure

I don't remember anyone claiming it is. Nothing is 100% secure.

---

### Post by lmn. on 2011-05-11
> **FuturePilot said:**
> I don't remember anyone claiming it is. Nothing is 100% secure.

I've definitely read that somewhere. shame its not..

---

### Post by movieman on 2011-05-11
> **lmn. said:**
> If ubuntu is 100% secure, why would you need to encrypt its data?

Ubuntu is very secure against remote exploits, but if you want protection from local users you need to encrypt your data. Otherwise anyone can boot with a live CD and read any files on the system.

Plus you should always encrypt all files on any computer you travel with in case it's stolen.

---

### Post by lovinglinux on 2011-05-12
> **lmn. said:**
> If ubuntu is 100% secure, why would you need to encrypt its data?

just posted this in one of my own threads, but I think its relevant.

```
https://www.eff.org/https-everywhere
```

As FuturePilot mentioned, nothing is 100% secure. Besides, the OP wants to encrypt the stored data, not the data transfer. The main reason is that several extensions store user information on databases.

@Saeen 	

I would also suggest encrypting the home folder.

However, you might want to use Private Browsing feature of Firefox. There is a rule for add-ons development that extensions should respect private browsing mode to be approved and thus do not store any data.

---

### Post by Saeen on 2011-05-12
Lovinglinux yea but i think the reason i want to encrypt this data is that i want to keep it. I spend time learning stuff like this and then when i come across useful information i like keeping it for future or detailed reading because i normally take an overview. 
#lmn you might be reffering to the firewall section. I remember reading that ubuntu is considered so secure that they dont include any tool like firestarter. That in a way is claiming to be 100% secure. 

One question though the link i pasted in the first post says to create a script and save it in the encrypted folder.
```

#!/bin/sh

cd `dirname $0`
HOME=`pwd` firefox

```
when i run it from my terminal it shows this message:
```

(firefox-bin:6409): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.

(<unknown>:6455): Gdk-CRITICAL **: gdk_drawable_get_display: assertion `GDK_IS_DRAWABLE (drawable)' failed



```
Any ideas ?

---

### Post by lovinglinux on 2011-05-12
> **Saeen said:**
> Lovinglinux yea but i think the reason i want to encrypt this data is that i want to keep it. I spend time learning stuff like this and then when i come across useful information i like keeping it for future or detailed reading because i normally take an overview. 
#lmn you might be reffering to the firewall section. I remember reading that ubuntu is considered so secure that they dont include any tool like firestarter. That in a way is claiming to be 100% secure. 

One question though the link i pasted in the first post says to create a script and save it in the encrypted folder.
```

#!/bin/sh

cd `dirname $0`
HOME=`pwd` firefox

```
when i run it from my terminal it shows this message:
```

(firefox-bin:6409): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.

(<unknown>:6455): Gdk-CRITICAL **: gdk_drawable_get_display: assertion `GDK_IS_DRAWABLE (drawable)' failed



```
Any ideas ?

That tutorial is from 2006. Things change pretty fast on Ubuntu, so I wouldn't use it.

I am not sure if it still valid, but you can try [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

Basically you will create a Private encrypted directory, move the ~/.mozila folder to it and make a symlink from the ~/Private/.mozilla folder to ~/.mozilla.

---

### Post by rookcifer on 2011-05-13
> **lmn. said:**
> If ubuntu is 100% secure, why would you need to encrypt its data?

just posted this in one of my own threads, but I think its relevant.

```
https://www.eff.org/https-everywhere
```

No one ever said it was 100% secure.  Besides, encryption has nothing to do with OS security anyway -- it's only there to stop someone with physical access to your machine from reading the encrypted files.  It does nothing for network security.

Of course, TLS and website encryption is another matter, but all browsers do that automatically anyway.

---

