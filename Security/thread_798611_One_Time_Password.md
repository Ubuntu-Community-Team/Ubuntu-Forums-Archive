---
title: "One Time Password"
date: 2008-05-18
forum: Security
---

### Post by satimis on 2008-05-18
Hi folks,


Ubuntu 7.04 server amd64


I'm prepared installing One-time-password on the mail server as a test.  On googling I found;

opie-client
opie-server
libopie-dev


They are on Ubuntu repo.


Please advise whether it needs installing all of them?

Where can I find the how-to/guide to config them?  Where is their official website?  TIA


On googling I also find;

Using FreeNX to secure Terminal Services and VNC with two-factor authentication
[http://www.wikidsystems.com/documentation/howtos/2_factor_vnc](http://www.wikidsystems.com/documentation/howtos/2_factor_vnc)

It seems for Fedora?  Any comment?


OR is there any other suggestion on One-time-password?


B.R.
satimis

---

### Post by nowen on 2009-08-26
You can run the WiKID Strong Authentication server on Ubuntu, if you want:

[http://www.wikidsystems.com/support/wikid-support-center/installation-how-tos/how-to-install-the-wikid-strong-authentication-system-on-ubuntu/](http://www.wikidsystems.com/support/wikid-support-center/installation-how-tos/how-to-install-the-wikid-strong-authentication-system-on-ubuntu/)

HTH,

Nick

---

### Post by Lars Noodén on 2009-09-24
Here is one article on OPIE:
[http://www.h-online.com/security/One-time-passwords-for-home-users--/features/88570](http://www.h-online.com/security/One-time-passwords-for-home-users--/features/88570)

In general, the tutorials and HowTos for Debian will be very relevant for Ubuntu.  In many cases, so are the documents for other linux distros, though some details, like file locations may vary.  


There is also the package donkey in Ubuntu: 
[http://packages.ubuntu.com/jaunty/donkey](http://packages.ubuntu.com/jaunty/donkey)

Earlier this year I saw a dongle used for single-use passwords:
[http://www.yubico.com/products/yubikey/](http://www.yubico.com/products/yubikey/)

---

### Post by satimis on 2009-09-25
> **nowen said:**
> You can run the WiKID Strong Authentication server on Ubuntu, if you want:

[http://www.wikidsystems.com/support/wikid-support-center/installation-how-tos/how-to-install-the-wikid-strong-authentication-system-on-ubuntu/](http://www.wikidsystems.com/support/wikid-support-center/installation-how-tos/how-to-install-the-wikid-strong-authentication-system-on-ubuntu/)

HTH,

Nick

Hi Nick,

Thanks for your info


B.R.
satimis

---

### Post by satimis on 2009-09-25
> **Lars Noodén said:**
> Here is one article on OPIE:
[http://www.h-online.com/security/One-time-passwords-for-home-users--/features/88570](http://www.h-online.com/security/One-time-passwords-for-home-users--/features/88570)

In general, the tutorials and HowTos for Debian will be very relevant for Ubuntu.  In many cases, so are the documents for other linux distros, though some details, like file locations may vary.  


There is also the package donkey in Ubuntu: 
[http://packages.ubuntu.com/jaunty/donkey](http://packages.ubuntu.com/jaunty/donkey)

Earlier this year I saw a dongle used for single-use passwords:
[http://www.yubico.com/products/yubikey/](http://www.yubico.com/products/yubikey/)

Hi Lars Noodén,

Thanks for your info and URL


B.R.
satimis

---

### Post by nowen on 2011-05-13
I know this thread is quite old, which only shows how late we are, but we have just released .deb packages for ubuntu for the WiKID Strong Authentication server.  The open source Community Edition is available on sourceforge: [http://sourceforge.net/projects/wikid-twofactor/](http://sourceforge.net/projects/wikid-twofactor/) and the Enterprise version is available from our site: [http://www.wikidsystems.com/downloads](http://www.wikidsystems.com/downloads) (the difference: [http://www.wikidsystems.com/community-version/support/wikid-support-center/faq/whats-the-difference-between-the-community-release-and-enterprise-release/](http://www.wikidsystems.com/community-version/support/wikid-support-center/faq/whats-the-difference-between-the-community-release-and-enterprise-release/)).  Feedback, contributions and documentation always appreciated.

---

