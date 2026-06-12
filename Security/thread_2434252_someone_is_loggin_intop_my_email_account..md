---
title: "someone is loggin intop my email account."
date: 2020-01-02
forum: Security
---

### Post by wolftrax on 2020-01-02
a few month back someone was into my email account and I changed passwords and got a new router because I was not sure if someone had access to my computer as well. 
now last night I installed privacy badger add on to firefox and after that quoara wont let me login and sendt me sms to make sure its me logging in. 

I thought that was strange and logged in using a other email account and nothing wrong there and went to bed. 
when I woke up and wanted to check my email there was a security warning about a unknown devicel loggin  in on my account the middle of the night when I am sleeping and the IP address is my own isp provider. 

I changed passwords on my account again and called my ISP provider that says he only read about these things but he is aware that if somone steals your account he can use the ISP adress from a phone company to avoid getting tracked 


can anyone here help me sort this out ?

---

### Post by TheFu on 2020-01-02
Change email accounts.
Have 5+ email accounts, each for different levels of secure access.

Each bank gets a separate email account. NEVER use this one anywhere else.  Don't use it on your phone, ever.  If you have 3 different bank accounts, then you need 3 different email addresses.

Use a different email account for places where you spend money online.  This is similar to banks.

Use a different email account for the mobile phone. Treat this like a bank, since some people might clone the SIM in a phone. With this access, they can easily convince businesses they are you.  SMS as a 2nd factor authentication is useless when someone has cloned your SIM.  This problem has been known for over a decade.  

Use a different email address for all the utilities - electric, gas, cable. These can be shared.

Use a different email address for family.

Use a different email address for any social networks.  I would put Quora and Ubuntu Forums in the same "group", but add a +uf and +qu to the email address.  This should effectively provide 20+ email addresses that all end up in the same account.

A new router doesn't mean better security. There are only a few router vendors who properly maintain their firmware.  Using trivial passwords is a huge issue for normal people.  That's where a password manager can help.  Good ones will generate long, random, passwords. Since you'll never actually type it in, why not make all of these 50+ characters?

I don't understand what>  if somone steals your account he can use the ISP adress from a phone company to avoid getting tracked  means.  For TCP connections, the only way someone can appear to be from your IP is to hack a computer inside your subnet.  With UDP, there are other methods, but those don't work with HTTP or HTTPS connections.

---

### Post by wolftrax on 2020-01-02
thanks.   I don't use mobile phones or computers to do any form of transaction of money . its only to use sites like this I have a email account.  

what I mean by that sentence is that I was told that its possible to change the IP address to a other IP so they cant see which IP its really been that logged on but I don't know how its done . 

someone have deleted one of my email accounts within the last 5 hours when I had my computer shutdown and went shopping.  so I changed passwords again and I am going to create a new email address and start over again. 

good advise and thank you :)

---

### Post by TheFu on 2020-01-02
> **wolftrax said:**
>  what I mean by that sentence is that I was told that its possible to change the IP address to a other IP so they cant see which IP its really been that logged on but I don't know how its done . 

It cannot be done unless they are running a VPN server on your subnet at home, inside the router.  Look at all the open network connections and see if any don't make sense.  **netstat** and **lsof** can be used for that. There could be 50+ and most are normal, so you'll be looking at each one and need to think outside the box.  Look for a VPN or ssh connetion outbound.

These things almost always turn out to be user error.  If you aren't really careless, with terrible email passwords, or work for some organization that a govt somewhere (or your own) really wants to be quiet, it is very unlikely any one would be targeting your systems.

I've heard through friends of people being targeted.  They were either famous or high networth people and paid a professional to come in and audit their complete internet security.  A few had their cell phones cloned and were using that for almost everything online. Since you don't use any cell phone, it means either the router has been completely hacked or someone is physically close.

But my bet is still on user error and misunderstanding.

---

### Post by wolftrax on 2020-01-02
I don't know what exactly is going on .  I am going to read a little on this one and thanks for the information.  internet is NOT my strong side at all.

edit: it started when I was about to go to court against the danish government.  there was someone hijacking my email account and I was using it to contact the newspapers and poltical parties .  the danish government would like me to shut up but I would sound paranoid if I said it has something to do with this. 

its because a doctor tried to kill me and I off course reported this to the police but these cases are something the system does not like getting out in the open so they try to cover it up as much as possible.  I received threats on my life after that incident as well.

---

