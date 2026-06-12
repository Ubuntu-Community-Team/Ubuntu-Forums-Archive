---
title: "Network Security"
date: 2010-03-30
forum: Security
---

### Post by ubuchignome on 2010-03-30
:mad: Since installing Ubuntu I have noticed an increase in DoS and other attacks against my firewall. Anyone else having this issue?

---

### Post by iponeverything on 2010-03-30
> Since installing Ubuntu I have noticed an increase in DoS and other attacks against my firewall. Anyone else having this issue? 

It seems like your implying that installing Ubuntu somehow attracts attacks.

---

### Post by Soul-Sing on 2010-03-31
> **ubuchignome said:**
> :mad: Since installing Ubuntu I have noticed an increase in DoS and other attacks against my firewall. Anyone else having this issue?

How do you monitor these "attacks", in other words which tools are you using, and may we take a look at the outcome?

---

### Post by uRock on 2010-03-31
We need to know how you detected these instances to make sure they aren't just false alarms.

---

### Post by dE_logics on 2010-03-31
Maybe the hardware firewall is playing tricks...

---

### Post by ubuchignome on 2010-03-31
I have a Cisco firewall that monitors the network

---

### Post by iponeverything on 2010-03-31
> **ubuchignome said:**
> I have a Cisco firewall that monitors the network

Cisco has several different firewall solutions available. 

> **ubuchignome said:**
> 
Since installing Ubuntu I have noticed an increase in DoS and other attacks against my firewall. Anyone else having this issue? 

On a side note. How is it that anyone outside of your network knows what operating systems the machines behind your firewall are running. Any increase in logged activity on your firewall could just as easily be attributed to sun-spots as having a new linux box on your local network.

---

### Post by ubuchignome on 2010-03-31
That is what I was thinking, or possibly the update manager or package manager could be triggering these events?

---

### Post by iponeverything on 2010-03-31
> **ubuchignome said:**
> That is what I was thinking, or possibly the update manager or package manager could be triggering these events?

The firewall should not be logging events originating on inside, otherwise you would be bombarded with junk. Post one of event notifications and we can take a look at it to see if it originated from the outside or if is in response to something from the inside.

---

### Post by ubuchignome on 2010-03-31
Thanks for the replies. I am sure that is not from inside, but something could be initiating the requests that I am not aware of. The Ip addresses listed in the blocked items are not from my network. I will copy the log and paste it in.[FONT=Times New Roman] [/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]Thanks much,[/FONT]
[FONT=Times New Roman][/FONT]

---

### Post by ubuchignome on 2010-03-31
[FONT=Times New Roman][SIZE=3]PS any one want to buy Windows 7 and some other software LOL! [/SIZE][/FONT]

---

### Post by ubuchignome on 2010-03-31
This is the log for the incoming blocked attacks.
[B]

1[/B]2010-03-31 14:47:56Possible DoS HGOD SynKiller Flooding122.227.164.71**2**2010-03-31 14:47:56Possible DoS HGOD SynKiller Flooding122.227.164.71**3**2010-03-31 12:59:48Possible DoS HGOD SynKiller Flooding61.176.216.44**4**2010-03-31 12:08:35Possible DoS HGOD SynKiller Flooding61.176.216.44**5**2010-03-31 12:03:20Possible DoS HGOD SynKiller Flooding60.217.65.115**6**2010-03-31 11:15:54DoS MS-SQL Slammer Worm61.235.46.146**7**2010-03-31 09:28:35Possible DoS HGOD SynKiller Flooding122.227.164.71**8**2010-03-31 09:28:35Possible DoS HGOD SynKiller Flooding122.227.164.71**9**2010-03-31 07:37:51DoS MS-SQL Slammer Worm122.225.100.154**10**2010-03-31 06:12:18DoS MS-SQL Slammer Worm61.233.103.34**11**2010-03-31 06:12:04Possible DoS HGOD SynKiller Flooding221.5.4.225

---

### Post by uRock on 2010-03-31
> **ubuchignome said:**
> This is the log for the incoming blocked attacks.
[B]

