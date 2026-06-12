---
title: "Bulding a web hosting server with ubuntu 9.10  HELP!"
date: 2010-01-25
forum: Server Platforms
---

### Post by programming.name on 2010-01-25
Hi, 
It's been almost a month to try to build my own web hosting server with ubuntu 9.10 server edition and I have got nothing. I did a lot of googling and it was not enough so I just bought a book on how to admin. a ubuntu server, but it was still not helpful at all. 
Could anyone provide links or explanation that suit me on how to build ubuntu server with ubuntu 9.10 server edtion please? My circumstance is like this:

- Internet accessed by 4 wired/wireless computers via a router
- My IP is dynamic
- I purchased my own domain

My preffered server setting:
-Since this is only a learning purpose, I don't want to have a static IP address to pay extra money, and I just  want to use my dynamic IP address assigned by the ISP.
-I want to use my own DNS server (Although I don't really know what this means, I guess in this case I don't need to depend on the site like EditZone.com (not sure).
- All I want is everyone in the world can access my website.

PLEASE HELP!


ps. I asked someone how to set up the DNS server, and they said my domain's nameserver(DNS) has to be chaged to my IP. But I'm pretty confused as I only have ONE dynamic IP address from ISP, and to change the DNS for my purchased domain requires two DNSs being primary and secondary. What should I do? Do I nned to own Ubuntu DNS like BIND9 to solve this problem? Since I have a lack of concept of how a sever works, please explain in a extrem super ultra easy way please!

Thanks a lot!

---

### Post by prshah on 2010-01-25
> **programming.name said:**
> try to build my own web hosting server with ubuntu 9.10 server edition 

- Internet accessed by 4 wired/wireless computers via a router
- My IP is dynamic
- I purchased my own domain

My preffered server setting:

- All I want is everyone in the world can access my website.


Here's some simple steps and background information:
- First, install Ubuntu Server 9.10, and during installation, choose to setup a LAMP system. Set up your networking as per your LAN configuration.

- After completing the setup, update your system```
sudo apt-get upgrade && sudo apt-get update
```
- After completing the setup, install lynx, which is a text mode browser.```
sudo apt-get install lynx
```
- After lynx is installed, check if your webserver is accessible on the server machine itself; ```
lynx http://127.0.0.1
``` This should give you a blank screen with "It works!" if everything is setup correctly.

- Next, check if any of the other computers on the LAN can access your server; in the address bar, give the IP address of your server, eg. [http://192.168.1.13](http://192.168.1.13) . You should get the same "It works!" message.

- Then, you have to allow access to your server from the Internet. Sitting between your server and the Internet is your router. You have to either [indent] # Port forward port #80 (http) to your server's internal IP address (Eg 192.168.1.13)
== OR ==
# Set the DMZ on the router to your server's internal IP address (Eg 192.168.1.13)[/indent]
To find out how to change these settings on your router, visit [http://www.portforward.com](http://www.portforward.com) and look up your model for instructions.

- Find out your external IP address by visiting whatismyip.com using lynx from your server (Eg 54.65.75.300 - IP address purposely obfuscated)```
lynx http://www.whatismyip.com
```
- Now, with a computer that uses a DIFFERENT Internet connection from your server (Eg, not any computer on the same LAN as your server), try to browse to your external IP. In the browser, enter [http://54.65.75.300](http://54.65.75.300) (replace with the IP address you got from whatismyip.com). If all is correct, you should get the "It works!" message again.

- For dynamic DNS to work, you will need the help of a forwarder such as DynDNS.org. To use your own domain name, you will probably have to get a paid account at DynDNS. The free account will give you a domain name such as yourwebserver.dyndns.org.

- After you setup a (free / paid) account at DynDNS.org, you will have to configure your computer / router to report it's dynamic DNS to DynDNS.org. [indent]- Usually, most modern Internet routers (aka ADSL modem) will have settings for dyndns.
- If your router does not have this, then you need to setup "ddclient" on your server```
sudo apt-get install ddclient
```[/indent]
- Now you can check if your server is accessible through the domain name that you have setup at DynDNS.org.

These are general instructions. Try them, and if you run into problems, for more specific steps, please post back with your exact question.

---

### Post by BkkBonanza on 2010-01-25
All above is good. I wanted to add that you shouldn't attempt to run a public DNS server off a dynamic IP. You don't need to, there is no advantage for you, and you will have problems trying to update the IP for the primary/secondary DNS records. Just use a free DNS server like zoneedit or your domain registrar. Will work much better and is much easier to set up. You simply point your domain to your current IP and enable dynamic dns. Then configure your router to use dynamic dns to update that.

---

### Post by BobVila on 2010-01-25
Go to zoneedit.com and use them or another free DNS host. No use paying for the DNS servers, and I definitely wouldn't bother trying to host this yourself on a dynamic IP. Once you've registered your domain, they'll give you a pair of DNS servers to add to your domain listing. Go back to your registrar, enter that info.

A dynamic update client will be helpful to keep your IP current with zoneedit or whoever you go with.

---

