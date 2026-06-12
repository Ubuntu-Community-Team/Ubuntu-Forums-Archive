---
title: "firestarter shutting down with out warning or error"
date: 2007-10-27
forum: Server Platforms
---

### Post by m0rk on 2007-10-27
Since I have upgraded to Gutsy, I have been experiencing random, unpredictable, non-errored, no-warning, shut downs of Firestarter.

I've also been seeing continual UDP events from europium.canonical, and also seeing lingering traffic from a google server on port 80. Port 123 for NTP seems to be the one coming from europium.canonical which is really puzzling me. NTP does not need to update every 10-15 minutes. That's a once a day task as far as I've ever seen.

So what's happening here? Why the random shutdown and what's with the random traffic that i've not experienced in the past before the Gutsy upgrade?

Any help would be great. 

I have no logs of the Firestarter failures. There is no reported error, no stack trace, no core dumps, nothing. It just shuts down ... 

Thanks,
m0rk

---

### Post by steve.horsley on 2007-10-27
Are you worried that the firestarter GUI shutdown is leaving your firewall inoperable? If so, you can verify that iptables (the firewall that firestarter configures) is still protecting you by using the command **sudo iptables -L** both when the GUI is running and after it has shut down. The output should be the same.

---

### Post by robert_pectol on 2007-10-27
> **m0rk said:**
> ...NTP does not need to update every 10-15 minutes. That's a once a day task as far as I've ever seen.

Sure it does.  In fact, when ntp is first started, it may make queries every few seconds.  After a period of time, the duration between queries will lengthen out.  You should probably read up on ntp before you assume things.  That being said, there is the ntpdate utility that can be used to sync up to a remote time server and it's more of a one-shot deal.  It's common to have it be called from an init script or have a cron job that runs it at specified intervals to keep your clock on time.  Perhaps that is what you were expecting from ntp.  But ntp is actually a daemon that runs all the time, constantly steering your clock as it communicates with the remote time servers.  It maintains a much higher degree of accuracy than just calling the ntpdate utility every so often.

---

### Post by m0rk on 2007-10-28
> **robert_pectol said:**
> Sure it does.  In fact, when ntp is first started, it may make queries every few seconds.  After a period of time, the duration between queries will lengthen out.  You should probably read up on ntp before you assume things.  That being said, there is the ntpdate utility that can be used to sync up to a remote time server and it's more of a one-shot deal.  It's common to have it be called from an init script or have a cron job that runs it at specified intervals to keep your clock on time.  Perhaps that is what you were expecting from ntp.  But ntp is actually a daemon that runs all the time, constantly steering your clock as it communicates with the remote time servers.  It maintains a much higher degree of accuracy than just calling the ntpdate utility every so often.

Yes, I'm rather familiar with NTP and it's frequency of connectivity. I have assumed nothing. I am speaking with 8 years of Linux experience here. NTP does not need to connect every 5 minutes to time sync with NTP servers, period. End of story.

But that is essentially beside the point. The question I wrote in with was this:

WHY IS MY FIREWALL SHUTTING DOWN UNDER GUTSY? If the gui is shutting down under GUTSY, that's a bug and should be submitted as such. So if you can work yourself around the minor details and look at the big picture, we'd be doing great - thanks in advance.

---

### Post by robert_pectol on 2007-10-30
> **m0rk said:**
> Yes, I'm rather familiar with NTP and it's frequency of connectivity. I have assumed nothing. I am speaking with 8 years of Linux experience here. NTP does not need to connect every 5 minutes to time sync with NTP servers, period. End of story.
Again, you should probably read up on it!

> **m0rk said:**
> But that is essentially beside the point. The question I wrote in with was this:

WHY IS MY FIREWALL SHUTTING DOWN UNDER GUTSY? If the gui is shutting down under GUTSY, that's a bug and should be submitted as such. So if you can work yourself around the minor details and look at the big picture, we'd be doing great - thanks in advance.
Actually, you wrote in with 2 questions; one regarding your firewall, and one regarding ntp as quoted here:
> **m0rk said:**
> ...I've also been seeing continual UDP events from europium.canonical, and also seeing lingering traffic from a google server on port 80. Port 123 for NTP seems to be the one coming from europium.canonical which is really puzzling me. NTP does not need to update every 10-15 minutes. That's a once a day task as far as I've ever seen.
I chose to respond to the ntp question.  I'm sorry you didn't like my response.  I meant no offense.  Anyway, good luck.

