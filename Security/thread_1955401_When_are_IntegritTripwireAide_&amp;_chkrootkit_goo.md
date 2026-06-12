---
title: "When are Integrit/Tripwire/Aide &amp; chkrootkit good to use &amp; when are they too much?"
date: 2012-04-09
forum: Security
---

### Post by CottonCandy on 2012-04-09
I know that the number one security flaw in any system is the user, and most attacks are social engineering or browser/email based, so the best things to do are to educate myself, secure Firefox, configure the firewall to allow only the ports I need, and set up AppArmor profiles to confine applications. Would adding things like an intrusion detection system and/or rootkit hunter be overkill, or are they good things to have & use periodically?  

I imagine the answer probably depends on how one uses their computer, so in your opinion, what sort of computer usage “requires” (or at least makes it a a good idea to have) an intrusion detection system and/or rootkit hunter?  

**For example:** Person A, B, C, and D all have set the firewall to allow only the ports they need, installed and enforced the default AppArmor profiles, and use Firefox with NoScript, Ad-Block, and cookie managers to allow only cookies they choose and delete flash (lso) cookies. 

**Person A **checks email and occasionally browses the web. The rest of their computer activity is offline - things like listening to music and playing games from Ubuntu's Software Center. 

**Person B** frequently browses the web and checks email, goes on Facebook/other   social networks, watches TED talks & select YouTube videos, downloads files from various websites, uploads files   to their website, and does things like banking and filing taxes  online.  Their files may contain sensitive financial info. They may   occasionally use instant message programs and/or Skype, and play online   games. 

**Person C** frequently browses the web and checks email, goes on Facebook/other   social networks, chats with friends online and/or using instant message   programs, uses Skype, downloads files from various websites and torrent   sites and shares them with their friends, updates their blog or  tumblr,  watches funny videos on YouTube and comments on them, and plays  all  sorts of online games. They frequently use Wine to play games  and  use programs that don't run on Ubuntu. 

**Person D** frequently browses the web and checks email, goes on Facebook/other   social networks, chats with friends online  and/or using instant message   programs, uses Skype, downloads files  from various websites, watches YouTube videos, and plays online   games. They also frequently use Wine to play games  and  use programs that don't run on Ubuntu. They have several computers and have are setting one up to be a server. 

In which, if any, of these situations is installing a HIDS such as Integrit/Tripwire/Aide and a rootkit hunter a good idea? In which is it unnecessary? 

    From what I've read if someone really wants to get into your computer, they will. I imagine if they saw intrusion detection and/or rootkit hunter files, rather than a deterrent, it would make them more curious about what is on your computer. Do you agree or disagree?

---

### Post by Ms. Daisy on 2012-04-10
You're asking for a risk analysis.  The answer to your question is you employ the security tools that are necessary for you to achieve the level of security you have deemed necessary and achievable on your system. 

