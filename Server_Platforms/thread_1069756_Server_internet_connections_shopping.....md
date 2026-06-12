---
title: "Server internet connections shopping...."
date: 2009-02-14
forum: Server Platforms
---

### Post by hockey97 on 2009-02-14
Hi, I been surfing the web.  I currently am trying to find the best deal with a quality service to provide a business graded internet service.

I want to host my own server from home. 


I just looked and talk to a rep at covad. They only offer me dsl and the cheapest is a 1.5 download and some kb for upload. For 69 bucks a month. Plus 10 bucks a month for 5 static ip addresses.

My dad was telling me that dsl is not good at all. He suggested me to look for broadband cable interent.


So I want to know what is the best. DSL? or Broad Band?


Also I am trying to find a service provider that will give me high speeds for less.

at least 8mb for download and 3mb for upload.

I currently have such a connection that is cheap.

Yet they don't allow servers and I got a dynamic ip address.


Is there any one I should check out?

Is business dsl any good?

I been searching for a provider for about a year now.

I found cogent the network provider for Google and yahoo etc.

Their cheapest is 1,000 bucks a month. I talked to a rep on the phone.

they suggested me to try version internet. I called them and I don't have their lines  by my house.

Yet their reps told me they only allow servers on the business package.

So I am still searching . I only found covad but they only offer business dsl to me. with speeds of 1.5mbs for download and some kb for upload.

is their anyone you can recommend me to check them out?

---

### Post by tubezninja on 2009-02-14
You're going to find a lot of variations in quality from one provider to another.  DSL isn't necessarily bad, and Cable isn't necessarily good.  Some of the common plusses and minues:


1. Typically, advertised incoming speeds are significantly faster on most larger cable systems than on DSL.  Additionally, incoming speeds on a DSL line decrease the farther you are from the central office, while this is largely not an issue with cable.

2. On the other hand, cable is shared bandwidth across a group of users, usually a city block or a cluster of city blocks. if a particular cable head end is crowded with high-bandwidth users, the whole group will see degraded performance.  This is less of an issue on DSL.

3. In **my** experience (and yours may vary), I've found that my cable ISP (Comcast) has more frequent outages, but these outages are typically brief, not lasting more than an 30 minutes to an hour or so.  With DSL, the service has remained up for very long periods of time, but, the one time it did go down, it was down for a few days before being fixed.


One other thing to consider here: How much extra is this going to cost you to get a business class connection in your home to host a server?  You might want to see what the cost difference is, and then check to see if maybe that money would be better spent on getting yourself a virtual private server somewhere.  That way you have yourself a server with root access, a linux distro of your choosing, and the reliability of the internet connection will be the host's problem, not yours.  Most of them are peered off multiple providers, and the reliability is very good.  And, if you mess up your install, clearing it out and starting over is a breeze.

If that $79 you're paying is JUST for the internet connection to the server, keep in mind that you can get yourself a decent VPS for the same price, or even a whole dedicated server in a datacenter somewhere.

---

### Post by hockey97 on 2009-02-14
well the datacenters in my area are expensive and they have restrictions on what I can do and can't.

THe virtial ones is cheaper but the ones I found have restrictions on what you can do and can't.

Like  e-mail. I seen many allow apache and web server type software. 

I don't find ones that allow you to use mail servers. I do seeo some that allow php and mysql.

I checked many but I haven't found one that has like very limited restrictions.

I really don't like the idea to use a service that I pay for that gives restrictions.

I also later down the road would like to sell domain names.

So I would rather look for a internet connection to do such a thing.

I found verizon to be the best so far on internet connections.

Just that I don't have any of their lines in my area.


the covad business grade seems too expensive. I mean I pay less with broadband with a 8mb download and a 3mb upload. which was 34 bucks plus 10 bucks for the upgrade so about 44 bucks which you will have to add the tax and other fees.


with covad a business graded dsl I would be getting 1.3mb download and 512kb upload.

for 69 bucks and if I need static ip address I have you pay 10 bucks and they will give me 5 static ip addresses.

My dad said he will pay one line for my server and keep the wowway line for home use.

so I need something that is good for me to start out on.


What is the difference between a residential grade internet and a business grade internet???

My told explain to me that business graded internet is just internet connections that have a higher priority to get fix then the residential ones.


So if the internet is down for some reason they will fix the business graded connections first before they fix the residental ones.

---

### Post by tubezninja on 2009-02-14
> **hockey97 said:**
> well the datacenters in my area are expensive and they have restrictions on what I can do and can't.
THe virtial ones is cheaper but the ones I found have restrictions on what you can do and can't.
Like  e-mail. I seen many allow apache and web server type software. 
I don't find ones that allow you to use mail servers. I do seeo some that allow php and mysql.
I checked many but I haven't found one that has like very limited restrictions.


