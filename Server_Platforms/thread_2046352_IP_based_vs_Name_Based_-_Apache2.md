---
title: "IP based vs Name Based - Apache2"
date: 2012-08-22
forum: Server Platforms
---

### Post by acc61287 on 2012-08-22
Hey guys! What do you prefer to use, ip based or name based on apache virtual hosting? Can you tell me some advantages and disadvantages?

Thanks!;)

---

### Post by sandyd on 2012-08-22
Fundamental Differences

[LIST=1]
[*]Name Based virtual hosting allows you to host several sites at one IP Address
[*]IP based virtual hosting allows you to host one site at each IP address
[*]No matter what you name the domain, if you are using IP Based Virtual Hosting, the content in the site will always be the content hosted on the IP.
[/LIST]
Really, IP based hosting is more expensive, as the prices of IP addresses are rising like nuts today.

For hosting multiple sites, name based virtual hosting makes more sense.

---

### Post by ungunyu on 2013-02-23
I have a dedicated ip and i choose that for hosting many of my websites.  When I enter the ip in my browser my primary site opens always :popcorn:

---

### Post by chrisguk on 2013-02-23
> **ungunyu said:**
> I have a dedicated ip and i choose that for hosting many of my websites.  When I enter the ip in my browser my primary site opens always :popcorn:

You need to create CNAME records for each of your websites, assuming they are on a local web server.  You can then create an alias in the VHost block something like this.  I recently made a tutorial on DNS Server and Virtual hosts which incorporated an automatic Vhost creation script.  Feel free to check it out.

For websites though you should always choose name based as opposed to IP based because thats just the way its done.  Imagine if we could only navigate to websites using an IP :popcorn:  that would be a hell of a task.

---

