---
title: "Internet Question (DHCP)"
date: 2011-01-06
forum: The Cafe
---

### Post by sinclair86 on 2011-01-06
I have a question. If it is unclear, please let me know and I will try to explain what I am asking in a different manner. 

How, on a DHCP connection, is my IP address tied to a geo location, service email (blahblah@verizon.net [email]asdasd@comcast.net[/email] etc), or physical address? Is it the MAC address of the device that they install that brings the service into your house, before the router, that, with my account information, is stored in a database somewhere on their server? Or something more complex?

---

### Post by koenn on 2011-01-06
start here

[http://en.wikipedia.org/wiki/Geolocation_software](http://en.wikipedia.org/wiki/Geolocation_software)

---

### Post by sinclair86 on 2011-01-06
I understand that, in my case verizon, owns the block of XX.XX.XX.XX-XX.XX.XX.XX for the location of my service meaning if I am in the US and I live in Montana I will not be getting an assigned IP address from or for a service in lets say Florida. I guess geo location isnt necessarily what I am asking about. What I am more concerned about is the fact that if my internet is used for anything it can be traced back to me.

---

### Post by koenn on 2011-01-06
> **sinclair86 said:**
>  What I am more concerned about is the fact that if my internet is used for anything it can be traced back to me.

That's simple.
Your ISP knows what IP address they gave you (or to the MAC address of whatever Customer Premises Equipment you got from them). So any connection coming from or going to that IP address, can be linked to you.

---

### Post by LowSky on 2011-01-06
DHCP is used for you local (ie: your house) connection. The modem you are given by your providor is an assigned address that is recorded and maintaind with the specific details of your location.

So anything you do can be traced back to you. It just a matter of someone wanting to trace what you've done.

---

### Post by sinclair86 on 2011-01-06
> **koenn said:**
> That's simple.
... Customer Premises Equipment ...

Just to be clear you arent talking about the router, correct? What you are addressing is the box/object/modem (whatever you want to call it) that takes the services from the street to inside the house. It is essential because without this device one would not be able to, let say dig up the cable(s) that provide the service and plug directly into it (with modifications of course).

> 
DHCP is used for you local (ie: your house) connection. The modem you are given by your providor is an assigned address that is recorded and maintaind with the specific details of your location.

So anything you do can be traced back to you. It just a matter of someone wanting to trace what you've done.  

So what you are saying is that the modem is actually leased the address and not the router? or does the modem itself act like a router and additional routers attached only provide different NAT'ed networks? or does the modem act like a switch that can be controlled remotely via verizon/comcast/whoever 

What I am really trying to understand is what is physically stopping me (besides laws) from going out front of my house and digging up cables to plug into and receiving internet? 
Also if people have the same service in my area it is all on one line going back to the business providing the service?

---

### Post by grahammechanical on 2011-01-06
I do not know how the physical connections are made in USA but in GB in my case the modem/router (it is a combined device) is connected into the telephone line. So the connection goes from my house to a telephone junction box/cabinet somewhere nearby, then to the telephone exchange and on to the servers run by the ISP. When I switch on the modem/router it dials the Internet Service Provider, makes a connection and I get Internet access through the ISP. They know who I am because I have an account with them. They know what IP address I have been assigned by them. Websites collect information about computers that access the site. Yep, they know that you are out there.

Regards.

---

### Post by sinclair86 on 2011-01-07
@grahammechanical Thank you for your response. Is that a broadband or dial up connection?

@anyone else who read this thread or post a response:

Although I feel like an ***, I want to get a few things out of the way first. 

To anyone that tells me to use Google. Hit the back button on your browser now. Without getting in why I will never use Google, I am not a little 14 year old kid that doesn't know how to do anything on the internet other than use facebook. I know how to do research, in fact I love it. I love reading and understanding how things work. I post on forums because I like having discussions with other people who might know what they are talking about. Its not often I get to talk to others on topics I enjoy.

No I am not trying to "hide" my activities. I run a tor server. I know how to use my neighbor's encrypted wifi. I know how to go to public places (college, starbucks, mcdonalds, etc.) to use the internet.


I realize that sometime I am too vague when asking questions. This comes from a belief that to understand something I have to pretend I know nothing of what I am asking. Starting from a blank slate I am sometime able to see things I couldn't/didn't before. SO let me start with what I know and see if anyone can add on or possibly correct me if I am in err. 


My question is how does an ISP know that 56.34.22.143 is assigned to __BLANK__ (on a DCHP connection)?

Lets say, for the sake of the discussion, that I am a master of electronics and that my neighbor has the same ISP and I know his or her MAC address of the modem (the device that the router is attached to). If it is solely based on the MAC address of the modem  what is stopping me from spoofing that address to take theirs? 

Why would someone want to do that? Because if that is the only means of a check, whats to stop that someone from buy the base service (i think its 15mb dl 5mb ul for fios) then spoofing to a neighbor who might have 35mb dl 35mb ul?

---

### Post by mips on 2011-01-07
> **sinclair86 said:**
> 
My question is how does an ISP know that 56.34.22.143 is assigned to __BLANK__ (on a DCHP connection)?

Lets say, for the sake of the discussion, that I am a master of electronics and that my neighbor has the same ISP and I know his or her MAC address of the modem (the device that the router is attached to). If it is solely based on the MAC address of the modem  what is stopping me from spoofing that address to take theirs? 

1. Your phone line has a phone number tied into the billing system & technical database so they know your physical address. Even if you don't have a phone service with your adsl the line is still recorded in the system.
2. The port on the DSLAM is linked to your phone line and easily traced back for billing & diagnostic purposes.
3. Your router or PC has to authenticate with a username & password.
4. Your IP address & MAC address is recorded against your username and password and can be referenced back to the DSLAM port in use and then obviously back to your phone line which in turn would yield your physical address. By law in most countries logs also have to be kept for a certain period of time (usually several years).

All this information is available instantaneously for technical support issues etc.

Secondly if you tried to use your neighbours MAC address and you are both online at the same it would cause problems with ARP and traffic delivery cannot be guaranteed seeing the router would be confused about where to send the packets. Keep in mind that your Layer 3 & up protocols like TCP/IP has to work down the OSI stack to deliver traffic to the lower layers and your MAC address is part of Layer 2, OSI Link Layer.

---

### Post by koenn on 2011-01-07
> **sinclair86 said:**
> Just to be clear you arent talking about the router, correct? 
no, I used a generic word because the type of device will vary with what sort of internet connection/subscription you have, and the mechanisms that identifies you will vary with how your ISP set things up.
I couldn't be any more precise because your post is vague as to what sort of connection you have.

Underneath the IP layer there's all sorts of "network access" (layers 1&2 in OSI-speak)  going on, copper or optic fiber, DSL, PPP, PPPoE, MAC, ... ,  but in order for IP to work, there has to be a relation between IP and the underlying protocols. This is managed by your ISP, so they'd be able to trace IP traffic back to the equipment at your place. 


mips' explanation is pretty accurate, and more precise.

---

### Post by t0p on 2011-01-07
The way I understand it:  your ISP assigns an IP address (either static or dynamic, depending on ISP and the customer's requirements) to the customer.  So the ISP knows that, at a certain time on a certain date, IP address AA.BB.CC.DD was being used by Customer X (Bob to his friends).

Bob's home router assigns IP addresses to the devices at Bob's place: his desktop computer, iPad, Android phone, whatever.  These IP addresses are in the ranges like 192.168.XX.YY.  These are kind of irrelevant to the ISP or the authorities.  Each device also has a MAC address (AB:CD:EF:GH:IJ) so Bob's router knows which device is doing what at what time.  Bob can probably whitelist his devices' MAC addresses, so no evil-doer can use Bob's internet connection without permission.  But most people never bother doing that.  Assuming the router is a wireless router, most Bobs will just use WPA connection security to keep outsiders out.  If Bob doesn't use a wireless router, he's even less likely to use a MAC whitelist, as it's unlikely anyone is going to physically tap into his phone line to use his service.

Anyway, if some crime were committed via an internet account with IP address AA.BB.CC.DD, the cops would look at their big cross-referenced list of IP addresses and ISPs to see which ISP actually uses that address.  Then the cop would go to that ISP (with a court order in many countries) and ask: "Who was using IP address AA.BB.CC.DD on January 7, at 3:30pm?"  The ISP would check its logs and reply "Bob."  So then the cops will go to Bob's house and arrest him for whatever evil deed had been done.

Of course, this isn't a fool-proof system.  There's a program called **macchanger** that allows your device to spoof a different MAC address.  So Bob's lawyer could look at the paperwork, see that a MAC address not belonging to Bob's devices was used, and say "It wasn't Bob - look at the MAC address."  To which the prosecution would reply "Yeah, but he could have used macchanger."  But whatever: this introduces *reasonable doubt* to the case, and might get Bob off.

Even more twisted: let's assume Bob uses a wireless router without *any* protection - so it's an open access point.  Bob's neighbour (Margaret to her acquaintances - she's too evil to have any real friends) uses a network sniffing program to find out the MAC address of Bob's laptop; then later on she uses macchanger to spoof that MAC address (when Bob isn't using the laptop - otherwise the router would get upset, MAC addresses are *supposed* to be unique}.  She then commits her evil crime, through Bob's connection, using a MAC address that was assigned to Bob's laptop!  So it would appear that Bob *did* commit the crime!

