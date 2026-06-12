---
title: "Okay, I am Gonna Setup My First Server!"
date: 2007-11-28
forum: The Cafe
---

### Post by user1397 on 2007-11-28
EDIT: I finally made this work.

Thanks again everyone for all your help, I really do appreciate it. :)

- - - - - Original Post - - - - -

OK so I want to make a personal website but I don't want to pay some hosting company, since I would like to take this opportunity to set up my own home web server.

I have more than a year's worth of ubuntu desktop experience, especially with troubleshooting and general knowledge about the system, but I know next to nothing about servers. I *am* aware of the ubuntu server edition, if you'd like to know.

I have an extra desktop lying around that is installed with ubuntu gutsy, not server version.  I would like to turn this into a web server to host my website.
Here are the specs:
amd athlon xp 2ghz
512mb ram
160gb hard drive
Lan connection (cable modem)
ubuntu 7.10

But...I have no idea where to begin or what proper steps to take.

I just want to use it as a web server to host a simple site, not as a file, print, email, or other type of server. No php or database applications (MySQL?) are needed. My understanding of a file server is just a sort of readily accessible storage space for my files (right?). Also, please don't suggest anything like wordpress or blogs, I want to design my own web site (I know that much).

I don't know much about apache though...

---

### Post by boast on 2007-11-28
I would of gone debian, but w/e

check out  howtoforge.com

---

### Post by p_quarles on 2007-11-28
The Ubuntu server edition CD gives you the option of installing an integrated LAMP setup. Same with Debian (and I second boast's recommendation of that). 

Those specs are more than enough (might even say overkill) for a small web site. 

Learning to use Apache is pretty easy, and PHP/Perl/Python + MySQL isn't that much more difficult. The difficult part is getting up to speed on the security implications of running a public web server. In my case, I treated my server as a development environment (invisible to the rest of the world) for about two months before putting it online. Give yourself a chance to learn the ropes before going public. The scriptkiddy attacks are a constant fact of life, and while most of them aren't dangerous, you do want to be able to tell the difference between those and the ones that *are* dangerous.

---

### Post by andhar on 2007-11-29
this is a good read..be sure to also read part 2.

[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)

---

### Post by Tenken on 2007-11-29
For just a small website I don't even think you would need the whole LAMP server, there is no reason to have a MySQL backend or PHP if you don't use them. They are just two more security issues that you have to worry about.

---

### Post by Lostincyberspace on 2007-11-29
If you are doing a home website I would set up a wordpress one it isn't very hard and can be done in minutes and you could use the extra space as a file server if you wanted.

---

### Post by getaboat on 2007-11-29
I've recently done this with come pointers from these forums.

webadmin and ssh for the admin.

It's a shared fileserver for the other computers in the house (more disk space required).

It's a printserver for 2 of the 4 house printers (soon to be all 4) - (Epson - grrrr)

Web calendar is up but not live while I try to get email via SMTP working.

Jinzroa up and running - for the house music library.

Next project is for zoneminder.

security wise there might be some eyebrow lifting - but hey it's inside my front door and inside my firewall. 

I've got some links that I found very useful to get up and running that I can post later.

---

### Post by regomodo on 2007-11-29
netBSD? 
Thought i'd just throw that in there

---

### Post by user1397 on 2007-11-29
I guess I haven't gotten the responses I was looking for (I don't mean to be an *** or anything, I am just saying...:))  Please read my edit in the first post.

---

### Post by user1397 on 2007-11-29
> **Tenken said:**
> For just a small website I don't even think you would need the whole LAMP server, there is no reason to have a MySQL backend or PHP if you don't use them. They are just two more security issues that you have to worry about.thank you, I hadn't realized that.

---

### Post by p_quarles on 2007-11-29
> **ubuntuman001 said:**
> I guess I haven't gotten the responses I was looking for.  Please read my edit in the first post.
You could have just replied with the clarification.

Anyway, all you need to do to setup Apache is

1) Install the Ubuntu Server Edition base system
2) Get Apache:
```
sudo apt-get install apache2
```
3) Make your web pages
4) Put them in the /var/www directory

That's really all there is to it. Once you've done that, you'll also want to assign the server a static IP address (there are numerous how-tos for that), and then make sure that you have your router set to forward web site requests to the server.

---

### Post by user1397 on 2007-11-29
> **p_quarles said:**
> You could have just replied with the clarification.

Anyway, all you need to do to setup Apache is

1) Install the Ubuntu Server Edition base system
2) Get Apache:
```
sudo apt-get install apache2
```3) Make your web pages
4) Put them in the /var/www directory

That's really all there is to it. Once you've done that, you'll also want to assign the server a static IP address (there are numerous how-tos for that), and then make sure that you have your router set to forward web site requests to the server.wow that's really all there is to it? awesome! I thought it would be a lot more complicated than that. thanks very much.

umm also, what about domains? can i just buy a domain somewhere and not have to be pulled into a whole plan? if you've bought one before, where did you go?

---

### Post by Crashmaxx on 2007-11-29
This is a pretty simple task. The most basic thing you want to do are:

1. Setup a static IP: This will make sure that the server is always the same place on your network and the router can get packets to it.

2. Install apache2: Just do:
```
sudo apt-get install apache2
```
And answer anything it may ask you the best you can. Defaults should be fine.

3. Forward port 80 to the server static IP on your router: This will allow the rest of the internet to access your webserver.

4. Setup a domain name with dyndns.org: This will let you pick a nice domain name and not have to worry about your connection's IP address changing. They have all the info you'll need to do this.

5. Put your website files in /var/www: Anything in this folder will be on your website. Add a index.html to have your page displayed instead of a list of files.

These two links should help, just ignore the stuff about installing Ubuntu or anything else you don't need. You may want webmin to manage your sever, but its not necessary.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html)

And that should get you started. Keep in mind that your server can only handle so much load, and your connection can max out too. But unless you site goes on digg or you host a lot of huge files, hopefully you'll have no problems.

---

### Post by user1397 on 2007-11-29
> **Crashmaxx said:**
> This is a pretty simple task. The most basic thing you want to do are:

