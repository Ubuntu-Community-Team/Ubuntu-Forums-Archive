---
title: "vsftp on UBUNTU Server 7.04"
date: 2009-11-07
forum: Server Platforms
---

### Post by mmistroni on 2009-11-07
hi all
 i have an ubuntu server on which i want to install vsftp.
i followed instructions here
[https://help.ubuntu.com/7.04/server/C/ftp-server.html](https://help.ubuntu.com/7.04/server/C/ftp-server.html)

but when i tried to install i got this message

Failed to fetch [http://gb.archie.ubunut.com/ubuntu/pool/main/v/vs0.5-2ubuntu2_i386.deb](http://gb.archie.ubunut.com/ubuntu/pool/main/v/vs0.5-2ubuntu2_i386.deb)  404 not found

i tried to run apt-get update but had no luck

anyone can tell me how can i amend my sources.list so that i can get vsftp?

thanks and regars
 marco

---

### Post by enbeto on 2009-11-07
Are you runing Ubuntu 7.04 on that server? If that is the case I'm afraid the ubuntu repositories are no longer available as the version is no longer supported since October 2008....

---

### Post by enbeto on 2009-11-07
You could try adding Hardy repositories. Just edit your sources.list and change Fesity by Hardy.

---

### Post by mmistroni on 2009-11-07
enbeto,
 thankx but last time i tried it messed up my whole server
plus my ubuntu server is on a virtual host...  

any other ftp packages i can use on 7.04?

regard
s marco

---

### Post by enbeto on 2009-11-10
Hi Marco,

ups, so no idea... Maybe you could try to download manually the vsftpd package and also all the dependencies from here
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

On the other hand, I think that as long as you don't make an upgrade of the system with the new repositories it wouldn't have to be any problem if you just install vsftpd and imediately disable the new repositories...  In fact, it would be the same result as installing manually the package as I'm proposing you above....
Sorry, but I'm not having other ideas...

---

### Post by Lars Noodén on 2009-11-10
It can avoid trouble by keeping all package management under the control of the package manager.  Try apt-pinning to use a special repository for a specific package:

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

See also

[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)
[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)

Even if you decide to download and compile a program, it is best if you can do that in the context of making your own package.  

[http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html#s-equivs](http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html#s-equivs)

At some future point when you upgrade from 7.04, you might at the same time leave FTP behind and replace it with SFTP.  There is an sftp subsystem built into openssh-server and you probably already have it installed.  It is active by default, and chrooting it is a matter of changing only a line or two in the configuration file.

---

