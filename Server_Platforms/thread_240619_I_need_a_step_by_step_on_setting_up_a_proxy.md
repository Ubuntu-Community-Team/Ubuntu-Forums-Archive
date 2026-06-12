---
title: "I need a step by step on setting up a proxy"
date: 2006-08-21
forum: Server Platforms
---

### Post by CameronCalver on 2006-08-21
Hello i am the biggest n00b at proxy servers as you can get but i would like a proxy server for http ftp and others so that websites that a regular visited sites get saved in a cache so and so i can filter sites out.
I would like this to be able to be acessed from within the network and from outside of the network.
Im not sure how good the computer has to be for a proxy server myn is a
550mhz celeron and 390mb ram with 10gb hdd i desperatly need someone that will stick with helping me for a while and someone that will give me step by step instructions
thanx

---

### Post by lamego on 2006-08-21
Here are the detailed instructions to setup a proxy server:
[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)

---

### Post by CameronCalver on 2006-08-21
will this save regulary visited sites in a cache to improve internet spead

---

### Post by Ahriman on 2006-08-21
There is also this: [http://www.squid-cache.org/]("http://www.squid-cache.org/")

---

### Post by CameronCalver on 2006-08-21
lamego will this proxy allow access from outside the lan and also with this section in the help where it says 

#acl our_networks src 192.168.1.0/24 192.168.2.0/24
#http_access allow our_networks

You'll need to change 192.168.1.0/24 to match your network. Unless you have a second subnet you can delete 192.168.2.0/24 

what does that meen does it meen your lan ip and do i just do 
```
acl our_networks src 192.168.1.102
```
is that right

---

### Post by CameronCalver on 2006-08-21
ok i can now acces the internet threw my proxy but on a computer i cannon how do i make it allow certain ip addresses ?

---

### Post by fdoving on 2006-08-21
If your IP address is 192.168.1.102 you should set:
```

acl our_networks src 192.168.1.0/24

```

in squid.conf to allow everyone on your LAN to use the proxy.


- Frode

---

### Post by CameronCalver on 2006-08-21
ok i forward port 3128 to 192.168.1.102  how do i access it form outside of the lan just with my ip?

---

### Post by talrasha on 2006-08-21
There is also in
[https://help.ubuntu.com/ubuntu/serverguide/C/squid.html](https://help.ubuntu.com/ubuntu/serverguide/C/squid.html)

And this documentation is offcially created by Ubuntu Developers :)

---

### Post by CameronCalver on 2006-08-22
ok what about this for these questions ok
1. i no in the help it said how to block websites but i didnt really get it so if i have the file block.html in my /var/www folder and i have apache set up how do i block certain words in websites and whole url's

2. If i have my proxy set up at home with my 512kbs connection and i have forwarded port 3128 to 192.168.1.102 if i get on a computer outside of my lan in connection setting would it be the same but not 192.168.1.102 my public ip ? and if want to access it outside of my lan would it use my 512kb/s download speed or the 256kb/s speed on the computer that i am on

3.How do i set the cache folder so if a website is visited more than 3 times it saves it into /home/user/cache dir but only saves up to 100mb?

---

