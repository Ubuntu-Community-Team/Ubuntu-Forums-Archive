---
title: "I want to setup a Web Hosting Server"
date: 2008-08-19
forum: Server Platforms
---

### Post by rakan_dr on 2008-08-19
Hi,
I'm a website designer and developer and want to setup a web hosting server. I want to Host my website and my clients websites on it, but I don't have enough info about that. Please help me with links and tutorials.

I know that i have to install these on the Ubuntu server machine:
1- Apache
2- PHP
3- Mysql
and to buy a domain name "or an IP, dunno!" for my server, right???
I don't know the recommended internet speed for such a purpose, plz help me with this also.

I know that it's not too complicated to do that especially with Ubuntu and Linux in General, cuz i saw a lot of people hosting their websites on their servers, but with IPs instead of domains such as this one: [http://62.251.79.239/basing/esl/](http://62.251.79.239/basing/esl/)
I don't know what i have to do to make it with domain name,but what i know is that i should buy a domain name and then connect it with the server, right?? Have i to buy an IP or something to connect the domain with my hosting server??? 

Thnx.

---

### Post by El Conquistador on 2008-08-19
ok in the terminal type in "tasksel" without the quotes and then choose Lamp server. that will take care i believe all of those apps that you listed if not all then atleast most. hope it helps

---

### Post by cariboo on 2008-08-19
For a domain name go to some service like Godaddy. They can walk you through the process of setting things up. As far as an ip address, talk to your isp to see what kind of services they offer.

As far a setting up your server have a look at this document:

