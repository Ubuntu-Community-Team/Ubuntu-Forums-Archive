---
title: "Web server not accessable internally"
date: 2008-07-01
forum: Server Platforms
---

### Post by kerryhall on 2008-07-01
Hey all! I am sure this is a simple problem, but I am have difficulty solving it.

I have set up a web server on my home network. The web site can be accessed by the outside world, (tested with proxy) but when I try the domain name (eg [www.kerryhall.com](www.kerryhall.com)) internally the web site won't load. When I type in the local IP address of my web server (192.168.1.101) it works, and when I try 192.168.1.1 I get the web log on page for my router. And of course 127.0.0.1 works from the server itself.

Basically I would like [www.kerryhall.com](www.kerryhall.com) to work for my internal network. I know this has something to do with DNS and BIND9, but I really have no idea....

My friend bought the domain for me, and has it redirect(?) to my ip address where I just have it port forward to my server. So internally, can I set up google.com or x.y.z.com to redirect to whatever internal server I want?

Thanks, sorry about how poorly worded this question is.

---

### Post by 505 on 2008-07-01
I think it is not a linux problem but a problem with your router. I had the same issue with a router once. The key is to enable NAT loopback on the router. How to do that depends on your router of course.
I had these issues with a Zyxel router and it involved making a telnet connection and entering a command in the command mode. It could not be done using the web interface.

---

### Post by kerryhall on 2008-07-01
So I don't need to set up a local DNS server? Could that work as a work around if I can't figure out loopback on my router?

---

### Post by 505 on 2008-07-01
That I really don't know. I have been running a server for more than a year know (Debian in this case) and no DNS server is installed.

My setup is```

internet ---> router  ---> desktop
                      \--> server
```
So the server does not act as gateway for the whole network. Actually, I don't even know it another setup would change anything, that is if you then have a need for BIND9.
All I can say it this is how I have done it and it works.

PS: one other thing. If you do enable NAT loopback, you might also have the change the startup script of your router, otherwise NAT loopback will be off again after a router reboot (or power failure).

---

### Post by kerryhall on 2008-07-01
I would just like to be able to access my server internally with a name (kerryhall.com or whatever) just like anyone can externally.

Thanks!

---

### Post by kerryhall on 2008-07-01
A clarification:

ubuntu.kerryhall.com works from the local network

[www.kerryhall.com](www.kerryhall.com) does not

---

### Post by camccall on 2008-07-01
Try running this command and post the output
```
dig www.kerryhall.com
```
This way we should be able to determine if it's a dns issue or not.  I was able to access your website no problem.  I think it's probably a local dns look-up issue. 
Also if check your /etc/hosts file and make sure you don't have an incorrect entry for [www.kerryhall.com](www.kerryhall.com) there.

---

### Post by kerryhall on 2008-07-01
It's not actually kerryhall.com, i was using that domain as an example, as I have had this happen on several networks with different web sites. I would prefer to not post the actual web sites, as I am trying to help out a few friends with setting this stuff up, and I don't know how much of their personal info they want posted. Needless to say, I am almost positive that it is a local dns problem, the web site can be accessed as a URL fine from any computer except on the local network. On the local network it can only be accessed by ip address. 


For info below:
*kerryhall.com is just a placeholder
*Local machine means any local machine except the server
*The server's ip is static, set to 192.168.0.3
*The server's hostname is ubuntu.kerryhall.com

Summary: 
External machines trying "kerryhall.com" -> works
External machines trying "ubuntu.kerryhall.com" -> works (do not want!)
Local machines trying "kerryhall.com" -> router login
Local machines trying "ubuntu.kerryhall.com" -> router login (???)
Local machines trying "192.168.0.3" which is the server ip -> works
Server trying "192.168.0.3" -> works
Server trying "kerryhall.com" -> "address not found"
Server trying "ubuntu.kerryhall.com" -> works
Server trying "127.0.0.1" -> works

