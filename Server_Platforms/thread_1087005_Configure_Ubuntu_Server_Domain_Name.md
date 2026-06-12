---
title: "Configure Ubuntu Server Domain Name"
date: 2009-03-04
forum: Server Platforms
---

### Post by richard.w.hall on 2009-03-04
Hi guys,

Now this is a very basic question, but I have never done this before and am finding it hard to work out what exactly I should be googling to solve it. 

I have an Ubuntu Server 8.10 vps and a domain name which I have just purchased. Now I thought the configuration of the domain name would be relatively straight forward...how wrong I was. Can anyone give me a step by step guide of how to set up my domain name, or point me to a site that will?

Do I need to install bind? A lot of the "guides" I have found seem to talk about setting up your own DNS. Is this required? I wouldnt have thought so, as the whole point of a domain name (as I see it) is to make life easier "finding" your machine. The name gets translated to an IP address by a DNS server. If the request can get to the DNS for translation...what is the point if it is located on your machine? So following that logic I am guessing that that is only required if you want to set up domains on your own LAN. But then again, you could just use the hosts file for that. 

I am assuming that somehow you need to provide your ip address and domain name to a DNS, but none of the "guides" I have tried to follow make this clear. 

Is a nameserver the same as a DNS? Im guessing it is not, but again I have struggled to get past the terminology of some of the guides which I think assume too much knowledge. 

I am a competent linux user and am not afraid of command line applications, I just have never done this before and as i said the info out there is a little difficult to get your head round....or even know if it is what you require.

Any help would be very much appreciated

---

### Post by capscrew on 2009-03-04
> **richard.w.hall said:**
> Hi guys,

Now this is a very basic question, but I have never done this before and am finding it hard to work out what exactly I should be googling to solve it. 

I have an Ubuntu Server 8.10 vps and a domain name which I have just purchased. Now I thought the configuration of the domain name would be relatively straight forward...how wrong I was. Can anyone give me a step by step guide of how to set up my domain name, or point me to a site that will?

Do I need to install bind? A lot of the "guides" I have found seem to talk about setting up your own DNS. Is this required? I wouldnt have thought so, as the whole point of a domain name (as I see it) is to make life easier "finding" your machine. The name gets translated to an IP address by a DNS server. If the request can get to the DNS for translation...what is the point if it is located on your machine? So following that logic I am guessing that that is only required if you want to set up domains on your own LAN. But then again, you could just use the hosts file for that. 

You are right.  You do not need local dns if you are only interested on Internet DNS (name resolution).

The use of hosts file vs a nameserver is more a matter centralized control.  If you have many hosts and want to resolve names from a centralized point then a DNS (Doman Name Services) nameserver is best.

> 

I am assuming that somehow you need to provide your ip address and domain name to a DNS, but none of the "guides" I have tried to follow make this clear. 

Is a nameserver the same as a DNS? Im guessing it is not, but again I have struggled to get past the terminology of some of the guides which I think assume too much knowledge.

DNS = Domain Name Services
Nameserver = sever to provide DNS 
> 
I am a competent linux user and am not afraid of command line applications, I just have never done this before and as i said the info out there is a little difficult to get your head round....or even know if it is what you require.

Any help would be very much appreciated

I would have the entity where you got the Domain name provide DNS hosting.  This way your domain name is available on the internet (Web).  If you want to provide DNS for your LAN you can do that yourself.

Bottom line is:
Pay for hosting DNS for the Internet
Run your own DNS for the LAN (optional (this can be via /etc/hosts files))

