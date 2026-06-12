---
title: "Hosting Advice?"
date: 2012-09-25
forum: The Cafe
---

### Post by TheodoreP on 2012-09-25
Currently my site is freely hosted by 000webhost.com, but for some  reason when a user uploads a new recipe with a custom image or the  default no image image  the mysql database is corrupting the file and my  showimage.php script can't display it. Thus I am looking into new web  hosts. I am open to all possibilities whether they be paid hosting or  free hosting. I am just looking for a few places to start looking in.

As well if anyone knows of any way to use a desktop running Ubuntu  server as a professional production server I would really like to know  if it is possible. As well, does anyone know if it is possible to  register a domain personally for free. If so, please explain how? Back  to the Ubuntu server install info. I am wondering about if Ubuntu server  is capable of being used as a production server because my parents have  an old Compaq desktop in the basement that if possible I would like to  use as a production server. Right now it is not being used at all. If I  can use it as a production server for my site I will just do that  instead of paying for hosting and save my money to upgrade the server  hard drive and other equipment.

I thank you for all the information you can give me.

---

### Post by BrianBlaze on 2012-09-25
For a free solution you could always host the website from any linux server from home the problem is if you want a domain name you are going to have to pay no matter what... on the free side you can always just get to your website with the IP and port... but no baisically you will rely on crappy free hosts or pay money for the good stuff...

---

### Post by TheodoreP on 2012-09-25
> **BrianBlaze said:**
> For a free solution you could always host the website from any linux server from home the problem is if you want a domain name you are going to have to pay no matter what... on the free side you can always just get to your website with the IP and port... but no baisically you will rely on crappy free hosts or pay money for the good stuff...

So Basically, what your saying is that ubuntu server can be used to publicly host my site. But I will still need to pay to obtain a professional domain. Have I understood what your saying correctly?

---

### Post by HugoSerrano on 2012-09-25
Sure you can use that old PC. You don't need the Desktop version. Can install ubuntu server.

You will need to install a lamp server and a ssh server so you can login into your PC/Server remotely.

Create a no-ip account, or other, and install the client in your server, or check if your router supports it. 
You will need a place where you can manage your dns. But probably you got your domain in godaddy or something like that, so you can manage it there.
Create a CNAME entry, pointing for the no-ip (or other) domain name your created. Of course, if you don't have any domain, you can use that one that you created in no-ip! No problem.

So, without great tears, after you got ubuntu server installed:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install openssh-server
sudo apt-get install lamp-server^

Now you can access you webserver placing the private server IP on a browser.
Next step, port forwarding in your router. port 80 TCP for server private IP. You need to give a static IP to server.
Also, port forwarding port 22 TCP, so you can access server CLI from outside.

Now, place your code in folder /var/www/
and restore a dump from your database.

This it's a very simple guide, as I don't know what's your skills, so if you need help in any of this, just tell and we help!

Regards!

---

### Post by Mmmbopdowedop on 2012-09-25
All I can add is that your old host probably used phpmyadmin

So if you run

"apt-get install phpmyadmin"

