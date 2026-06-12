---
title: "how to auto format hdd with X amount of incorrect login attempts?"
date: 2009-04-22
forum: Security
---

### Post by gkc01 on 2009-04-22
Hello,

I don't know if this is possible yet on Ubuntu, I found some software called SecureGuard that does the trick but I don't think it will work on Ubuntu.

I have some very sensitive data on my notebook. I have encrypted my hdd and you need a 16 character password to get though it.

I would like to know if there is a way you could automatically format the hdd after x amount incorrect login attempts. Yea yea, I know this is not the movies! 

Any help with this would be appreciated.

Thanks,

Greg

---

### Post by euler_fan on 2009-04-22
Assuming the encryption is strong and the password is hard, then there's no reason to do this. The whole point of encrypting a hard drive is to protect the data it contains in the event of loss.

---

### Post by mrobaer on 2009-04-22
That would be somewhat like a DoS attack.  Just keep trying to log in until it formats itself.  :o  I surly hope you have backups of this sensitive data.....

---

### Post by tommynz1975 on 2009-04-22
it sounds quite logical. if one can have an account locked after X failed log in attempts, then assuming you have set your system to boot in as root then it could format your hdd. 

Ths brings up yet another question. I dont think you can format a mounted HDD..  Can you just not put your home directory on its own partition and set the partition as hidden? 


[LIST]
[*]Maybe use SRM for file deletion and use its set of utilitys to delete the swap and whats stored on the ram... on a regular basis.
[*] I think the whole package is called secure-delete
[/LIST]

```
sudo apt-get install secure-delete
```

---

### Post by avolknet on 2011-09-15
Hi all !

I would like to know how to setup after x failed login enterys the sistem automatick starts to delete partition. I need it for security reasons. The so that the person ho uses the server is only me if someone else starts to do somethings so that he wount get my files or information.

Can some one please help me ?

---

### Post by Sc0urgeTR on 2011-09-15
Quick he's got a 16 character long password! Lets steal his emotionally unstable datas!

No you can't format a mounted drive. Stick another HDD in there and have the sensitive data on it and you could set it up. Write your own script and be like POW own that HDD.

What does DoS have to do with loggin attempts? >_> I'm going to DoS your network and it will be a living packet that jumps out of your rj45s and plug in passwords bruteforce style woooh. Have some carrot juice.

---

### Post by Sc0urgeTR on 2011-09-15
Subnote if you're really worried about sensitive data being seen you'd have to format it several passes. Formatted hard drives can be recovered. (lol kiddie pr0n?)

---

### Post by Sc0urgeTR on 2011-09-15
> **avolknet said:**
> Hi all !

I would like to know how to setup after x failed login enterys the sistem automatick starts to delete partition. I need it for security reasons. The so that the person ho uses the server is only me if someone else starts to do somethings so that he wount get my files or information.

Can some one please help me ?

Why do you need a  server if it's only for you? Take it offline and no one will have access to it.

---

### Post by bodhi.zazen on 2011-09-16
> **avolknet said:**
> Hi all !

I would like to know how to setup after x failed login enterys the sistem automatick starts to delete partition. I need it for security reasons. The so that the person ho uses the server is only me if someone else starts to do somethings so that he wount get my files or information.

Can some one please help me ?

Use encryption.

---

