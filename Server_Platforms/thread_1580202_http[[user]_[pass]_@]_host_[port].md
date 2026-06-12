---
title: "http://[[user] [pass] @] host [:port]"
date: 2010-09-23
forum: Server Platforms
---

### Post by tlf30 on 2010-09-23
I'm just loading my ubuntu server and my URL is _www.liquidcrystalstudios.co.cc_ but how do i put that in to _"http://[[user] [pass] @] host [port]"_ format. 
 
[CENTER]Please help.[/CENTER]

---

### Post by madverb on 2010-09-23
Please explain more thoroughly what you are trying to do. Is this an FTP server?

---

### Post by SaintDanBert on 2010-09-23
Your URL is the "host" part.

~~~ 0;-Dan

---

### Post by tlf30 on 2010-09-23
Im trying to run an FTP server to host a web sight, this is the first server I'v ever loaded im trying to go cheap with ubuntu.

---

### Post by tlf30 on 2010-09-23
Also the server is a 10 year old desktop, so i don't have a lot of options.

---

### Post by BkkBonanza on 2010-09-24
You just use it like this,

[http://www.liquidcrystalstudios.co.cc](http://www.liquidcrystalstudios.co.cc)

unless you need to provide username/pwd info then you add them like,

[http://joe:secret@www.liquidcrystalstudios.co.cc](http://joe:secret@www.liquidcrystalstudios.co.cc)

For ftp it's usually,

[ftp://joe:secret@www.liquidcrystalstudios.co.cc](ftp://joe:secret@www.liquidcrystalstudios.co.cc)

Only add the port on the end of url if it's using a non-standard port (not 80).

---

### Post by tlf30 on 2010-09-24
Thank you.

---

### Post by tlf30 on 2010-09-24
If any of you could give me one more piece of info, the instlation wants me to slect software it gives me the options:
 
DNS Server
LAMP Server
Mail Server
openSSH server
postgreSQL database
Print Server
samba file Server
Tomcat Java Server
virtual machine host.
 
What I'm doing with it is running a web site hosting a java game.
I also can choose none or Manual package selection.

---

### Post by lisati on 2010-09-24
<side note>I'm a bit wary of the .co.cc people's setup. I signed up with them with a view to checking them out. [no-ip]("http://www.no-ip.com/") and [dyndns]("http://www.dyndns.com/") seem easier to use, and what I'm guessing is a registration confirmation email from them was rejected with the following error by my server:
> 550 5.7.1 Client host rejected: cannot find your hostname

---

### Post by tlf30 on 2010-09-24
My URL worked, thankfuly.
But i building a game in java so im not sure if any of the software listed above is nessesary to run the game.

---

### Post by BkkBonanza on 2010-09-24
Just LAMP (**L**inux/**A**pache/**M**ysql/**P**HP) server, your typical base web server. And maybe Tomcat for Java but I'm not familiar with running Java games and if they need that.

---

### Post by tlf30 on 2010-09-24
Thanks,
another thing I could use some help with is how do i find the name server.

---

### Post by tlf30 on 2010-09-24
More info on the name server: 
To register the url it asks me for the name server.

---

### Post by tlf30 on 2010-09-24
Another thing i ccould use help on is getting my web site on the server if anyone knows how to do that.

---

### Post by BkkBonanza on 2010-09-25
When you register your domain name they will usually provide name servers for you. At least at first as you may move to your own or other name servers. But initially the registrar, eg. Godaddy.com, name.com, etc will be the nameserver recorded. So you would start by going to your registrar and looking at your account details there.

Normally you don't need to know your domain nameservers for getting the web server setup. You shouldn't bother with setting up your own DNS servers (Bind etc), at first. It's not needed and less effective than using the free ones provided by your registrar.

Usually to set up your web server you would go to your name sevrer (your registrar) and in your ccount you can edit the DNS values to correspond with your web server. The A record should point to your server IP and likely you should have a CNAME record for www subdomain pointed at the A record.

How you upload your site files depends completely on how you set up your server. Where it's located, and how you usually get access. If you use SSH for access then rsync is a good way to get files put there.

---

### Post by tlf30 on 2010-09-25
The reason I'm using my own server is I'm gone a lot and want to be able to keep track of the game, the problem of being gone is when I'm gone I have no internet and thats at my other job which is commercial fishing, and the season is 3 months.
 
My ant told me that my name server could be my url, and the host liked it.
But I haven't been able to accses my server through my network places->new network connection->[http://www.liquidcrystalstudios.co.cc](http://www.liquidcrystalstudios.co.cc) .

---

### Post by BkkBonanza on 2010-09-25
It sounds like you're quite confused about how these things work. You do not want to run your own name servers, especially if you are away for long times.

Anyway, I'm confused by what you are trying to do. I'd like to help but your intent and details are coming across scrambled to me.

You want to have a functioning web server, right?

You registered a name at .co.cc. You need to login to the .co.cc control panel and set it to point to your web server IP address (wherever that may be). If your web server IP is "dynamic" you have a few more steps too.

I tried your name given above and right now it's not resolving at all. It seems something is wrong with .co.cc names as other names I tested resolved fine.

(btw I checked the co.cc web site and it drove Firefox crazy with something. I personally don't trust it. Why not use another free domain like no-ip.com or dyndns.com? co.cc is owned by some Kim Jong Sung (apparently) in China and sure sounds like North Korean. It could be just fine but it doesn't seem so fine to me. He even appears to hide this by not putting a country in his registration. Just weird. If you already setup your IP with them, and entered personal info, then I'd be a bit suspicious of it not working. Your name should at least resolve if the co.cc name servers are functioning. It should respond with an IP but it just hangs. Oh, tell me they didn't ask for credit card details...)

---

### Post by tlf30 on 2010-09-25
Ok so what your teling me is to dump .co.cc and get a real URL second dont host my own wesite.

---

### Post by BkkBonanza on 2010-09-25
Umm. I don't think I said anything like that.
Sure, host your web site. Go for it. I'd like to help you. But you haven't told me even what you have done so far. I don't know what stage you're at.

I'm just suspicious about co.cc - that's all.

If you registered that name at co.cc then it should resolve now. Normally it would go to a parking page until you go in and set up your own IP address. But whatever, you haven't said what you've done so far, not given any info that would allow anyone to help you out.

Hosting your web site is different from hosting name servers. Name servers are what the co.cc guys are doing for you. Or I assume they are since I haven't signed up with them and don't know what they give you for free anyway. I've told you a few time snow you need to login into their control panel and set your IP. But you refuse to say if you did that, tried to do it, or just plan to have the net work for using magic fairy dust.

---

### Post by lisati on 2010-09-25
Like I indicated in an earlier post, I'm suspicious of .co.cc too. I prefer dyndns and no-ip.

---

### Post by SaintDanBert on 2010-09-25
> **BkkBonanza said:**
> 
...
If you registered that name at co.cc then it should resolve now. Normally it would go to a parking page until you go in and set up your own IP address. But whatever, you haven't said what you've done so far, not given any info that would allow anyone to help you out.
...


Once you register your domain name and it has an assigned IP address,
name services will spread the word of that affiliation. In my experience, it can take from 2 to 7 days for "everyone" to get the word so that every resolver on every DNS will find you. Your mileage may vary, and "every" means 95% or better. There are always reasons why some DNS request in the wild might fail to find you. Such an outage should be short lived and rare ... but they do happen.

Cheers,
~~~ 0;-Dan

---

### Post by tlf30 on 2010-09-25
So if I'm going to get a .com who do I go through also who will host a server with my HTML code.

---

### Post by tlf30 on 2010-09-25
Here is what I'v done,
I'm building a game in java, i also built a website in  HTML.
I took a ten year old desktop into a server that I'm trying to get running
on the instlation I have put the proxy in standed form as shown
[http://[](http://[)[tlf30] [pass] @ [www.liquidcrystalstudios.co.cc](www.liquidcrystalstudios.co.cc) [:80] 
next I instaled DNS, LAMP, tomcat java.

---

### Post by BkkBonanza on 2010-09-26
You don't need to get a .com. Nobody is saying that here. But your .co.cc name should work and **it isn't** even when I enter it here on my browser. You seem to refuse to say whether you went to co.cc and updated your IP. Maybe it can work if you do something to make it work.

(Nowadays names work within minutes of being registered, particularly for these second level names, where it only depends on the company updating their own DNS servers.)

Go to dyndns.com and get a free name there, like liquidcrystalstudios.dyndns.org

Use that instead.

> 
[noparse]http://[tlf30] [pass] @ www.liquidcrystalstudios.co.cc[/noparse] [:80] 
That's not going to work for anything. Like I posted above you remove the [] brackets and do like this, **[noparse]http://tlf30:pass@www.liquidcrystalstudios.co.cc[/noparse]**  (and NO [:80] stuff after it, and no [] around terms).

I'm sorry to say that you need to do a lot more reading up and learning before you can expect to setup and run a web server. I don't think I can help you out here. There are lots of good starter tutorials around using google. They may help you.

---

### Post by tlf30 on 2010-09-26
Ok I will get the dyndns.org URL.
Whern i enterd the [http://[](http://[)[user] [pass] @] host [:port] i dod not use the brackets.
The thing i worried about with the port is the computer is 10 years old so it's not very smart... 
But I did leave it out.
 
I will have the server on the new url in a sec.

---

### Post by tlf30 on 2010-09-26
I have run into a problem my internet provider will not alow me to run a server, so because this is nessesary to run the game on how do I hook it up to run just within my network.
 
The reason the server has not woked my internet provider has cut it off form the internet and would like the charg a fee to run it out side my network to the internet.
 
So if any of you know of a hosting that will let me use my own html code,
and if some one could help me just set it up in a network.

---

### Post by SaintDanBert on 2010-09-27
How does you ISP determine that you are "running a server?"  I'm not suggesting that you violate their terms of service, but I'm curious?

Do they have a list of ports that are "server" ports -- and they block them?

Do they reach into your LAN and interrogate whatever they find there?
How do they get past YOUR gateway router?

I'm sure you know that a "server" is any computer with connections available to the network -- LAN or WAN does not matter. If any one of your computers will respond to **http://{LAN IP address}:{some port}** then it is a server. Of course, **http** is one of many available protocols. Your mileage may vary.

~~~ 0;-Dan

---

### Post by tlf30 on 2010-10-31
Sorry I have not been responding, I have been in Bismark ND with no computer, to answer you question, they know its a server by how its trying to access web, and how the IP is configured, I think, that is what my cousin told me who runs databases. 

I have found I can actually have some one host the server for me, cheaper than I can run it. I'm using a local serves.  

The other problem I ran into was the port I was using was not 80 I have no idea what it is, but because I have to use an extension networking card it has its own port #'s.

---

### Post by tlf30 on 2010-12-19
I think I'm using port # 0.

---

### Post by spynappels on 2010-12-19
Hi,

You need to do a little reading up on what ports are. I suggest you start with links like

[http://en.wikipedia.org/wiki/TCP_and_UDP_port](http://en.wikipedia.org/wiki/TCP_and_UDP_port)

You need to understand that these ports are not physical, they are virtual, and each and every network interface is capable of listening for network traffic on a range of ports from 1 to 90,000+ Having said that, most services have default ports that they use such as port 80 for normal web traffic. If these default ports are used on your server, you do not need to add them to your URL as the browser will use these as standard. 

I don't want to dent your enthusiasm, but you do need to have a basic understanding of the technologies you are using, as this will impact on the security of your server and the reliability of your site.

---

