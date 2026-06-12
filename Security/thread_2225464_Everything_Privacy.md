---
title: "Everything Privacy"
date: 2014-05-21
forum: Security
---

### Post by chadrlz on 2014-05-21
I have a machine that I am trying to make anonymous. I have been reading a lot lately about the different ways of anonymizing ones computer online through proxy services,VPNs,and different browsers specifically TOR and I2P. I hit a wall while tring to configure I2P to browser eepsites. I am also trying to set up some easy to use yet very secure encryption. I do not want anything that has to be run through a command line. I am doing this for someone else who isn't real savvy so I need to have programs in place which are easy to use and don't require a lot of customizing/updating after the fact. If I was a bit smarter than I am I could make front-end GUIs for all the things I really like and call it a day however I am not at that level as of yet. There are other aspects of this which I haven't touched on yet because I would like to accomplish these goals first. Any help that I can get on this would be appreciated greatly.

---

### Post by Lars Noodén on 2014-05-21
You might look at the Tails live distro instead.  

[https://tails.boum.org/](https://tails.boum.org/)

Much of the work you describe is already done there.

---

### Post by sudodus on 2014-05-21
One way to go is to use a linux distro that is made for that purpose, for example Tails

[https://tails.boum.org/](https://tails.boum.org/)

It is much easier and much less risk that you make a mistake compared to starting with Ubuntu and fixing the security level on your own.

---

### Post by chadrlz on 2014-05-21
I am aware of TAILS and for myself I might do something like that if I needed it, however for this person I have to take what they are already familiar with and modify it accordingly. This is what I must do. While I am talking about it I am also looking for a good secure email service. I already know of a few some free(hushmail and lavaboom) some not. I want to look at all my options and choose the best ones for the purpose and within the guidelines that I have to work within. I am sure that this type of information would be useful to many people for the simple reason that most people just do not like change. If we can seemlessly do this that would be ideal.

---

### Post by 1clue on 2014-05-21
Yeah, and the idea of anonymity is a myth anyway.  You're connecting through an ISP right?  There's a log.  All TOR will do is cause it to take longer to get the subpoena.  And as far as that's concerned probably every byte into and out of TOR servers is being watched by 30 different countries anyway.

---

### Post by Habitual on 2014-05-21
> **1clue said:**
> Yeah, and the idea of anonymity is a myth anyway. Finally! Someone else said it.

---

### Post by Chayak on 2014-05-21
> **chadrlz said:**
> I am doing this for someone else who isn't real savvy so I need to have programs in place which are easy to use and don't require a lot of customizing/updating after the fact.

TOR isn't a magic bullet.  You have to be very disciplined when you use it.  There's a long list of arrests of people that were using TOR to prove it.  There are certain elements of OPSEC (Operational Security) that you have to follow for any real security.  By making a static distro with 'anonymous' tools you're already breaking a lot of that OPSEC.  Government intelligence and law enforcement agencies are watching TOR *very* closely.  They have monitoring nodes within the TOR system.  If you make a mistake they'll know exactly who you are.  If your friend isn't savvy enough to use Talis as a live CD to do what he/she needs to do then using TOR on an installed system is just going to present a false sense of security.

TOR is best used with a shoot and scoot mentality.  You get on public WIFI with a randomized MAC address with something like Talis, do exactly what you need to do with things prepared ahead of time, and then move on.  The more time you spend and data you generate over TOR just feeds the tools to locate and identify you.

I'm not someone who does it myself.  I don't have the need, but I know a good deal about the topic from people I've worked with in the past.

---

### Post by 1clue on 2014-05-22
> **Chayak said:**
> TOR isn't a magic bullet.  You have to be very disciplined when you use it.  There's a long list of arrests of people that were using TOR to prove it.  There are certain elements of OPSEC (Operational Security) that you have to follow for any real security.  By making a static distro with 'anonymous' tools you're already breaking a lot of that OPSEC.  Government intelligence and law enforcement agencies are watching TOR *very* closely.  They have monitoring nodes within the TOR system.  If you make a mistake they'll know exactly who you are.  If your friend isn't savvy enough to use Talis as a live CD to do what he/she needs to do then using TOR on an installed system is just going to present a false sense of security.

TOR is best used with a shoot and scoot mentality.  You get on public WIFI with a randomized MAC address with something like Talis, do exactly what you need to do with things prepared ahead of time, and then move on.  The more time you spend and data you generate over TOR just feeds the tools to locate and identify you.

I'm not someone who does it myself.  I don't have the need, but I know a good deal about the topic from people I've worked with in the past.

++ on "shoot and scoot."  The only way TOR has any hope of being truly private is if you're going from place to place, never using the same access point twice.  The only thing I can imagine making it worth the effort is if you're doing something naughty.

Seriously, you do NOT have anonymity unless you do this sort of thing, and then you only have the anonymity for the duration of a short session when you know what you're doing.  If you're doing something that somebody is really curious about, they WILL figure out what to look for if you use a consistent access point.  I would go so far as to say that if you do something illicit (why else use TOR, other than to realize what a crappy tool it is?) and do it twice from the same location, probably there is going to be a wire tap on the address you're sitting at on that second session.  If it's a public place, they'll probably have a security camera image or webcam with your mug shot.

I used TOR once, because of the privacy issues being discussed on forums like this one.  I wanted to know what everyone was talking about.  There's no way I'd do it on a regular basis just because of how incredibly inconvenient it is, and also because simply using it is probable cause, especially when my government isn't obeying its own privacy laws anyway.  You can be sure that within a few minutes of the time any TOR server gets put online, there's a wiretap on all possible routes in.

The moral of the story is, don't do anything you'll be horribly embarrassed about if people know, and just use normal security measures.

---

### Post by sudodus on 2014-05-22
TOR hides the PC's IP address from the final server, but if the owner of the proxy server (which helps you hide it) is the security service of a superpower country, you are not helped much. And it is hard to know who owns the proxy servers, that are used by TOR. 

You must realize that there is no privacy on the Internet.

-o-

If your client/friend uses only encrypted connections or sends/receives only encrypted mails, it might be hard to read, but it will be rather easy to know where your client/friend is browsing (which web pages) and with whom your client/friend exchanges mail.

Lets us say that your client/friend is doing legal but secret things (for example research or other commercially classified information). Then I think it should be enough to send and receive encrypted messages, for example encrypted mails. This is not a typical case for using TOR.

- One way to do it is to use ***Enigmail*** that can be installed in Thunderbird. The difficult part is to make the guy[s] at the other end to install and use it too.

- Another way is to simply attach encrypted files to the mails. Pretty Good Privacy is a good method, and the linux software for it is ***gpg***. There is a GUI front end, ***Seahorse***.

---

### Post by LastDino on 2014-05-22
I'm not going to point fingers, but what does an average desktop user (who isn't tech savvy) needs something like TOR for? Like many people mentioned before, if anything, using it WILL attract attention rather than being discrete. Everybody wants to know whats it is used for by ''you'' when we hear things like it has been used by certain run-away intelligence agent. IMO, true anonymity  on internet is only ''hypothetical'' and if people really want to know what you're doing on the certain end machine, they will find a way to know it within the time period of repetition of that action. Best way for avergae people to go about is to keep them disinterested and usually you will get away with more that way :P

---

### Post by Chayak on 2014-05-22
> **1clue said:**
> ++ on "shoot and scoot."  The only way TOR has any hope of being truly private is if you're going from place to place, never using the same access point twice.  The only thing I can imagine making it worth the effort is if you're doing something naughty.

Or you are a blogger or journalist being critical of a country with a history of arresting critics.

---

### Post by chadrlz on 2014-05-22
I have thought about Seahorse, husmail, and lavaboom. If I could get this i2p thing figured out I would be thrilled. I understand the concept and how to change proxy settings but Im not having much luck there. Anyone using i2p that can help me wouold be appreciated. Thanks again guys..

---

### Post by Chayak on 2014-05-22
> **chadrlz said:**
> I have thought about Seahorse, husmail, and lavaboom. If I could get this i2p thing figured out I would be thrilled. I understand the concept and how to change proxy settings but Im not having much luck there. Anyone using i2p that can help me wouold be appreciated. Thanks again guys..

I2P isn't very usable.  It would help if you would describe the reason behind taking such measures.  There are many solutions for online security based upon a realistic threat assessment.  If you don't want to discuss it openly then send me a private message or I can send you my GPG public key.

---

### Post by 1clue on 2014-05-22
> **Chayak said:**
> Or you are a blogger or journalist being critical of a country with a history of arresting critics.

Realistically speaking I don't think Tor would be much of a help in that case, unless you're in a country with little or no technological sophistication.  There was a short period where that was a significant factor, but the "Arab Spring" convinced most countries who don't hold human rights as a priority that they need to keep better tabs on their Internet security.

The thing is, every country who cares (most of them) control Internet access points when data crosses their borders.  A company might own the wires, but you can be sure the government has hooks into it to see what goes through the pipe.

Second point, a country which is oppressive to critics will almost certainly not have a TOR proxy inside its borders, and they'll probably have a reasonably good list of those proxies.

If I were a dictator of some small country trying to keep control of my peasants, I'd consider access to a TOR server to be an act of treason, or at least as probable cause.  Who could you possibly be trying to keep secrets from, other than your beloved dictator?

---

