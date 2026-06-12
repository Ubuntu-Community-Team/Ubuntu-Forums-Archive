---
title: "Ubuntu Servers Hijacked, Used to Launch Attack"
date: 2007-08-16
forum: Server Platforms
---

### Post by newbie2 on 2007-08-16
> Members of the Ubuntu colocation team suggest the attack could have begun with a Chinese IP address.
	
The Ubuntu community had to yank five of the eight Ubuntu-hosted community servers sponsored by Canonical offline Aug. 6 after discovering that the servers had been hijacked and were attacking other machines.
It was suggested during an IRC (Internet relay chat) meeting of the Ubuntu colocation team Aug. 14 that the source of the troubles might have been a Chinese IP address trying to log onto the servers by brute force "for a long time now it seems," said a participant. 
[http://www.eweek.com/article2/0,1895,2171318,00.asp](http://www.eweek.com/article2/0,1895,2171318,00.asp) 
:rolleyes:

---

### Post by koenn on 2007-08-16
not good.

---

### Post by Seisen on 2007-08-16
It just goes to show you that your server is only as secure as you make it and apparantly those were not.

---

### Post by koenn on 2007-08-16
True. 
I've seen too many "Ubuntu/Linux is sooo secure (so I don't have to pay attention to security)" style threads on these forums. And way too many "my computer got compromised" threads recently, as well.

---

### Post by p_quarles on 2007-08-16
I saw this on Slashdot, too. Apparently these servers (belonging to the LoCo teams) were running old school FTP daemons, and these were possibly to blame for the attack. They were also apparently running the no-longer-supported Breezy version of Ubuntu. 

I think the "Ubuntu is so secure" attitude comes from newcomers getting excited when they learn how hard it is to get a virus/trojan. Windows users are accustomed to that being the main threat. The second you start running services, though, it's a completely different story.

---

### Post by insane_alien on 2007-08-16
yeah, i hate it when people see something that is secure and then think it'll cover them in all situations. with enough tinkering in the right places you could probably make ubuntu LESS secure than windows. although, even with top notch security, it takes just 1 stupid mistake to negate all the wonderful gizmos.

---

### Post by p_quarles on 2007-08-16
> **insane_alien said:**
> yeah, i hate it when people see something that is secure and then think it'll cover them in all situations. with enough tinkering in the right places you could probably make ubuntu LESS secure than windows. although, even with top notch security, it takes just 1 stupid mistake to negate all the wonderful gizmos.
Wouldn't take much tinkering at all:
```
sudo mv ~/username/bank_info/* /var/www/
```
:-)

---

### Post by insane_alien on 2007-08-16
heh, i meant stuff like having an easy to guess root password, only using your root account and having nearly everything open to the outside.

---

### Post by netlogic on 2007-08-16
Why do security folks still debate about where the IP range came from? The destination address information is totally meaningless in the today's world. Today's kids own so many zombie machines thanks to stupid folks using Windows and OSX who love to pirate applications. Hey, ssh runs on every platforms now and those zombies are everywhere. That's why without the security policy in place, no OS can save you.

---

### Post by koenn on 2007-08-16
> **netlogic said:**
> Today's kids own so many zombie machines thanks to stupid folks using Windows and OSX who love to pirate applications. 
About those stupid people ...
Apparently Ubuntu's userbase has expanded enough to also include stupid people that run publically accessible servers without applying basic security.

---

### Post by Seisen on 2007-08-16
That is just ignorance on their part a lot of people have no idea what computer security really is about. Look at all the people that click on those links for paypal or ebay and their banks that they get in a email  and then give their information out. 

I think Ubuntu does a good job security wise on the Desktop because you don't have to worry about malware/spyware and virii. Now on the other hand server security is a completely different story since a lot of people really have no idea on how to secure their server because it is easy to just install LAMP and be off to the races. Also thier are so many guides on how to setup servers but the key element they lack is how to secure them properly.

---

### Post by netlogic on 2007-08-16
Hello, Mr.Koenn. I am not sure if I am starting to enjoy your sarcasm. It isn't dry enough. It is kind of wet. 

These days, only thing you have to do is recompile the Windows CD using nlite and other servicepack streaming applications to create a new iso and load it on the bittorrent sites. Probably create few thousands zombies within a month. If people are going to pirate an OS, I don't understand why they don't bother check all the library for timestamp and MS signatures for every dlls. If they are going to bother pirating an OS, they better take pre-cautions. Let's don't even bother getting into running a IRC client and ssh server as a rootkit app in Windows. The worst part is people pirate firewall, malware detection, other security apps, and anti-virus. That is like purchasing stolen combination lockers. All of them login into IRC, listening to commands without users knowing about it.

