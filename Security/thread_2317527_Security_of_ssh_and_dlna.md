---
title: "Security of ssh and dlna"
date: 2016-03-17
forum: Security
---

### Post by DGINSD on 2016-03-17
I recently read a post about the dangers of running ssh on a non-standard port, and why it's a bad idea, something I've done since I started using ssh. I have both my boxes running on ports above 4000 and both forwarded to through a virtual server on a nat router, both are also using 4096 bit, encrypted, rsa private key authentication only. Here's a link to the article: [https://www.adayinthelifeof.nl/2012/03/12/why-putting-ssh-on-another-port-than-22-is-bad-idea/](https://www.adayinthelifeof.nl/2012/03/12/why-putting-ssh-on-another-port-than-22-is-bad-idea/)
The jist of this article is it's a bad idea to do this because ssh is started by root and opens a low port that only root is allowed to open, by using a higher random port it would be easy for a skilled cracker to write a script to fake ssh into giving the cracker root access (this stuff is a lot above my head),  because of the high port number that any non root process is capable of opening. There is a disclaimer before the article that some of the writers points are no longer valid. His basic premise remains though. One premise is that the reason we move away from 22 is to deny those searching for the well known port to limit probing attacks. His claim is these attacks should be of no concern if other proper security precautions are taken, mainly elimination of password login in favor of private key authentication. Is this true? And is there any real danger in using higher non-standard ports?

With regards to dlna, I recently set up minidlna on an old laptop for my movie collection, it's set up to not be accessible outside my local network (I think) what are the dangers posed by this service and are there and good ways to secure it to limit those risks? I'm new to running any type of server so I'm sure any ideas will be helpful.

---

### Post by bab1 on 2016-03-18
> **DGINSD said:**
> I recently read a post about the dangers of running ssh on a non-standard port, and why it's a bad idea, something I've done since I started using ssh. I have both my boxes running on ports above 4000 and both forwarded to through a virtual server on a nat router, both are also using 4096 bit, encrypted, rsa private key authentication only. Here's a link to the article: [https://www.adayinthelifeof.nl/2012/03/12/why-putting-ssh-on-another-port-than-22-is-bad-idea/](https://www.adayinthelifeof.nl/2012/03/12/why-putting-ssh-on-another-port-than-22-is-bad-idea/)

The jist of this article is it's a bad idea to do this because ssh is started by root and opens a low port that only root is allowed to open, by using a higher random port it would be easy for a skilled cracker to write a script to fake ssh into giving the cracker root access (this stuff is a lot above my head),  because of the high port number that any non root process is capable of opening.

Thia is not how TCP ports function.  First thing to note is that the first 1024 TCP port can only be *_**configured**_* by the root user.  Anyone can use them.  For example Apache is started by root, but drops to running under a *nologin* system user system user.  In Ubuntu this is www-data.  Apache2 runs on the well known (low number) port 80 and anybody can access the server (listener).

It's worth noting that TCP ports are not the same as a water faucet or a Ethernet port on a switch or router.  The port is nothing more than a header configuration in the sequence section of the data packet.  The ability to restrict the ***_configuration_*** of these low numbered TCP ports to the root user is a sanity check so that there is some constancy in TCP port assignment between the hosts on networks.  The user can be reasonably confident what the TCP port port number associated with the HTTP server, DNS server, DHCP server or any other low numbered TCP port listener is.  The TCP port can't be configured or changed by a regular user or system user.  Only the root user (a system administrator)  The OS does not concern itself with which TCP ports  above 1024 are used in ad hoc configuration by apps or normal users.     
> 
There is a disclaimer before the article that some of the writers points are no longer valid. His basic premise remains though. One premise is that the reason we move away from 22 is to deny those searching for the well known port to limit probing attacks. His claim is these attacks should be of no concern if other proper security precautions are taken, mainly elimination of password login in favor of private key authentication. Is this true? And is there any real danger in using higher non-standard ports?

The author's points don't make any sense when it comes to why or why not one should configure and use low numbered TCP ports.  The advantage to using a non-standard TCP port is that the amount of script probing can be substantially reduced.  This reduces CPU cycles and log file growth.  The sys admin has tools to limit the amount of probing on a specific port these days, so the need to move to a non-standard port is not as big a concern as it used to be.  My feeling is that it doesn't matter which port you want to use as far as it is your network.

For more information on TCP ports you can start reading up on it [**here**]("https://en.wikipedia.org/wiki/Port_%28computer_networking%29").

---

### Post by HermanAB on 2016-03-18
If you want the script kiddies to go away, put a rate limit rule in iptables:
[http://www.aeronetworks.ca/2013/05/ssh-brute-force-attacks.html](http://www.aeronetworks.ca/2013/05/ssh-brute-force-attacks.html)

With that rule, you get three chances to log in, after which only one attempt per 20 seconds is allowed through.  So the scoundrels realize that they have been had, give up and move on.

---

### Post by DGINSD on 2016-03-18
bab1 thank you for the explanation and link, I thought that article was off, but didn't know enough to know why. I'll do some reading on the link to educate and further put my mind at ease.

HermanAB I actual am using rate limiting, through I'm doing it through GUFW rather than direct configuration of IPtables, I'm also using the built in connection limit of ssh (set very low as it's typically just  me that's connecting). Is this typically enough, or do I need to task the time and learn to configure IP tables manually?

---

### Post by HermanAB on 2016-03-19
First of all, you should use looooong passwords, of 12 characters or more, then slow things down and if you are totally paranoid, use key logins only and disable password logins.  

Running sshd on a non-standard port will make all the children go away.  It may not make the professional crackers go away though, but I still have to encounter a real pro, despite decades of running Linux servers - they are few and far between it seems.

---