1[/B]2010-03-31 14:47:56Possible DoS HGOD SynKiller 
Flooding122.227.164.71**2** 2010-03-31 14:47:56Possible DoS HGOD SynKiller 
Flooding122.227.164.71**3 **2010-03-31 12:59:48Possible DoS HGOD SynKiller 
Flooding61.176.216.44**4 **2010-03-31 12:08:35Possible DoS HGOD SynKiller 
Flooding61.176.216.44**5 **2010-03-31 12:03:20Possible DoS HGOD SynKiller 
Flooding60.217.65.115**6** 2010-03-31 11:15:54DoS MS-SQL Slammer
 Worm61.235.46.146**7** 2010-03-31 09:28:35Possible DoS HGOD SynKiller 
Flooding122.227.164.71**8** 2010-03-31 09:28:35Possible DoS HGOD SynKiller 
Flooding122.227.164.71**9** 2010-03-31 07:37:51DoS MS-SQL Slammer 
Worm122.225.100.154**10** 2010-03-31 06:12:18DoS MS-SQL Slammer 
Worm61.233.103.34**11 **2010-03-31 06:12:04Possible DoS HGOD SynKiller 
Flooding221.5.4.225
Trying to make it easier to read.

---

### Post by iponeverything on 2010-03-31
> **ubuchignome said:**
> This is the log for the incoming blocked attacks

That just looks like the usual noise that pops up in the firewall logs from time to time. Its probably just someone/something running probes looking for vulnerabilities in your netblock. I doubt that it's anything personal, just bots looking for more slaves..

---

### Post by ubuchignome on 2010-03-31
Do you experience this type of traffic?

---

### Post by iponeverything on 2010-03-31
> **ubuchignome said:**
> Do you experience this type of traffic?

In the networks that I have managed, yes. All the time. I found it bit like listening to static on the radio.

---

### Post by ubuchignome on 2010-03-31
Thanks for your time and help, be well.

---

### Post by spynappels on 2010-04-01
Just FYI, none of these will infect a Linux system directly even if they did get through. MS-SQL is not normally present, and the other one specifically targets XP and Win2k

Reference:
[https://mysecurity.zyxel.com/mysecurity/jsp/policy.jsp?ID=1051774](https://mysecurity.zyxel.com/mysecurity/jsp/policy.jsp?ID=1051774)

---

### Post by juliamat on 2010-04-01
HELLO julia here..Security Management for networks is different for all kinds of  situations. 

[LIST]
[*]Assign STATIC IP addresses to network devices.
[*]Disable ICMP ping on router.
[*]Review router or firewall logs to help identify abnormal network  connections or traffic to the Internet.
[*]Use passwords for all accounts.
[*]Have multiple accounts per family member, using non-administrative  accounts for day-to-day activities. Disable the guest account (Control  Panel> Administrative Tools> Computer Management> Users).:popcorn:
[/LIST]

---

### Post by EJeanmaire on 2010-04-01
This is interesting... please do tell me why STATIC IP addressing would be "more secure" than dynamic. 

> **juliamat said:**
> HELLO julia here..Security Management for networks is different for all kinds of  situations. 

[LIST]
[*]Assign STATIC IP addresses to network devices.
[*]Disable ICMP ping on router.
[*]Review router or firewall logs to help identify abnormal network  connections or traffic to the Internet.
[*]Use passwords for all accounts.
[*]Have multiple accounts per family member, using non-administrative  accounts for day-to-day activities. Disable the guest account (Control  Panel> Administrative Tools> Computer Management> Users).:popcorn:
[/LIST]

---

### Post by uRock on 2010-04-01
> **EJeanmaire said:**
> This is interesting... please do tell me why STATIC IP addressing would be "more secure" than dynamic.

In a home network environment, assigning static addresses also means that if one connects he/she has to figure out the gateway IP on his/her own because it is not being broadcasted making it much harder to get a base address to use for scanning.(with all the proper settings in place.)

---

### Post by EJeanmaire on 2010-04-01
> **iRock said:**
> In a home network environment, assigning static addresses also means that if one connects he/she has to figure out the gateway IP on his/her own because it is not being broadcasted making it much harder to get a base address to use for scanning.(with all the proper settings in place.)

It would be very easy to determine the gateway, no broadcasting required.  Infact, 99.999% in a "home" environment that gateway IP is X.X.X.1 . If you want to talk corporate server environment and more complex netmasking we can do that too if you'd like.

Now I'll give you a reason why static is worse.  I decide to compete with your computer for that IP address from the gateway resulting in a DOS.

---

### Post by EJeanmaire on 2010-04-01
My point moreso however is that using static or dynamic is a decision made based on your network requirements, not which is "more secure" as they both have pros and cons, which are mostly negligible from a security stand point. 

What would have been a MUCH better point on her bullet list would have been the use of internal IP addressing inside the LAN instead of external IP addressing.

---

### Post by uRock on 2010-04-01
> **EJeanmaire said:**
> It would be very easy to determine the gateway, no broadcasting required.  Infact, 99.999% in a "home" environment that gateway IP is X.X.X.1 . If you want to talk corporate server environment and more complex netmasking we can do that too if you'd like.

Now I'll give you a reason why static is worse.  I decide to compete with your computer for that IP address from the gateway resulting in a DOS.

You are right about most home routers being something like 192.168.1.1, because most people don't make any changes to their routers.

You can't compete with my computer for its IP, unless you can find its MAC and spoof it. Then I'd notice it immediately and make the necessary changes.

---

### Post by uRock on 2010-04-01
> **EJeanmaire said:**
> My point moreso however is that using static or dynamic is a decision made based on your network requirements, not which is "more secure" as they both have pros and cons, which are mostly negligible from a security stand point. 

What would have been a MUCH better point on her bullet list would have been the use of internal IP addressing inside the LAN instead of external IP addressing.

I agree.

---

### Post by EJeanmaire on 2010-04-01
> **iRock said:**
> You can't compete with my computer for its IP, unless you can find its MAC and spoof it. Then I'd notice it immediately and make the necessary changes.

You can certainly take someone's IP address in a static environment, as there is no central management of IP addressing (usually).  You just respond to all the ARP requests that you are that address and if you beat out the computer to the request you would get the data (temporarily).  

Now if we were talking dynamic, the gateway would be centrally storing the IP/MAC assignments, and I would have to spoof your MAC to play the fun DOS game.  ;)

