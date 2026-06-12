---
title: "If someone wanted to put this together."
date: 2010-12-10
forum: The Cafe
---

### Post by ki4jgt on 2010-12-10
If someone wanted to put this together as a new Internet alternative:
How would they go about it?

> 
- Every user could potentially get an unlimited connection
- Every Server (Website) could have an unlimited connection to everyone using it!
- Every server (Website) could have the ability to experience 100% uptime
- All communications could be completely confidential between the two individuals talking and no one else.
- All using the current set of protocols we are currently using (TCP/IP)
- No one could monitor your communications
- HTML could be made simpler and still maintain it's (complete) functionality
- The Internet could be FREE (No Price)
- While maintaining proper authentication protocols (people would still be able to be traced for illegal stuff)
- Governments could not block websites

Meaning you have to believe it's possible to make a suggestion or at least partially possible

---

### Post by ki4jgt on 2010-12-10
Unlimited is interpreted as the bandwidth the end user can receive through their hardware.

---

### Post by 3Miro on 2010-12-10
> **ki4jgt said:**
> Unlimited is interpreted as the bandwidth the end user can receive through their hardware.

What do you think is the limit now? It is hardware, not something else. 

The signal has to go through fiber optics and someone has to install those, that means money. There is no way this can be done for free, you will always have an ISP.

There is no way you can create a point-to-point connection between everything in the world. There will always be a middle-man. If you don't want someone listening to your traffic, use encryption, like the Banks and e-mail web-sites. This is already implemented.

A web-page has to stay on a physical server and every server is vulnerable to the infamous "cruse missile attack", therefore, the government can always block web-pages. If you don't want them doing that, you make up laws, this is a legal not technological issue.

---

### Post by Spice Weasel on 2010-12-10
Making HTML simpler is a bit like turning granite in to a gas - it just can't be done.

But yes, this already has been (partly) done. See Freenet.

---

### Post by ki4jgt on 2010-12-10
I'm thinking combo Freenet, netsukuku, AllianceP2P and Bittorent

Me going into detail on this a few months ago. I've edited a lot of the ideas now to include better ones LOL that's the best way I know to explain it.

