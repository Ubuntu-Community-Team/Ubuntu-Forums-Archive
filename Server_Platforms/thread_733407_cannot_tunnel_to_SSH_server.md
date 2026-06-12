---
title: "cannot tunnel to SSH server"
date: 2008-03-23
forum: Server Platforms
---

### Post by elchico04 on 2008-03-23
Alright. I'm starting to get a little annoyed at not being able to figure this out. From all the guides and threads I read it makes it sound as if this should be simple. I'm running gutsy if it make any difference

i installed the SSH package and configured SSH to listen for port 80 (I don't know if this is correct or if I should be using a different port).

I then went to a terminal window and entered
sudo /etc/init.d/ssh start

and I got the OK message that it was up and running.

Then I went to my router settings and forwarded port 80 to the local IP address of the box running the SSH server.

I then run downstairs to try to establish the tunnel from a different box.
I open up a terminal window and type

torres@torres-desktop:~$ ssh -D 9999 usrname@external_IP

so let me break this down and see if I'm analyzing this correctly.
I'm not sure what the "-D" parameter is for but in the gutsy gibbon wiki it says to use it.
The "9999" can be any random port number
The "usrname" is the same user name that I use to log onto the  box running the server.
"external_IP" is my 'real' IP address that I could find by going to a website like [www.whatismyip.org](www.whatismyip.org)

When I enter that command it gives me this

ssh: connect to host xx.xxx.xx.xxx port 22: Connection refused

I am confused as to why it is saying anything about port 22 when I edited the sshd_config file to listen to port 80.
I also tried to connect using putty and I got an error saying something along the lies of 'server unexpectedly closed connection'

Is my problem that something is configured wrong? or maybe that it just won't work when trying to test it from the same IP address. Do I need to call a friend or go somewhere to test it?

Any help is much appreciated.

---

### Post by geek_Man on 2008-03-23
You have two problems, I believe. First, when you connect to a different port than what ssh is used to, you have to specify it: ```
ssh -p 80 user@machine
```

Also, (I had this problem with my DSL modem) some modems won't let you connect to a machine on the inside from an external address *from inside the LAN* (confusing, I know). Just try typing in the local IP of the server to see if it works. If that does, try jumping onto someone elses LAN and try the external address.

(Someone should correct me if I've got anything wrong...)

---

### Post by elchico04 on 2008-03-23
are you saying I need to run

ssh -p 80 user@machine -D 9999 usrname@external_IP
or just
ssh -p 80 -D 9999 [email]usrname@external.IP[/email]

?

---

### Post by ctyc on 2008-03-23
port 80 is for the web, ssh uses port 22.

---

### Post by elchico04 on 2008-03-23
yeah...about that. I wasn't really sure what port to set it to. I saw a bunch of tutorials setting it to different port numbers.

I just entered
ssh -p 80 -D 9999 [email]usrname@external.IP[/email]
the terminal seems to be stuck. The cursor is flashing but without the normal user$ prompt (you know when its 'working')

am i supposed to get some message confirming that I am connected?

---

### Post by kevdog on 2008-03-23
Are the client and server on the same local IP subnet or is the server actually outside on a different subnet.

Can you post the server's sshd_config file?

---

### Post by elchico04 on 2008-03-23
its not neccessary to post my config file. I justed changed the default port number.

```
# What ports, IPs and protocols we listen for
Port 443
```

it is in the same subnet. I won't be able to test if it works between different subnets till tomorrow. All of my linux buddies are sleeping.

---

### Post by kevdog on 2008-03-23
Ok but I would try the following if on the same subnet:

ssh -p 443 -D 9999 -C [email]usrname@internal.IP[/email]

---

### Post by elchico04 on 2008-03-24
okay. it works within my subnet but not outside. So its pretty much useless right now?
Anything I should tweek?  People connecting from the outside got time out errors.

---

### Post by kevdog on 2008-03-24
Ok -- so what is between your server and the internet -- a router perhaps??

Since the server is running and accepts lan connections, that takes out a lot of things that could be causing problems.

Lets just verify a few things?

1. You dont have apache running do you?? or no other process listening on port 443?
2. You have port forwarded port 443 on the router to the server
3. You have registered the IP address of the router with a DNS server -- like noip.com or dyndns.com or something like that

---

### Post by elchico04 on 2008-03-25
I don't have apache running. No other processes using port 443 that I know of.
I have forwarded port 443 on my router to the local IP that is running the SSH server
I haven't resgistered the IP of the router with a DNS server. I'll go try that right now.

edit:
okay so I registered my IP address with DynDNS's dynamic DNS service.
I'll try to find someone to test it out for me and I'll report back.

edit #2:
The person from outside my subnet got a "server is taking too long to respond" error.

---

### Post by kevdog on 2008-03-26
Try by IP address rather than domain name to take any DNS problem out of the loop

ssh -p 443 [email]user@IP.address.com[/email].x

---

### Post by elchico04 on 2008-03-26
I'll try that.

I used the network tools utility to do a port scan on my ip address and it showed I only had two open ports, 23 telnet and 80 http. Then after a moment, 8080 web cache would appear. And THEN after 3-4 minutes of scanning, port 24727 is found to be open. (thats the port I forward to use bittorrent)

Could this be part of my problem?

---

### Post by elchico04 on 2008-03-26
using the IP instead of the domain name made no difference.

---

### Post by geek_Man on 2008-03-26
What kind of internet do you have? Does it use any kind of modem or anything?

---

### Post by kevdog on 2008-03-27
Open up port 443 on the router --

Do you have a firewall installed on the router possibly?

---

### Post by celliott on 2008-03-27
Hi,

I know this may sound silly and please dont bash me if it is, but when you changed the port for SSH, did you restart the service??

Cheers

---

### Post by MikePB on 2008-03-27
I'm having the same problem. And yeah, I did restart the service.

I, too, can connect from within my subnet, not from outside. I'll double check when I get home, but I'm pretty sure I opened the port on my router, too.

---

### Post by elchico04 on 2008-03-28
DSL internet. Yes I use a modem to connect to the internet (don't we all?).

I am restarting the service everytime I make any minor change.

I am not using any firewall that I know of.

Is opening a port the same as forwarding? If so, then I am doing that.

Should it be any concern that only 3 ports come up (none being the one I assigned for SSH) when doing a port scan of mu external IP?

I also tried having my friend ping my external IP and got nothing.

---

### Post by mangoes on 2008-03-28
These might be stupid questions.

1) I guess you have you set static lan ip for your computer before port forwarding, because you can locally ssh to that lan ip each time. 

2) I had a lot of difficulty setting remote ssh because my modem was connected to a router.

 If this is the case with you, you may need to forward the port from modem to router, then from router to your computer.  I tried to do it following this[ portforward link]("http://forum.portforward.com/YaBB.cgi?board=Knowledge;action=display;num=1139203841")
but was unsuccessful (still a noob).  In the end I used a modem/router and everything worked smoothly.

---

### Post by elchico04 on 2008-03-28
No question is stupid as long as you are trying to help (I don't think you actaully asked any questions though).

I do have a static LAN IP and the connection to the internet is

internet - DSL modem - router - server

I don't trust that guide you sent me a link to. The guy who wrote it claims that the siemens speedstream modems are modem/router combinations when I have never seen one of these. Anyways the guide says that if i have a modem - router setup that all I would have to do is forward the port which obviously isn't working for me.

---

### Post by mangoes on 2008-03-29
> **elchico04 said:**
> No question is stupid as long as you are trying to help (I don't think you actaully asked and questions though).

I do have a static LAN IP and the connection to the internet is

internet - DSL modem - router - server

I don't trust that guide you sent me a link to. The guy who wrote it claims that the siemens speedstream modems are modem/router combinations when I have never seen one of these. Anyways the guide says that if i have a modem - router setup that all I would have to do is forward the port which obviously isn't working for me.

Hmm that may partially explain why I couldnt get it to work. Are you able to connect the server directly to the modem and  port forward from modem to server, and see if remote ssh is working?  (now that's a question :) )

---

### Post by elchico04 on 2008-03-29
Reword your sentence, it's confusing.
Are you saying I should connect directly to the modem and test it?
If so, I can't because it would be a great hassle to move all my equipment over to the other room.

---

### Post by geek_Man on 2008-03-29
I'm pretty sure mangoes is right. I eventually got remote ssh to work, but you have to forward the port from the modem *to* the router which in turn forwards it to the server. So you kinda have to set up two rules, one for the modem and one for the router. And a lot of modems do act as routers, but that's beside the point...
Hope this helps.

---

### Post by elchico04 on 2008-03-29
How do I forward ports from the modem to the router?
Is this the same port forwarding that is in the router settings?

---

### Post by mangoes on 2008-03-30
> **elchico04 said:**
> Reword your sentence, it's confusing.
Are you saying I should connect directly to the modem and test it?


Sorry, that was what I meant. 
15 years in this country and still carnt writ engrish powperly.:lolflag:

If that would be too inconvenient,  see if [this link ]("http://www.techsupportforum.com/networking-forum/networking-support/136545-port-forwarding-modem-attached-router.html")helps.  The point is to set your modem in the bridge mode. Of course that does not work for all modems. :)

Hope that helps.

---

### Post by elchico04 on 2008-03-30
Bridge mode? Isn't that only an option to change your modem/router combo into strictly a modem? I have the latter.

I think I am going to try plugging straight into my modem with my laptop running linux with a live CD.

---

### Post by mangoes on 2008-03-30
> **elchico04 said:**
> Bridge mode? Isn't that only an option to change your modem/router combo into strictly a modem? I have the latter.

I think I am going to try plugging straight into my modem with my laptop running linux with a live CD.

Didnt pick up that yours is a strictmodem :oops:
Yes if it its a strict modem then the  above link  is irrelevant.

By the way, are your modem and router in the same subnet ?

---

### Post by elchico04 on 2008-03-30
no they aren't

AHHHHHHHHh!!!!! this makes me so angry!!! so angry!!!
I think I may have "figured it out" but not really. I decided for no reason to try connecting to the server with the external ip (previously didn't work) and it prompted me for the password and it worked. I then did the port scan of my public IP and then BOOM right away the first port is 22 for ssh (I changed back to the default port #).
I won't know for sure if it works till tomorrow but I am assuming it will.

The thing is that I don't think I changed anything... *sigh*

---

### Post by mangoes on 2008-03-30
> **elchico04 said:**
> no they aren't

AHHHHHHHHh!!!!! this makes me so angry!!! so angry!!!
I think I may have "figured it out" but not really. I decided for no reason to try connecting to the server with the external ip (previously didn't work) and it prompted me for the password and it worked. I then did the port scan of my public IP and then BOOM right away the first port is 22 for ssh (I changed back to the default port #).
I won't know for sure if it works till tomorrow but I am assuming it will.

The thing is that I don't think I changed anything... *sigh*

If you figure out the reason why it eventually works, please post it here. I'll be very interested.

---

### Post by elchico04 on 2008-03-30
I'm just afraid that it will change back on it's own. I exported my router settings just in case it does.

yeah if i find out I will.

I just hope it works.

---

### Post by elchico04 on 2008-03-30
Well I had it working for a while. My friend confirmed it.
But now, if I do a port scan, port 22 no longer shows as being one of the open ports.
So I am back where I started.
How do I permanently forward this port? I have it forwarded in the router. is there anything else I have to do?

---

### Post by kevdog on 2008-03-31
Open up port 22 for incoming connections possibly on the server firewall or on the router firewall if either has a firewall installed (or iptables).

---

### Post by mangoes on 2008-03-31
> **elchico04 said:**
> 
How do I permanently forward this port? I have it forwarded in the router. is there anything else I have to do?

What protocol do you use ? TCP, UDP, both?

---

### Post by kevdog on 2008-04-01
Any resolution on this issue at all??

Can you log into the modem and are you able to change the settings?

What is the IP address (internal) of the modem, router, and server computer?  Does the router have a static IP address, or where is the DHCP server located?

---

