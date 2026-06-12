---
title: "Users with different firewall needs - works best with separate Ubuntu installations?"
date: 2011-03-05
forum: Security
---

### Post by DawieS on 2011-03-05
Just to confirm - I have come to the conclusion that it is best to have separate Ubuntu installations if users of the same computer have different default firewall blocking needs.

Me and my wife have totally different Internet surfing habits. I also tend to block most of the websites that she normally uses, some of which are dialed by default when opening Firefox.

We have used one desktop computer for a while now with two users in one Ubuntu installation. It is becoming too much of a hassle having to change the firewall settings each time it was changed by the other user with a previous log-on.

We also have two other computers in the household for the children. I have created a Local Repository, and download updates only on my computer, saving on time and bandwidth (the only replication that takes place is downloading the index files from the update servers for each computer). Having another Ubuntu installation on the same computer will just add to the "auto update" list.

Another advantage is that my "more secure" Ubuntu partition (which may contain sensitive information from time to time) will not be mounted when my wife is on the Internet.

Agreed?:smile:

---

### Post by wacky_sung on 2011-03-05
I do not get to understand what you actually meant by?

> Just to confirm - I have come to the conclusion that it is best to have separate Ubuntu installations if users of the same computer have different default firewall blocking needs.

Me and my wife have totally different Internet surfing habits. I also tend to block most of the websites that she normally uses, 

My wife at times using my system for her surfing as it come to my firewall setting remain the same inregardless of her surfing habit which is difference from mine(using iptables to firewall and ebtable from router).If you wanna save your bandwidth and time, then you shall start to install squid and privoxy which can really help you up.

---

### Post by DawieS on 2011-03-05
> I do not get to understand what you actually meant by?
When two users of a single Ubuntu installation keep on changing and reverting each other's settings, it can become frustrating. Obviously a solution would be to have two separate Ubuntu installations, each on its own partition.:smile:

---

### Post by handy on 2011-03-05
> **DawieS said:**
> When two users of a single Ubuntu installation keep on changing and reverting each other's settings, it can become frustrating. Obviously a solution would be to have two separate Ubuntu installations, each on its own partition.:smile:

Do you & your wife change the IP Table settings each time you login?

---

### Post by wacky_sung on 2011-03-06
> **DawieS said:**
> When two users of a single Ubuntu installation keep on changing and reverting each other's settings, it can become frustrating. Obviously a solution would be to have two separate Ubuntu installations, each on its own partition.:smile:

I do not quite understand why there is a need for reverting each other setting if they can create each person using a difference account under a single installation.Isn't that a solution?

_Example_ 
My wife like to use my computer for her surfing habits which will never complains about my security setting which never fail her using whatever she want under my account.I use a separate bookmark Keepassx for all my bookmarks whenever she can do whatever she want on her bookmark within the browsers.:lolflag:

---

### Post by cariboo on 2011-03-06
@DawieS, wouldn't it be easier just to create a separate account for your wife? Any accounts created after the first user have limited privileges, unless you specifically give them extra rights.

---

### Post by bodhi.zazen on 2011-03-07
Just use iptables rules that match per user.

[http://bodhizazen.net/Tutorials/iptables#Additional_Tips](http://bodhizazen.net/Tutorials/iptables#Additional_Tips)

---

### Post by DawieS on 2011-05-10
Hi everyone,
Please accept my apologies for taking so long to respond. I went off working in a place without Internet access for the past few weeks.

@handy
Yes, we change the IP Table settings each time if it has been modified by the other user.

@wacky_sung & cariboo907
The IP Table settings remains the same for all accounts as it was last set by a user.

@bodhi.zazen
Thanks a lot for the advice. I will surely implement this solution as soon as I find the time to brush up on my Linux skills.:grin:

---

