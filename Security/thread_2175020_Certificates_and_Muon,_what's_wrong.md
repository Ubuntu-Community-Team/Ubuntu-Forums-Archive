---
title: "Certificates and Muon, what's wrong?"
date: 2013-09-17
forum: Security
---

### Post by satnrzn on 2013-09-17
Hi.
 Please excuse me for a very poor knowledge of my english language.
I recently reinstalled Kubuntu 13.04 X64 . recently I opened  Muon (Center Application) and there was a warning that the image. Warning that the certificate is not valid and can not be verified.I am a long time user Ubuntu, but that he saw for the first time.
[[IMG]http://storage8.static.itmages.ru/i/13/0917/s_1379395495_3292167_25830a6eb3.png[/IMG]]("http://itmages.ru/image/view/1222158/25830a6e")
A disk image is an official, was downloaded from here [http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/](http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/)
The system software from the very Kubuntu repositories and Launchpad.
Moun and when he opened it there was a warning, was a short-term problem with the Internet. Maybe it's because of the problems with the Internet work?More warnings were not.
 Should I worry about this? Or was it just what that bug?
Thanks!

---

### Post by oldos2er on 2013-09-18
Does ```
sudo apt-get update && sudo apt-get upgrade
``` show any errors?

---

### Post by satnrzn on 2013-09-19
Good morning. Yes, when you try to update a mistake.The key is not available this repository [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) raring-getdeb games.
Although on a different laptop with Kubuntu 13.04 x86 architecture - error when updating the link to the key repository is not available - were, but with certificates - no.
In general, I did not like how the Kubuntu x86_64.I put in the EFI. Lots of bugs. X86 architecture is much better. Put back on this laptop Ubuntu 12.04 x86..The theme can be considered solved and probably close.
Perhaps it is not a terrible problem was, when the system has only officially repositories
**oldos2er **I am very grateful for their assistance. All the best to you.
And once again I'm sorry for my very poor knowledge of the English language.

---

### Post by oldos2er on 2013-09-20
You can get the key with ```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -

sudo apt-get update
```

Your English is very good, no need to apologize.

---

