---
title: "ShieldsUp!"
date: 2008-05-30
forum: The Cafe
---

### Post by Bruce M. on 2008-05-30
Hi Folks,

I just did a port test at [ShieldsUP!]("https://www.grc.com/x/ne.dll?bh0bkyd2") clicked on [Proceed] and then selected [All Service Ports].

The result for TruStealth Analysis = **[COLOR="Red"]Failed[/COLOR]**

> Solicited TCP Packets: RECEIVED (FAILED) — As detailed in the port report below, one or more of your system's ports actively responded to our deliberate attempts to establish a connection. It is generally possible to increase your system's security by hiding it from the probes of potentially hostile hackers. Please see the details presented by the specific port links below, as well as the various resources on this site, and in our extremely helpful and active user community.

Unsolicited Packets: PASSED — No Internet packets of any sort were received from your system as a side-effect of our attempts to elicit some response from any of the ports listed above. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system remained wisely silent. (Except for the fact that not all of its ports are completely stealthed as shown below.)

Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.

The text Summery reads:
```
This textual summary may be printed, or marked and copied
for subsequent pasting into any other application:

----------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2008-05-31 at 02:16:41

Results from scan of ports: 0-1055

    0 Ports Open
 1055 Ports Closed
    1 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

The port found to be STEALTH was: 25

Other than what is listed above, all ports are CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

```

Now I'm curious. With everything "closed" isn't that a good thing?

I read once, can't remember where, that if "everything" was "stealth" attackers would become more interested. But I know precious little about this, except I like the fact that "iptables" has at least closed them.

Or should I try to get them all on "stealth" mode? My mind tells me if everything is on "stealth" mode then no one can see me and that that would be better. 

Is there anything I should be worried about?

Have a nice day.
Bruce

---

### Post by Bruce M. on 2008-05-30
Also went here [Nmap Online]("http://nmap-online.com/")

And got these results (red edited by me)

> Nmap Options: -p1-5000 -T4 -sS [COLOR="Red"]000.000.000.00[/COLOR]

Starting Nmap 4.11 ( [http://www.insecure.org/nmap](http://www.insecure.org/nmap) ) at 2008-05-31 03:36 Central Europe Daylight Time
Interesting ports on [COLOR="Red"]000-000-000-00.net.somewhere.com.ar (000.000.000.00)[/COLOR]:
Not shown: 4996 closed ports
PORT STATE SERVICE
25/tcp filtered smtp
179/tcp filtered bgp
1720/tcp filtered H.323/Q.931
2628/tcp open dict

Nmap finished: 1 IP address (1 host up) scanned in 102.687 seconds

and have no idea what those results mean.

Have a good one.
Bruce

---

### Post by Tyche on 2008-05-31
With ShieldsUp, if it ain't stealth it's a fail.  Stealth means that not only couldn't they tell the state of your ports, they couldn't even tell that a computer was at that IP address.

I used to run it periodically, back when I HAD to run windows at work.  I put a firewall between me and the outside world that stealthed everything, but that didn't stop me checking.

Now, I'm on Ubuntu Linux and hadn't even thought of it untill you raised the question.  So I checked.  Still stealthed.  They couldn't find my computer.

:):):):):)

---

### Post by phaed on 2008-05-31
If you install Firestarter and enable ICMP filtering (in preferences),  you'll get a pass score.

---

### Post by Kevbert on 2008-05-31
Bruce M.  The test failed as anyone who pings your network address will get a response.  It should be possible to turn this off so that you remain anonymous to the outside world.  If you're using a wireless router it will be marked as something like 'Respond to PING on Internet WAN port' (my Netgear router) which can be disabled.

---

### Post by Lord Xeb on 2008-05-31
GRC Port Authority Report created on UTC: 2008-05-31 at 06:19:04

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.




Also, have ports closed is bad. I could go in and hack and open any closed port and gain access to your system. Stealth is what you want. When in steal, you exist, but you don't exist at the same time

---

