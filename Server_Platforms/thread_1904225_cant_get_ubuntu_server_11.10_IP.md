---
title: "cant get ubuntu server 11.10 IP"
date: 2012-01-04
forum: Server Platforms
---

### Post by nickos on 2012-01-04
I installed LAMP at ubuntu server 11.10 .I type ifconfig | grep inet and get the ip 192.168.3.90 ......i type it to my mum's netbook and expect to get the "It works!" message but in fact i get "server not found"....i also get "temporary failure resolving us.archive.ubuntu.com" when typing sudo aptitude update .... What is wrong?????


Thanks!

---

### Post by spynappels on 2012-01-04
Can you please post the output of the following commands:

```
cat /etc/network/interfaces
```
and
```
cat /etc/resolv.conf
```

I think you are trying to get the webserver from your Mum's computer, but where are you running the sudo aptitude aptitude update?

---

### Post by nickos on 2012-01-04
thanks for your answer.I am trying to view the web server's content from my mums netbook which is inside the network.In fact i was able to view my main computer's server's content with my mum's netbook which means that it works.


here are the outpouts:

```
#This file describes.....
#also text here
#The primary network interface
auto eth0
iface eth0 inet static
address 192.168.3.90
gateway 192.168.3.1
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255
```


```
search test.com
nameserver 192.168.3.2
```


Thanks for your reply!

---

### Post by spynappels on 2012-01-04
Ok, I think we may have 2 different issues, and I'll talk about them in reverse order.

To access a URL from the server, even using the aptitude (or apt-get) update, your DNS needs to work.
Have you set up your own DNS server? the resolv.conf points to 192.168.3.2, which is not your router IP (192.169.3.1) If you have your own DNS server set up and it is not working correctly, you could add a line to resolv.conf like below:
```
nameserver 8.8.8.8
```
This will add Google's DNS servers as a fallback DNS server for the primary one (192.168.3.2)
Don't forget to run
```
sudo /etc/init.d/networking restart
```
just to make sure new settings have taken effect.


As for accessing the server's webpage from the netbook, there could be a few different things going on. Can you ping the webserver from the netbook? Can you access the webpage from another computer in the LAN?

---

### Post by nickos on 2012-01-04
> **spynappels said:**
> Ok, I think we may have 2 different issues, and I'll talk about them in reverse order.

To access a URL from the server, even using the aptitude (or apt-get) update, your DNS needs to work.
Have you set up your own DNS server? the resolv.conf points to 192.168.3.2, which is not your router IP (192.169.3.1) If you have your own DNS server set up and it is not working correctly, you could add a line to resolv.conf like below:
```
nameserver 8.8.8.8
```This will add Google's DNS servers as a fallback DNS server for the primary one (192.168.3.2)
Don't forget to run
```
sudo /etc/init.d/networking restart
```just to make sure new settings have taken effect.


As for accessing the server's webpage from the netbook, there could be a few different things going on. Can you ping the webserver from the netbook? Can you access the webpage from another computer in the LAN?

so will have to change the resolv.conf file into nameserver 192.168.3.1 which is my router IP?Sorry if these are noob questions its my first try with ubuntu server i installed full LAMP at my ubuntu natty and it works great and is accesible by the notebook and other computer's inside the lan.However i seem to be in trouble with only ubuntu server's command line.

---

### Post by nickos on 2012-01-04
i may sound silly but DOES THE SERVER HAVE INTERNET CONNECTION?or it is not accesible because of that?damn im getting pissed off.....

---

### Post by spynappels on 2012-01-04
> **nickos said:**
> so will have to change the resolv.conf file into nameserver 192.168.3.1 which is my router IP?

You could, but I would also add the other line below that entry, just for a failback solution.
You can test internet connectivity and URL resolution by simply pinging [www.google.com](www.google.com), This will check if [www.google.com](www.google.com) can be resolved (so DNS is ok) and whether you can ping it (which means you have internet connectivity).

You do not have to have internet connectivity to view the served pages internally on your LAN, but let's get the DNS sorted first and then move on to the webserver problem.

---

### Post by nickos on 2012-01-04
> **spynappels said:**
> 
You can test internet connectivity and URL resolution by simply pinging [www.google.com](www.google.com), This will check if [www.google.com](www.google.com) can be resolved (so DNS is ok) and whether you can ping it (which means you have internet connectivity).

You do not have to have internet connectivity to view the served pages internally on your LAN, but let's get the DNS sorted first and then move on to the webserver problem.

i edited the /etc/resolv.conf file which only contains:

```

nameserver 8.8.8.8

``` as you said

how can i ping [www.google.com?](www.google.com?) how can i get the dns sorted?


Cheers

---

### Post by spynappels on 2012-01-04
In the terminal just type:
```
ping www.google.com
```
 Ctrl+C will stop the pings, just a couple will tell you if it is working.

---

### Post by nickos on 2012-01-04
i tried and after waiting for about 30 seconds it says unknown host google.com

---

### Post by nickos on 2012-01-04
Alright first of all im f@@@@ing pissed with that p!ece of sh*t!!!!!!
At first it worked excellent and then nothing!I tried installing it again and during the installation it says that it found 3 internet connections,eth0,eth1 and wireless.I have chosen eth0 at first,somethings wrong it says.eth1 same thing,same thing for wireless!!!!!!!!!!!!!!Then all the packages i try to install do nothing and so does ping google.com !!!I think i will remove that idiotic command line thing and install ubuntu 10.04 LTS and install LAMP there with all the necessairy packages,unless someone can help me get that Server going on!For god sake ubuntu!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by spynappels on 2012-01-04
Ok, if that's how you feel about it, have fun with that.

I'm afraid I can't offer instant gratification. Your first post on this topic in a volunteer support forum was 6 hours ago, there is always paid support if we're too slow.

---

### Post by nickos on 2012-01-04
> **spynappels said:**
> Ok, if that's how you feel about it, have fun with that.

I'm afraid I can't offer instant gratification. Your first post on this topic in a volunteer support forum was 6 hours ago, there is always paid support if we're too slow.



lol :D 

what do you recommend?i did what you said but still nothing..whats the next suggestion?should i move to standard ubuntu and install it there?of course i appreciate your help but its so hard :P

---

### Post by nickos on 2012-01-04
I decided to reinstall it ,with a better mood(lets see)

ping google.com still returns unknown host.

now i want to set it a static ip adress so that i can acess it from computers in the network.

here are the files:

/etc/network/interfaces 

```

inet addr:127.0.0.1 Mask 255.0.0.0
inet addr : 1/128 Scope Host

```

resolv.conf has something with auto lo inside.

---

### Post by nickos on 2012-01-05
i tried with the fresh install:


i edited the file network/interfaces :


```

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

resolv.conf didnt exist so i created a new one :

```

nameserver 192.168.1.100 
```

tried to open 192.168.1.100 from my main computer in the lan and doesnt load.ping google.com doesnt work either.i get unkown host error.

---

