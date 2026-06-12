---
title: "EEK!  An Open Port!  Is security compromised? Is it really open?"
date: 2012-04-09
forum: Security
---

### Post by slowtrain on 2012-04-09
It looks like an unnerving number of people are interested in hacking my machine, which has been online for a week.  I've already got over 15 entries in denyhosts of ip's trying to guess my root password.

So, a two-part question for the security experts here:  1) I have firestarter installed on my system and had only port 22 and another port open on it.  Does that mean other ports are closed?  Nmap doesn't seem to think so (see below).  2) That 'other port' was an arbitrary port in the 6000 range I left open to experiment with WOL.  I closed it today, but how likely is it that someone hacked the machine through it?

About 1):  nmap, run from another machine, tells me there are 15 ports open on my computer, which is running the latest Ubuntu.  This is stuff like smtp, http, pop3, imap, sun-answerbook.  I guess this is software that came with my default installation.  But with firestarter set to only allow 22 and that 6000 port, are these *really* open?  I tried connecting to http w/ a browser and nothing happens.

As for 2):  If there's a decent chance the machine could be hacked through that port is there any way to see if something used my WOL port?  I tried scanning the auth.log and kern.log for the port # but found nothing.

---

### Post by Dangertux on 2012-04-09
> **slowtrain said:**
> It looks like an unnerving number of people are interested in hacking my machine, which has been online for a week.  I've already got over 15 entries in denyhosts of ip's trying to guess my root password.

So, a two-part question for the security experts here:  1) I have firestarter installed on my system and had only port 22 and another port open on it.  Does that mean other ports are closed?  Nmap doesn't seem to think so (see below).  2) That 'other port' was an arbitrary port in the 6000 range I left open to experiment with WOL.  I closed it today, but how likely is it that someone hacked the machine through it?

About 1):  nmap, run from another machine, tells me there are 15 ports open on my computer, which is running the latest Ubuntu.  This is stuff like smtp, http, pop3, imap, sun-answerbook.  I guess this is software that came with my default installation.  But with firestarter set to only allow 22 and that 6000 port, are these *really* open?  I tried connecting to http w/ a browser and nothing happens.

As for 2):  If there's a decent chance the machine could be hacked through that port is there any way to see if something used my WOL port?  I tried scanning the auth.log and kern.log for the port # but found nothing.

An open port does not necessarily signify a vulnerable service. It is conceivable that if a service is accessible it can be compromised. With the information you've provided nobody here can give you an accurate "what are the chances of" which is nothing but dulled down risk assessment. If they try, they're lying.

As far as nmap goes, what syntax did you use on nmap, and what firewall rules do you have in place with firestarter (Which btw is not supported any longer). It is conceivable that your firewall is set to permit traffic from your local lan, but not the internet. Meaning an nmap scan internally would show up different than an external scan.

If the machine was compromised, you could attempt auditing logs, but depending on the level of compromise they may or may not be valuable any more.

I hope this helps, truthfully you have not provided enough information to really give an accurate assessment.

Like I said, specifics on firewall rules would be necessary to explain the nmap scan. Also a list of what services you're running (netstat -anlp would work) 

Additionally , the syntax you're using with nmap as well as any logs you feel may indicate your machine is compromised.

Thanks.

---

### Post by CharlesA on 2012-04-09
+1 to what DT said. I'd recommend using ufw or gufw instead of firestarter as it is no longer supported.

The firewall rules you have in place would probably be a good idea.

---

### Post by abyrne on 2012-04-09
If you're using any kind of router, they usually block all incoming ports by default, opening only the ports explicitly specified by you. 

I used to get a bunch of fail log entries as well, my solution was to set SSH to use a non-standard port (say port 2211 instead of 22) and to install a log monitor called fail2ban.

---

### Post by bubylou on 2012-04-10
Definitely change the default port for ssh. Anyone can scan the internet for ssh on port 22 and attempt to brute force it. But be aware this doesn't make you invincible against these types of attacks. Make sure to beef up your ssh security. Such as disable root, key authentication, etc.