Of course, Bob's lawyer ought to know about this possibility, so again reasonable doubt *should* be introduced to the case.  But some courts seem to take the attitude that running an open wireless access point is evidence of evil and therefore is inadmissible as defence evidence; or a judge may rule that it's admissible but not very relevant.  So Bob may be punished for Margaret's crimes anyway.

Even worse: maybe Bob *does* use security, but Margaret cracks it then uses Bob's access point.  A court will decide that the access point was secure, therefore only Bob could have used it, therefore *Bob is guilty*.  This has happened many times, and will continue to happen - there is no such thing as 100% security.

I have no idea if this answers the OP's question.  But I had fun typing it, and maybe *someone* will find it useful.  (Note: if anyone actually *does* anything I've typed here, I accept no liability.  It's all just for entertainment or something.  And I would *never* condone crime...)

---

### Post by sinclair86 on 2011-01-07
@top well as much as I enjoyed reading that, it is not within the scope of what I was asking.

@koenn

> Secondly if you tried to use your neighbours MAC address and you are both online at the same it would cause problems with ARP and traffic delivery cannot be guaranteed seeing the router would be confused about where to send the packets. Keep in mind that your Layer 3 & up protocols like TCP/IP has to work down the OSI stack to deliver traffic to the lower layers and your MAC address is part of Layer 2, OSI Link Layer. 

