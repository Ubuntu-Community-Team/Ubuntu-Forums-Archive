---
title: "Tor"
date: 2011-10-22
forum: The Cafe
---

### Post by mmsmc on 2011-10-22
is anybody here a user of TOR?

---

### Post by Gremlinzzz on 2011-10-22
Not me, i don't believe there can be Online Anonymity using a home computer:popcorn:

---

### Post by donkyhotay on 2011-10-22
It's been shown that you *can* be traced even using tor. Admittedly it's extremely difficult and requires government/military level resources to do. Even then they generally won't unless there is a very good reason because of the cost. I tried it once, just to do so, but it's so slow I wouldn't use it unless I was protesting strongly against a government known for human rights violations. Even then I would assume I am being watched and that my protest was worth the potential repercussions.

---

### Post by mmsmc on 2011-10-22
is it worth just having, meaning should i download it even though i may never use it?

---

### Post by benc1213 on 2011-10-22
I haven't used it (yet). I am tempted to though.

---

### Post by mmsmc on 2011-10-22
and this is purely speaking that nothing illegal is happening, but i like to do penetration testing on my own servers, computers and so on, and just recently found out about this, just would like some 2nd opinions before i download

---

### Post by Dangertux on 2011-10-22
> **mmsmc said:**
> and this is purely speaking that nothing illegal is happening, but i like to do penetration testing on my own servers, computers and so on, and just recently found out about this, just would like some 2nd opinions before i download

If what you're pen testing is yours you shouldn't need Tor. It really has nothing to do with pen testing anyway. 

Tor has never done more than obfuscating the beginning and endpoint for a packet. It does a decent job at it, though it's a lot more easy to track Tor traffic then the previous posts have eluded to. 

Keeping in mind if you're using it for something like (in the pentesting case) sqlmap your dns lookups are going to be done without Tor, so you can still make the association. 

In my opinion if you have nothing to hide there is no reason to hide. That being said end point router's in the tor network have pretty much unrestricted access to whatever you're sending through them.

Hope that helps.

---

### Post by mmsmc on 2011-10-22
hey guys, thanks for the feed back, it was really helpful

---

### Post by haqking on 2011-10-22
> **mmsmc said:**
> is it worth just having, meaning should i download it even though i may never use it?

why would you download something you would never use ?

and as mentioned it has nothing to do with Pen testing.

if you want to download something useful for Pen testing try here 

[http://www.isecom.org/osstmm/](http://www.isecom.org/osstmm/) ;-)

---

### Post by mmsmc on 2011-10-22
> **haqking said:**
> why would you download something you would never use ?

and as mentioned it has nothing to do with Pen testing.

if you want to download something useful for Pen testing try here 

[http://www.isecom.org/osstmm/](http://www.isecom.org/osstmm/) ;-)
cool, thanks ill check it out

---

### Post by ki4jgt on 2011-10-23
> **mmsmc said:**
> is it worth just having, meaning should i download it even though i may never use it?

I use Tor (on my laptop) for accessing sites which have been blocked in government buildings (Schools, Archive Buildings, hospitals). For some reason, most of them have horrible banning filters. My Uncle couldn't even access a website about the history of trees in a public hospital's wifi network. The last I checked, looking at trees wasn't a crime. Tor just helps when people put up filters instead of blocking sites for their content, they choose to use keywords. I honestly can tell you two words that are on EVERY adult site that wouldn't block ANY other sites. Until people start choosing their keywords more carefully though, you better believe I'm going to install Tor on every OS I install.

WTTW: In case you didn't know already, just be careful with what you type in. The network is fully encrypted inside, but when your data reaches the exit node (The user connecting you to your website) the exit node must decrypt your data before sending it to the site and they can see everything.

---

### Post by mmsmc on 2011-10-23
> **ki4jgt said:**
> I use Tor (on my laptop) for accessing sites which have been blocked in government buildings (Schools, Archive Buildings, hospitals). For some reason, most of them have horrible banning filters. My Uncle couldn't even access a website about the history of trees in a public hospital's wifi network. The last I checked, looking at trees wasn't a crime. Tor just helps when people put up filters instead of blocking sites for their content, they choose to use keywords. I honestly can tell you two words that are on EVERY adult site that wouldn't block ANY other sites. Until people start choosing their keywords more carefully though, you better believe I'm going to install Tor on every OS I install.

WTTW: In case you didn't know already, just be careful with what you type in. The network is fully encrypted inside, but when your data reaches the exit node (The user connecting you to your website) the exit node must decrypt your data before sending it to the site and they can see everything.
of course, i read that the tor browser helps conceal some of that info, but not all off it, i also believe that full online anonymity cannot be achieved, but im also looking for software that can help conceal that info, or ill just try to make my own

thanks for the info

---

### Post by ki4jgt on 2011-10-23
You could try creating your own exit node. Setup a Tor .onion address and run a VPN/proxy through it. That would ensure that only you were decrypting the information before it reached it's destination. You'd lose the anonymity, but you'd be using basically a personal VPN that has all the advantages of Tor Hard to block (because the network doesn't come from just one place), full wifi encryption (which is also provided by any adequate VPN protocol).

Also, since every node in the Tor network is a relay node, you would be contributing to the network just by having the software running. So you wouldn't have to feel bad about using it as a VPN.

---

### Post by mmsmc on 2011-10-23
> **ki4jgt said:**
> You could try creating your own exit node. Setup a Tor .onion address and run a VPN/proxy through it. That would ensure that only you were decrypting the information before it reached it's destination. You'd lose the anonymity, but you'd be using basically a personal VPN that has all the advantages of Tor Hard to block (because the network doesn't come from just one place), full wifi encryption (which is also provided by any adequate VPN protocol).

Also, since every node in the Tor network is a relay node, you would be contributing to the network just by having the software running. So you wouldn't have to feel bad about using it as a VPN.
thanks, i think i found a new project to work on

---

### Post by ki4jgt on 2011-10-23
> **mmsmc said:**
> thanks, i think i found a new project to work on

No prob. Good Luck.

---

