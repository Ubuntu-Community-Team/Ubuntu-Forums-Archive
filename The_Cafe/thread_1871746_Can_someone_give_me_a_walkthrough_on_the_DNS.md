---
title: "Can someone give me a walkthrough on the DNS"
date: 2011-10-29
forum: The Cafe
---

### Post by ki4jgt on 2011-10-29
Hi guys, I'm looking for a tutorial on DNS that would meet these specifications.

If the entire world went post nuclear war and there were only 200 computers (average every day computers not servers) on the Earth which all wanted to establish another Internet, is there a tutorial I could follow to allow those computers to setup domains for themselves and also code a working DNS protocol? I'm not allowed to look at anything except this tutorial. No program code, no other programs are installed besides what's on an average every day computer. How would someone go about coding a DNS for this network?

---

### Post by SeijiSensei on 2011-10-29
This sounds like [homework]("http://ubuntuforums.org/index.php?page=policy").

Nevertheless, the standard resource is the "Requests for Comments," or RFCs, maintained by the Internet Engineering Task Force.  All the aspects of the protocols are described in full.  I'd start with [1034]("https://www1.ietf.org/rfc/rfc1034.txt") and [1035]("https://www1.ietf.org/rfc/rfc1035.txt").

---

### Post by Tibuda on 2011-10-29
In a post nuclear war world, you better worry about food and radiation than compuer networks.

---

### Post by del_diablo on 2011-10-29
The real question is: "Has somebody managed to rip a complete copy of the English wikipedia before everything was destroyed?"

---

### Post by CharlesA on 2011-10-29
> **del_diablo said:**
> The real question is: "Has somebody managed to rip a complete copy of the English wikipedia before everything was destroyed?"
Haha, so true.

@OP: This wouldn't happen to be related to your router thread from the other day, would it?

---

### Post by ki4jgt on 2011-10-29
> **SeijiSensei said:**
> This sounds like [homework]("http://ubuntuforums.org/index.php?page=policy").

Nevertheless, the standard resource is the "Requests for Comments," or RFCs, maintained by the Internet Engineering Task Force.  All the aspects of the protocols are described in full.  I'd start with [1034]("https://www1.ietf.org/rfc/rfc1034.txt") and [1035]("https://www1.ietf.org/rfc/rfc1035.txt").

It's not homework, but I'm interested (intrigued by) it enough to want to attempt a replication. I've read soo many documents on it already about the header, oppcode, res1, res2, and that's about as far as I get. I didn't really want the FRCs anymore. In truth, I'm tired of the RFCs and was wondering if someone could play tutor :-( LOL.

I'm wanting to do an open p2p DNS system. I'm basically wanting to skip all the codes and just get to the here's my URL, give me my IP. I know all the codes are what makes it work, but it's about to drive me insane.

EDIT: Sorry mispelled that RFCs.

---

### Post by ki4jgt on 2011-10-29
> **CharlesA said:**
> Haha, so true.

@OP: This wouldn't happen to be related to your router thread from the other day, would it?

sort of.

---

### Post by CharlesA on 2011-10-29
> **ki4jgt said:**
> sort of.
;)

Take a look here:
[http://www.howstuffworks.com/dns.htm](http://www.howstuffworks.com/dns.htm)

It might be a bit simplified, but it'll give you the basics.

---

### Post by ki4jgt on 2011-10-29
> **CharlesA said:**
> ;)

Take a look here:
[http://www.howstuffworks.com/dns.htm](http://www.howstuffworks.com/dns.htm)

It might be a bit simplified, but it'll give you the basics.

I know all this. I'm morely asking are there a general set of questions and responses given which would cover the system until I could read more into what all the codes and such mean. I know what it does, I just don't know how it works. I know it's not magic, I just want to know the protocol shortcuts without having to spend forever learning the protocol just to finally use the fundamentals. I guess what I'm asking for, is some hands on experience with it.

---

### Post by CharlesA on 2011-10-29
> **ki4jgt said:**
> I know all this. I'm morely asking are there a general set of questions and responses given which would cover the system until I could read more into what all the codes and such mean. I know what it does, I just don't know how it works. I know it's not magic, I just want to know the protocol shortcuts without having to spend forever learning the protocol just to finally use the fundamentals. I guess what I'm asking for, is some hands on experience with it.
Throw BIND on a VM and play around with it.

---

### Post by haqking on 2011-10-29
> **CharlesA said:**
> Throw BIND on a VM and play around with it.

+1

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

Set it up and go crazy !

Also i recommend DNS & BIND by Cricket Liu, it is like the printed version of Tylenol PM ;-)

