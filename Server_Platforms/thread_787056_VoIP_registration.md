---
title: "VoIP registration"
date: 2008-05-08
forum: Server Platforms
---

### Post by Rick Z on 2008-05-08
Hi community,

What's the step of setting up a voip server/service using ubuntu.  I saw many post and many tutorial over internet, but I am not sure the very first step and wondering if anyone can help me out.

After install Asterisk or any other opensource, how do I get the phone number?  Do I register with the voip provider?  So that they assign me a phone number and I configure it with the Asterisk?

thanks.

---

### Post by tamoneya on 2008-05-08
I am looking into building a large asterisk system this summer and what i can tell there are a couple options.  
This is how I understand it at the moment:  The method you mentioned is one option but I dont know yet who the best voip providers are.  The other way is you can stick a couple of modems into the computer and you then distribute a handful of phonelines to many users.

---

### Post by songshu on 2008-05-08
asterisk is a beast.

i'm not saying its difficult but you could compare it to a 50.000 Euro enterprise telephone system and you basically become a provider so there are some more things to consider.

this is fine offcourse if that is what you need and want.
if you want just 1 or 2 voip numbers then skype or ekiga might be a more suitable choice.

---

### Post by Rick Z on 2008-05-09
Hi guys, thanks for the respond.

@tamoneya - please (please) keep me update how you actually setup your large VoIP system.  Also... What are the essential hardware components for the VoIP system using Asterisk?  Lastly, how can I configure “couple of modems into the computer and then distribute a handful of phone lines to many users”?  Where can I get the real land line number(s)?

@songshu – I know that Asterisk is a beast and just reading upon the history of Asterisk, it inspire me to learn even more…  telephone system is still crucial for many business.  I know I can just purchase a [http://www.digium.com/en/products/](http://www.digium.com/en/products/) and deploy it with Digium’s support, but I want to learn!!!  Some of my friends want to start a daycare/cram school in foreign country so they ask me to support/setup a server for their school.  Of course, telephone system is one of the services they need and I am hoping to utilize open source for their needs.

My goal is to setup a 10 – 20 telephone system using Asterisk…  Please help me out.

R

---

### Post by songshu on 2008-05-09
i'm planning to deploy it as well, guess i'm not alone..actually its the next one on my list
[http://songshu.org/doku/doku.php](http://songshu.org/doku/doku.php)

on the link above i keep my notes and would not mind to see yours either.


as far as i inderstood, 
1 - if you want to plug an oldfashioned pstn telephone line in to your computer you would need something like this
[http://www.digium.com/en/products/digital/](http://www.digium.com/en/products/digital/)

i guess the digium cards are recomended, but not the cheapest either

2 - you could actually go without a real telephone line and use a voip service provider, depending on your location wich one to choose but there seem to be plentu of those nowadays.

as far as i know, they charge a little less for the costs per minute but according to some the reliability is a little less then the oldfashioned way.
your results may vary

3 - if you say foreign country, you might want to add a second asterisk server.

like so

normal handtelephone--asterisklocationA--------asterisklocationB--connect to telephoneprovider

this would depend on the international calling rates offcourse

---

### Post by Rick Z on 2008-05-09
@ songshu,

Thank you so much for sharing your documentation with me.  I really need to document what I’ve been doing.

Yes, the price of the hardware isn’t cheap, but if this helps us save money in the long run I would purchase it.  

I think this is going to be the temporary solution for the cram school that setup in foreign country…  We probably end up setup skype (or any other provider) to placing international calls.  As for as for the local (foreign country) telephone system, I need find out what local landline is offering.  I hope VoIP (Asterisk) is feasible.  But I still want to explorer to Asterisk!!!

R

---

### Post by songshu on 2008-05-09
gaining knowledge is always feasible ;)

wich country's are you talking about by the way?

---

### Post by Rick Z on 2008-05-09
We are looking at 3 places.  Japan, China or Taiwan.  Mostly likely to be in Taiwan, but our plan may change.

---

### Post by songshu on 2008-05-09
cool,

the reason i'm interested is cause i want to set it up for in between offices europe-china.

definetely keep me posted ;)

---

### Post by tamoneya on 2008-05-09
> **Rick Z said:**
> Hi guys, thanks for the respond.

@tamoneya - please (please) keep me update how you actually setup your large VoIP system.  Also... What are the essential hardware components for the VoIP system using Asterisk?  Lastly, how can I configure &#8220;couple of modems into the computer and then distribute a handful of phone lines to many users&#8221;?  Where can I get the real land line number(s)?

@songshu &#8211; I know that Asterisk is a beast and just reading upon the history of Asterisk, it inspire me to learn even more&#8230;  telephone system is still crucial for many business.  I know I can just purchase a [http://www.digium.com/en/products/](http://www.digium.com/en/products/) and deploy it with Digium&#8217;s support, but I want to learn!!!  Some of my friends want to start a daycare/cram school in foreign country so they ask me to support/setup a server for their school.  Of course, telephone system is one of the services they need and I am hoping to utilize open source for their needs.

My goal is to setup a 10 &#8211; 20 telephone system using Asterisk&#8230;  Please help me out.

R

I will keep you updated bu unfortunately it is not ultimately my choice when it comes to which server OS to use.  Currently it is about 50-50 between asterisk and Microsoft Communications Server.  I personally am pulling for asterisk but I think they already have MCS installed for other purposes and it may be better to just add on to that.  MCS's system requirements however are HUGE.  they want something like 3.4 GHz dual core with 2 GB ram and a 15K SCSI RAID 10.  Compare this to asterisk which need: a 486 processor and at least 128 MB of RAM.  I dont know what microsft was thinking.

---

### Post by Rick Z on 2008-05-09
Just a little update...  I found this link about asterisk setup with Internet Phone Company. 
[http://www.linux.com/articles/52030?tid=104&tid=132](http://www.linux.com/articles/52030?tid=104&tid=132)  

R

---

