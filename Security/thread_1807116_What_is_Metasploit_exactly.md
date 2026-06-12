---
title: "What is Metasploit exactly?"
date: 2011-07-18
forum: Security
---

### Post by stamatiou on 2011-07-18
Hey guys,
I would like to ask a question about metasploit framework.
Is it something lime programming?
Is it a database of exploits?
Do I need to know Ruby to use it?

---

### Post by Dangertux on 2011-07-18
Metasploit is an exploitation framework written in Ruby.  It is designed for penetration testers and security researchers. You do not have to know Ruby, however it is greatly helpful particularly if you want to create your own modules.

---

### Post by stamatiou on 2011-07-18
> **Dangertux said:**
> Metasploit is an exploitation framework written in Ruby.  It is designed for penetration testers and security researchers. You do not have to know Ruby, however it is greatly helpful particularly if you want to create your own modules.
So the users are not "script kiddies" or something?

---

### Post by Dangertux on 2011-07-18
> **stamatiou said:**
> So the users are not "script kiddies" or something?

I'm not sure that using Metasploit or not using Metasploit qualifies one as a script kiddie or otherwise. If anything it depends on the purpose for why they are using Metasploit. Like anything Metasploit is a tool, your intentions and how you use it dictate the script kiddie factor.

---

### Post by bodhi.zazen on 2011-07-19
> **stamatiou said:**
> So the users are not "script kiddies" or something?

"script kiddies" is a derogatory term used for crackers. The implication is that they have enough knowledge to run a script, and automated "attack" but not enough knowledge to be a "real threat" so as to leverage any vulnerability they identify.

I see the term most often applied to port scans or scripts that automate ssh (or other) logins - common users (root, staff, etc) and common passwords.

---

### Post by stamatiou on 2011-07-19
So it is something like a programming language?

---

### Post by stlsaint on 2011-07-21
> **stamatiou said:**
> So it is something like a programming language?

I guess you completely missed the first reply.

[Metaploit]("http://www.metasploit.com/") - A penetration testing framework!

1. No it is not a programming language
2. No not only script kiddies or crackers use it
3. No you do not have to know a the acutal language that it was made in to use it.

---

### Post by stamatiou on 2011-07-22
> **stlsaint said:**
> I guess you completely missed the first reply.

[Metaploit]("http://www.metasploit.com/") - A penetration testing framework!

1. No it is not a programming language
2. No not only script kiddies or crackers use it
3. No you do not have to know a the acutal language that it was made in to use it.
I am asking beacause the only framework I know iis Django and in order to use it you must learn it. Also, what is a module?

---

### Post by stlsaint on 2011-07-22
> **stamatiou said:**
> I am asking beacause the only framework I know iis Django and in order to use it you must learn it. Also, what is a module?

The best way to learn is to dive in and get your hands dirty. There is way too much in metasploit to try and explain every aspect here in this thread. Head over and install metasploit or grab a copy of backtrack and have at it! Trust me you will gain WAY more knowledge by doing it yourself instead of being spoon feed here.

---

### Post by Dangertux on 2011-07-22
I would definitely agree with the above post. 

Also a module is an add-on for metasploit written in ruby adding functionality to metasploit. This could be an exploit , fuzzer ,denial of service module, encoder, payload or anything else you wish to add in and have the functionality of within the framework. Even something simple like a banner grabber.

---

