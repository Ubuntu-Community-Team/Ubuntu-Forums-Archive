---
title: "How much coding is involved in networking?"
date: 2010-05-25
forum: The Cafe
---

### Post by NMFTM on 2010-05-25
I'm going to school to learn about networking and hope to maybe eventually specialize in network security. Because I find cat and mouse of game about how things can be exploited and in turn prevented from being exploited very interesting.

But, I've always been terrible at math and I don't like coding at all. Even though I'm not very good at it, it's not too terrible once I really get into it. So far I've only done a little PHP and Visual Basic and only very basic things in each. But the problem is that most of the time I can't seem to find the will to sit down and figure out the solution to a problem and how to implement it and it takes me awhile to actually get into it.

I find setting things up and tinkering around with settings to be a lot more fun than creating things from scratch. I find that whenever I'm supposed to be coding an assignment I'll instead find something on my OS that doesn't work quite the way I want it to and spend most of the time that I'm trying to code thinking about how I'd rather be reading howto's and forum posts about how to modify it. But by the time I finish up coding my assignment I've kind of had the metaphorical life sucked out of me and don't feel like really doing anything productive. I've also found that I like thinking about the theoretical aspect about how different things interact with each other just as much, if not more fun and exciting than actually putting the theory into practice.

I know that shell scripting (like Bash and Powershell) is required for networking. But from what I've seen, that's more like just automating tasks than actually building applications, which I can live with. Because it's basically just taking simple commands and modifying the syntax into doing more intensive things to save yourself from writing out tons of long commands.

I've also noticed, at least among the students in the school that I go to with a few exceptions. That the students who are really good at coding seem to also be somewhat poor at tinkering around with settings or getting things that I would find easy setup. While the students who are good at networking seem to be exactly the opposite. It seems like programmers are better at focusing on and solving very specific and intricate problems. While networkers (being exactly the opposite) are better at taking a look at the big picture and doing a lot of different things, but not necessarily doing them all extremely well. This is a very broad generalization, but it's just what I've noticed. I hope I didn't offend anyone.

So, in a nutshell. What I'd like to know is, how much coding is actually involved in network administration? I know that the better a networker knows how to code the more valuable he will be in the workplace and the more he'll get paid. But, can you be a successful networker without actually having to really code any applications? If it's something like coding or modifying a web interface in PHP that would take user log in information and store it in a database or match it against logged usernames and passwords I wouldn't find that too painful as long as I didn't have to do it on a weekly basis. But I really don't like to program.

Sorry if I repeated myself or made overuse of run on sentences.

---

### Post by KoRnholio on 2010-05-25
I'm not a network administrator, but I think the most they really do is shell scripting. You should be all set if you're fine with scripting.

---

### Post by 3rdalbum on 2010-05-26
> **NMFTM said:**
> I'm going to school to learn about networking and hope to maybe eventually specialize in network security. Because I find cat and mouse of game about how things can be exploited and in turn prevented from being exploited very interesting.

Here's a tip for you: If you find that you're playing that "cat and mouse game", then your network is not designed properly. If your network is properly segmented, with a firewall and good host security, and each client computer is fairly well locked down with known and trusted programs only, then an attacker would be hard-pressed to get into your network.

---

### Post by Frak on 2010-05-26
Technically, none. You can be a Network Administrator and not know anything about programming. In reality, the ability to program is a very important quality to your employer.

As 3rdalbum said above, a properly designed network keeps itself safe due to the difficulty of accessing the multitudes of hosts on the network. Exploiters will always go for the weaker target.

---

### Post by Gone fishing on 2010-05-26
Very little coding. 

Obviously you will need to learn to be very familiar with networking applications, protocols and utilities. Yu will have to get comfortable with the commandline, vi etc.

But coding very little.

---

### Post by julio_cortez on 2010-05-26
> **NMFTM said:**
> So, in a nutshell. What I'd like to know is, how much coding is actually involved in network administration?
I found that coding skills required to be a network administrator are close to none.
There's a colleague of mine that is a wizard at networking which knows close to nothing about programming.
Still he can easily solve quite any networking problem immediately, and the other ones with just a little reading.

On the other way round, I found that at least a decent knowledge of networking is required if you are a coder (that's the way I discovered networking and I liked it, for the record).

---

### Post by NMFTM on 2010-05-26
> **julio_cortez said:**
> On the other way round, I found that at least a decent knowledge of networking is required if you are a coder (that's the way I discovered networking and I liked it, for the record).
Wouldn't that depend on the type of applications you were developing?

---

### Post by new_tolinux on 2010-05-26
> **julio_cortez said:**
> I found that coding skills required to be a network administrator are close to none.
+1
Although a little knowledge of scripting will do no harm. In some cases you'll need to write login-scripts, create some (simple) scripts for cronjobs, etc. Apart from that, a network admin only have to know a lot about the systems on which that particular network is relying and probably never use any coding skills at all.

> **NMFTM said:**
> Wouldn't that depend on the type of applications you were developing?
Ofcourse.
A Word processor should not require much network-knowledge, but as one can imagine that's different for an internet browser.

---

### Post by julio_cortez on 2010-05-26
> **NMFTM said:**
> Wouldn't that depend on the type of applications you were developing?
Sure, my fault. Of course if you are developing a word processor you don't need any networking knowledge.
I've been working on an RSS reader by the way when I was at uni and that's why I had to learn networking basics (which indeed have been widely deepened in a specific networking course little after I passed the Java programming test).
Before that I had to develop a simple (offline) address book in C and, of course, networking knowledge wasn't necessary ;)

**EDIT:**
> **new_tolinux said:**
> A Word processor should not require much network-knowledge, but as one  can imagine that's different for an internet browser.
Ahahah beaten me to it for just a minute :D

---

