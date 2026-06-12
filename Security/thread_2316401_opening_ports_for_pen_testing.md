---
title: "opening ports for pen testing"
date: 2016-03-07
forum: Security
---

### Post by matt18 on 2016-03-07
ok here is an odd question. i need to open up ports for http, DNS and SMTP. I have a PFSense firewall with backbox on vmnet5 and then ubuntu 14.04 on vmnet 6. I am using nmap to scan accross the FW with basic rulesets, advanced rulesets, and stateful rulesets. But i need to have the above ports open. In order to do that, does that mean i actually need the service to running on each port? if so, what is the easiest way to do that with out setting up an actual webserver, dns server and mail server. I just want the ports to be available to scan with nmap:)

thanks

---

### Post by SeijiSensei on 2016-03-08
Yes, you need listeners on the ports. Take a look at **netcat** with "man netcat".  You can have it listen on a port with 
```
$ nc -l 12345
```

To listen on privileged ports below 1024 like you want, you need to run it with root privileges via sudo
```
$ sudo nc -l 80
```

You can use the -u option to have it use UDP instead of TCP.  DNS servers listen on 53/udp.  Usually DNS uses TCP only for domain transfers between servers.

---

### Post by matt18 on 2016-03-08
ok, cool. thats what i thought. I was hoping there was a way to not have to install services to ports in order to scan. i knew it didnt make sense but i was hoping it was possible haha. It was a LOOONG shot. 

Ok, so with that in mind, i am trying to find a small distro (1gb) that i can spawn 3 times. One as http, DNS and smtp. 

I tried DSL linux but the mouse does not work in vmplayer at all. 

Thnaks for the help

---

### Post by SeijiSensei on 2016-03-09
> **matt18 said:**
> Ok, so with that in mind, i am trying to find a small distro (1gb) that i can spawn 3 times. One as http, DNS and smtp.
Why?  The same machine can listen on all three ports simultaneously.

---

### Post by ecaep on 2016-03-10
Matt18, Could please explain what your overall goal is for needing to open of these ports and how the traffic is going to be flowing into/out of the network. 

Opening these port in a incorrect way can cause a serious security problems with in a network.

Just wanting to make sure what you are doing isn't going to let bad things happen.

---

### Post by SeijiSensei on 2016-03-13
If he uses netcat as a listener, few if any "bad things" could happen.  All that does is send the traffic that arrives on the port to standard output.

Just opening a port in the firewall rules doesn't create a vulnerability.  There needs to be a program listening on the port that might be compromised.  Even if he chose to run Postfix, BIND9 and Apache to handle ports 25, 53 and 80, they are pretty bullet-proof after all these years.  There are the occasional BIND9 exploits, but they are pretty rare.  I've run Internet-facing servers with all three of those applications for years and not been compromised.

---

### Post by ecaep on 2016-03-14
> **ecaep said:**
> Matt18, Could please explain what your overall goal is for needing to open of these ports and how the traffic is going to be flowing into/out of the network. 

Opening these port in a incorrect way can cause a serious security problems with in a network.

Just wanting to make sure what you are doing isn't going to let bad things happen.


Sorry "Opening these port in a incorrect way can cause a serious security problems with in a network." is just worded wrong, and  should have said something more like this.

"Opening these ports and  setting up these services in a incorrect way can cause a serious security issues with in a network."

---

### Post by ecaep on 2016-03-14
SeijiSensei, I agree with you that there is no immediate security problems using netcat, but it doesn't do the user much good to use it for a pen test as there is no actual service to test. This goes into not knowing enough of the OP's situation to determine the best action.


I must disagree with just opening ports. This is bad practice, and  no one should ever open ports unless they have a valid reason such as setting up internet facing services or if a vendor needs access to their devices in the DMZ. In this case just because a pen tester might have asked asked you to do it does not make it a good reason.


I also must disagree with Postfix, BIND9, and Apache being mostly bulletproof given that if setup wrong can cause security problems, and thinking that they aren't as open to compromise is just a poor way to think of any apps/services. BIND9  alone had 3 high rated vulnerabilities this month that could be exploited remotely. As for the other two there hasn't been any serious vulnerability released, but I like to think it's just a matter of time till they have another security vulnerability.