[http://www.debian.org/doc/manuals/network-administrator/index.html#contents](http://www.debian.org/doc/manuals/network-administrator/index.html#contents)

Jim

---

### Post by rakan_dr on 2008-08-19
Does the ISP has a role in the Hosting operation???
Can i make everything without the need of my ISP??? I'm not talking about the internet of coures!!!

By the way what is the recommended internet speed for such a purpose?
I have a ADSL connection with 3Mb/s.

---

### Post by johan.alfa on 2008-08-19
> **rakan_dr said:**
> Does the ISP has a role in the Hosting operation???
Can i make everything without the need of my ISP??? I'm not talking about the internet of coures!!!

By the way what is the recommended internet speed for such a purpose?
I have a ADSL connection with 3Mb/s.

You must check your ADSL connection upload vs download speed.

greetings,

---

### Post by mellowd on 2008-08-19
If you plan to host clients sites as well I would recommend you host the server itself in a datacentre (colo if you will)

It's not that expensive. You get better bandwidth and more reliable power.

You could certainly try and host it from your house, but ADSL isn't going to cut it. You'll need at least a fairly decent SDSL connection to even hope of serving pages to the world.


Either way you're going to need a static public IP. You can ask your ISP for one. If you colo with them they'll certainly allow you to have a static IP

---

### Post by rakan_dr on 2008-08-19
What is a Datacenter?? Where can i find one??

---

### Post by mellowd on 2008-08-19
> **rakan_dr said:**
> What is a Datacenter?? Where can i find one??

[http://www.google.com/search?q=datacentre&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=datacentre&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by mbeach on 2008-08-19
you'd likely be looking to rent a server.

one of these places:
[http://www.google.com/search?q=server+rental](http://www.google.com/search?q=server+rental)

these places will rent you a server, or more likely a shared server which appears to be all yours - be sure to learn the difference.

if you are not hosting big clients, and there are very few page requests you might want to try it at home first, then move to a rental facility if you find response times are too slow.  Keep in mind that customers are very demanding people, and are not too understanding if you happen to have a power outage, or your internet goes out, your hard drive fails, you lost their files and didn't have a backup etc - that's why people are recommending you move your sites to a datacenter which can relieve some of the stresses involved.

Home based is good if you are demoing a site for a particular client, but it all depends on how many hits you are anticipating.  If you are only really serving up business card (1 or 2 pages per client) type sites, you may be ok - try it, but be prepared to migrate to a datacenter.

An IP address is assigned by your internet service provider (ISP).  Typically home service gets a dynamic ip, unless you pay extra for a static ip.  Dynamic ip means that your ip will change occasionally, so what you have today is not necessarily what you have tomorrow.  There are services like [www.dyndns.com](www.dyndns.com) or [www.no-ip.com](www.no-ip.com) which can be updated with your changing dynamic ip but arguably not the best solution for a proper business.

See [www.whatismyip.com](www.whatismyip.com) to see what you ip is now.

You can buy your domain name from godaddy, netfirms or any other registrar.  Most have decent control panels to direct requests for your domain name to whatever IP address you tell them to.  A domain name is simply a pointer to an IP address (I know, a bit understated).

Good luck, and be sure to read what you can first after searching Google/Yahoo/these forums, then ask for help when you run into stumbling blocks.

---

### Post by rakan_dr on 2008-08-19
thnx mbeach, I understanded the idea.
I might make the Hosting just for my website.
Is my internet speed enough for my website hosting?

---

### Post by mellowd on 2008-08-19
> **rakan_dr said:**
> thnx mbeach, I understanded the idea.
I might make the Hosting just for my website.
Is my internet speed enough for my website hosting?

As I said before, you have a 3mb adsl connection. That means you can download at 3 megabits per second, but your upload is far less. When people visit your page you're uploading to them.

Go to [www.speedtest.net](www.speedtest.net) and you'll see exactly how slow your upload speed is

---

### Post by rakan_dr on 2008-08-19
What if i get 3mb upload and download??? Is that enough???

I'll use a GSHDSL Line. This line gives same download and upload rate.

---

### Post by mellowd on 2008-08-19
> **rakan_dr said:**
> What if i get 3mb upload and download??? Is that enough???

I'll use a GSHDSL Line. This line gives same download and upload rate.


It all depends, the question you're kind of asking, is my car fast enough?

If you expect 1 - 5 visitors a day, all at different times then it'll be fine. If you expect hundreds, you've got no chance with a 3mb line

---

### Post by krayton8 on 2008-08-19
rakan_dr

El Conquistador is right, it'll be quicker to get started if you specify LAMP server (Linux, Apache, MySQL, PHP) during installation time.

You will need an ISP that offers static IP addresses and port 80 is requested to be open for web traffic. If you go through a registrar like yahoo or godaddy for your domain name, make sure to configure it to point to your IP address.

Tell us how it goes.

Good luck!

---

### Post by rakan_dr on 2008-08-19
Oh god! I'm expecting thousands of users!!! What internet speed should i use??

---

### Post by vpsville on 2008-08-19
Your upload connection speed is what counts when hosting a website.  Most ISP's restrict this speed to only a fraction of your download speed to prevent you from hosting sites at home.  You'll also need a static IP address.

For hosting websites, consider a shared hosting account or a VPS (private server on another network you can rent).

---

### Post by windependence on 2008-08-19
> **mellowd said:**
> If you plan to host clients sites as well I would recommend you host the server itself in a datacentre (colo if you will)

It's not that expensive. You get better bandwidth and more reliable power.

You could certainly try and host it from your house, but ADSL isn't going to cut it. You'll need at least a fairly decent SDSL connection to even hope of serving pages to the world.


Either way you're going to need a static public IP. You can ask your ISP for one. If you colo with them they'll certainly allow you to have a static IP

ON the contrary, I host several sites with my adsl connection, one getting over 13,000 page views a day. My upload speed is 1.5mbs and I am not even using close to that. You should have a static Ip though for a professional site. I am lucky in that my ISP only charges $5 for one IP and $14.95 for a block of 8. You can try [www.speakeasy.net](www.speakeasy.net) if you are in the US. If you can't get them, or you don't want to change ISPs, you can ask them about a business account. As a developer, you will probably want to have physical access to your server.

-Tim

---

### Post by rakan_dr on 2008-08-20
> **windependence said:**
> ON the contrary, I host several sites with my adsl connection, one getting over 13,000 page views a day. My upload speed is 1.5mbs and I am not even using close to that. You should have a static Ip though for a professional site. I am lucky in that my ISP only charges $5 for one IP and $14.95 for a block of 8. You can try [www.speakeasy.net](www.speakeasy.net) if you are in the US. If you can't get them, or you don't want to change ISPs, you can ask them about a business account. As a developer, you will probably want to have physical access to your server.

-Tim

oh that's a good news!
thnx, yeah that's why i don't want to rent servers cuz If i do, i can't access it physically and install what ever i want.
For example: if i have my own server, i can install the most recent PHP and Mysql also Java, Ruby.........and others, which if i want them in the rented server, it would cost me thousands!
But with my OWN server it's like free with Ubuntu!

---

### Post by mellowd on 2008-08-20
> **rakan_dr said:**
> oh that's a good news!
thnx, yeah that's why i don't want to rent servers cuz If i do, i can't access it physically and install what ever i want.
For example: if i have my own server, i can install the most recent PHP and Mysql also Java, Ruby.........and others, which if i want them in the rented server, it would cost me thousands!
But with my OWN server it's like free with Ubuntu!


Actually you can rent the hardware, you can then install whatever you like :)

---

### Post by Ximbiot on 2008-08-20
> **rakan_dr said:**
> that's why i don't want to rent servers cuz If i do, i can't access it physically and install what ever i want.
For example: if i have my own server, i can install the most recent PHP and Mysql also Java, Ruby.........and others, which if i want them in the rented server, it would cost me thousands!
But with my OWN server it's like free with Ubuntu!

You might also try a [Linode]("http://linode.com").  They rent virtual Linux machines with a nice management interface and have a very knowledgeable staff, at pretty affordable prices.  I've been a customer for a few years and they keep handing out more disk space and more memory without raising prices.  How many other companies would do anything like that?

---

### Post by rakan_dr on 2008-08-20
> **Ximbiot said:**
> You might also try a [Linode]("http://linode.com").  They rent virtual Linux machines with a nice management interface and have a very knowledgeable staff, at pretty affordable prices.  I've been a customer for a few years and they keep handing out more disk space and more memory without raising prices.  How many other companies would do anything like that?

I can't install and do what ever i want if i rent VM servers!

---

### Post by Ximbiot on 2008-08-20
> **rakan_dr said:**
> I can't install and do what ever i want if i rent VM servers!

With Linode, you can, unless you mean you want to diddle the hardware, compile a custom kernel, or don't think you can deal with the memory limitations at your price level.  They support a few dozen distro/versions, including Dapper and Hardy, and give you control right down to console access via lish.

Even when it comes to hardware, you can chop up your total disk allocation into as many partitions as you like via their web-based VM manager and they now support IP fail-over between two machines.

Anyhow, as I said, I've been very happy with them and grew out of my custom kernel inclinations some time ago.  I keep my own machines around for disk-intensive but fault-robust applications like file and mail servers, but I keep my web servers on Linodes for high-bandwidth and high-availability.

If you want a large disk, want to customize your kernel, or want to diddle your hardware in some other manner, you might very well be better off buying or renting your hardware, but it's going to cost you more.  If you can keep to a trim resource usage on your production web server, it's hard to beat the availability, bandwidth, and convenience of a Linode at such a low cost-point, in my experience.

---

### Post by Ximbiot on 2008-08-20
Of course, to be fair, I ran a fairly high-traffic (but low-bandwidth - few images, binary downloads, etc.) site out of my home office over a cable modem and on my own hardware for a long time.  The modem had less than 756k up, IIRC, and it wasn't a big deal.  The only two things that finally got to me were that the cable connection died for hours at a time with relative frequency and I thought that was a bad face to present to potential customers, and I moved physically.  Moving to a Linode meant that I didn't have to take the site down for days while I packed up, moved to another state, and unpacked.

Of course, running my own site for years in a house with cats and dogs (who's hair got caught up in cooling fans) meant that I went through a server every year or two, as well, which is another cost that needs to be factored in.  :)

---

### Post by mellowd on 2008-08-20
> **rakan_dr said:**
> I can't install and do what ever i want if i rent VM servers!


Of course you can

---

### Post by bvidinli on 2008-08-21
you can do hosting easily on ubuntu with ehcp, Easy Hosting Control Panel
see [www.ehcp.net](www.ehcp.net), and 
[http://ubuntuforums.org/forumdisplay.php?f=180](http://ubuntuforums.org/forumdisplay.php?f=180)

---

### Post by windependence on 2008-08-21
> **rakan_dr said:**
> oh that's a good news!
thnx, yeah that's why i don't want to rent servers cuz If i do, i can't access it physically and install what ever i want.
For example: if i have my own server, i can install the most recent PHP and Mysql also Java, Ruby.........and others, which if i want them in the rented server, it would cost me thousands!
But with my OWN server it's like free with Ubuntu!

I really think this is totally doable for you. My server gets over 5 million hits per month. Bandwidth is not going to be an issue. the biggest issue you will face is getting a static IP. If you are fortunate like me, it will be as easy as a phone call. If not, you may have to sign up for business services with your ISP which IMHO will still be cheaper and less trouble than renting server space or a dedicated server in a co-lo. I perfectly understand where you are coming from since I do pretty much what you are wanting to do, and there is nothing like having physical access to your dev server.

If you need help, I will be glad to assist you.

-Tim

---

### Post by bvidinli on 2008-08-21
i should append that:
ehcp uses most recent server software while installing, using ubuntu's apt-get system, 

this way, you always get most uptodate software, and it may be upgraded easily with apt-get update...

ehcp is full php/oop/opensource/gpl/free/easily modifiable...

---

### Post by windependence on 2008-08-21
> **bvidinli said:**
> i should append that:
ehcp uses most recent server software while installing, using ubuntu's apt-get system, 

this way, you always get most uptodate software, and it may be upgraded easily with apt-get update...

ehcp is full php/oop/opensource/gpl/free/easily modifiable...

Latest and greatest is not always the best or what is needed. Especially if he is a developer, there will be times when he needs to have older versions installed for testing, etc.

-Tim

---

### Post by bvidinli on 2008-08-21
yeah, absolutely right..
latest may not be best....

nevertheless, ehcp installs latest... ;)

---

### Post by rakan_dr on 2008-08-21
> **windependence said:**
> I really think this is totally doable for you. My server gets over 5 million hits per month. Bandwidth is not going to be an issue. the biggest issue you will face is getting a static IP. If you are fortunate like me, it will be as easy as a phone call. If not, you may have to sign up for business services with your ISP which IMHO will still be cheaper and less trouble than renting server space or a dedicated server in a co-lo. I perfectly understand where you are coming from since I do pretty much what you are wanting to do, and there is nothing like having physical access to your dev server.

If you need help, I will be glad to assist you.

-Tim

Thanks man for everything, 
you understand what i'm thinking about. There is nothing better than having a physical access to your hosting server. 
I think it's cheaper, easier and "SAFER".
1- It's cheaper cuz you can install a 500GB hard drive for about 100$ and forget about it forever! You don't have to pay 100$ every month! It's the same with RAM, the 2GB 800MHz Kingston RAM cost about 40$! And you pay that only once. What you should pay is the internet connection only.
2- It's easier cuz if you r a developer it's easier to just start installing and upgrading software without waiting others to start doing that. You are freeeee.
3- It's safer cuz you can be sure that no one inside the hosting company or "OTHER governments guys" can access the database or the info inside the server, or even steal the code pages ;)
I can't trust any hosting company. I can't believe that google guys would put the google algorithm "i.e code"  inside a hosting company server "I'm talking when they started google".

I just want to say something to Ximbiot, why do someone want to put a server near CATS and DOGS!!!!!!! Common man, it's a server!!! You should put it in a clean safe cold and locked room. It's a server man! It contains important info for u and for ur customers. I can't believe that a Hosting company can be more worried about my customers' info than me.

---

### Post by Ximbiot on 2008-08-21
> **rakan_dr said:**
> 2- It's easier cuz if you r a developer it's easier to just start installing and upgrading software without waiting others to start doing that. You are freeeee.


Well, the Linode guys are pretty good about upgrades and the only upgrades they are needed for is the kernels anyhow.  I can't argue with you about price, however, if you need that much disk and memory.

> **rakan_dr said:**
> I can't trust any hosting company. I can't believe that google guys would put the google algorithm "i.e code"  inside a hosting company server "I'm talking when they started google".

Well, I'm not hosting anything proprietary or that I'm particularly worried about anyone stealing, and I keep remote backups of everything important.

That said, Google may have their own uplinks now, but I know plenty of smaller companies that keep servers in colo's.  The maintenance guys there still have keys, but past a certain traffic level it's hard to avoid unless you have a big budget.  I wouldn't be surprised to find that Google *was* using colo's at the start, before the started bringing in tons of cash.

> **rakan_dr said:**
> I just want to say something to Ximbiot, why do someone want to put a server near CATS and DOGS!!!!!!! Common man, it's a server!!! You should put it in a clean safe cold and locked room. It's a server man! It contains important info for u and for ur customers.

At the time, I didn't know of any affordable alternative.  I kept backups so I wouldn't lose data, but my basement flooded and my home office was the only feasible alternative.  The servers were kept off the ground, but they shared air with the rest of the house and fur goes airborne.

:guitar:

---

### Post by windependence on 2008-08-21
> **rakan_dr said:**
> Thanks man for everything, 
you understand what i'm thinking about. There is nothing better than having a physical access to your hosting server. 
I think it's cheaper, easier and "SAFER".
1- It's cheaper cuz you can install a 500GB hard drive for about 100$ and forget about it forever! You don't have to pay 100$ every month! It's the same with RAM, the 2GB 800MHz Kingston RAM cost about 40$! And you pay that only once. What you should pay is the internet connection only.
2- It's easier cuz if you r a developer it's easier to just start installing and upgrading software without waiting others to start doing that. You are freeeee.
3- It's safer cuz you can be sure that no one inside the hosting company or "OTHER governments guys" can access the database or the info inside the server, or even steal the code pages ;)
I can't trust any hosting company. I can't believe that google guys would put the google algorithm "i.e code"  inside a hosting company server "I'm talking when they started google".

I just want to say something to Ximbiot, why do someone want to put a server near CATS and DOGS!!!!!!! Common man, it's a server!!! You should put it in a clean safe cold and locked room. It's a server man! It contains important info for u and for ur customers. I can't believe that a Hosting company can be more worried about my customers' info than me.

Well I know because I am doing exactly what you want to do. :)

I'll give you some other ideas. I have two main boxes, they are both very powerful, server class hardware I built myself. They have 1.5 TB each of storage (like you said, it's cheap) and 12 Gigs of RAM. Then, I run VMware server on one box and ESXi on the other. I can set up VMs with different OSs for testing or whatever. My main hosting VM runs FreeBSD, which incidentally runs a huge portion of the web at present. With two boxes, one is my main box and one is the backup box. I can move VMs from one to the other simply by SCP or Rsync, ect. since a VM is just a directory. I can also clone them, so I can set up a staging server and a production server. All the development work is done on staging and tested to make sure it works before transferring it to the prod machine. The VMs make it soooo much easier to move machines, do testing, and backup entire servers. I also have two UPSs, one rack mount and the other is a 2200 VA floor model. Each machine has redundant power supplies and is plugged in to both UPSs in case one goes down. I should say I didn't buy all this stuff all at once but I will say I paid about one tenth of what this would cost if someone else did it all for me. I love being able to do exactly what I want WHEN I want, even if it's 2 am. ;)

