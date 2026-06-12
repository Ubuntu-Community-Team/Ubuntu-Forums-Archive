---
title: "SSH not accessible externally on standard ports"
date: 2009-03-18
forum: Server Platforms
---

### Post by MuShoe on 2009-03-18
I am a relatively new linux user, but have made it past the honeymoon phase and am still in love.  I have recently decided to increase my use of Ubuntu and setup a file server (with intention to eventually run a web & FTP server).  I resurrected an old PC and easily installed Ubuntu 8.04 server with the OpenSSH server option.

Ok, so here's where things get interesting (and very frustrating!).  I opened up port 22 on my router (Linksys wrt54g), verified that sshd was listening on that port, and happily went to work the next day and tried to login.  I got a "connection refused" error.  I then went home, setup my router to forward port 21, setup sshd to listen on 21, returned to work the next day and got the same error.  This did not make sense because my buddy can ssh into his server from work on port 21 just fine.  At this point, I started thinking that I had setup my router wrong.  Though I was convinced I had not, I was hoping to find something simple that I had forgot, but could not do so.  I repeated this process several times, trying ports 21, 22, 443, 8080, and a random port like 43210.  None of these ports worked.  My buddy and I then ssh'd into his server and from there tried the above ports to access my server.  Interestingly enough, only the random port 43210 worked.  So now I know that my router is forwarding properly and sshd is configured correctly.  I have confirmed this behavior on two other external computers.  Note: as I tried new ports, I left the other ones open so I could test them all.  Great, you might say, then just use port 43210 and get on with it.  Well, the problem is that my company blocks all but "standard" ports, so this won't work.  I would really like to use a "standard" port so I can SSH from work also.

I contacted my ISP (comcast) and asked if they block any ports.  After the first person I talked to asked "are you talking about the ports on the back of the modem...", I finally got to speak to a person who seemed to have somewhat of a clue.  The answer was "no", they don't block any ports.  This would be confirmed by my buddy (who also has Comcast) and can ssh in on port 21 or 22.  I then thought about my modem (an Arris TM602G) and wondered if it was blocking ports.  After some research, it appears that this device is not a router and can not block any ports.  So now I am confused.

Has anyone heard of Comcast blocking these standard ports?  If my router is setup to forward these ports (and they are enabled), why won't a portscan show them as open (btw, port 43210 does show open as a portscan).  Is there any way that Ubuntu 8.04 Server is refusing the connection?  Is there any way I can verify that Comcast is not blocking any ports?

Thanks for taking the time to read!

---

### Post by HermanAB on 2009-03-18
Divide and conquer:
First rule out a problem on your server by logging into yourself:
$ ssh [email]user@server.lan.ip.addres[/email]s

If that works, try logging into yourself using the external WAN (router) ip address.

Cheers,

Herman

---

### Post by MuShoe on 2009-03-19
> **HermanAB said:**
> Divide and conquer:
First rule out a problem on your server by logging into yourself:
$ ssh [email]user@server.lan.ip.addres[/email]s

If that works, try logging into yourself using the external WAN (router) ip address.

Cheers,

Herman

I am able to ssh into my server internally (on 21, 22, 443, 8080, and 43210), but only externally on 43210.  My router is setup to forward the above ports all to my server's internal IP address.  I believe that this does confirm that sshd is configured properly and that I have my router setup to properly forward ports.  Also, I should note that I flashed my router with the latest firmware, but that did not help.

Thanks!

---

### Post by windependence on 2009-03-19
From your server, go to canyouseeme.org and check each port to see if it shows open. Remember, to have all these ports open for ssh, you must start an ssh daemon for each of these ports. If the ssh daemon is not listening on that port, the web site will not show it open, even though it may be technically open. This is a good thing though, because it will show if there is a daemon listening on that port. 

Also, Comcast is one of the WORST violators of blocking ports such as 80 or 25. I doubt that they would be blocking 22 though.

-Tim

---

### Post by jbrevik on 2009-03-19
Cox also blocks port 80. Sucks but easy to work around

