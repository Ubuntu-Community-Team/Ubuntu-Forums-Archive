---
title: "Is there a web based program to manage squid proxy server?"
date: 2009-05-27
forum: Server Platforms
---

### Post by kevin.wu on 2009-05-27
I have set up a squid proxy server on ubuntu server 9.04, I wonder if there is a web base program I can use to manage it, then I need not to edit the *squid.conf* file.

---

### Post by sanderj on 2009-05-27
> **kevin.wu said:**
> I have set up a squid proxy server on ubuntu server 9.04, I wonder if there is a web base program I can use to manage it, then I need not to edit the *squid.conf* file.

Webmin. See [http://www.webmin.com/standard.html](http://www.webmin.com/standard.html) and search for 'squid'.

---

### Post by kevin.wu on 2009-05-27
[https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin)
I have read from there Webmin is not compatible with the way that Ubuntu packages handle configuration files, and caused unexpected issues with people's systems. 

Is there other choice?

---

### Post by BbUiDgZ on 2009-05-27
> **kevin.wu said:**
> [https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin)
I have read from there Webmin is not compatible with the way that Ubuntu packages handle configuration files, and caused unexpected issues with people's systems. 

Is there other choice?

webmin works fine with ubuntu, you might need to change some the paths to config files 
see [HERE](http://franchett1.com/gerry/?p=22)

---

### Post by madverb on 2009-05-27
There is also eBox

---

### Post by samosamo on 2009-05-27
webmin.

---

### Post by bboston7 on 2009-05-27
> **kevin.wu said:**
> [https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin)
I have read from there Webmin is not compatible with the way that Ubuntu packages handle configuration files, and caused unexpected issues with people's systems. 

Is there other choice?

Webmin works great, it just takes a little configuring.

---

