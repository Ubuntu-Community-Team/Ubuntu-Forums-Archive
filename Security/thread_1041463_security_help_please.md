---
title: "security help please"
date: 2009-01-16
forum: Security
---

### Post by pdtpatrick on 2009-01-16
i'm looking to really get into information security (mostly for linux)

i currently work as a linux engineer (mid level) and have my security+ and some other certs but i wanted to get first hand advice from you guys and see what i should learn or pick up.

I like intrusion detection, penetration testing - stuff like that.

So far im learning wireshark and i want to also learn iptables (this seems like a huge topic)

Any ideas are welcomed please.

---

### Post by bodhi.zazen on 2009-01-16
> **pdtpatrick said:**
> i'm looking to really get into information security (mostly for linux)

i currently work as a linux engineer (mid level) and have my security+ and some other certs but i wanted to get first hand advice from you guys and see what i should learn or pick up.

I like intrusion detection, penetration testing - stuff like that.

So far im learning wireshark and i want to also learn iptables (this seems like a huge topic)

Any ideas are welcomed please.

There are a number of stickies here that may interest you.

Funny you should ask re : iptables, I am working on a how to for these forums, it is still in draft form, but I hope to post it in the next few days.

---

### Post by HermanAB on 2009-01-17
For IPtables, the ultimate reference is Rusty Russel's Amazingly Inaccurate Web Site.

Google for it.

Cheers,

Herman

---

### Post by albinootje on 2009-01-17
> **pdtpatrick said:**
>  I like intrusion detection, penetration testing - stuff like that.

So far im learning wireshark and i want to also learn iptables (this seems like a huge topic)


OpenVAS (software) is interesting imho. 
Also check out fcheck, rkhunter, chkrootkit, (the not so easy) snort, iftop, darkstat, nikto, ntop.

The Linux distribution BackTrack could be interesting for you to try :
[http://en.wikipedia.org/wiki/BackTrack](http://en.wikipedia.org/wiki/BackTrack)

---

### Post by Dr Small on 2009-01-17
> **bodhi.zazen said:**
> There are a number of stickies here that may interest you.

Funny you should ask re : iptables, I am working on a how to for these forums, it is still in draft form, but I hope to post it in the next few days.
I shall be interested in reading it :)

---

### Post by cjacobsen on 2009-01-23
[LIST]
[*]Snort for intrusion detection. 
[*]Nessus for intrusion prevention
[*]Nmap for intrusion prevention
[*]Rkhunter and Chkrootkit
[*]Logwatch for log monitoring
[*]A firewall. Start with UFW and take it from there
[/LIST]

Check out my signature link for some howto's on Ubuntu security. I have covered all the programs listed in this post.

---

### Post by albinootje on 2009-01-23
> **cjacobsen said:**
> [LIST]
[*]Snort for intrusion detection. 
[*]Nessus for intrusion prevention
[*]Nmap for intrusion prevention
[*]Rkhunter and Chkrootkit
[*]Logwatch for log monitoring
[*]A firewall. Start with UFW and take it from there
[/LIST]

Check out my signature link for some howto's on Ubuntu security. I have covered all the programs listed in this post.

Thanks for your comment. Very interesting to read!

I'm however a little surprised that already in your preface you start writing that people should get a Gmail account.
I have some doubts about using the email services of the advertisement company that Google is, doubts about privacy issues.
As far as I'm concerned it would be fine if you plugged Gnupg email encryption as well in that same preface, and added a small disclaimer about Gmail.