Corrections I want to happen:
Local machines trying "kerryhall.com" -> should work [high priority]
Server trying "kerryhall.com -> should work [high priority]
External machines trying "ubuntu.kerryhall.com" -> should be "address not found" [medium priority]
Local machines trying "ubuntu.kerryhall.com" -> should be "address not found" [low priority]
Server trying "ubuntu.kerryhall.com' -> should be "address not found" [low priority]


I have been reading BIND9 docs for the past week or so, with little to no comprehension... :confused:

I don't think I could have made this more complicated if I had tried, but thanks for all your help!

---

### Post by osjak on 2008-07-01
(Someone already beat me to it, so I removed my unnecessary question.)

---

### Post by kerryhall on 2008-07-01
Correction: hostname was ubuntu.kerryhall.com

I added the line 

192.168.0.3 kerryhall.com

to my hosts file,

and i changed the hostname file from
ubuntu.kerryhall.com to
kerryhall.com

then did 
sudo /etc/init.d/hostname.sh

result:
External machines trying "ubuntu.kerryhall.com" -> still works, dont want
Local machines trying "kerryhall.com" -> still router login
Local machines trying "ubuntu.kerryhall.com" -> still router login (???)
Server trying "kerryhall.com" -> works(!!)
Server trying "ubuntu.kerryhall.com" -> address not found(!!)

so it looks like two of the five things are fixed.

but this is without dns i guess

thanks again!

---

### Post by hockey97 on 2008-07-01
hold up, Ok this is what you do.

First on the service that are providing the domain name you need to have the external ip address in the a record. So I can see the external traffic works.

Now you want to be able to get on your website but found out any internal computer can't log on but yet people outside your house ect can access your website ect.

well here is what you do, the people that are hosting your domain name, make a A record for your internal ip address somthing like 192.168.1.#.

ok after you got that then edit your host file, by default it's in /etc/hosts

change the permissions so you will be able to save the edit settings.

add their your domain names and ip address.

so for example

192.168.1.#  yourdomain.com
67.148.2.#  yourdomain.com

these show 2 ip addresses external and internal it's really just the same thing you done for the external but just only different by the ip adress.

you also need to change the DNS a record on your DNS server you have meaning bind9 ect. Do the same thing as you did for the external but this time use the internal ip address.

so you should have the exact same thing as what you done with the config on for the external traffice but the only difference would be the ip address you would need to just add your internal ip address.

hope this helps.

---

### Post by kerryhall on 2008-07-01
Even more ridiculous: [www.kerryhall.com](www.kerryhall.com) doesn't work from the server, but kerryhall.com does....

---

### Post by kerryhall on 2008-07-01
Will give that a try, thanks a ton! :)

---

### Post by hockey97 on 2008-07-01
Ok so when you try your website somthing.com you get your router instead of your website.


the easy thing is how did you config  your website for external traffic.

because you just need to do that same thing make new a records but instead of using your external ip address you would use your internal ip address somthing like 192.168.1.#  ect.

you have to have both 2 A records one for externial ip address and one for the internal ip address which would allow people both internally and externally to log on to your website.

you will need to add your internal ip address and your domain name in the hosts file located in /etc/hosts  which is a text file at the bottom.

You would need bind9  a dns server. You need a DNS server on your computer with a records that points to both eternal ip address and internal ip addresses.

so if you know how you setup that domain name and how you got the external traffice to see your website  you just do the same thing as that just adding the same records and file but the only difference would be the ip address, one A record  would point to your external ip like 69.345.1.# then have another A record with the same name as the external one but using the internal ip address like 192.168.1.#.

this should work.

so to sum it up.

create new domain records like A at the people that are hosting your domain name  so you should have 1 external and 1 internal ips that have a record each.

then edit hosts file located in /etc/hosts  add your domain name with your internal ip address.

then edit bind9/dns server.

This should work 

Hope this helps.

---

