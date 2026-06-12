---
title: "Security Concerns"
date: 2010-03-30
forum: Security
---

### Post by krmboya on 2010-03-30
Hi.
 I've been using Ubuntu Linux 9.04 for a few months now and I'm a strong supporter of Open source and open systems.
Recently a friend of mine boasted that he could 'crack' my user account and went on to boot in recovery mode and actually managed to change my account password leaving me with no way to log onto my own machine.
This left me worried on security implications that such an incident could have, and if an account could be cracked so easily, it would prevent uptake of Ubuntu by the masses.
Is there a way a computer owner can prevent this?

---

### Post by sisco311 on 2010-03-30
Once one has physical access to a computer, no OS is secure. 

Encryption is the only way if you have sensitive data, even then they could install a new OS.

[thread=989517]Physical access is root access[/thread]

---

### Post by yeleek on 2010-03-30
What your friend most likely did...

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

And as per sisco311 - encryption is only defense for a home user (business users may have secure data centers for their servers, so actually have far higher physical security).

---

### Post by tubbygweilo on 2010-03-30
Full disk encryption when installing via an alt install disk but don't forget or loose your pass phrase and take lots of encrypted backups!

---

### Post by a.walker on 2010-03-30
You should take a moment to think about what sorts of security threats your computer will face. Do people often have unsupervised physical access to your computer? I have a desktop system. When I thought about it, I realized that the odds of someone breaking into my house and accessing my computer with nefarious intent are vanishingly small.

If I encrypt my important data and take lots of measures to keep people out of my computer, I just increase the risk of me losing my important data by forgetting passphrases and locking myself out of my computer.

---

### Post by Nisal on 2010-03-30
yeah encrypt your data and even encryption is not 100% safe bcz for a long time i belived "true crypet" was a good encrypting tool but recently it had been crack by 14 years guy..
so u can't except 100% secure from anything ( nor from windows or linux)
what u can do use a better encryption method and long and complex passwords

---

### Post by iponeverything on 2010-03-30
As it has been mentioned, if you don't want some clown messing with your system, like your buddy -- don't let them have physical access or encrypt your disk. Even then, what's to keep him unplugging it from wall and walking away it.. He might not be able to read your data, but he will "own" it.  Download the UBCD and you will be able to do the same thing to his windows box with physical access, in about a minute.

---

### Post by tubbygweilo on 2010-03-30
> **Nisal said:**
> yeah encrypt your data and even encryption is not 100% safe bcz for a long time i belived "true crypet" was a good encrypting tool but recently it had been crack by 14 years guy..

Nisal, could you please point me to the cracking of Truecrypte. I have recommended the use of Truecrypt to others and would like to review my recommendations if needed.

Many thanks.

---

### Post by Nisal on 2010-03-30
> **tubbygweilo said:**
> Nisal, could you please point me to the cracking of Truecrypte. I have recommended the use of Truecrypt to others and would like to review my recommendations if needed.

Many thanks.

This is one part,this shows how its been unsecured,and il post the link about that news i could't remember where i found that 

> howed on black hat how to disable truecrypts encryption
he used a mbr rootkit this rootkit loads the bootloader of 
truecrypt and modifyes the i/o-interrupt 13h handle 
to "double forward" it ... ^^



also some news to mbr rootkits...
they will be outdated in the near futer cause
unwanted changes can be detected by the mbr hash
by using the tmp module... 

---

### Post by krmboya on 2010-03-30
Now guys, if for example someone uses Ubuntu instead of windows in an internet cafe. Does that mean that anyone who has mastered just a single command will be able to run all the machines as root?
At least for Windows one has to do some searching to find whatever software he'll use to crack the Admin account.

---

### Post by iponeverything on 2010-03-30
> **krmboya said:**
> Now guys, if for example someone uses Ubuntu instead of windows in an internet cafe. Does that mean that anyone who has mastered just a single command will be able to run all the machines as root?

It is easy enough to lock down a kiosk type machine, my guess is for special cases like a internet cafe the same could be done. Anyone running this type of business probably would not want to use linux anyway, you want something the customers are comfortable and familiar with.

> **krmboya said:**
> 
At least for Windows one has to do some searching to find whatever software he'll use to crack the Admin account.

same deal as above, taking special precautions with regard to the configuration of the box and reloading the os image often will mitigate the risk to large degree. And again, internet cafe's are not a normal case.

To each their own. I have used linux since 1993 and I trust it. I specialized in OS design and understand very well that OS's are not one size fits all. I have never had my box cracked or otherwise needed to reinstall because my system degraded on its own over time. Its always been very easy to get a view into what is going on under the hood, good luck with that under windows. 

To have someone show you a simple card trick as proof of anything is, at best, trying to look smart and at worst deceptive.

---

