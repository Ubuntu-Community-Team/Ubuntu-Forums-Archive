---
title: "Script Kiddies. Are they all bad?"
date: 2011-08-23
forum: The Cafe
---

### Post by amiacamal on 2011-08-23
Posting here instead of community cafe as i intend a security centric discussion, feel free to move if im doin it wrong :)

The Internet has a tendency to look down on / Belittle these so called "script kiddies" and "Crackers" but I am curious. Is it fair to say its not the knowledge these people have that earns them a bad name but rather their use of it? Personally I think it would be interesting to know how to hack the living hell out of my wifi connection, if only to gain a further understanding of how to prevent others from doing the same. But in knowing that, I can then do it to unsuspecting others. What does that make me?

*note, i cant actually crack peoples wifi connections, that was an example*

---

### Post by haqking on 2011-08-23
> **amiacamal said:**
> Posting here instead of community cafe as i intend a security centric discussion, feel free to move if im doin it wrong :)

The Internet has a tendency to look down on / Belittle these so called "script kiddies" and "Crackers" but I am curious. Is it fair to say its not the knowledge these people have that earns them a bad name but rather their use of it? Personally I think it would be interesting to know how to hack the living hell out of my wifi connection, if only to gain a further understanding of how to prevent others from doing the same. But in knowing that, I can then do it to unsuspecting others. What does that make me?

*note, i cant actually crack peoples wifi connections, that was an example*

The point is that Crackers are Hackers with Malicious intent.

Script Kiddies are people who download and use tools and scripts that are already made usually for malicious intent and casue damage with them often because they lack the real skill to create the tools themselves.

Anyone can run a script, or download a tool to brute force a password, that does not make you a hacker.

Cracking is illegal hacking.
Ethical hacking or penetration testing is testing the security of a system with legal authority from the systems owner.

So when the media uses terms such as hackers they are generalising without the understanding of the terms or the culture.

A knife can be a tool that creates beauty in the hands of a skilled sculptor or carpenter, if you give it to a thug it can create misery ;-)

as for what it makes you if you have the knowledge to do something...well you are defined by your morals, ethics and more so your actions ! Knowledge does not make a person, what they do with the knowledge defines them

---

### Post by amiacamal on 2011-08-23
> **haqking said:**
> 
A knife can be a tool that creates beauty in the hands of a skilled sculptor or carpenter, if you give it to a thug it can create misery ;-)


Well that sums it up :P

---

### Post by SoFl W on 2011-08-23
> **haqking said:**
> So when the media uses terms such as hackers they are generalising without the understanding of the terms or the culture.

The media reporting on things they don't know about and not researching any topic to get facts and present more information?  ARE YOU MAD?  These people are journalists, they are smarter than everybody... except for politicians.  THEY KNOW BETTER THAN ANYONE!
Always trust what the news and the media tells you without question!

---

### Post by amiacamal on 2011-08-23
> **SoFl W said:**
> The media reporting on things they don't know about and not researching any topic to get facts and present more information?  ARE YOU MAD?  These people are journalists, they are smarter than everybody... except for politicians.  THEY KNOW BETTER THAN ANYONE!
Always trust what the news and the media tells you without question!


D'uh... Well... Just no...

---

### Post by jramshu on 2011-08-23
Skilled hackers and skilled crackers look down on script kiddies (they are also calling them "skiddies.) It's fine to use others tools, that's what they are for, but if you don't know anything and totally rely on others tools, then you are a skiddie. 

All the ones I have been talking to tell me "learn it by typing it, don't rely on others work. Once you get a good understanding then the tools are even more powerful."

So in a round about way I say the answer to your question is yes, if it wasn't for the hackers(aka good guys) then a lot of these vulnerabilities would only be known by the crackers. I would include the skiddies here, but they generally tend to find exploits by accident, or a skilled cracker is their friend. 

Here's a recent example, there was a recent 0 day myBB exploit that was discovered by a couple of hackers. The first thing they did was release it on their forums, within minutes they notified myBB users and developers of the exploit.

---

### Post by amiacamal on 2011-08-23
Well then, considering that this stuff can be used for good or ill, where does one go to learn it, without the hassle of people assuming your intentions are the latter?

---

### Post by Dangertux on 2011-08-23
> **amiacamal said:**
> Well then, considering that this stuff can be used for good or ill, where does one go to learn it, without the hassle of people assuming your intentions are the latter?

A lot of great answers in this thread so far.

Your intentions become clear with your actions, not the level of knowledge you possess. There is nothing wrong with learning about security or even exploitation methods. It is what you use it for that makes the difference.

As far as where would one go to learn, there are lots of places to learn. This is also a question that is asked fairly regularly. The truth is , if you want to be able to exploit something you need to know how it works REALLY. 

Vulnerability research and penetration testing is all in the details. Something you could do is set up a vulnerable system on your own home network and learn to exploit it.  You can either set up a dedicated machine or perhaps run one in a VM. Windows XP SP1/2/3 are always good targets for this. If you prefer Linux there is a distro called metasploitable based off Ubuntu 8.04 that contains a variety of vulnerable services. As far as wireless goes, practice on your own router. Or buy a cheapo 30 dollar wifi router and set it up with WEP or a weak WPA key.  Learn to find buffer overflows in software, learn to develop both exploits and patches for them. Learn how networks function, learn about intrusion detection, as well as various firewalling methods (application and network). 

In case you haven't gotten the key word here it is LEARN, learn everything you can about everything you can. Understanding is the key.

---

### Post by amiacamal on 2011-08-23
> **Dangertux said:**
> 

 set up a vulnerable system on your own home network and learn to exploit it.  

I have an old dell laptop i got from a friend of mine that i was considering using as a backup, but my interest has been piqued now. Enabling a poorly set up remote desktop and hacking myself is prob the best way to learn how easy it is for someone else to do the same :)