[http://forum.codecall.net/general-programming/32018-network-encryption-programing.html](http://forum.codecall.net/general-programming/32018-network-encryption-programing.html)

---

### Post by mips on 2010-12-10
> **ki4jgt said:**
> 
How would they go about it?


Money and LOTS of it.

---

### Post by tgm4883 on 2010-12-10
> **ki4jgt said:**
> - Every user could potentially get an unlimited connection


Every user can potentially get an unlimited connection now? You just need to have fiber. This also becomes an issue with multiple people connecting to the same website. Potentially, they both can't max out their connections (eg. 100MB + 100MB != 100MB)

> **ki4jgt said:**
> 
- Every Server (Website) could have an unlimited connection to everyone using it!


See above


> **ki4jgt said:**
> 
- Every server (Website) could have the ability to experience 100% uptime


Again, this is true right now. Aside from hardware failure, if a route between two points is broken then it finds another route. This currently is an issue with major links between two places, but there shouldn't be a single point of failure anywhere.

> **ki4jgt said:**
> 
- All communications could be completely confidential between the two individuals talking and no one else.


This is possible, use SSL and tunnel your traffic

> **ki4jgt said:**
> 
- All using the current set of protocols we are currently using (TCP/IP)


Obviously already done

> **ki4jgt said:**
> 
- No one could monitor your communications


Well, if nobody could monitor your communications that could be pretty difficult. Lets say you want to see a webpage, so you send the request to the web server anonymously. Who does the webserver send the request back to?

What about sites that you need to login to? (like banks, email, etc)

I suppose you mean 3rd parties, in which case, see section above on SSL 

> **ki4jgt said:**
> 
- HTML could be made simpler and still maintain it's (complete) functionality


Sure. 

> **ki4jgt said:**
> 
- The Internet could be FREE (No Price)


No, it could not. Nobody would lay the fiber/copper for free, so you couldn't connect to anyone else. You might be able to go wireless in some sort of ad-hoc mesh sense, but that really wouldn't work either, not enough people have the hardware that would require ($)

> **ki4jgt said:**
> 
- While maintaining proper authentication protocols (people would still be able to be traced for illegal stuff)


Again, see section on SSL

> **ki4jgt said:**
> 
- Governments could not block websites

They can't block websites now. They can block IP addresses and domain names, but the website can move if necessary. I've heard things about a more distributed DNS system, but I don't really like that. Too easy to be malicious.

---

### Post by ki4jgt on 2010-12-10
I go into detail on this thread at codecall:
[http://forum.codecall.net/general-programming/32018-network-encryption-programing.html](http://forum.codecall.net/general-programming/32018-network-encryption-programing.html)
> Quote:
Originally Posted by ki4jgt  
- Every user could potentially get an unlimited connection
Every user can potentially get an unlimited connection now? You just need to have fiber. This also becomes an issue with multiple people connecting to the same website. Potentially, they both can't max out their connections (eg. 100MB + 100MB != 100MB)

Picture the Internet as a living thing. as it flows from one computer to the next. Now, picture your website being hosted not only by your computer but by every computer which visits your site. How in the world are you going to max out all those connections? I shouldn't say every server. This idea would tern the Internet into a huge single server. Hardware failure wouldn't even mess this up! Not unless every computer on the planet went kaputt.

> Originally Posted by ki4jgt  
- No one could monitor your communications
Well, if nobody could monitor your communications that could be pretty difficult. Lets say you want to see a webpage, so you send the request to the web server anonymously. Who does the webserver send the request back to?

What about sites that you need to login to? (like banks, email, etc)

I suppose you mean 3rd parties, in which case, see section above on SSL 

If the entire Internet is the server then any computer could be the computer which sends you the data. You would be able to verify the author with the same technology Freenet uses.
Databases would be hosted amoung trusted computer networks for login purposes.

> Quote:
Originally Posted by ki4jgt  
- The Internet could be FREE (No Price)
No, it could not. Nobody would lay the fiber/copper for free, so you couldn't connect to anyone else. You might be able to go wireless in some sort of ad-hoc mesh sense, but that really wouldn't work either, not enough people have the hardware that would require ($)

It could be close to free anyway. You know how people reacted to the open software movement, how much more do you think they'll act towards a free Internet? Using Netsukuku's technology if you're within wifi distance of another computer, your computers are automatically linked and the Internet established from you to that person to who ever else you're around. If you setup a wifi box, everyone who connects to the wifi box will share their internet with you and you with them. So if your connected to a public wifi and mindy a few block down who can't get into the wifi is connected to your laptop, then anyone she is connected to, is also connected to you!

About the governments not being able to block it, the internet would be one big server so the author wouldn't have to reset their IP address.

---

### Post by 3Miro on 2010-12-10
This is a very idealistic picture, which I don't think is realistic. 

Not all internet traffic can be done in a torrent fashion, your Bank information is your personal and you should be the only one to access it, it should never come anywhere near my computer. The Database of the Bank should be stored only on Bank servers, it should never leave those servers, you cannot make a distributed database of Bank information. Another example is the web-page created by your Google search, it is uniquely yours, it cannot be transmitted in a torrent fashion.

If I get a piece of information on the Internet, then I wouldn't mind sharing parts of it in a torrent fashion (for a limited amount of time, I cannot permanently share everything I have ever downloaded). However, even disregarding the violation of privacy that it may cause if you or someone else can see that I have visited this or that web-page, I still wouldn't want anyone uploading their web-page on my computer without my "permission" (I think Kaza did something like that at one point and it was a disaster).

Free Internet and Free software are completely different animals. If you make a program and then give me a copy of it, then both of us will have exact same copies of the exact same program. If you mine some copper to make a wire and then you give me that copper then you will not have a wire of your own. 

The Internet could become "free", if it were sponsored by the government, but then everyone would be paying for it in taxes. This may be good, but it is not "free". Wire and fiber across the oceans are way too expensive for a charity/foundation. As for wireless, the bandwidth is very limited, theoretically you can only push so much data on air and if everyone is going wireless, that means that everyone would have to share the same bandwidth.

---

### Post by tgm4883 on 2010-12-10
This whole thing isn't very good in practice, but i'll play along.

> **ki4jgt said:**
> I go into detail on this thread at codecall:
[http://forum.codecall.net/general-programming/32018-network-encryption-programing.html](http://forum.codecall.net/general-programming/32018-network-encryption-programing.html)


Picture the Internet as a living thing. as it flows from one computer to the next. Now, picture your website being hosted not only by your computer but by every computer which visits your site. How in the world are you going to max out all those connections? I shouldn't say every server. This idea would tern the Internet into a huge single server. Hardware failure wouldn't even mess this up! Not unless every computer on the planet went kaputt.


Yum, socialism. Why that sounds like an outstanding idea. BTW, here are all of my banking details, what I order on amazon, the emails that I sent to my best friend complaining about you, and some deep dark secrets.

Oh, and don't ever update your site. Every computer out there is now out of date. How do they know to get the new updates from you? There's your downtime right there.

> **ki4jgt said:**
> 
If the entire Internet is the server then any computer could be the computer which sends you the data. You would be able to verify the author with the same technology Freenet uses.
Databases would be hosted amoung trusted computer networks for login purposes.


I'm assuming this would use some sort of P2P type software? Which IIRC requires a central server to be the tracker. Which sounds like it fails your non-tracking clause.

> **ki4jgt said:**
> 
It could be close to free anyway. You know how people reacted to the open software movement, how much more do you think they'll act towards a free Internet? Using Netsukuku's technology if you're within wifi distance of another computer, your computers are automatically linked and the Internet established from you to that person to who ever else you're around. If you setup a wifi box, everyone who connects to the wifi box will share their internet with you and you with them. So if your connected to a public wifi and mindy a few block down who can't get into the wifi is connected to your laptop, then anyone she is connected to, is also connected to you!


No, it's free for you. It's expensive for whoever owns the copper/fiber. Never mind the fact that Mindy (and joe, tim, robin, and fred) all are using your internet for free and not contributing an internet connection. Your speed now suffers because you have 1 internet connection and 45 people using it.

I won't ever talk about the latency that would happen in this scenario.

> **ki4jgt said:**
> 
About the governments not being able to block it, the internet would be one big server so the author wouldn't have to reset their IP address.

They could shut down the tracker, requiring all of your nodes to find a new tracker. Which is A) a pain, and B) downtime


You have good ideals, but a narrow view of how things actually work. I suggest you research a bit about how the Internet works and the different technologies in play here.

---

### Post by ki4jgt on 2010-12-10
I'm currently busy so I haven't had the chance to read your response in it's entirity. I skimmed and you have pointed out a lot of things. But firstly I want to clear something up that you're assuming. The Internet isn't coming from any particular place. So if mindy is piggybacking off of joe then she's not robbing anything b/c there's nothing there to rob. She is contributing the resources she has in her directory. I also would like to point out that the traffic is encrypted from point a to point z. Lastly I do not expect this to handle info like Bank accounts until it gets a little farther along.

---

### Post by tgm4883 on 2010-12-10
> **ki4jgt said:**
> I'm currently busy so I haven't had the chance to read your response in it's entirity. I skimmed and you have pointed out a lot of things. But firstly I want to clear something up that you're assuming. The Internet isn't coming from any particular place. So if mindy is piggybacking off of joe then she's not robbing anything b/c there's nothing there to rob. She is contributing the resources she has in her directory. I also would like to point out that the traffic is encrypted from point a to point z. Lastly I do not expect this to handle info like Bank accounts until it gets a little farther along.

Let me try to clarify that another way. Mindy has only contributed her computer. She herself has no ISP, she gets her internet from joe, who gets his internet from fred, who gets his internet connection from you (you get it from comcast in this scenario). Mindy, joe, and fred don't have a comcast internet connection, so now you are paying for an internet connection for everyone. Such a nice guy you are, but you should probably upgrade your comcast plan since your connection is getting saturated.


Your response to that will be that you need no comcast connection as everyone is in an ad-hoc mesh. OK, lets go down that road.

Take Las Vegas. Very populated, but roughly isolated. Everyone there is connected via the ad-hoc mesh. How does someone in Las Vegas go to NYTimes.com and read that website? Surely the ad-hoc mesh isn't going to reach from Las Vegas to a surrounding city.

---

### Post by 3Miro on 2010-12-10
Sometimes it is enough to know which page has been visited to do damage to someone. It doesn't matter how encrypted the traffic is, everyone in the middle can see that point A is talking to point B. That includes:

The College professor reading: perfectly_legal_nude_college_girls.com

The cop reading: porn_actresses_acting_like_they_are_in_jail.com

The hacktivist reading: lets_keep_wikileaks_alive.org

Citizen in country X reading: the_corruption_in_government_X.net

If I pay the ISP money, they have an incentive to keep my information confidential (otherwise they will lose clients). If I bounce through random people in the world, everyone will know that I have a fetish for: hot_chicks_dressed_like_penguins.com

---

### Post by tgm4883 on 2010-12-10
> **3Miro said:**
> Sometimes it is enough to know which page has been visited to do damage to someone. It doesn't matter how encrypted the traffic is, everyone in the middle can see that point A is talking to point B. That includes:

The College professor reading: perfectly_legal_nude_college_girls.com

The cop reading: porn_actresses_acting_like_they_are_in_jail.com

The hacktivist reading: lets_keep_wikileaks_alive.org

Citizen in country X reading: the_corruption_in_government_X.net

If I pay the ISP money, they have an incentive to keep my information confidential (otherwise they will lose clients). If I bounce through random people in the world, everyone will know that I have a fetish for: hot_chicks_dressed_like_penguins.com

Don't forget that in the OP's scenario, there is no end point. Since every machine is hosting the website, (please think of the hard drives), then those hosting can see exactly what you are looking for.

---

### Post by koenn on 2010-12-10
[QUOTE=tgm4883;10223668]Yum, socialism. Why that sounds like an outstanding idea.QUOTE]
maybe better keep your political preferences out of it, no ? 
CoC and all that ...