### Post by mcduck on 2008-05-31
It's absolutely OK to only have ports only closed instead of stealthing them. As long as there is no program running that would respond to incoming connections on that port there is no way anybody could use it to access your computer.

The only difference stealthing makes is that possible attackers may have a little harder time figuring out if any machine exists on your address. But if they already know that there is a machine, stealthing will quite likely only make them more interested in gaining access.

For those who are getting the "stealth" results, using any router with NAT will change your results, and many routers also have different firewall functions that may also change the results you are getting. If you really wish to test your computer with these tools, you should do it when connected directly to internet.

---

### Post by Bruce M. on 2008-05-31
> **Lord Xeb said:**
> Also, have ports closed is bad. I could go in and hack and open any closed port and gain access to your system. Stealth is what you want. When in steal, you exist, but you don't exist at the same time

You can open a closed port on my machine???

> **mcduck said:**
> It's absolutely OK to only have ports only closed instead of stealthing them. As long as there is no program running that would respond to incoming connections on that port there is no way anybody could use it to access your computer.

Oh oh ... **Stealth vs Closed**.  Don't want and didn't mean to get a "**vs**" thing going here.

The only programs here that have Internet access are: Firefox, Thunderbird and Conky. I have nothing else active.

*{thinking out loud: I wonder if Conky has a "what port is open" function? Must take a look see!}*

> **mcduck said:**
> The only difference stealthing makes is that possible attackers may have a little harder time figuring out if any machine exists on your address. But if they already know that there is a machine, stealthing will quite likely only make them more interested in gaining access.

That's what I was referring to earlier.

I do notice that Conky reports my IP address differently at times.
I would guess that's good news.

Thanks to everyone who has responded.
Learning a few things here.

Have a good one, I'm still watching this.
Bruce

---

### Post by p_quarles on 2008-05-31
> **Bruce M. said:**
> You can open a closed port on my machine???
Under normal circumstances and with a decently secure setup, no.

The problem with closed ports rather than stealthed ports is that the former confirm the existence of a computer on a particular network address. In other words, a stealthed port doesn't tell an attacker that there's anything to attack. 

If an attacker were to find a bunch of closed ports, he would have confirmed the existence of a machine at that address. Attacking that computer would be specific to the situation, and would most likely be a lot more complicated than just opening a port (which would require the machine to be already compromised in the first place).

---

### Post by anaconda on 2008-05-31
Test passed.. All ports are stealth!

But the problem is that it isnt my firewall.. I am berhind my ISP:s restrictive firewall, and so I cant open ANY ports

---

### Post by eragon100 on 2008-05-31
Determine the status of your
system's first 1056 ports

This Internet service ports "grid scan" determines the status &#8212;  Open,  Closed, or  Stealth &#8212; of your system's first 1056 TCP ports.
	32 ports, represented by each horizontal row, are probed as a group. The results are posted as the next set of ports are probed.
	During off-peak hours the entire scan requires just over one minute.
	For guaranteed accuracy, the scanning time will increase during peak usage when many people are sharing our scanning bandwidth.
	A scan of a stealthed system is up to four times slower since many more probes must be sent to guarantee against Internet packet loss.
	The test may be abandoned at any time if you do not wish to wait for the scan to finish.
	You may hover your mouse cursor over any grid cell to determine which port it represents, or click on the cell to jump to the corresponding Port Authority database page to learn about the port's specific role, history, and security consequences. (Depress SHIFT when clicking to open new window and allow unfinished test to continue.)

Your computer at IP:

 nice.place.to.live (:lolflag:)

Is being carefully examined:


*lots of crab*

	Open    		Closed    		Stealth
Total elapsed testing time: 68.065 seconds	

**Your system has achieved a perfect "TruStealth" rating. Not a single packet &#8212; solicited or otherwise &#8212; was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.**

---

### Post by happy-and-lost on 2008-05-31
My light Debian setup passed TruStealth. I haven't even manually added any security beyond the base netinstall system (w/o desktop).

---

### Post by meborc on 2008-05-31
yep, a clean hardy install... and OF COURSE pass on all tests... all ports stealth... sweet

---

