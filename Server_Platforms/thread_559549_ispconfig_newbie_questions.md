---
title: "ispconfig newbie questions"
date: 2007-09-25
forum: Server Platforms
---

### Post by dysolve on 2007-09-25
hello all,
 I have a few little question about ispconfig.

1. Is there a way of accesing a site locally
   e.g site is [www.mydomian.com](www.mydomian.com) and server addy is 192.168.0.3, I would like to access that site from another machine on my network, I thought it would be something like 192.168.0.3/~mydomain.com/ but that does not work.

2. I currently have a dynamic ip and I have a dyndns service. how do I setup ispconfig to receive requests from my/any dyndns addy and send it to the right site on my server?

3. can you setup an e-mail server with a free dyndns addy?

4. can you access ftp's locally? and if so what would be a ftp address?

once i get the server and connection fully tested and am happy with it and how I run it I will upgrade my internet connection to have static ip's..

again thanks in advance
David.

---

### Post by twistedtwig on 2007-09-25
to access a site "locally" (presuming you mean within your local network), you just need to type in the IP address (or dns name if you have BIND or something of the like installed); into a browser.

This assumes that the firewall is not blocking connections to it from the local network.

To access it in the wilderness of the internet you would put the PUBLIC IP (if you have it, i.e. not behind a NAT router)

not sure what ispconfig is in all honesty.

for net users to see your site you have to have (as stated by ur self) a domain name.  You also need to have port 80 open to the internet.

to have a mail server you need port 25 open, dont know about the rest of that never set one up.

you can use virtualhosts in apache if you want to host more than one website (or subdomains).

Static IP's??? guessing you mean you want your server to have a static IP. this would need to be bought from your ISP

---

### Post by Aberrix on 2007-09-25
> **dysolve said:**
> 
1. Is there a way of accesing a site locally
   e.g site is [www.mydomian.com](www.mydomian.com) and server addy is 192.168.0.3, I would like to access that site from another machine on my network, I thought it would be something like 192.168.0.3/~mydomain.com/ but that does not work.


you would need to add an entry into the hosts file of the 'other' pc;
192.168.0.3      [www.mydomain.com](www.mydomain.com)      mydomain.com

> **dysolve said:**
> 
2. I currently have a dynamic ip and I have a dyndns service. how do I setup ispconfig to receive requests from my/any dyndns addy and send it to the right site on my server?

I am not quite sure you can do that... but if you could it'd be in the DNS Manager panel.

> **dysolve said:**
> 
3. can you setup an e-mail server with a free dyndns addy?

again, not quite sure you can do this with ispconfig...

with ispconfig, it's really more based upon the idea you're going to run your own DNS and your own e-mail vs. using a dyndns address.

> **dysolve said:**
> 
4. can you access ftp's locally? and if so what would be a ftp address?

yes you can access ftp locally, just use an ftp client and ftp to the servers ip. but you need to make sure your user has proper access.

for more comprehensive questions regarding ispconfig, it'd be a good idea to check out their forums; [http://www.howtoforge.com/forums/forumdisplay.php?f=14](http://www.howtoforge.com/forums/forumdisplay.php?f=14)

good luck!
ispconfig user for over a year now,
Aberrix

---

### Post by dysolve on 2007-09-26
the dyndns service is working great.. directs to the site I want .. but ftp access is not working.. and I am unable to connect to the www server locally.. it just keeps bring up the ispconfig default screen.. time to do more reading I suppose..

---

### Post by dysolve on 2007-10-10
ok I have ftp working now internally but its very slow.. I change ftp clients on the remote machine and now its tells me 

"A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond."

any ideas why access is so slow locally and that would explain the connection timing out

I have another issue now, I can not connect to my mail server.. I have turned off all firewalls and routed all traffic on my wan to the server..

thanks
David.

---

### Post by dysolve on 2007-10-11
it seems i have now got mail working remotly but if I try and connect locally to server i get the following error

"Unable to connect to POP server 192.168.0.3.
Error sending password: -ERR chdir Maildir failed"

any ideas?

---

