---
title: "cannot get server to display webpages/connect to internet"
date: 2009-02-20
forum: Server Platforms
---

### Post by danastasio on 2009-02-20
ok ok i know you've heard this before sorry ;) but how can i configure my server (Ibex) so that i can use it as a web server. to host my own website, shoveling out webpages to the general public. i will be starting an internet based business soon, so this is crucial obviously :KS i followed the howto here:
[http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)

everything is working, if i type the IP of the server internally i get the "IT WORKS" page, i can ftp and ssh into it internally and exteranlly without a problem. however putting the public IP in the URL bar it simply wont connect from an external connection. i do have port 80 forwarded to the server. i also have Zone edit set up (properly i hope). and i have registered the domain that i wish to use, however i cannot get the darned thing to show a website. :( 
uhhhhhh i dont think i can show any files that would be of any use. lemme know what you need, and i'll get it for you :D
any and all help is appreciated, i've had rather bad luck with this forum actually, none of my previous posts for help were ever answered.  and im hoping for better from this one. :D

update:
[http://localhost/](http://localhost/)     loads nothing in FF

---

### Post by danastasio on 2009-02-20
alrighty, i dunno what i did, but i got localhost working, and i can get to the index.html page from another computer locally, but i still cant get it to make an external connection. but i can still ssh and ftp into the thing w/o a problem externally. do you think its just apache being weird?

---

### Post by danastasio on 2009-02-20
thank you to the forty six people that have seen this thread and didnt bother to leave even a single comment. thanks guys it means alot
ubuntu is praised for the community that supports it.
so why is it that everytime i reach out to the community, it never reaches back?
i love ubuntu, but this is ridiculous.

---

### Post by E_K on 2009-02-20
> **danastasio said:**
> thank you to the forty six people that have seen this thread and didnt bother to leave even a single comment. thanks guys it means alot
ubuntu is praised for the community that supports it.
so why is it that everytime i reach out to the community, it never reaches back?
i love ubuntu, but this is ridiculous.

I understand your frustration, maybe they were people looking to help but didnt know a solution to help you, and possibly some views could have been people with the same problem looking for a solution ;)

You say that you can ssh and ftp into the box from outside the LAN, which means you must have setup the port forwards properly.

Check you have port 80 (http) forwarded to the correct box on the local network.

If it is still not working could your ISP be blocking port 80? if they are all hope is not lost, there are services that you can use to get around this.

Make sure everything is working from the LAN before you concentrate on the WAN.

Try logicaly work the problem out, what programs are you using to control what, is it working and then why not check the logs in /var/log/

Post back if you need some more help

---

### Post by cariboo on 2009-02-20
Go to [canyouseme]("http://www.canyouseeme.org/") and make sure your isp isn't blocking port 80.

It is froum policy to only bump a thread after 24 hours, and if you keep adding post to your thread, people will assume someone is helping you, and won't even look.

Jim

---

### Post by danastasio on 2009-02-20
yeah, i guess i over reacted... :-( but thank you to the both of you, i've never really had anyone to talk to about forum policies, and what not. apparently my ISP is blocking port 80, how can i change the default port? *frantically googling*

---

### Post by E_K on 2009-02-20
i think most are paid services, changing port 80 on your side will be in the apache config, if you want you can send me your msn addy in a pm and i can give you some "live" help

---

### Post by E_K on 2009-02-20
no-ip is probably a good service to go with, theh also have good support if you need it.

Though canyouseeme is not really a sure answer if your ISP is blocking a port, locally i run a server on 8080 though i have no forwarded this port because i want to keep whatevers there only on the local network, and according to the website my port 8080 is blocked, if i forward it in smoothwall (my router) then i do get access from WAN proving it is not blocked.

Just food for though :)

---

### Post by 3L33T on 2009-02-20
> **E_K said:**
> 

If it is still not working could your ISP be blocking port 80? if they are all hope is not lost, there are services that you can use to get around this.



It is highly likely that port 80 and/or 8080 is blocked by your ISP.  Google "ubuntu default apache port" and you'll see a lot of good links that tell you how to change default apache port as well as how to debug problems after changing default apache port.

To find out what your public IP address is, point your browser to:

[www.whatismyip.com]("http://www.whatismyip.com")

HTH

---

### Post by E_K on 2009-02-20
> **3L33T said:**
> It is highly likely that port 80 and/or 8080 is blocked by your ISP.  Google "ubuntu default apache port" and you'll see a lot of good links that tell you how to change default apache port as well as how to debug problems after changing default apache port.

To find out what your public IP address is, point your browser to:

[www.whatismyip.com]("http://www.whatismyip.com")

HTH


was this directed towards me? then it is highly unlikely that they are not blocked, one because i use port 80 along with alot of other unique users every day and ...

> if i forward it in smoothwall (my router) then **i do get access from WAN proving it is not blocked.**

---

### Post by 3L33T on 2009-02-20
> **E_K said:**
> was this directed towards me? 

ooops, pardon me, this comment intended for the original post

---

### Post by 3L33T on 2009-02-20
> **E_K said:**
> was this directed towards me? then it is highly unlikely that they are not blocked, one because i use port 80 along with alot of other unique users every day and ...

you are in the netherlands so consider yourself fortunate. In the U.S., the ISP's block port 80.  They want U.S. customers to upgrade to a 'business account' to have static IP's and unblocked port 80.

---

### Post by E_K on 2009-02-20
no worries,

There always an option such as using a service as what is offered from no-ip that will accept the traffic on port 80 for you and send it then onto you on a port of your choice :)

I had to do this for port 25 :( that they did block

---

### Post by danastasio on 2009-02-23
you guys are awesome!thanks so much for all the help,really, it means alot. now how do i mark this as solved? XD

---

