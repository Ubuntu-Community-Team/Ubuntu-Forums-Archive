---
title: "Attack Response"
date: 2005-05-22
forum: Server Platforms
---

### Post by dmccarney on 2005-05-22
I currently run a SSH server on my new Ubuntu box, and as I'm sure many of you are aware, they tend to be attacked almost nightly by script kiddies. Now after some research and suggestions from others I've switched to only allowing Key Pair authentication and only allow my username to connect. This has made me feel rather confident that my box will not be compromised through the SSHD.

And now I come to my real point. Today I came home to find my log full of more dictionary attacks on the SSHD in an attempt to guess a username. Of course these failed but the ip was logged. A quick lookup with the Network Tools showed the ip belonging to an ISP in Europe. Browsing over to our friend Google I found the ISP website and contact information and sent off a quick mail about this harmfull activity on their IP range, more of an experiment than actually expecting concrete results. I also included a tail of my auth.log that shows the attacks from the specific IP. 

Now I'm curious, has anyone had any results with contacting the ISP's that host the nameless attackers that batter our boxes?

I'll post a synopsis of the response I get if any.

If anyone has similar experiance I'd be glad to here it  :)

---

### Post by jdong on 2005-05-22
My router keeps pretty comprehensive logs exportable via CSV. (pretty typical)

Once every month or so, I'll download this data, plot/sort it, and if there was a pretty substantial number or a fairly substantial attack against my computer, I will report it to abuse@.

I've gotten some "we found a guy with a worm, and we'll clean him up" responses, about 10% of the time.

---

### Post by LordHunter317 on 2005-05-22
Ignore them.   They're automated attacks by botnets, so it's not worth reporting unless they all were coming from the same block of IPs.

---

### Post by dmccarney on 2005-05-22
Thats pretty much what I figured but I thought I'd give it a shot and see if anyone else had any results. More of an experiment than anything else  ;-)

---

### Post by nmsa on 2005-12-07
[QUOTE=dmccarney]...

And now I come to my real point. Today I came home to find my log full of more dictionary attacks on the SSHD in an attempt to guess a username. Of course these failed but the ip was logged. A quick lookup with the Network Tools showed the ip belonging to an ISP in Europe. Browsing over to our friend Google I found the ISP website and contact information and sent off a quick mail about this harmfull activity on their IP range, more of an experiment than actually expecting concrete results. I also included a tail of my auth.log that shows the attacks from the specific IP. 

Now I'm curious, has anyone had any results with contacting the ISP's that host the nameless attackers that batter our boxes?

I'll post a synopsis of the response I get if any.

If anyone has similar experiance I'd be glad to here it  :)[/QUOTE]
I just discovered the same thing today. At first I was scared, then I changed my passwd's on the system with better ones.
my auth.log file reports ~ 4000 attampts from where ~ 2500 are unique
I did a whois on some IP's and find the name of the domains and reg. info based on this, coming from europe.
I will try and find if entries in the logs are repeated.

Now, what I am asking myself is what type of person will do such things. What is the scope? Clear is that if the systems get hacked, the data they will find might be worthless or simply personal.

---

### Post by A-star on 2005-12-07
The first thing I did was changing the port that ssh runs on, then I applied a strong password to my user account and disable root access in ssh.

I'm now looking into Key Pair authentication to make it even more secure.

---

### Post by jdong on 2005-12-07
Well, a few comments:

(1) Nobody's out to get you. 99.9999% of these probes are merely automated attacks done by a script, program, or worm with no user intervention. It tries common account names (john, bob, root, guest, admin, etc) with common passwords (password, youcantguessthis, pass, etc etc etc).

(2) Sometimes these probers are zombie computers already compromised by a hacker, and are the launchpad for more attacks at the overlord's command.

(3) Sometimes hackers actually own high-speed internet connections and launch these attacks via bots on their own networks.

(4) The motive is usually NOT to steal any information, but use YOUR computer as a zombie for more attacks.


Linux keeps itself fairly safe from these attacks in its default configuration:

