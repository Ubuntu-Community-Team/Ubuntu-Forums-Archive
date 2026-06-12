---
title: "Wanting to set up Ubuntu Server 14.04 LTS to be accessed from anywhere."
date: 2015-03-31
forum: Server Platforms
---

### Post by ace8 on 2015-03-31
My Setup:
[LIST]
[*]Ubuntu 14.04 LTS installed onto an old rig.
[*]Configured everything to be accessed locally. (I can access my server while on my local network with 192.168.1.116)
[*]I have a router connected to a modem. I have the level of access to be able to port forward on both the modem and router.
[*]I have tried ports 20-25 and 80 to no avail. ([www.canyouseeme.org](www.canyouseeme.org) is not able to see my open ports)
[*]I have a Nighthawk R8000 router and a Zyxel Modem.
[/LIST]

If someone could help me out it would really be appreciated.

---

### Post by darkod on 2015-03-31
Are you sure the isp is not blocking the well known services ports?
Also, I assume you tried ssh login for example from the outside regardless what canyouseeme says.

The modem + router combination usually means the modem passes the public ip directly to the router so you need to do port forwarding only there. Not on both devices.
Also double check your router firewall options. On some models port forwarding does not disable the firewall for that port automatically. In such case you need to create access rules for the ports you want to allow.

---

### Post by SeijiSensei on 2015-03-31
Try adding a rule that uses a "high-numbered" port above 1023.  For instance, have the router forward its port 22222 back to the server's port 22.  Then see if you can connect with an SSH client using port 22222.

---

### Post by TheFu on 2015-03-31
If it isn't clear from the other replies, you need a few things setup for remote connections to work.

a) pick a remote connection protocol.  ssh is the most secure AND the easiest.  It supports sftp and scp and sshfs and NX connections - with those, you can have complete remote control of any Linux machine.  Avoid telnet and plain ftp.  **sudo apt-get install openssh-server fail2ban**

b) your "server" needs to have a static IP, so it doesn't change. I assume you can figure out how to do this for your network.

c) your router needs to forward a TCP port from the public interface (WAN) to the private LAN static IP of the server to the port you setup for ssh. On the LAN side, I keep the default port, 22.  On the WAN side, I use a high TCP port for a number of reasons - 64022 - something like that.  WAN:64022 --> LAN:22  I've seen an entire website setup to explain how to do port forwarding - easily found with google.

d) you will need to know the current public IP of your WAN interface. It needs to be internet routable, so not 10.x.x.x or 172.16.x.x-172.32.x.x or 192.168.x.x. Those will not work.  If your WAN IP isn't static, you can use a **dynamic DNS** service - there are paid and free versions. Some ISPs change your public IP every 4 hours and others change them every 5+ yrs (they always wait until you are out of town ;) to make the change IME.

e) If you like, you can pay to have a real, internet domainname, get an internet DNS service and have everyone in the world be able to find your ssh server.

If you are really knew to *nix, it is smart NOT to run a web server at home, plus this probably violates the ToS with the ISP - most have a "No servers" clause.  Running a small web server for personal use isn't likely to get you banded, but if the traffic becomes non-trivial, it might.  It is a good place to learn about securing a web server, but expect to get hacked if you don't take reasonable security steps.

So - with all this setup ... go to someone elses house or any place with free wifi and connect back home.
**ssh -p 64022 userid@WAN-IP**
Magic?!!!
Learn more: [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)
ssh security: [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

---

### Post by ace8 on 2015-03-31
Thank you to all for the replies. I am at home now and will start this process immediately. I know my static public IP. I'm guessing that I've done the forwarding wrong. I have only tried to type in my public IP from my phone's internet browser and I'm guessing this won't work, so I'll try a friend's house on WIFI with my laptop.

I'll also try the unique high-numbered port to see if that will work as well.

I plan on using this with my Software Engineering team in school (4 people max) so I should have problems with my ISP's Server Clause (if they have one, didn't check).

I will be back to this post to let everyone know how it went.

Again, Thanks for the replies.

---

### Post by TheFu on 2015-03-31
If your phone has a data plan and you are connected through the cell network, not the LANwifi, it should work - assuming the correct protocol was used and port specified - probably sftp.  Be certain to read my links on security. Do not put an open port on the internet that allows passwords - especially ssh.

There is a port scanning tool that can be handy - grc.com ... shields up.  Also, from any other WAN ip, you can use **nmap**.

---

