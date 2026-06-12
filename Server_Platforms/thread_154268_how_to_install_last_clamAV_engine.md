---
title: "how to install last clamAV engine?"
date: 2006-04-02
forum: Server Platforms
---

### Post by milen on 2006-04-02
Is there any way to install the latest clamAV engine (0.88), for example, from a .deb file? Why doesn't this system support installation of a NEW antivirus engine? There is a libgmp3 file missing. This is not the same as libgmp3c2. I began thinking it's been done for a purpose. Need we hear again all this bullshit talk about Linux free of viruses?! There are tens of thousands of viruses for Linux. That's just binary files, man.
In short, if you are not so optimistic and have run through this, can you tell me if there is some way to install that last clamAV engine? Please don't tell me just "source tarball". I'm really suspicious that there is a man in the world capable of installing clamAV 0.88 source tarball on Ubuntu system. Bur if you've tried and done it, please tell me how.

---

### Post by rcerreto on 2006-04-03
Try adding this to /etc/apt/sources.list :

> deb [http://ftp2.de.debian.org/debian-volatile](http://ftp2.de.debian.org/debian-volatile) sarge/volatile main

then you'd be able to install/update clamav via apt-get.


HTH

---

### Post by wh0rd on 2006-04-03
> W: GPG error: [http://ftp2.de.debian.org](http://ftp2.de.debian.org) sarge/volatile Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7EF7FFF4276981F4
W: You may want to run apt-get update to correct these problems

I get that message in the end after a "apt-get update"

---

### Post by rcerreto on 2006-04-04
That's only a warning, informing you that apt-get could not verify the packages signature.
To get rid of it, you might want to import the needed key:
> gpg --keyserver subkeys.pgp.net --recv-keys 7EF7FFF4276981F4
gpg --export --armor 7EF7FFF4276981F4 | sudo apt-key add -

---

### Post by Chareos on 2006-04-13
Hi ! I'm trying to do the same, but having dependancies problem:

I can't update libclamav1 cause it requires libgmp3... while on kubuntu I find libgmp3c2


Any suggestions ?


Thanks

---

### Post by ebutton on 2006-04-13
[QUOTE=rcerreto]That's only a warning, informing you that apt-get could not verify the packages signature.
To get rid of it, you might want to import the needed key:[/QUOTE]

Thanks!  I too was stuck, not knowing how to get the correct new key.

EdB

---

### Post by kvdbreem on 2006-12-16
I get the following when I try to install.  Sounds like they don't have things set up properly.  Luckily there are other mirrors for the deb packages at :

[http://www.clamav.net/binary.html#pagestart](http://www.clamav.net/binary.html#pagestart)

Here's the error message:

```
$ sudo apt-get install clamav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  clamav: Depends: libclamav1 (>= 0.88.7) but 0.88.4-1ubuntu2 is to be installed
E: Broken packages
$ sudo apt-get install 0.88.4-1ubuntu2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 0.88.4-1ubuntu2
```

---

### Post by Jad on 2006-12-21
got same problem here too

---

### Post by Cactus Sediento on 2007-01-17
Same problem here....updated with Synaptic using the above repository



> clamav:
  Depends: libclamav1 (>=0.88.7) but 0.88.4-1ubuntu2.1 is to be installed


libclamav1:
 Depends: libgmp3  but it is not installable


any suggestion?

---