---

### Post by tgm4883 on 2010-12-10
> **koenn said:**
> [QUOTE=tgm4883;10223668]Yum, socialism. Why that sounds like an outstanding idea.QUOTE]
maybe better keep your political preferences out of it, no ? 
CoC and all that ...

Thanks for taking that completely out of context and changing it to fit how you wanted to see it. I actually went back and added that part after typing it up, as it does sound a bit like socialism. But ok, I give. I appoligize if I offended you with that statement. 

In any case, that doesn't change anything about what the OP has described he wants to or how it fails.

---

### Post by ki4jgt on 2010-12-10
I agree. It does fail. It's a new technology. It's not iron clad yet! My question here though is if you are computer a and you request information from computer z how is anyone in the middle supposed to know if you're requesting the information yourself, or just passing it along to someone else?
Socialism??? Not hardly! If I'm not mistaken, that is how the normal internet functions today. One computer relays traffic to another, but everyone in the middle knows what computer requested it and what computer hosts it.
Also take in mind, Freenet's encryption containers. How they work is everything in a particular user's node is encrypted. Not even the user knows what they have on their node to share. You simply insert your site using a program then your site is capable of being shared.
Freenet also searches for newer versions of sites every time it visits a site to make sure you have the most updated version. So if you visit a website and then 2 hours later it's updated, it will be updated to you and then when someone else visits you will serve them the updated material.