---

### Post by Seisen on 2007-08-16
They don't check it because they probably have no idea how to nor do they care all they want is a pirated version of Windows.

---

### Post by eentonig on 2007-08-16
I'm the first to say to newcomers

"Don't bother configuring a firewall or installing a virusscanner......as long as you don't install server software"

---

### Post by netlogic on 2007-08-16
The reality is you can lock down the Windows box pretty hard, but it is tons of work. I was working on an application to lock down the Windows box few years ago, but I really don't have any motivations to do anything for Windows project.  Anyway, Blackhat hackers are mostly social engineers. There is no such a thing as a simple application hacking. I haven't read the article yet, but I bet they installed a sniffer in the weakest link somewhere in the same network. That's why I never use FTP servers. People tend to use the same passwords for different applications and servers.

---

### Post by koenn on 2007-08-16
> **netlogic said:**
> Hello, Mr.Koenn. I am not sure if I am starting to enjoy your sarcasm. It isn't dry enough. It is kind of wet. 

These days, only thing you have to do is recompile the Windows CD using nlite and other servicepack streaming applications to create a new iso and load it on the bittorrent sites. Probably create few thousands zombies within a month. If people are going to pirate an OS, I don't understand why they don't bother check all the library for timestamp and MS signatures for every dlls. If they are going to bother pirating an OS, they better take pre-cautions. Let's don't even bother getting into running a IRC client and ssh server as a rootkit app in Windows. The worst part is people pirate firewall, malware detection, other security apps, and anti-virus. That is like purchasing stolen combination lockers. All of them login into IRC, listening to commands without users knowing about it.

How a machine gets zombified is of no interest to me. Whether it's because stupid (your words) people download compromized Windows iso's or because stupid  (my opinion) Ubuntu serveradmins
run a pile of unpatched web software on an outdated and unpatched operating system doesn't really matter : it's the ignorance/stupidity of the people involved that results in a zombie machine. 
[https://lists.ubuntu.com/archives/loco-contacts/2007-August/001510.html](https://lists.ubuntu.com/archives/loco-contacts/2007-August/001510.html)

I found it rather strange that you'd emphasize the stupidity of the Windows users, but ignored the responsibility of the Ubuntu sysadmins, and I choose to ignore your remarks about my sarcasm and its alledged humidity.

---

### Post by p_quarles on 2007-08-16
It kind of bothers me, too, that these were the LoCo team servers. I mean, yes, there are plenty of Ubuntu users who don't have a clue about security, but you'd think these folks would. 

Of course, these were eight machines being operated by numerous admins, so I guess it takes just one weak link.

---

### Post by netlogic on 2007-08-16
> **p_quarles said:**
> It kind of bothers me, too, that these were the LoCo team servers. I mean, yes, there are plenty of Ubuntu users who don't have a clue about security, but you'd think these folks would. 

Of course, these were eight machines being operated by numerous admins, so I guess it takes just one weak link.

Most people don't want to worry about the psychology aspect of security. Everyone is looking for a software solution. The security isn't a software. The security is always a policy. If one machine is installable somehow, it is pretty easy to get the rest of information if there are no administration policy in the place. Everyone says firewall, firewall, firewall... Who cares if your front door is made from a steel if the rest of the house is made from glass. The app patching is like 10% of security.

---

### Post by koenn on 2007-08-16
> **p_quarles said:**
> It kind of bothers me, too, that these were the LoCo team servers. I mean, yes, there are plenty of Ubuntu users who don't have a clue about security, but you'd think these folks would. 
exactly. 

And then this one :
> The servers have not been upgraded past breezy due to problems  with the network card and later kernels.  This probably allowed the attacker to gain root.
They choose to remain on an unpatched and unsupported OS version because of an incompatible NIC ? There was absolutely no other  sollution, such as getting a compatible NIC ? 
What were they thinking ?

---

### Post by p_quarles on 2007-08-16
> **netlogic said:**
> Most people don't want to worry about the psychology aspect of security. Everyone is looking for a software solution. The security isn't a software. The security is always a policy. If one machine is installable somehow, it is pretty easy to get the rest of information if there are no administration policy in the place. Everyone says firewall, firewall, firewall... Who cares if your front door is made from a steel if the rest of the house is made from glass. The app patching is like 10% of security.
Hmm. The glass/steel analogy seems like a bad analogy for the point you're making, since neither glass nor steel is a "policy."

I don't know where you got 10%, but I agree that there is no single cause, here. It looks like a bunch of things:
1) FTP servers
2) Bad passwords for those FTP servers
3) Unpatched software
4) Outdated hardware
5) Lazy and/or underqualified admins

