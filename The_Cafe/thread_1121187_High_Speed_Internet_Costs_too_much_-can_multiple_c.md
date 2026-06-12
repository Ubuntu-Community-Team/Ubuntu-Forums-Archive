---
title: "High Speed Internet Costs too much -can multiple computers use Dial Up?"
date: 2009-04-09
forum: The Cafe
---

### Post by EnglishSparrow on 2009-04-09
We have 6 computers in our house. Mine, the families, my laptop(that the family uses more than me), my sisters computer, my old laptop, and my apache server.

But, my fathers says that Comcast costs to much and he wants to get dial up, since he just needs the Internet for business, but what about everyone else in the house? He seems to not care....

And most importantly -I am running a project with several online friends, and the files are stored on my web server. They need to access the .iso files at random times. And I run 8 web sites from that server(it's an old debian box).


Is there a way to have a dial up modem that connects to an Ethernet router? 

Thanks!

---

### Post by Joeb454 on 2009-04-09
I'm not 100% sure that there is a way to do it, although even if there was, sharing dial-up between that many computers isn't feasible, it would be way to slow to actually do anything (literally)

---

### Post by Mokoma on 2009-04-09
> **EnglishSparrow said:**
> We have 6 computers in our house. Mine, the families, my laptop(that the family uses more than me), my sisters computer, my old laptop, and my apache server.

But, my fathers says that Comcast costs to much and he wants to get dial up, since he just needs the Internet for business, but what about everyone else in the house? He seems to not care....

And most importantly -I am running a project with several online friends, and the files are stored on my web server. They need to access the .iso files at random times. And I run 8 web sites from that server(it's an old debian box).


Is there a way to have a dial up modem that connects to an Ethernet router? 

Thanks!

lmao. dude your going down to 5.6kps at best unless it uses server side compression. any online projects are dead in the water with dial up

---

### Post by EnglishSparrow on 2009-04-09
I care about the speed -but if it does happen I would like to at least be able to chat with my friends with pidgin :(:(:(

---

### Post by Mokoma on 2009-04-09
> **EnglishSparrow said:**
> I care about the speed -but if it does happen I would like to at least be able to chat with my friends with pidgin :(:(:(

you can still use im, but dial up server access is NASTY

---

### Post by Kareeser on 2009-04-09
Internet Connection sharing in Windows. There's probably an alternative in Ubuntu.

Your upload is going to be messed around with. You need to find a new place to host your projec.t

---

### Post by speedwell68 on 2009-04-09
It is possible to share a dial up connection, I did it years ago in Windows when dial up is all we had.  I'd have no idea how to do it in Linux, but anything is possible.  But it would be so slow, I mean awful.  At best you are going to get is 5.6k a second, this thread alone would take 17 seconds to load.

---

### Post by Mokoma on 2009-04-09
> **speedwell68 said:**
> It is possible to share a dial up connection, I did it years ago in Windows when dial up is all we had.  I'd have no idea how to do it in Linux, but anything is possible.  But it would be so slow, I mean awful.  At best you are going to get is 5.6k a second, this thread alone would take 17 seconds to load.

if he gets a isp that uses server side compression, it would be more like 2 seconds

---

### Post by EnglishSparrow on 2009-04-09
He wants AOL.

---

### Post by EnglishSparrow on 2009-04-09
> **speedwell68 said:**
> It is possible to share a dial up connection, I did it years ago in Windows when dial up is all we had.  I'd have no idea how to do it in Linux, but anything is possible.  But it would be so slow, I mean awful.  At best you are going to get is 5.6k a second, this thread alone would take 17 seconds to load.

Is there some kind of dial up-ethernet adapter?

---

### Post by Mokoma on 2009-04-09
> **EnglishSparrow said:**
> He wants AOL.

noone wants ao***************************l. useless *************. seriously DO NOT GET AOL

---

### Post by Yvan300 on 2009-04-09
Just ask your dad to sing up with an isp that has a more reasonable price, because dial up by itself is a pain, and imagine dividing that bandwidth into 5 or 6. That's a no go :)

---

### Post by FrankT-Qc on 2009-04-09
Of course you can have many computer sharing your connection. You just need a router that has NAT (I have never seen a home router without NAT...). 

The only thing is you might have a hard time finding a home router that plugs into dial-up.

An option : Have one of you computers act as the router... An Ubuntu box can do this "finger in the nose". If you have a web server, you probably keep your box on all the time anyway...

here's a good starting point :

[https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

If you don't feel like playing with iptables, I think that Firestarter gets you there (or at least somewhere !) in a few clicks. 

About your limited connection... If you're going to share heavy stuff with your friends, have you considered using torrents ?

---

### Post by -grubby on 2009-04-09
Explain to your dad why dialup wouldn't work out, and then try to find a cheaper broadband ISP.

---

### Post by Shpongle on 2009-04-09
man look for a better cheaper isp seriously dial up  will slow things ridiculously, it will takes ages to do anything online!! , maybe your friends could pitch in and help foot the bill since your hosting in your house using your electricity and bandwidth. its just an idea but im sure theres another isp you could use! .

---

### Post by swoll1980 on 2009-04-09
> **EnglishSparrow said:**
> We have 6 computers in our house. Mine, the families, my laptop(that the family uses more than me), my sisters computer, my old laptop, and my apache server.

But, my fathers says that Comcast costs to much and he wants to get dial up, since he just needs the Internet for business, but what about everyone else in the house? He seems to not care....

And most importantly -I am running a project with several online friends, and the files are stored on my web server. They need to access the .iso files at random times. And I run 8 web sites from that server(it's an old debian box).


Is there a way to have a dial up modem that connects to an Ethernet router? 

Thanks!
Pay for the high speed yourself.

---

### Post by EnglishSparrow on 2009-04-09
He refuses to stick with comcast.....
I asked about going back to dsl and he said no.


But of course, we have to keep the beloved cable:mad:

So... The reason he wants to get AOL is so he can use multiple ip addresses to spoof ebay so he can have multiple accounts.

---

### Post by smartboyathome on 2009-04-09
> **EnglishSparrow said:**
> He wants AOL.

+1. AOL was actually the first internet connection I used, and it was pretty good. :popcorn: *hides in corner before he gets flamed*

---

### Post by Mokoma on 2009-04-09
huh where did my hack comment go?

---

### Post by EnglishSparrow on 2009-04-09
> **swoll1980 said:**
> Pay for the high speed yourself.

I don't have any money!

Maybe once I finish my novel.

But if I do that then I get to be in control... I like that lol.

Still, that will take a year to get published. Takes around 6 months just to get a reply from publisher :(

---

### Post by speedwell68 on 2009-04-09
> **EnglishSparrow said:**
> Is there some kind of dial up-ethernet adapter?

No, MS had this thing called 'Internet Connect Sharing'.  You could do it through your home network.  Basically computer A was connected to the web with a modem and computer B connected by sharing computer A's connection.  It was bloody slow TBH.

---

### Post by Mokoma on 2009-04-09
> **smartboyathome said:**
> +1. AOL was actually the first internet connection I used, and it was pretty good. :popcorn: *hides in corner before he gets flamed*

dude aol is utter hell on broadband, it constantly cuts out, slows down to virtually nothing. ive had to ring them over 200 times since january alone. i hate to think what there dial up is like now :S

---

### Post by s3a on 2009-04-09
**Firestarter** can share dial-up with a router. However, your internet will then be painfully slow but having been a dial-up user, I would advise that while you view one website u load one other website in another tab while you view the website so that you don't find yourself waiting for things to load. In addition, I recommend you only load one tab at a time while viewing another.

---

### Post by Kingsley on 2009-04-09
> **EnglishSparrow said:**
> He refuses to stick with comcast.....
I asked about going back to dsl and he said no.


But of course, we have to keep the beloved cable:mad:

So... The reason he wants to get AOL is so he can use multiple ip addresses to spoof ebay so he can have multiple accounts.
He wants multiple IP addresses? Just teach him how to proxy.

---

### Post by EnglishSparrow on 2009-04-09
With firestarter does the main computer have to be the router, or does it connect to the main router as it normally would, or would their be 2 ethernet cables involved?

---

### Post by EnglishSparrow on 2009-04-09
> **Kingsley said:**
> He wants multiple IP addresses? Just teach him how to proxy.

He says that if you use a proxy ebay will detect it and ban you.

---

### Post by Joeb454 on 2009-04-09
If you have multiple accounts, ebay would more than likely find out eventually.

---

### Post by Cybie257 on 2009-04-09
> **EnglishSparrow said:**
> We have 6 computers in our house. Mine, the families, my laptop(that the family uses more than me), my sisters computer, my old laptop, and my apache server.

But, my fathers says that Comcast costs to much and he wants to get dial up, since he just needs the Internet for business, but what about everyone else in the house? He seems to not care....

And most importantly -I am running a project with several online friends, and the files are stored on my web server. They need to access the .iso files at random times. And I run 8 web sites from that server(it's an old debian box).


Is there a way to have a dial up modem that connects to an Ethernet router? 

Thanks!


Call up Comcast. Many times they have given a price break to members threatening to cancel their service. Tell them that your dad is thinking about going to Dial-Up because of price. I'm sure they will do what they can to get as close to the price as possible to keep a customer these days. 

And... Dial-Up with 6 computers sharing... UGH. 

(Dial-Up) WWW = World Wide Wait

BTW, for the price of an ISP and the phone line, which I assume would be basically dedicated to the Internet, there are some low-speed (in today's terms) such as 1.5Mbps going for around $14.95-$19.95.

Not sure where you live, but I'm sure there is something that you can find cheaper rather than dial-up. 

-Cybie

---

### Post by EnglishSparrow on 2009-04-09
> **Cybie257 said:**
> Call up Comcast. Many times they have given a price break to members threatening to cancel their service. Tell them that your dad is thinking about going to Dial-Up because of price. I'm sure they will do what they can to get as close to the price as possible to keep a customer these days. 

And... Dial-Up with 6 computers sharing... UGH. 

(Dial-Up) WWW = World Wide Wait

BTW, for the price of an ISP and the phone line, which I assume would be basically dedicated to the Internet, there are some low-speed (in today's terms) such as 1.5Mbps going for around $14.95-$19.95.

Not sure where you live, but I'm sure there is something that you can find cheaper rather than dial-up. 

-Cybie

:lolflag: Do you know of any services that cheap in the USA?

1.5mbps I can deal with. We have 7mbps now.

---

### Post by collinp on 2009-04-09
Seriously, though, hosting anything on Dial-up or having multiple computers on dial-up is going to /kill/ your speed. Get a job, earn money for your internet.
Also, like Joeb454 said, if you have multiple accounts on Ebay, they will eventually find out. Plus, I dont much see the point in having multiple IP addresses /just/ for ebay.

---

### Post by Polygon on 2009-04-09
i use comcast. Our high speed connection is like 30 dollars a month...if you have 6 computers...i assume that that should be no problem......hell i could pay for high speed internet and i'm working minimum wage =P

---

### Post by pwnst*r on 2009-04-09
> **EnglishSparrow said:**
> We have 6 computers in our house. Mine, the families, my laptop(that the family uses more than me), my sisters computer, my old laptop, and my apache server.

But, my fathers says that Comcast costs to much and he wants to get dial up, since he just needs the Internet for business, but what about everyone else in the house? He seems to not care....

And most importantly -I am running a project with several online friends, and the files are stored on my web server. They need to access the .iso files at random times. And I run 8 web sites from that server(it's an old debian box).


Is there a way to have a dial up modem that connects to an Ethernet router? 

Thanks!

seriously.  i suggest one or two of you get a part time job if you want it that bad.

---

### Post by EnglishSparrow on 2009-04-09
Parents have no jobs at the moment(though they are writers, they haven't published anything yet).


And they won't let me get a job. My only option is to finish my book. 


Our comcast bill is $300 some how. Cable+Internet.

---

### Post by pwnst*r on 2009-04-09
> **EnglishSparrow said:**
> Parents have no jobs at the moment(though they are writers, they haven't published anything yet).


And they won't let me get a job. My only option is to finish my book. 


Our comcast bill is $300 some how. Cable+Internet.

if i had to choose, cable would be out. 

but, your 'rents have a legitimate beef to kill that bill with no income flowing.  sorry.

---

### Post by swoll1980 on 2009-04-09
> **EnglishSparrow said:**
> Parents have no jobs at the moment(though they are writers, they haven't published anything yet).


And they won't let me get a job. My only option is to finish my book. 


Our comcast bill is $300 some how. Cable+Internet.

No offense, but if your parents don't have jobs, and won't let you get a job, Internet speed is the least of your problems

---

### Post by EnglishSparrow on 2009-04-09
> **swoll1980 said:**
> No offense, but if your parents don't have jobs, and won't let you get a job, Internet speed is the least of your problems

Then what would you say my problem is, all knowing swoll?

---

### Post by EnglishSparrow on 2009-04-09
We are getting a bit off topic.


Is it possible to share AOL from a windows machine to the other machines running Linux?

---

### Post by pwnst*r on 2009-04-09
> **EnglishSparrow said:**
> Then what would you say my problem is, all knowing swoll?

he's being serious.  i'd be concerned about the roof over my head for one.  food is next.

---

### Post by swoll1980 on 2009-04-09
> **EnglishSparrow said:**
> We are getting a bit off topic.


Is it possible to share AOL from a windows machine to the other machines running Linux?

You can set something up with a crossed Ethernet cable, but you would have to be a doctor of computer sciences to configure it. And the speed would be so god awfully slow you could probably run to the server you were trying to pull data from before the computer could pull it up. Plus the cross cable is like $30 for 3 feet.

---

### Post by EnglishSparrow on 2009-04-09
> **pwnst*r said:**
> he's being serious.  i'd be concerned about the roof over my head for one.  food is next.

They have, um, what is it called when you get free money from other peoples taxes? :p

---

### Post by EnglishSparrow on 2009-04-09
> **swoll1980 said:**
> You can set something up with a crossed Ethernet cable, but you would have to be a doctor of computer sciences to configure it. And the speed would be so god awfully slow you could probably run to the server you were trying to pull data from before the computer could pull it up.

It's that slow now anyway :lolflag:

So your saying I would need 5 network cards in this machine?

I only have 2 pci slots.

I do have a P3 450mhz that runs debian well with 6 pci slots and an isa slot. That should work right? IPtables isn't that hard... But, isn't aol windoz only?

---

### Post by Onoskelis on 2009-04-09
> **EnglishSparrow said:**
> We are getting a bit off topic.


Is it possible to share AOL from a windows machine to the other machines running Linux?

High speed honestly doesn't cost that much.

I'm paying $37 a month for a 10 Mbit full duplex connection here in Vancouver. The ISP is Novusnow.

Don't go for big ISPs like Comcast. Try looking for smaller Telecom companies. They usually have much cheaper rates.

---

### Post by EnglishSparrow on 2009-04-09
> **Onoskelis said:**
> High speed honestly doesn't cost that much.

I'm paying $37 a month for a 10 Mbit full duplex connection here in Vancouver. The ISP is Novusnow.

Don't go for big ISPs like Comcast. Try looking for smaller Telecom companies. They usually have much cheaper rates.

I'm trying to find an isp that gives service that cheap in Pennsylvania.

I'll look into Novusnow.

---

### Post by collinp on 2009-04-09
> **EnglishSparrow said:**
> They have, um, what is it called when you get free money from other peoples taxes? :p

Social security? Seriously, though, with no cash flowing, I would be worrying about other things than your internet.

---

### Post by EnglishSparrow on 2009-04-09
Novusnow has excellent prices, but what from I see they are Canada only?


Too bad. Canada is just too great. ;)

---

### Post by swoll1980 on 2009-04-09
> **EnglishSparrow said:**
> It's that slow now anyway :lolflag:

So your saying I would need 5 network cards in this machine?

I only have 2 pci slots.

I do have a P3 450mhz that runs debian well with 6 pci slots and an isa slot. That should work right? IPtables isn't that hard... But, isn't aol windoz only?

Oh! you have 6 computers! I was thinking 2 for some reason. You would have to set up a box connect it to the modem then use it as a gateway. If you had a router you should only need one network adapter. You would still have to be a networking superstar to configure it. Way beyond my scope.

---

### Post by hiddensoul on 2009-04-09
Yes it is possible to run multiple computers over one dialup connection, I personally ran this way when I was living in country Australia nad only had access to satellite (To costly) or dial up. 

I would suggest setting up a box to act as your connection point and have it run something like smoothwall or ipcop.

These will let you run the machine as a firewall for the network you create as well as provide a caching proxy. What the proxy does is provide a local copy of webpages visited in say the last 10 days, If person B visits a page shortly after person A then the images etc dont have to be pulled of the internet they will stay on the proxy.

This speeds up pages that more then one person is using as well as speeding up pages that you go to all the time as they dont get a chance to be flushed

The proxy will check to see if the page has changed and if it has it will download the new content rather then using the proxy.

We had 5 computers running on one dial up connection yes it was slow, but with the right setup and some patience it can be done.

And both IPcop and Smoothwall are bootable linux cds that will take the donor PC and tur it in to a gateway, no real experience needed and you administer them from a webpage so you can run the gateway with no screen keyboard or mouse ie. Headless.

---

### Post by EnglishSparrow on 2009-04-09
> **swoll1980 said:**
> Oh! you have 6 computers! I was thinking 2 for some reason. You would have to set up a box connect it to the modem then use it as a gateway. If you had a router you should only need one network adapter. You would still have to be a networking superstar to configure it. Way beyond my scope.

I have a router :KS

So, I can setup the Windows machine as the main pc(the one with aol) and have it's ethernet adapter connected to the Router's input?

My little assumption:
[B]
AOL -->> WINDOWS -->> ROUTER -->> SAD USERS.[/B]

Is this correct?

---

### Post by Onoskelis on 2009-04-09
You could always just leech off your neighbor's wi-fi. :tongue:

I swear, in my neighborhood, there are at least 5 unsecure networks that anyone can just access. 

It leaves your own PC wide open to packet sniffing though.

---

### Post by swoll1980 on 2009-04-09
> **EnglishSparrow said:**
> I have a router :KS

So, I can setup the Windows machine as the main pc(the one with aol) and have it's ethernet adapter connected to the Router's input?

My little assumption:
[B]
AOL -->> WINDOWS -->> ROUTER -->> SAD USERS.[/B]

Is this correct?

Yeah, that's how it would work. It will work if it's configured correctly.

---

### Post by EnglishSparrow on 2009-04-09
> **hiddensoul said:**
> Yes it is possible to run multiple computers over one dialup connection, I personally ran this way when I was living in country Australia nad only had access to satellite (To costly) or dial up. 

I would suggest setting up a box to act as your connection point and have it run something like smoothwall or ipcop.

These will let you run the machine as a firewall for the network you create as well as provide a caching proxy. What the proxy does is provide a local copy of webpages visited in say the last 10 days, If person B visits a page shortly after person A then the images etc dont have to be pulled of the internet they will stay on the proxy.

This speeds up pages that more then one person is using as well as speeding up pages that you go to all the time as they dont get a chance to be flushed

The proxy will check to see if the page has changed and if it has it will download the new content rather then using the proxy.

We had 5 computers running on one dial up connection yes it was slow, but with the right setup and some patience it can be done.

The server is also a squid caching proxy! w00t...

---

### Post by EnglishSparrow on 2009-04-09
> **swoll1980 said:**
> Yeah, that's how it would work

Does AOL have the ability to share the connection?

It's going to be really funny if this does actually get setup like this and the windows box crashes... constantly...

---

### Post by swoll1980 on 2009-04-09
Ice cream is good

---

### Post by EnglishSparrow on 2009-04-09
> **swoll1980 said:**
> Someone already got an infraction for that one edit yours and I'll edit this no one will have to know ;)

Your the nicest admin I know so far...

---

### Post by swoll1980 on 2009-04-09
> **EnglishSparrow said:**
> Does AOL have the ability to share the connection?

It's going to be really funny if this does actually get setup like this and the windows box crashes... constantly...

AOL won't know. As far as it knows all the request will come from the gateway box

---

### Post by swoll1980 on 2009-04-09
> **EnglishSparrow said:**
> Your the nicest admin I know so far...

I'm not an admin I was just trying to save him some trouble. To late now though.

---

### Post by Dragonbite on 2009-04-10
> **EnglishSparrow said:**
> We have 6 computers in our house. Mine, the families, my laptop(that the family uses more than me), my sisters computer, my old laptop, and my apache server.

But, my fathers says that Comcast costs to much and he wants to get dial up, since he just needs the Internet for business, but what about everyone else in the house? He seems to not care....

And most importantly -I am running a project with several online friends, and the files are stored on my web server. They need to access the .iso files at random times. And I run 8 web sites from that server(it's an old debian box).


Is there a way to have a dial up modem that connects to an Ethernet router? 

Thanks!

I just recently moved from Dial-Up to DSL and I have to say going back the other way is going to hurt.

Cable (and DSL) has not only the speed advantage but the "always on" advantage of not having to manage dialing in and hanging up (I have only one phone line in the house).

IPCop does make routing/firewalling/etc. very easy and I saw some dial-up options listed which may make it easy to manage. I would look on their site to see if it does what you need.

I stuck with dial-up before because I didn't want to pay the cost the cable company was charging and DSL was not available.  When DSL was made available they gave me a discount so my DSL costs $10/month compared to the $20/month for entry-level DSL.  Funny thing is my dial-up was close to $20/month so not only did I get faster connection but I'm saving money to boot! :guitar:  It has rated up/down speeds of 384 Kbps/768Kbps so its no speed demon but completely adequate.


If you are forced to go with dial-up, hopefully it is a dedicated line.  I have heard of people being able to utilize 2 phone lines for internet connection to speed things up.

---

### Post by pwnst*r on 2009-04-10
> **EnglishSparrow said:**
> They have, um, what is it called when you get free money from other peoples taxes? :p

um, no.

---

### Post by Paqman on 2009-04-10
> **EnglishSparrow said:**
> I am running a project with several online friends, and the files are stored on my web server.

Do you actually know these friends IRL? If so, you could give the server hosting job to one of them until you sort your bandwidth problem.

---

### Post by forrestcupp on 2009-04-10
If you already had all of your computers running high speed, then that means that you already have them on a network.  So that's one step out of the way.  They must already be networked together or else you couldn't have been running high speed on them all.  Now you just need to run dial-up into one of the computers through a modem, and set that computer to share its internet connection on the network.  I've done it in Windows XP, and it was easy to set up, but I've never messed with dial-up in Linux.

Or you could just get a modem for your computer, run a phone line to it, and take turns with who's on the internet.

Some tips about dial-up.  If you don't have a dedicated phone line for the internet, you won't be able to get phone calls while you're on the net without disconnecting.  If you *do* have a dedicated phone line, you need to check you're ISP's terms of service.  A lot of ISP's say you get unlimited hours, but if you check deeper, they only allow you to stay connected for a certain number of hours at a time.  That's because they don't want people leaving it on all the time.  Check with an ISP about that before you go with them.  And as you already know, it's going to be so slow that you will not possibly be able to run web sites from your computer at home anymore.

And to the people saying to just find a cheaper ISP:  Not everyone has that option.  Where I live, I have Comcast and Verizon DSL and that's it.  They both pretty much cost the same.  A lot of people *can't* just find a cheaper ISP.

---

### Post by koenn on 2009-04-10
> **forrestcupp said:**
> If you already had all of your computers running high speed, then that means that you already have them on a network.  So that's one step out of the way.  They must already be networked together or else you couldn't have been running high speed on them all.  Now you just need to run dial-up into one of the computers through a modem, and set that computer to share its internet connection on the network.  I've done it in Windows XP, and it was easy to set up, but I've never messed with dial-up in Linux.


I used to do that with Freesco, a linux nat router on a floppy, with support for dialup through a standard serial modem. It could do  dial-on-demand, i.e. only dial out when one of the networked computers needed internet access. (wouldn't be any good for a server that needs to be online all of the time, though). It was OK to share web browsing to the 2-3 computers we had back then, because once you've loaded a page and are reading it, the others have the full bandwidth do download their page. Today's web with all the streaming and the downloads etc might e less enjoyable, but it's doable. Some serious caching might also help

---

### Post by Nevart on 2009-07-15
The cheapest dial-up where I live is $8.50 per month, while the cheapest ASDL1 is $20/mo.  That's a difference of only a few dollars a week more, but a huge difference in performance.

Dial-up is not really feasible.  If your dad thinks he can get by with dial-up for business, he had better only be using it for e-mail.  Otherwise he will very quickly learn what a big mistake he made.

The worst case scenario is that he cancels the internet completely.  If he goes to dial-up, you will have to take in turns to use the internet, and it will still suck.

If time = money, then the extra time you spend waiting for that slow connection is going to cost much more than sticking with cheap broadband.

Why does it have to be comcast?  There are plenty of other providers around.

---

### Post by lisati on 2009-07-15
Not counting special offers with terms and conditions that might not suit, the cheapest dial-up I know of in my area is something like $9.95 a month, and the cheapest ADSL connections I'm aware of are something like $20 per month.

There might also be packages that help save money - the one I'm on, which includes both a phone line and ADSL, saves us money by having free national calls to landlines and discounted calls to mobiles. The savings from the "free" and discounted calls usually makes up for the extra $$$ we have to pay for the plan. And we do that "recycle tax-payers' money" thing for our main source of income.

---

### Post by PartisanEntity on 2009-07-15
> **EnglishSparrow said:**
> Parents have no jobs at the moment(though they are writers, they haven't published anything yet).


And they won't let me get a job. My only option is to finish my book. 


Our comcast bill is $300 some how. Cable+Internet.

You're paying $300 for internet and phone!? Wow, that's really expensive.

Just out of interest, are multiple accounts on Ebay really necessary?

---

### Post by Glucklich on 2009-07-15
> **Hellow said:**
> Social security? Seriously, though, with no cash flowing, I would be worrying about other things than your internet.

Listen to this guy's advise. He's right.

... And 300$ for a Internet Connection + Cable? 200&#8364;? That's ******* surreal!

---

### Post by XubuRoxMySox on 2009-07-15
There really is a device which allows multiple computers to wirelessly share a dialup connection (check it out [here](http://www.pcmag.com/article2/0,2817,1770850,00.asp)). It's pretty much a snap to install and get going. But it would only makes sense to share a dialup connection between two or three computers, certainly not six! 

But the device costs $150 (and all you're paying for the convenience of not having to string some cable and set it up yourself). Not really useful if money is the main concern... 

I would ditch the Cable TV and watch TV shows online using the much cheaper internet service, and use Magic Jack or something instead of the Comcast "bundle" that costs so very much! The dialup alternative is useful for little more than e-mail.

-Robin

---

### Post by oldsoundguy on 2009-07-15
$300 bucks a month for Comcast.  Think you are either being told the wrong figures by your parents, or they are getting hosed!
I have high speed internet, two VoIP phone lines with all features. Digital TV service with two converters, HDTV with one converter, 3 premium channels for movies and I pay $220 US for the whole package.
AND as soon as Fios becomes available in my area, I will be changing over (my eMail addy is NOT that important when it comes to saving well over $100 a month!)

---

### Post by Dragonbite on 2009-07-15
> **Glucklich said:**
> Listen to this guy's advise. He's right.

... And 300$ for a Internet Connection + Cable? 200€? That's ******* surreal!

Man, I'm doing $10 for DSL and don't bother with cable TV.

---

### Post by ukripper on 2009-07-15
Nice joke $300 for internet and phone rental. Seriously, 300 X 12 = $3600 a year in this day n age, sounds you been ripped off. Apart from that when you don't have money why pay for phone, use pay as you go sim for receiving only?

---

### Post by MikeTheC on 2009-07-15
I think your parents need to come to the realization that it takes a *long* while in the creative arts to get to the point of being able to use that to support oneself. For that matter, *most* "writers" never reach that point, and consequentially have real jobs and do writing purely as a sideline.

Maybe your folks need to re-visit their own personal priorities in life. And clearly if the difference between budget rate dial-up and bottom tier DSL service is a deal-breaker, then I don't think your family should even *think* about having Internet service. You should be more focused on putting food on the table.

This isn't a technological matter so much as it is a priorities matter.

---

