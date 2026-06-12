---
title: "Will update manager force me to install OpenJDK at some point?"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Avaritia on 2012-04-14
I did a fresh install of 12.04 last night and noticed OpenJDK is not in the repositories (or the restricted extras package) anymore, so I installed the Oracle version using this guide: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

I like how much more compatible it is with my Java apps than the OpenJDK version and wish to keep it but at some point during the development of Ubuntu 12.04 will download manager force me to download OpenJDK instead?

---

### Post by Pilot6 on 2012-04-14
No. Oracle Java will be always used by default. But you will need to update it manually to get security fixes.

---

### Post by meborc on 2012-04-14
> **Pilot6 said:**
> No. Oracle Java will be always used by default. But you will need to update it manually to get security fixes.

You can always choose which java install is the "current" in your system. For compatibility with some custom programs I have several versions of java on my machine. I switch between them using ```
sudo update-alternatives --config java

```

---

### Post by Avaritia on 2012-04-14
Thanks for clearing that up.

---

### Post by grahammechanical on 2012-04-14
Please see this link:

[http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/]("http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/")

I understand this this is no longer correct:

> Users who have the &#8216;sun-java-6&#8242; package installed on their system will see it removed via a future software update &#8211; the exact date of which is &#8216;TBD&#8217;.

But the other stuff in the link is correct as far as I know.

Regards.

---

### Post by na5h on 2012-04-14
There is also a PPA available if you want your Oracle Java to stay up-to-date. It only provides the full Oracle JDK package, though:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

