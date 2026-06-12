---
title: "Apache 2.2.12+ on 8.04 for multiple SSL-Certificates"
date: 2011-01-06
forum: Server Platforms
---

### Post by black_jet on 2011-01-06
Hi there!

Following problem:
I have Apache 2.2.8 running on my Ubuntu 8.04 Server and would like to update Apache to
any version higher than 2.2.12 so I get support for multiple SSL-Certificates on 1 IP-address.
I cannot upgrade my Distro since my provider does not give me that option and afaik I
cannot use the repositories since 2.2.8 is the highest version for 8.04.

Does someone know of a way to update to a higher Apache version, without doing it "fully"
manually? I would like to avoid the hassle of manually taking care of PHP, Ruby and
further updates.

Or alternatively how to add support for multiple SSH certificates?

Thanks in Advance,
Black_Jet

---

### Post by James78 on 2011-01-06
Can you install deb packages? Backup your apache configuration (/etc/apache2), then uninstall all the apache2 packages, then install the deb packages of the [latest one]("http://packages.ubuntu.com/maverick-updates/apache2") (take in mind the dependencies required; you'll need to download those also).

---