---

### Post by Dangertux on 2011-10-29
I'm just not sure what it is you want. You want to create something, highly technical that requires a lot of things going on. However, you don't want to read technical documents. I'm not sure you will be able to accomplish your goal of "creating" this network you want if you can't even deal with a little bit of documentation beforehand.

---

### Post by ki4jgt on 2011-10-29
> **Dangertux said:**
> I'm just not sure what it is you want. You want to create something, highly technical that requires a lot of things going on. However, you don't want to read technical documents. I'm not sure you will be able to accomplish your goal of "creating" this network you want if you can't even deal with a little bit of documentation beforehand.

It's not that I can't. It's just that, I've been reading documents all my life. I've been interpreting what this means to this person, what that means to that person, and in return they've all taken my advice and then went off with their own things. That was all fine and dandy but, I was left to clean up the mess of what ever they started. I was left to fix what ever they broke after they got finished doing what ever they wanted. I was the one left doing it, b/c I was the only one who knew how. (I read it somewhere, or figured it out in my head) While they were out with friends or having a life, I was fixing their mess. Now, when I try learn something new, my brain remembers that and as a defense mechanism of being tired of all the years of doing it, I get a migraine when I start to read something in-depth. I get tired, frustrated, angry and just plain hateful. That, plus the fact that I usually can relate to what I'm reading. In HS, I passed all my classes while sleeping through them, (I could see how the equations and sentences and other things formed in my head.) My teacher made me redo my work several times in a certain math class, because I did it in my head and they couldn't see my work. I did it in my head because I could apply the math to real life. I could see how fractions were added in real life and wasn't just seeing numbers. I could see how the algebra worked. While I did this, everyone else was out having a social life, doing the do, and whatever else people do and I was cleaning up messes (because they didn't know how). Every college has rejected me (not because I'm not accepted, but because I can't afford it). The gov won't allow me to take out a loan until I'm 25 and can declare myself independent from my paranoid dad. So, I've decided that the best way for me to enjoy life, is to play the ignorant card just like everyone else, while at the same time still wanting to hang the moon in the process. :-(. I don't like the RFCs (not because I can't see how they're working, but b/c it's one big code after another, even though the process could be repeated by using custom codes, it would be incompatible and I can't actually force myself to read anything anymore b/c I'll get a migraine :-(. That's why I was asking for hands on experience, something I could relate the codes to.

---

### Post by haqking on 2011-10-29
> **ki4jgt said:**
> It's not that I can't. It's just that, I've been reading documents all my life. I've been interpreting what this means to this person, what that means to that person, and in return they've all taken my advice and then went off with their own things. That was all fine and dandy but, I was left to clean up the mess of what ever they started. I was left to fix what ever they broke after they got finished doing what ever they wanted. I was the one left doing it, b/c I was the only one who knew how. (I read it somewhere, or figured it out in my head) While they were out with friends or having a life, I was fixing their mess. Now, when I try learn something new, my brain remembers that and as a defense mechanism of being tired of all the years of doing it, I get a migraine when I start to read something in-depth. I get tired, frustrated, angry and just plain hateful. That, plus the fact that I usually can relate to what I'm reading. In HS, I passed all my classes while sleeping through them, (I could see how the equations and sentences and other things formed in my head.) My teacher made me redo my work several times in a certain math class, because I did it in my head and they couldn't see my work. I did it in my head because I could apply the math to real life. I could see how fractions were added in real life and wasn't just seeing numbers. I could see how the algebra worked. While I did this, everyone else was out having a social life, doing the do, and whatever else people do and I was cleaning up messes (because they didn't know how). Every college has rejected me (not because I'm not accepted, but because I can't afford it). The gov won't allow me to take out a loan until I'm 25 and can declare myself independent from my paranoid dad. So, I've decided that the best way for me to enjoy life, is to play the ignorant card just like everyone else, while at the same time still wanting to hang the moon in the process. :-(. I don't like the RFCs (not because I can't see how they're working, but b/c it's one big code after another, even though the process could be repeated by using custom codes, it would be incompatible and I can't actually force myself to read anything anymore b/c I'll get a migraine :-(. That's why I was asking for hands on experience, something I could relate the codes to.

WOW

anyways as mentioned above, install it and use it.

If you dont want to read or use what others say then why ask ? ;-)

