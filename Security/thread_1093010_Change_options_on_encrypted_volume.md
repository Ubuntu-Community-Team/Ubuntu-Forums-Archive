---
title: "Change options on encrypted volume"
date: 2009-03-11
forum: Security
---

### Post by julian.evans on 2009-03-11
Hi,

I used to ubuntu installer to create an encrypted filesystem for myself without completely knowing what I was doing. Everything seems to be working fine except it prompts me for my passphrase twice because I set up the swap wrong somehow and used a passphrase instead of a random key. Is there a way to change the options on the disk without reformating/reinstalling Ubuntu? Thanks!
Julian

---

### Post by Tubes6al4v on 2009-03-11
[http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

For some reason I kept getting the response that I could not load the volume. You may need to do this from a live CD.

---

### Post by hyper_ch on 2009-03-11
either add a keyfile as the previous poster pointed out or re-create the swap partition with random key (see my other howto:  [http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04-p4](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04-p4) )

---

