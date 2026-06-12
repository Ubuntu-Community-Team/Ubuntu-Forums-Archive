---
title: "How to make website accessible by the outside world?"
date: 2007-04-12
forum: Server Platforms
---

### Post by elysium444 on 2007-04-12
Hi to all,

I am new to webservers but I spent the last week learning about it and managed to install and run apache2 on my ubuntu 6.10. 

1-My external ip is  **80.91.120.28** and it doesn't change while I restart my pc, so it is static.

2-My internal ip is **192.168.1.4**, I am connected to internet by **lan**.

3-I got a Static DNS Host from **DynDNS**, which is: shpetimandviola.homelinux.com

4-I edit the file **"/etc/apache2/httpd.conf"** by adding the following line
**ServerName shpetimandviola.homelinux.com**

5-I also changed in networking. I attached screenshots for that.

6-the listen port is 80. 

The problem is that others can't connect to my site. And I can connect to it only by typing "http://localhost/", "http://192.168.1.4/" and "http://127.0.0.1/".

Is this because isp is blocking me or a router, how can i get through? 
Please help me :(

---

### Post by 95aspire on 2007-04-12
is the port forwarded for the webserver?

do you have access to your router config?

---

### Post by elysium444 on 2007-04-12
I don't know if the port is forwarded, How can I do that?
No I don't have acces to the router.

---

### Post by elysium444 on 2007-04-12
So, if i forward the port for the webserver (apache2?), my problem is solved? 
Please can somebody help how to forward the port?

---

### Post by Nikron on 2007-04-12
If there is a router that you can't access with its firewall on, I'm pretty sure you can't that webserver up and running.

---

### Post by elysium444 on 2007-04-12
if I gain access to that router, what do I do to fix my problem?

---

### Post by Nikron on 2007-04-12
> **elysium444 said:**
> if I gain access to that router, what do I do to fix my problem?

you forward port 80 to your computer

---

### Post by elysium444 on 2007-04-12
How is this done, whats the command to use, for forwarding port 80 to my pc? An example please

---

### Post by primski on 2007-04-13
Its probably just some select boxes in your router admin panel.

try opening site [http://192.168.1.1](http://192.168.1.1) (your router ip, check your net settings for default gateway), usrename and password are probably default too, if you dont know for sure, try googling for 'router model default password'

---

### Post by elysium444 on 2007-04-13
> **primski said:**
> Its probably just some select boxes in your router admin panel.

try opening site [http://192.168.1.1](http://192.168.1.1) (your router ip, check your net settings for default gateway), usrename and password are probably default too, if you dont know for sure, try googling for 'router model default password'

Couldn't connect to [http://192.168.1.1](http://192.168.1.1).

My situation is like this:
My cable comes from an internet coffee that is near me, They use a pc with windows xp installed and two network card to deliver the signal. The signal cable is connected to a one of the network card and another cable connects from that pc to the hub. and other pc connected to the hub. My cable is connected to their hub... I hope I am clear

Do I have to go and see the ip of the pc where the signal cable is connected and try to connect to that ip for the router, or I can connect through my dns servers which I setup to be able to connect to internet?

Please help.

---

### Post by hockey97 on 2007-04-13
Hi, What router do they have?? 192.168.1.1 is a default link system router ip but can be changed in the routers settings, search google with the router name, if you connect to their router and have a internal ip you would be on a lan which means you have access to the router but depends if they set a password or a key on the router.

what you need to do is find the ip adress of the router you can use ettercap which is a sniffer it would show the ip adresses on the lan ect internal network also it would show up the routers ip adress type the ip adress of the router in your web browser  a login would then be prompet then for password type admin this is default if the person made a password or user name then you would have to use that once passed that you get in a webpage interface looking thing where you can config your router you look at the tabs try to find forward or port forward or program forward anything that has forword in it and has check boxes mostly their would be names like ftp, http ect next to names shows the default ports for http or webpages it's 80 or 8080 for smtp or mail server ect it's 25 ect their then next to the ports are check boxes you need to check the 80 box or 8080 box. these makes the router and lets you forward request only on those ports, how ever their are some routers that have like dMZ or somthing that you have to go in, it would should be on status and a tab named DMZ ect their will be a box for you to input a internal ip adress so like exampl if your internal ip adress is 192.168.2.500  then you put that in , what this option does is tell the router to let internet traffic from your external ip to be forward and see the interal computer, or to that specific computer. this should fix the problem.

---

### Post by elysium444 on 2007-04-16
Thanks a bunch hockey97, for adressing me to ettercap. I found it really cool.
They are using Blue Quartz, and they have changed password.
Any suggestion what to do next?

---

### Post by hockey97 on 2007-11-15
ok sorry for not replying in a long time, don't know if you got it to work.

forgot kinda what the problem was on here??

I took a quick look and guessing your having problmes for people from the internet being able to see your website/server.

well you have a router.

you need to port forward the ports. and also dmz it, 

ok  well first you need to get in your router.

linksys usally you have to type 192.168.1.1, you can check your manuel for it,  their is also a website online that tells how to port forward your router and stuff .

you can type in your external ip address,  google what's my external ip, their are websites that will tell you this, copy and paste it into your web address press enter.

you will get a login promt,  for linksys  by defalt you put the password only , which is admin  .

diffent router company's and different models may have different defaults.

when you log into your router you should see a tab where it say's  port forword. where you can check boxes to enable them.

in linksys they have an option DMZ this where you put the ip of your computer well the internal ipaddress . The DMZ option tells your router to let traffic from the internet go to that computer with that internal ipaddress.

any computer connected to your router get's an internal ip addrss from your router, this changes when you turn off your computer.
becsue the router keeps assinging internal ip address when a computer is turned on and connected to the router to the internet.

so the DMZ would forward traffice to the computer that you gave that computers internal ip.

now you then would go to a tab where it say's application/games
you have to put the last 3 part of the internal address, and also the start and end port, which for webserver usally you just put 80 for start and 80 for end.

when you finish that save it and type in your internal ip address in your browser, you should see apache.

if it went all well,  then you want to test the domain name.

first make sure where you got your domain name or a static ip, that it is config to point to your external ip address.

you then would have to test it by using vtunnel, or any proxy server that will show you what the people see that are from the internet loggin onto your website ect.

Hope this helps.

ettercap-  is  nothing but a sniffer, you can see traffic on your internal network.

I hope you put a password on your router  if you have wireless connect option on.

---

### Post by elysium444 on 2007-11-15
thanks, hockey97.  Now I know how to do it, but didn't solve the problem at that time because the router wasn't mine and I didn't know the password.

---

### Post by hockey97 on 2007-11-16
oh, that sucks, lol  , I one time had to help my dad's friend son, to put a password on their router, I told them how unsafe that is not having a password  while the router is wirless, so I created a password, and they after told me who config the router in the beginning, it was some guy that thinks he know's evertyhing about computer, well he screwed up their config,  they had internet phone service also, so he config it so when a call comes the internet connection would be down  for any of their computers until the person stop talking on the phone.

well I made the password and how the guy config it, was crappy, and the router ended up locking up, I tried connecting their computer to the internet and their router password loging prompt came up I typed the password and it didn't buged, lol then his sister started to freak out, becuse she had to send a paper to her professor the next day.

so I asked  where their router is and dsl modem, and I reset it and it
went to it's defaults and worked.

so routers can goof up lol. 

if you need help with anything else you can alway's im me .

---

