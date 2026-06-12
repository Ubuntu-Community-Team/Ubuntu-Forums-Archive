---
title: "Creating a Firewall for Your Ubuntu Desktop"
date: 2011-11-05
forum: Security
---

### Post by Dangertux on 2011-11-05
The following will discuss three different methods by which you may implement a decent host based firewall for your Ubuntu Desktop Installation. This guide is provided in light of the following thread : [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

Several users have expressed concern about being able to create the type of firewall that was mentioned in that discussion. So here we will elaborate on three different methods in which you may do so under Ubuntu. This demonstration was completed using Ubuntu 11.10 Oneiric Ocelot 32 bit, however it should hold true for Most versions of Ubuntu post 8.04 (pre 8.04 needs to use the iptables section as the UFW syntax was different) on both 64 bit and 32 bit systems.

The three methods we will be using will be the following

- GUFW : This is the graphical user interface for Uncomplicated Firewall, the front end for iptables provided by default in Ubuntu
- UFW : The CLI front end application for controlling iptables/netfilter, which is included by default in Ubuntu. 
- iptables : We will create an iptables script to create our firewall

It is important to understand that each of these three methods accomplish the same goal, and only one needs to be used. Since they are all methods for interfacing with iptables/netfilter, and kernel level packet filtering. Each method will do exactly the same and preference is needed only in what you feel more comfortable with. Personally, I find iptables more intuitive than the other two methods, so it is what I would use. However you may find GUFW or UFW more convenient that is why I am discussing all three methods. I will not be covering Firestarter, it is similar to GUFW, and it is outdated and not supported by default. Therefor if you choose to use that it is entirely on you. It does not offer any functionality that the following methods do not.

Without further ado, here we go.
[B]
Method 1 : GUFW[/B]

GUFW is not installed by default so if you wish to use it you must first install it from the repositories. You can do so by giving the following command in a terminal, or by downloading it from the Ubuntu Software Center.

```

sudo apt-get update && sudo apt-get install gufw

```Once it has finished installing you may open it up, either by entering the following in a terminal 

```

gufw

```Or by running the Firewall Configuration application from the Dash. (note for Non-Unity Users this is located in Administration)

[IMG]http://dangertux.no-ip.org/downloads/1.png[/IMG]

Once you have executed GUFW you will be presented with a Window that looks like this, assuming that you do not have any firewall rules currently, and UFW is disabled your window should look identical to this one.

[IMG]http://dangertux.no-ip.org/downloads/2.png[/IMG]

Note : Before you can make any changes you must click on the lock in the lower right hand corner of the Window and enter your sudo password.


The first order of business is to enable UFW if it is not already enabled. To do this click the slider tab next to Firewall Status, it should change to "On"

Once we have done this we can begin configuring our firewall policies. We will notice under the slider we just adjusted there is both an Incoming and and Outgoing policy, we want to make sure that both are set to Deny. This will block all traffic going in and out of our machine, don't worry we're going to allow some outbound traffic next.

The next thing we need to do is click on the little plus in the lower left hand corner of the Window. This will allow us to add new rules to our Firewall.

For this guide we will be creating restrictive policies, in order for us to do that we must know exactly what ports we need access to. This is going to be a fairly basic system and as such we are going to add rules to allow the following outbound traffic

DHCP Access - Port 67 and 68 UDP

Web Access - Ports 80 and 443 Protocol TCP

Email Access - Ports 25 and 110 , 143 Protocol TCP

DNS Access - Port 53 Protocol TCP and UDP (This is absolutely required)

Bittorrent Access Through Transmission - Bittorrent is different in that it uses a mulitude of unregistered ports to make connections. So we will use some of the added functionality of GUFW to give us this ability.

note : you may need additional services, look up the ports your service use. At the end of this post there will be a list of commonly used services and their default ports.

Now that we've clicked the plus to create our new rule, we will be presented with a window that looks like this.

[IMG]http://dangertux.no-ip.org/downloads/3.png[/IMG]

The first thing we will do is allow traffic from our Transmission Application. 

We choose the action Allow, the direction Out, the type Application and the application is Transmission. Once those settings are correct we click "Add"

Next we will click on the "Simple" tab in the Firewall : Add Rule window. 

We will then choose the rule Allow, Direction Out, Protocol TCP, and in the line following TCP we will add the TCP ports we want access to outbound. Which will look like this 25,53,80,110,443. Note when we add an additional port we seperate it from the last with a comma. Port ranges are indicated in this manner.

```

6667:7000

```This would indicate ports 6667 through 7000.

Once we have added our TCP outbound ports we must also remember to add any UDP outbound ports we need, in this case we will add port 53 for DNS.

We will choose the action Allow, direction is Out, Protocol is UDP and in the line beside UDP enter 53. Click on add and you are done.

(OPTIONAL)

If you wish to add more fine grained control you may do so in the advanced tab. For instance if you want to allow outbound SSH traffic only from your IP address to a specific IP address it would look like this.

[IMG]http://dangertux.no-ip.org/downloads/4.png[/IMG]

Once you have finished editing your rules as you want them, you are done and may close the Firewall: Add Rule window as well as GUFW


**Method 2 : UFW **

In this section we will create the exact same rules we did above however we will do so by utilizing UFW instead of the Graphical front end for it.

This section is done entirely from the command line. We will be creating the same policies as before, default drop inbound, default drop outbound, with rules allowing the services listed below.

DHCP Access - Ports 67 and 68 UDP

Web Access - Ports 80 and 443 Protocol TCP

Email Access - Ports 25 and 110 , 143 Protocol TCP

DNS Access - Port 53 Protocol TCP and UDP (This is absolutely required)

Bittorrent Access Through Transmission - Bittorrent is different in that it uses a mulitude of unregistered ports to make connections. 

So now that we know where we're going we are going to fire up a terminal window and create the same rules using UFW at the CLI.

First we want to enable UFW by doing the following

```

sudo ufw enable

```Then we want to enable our default inbound and outbound policies by doing the following

```

sudo ufw default deny incoming && sudo ufw default deny outgoing

```Now we will add our outbound TCP rules

```

sudo ufw allow out 25,53,80,110,443/tcp 

```Then our outbound UDP rules

```

sudo ufw allow out 53,67,68/udp

```And now our Transmission rule

```

sudo ufw allow out 51413/tcp
sudo ufw allow out 51413/udp
sudo ufw allow out 6969/tcp

```Restart your firewall for good measure.

```

sudo ufw disable && sudo ufw enable

```Then you're done.
[B]
Method 3 : iptables[/B]

This method in my opinion is the best, because it gives you the most control over your firewall. However iptables may not be for the new user. For completeness sake I will cover it here. 


Please note: iptables works best without UFW installed. So we will remove it now.
```

sudo apt-get remove ufw gufw

```Again in this section we will be enabling the same services as before.

DHCP Access - Ports 67 and 68 UDP

Web Access - Ports 80 and 443 Protocol TCP

Email Access - Ports 25 and 110 , 143 Protocol TCP

DNS Access - Port 53 Protocol TCP and UDP (This is absolutely required)

Bittorrent Access Through Transmission - Bittorrent is different in that it uses a mulitude of unregistered ports to make connections.

However, here I am going to walk you through the iptables script with the comments in the script, as opposed to step by step like the previous sections. You will want to create a file for your script, for this we will call it iptables.sh , but you can call it whatever you want. Below you will find the sample iptables script. 

```

#!/bin/bash
#Simple Firewall Script.


#Setting up default kernel tunings here (don't worry too much about these right now, they are acceptable defaults)
#DROP ICMP echo-requests sent to broadcast/multi-cast addresses.
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
#DROP source routed packets
echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route
#Enable TCP SYN cookies
echo 1 > /proc/sys/net/ipv4/tcp_syncookies
#Do not ACCEPT ICMP redirect
echo 0 > /proc/sys/net/ipv4/conf/all/accept_redirects
#Don't send ICMP redirect 
echo 0 >/proc/sys/net/ipv4/conf/all/send_redirects
#Enable source spoofing protection
echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter
#Log impossible (martian) packets
echo 1 > /proc/sys/net/ipv4/conf/all/log_martians

#Flush all existing chains
iptables --flush

#Allow traffic on loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT


#Creating default policies
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP #If we're not a router

#Allow previously established connections to continue uninterupted
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

#Allow outbound connections on the ports we previously decided.
iptables -A OUTPUT -p tcp --dport 25 -j ACCEPT #SMTP
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT #DNS
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT #HTTP
iptables -A OUTPUT -p tcp --dport 110 -j ACCEPT #POP
iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT #HTTPS
iptables -A OUTPUT -p tcp --dport 51413 -j ACCEPT #BT
iptables -A OUTPUT -p tcp --dport 6969 -j ACCEPT #BT tracker
iptables -A OUTPUT -p UDP --dport 67:68 -j ACCEPT #DHCP
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT #DNS
iptables -A OUTPUT -p udp --dport 51413 -j ACCEPT #BT

#Set up logging for incoming traffic.
iptables -N LOGNDROP
iptables -A INPUT -j LOGNDROP
iptables -A LOGNDROP -j LOG
iptables -A LOGNDROP -j DROP

#Save our firewall rules
iptables-save > /etc/iptables.rules

```Now that we have our script created we may save it and execute it

```

sudo chmod 755 iptables.sh
sudo ./iptables.sh

```Making your rules persistent :

If you want these rules to be restored on every reboot you can do the following. 

```

sudo nano /etc/network/interfaces

```Assuming wlan0 is the interface you use to connect to the network add the following at the end of the block. Alternatively you can add it to any interface you want and the rules will be loaded when that interface is brought up. Keep in mind this does not change the nature of the rules, or how they are applied.

```

pre-up iptables-restore < /etc/iptables.rules

```Then save the file.

This bit of information as well as other ways for making your iptables rules persistent can be found here : [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

We're done.
[B]

Common Ports and Services[/B]

FTP - 21 TCP
SSH - 22 TCP
TELNET - 23 TCP
SMTP - 25 TCP
DNS - 53 TCP/UDP
DHCP - 67 , 68 DHCP
HTTP - 80 TCP
POP3 - 110 TCP
IMAP - 143 TCP
HTTPS - 443 TCP
VNC - 5900-6000
IRC - 6667-7000
Gmail SMTP TLS: 587
Gmail SMTP SSL: 465
Gmail POP SSL:  995
Gmail IMAP SSL: 993

More here : [http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

Hopefully this was helpful to someone. This was done as a contribution  to the Security for Newbies Wiki thingy which can be found here : [http://ubuntuforums.org/showthread.php?t=1873643](http://ubuntuforums.org/showthread.php?t=1873643)


P.S : Sorry if the images load slowly my server has horrid bandwidth :-(

P.P.S : If this is in the wrong place feel free to move it, stick it delete it, throw it in a river, feed it to your dog, whatever's  clever

---

### Post by OpSecShellshock on 2011-11-05
So one or two things I wonder about:

A number of email clients and services use POP or IMAP, and those will have different server-side ports than SMTP uses. I'm not sure off the top of my head if that's relevant, but it might be worth letting folks know that it might come up. The same steps will apply, just with the relevant port number(s) being added.

The other thing is DHCP, which a lot of home routers are going to use. That I think uses 67 and 68, but I can't remember the protocol off the top of my head. I recall some of my own logs being full of DHCP denials in cases where I didn't allow it, and while I knew what it was I can see some cases where users might get nervous after seeing a log full of such denials.

This is an excellent post.

---

### Post by Dangertux on 2011-11-05
Yeah if you're having issues with any of the above check the services list at the end. I wasn't using DHCP for the VM I did this in, so that's a good point. It's edited to reflect DHCP as well.

---

### Post by Ms. Daisy on 2011-11-05
> **Dangertux said:**
> Yeah if you're having issues with any of the above check the services list at the end. I wasn't using DHCP for the VM I did this in, so that's a good point. It's edited to reflect DHCP as well.This is awesome!  You rock.  

I tried method #1 and subsequently blocked absolutely all internet traffic.  Whoops, I forgot to add port 53 UDP.  Now it's working.  If I can get it to work, then I'm going to call your guide idiot-proof.

---

### Post by Dangertux on 2011-11-05
Yeah dns is hugely important remember if you are using a dynamic ip you need to enable dhcp port 67 and 68 UDP or you will be very confused the next time you reset your network interface.

---

### Post by Bukie on 2011-11-07
> **Dangertux said:**
> Yeah dns is hugely important remember if you are using a dynamic ip you need to enable dhcp port 67 and 68 UDP or you will be very confused the next time you reset your network interface.


 Thank you for your help. Two quick questions though. 

 1) Where did you get this information from? I have read the information found on **[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)** as well as the man pages. Is there any other place I can look in order to learn more?  

2) My knowledge of ports is somewhat lacking but what if someone attempts to hack into my computer using a common port, say port 80? This is not a port I can block, obviously, but is there any other way to protect myself other than blocking that IP address?

---

### Post by Dangertux on 2011-11-07
> **Bukie said:**
> Thank you for your help. Two quick questions though. 

 1) Where did you get this information from? I have read the information found on **[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)** as well as the man pages. Is there any other place I can look in order to learn more?  

2) My knowledge of ports is somewhat lacking but what if someone attempts to hack into my computer using a common port, say port 80? This is not a port I can block, obviously, but is there any other way to protect myself other than blocking that IP address?

Knowledge of the commands and the applications used can be obtained by reading the man(ual) pages for the application in question. For instance man iptables

In terms of ports that need to be open. You can do your best to keep the service up to date with the latest security patches. Harden the configuration of the service (different for every service). In the case of a web server like Apache you could use something like Mod-Security which is a web application firewall. Also you could further confine a service through mandatory access controls such as apparmor or security enhanced linux.

Hope this helps.

---

### Post by Azrael84 on 2011-11-07
Does your transmission work with just these 51413/tcp 51413/tcp allow out rules added? I've added these as rules #1 and #2 before the deny all out/in final rules and transmission just wont start downloading a torrent unless I turn the ufw off.

---

### Post by Dangertux on 2011-11-07
The inbound rules should be the only ones effecting downloading the file themselves. And the connection should be considered established or related. As for 51413 being the default port for seeding, that is also correct. Yes, mine works fine.

---

### Post by Azrael84 on 2011-11-08
> **Dangertux said:**
> The inbound rules should be the only ones effecting downloading the file themselves. And the connection should be considered established or related. As for 51413 being the default port for seeding, that is also correct. Yes, mine works fine.

That is strange then, since I have added

```
[ 1] 51413/tcp                  ALLOW IN    Anywhere
[ 2] 51413/udp                  ALLOW IN    Anywhere
[ 3] 51413/udp                  ALLOW OUT   Anywhere (out)
[ 4] 51413/tcp                  ALLOW OUT   Anywhere (out)

```and yet transmission just does not start a torrent until the firewall is switched off and netstat shows:

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      1435/sendmail: MTA:
tcp        0      0 0.0.0.0:51413           0.0.0.0:*               LISTEN      2408/transmission-g
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      932/cupsd       
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1435/sendmail: MTA:
tcp        0      1 192.168.0.2:42033       109.235.55.11:6969      SYN_SENT    2408/transmission-g
tcp        0      1 192.168.0.2:55947       91.199.108.232:3310     SYN_SENT    2408/transmission-g
tcp        0      1 192.168.0.2:32817       62.149.5.203:80         SYN_SENT    2408/transmission-g
tcp        0      1 192.168.0.2:53229       122.224.5.45:2710       SYN_SENT    2408/transmission-g
tcp        0      1 192.168.0.2:46606       82.94.217.189:6970      SYN_SENT    2408/transmission-g
tcp        1      0 192.168.0.2:50260       216.137.57.143:80       CLOSE_WAIT  2156/gvfsd-http 
tcp        1      0 192.168.0.2:43195       216.137.57.225:80       CLOSE_WAIT  2156/gvfsd-http 
tcp        0      1 192.168.0.2:35167       194.54.80.150:6969      SYN_SENT    2408/transmission-g
tcp        1      0 192.168.0.2:46195       216.137.57.102:80       CLOSE_WAIT  2156/gvfsd-http 
tcp        0      1 192.168.0.2:55944       91.199.108.232:3310     SYN_SENT    2408/transmission-g
tcp        0      1 192.168.0.2:42197       193.107.16.156:2710     SYN_SENT    2408/transmission-g
tcp6       0      0 :::51413                :::*                    LISTEN      2408/transmission-g
tcp6       0      0 ::1:631                 :::*                    LISTEN      932/cupsd   

```Any idea why it wouldn't work for me to allow downloads? It seems to be listening on 51413 but maybe trying to do something else sending SYN on these other high ports?

---

### Post by Dangertux on 2011-11-08
Open up Transmission go to Edit > Preferences then the network tab. Make sure 'Port used for incoming connections' is 51413 and that pick a random port every time transmission is started is not checked.

See if this helps.

---

### Post by Lars Noodén on 2011-11-08
SSH gets hammered by brute force attacks pretty much from the moment it is first turned on.  An example of limiting the rate of connection attempts might be helpful.

---

### Post by Dangertux on 2011-11-08
This guide was designed for the desktop system running no services. However here is an example of using iptables to rate limit. 

```

iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set
iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 10 -j DROP

```

This will drop any connections that are attempted more than 10 times in 60 seconds to port 22 TCP. Keep in mind if you have a rule like this

```

iptables -A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT

```

the first rule must come before it.

Hope this helps.

---

### Post by Azrael84 on 2011-11-08
> **Dangertux said:**
> Open up Transmission go to Edit > Preferences then the network tab. Make sure 'Port used for incoming connections' is 51413 and that pick a random port every time transmission is started is not checked.

See if this helps.

Yep, those are the setting I have. So still no joy :(

It seems from netstat that transmission is listening on 51413 but is also attempting connections on various high number ports..

---

### Post by Dangertux on 2011-11-08
> **Azrael84 said:**
> Yep, those are the setting I have. So still no joy :(

It seems from netstat that transmission is listening on 51413 but is also attempting connections on various high number ports..


Okay this is really weird, I can't reproduce this 100% of the time but if you're having issues with bittorrent and this guide allow port 6969 TCP outbound in your firewall. For some reason some versions netfilter will consider the tracker connection RELATED others it does not, I'm not sure why. But that should fix your problem.

---

### Post by Azrael84 on 2011-11-08
> **Dangertux said:**
> Okay this is really weird, I can't reproduce this 100% of the time but if you're having issues with bittorrent and this guide allow port 6969 TCP outbound in your firewall. For some reason some versions netfilter will consider the tracker connection RELATED others it does not, I'm not sure why. But that should fix your problem.

Still no joy for me :(...well actually I did manage to get a torrent downloading at a very very very slow speed for a few seconds, but then nada on any others after that unless I turn the ufw off. After having a google, I wonder if for some reason when the firewall is on I need to do portforwarding on 51413 to allow transmission to work? I'm not not sure about this though..

---

### Post by Dangertux on 2011-11-08
You shouldn't have to port forward anything, since the firewall is local to the machine there is really nothing to port forward to.

---

### Post by tr333 on 2011-11-09
> **Lars Noodén said:**
> SSH gets hammered by brute force attacks pretty much from the moment it is first turned on.  An example of limiting the rate of connection attempts might be helpful.

I've found that fail2ban works wonders for brute force attacks.

---

### Post by Dangertux on 2011-11-10
Added a little bit to the iptables section. Because Debian based systems are stupid about iptables-save. Should solve some of the persistence problems several users have PM'ed me about where their iptables rules are disappearing when they reboot.

---

### Post by Doug S on 2011-11-13
An excellent posting, and it obviously took some time to do.
In method 3, iptables, I do not understand something about the peristent stuff. I understand the part about saving the rules and using the saved version on boot up (and I have used that method in the past). What I am not understanding is how the various /proc/sys/net bits would get set or reset as per the original script, as this part would not be done via the iptables-restore command. As mentioned in the comments in the example script, maybe it doesn't matter for this case. I use the rc level stuff to execute my firewall script on system startup, and actually didn't know about the pre-up method used in this example. If one needs it for some reason, such as some non-iptables related stuff, could the pre-up method just execute the original script? For example:```
pre-up /home/doug/init/iptables.sh
```

---

### Post by BigCityCat on 2011-11-13
This was awesome thanks. This and the security thread for newbies helped me get my firewall set up properly and inspired me to learn AppArmor. I finally got the AppArmor Firefox profile customized for me and working. More secure but didn't lose the functionality.

---

### Post by Dangertux on 2011-11-13
> **BigCityCat said:**
> This was awesome thanks. This and the security thread for newbies helped me get my firewall set up properly and inspired me to learn AppArmor. I finally got the AppArmor Firefox profile customized for me and working. More secure but didn't lose the functionality.

Great I'm glad it helped :-) 

Good luck with Apparmor if you have any questions feel free to ask [http://ubuntuforums.org/showthread.php?t=1049698](http://ubuntuforums.org/showthread.php?t=1049698)

---

### Post by GhettoYhetti on 2011-11-13
This was perfect!  Great detail!  And you were willing to update your post and took suggestions!

---

### Post by GhettoYhetti on 2011-11-13
Do you know if the log file rolls over?  I want to be able to log, but don't want a huge logfile to swim through.  

I guess I could cron something, but automagic from the provider usually works better.

---

### Post by Dangertux on 2011-11-13
> **GhettoYhetti said:**
> Do you know if the log file rolls over?  I want to be able to log, but don't want a huge logfile to swim through.  

I guess I could cron something, but automagic from the provider usually works better.

Thanks I'm glad it worked out for you. The log file for which? UFW or the iptables script? Both logs should continually roll ufw.log for ufw/gufw syslog for iptables blocks.

---

### Post by needhelppeeps on 2011-11-13
I think there should be a link to this thread in the stickies, very well documented. tutorials like this are what gets people from thinking they need to do something to actually implementing the available tools. Let's not let good threads like this go to waste.

---

### Post by Dangertux on 2011-11-13
> **needhelppeeps said:**
> I think there should be a link to this thread in the stickies, very well documented. tutorials like this are what gets people from thinking they need to do something to actually implementing the available tools. Let's not let good threads like this go to waste.

I'm very glad it was helpful to you, if you have any questions or issues feel free to ask :-)

---

### Post by BigCityCat on 2011-11-14
Dangertux

I have a small problem. I was trying to play spades on aolgames but apparently the firewall is blocking me from playing. When I turn off the firewall I can play, and with it on I can not. I googled ports and java but nothing definitive. Can you help me out with this?

---

### Post by Dangertux on 2011-11-14
> **BigCityCat said:**
> Dangertux

I have a small problem. I was trying to play spades on aolgames but apparently the firewall is blocking me from playing. When I turn off the firewall I can play, and with it on I can not. I googled ports and java but nothing definitive. Can you help me out with this?

I've never really used AOL games myself, however from what I'm able to see from google they use the default AIM ports which are 5190 through 5193 TCP. You could try allowing outbound from those.

Alternatively you can do this in a terminal

```

sudo watch netstat -anlp

```Then start trying to play the game you want and see what ports connections are being made on   (note the outbound ports and protocol it may be but probably isn't UDP). Then open up those ports as appropriate. Hope this helps, AOL's documentation of the games was less than impressive so this is kind of a guess, give the netstat some trial and error and you'll get it eventually.


Side tip : Always bet nil (it works for me lol)

---

### Post by BigCityCat on 2011-11-14
Okay I got it. Thanks once again. I keep learning new tricks. 443,80,8996

I am assuming that 8996 was the offender.

Thanks

---

### Post by Dangertux on 2011-11-14
> **BigCityCat said:**
> Okay I got it. Thanks once again. I keep learning new tricks. 443,80,8999

I am assuming that 8999 was the offender.

Thanks

Great I'm glad you were able to fix it. Sometimes those poorly documented applications can be a pain  to get working with a scheme like this.

---

### Post by Thewhistlingwind on 2011-11-14
> **Dangertux said:**
> Great I'm glad you were able to fix it. Sometimes those poorly documented applications can be a pain  to get working with a scheme like this.

Poorly documented applications are a pain to get working period, the functionality of a software is only as good as the amount of features it's user knows.

---

### Post by BigCityCat on 2011-11-14
yeh because it is still giving me problems. Sometimes it works and others not. Turn the firewall of and it fires right up. going to sleep now. gonna give it another go tomorrow.

---

### Post by Dangertux on 2011-11-14
> **BigCityCat said:**
> yeh because it is still giving me problems. Sometimes it works and others not. Turn the firewall of and it fires right up. going to sleep now. gonna give it another go tomorrow.

It may be a range of ports it's trying to use I just tried to play the game and it used port 9000 TCP when I tried.

Hope this helps.

---

### Post by Doug S on 2011-11-15
> **Doug S said:**
> An excellent posting, and it obviously took some time to do.
In method 3, iptables, I do not understand something about the peristent stuff. I understand the part about saving the rules and using the saved version on boot up (and I have used that method in the past). What I am not understanding is how the various /proc/sys/net bits would get set or reset as per the original script, as this part would not be done via the iptables-restore command. As mentioned in the comments in the example script, maybe it doesn't matter for this case. I use the rc level stuff to execute my firewall script on system startup, and actually didn't know about the pre-up method used in this example [edit: or had forgotten]. If one needs it for some reason, such as some non-iptables related stuff, could the pre-up method just execute the original script? For example:```
pre-up /home/doug/init/iptables.sh
```
I tried the pre-up method to execute my firewall script, which includes several non iptables commands, on system statrup and it worked fine. I will probably change to this method permanently.

---

### Post by Dangertux on 2011-11-15
> **Doug S said:**
> I tried the pre-up method to execute my firewall script, which includes several non iptables commands, on system statrup and it worked fine. I will probably change to this method permanently.


Wow I didn't even see that question back there. 

You have a valid point about setting the /proc/sys/net bits, they will be reset by sysctl on reboot (if they are defined there).

You can work around this via the method you mentioned with the runlevel script. Alternatively you could modify your/etc/sysctl.conf to reflect appropriately

---

### Post by BigCityCat on 2011-11-15
> **Dangertux said:**
> It may be a range of ports it's trying to use I just tried to play the game and it used port 9000 TCP when I tried.

Hope this helps.

yeh that was it. I did a range and it's working. You are awesome thanks.

---

### Post by Dangertux on 2011-11-15
> **BigCityCat said:**
> yeh that was it. I did a range and it's working. You are awesome thanks.

Glad it worked out for you :-)

---

### Post by spynappels on 2011-11-16
Hi DT,

Might be an idea to add the Gmail SSL imap and smtp ports:

Gmail SMTP TLS: 587
Gmail SMTP SSL: 465
Gmail POP SSL:  995
Gmail IMAP SSL: 993

Great how-to though.

Stefan

---

### Post by Ms. Daisy on 2011-11-16
> **spynappels said:**
> Hi DT,

Might be an idea to add the Gmail SSL imap and smtp ports:

Gmail SMTP TLS: 587
Gmail SMTP SSL: 465
Gmail POP SSL:  995
Gmail IMAP SSL: 993

Great how-to though.

StefanOr maybe more broadly, where does one go to find out what ports my services & hardware use? I suppose there's no big repository out there.  If you just watch what ports it uses on your machine, you won't see the range of ports if that's how they do it. Should I just google, for example, Gmail & Ports?

---

### Post by Dangertux on 2011-11-16
Generally speaking if you're using an application such as thunderbird to check your gmail or whatever as opposed to the web based interface those services provide you will know the ports it uses (since you likely configured it) If you didn't configure it you can consult that services documentation as it will usually point out what ports need to be used to communicate with the service.

As a side note, not related to the original two questions asked, I don't particularly condone use of an additional email client, surface area and all. It's adding another application to the mix that can be exploited, opening more avenues of communication for malicious code to utilize etc. 

That being said, I'll add the gmail ports to the list as it is a popular service.

---

### Post by ubun3 on 2011-11-16
well this takes a long time to learn.
going back to windows I feel safer at least I do not have to configure all these :(

---

### Post by Dangertux on 2011-11-16
> **ubun3 said:**
> well this takes a long time to learn.
going back to windows I feel safer at least I do not have to configure all these :(

There are three different methods illustrated you only have to use 1 of them, they all do the same.

As far as Windows goes you should really be doing the same there, basically firewall methodology is not different between platforms. By default neither Windows firewall, nor commercial products like Zone Alarm come in a particularly secure configuration. If you want to make a configuration equivalent to a default Windows Firewall simply do the following.

```

sudo ufw enable

```

Done.

Hope this helps.

---

### Post by sammiev on 2011-11-16
Hi Dangertux, I like to thank you for a well written thread. I checked a lot of my settings with yours as I did it cold and now I feel much better. :) Keep up the great work! :popcorn:

---

### Post by Dangertux on 2011-11-16
> **sammiev said:**
> Hi Dangertux, I like to thank you for a well written thread. I checked a lot of my settings with yours as I did it cold and now I feel much better. :) Keep up the great work! :popcorn:


Glad it was helpful. Thanks for the encouragement :-)

---

### Post by BigCityCat on 2011-11-18
Need help with my network wireless epson printer. Working on the network with firewall off. Not working with firewall on. Is it just a matter of ports?

---

### Post by Dangertux on 2011-11-18
> **BigCityCat said:**
> Need help with my network wireless epson printer. Working on the network with firewall off. Not working with firewall on. Is it just a matter of ports?

This could be several issues, since you didn't mention the model of your printer you need to consult the documentation. If it mentions the ports that must be utilized make sure you allow them. If it still does not work after that you may need to enable IGMP multicast traffic (your documentation should tell you this). Though none of these settings should have effected Ubuntu's default policy on that (except maybe the iptables method if you're using that let me know)

Hope this helps.

---

### Post by BigCityCat on 2011-11-18
I can't find anything on ports. It's a epson stylus nx 420. I have 631 allowed so I don't think it's ports.

> tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1308/cupsd
tcp        0      0 0.0.0.0:17500           0.0.0.0:*               LISTEN      1867/dropbox
tcp        0      0 192.168.1.71:45378      76.13.117.181:80        ESTABLISHED 1768/gnome-shell
tcp       38      0 192.168.1.71:53654      199.47.217.173:443      CLOSE_WAIT  1867/dropbox
tcp       38      0 192.168.1.71:42710      107.20.249.148:443      CLOSE_WAIT  1867/dropbox
tcp        0      0 192.168.1.71:45944      199.47.216.147:80       ESTABLISHED 1867/dropbox
tcp        0      0 192.168.1.71:59766      209.191.70.53:80        ESTABLISHED 1768/gnome-shell
tcp        0      0 192.168.1.71:42629      98.136.48.46:5050       ESTABLISHED 2055/telepathy-haze
tcp6       0      0 :::5298                 :::*                    LISTEN      2094/telepathy-salu
tcp6       0      0 ::1:631                 :::*                    LISTEN      1308/cupsd
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1459/dhclient
udp        0      0 0.0.0.0:57913           0.0.0.0:*                           933/avahi-daemon: r
udp        0      0 0.0.0.0:17500           0.0.0.0:*                           1867/dropbox
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           933/avahi-daemon: r
udp6       0      0 :::49284                :::*                                933/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                933/avahi-daemon: r

---

### Post by Dangertux on 2011-11-19
> **BigCityCat said:**
> I can't find anything on ports. It's a epson stylus nx 420. I have 631 allowed so I don't think it's ports.

Are you allowing cupsd input and output? Also are you using ufw or...? 


If you're using UFW/GUFW you might try doing the following

```

sudo ufw allow out to 224.0.0.0/4

```

That might fix your issue.

---

### Post by lambcrazy on 2011-11-19
all these things that are described are increasing my interest about the ubuntu . i am trying to install the ubuntu on my system .. i will try all these methods on my system .. .

---

### Post by BigCityCat on 2011-11-19
> **Dangertux said:**
> Are you allowing cupsd input and output? Also are you using ufw or...? 


If you're using UFW/GUFW you might try doing the following

```

sudo ufw allow out to 224.0.0.0/4

```

That might fix your issue.

edit post below.

---

### Post by sammiev on 2011-11-19
Hi folks. I'm using a pptp vpn and opened up the following ports on the firewall with no luck. Am I missing something here?

For PPTP:

    IP Protocol=TCP, TCP Port number=1723  <- Used by PPTP control path
    IP Protocol=GRE (value 47)  <- Used by PPTP data path

For L2TP:

    IP Protocol Type=UDP, UDP Port Number=500   <- Used by IKEv1 (IPSec control path)
    IP Protocol Type=UDP, UDP Port Number=4500 <- Used by IKEv1 (IPSec control path)
    IP Protocol Type=UDP, UDP Port Number=1701  <- Used by L2TP control/data path
    IP Protocol Type=50  <- Used by data path (ESP)

For SSTP:

    IP Protocol=TCP, TCP Port number=443   <- Used by SSTP control and data path

Update: If I start the VPN before the firewall all works great and even tested it on gaming sites which are closed to the firewall and my IPS address is not mine from my IPS. So all is working that way but I would perfer not having to do that every time I reboot. Thanks

---

### Post by BigCityCat on 2011-11-19
Found the solution by reading through countless threads and trying a bunch of things. I have no idea why this works but it does. Here is the solution.
> 
I fixed it by opening TCP 515 and UDP 1155. I don't know why the UDP port needs to be opened but it does.

Well that worked for the printer but not the scanner. Soo...I am off on another mission.

---

### Post by Dangertux on 2011-11-19
> **sammiev said:**
> Hi folks. I'm using a pptp vpn and opened up the following ports on the firewall with no luck. Am I missing something here?

For PPTP:

    IP Protocol=TCP, TCP Port number=1723  <- Used by PPTP control path
    IP Protocol=GRE (value 47)  <- Used by PPTP data path

For L2TP:

    IP Protocol Type=UDP, UDP Port Number=500   <- Used by IKEv1 (IPSec control path)
    IP Protocol Type=UDP, UDP Port Number=4500 <- Used by IKEv1 (IPSec control path)
    IP Protocol Type=UDP, UDP Port Number=1701  <- Used by L2TP control/data path
    IP Protocol Type=50  <- Used by data path (ESP)

For SSTP:

    IP Protocol=TCP, TCP Port number=443   <- Used by SSTP control and data path

Update: If I start the VPN before the firewall all works great and even tested it on gaming sites which are closed to the firewall and my IPS address is not mine from my IPS. So all is working that way but I would perfer not having to do that every time I reboot. Thanks

Your solution is not quite that simple If you're using ufw/gufw you need to do the following

sudo nano /etc/ufw/before.rules and find the following

```

# quickly process packets for which we already have a connection
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT

```change it to the following

```

# quickly process packets for which we already have a connection
-A ufw-before-input -p 47 -j ACCEPT
-A ufw-before-output -p 47 -j ACCEPT
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT

```If you're using iptables you need to add the following prior to the same lines in your iptables rules

```

iptables -A INPUT -p 47 -j ACCEPT
iptables -A OUTPUT -p 47 -j ACCEPT

```This will allow general router encapsulation protocol.

Hope this helps.
> **BigCityCat said:**
> Found the solution by reading through countless threads and trying a bunch of things. I have no idea why this works but it does. Here is the solution.

Well that worked for the printer but not the scanner. Soo...I am off on another mission.

Port 515 is the line printing daemon
Port 1155 is network file services 

So it makes sense that these are required, though most of this can be handled through cups , most printers are not made with Unix/Linux in mind.

---

### Post by sammiev on 2011-11-19
> **Dangertux said:**
> Your solution is not quite that simple If you're using ufw/gufw you need to do the following

sudo nano /etc/ufw/before.rules and find the following

```

# quickly process packets for which we already have a connection
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT

```change it to the following

```

# quickly process packets for which we already have a connection
-A ufw-before-input -p 47 -j ACCEPT
-A ufw-before-output -p 47 -j ACCEPT
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT

```If you're using iptables you need to add the following prior to the same lines in your iptables rules

```

iptables -A INPUT -p 47 -j ACCEPT
iptables -A OUTPUT -p 47 -j ACCEPT

```This will allow general router encapsulation protocol.

Hope this helps.


Port 515 is the line printing daemon
Port 1155 is network file services 

So it makes sense that these are required, though most of this can be handled through cups , most printers are not made with Unix/Linux in mind.

Thanks will try it in a bit. :)

---

### Post by Dangertux on 2011-11-19
> **sammiev said:**
> Thanks will try it in a bit. :)


Make sure you restart your firewall afterwards to apply the rules

```

sudo ufw disable && sudo ufw enable

```

Hope it works for you (though it should)

---

### Post by sammiev on 2011-11-19
Firewall and VPN worked in just seconds. Thanks for the help! Should be made into a "How To" :)

Now to clean out the extra unneeded opened ports I tried to get it working with.

---

### Post by Dangertux on 2011-11-19
> **sammiev said:**
> Firewall and VPN worked in just seconds. Thanks for the help! Should be made into a "How To" :)

Now to clean out the extra unneeded opened ports I tried to get it working with.


Glad it worked :-)

---

### Post by P.T. on 2011-11-21
I created a firewall with iptables and everything works, but when I scan  my pc for open ports (from another pc in the same network) it shows  closed ports:

```
PORT     STATE  SERVICE
80/tcp   closed http
139/tcp  open   netbios-ssn
443/tcp  closed https
445/tcp  open   microsoft-ds
8080/tcp open   http-proxy
```

They are closed because there is no service listening to them right now. Is there any way I can make those ports 'hidden' when no service is listening?

---

### Post by sammiev on 2011-11-21
> **P.T. said:**
> I created a firewall with iptables and everything works, but when I scan  my pc for open ports (from another pc in the same network) it shows  closed ports:

```
PORT     STATE  SERVICE
80/tcp   closed http
139/tcp  open   netbios-ssn
443/tcp  closed https
445/tcp  open   microsoft-ds
8080/tcp open   http-proxy
```

They are closed because there is no service listening to them right now. Is there any way I can make those ports 'hidden' when no service is listening?

This is what I was getting before the firewall setup and also before I went with a VPN as well. :) I'm still the same but I now have a new IP addie with no backward DNS. :)

---

### Post by Matrix01 on 2012-01-28
i am no sure how to determine whether ufw, gufw, or iptables.
is GUFW good for someone viewing videos a lot?

---

### Post by Dangertux on 2012-01-28
It doesnt they are three different methods for controlling the same thing. So long as you're creating the rules properly streaming video should not be affected as netfilter when properly configured is rather transparent. 

Hope this helps.

---

### Post by 0011235813 on 2012-02-02
> **Bukie said:**
> Thank you for your help. Two quick questions though. 

 1) Where did you get this information from? I have read the information found on **[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)** as well as the man pages. Is there any other place I can look in order to learn more?  

2) My knowledge of ports is somewhat lacking but what if someone attempts to hack into my computer using a common port, say port 80? This is not a port I can block, obviously, but is there any other way to protect myself other than blocking that IP address?

You know, you could try hardening the kernel to randomize ports, making you safer. I'm not sure exactly how that could done, but from what I've heard it requires the installation of software that need self-compilation, and the re-compiling of the Linux kernel.

On a side note, is there any way to make the firewall allow a certain programme through? Like through process ID? Since it would be nigh impossible to regulate outbound traffic on the firewall with a hardened kernel otherwise.

---

### Post by Dangertux on 2012-02-02
> **0011235813 said:**
> You know, you could try hardening the kernel to randomize ports, making you safer. I'm not sure exactly how that could done, but from what I've heard it requires the installation of software that need self-compilation, and the re-compiling of the Linux kernel.

On a side note, is there any way to make the firewall allow a certain programme through? Like through process ID? Since it would be nigh impossible to regulate outbound traffic on the firewall with a hardened kernel otherwise.

What are you talking about? You can't randomize the fact that your system is connecting to a service on port 80 when you visit this website. You can control related reverse connections but they are usually already randomized (based on free sockets) by the program requesting them (and the kernel). 

As far as limiting by pid with iptables you can limit by the owner of a process. Look at the match target --owner in the iptables man pages.

---

### Post by 0011235813 on 2012-02-03
> **Dangertux said:**
> What are you talking about? You can't randomize the fact that your system is connecting to a service on port 80 when you visit this website. You can control related reverse connections but they are usually already randomized (based on free sockets) by the program requesting them (and the kernel). 

As far as limiting by pid with iptables you can limit by the owner of a process. Look at the match target --owner in the iptables man pages.

I was refering to something someone mentioned on another thread.... I'm sorry if I didn't make any sense, mea culpa :(
I believe it was something called [http://grsecurity.net/](http://grsecurity.net/).

Is there any way to do this with ufw?

---

### Post by Dangertux on 2012-02-03
> **0011235813 said:**
> I was refering to something someone mentioned on another thread.... I'm sorry if I didn't make any sense, mea culpa :(
I believe it was something called [http://grsecurity.net/](http://grsecurity.net/).

Is there any way to do this with ufw?

GRSec is not a firewall, it deals with memory protection, and mandatory access controls. UFW is a frontend for iptables the front end for netfilter. Which has absolutely nothing to do with kernel level access or application level access to memory (other than that netfilter access memory itself).

Hope this helps.

---

### Post by 0011235813 on 2012-02-03
> **Dangertux said:**
> GRSec is not a firewall, it deals with memory protection, and mandatory access controls. UFW is a frontend for iptables the front end for netfilter. Which has absolutely nothing to do with kernel level access or application level access to memory (other than that netfilter access memory itself).

Hope this helps.

Sorry I think I confused you. My second paragraph was refering to what you mentioned about allowing process IDs with IP tables. I asked if there was any way that could be done with ufw.

---

### Post by Dangertux on 2012-02-03
> **0011235813 said:**
> Sorry I think I confused you. My second paragraph was refering to what you mentioned about allowing process IDs with IP tables. I asked if there was any way that could be done with ufw.

If you edit the /etc/ufw/before.rules you can add additional input/output rules based on iptables syntax. However I do not believe there is a process for doing it directly through the UFW interface though I could be wrong.

Hope this helps.

---

### Post by 0011235813 on 2012-02-03
> **Dangertux said:**
> If you edit the /etc/ufw/before.rules you can add additional input/output rules based on iptables syntax. However I do not believe there is a process for doing it directly through the UFW interface though I could be wrong.

Hope this helps.

Do you know what the iptables syntax is for allowing or denying process IDs is? I can gedit the file, but I have no inane knowledge of these syntaxes...

---

### Post by Dangertux on 2012-02-03
> **0011235813 said:**
> Do you know what the iptables syntax is for allowing or denying process IDs is? I can gedit the file, but I have no inane knowledge of these syntaxes...

iptables does not work like that, I already told you. It works by limiting the OWNER of the pid and that's dodgy anyway. As I said if you need syntax look in the man pages for the match target --owner.

Hope this helps.

---

### Post by BlinkinCat on 2012-02-17
Hi Dangertux, You may remember I created another thread regarding the second method of installing ufw. I have marked that thread as solved following kevdog's suggestion about looking at iptables. I will follow up with that but in the meantime I have another question for you. I will be surprised if there is not a simple answer to it but I am just confused. Regarding the rules for email access, Ports 25 and 110, 143 Protocol TCP - what happens to 143? -  The number 143 is not included in the input code. What happens to it? I have noticed that with the Thunderbird IMAP server the Port is 143.

I have had no luck in finding a solution to my problem in getting Thunderbird to work when ufw is connected. 

Thank you kindly for taking the time to answer,

Cheers - :)

---

### Post by Dangertux on 2012-02-17
> **BlinkinCat said:**
> Hi Dangertux, You may remember I created another thread regarding the second method of installing ufw. I have marked that thread as solved following kevdog's suggestion about looking at iptables. I will follow up with that but in the meantime I have another question for you. I will be surprised if there is not a simple answer to it but I am just confused. Regarding the rules for email access, Ports 25 and 110, 143 Protocol TCP - what happens to 143? -  The number 143 is not included in the input code. What happens to it? I have noticed that with the Thunderbird IMAP server the Port is 143.

I have had no luck in finding a solution to my problem in getting Thunderbird to work when ufw is connected. 

Thank you kindly for taking the time to answer,

Cheers - :)

You do not need to include port 143 in the input because it will be considered related,established if it is in conjunction with a connection to an external server.

So for instance when you connect to a mail server running on port 143 that is the destination port, the local port will be something like 31232 or whateve random port the mail client grabs.

port 31232 will be related or established to the rule that allows outbound traffic to port 143.

Does that make more sense?

---

### Post by kevdog on 2012-02-17
The best way to configure your firewall with iptables -- is to define the ruleset, and then try to access the service behind the firewall. If it doesn't connect or work as expected, check the log file to see what packet was dropped -- you're really going to have to get used to troubleshooting your firewall rules initially doing this since a lot of times ports want to get opened up different than what you expect.  

If you want I can post a fairly good iptables startup script that can be used as an example.  If you just spend some time looking at how the rules are written, you'll see a pattern and begin to understand the way INPUT/OUTPUT/FORWARD chains are constructed.  All dropped packets are logged, so its easy to examine either dmesg or /var/log/syslog to see the dropped packets.  You then modifiy your criteria trying to be restrictive as possible but buy allowing the blocked packet to pass (if that is your intention).

---

### Post by Lars Noodén on 2012-02-17
> **kevdog said:**
> ...If it doesn't connect or work as expected, check the log file to see what packet was [blocked]


That brings up a good point about [reject vs drop](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject).  If you use [reject instead of drop](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/) to block the packets, diagnosis and rule-building become much easier.

---

### Post by nrundy on 2012-02-17
> **BlinkinCat said:**
> Hi Dangertux, You may remember I created another thread regarding the second method of installing ufw. I have marked that thread as solved following kevdog's suggestion about looking at iptables. I will follow up with that but in the meantime I have another question for you. I will be surprised if there is not a simple answer to it but I am just confused. Regarding the rules for email access, Ports 25 and 110, 143 Protocol TCP - what happens to 143? -  The number 143 is not included in the input code. What happens to it? I have noticed that with the Thunderbird IMAP server the Port is 143.

I have had no luck in finding a solution to my problem in getting Thunderbird to work when ufw is connected. 

Thank you kindly for taking the time to answer,

Cheers - :)

BlinkinCat, an easy way to figure this all out is to run Comodo Firewall on MS-Windows. If you have access to a Windows machine, install Thunderbird and "Comodo Internet Security--Firewall Only." Once done, restart Windows and open Comodo > Firewall > Network Security Policy > Application Rules. Delete every single entry that is present. Now start Thunderbird and allow the prompts/popups that appear from the firewall. After you've allowed all the prompts, open the Comodo firewall log viewer and look and see what ports Thunderbird requested to use. Write down those port numbers and return to Ubuntu. Now configure those same ports to have TCP outbound access on ubuntu. Then everything will work.

It's hard to configure on Ubuntu because there is no log or prompts that communicate what application needs what ports at what time. I use Windows to figure it out and then replicate it on Ubuntu. On Windows, once you configure your applications within the Firewall you never receive anymore prompts UNLESS something unfamiliar tries to connect to the internet.

---

### Post by BlinkinCat on 2012-02-17
> **Dangertux said:**
> You do not need to include port 143 in the input because it will be considered related,established if it is in conjunction with a connection to an external server.

So for instance when you connect to a mail server running on port 143 that is the destination port, the local port will be something like 31232 or whateve random port the mail client grabs.

port 31232 will be related or established to the rule that allows outbound traffic to port 143.

Does that make more sense?

> **kevdog said:**
> The best way to configure your firewall with iptables -- is to define the ruleset, and then try to access the service behind the firewall. If it doesn't connect or work as expected, check the log file to see what packet was dropped -- you're really going to have to get used to troubleshooting your firewall rules initially doing this since a lot of times ports want to get opened up different than what you expect.  

If you want I can post a fairly good iptables startup script that can be used as an example.  If you just spend some time looking at how the rules are written, you'll see a pattern and begin to understand the way INPUT/OUTPUT/FORWARD chains are constructed.  All dropped packets are logged, so its easy to examine either dmesg or /var/log/syslog to see the dropped packets.  You then modifiy your criteria trying to be restrictive as possible but buy allowing the blocked packet to pass (if that is your intention).

> **nrundy said:**
> BlinkinCat, an easy way to figure this all out is to run Comodo Firewall on MS-Windows. If you have access to a Windows machine, install Thunderbird and "Comodo Internet Security--Firewall Only." Once done, restart Windows and open Comodo > Firewall > Network Security Policy > Application Rules. Delete every single entry that is present. Now start Thunderbird and allow the prompts/popups that appear from the firewall. After you've allowed all the prompts, open the Comodo firewall log viewer and look and see what ports Thunderbird requested to use. Write down those port numbers and return to Ubuntu. Now configure those same ports to have TCP outbound access on ubuntu. Then everything will work.

It's hard to configure on Ubuntu because there is no log or prompts that communicate what application needs what ports at what time. I use Windows to figure it out and then replicate it on Ubuntu. On Windows, once you configure your applications within the Firewall you never receive anymore prompts UNLESS something unfamiliar tries to connect to the internet.

Many thanks to you all for the detailed explanations - I thought there was likely to be a comparatively simple explanation - However it did confuse me.

Cheers - :)

---

### Post by nrundy on 2012-02-17
> **BlinkinCat said:**
> Many thanks to you all for the detailed explanations - I thought there was likely to be a comparatively simple explanation - However it did confuse me.

Cheers - :)

On my box 993 and 465 are used by Thunderbird (which is the SSL ports for IMAP email). So then that means that you would need to create an outbound rule within GUFW that allows protocol TCP outbound on ports 993 and 465. Yours may be different though depending on how you configured your IMAP connection. That's why I recommended using Windows to sort it out.

---

### Post by cariboo on 2012-02-17
> **nrundy said:**
> On my box 993 and 465 are used by Thunderbird (which is the SSL ports for IMAP email). So then that means that you would need to create an outbound rule within GUFW that allows protocol TCP outbound on ports 993 and 465. Yours may be different though depending on how you configured your IMAP connection. That's why I recommended using Windows to sort it out.

Using:

```
sudo lsof -i -P -n
```

Will also show what outbound port any running program is using, this is a snippet of the output:

```
chromium- 2221 cariboo   57r  IPv4  28566      0t0  TCP 192.168.1.225:54876->173.194.33.37:80 (ESTABLISHED)
chromium- 2221 cariboo   86u  IPv4  15596      0t0  TCP 192.168.1.225:46529->74.125.53.125:5222 (ESTABLISHED)
thunderbi 2480 cariboo   44u  IPv4  28846      0t0  TCP 192.168.1.225:43907->74.125.157.16:993 (ESTABLISHED)
thunderbi 2480 cariboo   49u  IPv4  28540      0t0  TCP 192.168.1.225:43913->74.125.157.16:993 (ESTABLISHED)
```

---

### Post by kevdog on 2012-02-18
Here is my iptables.sh script

Its an example of how to write iptables rules -- and I stress AN EXAMPLE!!.  But if you peruse the post, you'll see its quite easy to write these:

#!/bin/bash

### Gloval Variables
IPTABLES=/sbin/iptables
IP6TABLES=/sbin/ip6tables
MODPROBE=/sbin/modprobe
INT_NET=10.0.1.0/24
SSH_PORT=22
SERVER_INTERFACE=br0

##Function to determine Local IP address of server
getaddr() {
  dev=$1
  name=$2
  L=`ip addr show dev $dev | grep inet | grep -v :`
  test -z "$L" && { 
    eval "$name=''"
    return
  }
  OIFS=$IFS
  IFS=" /"
  set $L
  eval "$name=$2"
  IFS=$OIFS
}

getaddr $SERVER_INTERFACE SERVER_IP


### flush existing rules and set chain policy setting to DROP
echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

### this policy does not handle IPv6 traffic except to drop it.
#
echo "[+] Disabling IPv6 traffic..."
$IP6TABLES -P INPUT DROP
$IP6TABLES -P OUTPUT DROP
$IP6TABLES -P FORWARD DROP

### load connection-tracking modules
#
$MODPROBE ip_conntrack
$MODPROBE iptable_nat
$MODPROBE ip_conntrack_ftp
$MODPROBE ip_nat_ftp

###### INPUT chain ######
#
echo "[+] Setting up INPUT chain..."

### state tracking rules
echo "         .....State Tracking Rules"
$IPTABLES -A INPUT -m state --state INVALID -j LOG --log-prefix "DROP IN INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### anti-spoofing rules
#$IPTABLES -A INPUT ! -s $INT_NET -j LOG --log-prefix "SPOOFED PKT "
#$IPTABLES -A INPUT ! -s $INT_NET -j DROP

### ACCEPT rules
echo "         .....Common Ports"
$IPTABLES -A INPUT -p tcp -s $INT_NET --dport $SSH_PORT --syn -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

# CIFS/SMB ACCEPT Rules
echo "         .....CIFS/SMB"
$IPTABLES -A INPUT -p tcp -s $INT_NET --sport 137:139 --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p udp -s $INT_NET --sport 137:139 --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p tcp -s $INT_NET --sport 137:139 --dport 1024:65535 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p udp -s $INT_NET --sport 137:139 --dport 1024:65535 -m state --state NEW -j ACCEPT

# MULTICAST
echo "         .....Multicast"
$IPTABLES -A INPUT -p udp --dport 5353 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 5353 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -s 0/0 -d 224.0.0.0/24 -m state --state NEW -j ACCEPT

### default INPUT LOG rule
echo "         .....Default INPUT LOG Rule"
$IPTABLES -A INPUT ! -i lo -j LOG --log-prefix "DROP IN- " --log-ip-options --log-tcp-options

### make sure that loopback traffic is accepted
$IPTABLES -A INPUT -i lo -j ACCEPT

###### OUTPUT chain ######
#
echo "[+] Setting up OUTPUT chain..."

### state tracking rules
echo "         .....State Tracking Rules"
$IPTABLES -A OUTPUT -m state --state INVALID -j LOG --log-prefix "DROP OUT INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A OUTPUT -m state --state INVALID -j DROP
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules for allowing connections out
echo "         .....Common Ports"
$IPTABLES -A OUTPUT -p tcp --dport 21 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 2222 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 25 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 43 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 4321 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

## NoIP
echo "         .....NoIP"
$IPTABLES -A OUTPUT -p tcp --dport 8245 -m state --state NEW -j ACCEPT

# Multicast DNS
echo "         .....Multicast"
$IPTABLES -A OUTPUT -p tcp --dport 5353 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 5353 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -s $SERVER_IP -d 224.0.0.0/24 -m state --state NEW -j ACCEPT

# CIFS
echo "         .....CIFS"
$IPTABLES -A OUTPUT -p tcp --sport 137:139 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --sport 137:139 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --sport 1024:65535 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --sport 1024:65535 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT

# SMB
echo "         .....SMB"
$IPTABLES -A OUTPUT -p tcp -s $INT_NET --dport 445 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp -s $INT_NET --dport 445 -m state --state NEW -j ACCEPT 

## GMail SMTP
echo "         .....Gmail SMTP"
$IPTABLES -A OUTPUT -p tcp --dport 993 -m state --state NEW -j ACCEPT

### default OUTPUT LOG rule
echo "         .....Default OUTPUT LOG Rule"
$IPTABLES -A OUTPUT ! -o lo -j LOG --log-prefix "DROP OUT- " --log-ip-options --log-tcp-options

### make sure that loopback traffic is accepted
$IPTABLES -A OUTPUT -o lo -j ACCEPT

###### FORWARD chain ######
#
echo "[+] Setting up FORWARD chain..."

### state tracking rules
echo "         .....State Tracking Rules"
$IPTABLES -A FORWARD -m state --state INVALID -j LOG --log-prefix "DROP INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A FORWARD -m state --state INVALID -j DROP
$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

### anti-spoofing rules
#$IPTABLES -A FORWARD ! -s $INT_NET -j LOG --log-prefix "SPOOFED PKT "
#$IPTABLES -A FORWARD ! -s $INT_NET -j DROP

### ACCEPT rules
echo "         .....Common Ports"
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 21 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 25 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 43 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 4321 --syn -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p tcp --dport 53 -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p udp --dport 53 -m state --state NEW -j ACCEPT
#$IPTABLES -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT

# CIFS
echo "         .....CIFS"
$IPTABLES -A FORWARD -p udp -s $INT_NET --sport 137:139 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT

# MULTICAST
echo "         .....Multicast"
$IPTABLES -A FORWARD -p udp -s $INT_NET --sport 5353 -d 224.0.0.0/24 --dport 5353 -m state --state NEW -j ACCEPT

# Dynamic Device Discovery
echo "         .....Dynamic Device Discovery"
$IPTABLES -A FORWARD -p udp -s $INT_NET --sport 9131 --dport 9131 -m state --state NEW -j ACCEPT

### default LOG rule
echo "         .....Default FORWARD LOG Rule"
$IPTABLES -A FORWARD ! -i lo -j LOG --log-prefix "DROP F- " --log-ip-options --log-tcp-options

###### NAT rules ######
#
echo "[+] Setting up NAT rules..."


###### forwarding ######
#
echo "[+] Enabling IP forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward


exit
### EOF ###

---

### Post by BlinkinCat on 2012-02-18
> **cariboo907 said:**
> Using:

```
sudo lsof -i -P -n
```Will also show what outbound port any running program is using, this is a snippet of the output:

```
chromium- 2221 cariboo   57r  IPv4  28566      0t0  TCP 192.168.1.225:54876->173.194.33.37:80 (ESTABLISHED)
chromium- 2221 cariboo   86u  IPv4  15596      0t0  TCP 192.168.1.225:46529->74.125.53.125:5222 (ESTABLISHED)
thunderbi 2480 cariboo   44u  IPv4  28846      0t0  TCP 192.168.1.225:43907->74.125.157.16:993 (ESTABLISHED)
thunderbi 2480 cariboo   49u  IPv4  28540      0t0  TCP 192.168.1.225:43913->74.125.157.16:993 (ESTABLISHED)
```

Hi cariboo907 and guys,

I have produced the following, however I am unsure how to read it. Can someone interpret it please?

Thanks in advance - :)

```

firefox   2062 geoff   71u  IPv4 829808      0t0  TCP 10.1.1.2:44267->74.125.237.74:80 (ESTABLISHED)
thunderbi 2156 geoff   37u  IPv4 866313      0t0  TCP 10.1.1.2:36374->211.29.132.250:143 (ESTABLISHED)
thunderbi 2156 geoff   51u  IPv4 854939      0t0  TCP 10.1.1.2:36382->211.29.132.250:143 (ESTABLISHED)

```

---

### Post by kevdog on 2012-02-18
Sure -- lets just take one as an example since they are all similar:

thunderbi 2156 geoff   37u  IPv4 866313      0t0  TCP 10.1.1.2:36374->211.29.132.250:143 (ESTABLISHED)

Application thunderbird running under username geoff, (I believe 866313 is the process number), has an outgoing TCP port open on IP address 10.1.1.2 port number 36374 connecting to remote computer at 211.29.132.250 at port 143.  This connection is established.

A similar IPtables ruleset could be written for this connection (excluding the username) like this:
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A OUTPUT -p tcp -d 211.29.132.250 --dport 143 -m state --state NEW -j ACCEPT

If you didn't want to be so restrictive with the connecting IP address but only the port the second line could be:
$IPTABLES -A OUTPUT -p tcp --dport 143 -m state --state NEW -j ACCEPT

And if you wanted to be just super restrictive (meaning filter to exact IP address and by username:

$IPTABLES -A OUTPUT -p tcp -d 211.29.132.250 --dport 143 -m owner --uid-owner geoff -m state --state NEW -j ACCEPT

---

### Post by nrundy on 2012-02-18
> **cariboo907 said:**
> Using:

```
sudo lsof -i -P -n
```Will also show what outbound port any running program is using, this is a snippet of the output:

```
chromium- 2221 cariboo   57r  IPv4  28566      0t0  TCP 192.168.1.225:54876->173.194.33.37:80 (ESTABLISHED)
chromium- 2221 cariboo   86u  IPv4  15596      0t0  TCP 192.168.1.225:46529->74.125.53.125:5222 (ESTABLISHED)
thunderbi 2480 cariboo   44u  IPv4  28846      0t0  TCP 192.168.1.225:43907->74.125.157.16:993 (ESTABLISHED)
thunderbi 2480 cariboo   49u  IPv4  28540      0t0  TCP 192.168.1.225:43913->74.125.157.16:993 (ESTABLISHED)
```

true, but the output is evanescent and no log can be created of the output. It makes it hard to actually do stuff--you have to constantly be flipping back to check on the output. and since it's evanescent, if you don't check right away you miss stuff.

---

### Post by Ms. Daisy on 2012-02-18
> **nrundy said:**
> BlinkinCat, an easy way to figure this all out is to run Comodo Firewall on MS-Windows. If you have access to a Windows machine, install Thunderbird and "Comodo Internet Security--Firewall Only." Once done, restart Windows and open Comodo > Firewall > Network Security Policy > Application Rules. Delete every single entry that is present. Now start Thunderbird and allow the prompts/popups that appear from the firewall. After you've allowed all the prompts, open the Comodo firewall log viewer and look and see what ports Thunderbird requested to use. Write down those port numbers and return to Ubuntu. Now configure those same ports to have TCP outbound access on ubuntu. Then everything will work.

It's hard to configure on Ubuntu because there is no log or prompts that communicate what application needs what ports at what time. I use Windows to figure it out and then replicate it on Ubuntu. On Windows, once you configure your applications within the Firewall you never receive anymore prompts UNLESS something unfamiliar tries to connect to the internet.
I'll have to give this idea a try. I cannot for the life of me get the printer to function through the firewall.

However, surely there's a way to log the established connections in Ubuntu.  [This]("http://ubuntuforums.org/showthread.php?t=1158091") is super old, but does it still apply? 
```
iptables -I INPUT -m state --state NEW -j LOG --log-prefix "New Connection: " 
iptables -I OUTPUT -m state --state NEW -j LOG --log-prefix "New Connection: "
```

---

### Post by BlinkinCat on 2012-02-18
First of all, to the six contributors on this and the previous page, namely Dangertux, kevdog, cariboo907, nrundy, Lars Nooden and Ms.Daisy I am extremely grateful for all the time and effort you each have put in to help me. Hopefully the information you have brought forward will also be of benefit to others. To me, the iptables are a little confusing and will take me some time to learn up on. I have saved this and the previous page to study more closely at my leisure.

Secondly, I have finally got ufw working correctly on Thunderbird. It appears that I had two accounts set up as IMAP. When I was fiddling around to get myself out of this problem I decided to purge both accounts and create a new one. As a result, Thunderbird wouldn't let me create another IMAP account. Therefore I was left with the POP3 option. For whatever reason, I now find that Thunderbird sends and receives messages correctly with ufw activated. (Which it wasn't doing before) So right now I am quite pleased with the situation.

Therefore reiterating, I simply say thank you to you all for all of your assistance.

With kind regards,
BlinkinCat - :)

---

### Post by kevdog on 2012-02-18
> **Ms. Daisy said:**
> I'll have to give this idea a try. I cannot for the life of me get the printer to function through the firewall.

However, surely there's a way to log the established connections in Ubuntu.  [This]("http://ubuntuforums.org/showthread.php?t=1158091") is super old, but does it still apply? 
```
iptables -I INPUT -m state --state NEW -j LOG --log-prefix "New Connection: " 
iptables -I OUTPUT -m state --state NEW -j LOG --log-prefix "New Connection: "
```

This would log all input/output packets.  Is this what you want to do?

---

### Post by Ms. Daisy on 2012-02-18
> **kevdog said:**
> This would log all input/output packets.  Is this what you want to do?
I want to print and scan something, then look at some log & find out exactly what ports were used & when. Then I'd use that info to configure my firewall to allow my printer to function.

I tried watching the ufw logs while printing, then writing rules for all the ports that got blocked, but gufw still won't let the printer through.

---

### Post by kevdog on 2012-02-18
> **Ms. Daisy said:**
> I want to print and scan something, then look at some log & find out exactly what ports were used & when. Then I'd use that info to configure my firewall to allow my printer to function.

I tried watching the ufw logs while printing, then writing rules for all the ports that got blocked, but gufw still won't let the printer through.

Just want to make sure but it will print with the firewall completely disabled?

---

### Post by sammiev on 2012-02-18
> **Ms. Daisy said:**
> I want to print and scan something, then look at some log & find out exactly what ports were used & when. Then I'd use that info to configure my firewall to allow my printer to function.

I tried watching the ufw logs while printing, then writing rules for all the ports that got blocked, but gufw still won't let the printer through.

I ran into the same as you as needed to add this line in the rules. sudo ufw allow out to 224.0.0.0/4 Just a thought.

---

### Post by Ms. Daisy on 2012-02-18
> **kevdog said:**
> Just want to make sure but it will print with the firewall completely disabled?
Yup, perfectly
[QUOTE=sammiev]I ran into the same as you as needed to add this line in the rules. sudo ufw allow out to 224.0.0.0/4 Just a thought.     [/QUOTE]
I added that rule but communication with the printer is still blocked. Did you have to let the traffic in as well?

---

### Post by sammiev on 2012-02-18
> **Ms. Daisy said:**
> Yup, perfectly

I added that rule but communication with the printer is still blocked. Did you have to let the traffic in as well?

Nope but add port 631 for cups.

---

### Post by Ms. Daisy on 2012-02-18
I have an HP LaserJet M1522, multi-function printer.  I'll report what I did for it to work, hopefully it will help someone else along the way.

Yes, I've allowed out on port 631 (thanks sammiev).  I allowed out on ports 161, 162, and 9100 per [this guide]("http://hplipopensource.com/node/216") as well.

I read the [documentation]("http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=120&prodSeriesId=3442750&prodTypeId=18972&objectID=c01796004") for my printer which says the scanner uses TCP port 82980. ufw says that's a "bad port". I looked at my ufw logs & it's blocking 8289 during a (failed) scan, so I have to assume that's the actual port it's using.  

edit: on my other computer scanning used ports 8610:8614.  I guess you have to look at your logs to see what ports your computer will use to scan on this printer.

And I'm in business!  Thanks for the help guys. :D

---

### Post by JKyleOKC on 2012-02-19
> **Ms. Daisy said:**
> I read the [documentation]("http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=120&prodSeriesId=3442750&prodTypeId=18972&objectID=c01796004") for my printer which says the scanner uses TCP port 82980. ufw says that's a "bad port". I looked at my ufw logs & it's blocking 8289 during a (failed) scan, so I have to assume that's the actual port it's using.Just FYI, the largest port number is 65535, so any documentation that gives a larger number for any port HAS to be wrong. Checking the logs for failed attempts is the best way to get the correct values.

---

### Post by chickenPie4breakfast on 2012-03-02
I DONT understand the IP tables example you give. With the other methods you show how to set up incomming and outgoing ports but in the IPtables example I only see OUTPUT examples?

I chose to use the gui as I understood it, well thought I did but 
the main ports I was needing open for email were
587 out
995 in   (used to collect from hotmail)
I set these up and tried to acess my email in Thunderbird and Alpine (used in terminal) both could not connect.
I went  back to GUFW and clicked the incoming "Allow ALL"    the email could still not be collected.
I had to switch off the firewall altogether and then both email programs worked.

---

### Post by JKyleOKC on 2012-03-02
> **chickenPie4breakfast said:**
> I DONT understand the IP tables example you give. With the other methods you show how to set up incomming and outgoing ports but in the IPtables example I only see OUTPUT examples?You must have missed the two rules for the INPUT chain. The first rule allows any input packet with state ESTABLISHED to be accepted. The second forces any input packet that was not accepted by the first to be logged and dropped.

That's all that's necessary unless you want outsiders to be able to initiate connections to your machine. The large number of OUTPUT rules let you initiate outbound connections; any responses to those will have the ESTABLISHED state and be accepted by the single INPUT rule.

---

### Post by bohemian9485 on 2012-04-03
Thank you sir for a great tutorial that even a Linux newbie like me can understand. I have set up my firewall using GUFW (the easiest one) and I'm pretty much satisfied with the result. The only thing that needs tweaking is ktorrent. I have already added outbound rule for it but the torrent download would still stall. I have observed that if I change the outbound rule to allow and re-start the download, everything would back to normal, even when I re-enable the deny mode for outbound traffic. Why is it so?

---

### Post by WeAreLinux on 2012-04-11
This is my first time messing around with custom UFW rules, so before I mess up my config, I have a question.

Is the DHCP rules needed for proper function? 

I changed the default outgoing rule to deny, but only allowed ports for web browsing (80 & 443 TCP) & DNS (53 UDP) and my connection still works so I assume all will be fine? :-/

I basically only use this machine for web browsing. Its connected through a router. I was under the impression that a block all incoming rule would be strong enough till I read your guide.

Thank You

---

### Post by haqking on 2012-04-11
> **WeAreLinux said:**
> This is my first time messing around with custom UFW rules, so before I mess up my config, I have a question.

Is the DHCP rules needed for proper function? 

I changed the default outgoing rule to deny, but only allowed ports for web browsing (80 & 443 TCP) & DNS (53 UDP) and my connection still works so I assume all will be fine? :-/

I basically only use this machine for web browsing. Its connected through a router. I was under the impression that a block all incoming rule would be strong enough till I read your guide.

Thank You

Only if you use DHCP ;-)

Any service that is needed should have rules for proper function , any service that isnt shouldnt.

Peace

---

### Post by bohemian9485 on 2012-05-10
Now I have set my UFW incoming and outgoing rules to deny, and the simple ping command produced the following error:

```
ping: sendmsg: Operation not permitted
```

Even the Network Tools could not function properly.


Now my question is: what port should I open so network utilities like ping would not generate error?

---

### Post by Lars Noodén on 2012-05-10
> **bohemian9485 said:**
> Now my question is: what port should I open so network utilities like ping would not generate error?

You need to allow [ICMP](https://tools.ietf.org/html/rfc792) through.  At the very least, for ping, allow ICMP Echo-Request:

```

   iptables -A INPUT -p icmp --icmp-type echo-request \
        -m limit --limit 2/s -i eth0 -j ACCEPT

```

It would be good to let Traceroute through also.  Traceroute comes in as UDP on ports 33434-33535, or something like that.

---

### Post by Ms. Daisy on 2012-05-10
Choose to modify either iptables or UFW, but you have to stick to one or the other. 

The syntax for **UFW **to allow ICMP traffic (Lars Nooden showed it above for iptables) is this:

```
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
```

---

### Post by confused57 on 2012-05-10
> **Ms. Daisy said:**
> Choose to modify either iptables or UFW, but you have to stick to one or the other. 

The syntax for **UFW **to allow ICMP traffic (Lars Nooden showed it above for iptables) is this:

```
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
```

My /etc/ufw/before.rules shows the above icmp accepted by default, a google search mentioned to change the "ACCEPT" to "DROP" not to accept icmp requests.  I'm only beginning to be aware of security in Ubuntu, thanks to Dangertux's tutorial I'm trying to get ufw configured, but I guess it's OK to leave ufw at it's icmp defaults.  Thanks for all your work on the Basic Ubuntu Security Wiki putting it together with haqking, Dangertux, and many other contributors.

---

### Post by Electron on 2012-06-06
Question:

I have just installed and configure the firewall with the info here and everything work. However, my wireless network printer (it was tested before configure the firewall) is not working now. I know that is the firewall setting because when it is disable the printer work. So my question is how I create a rule to allow the printer? Can you point me out a link to get more info on this?

---

### Post by sammiev on 2012-06-06
> **Electron said:**
> Question:

I have just installed and configure the firewall with the info here and everything work. However, my wireless network printer (it was tested before configure the firewall) is not working now. I know that is the firewall setting because when it is disable the printer work. So my question is how I create a rule to allow the printer? Can you point me out a link to get more info on this?

Make sure TCP 631 is open. Also do a search on your printer as another port may need to be open. :)

---

### Post by confused57 on 2012-06-09
> **Electron said:**
> Question:

I have just installed and configure the firewall with the info here and everything work. However, my wireless network printer (it was tested before configure the firewall) is not working now. I know that is the firewall setting because when it is disable the printer work. So my question is how I create a rule to allow the printer? Can you point me out a link to get more info on this?

What I did was open ufw log file viewer and saw that port 9100 tcp was being blocked whenever I tried to access my HP wireless printer.
Opened the port in ufw & all was well.

---

### Post by CoyoteMX on 2012-09-19
@Azrael84; Hey, I had the same problem with Transmisson, you just have to add a rule for 80,6969/udp, wich are the ports used by trackers, cheers.

---

### Post by liju.g.chacko on 2012-11-18
Leopard Flower personal firewall for Linux (LPFW) gives the user control over which applications are allowed to use the network and is very easy to setup. Detailed steps are shown below


[LIST]
[*]These packages should be installed for compiling-
[LIST]
[*]  iptables
[*]  libnetfilter-queue
[*]    libnetfilter-conntrack
[*]    python-qt4
[*]    libnetfilter-queue-dev
[*]    libnetfilter-conntrack-dev
[*]    libcap-devlibpython2.6
[*]    zenity
[*]    python2.6-dev
[/LIST]
 
[/LIST]

[LIST]
[*]Download source code of leopard ( I have used leopard version -0.4 on ubuntu 12.04 i386)
[/LIST]

[LIST]
[*]extract the zip file
[*]Open terminal and cd to that directory
[*]    Execute following commands
[LIST]
[*]        mkdir build
[*]        cd build
[*]        make -C ../ DESTDIR=`pwd`
[/LIST]
 
[*]    Now 'build' folder will contain lpfw-pygui folder and three binary files lpfwcli, lpfw, lpfwgui, lpfw
[*]    Include one more file in this folder in the name 'leopardclient' and add following text into it
[/LIST]
        > #!/bin/sh
        set -e
        cd `pwd`
        #!/bin/sh
        pkill -9 -f lpfwgui.py
        cd /usr/local/leopardfirewall
        pidof lpfwpygui && yes=1 || yes=0
        if [ $yes -eq 1 ]
        then
            echo "Some other user has started lpfwpygui"
         else
            echo "starting lpfwpygui-1"
            ./lpfwpygui
        fi
[LIST]
[*]    Give execution permission to this file. (In Nautilus file manager-: property>permisssion> Execution: <tick>)
[*]    Copy build folder into /usr/local and rename as say, leopardfirewall (for that you have to open nautilus in as root user; execute:  sudo nautilus /usr/local )
[*]    Now make usergroup with name "lpfw" (Make use of Users and Group application). Don't add any user into this account
[*]    Now we have to start lpfw as root user on boot up, for that do following
[*]    In etc/init.d make a file in the name 'leopard' and add following text into it
[/LIST]
        > #!/bin/sh
        # Starts and stops leopard -lpfw
        #


        case "$1" in
        start)

            start-stop-daemon --start --exec /usr/local/leopardfirewall/lpfw
               
        ;;

        stop)
           
            start-stop-daemon --stop --exec /usr/local/leopardfirewall/lpfw
        ;;

        restart)
              $0 stop
              $0 start
        ;;


        *)
                echo "Usage: $0 {start|stop|restart|status}"
                exit 1
        esac
[LIST]
[*]    In etc/init make a file in the name 'leopard.conf' and add following text into it
[/LIST]
        > start on (starting networking and started rsyslog)

        exec /usr/local/leopardfirewall/lpfw
[LIST]
[*]    Now you restart PC and login , you will find that application cannot access internet. open terminal and execute '/usr/local/leopardfirewall/leopardclient'
[*]    Now gui will open and ask for your permission to allow/deny applications
[*]    Once you have allowed/denied permanently that rule will be added to /etc/lpfw.rules. and those applications can access internet even if you have not started leopardclient software.
[*]    If want to open  leopardclient from dash or application menu, do following
[*]    Make  a file in '/usr/share/applications/' in name 'LEOPARD.desktop' add the following and make execution bit true
[/LIST]
        > [Desktop Entry]
        Version=0.4
        Type=Application
        Terminal=false
        Exec=/usr/local/leopardfirewall/lpfw
        Name=Firewall-Leopard client
        Comment=Allows you to allow internet access
        Icon=/usr/share/icons/filefWo6iH.png
        Categories=Application;Network;[INDENT](see whether icon is present in the folder or assign a picture of your choice)
[/INDENT]
[LIST]
[*]Now Firewall-Leopard client will appear under internet applications
[/LIST]
 
:)-----------------------------------------------------------------------------------------------------------------------:)

---

### Post by bayvista on 2013-01-12
Thanks for the great guide. I installed GUFW and lost communication to my 2 wifi printers. Is there another port I need to allow?

---

### Post by cariboo on 2013-01-12
I'd suggest turning off your firewall, opening a terminal and enter the following command:

```
sudo watch netstat -anltp
```

then send a print job to each of your wireless printer,

you should see something like this:

```
tcp        0  27304 192.168.0.102:38328     192.168.0.109:9100      ESTABLISHED 32171/192.168.0.109
```

In the above example the ip address of the system I'm using is 192.168.0.102, and the ip address of the networked printer is 192.168.0.109. you can tell which ports they are using by the number after the ip address, in this case the host is using port #38328, and the printer is using port #9100. With this info in hand, you should be able to choose what ports to leave open in order to print.

---

### Post by six^letters^digits on 2013-06-04
the original Poster of this page :
Creating a Firewall for Your Ubuntu Desktop
     fails to include these pictures :
[http://dangertux.no-ip.org/downloads/1.png]("http://dangertux.no-ip.org/downloads/1.png")
[http://dangertux.no-ip.org/downloads/2.png]("http://dangertux.no-ip.org/downloads/2.png")
[http://dangertux.no-ip.org/downloads/3.png]("http://dangertux.no-ip.org/downloads/3.png")
[http://dangertux.no-ip.org/downloads/4.png]("http://dangertux.no-ip.org/downloads/4.png")

perhaps insert the images or use a third party ...

---

### Post by sammiev on 2013-06-04
> **six^letters^digits said:**
> the original Poster of this page :
Creating a Firewall for Your Ubuntu Desktop
     fails to include these pictures :
[http://dangertux.no-ip.org/downloads/1.png]("http://dangertux.no-ip.org/downloads/1.png")
[http://dangertux.no-ip.org/downloads/2.png]("http://dangertux.no-ip.org/downloads/2.png")
[http://dangertux.no-ip.org/downloads/3.png]("http://dangertux.no-ip.org/downloads/3.png")
[http://dangertux.no-ip.org/downloads/4.png]("http://dangertux.no-ip.org/downloads/4.png")

perhaps insert the images or use a third party ...

Your 4 links are dead.

---

### Post by Doug S on 2013-06-05
Yes, we know that dangertux's screen shots are no longer available. The rumor was that he had some server failure, and then never put them back. He is no longer around. Ms. Daisy (also no longer around) converted this this thread to a [wiki]("https://wiki.ubuntu.com/BasicSecurity/Firewall") and at one time was asking for help getting the old screen shots or making new ones. I see that someone just added note to the [wiki]("https://wiki.ubuntu.com/BasicSecurity/Firewall") about the missing screen shots.

---

### Post by J4nbhp4 on 2013-08-11
I know this is an old thread, but I wonder why the original author decided to default policy "DROP" all incoming connections. It makes it a lot easier to figure out why applications won't work with your firewall enabled when your default policy on the INPUT chain is ACCEPT and then drop&log everything that doesn't get explicitly accepted. Once you do this there will have to be a log with the source/destination IP and the source/destination PORT number. This should make it super easy to track down what the firewall is stopping from incoming. 

This same procedure can be done for the outgoing packets to. Oh well, probably a day late and a dollar short on my advice

---

### Post by Doug S on 2013-08-11
Yes, but aren't the default policy and creating a last catch all "log-n-drop" in the INPUT chain two independent things?
I do exactly what you are recommending, for exactly the reasons you mentioned, however my default policy is still "DROP". I merely expect to see 0 packets never hit the default policy rule (and they don't).

Also, some (not me) prefer to have a minimum number of entries in the log files and therefore prefer to have the packet dealt with silently.

---

### Post by J4nbhp4 on 2013-08-11
Well, as far as I know you have to log the packets before you drop them. The way my iptables look is I have the packets that I want to accept explicitly defined. Then I log all the other packets before before I drop them. If you drop them by default how are they getting logged? I am with you, once you get your iptables up and running, dropping by default might be a good thing, but if you are having issues then it pays to have everything logged accept the packets you want through. This way there is a clear and concise record of what is being dropped. No guessing on what ports need to be open, just check the log, find your IP or the ip of the service you are using and then check the ports. 

I guess maybe it is just me, but I really like my logs. When things break there is no better way to track down an issue then having a log to read to be parsed for answers. As long as log rotate is setup and working correctly you shouldn't be wasting that much space. Just something I have come to embrace, it is my one huge beef with other OS's, A lack of clear direction when something goes wrong, but not with linux.

---

