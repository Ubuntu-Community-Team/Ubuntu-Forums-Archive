---
title: "Do i use LAMP or manually Install the php, apache2, mysql?"
date: 2020-02-11
forum: Server Platforms
---

### Post by sudo1211 on 2020-02-11
Is there is any difference in installing package separately or using Lamp?

I know lamp package saves time in installation but i am asking in terms of memory usage or security?

Reasons to go for manual installation?

---

### Post by SeijiSensei on 2020-02-11
Use the LAMP package. There are additional packages like libapache2-mod-php that are needed for all of this to work properly. Over my years here, I've seen a number of posts from people who had installed Apache and PHP manually and couldn't get them to work properly. Often the problem was not having installed something like libapache2-mod-php. The LAMP package includes all these things.

There are many other modules for Apache and PHP that, if you require them, must be installed manually. Run the commands "apt-cache search libapache2" and "apt-cache search php-" to see the lists of available packages.

---

### Post by slickymaster on 2020-02-11
Thread moved to **Server Platforms** for a better fit

---

### Post by LHammonds on 2020-02-12
> **sudo1211 said:**
> Is there is any difference in installing package separately or using Lamp?
Yes

> **sudo1211 said:**
> I know lamp package saves time in installation but i am asking in terms of memory usage or security?
You can install the separate components and end up with a similar install using the pre-package but you are restricted in the design flexibility when using the package.

> **sudo1211 said:**
> Reasons to go for manual installation?
Flexibility in design
To use MariaDB instead of MySQL
To use multiple dedicated servers for scaleability and increased security.
To make use of high-availability with HAProxy / Clustering

Here is an example of a server design that can handle growth easily:
[IMG]https://hammondslegacy.com/images/linux/design-ha-lamp-service.jpg[/IMG]
And here's the install documentation on the steps I took to create the above HA design:
[Web load balancer](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=260)
[Web server](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=261)
[Database load balancer](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=264)
[Database cluster](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=262)

Of course, not every app needs such a design but having your database clustered like this with a load balancer makes it VERY robust and allows you to keep it online and working even if you have to perform maintenance/upgrades to a single node.

I try to setup development / test platforms very-much how I would set it up in production.  Why?  Because more often than not, the development system gets turned into production as is for whatever reason and you don't get to go back and "fix" the design issues that was created because it was simply considered "development" and afforded a lot of extra slack because it was not "production."

LHammonds

---

### Post by SeijiSensei on 2020-02-12
I'll just say that I have hosted a number of websites over the years and never had an infrastructure as complex as that.

---

### Post by LHammonds on 2020-02-12
> **SeijiSensei said:**
> I'll just say that I have hosted a number of websites over the years and never had an infrastructure as complex as that.Personal/small/medium sites typically do not.  But sites with significant traffic such as popular sites or business web applications do require the ability to scale.  Uptime is the other consideration if its mission-critical.

---

### Post by SeijiSensei on 2020-02-12
Right. I'm definitely in the first group; I suspect the OP is as well.

---

### Post by LHammonds on 2020-02-12
Well, he just asked what's different...thus I gave some various reasons (but not all-inclusive) regarding differences.

---

