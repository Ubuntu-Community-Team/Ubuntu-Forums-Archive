---
title: "trying to figure out Linux + web &amp; mail server"
date: 2007-12-04
forum: Server Platforms
---

### Post by rebeltaz on 2007-12-04
Ok.. I'll admit it straight out - I have absolutely no idea what I am doing here! I have been studying computers (in the school of practical experience, of course) since I was 10. I hate to admit it, but yes... I was a faithful follower of Lord Bill Gates. But all that is changing. I have migrated most of my computing to iMacs and now I am trying to learn Linux for a web server system I built. 

Here's where I am at right now...

I have Ubuntu Server 7.10 installed running the following support software - Apache 2.2, ProFTPd, BIND9, MySQL 5.0, PostFix, Courier-POP3/Courier-IMAP and ISPConfig. I followed a tutorial that I found on HowToForge.com called The Perfect Server - Ubuntu Gutsy Gibbon (Ubuntu 7.10) for directions on setting up the web server. 

Through trial-and-error (along with a little help from the guys on the HowToForge forums) I have succeeded in setting up four domain names through 1and1.com and hosting them on my own local server. I am told that the way I am doing it doesn't work, but it is the only way that I could get it to.  

I am able to FTP into any one of the four accounts and transfer files to and from the server. 

This is where my efforts have ground to a halt - What I want to do is to 1) use my own server to host one of the DNS name servers (I only have one static IP available to me right now) and 2) I want to use my server as a mail server. 

](*,)

I guess I am getting too old to be learning new tricks, but I am determined! I will GREATLY appreciate any advice/tutorials/referrals that you think might help!

BTW - in case you are interested, the sites that I am currently hosting are:

[www.ShelbyTVServices.com](www.ShelbyTVServices.com)
[www.RobotsAndComputers.com](www.RobotsAndComputers.com)

and

[www.Computer-Graveyard.com](www.Computer-Graveyard.com)

I will use that one as a test bed as I have decided to use the RobotsAndComputers domain instead. 

!!!  PLEASE  HELP  !!!

---
Derek Tombrello
ShelbyCycle.com

---

### Post by HermanAB on 2007-12-04
Here you go: [http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

The Citadel quick install script takes about 20 minutes.  Figuring out how to install Postfix/Apache/Roundcube/Webcal/Dovecot/Jabber/SpamAssassin/ClamAV from scratch will take about 2 weeks.  Your choice!

Cheers,

Herman

---

### Post by DDuong on 2007-12-04
Hello,

Welcome to the world of linux!

Anyways, I was in the same situation as you when I was building my first mail/web server.

First off, since you have BIND9 installed, you will have to learn how DNS works and how to set one up.  Since you mentioned that your server for DNS, I suggest you read the following:

> 
[http://www.howtoforge.com/traditional_dns_howto](http://www.howtoforge.com/traditional_dns_howto)


Basically you will need to get your server to be reconized on the internet.  So a DNS record (I believe an A record) would have to point to your server.  

I noticed that you are with 1and1.  I didn't have success with them (but that could just be me).  I'm currently with GoDaddy and I'm fairly happy with them.

DNS was the hardest part for me but after doing a lot of reading, it's very easy.

Good Luck!

---

### Post by Brazen on 2007-12-04
Howtoforge has some descent information on it, but thos "Perfect Setup" guides are the worst I have ever seen.

Number 1, you'll be MUCH better off sticking to the LTS releases of Ubuntu on a server.  That would currently be Ubuntu 6.06 Server.

Number 2, read the relevant sections here for setting up your server: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html)

---

### Post by rebeltaz on 2007-12-04
I appreciate all of your replies... 

I glanced at all three suggestions. Right now I am about as far under the weather as I can get, so technical reading is giving me a headache! 

I will study all three more in depth when I am feeling better... :(

I'm glad I have somewhere to turn for help on this! :)

---

### Post by rebeltaz on 2007-12-04
[QUOTE=Brazen;3889834]Howtoforge has some descent information on it, but thos "Perfect Setup" guides are the worst I have ever seen.

Number 1, you'll be MUCH better off sticking to the LTS releases of Ubuntu on a server.  That would currently be Ubuntu 6.06 Server.



Why do you suggest 6.06 over 7.10? Just curious...

---

### Post by rebeltaz on 2007-12-04
> **DDuong said:**
> 
Welcome to the world of linux!

First off, since you have BIND9 installed, you will have to learn how DNS works and how to set one up.  Since you mentioned that your server for DNS, I suggest you read the following:



Basically you will need to get your server to be reconized on the internet.  So a DNS record (I believe an A record) would have to point to your server.  


I read the tutorial you suggested, and I think I can figure out DNS... not too difficult. What I don't understand is this... How does the rest of the world see my DNS server? 

The settings in ISPConfig show that NameServers 1 & 2 are set to server.shelby.com - the host name of my server computer. On 1&1, I tried to use 72.149.151.22 (my IP address) as the name server, but it didn't accept that. I created a sub-domain under Computer-Graveyard.com called ns1 and used that instead. It took that, but that the only way I can see that working is if I use that same (ns1.computer-graveyard.com) as the name server for all my sites - which would work I guess, but it wouldn't be as intuitive.

How would I make 1&1, or the rest of the world, see say - ns1.server.shelby.com that I could use for ALL of my sites, without registering yet another domain name? Or, will creating an ns1 subdomain under each domain name still work? If so, what would I do with the Name Server settings under ISPConfig? 

Why on earth did I get myself into this!?

---

### Post by justtech on 2007-12-09
I am in the process of wanting to do this myself.  Any luck with finding your answer?

---

### Post by rebeltaz on 2007-12-17
Unfortunately no. You?

---

### Post by now-new on 2007-12-18
first of all the first domain is not working and second of all 
check this web and see if it works
I was going to do it right now but I am tired and I am going to sleep  now.
let me know what happends
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

