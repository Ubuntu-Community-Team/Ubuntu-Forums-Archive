---
title: "Does tor keep logs?"
date: 2011-03-06
forum: Security
---

### Post by asdfghjkl67 on 2011-03-06
I know this isn't the place but tor dosent have its own forum which is why im posting here. To that end can anyone post here about tor logs. 

  	 	 	 	p { margin-bottom: 0.21cm; }  First off does tor ever keep IP logs or other data of what users do over tor? Ive heard rumors that the some servers keeps logs of what the servers do for 24 hours in RAM memory (which is volatile when the server is restarted). Is this true? what happens when law enforcement agencies demand to see the server logs-do the server admins hand it over?

---

### Post by alphaamanitin on 2011-03-07
Well, unless TOR is a complete lie, no.  Since TOR relies lots on the every day person to run exit nodes even I don't think TOR can have any control over what the servers do.  Also, assuming TOR does not lie, even if police (or anyone) searched an exit node they still would not be able to find the original computer that used that exit node to do whatever it is that got them interested in it in the first place.

I doubt there are logs or anything like it.  It would render TOR pointless and as it is open source I think that people would have found and made public any flaws in TOR that were built in like that on purpose.  

AlphaA

---

### Post by uRock on 2011-03-07
If I were an exit node, then I would be logging everything. 

I don't think police would be looking for such info, but if the FBI were to kick the door in, then I think their IT people would be able to find just about anything on a system. If logging is enabled on the router, then the incoming and outgoing IP connections will be logged.

---

### Post by Joeb454 on 2011-03-07
Thread re-opened as per RC discussion

---

### Post by alphaamanitin on 2011-03-07
This is true that the exit nodes may record everything that goes on, but it was my understanding that having a complete log of an exit node would still get you no closer to finding the person who was using that exit node.  

It was also my understanding that this applies on the other end.  So, if some one was trying to hijack my browsing history while I was on a tor node all they could see was that I connected to a tor node and they could not connect me with the exit node used (unless there was so few nodes it was possible to check all nodes).  

I understand that this thread cannot discuss illegal activities and I for one do not wish to do so.  I do not know about the OP, but I think we can have a nice discussion over the relative security and inherent trust one puts in the tor network. I would like to say that the tor network is used in many legal and responsible ways to help protect human rights.  It can even help in preventing companies that track your browser sessions to target adds towards you.  Here is more information on how the tor network is legally and responsibly used.  

