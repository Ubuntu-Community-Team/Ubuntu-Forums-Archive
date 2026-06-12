---
title: "Kubuntu 5.04 repository problems"
date: 2005-04-11
forum: Repositories &amp; Backports
---

### Post by Vertical on 2005-04-11
hello
my sources.list is:

```
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb http://ru.archive.ubuntu.com/ubuntu/ hoary main restricted
deb-src http://ru.archive.ubuntu.com/ubuntu/ hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://ru.archive.ubuntu.com/ubuntu/ hoary-updates main restricted
deb-src http://ru.archive.ubuntu.com/ubuntu/ hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ru.archive.ubuntu.com/ubuntu/ hoary universe
deb-src http://ru.archive.ubuntu.com/ubuntu/ hoary universe

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted

deb http://security.ubuntu.com/ubuntu/ hoary-security universe
deb-src http://security.ubuntu.com/ubuntu/ hoary-security universe

deb http://ru.archive.ubuntu.com/ubuntu/ hoary multiverse
deb-src http://ru.archive.ubuntu.com/ubuntu/ hoary multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

deb http://www.bootsplash.de/files/debian/ unstable main
deb http://ubuntu.tower-net.de/ubuntu/ warty java

deb ftp://ftp.snt.utwente.nl/pub/linux/debian unstable main
```

After updating repository info I recieve this errors:

```
W: GPG error: ftp://ftp.snt.utwente.nl unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1D53D8C4F368D5D
W: GPG error: ftp://ftp.nerim.net stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: ftp://ftp.nerim.net unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: ftp://ftp.nerim.net testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
```

Also, I want to install j2re from synaptic. But then I select 'sun-j2re.1.5' and click apply, synaptics says:

```
sun-j2re1.5:
Depends: sun-j2re1.5debian  but it is not installable
```

what's wrong with it?

---

### Post by humanity_to_others on 2005-04-11
[QUOTE=Vertical]
After updating repository info I recieve this errors:

```
W: GPG error: ftp://ftp.snt.utwente.nl unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1D53D8C4F368D5D
W: GPG error: ftp://ftp.nerim.net stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: ftp://ftp.nerim.net unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: ftp://ftp.nerim.net testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
```

Also, I want to install j2re from synaptic. But then I select 'sun-j2re.1.5' and click apply, synaptics says:

```
sun-j2re1.5:
Depends: sun-j2re1.5debian  but it is not installable
```

what's wrong with it?[/QUOTE]
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

---

### Post by Vertical on 2005-04-11
I read ubuntu FAQ about java, but really I don't like this solution. I want to be able to easy uninstall package I installed, but ubuntuguide's solution doesn't give me such privilegies..  :-? 
How to get it working from installing .deb packages?

---

### Post by mendicant on 2005-04-11
The entry in that guide is a little odd, not to mention that somebody besides Sun is distributing the JRE, which I suspect is a no-no.  You just want to follow the directions here:

[http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)

Under method 2.  This will work under hoary.

---

### Post by Chibi on 2005-04-13
That first "error" Isn't a problem, it's that the older repositories haven't been GPG signed yet. It's not going to be a fast transition, and as long as you have extra repositories, at least for a year or so, you will get that error. :D

---