1. Setup a static IP: This will make sure that the server is always the same place on your network and the router can get packets to it.

2. Install apache2: Just do:
```
sudo apt-get install apache2
```And answer anything it may ask you the best you can. Defaults should be fine.

3. Forward port 80 to the server static IP on your router: This will allow the rest of the internet to access your webserver.

4. Setup a domain name with dyndns.org: This will let you pick a nice domain name and not have to worry about your connection's IP address changing. They have all the info you'll need to do this.

5. Put your website files in /var/www: Anything in this folder will be on your website. Add a index.html to have your page displayed instead of a list of files.

These two links should help, just ignore the stuff about installing Ubuntu or anything else you don't need. You may want webmin to manage your sever, but its not necessary.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html)

And that should get you started. Keep in mind that your server can only handle so much load, and your connection can max out too. But unless you site goes on digg or you host a lot of huge files, hopefully you'll have no problems.thank you.

---

### Post by tech9 on 2007-11-29
> **ubuntuman001 said:**
> thank you.

Hi ubuntuman001

Let me know how you did, how easy/hard it was. I may want to host my own site too :)

T9

---

### Post by p_quarles on 2007-11-29
> **Crashmaxx said:**
> 4. Setup a domain name with dyndns.org: This will let you pick a nice domain name and not have to worry about your connection's IP address changing. They have all the info you'll need to do this.
Just a quick addition to this advice: I found setting up DynDNS kinda wonky when I first attempted it. Hopefully, their instructions have become a little more clear since I did it, but here's the basic process:
Get the client program:
```
sudo apt-get install ddclient
```
Then, cut and paste the Linux config file that DynDNS makes for you (this is what threw me -- you cannot just modify the default config file) to /etc/ddclient.conf. Then you have to edit it to include your DynDNS account username and password. 

Good luck.

---

### Post by user1397 on 2007-11-29
> **tech9 said:**
> Hi ubuntuman001

Let me know how you did, how easy/hard it was. I may want to host my own site too :)

T9okay, will do :)

---

### Post by user1397 on 2007-11-29
> **p_quarles said:**
> Just a quick addition to this advice: I found setting up DynDNS kinda wonky when I first attempted it. Hopefully, their instructions have become a little more clear since I did it, but here's the basic process:
Get the client program:
```
sudo apt-get install ddclient
```Then, cut and paste the Linux config file that DynDNS makes for you (this is what threw me -- you cannot just modify the default config file) to /etc/ddclient.conf. Then you have to edit it to include your DynDNS account username and password. 

Good luck.thanks again for the information, you've been a real big help.

I got a couple of new questions:
1) is it really necessary for the server to be command line only (considering the specs I gave) ? Will the server really work that much faster without any GUI?

2) is it possible to host more than one site? (like could I make two separate folders in /var/www and have index.html files in both of them?

---

### Post by p_quarles on 2007-11-29
> **ubuntuman001 said:**
> thanks again for the information, you've been a real big help.
Glad I could help.

> 1) is it really necessary for the server to be command line only (considering the specs I gave) ? Will the server really work that much faster without any GUI?
That system should be able to run a light GUI (like Xfce or Fluxbox) and still work well as a server for a moderate amount of traffic. 

What I *wouldn't *do, though, is keep the GUI running normally. You'll probably just be using it occasionally, and there's no reason to tie up resources (and electricity!) by keeping it running all the time. 

That said, running Apache from the command line is actually not complicated at all. What you would be doing, mostly, is using basic commands like "mv" or "cd" to manage files, and then occasionally the Nano text editor to edit config files. 

If you want a GUI for editing your html files, there's an easy way to do that, too:
```
sudo apt-get install openssh-server
```
That will allow you to remotely log-in to your server, but it also comes with a file upload server (sftp). Using this, you could design the site with Quanta/Amaya/Bluefish/Dreamweaver and then use an FTP program to upload the files to the server. 

Either way should work all right. Just be aware that running a GUI adds a security risk, so don't leave it running all the time. 

