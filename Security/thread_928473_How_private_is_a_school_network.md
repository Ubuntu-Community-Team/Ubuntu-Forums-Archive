---
title: "How private is a school network?"
date: 2008-09-24
forum: Security
---

### Post by ucal on 2008-09-24
I am currently using ResNet provided to me by the UW Madison. My concern is privacy. I haven't been able to find a privacy policy dealing with how my information is treated, so I would like to take it into my own hands so to speak, and enforce privacy.  How private are networks like these, and is there anything I can do to increase privacy?

---

### Post by The Tronyx on 2008-09-24
To increase privacy you might want to look into a nifty little application called ptunnel depending on what it is you want to do.  If you want to encrypt all of your traffic you could also piggy back off of a SOCKS 5 proxy via an established SSH connection.  Generally whenever I am on anyone's network other than my own, I assume I have no privacy whatsoever. 

This may be of some use to you [http://muffinresearch.co.uk/archives/2007/01/19/ssh-socks-proxy/](http://muffinresearch.co.uk/archives/2007/01/19/ssh-socks-proxy/)

---

### Post by cdenley on 2008-09-24
> **ucal said:**
> I am currently using ResNet provided to me by the UW Madison. My concern is privacy. I haven't been able to find a privacy policy dealing with how my information is treated, so I would like to take it into my own hands so to speak, and enforce privacy.  How private are networks like these, and is there anything I can do to increase privacy?

Are you concerned about privacy from the university, or your neighbors? Dorm networks are usually switched, which means they rely on the ARP protocol, which is sort of like using the honor system to determine where your traffic should go. Basically, any of your neighbors can very easily perform a man-in-the-middle attack and inspect your unencrypted network traffic without you realizing it. They can also inject their own SSL certificate into SSL sessions, so they can decrypt it. If firefox warns you about an SSL certificate, don't "make an exception".

As far as your school, it varies from one to another. When I was in school, my biggest concern was getting into trouble for piracy (I love movies). Some schools will hand over student information to RIAA/MPAA people with little trouble, but mine wouldn't unless they were legally obligated.

What aspect of privacy are you concerned about?

---

### Post by ucal on 2008-09-24
> **cdenley said:**
> Are you concerned about privacy from the university, or your neighbors? Dorm networks are usually switched, which means they rely on the ARP protocol, which is sort of like using the honor system to determine where your traffic should go. Basically, any of your neighbors can very easily perform a man-in-the-middle attack and inspect your unencrypted network traffic without you realizing it. They can also inject their own SSL certificate into SSL sessions, so they can decrypt it. If firefox warns you about an SSL certificate, don't "make an exception".

As far as your school, it varies from one to another. When I was in school, my biggest concern was getting into trouble for piracy (I love movies). Some schools will hand over student information to RIAA/MPAA people with little trouble, but mine wouldn't unless they were legally obligated.

What aspect of privacy are you concerned about?

I'm concerned about both the school, and the people around me.  My floor is occupied by some very nifty computer science majors, so they definitely have the capability to do something like that (though I wouldn't think they would, it has demonstrated just how computer literate everyone is here).  

As for the school, I can't find any policy that describes how they use the information they collect, so I don't trust them automatically.  I'm not worried about the RIAA showing up at my door because I don't pirate stuff anymore.  I am however paranoid.  

[QUOTE=2point0]To increase privacy you might want to look into a nifty little application called ptunnel depending on what it is you want to do. If you want to encrypt all of your traffic you could also piggy back off of a SOCKS 5 proxy via an established SSH connection. Generally whenever I am on anyone's network other than my own, I assume I have no privacy whatsoever.

This may be of some use to you [http://muffinresearch.co.uk/archives...h-socks-proxy/](http://muffinresearch.co.uk/archives...h-socks-proxy/)[/QUOTE]

Seems nice. I'll have to try it out, but will it help me remain private from my school?

---

### Post by ucal on 2008-09-25
I found a program called Tor.  Its an Onion encryption.  This should keep my information secure right?

---

### Post by cdenley on 2008-09-25
> **ucal said:**
> I found a program called Tor.  Its an Onion encryption.  This should keep my information secure right?

It will keep your information secure from your neighbors and your school. It will not make your information secure from the tor exit node (or anyone between the exit node and the destination server), only the source of the information. The easiest way to capture passwords is to make yourself a proxy server or tor node. Then people send you their web traffic willingly, and sometimes don't even encrypt it!

Also, if someone happens to have access to both your initial tor node and your exit node, they will be able to not only see your traffic, but also determine where it is coming from.

Tor also makes your network connections much slower, especially if you're used to a dorm network. I think the best thing you could do is to not send any sensitive data unless it is encrypted with a verified SSL certificate. If firefox gives you a warning about an SSL certificate, it couldn't verify that the intended server is the one you are actually connected with.

---

### Post by ucal on 2008-09-25
> **cdenley said:**
> It will keep your information secure from your neighbors and your school. It will not make your information secure from the tor exit node (or anyone between the exit node and the destination server), only the source of the information. The easiest way to capture passwords is to make yourself a proxy server or tor node. Then people send you their web traffic willingly, and sometimes don't even encrypt it!

Also, if someone happens to have access to both your initial tor node and your exit node, they will be able to not only see your traffic, but also determine where it is coming from.

Tor also makes your network connections much slower, especially if you're used to a dorm network. I think the best thing you could do is to not send any sensitive data unless it is encrypted with a verified SSL certificate. If firefox gives you a warning about an SSL certificate, it couldn't verify that the intended server is the one you are actually connected with.

So it deals with the school problem but adds the potential for an unknown person to know my info?  I'll stay away from unencrypted sites that ask for passwords for a while then.  I'm actually planning to set up an SSH server at my house.

---

### Post by cdenley on 2008-09-25
> **ucal said:**
> So it deals with the school problem but adds the potential for an unknown person to know my info?  I'll stay away from unencrypted sites that ask for passwords for a while then.  I'm actually planning to set up an SSH server at my house.

No matter how you tunnel or redirect your traffic, it will always need to reach it's destination in a way the server would understand. If you're connecting to a server which doesn't use encryption, then the unencrypted data will have to be sent to the server over the internet at some point.

---