---

### Post by EmiOfBrie on 2007-10-30
> **m0rk said:**
> Since I have upgraded to Gutsy, I have been experiencing random, unpredictable, non-errored, no-warning, shut downs of Firestarter.

Glad to see I'm not the only one getting this problem

But to answer an earlier question, Firestarter was not among the running processes when the GUI for it disappears, so it is a full shutdown of the program.

I think it's just that the current version of Firestarter may have a slight incompatibility with Gutsy.  That's the only problem with adapting the leading edge OS right away, we get to play "wait for the 3rd-party apps to catch up"  *heh*

I'm not too worried...all that's on my Ubuntu system is backed up elsewhere, so if I get infected I can reload, it's just a pain in the ***.  *heh*

---

### Post by MJN on 2007-10-30
> **m0rk said:**
> Yes, I'm rather familiar with NTP and it's frequency of connectivity. I have assumed nothing. I am speaking with 8 years of Linux experience here. NTP does not need to connect every 5 minutes to time sync with NTP servers, period. End of story.

Hi Mork,

Robert was bang on with his response.

Ntpd will indeed periodically make queries to time servers - it runs in this continous mode by default and the exact update interval is defined by a very complex algorithm based on current performance and state. However, suffice to say it starts making queries every 64 seconds and gradually raises this towards 1024 seconds (17 minutes) as your clock drift tends to zero. Hence what you are observing is entirely normal. Is your machine on 24/7? You should see the update intervals increase over time but if you're turning it on/off every day it is within reason that you'd never reach the minimum poll rate.

If, for whatever reason, you don't like this behaviour then check out ntpdate. As Robert says this is indeed more of a one-shot solution to setting the clock, and arguably better suited for machines that aren't left on 24/7. Alternatively, you can even run your nptd daemon with the -q flag to cause a one-time clock update (and quit) but there's little point in having the daemon installed if you are going to use it like this.

Do you have any logs for the Google port 80 traffic? Do you mean it's coming *from* port 80 at Google's side? And there are no client packages open (browsers in particular)? Install a packet sniffer (e.g. Ethereal/Wireshark) and check the packet contents - assuming non-https it should be possible to determine exactly what's being sent (and hence hopefully why!).

Mathew

---

### Post by pedja_portugalac on 2007-10-30
I also face same problem, firestarter shuting down and leaving ports 80 and 443 open. I am not any kind of security specialist but I don't like this! Even to get updates, just after installing gutsy, I had to change some things in software sources menu. I don't think it's good for the sistem who claim to be easy for beginers and fairly secure out of box. I hope we'll soon have the best linux distribution like it was feisty. I am sorry that I can't, at the moment,  do nothing else but testing and reporting what I think is important for all of us.

---

### Post by MJN on 2007-10-31
> **pedja_portugalac said:**
> I also face same problem, firestarter shuting down and leaving ports 80 and 443 open
 
What do you mean by 'open'? Are you running a web server (on port 80 and 443)? If not, you need not be concerned given there's no listening process.
 
Mathew

---

### Post by pedja_portugalac on 2007-11-01
> **MJN said:**
> What do you mean by 'open'? Are you running a web server (on port 80 and 443)? If not, you need not be concerned given there's no listening process.
 
Mathew

That's the problem I don't understand. Why the shield up test failed and why it passed when I was on feisty? I have just installed firestarter, security updates and noscript plugin for Firefox. Firestarter is configured the same way it was on Feisty but when I check visibility of all ports on shield up site it say ports 80 and 443 are open, all the others are stealth. I don't think that Gutsy is running server out of the box and I don't know how to make those ports stealth using firestarter gui? Somebody can help please? :(

---

### Post by DarkN00b on 2007-11-01
Is there any particular reason you need Firestarter to be running all the time? It is not a firewall, all it does is configure iptables. I run it when I want to check on things, then kill it.

---

### Post by pedja_portugalac on 2007-11-01
> **DarkN00b said:**
> Is there any particular reason you need Firestarter to be running all the time? It is not a firewall, all it does is configure iptables. I run it when I want to check on things, then kill it.

I am not able to configure iptables by myself. That's why I use firestarter. But I am learning at this moment iptables configuration cause I would like to have completely invisible computer for any ping-ponger out there. :confused:I have learned about linux security from this community forum [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) and I am not sure if you are doing right not firewalling all the time you are connected to the internet. Be careful if you are doing important things on your machine. First step to break somebody's computer security is to find that he exist and that's why we should try to hide all the time we are connected to the internet. That's my opinion. :)