> 2) is it possible to host more than one site? (like could I make two separate folders in /var/www and have index.html files in both of them?
Yeah, that's referred to as "virtual hosts." A couple of guides:
[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)
[http://httpd.apache.org/docs/1.3/vhosts/](http://httpd.apache.org/docs/1.3/vhosts/)

---

### Post by user1397 on 2007-11-29
> **p_quarles said:**
> Glad I could help.


That system should be able to run a light GUI (like Xfce or Fluxbox) and still work well as a server for a moderate amount of traffic. 

What I *wouldn't *do, though, is keep the GUI running normally. You'll probably just be using it occasionally, and there's no reason to tie up resources (and electricity!) by keeping it running all the time. 

That said, running Apache from the command line is actually not complicated at all. What you would be doing, mostly, is using basic commands like "mv" or "cd" to manage files, and then occasionally the Nano text editor to edit config files. 

If you want a GUI for editing your html files, there's an easy way to do that, too:
```
sudo apt-get install openssh-server
```That will allow you to remotely log-in to your server, but it also comes with a file upload server (sftp). Using this, you could design the site with Quanta/Amaya/Bluefish/Dreamweaver and then use an FTP program to upload the files to the server. 

Either way should work all right. Just be aware that running a GUI adds a security risk, so don't leave it running all the time. 


Yeah, that's referred to as "virtual hosts." A couple of guides:
[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)
[http://httpd.apache.org/docs/1.3/vhosts/](http://httpd.apache.org/docs/1.3/vhosts/)thank you! for answering all of my questions again, I can't stress enough how much you have helped me in this endeavor :)

---

### Post by tr333 on 2007-12-01
A quick note on the DynDns.org address:  for the free services, you have to "update" your information on dyndns.org once a month to prevent it getting deleted, which is a small price to pay for getting a high-quality free service (never had downtime on it yet).  This is just basically logging in to the dyndns.org website with your account details and clicking "modify" on the dynamic host page to register that you're still using the subdomain address.  They don't want people signing up for multiple subdomains that just get left unused.

---

### Post by tr333 on 2007-12-01
Here are a few other programs that are really useful for running a server.

**fail2ban** - essential if you're running a server that will be connected to the internet (via apache or other software).  It will block any computers that fail to login properly after a specified number of attempts, for a set period of time.  This is usually long enough to stop the bots that randomly target machines for security weaknesses.  configs are located at /etc/fail2ban/

**ntpd** - Network Time Protocol daemon.  This will keep the time on your server synchronised to internet time servers.  config file is located at /etc/ntp.conf.  I use the [NTP Pool](http://www.pool.ntp.org/) for the timeservers.  If you set ntpd to broadcast the time on the local subnet, then you can point your other computers on the local LAN to get their time from this server instead of some random server that might be anywhere (much faster, and more accurate).

**cups** - [https://help.ubuntu.com/7.10/server/C/cups.html](https://help.ubuntu.com/7.10/server/C/cups.html).  Print server.  Once the config files in /etc/cups/ have been set properly, you can access the web-gui via "http://server-address:631" (cups runs on port 631).

More information on installing Ubuntu Server and related programs is available on the [Ubuntu Server Guide](https://help.ubuntu.com/7.10/server/C/), part of the online Ubuntu documentation, and also [Servers](https://help.ubuntu.com/community/Servers), part of the online Ubuntu Community documentation.

---

### Post by user1397 on 2007-12-02
> **tr333 said:**
> A quick note on the DynDns.org address:  for the free services, you have to "update" your information on dyndns.org once a month to prevent it getting deleted, which is a small price to pay for getting a high-quality free service (never had downtime on it yet).  This is just basically logging in to the dyndns.org website with your account details and clicking "modify" on the dynamic host page to register that you're still using the subdomain address.  They don't want people signing up for multiple subdomains that just get left unused.

> **tr333 said:**
> Here are a few other programs that are really useful for running a server.

**fail2ban** - essential if you're running a server that will be connected to the internet (via apache or other software).  It will block any computers that fail to login properly after a specified number of attempts, for a set period of time.  This is usually long enough to stop the bots that randomly target machines for security weaknesses.  configs are located at /etc/fail2ban/

**ntpd** - Network Time Protocol daemon.  This will keep the time on your server synchronised to internet time servers.  config file is located at /etc/ntp.conf.  I use the [NTP Pool]("http://www.pool.ntp.org/") for the timeservers.  If you set ntpd to broadcast the time on the local subnet, then you can point your other computers on the local LAN to get their time from this server instead of some random server that might be anywhere (much faster, and more accurate).

**cups** - [https://help.ubuntu.com/7.10/server/C/cups.html](https://help.ubuntu.com/7.10/server/C/cups.html).  Print server.  Once the config files in /etc/cups/ have been set properly, you can access the web-gui via "http://server-address:631" (cups runs on port 631).

More information on installing Ubuntu Server and related programs is available on the [Ubuntu Server Guide]("https://help.ubuntu.com/7.10/server/C/"), part of the online Ubuntu documentation, and also [Servers]("https://help.ubuntu.com/community/Servers"), part of the online Ubuntu Community documentation.thank you very much for this information!

---

### Post by rouge568 on 2007-12-02
I came across an article on Digg just the other day on this: [http://www.techenclave.com/forums/how-build-low-cost-linux-home-102018.html](http://www.techenclave.com/forums/how-build-low-cost-linux-home-102018.html)
Personally, this is one project that I really want to do, just as soon as I get home from school. Let us know how it goes!

---

### Post by user1397 on 2007-12-02
question:
1) is a DNS server the same as a web server?

2) are domains only payable by subscriptions and such, i.e. can you not "own" your domain fully with a one time payment or something?

---

### Post by user1397 on 2007-12-02
> **rouge568 said:**
> I came across an article on Digg just the other day on this: [http://www.techenclave.com/forums/how-build-low-cost-linux-home-102018.html](http://www.techenclave.com/forums/how-build-low-cost-linux-home-102018.html)
Personally, this is one project that I really want to do, just as soon as I get home from school. Let us know how it goes!will do!

---

### Post by imon9 on 2007-12-02
> **ubuntuman001 said:**
> question:
1) is a DNS server the same as a web server?

2) are domains only payable by subscriptions and such, i.e. can you not "own" your domain fully with a one time payment or something?

(1) DNS server is a domain name server, it is not the same as web server! DNS is used for translating web-adresses such as [www.google.com](www.google.com) to its IP adress eg:435.123.55.43 (as IP adresses as the concrete way to point to a concrete server). DNS server is used in ISP, and internet sharing machine, routers. It is not needed for webserver

(2) domain is ONLY by subscription.

---

### Post by user1397 on 2007-12-04
Okay, I was planning on doing the whole domain buying thing and setting up the rest of the stuff on my server today, but I still am very confused on some things...

I don't know if this info is of any use, but my intention is to host a professional website on this server, explaining my services, so I would like the URL to be something easily readable, not a random IP address.

Questions:

1) What do I need to do to setup a static IP address for my server? Do I have to request something from my ISP (cox) or change some router settings in my browser? or do i do it all in ubuntu?

2) Do I have to do the whole DynDNS thing? Is there any way I can host my own website without having to pay for something? Does DynDNS basically control this market? I thought there were so many other web hosting companies and services...

3) If I choose DynDNS, should I do Dynamic DNS or Custom DNS?  Why one over the other?

---

### Post by user1397 on 2007-12-04
bump

---

### Post by dfreer on 2007-12-04
Hey ubuntuman001,

 Just saw this thread, and thought I'd chime in since this is exactly what I've already done (created a home web server). 
As for the questions you recently asked:

**(1).** There's two IP addresses you need to worry about when you create your own web server, your external IP address (the IP address your ISP gives you, that everyone else uses to access your site), and your internal LAN IP address (the IP address that your home router gives you, generally a private IP address like 192.168.1.5).

Now, in an ideal world you'd want both IP addresses to be static, but it is almost assured that your ISP gives you a dynamic external IP address. And, depending on your ISP, they may cancel your service if you run a webserver, due to you violating their terms of service. OR, they may decide to charge you business access rates, in my area that's like the difference between $40 a month to $100+ dollars a month. Some ISP's don't care, and some may be operating on the "Don't ask, don't tell" philosophy. Either way, I'd just assume that you are stuck with a dynamic IP address, and that they won't mind the little traffic your site might generate.

That's why you need dyndns.com/no-ip.com/etc to monitor your current external IP address, and update it on various domain name servers. But it appears you've already covered this part.

Your internal IP address should also be static, so that it is easier to set up port forwarding from your router to your server. Port Forwarding is the key that is going to let visitors to your site access your **internal** web server from the **external** IP address. Setting up a static IP address in Linux is rather easy, just look at /etc/network/interfaces file. I'd need to know the specifics of your internal LAN to tell you exactly what information to put in there, but here's an example of an interface using DHCP and a static interface:
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
  pre-up iptables-restore < /etc/iptables.up.rules
    address 192.168.1.5
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

```

A further safeguard would be to enter your router's configuration page, and depending on your router, you should be able to specify that certain MAC addresses will get static IP addresses, whereas all other computer's will continue using DHCP. Set the MAC address of your web servers network card to have the same static IP address you set in your /etc/network/interfaces file.

If your router doesn't let you do that, at least set the DHCP pool range to not include your server's static IP address. For example, if I set my static IP to my 192.168.1.5, I'd set my DHCP pool to begin assigning IP address at 192.168.1.100, that way I'm sure no other computer on my LAN will get my server's IP address assigned to it from DHCP.

**(2). **You can host your website for absolutely nothing simply by referring to it by it's external IP address. Of course, it's going to be mighty inconvienent if your external IP address keeps changing, and no one wants to type a string of numbers just to visit your site.

  So, the two things you'll want here is a Nameserver, and a domain name. The domain name should be obvious, it can be as simple as [http://google.com](http://google.com) or as long as [http://freedm.angelfire.com/~users/planet/mysite/](http://freedm.angelfire.com/~users/planet/mysite/). 

  The top level domains like google.com, dfreer.org, etc are going to cost money, I don't think there is any way around that. However, for dfreer.org I pay like $15 a year, and I'm told you can get top-level domain names even cheaper than that. 

   Nameservers == DNS, it basically is just a database mapping the name of the site with the IP address of the site. Do a google for Free DNS and you should get an idea of your options to choose from, some better than others.

   The beauty of dyndns.com or no-ip.com, is that they provide you with multiple Nameservers, domain name, and an update client for FREE. I'd definitely recommend one of those sites, or even both if you are looking for the free/cheap route. There are other solutions out there, although they often aren't intergrated. 

For free nameservers/DNS, just do a google for "free DNS".
For free intergrated services, check this link out:
[http://www.dmoz.org/Computers/Software/Internet/Servers/Address_Management/Dynamic_DNS_Services/](http://www.dmoz.org/Computers/Software/Internet/Servers/Address_Management/Dynamic_DNS_Services/)

**(3).** Custom DNS is what I currently use for dfreer.org. It lets you use a purchased domain name (I bought dfreer.org through dyndns.com because I wanted to keep things all in one spot, but you can use Custom DNS with a domain name purchased elsewhere). It's really nice, and I think for the domain name + custom DNS I pay a total of $30 a year. Not too shabby.

Dynamic DNS is the free solution, that gives you a domain name like [http://mysite.dynamic.com](http://mysite.dynamic.com), and really isn't a bad solution if you don't feel the need for a top-level domain name.

---

### Post by ghandi69_ on 2007-12-04
> **ubuntuman001 said:**
> Okay, I was planning on doing the whole domain buying thing and setting up the rest of the stuff on my server today, but I still am very confused on some things...

I don't know if this info is of any use, but my intention is to host a professional website on this server, explaining my services, so I would like the URL to be something easily readable, not a random IP address.

Questions:

1) What do I need to do to setup a static IP address for my server? Do I have to request something from my ISP (cox) or change some router settings in my browser? or do i do it all in ubuntu?

2) Do I have to do the whole DynDNS thing? Is there any way I can host my own website without having to pay for something? Does DynDNS basically control this market? I thought there were so many other web hosting companies and services...

3) If I choose DynDNS, should I do Dynamic DNS or Custom DNS?  Why one over the other?

Ubunutuman, I basically just got through doing exactly what you plan on doing.  However, I was blessed with the following

And ISP that provides me with a static ip, and and ISP that does not block port 80.

So all I had to do, was install server edition on my old comp, give it a local static ip address, buy a domain name from godaddy.com and forward that name to my ip given to me by my isp, install apache on the machine, but stuff into the /var/www folder, and then last but not least, forward port 80 from the router to my server, I did not have to do anything with DynDNS or anything like that.

If you have any more questions I could be glad to go into detail on any of those steps.

---

### Post by user1397 on 2007-12-04
> **dfreer said:**
> Hey ubuntuman001,

 Just saw this thread, and thought I'd chime in since this is exactly what I've already done (created a home web server). 
As for the questions you recently asked:

**(1).** There's two IP addresses you need to worry about when you create your own web server, your external IP address (the IP address your ISP gives you, that everyone else uses to access your site), and your internal LAN IP address (the IP address that your home router gives you, generally a private IP address like 192.168.1.5).

Now, in an ideal world you'd want both IP addresses to be static, but it is almost assured that your ISP gives you a dynamic external IP address. And, depending on your ISP, they may cancel your service if you run a webserver, due to you violating their terms of service. OR, they may decide to charge you business access rates, in my area that's like the difference between $40 a month to $100+ dollars a month. Some ISP's don't care, and some may be operating on the "Don't ask, don't tell" philosophy. Either way, I'd just assume that you are stuck with a dynamic IP address, and that they won't mind the little traffic your site might generate.

That's why you need dyndns.com/no-ip.com/etc to monitor your current external IP address, and update it on various domain name servers. But it appears you've already covered this part.

Your internal IP address should also be static, so that it is easier to set up port forwarding from your router to your server. Port Forwarding is the key that is going to let visitors to your site access your **internal** web server from the **external** IP address. Setting up a static IP address in Linux is rather easy, just look at /etc/network/interfaces file. I'd need to know the specifics of your internal LAN to tell you exactly what information to put in there, but here's an example of an interface using DHCP and a static interface:
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
  pre-up iptables-restore < /etc/iptables.up.rules
    address 192.168.1.5
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

```A further safeguard would be to enter your router's configuration page, and depending on your router, you should be able to specify that certain MAC addresses will get static IP addresses, whereas all other computer's will continue using DHCP. Set the MAC address of your web servers network card to have the same static IP address you set in your /etc/network/interfaces file.

If your router doesn't let you do that, at least set the DHCP pool range to not include your server's static IP address. For example, if I set my static IP to my 192.168.1.5, I'd set my DHCP pool to begin assigning IP address at 192.168.1.100, that way I'm sure no other computer on my LAN will get my server's IP address assigned to it from DHCP.

**(2). **You can host your website for absolutely nothing simply by referring to it by it's external IP address. Of course, it's going to be mighty inconvienent if your external IP address keeps changing, and no one wants to type a string of numbers just to visit your site.

  So, the two things you'll want here is a Nameserver, and a domain name. The domain name should be obvious, it can be as simple as [http://google.com](http://google.com) or as long as [http://freedm.angelfire.com/~users/planet/mysite/]("http://freedm.angelfire.com/%7Eusers/planet/mysite/"). 

  The top level domains like google.com, dfreer.org, etc are going to cost money, I don't think there is any way around that. However, for dfreer.org I pay like $15 a year, and I'm told you can get top-level domain names even cheaper than that. 

   Nameservers == DNS, it basically is just a database mapping the name of the site with the IP address of the site. Do a google for Free DNS and you should get an idea of your options to choose from, some better than others.

   The beauty of dyndns.com or no-ip.com, is that they provide you with multiple Nameservers, domain name, and an update client for FREE. I'd definitely recommend one of those sites, or even both if you are looking for the free/cheap route. There are other solutions out there, although they often aren't intergrated. 

For free nameservers/DNS, just do a google for "free DNS".
For free intergrated services, check this link out:
[http://www.dmoz.org/Computers/Software/Internet/Servers/Address_Management/Dynamic_DNS_Services/](http://www.dmoz.org/Computers/Software/Internet/Servers/Address_Management/Dynamic_DNS_Services/)

**(3).** Custom DNS is what I currently use for dfreer.org. It lets you use a purchased domain name (I bought dfreer.org through dyndns.com because I wanted to keep things all in one spot, but you can use Custom DNS with a domain name purchased elsewhere). It's really nice, and I think for the domain name + custom DNS I pay a total of $30 a year. Not too shabby.

Dynamic DNS is the free solution, that gives you a domain name like [http://mysite.dynamic.com](http://mysite.dynamic.com), and really isn't a bad solution if you don't feel the need for a top-level domain name.Thank you so much for all the info you've given me.

So I made a dynamic dns hostname, all for free. :)
I found out my ISP does assign dynamic external IP addresses.

I went into my router settings too, and I forwarded port 80 to this IP address: 192.168.1.150 which is just out of range of my DHCP.

So, all I think I have to do now is set my webserver's IP to static...but I'm not sure what information to put in the /etc/network/interfaces file...

---

### Post by p_quarles on 2007-12-04
To set the static IP address, go to the listing for the main network device (probably eth0), and delete the word "dhcp." Replace it with "static." Then add the following three lines directly under that:
```
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.0.1
```The "gateway" setting is the address of your router, so be sure to change that one to whatever the router actually is.

---

### Post by user1397 on 2007-12-04
> **p_quarles said:**
> To set the static IP address, go to the listing for the main network device (probably eth0), and delete the word "dhcp." Replace it with "static." Then add the following three lines directly under that:
```
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.0.1
```The "gateway" setting is the address of your router, so be sure to change that one to whatever the router actually is.Thanks!!!
This was the final step to make it work, I'm finally done! Yay!!!!! :) :) :)

I will post a detailed account of how I did it all and add it to my first post as an edit.

Thank you so much everyone who helped me with this.

---

### Post by dfreer on 2007-12-04
So you are able to access your site from the internet? Congrats!

One useful tool I like to use is a internet proxy, to be able to check whether my site is accessible from the internet and not just my LAN, here's one I use:
[http://www.free-canadian-proxy.info/](http://www.free-canadian-proxy.info/)

---

### Post by user1397 on 2007-12-04
> **dfreer said:**
> So you are able to access your site from the internet? Congrats!

One useful tool I like to use is a internet proxy, to be able to check whether my site is accessible from the internet and not just my LAN, here's one I use:
[http://www.free-canadian-proxy.info/](http://www.free-canadian-proxy.info/)
Oh no! It only works on my LAN...:(
That site says "error 110: connection timed out"

What should I do?

Am I supposed to edit any apache config files or ddclient files or something? (Is ddclient even necessary?)

---

### Post by p_quarles on 2007-12-04
ddclient just updates the dns server whenever your IP address changes, so that isn't the problem (though you will need to configure that before it works). 

Some things to do:
1) If you didn't already, restart networking on the server:
```
sudo /etc/init.d/networking restart
```
I forgot to mention that, but you need to do that (or restart the computer) before the static IP address will take effect. 

2) Edit /etc/apache2/ports.conf. Change the default configuration to include your machine's IP address:
```
Listen 192.168.1.150:80
```
Then, restart Apache:
```
sudo /etc/init.d/apache2 restart
```
3) Finally, it may be that your ISP is blocking port 80. To find out, change Apache to listen on a different port. Edit the same file as in step, but change the "80" after the colon to something like "15912". Again, restart Apache. This time, however, you will also need to change the port-forwarding settings on your router to indicate the new port. When you browse to your site, you'll need to specify the port number now:
```
http://some.site.org:15912
```

---

### Post by user1397 on 2007-12-04
> **p_quarles said:**
> ddclient just updates the dns server whenever your IP address changes, so that isn't the problem (though you will need to configure that before it works). 

Some things to do:
1) If you didn't already, restart networking on the server:
```
sudo /etc/init.d/networking restart
```I forgot to mention that, but you need to do that (or restart the computer) before the static IP address will take effect. 

2) Edit /etc/apache2/ports.conf. Change the default configuration to include your machine's IP address:
```
Listen 192.168.1.150:80
```Then, restart Apache:
```
sudo /etc/init.d/apache2 restart
```3) Finally, it may be that your ISP is blocking port 80. To find out, change Apache to listen on a different port. Edit the same file as in step, but change the "80" after the colon to something like "15912". Again, restart Apache. This time, however, you will also need to change the port-forwarding settings on your router to indicate the new port. When you browse to your site, you'll need to specify the port number now:
```
http://some.site.org:15912
```Yep, my ISP is blocking port 80. What can I do about that?