Maybe a better way to answer your question is for you to better understand what HIDS and rkhunter (and whatever tool you're considering) will do and not do for you when you're exhibiting the behavior you outlined.  

> **For example:** Person A, B, C, and D all have set the firewall to  allow only the ports they need, installed and enforced the default  AppArmor profiles, and use Firefox with NoScript, Ad-Block, and cookie  managers to allow only cookies they choose and delete flash (lso)  cookies.  I hope they're also updating their systems routinely, using strong passwords, and only running services that they need (see the [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity") for my recommendations).

However, if you're running a server, the answer is a little simpler I believe. Yup, HIDS and rkhunter are tools you should consider installing.

---

### Post by spynappels on 2012-04-10
> **Ms. Daisy said:**
> However, if you're running a server, the answer is a little simpler I believe. Yup, HIDS and rkhunter are tools you should consider installing.

And also learn to use them, so false positives can be spotted and logs can be interpreted correctly. Without this, they can do more to feed paranoia than keep you safe.

---

### Post by CottonCandy on 2012-04-10
> **Ms. Daisy said:**
> You're asking for a risk analysis.  The answer  to your question is you employ the security tools that are necessary  for you to achieve the level of security you have deemed necessary and  achievable on your system. 
I didn't think posting "here's  exactly what I do online, how do I secure my system" was a very secure  idea. :wink:  But yes, in a roundabout way I am attempting to determine what is  nessecery for my needs. Just asking what sort/level of usage would make  HIDS/rootkit hunters a good idea didn't get a response so I added an  example. But I think you've somewhat answerd my question:  
> **Ms.  Daisy said:**
> However, if you're running a server, the answer is a  little simpler I believe. Yup, HIDS and rkhunter are tools you should  consider installing. 
So HIDS and  rootkit hunters are a bit much for the average user and intended more for those  running servers. That makes sense. However, (I think this was discussed  in the security for newbies thread) using things like SSH or VNC turns  your computer into a server even if you don't realise that, yes? 

So  in my example, HIDS/rootkit hunters are unnecessary for Person A, and  may be a good idea for Person D. What about B and C? If in addition to  regular (browser-based) downloading and uploading of files, Person B  uses SSH &/or FTP while Person C uses BitTorrent or another torrent  program, would it be good for both of them to look into HIDS and/or  rootkit hunters? SSH is a server type program so it is likely a  good idea for Person B, correct? What about Person C? 
      
> **Ms. Daisy said:**
> I hope they're also updating their systems  routinely, using strong passwords, and only running services that they  need (see the [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity") for my recommendations).
I have read the Basic Security Wiki (and the thread!) and  found it very helpful. I think it should be a sticky here in the forums,  even if it's just a singe post with nothing but a link to the Wiki. I'm  going to put a link to it in my signature here when I reach the required level of  posts. :smile: 
> **spynappels said:**
> And also learn  to use them, so false  positives can be spotted and logs can be  interpreted correctly. Without  this, they can do more to feed paranoia  than keep you safe.
Thank you for the good advice. :) I completely agree. As I mentioned above, I know that I am the number one security flaw so the best  thing to do is educate myself about security. Starting this discussion is one way of doing that. (I am also reading and trying things myself, but sometimes I have questions that I'd like to get answers to from actual people.)

---

### Post by needhelppeeps on 2012-04-10
Threats to the integrity of data should be a principle concern of home users. For example, you might not notice your family picture collection was suffering loss of integrity unless system files were also impacted. An integrity checking routine could be useful and does not require a lot of maintenance. Integrity checking is an effective method of detecting malware but to securely maintain and monitor the database requires commitment. One thing I like to do is create a baseline of performance, processes, resource usage, and so on. I can then refer back to the baseline to see if a process has been recently added or recently began consuming more resources. Another area home users often take for granted is the ability to recover from a disaster using a tested backup system utilizing multiple media sources. By the time an attacker realized you were using an integrity checking system, they'd already be inside so I think it's a non-issue. I'd be more concerned about threats from component failure, theft, or water/fire/impact than from Internet based attackers on a normal desktop without any extra services added. Thus far there seems to be few web exploits effecting Ubuntu users but that could change at any time. I would definitely use no-script, limit browser addons to those needed, and create apparmor profiles, though. A bit off topic, but there are a lot of poorly secured wireless routers out there. A new client of mine told me their wireless was secure. I found it had WEP turned on.

---

### Post by CottonCandy on 2012-04-11
Checking the integrity of files is what the HIDSs do, correct? Don't they only check system files because user files are likely to  change often?
> **needhelppeeps said:**
> By the time an attacker realized you were using an integrity checking  system, they'd already be inside so I think it's a non-issue.
I'm going to count that as vote 2 for "HIDS/rootkit hunters are not necessary for the average user". 

I agree it is good to regularly backup your files, use AppArmor and extensions like NoScript, and properly secure your router. 

I still wonder though if using things like SSH/FTP/torrent  programs turns your computer into a server, does that mean you should look into HIDS and/or rootkit hunters? Does it depend on what you are doing with those services? If you take proper steps to secure the service(s) should you still look into HIDS and/or rootkit hunters?

---

### Post by Ms. Daisy on 2012-04-11
Did you read these?

[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

I think a lot of what you're wondering about is discussed in bodhi's stickies.

From the Security Sticky:
> The two most common cracks posted on these forums are ssh and vnc, both running with password authentication.

If you wish to run these services, please secure them.

[LIST]
[*]In the case of ssh, use keys (and disable password  authentication) and either configure iptables or use a service such as  denyhosts or fail2ban (both are in the repositories).
[*]In the case of VNC, either tunnel it over ssh, use FreeNX, or use VPN.
[/LIST]

---

### Post by CottonCandy on 2012-04-11
I'm starting to think I'm not very good at asking clear questions... :(

Yes I have read both of those stickies. I know to use a strong password, always backup my files, keep Ubuntu updated, use AppArmror, set up the firewall, secure Firefox by changing settings and using Request Policy, NoScript, Better Privacy, an ad-blocker, and a cookie manager, learn to read log files so I know what is normal and what is not, and use only the services I need and learn to secure them. 
If I set up SSH or VNC I will certainly follow bodhi.zazen & others' advice to secure it. (use keys, disable passwords, etc.)

What I am wondering is,  
**When is following the above steps enough?** (Adding HIDS/rootkit hunters would likely be more for peace of mind than a necessary security measure.)
and [B]
When is just following the above steps probably not enough?[/B] (Adding HIDS/rootkit hunters would be a good idea.)

The consensus seems to be that if one is not using SSH/VNC one is likely  fairly secure by following the above suggestions and adding  HIDS/rootkit hunters would likely be unnecessary. What about** someone who does use SSH and/or VNC?** Is following just the above steps probably enough in that situation or is following just the above steps probably NOT enough? Does it depend on what you are doing when using those services? 

**Are HIDS/rootkit hunters mainly intended for corporations and people in (or interested in) the computer/information security field? **

I get that they're unnecessary for the average user, but **what about a freelancer or small business owner? **

**I am very well aware that the answers I get will be purely opinions and  that I must decide for myself what my tolerance for risk and acceptable  balance between usability and security is. **As I said before I  know that the number one security flaw in any system is the user, and  the best  thing I can do  is educate myself about security. But there is only so much one can  learn from reading. Reading can tell me how things work and how to  secure them, but I have not come across anything so far that says  HIDS/rootkit hunters are suggested for x type of computer usage. And that is why I'm posting here. I am trying to figure out what type of computer usage HIDS/rootkit hunters are unecessery for and what type of computer usage may make it a good idea to have HIDS/rootkit hunters. 

*EDIT: I know this is not a one-size-fits-all kind of thing, that's why I stated that I am aware that I am asking for people's opinions. I also understand that it is hard to determine what type of computer usage may require a HIDS/rootkit hunter, and that is why I have tried to provide examples and be as clear as possible. *

I really hope I'm being more clear this time. I'm not really sure how else to ask this question...

---

### Post by Ms. Daisy on 2012-04-11
LOL- I just wrote a really long and (I dare say) inspired reply. But I lost it because it took me so long to write that I got automatically logged out. :-({|=

So here's what I remember about my deleted thoughts:

Sorry if I frustrated you.  The problem is that your questions require an expert's advice. And I'm no expert.  I can give you my slightly educated opinion for whatever it's worth since you seem to really want it.

Here we go.

If you're a typical desktop user then IMO the tools in the title are more trouble than they're worth.  The basic security wiki is probably enough for a typical user, and I've heard numerous arguments that there's some overkill in it.  Based on your own comments in this thread, it's clear that you understand the risks of dowloads and torrents.  AFAIK, security tools are designed to keep people out, they're not designed to protect you from yourself.  So if someone insists on risky behavior, the only antidote I know is to have good backups so they can reinstall when they get burned.

If you're a small business owner/ freelancer using a desktop then your information is way more valuable to you.  So more security might be a good idea.  Frequent and multiple backups stored in several physical locations are definitely a good idea.  

If you're running any kind of server (file, email, web...) that faces the internet, then you obviously need more security to prevent unauthorized access.  If you use ssh only inside of your LAN then less is probably necessary.  If you use ssh over the internet then more's probably necessary.  But I can't say how much because I've only just begun using ssh myself.  All I can say is that the security sticky has served me well with ssh so far.

You won't find anyone to tell you definitively "HIDS/rootkit hunters are suggested for x type of computer usage" because that is a risk assessment and there are too many variables. You have listed computer use and services in your examples, but what about the value of the information stored on the hard drive? And how much time do you have to devote to learning and using the tool? How much money will it cost to deploy and run it?  And will the costs outweigh the results?  Read [this]("http://www.sans.org/reading_room/whitepapers/auditing/data-centric-quantitative-computer-security-risk-assessment_1209") and [this]("http://www.sans.org/reading_room/whitepapers/auditing/introduction-information-system-risk-management_1204") for more (they are pdfs).

That's the best I've got.

---

### Post by CottonCandy on 2012-04-11
Sorry to hear the forum logged you out & ate your first post. Thank you very much for taking the time to respond so many times Ms. Daisy, you have been very helpful. :) 

I think your last post answered my question. In general, for the average person, HIDS/rootkit hunters are likely not necessary. If you use SSH or VNC or run any kind of server, you should probably consider using HIDS/rootkit hunters. And if you are a freelancer or small business owner it is up to you to determine your level of risk and what you are willing and able to do to secure your system. 

And of course, regular backups are always a good idea.  

I found this particularly helpful: 

> **Ms. Daisy said:**
> what about the value of the  information stored on the hard drive? And how much time do you have to  devote to learning and using the tool? How much money will it cost to  deploy and run it?  And will the costs outweigh the results?  Read [this]("http://www.sans.org/reading_room/whitepapers/auditing/data-centric-quantitative-computer-security-risk-assessment_1209") and [this]("http://www.sans.org/reading_room/whitepapers/auditing/introduction-information-system-risk-management_1204") for more (they are pdfs).

Knowing we need to figure out what our level of risk is and what we are willing and able to do to put that at an acceptable level is one thing, knowing exactly HOW to do that is another. You provided some very useful tips on that. Thank you! 

Marking this thread as [SOLVED]. 

And in response to this: 
> **Ms. Daisy said:**
> The basic  security wiki is probably enough for a typical user, and I've heard  numerous arguments that there's some overkill in it. 
Overkill? I completely disagree with that. I think it is a WONDERFUL guide to basic security and I can't think of a single section that should be taken out. I really do mean what I said before-there should be a sticky here in the forums with a link to the Basic Security wiki. Bodhi.zazen's stickies are filled with lots of good information, but are very hard to understand for new users. I really think anyone new to Ubuntu or new to computer security should read the wiki first before even looking at the current stickies. 

I think many of us decide to try Ubuntu because we've heard that linux is more secure than Windows and doesn't get viruses, and Ubuntu seems user friendly. But (as you mention in the wiki) just because linux is designed to be more secure and viruses for linux are rare does not mean that you can install Ubuntu and then safely go wherever you want online, click links in strange emails, and download a bunch of pirated movies & music. And when people find out that Ubuntu is not as secure "out of the box" as they thought, they may feel disappointed, annoyed, or even angry. If that is how they feel when they start looking for information here on the forum, I would much rather them find the link to the Basic Security wiki first and read bodhi.zazen's sticky afterwards. I wish I had found the Basic Security wiki first when I started looking for information on how to secure my computer. It probably would have saved me a lot of time and confusion. 

Well that got rather long... Should I post this in a new thread somewhere to suggest a post linking to the Basic Security wiki be made a sticky? :)

---

### Post by Ms. Daisy on 2012-04-11
> **CottonCandy said:**
>  I think many of us decide to try Ubuntu because we've heard that linux is more secure than Windows and doesn't get viruses, and Ubuntu seems user friendly. But (as you mention in the wiki) just because linux is designed to be more secure and viruses for linux are rare does not mean that you can install Ubuntu and then safely go wherever you want online, click links in strange emails, and download a bunch of pirated movies & music. ...people find out that Ubuntu is not as secure "out of the box" as they thought...

I just wanted to quote that so it showed up again on this forum ;)  We hear a whole lot of the opposite around here.  


As for being a sticky, there are a lot of resources available to Ubuntu users, the stickys in this forum, wiki.ubuntu.com, help.ubuntu.com, man pages, developer websites, countless blogs & tutorials...  I guess I see the forum as a way to point people to the correct resources. I don't see a need to repeat resources in multiple locations.  But I understand  your frustration - knowing where to find the correct resource for any particular issue took me a while when I was new to Ubuntu.  I still need help as I learn new stuff.

---

### Post by CottonCandy on 2012-04-12
No problem. :) 

Yes it can be difficult to find the information you're looking for in an understandable format. I tend to search here and using Ixquick/Startpage. But some people come straight to the forums. I'd like for those people to see [Basic Security]("https://wiki.ubuntu.com/BasicSecurity") (read this first) [Moderate to Advanced Security]("http://ubuntuforums.org/showthread.php?t=510812") (read this next). After all the Basic Security wiki was created to provide newbies with a clear, concise introduction to security and to tell them what to do to secure their system right now, and what things they can learn about later. I think a link to it in a sticky would be useful. But sticky or no sticky I can link to it in my signature once I reach 50 posts. ;)