### Post by Bruce M. on 2008-05-31
> **phaed said:**
> If you install Firestarter and enable ICMP filtering (in preferences),  you'll get a pass score.

Just for fun and to help learn I installed Firestarter and did what you said, left the other options under ICMP alone and:

```
GRC Port Authority Report created on UTC: 2008-05-31 at 17:54:21

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

```

So now to the serious question:

Is this better or worse then "Closed"

Closed: people can see me, but can't get in.
Stealthed: people can see me but Firestarter still shows stuff going on under [Events]

ie:
May 31 14:58:36 Unknown eth0 [COLOR="DarkRed"]xxx.xxx.xxx.xxx xxx.xxx.xxx.xx[/COLOR] 52 0x00 UDP Samba (SMB)
or
May 31 15:02:25 Unknown eth0 [COLOR="DarkRed"]xxx.xxx.xx.xxx xxx.xxx.xxx.xx[/COLOR] 52 0x00 TCO Microsoft-ds

What gives?
Thanks
Bruce

---

### Post by smartboyathome on 2008-05-31
I am on arch behind my comcast router PLUS my linksys one, and it says I pass, all ports stealth. I wonder which oneis protecting me. ;)

---

### Post by Kernel Sanders on 2008-05-31
Tested with Windows Vista Ultimate 32 bit, with the default setup with no separate anti-virus or firewall installed:

> 
Your system has achieved a perfect "TruStealth" rating. Not a single packet — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.


I'm getting more and more impressed with Vista's security by the day. We should also remember that it performed amazingly well in the recent hacker challenge, lasting until user interaction was required to exploit a flash vulnerability.

Well done Microsoft!

---

### Post by Kernel Sanders on 2008-05-31
> **Bruce M. said:**
> 
So now to the serious question:

Is this better or worse then "Closed"

Closed: people can see me, but can't get in.
Stealthed: people can see me

That's where you're wrong.

Open: Nightmare
Closed: Your computer is clearly visable, responding to requests sent to it, albeit with a virtual "no".
Stealth: Your computer ignores incoming unsolicited requests, so you are invisible. They literally have no idea you are there, whether there is a machine there to hack or not.

Stealth is obviously the best, because they are unlikely to waste time trying to hack what may not even be there. Open is the worst, and closed is a kind of middle ground, where you are secure, but you are clearly visible, so if they wanted to spend time trying to hack you, they can.

---

### Post by Ripfox on 2008-05-31
screen

---

### Post by popch on 2008-05-31
> **Kernel Sanders said:**
> and closed is a kind of middle ground, where you are secure, but you are clearly visible, so if they wanted to spend time trying to hack you, they can.

To my mindset, 'closed' would be best because it would waste the time of would-be intruders. If they spent that time themselves, that is.

---

### Post by p_quarles on 2008-05-31
> **popch said:**
> To my mindset, 'closed' would be best because it would waste the time of would-be intruders. If they spent that time themselves, that is.
Stealth is probably best for the typical home computer (insofar as such a thing exists), but closed is not inherently less secure. Stealthed ports can still be attacked, and having some ports stealthed won't benefit you much if you need to have others responding to outside requests.

---

### Post by scorp123 on 2008-05-31
> **popch said:**
> To my mindset, 'closed' would be best because it would waste the time of would-be intruders. Only on that particular port that reported being 'closed', yes. But they now know that you are there.

What puzzles me is that nobody has so far mentioned another possible result that you might get for port scans:  **"filtered."**

So to pickup Sander's list of results and their meanings again:

