---
title: "How an application in a web browser finds your ip?"
date: 2010-05-28
forum: Security
---

### Post by johnkills on 2010-05-28
I am a newbie so try to follow my newbie logic. :)

Lets say you visit a website and the website starts an application in java or flash. That application can reveal your IP, even if you are using proxy but how does it do it?

I think the application starts and it asks the computer for the IP and that information must be stored somewhere in a file. It must be written somewhere what is your IP so it can send it.  
Their talk I think is something like: 

**_Application_** says "computer what is your IP?"
**_Computer_** says "let me check in that file.. oh it is xxx.xxx.xx.xx, got that?"
**_Apllication_** says "sure, I got your IP and I will store that for security reasons so I know who was using my application"

But my question is since the application like any software follow a path of execution or whatever you call it and after that first talk about what is you IP, it will do other things. If it is an online game, lets pretend the talk they will do after it is to download image for the game. 
So their talk will be something like:  
_**Computer**_ says "application, can you send the images to the game?"
**_Application_** says "here, take the images"

So in that other talk, if one were to analyze the packets going back and forth, they could see the IP of whoever is downloading. But if you dont analyze, if you dont capture the packets, that information will be forever gone. 

The question really is if the _**Computer**_ lied to the **_Application_** in that first talk and said a false IP, do you think the application would continue to work and do things like download images and other information for the online game? Because I think it would work fine. Since the**_ Application_** knows what it wants and where it is located and when it asks for information it needs, it will find it and receive it. 

If I didnt explain very well my question, tell me and I will write and make graphs to show you what I want to say. Thanks

---

### Post by marcottebj on 2010-05-28
You're IP address is the Internet Protocol address, and it's the basis for all communication within a network such as the internet.  If you send a request to a web server (for instance), you are asking for it to return a page to your IP address on a certain port such as XXX.XXX.XXX:80    If your computer didn't provide it's IP address, then you wouldn't receive a response from the web server, so your page would never be displayed.  
 
In the case of NAT, you have an inside IP which is masked by your router.  The router handles all requests on behalf of the host PC, and forwards responses back to the appropriate client,  by caching a list of requests from each host connected to it.  
 
This is a bit of an over simplification, but for more information you need to research TCP/IP and UDP.

---

### Post by johnkills on 2010-05-28
> **marcottebj said:**
> You're IP address is the Internet Protocol address, and it's the basis for all communication within a network such as the internet.  If you send a request to a web server (for instance), you are asking for it to return a page to your IP address on a certain port such as XXX.XXX.XXX:80    If your computer didn't provide it's IP address, then you wouldn't receive a response from the web server, so your page would never be displayed.  
 


Sure but for security reasons a web application often stores or check an IP address. In order to do that storing/checking it must somehow ask for the information. After that, it will do a lot of things and of course those things require my IP address for it to receive or send information but I dont believe the application will check again my IP to store it for security reasons. If there was a network admin analyzing the connection, it would see the packets and those would contain my IP of course. But if it wont analyze the packets, how could they see my IP if I provided a false one?  That is if the application worked. 

Let me give you a fine example: 

Youtube. Some countries cant use it. So a user goes to their website and when they try to see a video, it says : "Video is not allowed in your area" How do they know my IP? They must ask for it and that information must be sent in the form of a packet. So if I supplied it a different one, would I still be able to make the following connection to download the video packets?

---

### Post by johnkills on 2010-05-28
My point is the web application WONT analyze the traffic of packets, that is not how it will find you IP. It WILL ask for it. 
Is it true?

---

### Post by Penguin Guy on 2010-05-28
> **johnkills said:**
> My point is the web application WONT analyze the traffic of packets, that is not how it will find you IP. It WILL ask for it. 
Is it true?
No; your computer probably doesn't even know it's IP address, the website automatically detects it. You can get around this by using a proxy or another anonymity service like [TOR]("http://www.google.com/search?q=TOR").

---

### Post by marcottebj on 2010-05-28
Exactly!  It's not "asking" for an IP.  You'd have to use a proxy or anonymizer of some sort to forward requests back to you.  IP isn't used at the application layer.

---

### Post by Lucky. on 2010-05-29
> I am a newbie so try to follow my newbie logic.

Dude, you have pretty good logic for a newbie.  Your post is well thought out.

