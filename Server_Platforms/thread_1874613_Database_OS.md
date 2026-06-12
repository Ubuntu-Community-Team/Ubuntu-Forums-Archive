---
title: "Database OS"
date: 2011-11-03
forum: Server Platforms
---

### Post by Katu Mala on 2011-11-03
I'm building a database for my section at work place to store customer information. I still need to make a decision between the server OSes. I will have to use either Ubuntu or Freebsd.:)

I've never build a database using either of the two OSes, I'm doing
a research on both to figure-out which one is suitable to use.:)

Please I need help.:)

---

### Post by volkswagner on 2011-11-03
I think the bigger question would be what database software, not so much what operating system to use.  I'd start with deciding the software.  Likely either OS will be a fine choice.  

Stick with the OS you are more familiar with.  If you are equally unfamiliar with either, I'd go with Ubuntu based on these great forums get you through what you are not ready for on your own.

---

### Post by SeijiSensei on 2011-11-03
For the database software, I recommend PostgreSQL unless you need to impress corporate executives and have money to burn, in which case I'd recommend Oracle.  If you're going to spend the money on Oracle, buy it with Oracle Linux so they'll support the whole thing.

If you're looking for something free, PostgreSQL on  Ubuntu Server 10.04, Debian stable, or CentOS 6 would be my recommendation.  CentOS is a free "respin" of RedHat Enterprise Linux 6, the dominant flavor of Linux in corporate server rooms.  

Lots of people swear by the BSDs, but they don't have nearly the degree of community support that Linux does.  I started with Linux fifteen years ago and haven't been unhappy with my decision.

---

### Post by elico on 2011-11-03
i dont see any reason why not to choose ubuntu TLS (10.04) with let say mysql.
it's really depends on the size and the usage of the database.
i dont have much experience with  PostgreSQL so i can say anythings about it.

---

### Post by Jonathan L on 2011-11-04
> **Katu Mala said:**
> I'm building a database for my section at work place to store customer information. I still need to make a decision between the server OSes. I will have to use either Ubuntu or Freebsd.:)

I've never build a database using either of the two OSes, I'm doing
a research on both to figure-out which one is suitable to use.:)

Please I need help.:)

Hi Katu Mala

I have had a lot of experience with databases on various operating systems, both technically and as the person authorising the spend.   From a technical point of view it's mostly what interfaces with your applications; from a management point of view it's about what's easiest to set up and keep running, and to find help for.

From this point of view I'd suggest MySQL on Ubuntu 10.04.3 Long Term Support server edition for the following reasons:

[LIST]
[*] Very easy to set up the operating system, much help on forums, paid support if you want it
[*] Database is ubiquitious and easy to find help for, and runs well both at the small scale and the large
[*] Cheap
[*] Can run in the cloud easily and find hosting for
[/LIST]
 
I don't recommend Oracle as the databases are unecessarily complex to manage, and would only be a good idea if you had an application which really couldn't run with another. And just as Seiji says, if you have to run Oracle, use a paid Linux they explicitly suport: I did (on Red Hat) and was glad I did, for a host of mostly political reasons.  If you have to run Oracle, don't run it on Windows unless your job is more important than your sanity.  The main thing here was it was incredibly time-consuming to do anything unless you were already an expert, as finding things out was difficult.

I have had only light experience with Postgress, but it appeared to be excellent technically, if a little more difficult to find people who were very familiar with it.

FreeBSD is first rate, and if you have a server application it's really very stable indeed; again a bit harder to find help for than Ubuntu, doesn't have the range of applications if you want a general purpose machine, and also fewer drivers which can be a problem when choosing hardware.  One of the reasons why it's so stable is I believe that it's a bit easier to lock down in terms of automatic updating and library version control, and it's not unusual at all to see server processes run for years, with OS uptimes often several years: ie, the lifetime of the hardware.

A thing to remember about databases: your security needs a bit of different thinking, as you may well require more internal security than you're used to.  Customer information is valuable!

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by Katu Mala on 2011-11-09
Hi Jonathan,
 
I thank you for your response and advice.
 
I believe I have some more question to ask, but will do later. Yes, I would also need directions on going about building a secure database with the OS I will choose. But because of time I think I'll work with ubuntu but than again I do not know how secure is it as as server operating system (security)...???
 
This is only an assignment that was tasked to me by bosses, after I have undergone a two semester (5 months each) course on web design and database, which was based on Oracle system.
 
I am not paid for this assignment, however I took the challenge and I like it more better when I have  to work with open source softwares, such as Linux and FreeBSD to work with.
 
Too, what I do daily in at my work is totally different from building database system.
 
Again, thank you. :)

---

### Post by Katu Mala on 2011-11-09
I thank you for your response and advice.
 
Because of TIME I think I'll work with ubuntu but than again I do not know how secure is it as as server operating system (security)...???
 
This is only an assignment that was tasked to me by bosses, after I have undergone a two semester course on web design and database, which was based on Oracle system.
 
I am not paid for this assignment, however I took the challenge and I like it more better when I have to work (and also ***[COLOR=dimgray]_learn_[/COLOR]***) with open source softwares, such as Linux and FreeBSD to work with. :)
 
Too, what I do daily in at my work is totally different from building database system.
 
Again, thank you. :)

---

### Post by Katu Mala on 2011-11-09
**Hi Volkswagner,**
I thank you for your response and advice.

Because of TIME I think I'll work with ubuntu but than again I do not know how secure is it as as server operating system (security)...???

This is only an assignment that was tasked to me by bosses, after I have undergone a two semester course on web design and database, which was based on Oracle system.

I am not paid for this assignment, however I took the challenge and I like it more better when I have to work (and also ***[COLOR=dimgray]_learn_[/COLOR]***) with open source softwares, such as Linux and FreeBSD to work with. :smile:

Too, what I do daily in at my work is totally different from a building database system.

Again, thank you

---

### Post by Katu Mala on 2011-11-09
SeijiSensei,
 
Thank you for response and information. :)
 
Because of TIME and maybe because of the purpose of learning, I am using Ubuntu. I'll settle with it. But the next question I am asking is SECURITY because, I will be using customer data.
 
If you could provide me any information based on Ubuntu security I will very much appreciate it. :)
 
Please do know that I am more happier and eager to learn, and what I am building is something I am not paid for doing. 
 
Again, Thank you. :)

---

