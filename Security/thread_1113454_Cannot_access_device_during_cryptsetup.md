---
title: "Cannot access device during cryptsetup"
date: 2009-04-01
forum: Security
---

### Post by yeehi on 2009-04-01
I am trying to follow the Automatically Unlock LUKS Encrypted Drives With A Keyfile tutorial [here]("http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile").

At the command below I receive an error message:

```
sudo cryptsetup luksAddKey /dev/sdX /root/keyfile
Command failed: Can not access device
```

What should I do?

This is an AMD64 alternate installation of Jaunty Jackalope.

---

### Post by bodhi.zazen on 2009-04-01
you need to specify the device

sdxy or sdx needs to change to the proper patition

/dev/sda1

if you do not know the partition see :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

probably same with /root/keyfile , unless you named it "keyfile"

---

### Post by yeehi on 2009-04-01
Oh thank you for such swift help! :)

So, would I use ```
/dev/mapper/sdb5_crypt
``` instead of ```
sdxy
```?

```
sudo cryptsetup luksAddKey /dev//dev/mapper/sdb5_crypt /root/keyfile
```


If I wanted to do the same thing for other encrypted partitions, such as /opt and /home, would I need to do something extra or different?

Thank you very much, again!

---

### Post by bodhi.zazen on 2009-04-01
no, no, the other /dev, :lolflag:

In your case I think /dev/sda5

---

### Post by yeehi on 2009-04-01
```
sudo cryptsetup luksAddKey /dev/mapper/sdb5 /root/keyfile 
[sudo] password for ****: 
Command failed: Can not access device

****ubuntu:~$ sudo cryptsetup luksAddKey /dev/mapper/sda5 /root/keyfile 
Command failed: Can not access device

```

I still can´t get it to go... :confused:

---

### Post by bodhi.zazen on 2009-04-01
Where did you get mapper from ?

```
sudo cryptsetup luksAddKey /dev/sdb5 /root/keyfile
```

---

### Post by yeehi on 2009-04-01
That  worked! 

I went through the instructions and rebooted; however, I had to manually enter all the encryption passwords again. The boot didn´t go straight to the login screen, either.

I think the problem is what I entered here:

> LUKS devices need to create a mapper that can then be referenced in the fstab. Open /etc/crypttab

sudo nano /etc/crypttab

and add then a line like this:

sdX_crypt      /dev/sdX  /root/keyfile  luks


I entered the following line into fstab: 

```
sdb5_crypt      /dev/sdb5  /root/keyfile  luks

```

---

### Post by bodhi.zazen on 2009-04-01
You need an entry for /etc/crypttab as well as /etc/fstab

That entry goes in /etc/crypttab

---

### Post by hyper_ch on 2009-04-02
Is my howto so unclear?

---

### Post by yeehi on 2009-04-03
Thanks for your great How To, hyper_ch!

I think it was aimed at people with a lot more working knowledge than I have.

At the moment, my system boots, but I still always have to enter all the passphrases.

If you could add some more lines to explain what is needed, that would be a big help for me. I have created a separate /opt partition, too.

I hope I can undo what I have done, so that I can boot normally again :oops:

er, actually, I think I had better start this again. What is the simplest way to undo my earlier efforts?

---