See i thought about that as well. From what I currently understand how the white box (see picture below) is that it might potentially split into 2 parts. One verizon has access to and the second part is past that and becomes the basis for my home network. I assume this because if they test my line to my house wouldn't they need some type of access to it from their end? ALSO I run a server at work behind a staic ip. There is a coax line directly from outside to the router (the only thing they gave us). I have found that device was split into 2. One side comcast could access from their end and one side I could access from the local net. Granted what I could do was very limited. So with that in mind AND with the possibility that this could be done, couldn't someone potentially abuse the access the ISP has to preform a dos attack on the device (the white box)? What if that person had access to their local net, as it is, and rendered their router (not the white box) useless. If no information is being pulled from either device then the spoofed one can become the real one. Yes I understand if someone is having a problem with their internet of course they will call their ISP and someone will come out and look at it, but when one is a sleep the world still turns yet they are unaware of it.

OR what if it were possible to switch MAC addresses. I take his he takes mine.

Also > our router or PC has to authenticate with a username & password. this is for a PPPoE connection correct?

---

### Post by sinclair86 on 2011-01-07
>_<

---

### Post by mips on 2011-01-07
> **sinclair86 said:**
> @top well as much as I enjoyed reading that, it is not within the scope of what I was asking.

@koenn



See i thought about that as well. From what I currently understand how the white box (see picture below) is that it might potentially split into 2 parts. One verizon has access to and the second part is past that and becomes the basis for my home network. I assume this because if they test my line to my house wouldn't they need some type of access to it from their end? ALSO I run a server at work behind a staic ip. There is a coax line directly from outside to the router (the only thing they gave us). I have found that device was split into 2. One side comcast could access from their end and one side I could access from the local net. Granted what I could do was very limited. So with that in mind AND with the possibility that this could be done, couldn't someone potentially abuse the access the ISP has to preform a dos attack on the device (the white box)? What if that person had access to their local net, as it is, and rendered their router (not the white box) useless. If no information is being pulled from either device then the spoofed one can become the real one. Yes I understand if someone is having a problem with their internet of course they will call their ISP and someone will come out and look at it, but when one is a sleep the world still turns yet they are unaware of it.