---

### Post by p_quarles on 2007-12-04
> **ubuntuman001 said:**
> Yep, my ISP is blocking port 80. What can I do about that?
Well, you could always ask them to unblock it, but it's very unlikely that they will. Apart from that, you'll just have to run the site on an alternate port.

---

### Post by user1397 on 2007-12-04
> **p_quarles said:**
> Well, you could always ask them to unblock it, but it's very unlikely that they will. Apart from that, you'll just have to run the site on an alternate port.Really? So to go to my site I'll always have to have a colon and port number after the url?
I am going to have a nice conversation with the folks at cox communications...

---

### Post by user1397 on 2007-12-05
> **p_quarles said:**
> Well, you could always ask them to unblock it, but it's very unlikely that they will. Apart from that, you'll just have to run the site on an alternate port.Thanks again for all your help.
What ports could I use? Which ones are more convenient? (Cause I'd rather have a port 65 or something rather than port 15912...)

---

### Post by dfreer on 2007-12-05
I do believe one of those dynamic dns services allow you to do HTTP port redirection, which basically allows you to run apache on a nonstandard port, but users access your site without having to type in the port number. To them, it appears like your site is at port 80.

Although, did you throughly test port 80 or know somehow that your ISP blocks port 80? I'm not entirely convinced that is the case, but if you know for sure then that's fine.

---

### Post by p_quarles on 2007-12-05
You could use any port that's not being used by another service. There's a list (incomplete) of default port numbers [here]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers") [wikipedia]. 65 looks okay. 

As far as I know, the most commonly blocked ports are 25 (smtp; this prevents customers from getting their boxes turned into spambots), and 80. Blocking port 80 *could *be seen as a lazy way of preventing innocent people from hosting phishing sites, but it's not that effective. The likelier reason is that web sites can be easily turned into commercial ventures (via AdSense, etc.), so the ISPs will want extra before they let you run one.

[edit]@dfreer: Good points. I'm fairly sure that DynDNS doesn't provide custom port service, but it's definitely worth investigating other services. 

As for making really sure that port 80 is blocked, this is a pretty good way.
1) Get nmap:
```
sudo apt-get install nmap
```2) Find your public IP address (e.g., myip.com)
3) Run nmap on your public IP address:
```
nmap -P0 *your*.*public.ip.address*
```It would be even better to run this scan from a computer outside your LAN, but I've found this method to be 100% reliable in my own tests so far.
[ /edit]

