---
title: "Ubuntu 10.10 Home Server Issue"
date: 2010-12-28
forum: Server Platforms
---

### Post by odinsmasher on 2010-12-28
[FONT="Verdana"]Hi all; 

I have just installed all the components to get my local machine working with Apache/PHP (LAMP!) etc. 

When I point my local browser to the [http://localhost](http://localhost), I get the it works message, 

When I point my local browser to [http://localhost/phpmyadmin](http://localhost/phpmyadmin), it shows correctly

I have set a custom name/host odin.dev and and when I point my local browser to this it shows the files in the correct folder.

so everything up to here is fine.... then:

My aim is to be able to get my other machines to look at my web-page hosted on the 1st machine. 

Currently when I point my browser to my 192.168.0.250 it shows the 'it works' page but when I point to the [http://odin.dev](http://odin.dev) I get an error, its looking via google for odin.dev

Is it even possible for me to achieve what I am after?

Thanks in advance - odin[/FONT]

---

### Post by gordintoronto on 2010-12-29
I assume you mean, "it is going to my DNS server to try to find odin.dev." Which is the normal behavior.

I don't know what you mean by: "I have set a custom name/host odin.dev"

---

### Post by HugoSerrano on 2010-12-29
Hi!
Did you got a DNS server inside your Lan?

If not, you need to edit hosts file in the other Computers.
In ubuntu the file is /etc/hosts
Windows I think it's c:/windows/system32/etc/drivers/hosts (not sure)


Regards

---