### Post by ace8 on 2015-03-31
On my router for port forwarding, I set up the following:

Name                Protocol        External Port     Internal Port     IP Address
Server (SSH)     TCP/UDP           64022                 22           192.168.1.116
Server (WEB)    TCP/UDP           64080                 80           192.168.1.116

My Public IP is 74.XX.XX.XXX

On the server I have configured the firewall with:
ufw allow 22
ufw allow 80

The only thing that I consciously know that I have not ported is the firewall on the router, but I don't believe that there is one.

Still no outside connection... Is there anyway to test this from the server rather than a different unit? Any other suggestions other than configuring the possible router firewall?

---

### Post by darkod on 2015-03-31
Note that the mentioned SSH test is for ssh only. It is easy to use a different port on the outside interface and make the router forwarding rule to match that.

However, if you plan to run web or mail services (even for a limited number of people), because you mentioned ports 25 and 80, the task becomes more complex if your ISP is blocking those ports. Then you have to use the same forward from high number port to the service ports (25, 80, etc) to avoid ISP block. But in such case all people using these services have to know that, and use the ports accordingly. Again, for a small number of people, that is not difficult to do.

And in such case you need to do your testing accordingly too. For example if you decide to use 11111 for web and set the router to forward 11111 from outside to 80 on inside, the address you need to be opening on the browser is http://<router public IP>:11111

If you don't put any port, it uses the default port 80 but your router external interface is expecting 11111. In fact, traffic on port 80 won't even reach your router if we assume the ISP is blocking it.

For mail it becomes even more complex if not impossible since world mail servers expect to communicate on default ports and you can't "tell them" to use other ports as easy as you can type a different port in a browser.

---

### Post by darkod on 2015-03-31
Your server is on a private network so you can disable ufw while testing. It should be like
sudo ufw disable

Make sure that you don't need to open 64022 and 64080 on the router firewall too. If it's blocking them then all your attempts will fail.

Otherwise it should work. At least the ssh part. When trying to access it by ssh make sure to use port 64022 otherwise it will use the default 22 and it won't work.

---

### Post by TheFu on 2015-03-31
Already answered.

Test using "shields up."  [https://grc.com/x/ne.dll?bh0bkyd2](https://grc.com/x/ne.dll?bh0bkyd2) - I googled it for you. It only checks lower ports by default.

DO NOT forward UDP if you don't need it. It is a hacker's dream to get UDP access. Only a full VPN (openvpn) or DNS need UDP. Most people shouldn't run internet facing DNS - it is much harder than it seems.

Most home routers have firewalls built-in. But if you use their GUI to do port forwarding, they handle the firewall for you. After all, those routers are probably running linux and both the firewall and forwarding is actually being accomplished with iptables rules under the webGUI.

---

### Post by ace8 on 2015-04-01
Hmmm... I don't know what I'm doing wrong. It seems as though I've done everything that you guys have suggested with no luck. When I got home yesterday, I deleted the policy rules that I had done on the modem since it was stated that the modem automatically passes the router the public IP. Then I changed the ports to Externals **64080/64022** and Internals **80/22**. I did the **ufw disable**. Still no outside connection, but I'm not giving up.

To TheFu:
I haven't tried the ShieldsUp software yet, but I plan to today. I also don't know exactly what you mean by using **nmap **from any other WAN IP because I am assuming that I would first need to be able to gain access to the public. I'm pretty sure I may be able to google this and find something though.

I also jumped onto my Ubuntu laptop and tried running the **ssh -p 64080 userid@PublicIP **with no luck either.

Thanks again for your replies, and for being patient with me. I didn't expect it to be this difficult. I thought I knew technology.

---

### Post by TheFu on 2015-04-01
Try **ssh -p 64022 userid@PublicIP**
However, many home routers will see this as an mistake/attack and block it. To test it, you need need to visit that website - it is just a webapp - not "software" you need to load.

nmap is sofware you'd load on your laptop and use to test from some other network. There are hundreds of nmap how-to videos on youtube.

Before you do all that - can you ssh from the laptop to the server from inside the LAN? If not, it will never work from outside.

---

### Post by darkod on 2015-04-01
If your laptop is in your home lan while doing that you can't ssh on 64022.

From inside on 22, from outside on 64022. The machine has to be outside your local lan.

PS. I will mention it again. Did you double check the router firewall in its GUI? If it is blocking you it is no surprise it doesn't work. Don't ignore that possibility, check and rule it out.

---

### Post by TheFu on 2015-04-01
My point, subtle as it was, was that 64080 is the incorrect port for ssh from the WAN.  64022 should be the WAN ssh port.
Details matter.

---

### Post by ace8 on 2015-04-03
So... I just noticed this while going through my router settings to ensure that the firewall wasn't blocking the ports. I stumbled across the fact that my router has settings enabled to configure itself as a DLNA Media Server that shares on all of the internal ports that we have been discussing. Could this be the reason that I can't access anything on those internal ports? If so, I'm guessing that it will mean that I must change the listening ports on my server to be the same as my unique external ports. Does that sound about right?

---

### Post by ace8 on 2015-04-07
Also, would it help if I posted images for you guys to see?

---

### Post by darkod on 2015-04-07
If you don't need to use the router dlna function simply disable it and it shouldn't share any services/ports. If you do plan to use it then see if you can control which ports it shares and remove 80 and 22 from the list. I see no reason a dlna media server to share 22. It might share 80 for a web gui.
Also these settings might not even affect your setup because the port forwarding sends the traffic to the server ip, it doesn't stay in the router. If the sharing you mention is for the router ports it shouldn't be a problem since the server and router have different lan ip.

---

### Post by TheFu on 2015-04-07
I don't want to see any images.

BTW, there is a website that will teach you how to forward ports on your specific router. Google finds it easier.

Before we go too far, please check a few things.
a) With both the desktop and the laptop on the same subnet (LAN), try ** ssh userid@serverIP** - this will connect on port 22 - the default. From inside, that should always work.
b) On your router, if you don't have storage directly connected to it (usually USB), then disable the DLNA crap. DLNA support on a router is a secure nightmare, IMHO.