Well, keep in mind you don't necessarily need the datacenter to be near you.  I have VPSes that are half a continent away, and they are no different to me than the ones i have running in the same state.

As for restrictions, there are quite a few that aren't so restricted.  VPSLink, tektonic, slicehost, and Linode are just the ones off the top of my head that allow anything so long as it's legal, isn't spam, and doesn't involve any malicious activity.  Tektonic doesn't permit running irc, but that's about it.

> What is the difference between a residential grade internet and a business grade internet???

The number one difference: Most residential broadband internet services expressly prohibit running servers of any kind.  Web, e-mail, all the restrictions you were worried about, are pretty much prohibited in most cases on residential service.  They are allowed on business plans though.

> My told explain to me that business graded internet is just internet connections that have a higher priority to get fix then the residential ones.

While that is true, many also block ports 80 and 25 as well as a few others, due to the restrictions I mentioned above.

---

### Post by jimv on 2009-02-14
What exactly are you wanting to do with the server anyway?

---

### Post by hockey97 on 2009-02-14
nevermind... I found a ISP cheap.  16mbs  download and 2mbs upload for just 74 bucks a month.

and a 8mbs download and a 1mb upload for 34 bucks a month.

They allow servers.


Well I want to host 2 websites with it. I also want to get into hosting my own domain names.

I heard that I can host my own domain names just have to pay a regsitar.

I am not fully sure on that but how I read about it was like I can pay a buck per year for a domain name registration and renewal. I would have to have a dns server to host the domain name.

Which I want to do that and hopefully provide a dns servers to people.

I firstly just want to host my own website and e-mail.

I then later would like to host my own domain.

Once I make enough money I plan to slowly get into an ISP business that is slowly.

I plan to keep expanding that are my overall goals.  Right now I am just at starting my website. I am still working on it and hope to soon launch it with my new ISP.

cause my current isp has policies against servers.


that is my plan.

---

### Post by hockey97 on 2009-02-14
> **scaredpoet said:**
> Well, keep in mind you don't necessarily need the datacenter to be near you.  I have VPSes that are half a continent away, and they are no different to me than the ones i have running in the same state.

As for restrictions, there are quite a few that aren't so restricted.  VPSLink, tektonic, slicehost, and Linode are just the ones off the top of my head that allow anything so long as it's legal, isn't spam, and doesn't involve any malicious activity.  Tektonic doesn't permit running irc, but that's about it.



The number one difference: Most residential broadband internet services expressly prohibit running servers of any kind.  Web, e-mail, all the restrictions you were worried about, are pretty much prohibited in most cases on residential service.  They are allowed on business plans though.



While that is true, many also block ports 80 and 25 as well as a few others, due to the restrictions I mentioned above.



Thanks for the explanation.  I can now fully understand the difference.

The weird thing is I have residential internet and yet they don't block port 80 or any ports.

They didn't even know I was running a server.

I was running my server for a while ... when I was working on my website.

I rand into problems when I was setting up my e-mail server. Aol and many big e-mail provideers rejects my e-mails do to blocks caused by my reverse name showing not my domain name.

So I was told to e-mail my ISP to fix the reverse record. While I e-mail them.

They gave me a policy thing in a response and said I better not have a server on their network else they can sue us.

So I replied saying no and now I currently don't turn it on unless I have to test something if my site works.

I checked with my ISP and the business graded internet does have restrictions. No server allowed.

So I am still going to switch. 


Thanks for the help.

---

### Post by netztier on 2009-02-14
> **hockey97 said:**
> nevermind... I found a ISP cheap.  16mbs  download and 2mbs upload for just 74 bucks a month.

and a 8mbs download and a 1mb upload for 34 bucks a month.


You intend to serve your customers off a 1Mbps or 2Mbps upstream? They're going to be complaining, make no mistake.

Did you count in the hardware you have to buy, the electricity to run it, how to cool it's environment, have UPS for server, network equipment and air con? I think you'll be better off getting what is called a "root server" by the hosters.

Basically a machine you can do whatever you want with - be it a virtual one (like provided by KVM or VMware ESX) or an actual physical machine. 

You can install almost any OS you like, run a DNS server on it and host your own domain names, you can run apache, postfix, sendmail etc on it and host as many web and mail sites as you want. 

And it's going to be connected to the Internet at speeds you'd never be able to afford at home, and it doesn't matter where you are nor where the machine is, it could be on the other side of the globe. All you need to maintain it is SSH and a web browser.