(1) I hope your passwords aren't simple words found in wordlists, ESPECIALLY if you enabled SSH / remote logins. Change them now if  you are feeling kind of guilty!

(2) SSH only allows one password per account per connection per 5 seconds. Note how there is a 3-5 second delay if you type in your password incorrectly via SSH. This DRASTICALLY limits the rate at which hackers can try new passwords (brute forcing), which makes it nearly impossible for even a 4-letter/number password to be guessed within a reasonable time frame.


So in conclusion, nothing to worry about; just white noise. I'd be a lot **MORE** concerned about keeping an eye on **successful** logins, not failed logins, and make sure YOU are the one doing it. It's a lot more realistic a threat that when logging in via SSH on a public workstation, that there is a keylogger that captured your user/pass/IP.

---

### Post by jrib on 2005-12-07
I just checked my logs and had 902 attempts from 211.42.90.126.  Who wants to guess where it is coming from?  Yep, an elementary school in Seoul...  I think I'll try to contact them and let them know since I doubt they encourage fourth graders to try to crack ssh passwords.  Instead, their systems are probably just full of worms/trojans.

From: [http://whois.nic.or.kr/english/index.html](http://whois.nic.or.kr/english/index.html)
```

IPv4 Address       : 211.42.90.0-211.42.90.127
Network Name       : GOEUNES
Connect ISP Name   : PUBNETPLUS
Connect Date       : 20031215
Registration Date  : 20031215
Publishes          : Y

[ Organization Information ]
Organization ID    : ORG306642
Org Name           : Goeun Elementary School 
Address            : Hongje-dong, Seodaemun-gu, Seoul
Detail address     : 320
Zip Code           : 120-090

[ Technical Contact Information ]
Name               : Hyoeon Lee
Org Name           : Goeun Elementary School
Address            : Hongje-dong, Seodaemun-gu, Seoul
Detail address     : 320
Zip Code           : 120-090
Phone              : +82-2-396-2653
E-Mail             : sim20967@hanmail.net

```

Question: Is it a good idea to change the ssh port from 22 to something else?  Or will this pretty much do nothing?

---

### Post by M3ta7h3ad on 2005-12-07
It'll mean an automated script set to look for open port 22's will simply not be able to connect, and it wont find you running ssh without doing a portscan. Port scans are time consuming for a bruteforcing bot. They are typically working with the laws of probability.

If there are enough targets... I will have some success.

You may notice a decrease in attacks, you may not, either way it cant hurt

---

### Post by jdong on 2005-12-07
I wouldn't be overly concerned about this enough to be swapping SSH ports or anything of that nature....

---

### Post by LordHunter317 on 2005-12-07
[QUOTE=A-star]The first thing I did was changing the port that ssh runs on, [/quote]This, as stated many times before, adds no real security.  You're one quick portscan from being uncovered.  The rest of what you did is smart though.

[quote=M3ta7h3ad]Port scans are time consuming for a bruteforcing bot.[/quote]No, they're not.  They're a few seconds of upfront scanning.

---

### Post by jdong on 2005-12-07
Compared to the maximum rate of guessing passwords (1 guess per 3-5 seconds), a quick TCP Connect portscan with a timeout can be done in the time of less than 10 password guesses -- which is nothing on the scale of brute forcing.

---

### Post by cactus on 2005-12-07
I used to report stuff...but these days I just add a couple network blocks to my iptables rules for sshd traffic..
one rubber chicken sacrifice later....and no more ssh connections from spain!

---

### Post by M3ta7h3ad on 2005-12-08
[QUOTE=LordHunter317]This, as stated many times before, adds no real security.  You're one quick portscan from being uncovered.  The rest of what you did is smart though.

No, they're not.  They're a few seconds of upfront scanning.[/QUOTE]

Its time wasted when it could try another few targets in the time it takes (cumulative) to port scan every single IP address.

Its rare that a bot (I certainly dont see or hear of many) will portscan, and try to connect to every open port on a machine to check if its possibly running an sshd.

As I mentioned before the success of botnets relies either on pre-determined targets, or on probability, basically "if I try enough addresses, I will get some successes." Similar in concept is the "wireless security"... while both wep and WPA (wpa more so in my experience ;)) is easy to crack... they both provide deterrents to possible intruders.

