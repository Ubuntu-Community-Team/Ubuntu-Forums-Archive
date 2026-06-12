---
title: "Wierd files just appeared - hack attempt??"
date: 2010-03-31
forum: Security
---

### Post by iamgeniusrnti on 2010-03-31
I have Ubuntu Ultimate running on an Acer One.  I have the SSH server running on it and I use the key pair to authenticate to my server.  I have the keyboard authentication disabled and I have the authorized keys stored in the /home/<username> dir.

I came home today and discovered two files on my desktop.  One was named De        sktop and the other was named De        sktop.pub.  They were key pairs.  Fortunately they were accessible only by me.  BUt I have no idea how they got there....

Has anyone seen this before?

---

### Post by Agent ME on 2010-04-01
I would guess that when generating your keys or moving them to where they needed to go, you made extra copies on your desktop. Are they the same as your keys in your ~/.ssh folder? Using "md5sum *filename*" on several files and comparing is an easy way to see if they have the same content.

---

### Post by iamgeniusrnti on 2010-04-01
I don't know, I deleted the keys and intend to generate new ones when I get a chance.
 
You noticed how there were spaces in the file names?  That wasn't a typo.  Those were the actual files' names!
 
I checked teh auth_logs and didn't see anything unusual, so I guess I'm fine...

---

### Post by wirelessmonkey on 2010-04-01
Are you running VNC? (Remote desktop)

---

### Post by iamgeniusrnti on 2010-04-01
> **wirelessmonkey said:**
> Are you running VNC? (Remote desktop)

Why yes I am.  I remote control my desktop thru an ssh pipe on my Droid.

---

### Post by cdenley on 2010-04-01
> **iamgeniusrnti said:**
> Why yes I am.  I remote control my desktop thru an ssh pipe on my Droid.

Did you check the box which uses upnp to port forward on your router allowing anyone to connect over the internet?

---

### Post by iamgeniusrnti on 2010-04-01
> **cdenley said:**
> Did you check the box which uses upnp to port forward on your router allowing anyone to connect over the internet?

Firstly, thank you for your valuable time!

Ok, no I did NOT check the UPNP box.  In fact, 5900 and 5901 is blocked on the router.  The only way into VNC is thru the other computer in the house OR by connecting via ssh and then port forwarding over the connection.

To connect to my ssh server you MUST use a key pair as it will reject user name/pass.

There are only two keys in my auth_keys file and both private keys are stored on my Droid and passphrased.  The auth_keys file is chmodded to prevent tamper but I don't remember what the permission was now.  Only sudo can modify.

Maybe they aren't key pairs afterall, I just assumed they were?

---

