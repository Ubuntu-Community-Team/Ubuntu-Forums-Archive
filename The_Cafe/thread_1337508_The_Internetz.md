---
title: "The Internetz"
date: 2009-11-25
forum: The Cafe
---

### Post by whiskeylover on 2009-11-25
Aren't ISPs dictating the way people should use the Internet these days? Like, they block common server ports and stuff. I once posted a question of Verizon's forums asking if their FiOS blocks 80 and 21... and that it shouldn't be blocked. I got chewed out just for asking that. The customers were like "Why do you need 80 and 22?," "Get a business account," "Because of people like you, the speed of our connections goes down"... blah blah blah. Isn't this redefining the meaning of the Internet? Isn't internet supposed to be bidirectional, instead of WWW download only? I mean I understand that some people misuse their internet connection by hosting servers. But the same is true for extreme downloaders. 

My two cents.

---

### Post by earthpigg on 2009-11-25
for personal use of port 22, i am assuming you want ssh?

don't use port 22 :D

port 22 is the popular ***convention*** for ssh, not the ***requirement***.

```
[chris: ~]$ cat /etc/ssh/sshd_config | grep Port
Port 22222
```

so, to connect...

```
ssh -p 22222 user@domain
```

what i actually use is a 5-digit number that is easy for me to remember due to personal meaning to me.

you can also use an alias to make things easy...

```
[chris: ~]$ cat .bashrc | grep callmyserver
alias callmyserver='ssh -X -p 22222 user@domain'
```

for a website that you and only you plan to use? same. don't use port 80. use port 8000 or something.