---

### Post by rookcifer on 2012-04-16
Basically if you're running a desktop machine Tripwire/AIDE are overkill.  Chrootkit is worthless even on servers since no smart hacker is going to allow a mere rootkit scanner to detect his presence.  If he has root, he is God.

---

### Post by CottonCandy on 2012-04-16
Thanks for adding your thoughts. :)

---

### Post by JKyleOKC on 2012-04-18
Even though you've marked the thread as solved, I'll add my own opinion based on some 10 years of experience with Linux (not all with Ubuntu, which is not quite that old).

I do database recovery for customers worldwide, who upload their damaged files to my private FTP server. These files include, at times, full accounting data for the customer's business, patient health records for doctors' offices, and other highly sensitive information, so security is a most important consideration for me.

My initial installation of Linux included TripWire, which I configured to be pretty paranoid. Over the course of several years, I fine-tuned it so that it only told me about significant changes. I also, of course, took great pains to lock down the FTP server and make it as secure as possible, and learned to tweak iptables so as to have an effective firewall. However, I've never installed rkhunter or any other rootkit detection tools. My feeling about them is simple: once a rootkit is present, no software can be trusted, so they are a total waste of time. If the logs indicate the possibility of an invasion -- and I was invaded once -- I nuke everything and restore from backups.

