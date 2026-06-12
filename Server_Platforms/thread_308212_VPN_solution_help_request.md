---
title: "VPN solution help request"
date: 2006-11-27
forum: Server Platforms
---

### Post by doogy2004 on 2006-11-27
I am looking for a vpn solution that will accomplish the following:

Login using a username and password
connect using the windows xp VPN setup wizard
connect using a mac
connect using linux(any distro)
forward all traffic from the client through the vpn and back out to the rest of the internet(e.g.  I connect to the vpn using any os, i browse to [www.google.com](www.google.com), all the data that i see is comming to me securely through the vpn connection.)
user management must be simple and secure(adding new users, changing passwords, deleting users)
list of port numbers used(to allow for port forwarding through a router)
allow multiple connections/users at the same time

Thank you in advance for your help

---

### Post by marianom on 2006-11-27
I would say OpenVpn. I use it and no complains: [http://openvpn.net/](http://openvpn.net/)

Drawbacks (regarding your requests):

1- I know it can be done but not exactly how is the thing about tunneling all with the vpn. Seems it's something in the server conf file
2- I'm pretty sure you cannot use Xp Setup Wizard to connect. Anyway in Windows it's just a little icopn in your tray, nothing terrible. Click, enter password and you're done.

---

### Post by doogy2004 on 2006-11-27
i appriciate your recomendation.  my next question is how does one install and configure openvpn to accomplish what i'm looking to do.

i have done this so far
```
sudo apt-get install openvpn
```

how would i configure openvpn to accomplish my goals, and do i need any other packages to accomplish my goals.  I would like to keep this solution as minimalistic as possible without loosing features.  features are very important, i would like this solution to be as user friendly as possible, in a server environment, meaning command line.

i would also like to let everyone know that i am willing to create a complete write up in the form of a how-to and possibly a script that a user can run to install and configure this solution in a simplified manner.

---

### Post by marianom on 2006-11-27
I took a look at synaptic (didn't know it was there, I could save some time months ago...), anyway there's a few dependencies (libc6, liblzo1 and libssl) but I think the .deb would take care of them. 
I see some additional packages that might help you administer your conf files in case you have lots of users (right now I'm supporting 6 simultaneous users with my vpn: not a big deal so I manage their accounts manually): carpaltunnel (funny name) and tunneldigger: cannot comment since I never tried'em. There are other GUI that might help you but I cannot comment too: I'm too lazy to get up and walk to the server so I manage it with ssh and the command line.

1- Regarding configurating it, the howto is a good starting point: [http://openvpn.net/howto.html](http://openvpn.net/howto.html). I read all of it and followed all instructions and no problem: you can see there how to generate certificates, touch the conf file and stuff.  
2- regarding the router, you have to forward the 1194 port (I did it directly in my Netgear router).
3- people using windows should download (I assume they're the clients), install and you should help them configuring their client.ovpn conf files, give them the certificates and you're done (check the howto: everything it's there).
4- MAC Os: follow Tunnelblick from the openvpn page.
 
Start on the HowTo and try some combinations: in case of problems, let me know and I would try to help in whatever I can.
Good luck.

---

### Post by marianom on 2006-11-27
I forgot to mention that there's a good forum for OpenVpn users: [http://www.vpnforum.de/](http://www.vpnforum.de/) They speak in german but there's subforums for english speaking users. It's a good forum, they're usually very helful guys.

---

### Post by doogy2004 on 2006-11-27
dito on the ssh, this should be a total command line solution at this stage.  it could be adapted to use a gui at a later time, but that is out of the scope of this solution.

as far as the clients go they will be cross platorm meaning there will be windows, mac, and linux clients.  my main concern right now is getting the clients according to the following, getting windows clients to work comes first, then mac, then linux. (sorry for putting linux last, but i just don't see it as user friendly as windows or mac, in this solution simplicity is key, and useing the vpn clients that are built into each OS is the preferable method. using a client software is an extreme last option)

---

### Post by zhenya on 2006-11-28
I strongly second the OpenVPN recommendation.  After going through a CISCO PIX VPN router, then to the Windows PPTP VPN system, we finally have everything we need with OpenVPN.  Depending on your skill level, OpenVPN may take some time to set up properly, but it is an amazingly logical program, so not too hard to pick up.  The time taken to get to know it is well worth it, imo.

---

### Post by doogy2004 on 2006-11-28
The hardware and OSs that you said are similar to what i'm looking for except i'm using a linksys router(i like to call linksys the cisco for home use)

thanks for the recommendation, do you have any documentation on how to set this up?

---

### Post by marianom on 2006-11-28
Don't wanna sound like Travis Bickle :) but are you talking to me or to zhenya?

If you need a guide for port forwarding in linksys, here's one:
[http://www.dslwebserver.com/main/sbs-linksys-port-forwarding.html](http://www.dslwebserver.com/main/sbs-linksys-port-forwarding.html)
It might vary regarding the model but I would say they're more or less the same.

---

### Post by doogy2004 on 2006-11-28
i posed the question to marianom but, i would like anyone who has any type of documentation to help contribute to the solution.

---

### Post by doogy2004 on 2006-11-30
i'm reading the how to section on routed and bridged vpn, does anyone have any information on how each one of these would be set up?

---

### Post by marianom on 2006-11-30
How to bridge is here:
[http://openvpn.net/bridge.html](http://openvpn.net/bridge.html)
routed is the default method, if you follow the howto and configure the vpn as it said there it will lead you to a routed network.

---

### Post by chrisfay on 2006-12-01
I was using OpenVPN temporarily and found that if I connected to the vpn server, then let my session sit for over a couple minutes, it would time out. The session would act like it was still connected but I couldn't ping anything on the vpn subnet, then it would come back up after reauthenticating. 

This ultimately became too much of a hassle since I wanted a solution that I could connect to and leave open then come back to later. I messed with all the config options for keeping alive but to no avail. Has anyone else had this problem?

---

### Post by marianom on 2006-12-02
Pretty sure we are not experiencing that problem, our vpn reconnects by itself each time the client goes back to work. 
I would call it luck since I don't have a clue why it happens.
I check my conf file to see if I can figure it out. 

Can you post here (stripped from comments and sensible information) your conf. file? I can compare it with mine.

---

### Post by marianom on 2006-12-02
*Maybe* this part of the conf file might help:

```
# The keepalive directive causes ping-like
# messages to be sent back and forth over
# the link so that each side knows when
# the other side has gone down.
# Ping every 10 seconds, assume that remote
# peer is down if no ping received during
# a 120 second time period.
keepalive 10 120 
```

You can tune these two values to let the vpn (on the server side) to evaluate the status of the connection.

---

### Post by marianom on 2006-12-02
I asked my coworkers (I'm the servers admin and I have no really "client" experience) about the "keepalive" thing you asked and 
1- they all use windows xp 
2- the openvpn reconnects by itself unless windows has killed the service (making impossible to the openvpn client to answer the ping sent by the server). In that case it's necessary to re enter the password again.

My linux clients are out of reach right now so I cannot talk to them to see how they do.

---

### Post by chrisfay on 2006-12-02
Thanks for the info. I gave up a couple months ago after attempting every modification I could think of to the keepalive option. I tested both XP, Win200 and linux clients. All did the same thing.

According to the docs, the server will ping every 10 seconds and assume that remote peer is down if no ping received during a 120 second time period. Upon initial connection, I would be connected to the vpn subnet. But, once I let the connection idle without disconecting, it would lag and ultimately restart the authentication process. Durring this time, I would have no connection at all between client and server.

I was under the assumption that the 'keepalive' was there for this exact reason; so you could leave your connection going and come back to it without any hitch. Unfortunately, after all the testing, I purged-removed the package and all config files.

While it was installed,  I did use the default keepalive setting and tried a multitude of variations without success. I suppose it could have been some error in my net routing table or router configs, but who knows. Seems if that was the case I would have not been able to connect 'at all'.

---

### Post by marianom on 2006-12-02
Sorry for not being of more help. On monday I'll ask the other guys that use the service to see if they have a clue. If there's something I'll post.

In case you're still curious why it did not worked or might want to try openvpn other time, I suggest posting this same question in the [openvpn forums]("http://www.vpnforum.de/viewforum.php?f=25"). 
They seem to know a lot about vpn.

---

