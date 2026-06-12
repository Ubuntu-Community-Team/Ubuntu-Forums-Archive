---
title: "Few questions regarding Ubuntu Server"
date: 2010-07-20
forum: Server Platforms
---

### Post by Chris.Whitley on 2010-07-20
I work at a small company that uses 35 computers, all Windows XP .  I just started this job as an assistant IT Tech on the recommendation of a friend though I have have very little background in networking.

One of the first things I noticed about the company is that everything is setup on a p2p network and not a client/server network.  Listening to some of the people that are employed there, the request that they are making is geared for a client/server setup.  I have to prepare a report for the upper management on the benefits of setting up a server but I have little background on sever setups.  

I've used Ubuntu at home for a while, so I'm familiar with the OS, but never used the Sever OS version and need to get some knowledge base before I propose this to the management.  I just have a few questions, if someone doesn't mind answering for me.


[LIST=1]
[*]Is there a way for me to store the Windows XP client user accounts on the server to allow users to access the accounts from any workstation using their log in credentials?
[*]I've seen some people talk about Samba as the file server on the forums.  What other alternatives are there other than Samba and are they even worth checking into versus Samba
[*]I've read a little on using Squid as a proxy for web monitoring.  Are there any alternatives to this that are just as good? Also, If I'm setting up Squid, will I need (or is it required) to setup a DNS server along side it?
[*]There are three printers setup throughout the building, 2 Kyocera KM-5050's and a Kyocera KM-4050.  I've setup different workstations to print to these based on workstation locations using TCP/IP ports.  Would we gain any benefit implementing a print sever to do this or is TCP/IP ports just fine?
[/LIST]
That's all the questions I can think of right now for what I think they need.  If there are any other suggestions you can give me, I'm open to anything.

Thanks in advance for any help
-Chris

---

### Post by kevinthecomputerguy on 2010-07-20
I perfer to buy printers with print servers already embedded, but for your other needs, example:samba, try out this guide. found here at [http://woodel.com](http://woodel.com)

---

### Post by HermanAB on 2010-07-20
Howdy,

If you haven't done this before, then Ubuntu is the wrong distribution for this.  Mandriva, Suse and Redhat all have wizards that can be used to configure a corporate server with a few mouse clicks.  Doing the same with Ubuntu is rather difficult.

---

### Post by mcarrara on 2010-07-20
I have uses Suse and Ubuntu and personally I prefer the command line interface of Ubuntu rather than the wizards of Suse.  However I have 15 years of networking behind me.

As for your original question Samba is the only way to go and it can do sign ons for XP, file sharing and print sharing.

Mark

---

### Post by scottuss on 2010-07-20
I really don't mean to be rude, but shouldn't you consult someone with a little more knowledge? If you don't have a lot of networking experience, setting up a network for a corporate environment isn't an easy task to be taken lightly.

Then again, I guess everyone has to start somewhere. Just be really careful that you don't go getting yourself into a mess! On the other side of things, there's nothing worse than someone with lack of technical knowledge taking critical systems into their hands....

(I hope my post sounds friendly rather than arrogant! :) )

---

### Post by Chris.Whitley on 2010-07-28
> **scottuss said:**
> I really don't mean to be rude, but shouldn't you consult someone with a little more knowledge? If you don't have a lot of networking experience, setting up a network for a corporate environment isn't an easy task to be taken lightly.

Then again, I guess everyone has to start somewhere. Just be really careful that you don't go getting yourself into a mess! On the other side of things, there's nothing worse than someone with lack of technical knowledge taking critical systems into their hands....

(I hope my post sounds friendly rather than arrogant! :) )

Wow, I subscribed to the thread, but It never sent me emails on responses, sorry I haven't checked back at the answers and thanks for responding everyone

I understand where you are coming from on this and i didn't take it arrogantly at all.  The company is really small and when setting this up, the cheaper I can go the better, which is why I opted to first try Ubuntu server.  Looking up Mandrive, Suse, and Redhat, the price point for the server OS is a little much compared to the, excuse my terminology, "freeness" of Ubuntu.  As long as it's eventually possible to set it up on Ubuntu, then I more than confident that I can figure/learn out how to do it, no matter how much of a headache It'll seem


Keventhecomputerguy, thanks for the link to the guide you have, it's been wonders in steps to preparing and learning this stuff