[http://123.123.123.123:8000/](http://123.123.123.123:8000/)

and tinyurl.com it for extra laziness.

---

### Post by earthpigg on 2009-11-25
and if you are using ssh and a webserver for more than just you and your household and thus must use the standard conventional ports... then perhaps getting a business account ***would*** be the correct thing for you to do?

---

### Post by whiskeylover on 2009-11-25
Well, what if I want to host my personal webserver with, say, a picture gallary? Not exactly a business venture, but I want my friends to be able to get to it without using the :8080 hack.

---

### Post by earthpigg on 2009-11-25
> **whiskeylover said:**
> Well, what if I want to host my personal webserver with, say, a picture gallary? Not exactly a business venture, but I want my friends to be able to get to it without using the :8080 hack.

i think [these guys]("http://www.dyndns.com/") will provide that service for free - and you can set it up to still work even if you have a dynamic IP address.

i have no idea what your ISP will or will not do if they find out.

i agree with what you are saying about [Net Neutrality]("http://en.wikipedia.org/wiki/Net_neutrality"), btw, and i think you will find that you are mostly 'preaching to the choir', as they say, by bringing this subject up on ubuntuforums.org...

...as Linux users, i think we pretty much ***all*** (or nearly all) want to get the absolute most possible out of our computers and every dollar we spend on related services. :D

---

### Post by RabbitWho on 2009-11-25
[http://xkcd.com/181/](http://xkcd.com/181/)
Why do people do this? I don't understand.

---

### Post by whiskeylover on 2009-11-25
Everybody knows the correct term is "The Tubes". Notice the capitalized Ts.

---

### Post by ZankerH on 2009-11-25
> **whiskeylover said:**
> I mean I understand that some people misuse their internet connection by hosting servers. But the same is true for extreme downloaders.

How the hell are you "misusing" your connection by running a server? I pay for an "unlimited" internet connection, so I make sure I've got it running at full speed all the time - if there's nothing else, I'll just seed or re-download random torrents. Unless you've got an incompetent ISP that can't provide what they sold you, that shouldn't be a problem.

Also, what the hell, ssh? That hardly uses any bandwidth at all unless you move huge files around - but then again, the same can be said for any file server. 

I feel sad for the people chained to ISPs who limit what you can do with your connection.

---

### Post by Frak on 2009-11-25
Want more access? Buy a plan that gives you unlimited use. AT&T just requires me to call them and sign an extra contract that says I won't use port :80, :21, and :22 for malicious purposes. You can use :22 to bypass international blocks. Say you want to use the BBC iPlayer in the US, one of the best ways is to use :22 through SSH.

---

### Post by koenn on 2009-11-25
> **whiskeylover said:**
> Aren't ISPs dictating the way people should use the Internet these days? Like, they block common server ports and stuff. ... Isn't this redefining the meaning of the Internet? Isn't internet supposed to be bidirectional, instead of WWW download only?

Simple answer:
Your ISP provides you a service, i.e. internet access, on known terms and conditions, for a given price.
If the conditions don't suit your need, get a different deal, possibly with a different provider. 

More complex answer : 
their prices and offerings are probably based on a number of categories of expected use, and their network's capacity in terms of throughput. They have to make it work, so they te'll yu how it's going to work. 


No, they're not redefining the internet. The defined what sort of acess to it you have - or you defined what sort of access you were willing to pay for.

---

### Post by whiskeylover on 2009-11-25
> **ZankerH said:**
> 
I feel sad for the people chained to ISPs who limit what you can do with your connection.

Unless you're on a university network, almost all ISPs put a cap on their "unlimited" bandwidths. Its usually huge (a few hundred gigs), but its there... atleast in the US.

---

### Post by Frak on 2009-11-25
> **whiskeylover said:**
> Unless you're on a university network, almost all ISPs put a cap on their "unlimited" bandwidths. Its usually huge (a few hundred gigs), but its there... atleast in the US.
I downloaded 330GB within one month, no cap. This being on AT&T, one of the largest ISPs.

---

### Post by doas777 on 2009-11-25
I fully support your premise, but those ports are blocked to prevent hackers from scanning them. it's probably to prevent the scans from taking bandwidth rather than to protect us though. it probably also protects the web/ssh interfaces on all their networking kit as well.

---

### Post by oldsoundguy on 2009-11-25
When you sign up for service, you have an EULA that you OK.  MOST providers will include "not to be used for server traffic" or similar in their HOME usage agreement.  If you want to run a server, you get a commercial account.  Simple as that.
There are far more users assigned to a home type node than a commercial node.  When some jerk decides to run a server on a home node, they are stealing bandwidth from every other PAYING customer.

Only if you have WIRELESS internet (such as Clear) can you run a server on your location without damaging the on line traffic of others.

---

### Post by t0p on 2009-11-25
> **Frak said:**
> I downloaded 330GB within one month, no cap. This being on AT&T, one of the largest ISPs.

Wow, you Americans are lucky.  In the UK, ISPs routinely offer "unlimited" internet packages, but in the small print they say the service is subject to a "fair use" policy that limits your "unlimited" service to a few gigs per month.

And this craziness is encouraged by our government.  Apparently, the law works such that the ISP can call it an "unlimited" service so long as the majority of users won't be affected by the actual limit.

Tell you what though, I'm sure I heard on a podcast that US ISPs do a similar trick.

---

### Post by RabbitWho on 2009-11-25
I was with a company called IOL who went out of business, they called their service "unlimited" they they sent us a letter saying we had exceeded our limit... which was funny because the top of the letter had "unlimited" written on it... There was no small print though so you could say they were doing it posthumously i guess... in the end they went bankrupt and we didn't have to pay it.. score

---

### Post by Thirtysixway on 2009-11-25
A lot of ISPs will block ports because they don't want you running servers and things that could make them somewhat liable.  If I'm running a torrent search engine off my machine at home, who's going to have to deal with it if I have illegal content? Comcast.

I would also imagine there's security involved, too.  Do a lot of ISPs block ports commonly used for mail servers? Yes.  It can help stop spam when people running windows become infected.

It's not that I agree with the ISP, I just see their side of things.  Comcast doesn't block 80 or 22, but I have changed my port 22 to something else to become more secure(ish).  I don't believe they should be able to tell you what you can and can't do online, although when it comes down to liability they have no choice but to try and save their asses.

(and I know Comcast has it in their terms of service that you're not allowed to use their connections to run servers or provide services to non-comcast users..)

---

### Post by dragos240 on 2009-11-25
I have comcast at home. It doesn't block any ports. I've been running an http server and an ssh server on it....

---

### Post by Frak on 2009-11-25
> **Thirtysixway said:**
> (and I know Comcast has it in their terms of service that you're not allowed to use their connections to run servers or provide services to non-comcast users..)

> **dragos240 said:**
> I have comcast at home. It doesn't block any ports. I've been running an http server and an ssh server on it....

Just wanted to put that there.

---

### Post by Thirtysixway on 2009-11-25
> **Frak said:**
> Just wanted to put that there.

Yes, they have it in their terms of service but they don't block any of the ports.  I also run an http server from home and I've yet to get a letter in the mail or have my account canceled.  It may just be one of those "see we told them it was bad" type of things.

---

### Post by Frak on 2009-11-25
> **Thirtysixway said:**
> Yes, they have it in their terms of service but they don't block any of the ports.  I also run an http server from home and I've yet to get a letter in the mail or have my account canceled.  It may just be one of those "see we told them it was bad" type of things.
It's hard to determine, at first, which requests are normal browser requests and which are requests to a server. They may find you, they may not, but I can tell you now that they don't know that you're doing it. Comcast is very prompt at stopping offenders.

---

### Post by Sporkman on 2009-11-25
> **earthpigg said:**
> and if you are using ssh and a webserver for more than just you and your household and thus must use the standard conventional ports... then perhaps getting a business account ***would*** be the correct thing for you to do?

Agreed. That's what I did - I got a business account, and am able to run anything on any port with no cumulative bandwidth limits.

---

### Post by Sin@Sin-Sacrifice on 2009-11-25
All corporate entities will do anything they can to trap you into their idealistic reality. That being said I also have a business account and supposedly have no limits but yet my bandwidth was cut in half in the last month (oh I will be contacting time warner once I ascertain that my tweaking hasn't been the issue), I was served a notice to stop hosting my friend's web site (which was thrown out by me and them once I talked to a sup), and they tried to accuse me of pirating software with my bandwidth... little did they know that I use open source and can't pirate it (yes they sent a rep and a cop to check). All corporate entities are social hackers and will do whatever they can to save a penny. As will you. The world's monetary system is a self-serving black hole.

---

### Post by Frak on 2009-11-26
> **Sin@Sin-Sacrifice said:**
> All corporate entities will do anything they can to trap you into their idealistic reality. That being said I also have a business account and supposedly have no limits but yet my bandwidth was cut in half in the last month (oh I will be contacting time warner once I ascertain that my tweaking hasn't been the issue), I was served a notice to stop hosting my friend's web site (which was thrown out by me and them once I talked to a sup), and they tried to accuse me of pirating software with my bandwidth... little did they know that I use open source and can't pirate it (yes they sent a rep and a cop to check). All corporate entities are social hackers and will do whatever they can to save a penny. As will you. The world's monetary system is a self-serving black hole.
Maybe they just don't want:

1. To be sued for actions caused on behalf of their own users, or
2. Their end of the infrastructure to come crashing down.

---

### Post by t0p on 2009-11-26
> **Thirtysixway said:**
> A lot of ISPs will block ports because they don't want you running servers and things that could make them somewhat liable.  If I'm running a torrent search engine off my machine at home, who's going to have to deal with it if I have illegal content? Comcast.


Nonsense.  The ["safe harbor"]("http://en.wikipedia.org/wiki/Online_Copyright_Infringement_Liability_Limitation_Act") principle indemnifies the ISP from liability for your copyright infringement.  The ISP does not need to stop users running servers just in case infringement happens.  If you infringe copyright and the rights-holder finds out, they send a takedown notice to you and the ISP; the ISP kills your service (and the rights-holder might tell you to pay them some money or they'll take you to court).  ISPs don't stop users  running servers "just in case" they violate the law.  

ISPs who ban users from running servers do it for bandwidth reasons; they want the users to pay extra.  That's it.

---

### Post by Frak on 2009-11-26
> **t0p said:**
> Nonsense.  The ["safe harbor"]("http://en.wikipedia.org/wiki/Online_Copyright_Infringement_Liability_Limitation_Act") principle indemnifies the ISP from liability for your copyright infringement.  The ISP does not need to stop users running servers just in case infringement happens.  If you infringe copyright and the rights-holder finds out, they send a takedown notice to you and the ISP; the ISP kills your service (and the rights-holder might tell you to pay them some money or they'll take you to court).  ISPs don't stop users  running servers "just in case" they violate the law.  

ISPs who ban users from running servers do it for bandwidth reasons; they want the users to pay extra.  That's it.
Yes, but if the user doesn't remove the information, and the ISP refuses to take down the user, then the ISP can be held liable in a court.

As for the pay extra part, yes and no. Are they doing it for the money? Yes. Are they doing it **just** for the money? No. To keep high bandwidth networks in peak condition, they are maintenanced more than residential blocks, and are kept in a condition to where services can still run while the networks are still operating. Besides that, fewer users can be run on a per block basis. To cope with the extra costs of maintenance, zero-downtime, and fewer users/block, the ISP raises the price. By using residential networks for medium-to-high-bandwidth services, you are robbing other subscribers of bandwidth (and in this case, service that they pay for), and going the cheap way out of buying the plan that was tailored to your operation.

---

### Post by quinnten83 on 2009-11-26
> **Frak said:**
> Want more access? Buy a plan that gives you unlimited use. AT&T just requires me to call them and sign an extra contract that says I won't use port :80, :21, and :22 for malicious purposes. You can use :22 to bypass international blocks. Say you want to use the BBC iPlayer in the US, one of the best ways is to use :22 through SSH.

How?
please send links to tutorials...

---

### Post by jacobs444 on 2009-11-26
semper STFU, i hate the marines. Anyway the answer is yes, they try to dictate what you do nowadays!

---

### Post by Frak on 2009-11-26
> **quinnten83 said:**
> How?
please send links to tutorials...
It's just using SSH to redirect traffic. You need to have an SSH account in an area that supports the BBC iPlayer.

---