I'd say change your ports if you can afford to... it wont do any harm, and it may help your security. The true test would be that if you change your ports... would you still get the logs full of connection attempts? If not, then clearly its worked for you.

---

### Post by LordHunter317 on 2005-12-08
[QUOTE=M3ta7h3ad]Its time wasted when it could try another few targets in the time it takes (cumulative) to port scan every single IP address.[/quote]No, it's not.  Given the amount of work you have to try to definitevely break the machine, even **without** login delays is insurmountable, and will never be done.  The amount of time to do a portscan first is just noise.

That ignores the fact that a bot can operate in parallel anyway, and a botnet operates in parallel by definition.  So no, it's not time wasted in the least, if it'll yield more targest to attack.

> Its rare that a bot (I certainly dont see or hear of many) will portscan,Yes, it is rare.  The point is if moving the SSH port becomes a common activity, portscanning bots will become common.  The threshold just hasn't been breeched yet.

> I'd say change your ports if you can afford to... it wont do any harm, and it may help your security.Yet it reduces functionality to a small degree  and in the event a portscanning bot appears, it doesn't help you.

> The true test would be that if you change your ports... would you still get the logs full of connection attempts?For the short-term, perhaps.  I'm not paid to provide short-term solutions though, unless they're followed by a proper long-term one.

---

### Post by towsonu2003 on 2005-12-08
[QUOTE=dmccarney]
Now I'm curious, has anyone had any results with contacting the ISP's that host the nameless attackers that batter our boxes?
If anyone has similar experiance I'd be glad to here it  :)[/QUOTE]
This was the original question? I would be glad if you could stop the bot discussion and help dmccarney if you can?  

as for the original question, I read one time (at slashdot I believe???) that ISPs tend not to pursue these unless they are threatened (by a big company that is under attack). have no idea where or when i read this though... I would say it was a comment but not an actual news item.

PS. I always like to read these security discussions, as long as they dont hijack the thread (thus would be nice to see a bot-usage thread under Security section)... sorry if I came on too harsh - no offense. eng language is not native, thus hard :)

thanks.

---

### Post by dbee on 2005-12-12
> 
I just checked my logs and had 902 attempts from 211.42.90.126. Who wants to guess where it is coming from? Yep, an elementary school in Seoul...

:D  ... well I never would have guessed it certainly :D :D 
... but now that I come to think of it, the attack had all the hallmarks of crime perpetrated by 8 year-olds from hongdae ;)

---

### Post by Oceola on 2005-12-12
I had about a hundred fifty name tries in under 15 minutes which came through the Ministry of Education in Taiwan. Also a dozen or so through my IP's tech support group. Wrote letters to both saying how it was fun watching them bang their heads on a wall but their children really do need a new hobby. 

Haven't had many lately.
So far logged: Austria, Dubai, Long Beach California, Singapore, Taiwan and Langley Virginia. They seem to be dropping off as my ISP gets a heads up, even if they are conspicuous as well.

I'm usng the networktools and it seems to do fairly well in tracking down the final party. Gives the address, phone and email along with different folks who you can contact (Hoary Repositories)
:rolleyes:

---

### Post by jsw060953 on 2006-03-06
Greetings,

One of my servers was successfully attacked and compromised.  Eventually, it became unaccessible via ping or ssh.  I am sure that it was a stupid password somebody stuck in there. Mea culpa.  I checked other servers and found the auth.logs full of dictionary attacks on my ssh port.  The attacks came from a Taiwanese ISP.

I have noticed that on my other machines, I was no longer able to get my Xwindows to start.  I use RealVNC to connect remotely, and I have a good password set.  I believe that xinit failed on a chmod instruction (illegal instruction).  I tried to use chmod, e.g. chmod a+x junk.  I got a message "illegal instruction".  This lead me to believe that the chmod command had been corrupted.  Is this likely a result of the attack, an installation problem, or a hardware problem?

