---
title: "Setting Up an Email Server"
date: 2009-06-16
forum: Server Platforms
---

### Post by hmx_ryan on 2009-06-16
Good Day,

I'm having problems with setting up my own Email Server... As basic information for first timer, I followed the information/step/procedures posted in the ```
http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3
```... However, I'm having problem with setting up my server to be seen outside my Domain... Example, [http://servername.mydomain.com](http://servername.mydomain.com)... Instead, I can only access my server in our local IP Address... Hopefully you could spare some information regrading my problem...

In addition, how could I add an email account on my server... Plus, can also please provide me with the prerequisites on setting up an Email Server using Ubuntu... Example, is there a need to ask something from my ISP, or just merely having an internet connection is enough for me to set up an Email Server...

Please Help... Its my first time to set up an Ubuntu Server...

Thanks in Advance...

---

### Post by hictio on 2009-06-17
You are going to handle an email server for a domain, that is, a server that will be able to receive over the internet emails sent to that domain, is that right?

Do you have your own domain already?
If you do, who handles the DNS for such domain?

You'll have to, prior to anything, setup the DNS for that domain in order that the MX records point to the IP address that your Ubuntu Server box has, the one that will be the mail server.
Needless to say, if you want to receive emails over the internet, that IP address has to be a public one.

The other thing, your ISP has to have the smtp port (25 TCP) open on that public IP address for you to receive emails for this domain.

Other than that, you can start by reading this [Chapter 13. Email Services](https://help.ubuntu.com/8.10/serverguide/C/email-services.html), from the [Ubuntu Server Guide](https://help.ubuntu.com/8.10/serverguide/C/)

---

### Post by hmx_ryan on 2009-06-17
Oh no... I don't have any DNS yet.. I'm setting my Router to act as a DNS also..Is this fine?

---

### Post by hictio on 2009-06-17
> **hmx_ryan said:**
> Oh no... I don't have any DNS yet.. I'm setting my Router to act as a DNS also..Is this fine?

Nope.
Yes, the Ubuntu Server that will work as an email server will definitively need name resolution, and will need to use a DNS server for that.
But, what I meant was that if you want to handle the email for a domain, the first thing you have to do is get that domain, and in doing so, at the registrar you'll have to define the DNS records for the domain, the MX record has to point to the public IP address of your Ubunte Server.

That's step one.

The other one, your ISP has to let pass SMTP traffic, so the people that sends email to your box actually reaches.

On your network, you have to make sure, if you have a router connecting to the internet, that the router allows SMTP traffic all the way to your Ubuntu Server on your network.
Depending on your router/ setup, most likely you'll have to either do a port forwarding, or directly place the Ubuntu Server on the DMZ.

And then, you have to setup on your Ubuntu Server box the necessary programs to receive email, and the other program to store and deliver it when a user connects to your Ubuntu Server to download it.
For these, you can check the link to the Ubuntu Server Guide I posted above.

All of this steps are related in order to get an email server up and running, but you can start working on most of them at the same time.
The way you can setup the necessary software on your Ubuntu Server depends, you can do everything from the command line, or you can install, for instance, [Webmin](http://www.webmin.com/), or the one you linked, ISPConfig, and do it using a webfront.

---

### Post by kustomjs on 2009-06-18
if you use godaddy for your domain register use there domain name and point your ip address to the domain and make sure you do MX and SPF records and CNAME records. most people tell you have to mess with the dns that isnt true I was able to get 2 email servers with out messing around with dns.

only thing you need to do is point your IP at host, create spf record and a cname record and noting for dns.

also you can create a working email server with Dovecot+Postfix+Mysql+Webmin. with out configuring alot of software to get a working email server.

---

### Post by jasonsjunk on 2009-06-18
I tried running a mail server from home the biggest difficulty you will run into is that most spam blockers especially the ones used by big corporations, yahoo, google, hotmail etc will automatically send all mail from your server to the spam box or they won't accept them at all.  The primary reason for this is rdns (reverse dns)  Most ISP's won't provide you with an rdns so that is resolves to your domain name.  Regular dns translates your domain name to an ip address rdns translates an ip address to a domain name/s.  

By default the ip addresses used by residential ISP's are flagged by many blacklists because it is rare for port 25 to be open on residential systems.  The reason these ips are blacklisted is to prevent open relays from improperly configured or insecure mail servers that spammers love to hijack and use them to do thier bidding.  

In addition to rdns you also need to install domain keys if you want to send mail to yahoo and hotmail email addresses.  You can find more information on this on Yahoo.  

With all of this working against me despite having a properly setup e-mail server with that was verified as secure the rdns is what got me.  I gave up and ended up routing all of the email for my domains through Google using Google Apps, it works flawlessly, I never have to worry about my mail server going down and missing e-mails, and they take care of spam filterting for me.  Best part about this is it is free!

Here are some links on what I am talking about...
[http://www.likoma.com/using-google-apps-and-gmail-for-youyourdomaincom/](http://www.likoma.com/using-google-apps-and-gmail-for-youyourdomaincom/)
[http://www.internetbusinesspath.com/ecommerce/setup-your-business-emails-using-google-apps](http://www.internetbusinesspath.com/ecommerce/setup-your-business-emails-using-google-apps)

In the end I learned alot about setting up a mail server which was good educationally but it wasn't worth the headaches trying to work  around all of the issues encountered running a mail server out of my home.  I still run the websites from home but I let Google take care of the mail for me.

---

### Post by LepeKaname on 2009-06-18
> **jasonsjunk said:**
> The primary reason for this is rdns (reverse dns)  Most ISP's won't provide you with an rdns so that is resolves to your domain name.  Regular dns translates your domain name to an ip address rdns translates an ip address to a domain name/s. 
...
I gave up and ended up routing all of the email for my domains through Google using Google Apps, it works flawlessly, I never have to worry about my mail server going down and missing e-mails, and they take care of spam filterting for me.  Best part about this is it is free!

I Agree with JasonsJunk... RDNS are the most difficult part. To explain it in other words, normally you can use several domains pointing to the same IP address, but the RDNS its one IP address pointing to only (and no more than) one domain name. This is required for security reasons and that is why google, yahoo, etc. will send you mails to the JUNK folder if you can't set the RDNS. 

For my personal use, I also have a Google Apps account and its very convenient. I also suggest to go with it if you don't really need anything pro.

---

### Post by hmx_ryan on 2009-06-18
Wow, you guys are way over my league... Your so great... I think I need to do some reading on setting up a private domain with my personal web and email server... I just spoke to our ISP, and he confirms to me that the SMTP Protocol was not Blocked... This is a Good news right?

I'm really confused now, I thought its an easy task to put up my PLAN... Guys, please help me more, don't worry, I'll try my best to cope up...

Anyway, I Wanted to put up my OWN Domain Server which would cater my Web Site along with my EMail Server... my Question is, How am I going to do that? Any prerequisites that I need? I do have now a Stable and Static Ip Address from my ISP... I do have two server box here at home... please, what else do I need to know...

Also, I would like o know on how I could set up an RDNS... Can I do that with my own Domain Server?

---

### Post by kustomjs on 2009-06-18
man I don't understand why everybody saying about dns when you really don't need dns for email server all you need is:

CNAME, SPF Records, Static IP from your ISP and use your DNS from the register you got your domain name from say like (godaddy, register.com or any register site)

trust me I know what I am talking about because I already setup 2 working email servers on residential line.

the key is having CNAME, SPF Records and MX records pointing to your static IP.

also on spam filtering you need to setup spamassassin.

also its best to have email server separated from your web server meaning you will have port 8080 open also. because if you don't your webserver and email server apart might not work as well like its post to.

---

### Post by hictio on 2009-06-18
> **kustomjs said:**
> man I don't understand why everybody saying about dns when you really don't need dns for email server all you need is:

CNAME, SPF Records, Static IP from your ISP and use your DNS from the register you got your domain name from say like (godaddy, register.com or any register site)

trust me I know what I am talking about because I already setup 2 working email servers on residential line.

the key is having CNAME, SPF Records and MX records pointing to your static IP.

also on spam filtering you need to setup spamassassin.

also its best to have email server separated from your web server meaning you will have port 8080 open also. because if you don't your webserver and email server apart might not work as well like its post to.

And where would you setup the "CNAME, SPF Records and MX records" if not on a DNS?
Granted, you don't have to have your own DNS server, but you need one if you want to have email, specially if your email server is for a domain, and you want it to receive emails routed over the internet.

---

### Post by kustomjs on 2009-06-18
like I said you dont need a dns just use the registers domain name and godaddy information:

You will need to add an “A” record at GoDaddy for mail.yourdomain.com -> your static ip from your ISP

 

[http://help.godaddy.com/article/681](http://help.godaddy.com/article/681)

 

Creating SPF record

[http://help.godaddy.com/article/3047](http://help.godaddy.com/article/3047)

 

A SPF record basically tells other mail servers, what servers are authorized to send mail for your domain.

---

### Post by hmx_ryan on 2009-06-18
Based on the information that you guys share, in order for me to create my own web site in my own server, I need to register my domain? If yes, where could I do that? Does it cost that much?

---

### Post by jasonsjunk on 2009-06-19
DNS isn't the problem you can manage that from where ever you registered your domain name I use Go Daddy myself.  I have had a working e-mail server but I never could get around the spam blocker/blacklist issues I mentioned in my earlier post.  Ask your ISP if they will provide you with an RDNS record that associates your IP address to your domain name.  Forward DNS )regular DNS translates your domain name to an IP address but if you do the search in reverse by just typing in the IP address it will point to your ISP not your domain name.  

Trust me on this one the Google Apps is the easiest most pain free solution for this.  I don't have to run a DNS server out of my house I just run my webserver and use Go-Daddy for DNS.  This setup is easy and headache free.

---

### Post by kustomjs on 2009-06-19
just PM me and I will help you setup it up. like I was saying before there no need for RDNS or any type of DNS just use your registers dns.

also for domain name go with godaddy they are about the cheapest you can go with.

---

### Post by windependence on 2009-06-19
> **jasonsjunk said:**
> DNS isn't the problem you can manage that from where ever you registered your domain name I use Go Daddy myself.  I have had a working e-mail server but I never could get around the spam blocker/blacklist issues I mentioned in my earlier post.  Ask your ISP if they will provide you with an RDNS record that associates your IP address to your domain name.  Forward DNS )regular DNS translates your domain name to an IP address but if you do the search in reverse by just typing in the IP address it will point to your ISP not your domain name.  

Trust me on this one the Google Apps is the easiest most pain free solution for this.  I don't have to run a DNS server out of my house I just run my webserver and use Go-Daddy for DNS.  This setup is easy and headache free.

You need to have your connection provider set up the RDNS. For example, I use Godaddy also, and I have my regular DNS set up there. My RDNS is set up with Qwest since they provide my internet connection as well as my IP addresses. Really, the only way to do this right is to use an internet provider that isn't a jerk like Comcast. You should try SpeakEasy or someone like that who will provide you with a block of IP addresses and then you are good to go. In that case, you would ask SpeakEasy to set up RDNS for your IPs and then set up the rest of your DNS through GoDaddy. It's not that hard, but trying to do it with a dynamic IP is useless. No-ip provides a service where you can use a dynamic IP and it works good. basically they provide you with a static connection that points to your dyanamic IP.

-Tim

---

### Post by jasonsjunk on 2009-06-20
> **windependence said:**
> You need to have your connection provider set up the RDNS. For example, I use Godaddy also, and I have my regular DNS set up there. My RDNS is set up with Qwest since they provide my internet connection as well as my IP addresses. Really, the only way to do this right is to use an internet provider that isn't a jerk like Comcast. You should try SpeakEasy or someone like that who will provide you with a block of IP addresses and then you are good to go. In that case, you would ask SpeakEasy to set up RDNS for your IPs and then set up the rest of your DNS through GoDaddy. It's not that hard, but trying to do it with a dynamic IP is useless. No-ip provides a service where you can use a dynamic IP and it works good. basically they provide you with a static connection that points to your dyanamic IP.

-Tim

Thats good to know about Qwest, my ISP Embarq won't do it for me unless I go for a full fledged business account which would simply cost too much.  

I did want to clarify something to everyone that has been reading this post, you can set up an email server to receive mail very easily the issues I was talking about with RDNS come into play when you are trying to send mail from your home e-mail server.

---

### Post by kustomjs on 2009-06-20
My ISP is using Qwest for there DNS. but like I said you can use your registers DNS servers.

if you want a good DNS use:

205.171.2.65
205.171.3.65

[http://dns.arl.qwestip.net/new_resolver_settings.html](http://dns.arl.qwestip.net/new_resolver_settings.html)

---

