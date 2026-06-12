---
title: "Able to ping internal computers but not outside?"
date: 2008-11-18
forum: Server Platforms
---

### Post by ndnd on 2008-11-18
Hello,
I wanted to check if I am connected to internet or not. 
Running latest UBUNTU Server edition on my Lenovo T61p laptop. 
I am a newbie with linux (admin stuff) details would be helpful. 


Based on notes in forums I was able to configure my network connection (I think..)I am able to ping other computers in the network. 

However, when I ping [www.google.com](www.google.com) 
PING [www.l.google.com](www.l.google.com) (64.233.169.99)56 (84) bytes of data

Nothing happens...

> I hit Ctrl+C 
--- [www.l.google.com](www.l.google.com) ping statistics ---
425 packets transmitted, 0 received,100% packet loss, time 424018ms



When i try 

> 
sudo apt-get install wireless-tools
Reading package lists.... Done
Building dependency tree
Reading state information... Done
wireless-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.




Steps taken to get the network connection 

1) Modified /etc/network/interfaces file 

> #This file describes the network interfaces available on your system and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto etho0
iface etho0 inet dhcp
 

Once again- when I am able to ping other computers from my Laptop. So I do suspect this may be a firewall issue. However, when I connect from the same laptop through Windows (as I have dual boot) no problems. 

Do need to something else or is there a browser or something similar through which I can check my connectivity ? 
I also did as per 

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

> 
ping -n 4.2.2.2 -c 4

I received 

4 packets tranmitted, 0 received, 100% packet loss, time 3010ms


---

### Post by mikewhatever on 2008-11-18
Ubuntu itself shouldn't block the pings, but a lot of routers do, especially external ones. Is pinging the outside all you require? Can you browse the web with Firefox?

---

### Post by hictio on 2008-11-18
Lets do a simple one, can you browse the internet?
Where are you doing this tests? Can you check with someone from IT to see if there is a block on outgoing ping?

---

### Post by ndnd on 2008-11-18
Hello all,
Thanks for the input. So I tried pinging from windows machine- you are right it didn't ping outside. It is also able to get the google address but had a packet loss. 

So there must be some restriction/firewall. 

Now the question is installing packages etc. using apt-get ? How can I do that ? 

Also regarding checking with browser ? How can I do so from the terminal (as I have server edition) and I am not familiar with the commands ?

---

### Post by hictio on 2008-11-18
For browsing from the CLI, I can dearly recommend [elinks](http://freshmeat.net/projects/elinks).
To install it, type:

```

sudo aptitude install elinks (ENTER)

```

It will ask you password, and download and install it (as well as the necessary dependencies)

Then, you can browse the internet, via text, by typing 'elinks' and an enter to start it, it is very good, and might fast :D

---

### Post by cdenley on 2008-11-18
> **ndnd said:**
> 
Also regarding checking with browser ? How can I do so from the terminal (as I have server edition) and I am not familiar with the commands ?

The command commonly used to retrieve files from web servers is wget.
```

wget http://ubuntu.com/

```
You can also test whether you can connect to remote servers using telnet or netcat
```

nc -z -v ubuntu.com 80
telnet ubuntu.com 80

```

---

### Post by ndnd on 2008-11-18
Hi,
Thanks so I installed elinks and it worked fine. I also was able to go to wifi. I tried to surf however, my company's login page appeared and I couldn't figure out how to 'click accept'. 

So anyway it seems Wifi works fine but NOT LAN. 

Is there a way I can get a GUI based browser ? Or will this create too many problems ?

---

### Post by hictio on 2008-11-18
The thing is, you'll have to install a lot of packages due to dependencies, not to mention, that the "Server" tag (of sorts :) ) will be somehow lost on the given machine.
But, yes, you can.

Take a look here [Ubuntu Minimal Desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop), or here [Installation on Low Memory Systems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

If I may ask, what are the specs of your box? Why did you chose a Server install?

The problem with elinks, sometimes the page is coded in a way that you won't be able to navigate it (the same goes for those that only work on Internet Explorer, getting fewer and fewer luckily).
Try, in order to input text, moving to the box, and then hitting the space bar.

---

### Post by ndnd on 2008-11-18
Okay so it did work! 
I was able to go to google using elinks as well as checked telnet. 
Whew this is great...

However, now I will have to tackle the next monster wireless.

---

