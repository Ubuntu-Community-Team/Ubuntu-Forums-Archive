---
title: "Spamfilter server"
date: 2008-09-13
forum: Server Platforms
---

### Post by Kemicaze on 2008-09-13
Hi guys!

I've been looking around the forums and community pages, but haven't found what I've been looking for! So I will try here!

I got the Ubuntu server 8.04 running on a dedicated machine, and I want to use it as a Spamfilter of sorts... I want it to go online and get my email from a external POP3 server (not under my control) then pull it down to the server, where the mail is filtered. So I can then connect to it from my normal mail program (with POP3) and get the filtered email.

Is this at all possible?
I'm sort of a linux noob, but I've played alot around so sorta got a hang of the normal commands! So a kinda detailed guide would be kinda nice, but I can use anything u throw at me ;-)

Thx in advance!

-- 
Kemicaze

---

### Post by windependence on 2008-09-13
Yes, it is, you want to take a look at Spamassassin and ClamAV. If you want an all in one solution, look at untangle or pfsense.

-Tim

---

### Post by Kemicaze on 2008-09-13
So I don't need any of those mail handeling programs that came with Ubuntu server? I can remove them?

-- 
Kemicaze

---

### Post by Kemicaze on 2008-09-13
Also I'm look for a guide to setting it up, so it automatically gets the mail from the pop3 server, scans it, and then stores it for me to get when I start my mail program.
So some sort of POP3 server with a spamfilter attached.
A little more detailed than just the name of some filters plz!
But thx for answering so fast Windependence! :-)

-- 
Kemicaze

---

### Post by windependence on 2008-09-13
Well, I'm going to be back on the board later tonight so I will post some more information for you. To clarify, you want to just pull email from your ISP and filter it for spam and viruses and then deliever it to your box?

-Tim

---

### Post by Kemicaze on 2008-09-13
Yes as follows:
Server get mail from ISP's POP3 server.
Server filter mail.
Server holds onto filtered mail.
I start my mail program and download the filtered mail from the server!

So I want the server to get mail at specific intervals... say every 10 mins, and then filter it. and then hold onto it, untill I decide to download the mail onto my normal computer!

And thank u for takeing the time to help me!

-- 
Kemicaze

---

### Post by Kemicaze on 2008-09-16
Any1 got any guides for this? plz see above post for what I'm trying to do!

---

### Post by schettj on 2008-09-16
Not tested, but looks promising

[http://thalamus.no-ip.com/blog/?p=63](http://thalamus.no-ip.com/blog/?p=63)

fetchmail is the bit that gets your mail from elsewhere

Then, what you do with it determines how you filter spam.

So, if you can get fetchmail working, and you want to set up posfix + clamav + spamassassing - there are a million howtos on the second half...

---

### Post by FakeOutdoorsman on 2008-09-16
Why don't you just use a client that can handle a good spam filter?  Claws-Mail can use bogofilter and spamassassin.  At least you'll save power.

---

