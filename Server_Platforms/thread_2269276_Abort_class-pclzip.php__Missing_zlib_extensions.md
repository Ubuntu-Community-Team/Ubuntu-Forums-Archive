---
title: "Abort class-pclzip.php : Missing zlib extensions"
date: 2015-03-14
forum: Server Platforms
---

### Post by zkvvoob on 2015-03-14
Hello,

Since I recovered from some mess that I was having after upgrading my Ubuntu server to 14.04, the two Wordpress websites that I have hosted on the server have been randomly displaying the following error message upon opening:

```
Abort class-pclzip.php : Missing zlib extensions
```

The strange thing is that a refresh gets rid of the message. While this works for me, it's not a good idea to rely on guest visitor's quick-wittedness.

So, could you help me figure out what's missing and how to add it?

Thank you!

---

### Post by Thirtysixway on 2015-03-19
> **zkvvoob said:**
> [SIZE=3][FONT=arial][COLOR=#333333]Hello,

Since I recovered from some mess that I was having after upgrading my Ubuntu server to 14.04, the two Wordpress websites that I have hosted on the server have been randomly displaying the following error message upon opening:[/COLOR]

```
Abort class-pclzip.php : Missing zlib extensions
```
[COLOR=#333333]
The strange thing is that a refresh gets rid of the message. While this works for me, it's not a good idea to rely on guest visitor's quick-wittedness.[/COLOR]
[COLOR=#333333]
So, could you help me figure out what's missing and how to add it?[/COLOR]
[COLOR=#333333]
Thank you![/COLOR][/FONT][/SIZE]

[https://wordpress.org/support/topic/missing-zlib-extensions-php-error](https://wordpress.org/support/topic/missing-zlib-extensions-php-error)
sudo apt-get install --reinstall zlibc zlib1g zlib1g-dev

---