---

### Post by Crashmaxx on 2007-12-05
> **p_quarles said:**
> You could use any port that's not being used by another service. There's a list (incomplete) of default port numbers [here]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers") [wikipedia]. 65 looks okay. 

As far as I know, the most commonly blocked ports are 25 (smtp; this prevents customers from getting their boxes turned into spambots), and 80. Blocking port 80 *could *be seen as a lazy way of preventing innocent people from hosting phishing sites, but it's not that effective. The likelier reason is that web sites can be easily turned into commercial ventures (via AdSense, etc.), so the ISPs will want extra before they let you run one.

[edit]@dfreer: Good points. I'm fairly sure that DynDNS doesn't provide custom port service, but it's definitely worth investigating other services. 

As for making really sure that port 80 is blocked, this is a pretty good way.
1) Get nmap:
```
sudo apt-get install nmap
```2) Find your public IP address (e.g., myip.com)
3) Run nmap on your public IP address:
```
nmap -P0 *your*.*public.ip.address*
```It would be even better to run this scan from a computer outside your LAN, but I've found this method to be 100% reliable in my own tests so far.
[ /edit]

I just use shields up to see what ports are open. It checks your public ip and you tell it which ports to check, common ports or all service ports is what I do, and it will tell which are open, closed, and stealthed. It is designed to check that your firewall is secure, but I find it great for just this sort of thing. I also used it here at school to find an open port for torrents.
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Oh and if you need to use a different port, two things. One, you can use port 80 for the actual server if you want and when you setup port forwarding, have your LAN port 80 forward to the internet as another port, 8080 is a common alternative. Second, dyndns.com does support alternate ports and will even cloak them if you like, here is the FAQ on it.
[https://www.dyndns.com/support/kb/webhops_redirections.html](https://www.dyndns.com/support/kb/webhops_redirections.html)

---

### Post by user1397 on 2007-12-05
> **dfreer said:**
> I do believe one of those dynamic dns services allow you to do HTTP port redirection, which basically allows you to run apache on a nonstandard port, but users access your site without having to type in the port number. To them, it appears like your site is at port 80.

Although, did you throughly test port 80 or know somehow that your ISP blocks port 80? I'm not entirely convinced that is the case, but if you know for sure then that's fine.I don't know just because; I tried p_quarles way of getting apache to listen to a different port, and then it worked.

> **p_quarles said:**
> You could use any port that's not being used by another service. There's a list (incomplete) of default port numbers [here]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers") [wikipedia]. 65 looks okay. 

As far as I know, the most commonly blocked ports are 25 (smtp; this prevents customers from getting their boxes turned into spambots), and 80. Blocking port 80 *could *be seen as a lazy way of preventing innocent people from hosting phishing sites, but it's not that effective. The likelier reason is that web sites can be easily turned into commercial ventures (via AdSense, etc.), so the ISPs will want extra before they let you run one.

[edit]@dfreer: Good points. I'm fairly sure that DynDNS doesn't provide custom port service, but it's definitely worth investigating other services. 

As for making really sure that port 80 is blocked, this is a pretty good way.
1) Get nmap:
```
sudo apt-get install nmap
```2) Find your public IP address (e.g., myip.com)
3) Run nmap on your public IP address:
```
nmap -P0 *your*.*public.ip.address*
```It would be even better to run this scan from a computer outside your LAN, but I've found this method to be 100% reliable in my own tests so far.
[ /edit]I'll try this method and see how it goes.