OR what if it were possible to switch MAC addresses. I take his he takes mine.

Also  this is for a PPPoE connection correct?

No disrespect but my suggestion to you is to go learn about the OSI model, routing, telco infrastructure & general internet. You lack understanding of how things actually work and the underlying principals. Even with my previous explanation you seem not to grasp how things work.

If you have questions I would be glad to answer them though.

---

### Post by koenn on 2011-01-07
> **sinclair86 said:**
> @koenn

sounds like you're referring to someyhing mips said (and I have the impression he knows a lot more about the electronics side and layer 1 and 2 than me. I rarely have to deal with anything below layer 3 )  but I'll have a go.


>  So with that in mind AND with the possibility that this could be done, couldn't someone potentially abuse the access the ISP has to preform a dos attack on the device (the white box)? What if that person had access to their local net, as it is, and rendered their router (not the white box) useless. 
I'm guessing the white box is a cable modem or so. 
I'm pretty sure your ISP has management access to it, so they could simply disable it or disconnect it at their end. There's your DOS. 
How likely it is for someone to gain access to the ISP's network and disconnect you, I don't know.

> If no information is being pulled from either device then the spoofed one can become the real one.

I don't know exactly how they do it, but I'm pretty sure ISPs can (and do) record characteristics of the cable modem and link them to you as a subscriber. Eg When I had my cable modem replaced, I had to inform my ISP so they could "activate" it - I assume that translates to "allow it to bridge with their network, and  attach my name to it so they can bill me for the traffic if I go over the monthly volume"



What exactly are you up to ?

---

### Post by cariboo on 2011-01-07
I know with my isp the modem serial number is a way of identifying the customer. 

For instance when adding or removing email addresses, you have to enter the modem serial number as part of the identification process. For all I know, the serial number is broadcasted along with the mac address and ip address.

---

### Post by mips on 2011-01-07
> **koenn said:**
> 
I don't know exactly how they do it, but I'm pretty sure ISPs can (and do) record characteristics of the cable modem and link them to you as a subscriber. Eg When I had my cable modem replaced, I had to inform my ISP so they could "activate" it - I assume that translates to "allow it to bridge with their network, and  attach my name to it so they can bill me for the traffic if I go over the monthly volume"


About a month ago I realised I was still paying for a dialup account I cancelled 6yrs ago. I informed the ISP of this and they actually had records of the exact date & time of last usage which was about a year later but I forgot that I "loaned" the account to a friend for his business.

I used to work for a large telco so I kinda know what's going on in case anyone thinks I'm waffling. Mostly Layer 3 & up but working in a telco I got exposure to the lower layers from providing management for them, X.25, ATM, SDH (SONET), FR etc etc.