---

### Post by ki4jgt on 2010-12-10
Oh and:
> They could shut down the tracker, requiring all of your nodes to find a new tracker. Which is A) a pain, and B) downtime

There is no tracker! Or at least not a central one. Every computer is a part of the server. or Every computer is a server to every other computer.

Hard drive space. Freenet asks every user to devote an encrypted container (size is up to the user) to the network. The user can't access what's in the container. I usually do 1 gig. I haven't used it in forever though.

---

### Post by tgm4883 on 2010-12-11
> **ki4jgt said:**
> I agree. It does fail. It's a new technology. It's not iron clad yet!** My question here though is if you are computer a and you request information from computer z how is anyone in the middle supposed to know if you're requesting the information yourself, or just passing it along to someone else?**
Socialism??? Not hardly! If I'm not mistaken, that is how the normal internet functions today. One computer relays traffic to another, but everyone in the middle knows what computer requested it and what computer hosts it.
Also take in mind, Freenet's encryption containers. How they work is everything in a particular user's node is encrypted. Not even the user knows what they have on their node to share. You simply insert your site using a program then your site is capable of being shared.
Freenet also searches for newer versions of sites every time it visits a site to make sure you have the most updated version. So if you visit a website and then 2 hours later it's updated, it will be updated to you and then when someone else visits you will serve them the updated material.

It's late and I don't feel like responding to this entire post, with every post you make you seem to forget about earlier posts where people point out exactly why some part won't work. I'll play along for a little longer, but I've dealt with your type of person in the past. Your idea is flawless and anyone who objects is closeminded. Frankly it gets tiring after a while.

I'll disregard all your other points that you have forgotten about and deal with your question from your previous post. I'll answer it with another question. When the information gets passed back to computer A from computer Z. If nobody in the middle knows where it is suppose to go A) how do they know which computer to pass it to next, and B) how does computer A know that the information is for them?

