---
title: "Chinese Invasion ?"
date: 2009-03-16
forum: Server Platforms
---

### Post by mistypotato on 2009-03-16
Hello,

Today I was watching my router and modem and they were going to town (lights blinking) so I decided to see what was going on.

I saw from etherape that the IP address doing the data dance was based at an IP technology center in China.

I immediately disconnected from the Internet and blocked ALL IP addresses starting with 219.  (219.0.0.1 - 219.255.255.254)   Then I reconnected my Internet connection.

Then, I looked at my firewall logs and saw they tried several more times (unsuccessfully) to reconnect to Port 21 after the block.

Now, that leaves me a bit worried....what was all that data transfer going on ?  There is no trace of their IP in any logs on the server. :confused:

Is there a way they found a back door or something that wasn't logged?   If I type [ftp://(my](ftp://(my) server ip)
I get a connection refused message....so doesn't that mean the port they were trying to use was secure?

Being an IT firm, I'm sure they know ALL the tricks of the trade so I'm a bit concerned.

The auth logs are clean, fail2ban shows nothing....I'm baffled as to what they were doing (or able to do) and whether or not I should suspect a breach?

thanks

---

### Post by hictio on 2009-03-17
Sorry, I don't understand...
Your server is an FTP server? And you detected connections attempts from China?

---

