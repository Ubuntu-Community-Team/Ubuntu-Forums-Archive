---
title: "Tor anonymity/security at exit node"
date: 2012-03-07
forum: Security
---

### Post by redmon on 2012-03-07
I have recently started using Tor and am still trying to understand the limitations. One is that Tor does not encrypt traffic between the exit node and final destination.

If the main benefit of Tor is anonymity, and if the number of people seeking anonymity potentially includes a higher percentage of political dissidents, etc., and if an organization wanted to detect and monitor political dissidents, etc., would not that organization be more likely to set up a Tor exit node to monitor Tor traffic than to monitor non-Tor traffic? If that is true, then would using Tor potentially provide less anonymity and security than using higher traffic volume non-Tor connections?

Hope that makes sense.

---

### Post by |{urse on 2012-03-07
Tor is great, if you are worried about exit nodes being sniffed try i2p.

[http://www.i2p2.de/how_networkcomparisons](http://www.i2p2.de/how_networkcomparisons)

"Unidirectional tunnels instead of bidirectional circuits, doubling the number of nodes a peer has to compromise to get the same information."

Not foolproof but a little safer. At this point you have gotten into the 'paranoid dimension' of security. If you actually need this level of anonymity I'd be shocked.

Also, i2p is relatively new and not yet blocked by many of the sites that block tor so more of the net will be accessible.

---

### Post by redmon on 2012-03-08
Maybe my hypothetical situation was too extreme.  Still trying to understand the level of anonymity of Tor.  Also when and when not to use Tor.

 If I understand correctly, an exit node could read what is sent, but  will not know who sent it.  How does webmail fit in?  Could an exit node  read email sent from the gmail website?  If purchasing something  through a website, could the exit node read confidential information  such as a credit card number?


  A reply to a thread in another forum stated that Tor should not be  used for webmail or anything personal.  Which leads back to my question:   when and for what should I use Tor?

---

### Post by winh8r on 2012-03-08
Tor is a great resource for those requiring short periods of "anonymity" such as sending a report out of an oppressive regime or something along those lines. It is however not such a great proposition for general everyday use. That and the fact that it can potentially cut your connection speed by a considerable amount, coupled with the points you raised in your first post about "rogue nodes" sniffing traffic passing through.

I would agree that it would be unwise to send sensitive personal data through a tor network, due to the fact that it is "secure" it therefore tends to attract an interest from those with a desire to circumvent "security", generally speaking.

I usually advise people that unless you actually NEED to use Tor, it is best to avoid using it. By need, I mean those people who for whatever reason cannot communicate through "normal" channels for fear of reprisals.

A well configured operating system using encrypted connection and pgp keys , coupled with a sensible operator is just as secure as a Tor connection.

As I said earlier, it is good at what it does, so long as what it does is what you need.

There is virtually no way to use the internet in "Total Anonymity", there are ways to disguise who you are and where you are but the truth is , wherever you go you leave a digital fingerprint somewhere along the trail.

---

### Post by imagecko on 2012-03-09
For a few years ago a swedish guy started to "listen" to what what was sent in Tor.
He had a large list of working passwords to different mailboxes and stuff on his harddisk after a while.

---

### Post by ottosykora on 2012-03-11
People sometimes confuse TOR with some kind of vpn.

OK, we can to certain limit see it as vpn between the user and the exit node.
But remember: it is asymmetric encryption between the nodes involved and this can not be understood by anyone or anything else then other tor node.
So the traffic has to be decrypted at the end and delivered in its normal standard language to the called web servers. Because the web servers do not understand anything else.

However the origin of the original request to the web server is wiped, it is non existent and can not be reconstructed.
Traffic between the TOR nodes can not be monitored or decrypted, no such technology exists so far.
The actual traffic between the exit node and the destination can be read as if there was no tor involved.
Everybody who knows to operate some network sniffer efficiently can monitor all traffic as he can do otherwise.
(If ssl is involved, he might have slight problems here too.)

Webmail:
thinking about it. The browser in users computer sends requests, gets data back , then user writes text and mail commands, sends it to the webmail server. All is normal web server! Therefore also here, the origin is wiped completely, but after exit node, everything can be monitored, all data going back and forth as the webmail server does not understand anything else, in some cases it understands ssl, so tor will use it. 

SMTP Mail:
one can make the mail client to use the tor subsystem too. But then again, it will travel highly encrypted from the users computer to an exit node. From there it has to go again as normal SMTP, if the server understands some ssl, then tor will use it too.

Few things has to be considered. Today a browser does not only send requests to port 80 on some destination and asks for some picts and texts.
Browser will employ number of other programs as plugins and addons and those can find their own communication, using own way to communicate with some servers where ever.

Have met someone who complained that in the bundle tor browser he can not use flash for youtube videos...  ;-)