EDIT: @koenn: That was the most confusing part. I mean, a perfectly good NIC *retails* at US$15. Silliness.

---

### Post by netlogic on 2007-08-16
Many 100% patched servers get hacked all the time. The whole patched and unpatched idea isn't always the cause of security failures.The network to physical designs all affect everything. There are so many variables. Just to point out things weren't patched, so that is the result of being not patched isn't the answer. It could have been the million different things. If they really wanted to find out, they should have dd the drive to a different drive and start inspecting the changing of the files. It is too late now. I guess we never know. It isn't always the network services that make the security weak.
[B][I]
My comment about Windows users was about you can't determine any forensic results by the source ip address.[/I][/B]

---

### Post by p_quarles on 2007-08-16
> Just to point out things weren't patched, so that is the result of being not patched isn't the answer.
I don't think anyone said that old software was the sole reason the servers got broken into. But: using an OS with known vulnerabities is kinda asking for trouble. 

When we know that there were certain obvious, documented security  vulnerabilites on a system that got attacked, it's doesn't really meet the requirements of parsimony to say "it could have been a million different things." There were things they weren't doing. Maybe someone broke into the data center and made themselves a shiny new root user. "Maybe" doesn't let them off the hook for not doing things they should have.

---

### Post by santy_kushwaha on 2007-08-16
i read the whole article and found out that it was not the ubuntu is un-secure from now or it is a bad linux version it is just that they were not up to date with the security patches and they had a easy root password... so we can't help it all is there problem

---

### Post by netlogic on 2007-08-16
> **p_quarles said:**
> I don't think anyone said that old software was the sole reason the servers got broken into. But: using an OS with known vulnerabities is kinda asking for trouble. 

When we know that there were certain obvious, documented security  vulnerabilites on a system that got attacked, it's doesn't really meet the requirements of parsimony to say "it could have been a million different things." There were things they weren't doing. Maybe someone broke into the data center and made themselves a shiny new root user. "Maybe" doesn't let them off the hook for not doing things they should have.

I agree, but saying unpatched servers got hacked might not have been the issue. Like I SAID, only way to find out was to clone the drive and check for issues. *Not all hacks are based around network services.* Hey, you can even write a port scanner with a java running off a browser.

---

### Post by HermanAB on 2007-08-16
I repair one or two hacked servers per year.  All it takes is one idiot who thinks it is cool to create a 4 character password.  

OK, the other ingredient is a sysadmin who doesn't enforce password checking...

---