The question is where to begin....

---

### Post by haqking on 2011-08-23
> **amiacamal said:**
> I have an old dell laptop i got from a friend of mine that i was considering using as a backup, but my interest has been piqued now. Enabling a poorly set up remote desktop and hacking myself is prob the best way to learn how easy it is for someone else to do the same :)

The question is where to begin....

at the beginning ;)

how long will it take you ? how long is a piece of string...well twice as long as from the middle to one end.

First learn about networking as much as possible. start using packet sniffers and really understanding packets and what they contain.

The wireshark tool and a few books out there about it are very good and help you really understand packets.

Use NMAP and again its book by Fyodor which is excellent, again learning about packets and sniffing.

Then just keep on learning, and when you think you are good enough, think again and keep on learning

---

### Post by amiacamal on 2011-08-23
You Sir know quite a bit about this :) I'v seen wireshark before, we did a small analysis for one of our courses last year, but i didnt really knnow what i was looking at!

---

### Post by haqking on 2011-08-23
> **amiacamal said:**
> You Sir know quite a bit about this :) I'v seen wireshark before, we did a small analysis for one of our courses last year, but i didnt really knnow what i was looking at!


Well there is an easy way to fix that...use it and learn it ;-)

great book here [http://www.wiresharkbook.com/](http://www.wiresharkbook.com/)

but dont concentrate too much on the tool itself but more on what it does.  For which there are many similar tools.

Try them all, that is the point.  find out as much as you can about all that you can, when you try and like on tool, find as many others out there that do the same thing and learn them too but concentrate on what they give you not so much the tool itself.

There is no ending to this stuff, you learn something new everyday, technologies are always changing

But remember there is more to Pen testing and hacking than knowing the structure of a packet...i am merely giving you a starting point, learn all you can about networking before you try curcumventing the security mechanisms of networking

---

### Post by amiacamal on 2011-08-23
The joy of I.T, soon as you understand how something works, someones found a better way of doing it :) I'll give that a look and start from there, start playin around with the old  [edit] i always forget how strict this forums swear filter is... [/edit] laptop too :)

---

### Post by bodhi.zazen on 2011-08-23
Script kiddies is a derogatory term used for crackers. The implication is that these people run automated scripts without the knowledge to leverage any exploit they discover.

The term is used because "experienced sysadmins" feel they are easy to stop.

The fact of the matter is you do not know who is behind any particular script and should not underestimate the damage such crackers can do to your system if they discover an exploitation.

---

### Post by Dangertux on 2011-08-23
Something else of importance to note. 

A pentest and a hack are NOT the same. Besides the obvious legal reasons. I saw a great presentation about this at Black Hat in 2007. I can't honestly remember who gave the presentation, however it was called "The Pen Test is Dead/Long Live the Pen Test". 

Basically, it stated something I heartily agree with, a pen test creates repeatable, documented, and actionable results. A hack is just a workaround.

---

### Post by wacky_sung on 2011-08-24
Generally everyone start off as a script kiddies of being a newbie in the internet security. Once they got the tools onhand is a matter of free choice whether they used it on good or evil.In order to become a internet security expert they always start off as a script kiddies and this is just part of the process of learning curve.:guitar::guitar::guitar::guitar::guitar:

---

### Post by amiacamal on 2011-08-25
I have a feeling my learning will be slow for the next year... Final year of college and all that. But i've decided that once i get a job I'm making a point of buying (and reading) a book on a subject im not great at every month (when i get paid) :)

