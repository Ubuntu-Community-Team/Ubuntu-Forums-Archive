---
title: "Ubuntu/Apache/Web/Server - i am lost.need help."
date: 2015-02-15
forum: Server Platforms
---

### Post by andrei-tanase-m on 2015-02-15
Hello!

First of all,i don`t know if i posted in the right category,and if not i am sorry.

These are most networking issues that i have and i need some clarification/suggestions.

Here it goes:

I have an ASUS AC56u router.This router has it`s own cloud and ftp server.I used DDNS to acces these features.
I have Ubuntu 14.04 installed on one of my older laptops and i decided to play with it as a server and installing OwnCloud ,Apache and MySql.I used port forwarding for the Ubuntu laptop and all it`s fine but it`s messy.

When i acces "http://example.ddns.com" it displays the Apache2 ubuntu default page,until port forwarding it displayed the router administration page/
When i acces "**https**://example.ddns.com" it displays the Asus Aicloud.
When i acces "http://example.ddns.com/owncloud" it displays Owncloud.

How can i sort this out? For example the ddns default [http://example.ddns.com](http://example.ddns.com) to be router login,[http://example.ddns.com/aicloud](http://example.ddns.com/aicloud) to be asus cloud and so on.

Is this a router configuration problem or i can sort this out from Apache.

---

### Post by sandyd on 2015-02-15
> **andrei-tanase-m said:**
> Hello!

First of all,i don`t know if i posted in the right category,and if not i am sorry.

These are most networking issues that i have and i need some clarification/suggestions.

Here it goes:

I have an ASUS AC56u router.This router has it`s own cloud and ftp server.I used DDNS to acces these features.
I have Ubuntu 14.04 installed on one of my older laptops and i decided to play with it as a server and installing OwnCloud ,Apache and MySql.I used port forwarding for the Ubuntu laptop and all it`s fine but it`s messy.

When i acces "http://example.ddns.com" it displays the Apache2 ubuntu default page,until port forwarding it displayed the router administration page/
When i acces "**https**://example.ddns.com" it displays the Asus Aicloud.
When i acces "http://example.ddns.com/owncloud" it displays Owncloud.

How can i sort this out? For example the ddns default [http://example.ddns.com](http://example.ddns.com) to be router login,[http://example.ddns.com/aicloud](http://example.ddns.com/aicloud) to be asus cloud and so on.

Is this a router configuration problem or i can sort this out from Apache.
This sounds fun :)

Port forwarding forwards the port directly to the computer. As a result, it is not possible to get the router to mix both router and owncloud pages.

However, you can get apache2 to mix the router and owncloud pages by setting up a proxy.

Try adding something like
```

ProxyPass /owncloud !
ProxyPass / http://routeriphere      
ProxyPassReverse / http://routeriphere
ProxyPass /aicloud http://routeriphere
ProxyPassReverse /aicloud http://routeriphere

```

to your Apache2 configuration.

This will proxy the default index page (/) and the aicloud page (/aicloud) to the internal ip of your router, which you replace in the configuration above.

It will stop /owncloud from being proxied through

If you need help, post your apache2 vhost configuration.

Side note: I have moved your thread over to *server platforms*

---