---

### Post by windependence on 2009-03-19
> **jbrevik said:**
> Cox also blocks port 80. Sucks but easy to work around

I see you're in Phoenix. Dump Cox. I have 12mbps with Qwest. No blocks, but don't get the crappy MSN for your ISP, just take qwest. All my commercial web stuff is also connected through them. Also, if you don't like Qwest, check out speakeasy.net.

-Tim

---

### Post by MuShoe on 2009-03-19
> **windependence said:**
> From your server, go to canyouseeme.org and check each port to see if it shows open. Remember, to have all these ports open for ssh, you must start an ssh daemon for each of these ports. If the ssh daemon is not listening on that port, the web site will not show it open, even though it may be technically open. This is a good thing though, because it will show if there is a daemon listening on that port. 

Also, Comcast is one of the WORST violators of blocking ports such as 80 or 25. I doubt that they would be blocking 22 though.

-Tim

Thanks Tim,

I tried this and with 21, 22, 443, 8080, and 43210 forwarded in my router and my server listening (verified with netstat -nap), the only one I could see is 43210.  it appears as though all those other ports are indeed blocked or for some odd reason not being forwarded!

Thanks for the thoughts!

I will keep trying...

Jeff

---

### Post by brian_p on 2009-03-20
> **MuShoe said:**
> 

I tried this and with 21, 22, 443, 8080, and 43210 forwarded in my router and my server listening (verified with netstat -nap), the only one I could see is 43210.  it appears as though all those other ports are indeed blocked or for some odd reason not being forwarded!

You originally reported port 43210 did not respond. What changed the situation?

We'll get away from ssh and try netcat.

```
sudo nc -l -p 23
```

nmap from a machine on the LAN should close nc because it will respond to the probe.

Test at [www.canyouseeme.org](www.canyouseeme.org). CanYouSeeMe should indicate success and the terminal running nc will have returned to a prompt.

---

### Post by MuShoe on 2009-03-20
> **brian_p said:**
> You originally reported port 43210 did not respond. What changed the situation?


I guess I didn't explain that well in my OP.  most of my testing has been done from work (sorry if my boss sees this...)  My company opens up the standard ports (21, 80, 443, etc.), but it appears either my ISP, router, or server is blocking those ports.  Port 43210 is blocked by my company (so I can't test on that port from work), but when I try from anyplace outside of work, I can get in on 43210 (but not any other the other ports), so my ISP, router or server are not blocking that port.  Also, when I check those ports on [www.canyouseeme.org](www.canyouseeme.org), 43210 is the only one I show as open.

When at home, I can ssh in on port 21, 22, and 43210 (only ports I still have the server listening to) from any local machine.

on a side note: My server is not hosting any important data yet, so I decided to wipe the drive and start with a clean install again.  Thinking that I did something early on to screw things up... after a clean install and opening up ports 21, 22, and 43210, I still got the same results.

> **brian_p said:**
> nmap from a machine on the LAN should close nc because it will respond to the probe.

I have to admit, I don't fully understand (yet) what you are having me do, but I will glady try it tonight and report back.  What does nmap do?

Thanks!

Jeff

---

### Post by brian_p on 2009-03-20
> **MuShoe said:**
> 

... after a clean install and opening up ports 21, 22, and 43210, I still got the same results.

You have an Arris TM602G, which is modem. Do you also have a router? If not, how are you 'opening up ports'?

What do you have in /etc/ssh/sshd_config under the heading

```
# What ports, IPs and protocols we listen for
```

i.e What ports do you have sshd listening on?

> I have to admit, I don't fully understand (yet) what you are having me do, but I will glady try it tonight and report back.  What does nmap do?

Using netcat may (or may not) eliminate sshd as the problem. It listens on a port and responds to a request.

nmap is used to scan computers to see what services are available. It should be on your system.

---

### Post by MuShoe on 2009-03-20
Yes, that is the modem that I have.  I was initially thinking it may be acting as a router and blocking ports, but that no longer seems to be the case.  I have a Linksys wrt54g router behind the modem (obviously).  My server has a static IP address outside of the DHCP range I have set.