### Post by bapoumba on 2007-08-17
[http://www.linuxtoday.com/security/2007081603526NWDBSV]("http://www.linuxtoday.com/security/2007081603526NWDBSV")

---

### Post by BrokeBody on 2007-08-17
Ubuntu productions servers hacked beyond recognition had to be taken offline, as a desperate measure to stop attacks launched from the machines running the compromised Canonical distribution of the Linux open source operating system. There is a good reason why Microsoft is applauding Windows Vista as the most secure Windows platform available on the market. And in this context, while Vista has got the client side covered, Windows Server 2008 will do the same for the server side, nothing short of the security performances synonymous with its predecessor Windows Server 2003. But while both Linux and the Unix based Mac OS X are perceived as delivering superior security to Windows, a total of five out of eight Ubuntu production servers were shut down because of the poor security conditions.

[Read more...](http://news.softpedia.com/news/Ubuntu-Linux-Is-Nothing-Compared-to-Windows-Vista-or-Windows-Server-2008-62977.shtml)

---

### Post by ZipoTe on 2007-08-17
**./trash**, just move there windows vista and server :-P

---

### Post by lingnoi on 2007-08-17
I thought these were community maintained servers running **breezy badger**. I fail to see how you can compare this incident to Windows Vista. Breezy Badger was discontinued and is no longer supported with security updates. 

If a Windows 95 server got hacked would we be comparing it to Ubuntu Gutsy?

> a total of five out of eight Ubuntu production servers were shut down because of the **poor security conditions**.
They were logging into the servers using unencrypted passwords, what would anyone expect the same would have happened on any operating system.

---

### Post by curuxz on 2007-08-17
is there any verification of this story from a more reliable source?

---

### Post by Hallvor on 2007-08-17
Bad security will compromise any system.

---

### Post by Spr0k3t on 2007-08-17
This article is FUD.  They covered the bare facts.  They left out a gregarious bit so as to spin the article in favor of their preferred platform.  Just a quick glance at the first paragraph will tell you the article is FUD: "There is a good reason why Microsoft is..."

Lingnoi has hit the nail dead on.

Feel free to bury it as inaccurate: [http://digg.com/microsoft/Ubuntu_Linux_Is_Nothing_Compared_to_Windows_Vista_or_Windows_Server_2008](http://digg.com/microsoft/Ubuntu_Linux_Is_Nothing_Compared_to_Windows_Vista_or_Windows_Server_2008)

---

### Post by koenn on 2007-08-17
> **curuxz said:**
> is there any verification of this story from a more reliable source?
[https://lists.ubuntu.com/archives/loco-contacts/2007-August/001510.html](https://lists.ubuntu.com/archives/loco-contacts/2007-August/001510.html)

some discussion already took place at [http://ubuntuforums.org/showthread.php?t=527020](http://ubuntuforums.org/showthread.php?t=527020)
you'll find it a lot more balanced, and accurate, than the OP here.
(and let's keep it that way)

---

### Post by BrokeBody on 2007-08-17
> **lingnoi said:**
> I fail to see how you can compare this incident to Windows Vista. Breezy Badger was discontinued and is no longer supported with security updates. 


I'm  not comparing this to any ****. I just posted the news, dammit! :roll:

---

### Post by mctavish on 2007-08-17
Running ftp is a bit poor, but not the end of the world.

The big deal is running outdated, unpatched software. On an internet facing server, this equals ownage.

I think canonical needs to work far closer with the community in many ways. The  automatix debacle is a prime example.

---

### Post by darrenm on 2007-08-17
Shock horror. My Ubuntu server got hacked because I set a user up with the same password as username and enabled SSH. I'd better go and install Windows then.

---

### Post by az on 2007-08-17
> **mctavish said:**
> 
The big deal is running outdated, unpatched software. On an internet facing server, this equals ownage.

And Canonical immediately offered to move those sites to in-house, supported servers.

> **mctavish said:**
> 
I think canonical needs to work far closer with the community in many ways. The  automatix debacle is a prime example.

Huh?  First of all this is not a question of Canonical not working with the community, but of a Canonical-sponsored third-party hosting provider not providing state of the art service.  Secondly, Automatix would be completely integrated into Ubuntu if it were not for it's (automatix') leadership.

---

### Post by mctavish on 2007-08-17
I acknowledge my statement was a bit provocative, maybe I'm in a mood :) 

Keeping servers up to date is not state of the art, it is a minimum level of competence for internet available servers.

I think that canonical should set standards for community groups. A bit like a company having a security policy on how their systems should be set up.

I also think that canonical and senior project contributors could spend more time amongst the masses, like in these forums, helping people do things the right way. There is alot of crappy advice around.

---

### Post by OffHand on 2007-08-17
> **curuxz said:**
> is there any verification of this story from a more reliable source?

[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue52#head-b009291e4151391137b8f04a53adea995d0ee280](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue52#head-b009291e4151391137b8f04a53adea995d0ee280)

---

### Post by vexorian on 2007-08-17
> **Spr0k3t said:**
> This article is FUD.  They covered the bare facts.  They left out a gregarious bit so as to spin the article in favor of their preferred platform.  Just a quick glance at the first paragraph will tell you the article is FUD: "There is a good reason why Microsoft is..."

Lingnoi has hit the nail dead on.

Feel free to bury it as inaccurate: [http://digg.com/microsoft/Ubuntu_Linux_Is_Nothing_Compared_to_Windows_Vista_or_Windows_Server_2008](http://digg.com/microsoft/Ubuntu_Linux_Is_Nothing_Compared_to_Windows_Vista_or_Windows_Server_2008)
yay my digg account finally gets an use.

---

### Post by PriceChild on 2007-08-17
*merged threads*

---

### Post by primski on 2007-08-17
> **vexorian said:**
> yay my digg account finally gets an use.

ditto :D

---

### Post by az on 2007-08-17
> **mctavish said:**
> 
I think that canonical should set standards for community groups. A bit like a company having a security policy on how their systems should be set up.

But this was a third-party hosting provider.  I think telling people they should not run unsupported software is a bit obvious.  In the end, who's responsability was it?  Did Canonical chose this company or was it chosen by the Loco teams?

> **mctavish said:**
> 
I also think that canonical and senior project contributors could spend more time amongst the masses, like in these forums, helping people do things the right way. There is alot of crappy advice around.

I think quality control is important and there are several methods of quality control in place.  But I don't think that making Canonical/Ubuntu developers offer support is particularly cost-effective or even needed.  If anyone, the Doc Team should handle that responsibility.

---

### Post by southernman on 2007-08-17
> **p_quarles said:**
> 

EDIT: @koenn: That was the most confusing part. I mean, a perfectly good NIC *retails* at US$15. Silliness.Not to try and out do you here, but in my LUG at least, trading/swapping/giving of hardware is a REALLY common occurrence, especially if it's of a mission critical nature.

Blatant comes to mind here.

---

### Post by netlogic on 2007-08-17
> **BrokeBody said:**
> Ubuntu productions servers hacked beyond recognition had to be taken offline, as a desperate measure to stop attacks launched from the machines running the compromised Canonical distribution of the Linux open source operating system. There is a good reason why Microsoft is applauding Windows Vista as the most secure Windows platform available on the market. And in this context, while Vista has got the client side covered, Windows Server 2008 will do the same for the server side, nothing short of the security performances synonymous with its predecessor Windows Server 2003. But while both Linux and the Unix based Mac OS X are perceived as delivering superior security to Windows, a total of five out of eight Ubuntu production servers were shut down because of the poor security conditions.

[Read more...](http://news.softpedia.com/news/Ubuntu-Linux-Is-Nothing-Compared-to-Windows-Vista-or-Windows-Server-2008-62977.shtml)

Good security is creating good network and system polices. If you believe click and run security exist in this world, you live in the another world we don't know about. Every time, new security technology comes out, people do their best to beat it. That means relying on technology to be secure isn't the solution. You will always need a good security policy. Until, MS develops the jailing of dlls, MS will never get there. Just like a breaking a personal firewall in MS os takes no effort for a good hacker. MS has no memory dll inspection. There is a good reason, 98% of mid to large companies don't run Windows as their corporate firewall. I doubt MS will take a risk and  run their dlls in a VM state. That will break everything. The current apps will all break. In case, you don't know, DLL can work like exe. Dll has no level control long as it has an admin privilege. It is just a system call. That means intruder can easily move dlls to any position in the operating system by moving the command calls to the registry. The line between OS and apps are very blur in the today's world now. Some say, Linux OS is only the kernel and everything else are apps in Linux, so it is superior, but that also means security administrative headaches for person who doesn't understand how OS functions. Another argument is Windows' integrations make it more secure. However, Windows make money by catering to 3rd party software companies and users, so if they don't allow others to modify their OS, they are no longer in the business. Just like Beta version of VISTA had kernel locking, but look what happened at the end when Symantec whined and bitched. Whole OS debate isn't worth discussing. The perfect secure OS doesn't exist. If it does, all sysadmins will work from 9 to 5.

---

### Post by julian67 on 2007-08-18
From everything I've read I'm still unsure what  these machines were serving. Did they host any repositories? Did they host any .iso images that people download? Is there a threat to Ubuntu users from compromised packages? Have any forum or mailing list accounts been compromised/exposed? I've gone through the mailing lists and forums and news reports and nobody from Canonical (or anywhere else) has explicitly stated what the servers hosted and if there has been any threat to the users. Anybody out there with some hard information that can be referenced/verified?

---

### Post by koenn on 2007-08-18
> **julian67 said:**
> From everything I've read I'm still unsure what  these machines were serving. Did they host any repositories? Did they host any .iso images that people download? Is there a threat to Ubuntu users from compromised packages? Have any forum or mailing list accounts been compromised/exposed?
no, 
no, 
no, and 
no.



info : 
[https://lists.ubuntu.com/archives/loco-contacts/2007-August/001510.html](https://lists.ubuntu.com/archives/loco-contacts/2007-August/001510.html)
[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue52#head-b009291e4151391137b8f04a53adea995d0ee280](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue52#head-b009291e4151391137b8f04a53adea995d0ee280)
[http://www.linuxtoday.com/security/2007081603526NWDBSV](http://www.linuxtoday.com/security/2007081603526NWDBSV)

(all links were already in this thread ... )

---

### Post by julian67 on 2007-08-18
> **koenn said:**
> no, 
no, 
no, and 
no.



info : 
[https://lists.ubuntu.com/archives/loco-contacts/2007-August/001510.html](https://lists.ubuntu.com/archives/loco-contacts/2007-August/001510.html)
[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue52#head-b009291e4151391137b8f04a53adea995d0ee280](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue52#head-b009291e4151391137b8f04a53adea995d0ee280)
[http://www.linuxtoday.com/security/2007081603526NWDBSV](http://www.linuxtoday.com/security/2007081603526NWDBSV)

(all links were already in this thread ... )
 
thanks for the reply. I had already read all those linked messages/pages but *nowhere* is it stated what content the servers hosted, what other malicious code might have been on there, who might have been exposed to it and so on.  As far as hard facts go all that is stated is that they were not in Canonical's data centre but were sponsored community servers and that 5 of them had been used to attack other machines. Can anybody say with any authority (i.e. 1st hand or verifiable knowledge) say what the servers hosted ?

---

### Post by p_quarles on 2007-08-18
> This last week, 5 of the 8 servers that are loco hosted but Canonical sponsored, had to be shut down due to reports that they were actively attacking other machines. These servers were found to [[IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] have a variety of problems]("https://lists.ubuntu.com/archives/loco-contacts/2007-August/001510.html") including, but not limited to, missing security patches, FTP (not sftp, without SSL) was being used to access the machines, and no upgrades past breezy due to problems with the network cards and later kernels. Loco teams will be given a choice to: a. migrate to the Canonical data center, or b. stay on the hosted/outsourced servers. Each option has its good and bad points. Jono Bacon has therefore called for a meeting to discuss these issues.
They hosted the loco teams' stuff. Loco = local community. These are advocacy groups, and they host web sites, mailing lists, etc. No Ubuntu users were compromised. The problem was that the machines were being used by bots to carry out attacks on other machines.

---

### Post by julian67 on 2007-08-18
> **p_quarles said:**
> They hosted the loco teams' stuff. Loco = local community. These are advocacy groups, and they host web sites, mailing lists, etc. No Ubuntu users were compromised. The problem was that the machines were being used by bots to carry out attacks on other machines.

If there are mailing lists, forums, CD mail out options then there is the possibilty of  Ubuntu users personal details, (loco) forum user names and passwords being compromised. I've looked at a few loco websites and they vary but all these are being done. I don't know what facilities were offered to users specifically accessing the  5 compromised servers because they are of course down right now. I would find it surprising if the servers being used by malicious unknown parties weren't harvested for personal information and even more surprising if there was no such information on any of those 5 servers, some of which  > were running an incredible
      amount of web software.

---

### Post by p_quarles on 2007-08-18
> **julian67 said:**
> If there are mailing lists, forums, CD mail out options then there is the possibilty of  Ubuntu users personal details, (loco) forum user names and passwords being compromised. I've looked at a few loco websites and they vary but all these are being done. I don't know what facilities were offered to users specifically accessing the  5 compromised servers because they are of course down right now. I would find it surprising if the servers being used by malicious unknown parties weren't harvested for personal information and even more surprising if there was no such information on any of those 5 servers, some of which  .
Which is why:
1) You shouldn't put important personal information on public web sites. 
2) You shouldn't use your system's root password for a forum account
3) You shouldn't pretend that any information you share with a public web site is private

This *wasn't* a devastating attack that's going to result in massive identity theft. It *is *an embarrassment for the people running those servers. If you shared important personal information with an insecure, unencrypted web site . . . well, that's just embarrassing for you.

---

### Post by julian67 on 2007-08-19
> **p_quarles said:**
> Which is why:
1) You shouldn't put important personal information on public web sites. 
2) You shouldn't use your system's root password for a forum account
3) You shouldn't pretend that any information you share with a public web site is private

This *wasn't* a devastating attack that's going to result in massive identity theft. It *is *an embarrassment for the people running those servers. If you shared important personal information with an insecure, unencrypted web site . . . well, that's just embarrassing for you.

Yes that's all true, the people responsible for admin of those servers should be extremely embarrassed.

---

### Post by julian67 on 2007-08-19
Finally a statement from Canonical

[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue53]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue53")

> The Canonical staff wishes to point out that this event had no effect on the code, packages, or CD's for Ubuntu.

---

### Post by lingnoi on 2007-08-20
> **BrokeBody said:**
> I'm  not comparing this to any ****. I just posted the news, dammit! :roll:

I wasn't trying to personally attack you. I was just commenting on the subject at large. Apologies if that is what you thought.

---

### Post by BrokeBody on 2007-08-23
Oh, no no no :D

---

