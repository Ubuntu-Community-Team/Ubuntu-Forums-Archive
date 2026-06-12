---
title: "need help with apache 2 webserver"
date: 2009-10-20
forum: Server Platforms
---

### Post by NobuStarwind on 2009-10-20
Basically I've set the webserver to port 90 cause my Internet provider blocks port 80. When it was on port 80 I get a page that says it works. But when set to port 90 I get a page that says can't locate web page or something like that. I sort of think there might be a firewall block. I tried using Firestarter but at no avail couldn't get the host to be recognized. If anyone knows how I can fix this, it be appreciated. thanks. Also I am using Ubuntu 9.04

---

### Post by scragar on 2009-10-20
Have you tried:
[localhost:90](http://localhost:90/)

---

### Post by NobuStarwind on 2009-10-20
What exactly are you referring to? Like set firewall to allow Localhost:90 or type Localhost:90 into web browser?

---

### Post by scragar on 2009-10-20
Just try the link I posted, see if that works.

---

### Post by NobuStarwind on 2009-10-21
I tried the link as you suggested but still the same thing happened.

---

### Post by NobuStarwind on 2009-10-21
Could there be by chance a root certificate block or something when changing port number? or something else by chance not letting it go through?

---

### Post by NobuStarwind on 2009-10-22
Well obviously nobody knows the answer to this issue cause there's been like 100 views but no reply since I last posted. I would think that this being an official Ubuntu forum that at least a couple of people would know the answer.

---

### Post by confusedstingray on 2009-10-22
if it worked at port 80 why did you change it to port 90? The page "it works" is what the apache default is, you are supose to see this.Now you create a web page in the default directory that you set when installing apache eg; /var/www/. this will replace the "it works" with you web page

---

### Post by confusedstingray on 2009-10-22
I forgot to mention to check your router make sure it is forwarding the http protocol to your server. Depending on the router you should have a function port forward and set it to your server ip. so some thing like HTTP port 80  to 192.168.1.100 just a example.

---

### Post by NobuStarwind on 2009-10-22
I don't use a router. I explained earlier why I changed the port number is cause my Internet provider blocks port 80. I had the same problem on Vista but I was able to bypass it by changing the port number. Now shouldn't it be no different on Ubuntu?

---

### Post by volkswagner on 2009-10-22
> **NobuStarwind said:**
> What exactly are you referring to? Like set firewall to allow Localhost:90 or type Localhost:90 into web browser?

Are you using server edition?  How are you trying to access the page?

When you set Apache to a non standard port, you will need to specify the port for each url.

So you will always need to add :90 to the domain name.

ie:  [http://www.example.com:90](http://www.example.com:90) , [http://server.ip.address:90](http://server.ip.address:90) , [http://192.168.1.118:90](http://192.168.1.118:90).

---

### Post by Barriehie on 2009-10-22
What did you edit in what files to change it to port 90?

Barrie

---

### Post by NobuStarwind on 2009-10-22
I did check each url with :90 at the end of them. but still not work. the only file I've edited was the ports.conf which is what the apache faq tells me to edit. listen:80 or something like that and changed to listen:90. I can't remember if there was a : between listen and 90, it was a few days ago since I looked at it.

---

### Post by scragar on 2009-10-22
> **NobuStarwind said:**
> I did check each url with :90 at the end of them. but still not work. the only file I've edited was the ports.conf which is what the apache faq tells me to edit. listen:80 or something like that and changed to listen:90. I can't remember if there was a : between listen and 90, it was a few days ago since I looked at it.

There is a space, not a colon in the apache config, and it's upper case L
```
Listen 90
```

---

### Post by Barriehie on 2009-10-22
> **NobuStarwind said:**
> I did check each url with :90 at the end of them. but still not work. the only file I've edited was the ports.conf which is what the apache faq tells me to edit. listen:80 or something like that and changed to listen:90. I can't remember if there was a : between listen and 90, it was a few days ago since I looked at it.

I can't remember the default install value but in /etc/apache2/apache2.conf you should have these to lines:

```

# Include ports listing
Include /etc/apache2/ports.conf

```

Also, after you've made the changes to the .conf file(s) are you restarting apache?

```

sudo /etc/init.d/apache2ctl restart

```

Barrie

Edit: As an after thought...  I've got mine running on port 45826 and i'm including a virtual host definition for my machine.

---

### Post by NobuStarwind on 2009-10-23
Yes I restart the Apache server upon after changing the port number. And yes it's listen 90 not listen:90, thank you for reminding me. And someone asked if I was on Ubuntu Server Edition, no I am on Desktop Edition, but in another thread someone told me Apache would run fine on Desktop Edition.

---

### Post by Barriehie on 2009-10-23
What about the hosts and hosts.allow files in /etc.

/etc/hosts
```

127.0.0.1 localhost

```

/etc/hosts.allow
```

ALL: localhost

```

Mine is running on 8.04 Desktop Edition.

---

### Post by NobuStarwind on 2009-10-23
oh ok I'll check that.

---

