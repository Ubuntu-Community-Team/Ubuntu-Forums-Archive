---
title: "AV? or NO AV? that is the question."
date: 2014-03-30
forum: Security
---

### Post by gabriel13 on 2014-03-30
Right, a stupidity which I find often on forums and articles online is that Linux is a virus free OS...and the subsequent distros following with the same claim.
Due to this people often get confused whether they need an AV or not, and the reasons for having an AV, although quite valid, still leave much unanswered.
So let me clarify a couple myths about any linux distro, Ubuntu included.

**_1._** Yes, it is possible for a virus to infect a Linux machine. And Linux virii do exist.Now, the problem here is that it is virtually UNLIKELY that YOU will get infected. 
Reasons being that most viruses are meant to exploit windows faults, therefore there are very few virii which actually work on linux. 
Also linux is very distro specific, each distro has its own packaging method, e.g. deb, rpm, ipk etc... 
This creates another problem for the virus, it would have to be created to target a specific distro, or group of distros, thus limiting itself, windows doesn't have this problem. 
Constant updates help minimize the chances that a well supported distro will be infected. 
And last but not least a common Linux user is generally more experienced than a common windows user, therefore the Linux user would be able to suspect and avoid infected files with greater ease.

**_2._** No, AV software do NOT only scan for windows virii.
They scan for any virus whose signature is in its database, and those which do heuristic scanning can scan even more, this doesn't matter what OS the virus is targetting.

**_3._** No, you do not ONLY need an AV if you share files with windows machines. You need an AV on any machine which accesses the internet, independently of the OS.
Although it is true that if you catch a windows virus it will not affect you, but whoever you share it with, it is not the ONLY reason as to why you need an AV software.
The real-time scanning feature may be unnecessary, but a powerful AV should be installed in case of emergencies, and occasional scanning.
The scan will clean both the widows virii and any Linux virii which you might have picked up.

_**Conclusion:**_
AV software are a must in any OS. But on Linux distros you will be using them less frequently. You do not need real-time protection, but carry out regular scans, e.g. Once a month.  Both to make sure your box is clean and to keep your windows friends virus free.

---

