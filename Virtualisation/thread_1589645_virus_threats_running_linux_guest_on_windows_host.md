---
title: "virus threats running linux guest on windows host"
date: 2010-10-06
forum: Virtualisation
---

### Post by madoldfart on 2010-10-06
I realise that no one is safe from virus or malware but
 
1) Are you less prone to virus threats when using linux on a windows 7 host.

2) Also im guessing that i need to install windows antivirus software if i was to run windows 7 on a linux host - is this true

---

### Post by HermanAB on 2010-10-08
Howdy,

Windows always has issues with malware and you have to take all regular precautions even if it is a VM.  The only real solution is to quit using Windows.

---

### Post by tech7 on 2010-10-08
I hear a lot of talk about discontinuing use of windows to resolve virus/malware issues.  
While I don't personally care much for windows, I still have to use it quite a bit for work.  
I had tried a little experiment about two and a half years ago where I had completely quit using anti-virus software on all my windows machines.  Uninstalled every installation of AV software.
Can you guess what happened?
-NO MORE VIRUSES-
And that's crazy for me, too.  Because I am constantly d/l'ing somewhat risky torrents and installing questionable installations on my windows machines.  I honestly abuse the crap out of them, and have had absolutely no problems with viruses and whatnot since I did away with AV software all together.
So, something I wonder; as most linux and apple users I know do not use AV software, and myself and one other person that I know of does not use it on windows.  All said people no longer having issues with viruses; 
Is it actually Windows OS's that inspire malicious attacks or the software that we are told protects against these things???  According to what I've seen, it is the latter.  But irregardless, I would still suggest that anybody stop using windows, ubuntu's better.  sry for the long post.  I got on a soapbox..

---

### Post by madoldfart on 2010-10-08
Interesting thoughts tech, i enjoy linux and only use windows for gaming.

---

### Post by tech7 on 2010-10-09
Sorry I got off subject back there.

So, you plan to either use a win7 to host a linux box or host a win7 box on a linux machine for the purposes of gaming via win7?

I do something similar to that for some of my web development software.  One of the applications that I use is a hefty install.  But, irregardless I haven't bothered to make any prophylaxis preparations to protect the win7 box because if for some reason I get it all messed up; 7 is a real quick install and a piece of cake to configure my preferred settings.

BUUUT, to get back to your question.  Using a linux box on a windows host is still using a windows host.  I'm assuming that you are still going to be connecting to WWW, and if not, I wouldn't worry about it.
And vice versa on a linux machine running win7.  If your still using tcp/ip to connect to www in your box, then it's just like if you were only running a windows OS in your comp, at least while you are in your box.  If you are worried about the windows 7 os that is installed in your virtualbox, I would install antivirus software on whatever installation that you are using to execute applications that have came from or interface with www.

---

### Post by e79 on 2010-10-09
From my personnal point of view, if you run Windows 7 in a Virtual Machine ONLY to play games (no downloads, risky surfing or nothing), you can safely avoid the A/V. But if you do browse and work or hold sensible data with this VM, I would suggest installing an Anti-Virus.  The Linux hosts itself doesn't really need an A/V but you can still download one through the Software Center (ClamTK).

Just my $0.02

---

### Post by tgm4883 on 2010-10-09
> **tech7 said:**
> I hear a lot of talk about discontinuing use of windows to resolve virus/malware issues.  
While I don't personally care much for windows, I still have to use it quite a bit for work.  
I had tried a little experiment about two and a half years ago where I had completely quit using anti-virus software on all my windows machines.  Uninstalled every installation of AV software.
Can you guess what happened?
-NO MORE VIRUSES-

And that's crazy for me, too.  Because I am constantly d/l'ing somewhat risky torrents and installing questionable installations on my windows machines.  I honestly abuse the crap out of them, and have had absolutely no problems with viruses and whatnot since I did away with AV software all together.
So, something I wonder; as most linux and apple users I know do not use AV software, and myself and one other person that I know of does not use it on windows.  All said people no longer having issues with viruses; 
Is it actually Windows OS's that inspire malicious attacks or the software that we are told protects against these things???  According to what I've seen, it is the latter.  But irregardless, I would still suggest that anybody stop using windows, ubuntu's better.  sry for the long post.  I got on a soapbox..

Full disclosure: I work for a big yellow AntiVirus company. 

To respond to your thoughts. How did you know you didn't have a threat on the machine?(We don't call them viruses anymore, there are too many different types so we tend to be more specific on the naming with things like trojan, worm, rootkit, etc) 

Were you monitoring different system resources? Did you analyze what was running on the machine? Did you query what connections were being made across the network/Internet?

Unlike the 90's, the main purpose of most threats is no longer destruction. It is to obtain sensitive data in order to make money. Big money. The unsophisticated threats pop up a fake antivirus alert trying to trick you into buying fake software. Those work against unknowing users and are pretty easy to spot. The sophisticated ones run in the background never alerting you to their presence on the machine. They quietly send your private data back to the attacker when you order something over the web or log into your banking site. These are harder to find, but if you are doing regular network auditing and traffic analysis you can discover the infection, see whats running on the machine and remove it. The really sophisticated ones intercept calls to the kernel and alter the reply so <insert OS here> doesn't even know the files are on the machine.

My point is you said you had "NO MORE VIRUSES", but how did you know? Most threats I have to remove try their hardest not to be seen and use the least amount of resources. After all, if you find you are infected and remove the threat the attacker no longer gets your data.

You imply that the AV companies are doing something malicious and using tactics to get people to buy the software. The truth is there are too many malicious people in the world trying to make  a quick buck.

---

### Post by tgm4883 on 2010-10-09
Sorry that last post was kinda off topic but I felt the need to respond to that post.


As to the OP. You aren't going to be less prone to threats in either of those scenarios. What matters is what you are using the Windows 7 machine for.

---