However some five years ago I switched from my original Linux installation to Xubuntu, and did a fresh install since none of my older tools (including TripWire) were totally compatible with the new system. The old one was Red Hat based; Ubuntu is based on Debian. The differences are significant.

And that fresh install did NOT include TripWire. I felt I had not gotten enough information from it to justify the labor of configuring it again for the new system.

It might have alerted me to that one invasion, which happened after my changeover, but probably would not have been much if any sooner than did my daily inspection of /var/log/auth.log to see all logins.

So, as you've said, the real key is the personal attitude and commitment to checking things out. Nore that I'm the only user of my system, other than the customers who come in via the FTP server; if I had an entire family using the same machine, I might find TripWire still to be worthwhile since I could not trust everyone to be as paranoid about the Net as I am! The customers have no access to anything outside the server itself and are extremely limited there, so I do not consider them to be risks.

---

### Post by bodhi.zazen on 2012-04-18
> **JKyleOKC said:**
> Even though you've marked the thread as solved, I'll add my own opinion based on some 10 years of experience with Linux (not all with Ubuntu, which is not quite that old).

I do database recovery for customers worldwide, who upload their damaged files to my private FTP server. These files include, at times, full accounting data for the customer's business, patient health records for doctors' offices, and other highly sensitive information, so security is a most important consideration for me.