> **Crashmaxx said:**
> I just use shields up to see what ports are open. It checks your public ip and you tell it which ports to check, common ports or all service ports is what I do, and it will tell which are open, closed, and stealthed. It is designed to check that your firewall is secure, but I find it great for just this sort of thing. I also used it here at school to find an open port for torrents.
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Oh and if you need to use a different port, two things. One, you can use port 80 for the actual server if you want and when you setup port forwarding, have your LAN port 80 forward to the internet as another port, 8080 is a common alternative. Second, dyndns.com does support alternate ports and will even cloak them if you like, here is the FAQ on it.
[https://www.dyndns.com/support/kb/webhops_redirections.html](https://www.dyndns.com/support/kb/webhops_redirections.html)thanks for the link, I have some reading to do :)

---

### Post by user1397 on 2007-12-05
> **p_quarles said:**
> As for making really sure that port 80 is blocked, this is a pretty good way.
1) Get nmap:
```
sudo apt-get install nmap
```2) Find your public IP address (e.g., myip.com)
3) Run nmap on your public IP address:
```
nmap -P0 *your*.*public.ip.address*
```It would be even better to run this scan from a computer outside your LAN, but I've found this method to be 100% reliable in my own tests so far.
[ /edit]
So I tried this and it returns:
```
Interesting ports on (my ip address):
Not shown: 1696 closed ports
PORT    STATE  SERVICE
80/tcp  open   http
```so...it's NOT closed? :confused:

---

### Post by Crashmaxx on 2007-12-05
Does shields up say the same? If so then check that the ip is right for dyndns.com.

EDIT: I just tried nmap on my system which should only show port 53 open, shows a lot more then that, I think it is resolving the name and doing the scan internal to the NAT. A tool like shields up should do a better job being outside your network.

---

### Post by p_quarles on 2007-12-05
> **Crashmaxx said:**
> Does shields up say the same? If so then check that the ip is right for dyndns.com.

EDIT: I just tried nmap on my system which should only show port 53 open, shows a lot more then that, I think it is resolving the name and doing the scan internal to the NAT. A tool like shields up should do a better job being outside your network.
No, nmap is reliable. If you use it to scan your public address, it won't look at your computer at all: it's looking at your your gateway connection. After all, nmap isn't smart enough to know what your public IP address is, so it couldn't very well skip the public DNS lookup step. 

I second the idea of doublechecking the settings at dyndns, though.

---

### Post by user1397 on 2007-12-05
> **Crashmaxx said:**
> Does shields up say the same? If so then check that the ip is right for dyndns.com.

EDIT: I just tried nmap on my system which should only show port 53 open, shows a lot more then that, I think it is resolving the name and doing the scan internal to the NAT. A tool like shields up should do a better job being outside your network.hmm shields up says that all of my ports 1 - 1056 are in full stealth mode...

---

### Post by p_quarles on 2007-12-05
> **ubuntuman001 said:**
> hmm shields up says that all of my ports 1 - 1056 are in full stealth mode...
Are you positive that your scanning the *public* IP address?

---

### Post by user1397 on 2007-12-05
> **p_quarles said:**
> Are you positive that your scanning the *public* IP address?It has to be...I mean, it didn't let me choose one anyway, it just said "proceed" and then it showed me my IP address (and it is the same one that came up automatically in dyndns.com)

EDIT: I tried disabling a setting in my router titled: "Block anonymous internet requests" but shields up still said port 80 was in stealth status, yet it failed one out of three tests (the ping reply one)

then i tried my domain at a proxy server, but still no go.

---

### Post by Crashmaxx on 2007-12-05
> **ubuntuman001 said:**
> hmm shields up says that all of my ports 1 - 1056 are in full stealth mode...

That sounds right if your router firewall is working. But are you sure you forwarded port 80 on the router for the internal IP of the server?

---

### Post by user1397 on 2007-12-05
> **Crashmaxx said:**
> That sounds right if your router firewall is working. But are you sure you forwarded port 80 on the router for the internal IP of the server?I...think so :confused: but I'm not entrirely sure...

In the "applications and gaming" section of my router settings, I found the "Port Range Forward" and "Port Triggering" settings:

