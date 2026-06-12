---
title: "encryption methods"
date: 2007-11-27
forum: Server Platforms
---

### Post by eagleeyes on 2007-11-27
Here is a question: I work in law enforcement and so most of the material I work on or with is fairly incriminating and I wish to secure my data as best as possible. I have a couple of questions on how to do this and whether or not they are practical. I am also a newbie of sorts
1st: Is there a way to use the key-gen feature to secure the folder (like putting the private key or public key for that matter on a usb drive?
2nd: Is there a method of partitioning the hard drive with a password protect? is this even worth doing?
3rd: I eventually want to make an ssl server out of my hard drive so while I am out on my laptop I can access (not add or remove but read-only access) while on location. I dont know alot about computers but in other things, an opening is still an opening. is this a valid concern? ( I have removed root access on the ssh already)
4th: what other avenues should i be researching into? In the wide world of encryption and protection I am still learning, if you know of specifics I should learn about to better understand this process please point them out.

Thank you

---

### Post by bpny on 2007-11-27
I would check out Truecrypt at [http://www.truecrypt.org]("http://www.truecrypt.org") also you can install Ubuntu fully encrypted with the alternate install cd,[http://forums.truecrypt.org/viewtopic.php?t=7935]("http://forums.truecrypt.org/viewtopic.php?t=7935")

---

### Post by HermanAB on 2007-11-28
Read up on truecrypt and dmcrypt.

Cheers,

H.

---

### Post by stimpack on 2007-11-28
I would recommend EncFS, very simple to setup and use. It has the advantage that it is on the fly file encryption and not block encryption. Your data will be much more resilient to data corruption. Disadvantage to EncFS is your files appear as files and while the names are obscured, filesizes and creation dates remain.

Truecrypt's advantages like plausible deniability are of more use to people being pursued by law enforcement and not much use to law enforcement.

---

### Post by sciurus on 2007-11-29
The first thing you should do is encrypt your entire hard disk. Back up all your data, then install Ubuntu using the alternate install cd. During the disk setup process, select the option "Set up encrypted LVM". There is a walkthrough with pictures [here]("http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml"). This is easier and better supported then Truecrypt. This is very secure as long as you use a strong password.

For securely accessing files remotely, you should install the openssh-server. Next, set it up to use [public key authentication]("https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30").

---