> That application can reveal your IP, even if you are using proxy but how does it do it?

I think I understand you here, but just want to clarify.  Your actual IP address shouldn't be shown via a proxy.

Let's say you're behind a home router, and your computer's address is something like 192.168.0.54.  You can find out your computer's IP address by typing the following into the Linux terminal:

```
ifconfig
```

Or typing the following into the Windows command prompt:

```
ipconfig
```

Even though that 192.168.xxx.xxx (The "xxx" isn't literal, it could mean any valid 8 bit number) address is your computer's actual address, it probably won't show up in web applications.  

Why?  We'll get to that in a moment.  But bear with me.  If your theory was true (Web applications ask for your computer's IP address and then report it), then the 192.168.xxx.xxx address **would show up**.  But it doesn't.

In case you already didn't know, 192.168.xxx.xxx addresses are private addresses...meaning they're only used on home networks, never in the open Internet.  At home you probably only have a single "public"/"real" IP address, which your router uses.  Think about it - if you have more than one computer at home using the net, but you only have one IP address....how does that work?

It works because your router claims your "real" IP address, and then gives everyone else in your home those private 192.168.xxx.xxx addresses.  It uses NAT/PAT (Network Address Translation / Port Address Translation) to run multiple IP addresses and their connections over a single IP address.  This is what marcottebj was saying.

With all that said, every time you use a web app that displays your IP address, you probably don't see a 192.168.xxx.xxx number (your computer's actual IP address).  Instead, you might see some other number like 74.82.31.132 or so.  This IP address is the *external* address of your home router...which is your public/non-private IP address.

