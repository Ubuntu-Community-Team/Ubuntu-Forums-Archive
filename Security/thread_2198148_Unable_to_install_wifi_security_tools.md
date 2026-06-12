---
title: "Unable to install wifi security tools"
date: 2014-01-07
forum: Security
---

### Post by vkvikask13 on 2014-01-07
Hi

I have installed Ubuntu 12.04 Desktop Edition. I have imported the kali security tools repository into my Ubuntu sources list from [http://launchpad.net](http://launchpad.net)

[B]ppa:wagungs/kali-linux
[/B][B]ppa:wagungs/kali-linux2
[B]ppa:wagungs/kali-linux1

[/B][/B][B]By importing these repositories, I can install many security tools. But I'm unable to install wifi tools such as honeypot, airodump-ng, airplay-ng. It says that the package is broken
[/B][B][B]It is important for me to work with penetration testing tools. I have my wifi hardware properly working.

Can anyone say me solution for this.


[/B][/B]

---

### Post by r3dd on 2014-01-07
```

sudo apt-add-repository --remove ppa:wagungs/kali-linux
sudo apt-add-repository --remove ppa:wagungs/kali-linux2
sudo apt-add-repository --remove ppa:wagungs/kali-linux1
sudo apt-get update
sudo apt-get install aircrack-ng tinyhoneypot

```

You don't need the Kali PPA to do anything you just mentioned. There are a couple of different honeypots in the Ubuntu packages, just do a search for "honey" or "honeypot". The airodump-ng and airplay-ng will be installed with the aircrack-ng suite.

Also, the Ubuntu repos have wifite to make the process automated.
```
 sudo apt-get install wifite
```

Installing wifite will install all of the recommended dependencies like reaver and a few others (except cowpatty, I think) as well as the aircrack-ng suite since that is what wifite is build to automate.

---

### Post by Bucky Ball on 2014-01-07
*Thread closed.*

From the forum ***Code of Conduct***:

> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

---

