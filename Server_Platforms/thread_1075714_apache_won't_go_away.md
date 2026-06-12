---
title: "apache won't go away?"
date: 2009-02-20
forum: Server Platforms
---

### Post by asaturn on 2009-02-20
so I had this test site up and running fine. installed everything myself.

then lately I noticed whenever I'd go to my site via the IP, I'd get the "test page for apache installation" with the feather at the bottom

if I went to "localhost" I got the PHP site I had set up...

I checked all of my config files, and nothing pointed to the test page. I was using /var/www  as my web root.

I even went so far as to search for apache_pb.gif and delete it -- it still loaded even after clearing my cache, WTF?

so I uninstalled apache, removed /etc/apache2, and restarted... my local site was still loading under localhost, and the test page still loading under any IP address...

so I moved all of my files from var/www onto my desktop... now my localhost shows an empty folder (and reflects changes to var/www) and that stupid test page is STILL THERE. WHAT is going on? according to ubuntu I don't have apache installed ... yet:

```
root@koi:/home/saturn# ps aux | grep apache
root      7069  0.0  0.0  13484  2892 ?        Ss   14:50   0:00 /usr/sbin/apache2 -k start
www-data  7073  0.0  0.0  13256  2100 ?        S    14:50   0:00 /usr/sbin/apache2 -k start
www-data  7074  0.0  0.1 235000  3396 ?        Sl   14:50   0:00 /usr/sbin/apache2 -k start
www-data  7075  0.0  0.1 234980  3384 ?        Sl   14:50   0:00 /usr/sbin/apache2 -k start
root      8163  0.0  0.0   3236   792 pts/0    R+   15:11   0:00 grep apache

```


I can do killall apache2, which apparently makes those all disappear... the localhost server goes down, but the "test page" running on my IP IS STILL RUNNING.

what is going on? help!

---

### Post by cdenley on 2009-02-20
If you want to remove apache:
```

sudo apt-get --purge remove apache2*

```
You probably removed the apache2 meta-package.

If you want to see what sites you have configured:
```

cat /etc/apache2/sites-enabled/*

```

If you want to see what servers you have running:
```

sudo netstat -tlnp

```

---

### Post by asaturn on 2009-02-20
I did that above remove command...

the cat command says "no such file or directory"

netstat shows only 4984/cupsd

crazy, huh?

---

### Post by cdenley on 2009-02-20
> **asaturn said:**
> I did that above remove command...

the cat command says "no such file or directory"

netstat shows only 4984/cupsd

crazy, huh?

Well then any page you're seeing isn't coming from a web server on your computer, since there is no server to respond on that port.

---

### Post by asaturn on 2009-02-20
well now I feel like an idiot

my local IP changed... to 192.168.1.106

so now I have to find out what is on 192.168.1.100, there's only one other PC in the house and it's running Vista

edit:

turns out my wife had her macbook turned on when the power went out, so it took my static IP for some reason, then she turned on "web sharing" instead of "internet sharing"... so it was running an apache server on what I thought was my local IP.

I feel stupid.

NOTE TO SELF: run ifconfig next time.

---

### Post by 3L33T on 2009-02-20
> **asaturn said:**
> well now I feel like an idiot


Hehehehe, it happens.  BUT, this is the reason why I use static IP address on my servers serving www, ftp, proxy, etc.  It is so much easier to administer from router (opening tcp/udp ports) to server when using static IP's.

---

### Post by E_K on 2009-02-20
> **asaturn said:**
> I did that above remove command...

the cat command says "no such file or directory"

netstat shows only 4984/cupsd

crazy, huh?

that comand will show the contents of the files in the directory followin the cat command

i guess you have removed the directory (apache2) so it cant show what your asking it to

---

### Post by asaturn on 2009-02-20
> **E_K said:**
> that comand will show the contents of the files in the directory followin the cat command

i guess you have removed the directory (apache2) so it cant show what your asking it to

yeah I thought it was set to static but her mac somehow took the IP anyway. oh well. I'm back up and running -- I backed up all the important info.

---