---

### Post by ki4jgt on 2010-12-11
> **ki4jgt said:**
> **I agree. It does fail.** It's a new technology. It's not iron clad yet! My question here though is if you are computer a and you request information from computer z how is anyone in the middle supposed to know if you're requesting the information yourself, or just passing it along to someone else?
Socialism??? Not hardly! If I'm not mistaken, that is how the normal internet functions today. One computer relays traffic to another, but everyone in the middle knows what computer requested it and what computer hosts it.
Also take in mind, Freenet's encryption containers. How they work is everything in a particular user's node is encrypted. Not even the user knows what they have on their node to share. You simply insert your site using a program then your site is capable of being shared.
Freenet also searches for newer versions of sites every time it visits a site to make sure you have the most updated version. So if you visit a website and then 2 hours later it's updated, it will be updated to you and then when someone else visits you will serve them the updated material.

What part of **it does fail** means my idea is perfect (Flawless) Look, I understand that this idea is down right appalling. I understand that I have been arguing my points. Please tell me where I have been ignoring previous posts, b/c unknown to you, I may not understand how I was ignoring anything.

> [B]If someone wanted to put this together as a new Internet alternative:
How would they go about it?[/B]

Quote:
- Every user could potentially get an unlimited connection
- Every Server (Website) could have an unlimited connection to everyone using it!
- Every server (Website) could have the ability to experience 100% uptime
- All communications could be completely confidential between the two individuals talking and no one else.
- All using the current set of protocols we are currently using (TCP/IP)
- No one could monitor your communications
- HTML could be made simpler and still maintain it's (complete) functionality
- The Internet could be FREE (No Price)
- While maintaining proper authentication protocols (people would still be able to be traced for illegal stuff)
- Governments could not block websites
**Meaning you have to believe it's possible to make a suggestion or at least partially possible**