[LIST]
[*]"open": The TCP or UDP port in question is wide open, and other users can connect to it. This is necessary e.g. for servers where the relevant ports obviously have to be open (e.g. port 80 for web servers) but as a home user you might not want any open ports at all!
[*]"closed": The TCP or UDP port in question is closed, i.e. there is no process or service that is listening to it. Potential intruders cannot connect to this specific port in question (as I said: there is nothing that would listen to incoming connections) but they clearly know that you are there and they might try something else, e.g. a different port or scan for other potential weaknesses ...
[*]"filtered": The TCP or UDP port in question is OPEN and there is a service that is listening to incoming requests. BUT: There is a firewall in place which filters out unwanted IP ranges from connecting to the system. So far so good, but still no 100% security: A really good hacker might spoof his IP address so it looks like the packets are originating from a source that is allowed to connect. Or: A hacker might first go after a target that is allowed to connect and then attack you from there ... And of course "filtered" clearly proves to any potential intruder that you do exist, that you are connected, that there are processes listening, and that you are using a firewall. Still: This should keep out about 99% of the wannabe hackers and script-kiddies but it won't stop the 1% who truly deserve to be called "hacker". It will only delay them ...
[*]"stealth": The TCP or UDP ports in question are a "black hole". Whatever packet gets here is never ever seen again. No replies, no return codes, no scan results. A potential intruder doesn't really know if you exist or not and if you really are online or not, he might as well try a port scan on Santa Clause, the Yeti or E.T.  .... For a home user this is a very desirable result as it will keep everyone away. BUT: Of course this is only useful if really *ALL* ports are "stealthed"! It doesn't help you at all if e.g. your ICMP ports for "ping replies" are "stealthed" but your SSH on TCP port 22 is happy to reply and is shown as "open"! ;)
[/LIST]

---

### Post by nick09 on 2008-05-31
All ports are stealth, I used firestarter to activate the iptable firewall.

---

### Post by Bruce M. on 2008-05-31
> **popch said:**
> To my mindset, 'closed' would be best because it would waste the time of would-be intruders. If they spent that time themselves, that is.

> **p_quarles said:**
> Stealth is probably best for the typical home computer (insofar as such a thing exists), but closed is not inherently less secure. Stealthed ports can still be attacked, and having some ports stealthed won't benefit you much if you need to have others responding to outside requests.

Well, I have to say there is only one way to settle it.

Heads it's "Closed"
Tails it's "Stealth"

LaRoza; call it!  { FLIP }

heeeeelllllllooooo LaRoza!

Bruce

---

### Post by popch on 2008-05-31
> **Bruce M. said:**
> Heads it's "Closed"
Tails it's "Stealth"e

And what will you do if it stands on edge?

---

### Post by Bruce M. on 2008-05-31
> **p_quarles said:**
> Stealth is probably best for the typical home computer (insofar as such a thing exists)

Sure they do, look at my sig ... no router, no nothing.

The box, the monitor, printer, keyboard, mouse a set of speakers, oh yea and the cable modem.  :guitar:

Have a good one.
Bruce

---

### Post by Bruce M. on 2008-05-31
> **popch said:**
> And what will you do if it stands on edge?

A 1 in a 1,000,000 chance and you have to ask, creating yet more doubts.

:confused: {gee, but what if...} :confused:

---

### Post by popch on 2008-05-31
> **Bruce M. said:**
> A 1 in a 1,000,000 chance and you have to ask, creating yet more doubts.

Well, unfortunately I can not change the design of coins of your country. Otherwise, I would make them as thick as they are wide.

OTOH, in your situation I most likely would settle for 'stealth' as that might deter automated trespassers from trying more drastic measures. In the end, it might not matter.

---

### Post by Old_Grey_Wolf on 2008-05-31
I think that a Security Forum should be added to the Ubuntu Forums. It should have a sticky that explains Linux natural security policies. Then threads like this one could start there. 

When I first started using Linux, I felt uncomfortable without my anti-virus, anti-spyware, anti-this and anti-that. :lolflag:

Firewalls, NAT Routers, and the like are still good security measures even for Linux. ;-)

Edit: Forgot to mention that WPA, WPA2, etc. for wireless networks is must have.

---

### Post by Bruce M. on 2008-05-31
> **popch said:**
> Well, unfortunately I can not change the design of coins of your country. Otherwise, I would make them as thick as they are wide.

WHAT!!!!! You'd cheat?  No, not my old buddy :popcorn:ch! You must be someone else that hacked his account. :)

