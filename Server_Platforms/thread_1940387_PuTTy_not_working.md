---
title: "PuTTy not working"
date: 2012-03-13
forum: Server Platforms
---

### Post by D.Dadsgé on 2012-03-13
Hi all


I've set up a Xubuntu-server at my mom's home, I only installed openssh-server so I could access it from somewhere else. I'm running windows 7 on my laptop. I tried the connection via Putty on the same network which works fine, tried it again at my dad's, still working fine. But when i try to access it from my home, it just wont work, I always get the connection timeout error.
I do live like 50 km away from my mom, but at my work (right around the corner) everything works just fine.
As the error only occures at home, I tought it would be my router. I dont really know what all the settings are for so I went trought it all one by one, trial and error. Still there was no improvement...

Does any one know what might cause this error? Or even have a solution for it?


Greetz

Hannes

---

### Post by eric_1982 on 2012-03-13
Are you able to ssh to any other machines from your house? 

How are you connecting? (IP Address or some dynamic DNS)

---

### Post by D.Dadsgé on 2012-03-13
i'm connecting to the ip adress of the server
haven't tried any other machine yet, how can i test that?

---

### Post by volkswagner on 2012-03-13
What are make/model for your router?


Try connecting without your router.  Connect ethernet from your modem directly to your PC and see if you can ssh into the server.

Can you ping the ip address from your home?

---

### Post by D.Dadsgé on 2012-03-13
i have a linksys wireless-N ADSL2+ Modem Router, Model No. WAG160N.

Pinging my server was also one of the first things i did. It communicates just fine with an average latency of 44ms.

I'll try to connect to internet without my router tomorrow and retest the connection.
Is it possible that there is some sort of build-in firewall which i cannot disable in the router?

---

### Post by D.Dadsgé on 2012-04-17
well um, as it seems i overlooked that i have an **ADSL**/modem/router installed.. which means i cannot connect to the internet without it, without it i just have a telephone-cable comming in.
i have tried port-forwarding to my ip-address but it still doesn't make a difference :/
does anyone know what causes this connection problem?

---

### Post by darkod on 2012-04-17
In a very rare case (or maybe not so rare) your home ISP might be blocking port 22 which is the SSH port.

There is no need for any port forwarding on your end, you do hat only on the server end so that the router which has the public IP knows where to forward port 22, to which private IP.

---

### Post by D.Dadsgé on 2012-04-18
that would mean they are also blocking the ftp-port as i cannot connect to it either. But if this is true and i would change the ports on my server to some unused ports it should be working right?

---

### Post by darkod on 2012-04-18
If you are sure you are doing the port forwarding correctly, it sounds like an ISP issue.