---

### Post by slowtrain on 2012-04-10
Thanks for all the input!

bubylou, abyrne:  Good advice on changing the port #.  Am thinking of perhaps using port knocking.  I suspect that denyhosts plus a strong password, which I have, are pretty good but changing the port should help.

CharlesA:  Yup, I should get into ufw.

Dangertux:  Thanks!  I found your security discussions on UFW and will
follow the directions there.  Still, would like to figure out how much of a risk I have been running first--maybe I should reinstall the system.

I nmap'ed from outside my LAN and I see the same IP addresses open as from inside.  I'm using:

nmap -sT MyIpaddress

As for firewall rules, firestarter is GUI, so there isn't a lot of code I could paste here (unless there's some way of using the terminal to generate a list).  The Policy is to "Allow connections from host"--no one.  "Allow service"--port 22 and that port 6k I mentioned (until I shut it yesterday).  My understanding is that firestarter shuts all incoming traffic unless it is specifically allowed.  That's why I'm puzzled that nmap shows 15 ports open (and not even 'filtered'), though I can't tell whether there's really anything responding on these ports, except SSH.

If I understand you correctly, then I may not have a problem with my WOL port.  I opened a port to experiment with wakeonlan, but did not, to my recollection, install any kind of listening software yet.  If I understand you, the problem isn't open ports but open ports + exploitable listening software?

I've attached a file w/ output from nmap (run from another machine outside my lan; run from on my machine it only shows the 1st two ports open--also confusing) as well as netstat -anlp, which it sounded like you wanted to see (it's pdf--the forum wouldn't let me upload a text file this size).  Should be a pretty standard implementation for Oneiric--which also surprises me--why would they have so many ports open by default?

Thanks again for such a terrific set of responses!

Added the list of services/netstat results ~ CharlesA

```
Starting Nmap 5.00 ( http://nmap.org ) at 2012-04-10 12:43 EDT
Interesting ports on :
Not shown: 983 filtered ports
PORT STATE SERVICE
22/tcp open ssh
25/tcp open smtp
80/tcp open http
110/tcp open pop3
119/tcp open nntp
143/tcp open imap
443/tcp open https
465/tcp open smtps
563/tcp open snews
587/tcp open submission
993/tcp open imaps
995/tcp open pop3s
3128/tcp open squid-http
8008/tcp open http
8080/tcp open http-proxy
8081/tcp open blackice-icecap
8888/tcp open sun-answerbook
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN 915/sshd
tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 1106/cupsd
tcp 0 0 0.0.0.0:25 0.0.0.0:* LISTEN 1536/master
tcp 1 0 myIPaddress:53574 23.15.7.43:80 CLOSE_WAIT 2367/gweather-apple
tcp 0 0 myIPaddress:40753 74.125.228.21:443 ESTABLISHED 13930/firefox
tcp 0 0 myIPaddress:56835 74.125.228.22:443 ESTABLISHED 13930/firefox
tcp6 0 0 :::22 :::* LISTEN 915/sshd
tcp6 0 0 ::1:631 :::* LISTEN 1106/cupsd
tcp6 0 0 127.0.0.1:39973 :::* LISTEN 5822/java
udp 0 0 0.0.0.0:68 0.0.0.0:* 4847/dhclient
udp 0 0 0.0.0.0:41531 0.0.0.0:* 938/avahi-daemon: r
udp 0 0 0.0.0.0:5353 0.0.0.0:* 938/avahi-daemon: r
udp6 0 0 :::5353 :::* 938/avahi-daemon: r
udp6 0 0 :::47852 :::* 938/avahi-daemon: r
```

---