My question is how would they do it? I did not intend to make you upset or unsettled. I believe based on what I know about Freenet, which may not be all I need to know, that I have answered all your questions. If not, please tell me where my responses are contradicting each other. I do not believe you're too closed minded, I don't believe anyone is closed minded on Earth just a little stubborn, but stubborn makes the world go round :-) I've stated several things and you've assumingly added things to my statements. again **I know this is a fail** but the main question is how would one do it, with the condition that one must believe it's possible (As with any endevours. The person must believe what they're doing is possible or what's the point in doing it?) What we have been doing is arguing semantics. I am not arguing what is right and what is wrong here, simply requesting ideas from you. For an idea, which I believe is possible and you do not! (Which I like to do, b/c you pose the one question which no one else will - How does your system work, in all the nooks and crannies) I know it sounds like a sales pitch :-) But I am simply telling you the answers to your questions as to how I see them (I may not see everything, that's why God invented learning, so people wouldn't know everything and be all stuck up or b/c they weren't ready to accept the truth yet.) From my perspective, I am only arguing from what I know. If you know more, please tell me. You stated to me that I needed to read up on the idea and get more information, **politely I would like to say, yes, I do** and politely I would like to tell you that since I do not know everything you do, what seems to be contradicting to you, may have this huge hole missing to me. If you would like to help me, stop assuming I know something that you do. I also ask you to please (if it is not too much trouble, so reread everything, and instead of believing that I am trying to make you look **stupid**, explain to me with the mind set that maybe I actually believe it's possible and that I actually read your responses and that I am trying to respond to you the best way I know how.
Thanks and hope your night goes well.

---

### Post by 3Miro on 2010-12-11
This is getting nowhere fast.

@ki4jgt: read and study about the "7 layer model" and the connection between the hardware and software. Read about encryption, on what and how it can be encrypted. Read about the Torrent protocol as well as Freenet to see that they don't do what you think they do.

Look up Richard Stallman's view on "free hardware". Basically all hardware is free as in freedom/speech/GPL, but a lot of software is not. Software can be easily made free as in beer/cheap/charity, but hardware cannot be done in this way (until we develop Star Trek replicators).

Encryption and privacy are in direct contradiction with distributed web. Government cannot close web-sites contradicts government can catch illegal stuff like child porn. Everyone having an unlimited (or up to the limits of the hardware) connection is not possible either, read on how exactly the torrents work.

If such a perfect web could be achieved, I would be the first on board, but you want dry water and 2+2=5.

---

### Post by koenn on 2010-12-11
> **tgm4883 said:**
> 
Thanks for taking that completely out of context and changing it to fit how you wanted to see it. I actually went back and added that part after typing it up, as it does sound a bit like socialism. But ok, I give. I appoligize if I offended you with that statement. 

Hm, I can somewhat see why you'd call the phrase I quoted  "out of context" - I didn't quote the entire post to make it clear I was not responding to what you posted, other than the part I quoted. 

Apparently you didn't get what I was saying, so let me spell it out for you:

a/ Liking the OP's idea to "socialism" is about as silly as calling Open Source "communist". 
(and Linux is an  illegal hacker operation system, invented by a Soviet computer hacker named Linyos Torovoltos, It is used by hackers to break into other people's computer systems to steal credit card numbers) (1)

b/ calling something "socialism" because you disagree with it indicates you disagree with socialism. That's opening the door to a discussion on politics. 

c/ labeling something "socialism" to put it in a bad light only works well in that small part of the world where socialism is considered evil. 


There, 3 good reasons why you had better left that remark out of your post. Sorry that I seem to be making such a big deal out of it, but apparently the 2 sentences I posted earlier were insufficient for you to get my point. 

Oh, and thanks for the conditional apology. 



---
(1) [http://www.adequacy.org/stories/2001.12.2.42056.2147.html](http://www.adequacy.org/stories/2001.12.2.42056.2147.html)

---

### Post by tgm4883 on 2010-12-11
> **ki4jgt said:**
> What part of **it does fail** means my idea is perfect (Flawless) Look, I understand that this idea is down right appalling. I understand that I have been arguing my points. Please tell me where I have been ignoring previous posts, b/c unknown to you, I may not understand how I was ignoring anything.



My question is how would they do it? I did not intend to make you upset or unsettled. I believe based on what I know about Freenet, which may not be all I need to know, that I have answered all your questions. If not, please tell me where my responses are contradicting each other. I do not believe you're too closed minded, I don't believe anyone is closed minded on Earth just a little stubborn, but stubborn makes the world go round :-) I've stated several things and you've assumingly added things to my statements. again **I know this is a fail** but the main question is how would one do it, with the condition that one must believe it's possible (As with any endevours. The person must believe what they're doing is possible or what's the point in doing it?) What we have been doing is arguing semantics. I am not arguing what is right and what is wrong here, simply requesting ideas from you. For an idea, which I believe is possible and you do not! (Which I like to do, b/c you pose the one question which no one else will - How does your system work, in all the nooks and crannies) I know it sounds like a sales pitch :-) But I am simply telling you the answers to your questions as to how I see them (I may not see everything, that's why God invented learning, so people wouldn't know everything and be all stuck up or b/c they weren't ready to accept the truth yet.) From my perspective, I am only arguing from what I know. If you know more, please tell me. You stated to me that I needed to read up on the idea and get more information, **politely I would like to say, yes, I do** and politely I would like to tell you that since I do not know everything you do, what seems to be contradicting to you, may have this huge hole missing to me. If you would like to help me, stop assuming I know something that you do. I also ask you to please (if it is not too much trouble, so reread everything, and instead of believing that I am trying to make you look **stupid**, explain to me with the mind set that maybe I actually believe it's possible and that I actually read your responses and that I am trying to respond to you the best way I know how.
Thanks and hope your night goes well.

I've already said why each thing won't work, as have other people. I don't think you are trying to make us look stupid, I think you do believe this will work. The issue is when people explain why a point won't work you dismiss their claim. 

Your idea won't work because you want to replace the internet for free. The reason freenet works right now is that it is built on top of existing infrastructure that people pay for. Some of your points may work, others won't, and some of your points contridict other points (as said in previous posts).

As for you ignoring posts

Post #12
> 
Let me try to clarify that another way. Mindy has only contributed her computer. She herself has no ISP, she gets her internet from joe, who gets his internet from fred, who gets his internet connection from you (you get it from comcast in this scenario). Mindy, joe, and fred don't have a comcast internet connection, so now you are paying for an internet connection for everyone. Such a nice guy you are, but you should probably upgrade your comcast plan since your connection is getting saturated.


Your response to that will be that you need no comcast connection as everyone is in an ad-hoc mesh. OK, lets go down that road.

Take Las Vegas. Very populated, but roughly isolated. Everyone there is connected via the ad-hoc mesh. How does someone in Las Vegas go to NYTimes.com and read that website? Surely the ad-hoc mesh isn't going to reach from Las Vegas to a surrounding city.


Post #19
> 
When the information gets passed back to computer A from computer Z. If nobody in the middle knows where it is suppose to go A) how do they know which computer to pass it to next, and B) how does computer A know that the information is for them?