---

### Post by MJN on 2007-11-01
All Darkn00b is saying is that he's killing Firestarter, i.e. GUI 'frontend' for creating rules with iptables. Hence, he's still got the firewall in the background as it were.

Note I don't use iptables or Firestarter so I'm making the assumption that those rules created by Firestarter persist after you've closed it down (sudo iptables -L would verify this).

If your Shields-Up scan is saying port 80 and 443 is 'open' then that means it got a response on those ports which in turn suggests you've got services running on them. What's the output of **netstat -l **?

Mathew

---

### Post by pedja_portugalac on 2007-11-01
> **MJN said:**
> All Darkn00b is saying is that he's killing Firestarter, i.e. GUI 'frontend' for creating rules with iptables. Hence, he's still got the firewall in the background as it were.

Note I don't use iptables or Firestarter so I'm making the assumption that those rules created by Firestarter persist after you've closed it down (sudo iptables -L would verify this).

If your Shields-Up scan is saying port 80 and 443 is 'open' then that means it got a response on those ports which in turn suggests you've got services running on them. What's the output of **netstat -l **?

Mathew

pedja@pedja-laptop:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN     
udp        0      0 *:32768                 *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:mdns                  *:*

Or maybe You want a whole output?

---

### Post by MJN on 2007-11-01
And the Shields-Up test still shows 80 and 443 as open ports? How is your PC connected to the Internet? Is there a router in between you? Perhaps it's that that's responding on those ports.

That's the problem with some of these tests - they can be interpreted in different ways and they often flag up 'warnings' in big red boxes when often the wrong context has been assumed.

Mathew

---

### Post by pedja_portugalac on 2007-11-01
> **MJN said:**
> And the Shields-Up test still shows 80 and 443 as open ports? How is your PC connected to the Internet? Is there a router in between you? Perhaps it's that that's responding on those ports.

That's the problem with some of these tests - they can be interpreted in different ways and they often flag up 'warnings' in big red boxes when often the wrong context has been assumed.

Mathew

I am connected to the wifi hotspot in my hotel?
Maybe You are right, it must be because of this situation. Do you think it's secure consulting bank account or so from the connection like this one?

---

### Post by MJN on 2007-11-01
Ah, right, that indeed might have something to do with it!

The issue here is that you are likely sitting behind a NAT i.e. you get given a private IP address and all your incoming/outgoing traffic is being sent via the hotel's Internet connection. To do this requires them translating your address, as well as everyone elses, into a single public address and it is this address that ShieldsUp is actually testing.

You should be okay accessing your bank account assuming they use https as the data between you is being encrypted end-to-end.

Mathew

---

### Post by DarkN00b on 2007-11-02
> **MJN said:**
> All Darkn00b is saying is that he's killing Firestarter, i.e. GUI 'frontend' for creating rules with iptables. Hence, he's still got the firewall in the background as it were.

Note I don't use iptables or Firestarter so I'm making the assumption that those rules created by Firestarter persist after you've closed it down (sudo iptables -L would verify this).

If your Shields-Up scan is saying port 80 and 443 is 'open' then that means it got a response on those ports which in turn suggests you've got services running on them. What's the output of **netstat -l **?

Mathew

That's exactly what I'm saying. Firestarter is _not_ a firewall. Once you have used it to configure iptables, it does not need to be running. IPtables is actually your firewall (packet filter).

Believe me, I never go online with no firewall.

---

### Post by MightyMe on 2007-11-15
I have the same problem on my Gutsy. I think a bug needs to be filed somewhere.

---

### Post by m0rk on 2007-11-15
I agree. I had been interested in pursuing this further but some of the 'elder' posters were more hung up on telling me about ntp protocol and rubbing my nose in my perception of timeliness of connection to that service.

It's still happening and I have yet to see any signs of the issue being pushed forward.

I'm rather disappointed in the overall response to the problem and have essentially given up on following it through to an end.

I filed a bug through another means and have yet to hear any thing about it.

Good luck.
mb