---

### Post by kunal00731 on 2011-08-25
A very nice thread actually, i have a lot of interest in this area, after looking into all these comments, the obvious answer that i got was: THERE IS NO SHORTCUT, gotta do it myself.Thanks guys.

---

### Post by amiacamal on 2011-08-25
I'v come to the same conclusion :)

---

### Post by cariboo on 2011-08-26
This thread really has nothing to do with Ubuntu security. Moved to the Cafe.

---

### Post by amiacamal on 2011-08-26
It was supposed to, but drifted away from it somehow...  :)

---

### Post by ninjaaron on 2011-08-26
> **jramshu said:**
> Skilled hackers and skilled crackers look down on script kiddies (they are also calling them "skiddies.) It's fine to use others tools, that's what they are for, but if you don't know anything and totally rely on others tools, then you are a skiddie.

I'm a kernel kiddie.  I rely on the Linux kernel, and I have no real knowledge how it works.

Linus looks down on me. :cry:

---

### Post by cgroza on 2011-08-26
> **ninjaaron said:**
> I'm a kernel kiddie.  I rely on the Linux kernel, and I have no real knowledge how it works.

Linus looks down on me. :cry:
The analogy does not really apply. Those are wanna be cracker/hacker, while you are just a normal OS user.

---

### Post by ninjaaron on 2011-08-26
> **cgroza said:**
> The analogy does not really apply. Those are wanna be cracker/hacker, while you are just a normal OS user.

I'm a hacker according to definition #1 on the [Jargon File]("http://www.cosman246.com/jargon.html#hacker"), and I also use scripts (my scripts) to retrieve data from websites in ways other than the authors intended, though I have never tried to break into a server or directly access forbidden directories (well, I have tried to access forbidden directories, but they told they were forbidden and that was the end of that).

But I've no interest in hacking security or the kernel.

I'm also a browser kiddie!  I don't know how Gecko works!  The Mozilla team looks down on me!

---

### Post by dniMretsaM on 2011-08-26
This is a pretty interesting topic. Definitely a good read. I read an article one time (it was a while ago, before I started using Ubuntu) that opened my eyes, so to speak. It went over the difference between a hacker and a cracker. It was very good and it made me appreciate the fact that people with knowledge that COULD be used for bad (those with great understanding of networks, packets, encryption etc.) aren't always the "mad scientist" sitting in a dark basement looking for a new way to hack into their ex-girlfriend's Facebook. It also pointed out how the media and the general public always grouped crackers and hackers into the same group (which a lot of ethical hackers consider insulting). Now when I hear someone say "hacker" (in a derogatory sense) I kind of cringe.

---

### Post by amiacamal on 2011-09-05
> **dniMretsaM said:**
> Now when I hear someone say "hacker" (in a derogatory sense) I kind of cringe.

Haha, I do this too :) I think i may have read the same article,  It was also where I first saw the hackers emblem.  It's oddly fun enlightening people of the difference between hackers and crackers :)

---

### Post by haqking on 2011-09-05
This thread and script kiddies have something in common, should be put to sleep ;-)

---

### Post by Triblaze on 2011-09-05
Are script kiddies bad? Well, I guess more than good or bad, they are just uneducated in hacking/cracking, and rely on complex tools to do the stuff they don't understand.

Whether they're good or bad depends on what they use these for.
Although the definition of skiddie is pretty much those that use them for malicious intent, so I guess they are bad, but this thread has seemed to veer a bit into those that use scripts without understanding them, whether for good or bad.

Sometimes it's a learning thing. If someone just uses these scripts with no intention of realizing why they work or how they work, then that's not very good in terms of learning. But sometimes that's where you have to start. I got some packet analyzers and sniffers and stuff, and I have no idea really how networking works, but by poking around my router and local computers, I'm slowly learning, and it's helping me understand it more. It's interactive. Instead of just reading about it, I get to see all the packets and protocols and ports and stuff in action, and when I come across something I don't understand, I look it up and see how it works. I guess I'm similar to a skiddie in that I didn't write it or learn how it works before I started using it, but I don't have any malicious intent, I just use it as a more interactive learning tool. And I'm still pretty clueless, but lately I've learned a lot more than I knew a few weeks ago.

Even though using them to learn isn't really under the definition of skiddie, it's been brought up in the thread before, so that's just my two cents.

---

### Post by dniMretsaM on 2011-09-05
Found the article I was talking about: [http://www.techrepublic.com/blog/security/hacker-vs-cracker/1400](http://www.techrepublic.com/blog/security/hacker-vs-cracker/1400)

---

