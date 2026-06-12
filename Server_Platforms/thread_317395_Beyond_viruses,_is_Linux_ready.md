---
title: "Beyond viruses, is Linux ready?"
date: 2006-12-12
forum: Server Platforms
---

### Post by Hendrixski on 2006-12-12
We may not have to worry about Viruses, but what about phishing?  It's the more lucrative information-gathering schemes are the next generation of security threat, even Firefox and Red Hat (inc) users have been hit by these things.  When I google "Linux phishing" all of the articles are from 2004, what's the news?  What sorts of things are in place to protect Linux users from being tricked by malicious advertising programs?

---

### Post by az on 2006-12-12
> **Hendrixski said:**
>   What sorts of things are in place to protect Linux users from being tricked by malicious advertising programs?

Isn't phishing OS agnostic?

---

### Post by tturrisi on 2006-12-12
Phishing has nothing to do w/ what OS is being used.  Phishing works by tricking uneducated users into believing something is legit, such as spoofed trusted web sites & spoofed trusted corporation names.  Phishing can work IN CONJUNCTION w/ viruses or malware that exploit known OS or software vulnerabilities, but it is a separate thing, non-OS dependant.  example:

[New Ubuntu Release Here!]("http://microsoft.com")

---

### Post by aysiu on 2006-12-12
As far as I know, there are email clients and web browsers on every major operating system out there.

All you need are these three components in order for phishing to work:

1. A party willing to phish and send out an email with a link in it.
2. Someone with an email client and a web browser--or even just a web browser if it's webmail.
3. That second person to be dumb enough to click the link and give out credit card information or other personal information.

---

### Post by Hendrixski on 2006-12-12
> **azz said:**
> Isn't phishing OS agnostic?

That was Microsoft's position.  They claimed that it is not the responsibility of the software to prevent people from fraud.  They favored "education".  

You're probably right that it's OS agnostic, but phishing is not entirely Software agnostic though.  I know Opera is trying some things to prevent phishing (like a list of suspect web-sites, and a reporting tool).  But those are things that MS already has in place. 

What kinds of things do we have to advertise to perspective new users to say "your information is safer on Linux"?  What education do we have in place for Linux users to be made aware of scams? When I searched for phishing only 4 threads came up, 2 of which had more than 0 posts, non of which had more than 4 posts.  Can we afford to be complacent?

---

### Post by aysiu on 2006-12-12
[quote=Hendixski]What education do we have in place for Linux users to be made aware of scams? When I searched for phishing only 4 threads came up, 2 of which had more than 0 posts, non of which had more than 4 posts. Can we afford to be complacent?[/quote]We're not complacent.

There are probably several reasons it's not mentioned very often here:

1. It's generally (not *always*, but generally) people not that into understanding technology who fall for phishing scams, and it's generally (not always, of course) people who are into understanding technology who install and configure Ubuntu and come on the forums asking for help.

2. Help, also, tends to follow questions. If someone asks a question about firewalls, people answer back about firewalls. They don't add in, "And don't be a dumbass and click on links in emails that might be phishing scams." That's not relevant.

3. Since it's an OS-independent problem, it doesn't behoove Ubuntu users or Linux users any more than it does other people to educate users about phishing scams. **Everybody** in all contexts should know about it. It would make about as much sense as asking the Ubuntu community to make itself responsible for online dating woes or pedophiles on MySpace.

