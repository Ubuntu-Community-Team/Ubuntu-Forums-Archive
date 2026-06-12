---
title: "Synaptic Problem - Proxie Server"
date: 2005-03-30
forum: Repositories &amp; Backports
---

### Post by hugov on 2005-03-30
Hi 

I am on a proxie server and I get this error:

[http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

How can I get it to work? There is no option in Synaptic to enter a username and password.

Thanx

---

### Post by fdoving on 2005-03-30
[QUOTE=hugov]Hi 

I am on a proxie server and I get this error:

[http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

How can I get it to work? There is no option in Synaptic to enter a username and password.

Thanx[/QUOTE]
 Hello.

Edit /etc/apt/apt.conf as root.. and add something like:
```

// PROXY SETTINGS
acquire::http::proxy "http://username:password@proxy:port";

```


Enjoy.

---

### Post by Marsupilami on 2005-04-04
create 
/etc/apt/apt.conf.d/01acquire

and add in the lines from fdoving post :
acquire::http::proxy "http://username:password@proxy:port";

---

### Post by hugov on 2005-04-05
I have added it exactly as you guys said, but I still get this error:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

Synaptic does not work neither apt-get

I am also runnine Hoary now, will this make a difference? Cause I added it in Hoary.

---

### Post by ymeyer on 2005-04-07
install and configure tsocks 

then use "sudo tsocks apt-get ..."

or
                "sudo tsocks synaptic"

---