> **popch said:**
> OTOH, in your situation I most likely would settle for 'stealth' as that might deter automated trespassers from trying more drastic measures. In the end, it might not matter.

I let FireStarter run for a while on "Stealth" mode and the Event log kept growing ...
Both "black" and "red" {serious} entries.

Turned off "Stealth" mode and the same traffic is coming at me.

A LOT on Port 32317, all black, from unknown and now a new port: 51635

I need a time machine to go into the future, get a computer and Ubuntu 32.10.  That would fix it. :lolflag:

---

### Post by klange on 2008-05-31
My IP reports mostly closed, with a few open (SSH, SMTP, PrivMail, HTTP, FTP, HTTPS, IMAP, etc.), and for good reason. Most all of my traffic is routed into my server, and it wouldn't be good for it to appear to not be there. Also saw some interesting stealthed ports. The entire NETBIOS block is stealthed, which I guess is normal? None of the traffic on those ports would ever get near a Windows machine anyway.

Does this thing do any UDP port scans?

---

### Post by Bruce M. on 2008-05-31
> **Old_Gray_Wolf said:**
> I think that a Security Forum should be added to the Ubuntu Forums. It should have a sticky that explains Linux natural security policies. Then threads like this one could start there. 

When I first started using Linux, I felt uncomfortable without my anti-virus, anti-spyware, anti-this and anti-that. :lolflag:

Firewalls, NAT Routers, and the like are still good security measures even for Linux. ;-)

Edit: Forgot to mention that WPA, WPA2, etc. for wireless networks is must have.

I've never felt insecure or uncomfortable with Linux and lacking the "anti-" programs. It just that I found this site tucked away in my bookmarks, though what the heck and ... oops!

So like in my first post:
> **Bruce M. said:**
> Now I'm curious. With everything "closed" isn't that a good thing?

Is there anything I should be worried about?

I'd probably not be wrong in saying there is no such thing as a truly secure system or OS. But then again I don't think the "Pro-Hackers" are going to be interested in a home computer, it's just those "weekend warriors" they are teaching.  :)

Of course I could be way out to lunch on that too. ](*,)

---

### Post by p_quarles on 2008-05-31
> **Old_Gray_Wolf said:**
> I think that a Security Forum should be added to the Ubuntu Forums. It should have a sticky that explains Linux natural security policies. Then threads like this one could start there. 
There is such a forum, and there is such a sticky. :)

This thread is fine here, as far as I'm concerned, because it's more of a discussion than a support question.

---

### Post by Bruce M. on 2008-05-31
> **p_quarles said:**
> There is such a forum, and there is such a sticky. :)

I didn't know that. Not ever feeling I had a need, I never went looking.
Running the Desktop version, not a Server.

> **p_quarles said:**
> This thread is fine here, as far as I'm concerned, because it's more of a discussion than a support question.

Yup, you're 100% correct, I never meant it as a "security" issue, just a discussion to find out what's what and learn a bit.

CHIMO!
Bruce

**EDIT:**  next Friday... is Hawaiian shirt day. <<--- yea, right, coming up to winter here. Like I'm going to waer one.  :)

---

### Post by popch on 2008-05-31
> **Bruce M. said:**
> WHAT!!!!! You'd cheat?

If I could adjust your money, it wouldn't be cheating, would it, now?

> **Bruce M. said:**
> Event log kept growing ...
Both "black" and "red" {serious} entries.

Since the log only logs what's been thrown at your ports, you will not see any difference, regardless of the setting of your ports. You'd see different replies to the attempts to access your ports. In the case of 'stealth', you would not see any replies, while in the case of 'closed' you'd see negative acknowledgements issued by your computer, I presume.

---

### Post by bash on 2008-05-31
I recommend anyone not sure about the whole stealth or closed issue to read the following thread:

[http://forum.kaspersky.com/index.php?showtopic=68104&hl=stealth](http://forum.kaspersky.com/index.php?showtopic=68104&hl=stealth)

It's on the Forums of Kaspersky a quite renowned Anti-Virus company. They had to deal with a similar issue, as their new product doesn't stealth the ports anymore. It just makes sure that they are closed.

---

### Post by Bruce M. on 2008-05-31
> **bash said:**
> I recommend anyone not sure about the whole stealth or closed issue to read the following thread:

[http://forum.kaspersky.com/index.php?showtopic=68104&hl=stealth](http://forum.kaspersky.com/index.php?showtopic=68104&hl=stealth)

It's on the Forums of Kaspersky a quite renowned Anti-Virus company. They had to deal with a similar issue, as their new product doesn't stealth the ports anymore. It just makes sure that they are closed.

And I found this one: [Closed vs Stealthed Ports]("http://www.broadbandreports.com/forum/remark,3490473").  Good read even though I am only part way through it.

I'll check out the one you gave us too.

Have a good day.
Bruce

---

### Post by Bruce M. on 2008-05-31
> **popch said:**
> If I could adjust your money, it wouldn't be cheating, would it, now?

If you're trying to pad the odds on the coin landing on it's edge that would be cheating. Of course that's just my opinion.  :)

> **popch said:**
> Since the log only logs what's been thrown at your ports, you will not see any difference, regardless of the setting of your ports. You'd see different replies to the attempts to access your ports. In the case of 'stealth', you would not see any replies, while in the case of 'closed' you'd see negative acknowledgements issued by your computer, I presume.

Hmmmm, I'll have to check and see if there is a column for "Replies".
But yes, what you say makes sense even to this non-techie.

Now here's a techie type question that has arisen in my non-techie mind as a result of this thread.

How can a firewall report who is "pinging" a "stealthed" port? Doesn't it need to "pong" it to do that, thereby acknowledging that the port is really there? 

And no this is not a trick table tennis game question, go away Gump!

---

### Post by Old_Grey_Wolf on 2008-05-31
I didn't notice it was there. Sorry :(

> **p_quarles said:**
> There is such a forum, and there is such a sticky. :)

This thread is fine here, as far as I'm concerned, because it's more of a discussion than a support question.

---

### Post by popch on 2008-05-31
> **Bruce M. said:**
> How can a firewall report who is "pinging" a "stealthed" port? Doesn't it need to "pong" it to do that, thereby acknowledging that the port is really there? 

That's the way the internet works (when and if it does) most of the time:

One computer sends a 'packet' of data to another computer. The 'header' of the packet corresponds to the envelope of a letter. It contains the IP address of the computer and the 'port' of that computer which is to receive the packet.

The computer mentioned as recipient receives the packet (obviously) and passes it to the program which has registered as being responsible for the port mentioned on the 'envelope' (the header).

In the case of a 'stealthed' port, the package 'is silently vanished', i.e. it is read by the system and discarded without sending any response at all. That's the same as if the package was not received by any computer.

In the case of a 'locked' port, the receiving system sends (I think, at least) a package back saying that the port addressed by the package is set not to respond.

Hence, pinging a computer consists of asking that computer to send a reply. The reply sent by the computer thus 'pinged' could be called the 'pong'.

---

### Post by Bruce M. on 2008-05-31
> **Old_Gray_Wolf said:**
> I didn't notice it was there. Sorry :(

Don't be sorry, get involved in the discussion. It's a great learning experience ... for me at least.  :)

Welcome aboard
Bruce

---

### Post by Bruce M. on 2008-05-31
> **popch said:**
> That's the way the internet works (when and if it does) most of the time:

One computer sends a 'packet' of data to another computer. The 'header' of the packet corresponds to the envelope of a letter. It contains the IP address of the computer and the 'port' of that computer which is to receive the packet.

The computer mentioned as recipient receives the packet (obviously) and passes it to the program which has registered as being responsible for the port mentioned on the 'envelope' (the header).

In the case of a 'stealthed' port, the package 'is silently vanished', i.e. it is read by the system and discarded without sending any response at all. That's the same as if the package was not received by any computer.

In the case of a 'locked' port, the receiving system sends (I think, at least) a package back saying that the port addressed by the package is set not to respond.