### Post by CharlesA on 2012-04-10
> **slowtrain said:**
> 
```
Starting Nmap 5.00 ( http://nmap.org ) at 2012-04-10 12:43 EDT
Interesting ports on :
Not shown: 983 filtered ports
PORT STATE SERVICE
22/tcp open ssh
25/tcp open smtp
80/tcp open http
110/tcp open pop3
119/tcp open nntp
143/tcp open imap
443/tcp open https
465/tcp open smtps
563/tcp open snews
587/tcp open submission
993/tcp open imaps
995/tcp open pop3s
3128/tcp open squid-http
8008/tcp open http
8080/tcp open http-proxy
8081/tcp open blackice-icecap
8888/tcp open sun-answerbook
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
**tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN 915/sshd**
tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 1106/cupsd
**tcp 0 0 0.0.0.0:25 0.0.0.0:* LISTEN 1536/master**
tcp 1 0 myIPaddress:53574 23.15.7.43:80 CLOSE_WAIT 2367/gweather-apple
tcp 0 0 myIPaddress:40753 74.125.228.21:443 ESTABLISHED 13930/firefox
tcp 0 0 myIPaddress:56835 74.125.228.22:443 ESTABLISHED 13930/firefox
**tcp6 0 0 :::22 :::* LISTEN 915/sshd**
tcp6 0 0 ::1:631 :::* LISTEN 1106/cupsd
tcp6 0 0 127.0.0.1:39973 :::* LISTEN 5822/java
[COLOR="Blue"]udp 0 0 0.0.0.0:68 0.0.0.0:* 4847/dhclient
udp 0 0 0.0.0.0:41531 0.0.0.0:* 938/avahi-daemon: r
udp 0 0 0.0.0.0:5353 0.0.0.0:* 938/avahi-daemon: r
udp6 0 0 :::5353 :::* 938/avahi-daemon: r
udp6 0 0 :::47852 :::* 938/avahi-daemon: r[/COLOR]
```

Added bold and colors. The only services that you have listening on external interfaces are sshd and smtp. avahi has something to do with local link communication and dhclient is what grabs an IP from DHCP.

Overall it looks good. Do you have any other boxes hooked up to the same router?

---

### Post by slowtrain on 2012-04-11
CharlesA:  Thanks for explaining how to read this info!  It sounds like there aren't a lot of services listening, which is good.  I wonder why nmap seems to think there are 15 services w/ open ports?

Dangertux or others:  I tried GUFW.  The good news:  my office machine is now quite secure.  The bad news:  I couldn't access it through port 22 from my laptop at the office--which I need to rsync the machines.  I added a preprogrammed rule in GUFW for SSH service to allow from ANYWHERE, and rebooted and tried repeatedly.  The error I got was "ssh_exchange_identification: Connection closed by remote host."  When I went and tried to connect from home a few hours later, no problem.  Today, again, I can't connect from the laptop at the office.  The laptop is on a separate network, but never had a problem connecting before under Firestarter.

I've now gone back to Firestarter and seem to have the same problem (same error msg for a turn or two, and then "ssh: ... Connection timed out" and then back to the previous 'connection closed' msg when I restarted ssh).  I checked denyhosts--no evidence it's blocking my laptop.  The ssh service appears to be listening on 22 according to netstat, plus I reinstalled and restarted ssh.  I don't see the connection attempts in either auth.log or in Firestarter events.

Any clues on what might be going on here?

---

### Post by CharlesA on 2012-04-11
When you switched to ufw, did you create a rule to allow traffic on port 22?

---

### Post by slowtrain on 2012-04-11
Hi CharlesA:  Yup, in GUFW, I activated the preprogrammed SSH allow for Anywhere & then rebooted.  This really is perplexing, esp. given that the problem seems to persist when I turn off ufw with GUFW (and then completely remove it) and reinstall Firestarter and reboot.  iptable can't persist rules between boots, at least not unless I set that up, right?  ufw is still installed.  maybe I'll try completely removing that as well.

Am beginning to wonder whether the network administrators changed something just as I started experimenting with ufw.  Quite a coincidence, but I've got an email in to them.

---