---

### Post by ottosykora on 2012-03-11
> **redmon said:**
>  would not that organization be more likely to set up a Tor exit node to monitor Tor traffic than to monitor non-Tor traffic? If that is true, then would using Tor potentially provide less anonymity and security than using higher traffic volume non-Tor connections?

Hope that makes sense.

sure, but let think it to the end. This is the same as 'authorities' will just monitor encrypted traffic . They will just estimate from the amount of traffic what could go on.

There is no problem in setting up an exit node and monitor all traffic leaving it. If the contents of the traffic do not give any indication of who is the originator of the traffic, then the info is of limited use.
One could get the idea to set up a number of nodes and hope so to get some traffic from beginning to the end. But tor network is build to avoid this possibility. It forces the traffic via different parts of the world so such scenario can not happen.
The standard today is set to 3 hops, but it can also be increased to 5 or 6 and it would be essential to monitor the first entry point, all intermediate points and the exit node at the same time and even then the actual reconstruction of the original ip could be not easy.

---

### Post by ottosykora on 2012-03-11
> **imagecko said:**
> For a few years ago a swedish guy started to "listen" to what what was sent in Tor.
He had a large list of working passwords to different mailboxes and stuff on his harddisk after a while.

so what?
everybody can do this, you can do it too. Where is the problem?
There is no intention to prevent this at all.

---

### Post by redmon on 2012-03-11
ottosykora,

So if the webmail uses https, does that mean that the text in the messages is encrypted?

If the email client uses SSL/TLS for both incoming and outgoing, is the text in the emails encrypted?

Then the exit node would not know either source or contents?  If that is true, then Tor could be used for safely sending confidential information?

---

### Post by ottosykora on 2012-03-12
> **redmon said:**
> ottosykora,

So if the webmail uses https, does that mean that the text in the messages is encrypted?

If the email client uses SSL/TLS for both incoming and outgoing, is the text in the emails encrypted?

Then the exit node would not know either source or contents?  If that is true, then Tor could be used for safely sending confidential information?


hmm , have to be careful,  the thing with the https is such that if I tell you, yes 100% encrypted, I may earn some flames here... as they are real experts around here.



but ok, the communication is encrypted, so if someone intercepts the traffic, he will not be able to read anything unless he is able to run some of the attacks against ssl in reasonable amount of time.
What is probably wrong term is that the text is encrypted. The communication is encrypted as such, provided the server uses it all the time and not only during authentication process etc. which some of them do.

It does not say what does happen with the mail when it leaves the server however. In fact, webmail is just kind of remote control of mail client on other computer and therefore you would need to know what does happen with the mail when you click on the send button in that 'remote mail client'.

If you manage to use tor for mail protocols too, then clearly ssl/tls will remain as they are, the traffic will be encrypted by them.


BTW: there exists an addon for firefox which will test if a target server is able to understand ssl and will force ssl communication in such case.
This addon is also included in the tor browser bundle already.

---

### Post by wacky_sung on 2012-03-12
In short there is no such things as Anonymous. All can be traceable but it depend on the process or progression to track it down. I bet it is what you actually need is to protect your privacy.

---

### Post by kevdog on 2012-03-12
If you are really paranoid and considered about anonymity, I'd also take a look at Mixmaster as a way of anonymizing your email as well.  This program is often times mentioned in the same breadth of Tor/Privoxy.  Also utilize gnupg.

---

### Post by ottosykora on 2012-03-12
> **wacky_sung said:**
> In short there is no such things as Anonymous. All can be traceable but it depend on the process or progression to track it down. I bet it is what you actually need is to protect your privacy.

I would not call it that dramatical, but when I try to read infos about problems the devs of such software and networks have, then I think they had easy job some 10 years ago.