### Post by hockey97 on 2008-07-01
oh if like  yourdomain.com works but [www.yourdomain.com](www.yourdomain.com) dosen't check if you got a record for that.

All A records needs [www.yourdomain.com](www.yourdomain.com) and yourdomain.com that points to your external ip address and your internal ipaddress.

so their should be  4 A records   2 [www.yourdomain.com](www.yourdomain.com) records and 2 yourdomain.com records.

2 for internal ip addresses  which is consists of [www.yourdomain.com](www.yourdomain.com) and yourdomain.com

then 2 more copies of those record but just change the ip to external.

so A records  are the ones that sends commands to your dns server to respond to those names so you can have as many A record you want but you need to have a copy for the internal ip and another copy for the external ip so people outside from the internet can type that domain name you made and also so you can type that domain name and see your website if you didn't have an A record  for your internal ip then you would see your router login.

hope this helps.

---

### Post by osjak on 2008-07-01
hockey97, I'm pretty sure putting an internal IP into the A record is a bad idea. If you have more than one A record, DNS server just rotates them while accepting DNS requests. In your case, half people (from outside) will get correct IP, and half will get that internal IP and therefore - error. 

I am running a publicly accessible home server with just one A record with no problems. I believe the issue kerryhall is having is within his internal network. It would be great to see the results of that *dig* command that he was asked by camccall, unless he's already answered and I missed it.

---

### Post by camccall on 2008-07-01
Completely agree with you Osjak, that would be a bad idea.

Okay, so what IP address do the host names you are trying to access resolve to when you try and access them.  Dig won't work for this I discovered, try pinging the host names and see what ip address it tries.  

Also as far as [www.kerryhall.com](www.kerryhall.com) not working, that is because you put kerryhall.com in the hosts file only, that file is fairly specific so if you put [www.kerryhall.com](www.kerryhall.com) after kerryhall.com, it should work.  
So your hosts line would look like
192.168.2.2 kerryhall.com [www.kerryhall.com](www.kerryhall.com)


How many machines need to access this locally?  If it's just a few you could just update the /etc/hosts file on each machine to the right ip address.  

As far as the ubuntu.kerryhall.com working, there is a CNAME or an A record for that subdomain that needs to be deleted or pointed in a different direction depending on your needs.  

Sorry about the disjointed post.

---

### Post by hockey97 on 2008-07-01
ok.???

so are you behind a router???

I had the same problem what he was having, This is what I done to fix it and yet many people told me the same thing  which is not true.

I tested this, I tested the outside and inside. Before doing this I was told to config many things which I ended up at the end reinstalling the webserver and dns server again.

I tried this and it worked for me. I never had any failure because of having 2 ip addressed A records.

what happenes is that it will first try the external ip record one then if it fails it trys the second record with the same name but with the internal ip address. which is what you need to bypass the router. If this is not done  then you will get routed to the router.

he could config his router to obtain a different gateway ip but it would make things more confusing.

I don't fully think the dns server roates records, it goes by order so the first A record you made it's the first one tried then if failed it would then try another A record that has the same name and try that.

I have tested this and never had any problems at all. I

The point is  the DNS server job is to point traffice to an ip addres by a name.

so the reason I suggested this is because  your external ip address if you have a router when you type that in you will get routed to your routers login the reason why?? it's because your router is set to be  the internets gateway with that external ip address.

so when he types in his domain name that has only one A record that points to the external ip address it would show him his routers login page instead of his domain website.


I have tested this and this is what I use and stilled worked till this day.

He might have to change the routers port that is another way to get around this but I never done so.

---

### Post by osjak on 2008-07-01
> **camccall said:**
> Dig won't work for this I discovered, try pinging the host names and see what ip address it tries.  

I've been using *wget* to get useful information about http request routes. I know it's a download manager, not a true troubleshooting tool, but it shows all domain name resolutions and Apache redirections while trying to get to the page requested. 

kerryhall, since *dig* is not helping us here, run *wget* on your home page and post it's output. It should show us where your http request chokes:

```
wget http://www.example.com
```

---

### Post by kerryhall on 2008-07-01
I don't actually own kerryhall.com, it was just a placeholder for a random domain that doesn't matter.

Lets say I have a network that isn't connected to the internet at all. There is a dhcp server on it. two other computers are connected.

dhcp and dns server is 192.168.1.1
test1 is 192.168.1.101
test2 is 192.168.1.102

test1 is web server

I want to be able to type [www.example.com](www.example.com) into firefox from any of the three boxes, and have it take me to 192.168.1.101

How do I configure bind9 to do that?

Thats all I need to be able to do.

Thanks!

---

### Post by camccall on 2008-07-01
Hey kerryhall, can you please post the output of either ping or wget, it would tell us a lot.  We understand that you don't want to tell us the actual domain name, we are using kerryhall and example.com as placeholders to. 

 If your computers are resolving things correctly it should not matter what your bind9 is doing, the hostname would resolve to the appropriate external ip address and your computer would access that computer like any other external computer.  Somehow your machine is resolving to an incorrect ip address, if you told us what this ip address was we might be able to pinpoint where the dns problem is.  That is unless your have split dns and then unfortunately I will be unable to help you.

Of course split dns could possibly solve your problem though I don't see the need in this case.  More info here: [http://www.bind9.net/manual/bind/9.3.1/Bv9ARM.ch04.html#AEN767](http://www.bind9.net/manual/bind/9.3.1/Bv9ARM.ch04.html#AEN767)

---

### Post by hockey97 on 2008-07-01
well good luck.

I don't get how it can be an internal problem when it's the router.

he is under a router, the router slits traffic and assigns a computer an internal ip address that the router knows.

dns server does not rotate records. If it was true that dns server roatate records then  if I tried going on my website 4 times then I should have 2 failed attempts this is according to what your saying that the records alternate.

I have tried what I suggested and I was able to go on my website anytime I didn't get any failed or errors at any point.

I am behind a router and when you type in your domain name that points to your external ip address it will route you to the routers login page.

this is what is happening  he can test this by typing his internal ip address in the web browser  which would be somthing like 192.168.1.#

# that means that is where your computer with the server software.Thats your computers internal ip address .  Anyone that is on your network needs to use 192.168.1.#  in order to get your webpage, everyone outside the network needs the external ip address.

the external ip address would act just like the 192.168.1.1 where your router's login is at. so when you type in that domain name it takes to to the external ip address and you then get rerouted to your routers login.

and also you need to make A records for also the domain like [www.mydomain.com](www.mydomain.com)   and mydomain.com

So to me I can tell it's his router that's the problem he has to either reconfig it like change the port or he can make 2 A records. That is the only solution I see.

If you think it's somthing wrong with his internal configs.

then he should just try typing in his internal ip address of his computer with the server software it should take him to his website. If it dosen't then it's an config problem.

if it works and he can see his website or a list of the index then it's the router and DNS records problem.

---

### Post by kerryhall on 2008-07-01
It is just a few machines on the network, but they are all windows machines. I would prefer to be able to add new machines as well and have them work.

---

### Post by kerryhall on 2008-07-01
A ping from the server results in "unknown host"

A ping from the other machines on the network results in a reply from the router (192.168.0.1)

A ping from an external machine results in the domain being resolved successfully

---

### Post by kerryhall on 2008-07-01
All I need is this:

If anyone on my network types [www.kerryhall.com](www.kerryhall.com) it will take them to 192.168.0.3

---