---

### Post by ki4jgt on 2010-12-11
Firstly: no part of this is based on socialism. It's still plain republic democracy. The people who put in the best still get the best service. If you stay connected constantly, your computer gets a webpage faster than other users because you've had more exposure to other people requesting it from you and have had to tunnel it to them. If you're upset because your computer will be used to bring other people services without you knowing it, that happens every day on the job. You know what the service is, but you have no idea how it's used afterwards. Your pay would be the faster service to your self for the amount you have put into the Internet. That's pretty much how it works now. When ATT asks you to pay for it. They have local access to I don't know how many sites which they host. Because of the encryption, you will be able to host sites and not be able to hack them. So you will have local access to the ones you have forwarded. If the site hasn't updated. You will pull it directly from your 1 gig cache.

Secondly: If Freenet can do everything I've described, except databases, forms, and being able to trace who or where a user is requesting a website from over the Internet or a LAN, why can we not find a way to implement databases and forms and tracking into Freenet and since it already has the possibility to run over LAN, Netsukuku shouldn't be that hard to add to it, especially since Netsukuku is simply creating a Network.
Furthermore. No central tracker is needed by Freenet and it does all mentioned and more (Except it does it through the Internet.) I don't care how much you argue with the sign post, it's still there and the proof is in the pudding!

EDIT: sorry TGM I did not see your last post before I was able to get this one up :-)

---

### Post by tgm4883 on 2010-12-11
> **koenn said:**
> Hm, I can somewhat see why you'd call the phrase I quoted  "out of context" - I didn't quote the entire post to make it clear I was not responding to what you posted, other than the part I quoted. 

Apparently you didn't get what I was saying, so let me spell it out for you:

a/ Liking the OP's idea to "socialism" is about as silly as calling Open Source "communist". 
(and Linux is an  illegal hacker operation system, invented by a Soviet computer hacker named Linyos Torovoltos, It is used by hackers to break into other people's computer systems to steal credit card numbers) (1)

b/ calling something "socialism" because you disagree with it indicates you disagree with socialism. That's opening the door to a discussion on politics. 

c/ labeling something "socialism" to put it in a bad light only works well in that small part of the world where socialism is considered evil. 


There, 3 good reasons why you had better left that remark out of your post. Sorry that I seem to be making such a big deal out of it, but apparently the 2 sentences I posted earlier were insufficient for you to get my point. 

Oh, and thanks for the conditional apology. 



---
(1) [http://www.adequacy.org/stories/2001.12.2.42056.2147.html](http://www.adequacy.org/stories/2001.12.2.42056.2147.html)

No, I got your point. You were offended and someone may construe my post as having a political (Which is against the forum rules) point of view. I'd hope that open minded individuals would look past the idea that socialism is strictly a political idea and entertain the thought that my post was talking about the logistics behind the OP's idea.

Also, did you expect more than a conditional apology? I mean, if I didn't offend you what am I apologizing for?

In any case, it was a passing remark and it's done. I could go back and delete it to make you happy but what's the point.

---

### Post by tgm4883 on 2010-12-11
> **ki4jgt said:**
> Firstly: no part of this is based on socialism. It's still plain republic democracy. The people who put in the best still get the best service. If you stay connected constantly, your computer gets a webpage faster than other users because you've had more exposure to other people requesting it from you and have had to tunnel it to them. If you're upset because your computer will be used to bring other people services without you knowing it, that happens every day on the job. You know what the service is, but you have no idea how it's used afterwards. Your pay would be the faster service to your self for the amount you have put into the Internet. That's pretty much how it works now. When ATT asks you to pay for it. They have local access to I don't know how many sites which they host. Because of the encryption, you will be able to host sites and not be able to hack them. So you will have local access to the ones you have forwarded. If the site hasn't updated. You will pull it directly from your 1 gig cache.

Secondly: If Freenet can do everything I've described, except databases, forms, and being able to trace who or where a user is requesting a website from over the Internet or a LAN, why can we not find a way to implement databases and forms and tracking into Freenet and since it already has the possibility to run over LAN, Netsukuku shouldn't be that hard to add to it, especially since Netsukuku is simply creating a Network.
Furthermore. No central tracker is needed by Freenet and it does all mentioned and more (Except it does it through the Internet.) I don't care how much you argue with the sign post, it's still there and the proof is in the pudding!

EDIT: sorry TGM I did not see your last post before I was able to get this one up :-)

Thats ok that you missed it, you can still respond to it.

Other than home user sites and possible their own company sites, I don't think ATT hosts any sites.

It appears you have tossed out the idea of the Internet being free (as in beer) and given up the wireless adhoc mesh idea. That's good, as it was probably the most impossible part of your idea. Please let me know if that is the case.

---

### Post by ki4jgt on 2010-12-11
Ok, I did not intend for world war 3 to break out here. I just wanted to know if someone wanted to do it how they would. Some how semantics got involved and then politics. People stop making a mountain out of a mole hill.
I'm sorry. I'm sorry, I'm sorry. I honestly did not mean to offend anyone. I just wanted to know how to do it. I thought it would be neat. Then I got responses explaining it wasn't possible so I answered them the best way I could. Then people get upset about it! Look, I think it is possible. I'm just explaining why the same as everyone explaining why they think it isn't. I did have an answer to tgm's response but if WWIII is going to break out, then I'm leaving. I left that drama back in High School where everyone had to prove they were right and if someone had an arguement they were so upset because that person didn't understand or what not!

---

### Post by ki4jgt on 2010-12-11
Now, concerning the wireless thing, I still have that. That's what Netsukuku is. It's wireless. In my opinion cities are so close today it wouldn't be impossible. I understand there are remote areas these areas of course would have to have lines or satelites but in the cities in general Internet would be free and would require little to no maintainace.

Simple they pass it to the computer which requested it from them. Computer A would receive it b/c it knows it requested it.

---

### Post by tgm4883 on 2010-12-11
> **ki4jgt said:**
> Now, concerning the wireless thing, I still have that. That's what Netsukuku is. It's wireless. In my opinion cities are so close today it wouldn't be impossible. I understand there are remote areas these areas of course would have to have lines or satelites but in the cities in general Internet would be free and would require little to no maintainace.

And thus not free. It requires a great deal of money for those lines between cities. And no, cities aren't close enough together for it to just be wireless. Maybe in the northeast US, but not the western US and certainly not the rest of the world (don't forget to think globally ;) )


> **ki4jgt said:**
> 
Simple they pass it to the computer which requested it from them. Computer A would receive it b/c it knows it requested it.

This is circular logic. All the information that each computer is passing is encrypted so no computer in the middle knows what is in the package or where it is going, yet magically knows the next computer to send it to. 

As for Computer A, since no computer in the middle can know what is in the package or where it is going, how would computer A know that the package of information that was just received is for Computer A and not supposed to be passed on?


Let me try to this graphically. Take a look at the attached image. If computer B receives some encrypted information, how does it know who to pass it to or if the information is for B?

---

### Post by ki4jgt on 2010-12-11
I'm working on that part. Freenet merely passes the information as stated above from one encrypted container to another (I think) LOL. Still looking into that as requested from 3miro. But if the information was encrypted such as bank information or login data, The two sources would have to be identifiable. You're right on that one.
So yes, if you posted to an encrypted site a and z would have to identify with each other. But for normal sites the circular logic isn't bad.
That's one of the things I'm still ironing out, but when the Internet first started it didn't even have encryption.

***EDIT: As stated above the computer which found the information would pass it to the one which requested it. Example

A requests package 5 P2P client like in Freenet
B requests package 5
C has package 5
C says B requested package 5
C sends package 5 to B
B says A requested package 5
B sends package 5 to A
A says I requested package 5
A opens package 5

***EDIT: A, B, and C now have package 5

***EDIT Change ABC to ALC so the picture above makes better since.

---

### Post by Austin25 on 2010-12-11
@ki4jgt: What you are asking for is a distributed peer to peer network with unlimited bandwidth and security free of charge, correct? While it is good to dream, unfortunately this is impossible, similar to asking, "Why not convert everyone to jetcars, and have everyone share jet fuel so nobody runs out?" One more problem is even if it was possible, it would be extremely difficult to convert everybody to it, similar to the IPv6 dilemma.

@everyone else: Don't yell at those who are uninformed. This is ubuntuforums, not 4chan.

---

