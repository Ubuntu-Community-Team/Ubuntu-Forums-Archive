---
title: "Help me gather ammo to save my server"
date: 2006-08-10
forum: The Cafe
---

### Post by linkinpark342 on 2006-08-10
Hey folks. I'm the Server Administrator for a school organization "Techmasters" organization. Our server is currently running on a Fedora 3 linux on a student's really old computer. The server is used for other students to send requests to get their computer fixed by a techmaster (we're a boarding school) and for said techmasters to view these orders, as well as the TM's very limited playground (into php/html as they only get access to their home folder). The box is up for an update soon and I was thinking about installing either Ubuntu or Fedora 5. 

The problem: higher ups (a.k.a. faculty advisors) wants me to migrate to Windows Server. Of course I am highly against this and the 360+ day runtime of the Fedora does not phaze him in the least (nor the whole thing about me having to learn how to run a server on an entirely new operating system). I believe the reasons he gave me was that it was (don't hesitate to laugh) more stable. He's not a computer illiterate "noob" but he is a Windows proponant. Can anyone think of some other facts off the top of their head supporting Linux. I don't need "zomg linux is teh roxxors" stuff but if anyone can give me like their massive server uptime or something like that it would be greatly appreciated. Anything else that could help my cause would be too :)

Thanks,
--LP

---

### Post by cstudent on 2006-08-10
Money spent on licensing can be better spent on new hardware.

---

### Post by TravisNewman on 2006-08-10
I hate when non technical people try to claim they are. That really sucks. You could always just go ahead and install sever 2003 and then when things start messing up, say to the higher ups, well, this wouldn't be happening if you'd let me keep linux running on it. Give me a few hours and I'll have a linux server up and running that won't have these problems.

---

### Post by cstudent on 2006-08-10
Besides, a new Windows server version is probably not going to run on an old student's computer. So add the cost of a new computer. Plus the cost of the software. Plus the licensing. Plus the limitations of how many users can be connected.

---

### Post by cstudent on 2006-08-10
Annnddd! Through the ball back in the Mr. Know-it-alls court. Ask HIM to show proof a Windows server is more stable. Not that he probably will bother.

---

### Post by GuitarHero on 2006-08-10
Tell them that a majority of websites run off of linux servers(at least the stable ones)

---

### Post by bukwirm on 2006-08-10
Here's a link to the estimated prices of Windows Server 2003 - looks pretty expensive to me, especially compared to a Linux distro.

[http://www.microsoft.com/windowsserver2003/howtobuy/licensing/pricing.mspx]("http://www.microsoft.com/windowsserver2003/howtobuy/licensing/pricing.mspx")

---

### Post by hizaguchi on 2006-08-10
Woah, wait a sec, shouldn't this be up to the student who owns the computer?  How is somebody else able to tell this student what to run on his/her own computer?

I'd just tell them that if they want to provide the hardware, then they can run whatever they want on it.  But if they want you to maintain it, and want to run it on computers that they don't own, then it's really none of their business what OS you use.

This way, if they do provide the hardware you get a spiffy new server and you can just run whatever you want and tack on Windows Server in VMware and leave that running in full-screen mode all the time.  And if they don't provide the hardware, you can tell them to shove it.

---

### Post by TravisNewman on 2006-08-10
telling people that they have no business in something or especially telling them to shove it is a good way to lose a job :)

---

### Post by John.Michael.Kane on 2006-08-10
Though there are issues with windows as a server or linux as a server. the one issue with windows server might be with the IIS web server portion. both linux/windows is prone to attacks. it really comes down how the addmin ect has implemented patches,and what services will be running verses closed. 




**It may just take you a little more effort to get windows running on par.**


Just my thoughts..



"panickedthumb telling people that they have no business in something or especially telling them to shove it is a good way to lose a job" this is a very true statment..

---

### Post by bukwirm on 2006-08-10
Sites with the longest continuous uptimes: [http://uptime.netcraft.com/up/today/top.last.html]("http://uptime.netcraft.com/up/today/top.last.html")
Note how few of these are running Windows.

---

### Post by TravisNewman on 2006-08-10
> **bukwirm said:**
> Sites with the longest continuous uptimes: [http://uptime.netcraft.com/up/today/top.last.html]("http://uptime.netcraft.com/up/today/top.last.html")
Note how few of these are running Windows.
hmm... yes but #2-#5 say they are running BSD with IIS. I don't think that's really possible.

---

### Post by hizaguchi on 2006-08-10
> **panickedthumb said:**
> telling people that they have no business in something or especially telling them to shove it is a good way to lose a job :)
If the assumption I was making (that the faculty advisor is trying to limit the software that a student can run on his own computer) is accurate, then maybe that's not such a bad thing.  I mean, my job requires me to use Windows at work, and I actually use Windows at home nowdays too, but if they started telling me what I can and cannot do with my own personal property, I wouldn't be happy about it.

Anyhow though, the larger issue is that this doesn't sound like a "job" exactly.  It is a student organization.  Student organizations are generally created, governed, and maintained by students (hence the name) and the faculty advisors are usually just there to provide some oversight to ensure that the school's time/money/reputation isn't being abused.  Above all though, student organizations are meant to be educational opportunities for students to enjoy their hobbies and gain enrichment at the same time.  So this move is a little like telling the motorcycle club that they have to ride bicycles from now on.  It removes a portion of the students' enjoyment without any relation to the responsibilities of the advisor.

---

### Post by linkinpark342 on 2006-08-10
Thanks for all your replies. One thing i forgot to mention was that we have already purchased a new Dell server rack that has Windows Server pre-loaded onto it. My predecessor (the former system admin graduated) has made a very minor attempt to make it work as we had wanted.

@hizaguchi: the computer has been officially donated to the techmaster organization and the new rack is property of the techmasters. We can do whatever we want with the server basically.
What you say about the student organization being mostly run by students is true, I mean the President does most of the organization and all that stuff, but since our school requires the Techmasters so much, the faculty also plays a very significant role in the organization. For example at the beginning of the year we are normally responsible for getting about 300-500 computers (depending on the Freshmen IQ and how many people over the summer got a new lappy) as well as getting the older computers completely virus/malware free and basically catering to every single question from the students, although we do not deal with hardware problems for legal issues.

@bukwirm: excellent that's something I could really use. Although i never knew you could run IIS on "BSD/OS", might be an error in their software but still that including those that adds to 5. Thanks for the link, I'm adding it to del.icio.us now so I don't loose it.

(P.S. thumb i love your avvy)

[edit: missed half of hizaguchi's response before]

---

### Post by Brunellus on 2006-08-10
I'd imagine that the burden of proof is on the windows proponent to show there is a compelling reason to fix what ain't broke.

1) The server as it stands is highly-reliable, with excellent uptimes.  

2) The server administrators are qualified in the current environment, and would have to be requalified in a new environment.  Spin it as a recertification/retraining expense.

3) Security/patches/support.  Here's the Secunia "Unpatched vulnerabilities" report for windows server

[http://secunia.com/product/1173/](http://secunia.com/product/1173/)


here's ubuntu dapper:

[http://secunia.com/product/10611/](http://secunia.com/product/10611/)

A few things leap out right away:

1) There are simply fewer unpatched flaws in Ubuntu than Windows Server...1 % to 10 % !

2) the vulnerabilities exposed on Windows server are more serious, with many more leading to System Access.

---

### Post by siimo on 2006-08-10
there is no denying the IIS 6.0 and windows 2003 is a very stable and powerful platform - but for your needs just a computer to request computer repairs it sounds OVERKILL to pay all those licensing fees especially you being a school.  Save the money ;o) Go with ubuntu server install of 6.06 LTS it will be supported with security updates for 5 years and most n00bs script kiddies at school only know how to mess with windows anyway ;o)

