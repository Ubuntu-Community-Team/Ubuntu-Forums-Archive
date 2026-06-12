---
title: "Xen Webinterface"
date: 2008-05-16
forum: Server Platforms
---

### Post by sut123 on 2008-05-16
Hello,

I have created a Webinterface (php) for Xen (3.2.1). Maybe it's usefull for some people ;-)

Add the correect dir paths to the php file. You' ll also need to add:

www-data ALL= NOPASSWD: /usr/sbin/xm
www-data ALL= NOPASSWD: /usr/sbin/xentop

to your /etc/sudoers file.

sut

---

### Post by Thirtysixway on 2008-05-18
Can Xen be run on Ubuntu Server editon, without gui?

---

### Post by sut123 on 2008-05-19
Sure! Use Hardy. You' ll also need the vnc4server package. After this you are able to make remote vncviewer sessions to your virtual machines.

Example: vncviewer 192.168.10.24:5901:1

---

### Post by cb951303 on 2008-05-19
very nice effort

---

### Post by windependence on 2008-05-19
> **sut123 said:**
> Sure! Use Hardy. You' ll also need the vnc4server package. After this you are able to make remote vncviewer sessions to your virtual machines.

Example: vncviewer 192.168.10.24:5901:1

You can also control xen VMs with the CLI.

-Tim

---

### Post by jerle on 2009-06-05
> **sut123 said:**
> Hello,

I have created a Webinterface (php) for Xen (3.2.1). Maybe it's usefull for some people ;-)

Add the correect dir paths to the php file. You' ll also need to add:

www-data ALL= NOPASSWD: /usr/sbin/xm
www-data ALL= NOPASSWD: /usr/sbin/xentop

to your /etc/sudoers file.

sut

hi, i stumbled upon your mini web interface... i'm using it, and expanding it a little
(my version now let attach/detach iso images or cd drive, and has a little more configuration)
i'd like to know under what license do you distribute the code above, and so if i can make public my extensions
thanx, bye

---

### Post by jerle on 2009-06-20
> **jerle said:**
> hi, i stumbled upon your mini web interface... i'm using it, and expanding it a little
(my version now let attach/detach iso images or cd drive, and has a little more configuration)
i'd like to know under what license do you distribute the code above, and so if i can make public my extensions
thanx, bye

since you didn't answered, i assume the code in pubic domain i'm releasing the modified code also on my site, under gpl license....

---

### Post by frostmyname on 2009-06-24
> **sut123 said:**
> Hello,

I have created a Webinterface (php) for Xen (3.2.1). Maybe it's usefull for some people ;-)

Add the correect dir paths to the php file. You' ll also need to add:

www-data ALL= NOPASSWD: /usr/sbin/xm
www-data ALL= NOPASSWD: /usr/sbin/xentop

to your /etc/sudoers file.

sut

And what modules apache2php should be established?

---

### Post by jerle on 2009-06-25
> **frostmyname said:**
> And what modules apache2php should be established?

in debian, i've got this *php* packages installed:
libapache2-mod-php5
php-pear
php5
php5-cgi
php5-cli
php5-common

and a few others not directly related with the interface here, i think
(i'm not really sure what is used from this web interface, i've a lot of other php things on that machine)

---

### Post by sut123 on 2009-06-27
Hello,

sure, sure... do whatever you like with the code ;-)

---

### Post by sirtales on 2009-09-03
Hi,

what directory is /vt/configs/ ?

The only .hvm file I can find on my system is /etc/xen/examples/xmexample.hvm

Thanks :)

---

### Post by badeendjuh on 2009-09-07
Hi Jerle, could you maybe post the link to your website? I would like to have a look at your updated code. Thanks!

---

### Post by patton73 on 2009-09-25
I would like to look at the code to.
Can you post the link of the code please?

---

### Post by sootysam on 2009-10-02
> **jerle said:**
> hi, i stumbled upon your mini web interface... i'm using it, and expanding it a little
(my version now let attach/detach iso images or cd drive, and has a little more configuration)
i'd like to know under what license do you distribute the code above, and so if i can make public my extensions
thanx, bye

Hi Jerle.
Where is your version of the code? How can we view it please? Can you add some screenshots as well. cheers for now

---

### Post by jerle on 2009-10-04
> **sootysam said:**
> Hi Jerle.
Where is your version of the code? How can we view it please? Can you add some screenshots as well. cheers for now

here i am; some people asked me the modified code...
sorry, i was sure to have already posted the link even on the forum, checked now and that's not the case :(

so here is the link to my version of the interface:

[http://www.paultt.org/downloads/pttxwm/pttXwm-0.3.2.tar.bz2](http://www.paultt.org/downloads/pttxwm/pttXwm-0.3.2.tar.bz2)

---

### Post by peter6960 on 2010-07-08
I get the same screen when trying to use the script

Can you please assist?

> **frostmyname said:**
> And what modules apache2php should be established?

---

### Post by MrHien on 2010-09-22
Great code...thanks!

---

### Post by thenasko on 2011-01-26
> **jerle said:**
> since you didn't answered, i assume the code in pubic domain i'm releasing the modified code also on my site, under gpl license....

Could you provide a link to your website?

---

### Post by FlatTire on 2011-09-04
Jerle would you mind posting a link to the code you have written? I think the community would benefit from your additions. Thank you.

---

