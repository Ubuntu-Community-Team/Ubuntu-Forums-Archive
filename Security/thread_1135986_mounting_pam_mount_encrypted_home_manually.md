---
title: "mounting pam_mount encrypted home manually?"
date: 2009-04-24
forum: Security
---

### Post by relet on 2009-04-24
Dear all,

After an upgrade to jaunty, pam_mount fails to decrypt my encrypted home. If there are any well-known issues with jaunty/pam_mount/cryptoloop, I'd be happy for any pointers. Google hasn't been my friend so far. 

However, now that auto mounting fails, I would really like to try so manually. The relevant part of /etc/security/pam_mount.conf.xml reading
```
<volume fskeycipher="aes-192-ecb" options="loop,exec,encryption=aes,keybits=192" fskeypath="/data/home/me.key" user="me" mountpoint="/home/me" path="/data/home/me.img" fstype="auto">  
```my best guesses so far were

```
losetup -e aes -k 192 /dev/loop0 /data/home/me.img
-or-
losetup -p0 -e aes -k 192 /dev/loop0 /data/home/me.img < data/home/me.key 
```which fail to provide any mountable fs on the loop device. What would be the correct command?

Thanks a lot in advance,
=relet=, currently homeless.

---

### Post by cbkm on 2009-04-27
Hi,

I encountered a similar problem after my upgrade to Jaunty, could you have a read-over my blog where I've written this up:-

[http://www.kennynet.co.uk/2009/04/27/ubuntu-jaunty-upgrade-encrypted-home-not-mounting/](http://www.kennynet.co.uk/2009/04/27/ubuntu-jaunty-upgrade-encrypted-home-not-mounting/)

Let me know if that helps you get yours sorted (and maybe add a comment to the referenced Launchpad bug if it helps), thanks!

Edit: Oh, FWIW, you could try something like:-

```

# losetup /dev/loop0 /data/home/me.img
# openssl enc -d -aes-192-ecb -in /data/home/me.key | cryptsetup -c aes -s 192 create crypt-me /dev/loop0 
# mount /dev/mapper/crypt-me /home/me

```

(The above works for me, only I don't use /dev/loop0, just /dev/sda3 so I've kinda just thrown in the losetup / loop device without any real testing.)

---

### Post by jpmcc on 2009-04-28
> **relet said:**
> 
After an upgrade to jaunty, pam_mount fails to decrypt my encrypted home.

I used [http://tinyurl.com/tcrypt](http://tinyurl.com/tcrypt) to encrypt my home directory using Truecrypt - since upgrading to Jaunty, it's stopped working. The new version of pam_mount appears to have retired the “use_first_pass” option - maybe there are other changes.

John

---

### Post by relet on 2009-04-28
Thanks a lot, all and cbkm especially. The following succeeded to mount the data manually.
[FONT=monospace]
[/FONT]```
openssl enc -d -aes-192-ecb -in /data/home/me.key | losetup -e aes -k 192 -p0 /dev/loop0 /data/home/me.img

```

I haven't succeded to auto mount it yet with your package, but I will keep trying for a bit and give you feedback, cbkm.

---

### Post by cbkm on 2009-04-28
@relet: Glad you've been able to mount your home partition. Hmm, strange it doesn't work for you. 

Things to try/do:-

1. Can you show me what your <volume ...> block looks like now, you should have adjusted it in line with my blog... :)

2. Enable the debug option in /etc/security/pam_mount.conf.xml and then in a terminal do: 
```

$ su - $USER

```

It should print out a whole bunch of debug information to the terminal, paste that here. :)

---