-Tim

---

### Post by rakan_dr on 2008-08-21
> **windependence said:**
> Well I know because I am doing exactly what you want to do. :)

I'll give you some other ideas. I have two main boxes, they are both very powerful, server class hardware I built myself. They have 1.5 TB each of storage (like you said, it's cheap) and 12 Gigs of RAM. Then, I run VMware server on one box and ESXi on the other. I can set up VMs with different OSs for testing or whatever. My main hosting VM runs FreeBSD, which incidentally runs a huge portion of the web at present. With two boxes, one is my main box and one is the backup box. I can move VMs from one to the other simply by SCP or Rsync, ect. since a VM is just a directory. I can also clone them, so I can set up a staging server and a production server. All the development work is done on staging and tested to make sure it works before transferring it to the prod machine. The VMs make it soooo much easier to move machines, do testing, and backup entire servers. I also have two UPSs, one rack mount and the other is a 2200 VA floor model. Each machine has redundant power supplies and is plugged in to both UPSs in case one goes down. I should say I didn't buy all this stuff all at once but I will say I paid about one tenth of what this would cost if someone else did it all for me. I love being able to do exactly what I want WHEN I want, even if it's 2 am. ;)

-Tim

Yeah that's what i'm talking about it...[COLOR="Red"][SIZE="4"]FREEDOM[/SIZE][/COLOR]!