Hence, pinging a computer consists of asking that computer to send a reply. The reply sent by the computer thus 'pinged' could be called the 'pong'.

Hey, the fog is lifting a bit and this really explains things in a non-techie way.

Thanks :popcorn:ch

I've been doing some reading (from the links above) and I'm getting the impression that as far as "security" is concerned; "stealth" and "closed" are basically the same. They both tell "something" about your computer if someone already knows you are there.  And lets face it every time you use the net you are advertising your IP address in some way.

Firefox to get here to the forums, Thunderbird to get my email, conky to get the weather. Hackers will know you are there and still need to "hack" their way in through the ports.

**Rule of Thumb :** Don't leave an open port unattended.

CHIMO!
Bruce

---

### Post by klange on 2008-05-31
I think there is a good reason why the term is "stealth". If they don't know you're there, they don't know you're there, but if they already know you're there, the lack of response won't hinder their efforts.

If you know there's an F-117 in front of you and it's not on your side, you don't look at the lack of a blip on your radar and fly away, you shoot the damn thing.

**e**: Hmm. Well, I can't actually use the F-117 in my example, it was finally retired a month ago. Darn.

---

### Post by Mateo on 2008-05-31
[IMG]http://www.ilovebonnie.net/tinfoil-hat.jpg[/IMG]

Sometimes I think people who are obsessed with security are being overly paranoid.

---

### Post by Closed_Port on 2008-05-31
> **p_quarles said:**
> Under normal circumstances and with a decently secure setup, no.

The problem with closed ports rather than stealthed ports is that the former confirm the existence of a computer on a particular network address. In other words, a stealthed port doesn't tell an attacker that there's anything to attack. 

If an attacker were to find a bunch of closed ports, he would have confirmed the existence of a machine at that address. Attacking that computer would be specific to the situation, and would most likely be a lot more complicated than just opening a port (which would require the machine to be already compromised in the first place).

Hey, first post on this forum and I'm already disagreeing with a moderator. Now if that isn't a good start... ;-D

Anyway, I think it's a myth that stealth means your machine is invisible. On the contrary, setting the ports to stealth makes it clear that there is a machine there that simply drops packages. If there wasn't, that is, if there simply were no machine, the guy trying to connect to your machine would get a different answer:
[http://hansenonline.net/Networking/stealth.html](http://hansenonline.net/Networking/stealth.html)

Add to this that it also means that legitimate traffic doesn't get the answer it expects, which can for example lead to higher traffic, as a program tries to reach you again and again, I never really saw the attraction of stealth.

---

### Post by DigitalDuality on 2008-06-01
d

---

### Post by DigitalDuality on 2008-06-01
d

---

### Post by p_quarles on 2008-06-01
> **Closed_Port said:**
> Hey, first post on this forum and I'm already disagreeing with a moderator. Now if that isn't a good start... ;-D

Anyway, I think it's a myth that stealth means your machine is invisible. On the contrary, setting the ports to stealth makes it clear that there is a machine there that simply drops packages. If there wasn't, that is, if there simply were no machine, the guy trying to connect to your machine would get a different answer:
[http://hansenonline.net/Networking/stealth.html](http://hansenonline.net/Networking/stealth.html)

Add to this that it also means that legitimate traffic doesn't get the answer it expects, which can for example lead to higher traffic, as a program tries to reach you again and again, I never really saw the attraction of stealth.
You are completely correct: stealthing a port hides the computer only from those who aren't looking very closely. My earlier statement was made without thinking very hard about that, and I stand corrected. 

You also reminded me that nmap, in many cases, can gather a lot of details about a networked machine without receiving any ping replies at all. 

No one should get overly concerned about this, but it is good to remember that there is no "one-stop shopping" solution to security. Don't rely on something like stealthing ports to make up for other reckless security practices.

---

### Post by Closed_Port on 2008-06-01
> **p_quarles said:**
> 
No one should get overly concerned about this, but it is good to remember that there is no "one-stop shopping" solution to security. Don't rely on something like stealthing ports to make up for other reckless security practices.

Now that's really good advice!

---