You can access it via [http://localhost/phpmyadmin](http://localhost/phpmyadmin) if you're on your server
or
xx.xxx.xxx.xx/phpmyadmin

x's being your IP or domain name

---

### Post by sandyd on 2012-09-25
> **MasterProgram said:**
> Currently my site is freely hosted by 000webhost.com, but for some  reason when a user uploads a new recipe with a custom image or the  default no image image  the mysql database is corrupting the file and my  showimage.php script can't display it. Thus I am looking into new web  hosts. I am open to all possibilities whether they be paid hosting or  free hosting. I am just looking for a few places to start looking in.

As well if anyone knows of any way to use a desktop running Ubuntu  server as a professional production server I would really like to know  if it is possible. As well, does anyone know if it is possible to  register a domain personally for free. If so, please explain how? Back  to the Ubuntu server install info. I am wondering about if Ubuntu server  is capable of being used as a production server because my parents have  an old Compaq desktop in the basement that if possible I would like to  use as a production server. Right now it is not being used at all. If I  can use it as a production server for my site I will just do that  instead of paying for hosting and save my money to upgrade the server  hard drive and other equipment.

I thank you for all the information you can give me.

Shared
[http://www.webhostingtalk.com/forumdisplay.php?f=4](http://www.webhostingtalk.com/forumdisplay.php?f=4)

VPS
[http://www.webhostingtalk.com/forumdisplay.php?f=104](http://www.webhostingtalk.com/forumdisplay.php?f=104)

If your going for a Shared web host, check out Stablehost, MDDhosting, HawkHost, [MediaLayer ]("http://www.medialayer.com/")and [A Small Orange]("http://asmallorange.com/")

If you are going to a VPS, check the stickies at the top of the forum. I would probably check out WizzSupport (they have a promo going on [here]("http://www.webhostingtalk.com/showthread.php?t=1194174&highlight=wizzsolutions"), and its fully managed), OneProvider, StyleX networks, BuyVM, Direct Space, and SecuredDragon

---

### Post by sandyd on 2012-09-25
> **Mmmbopdowedop said:**
> All I can add is that your old host probably used phpmyadmin

So if you run

"apt-get install phpmyadmin"

You can access it via [http://localhost/phpmyadmin](http://localhost/phpmyadmin) if you're on your server
or
xx.xxx.xxx.xx/phpmyadmin

x's being your IP or domain name

just don't dl phpmyadmin from sourceforge - one of their mirrors is compromised, and dropped some real nasty stuff into phpmyadmin that allows others to execute sql queries.

Im pretty sure you don't want that.

---

### Post by CharlesA on 2012-09-25
> **sandyd said:**
> just don't dl phpmyadmin from sourceforge - one of their mirrors is compromised, and dropped some real nasty stuff into phpmyadmin
This. If you are going to run phpmyadmin, just install it from the repos.

Either that or just learn how to use sql itself, it isn't that difficult.

Also: Make sure it is not accessible from the internet.

---

### Post by TheodoreP on 2012-09-26
As well that old pc in the basement I also have a 1TB WesternDigital External Harddrive. Would that be able to be used as a public hosting server, using ubuntu server. My router has a usb connectivity option, so I would just probably plug-it directly into the router once everthing is set-up.

---

### Post by CharlesA on 2012-09-26
I doubt your router would work for hosting a website. Normally those with USB support are for file sharing only.

Just use an old machine and secure it and you should be good to go.

---

### Post by TheodoreP on 2012-09-26
> **CharlesA said:**
> I doubt your router would work for hosting a website. Normally those with USB support are for file sharing only.

Just use an old machine and secure it and you should be good to go.

Thanks for the info, I just thought i would ask about it. So that I could say that I've done my research and learned what the best setup is for a personal home hosting server for a website.

---

### Post by CharlesA on 2012-09-26
> **MasterProgram said:**
> Thanks for the info, I just thought i would ask about it. So that I could say that I've done my research and learned what the best setup is for a personal home hosting server for a website.
Also keep in mind that most major ISPs (at least the ones over in the US) block port 80 and port 25 on residential connections, and usually have a clause in their terms of service that forbids the running of servers.

Just something to keep in mind.

---

### Post by CharlesA on 2012-09-26
> **MasterProgram said:**
> Thanks for the info, I just thought i would ask about it. So that I could say that I've done my research and learned what the best setup is for a personal home hosting server for a website.
Also keep in mind that most major ISPs (at least the ones over in the US) block port 80 and port 25 on residential connections, and usually have a clause in their terms of service that forbids the running of servers.

Just something to keep in mind.

---

### Post by TheodoreP on 2012-09-27
I have ubuntu server loaded on the basement computer and alls I get is a terminal window? Is this normal or should it look like the desktop version?

---

### Post by CharlesA on 2012-09-27
That is normal. The server edition does not include a GUI.

---

### Post by Primefalcon on 2012-09-28
servers designed to be as light and fast possible since they typical do very hard workloads (serving thousands of request for example).

So they get rid of unnessary bloat that can interfere with performance... such as a GUI... you can install one if your really want, by sudo apt-get install ubuntu-desktop... but really why?

also remember all those extra dependances that create a gui desktop can also introduce possible attack vectors too

---

### Post by CharlesA on 2012-09-28
> **Primefalcon said:**
> servers designed to be as light and fast possible since they typical do very hard workloads (serving thousands of request for example).

So they get rid of unnessary bloat that can interfere with performance... such as a GUI... you can install one if your really want, by sudo apt-get install ubuntu-desktop... but really why?

also remember all those extra dependances that create a gui desktop can also introduce possible attack vectors too
Yep. As a general rule, it is best to have as few packages installed as possible if you have a server exposed to the internet because it lessens the number of packages that could possibly be exploited.

That being said, if you want a GUI, just install a Ubuntu desktop.

---

### Post by TheodoreP on 2012-09-29
Has anyone used the asimpleorange.com web-host before? If so, how good are they? What is the difference between shared hosting and regular hosting plans?

I have come to the conclusion that I don't really know how to work the terminal as good as I need to be to use the server edition of Ubuntu. However that is not the only reason why I am giving that up for now. Reason two is that the old desktop doesn't have a built wireless card and is quite far from the router. Although it does have a usb wireless adapter plugged in though it for one reason or another will not connect to the INTERNET. So I will just pay for hosting and brush up my computer skills and try again later in life.

Thanks for all the information you've provided me though, it was still helpful and informative.

---

### Post by sandyd on 2012-09-29
Go to [http://webhostingtalk.com](http://webhostingtalk.com), and put (including the quotes) "A Small Orange" into the search box.

You will find plenty of reviews and reccomendations for them there.

Medialayer (if you want speed) is probably the second-best IMO. They had extremely responsive support, even in the middle of the night, or at 4am in the morning :O.

The main problem is that they limit domains. If you have only one domain though, it shouldn't be a problem. They also have SSD Storage now, so it should be even faster than when I was there ;) They have coupons here [http://www.webhostingtalk.com/showthread.php?t=1195760](http://www.webhostingtalk.com/showthread.php?t=1195760)

Just another warning though - though hosts DO backup your data, it is only as a courtesy to the customer. There have been many times where hosts have not been able to return backups, or backups that are out of date.

Backup your own data. (it is simple in directadmin, there is a button to download the backup package)

---

### Post by mr john on 2012-09-30
Setting up your own server is a good way to go, if your isp allows it. You'd have full control of the server. If you go that route it's important to read up on server security though, so you know the best methods for protecting it. I have this sort of setup in Ireland, but here in Honduras my isp only gave me a shared external ip, so I cant do the necessary port forwarding.

---