On the other hand, 10-15 years ago, people did take care of what programs talk to someone in internet and why. 
Today everybody finds it is not a bug but a feature when your computer connects all  the time with dozens of servers all over the world 'just to check for updates'.

People are very keen of storing their most personal data on cloud servers and they never ask who else can see it.

With tor ,as with mixmaster etc, the idea was to remove the origin of the communication between a client and a webserver.

But when all that was designed, browsers had not hundreds of extensions and plugins which behave completely unpredictable in this context.

Tor will change your IP, but when your browser is full nice valuable other data which be collected by anyone then well privacy becomes relative.

You can try the tor bundle browser. This will make you browse with no scripting, no plugins , no fancy cookie mechanisms.

There are not many websites which you will be able to use.

---

### Post by wacky_sung on 2012-03-13
> **ottosykora said:**
> I would not call it that dramatical, but when I try to read infos about problems the devs of such software and networks have, then I think they had easy job some 10 years ago.

On the other hand, 10-15 years ago, people did take care of what programs talk to someone in internet and why. 
Today everybody finds it is not a bug but a feature when your computer connects all  the time with dozens of servers all over the world 'just to check for updates'.

People are very keen of storing their most personal data on cloud servers and they never ask who else can see it.

With tor ,as with mixmaster etc, the idea was to remove the origin of the communication between a client and a webserver.

But when all that was designed, browsers had not hundreds of extensions and plugins which behave completely unpredictable in this context.

Tor will change your IP, but when your browser is full nice valuable other data which be collected by anyone then well privacy becomes relative.

You can try the tor bundle browser. This will make you browse with no scripting, no plugins , no fancy cookie mechanisms.

There are not many websites which you will be able to use.

I do understand what you meant.Have you considered who setup those Tor servers and what information are they collecting from you.I do not need Tor because i pay for a VPN service which written clearly for their term and conditions. What we really need is privacy but not being anonymous. Tor is just another chain proxies to me.

---

### Post by ottosykora on 2012-03-15
>who setup those Tor servers and what information are they collecting from you.<

well tor server does not mean that any information can be collected. Everybody can do that and the system was set up by an voluntters org.
A relay server can be any computer, I run one too. With this there is so far no way to collect anythnig as all comes highly encrypted and leaves again highly encrypted and nothing is decrypted.

But do not confuse vpn with tor. Those are two entirely different things and for different purpose.
Some tor users tend to think of tor as vpn too, but this is completly wrong.


VPN is point to point operation, it can serve only two endponits and can only carry 'cargo' between them and those two have to trust each other.
It can not have any anonymising function as it would not work.
If the traffic has to be forwarded, it has to be done again in open format and free accessible to everyone again.

Tor is for wiping out the origin of the traffic and make it by this not traceable. And it should work reliably not only between two dedicated users, but worldwide, dynamic selfmanaging .
The purpose here is not to hide the traffic itself, only the origin of it.

That it is possible to view the traffic comming out of the exit server is clear.
That everybody can see the traffic coming out of the vpn server is also clear.
The traffic on a vpn is well protected while underway, but it has to leave the tunel at some time and there it ends up in open plain traffic as if nothing was between.

To have some term and agreements, well hope you understand that those things have zero security value, unless you absolutely  trust each single person involved in operation of such server or you are the only person who has physical access to such installation.

As far security of any software solutions today in the computer age, it is often considered anything open source to be more secure then any kind of pure proprietary and closed solution.
The open source solution can be free reviewed by many people worldwide, they will try to find holes and issues in it and will discuss all problems open.
With closed solutions this is often not possible and then we have 'security by obscurity' meaning an outsider has no idea what the solution actually does.

---

### Post by wacky_sung on 2012-03-15
> **ottosykora said:**
> >who setup those Tor servers and what information are they collecting from you.<
======================
Sound like you are new to data miner which can collect any information about you.Find out for yourself why google is evil.
=====================

well tor server does not mean that any information can be collected. Everybody can do that and the system was set up by an voluntters org.
A relay server can be any computer, I run one too. With this there is so far no way to collect anythnig as all comes highly encrypted and leaves again highly encrypted and nothing is decrypted.

==================
Does not mean highly encrypted which is not breakable.It depend on the talent and skill of breaking it
==================

But do not confuse vpn with tor. Those are two entirely different things and for different purpose.
Some tor users tend to think of tor as vpn too, but this is completly wrong.

