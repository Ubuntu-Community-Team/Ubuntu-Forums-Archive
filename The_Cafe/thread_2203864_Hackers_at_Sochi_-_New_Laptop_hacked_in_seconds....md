---
title: "Hackers at Sochi - New Laptop hacked in seconds..."
date: 2014-02-05
forum: The Cafe
---

### Post by neu5eeCh on 2014-02-05
Fascinating report here:

[http://www.huffingtonpost.com/2014/02/05/reporter-hacked-sochi-richard-engel_n_4731846.html](http://www.huffingtonpost.com/2014/02/05/reporter-hacked-sochi-richard-engel_n_4731846.html)

Interestingly, you can see Kyle Wilhoit, the American security expert, using Ubuntu in the video while monitoring the exploits used to hack the reporter's computer. From what I can tell, there almost _is no defense_ against anyone who logs on in Sochi. Even a live-CD would have to be used carefully and knowledgeably.

---

### Post by SeijiSensei on 2014-02-05
The hacked machines were Macs, too, not Windows devices.  I wonder how well a Ubuntu computer would fare if all the [recommendations]("https://www.gov.uk/government/publications/end-user-devices-security-guidance-ubuntu-1204") from the UK's CESG were applied.

---

### Post by fdrake on 2014-02-05
i do believe he was able to hack into his iphone and mac because he installed the program . I mean this is just pure bulls to scarry people.

---

### Post by The Spectre on 2014-02-05
I noticed that he was using Ubuntu on his computer to monitor the computers that where being Hacked. (Around 2:33 in the Video)
[https://www.youtube.com/watch?v=rXihFawHXBk](https://www.youtube.com/watch?v=rXihFawHXBk)

[ATTACH=CONFIG]250130[/ATTACH]

---

### Post by nothingspecial on 2014-02-05
Well that video looked like a well balanced piece of journalism with plenty of evidence to back up it's statements.

---

### Post by dbass81 on 2014-02-05
Meanwhile in other news, former child actress Mara Wilson joins us to discuss the pressure of growing up on film shoots for Hollywood hits like "Matilda."

---

### Post by neu5eeCh on 2014-02-05
> **fdrake said:**
> i do believe he was able to hack into his iphone and mac because he installed the program . I mean this is just pure bulls to scarry people.

and you do believe that -- why?

doesn't sound like you listened very carefully. he said that in the process of searching for information on the sochi olympics, he was hacked into. he didn't "install" a program. rather, as soon as he logged on malware was able to assert enough control that it could download software without his permission. Wilhoit asks him _if he notices_, not -- did you download? -- but did you notice that your phone is downloading? [Just before the 2 minute mark.]

Many public wifi sites require that you log in via a given website. Such websites can be vectors of attack and apparently _are_ in Russia. This isn't about _knowingly_ downloading and installing software.

---

### Post by Old_Grey_Wolf on 2014-02-05
The Mac and Lenovo (Windows 7) laptops were out of the box with no security software installed. He monitored the computers from a laptop that had Ubuntu Linux plus additional penteration testing software installed. 

If you go on a public wifi network anywhere without using protections or common sence, you will be hacked eventualy.

---

### Post by bashiergui on 2014-02-05
The most crucial piece of information IMO was left out of those reports. Did they connect the cell phones to wifi or a cell network or both? I would expect the wifi to be completely hostile. The cell network? I'd need more details. Are the hackers running rogue cell towers?

---

### Post by bashiergui on 2014-02-05
> **The Spectre said:**
> I noticed that he was using Ubuntu on his computer to monitor the computers that where being Hacked. (Around 2:33 in the Video)
[https://www.youtube.com/watch?v=rXihFawHXBk](https://www.youtube.com/watch?v=rXihFawHXBk)

[ATTACH=CONFIG]250130[/ATTACH]
Perhaps the most newsworthy tidbit from the screenshot is Wilhoit likes Unity! *gasp*

---

### Post by mastablasta on 2014-02-06
yesterday it was in the news how Canada monitored Wi-fi on airports etc. withouth users permisison. i guess if one had access to network they cpuld just as well be installing things on your mashcines. similar goes if they hacked the login website or something.

anyway i am so glad i didn't pay for wi-fi on one of the airports. no only it was expencive but i might have gotten the computer hacked (at the time it had a fresh out of the box win7 istalled with no additional firewall and only MS antivirus that is of medium quality)

---

### Post by neu5eeCh on 2014-02-06
> **bashiergui said:**
> Perhaps the most newsworthy tidbit from the screenshot is Wilhoit likes Unity! *gasp*

And if the report had been able to go into more depth, it would have been interesting to see how Ubuntu would have faired under the same circumstances. Given that it was so easy to hack the new Apple laptop (apparently), Ubuntu probably wouldn't offer any advantages. The exploits, I'm guessing, attack the weaknesses inherent in cross-platform applications along with the glaring weaknesses in public wifi.

I've been Googling and, interestingly, 99 out of a 100 websites simply echo the breathless NBC report without giving readers even the vaguest clue as to how to protect themselves. The only site I've found, so far, that addresses the actual problem is here:

[http://gizmodo.com/5990192/vpns-what-they-do-how-they-work-and-why-youre-dumb-for-not-using-one](http://gizmodo.com/5990192/vpns-what-they-do-how-they-work-and-why-youre-dumb-for-not-using-one)

And then, I just found this (finally something substantive!) at PCMAG:

> In a [blog post]("http://blog.trendmicro.com/honeypot-russia-experience/?cm_mmc=Social-_-Twitter-_-TW:Trend%2BMicro-_-sf22432318#sf22432318")  about the experiment, Wilhoit said that none of the devices had  security software installed, which would put any device at risk no  matter the country. They were running standard operational programs such  as Java, Flash, Adobe PDF Reader, Microsoft Office 2007, and a few  additional productivity programs. he said.

  Wilhoit said he will publish a more technical blog post on Friday  that details exactly how the devices were compromised. The target  audience of the NBC piece, [he said on Twitter]("https://twitter.com/lowcalspam"), "wasn't technical."


  In its Sochi visitors guide, meanwhile, the U.S. State Department  warned travelers that "Russian Federal law permits the monitoring,  retention and analysis of all data that traverses Russian communication  networks, including Internet browsing, email messages, telephone calls,  and fax transmissions."



Notice that the quote includes a link to blog post by Wilhoit.

---

### Post by tgalati4 on 2014-02-06
The data breech wouldn't bother me as long as the toilets work and the water is clean.

---

### Post by bashiergui on 2014-02-06
> And if the report had been able to go into more depth, it would have been interesting to see how Ubuntu would have faired under the same circumstances. Given that it was so easy to hack the new Apple laptop (apparently), Ubuntu probably wouldn't offer any advantages. The exploits, I'm guessing, attack the weaknesses inherent in cross-platform applications along with the glaring weaknesses in public wifi.Right, Ubuntu is just as vulnerable to wifi MITM as any other OS. If the experiment was done over wifi, then all an attacker has to do is intercept the traffic, inject his own malware & then forward it on to you. The cross-platform stuff would be the obvious target to reach the maximum number of users.

---

### Post by estamets on 2014-02-07
They weren't in Sochi, they were in Moscow. Here's another angle to that exact video. 

[http://blog.erratasec.com/2014/02/that-nbc-story-100-fraudulent.html#.UvSNmnVdW9U](http://blog.erratasec.com/2014/02/that-nbc-story-100-fraudulent.html#.UvSNmnVdW9U)

Oh yeah.. Read the comments too.. I was interested in how he opened that macbook too.

---

### Post by bashiergui on 2014-02-07
Yeah... My only response is WTH?

The NBC story was beyond FUD. It was just fiction. 

Note to self: if ever talking to the press, speak veeeeeerrrrrryyyyy slowly and use really small words. Maybe make pretty cartoons to illustrate your point.

---

### Post by mr-woof on 2014-02-08
I've come across some more details of the hack/incident, there is a link to the white paper pdf. 

[http://blog.trendmicro.com/russia-experience-part-2/](http://blog.trendmicro.com/russia-experience-part-2/)

---

### Post by neu5eeCh on 2014-02-08
> **estamets said:**
> They weren't in Sochi, they were in Moscow. Here's another angle to that exact video. 

[http://blog.erratasec.com/2014/02/that-nbc-story-100-fraudulent.html#.UvSNmnVdW9U](http://blog.erratasec.com/2014/02/that-nbc-story-100-fraudulent.html#.UvSNmnVdW9U)

Oh yeah.. Read the comments too.. I was interested in how he opened that macbook too.

Too bad,really. I was looking forward to reading about some interesting hacks (zero-day exploits), but if all they did, *after all*, was download malware and install, seems the story is more about the deliberately misleading dishonesty of a reporter than the expected dishonesty of Russian hackers.

---

### Post by bashiergui on 2014-02-08
Crikey, they slaughtered his original message which was worth telling.

[http://www.trendmicro.com/cloud-content/us/pdfs/security-intelligence/white-papers/wp-from-russia-with-love.pdf](http://www.trendmicro.com/cloud-content/us/pdfs/security-intelligence/white-papers/wp-from-russia-with-love.pdf) > The experiment results featured in this paper revealed that the following general best practices should help protect devices and the data they contain from similar attacks:
• Update software. When using a new laptop, immediately update it from a trusted source and on a secure Internet connection.
• Don’t rely on default security settings. Install a multilayered security solution that relies not just on malware detection but also on Web reputation, behavior monitoring, and email scanning.
• Trust your instinct. If you find an email from a random person suspicious, don’t click links embedded in or open files attached to it. Or better yet, don’t even open it.
• Go straight to the source. Rely only on trusted sites when looking for information on any much-discussed event such as the Sochi Olympics. Keep in mind that the more hype and attention an event gets, the more likely that attackers will abuse it.

---

### Post by Old_Grey_Wolf on 2014-02-09
I have always known that if you go on a public wifi network **anywhere** without using protections or common sence you will be hacked eventualy.

I was curious what exactly was installed on the Ubuntu laptop for monitoring the other computers and network. All I have seen so far are vague descriptions.

---

### Post by bashiergui on 2014-02-09
> **Old_Grey_Wolf said:**
> I was curious what exactly was installed on the Ubuntu laptop for monitoring the other computers and network. All I have seen so far are vague descriptions.
From the link I posted:

"We then needed to consider how to collect network traffic. Without having this ability, we would not be able to differentiate malicious from normal network traffic. To solve the problem, we tethered our own Wi-Fi access point off the physical connection within the hotel room. We then used a network tap to gain direct access to the traffic coming from our devices to the outside world. To keep the environment as clean as possible, we installed logging and monitoring tools on a separate Linux box and a virtual machine. We used these to capture and analyze network traffic. We used a combination of Snort (custom and standard rules), BroIDS, tcpdump, ntop, and internal Trend Micro tools to help identify known command-and-control (C&C) servers and malicious binaries that can affect the devices."

I'm guessing the "internal Trend Micro tools" are Deep Discovery [http://www.trendmicro.com/us/enterprise/security-risk-management/deep-discovery/](http://www.trendmicro.com/us/enterprise/security-risk-management/deep-discovery/)

---

### Post by Old_Grey_Wolf on 2014-02-09
> **bashiergui said:**
> I'm guessing the "internal Trend Micro tools" are Deep Discovery...

You are gussing. Like I said, vague.

---

### Post by bashiergui on 2014-02-09
I read it as "we installed our proprietary secret sauce", i.e. hire us/buy it from us to use in your business.

I'm pretty cynical though...

---

