---
title: "Password Mamager"
date: 2020-04-24
forum: Security
---

### Post by makitso on 2020-04-24
I have kicked around the idea of using a password manager but never done so.  I have several Ubuntu machines, one Windows laptop, an Android tablet and phones plus one (ick) iPad.  My question is, what product do you use and would it work for me.

Thanks in advance.

---

### Post by crip720 on 2020-04-24
I use Lastpass myself. it is cloud based, has a good free version or you can have pay version.  Free version does everything I need well.  Would suggest looking into others as some are local(USB or on computer only),  A password manager is very good to have.  Think with most you need to remember/write down main password because very difficult to replace or log back in with out it, they usually don't have easy email way of giving new password.

---

### Post by kevdog on 2020-04-27
I'm a big fan of Bitwarden -- open source. They also have a free tier similar to Last Pass. It's also possible to run your own Bitwarden server if you are so inclined so you personally control all your data and passwords.  I personally run a Bitwarden_RS server which runs on docker inside a Linux VM.  Took a little time to set up but wasn't too difficult.  I've been in the test phase for about 3-4 months and I really haven't had any problems -- in fact it's quite "boring".

---

### Post by TheFu on 2020-04-27
keepassxc. it  is F/LOSS and maintained. The DB is well-supported by keepass versions on all platforms.  TNO.  Don't trust cloudy services.

Getting the encrypted DB onto all the different devices can be accomplished using rsync, dropbox, nextcloud, seafile, wormhole, or any other method.  i use rsync, nightly.   KeepassXC supports using 2FA, like a yubikey, but some of the other platform versions do not which would make opening the DB impossible on other platforms.

TNO.

---

### Post by ahbart on 2020-04-29
> **kevdog said:**
> I'm a big fan of Bitwarden -- open source. They also have a free tier similar to Last Pass. It's also possible to run your own Bitwarden server if you are so inclined so you personally control all your data and passwords.  I personally run a Bitwarden_RS server which runs on docker inside a Linux VM.  Took a little time to set up but wasn't too difficult.  I've been in the test phase for about 3-4 months and I really haven't had any problems -- in fact it's quite "boring".
I've exactly the same. Bitwarden_rs on my own server. VPS in my case. It is running very stable and I created account for my whole family.
There are excellent aps for different devices and plugins for chrome, firefox and safari. maybe more.

---

### Post by TheFu on 2020-04-29
> **ahbart said:**
> I've exactly the same. Bitwarden_rs on my own server. VPS in my case. It is running very stable and I created account for my whole family.
There are excellent aps for different devices and plugins for chrome, firefox and safari. maybe more.

A VPS?  Someone else's computer on someone else's network? Really?

---

### Post by ahbart on 2020-04-29
> **TheFu said:**
> A VPS?  Someone else's computer on someone else's network? Really?

I do really know what you mean. VPS is a [Virtual Private Server](https://en.wikipedia.org/wiki/Virtual_private_server).

---

### Post by EuclideanCoffee on 2020-04-29
TheFu is referring to the wise advice to not place what you consider private onto a computer you do not have physical access to. Your passwords would be considered private data. Someone could hack the subnet your computer is on and retrieve your database. It's better to put this on a physical computer on your local network if possible.

---

### Post by ahbart on 2020-04-29
Yes that would be better. But the database is encrypted. [link](https://bitwarden.com/help/article/what-encryption-is-used/) . 
I've used keepass for many years. You have to sync / copy the database to different devices all the time. Then Bitwarden is much user friendly.

---

### Post by EuclideanCoffee on 2020-04-29
Yes, you're likely fine if you follow some basic security policies. For VPS security, I recommend this as a basic guide: [https://www.digitalocean.com/community/tutorials/7-security-measures-to-protect-your-servers](https://www.digitalocean.com/community/tutorials/7-security-measures-to-protect-your-servers)

---

### Post by TheFu on 2020-04-29
> **ahbart said:**
> Yes that would be better. But the database is encrypted. [link](https://bitwarden.com/help/article/what-encryption-is-used/) . 
I've used keepass for many years. You have to sync / copy the database to different devices all the time. Then Bitwarden is much user friendly.

Keepassxc has a CLI version, so if you have ssh access then you can get any credentials needed. For example:
```
$ keepassxc-cli show -a UserName -a Password   ~/tf-passwds.kdbx   '/Internet/Ubuntu Forums' 
```

Setup a nextcloud server that syncs selected files to our devices.  scp is really easy too. Most credentials aren't needed on all devices immediately, if ever. Waiting until the nightly sync isn't really any hardship.

---

### Post by EuclideanCoffee on 2020-04-29
Oh yes, nextcloud snap works great if you don't care to get into the weeds.

---