In  "Port Range Forward," it asks for the application (I left this blank), the starting port (I put 80 here), the end port (again I put 80 here), the protocol (tcp/udp/both, I put both), the ip address (i put my server's static ip here) and then it has an enable checkbox.

"Port Triggering" is similar, yet it does not ask for an ip address, nor the protocol, but instead it asks for a triggered range start and end port, and a forwarded range start and end port. (I left this alone)

With these settings, I am able to view my server's /var/www/index.html file through any browser through any computer in my LAN.

EDIT: I also see a "static routing" section in my router settings, but I don't know if this is what I need to get it to work. it asks for operating mode (with the choice of gateway or router), route name, destination LAN IP, subnet mask, default gateway, and interface (with the choice of LAN & Wireless OR WAN)
No luck with proxy servers though.

---

### Post by p_quarles on 2007-12-05
It sounds like you're doing everything right. I'm kinda running out of ideas here. A couple thoughts:

First, what happens if you run nmap without the "-P0" option? If you get a different result, that might point to something.

Second, do you have any network hardware "in front of" the router? For instance, I have a DSL modem and a separate router. The modem is essentially a one-port router as well, and I have to configure both it and my router to get ports forwarded to the proper destination.

---

### Post by user1397 on 2007-12-05
> **p_quarles said:**
> It sounds like you're doing everything right. I'm kinda running out of ideas here. A couple thoughts:

First, what happens if you run nmap without the "-P0" option? If you get a different result, that might point to something.nope, shows the same result.

> **p_quarles said:**
>  Second, do you have any network hardware "in front of" the router? For instance, I have a DSL modem and a separate router. The modem is essentially a one-port router as well, and I have to configure both it and my router to get ports forwarded to the proper destination.well yes, I have a cable modem and a separate router; the coaxial cable goes from the wall to the modem, and the ethernet cable goes from the modem to the router.
the only button on my modem is a standby button.

---

### Post by p_quarles on 2007-12-05
Well, if you're getting the same result with pings, it's probably not the cable modem that's the problem. 

I'm really not sure what's going on here. It looks like port 80 is open, and if your ISP were blocking inbound http traffic, it wouldn't have worked with the alternate port configuration you tried earlier. 

I guess it's time to look into what others have suggested: setting dyndns to automatically request the alternate port.

---

### Post by user1397 on 2007-12-05
> **p_quarles said:**
> Well, if you're getting the same result with pings, it's probably not the cable modem that's the problem. 

I'm really not sure what's going on here. It looks like port 80 is open, and if your ISP were blocking inbound http traffic, it wouldn't have worked with the alternate port configuration you tried earlier. 

I guess it's time to look into what others have suggested: setting dyndns to automatically request the alternate port.yes I guess that's my only option that's left, though it is rather confusing to set that dyndns stuff up.  I was trying to do it earlier, but it sure wasn't fun...

Oh well, thanks so much everyone for helping me with everything.

---

### Post by user1397 on 2007-12-05
Well I was finally able to figure out the webhop service from dyndns that allowed me to redirect my site.  It works now (YAY!)

Thanks again everyone who helped me along the way.

---

### Post by user1397 on 2007-12-05
Hmm I'm thinking about actually writing a howto for this.
If I do, I'll make a new thread in the tutorials forum.

---

### Post by alwiap on 2007-12-05
> **ubuntuman001 said:**
> Hmm I'm thinking about actually writing a howto for this.
If I do, I'll make a new thread in the tutorials forum.

please do. i've been glancing around the thread and preparing an old box for a server, i'm sure i'm not alone :)

---

### Post by user1397 on 2007-12-05
> **alwiap said:**
> please do. i've been glancing around the thread and preparing an old box for a server, i'm sure i'm not alone :)working on it as we speak :)

---

### Post by tr333 on 2007-12-06
If you're going to run apache on a different port than 80, you should probably be using port 8080.  This port number is assigned by IANA as 'HTTP Alternate'.  You shouldn't be using any port number below 123, as they are reserved port numbers.

[http://www.yougetsignal.com/openPortsTool/](http://www.yougetsignal.com/openPortsTool/), [http://www.canyouseeme.org/](http://www.canyouseeme.org/) - These websites will allow you to check if your port forwarding is setup correctly.

To get past the problem of having to type [http://yoursite.dyndns.com:8080/](http://yoursite.dyndns.com:8080/) with the port number, dyndns.com provides a free web redirection service.  This allows you to setup a web-redirect to [http://yoursite.dyndns.com:8080/](http://yoursite.dyndns.com:8080/) from a standard url like [http://yoursite.webhop.org/](http://yoursite.webhop.org/).

---

### Post by user1397 on 2007-12-06
> **tr333 said:**
> If you're going to run apache on a different port than 80, you should probably be using port 8080.  This port number is assigned by IANA as 'HTTP Alternate'.  You shouldn't be using any port number below 123, as they are reserved port numbers.

[http://www.yougetsignal.com/openPortsTool/](http://www.yougetsignal.com/openPortsTool/), [http://www.canyouseeme.org/](http://www.canyouseeme.org/) - These websites will allow you to check if your port forwarding is setup correctly.

To get past the problem of having to type [http://yoursite.dyndns.com:8080/](http://yoursite.dyndns.com:8080/) with the port number, dyndns.com provides a free web redirection service.  This allows you to setup a web-redirect to [http://yoursite.dyndns.com:8080/](http://yoursite.dyndns.com:8080/) from a standard url like [http://yoursite.webhop.org/](http://yoursite.webhop.org/).Thanks, but I've already gotten it to work.  I'm using port 8090, which is another alternate HTTP port, and I have already setup the free web-redirect service in dyndns.com with the webhop setting.

It all works fine now!

---

### Post by user1397 on 2007-12-06
Does anyone know how to remove the top frame that DynDNS puts on your webhop site? It advertises the free webhop redirection service, and it looks like a black bar across the top of your page.

---

### Post by tr333 on 2007-12-06
> **ubuntuman001 said:**
> Does anyone know how to remove the top frame that DynDNS puts on your webhop site? It advertises the free webhop redirection service, and it looks like a black bar across the top of your page.

I don't get that with the webhop that I use.  Maybe it appears when you have the url masking turned on.  I just let the webhop redirect to my webpage.dyndns.com:8080 page.

---

### Post by user1397 on 2007-12-09
> **tr333 said:**
> I don't get that with the webhop that I use.  Maybe it appears when you have the url masking turned on.  I just let the webhop redirect to my webpage.dyndns.com:8080 page.yep, you were right, taking off the URL masking solved the problem, thanks.

---

### Post by user1397 on 2007-12-13
By the way, I have written my guide on the steps I used to make this work, [_here_]("http://ubuntuforums.org/showthread.php?t=632841")

Thanks everyone who helped me with this.

---

### Post by tech9 on 2007-12-18
> **ubuntuman001 said:**
> By the way, I have written my guide on the steps I used to make this work, [_here_]("http://ubuntuforums.org/showthread.php?t=632841")

Thanks everyone who helped me with this.

nice work ubuntuman001 :)

---

### Post by alwiap on 2007-12-18
> **ubuntuman001 said:**
> By the way, I have written my guide on the steps I used to make this work, [_here_]("http://ubuntuforums.org/showthread.php?t=632841")

Thanks everyone who helped me with this.

great, i will do this tonight :)

---

