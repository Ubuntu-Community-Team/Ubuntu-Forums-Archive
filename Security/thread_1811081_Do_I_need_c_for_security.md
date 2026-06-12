---
title: "Do I need c for security?"
date: 2011-07-24
forum: Security
---

### Post by stamatiou on 2011-07-24
If I want to learn security and mostly pen testing do I need to know C?

---

### Post by wacky_sung on 2011-07-24
You need to know more than just C.:guitar:

You may also need to know A,B,C,D and more. Joke.:P

---

### Post by haqking on 2011-07-24
> **stamatiou said:**
> If I want to learn security and mostly pen testing do I need to know C?

as many programming languages as possible.

as much about computers, networks and their protocols as possible. (knowing C wont help you examine a packet)

as much about everything as possible ;-)

Sone would say C is best language to learn, best one to start with, others say Python, various forms of basic, C+ etc etc.

To find out best one to start with to learn programming head over to the programming section as there are already many threads discussed on the subject.

As for specific to Security/Pen testing then as said a knowledge of as many as possible.

---

### Post by Dangertux on 2011-07-24
I absolutely agree with haqking on all of that.

With penetration testing (assuming you are wanting to do it for a job, not just a hobby) you need to know as much about as many different systems and how they work as possible. If you don't know things ahead of time you may spend valuable time "figuring them out". Which wastes your time and your client's time. Conversely, during a pen test you will usually have plenty of time (given you or your employer grant you enough time to complete your job).

Things I would recommend (most of this has already been said)

- Understanding networking, protocols, and packet construction
- Understanding hardware (deeply not this is a graphics adapter) ; actually how the hardware interfaces with the operating system and the rest of the hardware in the machine.
- You may wish to learn how to build basic hardware, etch your own circuit boards, solder, how IC's work, programming EEPROM,  etc.
- Coding, pretty important as far as languages go I would highly recommend learning C, C++ and all of it's variants, ruby, php, python, perl, javascript and java are also helpful. Basically if you were going to do a bare minimum, I would say C , Python, PHP , and Java/script.
- A deep understanding of assembly is also very helpful.
- Understand binary, hex, base64, unicode etc
- Here's another huge one IMO : understand how memory addresses work.
- Understand how things are put together. Be able to figure out the logical flow of data through a system. For instance, when you make an HTTP request to a website, where does it go from there (exactly). IE: Not it goes to the server, the server gets the page and it comes back.
- Learn about Databases particularly how they are used and can be leveraged for exploiting web based applications. A working knowledge of SQL is almost imperative.

Anything else you can learn along the way, will always help you. It's just one more "tool" in your kit so to speak.

The important thing that I like to stress, particularly when people first get into the field. Pen testing requires a lot of knowledge and few people are ONLY pen testers (most do other duties when not pen testing). IMO , the best pen testers have vast experience in other parts of the IT field. For some reason somewhere along the line pen testing became a specific job, now yes there are some consultancies that ONLY do pen testing, however those pen testers are highly skilled. The company I work for does auditing and pen testing fairly frequently. Most of us that work with the company are always a little bit cautious of the "new guy". You know the guy straight out of college with a BS in Comp Sci and a few certs. IMO experience with the IT field pays off more during a pen test than any cert or degree will. The first question usually asked when encountering a proprietary system is "has anyone worked with something like this before" that level of experience / expertise on that subject becomes invaluable during the test. Reinventing the wheel is bad, so if you know something, you're better off for it. The point in that giant block of text is that if you are serious about becoming an auditor / pen tester the more you know about the systems you are testing, the better off you are.

Another side note -- In case I didn't make it very clear, most pen testers have an extensive background in some OTHER area in IT first. They didn't set out to be pen testers. This isn't to say you can't, but many of the skills you would use say, administering a network, would become very useful during a pen test. As we have already determined, the more you know the better off you are.

---

### Post by Chayak on 2011-07-25
Yes you need C.  It's pretty much a foundation requirement if you really want to understand what's going on in code.  x86 Assembly is also a must to learn but that'll come with time.  You need to understand how exploits work and that involves knowing how memory is allocated and manipulated.  You don't get that kind of understanding with a scripting language.  In a scripting language you'll just use a string.  In C you'll know that a string is an array of bytes that has a defined length.  If you try to push more information into that array that it has allocated and there are no protections then you'll get an overflow and start overwriting other memory.  That in a sense is a buffer overflow.  You need to know what C teaches you about that kind of thing.

Then pick a scripting language.  Python is what you'll see in the field mostly, but Ruby is good to know if you plan on using metasploit.  If you're just starting then you'll be using metasploit a lot so learn it and I mean really learn it.  If you rely on autopwn you're nothing more than a script kiddie.

The list of what you should know is huge and ever evolving and what's been mentioned already is a good start.

Take a look at getting a CEH.  That alone isn't proof of any skill what so ever but it'll expose you to the tools and methodology of pentesting.

---

### Post by Ezlivin on 2011-07-25
Chayak is right on the money. In fact I applaud that post! I love C and Ruby and like Python. Perl [ CPAN ] deserves a mention too. You'll have to experiment and pick what suits your style. Like CEH the CISSP certification is a good investment.

---

### Post by Chayak on 2011-07-25
Just remember that the difference between penetration testing and a felony is documented, signed permission.

---

### Post by haqking on 2011-07-25
> **Chayak said:**
> Yes you need C.  It's pretty much a foundation requirement if you really want to understand what's going on in code.  x86 Assembly is also a must to learn but that'll come with time.  You need to understand how exploits work and that involves knowing how memory is allocated and manipulated.  You don't get that kind of understanding with a scripting language.  In a scripting language you'll just use a string.  In C you'll know that a string is an array of bytes that has a defined length.  If you try to push more information into that array that it has allocated and there are no protections then you'll get an overflow and start overwriting other memory.  That in a sense is a buffer overflow.  You need to know what C teaches you about that kind of thing.

Then pick a scripting language.  Python is what you'll see in the field mostly, but Ruby is good to know if you plan on using metasploit.  If you're just starting then you'll be using metasploit a lot so learn it and I mean really learn it.  If you rely on autopwn you're nothing more than a script kiddie.

The list of what you should know is huge and ever evolving and what's been mentioned already is a good start.

Take a look at getting a CEH.  That alone isn't proof of any skill what so ever but it'll expose you to the tools and methodology of pentesting.

Just remember CEH is entry level and is the MCP of pentesting but yes it is good to give you an exposure to the tools available (albeit some very out of date).

There are much more sought after and more worthy credentials in the pen test arena, most pen testers worth using would not use CEH as their qual for their job though they have taken it as a entry level exam.

---

### Post by haqking on 2011-07-25
> **Ezlivin said:**
> Chayak is right on the money. In fact I applaud that post! I love C and Ruby and like Python. Perl [ CPAN ] deserves a mention too. You'll have to experiment and pick what suits your style. Like CEH the CISSP certification is a good investment.


CISSP has very little to do with pen testing, and would not be used to show pen test skills, Pen testing is a hands on technical skill.

CISSP is more geared towards the security manager and deals with risk assesssements, policies and procedures, compliance and assurance etc etc.

Though an understanding of pen testing is required to be an effective Security manager, CISSP and CISM and some others are geared towards documentation more than anything.

I speak as both a CEH and CISSP amongst others.

---

### Post by lisati on 2011-07-25
Thread closed to allow the participants time to cool down.

---

### Post by lisati on 2011-07-25
Please keep squabbles off this thread..... offending posts jailed.

---