### Post by camccall on 2008-07-01
If you want that and you are running a bind server, you should probably use split dns [http://www.bind9.net/manual/bind/9.3.1/Bv9ARM.ch04.html#AEN767](http://www.bind9.net/manual/bind/9.3.1/Bv9ARM.ch04.html#AEN767).  I personally don't know anything about bind, this was what I found in a quick Google search which seems to be the solution to your problem. 

Just know that you could also edit your computers lmhosts file or /etc/hosts file depending on which OS the system is running.  

Is there a specific reason why you need to access this machine via the local ip address, if you are going to be serving the same information to both internal and external ip's, you should just have the internal machines resolve to the external ip address and access that website like any other site.

---

### Post by windependence on 2008-07-02
> **kerryhall said:**
> All I need is this:

If anyone on my network types [www.kerryhall.com](www.kerryhall.com) it will take them to 192.168.0.3

I'm sorry that this has gone on so long without anyone giving you the real answer. I don't mean to be funny here but no one has given you correct advice.

To fix this problem:

Edit the C:\WINDOWS\system32\drivers\etc\hosts file on EACH of your windows boxes by adding a line like this at the end:

 ```
192.168.1.101   kerryhall.com 
```

This must be done on EVERY windows box you want to access the server from. This is NOT a bind9 issue, and you do NOT need a DNS server even set up on your network for your web site to work. The problem is really the way routers work. They are not going to send your request out to the internet and then have it come back in when the machine knows it's local. The request tries to find the ubuntu.kerryhall.com but cannot because it is not defined anywhere in DNS. Adding an entry in the hosts file lets each computer know that  ubuntu.kerryhall.com  is located at 192.168.1.101 on the internal network. You may need to reboot the Windoze boxes for the change to take effect.

-Tim

---

### Post by MJN on 2008-07-02
> **windependence said:**
> The problem is really the way routers work. They are not going to send your request out to the internet and then have it come back in when the machine knows it's local.
 
Mine does (D-Link DI-614).
 
(I do concede that the OP's obviously doesn't, but just pointing out that many do handle so-called NAT loopback perfectly well)
 
Mathew

---

### Post by windependence on 2008-07-02
Yes, but this is a function usually NOT included in a home router. Some SOHO routers do this and most all commercial routers do too, but the point is HIS obviously didn't and of course this should fix the problem.

You are correct though, you CAN buy them with NAT loopback and they will route traffic as if you were on the outside, it's just not a common feature.

Thanks for pointing this out.

-Tim

---

### Post by kerryhall on 2008-07-02
Awesome, thanks to everyone for their help on this issue!

Most of the routers on the networks I am working on are really shitty, but one of them has openwrt installed on a linksys router.


Does anyone know how I could configure my router so all machines on the local network do the www.kerryhall.com->192.168.0.3 redirection? or if not, how to set up 192.168.0.3 as the dhcp server to do this? Thanks!! :)

---

### Post by hockey97 on 2008-09-03
> **kerryhall said:**
> Awesome, thanks to everyone for their help on this issue!

Most of the routers on the networks I am working on are really shitty, but one of them has openwrt installed on a linksys router.


Does anyone know how I could configure my router so all machines on the local network do the www.kerryhall.com->192.168.0.3 redirection? or if not, how to set up 192.168.0.3 as the dhcp server to do this? Thanks!! :)

I don't think it's possible to do so.

you need to edit every computers host file that is on your network.

Edit the C:\WINDOWS\system32\drivers\etc\hosts file on EACH of your windows boxes by adding a line like this at the end:

Code:

192.168.1.101   kerryhall.com

That is the only way to do it.  

and the A record should be  your external ip address only.

then the host file of each computer needs you internal ip and the domain name.

I wish their is a better way because it's a pain if you have friends bring their computer and use your internet and have him to see my website.

but still this is the only fix that is told currently. I didn't hear any new type of fix around this.

---

### Post by windependence on 2008-09-03
It's possible if the router supports NAT loopback to use his domain name to access his server inside his network. Unfortunately, not too many routers do this. If you can find one that does, they are not too expensive though.

He could also set up an internal DNS server for use with his LAN. A bit much if you have less than say 10 computers, but worth it if you have a lot.

-Tim

---

### Post by bigfatdummy on 2008-09-15
You can always configure your router to use opendns. Within opendns you can have it redirect traffic.

---