---

### Post by uRock on 2010-04-01
> **EJeanmaire said:**
> You can certainly take someone's IP address in a static environment, as there is no central management of IP addressing (usually).  You just respond to all the ARP requests that you are that address and if you beat out the computer to the request you would get the data (temporarily).  

Now if we were talking dynamic, the gateway would be centrally storing the IP/MAC assignments, and I would have to spoof your MAC to play the fun DOS game.  ;)

My IPs are assigned to MAC addresses. I do have DHCP running. As I add a new device, I go in and give it a DHCP reservation. I only keep 1 extra IP open for visitors to use, which I randomly connect to the router to make sure it is not in use. I also use the logging features on my router.

---

### Post by EJeanmaire on 2010-04-01
> **iRock said:**
> My IPs are assigned to MAC addresses. I do have DHCP running. As I add a new device, I go in and give it a DHCP reservation. I only keep 1 extra IP open for visitors to use, which I randomly connect to the router to make sure it is not in use. I also use the logging features on my router.

You are using that dynamic DHCP blasphemy!! ;)  Previous poster would not be happy to see that you are not using the "less secure" ways, as static IP is the way to go.

Joking aside, I'm glad to see that you seem to have things pretty well set up and locked down.

---

### Post by cariboo on 2010-04-01
I set static ip addresses for most of the systems I use on a daily basis, I use the range from 192.168.1.200-254 for static ip addresses and 192.168.1.100-110 for dhcp addresses.

I have personally set the same static ip address on two computers by mistake, for the 15 minutes it took to realize what I'd done, I was getting really weird results. One of the systems is an iMac running Jaunty that I use for an mp3 player, and the other was a desktop system I was playing with, the music would stop and start for no rhyme or reason, and the desktop system would connect, and then drop the connection to the rest of the network.Pinging from an other system gave me different results every time I tried.

---

### Post by uRock on 2010-04-01
> **EJeanmaire said:**
> You are using that dynamic DHCP blasphemy!! ;)  Previous poster would not be happy to see that you are not using the "less secure" ways, as static IP is the way to go.