===========
Agree.
===========


VPN is point to point operation, it can serve only two endponits and can only carry 'cargo' between them and those two have to trust each other.
It can not have any anonymising function as it would not work.
If the traffic has to be forwarded, it has to be done again in open format and free accessible to everyone again.

Tor is for wiping out the origin of the traffic and make it by this not traceable. And it should work reliably not only between two dedicated users, but worldwide, dynamic selfmanaging .
The purpose here is not to hide the traffic itself, only the origin of it.

============
I totally disagree with you because it is still traceable in the memory even though you run it a relay as long as each relay does not break it memory.You just need to fix the puzzles to get to the actual person. The work is tough and long process.

============


That it is possible to view the traffic comming out of the exit server is clear.
That everybody can see the traffic coming out of the vpn server is also clear.
The traffic on a vpn is well protected while underway, but it has to leave the tunel at some time and there it ends up in open plain traffic as if nothing was between.

To have some term and agreements, well hope you understand that those things have zero security value, unless you absolutely  trust each single person involved in operation of such server or you are the only person who has physical access to such installation.

As far security of any software solutions today in the computer age, it is often considered anything open source to be more secure then any kind of pure proprietary and closed solution.
The open source solution can be free reviewed by many people worldwide, they will try to find holes and issues in it and will discuss all problems open.
With closed solutions this is often not possible and then we have 'security by obscurity' meaning an outsider has no idea what the solution actually does.

============
Quite true and half hearten disagree if someone break it without reported it till somebody discover an intrusion. There are quite a handful cases down the years such as kernel website being hack which went unreported till someone discover it.
===========

---

### Post by rg4w on 2012-03-15
> **wacky_sung said:**
> Have you considered who setup those Tor servers and what information are they collecting from you.
I don't mean to sound paranoid, but if I worked for the FBI I'd make sure I had a few dozen machines in the Tor pool.

---

### Post by ottosykora on 2012-03-16
>I totally disagree with you because it is still traceable in the memory even though you run it a relay as long as each relay does not break it memory.You just need to fix the puzzles to get to the actual person. The work is tough and long process.<

hmm, in memory of what? As my computer has to no time any knowledge where the origin of the traffic came from, it is keeping in memory:
'I have a traffic, but have no idea where it comes from'
My computer will do: encrypt the whole stuff to the next server I am assigned just now in this second to forward my traffic to and send it there.

So my computer has at this moment stored info that a traffic arrived from some tor part, and it ***appears*** to come from certain tor component.
The traffic was encrypted to the next server from the pool used just at that moment.

It has no information about the content of the traffic, no inofrmation where the traffic came from or what is its final destination (in case of tor relay)

So everybody is welcome to pick this valuable info and see what to make of it.

As far as cryptography, well best to say it is considered unbreakable at this state of knowledge and technology.

---

### Post by ottosykora on 2012-03-16
> **rg4w said:**
> I don't mean to sound paranoid, but if I worked for the FBI I'd make sure I had a few dozen machines in the Tor pool.

sure, Q is just what to use it for.

one can monitor traffic coming out of the exit relay, ok, no problem with that, one can monitor any other forwarding computer too, no secret in it, all free and open there and why to operate such exit?

To have normal relay in operation, well again the Q is what for?
To keep the tor operational, fine welcome. The more relays there is the more efficient is the network.

To sniff the traffic from a relay, hmmm, the info is highly encrypted, not decryptable with any currently known method within needed useful time .
No idea where it comes from, no idea where it goes to.
That there is increase of traffic let say from 0900-1200 and decrease of traffic during 1600-1900 is also an information which can be used. But it needs to be used statistically only, direct info is not present, but direct content might in many cases also not be particularly important.


Welcome everybody to monitor this random noise. The more someone tries this, the more secure in fact the network becomes.

So if FBI wants to set up some more relays, please do so, do as many as your power bill will allow you to have.

---

### Post by ubunbu on 2012-03-18
If you're concerned with mail there's always [Tormail]("http://ubuntuforums.org/jhiwjjlqpyawmpjx.onion/"), which is in the onion.

(Link didn't turn out quite right ... )

Edit: I realize this doesn't address the exit node issue at all. Though this would at least be, in theory, an anonymous origin.

---

