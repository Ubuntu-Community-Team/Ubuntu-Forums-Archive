---
title: "My Ubuntu Server named Greedo"
date: 2008-11-08
forum: Testimonials &amp; Experiences
---

### Post by DBrocks on 2008-11-08
It all started with an annoyance. I set up Gmail to forward incomming emails to my cell phone as text messages, so I would be able to read them. However, cell phone SMS (short messaging service) only allows messages of 160 characters. On most phones, it will break up texts longer than 160 characters into 160 character blocks and you will receieve multiple texts. However, on email forwarding, this is not possible. You see the first 160 characters of an email and thats it. Thats good because I'm alerted that I have a new email. But if I'm on the go, I cannot read it. I wanted to figure out how I could break emails into 160 character blocks and send them to my phone. I heard about Ubuntu and how powerful it could be. At my school, we had a bunch of Dell 486's (212 Mhz) we were going to throw out. I asked if I could have one, and I got one for free. My friend helped me install Ubuntu Server CLI, and taught me the basics of Ubuntu. Unlike most people, I tend to have a "Vertical learning curve", so I jumped into Ubuntu CLI with no experiance with the GUI. It was tough at first. I had a hard time even getting internet connection. :D However, I began to get more and more savvy with Ubuntu. My plan for the emails would be this: A) Fetchmail parses Gmail every minute. B) Fetchmail downloads new emails. C) A shell script removes all the headers, saving only the From, Subject, and Date, then breaks the message into 160 character blocks. C) Sendmail would send the messages to my phone. However, I started realizing the power of Ubuntu. I bought a 500gb HDD for about 100 bucks, and put it into my server. I learned Samba, and set up file sharing for my network. I set up SSH, and the server which I named "Greedo", was finally headless. Eventually I set up FTP, a web server, and I use Rtorrent for all my torrent needs. Eventually the server was virtually self sustaining. I have not had to do any maintence on it for several months now. The only time I SSH in is to write something in C or play around with it. The funny thing is, the original scope of the project (email) has been left in the dust. Hmmm... maybe I should get back to working on it now...

So a big thank you to Ubuntu, and all the developers that went into it. It is by far the most stable and sturdy OS I have used. If it can run on a Dell 486 from the early 90's with a 212Mhz processor, and 64 megs of ram without a hitch, Imagine what it could do on a fullscale server.

---

### Post by jorj82 on 2008-11-08
Your server's name is Greedo?  Watch out for Han Solo! :lolflag:

---

### Post by Joeb454 on 2008-11-08
> **DBrocks said:**
> 
So a big thank you to Ubuntu, and all the developers that went into it. It is by far the most stable and sturdy OS I have used. If it can run on a Dell 486 from the early 90's with a 212Mhz processor, and 64 megs of ram without a hitch, Imagine what it could do on a fullscale server.

What do you think these servers & ubuntu.com servers run on ;)

---

### Post by DBrocks on 2008-11-08
> **jorj82 said:**
> Your server's name is Greedo?  Watch out for Han Solo! :lolflag:

Yeah lol. Its from "[When Sysadmins ruled the world]("http://baens-universe.com/articles/When_Sysadmins_Ruled_the_Earth")", one of my favorite short stories. In it, there is a cooridnated strike against all countries, but the sysadmins locked away in the vaults with the critical servers are left alive, and try to keep the internet running. Its a  good read. In it, they named one of their servers Greedo, so I thought it would be fun to name mine Greedo too.

---