### Post by unspawn on 2014-03-31
> **gabriel13 said:**
> So let me clarify a couple myths about any linux distro, Ubuntu included. Ah, deities be thanked, we're saved!..   > **gabriel13 said:**
> virii Since you're clarifying it's good to know only VXers use "virii" (which isn't even proper Latin): the plural is "viruses".    > **gabriel13 said:**
> viruses are meant to exploit windows faults No, *exploits* make use of flaws: viruses *infect*.    > **gabriel13 said:**
> Also linux is very distro specific, each distro has its own packaging method, e.g. deb, rpm, ipk etc...  No, that's distro-specific modifications to software, a packaging method would in no way hamper or benefit a virus.   > **gabriel13 said:**
> Constant updates help minimize the chances that a well supported distro will be infected.  No, it wont: *sane practices (like browsing habits)* could have an effect.   > **gabriel13 said:**
> And last but not least a common Linux user is generally more experienced than a common windows user, therefore the Linux user would be able to suspect and avoid infected files with greater ease. No, they're simply not: most are just *users* half of which aren't even remotely aware they run Linux these days.   > **gabriel13 said:**
> No, AV software do NOT only scan for windows virii. They scan for any virus whose signature is in its database, and those which do heuristic scanning can scan even more, this doesn't matter what OS the virus is targetting. No, the OS does matter, that's simply a money thing ;-p    > **gabriel13 said:**
> The real-time scanning feature may be unnecessary, but a powerful AV should be installed in case of emergencies, and occasional scanning. No, realtime scanning (in whatever way) actually is helpful.   > **gabriel13 said:**
> The scan will clean both the widows virii and any Linux virii which you might have picked up. Is that a fact?.. Can you show us a sample of a Linux ELF infection and a perfect cleanup?..   > **gabriel13 said:**
> AV software are a must in any OS. But on Linux distros you will be using them less frequently. You do not need real-time protection, but carry out regular scans, e.g. Once a month.  Both to make sure your box is clean and to keep your windows friends virus free. While it certainly is worth something protecting lesser OSes, focusing on AV and viruses is (IMHO and with all due respect) Windows-centric thinking: with Linux you need to: - keep your OS up to date, - have sane browsing and software habits, - secure, harden and regularly audit your machine(s) as the threats we face are different from what users of "the other OS" experience.  Please focus on *that* instead.

---

### Post by ant2ne on 2014-03-31
Is it possible that the OP is confusing viruses with other forms of malware? Too often all malware is lumped into the category of virus. On a windows system I've seen viruses that then download other forms of malware. And your 'anti-virus' product is capable of cleaning up executable application based and java based types malware. Both of those things help blurr the lines of what exactly a true virus is. But I completely disagree. I've never run any "anti-virus" product on my linux workstations. My browsing habits are not the safest and I've never gotten a "virus". I have gotten this pop up once which showed my C:\ drive getting scanned and finding multiple malware hits. I thought that pretty funny since I don't have a C:\. I suppose that pop up could be considered malware.

EDIT:
Here is a good read [http://en.wikipedia.org/wiki/Computer_virus]("http://en.wikipedia.org/wiki/Computer_virus") Check out the section titled "Vulnerability of different operating systems to viruses" where the author says > In 1997, researchers created and released a virus for Linux&#8212;known as "Bliss".[23] Bliss, however, requires that the user run it explicitly, and it can only infect programs that the user has the access to modify. Unlike Windows users, most Unix users do not log in as an administrator user except to install or configure software; as a result, even if a user ran the virus, it could not harm their operating system. The Bliss virus never became widespread, and remains chiefly a research curiosity. Its creator later posted the source code to Usenet, allowing researchers to see how it worked.[24]

---

### Post by lisati on 2014-03-31
> **ant2ne said:**
> Is it possible that the OP is confusing viruses with other forms of malware? Too often all malware is lumped into the category of virus
Sounds a bit like some of my workmates, some of whom like to use their browser's default page's search box to get to Facebook. No doubt we could, if we chose, spend some time discussing bloopers of this type.
> I have gotten this pop up once which showed my C:\ drive getting scanned and finding multiple malware hits. I thought that pretty funny since I don't have a C:\. I suppose that pop up could be considered malware.
:D And then there's the ones which claim that your PC is slow, with a similar offers of software to download.

---

### Post by ant2ne on 2014-03-31
> And then there's the ones which claim that your PC is slow, with a similar offers of software to download. Right, and a registry cleaner.

---

### Post by PartisanEntity on 2014-04-01
Well you might disagree with this, but I clean the registry in Ubuntu at least once a month. I find the machine runs faster afterwards.

---

### Post by ant2ne on 2014-04-01
:lolflag: ^^ this guy

---

### Post by SeijiSensei on 2014-04-01
My only encounter with malware was an attempt to get me to buy [Antivirus 2010]("http://www.enigmasoftware.com/antivirus2010rtk-removal/"), and this came from the New York *Times*'s website!  When I closed a tab that contained the infected article, a window that looked very much like Windows Explorer appeared on my screen and began rattling off the number of infected DLL files it "found" on my machine.  After I finished laughing, I tracked it down to a Javascript that was delivered alone with the article I was reading.  Times readers like me were [not happy]("http://www.nytimes.com/2009/09/15/technology/internet/15adco.html") to see the Grey Lady distributing malware, but the source was some third-party advertising channel, not the paper itself.  They have since become more restrictive about third-parties, and I have not seen a repeat of the problem.

Note that this type of malware relies on the browser and user stupidity.  The operating system had nothing to do with it.

---

### Post by ant2ne on 2014-04-01
Are you sure it came from the Times? I mean, if I were to write something like that it would have a timer delay on it so sometime after you navigated away the thing would pop up thus making it harder to track what page attacked you. Then you wouldn't know who to contact about it. The webmaster remains unaware that it has been exploited. Leaving the vulnerability up longer to get more victims.

---

### Post by Xentime on 2014-04-01
> **PartisanEntity said:**
> Well you might disagree with this, but I clean the registry in Ubuntu at least once a month. I find the machine runs faster afterwards.

:lolflag: This put the biggest smile on my face.


But back on topic:
> **unspawn said:**
> While it certainly is worth something protecting  lesser OSes, focusing on AV and viruses is (IMHO and with all due  respect) Windows-centric thinking: with Linux you need to: - keep your  OS up to date, - have sane browsing and software habits, - secure,  harden and regularly audit your machine(s) as the threats we face are  different from what users of "the other OS" experience.  Please focus on  *that* instead.
I could not agree more to this statement. Trained browsing/software habits go a long way. I personally don't run any anti-virus on my Windows machine, but I do have Malwarebytes for on-demand scanning and malicious website blocking. Haven't had a single infection yet, but please keep in mind I wouldn't advise this to anyone unless you have well trained browsing/software habits.

All the anti-virus ruckus is really a Windows-centric approach and quite dated (in my opinion), these days it is easier to exploit weaknesses in third-party software be it click-jacking or drive-by attacks, let alone this usually allows you to attack multiple operating systems at once. Less work, more pay.

---

### Post by gabriel13 on 2014-04-01
Great got a conversation going :D Purpose of creating thread successful. *happy*

Well...now correcting bad terminology, I am sorry but yes ant2ne you are right, I meant general malware, not specifically viruses. That is my mistake for using the wrong word.

But to unspawn well...you sure picked my argument apart XD I will try to address every issue you have stated so far to the best of my understanding.

> **unspawn said:**
> Ah, deities be thanked, we're saved!..

Applause on the sarcasm, well placed.

> **unspawn said:**
>  Since you're clarifying it's good to know only VXers use "virii" (which isn't even proper Latin): the plural is "viruses".

Well...then again bad terminology from my part, I am sorry, but I am sure you understood what I meant there so no harm done.

> **unspawn said:**
>  No, *exploits* make use of flaws: viruses *infect*.

Malware must always find a way into your machine, this can only be achieve either if you are extremely stupid and have bad browsing practices or if there is a fault on your machine which allows the virus to enter the machine, install where it shouldn't have, do what it shouldn't be allowed to do etc...
The reason I specify this is because generally this is blamed on faulty programming which allows the malware to exploit the fault and do what it is meant to. An example could be a machine whose root permissions are accessible by a malware even though the OS tried to limit root access.

Exploits and shellcode are code, just like malware is code, if a malware is coded to take advantage of an fault it will, doesn't matter if it is an exploit or a malware it depends on what the code was written to do, this is generally called the payload.

> **unspawn said:**
>  No, that's distro-specific modifications to software, a packaging method would in no way hamper or benefit a virus. 

Yes again bad terminology, linux has many distros and each has its own specific modifications. I am sorry for the misunderstandings.

But the packaging method does actually make it more dificult for a malware to spread within the Linux community. The reason is the same as why programmers need to package their software with different packaging methods depending on which linux distro they want to install their program. If I download an rpm package on Ubuntu it won't work, because it uses a deb packaging method. While windows generally uses the exe packaging method. Even the shell commands used in different distros are different, therefore even malware written in shell script won't fully work on all distros. The distro has to decode the package to manage to read the clear binary, therefore if the malware is packaged with a certain method it cannot infect, or install, itself on distros which use a different packaging method than itself.
   
> **unspawn said:**
> No, it wont: *sane practices (like browsing habits)* could have an effect.

Well...you obviously did not understand nor read properly my original point. Notice the word "minimize", a distro with constant security updates with patches to its faults, and a constantly improving code will make it considerably harder for the machine to be infected. While sane practices DEFINITELY have, as opposed to could have, an effect it is not the only way to keep your box secure.
    
> **unspawn said:**
> No, they're simply not: most are just *users* half of which aren't even remotely aware they run Linux these days. 
   
Ok...just fyi servers do not count, neither phones nor any other firmware, I am talking stricly PCs.
All commercial PCs come with windows, most PC users won't have even heard of linux. In my IT course there were people who had no idea what linux was until we had to study it. During my CCNA course the lecturer had to take a whole lesson to explain to almost half the students what the apache server was and how linux played an important part with servers.
Considering all of this most people would rather have a member of family, or a friend, or a usual technician on who they always call to service their PCs, not even understanding how it works. 
Then assuming there is another percentage of PC users which are more aware of their choices of OS, they would rather not switch because they wouldn't know where to start with linux, they can barely take care of their windows machine, and are also still learning. They may find that using terminal often is not for them. And/Or they may just not want the change.

But to those who actually do the change and install a linux distro on their own machine must have researched the pros and cons, must have understood the technical jargon used to describe their differences. They are making a change knowingly thus must have some adequate knowledge of IT to keep their machine relatively clean, compared to a grandma who is just learning to send emails to her grandchildren.

If you disagree with this please explain how.

> **unspawn said:**
> No, the OS does matter, that's simply a money thing ;-p

Do you even know what I meant by what I said? 
I will break it down again....it simply means that which ever OS the malware is targeting if the signature is within the AV database, or through heuristic scanning the malware WILL be detected. The OS matters to the purpose of the malware, yes, but it doesn't affect its detectability by an AV. This is what I meant if you didn't understand it initially.

> **unspawn said:**
> No, realtime scanning (in whatever way) actually is helpful.

I never said it wasn't helpful, I said it MAY be unnecessary. There is a difference between MAY be and IS. And there is also a difference between NECESSARY and HELPFUL.
Since Linux distros are so good at keeping malware out, and if it doesnt come in, it is also good at keeping the malware from running with root permission, it is highly unlikely that a malware will manage to damage your box anytime soon. Therefore realtime scanning can be unnecessary in terms that you CAN wait until a scheduled or manual scan if you so wish. Obviously any extra such as realtime and a good firewall etc... would be helpful, but maybe not necessary.

> **unspawn said:**
> Is that a fact?.. Can you show us a sample of a Linux ELF infection and a perfect cleanup?..

When I made this statement I had assumed that both malware were detected before infection, after which would be a problem. The trick is always detecting the malware before it has a chance to run and install itself on the target machine and even possibly deal any damage. ELF infections in themselves are pretty rare and again they are distro and kernel specific, therefore they won't spread as fast. Therefore AVs haven't had much testing ground with these.

> **unspawn said:**
> While it certainly is worth something protecting lesser OSes, focusing on AV and viruses is (IMHO and with all due respect) Windows-centric thinking: with Linux you need to: - keep your OS up to date, - have sane browsing and software habits, - secure, harden and regularly audit your machine(s) as the threats we face are different from what users of "the other OS" experience.  Please focus on *that* instead.

You are mostly right. The malware hype is very windows-centric thinking, but my point is that the threat of malware infecting a linux box is still very real. It is unlikely but real. And personally from what I have seen through other posts is that people completely ignore this and count as if it was impossible, but it is not. Unlikely doesn't mean impossible, but simply that it is rare. The truth is that there is always the possibility for your box to be infected with malware, and with Linux becoming everyday more popular and technology improving then this possibility is also increasing. Linux malware is becoming more common, and eventually will be a problem.

You are also right that we need to keep the OS updated and have sane browsing and software habits, but to me an AV is part of "securing and hardening" my box.
And also IMHO we shouldn't focus on any particular aspect, but we should see the security of our PCs as a whole. I made this thread with this focus simply because I was tired of people claiming Linux is impossible to get infected, when most of them don't even know how it works.

I hope you understand.

> **Xentime said:**
> 
All the anti-virus ruckus is really a Windows-centric approach and quite dated (in my opinion), these days it is easier to exploit weaknesses in third-party software be it click-jacking or drive-by attacks, let alone this usually allows you to attack multiple operating systems at once. Less work, more pay.

While to you Xentime all I have to say is that for an exploit to really work it needs a payload, e.g. a way to connect back to the exploited system. This is generally in the form of a trojan, or worm with a backdoor connection allowing the hacker back into your machine after exploiting these weakenesses you mentioned. But malware is still a big part of this. Most hacks now days use faults in third-party software or an irreplaceble aspect of the network, e.g. java, javascript injection, MITM attacks etc...
But in all exploits there will always be a payload, which is generally (not always) in the form of a malware which could be blocked by an AV.

As I said to unspawn my aim is not about the AV ruckus, but more towards the full security of the system, AV included.

---

### Post by Xentime on 2014-04-01
> **gabriel13 said:**
> While to you Xentime all I have to say is that for an exploit to really work it needs a payload, e.g. a way to connect back to the exploited system. This is generally in the form of a trojan, or worm with a backdoor connection allowing the hacker back into your machine after exploiting these weakenesses you mentioned. But malware is still a big part of this. Most hacks now days use faults in third-party software or an irreplaceble aspect of the network, e.g. java, javascript injection, MITM attacks etc...
But in all exploits there will always be a payload, which is generally (not always) in the form of a malware which could be blocked by an AV.

I'm very aware that exploits do need payload. As you had mentioned, payloads won't always come in the form of malware. It is those kinds of payloads I'm most concerned about. Having on-demand scanning and a machine dedicated for packet analysis is more then enough to take care of either for me. I wasn't very clear on my stance and the reasoning for it, which I apologise for the extreme vagueness of my argument (just read it over). Oi. xD

But as stated before in my previous post, I do not advise anyone to run without anti-virus software.

---

### Post by PartisanEntity on 2014-04-02
Which AV do you all use on your Linux machines? I have never used AV software on any of my Linux computers so far, but have been contemplating it recently. ClamAV is often mentioned, but lately I saw that previous Windows-centric applications like Avast, Comodo, AVG, etc. are now available for Linux, are they worth it? ( [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus) )

---

### Post by ant2ne on 2014-04-02
> During my CCNA course the lecturer had to take a whole lesson to explain to almost half the students what the apache server was and how linux played an important part with servers. Considering all of this most people would rather have a member of family, or a friend, or a usual technician on who they always call to service their PCs, not even understanding how it works. Point and click admin's rarely make it past the help desk in their careers. I remember being in class and looking around and knowing probably 3/4 of these students will finish their degree in IT, and probably less than 1/4 will actually land a job in the IT field.

I've used avast on a bootable USB drive to clean a in infected windows machine. I've run avast on my linux box, just cause, and got a false positive. I've also played around with comodo and avira on my linux box, just cause. I've used clamav on my proxy server(s). For awhile I was using an AV product on my linux workstation because I didn't want to be responsible for accidentally spreading something to the windows machines. But then I figured 'screw em'. If I get infected it is because of them anyway LOL.

gabriel13, if you want to run some AV product on your linux machine go ahead. If it makes you feel safer then by all means. There is nothing wrong with one more layer to the onion that is security. But that layer isn't going to be the most important layer of that onion.

---

### Post by SeijiSensei on 2014-04-02
> **ant2ne said:**
> Are you sure it came from the Times?

I take it you did not follow this link in my post: [http://www.nytimes.com/2009/09/15/technology/internet/15adco.html](http://www.nytimes.com/2009/09/15/technology/internet/15adco.html).  A third-party advertising channel bought space to advertise for Vonage.  It provided legitimate Vonage ads for three or four days, then started distributing Antivirus 2010 on the following Saturday.

As a Javascript exploit, it could only run when the browser is open.  The supposed Windows Explorer page was actually just an web page that appeared in a new window on Firefox; the script opened the page in response to a window.close() event.

I think you give ordinary users too much credence if you think you have to resort to delays and the like to get them to infect themselves.  Just the other day I corresponded with a college classmate who had to get her computer revisioned after she fell for the [phony telephone support scam]("http://www.microsoft.com/security/online-privacy/avoid-phone-scams.aspx").  This is a very smart woman, too.  I got one of these calls myself, but  I was too busy at the time to play along with the guy and try to find my "Start" button.

---

### Post by ant2ne on 2014-04-02
> I take it you did not follow this link in my post Nah, I don't go around clicking every link I come accross. :cool:

> resort to delays and the like to get them to infect themselvesNot at all what I was saying. The delay would be so the person infected wouldn't know where it came form. Any idiot on the web closes their browser or moves to another page and then gets a pop up they ware going to say to themselves "I just left [www.mypage.com](www.mypage.com) and then this happend. It must have been caused by www.mypage.com!" But if there was a delay, then they would have moved on to [www.someotherpage.com](www.someotherpage.com) before the pop up and then they'd blame [www.someotherpage.com](www.someotherpage.com). Thus they'd contact [www.someotherpage.com](www.someotherpage.com) and not  [www.mypage.com](www.mypage.com). [www.mypage.com](www.mypage.com) never gets word that their site has been compromised and the exploit may persist longer.

---

### Post by gabriel13 on 2014-04-02
> **Xentime said:**
> I'm very aware that exploits do need payload. As you had mentioned, payloads won't always come in the form of malware. It is those kinds of payloads I'm most concerned about. Having on-demand scanning and a machine dedicated for packet analysis is more then enough to take care of either for me. I wasn't very clear on my stance and the reasoning for it, which I apologise for the extreme vagueness of my argument (just read it over). Oi. xD

But as stated before in my previous post, I do not advise anyone to run without anti-virus software.

Yeah, ur point is very valid...since linux is so good at keeping viruses out most hackers focus heavily on other exploits. Being well protected from those kind of exploits is a tricky job, people should definitely talk more about it.


> **PartisanEntity said:**
> Which AV do you all use on your Linux machines? I have never used AV software on any of my Linux computers so far, but have been contemplating it recently. ClamAV is often mentioned, but lately I saw that previous Windows-centric applications like Avast, Comodo, AVG, etc. are now available for Linux, are they worth it? ( [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus) )

Partisan, well clamAV is metioned more because it is an open source software than becouse of its ability as an AV...which is a shame. It has potential, it just hasn't reached it yet.
Bitdefender has the best scanning and detection engine, but its linux software has had no support in at least 4 years. It even has the same bugs as it had 2010, therefore would not recommend it.
Never been a big fan of AVG neither in windows nor on the phone, my personal experience with it is that it slows down your system too much, and has too many false positives and misses a 0 day infections. 
In the rankings Avast is quite high and I would definitely recommend it, but as a comodo windows customer I have had good experiences with it. Plus comodo AV for linux has the best GUI for a linux AV (personal opinion) thus it is the one I chose.

So overall I would recommend either Avast or Comodo. There is also another one with a good reputation, but I believe it is paid if I am not wrong....ESET. Worth having a look.

> **ant2ne said:**
> Point and click admin's rarely make it past the help desk in their careers. I remember being in class and looking around and knowing probably 3/4 of these students will finish their degree in IT, and probably less than 1/4 will actually land a job in the IT field.

I've used avast on a bootable USB drive to clean a in infected windows machine. I've run avast on my linux box, just cause, and got a false positive. I've also played around with comodo and avira on my linux box, just cause. I've used clamav on my proxy server(s). For awhile I was using an AV product on my linux workstation because I didn't want to be responsible for accidentally spreading something to the windows machines. But then I figured 'screw em'. If I get infected it is because of them anyway LOL.

gabriel13, if you want to run some AV product on your linux machine go ahead. If it makes you feel safer then by all means. There is nothing wrong with one more layer to the onion that is security. But that layer isn't going to be the most important layer of that onion.

You're right...I have been in the same situation. And the IT industry is really volatile, technology moving on so fast it is hard to keep up.

And the Avast you had on the USB drive...could it possibly have been on a sandisk U3 drive?? I had one like that, with Avast on it XD

And yeah I agree...security is never covered in just one layer, or one application etc... It is many layers of security, and AV is definitely not the most important, but I personally think that it is an essential part of any box's security.

> **SeijiSensei said:**
> Just the other day I corresponded with a college classmate who had to get her computer revisioned after she fell for the [phony telephone support scam]("http://www.microsoft.com/security/online-privacy/avoid-phone-scams.aspx"). This is a very smart woman, too. I got one of these calls myself, but I was too busy at the time to play along with the guy and try to find my "Start" button.

I hate those scams!! They are so annoying!
I once told the guy that they could give me any info about the attacks on my computer and I would deal with them since I am a "microsoft certified security technician", notice this is not a real qualification, the guy hanged up straight away. I had never laughed so hard in my life XD

---

### Post by PartisanEntity on 2014-04-02
Thanks for the tips on Avast or Comodo, I will look in to them a little more.

---

### Post by sammiev on 2014-04-02
Bitdefender has been good to me and has found items in FF over the years. Yes it's free.

---

### Post by lisati on 2014-04-02
My one and only experience with comodo was on a Windows machine a few years ago. It wasn't pleasent, because it didn't find something which subsequently did something nasty to my system...... :( Things might have changed in the meantime.

---

### Post by gabriel13 on 2014-04-02
> **PartisanEntity said:**
> Thanks for the tips on Avast or Comodo, I will look in to them a little more.

Your welcome, it is my pleasure to be of help.

> **lisati said:**
> My one and only experience with comodo was on a Windows machine a few years ago. It wasn't pleasent, because it didn't find something which subsequently did something nasty to my system...... :( Things might have changed in the meantime.

Was it only the AV or the internet suite? 
Because realistically comodo AV is definitely NOT the best AV there is. But I believe that it is the best full security suite that there is.
So my experience with comodo is with the internet suite, it includes the HIPS and firewall, plus my browsing practices are pretty safe. Therefore to me the most important thing is prevention, and comodo is great at doing that.
Also for more experienced users comodo allows a greater degree of customization which is generally not found in free suites.
But if you are looking at AV specifically there have been many tests which show bitdefender to be the best there is. On windows there's also 360safe...it uses 3 AV engines, bitdefender included, and it provides an even greater degree of security, but it is not a suite, and personally I prefer suites.

On linux I am currently using comodo AV, but I would happily switch back to bitdefender if they started developing again their linux software.

---

### Post by lisati on 2014-04-02
My experience of comodo was with the AV only, not the internet suite. These days, I tend to use AVG on my Windows installations, mainly out of familiarity. I haven't bothered on my Ubuntu installation.

---

### Post by 23dornot23d on 2014-04-02
ClamTk, v4.45
Thu Apr  3 03:42:37 2014
ClamAV Signatures: 3290609
Directories Scanned:
/media/keith/Verbatim/windows

Found 1 possible threat (4 files scanned).

/media/keith/Verbatim/windows/FSViewerSetup37.exe      Win.Trojan.Downloader-5319


Glad I checked - just some old files that I never use now ........... but the directory contained this above.
deleted now .........

But will do a thorough search of all my older files and recursive scan through the /home on each drive now.

[IMG]http://i.minus.com/ie5OHdtVEe5Yq.png[/IMG]

Here is a interesting one .... my computer has Windows 7 on it and I have never really used it since buying the computer
 ...... yet it has a pdf file that has a signature for a virus on it  .... unless its not a proper virus ... never quite sure what
types of threats they check for nowadays . ( no threat if I do not go into it anyway - as it will not delete from linux )

Found 1 possible threat (27629 files scanned). on the Windows 7 partition.

/media/keith/OS/Program Files (x86)/Adobe/Acrobat 6.0/Reader/Messages/ENU/RdrMsgENU.pdf      Heuristics.Encrypted.PDF

I think in answer to the initial question in this discussion - yes ..... to AV ...... and not to miss things by not to AV.

Even though the things I have found so far only posed a threat if I had used wine to run them - or to run them direct on a Windows system.

Better safe than sorry as once embedded in systems take some removing - which usually seems to be safe - using a clean install.

Good post as this is the first time in 5 years that a virus check has been run on this computer - so how many Linux only viruses have

been found up todate ?

---

### Post by gabriel13 on 2014-04-03
> **lisati said:**
> My experience of comodo was with the AV only, not the internet suite. These days, I tend to use AVG on my Windows installations, mainly out of familiarity. I haven't bothered on my Ubuntu installation.

Yeah as I had thought, Comodo is not well known for its AV. But as a internet suite it is a whole different game, and IMO it is the best FREE security suite available.

Something interesting I thought I would post is this article by AV TEST: [http://www.av-test.org/en/news/news-single-view/artikel/25-internet-security-suites-are-put-to-the-test-using-windows-81/](http://www.av-test.org/en/news/news-single-view/artikel/25-internet-security-suites-are-put-to-the-test-using-windows-81/)

It tested the best internet suites on windows 8.1  To be honest I was surprised with Comodo's performance XD I never expected it would be so good. 

Also was I surprised to find that Avast actually a low detection rate, I overestimated it. And assuming that the scanning engine architecture is the same on both windows and linux this would definitely reinforce my choice in having Comodo AV for my linux box.

Also for you lisati, since you use AVG I wouldn't recommend it, I already wasn't a big fan, but the test only confirms what I already thought.

> **23dornot23d said:**
> 
Good post as this is the first time in 5 years that a virus check has been run on this computer - so how many Linux only viruses have

been found up todate ?

Actually a good question, I already knew that Linux malware already existed. But I wasn't exactly sure of how many. So had to do some extra research myself.

[https://en.wikipedia.org/wiki/Linux_malware](https://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

These are the best lists I could find. It seems like it doesn't go higher than 50 in any list that I find. Which is a good thing, and also they don't seem to be plaguing the linux world which is even better.
But it still shows that they exist and it all depends on your own security to keep them at bay.

I hope this answered your questions.

---

### Post by 23dornot23d on 2014-04-03
Thats great thanks ........ ( and how many exist on Windows - and who paid them to do all that work ? ) this to me is the more interesting question as a lot of
firms make and made a lot of money - almost like the protection racket in the USA .... where if the bars did not have protection or insurance from their place
getting burnt down ....... then sometimes out of the blue it got burnt down or destroyed  ........... ( sometimes - like the very next day. )

Sort of makes you wonder how this sort of racket gets started off ........ what motivation does it take that is stronger than money to get people doing this type 
of thing.

Willl have a search see if the same type of effort goes into detection on Linux ...... or if the threat never raises its head to affect a lot of computers then why
would anyone bother .......... more to nowadays surveillance of computers than meets the eye though ...... and they only have to sit there quietly watching for
things that may be of interest to them ....... a virus maybe nowadays does not mean to destroy things - but just gain access to many computers.

Never really got into this in a big way - other than when running windows - and it seemed a routine to clear away 20 - 30 exploits on regular intervals .....

---

### Post by maglin2 on 2014-04-03
> **gabriel13 said:**
> 

Something interesting I thought I would post is this article by AV TEST: [http://www.av-test.org/en/news/news-single-view/artikel/25-internet-security-suites-are-put-to-the-test-using-windows-81/](http://www.av-test.org/en/news/news-single-view/artikel/25-internet-security-suites-are-put-to-the-test-using-windows-81/)

It tested the best internet suites on windows 8.1  To be honest I was surprised with Comodo's performance XD I never expected it would be so good. 

Also was I surprised to find that Avast actually a low detection rate, I overestimated it. And assuming that the scanning engine architecture is the same on both windows and linux this would definitely reinforce my choice in having Comodo AV for my linux box.


Comodo antivirus for linux (CAVL) has not been updated in over a year. It will not run on any kernel beyond 3.5 (redirect driver issue). You can find a completely unofficial patch on their forum - but if you are concerned about security enough to want to install a linux AV I can't really see why you would then load a patch from an unknown source.

PS - CAVL would run on kernels beyond 3.5 as an on demand scanner - but without the redirect driver there would be no real-time/on access functionality. Avast for linux is, I gather, now a paid for product only as of next Monday.

---

### Post by ant2ne on 2014-04-03
> [https://en.wikipedia.org/wiki/Linux_malware](https://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)Great links. This might change my opinion, slightly, but not much. Patch regularly and don't be stupid.

---

### Post by gabriel13 on 2014-04-06
> **23dornot23d said:**
> Thats great thanks ........ ( and how many exist on Windows - and who paid them to do all that work ? ) this to me is the more interesting question as a lot of
firms make and made a lot of money - almost like the protection racket in the USA .... where if the bars did not have protection or insurance from their place
getting burnt down ....... then sometimes out of the blue it got burnt down or destroyed ........... ( sometimes - like the very next day. )

Sort of makes you wonder how this sort of racket gets started off ........ what motivation does it take that is stronger than money to get people doing this type 
of thing.

Willl have a search see if the same type of effort goes into detection on Linux ...... or if the threat never raises its head to affect a lot of computers then why
would anyone bother .......... more to nowadays surveillance of computers than meets the eye though ...... and they only have to sit there quietly watching for
things that may be of interest to them ....... a virus maybe nowadays does not mean to destroy things - but just gain access to many computers.


Well on windows there are actually around 50.000 viruses in circulation, with some estimates reaching close to 80.000. And generally people are not paid for building malware, although some are, generally the malware are built to get the money, such as steal bank data, make fake transactions, collect data to sell to other companies. Others just do it for fun. It is a challenge to build a good malware, and some are real pieces of art...underground you can get high reps for this kind of thing, its like a hacker's portfolio.

On linux there is no where near the same amount of effort to detect malware...simply because there is no need for it. And malware, viruses in specific, has never meant to destroy things. This is a common misconception, very few were actually built to destroy things. It just defeats the purpose for which it was created. Viruses if it is going to replicate and infect other systems, the system which is already infected needs to survive long enough for that virus to infect another before the system is destroyed. And if the virus wants to accomplish other stuff like accessing data etc... the infected system needs to live longer than that. 

> **maglin2 said:**
> Comodo antivirus for linux (CAVL) has not been updated in over a year. It will not run on any kernel beyond 3.5 (redirect driver issue). You can find a completely unofficial patch on their forum - but if you are concerned about security enough to want to install a linux AV I can't really see why you would then load a patch from an unknown source.

PS - CAVL would run on kernels beyond 3.5 as an on demand scanner - but without the redirect driver there would be no real-time/on access functionality. Avast for linux is, I gather, now a paid for product only as of next Monday.

True, you are right, but Comodo's one year is much better than bitdefender's 4 years. Plus on linux having a real-time scanner would not be worth the memory and processing time. Therefore an on-demand scanner is perfect. And about avast...I searched and ddnt find anything. I guess it will be obvious after monday right??

> **ant2ne said:**
> Great links. This might change my opinion, slightly, but not much. Patch regularly and don't be stupid.

Sure :) And yeah you're right, on a linux the main thing is to patch/update regularly...and definitely don't be stupid. Thank you!!

---

### Post by ant2ne on 2014-04-07
I had a hard time finding avast as well. I could only find the link from another site not belonging to avast. The link was for the avast.com's download area but I couldn't find it from avast.com's site anywhere. Almost as thought they aren't 'really' supporting it.

---

### Post by maglin2 on 2014-04-07
From these posts on the avast forum.
[http://forum.avast.com/index.php?topic=145973.msg1059148#msg1059148](http://forum.avast.com/index.php?topic=145973.msg1059148#msg1059148)
[http://forum.avast.com/index.php?topic=145973.msg1078513#msg1078513](http://forum.avast.com/index.php?topic=145973.msg1078513#msg1078513)
[http://forum.avast.com/index.php?topic=145973.msg1060986#msg1060986](http://forum.avast.com/index.php?topic=145973.msg1060986#msg1060986)
It seems that the advent of their paid linux server product isn't quite the death knell for their previous free scanner but is a 'very significant nail in the coffin' (the free scanner uses avast 4VPS - which will die in the near(ish) future)

---

### Post by ant2ne on 2014-04-07
Interesting. I wonder how much the paid version is. The fact that they describe it as " linux server product line" means it will be expensive. Whenever they tack the word "server" on a product it becomes ten times more costly than it is worth.

---

### Post by canundrum69 on 2014-04-09
Realistically speaking, I use Ubuntu 100% on all of my computers, I gave up Microsoft everything 2 years ago.  The only windows software I keep are games I purchased that I run with Wine.  I do use both Chrome & Firefox, and run ClamAV on the system, and have Ad Blockers & Popup Blockers on both browsers.  My Root Password doesn't match anything else.

Te only thing Clam ever finds are Pics generated by my Cannon Power Shot.  I can right click & save a pic and it never comes up in Clam, but let me take a set of pics around town and Clam says they are threats. I kind of find it amusing.

I am however still a bit paranoid.  How likely is it that I need some sort of Malware tool, and is there any? or am I still just in a Windows state of mind and don't realize it?

---

### Post by HermanAB on 2014-04-09
Howdy,

I've been using UNIX systems since 1984 and Linux since 1998.  The probability of you getting malware on your desktop machine is almost exactly zero, unless you install VNC, in which case the probability of getting hacked is almost exactly 1.

It is different with servers, since people target servers on fast networks in order to send spam, but even so, server compromises are few and far between.

---

### Post by 23dornot23d on 2014-04-09
I would like to know from the Windows users - how many different forms of protection do they have on their own systems

Remembering back when I used to use it and going through most of my old software - a lot was to do with security ..........

and yet I remember having a continuous battle trying to keep on top of it all ...........

The difference on Linux .......... is ............ ?

A ...... We do not constantly scan for them
B ...... We do not see anything popping up that really worries us
C ...... Linux is more secure

or something else .......... 

I still feel a little better that I did a check the other day - but already it feels like a deja vu scenario

Maybe Linux is hitting the big time now ......... especially since MS has done so many odd changes lately ..........

Rightly or Wrongly ........ I still feel better on Linux - just because I can see the logs - I can see what I am installing .........

and when I pop on it after a while - like a day .......  that 22 new installs get put onto my computer and all I see is a circular gif

going around and around .......... while saying welcome ......... then the next thing I see is shutting down and rebooting

yet its still not over ......... now installing please wait and do not shut down your computer ..........

Odd ........ but its the only system that gets me swearing and into a bad mood before I even start to do any 3d or anything.

Was paranoid with XP and Windows 7 ......... then something happened ...... 

I stopped going back into them .......... on the net ...... what go me though even disconnected windows 7 somehow said it was

doing a update when I plugged a usb drive into it ........... it recorded 147 registry entries into itself ..... which was just about the

number of music files on that USB drive ......... gets me wondering what on earth it is doing and what is it recording.

Now back to making sure Linux is as secure as possible .......... ;)

---

### Post by SuperFreak on 2014-04-09
> **HermanAB said:**
> Howdy,

I've been using UNIX systems since 1984 and Linux since 1998.  The probability of you getting malware on your desktop machine is almost exactly zero, unless you install VLC, in which case the probability of getting hacked is almost exactly 1.

It is different with servers, since people target servers on fast networks in order to send spam, but even so, server compromises are few and far between.

What do you mean by a probability of 1. Do you mean 1% or 100%
You have me a little worried as I have VLC installed and I use it frequently. Can you elaborate on why it is a malware vector?

---

### Post by lisati on 2014-04-09
> **SuperFreak said:**
> What do you mean by a probability of 1. Do you mean 1% or 100%
You have me a little worried as I have VLC installed and I use it frequently. Can you elaborate on why it is a malware vector?

The way I read it, by "1", HermanAB means "100%", i.e. it's almost certain that someone will get up to mischief.

---

### Post by canundrum69 on 2014-04-09
> **23dornot23d said:**
> I would like to know from the Windows users - how many different forms of protection do they have on their own systems

Remembering back when I used to use it and going through most of my old software - a lot was to do with security ..........

and yet I remember having a continuous battle trying to keep on top of it all ...........
;)

I used to spend a lot of money keeping my windows computers secure.  Trading up from year to year, from Norton AV to Symantec Corporate Version to Bit Defender then NOD32, in addition to programs like "MalwareBytes" and popup blockers for browsers.  

Now I am on Ubuntu for a few years, but I still have an AV and Browser popup blockers, and the only real difference (the most important one) is the Lack of Virus or other Infection notifications popping up.  I'm still not the kind to just sit back, sigh and figure I'll never have troubles.  But My Linux Experience has been a lot less stressful than WIndows.  I can look back and wonder why I kept using Windows for so long even knowing Linux was not only available but "Free" *shrug*  I finally opened my eyes.

But once in a while, someone says something or I read something and I get that twinge and begin to wonder if I am 'REALLY' Doing everything I need to make sure I protect myself & my Files.

---

### Post by SuperFreak on 2014-04-09
> **lisati said:**
> The way I read it, by "1", HermanAB means "100%", i.e. it's almost certain that someone will get up to mischief.

I am trying to get my head around why VLC is a security issue. It is in the Ubuntu Software Center which I thought had safe programs for install. Furhtemore it is highly recommended and often cited as one of the first programs when should install for video. I need to know if this just FUD or if there is a reason for the original statement HermanAB made

EDIT: Googling VLC Security I see there were some issues in 2012 with ver 2.03 but updating to a newer version fixes this. I notice I am at ver 2.08. is this safe ?

---

### Post by canundrum69 on 2014-04-09
> **SuperFreak said:**
> I am trying to get my head around why VLC is a security issue. It is in the Ubuntu Software Center which I thought had safe programs for install. Furhtemore it is highly recommended and often cited as one of the first programs when should install for video. I need to know if this just FUD or if there is a reason for the original statement HermanAB made

EDIT: Googling VLC Security I see there were some issues in 2012 with ver 2.03 but updating to a newer version fixes this. I notice I am at ver 2.08. is this safe ?

Maybe there could be issues using VLC to steam media frmo the internet?

---

### Post by SuperFreak on 2014-04-09
I guess that is a good guess, but speculative. Why would Flash be any safer?. Personally I use VLC for local media on my PC mainly

---

### Post by canundrum69 on 2014-04-09
> **SuperFreak said:**
> I guess that is a good guess, but speculative. Why would Flash be any safer?. Personally I use it for local media on my PC mainly


Same here ... So I really can't see anything in VLC that could be an issue.  I'm not big on stream except maybe watching Netflix or the like,

---

### Post by SuperFreak on 2014-04-10
I see that HermanAB has edited his post to change VLC to VNC which is a relief. I don't understand why he has not posted in the ongoing thread but there it is

---

### Post by 23dornot23d on 2014-04-10
Ok seems to make more sense ....... [http://en.wikipedia.org/wiki/Virtual_Network_Computing](http://en.wikipedia.org/wiki/Virtual_Network_Computing)

So are we safe again ....... ;) ...... got to be less vulnerabilities soon 

This week alone has shown that the influx from the XP world has opened our eyes again .... thank god for threats what 
would security people do for jobs without them .......... and who creates them all in the first place .........

Pointless jobs in life ...... things that are created to do nothing other than disrupt others ....... bit like tripping the leader up
in a race ...... to say hey ..... look everyone I won ...... thing is they cannot keep tripping people up forever without being 
caught out at some point .........

I have a feeling sometime in the future - that a AI program will go back through all the data ever captured and highlight
how and where most of the vulnerabilities in systems started out and where they stemmed from.

Now there is something that is worth writing ...... who were the bad guys in the past ......... and how to stop them in the 
future ........ when all the time they make money from it - to carry on paying people to write more ..........

What is the logical FLOWCHART to end virus production once and for all ............

Identify the real culprits and sort them out ......

or is there another way ....... ( virus protection is like wearing a suit of armour and the arrows still come at you. )

---

### Post by gabriel13 on 2014-04-12
Hey hey I'm back!! :D Spent the weekend at Birmingham, checked out gadget show live! It was amazing, to all techies living in the UK you should check out their program, its loads of fun.
But back at the topic at hand:

> **canundrum69 said:**
> 
I am however still a bit paranoid.  How likely is it that I need some sort of Malware tool, and is there any? or am I still just in a Windows state of mind and don't realize it?

Well...simple answer you shouldn't be paranoid. You're security is fine, if you do get overzealous then all you need to do is install an AV with a better detection rate than ClamAV, everything else you are doing great. So no worries my friend you are safe.

> **HermanAB said:**
> Howdy,

I've been using UNIX systems since 1984 and Linux since 1998. The probability of you getting malware on your desktop machine is almost exactly zero, unless you install VNC, in which case the probability of getting hacked is almost exactly 1.

It is different with servers, since people target servers on fast networks in order to send spam, but even so, server compromises are few and far between.

True...and thank you for correcting the post from VLC to VNC. Big difference.
And for all those not mathematically minded out there, 1 = 100%, just like 0.1 = 10%. See the pattern? Any of you who remembers anything from secondary school maths will know this.

> **23dornot23d said:**
> 
This week alone has shown that the influx from the XP world has opened our eyes again .... thank god for threats what 
would security people do for jobs without them .......... and who creates them all in the first place .........

Pointless jobs in life ...... things that are created to do nothing other than disrupt others ....... bit like tripping the leader up
in a race ...... to say hey ..... look everyone I won ...... thing is they cannot keep tripping people up forever without being 
caught out at some point .........

I have a feeling sometime in the future - that a AI program will go back through all the data ever captured and highlight
how and where most of the vulnerabilities in systems started out and where they stemmed from.

Now there is something that is worth writing ...... who were the bad guys in the past ......... and how to stop them in the 
future ........ when all the time they make money from it - to carry on paying people to write more ..........

What is the logical FLOWCHART to end virus production once and for all ............

Identify the real culprits and sort them out ......

or is there another way ....... ( virus protection is like wearing a suit of armour and the arrows still come at you. )

And well...the problem with threats are not that they may disrupt your game session, but that they will collect data from you, or allow external access to you, or disrupt you for a specific purpose other than simply disrupting for the sake of it.
Most VXers want your information, whether to sell, or for their own purpose (e.g. bank details to steal from you) this information can be quite valuable. So much so that the government creates viruses to keep track of what you do illegally, and blame it on hackers so that they are out of trouble. Other uses are for business competition, a company trying to illegally keep track of another company's assests etc...
The only reason that security people exist is because threat existed first, and threat always has the first move. Something can only be made secure if the flaw has been exploited, otherwise not even the security person would know that the flaw exists. That is why the security guy is employed to find flaws and hack systems without revealing data, so that he can discover new flaws and make the system secure again, which is all a better option than a bad guy finding it first.

But carrying on with the reply you plan seems good....apart from that flaws can happen anywhere in a system, since it is not the VXers cause, but it is generally a mistake in coding from the programmers, and these kinds of mistakes are random errors. AI cannot predict random. Not even we can...so impossible. What we can do on the other hand is try to create a program testing sandbox powerful enough that it can bruteforce the program, in all ways possible testing for flaws, unexpected results in any part of the code. Thus protection by prevention. 
Hackers and VXers will always exist, we just need security guys good enough to switch the situation and stay one step ahead.

And as you said yes, virus protection REALLY IS like wearing a suit of armor while the arrows still come at you. The reason you wear a suit of armor in the first place is because you know arrows will be fired at you! 





And to everybody...thank you for your participation, I am loving it. Keep the questions coming, and lets bring knowledge and strength through unity, together we stand divided we fall.

---

### Post by gabriel13 on 2014-04-12
> **23dornot23d said:**
> I would like to know from the Windows users - how many different forms of protection do they have on their own systems

Remembering back when I used to use it and going through most of my old software - a lot was to do with security ..........

and yet I remember having a continuous battle trying to keep on top of it all ...........

The difference on Linux .......... is ............ ?

A ...... We do not constantly scan for them
B ...... We do not see anything popping up that really worries us
C ...... Linux is more secure

or something else .......... 

I still feel a little better that I did a check the other day - but already it feels like a deja vu scenario

Maybe Linux is hitting the big time now ......... especially since MS has done so many odd changes lately ..........

Rightly or Wrongly ........ I still feel better on Linux - just because I can see the logs - I can see what I am installing .........

and when I pop on it after a while - like a day .......  that 22 new installs get put onto my computer and all I see is a circular gif

going around and around .......... while saying welcome ......... then the next thing I see is shutting down and rebooting

yet its still not over ......... now installing please wait and do not shut down your computer ..........

Odd ........ but its the only system that gets me swearing and into a bad mood before I even start to do any 3d or anything.

Was paranoid with XP and Windows 7 ......... then something happened ...... 

I stopped going back into them .......... on the net ...... what go me though even disconnected windows 7 somehow said it was

doing a update when I plugged a usb drive into it ........... it recorded 147 registry entries into itself ..... which was just about the

number of music files on that USB drive ......... gets me wondering what on earth it is doing and what is it recording.

Now back to making sure Linux is as secure as possible .......... ;)

Haha your post is so awesome I had to create a reply for it alone.

Ok...As a windows user I have about five layers of security. But 3 are part of one program, which is a security suite, this cuts my problems in half :)

1 - Web protection: Adblocker, pop-up blocker, and browser security (Bitdefender Traffic light - worth having a look at)
2 - Firewall: Comodo Firewall (part of Comodo Internet Security)
3 - HIPS, Host intrusion detection system: (part of Comodo Internet Security)
4 - Comodo AV: (part of Comodo Internet Security)
5 - UAC, User Account Control: Native windows program works like sudo a prompt window opens everytime a program is run asking for allowance.

On a windows machine this is the best protection you could get, although web protection and HIPS tends to be optional they can help a lot.
UAC already comes with windows and it is advised to keep it on at all times.
Firewall there is windows firewall, but I feel like it is limited, while comodo does a much better job. This is all on windows 8.1

The difference on Linux is exactly as you put it, much more secure, there is no need to check all the time for malware so we can relax and not really think about it for a while.

And yeah, Microsoft's way of updating their system is sooo bad that I haven't been on my windows for over 2 weeks...then these weekend I had to go into windows to download some windows only steam games -_-
First thing that happens: "wait while we configure your system." Only 3 things to update and it took almost half an hour. Linux can get the same done in 5 minutes...

So yeah, windows sucks :/ Although I have to admit, once you set it up with all your favourite programs and make it work a charm it can still be quite tolerable. And if you know how, it can also be quite secure, all for free.

---

### Post by bashiergui on 2014-04-13
I'm reading the posts ... with all the ellipsis ... in the form of a bad 80's rap.... *cue the beatbox*

And no. Linux isn't more secure unless you do something to secure it more than you do on Windows. Every OS can be hardened and every OS can be vulnerable.

---