My initial installation of Linux included TripWire, which I configured to be pretty paranoid. Over the course of several years, I fine-tuned it so that it only told me about significant changes. I also, of course, took great pains to lock down the FTP server and make it as secure as possible, and learned to tweak iptables so as to have an effective firewall. However, I've never installed rkhunter or any other rootkit detection tools. My feeling about them is simple: once a rootkit is present, no software can be trusted, so they are a total waste of time. If the logs indicate the possibility of an invasion -- and I was invaded once -- I nuke everything and restore from backups.

However some five years ago I switched from my original Linux installation to Xubuntu, and did a fresh install since none of my older tools (including TripWire) were totally compatible with the new system. The old one was Red Hat based; Ubuntu is based on Debian. The differences are significant.

And that fresh install did NOT include TripWire. I felt I had not gotten enough information from it to justify the labor of configuring it again for the new system.

It might have alerted me to that one invasion, which happened after my changeover, but probably would not have been much if any sooner than did my daily inspection of /var/log/auth.log to see all logins.

So, as you've said, the real key is the personal attitude and commitment to checking things out. Nore that I'm the only user of my system, other than the customers who come in via the FTP server; if I had an entire family using the same machine, I might find TripWire still to be worthwhile since I could not trust everyone to be as paranoid about the Net as I am! The customers have no access to anything outside the server itself and are extremely limited there, so I do not consider them to be risks.

Words of wisdom, I agree 100 %

The only thing I would add is that you should learn to use Apparmor. When I run Ubuntu, I have an apparmor profile for all network aware applications.

---

### Post by CottonCandy on 2012-04-20
Thank you both. I very much appreciate the opinions of those who have more experience than I do.  It sounds like the conclusion is that learning about security and how computers work is much more helpful than anything else.   One of the reasons I like Ubuntu is because I have learned so much about computers from using it. It can be frustrating when a problem comes up but I always learn something new while figuring out how to solve it.

---

