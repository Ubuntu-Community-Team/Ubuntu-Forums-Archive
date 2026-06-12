---
title: "Network design &amp; MySQL backend"
date: 2005-04-21
forum: Server Platforms
---

### Post by venzen on 2005-04-21
Hi all,

The task of creating a new network design for our organisation has fallen to me and I have begun by installing Hoary on a Dell PowerEdge 4350. All went well and I was surprised at the ease of install and configuration (especially in contrast to Debian stable)! The purpose of this host will be to serve files, act as mailserver and to possibly run MySQL.

Can anyone on the list advise as to the best placement of a MySQL backend server on our LAN? Our webserver host out on the perimeter net will need to access MySQL (as a component of Mambo CMS). However, some of the MySQL database contents will include students' profiles & grades and will therefore be confidential - hence I am reluctant to place the MySQL server on a host on the perimeter net...

Any recommendations for a secure setup/design under these circumstances?

---

### Post by dataw0lf on 2005-04-21
Behind your firewall and/or DMZ.  Additionally, only allow localhost connections to the MySQL database.

---

### Post by rich on 2005-04-23
You're leaving out a lot of info here.

* how many hosts ? Are the hosts on one local net ?
 

This sounds pretty much like one of my setups. It runs mail/MySQL for around 100 local hosts. 

It sits behind a smoothie. This is the important bit. I'm not sure I'd make the same choice again, as the VPN engines seem to have improved since free swan. But it is essential to have an easy to use firewall on what you call the perimeter net. That way you can allow only certain applications / IP ranges access to the server. It's not the only security you'll need, but it will keep out the world. (and yes, do it on a physically separate box)


Rich

---

### Post by venzen on 2005-04-25
Our network will look something like this:

(internet)
      |
    firewall --- public webserver host (perimeter net 192.168.1.0)
      |
   (LAN 192.168.2.0) contains 20 hosts + file/mail/MySQL server


I hope this rudimentary diagram is clear - this network is simple and fairly standard I believe. My dilemma is this: My local network hosts need to access the public webserver and read/write sensitive information to MySQL. However, the public webserver needs to access MySQL also (with restricted, user-specific access to the sensitive data in MySQL), but I have been warned about allowing hosts on the perimeter net to access the local network - in case of intrusions...

So I am thinking that I would have to split the MySQL data between a MySQL server on the perimeter net (for public data) and a more secure MySQL server in the local net (for sensitive data) and then hack PHP to selectively write to the 2 different MySQL databases... 

I am sure that Amazon & others must have a way of storing sensitive data away from publicly visible hosts, but I am not sure that I am designing this scenario in the correct way.

---

### Post by rich on 2005-04-25
To clarify the decision, then :

Your firewall also serves a dynamic website to the public. It contains "stuff" (forms ?) which are populated by data from mysql. This info is provided by running a query as a specific user/password (website ?), which queries a different set of data to that used by your local users.

Clearly, everyone has a different perspective on what "safe" is. 

I suppose I'd build in several layers of comfort - from the bottom up :

* split the data - if you can get "sensitive" and "public" into separate databases then do so. You might chose to replicate a subset of your sensitive data to create the public stuff
* split user access rights - if user website will only ever need read access to a small section, that's all they should have. 
* pin down where your users are - allow an IP range for your local hosts and one IP for your webserver/webuser
* Don't store passwords in plain text inside any of your code on the box
* Worry about the website. There are plenty of ways through interactive forms to be a real pain. See if you can lock it down


Then, architecture-wise, I suppose I'd end up agreeing with dataw0lf. I don't think that running dynamic web servers on your firewall is a good idea. Your currently focussed on the database stuff, but I reckon I'd be sacked quicker for mail disruption than someone, somewhere reading stuff they shouldn't. 

So, 

[snip tried sketching something out in text]

192.168.1.0 firewall 

192.168.2.1 MySQL/mail server
192.168.2.x hosts

192.168.3.1 webserver


The 192.168.3.0 range acts as a DMZ (or orange). Traffic between green & orange is routed through the firewall. You can lock it down so it only allows appropriate traffic (mysql and http). More importantly you can lock down the firewall so the only web traffic it lets into 192.168.3.0 is 80. 


Difficult to write down - easier to scribble boxes & arrows.



HTH


Rich

---

### Post by venzen on 2005-04-25
Rich, your recommendations seem to be the best network design. I also think that your observations on data seperation are correct - I am thinking over this issue and will post again with any solutions or changes I discover.

attempting diagrams in email/forums always makes me realise just how well I have to explain in words what exactly I mean - I use my hands alot when talking, you see, so the fact that you understood me at all is a testament to the human capacity to interpret meaning!

Thanks a lot,
Werner

---

