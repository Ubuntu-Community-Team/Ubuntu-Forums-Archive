---
title: "internal DNS server with BIND?"
date: 2010-08-30
forum: Server Platforms
---

### Post by pavsid on 2010-08-30
Hi folks,

Basically, i want to be able to type in a domain on any PC in the house e.g. default.dev and it direct to the ../www/default folder on the Ubuntu Server on my network. 

The reason being is that as a web developer i have a number of sites that i'm working on locally and i'm getting tired of adding the domain to my hosts file and then creating a virtual host in Apache - i believe this can be done with BIND - is this right? If so what steps are required?

Thanks in advance...

---

### Post by brad82 on 2010-08-30
As far as I know, it is not possible with just BIND. Bind would stop the need for you having to edit the hosts file, but you would still need to create a new VHost for every domain.

---

### Post by pavsid on 2010-08-30
Well thats ok, i can live with that, the main pain is the hosts file - what do i need to set up in BIND to do this? I dont need the caching functionality, just the domain forwarding - but i don't know the terminology and so not sure where to look for a tutorial.

Thanks

---

### Post by terazen on 2010-08-30
In bind you can do a record like:
```
www                IN    A       192.168.10.10
*.site.com.        IN    CNAME   www.blah.com.
```

This would make any new site you make point to the same ip as long as the naming scheme ends in "site.com"...I don't know if this is what you were looking for though.

The best tutorial is to read the first 100 or so pages of the o'reilly dns and bind book.  It should be pretty easy reading for someone who already understands the host files and apache.

---

### Post by brettg on 2010-08-30
I strongly recommend using dnsmasq for this. MUCH easier to configure than bind.

---

### Post by jblomb on 2010-09-02
I have made a simple php-script for my own domains (example.com/index.php) - something in the style of:

```
<?php
$domain=$_SERVER['SERVER_NAME'];
$suf=$_SERVER['REQUEST_URI'];
$found=preg_match('/(.*?)\.(example\.com)/i',$domain,$match);
if ($found) {
        $sub=$match[1];
        $own=$match[2];
} else {
        $sub='';
        $own=$match[0];
}
$nyurl='http://home.' . $own . '/' . $sub . $suf;
header('Location:' . $nyurl);
?>

```Then all requests to:
[http://site1.example.com](http://site1.example.com) redirects to [http://home.example.com/site1/](http://home.example.com/site1/)
[http://site2.example.com/w00t.html](http://site2.example.com/w00t.html) -> [http://home.example.com/site2/w00t.html](http://home.example.com/site2/w00t.html)
etc.

Of course all requests to *.example.com must point to the correct ip.
i.e. with the example above:

```
*.example.com.        IN    CNAME   example.com.
```

---

### Post by BkkBonanza on 2010-09-02
Bind can do this but it's overkill and quite some work.

+1 for **dnsmasq** as a simple and very easy solution. It's a package in the repos.

Disable the dhcp part if you want to use your router for dhcp. Configure your router to give the machine running dnsmasq as the DNS server, and dnsmasq will handle local names and forward others to your usual DNS server.

Some better routers allow you to set local DNS names in their setup as well and that is an even better solution since nothing else need be done.

Edit: Ooops. Now I see this is an old post. Sorry.

---