So with that being said, without more information about what the OP goals are and more context on "pen test" like is this a home lab to learn pen testing or their company network. I will find it hard to give the user any sound advice.

---

### Post by SeijiSensei on 2016-03-14
The three [BIND9 vulnerabilities]("http://www.cvedetails.com/vulnerability-list/vendor_id-64/product_id-144/year-2016/opdos-1/ISC-Bind.html") you mention only result in a denial-of-service; none of them compromise the integrity of the system.  Moreover all three of them require some unusual configurations like running in debug mode or having certain atypical services (nxdomain-redirect) enabled.  In addition, I use the chroot features of BIND9 to sandbox the service.  This is a pretty common and easy-to-implement option on RedHat-flavored distributions.  I don't use Ubuntu on servers so I don't know how easy it is to implement it there.

Apache has been in use for over two decades now, and it is considerably less complex than BIND9, so I don't think my trust is misplaced.  I haven't used Postfix that long, since I'm still largely running sendmail on my mail servers.  I haven't ever had a sendmail compromise either.

Any service is vulnerable if not configured properly, though some like Apache offer few options to exploit.  Web services that run on top of Apache are usually where compromises occur.  

I think it's important to take a balanced approach to security.  My comments are based on two decades of running Linux servers.  If exploits were as easy to implement against fundamental software applications like these as you suggest, I would have seen them by now.  In fact the only time I was ever compromised came from running a vulnerable version of Apache 1.2 or 1.3 that I failed to upgrade.  Even then, all the hacker could do was turn my server into an IRC relay by writing something into /tmp as the Apache user.  They never gained root privileges.  And, of course, in that case it was my fault.  As you can see from the version number that was many years ago now.

---

### Post by ecaep on 2016-03-14
SeijiSensei, I feel like my last post came off kinda brash. I'm still working on transitioning from military to civilian life and some times I don't articulate my words very well and it can be off putting.

I do feel we are are on more on the same page you said what I was trying to a lot better.



There is no problem with the user setting up these services I just want to make sure they are not going to use some weird guide off the internet that could have them setup their servers incorrectly is all.

I am just wanting to know if this is a home pen testing lab the OP is asking about. If this is the case then I am all for assisting the OP setting all of the services and going crazy testing (this is what seems to be the case)
, but just on the off chance this a is a corporate/SOHO network the OP should not doing anything until getting guidance and authorization from the higher ups in their business especially in regards to pen test.

---

### Post by QIII on 2016-03-14
This thread started out looking at the "inside" parts of getting pen testing set up.  I saw this several days ago and allowed it to go on -- keeping an eye on it.

However, I'm concerned that in short order it is going to turn into a discussion of the actual external penetration testing.  We don't allow such discussions of the Ubuntu Forums.  We know quite good and well that most users asking such questions are well-intentioned and we have no reason to suspect any wrong-doing.  But even in helping those with the most innocent of motives, detailed instructions are left behind.  These may just as easily be used by those with nefarious intent.  We do not want the UF to become a resource for them.

Users like SeijiSensei have a great reserve of knowledge about security matters and I'm sure he would be quite happy to help you with any security settings/adjustments to keep your system safe (as can be) from intruders -- or even make the system vulnerable for testing to be discussed elsewhere -- but I don't want others to accidentally stumble in to describing the actual penetration testing methods from the outside.

So for everyone who posts from here on out:  Please keep this to what goes on *inside* a potentially exploitable machine.  If that means setting it up for testing, fine.  That is a security discussion about what renders your machine vulnerable.  But please don't discuss actual external pen testing attempts/tools to exploit the vulnerabilities created.  I think you can trust users like SeijiSensei to give you reasonable advice with regard to how certain conditions can make you vulnerable.

To that end, I'm moving this to Security.

---

### Post by HermanAB on 2016-03-15
Well, if you have to ask, then you are probably not the right person to do the penetration test, but how else are you going to learn?

I suggest setting up two or three machines on a standalone network switch and learn there, not on a production system.

---