Edit: Here is a google search for "domain name hosting": [http://www.google.com/search?q=domain+name+hosting&btnG=Go%21]("http://www.google.com/search?q=domain+name+hosting&btnG=Go%21")

But I bet you already knew this.

---

### Post by richard.w.hall on 2009-03-04
That is what I have done. I have purchased a domain name from swvps.com and also a vps, and assummed that it would be a case of them linking my ip address to the domain name. It would appear not and they have told me to "google it" when I requested assistance. So any idea of what I need to do to use my domain name?

---

### Post by Maheriano on 2009-03-04
They actually told you that? Wow. Some places like GoDaddy will actually host your DNS Entry for you even if you only buy the domain name and not the hosting. Other places like the one you used will only sell the domain and you're on your own to install bind9 on your server to host your own DNS entry. So either install bind9 and figure it out or transfer your domain to a place like GoDaddy.

---

### Post by capscrew on 2009-03-04
Nope.  They don't need an address from you.  Your digital "real estate" is at their site.  They use the name you select to point to space on one of their servers.

Here is the instructions to log in. [http://support.swvps.com/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=62]("http://support.swvps.com/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=62")

---

### Post by capscrew on 2009-03-04
> **Maheriano said:**
> They actually told you that? Wow. Some places like GoDaddy will actually host your DNS Entry for you even if you only buy the domain name and not the hosting. Other places like the one you used will only sell the domain and you're on your own to install bind9 on your server to host your own DNS entry. So either install bind9 and figure it out or transfer your domain to a place like GoDaddy.

Maheriano,

You would think that they would be a little more specific, but I believe that the OP and SWVPS are not quite on the same page.

SWVPS sells **virtual** hosting.  Not DNS services per se.  I think the OP has purchased a package that provides space on SWVPS's server and DNS services to that servers IP address.

---

### Post by richard.w.hall on 2009-03-04
OK, all I am looking for is a brief guide of what to do.  

"SWVPS sells virtual hosting. Not DNS services per se. I think the OP has purchased a package that provides space on SWVPS's server and DNS services to that servers IP address." - Correct...apart from the fact that I bought my domain name from them as well. 

You guys all seem to know what you are talking about so can any of you throw me a bone? I have my server, my ip address, my domain name which were all bought from swvps. So how do I get my domain name to work? Or...where can I find out how to do this. I can't imagine it is that hard to do it, but if you have never done it before it would appear it is not something you can just "figure out".

If you need any more info from me to help, then I will be more than happy to supply it.

Thanks again

---

### Post by capscrew on 2009-03-04
> **richard.w.hall said:**
> OK, all I am looking for is a brief guide of what to do.  

"SWVPS sells virtual hosting. Not DNS services per se. I think the OP has purchased a package that provides space on SWVPS's server and DNS services to that servers IP address." - Correct...apart from the fact that I bought my domain name from them as well. 

You guys all seem to know what you are talking about so can any of you throw me a bone? I have my server, my ip address, my domain name which were all bought from swvps. So how do I get my domain name to work? Or...where can I find out how to do this. I can't imagine it is that hard to do it, but if you have never done it before it would appear it is not something you can just "figure out".

If you need any more info from me to help, then I will be more than happy to supply it.

Thanks again

Did you get a login name and a password from swvps?  

The domain name may be working already.  What is the domain name?  How long ago did you get it?

---

### Post by richard.w.hall on 2009-03-04
"Did you get a login name and a password from swvps?

The domain name may be working already. What is the domain name? How long ago did you get it?" 

I have a login name and password...in fact I have a couple. One set for my account details and one set to access HyperVM. The domain name is rilhia.com and I purchased it a while ago.

It is a bit annoying how this has happened. When I originally purchased it I asked the question on their support site....how to do it. The support guy was a lot more helpful than the one I have been dealing with this time and set it up for me. I tried to get him to tell me how he did it, but once it was done he never responded. But it worked. Now I have been having trouble with issues on the original operating system (Centos 5.1) and decided to replace it with Ubuntu 8.10 (an option that HyperVM provides). Before doing this I tried to find out how this chap had set up my domain name, but couldnt. I assumed that I would be able to find the solution on google or by asking the swvps support again....and maybe find out how it was done. But no dice. 

So, I know the domain name is fine and registered....as it was up and running before. I just need to find how to configure my Ubuntu server to use it.

---

### Post by capscrew on 2009-03-04
> I just need to find how to configure my Ubuntu server to use it. 

This is not really a physical piece of hardware you own; correct?  I ask as most of the audience at this forum are assuming you own the box and have installed the Ubuntu server OS on it.  

What are you using to connect to the internet?  What are you using now? 

Have you tried to login to the new account?  The one using Ubuntu.  What happens?

---

### Post by richard.w.hall on 2009-03-04
"This is not really a physical piece of hardware you own; correct?" - Correct

"I ask as most of the audience at this forum are assuming you own the box and have installed the Ubuntu server OS on it." No, it is a virtual private server imaged with Ubuntu server 8.10. A very basic implementation. I have added mysql, apache, bugzilla (for a development project), svn (for the same development project) and can access all of these using the IP address.

"What are you using to connect to the internet? What are you using now?" - I am using either firefox. Sometimes use IE when using Vista and am also getting used to Chrome. I am using ssh to configure my vps and use putty for this.

"Have you tried to login to the new account? The one using Ubuntu. What happens? " - I can log in using HyperVM (via a browser), but I mainly use putty to get access to it. I can access the server using the ip address, but cannot using the domain name (rilhia.com).

---

### Post by capscrew on 2009-03-04
So you are really not far off.  Have you asked the hosting conpany to point the DNS servers they manage to the IP address of you Ubuntu server.

They are supposed to do it, not you.  It's part of the service.

The can add [www.rilhia.com](www.rilhia.com) too.

Edit:  BTW -- the Icon at the top of the editor is for quotes.

---

### Post by richard.w.hall on 2009-03-04
"So you are really not far off. Have you asked the hosting conpany to point the DNS servers they manage to the IP address of you Ubuntu server.

They are suppose to do it not you. It's part of the service."

I would assume that as this domain name has been set up in the past for this ip address, that if that is all it would take it would still work. The IP address hasnt changed, neither has the domain. The only thing that has changed is the operating system on the box. This is why I am sure that there is something that needs to be done on the box itself....but what I havent a clue. I can't believe how much of a "black box" procedure this is turning out to be.

---

### Post by capscrew on 2009-03-04
Actually you have a few options.

Looking at your DNS registration:
```
>whois rilhia.com

Whois Server Version 2.0

Domain names in the .com and .net domains can now be registered
with many different competing registrars. Go to http://www.internic.net
for detailed information.

   Domain Name: RILHIA.COM
   Registrar: DIRECTI INTERNET SOLUTIONS PVT. LTD. D/B/A PUBLICDOMAINREGISTRY.COM
   Whois Server: whois.PublicDomainRegistry.com
   Referral URL: http://www.PublicDomainRegistry.com
   Name Server: NS1.RILHIA.COM
   Name Server: NS2.RILHIA.COM
   Status: ok
   Updated Date: 04-dec-2008
   Creation Date: 05-oct-2008
   Expiration Date: 05-oct-2009

```

Reveals that you have asked to host your own DNS
```
Name Server: NS1.RILHIA.COM
```

This means you will maintain your own DNS.  IMHO it's a PITA.

I would have SWVPS to host the DNS for you.

---

### Post by richard.w.hall on 2009-03-04
"This means you will maintain your own DNS. IMHO it's a PITA.

I would have SWVPS to host the DNS for you. "

To be honest I didnt get the option. I realise now just how little information they have given me. I am not a newbie to linux, just to web hosting. It doesnt usually take me long to figure stuff out, but this has been a bit of a nightmare. Also the lack of information coming from swvps has left me completely in the dark. 

Anyway, thanks for your help so far. I have picked up more from you than I have from several hours of googling. So I am guessing that I need to add DNS software to my server. This must have been what the swvps support chap did when he did it for me. It worked well enough, so I guess I will try that. Do you know of any decent DNS software for Ubuntu, and is there anything I should know before trying to configure it?

---

### Post by capscrew on 2009-03-04
> Do you know of any decent DNS software for Ubuntu, and is there anything I should know before trying to configure it?

A direct answer is BIND.  It is the standard.  It's complex for your simple needs.  We have a netadmin team at our data center that only handles DNS an networking.

If SWVPS set DNS up for you before, I wonder if they will do it again.

If not then I would look for a hosting company just for the DNS and domain registration.  You can try the name registrar you have now. See [http://publicdomainregistry.com/]("http://publicdomainregistry.com/")

Edit:  this looks like a good start on understanding BIND9 [http://www.madboa.com/geek/soho-bind/]("http://www.madboa.com/geek/soho-bind/")

Edit 2:  Remember to point your registration to the IP address of the DNS server as in:```
Name Server: NS1.RILHIA.COM  x.x.x.x
```

---

### Post by richard.w.hall on 2009-03-05
Capscrew, you are right...it isnt that straight forward is it. I think if I can dedicate a day to reading up on this (if I find some more material...thanks for the links you sent me)and configuring it, I may just crack it. But this raises the question, how is a non IT bod supposed to do this? Im a programmer/technical consultant, so I wasn't expecting anything to really slow me down that much. I can't believe that SWVPS are getting away with what I would say is false marketing. They imply that what they offer is "easy" to configure...which it certainly is not.

---

### Post by capscrew on 2009-03-05
> **richard.w.hall said:**
> ...I can't believe that SWVPS are getting away with what I would say is false marketing. They imply that what they offer is "easy" to configure...which it certainly is not.

Richard,

I think it's a matter of whom they are advertising to.  Their audience seems to be for the more technically oriented... for sure.

But...I have poked around in the HV demo and found that you can configure DNS via a GUI interface.  Edit:  [COLOR="Red"]**This is not really true!**[/COLOR].  The instructions are for Red Hat (CentOS) and will not work for Ubuntu.  Now you have a legit gripe.  I would talk to support about this.

Go to the HV Admin Page and under resources you will see "All Dns".  Click on that and you will see a tab for "Dns Config".  Read the instructions very carefully.  The references to "RHEL and "yum" are Red Hat specific.  Once again you need to get their support team to help you!

---

### Post by richard.w.hall on 2009-03-07
Success!! I just thought I would let you guys know how I did it as I know how frustrating it was not being able to find a solution. The solution I found was to use PowerDns. It took me about 10 minutes to set up using the following guide.....

[http://www.howtoforge.com/installing-powerdns-with-mysql-backend-and-poweradmin-on-ubuntu-8.10](http://www.howtoforge.com/installing-powerdns-with-mysql-backend-and-poweradmin-on-ubuntu-8.10)

I hope this helps a few people in the future. Thanks for your help by the way capscrew :-)

---

### Post by capscrew on 2009-03-07
This appears to be a very nice solution.  There is the added overhead of the mySQL database instead of flat files, but the GUI interface looks very nice.  I may try this out myself.

-Capscrew

---

### Post by mrsteveman1 on 2009-03-07
Unless you have a good reason to do so it is best to leave the DNS serving to a 3rd party, there are a few free ones around. We have used zoneedit for a LONG time with very good results.

---