---

### Post by beercz on 2006-08-10
I recently had a linux server (Debian Sarge) runnung continuosly for over two years, and I managed it remotely.  None of my Windows servers ran for anythink like that long withut crashing.

---

### Post by tseliot on 2006-08-10
Can this help?
[http://fridge.ubuntu.com/node/481](http://fridge.ubuntu.com/node/481)

---

### Post by YourSurrogateGod on 2006-08-10
> **cstudent said:**
> Money spent on licensing can be better spent on new hardware.

Word. That's the first thing that I thought of.

---

### Post by VirtuAlex on 2006-08-10
This thread
[http://ubuntuforums.org/showthread.php?t=226852]("http://ubuntuforums.org/showthread.php?t=226852")
has link on very interesting presentation. You may want to take a look at it. It is more like case study for linux in an elementary school, but it is very comprehensive and some points could be very useful to you.

---

### Post by slimdog360 on 2006-08-10
> **bukwirm said:**
> Here's a link to the estimated prices of Windows Server 2003 - looks pretty expensive to me, especially compared to a Linux distro.

[http://www.microsoft.com/windowsserver2003/howtobuy/licensing/pricing.mspx]("http://www.microsoft.com/windowsserver2003/howtobuy/licensing/pricing.mspx")

arghh popup

---

### Post by gnomeuser on 2006-08-11
First identify your core use cases for the server

Now you'll want to geniunely ask the person who wants the switch what his goals are, listen and take notes don't debate - then go back to your office and write up a well thought out counter point - address issues of cost, maintance, stablity, support and whatever is relevant. 

You also have to be ready to accept that Linux might not be the perfect fit for all cases but it has worked really well untill now - we'll be looking for smoothing out the issues are present and highlighting the strengths. 

However you will want to avoid what you are doing, namely stonewalling and claiming Linux is superior without listening to his input - you are just as bad as him even though you might very well be right.

---

### Post by NESFreak on 2006-08-11
> **panickedthumb said:**
> hmm... yes but #2-#5 say they are running BSD with IIS. I don't think that's really possible.

[http://uptime.netcraft.com/up/accuracy.html#hz1000](http://uptime.netcraft.com/up/accuracy.html#hz1000)

---