For the rest, Nessus has gone closed-source, there's [http://openvas.org](http://openvas.org) as an alternative.
[http://en.wikipedia.org/wiki/OpenVAS](http://en.wikipedia.org/wiki/OpenVAS)

---

### Post by cjacobsen on 2009-01-23
Thanks for the advice! 
Had planned covering encryption later on, but I'll gonna add a section on it on the preface.


The reason I've added Gmail as an example is because of convenience. However, you can use any other mail service of your liking, but in many cases mails from your server end up in a spam filter by your ISP or email provider. Spam filters usually don't like mails from user@ubuntu.



Best regards
cjacobsen

---

### Post by albinootje on 2009-01-23
> **cjacobsen said:**
>  The reason I've added Gmail as an example is because of convenience. However, you can use any other mail service of your liking, but in many cases mails from your server end up in a spam filter by your ISP or email privider. Spam filters usually don't like mails from user@ubuntu.

The settings of the mail client should take care of that.

And it's fairly easy to use the smtp server of the ISP to prevent the blocking of dynamic "ip-addresses"
Although as a sysadmin I don't like that so much because I lose some of the overview/control when my users complain about delayed or returned emails.
> 
I'm going to cover encryption later on in the series by the way; entire system, disk, partition, hidden, files, email and so on.


Excellent! :)

---

### Post by cjacobsen on 2009-01-23
> **albinootje said:**
> 
For the rest, Nessus has gone closed-source, there's [http://openvas.org](http://openvas.org) as an alternative.
[http://en.wikipedia.org/wiki/OpenVAS](http://en.wikipedia.org/wiki/OpenVAS)

I've not heard about this application before. I'll check it out and update the part on prevention!

cjacobsen

---

### Post by pdtpatrick on 2009-01-23
Man appreciate all the help guys. 

I really like security but i guess i better get labbing. At my job we use snort for IDS and i recently learned to use wireshark for what its really worth but i have some stuff to learn .. like how to read plain text transmission protocols like http and see if i can sniff the username or password in it. 

I really like snort but it takes some understanding and i would love to get intune with iptables but i heard you have to know scripting pretty good? Im not really good at scripting.. i know basics and for the most part i can read some what medium complex scripts and what they are for but i dont really write scripts. Is this something i will definitely need to be a security expert? 

I should also mention that i like wireless communications.. the algorithms and such but those for a beginner can get overwhelming but after the first couple of headaches i get reading those huge books and tutorials online, they are finally starting to add up. 

Once again i appreciate the efforts and will read all the those materials mentioned :)

---

### Post by albinootje on 2009-01-23
> **pdtpatrick said:**
> At my job we use snort for IDS 

Installing+configuring+using snort gave me headaches some months ago, I gave up, for me it's better to concentrate on other things to learn or improve.
> 
and i recently learned to use wireshark for what its really worth but i have some stuff to learn .. like how to read plain text transmission protocols like http and see if i can sniff the username or password in it. 

You can filter within wireshark, no ?
> 
Im not really good at scripting.. i know basics and for the most part i can read some what medium complex scripts and what they are for but i dont really write scripts. Is this something i will definitely need to be a security expert? 


I'm very bad at programming and even at simple shell-scripts. 
I do realise that it can make work so much easier. But I will have to spend time on it, if I want to pass the LPI exams.

Also.. some months ago a friend of mine showed me some awk stuff.
Amazing, very useful for sysadmin stuff.
And he and another friend told me to learn python.
Well, I wish I could :)

---

### Post by Dr Small on 2009-01-23
> **albinootje said:**
> You can filter within wireshark, no ?

Wireshark has all kinds of filtering methods.

---

### Post by pdtpatrick on 2009-01-23
> **albinootje said:**
> Installing+configuring+using snort gave me headaches some months ago, I gave up, for me it's better to concentrate on other things to learn or improve.

You can filter within wireshark, no ?


I'm very bad at programming and even at simple shell-scripts. 
I do realise that it can make work so much easier. But I will have to spend time on it, if I want to pass the LPI exams.

Also.. some months ago a friend of mine showed me some awk stuff.
Amazing, very useful for sysadmin stuff.
And he and another friend told me to learn python.
Well, I wish I could :)


yeah even at my job, all the guys keep telling me to learn python and shell scripts. It makes life easy, so far i understand the basics of scripting and can create scripts to verify files and run applications and all that good stuff. But complex scripting like what the senior admin does, reading that stuff is insane sometimes. I'm sure in due time it will all make sense but man so many % and $ signs.. im like wtf.

But so far from where i started, ive made vast improvements.

Also in regards to the wireshark question above, yes you can filter wireshark to be more intuitive and subjective. But i would like to see or use it various ways to test out it's strength.

---

