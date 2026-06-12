---
title: "How can I use Ubuntu Server at Work???"
date: 2008-03-22
forum: Server Platforms
---

### Post by brown_ghost on 2008-03-22
Ok let me start by saying that I have learned how to setup and maintain my network at work through reading on sites like this. I work for this small company that has three offices in different cities and our work consist of scanning large quantity of documents to pdfs or tiffs and printing such quantity using high speed printers. I have created two separate networks for two of our offices, our scanning computers and printers are on it’s own internal network with no access to the internet except though one of the servers, our computers in the office are on another network with access to the internet. The third office is pretty small so everything is connected to the internet under same network. At main office we use QBooks for our financial  business and we use this other software to create and keep track of  our jobs, this other software uses a Microsoft database file to store the info. On main office the computers in the office have the application installed and the Microsoft database resides in one of our 2003 servers, I have install the application in the other offices but to access and write the database it takes about 5-10 second delay which to my boss its unpractical, so what I have done is have the other offices log in to the server via remote desktop and run the application from the server, I have 10 terminal cals on that server. I’ve also linked all three offices via vpn connecting Netgear router to router which makes things easier to see other computers from other offices without having to run an app. to log in vpn. Any ways I also have another server that I use as a file server to transfer files between networks both internal and external and I also use it as ftp server, I have another server with same specs at second office.
[IMG]http://i6.photobucket.com/albums/y210/joe_90015/CorporateOffice.jpg[/IMG]


[IMG]http://i6.photobucket.com/albums/y210/joe_90015/Office2.jpg[/IMG]


[IMG]http://i6.photobucket.com/albums/y210/joe_90015/Office3.jpg[/IMG]


[IMG]http://i6.photobucket.com/albums/y210/joe_90015/VPN.jpg[/IMG]

Now that I have given some detail on setup I have have a question for those that use Ubuntu server and know the capabilities of it, my boss was telling me that QBooks and our other software are moving towards SQL and wants to add and set it up, he also wants to let our customers be able to access their documents through the web and was thinking of letting them log in via remote desktop, I’m concern about security issues and I’m thinking of how to accomplish all this without a knowledgeable IT person on hand. From what I have read on the Ubuntu server it’s mainly use as LAMP server as well as file server and SQL, how can utilize this server for my needs?

---

### Post by kidders on 2008-03-23
Hi there,

As I'm sure you know well, mission-critical network environments don't tolerate "big bang"-style changes very well. I would very strongly advocate making very small (ie unnoticeable if possible) changes to the way your network works at any one time, and perhaps thinking about a transition to a more Linuxy way of doing things over the course of 12 months or so. Once a business goes too far down the Microsoft road, mixing in another paradigm is often frustratingly complicated. In my experience, it tends to involve an awful lot of time wasted creating interfaces between the two sets of technologies, simply because *not* doing so would simply involve making too many changes all at once.

Anyhow... your questions:

**Ubuntu**
My instinct is to say that Ubuntu may not necessarily be the right distro for you. Whatever about network clients, I would never even consider deploying Ubuntu *servers* in a business setting. In my opinion, there is simply nothing to justify _not_ using something like Debian itself, CentOS, or Red Hat. Having said that, I use Ubuntu servers quite a bit in other environments.

**LAMP**
Again, a standard LAMP install may or may not be adequate. If I were you, I would decide at an early stage ...[LIST]
[*]What kinds of database technologies you'll need 5 years down the road. If the answer is MySQL, then that's 1-nil to an out-of-the-box Ubuntu LAMP configuration. On the other hand, the answer might be Oracle ... or MSSQL.
[*]What kind of fault tolerance meets your minimum requirements. (Replication, disaster recovery, etc.)
[*]Is PHP really a smart idea? In practical terms (and remembering _you'll_ have to administer it all!) PHP can very quickly find itself out of its depth in mission-critical environments. In purely pragmatic terms, there's a lot to be said for ugly things (eg Apache + ColdFusion), or scary things (eg Apache + Rails).
[/LIST]
Anyhow, I suppose the point is to be sure you're 100% satisfied you've made the right decisions, when it comes to things it'd be hard to migrate away from.

**Remote desktop**
I don't like this idea at all, to be honest. If at all avoidable, I wouldn't go down that road. It's slow, resource-hungry, administratively time-consuming, insecure & comparatively difficult to operate.

Anyhow, those are just a few thoughts, in the hope something useful might fall out of them. It'd be interesting to know what (if anything) you think you'll want to change about your current networks, in the course of adding the new services, what other distros you've considered, what kind of usage load (10s, 100s, 1000s) is involved, etc.

---