---

### Post by MJN on 2007-11-15
Mork,

No need to throw your toys out of the pram just because you didn't get the answers you'd hoped for. We're a friendly bunch here and everyone tries their best to help but unless we can reproduce the error/fault then this is one of those situations that it's difficult, if not impossible, to offer any concrete advice.

Your original post contained two distinct queries - firestarter shutting down and the unexplained UDP traffic that you were observing. This latter issue was addressed but you flatly (and somewhat rudely IMHO) refused to accept the diagnosis and in doing so showed your ignorance of how NTPD works. The subsequent responses were offered to explain it in more detail as we all stand to benefit by sharing this knowledge. It's bad form to ask for help and throw it back in our faces just because it wasn't what you wanted to hear.

Going back to what it evidently your biggest concern (understandably) of firestarter shutting down you've done the right thing in looking for solutions and having found none filed a suspected bug. Post the bug ID then others who are in the same boat can add confirmations that they are witnessing the same and finger's crossed the developer/maintainer may be able to act on the reports and, through asking for further information as required, attempt to work towards a solution.

As frustrating as it might be don't give up simply because a quick solution you were hoping for isn't forthcoming - to do so is a strategy that is sure to cause you severe pain in the world of Linux - patience and perseverence is everything!

Good luck,

Mathew

---

### Post by m0rk on 2007-11-15
> **MJN said:**
> Mork,

No need to throw your toys out of the pram just because you didn't get the answers you'd hoped for. We're a friendly bunch here and everyone tries their best to help but unless we can reproduce the error/fault then this is one of those situations that it's difficult, if not impossible, to offer any concrete advice.

Your original post contained two distinct queries - firestarter shutting down and the unexplained UDP traffic that you were observing. This latter issue was addressed but you flatly (and somewhat rudely IMHO) refused to accept the diagnosis and in doing so showed your ignorance of how NTPD works. The subsequent responses were offered to explain it in more detail as we all stand to benefit by sharing this knowledge. It's bad form to ask for help and throw it back in our faces just because it wasn't what you wanted to hear.

Going back to what it evidently your biggest concern (understandably) of Firestarter shutting down you've done the right thing in looking for solutions and having found none filed a suspected bug. Post the bug ID then others who are in the same boat can add confirmations that they are witnessing the same and finger's crossed the developer/maintainer may be able to act on the reports and, through asking for further information as required, attempt to work towards a solution.

As frustrating as it might be don't give up simply because a quick solution you were hoping for isn't forthcoming - to do so is a strategy that is sure to cause you severe pain in the world of Linux - patience and perseverence is everything!

Good luck,

Mathew

You're entire reply is nothing but rude. I seriously doubt you have any form of actual public interaction and level of customer service satisfaction. Your knowledge is marred by your inability to constructively educate with out insult ("ignorant" I am not) and further the transfer of that knowledge to others. 

In this case, I am the "Customer" here, and the first rule of customer service, regardless of truth or not: the "Customer" is always right. Even if, by virtue of swallowing your pride, you need to tell to them to go to hell in such a manner they actually enjoy the ride. You've done that, but the wrong way. Which is why I don't really care about the problem any more.

As far as the issue with Firestarter, it's a problem. We've had numerous people reply to this thread with the same issue in regard. That should say some thing.

Thanks, once again, for making this more of a personal attack than an actual issue being addressed. Who cares if I was wrong about NTP, you made your point. 

Now you're just kicking at a dead horse. Essentially stepping over a dollar to pick up a dime.

---

### Post by MightyMe on 2007-11-15
Opps, I dont want to get caught in the middle here :) I just want say that some bugs regarding Firestarter has been filed here:

[http://bugzilla.gnome.org/buglist.cgi?query=firestarter](http://bugzilla.gnome.org/buglist.cgi?query=firestarter)

So it may very well be solved before we know it....i hope.

---

### Post by m0rk on 2007-11-15
> **MightyMe said:**
> Opps, I dont want to get caught in the middle here :) I just want say that some bugs regarding Firestarter has been filed here:

[http://bugzilla.gnome.org/buglist.cgi?query=firestarter](http://bugzilla.gnome.org/buglist.cgi?query=firestarter)

So it may very well be solved before we know it....i hope.

Hey, thanks. I might have been one of those submissions. I think it was a day or two after I posted here that I went to bugzilla and filled out a report. There were a couple of replies at the time with the same issue. There was a simple work-around suggestion and confirmation that certain functions that may have led to the crash. Yet to be determined at the time, though.

Thanks for the heads-up! :)