---

### Post by sinclair86 on 2011-01-07
Listen mips could it be possible that it you that doesnt understand. That you are assuming I possibly might know nothing of what I am asking when my current knowledge might actually surpass what you are able to comprehend? Its sometimes the simplest answers that are the hardest to find. When one starts from nothing its possible to see it in a way that he or she did not see before. Therefore essentially answering his or her own question.

FYI

when one say "no disrespect" how could one not take it as so? Its apparent that the word choice or the statement that came across in your head came off to you as disrespectful hence the need to state "no disrespect". so instead of stating your intentions why not try changing your choice of words and faith in the person you are trying to communicate with?

---

### Post by koenn on 2011-01-07
> **sinclair86 said:**
> That you are assuming I possibly might know nothing of what I am asking when my current knowledge might actually surpass what you are able to comprehend? 
I'm going to stay out of this, but just give you 2 pieces of information to consider:
1/ your OP strongly suggests that you don't know an essential property of dhcp, i.e. that it assigns IP addresses to hosts identified by MAC addresses, and that a DHCP server therefore can map (dynamic) IP addresses to (static) MAC addresses. That is so essential in tcp/ip that the assumption that your knowledge on the subject is lacking, is actually a logical conclusion.

2/I've seen mips post on networking, switches, routers, ..., displaying knowledge of core networking far beyond what's the norm on these forums

to paraphrase you: could it be that your knowledge is such that you don't even know how much ypu don't know ? 


but like I said, I probably should stay out of this.

---

### Post by mips on 2011-01-07
Well from the way you ask your questions and then repeat them again I come to the conclusion that you don't understand the subject matter, either that or you don't know how to formulate a proper question. I'm leaving out the feel good politeness as required by the forums now in case it is construed as as being patronising or disrespectful. (Mods, I'll take the infraction on the chin)

I have never in my life looked down or or belittled someone that does not understand something. There is no such thing as a stupid question & I hate people that laugh at people asking 'stupid' questions. I've lectured before and greatly enjoyed it. Nothing more satisfying than seeing someone grasp something, you can literally see the light bulb going on and then you know you achieved something for them.

I'm not assuming you know nothing, I don't know what you know. That is why I replied in a point/step manner so anybody reading my reply could follow. My reply to your original question is not false or flawed, just simplified to the basics.

I apologize for offending you, it was not my intention. I will now bow out of this thread.

---

### Post by bodhi.zazen on 2011-01-07
> **sinclair86 said:**
> Listen mips could it be possible that it you that doesnt understand. That you are assuming I possibly might know nothing of what I am asking when my current knowledge might actually surpass what you are able to comprehend? Its sometimes the simplest answers that are the hardest to find. When one starts from nothing its possible to see it in a way that he or she did not see before. Therefore essentially answering his or her own question.

FYI

when one say "no disrespect" how could one not take it as so? Its apparent that the word choice or the statement that came across in your head came off to you as disrespectful hence the need to state "no disrespect". so instead of stating your intentions why not try changing your choice of words and faith in the person you are trying to communicate with?

I have to agree with mips , I think your question was asked and answered. If you do have some superior knowledge you have not rephrased the question in any way to indicate that and thus it seems to me you do not understand the basics, and thus do not understand how an ip address is assigned by your ip provider nor how geoip works.

If somehow you do have such a superior knowledge, perhaps it would help if you rephrase the questions.

But basically in a nutshell, you public ip address is assigned by your ip provider and you can then be located based on that ip address with geoip. It has nothing to do with your MAC and very little to do with dhcp.

---

### Post by CharlesA on 2011-01-07
> **bodhi.zazen said:**
> 
But basically in a nutshell, you public ip address is assigned by your ip provider and you can then be located based on that ip address with geoip. It has nothing to do with your MAC and very little to do with dhcp.

With that said, I'm closing this thread.

@OP: If you have a specific question, make a new thread asking what you specifically want to know.

---