Install, play and configure and troubleshoot.

Happy DNS

---

### Post by koenn on 2011-10-29
> **Dangertux said:**
> I'm just not sure what it is you want. You want to create something, highly technical that requires a lot of things going on. However, you don't want to read technical documents. I'm not sure you will be able to accomplish your goal of "creating" this network you want if you can't even deal with a little bit of documentation beforehand.

+1

it's all "I want to build this from scratch, but I don't know the first thing about it, somebody bring me the cliffsnotes (I don't want to get them myself)"

---

### Post by Dangertux on 2011-10-29
Okay, I second the set up a nameserver yourself, it will give you the "hands on" experience you're looking for.

As for the rest of OP's last reply, that's a lot to process for a saturday afternoon. Maybe you should take a break from the computer for a bit? Just a thought...

Hope all works out

---

### Post by koenn on 2011-10-29
KoennsNotes on how to build a name resolving system

- database to store addresses and hostnames
- you need a "client" that can request, over a network,  addresses from the database for a given hostname
- you need a "server" to accept such requests, look up the addresses in its database, and return them to the "client"

- you need to make a design decision on whether you want that database centralized or distributed, and you need a mechanism for updating the database, of for exchange of info between decentralized parts of it, or to redirect requests to another server that has information the 1st server can't supply - things to that effect.

- you may want some additional mechanism to deal with discrepancies and inconsistencies (duplicate names, duplicate addresses, same address belonging to multiple machines, ...), but that's not really required in version 0.1 - just something to be aware of so you can easily add it later.

there, done. 
All it takes now is coding it.

---

### Post by ki4jgt on 2011-10-29
Sorry guys. I'm just tired. I was always taught to shoot for the stars and that by some miracle, you would get to where you were going. I've shot for the stars my whole life and I haven't reached a single one. Mean while, I see all these other people who have shot for nothing getting from star to star by catching a ride here and catching a ride there. While I've been as nice as they have to everyone else, I'm quiet about my business (or I used to be before I started whining about everything) and thus no one trusts me enough to offer me a ride from star to star like the people who didn't shoot for anything and somehow get everything. All in all, It's just been a VERY long day and it's just 1:30 :-(.

---

### Post by ikt on 2011-10-29
> **ki4jgt said:**
> Sorry guys. I'm just tired. I was always taught to shoot for the stars **and that by some miracle**, you would get to where you were going.

What? Whoever told you that was wrong.

Shoot for the stars and be prepared to work all day every day until you reach the stars, then be prepared to continue to work all day every day to keep your spot.

---

### Post by ki4jgt on 2011-10-29
> **ikt said:**
> What? Whoever told you that was wrong.

Shoot for the stars and be prepared to work all day every day until you get reach the stars, then be prepared to continue to work all day every day to keep your spot.

yeah well that was the inferred meaning. The fuel tank would have to provide the work and the ship would always have to be manned by working crew members.

---

### Post by Dangertux on 2011-10-29
> **ki4jgt said:**
> Sorry guys. I'm just tired. I was always taught to shoot for the stars and that by some miracle, you would get to where you were going. I've shot for the stars my whole life and I haven't reached a single one. Mean while, I see all these other people who have shot for nothing getting from star to star by catching a ride here and catching a ride there. While I've been as nice as they have to everyone else, I'm quiet about my business (or I used to be before I started whining about everything) and thus no one trusts me enough to offer me a ride from star to star like the people who didn't shoot for anything and somehow get everything. All in all, It's just been a VERY long day and it's just 1:30 :-(.

Hopefully this will give you some inspiration :-)

> 
Go to the people. Live with them. Learn from them. Love them. Start with what they know. Build with what they have. But with the best leaders, when the work is done, the task accomplished, the people will say "We have done this ourselves".

**~Lao Tzu**


---

### Post by KiwiNZ on 2011-10-29
@ ki4jgt

You seem to jumping from idea to idea and only spending a very short time on any one. Have you heard the idiom too many cooks spoil the broth? well too many broths confuse and spoil the cook. You need to decide your target, plan carefully how to get there and set target points . If your only target point is your final goal you will fail as you have little micro successes only the way.

You alo need to be single minded in your endeavours to reach you goal. There are no easy rides, there are seldom simple cures.

Listen to mentors and exclude the nay sayers. 

Be always prepared to alter your time frames to take into account the obstacles you meet on the way but always reaffirm your new path to your goal.

---

### Post by ki4jgt on 2011-10-29
> **KiwiNZ said:**
> @ ki4jgt

You seem to jumping from idea to idea and only spending a very short time on any one. Have you heard the idiom too many cooks spoil the broth? well too many broths confuse and spoil the cook. You need to decide your target, plan carefully how to get there and set target points . If your only target point is your final goal you will fail as you have little micro successes only the way.

You alo need to be single minded in your endeavours to reach you goal. There are no easy rides, there are seldom simple cures.

Listen to mentors and exclude the nay sayers. 

Be always prepared to alter your time frames to take into account the obstacles you meet on the way but always reaffirm your new path to your goal.

Thanks, I'm in for the ride like everyone else, and though it feels like I'm alone sometimes, I have to remember that the human experience is mutual to everyone. It's a part of growing up.
Also, thanks for the Lao Tzu quote Dangertux. Haven't read any of his works in a while. I used to love one which was basically worded as "a name achieves power, but the nameless receive fear. What is the difference?"

---

### Post by mips on 2011-10-29
[http://www.zoneedit.com/doc/rfc/](http://www.zoneedit.com/doc/rfc/)
[http://www.bind9.net/rfc](http://www.bind9.net/rfc)

Should keep you busy for a while.

---

### Post by madhi19 on 2011-10-29
After a nuke war provided that the radiation did not kill you am guess building a network of computers will be the least of your worry. With a bit of lowtech engineering your desktop could be retrofitted into a great rat trap.

---

### Post by krapp on 2011-10-29
> **ki4jgt said:**
> It's not that I can't. It's just that, I've been reading documents all my life. I've been interpreting what this means to this person, what that means to that person, and in return they've all taken my advice and then went off with their own things. That was all fine and dandy but, I was left to clean up the mess of what ever they started. I was left to fix what ever they broke after they got finished doing what ever they wanted. I was the one left doing it, b/c I was the only one who knew how. (I read it somewhere, or figured it out in my head) While they were out with friends or having a life, I was fixing their mess. Now, when I try learn something new, my brain remembers that and as a defense mechanism of being tired of all the years of doing it, I get a migraine when I start to read something in-depth. I get tired, frustrated, angry and just plain hateful. That, plus the fact that I usually can relate to what I'm reading. In HS, I passed all my classes while sleeping through them, (I could see how the equations and sentences and other things formed in my head.) My teacher made me redo my work several times in a certain math class, because I did it in my head and they couldn't see my work. I did it in my head because I could apply the math to real life. I could see how fractions were added in real life and wasn't just seeing numbers. I could see how the algebra worked. While I did this, everyone else was out having a social life, doing the do, and whatever else people do and I was cleaning up messes (because they didn't know how). Every college has rejected me (not because I'm not accepted, but because I can't afford it). The gov won't allow me to take out a loan until I'm 25 and can declare myself independent from my paranoid dad. So, I've decided that the best way for me to enjoy life, is to play the ignorant card just like everyone else, while at the same time still wanting to hang the moon in the process. :-(. I don't like the RFCs (not because I can't see how they're working, but b/c it's one big code after another, even though the process could be repeated by using custom codes, it would be incompatible and I can't actually force myself to read anything anymore b/c I'll get a migraine :-(. That's why I was asking for hands on experience, something I could relate the codes to.

Hey man one step at a time. You're young and you got your whole life ahead of you, and you still have time for college and to get into the job market or what's left of it! You've obviously got smarts, just work with the talents you got, not against them.

---

### Post by ikt on 2011-10-29
> **madhi19 said:**
> After a nuke war provided that the radiation did not kill you am guess building a network of computers will be the least of your worry. With a bit of lowtech engineering your desktop could be retrofitted into a great rat trap.

The problem I had with even 200 computers being around would mean that most of the technology would still be there, we'd simply scrape what was already implemented and build up from there.

---

### Post by ki4jgt on 2011-11-14
My work has been cut out for me and lined with pretty red roses LOL. DLink is/has released/ing a router which uses WIMAX to "allow smaller companies the opportunity to offer customers the same service as larger ones with the same quality only without the wired connections."

According to what I've read, WIMAX networks can be up to 3000 miles with one access point and provides speeds similar to a wired connection. Dlink has limited this to 5/8 miles but hey, that pretty much does what I've stated. It also has a built in Wireless G hotspot so wifi enabled computers can use it.

---

