---
title: "Proxy while passing through another URL?"
date: 2010-11-20
forum: Server Platforms
---

### Post by c0nfus3d1 on 2010-11-20
Probably not the best place for this, but I don't know where else to go..

I'm trying to set up a hot spot using a squid proxy server for network logging of accessed website URLs. I really would like to pass all web traffic through a custom PHP program.. Like when a computer tries to access [www.google.com](www.google.com) it first goes through the proxy server, and then the proxy server sends back a URL like [http://mysite.com/myapp.php?url=http://google.com](http://mysite.com/myapp.php?url=http://google.com) which is then accessed by the end-user's computer.. I'd eventually set up the php program to redirect the user to the requested URL after my application executes.

Is this at all possible to do, with or without squid?

Any help is appreciated!!

---

### Post by craigp84 on 2010-11-21
Hi, google "redirect_program"

Example redirector:

```
#!/usr/bin/perl
$|=1;
print while (<>){
  # chop # might need to uncomment this, cant remember if it comes with with a newline or not, it might...
  print "http://mysite.com/myapp.php?url=$_\n";
]
```

---

### Post by c0nfus3d1 on 2010-11-21
Thanks! You're awesome!!!

You did have a typo in your program that I had to fix.. but no worries

```
#!/usr/bin/perl
$|=1;
while (<>) {
print "http://mysite.com/myapp.php?url=$_\n";
}

```

Thanks again!! :)

---

