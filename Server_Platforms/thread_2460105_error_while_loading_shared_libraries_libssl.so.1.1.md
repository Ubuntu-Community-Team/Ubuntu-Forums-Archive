---
title: "error while loading shared libraries: libssl.so.1.1: invalid ELF header"
date: 2021-04-02
forum: Server Platforms
---

### Post by swcoffin on 2021-04-02
Ubuntu server 20.04.

After a power outage I could not connect to Ubuntu server with webmin, and webmin reported that libnet-ssleay-perl was not installed.  I know it is though.

After more investigation I find that openssl must be corrupted. 'openssl version' reports 'error while loading shared libraries: /lib/x86_64-linux-gnu/libssl.so.1.1: invalid ELF header'.

I've tried 'apt-get --reinstall -install' on openssl, libnet-ssleay-perl, etc. without any success and searches of invalid ELF header don't find anything helpful either.

Can this issue be fixed?

Thanks.

---

### Post by SeijiSensei on 2021-04-02
libssl1.1 is a separate package.  From "apt-cache search libssl"

libssl1.1 - Secure Sockets Layer toolkit - shared libraries

Try reinstalling that.

---

### Post by swcoffin on 2021-04-07
> **SeijiSensei said:**
> libssl1.1 is a separate package.  From "apt-cache search libssl"

libssl1.1 - Secure Sockets Layer toolkit - shared libraries

Try reinstalling that.


Thank you much for the suggestion.  That doesn't seem to have any effect.

Without further ideas, I'm beginning to think I'm just going to have to reinstall Ubuntu completely.

---

### Post by swcoffin on 2021-04-14
So, I finally fixed this and I thought I would post what fixed it for me in case it might be of assistance to others.

Here is what I did to fix it:

sudo rm /var/lib/apt/lists/lock
sudo rm /var/lib/dpkg/lock
sudo rm /var/lib/dpkg/lock-frontend
sudo dpkg --configure -a
sudo apt clean
sudo apt update --fix-missing
sudo apt install -f
sudo dpkg --configure -a
sudo apt upgrade
sudo apt dist-upgrade
sudo reboot
sudo dpkg -P webmin
sudo reboot
sudo apt-get update
sudo apt-get --reinstall install libapt-pkg-perl libnet-ssleay-perl libauthen-pam-perl libio-pty-perl apt-show-versions
sudo apt-get install webmin
sudo reboot

Now everything seems to be working.

---

