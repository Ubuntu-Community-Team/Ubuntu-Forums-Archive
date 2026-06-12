---
title: "subdomain to certain ports bind9"
date: 2008-04-04
forum: Server Platforms
---

### Post by Tavorisch on 2008-04-04
Hey! how do you assign your subdomains to certain ports? example:

ftp.example.com to only hit port 21, IE. you can ftp in to ftp.example.com but putting that in your address bar doesn't bring to your apache default web site.

This would probably be a helpful simple searched topic and any help would be much appreciated!

---

### Post by twistedtwig on 2008-04-04
who deals with your world wide dns?  do you have a static ip or dynamic?

i.e. i use easydns.com to update my ip and point my domain name and subdomains to my dynamic ip address.

I am not sure about how exactly you would deal with this off the top of my head.

---

### Post by Tavorisch on 2008-04-10
i use ait domains, i was wondering if it's possible with bind9.

---

### Post by Tavorisch on 2008-04-10
yah can't do anything with ports in ait domains. btw bind9 is a DNS app, so i'm not forwarding or anything. i just have a registrar from ait and thats it.

---

### Post by songshu on 2008-04-11
you would need a router to re route traffic to the ports you would want them on?

but if you go to [http://ftp.example.com](http://ftp.example.com)
you go to the http port number 80 where normally apache would be listening on
if you go to [ftp://ftp.example.com](ftp://ftp.example.com)
you go to ftp port 21


so basically if i type http:// in my browser the firefox will go via port 80 you your server
if you would want to redirect my incomming traffic on port 80 to port 21 you would need a router.

or
you could let your ftp program to listen on port 21 and port 80, but then your apache would have no port to listen on.

unless i'm misstaking i guess you would want to look into the difference between 
**http://**ftp.example.com 
and
**ftp://**ftp.example.com

---

### Post by Tavorisch on 2008-04-11
I am terrible at communicating!! haha, I was looking around it looks like i woudl want to go with iptables for routing.  Basically my domain, example.com  goes to the ip address and thats it.  if I make an A record so I have ftp.example.com  it works! but that also comes in on all ports, like if i went to [http://ftp.example.com](http://ftp.example.com) it would bring me to the website! if I typed [ftp://ftp.example.com](ftp://ftp.example.com) it would bring me to the ftp server. but then what would be the point of having ftp.example.com if i can just ftp in  to the server by using  example.com as the server address   how do I restrict  example.com and [www.example.com](www.example.com) to port 80!? how do i make it so putting in [http://ftp.example.com](http://ftp.example.com) wont go to the website? there will just be nothing there? and so ftping into example.com won't work, and you'll have to ftp in with the server address ftp.example.com  or the ip address..

---

### Post by songshu on 2008-04-11
the ftp part in ftp.example.com is just a description so people know to use ftp:// instead of http:// OR ftp.example.com could point to a different IP address then [www.example.com](www.example.com)
you could also make it example.example.com.

if [http://ftp.example.com](http://ftp.example.com) is resolvable so it goes to your http:// port 80 then do you  have something like this?
*.example.com     A     123.123.123.123

if so then remove the A record with the *

---

### Post by Tavorisch on 2008-04-12
What i'm trying to say is, I want to assign [www.example.com](www.example.com) to port 80, and other subdomains like, ftp.example.com to port 21 or other ports
.. When I ssh into the server I can just type [www.example.com](www.example.com) or basically any A record I have, instead of the IP address and I can get in.. (IP address works too ofcourse Which makes perfect sense) I don't want to be able to do that, I want for example. if I want to SSH into the server i wanna have to put the IP address or ssh.example.com I don't want [www.example.com](www.example.com) to work etc etc.

---

### Post by Tavorisch on 2008-04-13
I realize the difference between ftp:// http://  what if you had a self contained web service running, even webmin per say running on port 566  like if you type [http://xxx.xxx.xxx.xxx:566](http://xxx.xxx.xxx.xxx:566)  (random port) it brings you to that particualr web page, or utility.. instead of your apache which listens on 80... how would i make a subdomain go to it, like webmin.example.com goes to ip address on port 566..  one thing I have done is create a virtual host in apache for a subdomain and made a full size frame html document which contains [http://xxx.xxx.xxx.xxx:566](http://xxx.xxx.xxx.xxx:566)
it would be nice if you could just do it in bind.  subdomain.example.com IN A xxx.xxx.xxx.xxx:566  Does anybody get what I'm saying yet?

---

### Post by songshu on 2008-04-14
yes, i understand what you are saying.

but you are looking in the wrong direction i think.


DNS handles with the Dynamic Name System and not the Dynamic Port System, altough it would be a nice invention ;)

if you want to redirect ports you need to do that at the router side of things.

any program can listen on any port or all off them if you choose so, but they all (most) have a default.

you can have multiple domain names on 1 port..

no need for bind

---

