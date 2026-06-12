---
title: "HELP  I know I must have missed something simple :-)"
date: 2013-04-03
forum: Server Platforms
---

### Post by danshea on 2013-04-03
Hello Everyone.

I have not run a server in a while, but I just setup a pc running the latest Ubuntu server package and it installed fine. I also installed webmin and phpmyadmin. In the Ubuntu package,. I installed the OPENssh server, the LAMP server, the mail server and the mysql server. I have my domain pointing at my i.p. address and when you go to one of the domains I have ([www.socialpitchman.com]("http://www.socialpitchman.com")) , you can see that it is trying to go to my sevrer i.p. and open the page, but for some reason, it is not working. It just times out and then my i.p. address pops up into the address bar. I ran netstat -tlpn and the results are below. I am running apache 2 with virtual hosts and the conf. files fore the various sites are in the sites-available and the sites-enabled folders. what can I check next?    Thanks for your time.  Dan

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      16844/apache2   
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      1375/perl       
tcp        0      0 192.168.1.102:53        0.0.0.0:*               LISTEN      2434/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      2434/named      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      852/sshd        
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1170/master     
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      984/dovecot     
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      984/dovecot     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1003/mysqld     
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      984/dovecot     
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      984/dovecot     
tcp6       0      0 :::53                   :::*                    LISTEN      2434/named      
tcp6       0      0 :::22                   :::*                    LISTEN      852/sshd        
tcp6       0      0 :::25                   :::*                    LISTEN      1170/master     
tcp6       0      0 :::993                  :::*                    LISTEN      984/dovecot     
tcp6       0      0 :::995                  :::*                    LISTEN      984/dovecot     
tcp6       0      0 :::110                  :::*                    LISTEN      984/dovecot     
tcp6       0      0 :::143                  :::*                    LISTEN      984/dovecot

---

### Post by Doug S on 2013-04-03
When I try to go to the site you listed, a tcp session is opened and port 80 does respond, but I get a "301 moved permanently" response. The response also contains 76.29.34.164 as where it moved to, but that address never responds. For subsequent tries, my LapTop computer (a windows computer) never tries the original address again, only the referred to one. (this confused me for awhile as I was trying to capture the raw packets exiting my server with tcpdump).

---

### Post by danshea on 2013-04-04
Still trying to figure this out. So far, no luck.

---

### Post by darkod on 2013-04-04
Did you try the server local private IP? From another computer on the LAN, what happens if you try to open the server IP in a browser?

---

### Post by darkod on 2013-04-04
You said you installed a mail server too. Did you work on the configuration or not yet?

I am asking because the domain and the MX record seem to be pointed to different public IPs.
nslookup says that the domain is pointed to 50.63.202.23 (is that your public IP?) but the MX record is pointing to 72.167.238.201.

If the same machine is the web and mail server, they would be pointed to the same machine.

First of all do the local network check that I mentioned above, see if you can open the webserver from the local network. That will show you if apache2 is running fine. You can also try opening by domain name if you add it into your hosts file to see if it will open it locally.

---

### Post by Doug S on 2013-04-04
O.K. interesting... Darko mentioned an IP address which seemed odd to me, based on what I did last night. Indeed, the lookup address has changed since last night, when it was 184.168.221.30.
So now, at first I get a "moved temporiliy" response to some jibberish location, and then I get a TCP session reset reponse when my browser automatically tries the jibberish location. Then it gets a "moved perminently" response to the same IP address as my first post. 
So, and as Darko asked, what is your actual external IP address? Do you have a static external IP address? (I suspect not.) Does your ISP allow port 80 traffic?

---

### Post by darkod on 2013-04-04
They are both GoDaddy IPs. :)

So, I guess you didn't do the configuration in the GoDaddy panel correctly. You need to keep using their nameservers if you want to, but the main A host that says '@' you need to modify to point to your public IP where the web server will be. Otherwise as it is now, it will look for the website on the GoDaddy servers and it seems you haven't uploaded any files there. That is if you have a website hosting package at all, maybe you purchased only a domain registration.

---

### Post by danshea on 2013-04-04
Hi, 

I did changed my @ record on godaddy to point to my i.p. (76.29.34.164), and I believe if I park my nameservers in godaddy, then it should grab the @ record and direct the traffic to my server. The problem I am having is that when I parked my nameservers, and have my i.p. in the @ record and then check back on godaddy a couple hours later, the nameservers reverted back to "I have hosting with this account" and the i.p. changes to a godaddy i.p.. Very strange. I have now setup nameservers with freedns and have changed the nameservers in godaddy to point to the freedns nameservers which should then route the traffic to my sevrer. I have no idea why godaddy was reverting my changes. we'll see what happens with the nameserver change. Maybe that was the issue. If I am at my house and go on my laptop and open a browser and put in the local i.p. of the server (192.168.1.102), then the site comes up. I will add the site to the "Hosts" file and see how that goes. Is there anything else I should look at?