My /etc/ssh/sshd_config looks like this:
```

# What ports, IPs and protocols we listen for
Port 21
Port 22
Port 43210

# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2

```

when on my server and I type "sudo nc -l -p 22" (or 23, or 21) I get the error "can't grab 0.0.0.0:22 with bind".  Looking at the help, I did not find a way to tell it what IP or network card (I only have eth0) to listen on.

Now, to throw a bigger wrench into this whole fiasco, I tried the portscan again and port 21 is blocked, 22 is open(?!?), and 43210 is also open.  I then went to my router and turned off forwarding to 22 (yes, I did save settins...) and tried the port scan again and.... ...  still open.  it almost seems that my router has a mind of it's own!?!

Jeff

---

### Post by windependence on 2009-03-20
What is the output of;

```
sudo ps aux | grep sshd
```

on your server box.

-Tim

---

### Post by MuShoe on 2009-03-20
"sudo ps aux | grep sshd" gave the following result:

```

root      4076  0.0  0.3   5136  1004 ?        Ss   00:06   0:00 /usr/sbin/sshd
root     11628  1.9  1.1  11172  3656 ?        Ss   21:14   0:00 sshd: jeff [priv]
jeff     11630  0.1  0.5  11172  1844 ?        S    21:14   0:00 sshd: jeff@pts/0 
jeff     11650  0.0  0.2   2916   748 pts/0    S+   21:14   0:00 grep sshd

```

"netstat -nap" gave the following (after some trimming):

```

tcp6       0      0 :::43210                :::*                    LISTEN      -               
tcp6       0      0 :::21                   :::*                    LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -   

```

Hope that helps!  I sure am confused...

Jeff

---

### Post by windependence on 2009-03-20
Well, you only have one ssh process running so that is why you only have a connection on 43210.

Try starting another process like this:

```
sudo /usr/sbin/sshd -p 443
```

and then show me the output if the ps command again, and try to ssh to port 443. Remember, you need to do it like this ssh -p 443 username@serverip

-Tim

---

### Post by MuShoe on 2009-03-20
> **windependence said:**
> Well, you only have one ssh process running so that is why you only have a connection on 43210.



Good thought.  Why can I ssh in on 21, 22, or 43210 from my internal network, though?

here's the output after I started the new service.

```

root      4076  0.0  0.3   5136  1004 ?        Ss   00:06   0:00 /usr/sbin/sshd
root     11628  0.0  1.1  11172  3656 ?        Ss   21:14   0:00 sshd: jeff [priv]
jeff     11630  0.0  0.5  11172  1844 ?        S    21:14   0:00 sshd: jeff@pts/0 
root     11671  0.0  0.3   5136   996 ?        Ss   22:09   0:00 /usr/sbin/sshd -p 443
root     11676  0.9  1.1  12252  3708 ?        Ss   22:09   0:00 sshd: jeff [priv]       
jeff     11678  0.0  0.5  12252  1796 ?        S    22:09   0:00 sshd: jeff@pts/1        
jeff     11700  0.0  0.2   2916   748 pts/0    S+   22:10   0:00 grep sshd

```

I could ssh internally on 443, but not externally, even after opening the port on my router...

Jeff

---

### Post by MuShoe on 2009-03-20
interestingly enough, when I start a new sshd demon on port 21 or 22, it does not show up in the ps -aux command.  Only ports that are not already specified in the sshd_config file...

don't know if that helps...

Jeff

---

### Post by brian_p on 2009-03-21
The portion of /etc/ssh/sshd_config you quote is ok. As you know, you have sshd listening on three ports - 21, 22 and 43210 and have confirmed it will respond to requests on these ports from a machine on the local network.

> **MuShoe said:**
> 

when on my server and I type "sudo nc -l -p 22" (or 23, or 21) I get the error "can't grab 0.0.0.0:22 with bind".  Looking at the help, I did not find a way to tell it what IP or network card (I only have eth0) to listen on.