### Post by HermanAB on 2009-03-17
Fail2ban helps but is not very good.  You'll notice oodles of posts about it, which should be a warning sign.  It is far better to use iptables rate limiting to block any and all brute forcers:
```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

Cheers,

Herman

---

### Post by windependence on 2009-03-17
<Yawn>

Seasoned webmasters see this stuff every day. We don't get excited like some of you guys. Unless they are breaking in, they can hit my firewall all they want. The packets are dropped anyway. Why worry? :)

-Tim

---

### Post by askreet on 2009-03-17
Rule of the internet:  If you're listening on a default port with known security threats on particular servers, people will try non-stop.

I've had really good success with fail2ban as far as ssh goes.  Why on earth are you using FTP?  Tsk, tsk.

Also, it's probably not a technology firm in China attacking you, it's probably a customer of theirs, or maybe they are an ISP.  Contrary to popular belief, China is not trying to take over the world (over the Internet, anyway.)

:)
- askreet

---

### Post by mistypotato on 2009-03-17
> **askreet said:**
>  Why on earth are you using FTP?  Tsk, tsk.
:)
t

That response is Soooo confusing to a newbie.  :(

Why am I using FTP?  :confused:

Is that a trick ubuntu question ?

Maybe vsftpd is for something other than what I thought it was for ?(seriously).

hep

---

### Post by hictio on 2009-03-17
> **mistypotato said:**
> That response is Soooo confusing to a newbie.  :(

Why am I using FTP?  :confused:

Is that a trick ubuntu question ?

Maybe vsftpd is for something other than what I thought it was for ?(seriously).

hep

No, it isn't aimed at VSFTPD (or any other FTP server package that you might use).
It is aimed at the protocol per se, which is insecure, because it transmits everything in clear text.
[FTP Security Problems](http://en.wikipedia.org/wiki/FTP#Security_problems)

If you can, you should migrate all that FTP setup to sftp.

---

### Post by windependence on 2009-03-18
You're better off using SCP for file transfer if it will not be a public FTP server. That is, Secure Copy, which works on the ssh protocol and is very secure as the name implies.

The traffic you were seeing since it was not showing in your logs on the server, was merely dropped packets at your firewall. Nothing to get excited about, but they WILL give you the impression that you lots of activity because the packets are acknowledged at the outside of the firewall and then simply dropped. Almost everyone I know who is new to web serving of any kind gets excited like this and I usually get calls saying they have been hacked. Trust me, they haven't, they are just seeing the "real" traffic that bombards the internet on a daily basis.

-Tim

---

### Post by mistypotato on 2009-03-18
> **hictio said:**
> No, it isn't aimed at VSFTPD (or any other FTP server package that you might use).
It is aimed at the protocol per se, which is insecure, because it transmits everything in clear text.
[FTP Security Problems](http://en.wikipedia.org/wiki/FTP#Security_problems)

If you can, you should migrate all that FTP setup to sftp.

Oh....ok.   It's an issue of encrypted vs non-encrypted.  Good idea.

thx

---

### Post by mistypotato on 2009-03-18
Tim,
What you don't know is that I just migrated from a total Windows environment to a total ubuntu/Linux environment.  The Windows environment became infected with conflicker and other nasty Windows malware.  I believe the origin was an infection that occurred on my network when a laptop was accidentally booted with WiFi ON and no WEP protections that I didn't discover for a few days..   (once one bug gets in it opens the door for others) In that environment, a hidden http server had been set up in the MBR sectors of each harddrive on all networked computers and was contacting 1000's of servers throughout the day and when I first noticed it, all I saw was the same thing.....TONS of blinking lights on the router and modem.   And my computer grinding to a halt.  There were no logs of that activity either....the malware covered it's tracks.  Since it wasn't using apache and instead set up it's own sockets and ports, it was able to circumvent most logging etc.  After trying about 8 different anti virus programs and spending countless hours on the phone with anti virus engineers, I realized they couldn't help.  Low Level formatting that set ALL the hard drives sectors to zero was the only cure.  Of, course, on drives with mapped bad sector tables, those tables had to be rebuilt with the manufacturers software.  Truly brilliant (as far as malware goes). This is a home office situation.  No IT experts available unfortunately :P

We all tend to expect stuff on our computers to work according to processes we understand and expect.  Hackers, really good ones, apparently think outside the box and circumvent the traditional and expected.  The reason anti virus programs are becoming so ineffective is that the hackers are becoming better at hooking system resources BEFORE the installed OS and our installed protections.  By the way, I use Watchguard Firebox firewalls and when you log into your firewall, your UN/PW "could" be intercepted and stored by a key logger for example.  One day as I was fighting these infections on one computer using Process Monitor from Trend Micro? I think?, I noticed that the settings kept getting changed to filter certain activity.   Clever.  These hackers are not kids any longer.  They are highly trained professionals who know FAR more than most of us.  Some are former government security experts etc.  

Until I realized WHERE the malware was located (MBR and low sectors on the drive), I kept reinstalling windows only to have the malware reappear).  Partitioning the drive and Installing ubuntu DID NOT erase the malware.  When I first installed ubuntu, the hidden HTTP servers were still at work (in ubuntu) and only after I realized the nature of the infection and LOW LEVEL formatted the drives, then reinstalled was I able to stop the hidden traffic.

While the infections do not appear to have been able to spread in ubuntu, the http servers in the MBR did appear to continue to work.

So I'm kinda jumpy now when the lights start blinking like that and I'm not doing anything ;)

> **windependence said:**
> You're better off using SCP for file transfer if it will not be a public FTP server. That is, Secure Copy, which works on the ssh protocol and is very secure as the name implies.

The traffic you were seeing since it was not showing in your logs on the server, was merely dropped packets at your firewall. Nothing to get excited about, but they WILL give you the impression that you lots of activity because the packets are acknowledged at the outside of the firewall and then simply dropped. Almost everyone I know who is new to web serving of any kind gets excited like this and I usually get calls saying they have been hacked. Trust me, they haven't, they are just seeing the "real" traffic that bombards the internet on a daily basis.

-Tim

---

### Post by aspergerian on 2009-03-19
mistypotato's elaboration in this thread is appreciated. 

Today's NYTimes has an update about the ongoing changes in Conflicker, now Conflicker C. Is Conflicker able to infect Linux computers having no Microsoft? 

Computer Experts Unite to Hunt Worm
By JOHN MARKOFF
Published: March 18, 2009
[http://www.nytimes.com/2009/03/19/technology/19worm.html](http://www.nytimes.com/2009/03/19/technology/19worm.html)

---

### Post by mistypotato on 2009-03-19
Thanks aspergerian.  I read the article myself.
Here's an excerpt...
[I]
The researchers, noting that the Conficker authors were using the most advanced computer security techniques, said the original version of the program contained a recent security feature developed by an M.I.T. computer scientist, Ron Rivest, that had been made public only weeks before. And when a revision was issued by Dr. Rivest&#8217;s group to correct a flaw, the Conficker authors revised their program to add the correction.[/I]

How many guys on this forum are MIT calibre computer security experts ;)

My advice to all is simply.......**think again**.

Is Linux safe from all this?  I think the answer is that it is directly proportional to the user base.
And even if so now....for how much longer? :popcorn:

---

### Post by cariboo on 2009-03-19
Have a look at this Wikipedia [article]("http://en.wikipedia.org/wiki/Conficker"). Check the first paragraph to see which OSs are affected.

Jim

---

### Post by aspergerian on 2009-03-19
> **cariboo907 said:**
> Have a look at this Wikipedia [article]("http://en.wikipedia.org/wiki/Conficker"). Check the first paragraph to see which OSs are affected.

Jim, Thnx for the wiki link, which I notice doesn't seem to be updated for Conflicker C - perhaps same limitation to MS products, perhaps not???

---

### Post by mistypotato on 2009-03-19
Jim,

thx for the article.

Regardless, I can tell you, as outlined in a previous post, that there was in fact a malicious http server installed and functioning in the MBR sectors of my ubuntu hard drive containing no MS OS's.

The fact that it may have gotten there while the Windows OS was installed on the drive does not completely resolve the issue that it was still working in the absence of Windows.  I think the sophistication of professional Internet criminals has evolved to the point of fully self sufficient encapsulated snippets that can be OS independent.  And why not?
Isn't java for the most part?

Just a thought.  I personally, believe Linux is more secure overall than MS OS products partially due to the fact that most attacks are aimed squarely at MS products.

---

### Post by windependence on 2009-03-19
You're probably not going to like me but this infection was your fault if you are the admin of those computers. This worm has been around since November 2008 and the simple fix is to make sure your machines are patched with the fix from Micro$oft. This is strictly a Micro$oft bug, using a vulnerability that was identified in November last year and a patch has been available since then. Here are some snippets from the web:

> [Users can protect themselves]("http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9126349") from the worm by installing Microsoft's MS08-067 security update, using strong passwords and disabling Windows' Autoplay and Autorun features.> **What machines are most vulnerable to Downadup attack?** According to Microsoft, unpatched Windows 2000, [Windows XP]("http://www.computerworld.com/action/inform.do?command=search&searchTerms=Microsoft+Windows+XP") and Windows Server 2003 machines are at the greatest risk to exploits of the bug patched in October. That gibes with reports from security companies, which have highlighted the danger to PCs running Windows XP Service Pack 2 and XP SP3. Not coincidentally, those versions account for the bulk of Windows' market share. 
 Unpatched Windows Vista and Server 2008 systems, meanwhile, are less likely to fall victim to attack, since hackers must have authenticated access to the computer, or in other words, know the log-in username and password. 



 Any Windows-powered machines, however, can be compromised by the worm's password and USB attack strategies. 
 **I'm running [Windows 7]("http://www.computerworld.com/action/inform.do?command=search&searchTerms=Microsoft+Windows+7") beta... am I safe?** According to the [Microsoft support document]("http://support.microsoft.com/kb/958644") that details the October patch, yes you are. 
 Microsoft offered the fix as a security patch to users of the Windows 7 "pre-beta," the version it gave developers in late October and early November. It then integrated the patch into Windows 7 before it [launched the public beta on Jan. 10]("http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9125660"). 
[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9126349](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9126349)

The above snippet underscores that it doesn't even affect Vista unless you turned off the security features. Besides the fact that it isn't a cross platform virus, even if it was, because of the way user permissions are set up in Unix/Linux, it would not work there as well. It's pretty well evident to me that although you were infected by this worm, you still haven't done much research on how to prevent it or remove it. There are now removal tools freely available on the web for this threat.

I have found no evidence that this worm does anything to the boot sector of the hard drive. On the contrary, it affects the Windoze Server service:

> The flaw lies in the [Windows Server]("http://www.computerworld.com/action/inform.do?command=search&searchTerms=Microsoft+Windows+Server") service, which is used to connect different network resources such as file and print servers over a network. By sending malicious messages to a Windows machine that uses Windows Server, an attacker could take control of the computer, Microsoft said. 
 Although firewalls would typically prevent this type of attack from spreading across the Internet, it could wreak havoc within corporate local area networks, much as the Zotob computer worm did back in 2005. 
 Zotob affected [Windows 2000]("http://www.computerworld.com/action/inform.do?command=search&searchTerms=Microsoft+Windows+2000") systems, but this bug is rated critical for three versions of Windows: Windows 2000, Windows XP and Windows Server 2003. It is rated as a less-serious flaw for Windows Vista and Windows Server 2008, which require additional authentication from computers on networks. 
[http://www.computerworld.com/action/article.do?command=viewArticleBasic&taxonomyName=spam,_malware_and_vulnerabilities&articleId=9117958](http://www.computerworld.com/action/article.do?command=viewArticleBasic&taxonomyName=spam,_malware_and_vulnerabilities&articleId=9117958)

Indeed, you WOULD see more activity on the router if infected with this bug because you have hidden servers on all your Micro$oft machines sending out communications to the zombie network.

Your fears about the Linux machines are unfounded, however, because they are immune to this attack as usual. IMHO anyone using Windoze on their servers and having them connected to the internet is nuts. On the desktop, of course, you may not have a choice, but there ARE ways to make sure your desktops are secure. I hesitate to say it, but this one looks like a case of sloppy administration.

To your comment about Java. Java IS cross platform, however, when implemented correctly, it runs in it's own sand box which eliminates the chance of spreading malicious code to the host box. An explanation of Java's architecture would be way too long for this forum so you will have to trust me on this, or do your own research.

I'm gonna call you out on your claim of a server running in your boot sector of your Linux hard drive. I don't think so. Prove it. What evidence do you have that told you what was going on?

Hopefully, you have learned a valuable lesson from this.

-Tim

---

### Post by mistypotato on 2009-03-30
So you are stating that other than "sloppy administration", it is impossible to "hack" a Linux installation.?

I have a question to that..........
Then why are there so many security patches constantly being released?  

Because flaws are found.  Not that the ubuntu coders are sloppy, but writing an OS is a VERY difficult thing no doubt.  And, hardware and the whole computing experience (Hardware, Software, Internet etc) is constantly evolving.  It's not static like some of the outdated examples you gave.  In addition to the OS, any of the thousands of applications that you install can introduce their own flaws that compromise security.
I guess I'm in good company....right along with the experts at Microsoft since we've both done some sloppy admin work and basically asked for these intrusions.

Proving to you that code had been written to my hard drive would require my finding the code and then copying the code for you to see. 
This would require extensive research.   Even the experts have trouble doing this and it is not likely something you could do either.   Because I could not eradicate the behaviors associated with the infection until a low level format was performed, it was logical that sectors of the drive that are not usually written to during normal sessions had been altered.

Was my pure ubuntu Linux installation being affected by malware in the MBR or low, non-data sectors of the hard drive?  I am not 100% sure.
I do know for sure that my ubuntu PC was attempting to connect with large numbers of IP addresses (estimated several hundred simultaneously) as shown by etherape.   So, I believe there was such an infection and I'll re-state that it was operating under Linux although I cannot be sure of it's origin.

Because I did at one point have Virtualbox installed, it is possible that the Windows installation therein became infected.  However, that installation was removed and even with VMWare removed the behavior persisted...additionally...even after wiping the drive with Acronis, and re-installing ubuntu.  No other hard drive or partitions. Again, only a LLF cleared the problem.  Could that malware have been written to that area of the disc under Linux?  I do not know.   If not now, as the Linux user community reaches fruitful mass (for hackers) I'm sure that will come about.

You place too much faith in virus scanners.  I recently heard or read that only 17% of malware is ever detected by detection software including Microsoft's which by the way was never ever able to detect the infection on my system.  I personally feel this is VERY accurate due to recent experience.

I believe time will prove you wrong.  Patches are not end-all cure-alls.  They simply correct an **exposed** flaw.  Your underestimation of the present day malware coders is going to eventually prove all my points to you for me.   I do not personally believe 100% computer security is a reality unless said computer is never connected to the Internet and no disc, or external data device is ever connected,   

If we look at this step by step logically then it becomes self evident.

1). Flaws exist in all distributions of Linux, including ubuntu.
(this is actually true of all OS'es.  None yet have been found perfect)
2). Patches are constantly being released to address those security holes...so anyone can easily ascertain that they do exist.  This is true of Windows as well as Linux distributions.
3). Hackers have used those flaws to gain access to Linux computers
4). The sophistication of hackers is on the rise.
5).  Internet crime has increased steadily over the last 5 years.
6).  A truly good hack leaves little trace of it's existence.


Conflicker has evolved many times since it first appeared and will likely evolve more.  The severity and ingenuity of these malware attacks is increasing.  Personally, I love ubuntu and will accept the security risks.
It is a remarkable OS in every aspect.

But your beliefs very much remind me of thinking once that also caused so called knowledgeable men to scoff at another concept they did not believe or understand at the time......that the world was not flat.

Also...Java is not 100% safe and secure as you state...
[One example for you]("National Cyber Alert System Technical Cyber Security Alert TA07-022A 	archive 	 Sun Updates for Multiple Vulnerabilities in Java")
[http://www.us-cert.gov/cas/techalerts/TA07-022A.html]("http://www.us-cert.gov/cas/techalerts/TA07-022A.html")

Your statements that it is only through sloppy administration that opens the door for problems is wrong.  Even the best admins (see Microsoft Development Team for example, See ubuntu Development team as example 2), can make errors and will never be able to cover every possible avenue of attack.  When they do, there won't be any more need for security updates.  Breath deep and hold.

Exactly what "lesson" did you think one could learn from this?  That I am a "sloppy" admin?  I am the best admin I can be or care to be and that will not significantly change tomorrow or the day after.  
There is no new lesson to be learned here.  It's the same old story.
Most computer users are not highly skilled admins.  we do the best we can and trust those providing the OS'es and software to keep the bad guys out.  Occasionally we stumble as do they.  I am not even sure that I did anything that you would not have given the same environment, goals or requirements.  If there IS one lesson I learned, it's that all these new malware entries have left the very best of the best "experts" guessing.   (Except for you that is).

Just continue believing everything that comes out of Seattle, or ComputerWorld etc and I'm sure you'll be fine.  

Good luck.

---

### Post by mistypotato on 2009-03-30
So you are stating that other than "sloppy administration", it is impossible to "hack" a Linux installation.?

I have a question to that..........
Then why are there so many security patches constantly being released?  

Because flaws are found.  Not that the ubuntu coders are sloppy, but writing an OS is a VERY difficult thing no doubt.  And, hardware and the whole computing experience (Hardware, Software, Internet etc) is constantly evolving.  It's not static like some of the outdated examples you gave.  In addition to the OS, any of the thousands of applications that you install can introduce their own flaws that compromise security.
I guess I'm in good company....right along with the experts at Microsoft since we've both done some sloppy admin work and basically asked for these intrusions.

Proving to you that code had been written to my hard drive would require my finding the code and then copying the code for you to see. 
This would require extensive research.   Even the experts have trouble doing this and it is not likely something you could do either.   Because I could not eradicate the behaviors associated with the infection until a low level format was performed, it was logical that sectors of the drive that are not usually written to during normal sessions had been altered.

Was my pure ubuntu Linux installation being affected by malware in the MBR or low, non-data sectors of the hard drive?  I am not 100% sure.
I do know for sure that my ubuntu PC was attempting to connect with large numbers of IP addresses (estimated several hundred simultaneously) as shown by etherape.   So, I believe there was such an infection and I'll re-state that it was operating under Linux although I cannot be sure of it's origin.

Because I did at one point have Virtualbox installed, it is possible that the Windows installation therein became infected.  However, that installation was removed and even with VMWare removed the behavior persisted...additionally...even after wiping the drive with Acronis, and re-installing ubuntu.  No other hard drive or partitions. Again, only a LLF cleared the problem.  Could that malware have been written to that area of the disc under Linux?  I do not know.   If not now, as the Linux user community reaches fruitful mass (for hackers) I'm sure that will come about.

You place too much faith in virus scanners.  I recently heard or read that only 17% of malware is ever detected by detection software including Microsoft's which by the way was never ever able to detect the infection on my system.  I personally feel this is VERY accurate due to recent experience.

I believe time will prove you wrong.  Patches are not end-all cure-alls.  They simply correct an **exposed** flaw.  Your underestimation of the present day malware coders is going to eventually prove all my points to you for me.   I do not personally believe 100% computer security is a reality unless said computer is never connected to the Internet and no disc, or external data device is ever connected,   

If we look at this step by step logically then it becomes self evident.

1). Flaws exist in all distributions of Linux, including ubuntu.
(this is actually true of all OS'es.  None yet have been found perfect)
2). Patches are constantly being released to address those security holes...so anyone can easily ascertain that they do exist.  This is true of Windows as well as Linux distributions.
3). Hackers have used those flaws to gain access to Linux computers
4). The sophistication of hackers is on the rise.
5).  Internet crime has increased steadily over the last 5 years.
6).  A truly good hack leaves little trace of it's existence.


Conflicker has evolved many times since it first appeared and will likely evolve more.  The severity and ingenuity of these malware attacks is increasing.  Personally, I love ubuntu and will accept the security risks.
It is a remarkable OS in every aspect.

But your beliefs very much remind me of thinking once that also caused so called knowledgeable men to scoff at another concept they did not believe or understand at the time......that the world was not flat.

Also...Java is not 100% safe and secure as you state...
[One example for you]("http://www.us-cert.gov/cas/techalerts/TA07-022A.html")

Your statements that it is only through sloppy administration that opens the door for problems is wrong.  Even the best admins (see Microsoft Development Team for example, See ubuntu Development team as example 2), can make errors and will never be able to cover every possible avenue of attack.  When they do, there won't be any more need for security updates.  Breath deep and hold.

Exactly what "lesson" did you think one could learn from this?  That I am a "sloppy" admin?  I am the best admin I can be or care to be and that will not significantly change tomorrow or the day after.  
There is no new lesson to be learned here.  It's the same old story.
Most computer users are not highly skilled admins.  we do the best we can and trust those providing the OS'es and software to keep the bad guys out.  Occasionally we stumble as do they.  I am not even sure that I did anything that you would not have given the same environment, goals or requirements.  If there IS one lesson I learned, it's that all these new malware entries have left the very best of the best "experts" guessing.   (Except for you that is).

Just continue believing everything that comes out of Seattle, or ComputerWorld etc and I'm sure you'll be fine.  

Good luck.

---

### Post by sailthesea on 2009-03-30
Guys 
Your enlightening discussion in this very public domain certainly made me wonder about the vulnerabilities of Linux vs Windows in the future

---

### Post by windependence on 2009-03-31
You wouldn't be wondering if you read the article. Apparently he/she didn't either. This is a WINDOWS worm. If you understand how these things work, you would quickly realize it cannot execute under Linux. 

There are so many assumptions and misquotes in the reply, I will have to address those later since it's after 4 am here. IF his/her Linux box was contacting hundreds of IPs as was stated, it wasn't because of conflicker. I have an idea what it was after re-reading the post and will comment later.

This worm is rendered useless IF the M$ patch (not anti-virus) had been applied. This is why we apply patches in linux. Just because the community finds a hole and patches it, doesn't mean it has been compromised. on the contrary, in almost all cases, the hole is found BEFORE there has been any hacks. THIS is the difference between OSS and Windoze. The only people that can find holes before they are exploited in Windoze is Micro$oft. This is because there is no source code to view, and no one can check it. With OSS, EVERYONE can review the code. That's why it's generally more secure, besides the fact that users don't run as admin in Linux. There is quite a bit the OP doesn't understand about this OS.

-Tim

---

### Post by mistypotato on 2009-03-31
The question(s) remain unanswered.....

So you are stating that other than "sloppy administration", it is impossible to "hack" a Linux installation?  That vulnerabilities are never found first by hackers?  That there is no way it could happen.

And further, that it is impossible for malicious code to reside and work from inside a Linux partition...specifically the boot sectors and/or MBR?

I am not in a position to say either way.  Only what appears to have happened on my own Linux installation.....with exceptions.

Of course there is a lot the OP does not know about this OS.
The OP has been using Linux for only several months now.  Most of the OP's discussions are in the form of questions based on scenarios interpreted one way or the other. The OP is recovering from a series of malware infections on Windows machines that did not entirely stop after switching to Linux...for whatever reason.

I wish I knew it all, but unlike others, I'm having to go on a lot of observations.  well, that and the fact that I've been working with computers in general since about 1977 and later starting with LDOS and QDOS. (just before there was MS DOS).  Up until about 1986, computer viruses were mostly unknown of course at the time.
In 1985 when I ran my first "BBS"  which was up and available 24/7 with no firewalls, anti-virus etc at all.

I would love to learn that Linux (specifically ubuntu) is bulletproof as far as hackers are concerned.  However, like many, my fear is that many like you may have become overconfident simply because Linux has never been the real target of the more advanced hack attempts due to the fact that the Windows userbase far exceeds the Linux userbase and is therefore the target of choice.

Windependence may be misjudging my curiosity as something else.

You need not resort to accusations or assumptions about others abilities.
If you have solid information to offer, please do.   Someone learning a new OS is probably better described as  "untrained" than sloppy.

Sloppy implies lazy.   I have been anything but lazy in my attempts to learn to secure my ubuntu installations.  It's a lot to digest in a short time.

---