Thanks for your help.   Dan

---

### Post by Doug S on 2013-04-04
O.K. so your external IP address is 76.29.34.164: Last night there was no reply at all for TCP session SYN packets on port 80. ICMP echo worked fine.
Eariler today, there was now a response "ICMP host 192.168.1.101 unreachable", suggesting port forwarding is been used, and I assume your server is on your local lan at 192.168.1.101
Right now, and going by ip address only, name servers left out of it, I get the same ICMP response to a TCP SYN request to 76.29.34.164 port 80.
I wonder if there is some port forwarding issue or some firewall (iptables or ufw) rules on your server preventing the session.

If you run a tcpdump session (or wireshark if you prefer) on your server, do you see port 80 stuff coming in to it when someone tries from the WAN? Example:```
sudo tcpdump -n -nn -tttt -i eth1 port 80
```change eth1 to whatever interface is right for your server.

---

### Post by darkod on 2013-04-04
I think the original mistake was to change both the @ host and the nameservers. You should have left the GoDaddy nameservers to run the show, and you only work with the hosts and MX record. That takes the complication of running a DNS server off your shoulders. If you changed only the @ record, it would have worked great provided your ISP is not blocking port 80.

One reason why the nameservers might have reverted back is if your DNS server is not set up correctly or if it wasn't reachable. I think if GoDaddy system can't detect the nameservers you tried using, it will revert back.

The freedns was not necessary, you can control everything with GoDaddy.

---

### Post by danshea on 2013-04-04
Thanks Doug, I will run that when I get home today. 

I have 5 domains setup socialpitchman.com and thriftypeeps.com are using freedns and configured to my external i.p.  biddock.com, bazoodle.com and preownedentertainment.com are all using godaddy nameservers and I have the @ record pointing to my external i.p. . Port 80 is not blocked by my isp, so is there something I can look up in the iptables? I am also using a lynksys router and have multiple devices running off of it. I have the port forwarding setup for my internal i.p. (192.168.1.102 and 192.168.1.101). I know it must be something simple, but so far it is alluding me... :-)

---

### Post by darkod on 2013-04-04
Do you have a way to try from outside your home network? The problem is that many home routers can't send back the connection right away after you went out to the internet from it. And that's exactly what you are trying to do when trying to open the website from inside your home network.

You type the domain, it asks the DNS where is it, it gets the IP, and then your computer goes out of your router to the internet and then tries to go back right away since the public IP is your public IP.

Lots of home routers can't do that. But trying from another place, would help you rule that out.

You can view the accepted and blocked packets of iptables with:
sudo iptables -L

Flushing rules and allowing access for all:
sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT

Be careful when flushing if this is a remote server. Since it's in your home I guess you have terminal access too since flushing can leave you locked out. I think a better option is to run the flush command after setting the ACCEPT policies, at the end. But I'm not 100% sure. Doug knows more and will be able to comment on that.

---

### Post by danshea on 2013-04-04
Hi Darkod, I have tried to access my server and sites away form home (at work), and still don't get a response. I will check the ip tables and do the flushing and see what happens. I am also thining I may have missed something in the router. I'll have to plug my server directly into my modem to rule that out. DanThanks,

---

### Post by danshea on 2013-04-04
HOORAY, I am ALMOST there. one of my sites [www.biddock.com](www.biddock.com) works! Now the issue I have is that the other sites I have are all pulling up the biddock page even though I have the document root for each one set to go to their own. folders. Check Bazoodle.com or any of the others and you can see how they all resolve to Biddock. How do I get each one to go to its own folder? They should be doing name based, but it doesn't seem to be working.

Thanks,
Dan

---

### Post by danshea on 2013-04-04
I finally got it. had to change the ports.conf to the internal i.p. , now they all resolve to the server and each one to it's own folder. Thank you all for the help. !!:D

---

### Post by Doug S on 2013-04-04
Everything seems O.K. from here, except bazoodle.com goes to biddock.com web page. The others from your list above are O.K. However [www.bazoodle.com]("http://www.bazoodle.com") works, just bazoodle.com goes to the wrong page. Double check the aliases and such.

---

### Post by danshea on 2013-04-04
Done, Bazoodle now goes to it's own folder... :-)

---

### Post by Doug S on 2013-04-04
I guess I was trying things at the same time as you made changes. Now all is O.K.
But what about the original problem where it wasn't responding at all, except for the ICMP unreachable thing. What was the issue there?

---

### Post by danshea on 2013-04-04
Not sure, but I deleted the freedns stuff and am just using the godaddy nameservers. It may have had something to with the router ( I changed the port forwarding), or the firewall.

---