---

### Post by kevinthecomputerguy on 2010-07-28
Rock on !

---

### Post by arrrghhh on 2010-07-28
Well reading thru your requirement list, Ubuntu will satisfy all of them but one... > Is there a way for me to store the Windows XP client user accounts on the server to allow users to access the accounts from any workstation using their log in credentials?

This is going to be a problem.  What you describe is "roaming profiles" and I don't believe it's possible with Ubuntu... if it is, I'd like to know how it works :D  Samba is making leaps and bounds, and there are ways you can hack this type of functionality, but basically it won't work as well as a Windows server (as much as it pains me to say that...)

However, everything else should be pretty easy.  Samba is the standard for sharing files with Windows machines, was there a reason you wanted to look at alternatives?  There are, there usually just not for Windows or don't work as well as Samba does.

As far as squid goes, I don't have a whole lot of experience with it but what are you looking to achieve?  Do you want to monitor usage, filter sites, speed up requests...?

---

### Post by lykwydchykyn on 2010-07-28
Samba is going to be the answer to #1 and #2, I'd suggest reading through "samba by example" [http://www.samba.org/samba/docs/man/Samba-Guide/](http://www.samba.org/samba/docs/man/Samba-Guide/), which gives a pretty good overview of setting up a network based on samba.

The only caveat about that book is that it's a bit redhat-centric, so you just have to know when it gives you rpm commands they don't really apply to Ubuntu.  In other words, don't read it for exact commands or step-by-step instructions but for the concepts.

On #4, I spent years purging all the workstation-shared printers from our organization.  I can't tell you how many times I got a support ticket like "I can't print to the printer by so-and-so's computer"; reason being, so-and-so's computer was sharing the printer and so-and-so was on vacation for a week and his computer was shut off.

If your printers aren't networked, buy dedicated print servers.  If you can't get funding for that, use an old junker computer and set up a print server using Linux and CUPS.

---

### Post by Chris.Whitley on 2010-07-28
> **arrrghhh said:**
> Well reading thru your requirement list, Ubuntu will satisfy all of them but one... 
 
This is going to be a problem. What you describe is "roaming profiles" and I don't believe it's possible with Ubuntu... if it is, I'd like to know how it works :D Samba is making leaps and bounds, and there are ways you can hack this type of functionality, but basically it won't work as well as a Windows server (as much as it pains me to say that...)
 
However, everything else should be pretty easy. Samba is the standard for sharing files with Windows machines, was there a reason you wanted to look at alternatives? There are, there usually just not for Windows or don't work as well as Samba does.
 
As far as squid goes, I don't have a whole lot of experience with it but what are you looking to achieve? Do you want to monitor usage, filter sites, speed up requests...?
 
Hmm...no roaming profiles with Ubuntu.  They wanted me to find a solution to all of this the most cost effeicient way, but if I have to let them know we need to purchase a server OS then so be it.  Hopefully I can find a "hack" or solution to that problem with Ubuntu.
 
I was only asking what alternatives there where to Sambe and Squid as well because I just want to know what's avalible.  Having been using Samba for the past week or so messing around with it, I can safely say it's what I'll probably be using.
 
Basically with Squid, I'm hoping to get usasge monitoring and site filtering.  I'm sure I can get all that from Squid.

---

### Post by flatline on 2010-07-28
I recommend you check out _[http://wiki.samba.org/index.php/Samba_&_Windows_Profiles](http://wiki.samba.org/index.php/Samba_&_Windows_Profiles)_ and _[http://en.wikipedia.org/wiki/Roaming_user_profile](http://en.wikipedia.org/wiki/Roaming_user_profile)_ to make sure this is actually what you want to do.  It is certainly possible, but unless you plan ahead and are careful in your execution, you may end up with a lot of upset users.

---

### Post by lykwydchykyn on 2010-07-28
I don't want to be presumptuous, or be accused of a sour-grapes mentality, but IME roaming profiles are not necessary nearly as often as people tend to want them, and they're generally more trouble than they're worth.

We had roaming profiles at one of our facilities a few years back using winXP + Windows server 2003, and it was very problematic for us.  May have been an error on our part configuring things, but my point is that I probably would recommend against setting up roaming profiles unless someone presented me with an actual day-to-day operations need (i.e., more than just "it would be nice if..." or "on the off chance that...").

---