That said, in [my Ubuntu security FAQ](http://www.psychocats.net/ubuntu/security), one of the major things I espouse is not being dumb: > Don't be dumb. That's right. You can have your firewall all set up and encryption, etc., but if you're dumb, the battle is lost. **A lot of security breaches come through social engineering. Don't give your password away. Don't click on links in emails. Don't open attachments from people you don't know.** Don't be dumb.

---

### Post by az on 2006-12-12
> **Hendrixski said:**
> That was Microsoft's position.  They claimed that it is not the responsibility of the software to prevent people from fraud. ?



So what?  That's correct.

> **Hendrixski said:**
> 
 I know Opera is trying some things to prevent phishing (like a list of suspect web-sites, and a reporting tool).  But those are things that MS already has in place. ?


Sounds like spyware to me.  Another reason to avoid opera.


> **Hendrixski said:**
> 
What kinds of things do we have to advertise to perspective new users to say "your information is safer on Linux"?  

With respect to phishing, it's not.  

With respect to malware, it is, because malware uses vulnerabilities in the OS.  Phishing preys on the vulnerabilities of people.  It has nothing to do with your OS.  And trying to make it part of the OS is not the way to go.

The last thing I want is for some third-party authority to tell me which sites I may visit and which emails are scams.  I want to have a choice in spam-filtering my email.

---

### Post by Hendrixski on 2006-12-12
> **aysiu said:**
> 
3. That second person to be dumb enough to click the link and give out credit card information or other personal information.

These are all good points.  And while I agree that 90% of it is user error ("stupid" is an insensitive word that won't appeal to newcomers) software can help prevent some of it by educating people as they're using.

Imagine your grandmother (not your actual grandmother per se, just generically speaking of older, less web-savvy people using Linux) stumbles across a malicious link.  Her browser could tell her "listen, there's fishy here: the meta data doesn't match the content, and they want you to enter personal information.  BE CAREFUL!"  the same way that it tells her "we just stopped a pop-up."

Or Evolution could say "We suspect that this is a fraud" when they get an e-mail saying "please fill out this form for new Medicare benefits". 

Things like that which are aimed at educating people at the moment they encounter something that is questionable.  What currently exists along those veins, and what is in the works?  What do you think?  Ubuntu: Linux for human beings of all user levels?  


[quote=azz]The last thing I want is for some third-party authority to tell me which sites I may visit and which emails are scams. I want to have a choice in spam-filtering my email.[/QUOTE]
I personally don't want it either.  But you would definitely want to give that option to your grandmother using Linux.  We do support options, don't we?

I'd love to spread Ubuntu CE to members of my church, and morally I'd like to know that they'd be safer from having switched to Linux.

---

### Post by aysiu on 2006-12-12
You mean like this?
[http://www.mozilla.com/en-US/thunderbird/](http://www.mozilla.com/en-US/thunderbird/)

 > **Anti-Phishing Protection**
    Thunderbird protects you from increasingly common email scams&#8212;also known as &#8220;phishing&#8221;&#8212;which try to fool you into handing over your passwords and other personal information. Thunderbird will tell you when it thinks a message might be a scam. My guess is (I don't really know Evolution that well) that Evolution, KMail, even Outlook have either developed or are in the process of developing anti-phishing tools.

Those will happen.

Even when they happen or if they're happening now, people still need to be educated, and this has nothing to do with Ubuntu. This is just a general life skill, like tying your shoes, reading a book, not taking candy from strangers, and not driving when you're drunk.

---

### Post by az on 2006-12-12
> **Hendrixski said:**
> I personally don't want it either.  But you would definitely want to give that option to your grandmother using Linux.  We do support options, don't we?

Well, ones that are effective, I hope.  In this context, too weak of a protection is useless and dangerous to rely on without educating the user.  Too strong a protection has too great a danger of invading privacy and/or turning into censorship. 

I'm not optimistic of this approach.  And anyway, it's on the level of the email client, not the underlying OS.

> **Hendrixski said:**
> 
I'd love to spread Ubuntu CE to members of my church, and morally I'd like to know that they'd be safer from having switched to Linux.

You mean *preferably*.  Whether this is a vulnerability that can be addressed or not is not a moral dilemma, it's a matter of opinion.

---

### Post by Henry Rayker on 2006-12-12
As has been stated, phishing is non-OS dependent. The same phishing scam can hit a Mac that can hit a Windows machine that can hit a Linux machine.

The OS used has nothing to do with how protected a user is. Yes, microsoft is working on this...because they have IE...they have Outlook and Outlook Express. The Ubuntu devs aren't the Evolution/Firefox/Opera/Thunderbird/whatever other email/web-browser devs.

Yes, it is dangerous to say that Linux is, without a question, absolutely and 100% secure...however, I don't believe I have ever heard that stated. Linux machines CAN contract viruses...you just have to, in almost all cases, install them your self. The OS can not help you in terms of common sense and basic understanding of these fundamental issues. If the OSes have to start worrying about this kind of tom-foolery, they may as well start preaching gun safety; telling you that your hot coffee WILL be hot, so be careful; probably recommend abstinence or a safe sex method and God know what else.

You put too much pressure on the OS and not enough on the users themselves.

---

### Post by tturrisi on 2006-12-12
Linux is no more safe from phishing than windows 98.
The whole point is that it is somewhat "barking up the wrong tree" to prevent phishing via software controls.  Education is the only valid solution.  Now, let's define education:

[i]Education: simply, any action that results in an increased understanding through study.
Study: simply, to observe and conclude.[/i]

The bottom line is this:
All the education and study in the world will not defeat phishing completely because there are those who cannot be educated, either because they cannot observe well enough (includes reading), or they are too incompetant to begin with or they have missing essential body parts such as eyes & ears & nervous system!

Combatting phishing using software solutions is like using laws & police to combat crime, it does not work and only servers to create more problems in the longrun.

Sound phishy to you?  Well, it's true!  Here's an example: You think the Puritans were pure?  ha!  Have a look at the laws they had in Puritan times.  They would not have needed all those esoteric laws if the Puritan society had not been doing those things to begin with.  And the laws did not stop them from doing those things either!  And to prove it, go out & look at some Puritans today.  What?  Not there?  It's no surprise!

There will always be people who can be fooled & tricked.  The best solution is (a type of education) Public Service Announcements along this line from the users' isps, who use digitally signed certs to verify the legitamacy of the announcement messages.  If the user still gets duped...well you can't really say he deserves it...but on the other hand there is such a thing as karma!

---

### Post by chrisfay on 2006-12-13
I totally agree with everyone here that phishing thrives on the users ignorance, though I also tend to belive that certain steps can be taken by software providers to ease the brunt on naive users. 

My mail server is always configured with the latest rules from SARE on phishing emails and catch upwards of 10 to 15 emails per day. Without those rules, these emails would be landing in my users mailboxes. I prefer to bare the responsibility of protecting my users from these scams with the assumption that some users are just to non complacent to worry about self education in this realm.   

Yes I had to educate myself on the steps necessary to block those emails from my network, though a nice automated integration of these filters would definitely be to some benefit. A benefit only 'directly' seen by the admin, but indirectly seen by an unsuspecting user. 

Now, normal users won't be running mail servers nor will they have the access or knowhow to block phishing scams at the perimeter. If they did, they wouldn't be falling for them in the first place. But, if sys-admins put these scams higher on their priority list and utilized such an application feature, it may buffer the less educated users a bit more.

It seems phishing scams are so previlant partially due to their ambiguous nature, coupled with the lack of accepted responsibility on the part of software providers. A shared responsibility between the users, the developers and the admins would provide a much better wall of defense then pointing the expectation at any one of them. IMHO

> Combatting phishing using software solutions is like using laws & police to combat crime, it does not work and only servers to create more problems in the longrun.

I have one issue with this statement. It assumes a congruence between the methods for fighting traditional crime and scams such as phishing. This mentality will fail as you pointed out. We see traditional crime from an outside perspective, as something that only police should fight. Scams are not effectively handled in this manner and therefore require a shift in our methods. A shift that I believe includes a seat for relevant software providers right next to us.

---

### Post by Hendrixski on 2006-12-16
OK.  Thanks everybody.  I guess this thread is retiring.  I learned a few things from it.  And thought through a few things that I had been reading about lately.

---

### Post by imagine on 2006-12-16
> **azz said:**
> Sounds like spyware to me.  Another reason to avoid opera.
Being closed-source is the only reason to avoid Opera. There's not "another".
Opera sends the domain name and a hash of the visited URL to a server, which then compares the submitted information to a database of known phishing sites and sends back a response. All that happens in plaintext (except for HTTPS sites), so everybody can check it with a network sniffer. So please don't state that Opera is spyware when you don't know what the browser actually does, especially because the phishing filter is currently turned off by default.

---