You have sshd running on port 22. nc cannot use it. Either stop sshd or have nc listen on any other port and test from CanYouSeeMe. It doesn't matter what you do; the idea is to see whether your chosen port is forwarded correctly.

> Now, to throw a bigger wrench into this whole fiasco, I tried the portscan again and port 21 is blocked, 22 is open(?!?), and 43210 is also open.  I then went to my router and turned off forwarding to 22 (yes, I did save settins...) and tried the port scan again and.... ...  still open.  it almost seems that my router has a mind of it's own!?!

I'm inclined to think your problem resides in not having forwarding set up optimally.

---

### Post by brian_p on 2009-03-21
> **windependence said:**
> 

Well, you only have one ssh process running so that is why you only have a connection on 43210.

May I demur. Only one sshd process needs to be running.

```
desktop:/home/brian# netstat -tulnap

tcp6       0      0 :::99                   :::*                    LISTEN     14023/sshd          
tcp6       0      0 :::199                  :::*                    LISTEN     14023/sshd          
tcp6       0      0 :::299                  :::*                    LISTEN     14023/sshd          
tcp6       0      0 :::29999                :::*                    LISTEN     14023/sshd          
tcp6       0      0 :::22                   :::*                    LISTEN     14023/sshd
```

---

### Post by MuShoe on 2009-03-21
> **brian_p said:**
> 
nmap from a machine on the LAN should close nc because it will respond to the probe.

Test at [www.canyouseeme.org](www.canyouseeme.org). CanYouSeeMe should indicate success and the terminal running nc will have returned to a prompt.

Ok, so I tried this again, this time not using port 22, but using port 23, and it works exactly as described.  my server listens on port 23 and when I use
```
nmap -v -A 'server name'
```
it does cause nc to return to the command prompt.

I then opened port 23 on my router and setup nc to again listen to that port and could not see that port from [www.canyouseeme.org](www.canyouseeme.org)...

> **brian_p said:**
> 
I'm inclined to think your problem resides in not having forwarding set up optimally.

Yeah, it sure seems like my router or ISP is doing something goofy.  I dont' see how my port forwarding could be setup wrong.  I am not saying that it's not, but I don't see how something so simply could get screwed up.  My Linksys WRT54G router basically has entries for a name, start port, end port, protocol (TCP, UDP, BOTH -- I am set to both), internal IP to forward to, and an enable check box.  I don't see how it could be much easier.  :?

The fact that I can get in from the outside on 43210 suggests that my router is forwarding correctly.  Port scans confirm that when I enable port forwarding on that port, it can be seen, but when I disable it on the router, the port goes stealth.  Interestingly enough, port 22 is visible to the outside world right now, even though it's not being forwarded by my router.  :-x

Thanks for all the help!

---

### Post by windependence on 2009-03-21
> **brian_p said:**
> May I demur. Only one sshd process needs to be running.

```
desktop:/home/brian# netstat -tulnap

tcp6       0      0 :::99                   :::*                    LISTEN     14023/sshd          
tcp6       0      0 :::199                  :::*                    LISTEN     14023/sshd          
tcp6       0      0 :::299                  :::*                    LISTEN     14023/sshd          
tcp6       0      0 :::29999                :::*                    LISTEN     14023/sshd          
tcp6       0      0 :::22                   :::*                    LISTEN     14023/sshd
```

This is true IF he has the ports listed in his config file. Otherwise, the quickest way is just to start another daemon listening on the other port. His single process was listening on 21,22, and 43210. I wanted to use a completely different port. Comprende?

-Tim

---

### Post by quinny11111 on 2010-02-03
I have recently had the same problem with a Debian server I have set up. i.e can ssh in from internal network but not from the outside world.

I found the resolution in /etc/ssh/sshd_config

I added to the line allowed users

AllowUsers *@192.168.*.*, <allowed ssh IP address>

then restarted ssh

You could give this a try and if it works possibly look at turning it off and just using your firewall to open up SSH

---