[https://www.torproject.org/about/overview.html](https://www.torproject.org/about/overview.html)

AlphaA

---

### Post by Soul-Sing on 2011-03-07
> I would like to say that the tor network is used in many legal and responsible ways to help protect human rights.

yep sponsored by the EFF afaik.

> Re: Does tor keep logs?
"who is TOR", thats an ambigious question. TOR is not a company or a organization.
It is software depends on nodes. Individuals/universities/etc.

> Tor helps to reduce the risks of both simple and sophisticated traffic analysis by distributing your transactions over several places on the Internet, so no single point can link you to your destination.

Reduction indeed,but there is no promise of obsolute anonymity, it gives you a layer that protects your privacy.

Logging. A log as a trace of your personal behaviour on the world wide web? I doubt it, but imo it is possible.
[COLOR="Red"]The individual nodes are not controlled or certified[/COLOR]. Which could be done!

---

### Post by rookcifer on 2011-03-07
It depends on whether the OP means local logs or remote logs.  As for local logs, no.  If you setup TOR as explained on their documentation page, it will keep no local logs.

As for remote logs, as others said, it is possible for the exit node to see everything (unless you're also using SSL).  Keep in mind, the exit node can see *what* you're doing, but he can't see *who* you are (unless you reveal yourself by putting in passwords or usernames over insecure connections).

To break TOR, one would need to control all 3 nodes along the circuit (unlikely).  Another possibility is that an all powerful entity that can monitor the backbone of the Internet might be able to conduct some sort of timing attacks to see who is entering the network at what times, etc.  This can be used to correlate entry node times to exist nodes.  Again, this would take a large entity with a large budget.  Most of the known attacks like this are explained on the Tor website.

---

### Post by alphaamanitin on 2011-03-08
> **rookcifer said:**
>   Another possibility is that an all powerful entity that can monitor the backbone of the Internet might be able to conduct some sort of timing attacks to see who is entering the network at what times, etc.

Do you think that is really even doable?  Even by something like a multi-government effort it seems only possible in theory to me.

AlphaA

---

### Post by CandidMan on 2011-03-08
Check out this link when you're running your browser through tor, I was surprised, my rating was 1/55
[http://panopticlick.eff.org/index.php?action=log](http://panopticlick.eff.org/index.php?action=log)

EDIT: Just went to it myself after changing my theme and my anonymity's skyrockete(sans tor)

---

### Post by rookcifer on 2011-03-08
> **alphaamanitin said:**
> Do you think that is really even doable?  Even by something like a multi-government effort it seems only possible in theory to me.

AlphaA

It's hard to say.  We do know that NSA here in the states has a tap on the Internet backbone and can monitor all traffic that passes through it (this is a fact, not a conspiracy theory).  Since they are a multi-billion dollar organization that employs miles of supercomputers, the best computer security professionals, the best cryptologists, and hundreds of PhD mathematicians, I would not feel comfortable using Tor to try and hide from them.  What their capabilities are in *practice* is obviously secret, but I wouldn't take chances if such an organization is in your threat model (and if they are in your threat model, you're probably screwed already).

If you aren't trying to hide from such an organization, I would feel comfortable saying Tor is safe if used properly.  It's certainly effective against ISP snooping and will stop websites from collecting data about you.

The people who have *real* reasons to remain anonymous use Tor as only a tool in their toolbox.

---

### Post by alphaamanitin on 2011-03-08
@rootcifer, could you provide a citation about the NSA monitoring the back bone?  I would like to read things on that.  

AlphaA

---

### Post by rookcifer on 2011-03-08
> **alphaamanitin said:**
> @rootcifer, could you provide a citation about the NSA monitoring the back bone?  I would like to read things on that.  

AlphaA

[https://www.eff.org/nsa/faq](https://www.eff.org/nsa/faq)

[http://en.wikipedia.org/wiki/NSA_warrantless_surveillance_controversy](http://en.wikipedia.org/wiki/NSA_warrantless_surveillance_controversy)

At&T is not the only involved party.  NSA approached most of the major telecom operators.  They didn't only obtain phone calls, but Internet traffic as well.

From Wikipedia:

> The exact scope of the program is not known, but the NSA is or was provided total, unsupervised access to all fiber-optic communications going between some of the nation's major telecommunication companies' major interconnect locations, including phone conversations, email, web browsing, and corporate private network traffic.

In other words, I wouldn't trust TOR to combat an agency with more power than God (and an agency that answers to no one and is 100% above the law).

---

### Post by alphaamanitin on 2011-03-09
They answer to the US congress, at least in theory.  But before 1994 (I think, may be a different year but in the 1990s) they answered to no one but the president.  In fact most people in gov't before that year didn't even know the NSA existed.  I have heard that the joke among government workers not in the NSA is that the NSA stands for "No Such Agency".  

Still thought, that was only AT&T and I am not sure there is any evidence it went beyond AT&T.  Also, could they even analyze all that traffic?

AlphaA

---

### Post by rookcifer on 2011-03-09
> **alphaamanitin said:**
> They answer to the US congress, at least in theory.  But before 1994 (I think, may be a different year but in the 1990s) they answered to no one but the president.  In fact most people in gov't before that year didn't even know the NSA existed.  I have heard that the joke among government workers not in the NSA is that the NSA stands for "No Such Agency".  

Still thought, that was only AT&T and I am not sure there is any evidence it went beyond AT&T.  Also, could they even analyze all that traffic?

AlphaA

I don't want to continue in this thread because I feel it is probably too far off-topic.  The mods frown on "political" stuff, which this conversation could easily become.  I will just refer you to the links I gave above.  The Wikipedia article has a lot of information (that's well referenced) if you want to read further.  And, no, AT&T was not the only party involved.

---

### Post by alphaamanitin on 2011-03-09
Well I can understand that, but we could still talk about my last question.  Is it possible to accurately deal with that much and that variable data in a realistic way given the volume is reoccurring every day?


Anyway, I think this thread is not appropriate for the Security area, can a mod move this thread to some spot more appropriate for it?

AlphaA

---

### Post by rookcifer on 2011-03-09
> **alphaamanitin said:**
> Well I can understand that, but we could still talk about my last question.  Is it possible to accurately deal with that much and that variable data in a realistic way given the volume is reoccurring every day?

Yes, with supercomputers programmed with various algorithms specifically designed for it.  Back in the 80's when Echelon was first being brought public, people who worked on the project came forward and said they had helped design the algorithms the supercomputers used to sort through all the intercepted phone calls.  The computers basically sorted the data via keywords.

---

### Post by iiiears on 2011-03-14
Does TOR use an SSL CERT. to encrypt?

Would Skype be subject to COINTELPRO? A proxy isn't going to fix that if it were.

---

### Post by alphaamanitin on 2011-03-15
I know tor does encrypt connections between the user and all the internal nodes, but the exit node traffic to the www is not encrypted.  I do not know a what type of encryption it uses and I do not know that much about tor.

Also, is it even feasible to do a real-time timing attack?  You would need to analyze the traffic of at least all of europe and the usa to do a timing attack.  I don't know enough about super computers and the likes, but it just doesn't seem possible to deal with all that information.

> **uRock said:**
> If I were an exit node, then I would be logging everything. 


I would also like to say that in an ironic twist, if you are in the USA, doing this may be illegal.  The following is taken from the Tor Legal FAQ [http://www.torproject.org/eff/tor-legal-faq.html.en](http://www.torproject.org/eff/tor-legal-faq.html.en):

**Should I snoop on the plaintext that exits through my Tor relay?**

  **No.** You may be technically capable of modifying the Tor source code or installing additional software to monitor or log plaintext that exits your node. However, Tor relay operators in the U.S. can create legal and possibly even criminal liability for themselves under state or federal wiretap laws if they affirmatively monitor, log, or disclose Tor users' communications, while non-U.S. operators may be subject to similar laws. Do not examine the contents of anyone's communications without first talking to a lawyer.
 

 

 AlphaA

 
 

AlphaA

---

### Post by rookcifer on 2011-03-15
> **iiiears said:**
> Does TOR use an SSL CERT. to encrypt?

It uses a self-generated and signed certificate, which means there is no need for trusting a third-party CA that might be untrustworthy.  You can read technical details of how this is done at the Tor Wiki site.

> Would Skype be subject to COINTELPRO? A proxy isn't going to fix that if it were.

Not sure what you mean by COINTELPRO.  That was a program ran by the FBI decades ago and was more of a psyops program and had nothing to do with the Internet.

---

### Post by Eiji Takanaka on 2011-03-15
If i was some sort of all powerful entity that monitors people who are paranoid, id probably just compromise the ever so 'trusted resources' of ubuntu/linux. In fact i'd probably be the one who invented it in the first place eh. No need to monitor the whole internet then. Just the free-thinking radicals who might pose a threat of sorts further down the proverbial line. 

*scratches head hahahahaha who knows.

If i was running an intellgience agency i would probably have a complete back-up link to the entire facebook servers, as it would be a veritable treasure trove of information, and at the very least could be used to psychologically profile individuals. Profile/assess/categorise with some sort of risk analysis system. 

Hahahaha maybe i'm just being paranoid though eh...... =P

---

### Post by rookcifer on 2011-03-16
> **Eiji Takanaka said:**
> If i was running an intellgience agency i would probably have a complete back-up link to the entire facebook servers, as it would be a veritable treasure trove of information, and at the very least could be used to psychologically profile individuals. Profile/assess/categorise with some sort of risk analysis system. 

Hahahaha maybe i'm just being paranoid though eh...... =P

Something like this is already [being done.]("http://www.rawstory.com/rs/2011/02/18/revealed-air-force-ordered-software-to-manage-army-of-fake-virtual-people/")  It's even worse than profiling, they are creating armies of fake Facebook profiles.

---

### Post by alphaamanitin on 2011-03-16
Last I knew though there was no evidence to actually link HB Gary's plans do to this with the government wanting it, or asking for it.  This could be false now though.  

Anyway,  I think we have gotten a little off point, about the spirit of the post, tor keeping logs and the possibility that tor is able to be defeated.  I know tor can be defeated by a number of conventional means (eg stake outs, keyboard loggers, wiretaps, etc), but is it feasible to connect exit nodes and people in real time simply by logging packets from the exit node and the user of tor?  I think currently no.  Even if you had a handle on the backbone of the US you would still need Europe and more, and I just don't know if it is possible to trace.

AlphaA

---

