---
title: "Home Network Secure from Others on Network"
date: 2011-05-20
forum: The Cafe
---

### Post by NertSkull on 2011-05-20
So, this is kind of a support question, but not necessarily linux related, but maybe could be.  So I figured the cafe would be the best place.

A friend of mine got interested in, and started using ubuntu a couple years ago (partly from seeing it on my computer).  He's not super computer literate, but gets by ok.

Anyway, so he came to me with this question and I don't know nearly enough about networking to answer it.

He's got a sister her family that is going to be moving in with him temporarily (at least supposedly short term). Apparantly her husband is supposed to be pretty good with computers.

So, he's (slightly) annoyed with the situation, but in particular wants to make sure they have zero access to his computer/internet traffic.  They'll be sharing on his home network with their computer/laptop.  

Anyway, I didn't really know what to tell him other than make sure you don't have samba on (they'll be windows people he said) don't leave ports open, and similar types of things.

So I thought I'd ask here.  Is there anything I can tell him to do to make sure they aren't fiddling with his computer, sniffing his network that he's using, etc.

I know it sounds a little paranoid, but he probably is.  So any advice on how to secure between computers on a home network?  I figure this would be a good learning curve for me as well as network stuff is still pretty beyond me.

---

### Post by Bandit on 2011-05-20
Assign the network a login password. Something that they will not guess.
Also if hes on a wireless, turn off beaconing and apply a wireless password as well. With beaconing turned off on the wireless they will not even be able to see the network from their computers. Also most routers will even let you encrypt your network traffic between your computer and the router. 

Make sure you use strong passwords. Not BILL123...

---

### Post by Thewhistlingwind on 2011-05-20
Thankfully, Linux's incompatibility with windows works to his advantage here. Encrypt your wifi, relatives or not, don't open samba shares, and this guys untouchable AFAIK.

---

### Post by grahammechanical on 2011-05-20
I must be missing something here. The post said this:

>  They'll be sharing on his home network with their computer/laptop.  

I thought that the issue was if they had access to the network, this is the modem/router, would they be able to access his computer or his Internet trafffic?

I do not think so, but that is not a good answer.

Regards.

---

### Post by NertSkull on 2011-05-20
Yeah, I think they will have access to the home network.  I believe he told me he'll be giving them the password to his network which (I believe since I helped him set it up) is WPA2 encrypted.

So its not trying to keep them off his network.  But how to keep his computer and internet activity isolated from others using his same network.

As I've been reading, it seems that really its wifi thats the most insecure.  He has a desktop that is hooked straight to the router. From what I can tell, that is a lot more secure and harder to "sniff" network traffic than connecting via wireless.

Is that true?  If he is connected by ethernet cable does he effectively have nothing to worry about?

---

### Post by Thewhistlingwind on 2011-05-20
> **grahammechanical said:**
> I must be missing something here. The post said this:



I thought that the issue was if they had access to the network, this is the modem/router, would they be able to access his computer or his Internet trafffic?

I do not think so, but that is not a good answer.

Regards.

Your not missing a thing, I however, did. That is a much more complicated question, because someone ON your network is usually whats called being "compromised". 

I'm not sure about the specifics, but I would guess that your only option would be some form of tunneling? (The files on his disk are still fine.)

---

### Post by Sef on 2011-05-20
> With beaconing turned off on the wireless they will not even be able to see the network from their computers. 

With the right software, one can still get ahold of the SSID number.

---

### Post by Dustin2128 on 2011-05-20
Split it into two networks temporarily maybe? What exactly are you trying to do? What do you mean no access to computer/internet traffic? But one thing: they're relatives; everyone here is talking about them like they're a family of black hats moving in. In my experience though, people who think they're computer people rarely are- they're just people who happen to use computers a lot without neccisarily knowing what they're doing.

---