Yes, you could use other ports (it's best to change the default SSH port anyway), but as long as the ISP is not blocking those ports too. If it turns out it's the ISP.

Few years back, a friend of mine in the UK found out the ISP was blocking the port used by MS Exchange. With his work laptop at home, he couldn't connect to his email. Imagine that, blocking such a widely used port.

---

### Post by cackles on 2012-04-18
Have you setup a dynamic dns so that you can find the machine from anywhere on the internet?

Then have you told the router to forward the port to that machine?

---

### Post by D.Dadsgé on 2012-04-18
@darkod
as there is no router installed at my mom's (place where my server is installed) i dont forward any ports anymore. i was also planning on changing the ssh port anyway as the preset port is to risky, but i was going to do it after these problems were out of the way :D guess i should have done it sooner...
is there any way i can find out which ports ISP is blocking (if that would be the case here)? i searched their site but there's nothing there on practical use of the internet.

@cackles
well no i havent set that up.. for the moment im just hoping the server doesnt reboot or looses connection so the IP address would be reset :D but as i said, my work is right around the corner and im checkin it every day with no problems so far. the problem is not that i cannot find it, if i ping my server it works just fine, its only when i try to connect to it that everything seems to stop working.
i am working on somthing so that i can get the ipaddress from the server every time it gets reset but that's not running smoothly yet.

---

### Post by darkod on 2012-04-18
Easy way to see if you can reach the service (server) is:
telnet <public ip> 22

If that says something like "Connected to 22" that should mean the port is not blocked since you can see the service replying. You can hit Ctrl + C to quit the telnet session.

The problem might be after trying to establish the session but I can't see why since it is working from your office.

---

### Post by D.Dadsgé on 2012-04-18
how do i use this telnet function in windows? i dont have any linux system installed here at home.

---

### Post by SeijiSensei on 2012-04-19
You can telnet from putty.  Just choose the appropriate radio button in the connection screen.  

If I were you, I'd install [VirtualBox]("http://www.virtualbox.org/") on your Windows machine so you can run an instance of Ubuntu in a VM. If you install the server version of Ubuntu, you'll find it fits easily inside 512M since it doesn't run a GUI desktop environment by default.  If you want a desktop, [lubuntu]("http://lubuntu.net/") which uses LXDE is a good choice.

---

### Post by darkod on 2012-04-19
> **D.Dadsgé said:**
> how do i use this telnet function in windows? i dont have any linux system installed here at home.

Windows also includes the telnet client but it's not installed by default. If you go to Control Panel - Programs, and Add/Remove Windows Components, you will find the telnet client there to enable it.

---

### Post by CharlesA on 2012-04-19
> **SeijiSensei said:**
> You can telnet from putty.  Just choose the appropriate radio button in the connection screen.  

If I were you, I'd install [VirtualBox]("http://www.virtualbox.org/") on your Windows machine so you can run an instance of Ubuntu in a VM. If you install the server version of Ubuntu, you'll find it fits easily inside 512M since it doesn't run a GUI desktop environment by default.  If you want a desktop, [lubuntu]("http://lubuntu.net/") which uses LXDE is a good choice.
+1. If you are trying to connect to a remote site via ssh and you are unable to connect from one location but you can from another, I'd look at firewall rules on the remote site.

ISPs only block incoming ports, not outgoing ports as those would be on some randomly high numbered port and not port 22, for example.

---

### Post by D.Dadsgé on 2012-04-20
if i telnet to port 22 of my server with putty it just gives me an errorbeep and instantly shuts itself down.
i've installed virtual box on my windows desktop so i can run ubuntu server now, im going to my parents for the weekend so i'll change the ports while i'm there. i'll try to connect again from my home next monday.
thank u all for this support! i hope it will help :)

---

### Post by CharlesA on 2012-04-20
If you have a smartphone, you can try connecting from it to rule out something is messed up.

---

### Post by D.Dadsgé on 2012-04-20
No i dont have one... 
But what difference would it make? I can connect to my server from my laptop at my dad's and at the office, it only gets stuck when i try it at home. What could be messed up if it works elsewhere?

---

### Post by dharmavir on 2012-04-22
a simple question: can you ping your mom's machine's public ip? looks like it might be DHCP.

---

### Post by kevdog on 2012-04-22
Cygwin is a nice alternative to a full blown vm.  Couple of questions:
1. Are you on the same LAN as the server?
2. Can you ping the server?
3. Have you tried doing a port scan against the destination IP address using nmap (which is a stand alone windows program).
4. Do you have a router in the mix?
5. Have you set up port forwarding from the router?

---

### Post by D.Dadsgé on 2012-04-22
> **dharmavir said:**
> a simple question: can you ping your mom's machine's public ip? looks like it might be DHCP.

yes i can ping it.

> **kevdog said:**
> Cygwin is a nice alternative to a full blown vm. Couple of questions:
1. Are you on the same LAN as the server?
2. Can you ping the server?
3. Have you tried doing a port scan against the destination IP address using nmap (which is a stand alone windows program).
4. Do you have a router in the mix?
5. Have you set up port forwarding from the router?

1. no i am not on the same lan, i am trying to connect to it from a remote site over the internet
2. as awnsered above, i can ping the server.
3. no i did not try that yet
4. there is a router at my end of the connection, no router on server end.
5. as there is no router at the server end, i dont forward any ports. yes i have already tried to forward ports at my end but that still didnt work.

As a reply on the previous conversations:
I have changed the portnumbers of both ssh and ftp, i was able to connect to the server over LAN as well as over the internet. Now i tried to connect from my home again and it still fails. The question is now, these ports i chose, could they also be blocked by my ISP?? or is there still some other problem we are not seeing??

---