Joking aside, I'm glad to see that you seem to have things pretty well set up and locked down.

:DI live in Las Vegas. if you don't lock down your router here, the free loaders will bog your network.

---

### Post by ubuchignome on 2010-04-02
Thanks for all the info. My preference is using DHCP for the network with limited addressing and reservations. What are you using on the Linux machines for a firewall? UFW or Ip tables

---

### Post by uRock on 2010-04-02
> **ubuchignome said:**
> Thanks for all the info. My preference is using DHCP for the network with limited addressing and reservations. What are you using on the Linux machines for a firewall? UFW or Ip tables

When I am out and about with my netbook I run UFW to protect my system while using other people's networks. At home behind a router it isn't really needed. I SSH to all of the systems in my home to run updates and when needed, shut my daughter's system off. With the firewall up and unconfigured I can do this, so I prefer just to leave them off.

If you want to use UFW you can easily configure it with GUFW.

---

### Post by ubuchignome on 2010-04-02
Thanks much. I am using UFW at the moment. It is pretty simple without Gufw, but I use that for ease of use. Are you using Clam or anything for (Virus) although it is not really needed or is it. I have heard conflicting stories on both sides of that debate?

---

### Post by uRock on 2010-04-02
> **ubuchignome said:**
> Thanks much. I am using UFW at the moment. It is pretty simple without Gufw, but I use that for ease of use. Are you using Clam or anything for (Virus) although it is not really needed or is it. I have heard conflicting stories on both sides of that debate?

I don't use any AV on my ubuntu systems. Anytime I move folders to Windows, I use a flash drive and scan them before copying. I use the same sites now that I used with Windows, I never had virus issues with those site back then, so I feel confident that they are definitely safe with ubuntu. 

If you are using ubuntu as a file server to Windows machines, then I recommend using ClamAV or BitDefender. BitDefender is free for Linux machines. Both have definitions for Windows viruses.

---

### Post by cprofitt on 2010-04-04
The source of these 'DoS' attacks is:


inetnum:      122.227.164.0 - 122.227.164.127
netname:      NINGBO-LANZHONG-WANGLUOGONGSI
country:      CN
descr:        NING BO LAN ZHONG WANG LUO YOU XIAN GONG SI
descr:
admin-c:      TD189-AP
tech-c:       CN13-AP
status:       ASSIGNED NON-PORTABLE
changed:      [email]auto-dbm@dcb.hz.zj.cn[/email] 20090819
mnt-by:       MAINT-CN-CHINANET-ZJ-NB
source:       APNIC

role:         CHINANET-ZJ Ningbo
address:      No.180 Jiefang Road(North),Ningbo,Zhejiang.315010
country:      CN
phone:        +86-574-87278134
fax-no:       +86-574-87362712
e-mail:       [email]anti_spam@mail.nbptt.zj.cn[/email]
trouble:      send spam reports to [email]anti_spam@mail.nbptt.zj.cn[/email]
trouble:      and abuse reports to [email]anti_spam@mail.nbptt.zj.cn[/email]
trouble:      Please include detailed information and times in UTC
admin-c:      CH105-AP
tech-c:       CH105-AP
nic-hdl:      CN13-AP
mnt-by:       MAINT-CHINANET-ZJ
changed:      [email]master@dcb.hz.zj.cn[/email] 20031204
source:       APNIC

person:       Taichun Du
nic-hdl:      TD189-AP
e-mail:       [email]63130210@nbtelecom.com[/email]
address:      floor9£¬aolisai building£¬qianhubei road£¬Ningbo,Zhejiang.Postcode:315000
phone:        +86-15888000013
country:      CN
changed:      [email]auto-dbm@dcb.hz.zj.cn[/email] 20090603
mnt-by:       MAINT-CN-CHINANET-ZJ-NB
source:       APNIC
-----
My guess is it is an infected bot and part of the normal daily activity.

---

### Post by ubuchignome on 2010-04-04
Thanks, I will forward to the ISP Network Security department. 
 
Be well.

---

### Post by ubuchignome on 2010-04-13
I have been recieving blocked P2p aim requests on the firewall now. I have never had this go on before. Anyone else having this type of attack?

---

