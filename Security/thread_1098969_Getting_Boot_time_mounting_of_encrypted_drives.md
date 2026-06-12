---
title: "Getting Boot time mounting of encrypted drives"
date: 2009-03-17
forum: Security
---

### Post by jbrown96 on 2009-03-17
I have an encrypted partition on my system, and while I have created a simple script that keeps me from having to type so much (I used to have to type sudo cryptsetup luksOpen /dev/sdaX a && sudo mount /dev/mapper/a ./media/) now I just run the script and type my passphrase. 

What I would like to do is basically use the same script, but have it run during boot up, so I can mount it then. The reason is that I always seem to forget to mount the partition and then I open Amarok and since there isn't anything in ./media/ my music db is gone and has to be recreated. 

The thing is that I don't always want to mount the encrypted partition (since my passphrase is so long), so I would like an option (maybe yes/no, ^c, or something similar) and possibly a time out. I can probably figure all of this out in my script, but I just need a couple of things answered. 
1) Where do I put the script to make it execute on boot? 
2) How do I make sure the boot process waits for user input?
3) How do I make sure that the correct modules have loaded first?

Would there be a way to have the same prompt that shows when full-disk encryption is used with the Alternate CD?

---

### Post by dusan.saiko on 2009-03-18
I was following this howto when encrypting my system
[http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu)

just adding a line into /etc/crypttab asks me for a password on computer boot
.

---

### Post by jbrown96 on 2009-03-18
Are you able to bypass it if you don't want to mount it?

---