### Post by D.Dadsgé on 2012-04-22
btw i also found a pretty solution for my dynamic ip address. 
As i didnt want a dyndns trial-version, which expires within a few months, i started looking for an other solution. I ended up with "dropbox". 
I installed dropbox both on my server as on my laptop. Then i wrote a little script which will run every day at midnight and on a reboot. This script writes a timestamp and the whole "ifconfig" output to a file which is located in the dropboxfolder and this one is always synced with my dropbox account and with my laptop. 
So this way i can always look up my ip address wherever i am :)

---

### Post by CharlesA on 2012-04-22
FYI: after the trial, you get what amounts to a free account.

no-ip does the exact same thing as dyndns.

---

### Post by D.Dadsgé on 2012-04-22
yeah i remember now, there was another problem, to get a free trial u still needed to sign up with a visa-card or somthing. i dont have any credit cards so thats where i decided to create some simple script on my own :) but i'll keep that no-ip option in mind, might come in usefull later :D

---

### Post by kevdog on 2012-04-22
Forget the dynamic DNS for just a minute, you can try to ping by IP address (if you know it)!!  

I would first do a port scan against the IP address of the server specifically against the specific ports you are interested in.  This would confirm that your ISP is not blocking your port and would confirm a listening process on the other end of the port.

---

### Post by darkod on 2012-04-22
I understand you are mainly focused on the SSH problem right now, but I don't understand one detail you mentioned now.
You said there is no router on the server end. That is a very rare situation. Do you have a cable provider with only a cable modem of some sort? In most cases there would need to be something to route the traffic.
In some cases with cable modem they just pass the signal and the computer (server) connected to it is directly on internet. In this case that is a big security risk if you are not running any firewall on it.

I am also in favor of trying nmap. You can install it on windows on any computer, and run a test with it on the public IP of your server. See what ports/services it reports as open.

Also, try a trace route to the server IP. There is a remote possibility that the signal is somehow not routed from your location to the server location. It happens.

---

### Post by CharlesA on 2012-04-22
I'm guessing the other machine is directly connected to the internet.

---

### Post by D.Dadsgé on 2012-04-24
thats right, there is no router installed at my mom's. and yes the isp my mom has doesnt come with a router, only a modem and a switch.

yesterday i stumbled on a new problem. i cant seem to ping my server anymore. not from my home nor from the office. it could be that my ip address has changed and that my script doesnt work, or somthing else.. i was able to use nmap once before the connection went down. i performed an intensive scan on the ip address of my server, it told me only 4 ports are available, in the range from 0 to 1000.

i just checked up the services the ISP at my mom provides and i found that there are a lot of ports blocked. (0-1023,1080,12345,12346,31337-31339,31784,27374,1243,31785-31792,4444,1847,1900,3127)
what i dont understand is how i was able to connect to my server before? as ports 0-1023 are blocked so is the ssh port and ftp port.

---

### Post by CharlesA on 2012-04-24
Who knows.

You can always try connecting via Teamviewer and changing the port and see if that fixes it.

---

### Post by D.Dadsgé on 2012-04-29
apparently my sister removed the internet cable from my server.. its working fine now, my script is updating the file in dropbox every hour so i can check whether it's still working or not. 
Im gonna change the ports so they fit in the non blocked ports of my ISP. i hope this last change will do the trick...

---

### Post by D.Dadsgé on 2012-04-29
finally, its working! i adjusted my ports so they fit in the allowed ports of the ISP. thank you guys for helping me out! 
all i need to do now is set up a firewall :) and after all the trouble i've been trough it cannot be that hard :D

---

### Post by SeijiSensei on 2012-04-29
> **D.Dadsgé said:**
> apparently my sister removed the internet cable from my server

Maybe you need to "remove" your sister from the server, too? :D

---

### Post by CharlesA on 2012-04-29
> **SeijiSensei said:**
> Maybe you need to "remove" your sister from the server, too? :D

That would be a good idea. Physical access = root access as always. ;)

---

### Post by D.Dadsgé on 2012-05-01
hahaha :D nice one guys!
When i didn't have my switch installed i needed to unplugg the internetcable from the wifi access point, i forgot i told her how to put it back, but now that i have a switch there's no need to :D

---