Try it out!  [Click here](http://whatismyipaddress.com/).

The address that shows up in the link above should be the address that always shows up in web applications - no matter what computer you're using in your house behind the router...the external IP address should be the same because all of your computers are routed through that single IP address by your router.

**Note:  Your computer has no knowledge of the external IP address the router is using.  Your computer still thinks it has an internal private address of 192.168.xxx.xxx.  Likewise all web servers will have no knowledge of the private 192.168.xxx.xxx address...they will think your computer is at the address found in the link above.**

Now let's say that you decide to use a web proxy.  Try this test.  Visit the link above before and after you use a web proxy.  The addresses should be different.  This is because your connection is routed through someone else's server.  The proxy will communicate with any web sites itself, and give you the results.  So as far as the web servers know, they think your IP address is that of the proxy.

Note that in all of these scenarios, at no point is a web app on your computer asking your PC "Hey what's my IP address so I can report this?"  Instead, the IP protocol sends out your return address when you talk to a gateway or server.

Take a look at the following picture (a diagram of an IP header which gets sent out with every packet), and notice the "32-bit source" and "32-bit destination" address:

[Look here](http://www.enderunix.org/docs/en/rawipspoof/ipheader.png)

When you use a web browser to connect to a web page, it sends IP packets with this stuff all filled out.  However technically your web browser doesn't actually fill this stuff out and send it - your networking subsystems do the dirty work.  This is why marcottebj said:

> IP isn't used at the application layer.

Your web browser works at the application layer of the [OSI model](http://www.petri.co.il/images/osi_model.JPG).  IP works at the network layer, which as you can see is a far shot from the application layer (Each layer mostly operates on its own without knowing how the other ones work, so web browsers don't need to know your own IP address to run correctly).

With all of that said, web servers know your IP address because it works just like mail.  When your computer sends out an IP header, it fills out the source and destination address.  Whomever gets the packet gets the return address.  This is how web servers know your IP address.  And if the web server knows your IP address, it can send that information right back through your web application.

> My point is the web application WONT analyze the traffic of packets, that is not how it will find you IP. It WILL ask for it.

You're both right and wrong.  A web application on your computer won't analyze the traffic of the packets.  But it won't ask its own PC for the address either.  Instead the web server will analyze the packets, get the return address from the IP header, and then report it through your web application.

The funny thing is - when your computer sends out an IP header, your router picks it up and changes the header (NAT/PAT) and puts down its own return address.  When you run through a proxy, it can either change the header and put down its own return address, or it just makes a whole new connection of its own, and "bridges" information from its connection to the server with your connection to the proxy.

All in all, servers are simply looking at the return address, which is a requirement for valid IP communication.  At no point is your web browser or web application checking in on its own IP address and reporting it.  If this was the truth, most everybody would be reporting the wrong IP address (since we'd all be reporting private addresses instead of our external public ones).

Sheesh, that was long.  I hope I didn't make this worse.

Note that I use the term "web application" liberally.  For most people, web application means "web site."  For here we're talking about Flash / Java, right?

---

### Post by teh_drizzle on 2010-05-29
Nice post!

---

### Post by Rubi1200 on 2010-05-29
+1 to that! Excellent explanation in clear and coherent language.

:)

---

### Post by johnkills on 2010-05-29
> **Lucky. said:**
> Dude, you have pretty good logic for a newbie.  Your post is well thought out.



I think I understand you here, but just want to clarify.  Your actual IP address shouldn't be shown via a proxy.

Let's say you're behind a home router, and your computer's address is something like 192.168.0.54.  You can find out your computer's IP address by typing the following into the Linux terminal:

```
ifconfig
```Or typing the following into the Windows command prompt:

```
ipconfig
```Even though that 192.168.xxx.xxx (The "xxx" isn't literal, it could mean any valid 8 bit number) address is your computer's actual address, it probably won't show up in web applications.  

Why?  We'll get to that in a moment.  But bear with me.  If your theory was true (Web applications ask for your computer's IP address and then report it), then the 192.168.xxx.xxx address **would show up**.  But it doesn't.

In case you already didn't know, 192.168.xxx.xxx addresses are private addresses...meaning they're only used on home networks, never in the open Internet.  At home you probably only have a single "public"/"real" IP address, which your router uses.  Think about it - if you have more than one computer at home using the net, but you only have one IP address....how does that work?

It works because your router claims your "real" IP address, and then gives everyone else in your home those private 192.168.xxx.xxx addresses.  It uses NAT/PAT (Network Address Translation / Port Address Translation) to run multiple IP addresses and their connections over a single IP address.  This is what marcottebj was saying.

With all that said, every time you use a web app that displays your IP address, you probably don't see a 192.168.xxx.xxx number (your computer's actual IP address).  Instead, you might see some other number like 74.82.31.132 or so.  This IP address is the *external* address of your home router...which is your public/non-private IP address.

Try it out!  [Click here]("http://whatismyipaddress.com/").

The address that shows up in the link above should be the address that always shows up in web applications - no matter what computer you're using in your house behind the router...the external IP address should be the same because all of your computers are routed through that single IP address by your router.

**Note:  Your computer has no knowledge of the external IP address the router is using.  Your computer still thinks it has an internal private address of 192.168.xxx.xxx.  Likewise all web servers will have no knowledge of the private 192.168.xxx.xxx address...they will think your computer is at the address found in the link above.**

Now let's say that you decide to use a web proxy.  Try this test.  Visit the link above before and after you use a web proxy.  The addresses should be different.  This is because your connection is routed through someone else's server.  The proxy will communicate with any web sites itself, and give you the results.  So as far as the web servers know, they think your IP address is that of the proxy.

Note that in all of these scenarios, at no point is a web app on your computer asking your PC "Hey what's my IP address so I can report this?"  Instead, the IP protocol sends out your return address when you talk to a gateway or server.

Take a look at the following picture (a diagram of an IP header which gets sent out with every packet), and notice the "32-bit source" and "32-bit destination" address:

[Look here]("http://www.enderunix.org/docs/en/rawipspoof/ipheader.png")

When you use a web browser to connect to a web page, it sends IP packets with this stuff all filled out.  However technically your web browser doesn't actually fill this stuff out and send it - your networking subsystems do the dirty work.  This is why marcottebj said:



Your web browser works at the application layer of the [OSI model]("http://www.petri.co.il/images/osi_model.JPG").  IP works at the network layer, which as you can see is a far shot from the application layer (Each layer mostly operates on its own without knowing how the other ones work, so web browsers don't need to know your own IP address to run correctly).

With all of that said, web servers know your IP address because it works just like mail.  When your computer sends out an IP header, it fills out the source and destination address.  Whomever gets the packet gets the return address.  This is how web servers know your IP address.  And if the web server knows your IP address, it can send that information right back through your web application.



You're both right and wrong.  A web application on your computer won't analyze the traffic of the packets.  But it won't ask its own PC for the address either.  Instead the web server will analyze the packets, get the return address from the IP header, and then report it through your web application.

The funny thing is - when your computer sends out an IP header, your router picks it up and changes the header (NAT/PAT) and puts down its own return address.  When you run through a proxy, it can either change the header and put down its own return address, or it just makes a whole new connection of its own, and "bridges" information from its connection to the server with your connection to the proxy.

All in all, servers are simply looking at the return address, which is a requirement for valid IP communication.  At no point is your web browser or web application checking in on its own IP address and reporting it.  If this was the truth, most everybody would be reporting the wrong IP address (since we'd all be reporting private addresses instead of our external public ones).

Sheesh, that was long.  I hope I didn't make this worse.

Note that I use the term "web application" liberally.  For most people, web application means "web site."  For here we're talking about Flash / Java, right?



Thanks you for your post. Dont worry if you wrote too much, it only shows you want to explain yourself really well and it is good. 


The first part of your message about internal or external IPs/address.. Well for me it is the same. 

If I type "ifcongig", it shows under ppp0 my inet addrs: xxx.xxx.xxx.xxx is the same as my external address if I check a website that shows my ip. It is always the same. I only use one computer and it is connected directly to my ADSL modem, if that is the correct way to call it. If I disconnect and connect again my ip changes, therefore I think you would call it a dynamic IP. The only thing that never changes for me it is the IP of the first machine I "talk" to make connections over the internet. But then again that is another subject we can talk later.



Then the second part of your message..  It makes sense that an IP packet had "destination" and "source" adresses so it knows where it comes from and where it is going. If you think about the Tor project, it works fine but you are not able to use flash/java or it would display your real IP. My guess is that flash application dont use the same protocol to communicate over the web. if you use a normal proxy and you visit a website that requeries plugins. Your real IP will be revealed. Most people think they are hiding with a regular proxy but that is false if you use flash/java. 

I remind that once I used a software that would "encapsulate" or another term all protocols and would direct it to HTTTP so everything I used was encapsulated in that and all flash/java would only communicate over Tor and not around it like a regular proxy. I checked that with Wireshark and it went well. It was the only software using the internet and all its traffic was being encapsulated inside of Tor. All protocols were using tor. So I just answered half of my own question, then I agree with you. The application you download, either flash/java wont check the machine for the ip. It wont ask the machine for it, you are right and the others who said the same thing. But the server you are connecting will.

So we are left with that, the server will check your packets and register the IP but what packets? all of them? I highly doubt it. I think it would work like this... 

1. Java/flash makes a connection with the server.

2.  Then the SERVER analyzes ONE of tha packets and it says that back to you. "You are logged in with IP xxx.xxx..xxx.xxx" 
If you were using an online game and that online game registered IP addresses for security reasons. I think it would analyze only one of the packet and register that address in the database. Of course that for communicating with you it must know the address of all returning packets. Sure but for security reasons I think the server will analyze only one. So If I was able to send a false packet for that, it would analyze that packet, register that IP and continue to work normally. 

So if I wanted to "fool" a website into thinking I am from another country. I would first make a normal connection and capture all the packets with wireshark. Then if I knew what packets the server analyzes to determine my IP, I would either change the header of those IP packets or dont send them. Then I would send those modified packets again and when the SERVER checked those packets to see my IP, it would think I am from another country but all other packets would be normal and the application/game would work normally.  Well I think the packet the server analyze to determnie your IP is not necessary for the normal working of the web application. I think it is only an "empty" packet you send so the server can check it. All other packets that are required for the application to work would contain my true destination IP so I could receive. But in my "theory", only guessing, that packet is not necessary for the normal working of that application. 

I hope that all makes sense to someone. 

PS: Half of what I asked is already solved. I believe from reading other responses that an application wont ask my computer what is my IP but the SERVER that will analyze some packets. It is not all solved yet with that little doubt about when the server analyzes it. If anyone knows when the server does it, I would appreciate that.


Thank you :)

---

### Post by johnkills on 2010-05-29
Wait...

I was starting to believed IP is only checked by the server and not at your computer.

How is that possible? Is that code run on the server or your computer?

[http://www.rgagnon.com/javadetails/java-0390.html](http://www.rgagnon.com/javadetails/java-0390.html)

Right in the end it says: "To get the IP of a client from the server side, see this [HowTo]("http://www.rgagnon.com/javadetails/java-0363.html")."  So that phrase means it was checking the IP from the client side. Therefore asking the computer "what is the IP?" instead of analyzing the packets.

---

### Post by OpSecShellshock on 2010-05-29
Well no, the linked page actually says you won't get the real IP address if it's behind a proxy, unless it's one that has the x-forwarded-for string included in the http header.

I think you're possibly confusing identification details here, though. If you're behind a proxy, your IP address will not be accurately represented to the server you're accessing. However, there's more to your computer than just its IP address. It could be looking at all the other information contained in the http headers (for example the user-agent), but not all proxies necessarily send that information on. In any case, I think Firefox has extensions for manipulating headers.

But there are even more things that can be done. If you store cookies in order to maintain logins across sessions, then those will be accessible to scripts that are authorized to ask for them. They may contain unique identifiers. All manner of content stored in the browser's folders can be accessed in the same way. Part of that is because the servers want to make sure that your system is compatible with whatever they're hosting. Your OS can be revealed, the paths to files being accessed can possibly be revealed, loaded fonts, and on and on. If you've got an extension blocking ads and scripts the server can probably see that, too.

An IP address in and of itself is really not a very useful piece of information to have when you're talking about identification. I mean, if you're on a major ISP's home network block, the most anyone would be able to get from looking at your real IP address is the name of your ISP and the country you're in. It's the other identifiers that can be associated with user accounts and activities that most commercial sites are really interested in. Then again why would anyone go to the trouble of setting up a proxy or otherwise hiding their IP address only to log into their email account and other places that require specific authentication? It doesn't really make sense.

---

### Post by johnkills on 2010-05-29
> **OpSecShellshock said:**
> Well no, the linked page actually says you won't get the real IP address if it's behind a proxy, unless it's one that has the x-forwarded-for string included in the http header.
 

Maybe I was not clear in what I intend to do. I want to access a webpage/onlinegame with my IP but I dont want the website to get it right. I DONT want to use any proxy/Tor.

Again, **NO PROXY** between me and the website.  If the website use plugins to send my IP information in form of packet, inside of packets, I want to block those packets and if the website find my IP analyzing packet headers from some of my packets I want to know which packets is it analazying so I can alter them and still be able to use all things on that onlinegame websiite. 

There are only two ways I see a website can find your IP:

1. It has a software in your computer (java/flash) that finds your IP asking it. Then after it finds your IP, it puts it inside a packet and sends it to the server. The server reads the information inside of the packet and stores it as your IP. Many people said that is not possible and I almost agree with them. I will agree when someone explain to me how that java code above really works.

2. The second way it could find you IP is to look the packet headers but I dont believe it looks in ALL packets, always checking. I think it looks in some packets for the information and records it once. If I know which packet it is doing its analyses I could stop sending it or change it. 


>  Then again why would anyone go to the trouble of setting up a proxy or otherwise hiding their IP address only to log into their email account and other places that require specific authentication? It doesn't really make sense.Well.. well..well..

well well then well and well again.

---

### Post by Bachstelze on 2010-05-30
> **johnkills said:**
> 
There are only two ways I see a website can find your IP:


The problem is that here we're not talking about regular websites that use only HTTP and HTML files. We're talking about Flash/Java applications, and those applications are just that: applications. Just like a C or Python program, they can do basically anything. For example, they could just call whatismyip.com and get your IP from there. There are countless ways an application could get your IP, and unless you have access to its source code, you have no way of knowing how it actually does it.

---

### Post by johnkills on 2010-05-30
> **Bachstelze said:**
> The problem is that here we're not talking about regular websites that use only HTTP and HTML files. We're talking about Flash/Java applications, and those applications are just that: applications. Just like a C or Python program, they can do basically anything. For example, they could just call whatismyip.com and get your IP from there. There are countless ways an application could get your IP, and unless you have access to its source code, you have no way of knowing how it actually does it.
Yeah but in your example, I would want to know how whatismyip.com does it, not the original application. Really, can you think of another way besides checking your computer network settings or analyzing the packet headers? It would be impossible to have any other way. 

I dont need all but how java would get your ip? Someone explain to me how it analyze the packets or how a webserver analyzes it. 

If anyone know, I am guessing someone should know.

---

### Post by Bachstelze on 2010-05-30
> **johnkills said:**
> Yeah but in your example, I would want to know how whatismyip.com does it, not the original application.

In that case, whatismyip would do it as it usually does: just reading the IP stored in the packets. A Java application, even when running "inside" Firefox, is a completely separate application and will not use the Firefox proxy settings.

As to how a website can actually get your IP address, there are also a lot of ways to do that, one is the $_SERVER PHP superglobal ($_SERVER['REMOTE_ADDR']).

---

### Post by johnkills on 2010-05-30
> **Bachstelze said:**
> In that case, whatismyip would do it as it usually does: just reading the IP stored in the packets. 


That is what I am saying! I mean sure it will analyze packet header for your IP information. But EVERY packet you exchange with the server? Everyone of them? If you go to an website and log in, download image and videos.   I think it would go something like..

 Log in..
Then right there the server would analyze some packets to get you IP and store it for security reason but are those packets really necessary to log in or only "empty packets" you send so it can get your IP? Lets say it is empty packet and you dont send those packets and you are able to log in. 

Then you download images and movie and in ALL those packets it would contain your IP but is the server checking and storing that information?  I think the server only knows that information when it is happening. Since the server thinks.. "oh well, we already got the IP when he logged in" .. So after I am gone and the server admin would check the IP of whoever logged in, wait, there are no packets. I never sent it.

---

### Post by Bachstelze on 2010-05-30
You are talking about two different things here.

First, we have the actual web server (Apache). It knows your IP from as soon as you connect to it until the connection is closed. Your IP can never change in-between: if it does, you have to reconnect using the new IP.

Then the "login" mechanism in a website. Those can use a variety of methods to "recognize" a user (cookies, session variables, etc.) and how exaclty it would handle an IP address change or how it would store the IP is application-dependent.

---

### Post by Bachstelze on 2010-05-30
You are talking about two different things here.

First, we have the actual web server (Apache). It knows your IP from as soon as you connect to it until the connection is closed. Your IP can never change in-between: if it does, you have to reconnect using the new IP.

Then the "login" mechanism in a website. Those can use a variety of methods to "recognize" a user (cookies, session variables, etc.) and how exaclty it would handle an IP address change or how it would store the IP is application-dependent.

---

### Post by Bachstelze on 2010-05-30
You are talking about two different things here.

First, we have the actual web server (Apache). It knows your IP from as soon as you connect to it until the connection is closed. Your IP can never change in-between: if it does, you have to reconnect using the new IP.

Then the "login" mechanism in a website. Those can use a variety of methods to "recognize" a user (cookies, session variables, etc.) and how exaclty it would handle an IP address change or how it would store the IP is application-dependent.

---

### Post by Bachstelze on 2010-05-30
You are talking about two different things here.

First, we have the actual web server (Apache). It knows your IP from as soon as you connect to it until the connection is closed. Your IP can never change in-between: if it does, you have to reconnect using the new IP.

Then the "login" mechanism in a website. Those can use a variety of methods to "recognize" a user (cookies, session variables, etc.) and how exaclty it would handle an IP address change or how it would store the IP is application-dependent.

---

### Post by johnkills on 2010-05-30
> **Bachstelze said:**
> how it would store the IP is application-dependent.
I think you are right from when you say that. So each application like you said before has a way of finding your IP.  

You said that after you estabilish a connect with a server, it cant be changed, I agree with that too. But if you download and image and a video, that is 2 connections, right? 

With that in mind, lets say someone has in their website a flash application and that application does three things. Show your IP, download an image and download a video. Only those things. 

If when that flash application starts running, it will...

1. Execute some actions to show your IP, so it would send the server some packets then right there. I would change the information of those packets or stop it. That functionallity of that flash application would be compromised, it wouldnt show your IP since you never returned those packet.

But then the flash application would move to dowload a image and a video and that I would allow to go like the application wants it. So do you think the flash application would work if the first step failed?  Do you think it would proceed and download the image or video in the other steps or do you think after I blocked all packets in step 1 the rest of that flash application would stop to execute? 

Thanks

---