It is clear to me that I have to wipe the disks on all my servers, rebuild them, and redeploy with good passwords, keypair ssh authentication, and different ports for VNC and ssh.  Any other suggestions?  Is Ubuntu sufficiently hardened to be deployed on a public network? 

Thanks,

John

---

### Post by diebels on 2006-03-07
[QUOTE=jsw060953]Greetings,

One of my servers was successfully attacked and compromised.  Eventually, it became unaccessible via ping or ssh.  I am sure that it was a stupid password somebody stuck in there. Mea culpa.  I checked other servers and found the auth.logs full of dictionary attacks on my ssh port.  The attacks came from a Taiwanese ISP.

I have noticed that on my other machines, I was no longer able to get my Xwindows to start.  I use RealVNC to connect remotely, and I have a good password set.  I believe that xinit failed on a chmod instruction (illegal instruction).  I tried to use chmod, e.g. chmod a+x junk.  I got a message "illegal instruction".  This lead me to believe that the chmod command had been corrupted.  Is this likely a result of the attack, an installation problem, or a hardware problem?

It is clear to me that I have to wipe the disks on all my servers, rebuild them, and redeploy with good passwords, keypair ssh authentication, and different ports for VNC and ssh.  Any other suggestions?  Is Ubuntu sufficiently hardened to be deployed on a public network? 

Thanks,

John[/QUOTE]
apt-get install harden

And check for debian/ubuntu specific configurations explained in /usr/share/doc/$PACKAGE/README.Debian.gz

Take some time to research if you need to secure the services you are running.

---

### Post by daacosta on 2006-03-07
what do you think bastille?

Is it better or as good as harden?

---

### Post by jdong on 2006-03-08
harden and bastille are both too general to be any good, from my experience. They're useful if you have untrusted users with local shell access, in which case you need to manually check permissions on everything.

As far as the "compromise" story, are you sure it wasn't hard drive corruption? SSH probes are very common, but usually none of them succeed.

---

### Post by kosmic on 2006-03-13
Try using Port Knocking, it should help improve your security :) - [http://www.portknocking.org]("http://www.portknocking.org")
 
 
Port knocking is a method of establishing a connection to a networked computer that has no open ports [[IMG]http://www.portknocking.org/images/webopaedia.png[/IMG]]("http://www.webopedia.com/TERM/p/ports.html") [[IMG]http://www.portknocking.org/images/foldoc.png[/IMG]]("http://wombat.doc.ic.ac.uk/foldoc/foldoc.cgi?query=ports") . Before a connection is established, ports are opened using a port knock sequence, which is a series of connection attempts to closed ports. A remote host generates and sends an authentic knock sequence in order to manipulate the server's firewall [[IMG]http://www.portknocking.org/images/webopaedia.png[/IMG]]("http://www.webopedia.com/TERM/f/firewall.html") [[IMG]http://www.portknocking.org/images/foldoc.png[/IMG]]("http://wombat.doc.ic.ac.uk/foldoc/foldoc.cgi?query=firewall") rules to open one or more specific ports. These manipulations are mediated by a port knock daemon, running on the server, which monitors the firewall log file for connection attempts which can be translated into authentic knock sequences. Once the desired ports are opened, the remote host can establish a connection and begin a session. Another knock sequence may used to trigger the closing of the port

---

### Post by Dml on 2006-03-14
[QUOTE=jdong]Compared to the maximum rate of guessing passwords (1 guess per 3-5 seconds), a quick TCP Connect portscan with a timeout can be done in the time of less than 10 password guesses -- which is nothing on the scale of brute forcing.[/QUOTE]
He will also have to scan computers that do not run ssh. If there's 100 computers that do not run SSH per one that run SSH, that's sure about 100 times different. BTW, in the firewall logs i see port scans very rarely, much rarer than single port hits on 22.

---