Buddies of mine just recently got such a contract with actual dedicated hardware for EUR 49.-/month - that's USD 63.- And no hassle with old hardware, dead UPS batteries just when you need them, old harddisks giving up the ghost etc...

regards

Marc

---

### Post by Go_Big_Blue on 2009-02-14
> **hockey97 said:**
> nevermind... I found a ISP cheap.  16mbs  download and 2mbs upload for just 74 bucks a month.

and a 8mbs download and a 1mb upload for 34 bucks a month.

They allow servers.


If you don't mind sharing, what company did you find that with?  Also, are they providing you with a router?  What geographical area do you live in because I am looking at getting a full pipe T1 for my business.  The cheapest I could get was $299, and I live just west of Atlanta, GA.

---

### Post by hockey97 on 2009-02-14
ya, We have AC. My dad is an electrical engineer. He can build a power backup system.

I will give him hand.

Currently right now I just want to host 2 sites and my own domain names.

that is it. When I get the internet connection. I also have about 5 gigs of space for free hosting on that ISP server.

So I plan to put my php scripts that when my server is down for any reason it will switch the connections settings etc and display my pages hosted on that ISP.

It will just be a message saying that we are down.

I don't plan to have a heavy load of traffic right now. 

So I was told that this connection is good enough to start off.

---

### Post by hockey97 on 2009-03-07
> **Go_Big_Blue said:**
> If you don't mind sharing, what company did you find that with?  Also, are they providing you with a router?  What geographical area do you live in because I am looking at getting a full pipe T1 for my business.  The cheapest I could get was $299, and I live just west of Atlanta, GA.

I don't know if it's a T1 line I was told it is. 

here is the link : [http://business.comcast.com/internet/index.aspx](http://business.comcast.com/internet/index.aspx)

it's comcast. I live in michigan area.

I don't know if their in your area.

but just passing this on just in case anyone is looking  for such info.

For me looking for internet is a pain. I tried caviler and they rob us.

They promised a 30 day deal where if I am not happy within 30 days I can cancel with no bill  need to pay.


So on the first day of services I checked the speeds. I was supposed to be 8mb for download and upload. 

I got 1.5mb download and 256k download. I  The next day my dad called in and canceled .

Then they shut off our phone and internet services from them. 

So we had no phone operating  in 2 weeks. 

So we get our first bill... my dad is stupid.. he is very nice person so he decides to pay the bill.. the first one.

Then a month later we got another bill which is more expensive and they added late payments fee meaning we didn't pay our last bill and now we are getting overcharged.

My dad called them he was put on hold for an hour he hung up and then wrote a e-mail to them.

They never replied and this is what we are facing currently.


I am thinking to go with comcast since they have a retail store right in my neighborhood. Not far.

---

### Post by windependence on 2009-03-07
> **Go_Big_Blue said:**
> If you don't mind sharing, what company did you find that with?  Also, are they providing you with a router?  What geographical area do you live in because I am looking at getting a full pipe T1 for my business.  The cheapest I could get was $299, and I live just west of Atlanta, GA.

Try [www.speakeasy.net](www.speakeasy.net). Very good Linux friendly company. Been around for years. You can get a 3mbs symmetrical (down AND up) line for $380 a month. T1s are even cheaper and it's a dedicated connection with all the normal benefits of a commercial T1 line.

PM me if you are interested and I can give you the name and number of my private rep.

-Tim

---

### Post by windependence on 2009-03-07
> **hockey97 said:**
> I don't know if it's a T1 line I was told it is. 

here is the link : [http://business.comcast.com/internet/index.aspx](http://business.comcast.com/internet/index.aspx)

it's comcast. I live in michigan area.

I don't know if their in your area.

but just passing this on just in case anyone is looking  for such info.

For me looking for internet is a pain. I tried caviler and they rob us.

They promised a 30 day deal where if I am not happy within 30 days I can cancel with no bill  need to pay.


So on the first day of services I checked the speeds. I was supposed to be 8mb for download and upload. 

I got 1.5mb download and 256k download. I  The next day my dad called in and canceled .

Then they shut off our phone and internet services from them. 

So we had no phone operating  in 2 weeks. 

So we get our first bill... my dad is stupid.. he is very nice person so he decides to pay the bill.. the first one.

Then a month later we got another bill which is more expensive and they added late payments fee meaning we didn't pay our last bill and now we are getting overcharged.

My dad called them he was put on hold for an hour he hung up and then wrote a e-mail to them.

They never replied and this is what we are facing currently.


I am thinking to go with comcast since they have a retail store right in my neighborhood. Not far.

Comcast absolutely $uck$. 

PM me and I will give you contact info for my rep at speakeasy.net. Great service.

-Tim

---