### Post by slowtrain on 2012-04-11
Ok, I think I may have figured out what is happening.  Apparently the ipaddress for my laptop is a private one, so when it goes outside to the network my desktop is on, it gets rewritten.  The rewritten ipaddress *does* appear in my denyhosts ipaddress bad list.  Not really sure why, because I doubt I tried to guess my password 3 or more times, but maybe denyhosts was counting failed connection attempts.  Now, just to verify that someone isn't somehow running a man in the middle attack.

Anyway, whew!

---

### Post by CharlesA on 2012-04-12
SSH will tell you the host key has changed and display a warning if you are being man-in-the-middle'd.

In any case, you would have to allow the public IP of the machine you are connecting from thru the firewall in order to connect.

---

### Post by cariboo on 2012-04-12
@slowtrain. I have to ask, are you connected to the internet through an educational institute, or from work, because the results from your nmap scan, don't look like a home router.

---

### Post by slowtrain on 2012-04-12
CharlesA:  Thanks!  I now have several reasons to think the address is legit.

cariboo907:  You're right, the desktop is a personal research machine at my workplace.

All:  Looks like the fun isn't over yet!  Yes, I was right that denyhosts was the source of the problem and taking the rewritten ipaddress of my laptop out of hosts.deny would fix the issue.  But, that ipaddress appears magically back in the list every time I connect. 

The basic problem looks like this:  Reboot the machine.  Completely remove and then reinstall denyhosts.  Remove the laptop (external) address from hosts.deny.  Connect from the laptop to the desktop using ssh.  And, without doing anything else, look back in my hosts.deny file and my laptop's (external) ipaddress has reappeared in it!

My best guess as to what is happening is that ssh is shifting from port 22 to some other port once the connection is formed and denyhosts then treats the connection as illegitimate and adds the ipaddress to hosts.deny.  The auth.log entry for my ssh connection looks like this:  Accepted password for slowtrain from myLaptopIPaddress port 55379 ssh2 .  I'm just using standard ssh syntax and the firewall won't accept anything coming in other than on port 22, so I can only imagine ssh is moving the connection to this other port.  It probably has to in case there's more than one ssh connection.  This probably means I can only connect once from home as well.

But, before putting UFW on my machine I didn't have this problem and could connect w/ SSH as much as I liked.  On the other hand, I don't know that this is causal.  I've now shut down UFW and reinstalled Firestarter, but the problem persists.  On the other hand, maybe something UFW did to some configuration file that remains is making this happen?  Thoughts?

I wonder if I should start a new thread with this problem.

---

### Post by slowtrain on 2012-04-14
Ok, I'll bump my new problem to a new thread.

---

### Post by kevdog on 2012-04-16
The port listed in your logs is the source port.  The destination port on the server is port 22.  This does not change after the connection is made.  The source port however may change between different logins as usually a high random port number is chosen as the source port.

I'm sure you know for example you can whitelist certain IP addresses or certain blocks of addresses with the firewall, and not just filter by port number.

Just a personal opinion -- and take it only as this -- but since this is a "research" computer, ditch ufw/gufw and just communicate directly to netfilter through iptables directly.  Its not very difficult to do, and it gives you very granular control.

---

### Post by slowtrain on 2012-04-16
Hi KevDog:

Thanks for your input!  You were right that the port bumping in ssh did not cause my problem.  The problem, as I mention in another thread, was due to the difficulty of de-banning oneself once denyhosts decides your other computer's ipaddress is a bad one.  I did solve the problem eventually.

By 'research' I mean statistics, not computer science.  I'm not sure I have the time to learn how iptables works, though am increasingly thinking it may be worth it.  Looking through iptables -L, it almost looks like the organization for which I work has hacked my machine--probably to maintain security and check if I've put banned material on the machine, but still disconcerting given this is supposed to be a personal research machine.

---

### Post by CharlesA on 2012-04-16
iptables is pretty easy to deal with. I use it without using ufw or gufw.

See here for a good intro:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

