---
title: "Need help setting up my website"
date: 2009-02-28
forum: Server Platforms
---

### Post by CalvinMorrison on 2009-02-28
hello all.

After today and yesterday of googling and sitting on the IRC getting redirected to other random pages which didn't really explain much. My last resort was to turn to the forums for an answer.

Basically I've bought a web domain. I have a Ubuntu Server Edition. Now I just need to hook the one up to the other.

I don't really know much about web servers. other than I need to just make basic webpages in HTML.

What Programs Do I need? How Do i Configure it? 

Any Advice? *please just don't use fancy words*

---

### Post by cariboo on 2009-02-28
If you have a proper server set up, at the prompt type:

```
sudo tasksel
```

and select LAMP, this will install Apache2, mysql and Php5

If you have a gui go to System--Aministration-->Synaptic Package Manager-->Mark Packages by Task and select LAMP from the menu.

For more info on setting up a server have a look [here]("http://doc.ubuntu.com/ubuntu/serverguide/C/")

> Any Advice? *please just don't use fancy words* 

You're moving into different territory now, **fancy words** are the norm. Read the howto and learn the terminology.

Jim

---

### Post by CalvinMorrison on 2009-02-28
K, i got everything up til the static ip  address. when i edit the interfaces to create the static ip address (192.168.1.10 is what i tried). after that, i can connect to the network, can ssh into it using 192.168.1.10, but cannot connect to the internet in any form. any suggestions?

Thanks,
CalvinMorrison

---

### Post by jojo1224 on 2009-02-28
> **CalvinMorrison said:**
> K, i got everything up til the static ip  address. when i edit the interfaces to create the static ip address (192.168.1.10 is what i tried). after that, i can connect to the network, can ssh into it using 192.168.1.10, but cannot connect to the internet in any form. any suggestions?

Thanks,
CalvinMorrison

You will need a static ip from you isp too, not just on the webserver.

---

### Post by R.Bucky on 2009-02-28
The 192.168.1.10 address is internal only. Your static ip, as mentioned before, will be assigned by your internet service provider (e.g Comcast, Qwest). Once you have that, visit your domain registrar (e.g. Network Solutions) and enter your IP into the CNAME record. Basically, it tells your company where to push the traffic. Next, configure your server to allow traffic on port 80. I wrote a short post [here]("http://buckycomputing.net/weeklytopics/ubuntu_web_server_security_basics/"). 

Your server files are located at the directory /var/www. You will need to add the line **ServerName your_domain.com** to the **/etc/apache2/httpd.conf** file, then restart apache using **/etc/init.d/apache2 force-reload**. Remember to include sudo. That should at least get you online. 

Once you are comfortable, you could try using a Content Management System (CMS) such as Concrete5, Wordpress, or Drupal.

---

