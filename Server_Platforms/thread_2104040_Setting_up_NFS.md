---
title: "Setting up NFS"
date: 2013-01-11
forum: Server Platforms
---

### Post by chrisguk on 2013-01-11
Hi,

I used this tutorial among countless others on youtube and for some reason I still cannot mount the share on my client pc.

Nothing happens it just times out.  For the ensure I had not made any mistakes I used everything word for word on the tutorial.  Except the IP of course.  Here is my exports file on the Server:

```
/var/www   192.168.178.1/24(rw,no_root_squash,async)
```

I then restart the nfs kernel and follow the next step on the client PC:

```
sudo mount 192.168.178.150:/var/www /local/server
```

all I get is this:

```
mount.nfs: Connection timed out
```

Any ideas?  ):P)

---

### Post by bab1 on 2013-01-11
> **chrisguk said:**
> Hi,

I used this tutorial among countless others on youtube and for some reason I still cannot mount the share on my client pc.

Nothing happens it just times out.  For the ensure I had not made any mistakes I used everything word for word on the tutorial.  Except the IP of course.  Here is my exports file on the Server:

```
/var/www   192.168.178.1/24(rw,no_root_squash,async)
```

I then restart the nfs kernel and follow the next step on the client PC:

```
sudo mount 192.168.178.150:/var/www /local/server
```

all I get is this:

```
mount.nfs: Connection timed out
```

Any ideas?  ):P)

We can deal with both the NFS problem and the [**_[COLOR="Blue"]other post you have [/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2103819").

Are you using NFSv4?  If so you should do it [**_[COLOR="Blue"]this way[/COLOR]_**]("&#65279;https;//help.ubuntu.com/community/NFSv4Howto").

I just set up a development LAMP stack for a user on my network (I'm the admin) and used NFSv4 with it.  I can open a browser and go to any of the virtual hosts I have set up by the virtual host name only.  I have one for me that is named bab.  I can use either bab or [www.bab](www.bab).  You don't need DNS or FQDN on the dev server unless you want the hassle of running a LAN side DNS server.

FWIW - I don't keep my web content under /var/www.  I store the data at /data/www/<virtualhost> and set Apache to understand.  All the work is on Ubuntu 12.04 so it won't be any different for you set up.  Since I just completed this I have my notes handy.  Ask questions if you need more help.

---

### Post by chrisguk on 2013-01-11
Thank you for your reply.  I will have a look at your suggestions when I wake in the morning.  If you have a step by step user setup for virtual hosts that will be helpful.

By the way I did this while I was reading yours.

I setup the LAMP stack of course and pointed my browser on the client PC to [http://192.168.178.150](http://192.168.178.150)  (localhost) and it displayed the normal default page "It works"

I also installed phpmyadmin and did the same in the browser:

[http://192.168.178.150/phpmyadmin](http://192.168.178.150/phpmyadmin)

so if I setup a virtual host the normal way on the server for example:

[http://mytestsite.local](http://mytestsite.local)   Local folders on Server under /var/www

and point my browser to that URL above on the client PC, will it work and display the web content or is there something I have to do, like make my client PC part of the domain or something?

---

### Post by bab1 on 2013-01-11
> **chrisguk said:**
> Thank you for your reply.  I will have a look at your suggestions when I wake in the morning.  If you have a step by step user setup for virtual hosts that will be helpful.

By the way I did this while I was reading yours.

I setup the LAMP stack of course and pointed my browser on the client PC to [http://192.168.178.150](http://192.168.178.150)  (localhost) and it displayed the normal default page "It works"

I also installed phpmyadmin and did the same in the browser:

[http://192.168.178.150/phpmyadmin](http://192.168.178.150/phpmyadmin)

so if I setup a virtual host the normal way on the server for example:

[http://mytestsite.local](http://mytestsite.local)   Local folders on Server under /var/www

and point my browser to that URL above on the client PC, will it work and display the web content or is there something I have to do, like make my client PC part of the domain or something?

No you don't have to be part of a domain.  The domain is a centralized admin and security construct.  You can address the web server by its hostname or by virtual host name.  Remember that folks use the same naming for things (i.e. domain) and they mean different things depending upon the context.

---

