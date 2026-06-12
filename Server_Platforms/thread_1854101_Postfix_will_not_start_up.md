---
title: "Postfix will not start up"
date: 2011-10-03
forum: Server Platforms
---

### Post by yakatz on 2011-10-03
When my server restarts, I get this error on the console:
> Starting Postfix Mail Transport Agent postfix postfix: fatal: parameter inet_interfaces: no local interface found for _MY_PUBLIC_IP_ADDRESS_ [[COLOR="Red"]fail[/COLOR]]

This started appearing at some point over the last month but I can't pin down exactly when it started. It is only an issue during startup though, postfix starts when I run [FONT="Courier New"]service postfix start[/FONT].

---

### Post by hawk2010 on 2011-10-04
may be an interface related issues. why not paste your interfaces file here. Also paste the main.cf

---

### Post by yakatz on 2011-10-04
I found it!!
My server is on Linode.
From the Linode Library:
> By default, Linodes use DHCP to acquire their IP address, routing and DNS information. However, DHCP will only assign one IP to your Linode, so if you have multiple IPs, you'll need to use a static configuration. Even if you only have one IP, you can still do a static assignment, but it's not required in most cases.
Not sure what changed recently, but setting the IP address manually in interfaces fixes the problem.

---