Did "a" work or not?  If not, please copy/paste the exact command and output.

---

### Post by ace8 on 2015-04-07
"a)" has been working this entire time. That's what's vexing me. I think I've narrowed everything down. I can do everything on LAN, nothing on WAN. I have been through the port forwarding a number of times with no result. When I use the port scanner from portforward.com, ports 20-22,53,80,443 all time out and the rest say closed. I think my ISP have blocked any possibility of setting up my own server without arguing with them. That's the only other option that I see could be a solution.

---

### Post by TheFu on 2015-04-07
> **ace8 said:**
> "a)" has been working this entire time. That's what's vexing me. I think I've narrowed everything down. I can do everything on LAN, nothing on WAN. I have been through the port forwarding a number of times with no result. When I use the port scanner from portforward.com, ports 20-22,53,80,443 all time out and the rest say closed. I think my ISP have blocked any possibility of setting up my own server without arguing with them. That's the only other option that I see could be a solution.

What does shields up show for 64022 and 64080 (assuming you've forwarded those)?

22, 80 and 443 aren't forwarded by your router anymore, correct?  That will show as "closed" in that case.

---

### Post by ace8 on 2015-04-07
ShieldsUP says that both ports 64022, 64080 are closed and that they are unable to establish a TCP connection with those ports. The ports however are configured properly on my router.

---

### Post by TheFu on 2015-04-07
> **ace8 said:**
> ShieldsUP says that both ports 64022, 64080 are closed and that they are unable to establish a TCP connection with those ports. The ports however are configured properly on my router.

Well, if the router ports really are open and translating correctly to the server as suggested, and your server is not blocking requests from outside the LAN to those ports, then your ISP is blocking new inbound connections. Time to get a new ISP or buy a VPS and use a reverse ssh connection from your house to the VPS as a way in.

---

### Post by ace8 on 2015-04-09
Geez... That really makes me an unhappy person. I guess I could try contacting my ISP to see if any argument on my behalf can cause them to free me from their hold. I have been dealing with this server for too long. I really thank you guys for putting in the time to bestow your knowledge on me. I've learned a great deal. I'll come back to let everyone know how it goes with talking to my ISP. 

If all else fails I'll probably look into a VPS and try the reverse connection (I don't like things to be easy, if you guys can't tell). After that, I'll try a new ISP.

---

### Post by ace8 on 2015-05-21
Well, I'm finally back with an update as promised. 

I called my ISP and they informed me that they don't block any of my ports, so I did some more digging. Turns out that I had placed my global IP into the Port Forwarding portion that connected my router to the internet which was incorrect. I did not know this but everything is working perfectly fine now. Thanks again for your help guys. I learned a lot from you all.

---