---

### Post by SeanHodges on 2007-11-15
> **m0rk said:**
> You're entire reply is nothing but rude. I seriously doubt you have any form of actual public interaction and level of customer service satisfaction. Your knowledge is marred by your inability to constructively educate with out insult ("ignorant" I am not) and further the transfer of that knowledge to others. 

In this case, I am the "Customer" here, and the first rule of customer service, regardless of truth or not: the "Customer" is always right. Even if, by virtue of swallowing your pride, you need to tell to them to go to hell in such a manner they actually enjoy the ride. You've done that, but the wrong way. Which is why I don't really care about the problem any more.

As far as the issue with Firestarter, it's a problem. We've had numerous people reply to this thread with the same issue in regard. That should say some thing.

Thanks, once again, for making this more of a personal attack than an actual issue being addressed. Who cares if I was wrong about NTP, you made your point. 

Now you're just kicking at a dead horse. Essentially stepping over a dollar to pick up a dime.

I felt compelled after reading this thread to comment on this particular post. Sorry Mork but I believe that MJN was nothing but courteous. The only comment that could have been interpreted as rude was: "in doing so showed your ignorance of how NTPD works.", but under the context of the rest of this post I don't believe it was intended in this way.

You have had some good responses here, perhaps not immediate solutions (yet), but constructive ones.

You are not a customer, you are a member of a community. If this forum is too informal for your tastes, I recommend you pay for customer support from Canonical, but I do suggest you change your attitude if you decide to continue to use this forum.

---

### Post by m0rk on 2007-11-15
> **SeanHodges said:**
> I felt compelled after reading this thread to comment on this particular post. Sorry Mork but I believe that MJN was nothing but courteous. The only comment that could have been interpreted as rude was: "in doing so showed your ignorance of how NTPD works.", but under the context of the rest of this post I don't believe it was intended in this way.

You have had some good responses here, perhaps not immediate solutions (yet), but constructive ones.

You are not a customer, you are a member of a community. If this forum is too informal for your tastes, I recommend you pay for customer support from Canonical, but I do suggest you change your attitude if you decide to continue to use this forum.

I give up. I'll just wait until the update arrives. I see no sense in arguing with you people. 

Thanks for making more of it than what it actually was. 

HAND. :)

---

### Post by tech9 on 2007-12-21
> **SeanHodges said:**
> You are not a customer, you are a member of a community. If this forum is too informal for your tastes, I recommend you pay for customer support from Canonical, but I do suggest you change your attitude if you decide to continue to use this forum.

not trying to be rude to mork, but I completely agree with SeanHodges... if you paid for ubuntu then you would be a customer - but it is free!

---

### Post by m0rk on 2007-12-21
> **tech9 said:**
> not trying to be rude to mork, but I completely agree with SeanHodges... if you paid for ubuntu then you would be a customer - but it is free!

yeah, hey, that's why the word "Customer" was in quotes. I know it's free.

---

### Post by Floppyjoe on 2007-12-23
I am experiencing the same problem with 7.10
Here is output from the terminal window when run in the terminal.
> ***MEMORY-ERROR***: firestarter[9437]: GSlice: assertion failed: sinfo->n_allocated > 0
Aborted (core dumped)
and> Segmentation fault (core dumped)

and
> ***MEMORY-ERROR***: firestarter[11004]: GSlice: assertion failed: sinfo->n_allocated > 0
Aborted (core dumped)

and
> ***MEMORY-ERROR***: firestarter[11318]: GSlice: assertion failed: sinfo->n_allocated > 0
Aborted (core dumped)

...etc

I leave the firestarter on to monitor things in realtime.

---

### Post by SeanHodges on 2007-12-23
Floppyjoe it sounds like your particular problem is similar to this:

[https://bugs.launchpad.net/firestarter/+bug/120445]("https://bugs.launchpad.net/firestarter/+bug/120445")

One possible workaround is to run Firestarter as follows (taken from launchpad link above):

```
G_SLICE=always-malloc gksu /usr/sbin/firestarter
```

People have had varying degrees of success with this approach, be sure to post your experiences in the report.

---

