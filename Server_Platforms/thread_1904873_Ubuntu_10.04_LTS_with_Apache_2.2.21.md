---
title: "Ubuntu 10.04 LTS with Apache 2.2.21"
date: 2012-01-05
forum: Server Platforms
---

### Post by jernau on 2012-01-05
Hi All -

I'm wondering if there is a good way of upgrading Ubuntu 10.04 LTS's apache version to 2.2.21 . By default it's repos install 2.2.14, along with the security backports. I have a feeling I'm about to get asked to push all of our servers up to 2.21 . Is there a specific repo source I can add to accomplish this? I did a little googling, but either my google-fu is weak today or I'm missing it. The only option I seem to be able to find is to install 2.2.21 manually and remove the managed version. I would absolutely prefer to stick with the managed version if at all possible. 

Any advice/assistance would be greatly appreciated. Thanks!

---

### Post by umitoz on 2012-01-06
Same problem here, what I am specially after is NoDecode option in mod_proxy. However I only managed to find Phil Norbeck's PPA's on launchpad ([https://launchpad.net/~ptn107]("https://launchpad.net/%7Eptn107")), but they are either missing or I am doing something absolutely wrong. Any help is appreciated.

---

### Post by tcpiplab on 2012-01-09
Same problem here. We use a commercial scanning service to detect web app vulnerabilities and outdated software and OS levels. So my Ubuntu 10.04 LTS web server can't get "approved" until I bring Apache up to 2.2.21. Currently it is at 2.2.14, which has a couple of security vulnerabilities, including a DoS that I'd rather not neglect. 

And since I'd rather spend my time coding than doing sysadmin stuff, I was really hoping to be able to keep Apache, and everything else, under the Ubuntu package management system. 

That said, does anyone have a good URL for how to manually upgrade Apache instead of waiting for the official Ubuntu package of Apache? I just can't find such a link on Google. 

Thanks folks.

---

### Post by kneuzgi on 2012-04-10
Hi

same problem here :-(

Does anybody know how to solve that ?

Thanks

Regards

---