Thanks man, the ideas are great "even though i didn't understand all of them :)!"

Can u tell me what is ur ADSL speed "both download and upload"???

There is something that i don't understand, what is Bandwidth?
I know that bandwidth is the amount of data that you can download, which is limited by the ISP, right? 
For example: you can have a subscription with an internet connection plan for 2Mb download speed, but you can only download let's say 5GB a month, is that right???
Oky if that's is a bandwidth, why do i have to concern about bandwidth with my hosting server if i have unlimited download subscription???? I asked that question cuz one guy said that you have to be careful about the bandwidth. Please if my understanding about bandwidth is wrong, correct it for me.

Thanks.

---

### Post by windependence on 2008-08-21
My connection is just 1.5mps up and down.

Bandwidth when I refer to it is the size of your connecting (your pipe). When co-los refer to it, it can be what you were talking about, the amount of data transmitted and received. Some hosting providers charge that way. You don't need to worry about that if you host your own site.

If you need more help, I am here most of the time, just ask. ;)

-Tim

---

### Post by brian77095 on 2008-08-21
Hi, everyone.

I am new to this forum and, I want to set up my own server as well.  Here are a few links that I found very helpful.

[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)
this site asks you questions and helps you pick the right linux distro. for you.

[http://www.aboutdebian.com/network.htm](http://www.aboutdebian.com/network.htm)
get ready to read...this site has many many good pages of reading for setting up a hosting server and also talks a good deal about subnetting and DNS.  

You do not have to have a static IP address to do web hosting.  You can use sites like this

[http://www.easydns.com/](http://www.easydns.com/)

as an alternate.  That way if your IP changes or you loose power or need to perform maint it is ok because if some one tries to go to your web site and cant find it it goes to the alt. Witch would be at easydns.com  I probably did not explain this exactly right but, hope you get my point.

I would not recommend this for a big heavily used web site but, to just learn and maybe host a few small web sites it works great.

Hope this helps!!

Brian

---

### Post by windependence on 2008-08-22
Your last line is the most important part of your post. For SERIOUS hosting as the OP wants to do, there is no question he needs to have a static IP. You know it's not as expensive as most people think. Sometimes it just means you have to request a business DSL or cable account and the price isn't much different. Some of us like myself are lucky enough to ba able to get one that is very inexpensive. Mine is $5 per month. If you are gonna be a professional in the web business, you should try to do it right. You will also find that some people cannot access your site if you are hosting from a dynamic IP because their companies block those IP ranges. You may never know. I was fortunate enough to have people on my site contact me to let me know. Let's face it, probably 80% of people surf at work. Do you want to eliminate that traffic?

-Tim

---

### Post by rakan_dr on 2008-08-22
what are colos???

---

### Post by windependence on 2008-08-22
It's a co-location facility. A place where they house your server and they provide bandwidth, power, AC, etc. You can either rent a server from them or use your own equipment. Like having your server at your house only it's in a different building with all the protection of a data center. They usually charge by the rackspace unit, 1u, 2u, etc.

-Tim

---

### Post by rakan_dr on 2008-08-22
what is the Data center? And what did u mean by 1u, 2u?? Users...??

---

### Post by windependence on 2008-08-22
The 'u' which is not the actual character (I can't make it from this keyboard, no number pad) means "micro" and refers to the height of the server cabinet. 1u is about one inch, so a 6u case is about 6 inches high.

Well a typical data center is just a place that has redundant power and A/C available, usually in a controlled environment where dust and dirt are mostly eliminated. Most co-lo data centers have their own racks and you mount your server there.

-Tim

---

### Post by Ximbiot on 2008-08-22
> **windependence said:**
> Most co-lo data centers have their own racks and you mount your server there.

...and will usually have locking racks, so depending on how many "u"s you rent (I think a full rack is usually 32), you, the colo maintenance staff, and anyone else renting "u"s in your rack may have a key to the rack.

It you search Dell or some other site for rack-mount servers, you will see that the servers and many  rack-mount peripherals (power supplies, disk arrays, network switches, routers, etc.) will have their heights listed in "u"s.

---

### Post by brian77095 on 2008-08-22
I have never herd of people haveing connection problems while useing a dynamic ip.  Thanks for the info.  Any ideas why they cant veiw the web page?

I just called my ISP (att uverse)  they do not allow static IP addresses :( Oh well...

---

### Post by brian77095 on 2008-08-22
also here is a question for you....

I have two older computers one of them I want to use as a server to run Ubuntu server on.

One is a 1700 amd processor with 1g meg ram
I for got the processor name but it runs hot and its loud.

the other is 1200 Intel processor with 512 meg ram run cool and quiet.  

I think I would like to use the cool and quiet but would I notice a big diffence with the losse of processing power and ram?

thanks and sorry for getting a little off the original post.

brian

---

### Post by windependence on 2008-08-22
> **brian77095 said:**
> also here is a question for you....

I have two older computers one of them I want to use as a server to run Ubuntu server on.

One is a 1700 amd processor with 1g meg ram
I for got the processor name but it runs hot and its loud.

the other is 1200 Intel processor with 512 meg ram run cool and quiet.  

I think I would like to use the cool and quiet but would I notice a big diffence with the losse of processing power and ram?

thanks and sorry for getting a little off the original post.

brian

OK Brian, to answer your first question, here is what happened to me.

I started a small forum about 4 years ago in 2004. I originally hosted it from home on my ISP account using the IP they assigned me which wasn't technically static but never changed in years. After we reached 250,000 hits per month rather quickly, they cut off port 80 for me so I switched to port 8080 and used a no-ip dynamic host. That is when the trouble started. People called me and e-mailed me saying they could no longer reach the site. I finally figured out that most people COULD reach it but many people could not and it was due to the fact that their companies where they worked blocked all IPs from dynamic hosting providers. they do this because many spam sites use these to send mass mailings, and it is difficult to trace who they really are. That is when I got the static IP and everything has been fine since then. 

If this had been a sales site or some other content site where I didn't get feedback, I may have never known I was leaving these people out. Trust me, it happens. I have had arguments with people here on the forums saying dynamic DNS is no different than a static IP. They are dead wrong. If you want to host a site to make money or want a professional site that everyone can access, get a business account from your ISP and get a static IP or a block of them. With my new ISP, I can get 8 for $14.99.

Now to your second question, when I started hosting the forums, I was using a tiny AMD K6/2 500 processor with 512K RAM. I was using OpenBSD which is a bit more efficient than Linux but the point is you'll be fine with either of those boxen. Good luck!

-Tim

---

### Post by brian77095 on 2008-08-22
Thanks for that info!!  One day I hope to manage a few web site as successful as yours!


But right now I just need to get one up and running.....

---

### Post by windependence on 2008-08-23
We are here to help you get started. If you have questions, just ask. :)

-Tim

---

### Post by mikemir121 on 2008-08-23
Great setup, Tim. Looks like you really have gotten yourself busy. I envy you. I just had a couple of questions. Can someone who is just starting to create a development environment use one (physical) server instead of having two (possibly with the use of VMs)? I definitely believe in having the development and testing servers, but want to begin sooner rather than later. Also, as I am new to Linux, how do I setup my web server? I know I have to install Ubuntu Hardy Heron LAMP server on a machine that can connect to the internet, but don’t know what GUI to install. I also don’t see a guide as to how to begin setting up a web development environment.

---

### Post by mellowd on 2008-08-23
> **mikemir121 said:**
> Great setup, Tim. Looks like you really have gotten yourself busy. I envy you. I just had a couple of questions. Can someone who is just starting to create a development environment use one (physical) server instead of having two (possibly with the use of VMs)? I definitely believe in having the development and testing servers, but want to begin sooner rather than later. Also, as I am new to Linux, how do I setup my web server? I know I have to install Ubuntu Hardy Heron LAMP server on a machine that can connect to the internet, but don’t know what GUI to install. I also don’t see a guide as to how to begin setting up a web development environment.

for your webserver alone I wouldn't install a gui at all. I'd also use a VM as you mentioned instead of using 2 seperate servers, unless of course you can afford more for now

---

