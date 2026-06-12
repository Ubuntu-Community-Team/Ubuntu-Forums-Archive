---
title: "What can a rogue device realistically do on your network?"
date: 2019-03-07
forum: Security
---

### Post by John_Patrick_Mason on 2019-03-07
Let's suppose I have a rogue device on my network, the rogue device can:

1)  Use HTTPS spoofing using [Punycode]("https://arstechnica.com/information-technology/2017/04/chrome-firefox-and-opera-users-beware-this-isnt-the-apple-com-you-want/")  to create a domain that looks very  similar to the URL a person is  interested in. I'm guessing the way to guard  against this, would be to  check the detailed information contained in the certificate.

2)  Redirect the potential victim to a bogus site that infects the  victim's  browser in a drive-by download by exploiting a vulnerability  within the  browser that allows the attacker to steal a session cookie.  To redirect a  victim's computer to a bogus website in 1) and 2), does  the attacker need to modify  the IP address of the DNS server used by the victim or can the  attacker redirect a victim's  computer to a bogus website without  having access to the router?

3)  Use a [cross-site scripting attack]("https://doubleoctopus.com/security-wiki/threats-and-tools/session-hijacking/")  where the attacker tricks a browser  into running code that is treated  as trustworthy because it appears to belong to the server, but ends up  stealing the victim's session cookie for the attacker.

4) The person decides to log in  to a website,  that might use  encryption on the login page, but does not use encryption  for the rest  of the site once authenticated, thereby allowing the  attacker to steal  the victim's session cookie by sniffing packets and  impersonate him ([side jacking]("https://doubleoctopus.com/security-wiki/threats-and-tools/session-hijacking/")),  even if the password itself isn't compromised. Is  this one of those  websites said to have "mixed" content? Wouldn't this  website appear  with a gray padlock with a yellow warning sign next to the  address bar  in FF?

Is that all?

---

### Post by DuckHook on 2019-03-08
Firstly, the phrase "rogue device" is so vague as to be almost meaningless.

Taking rogue device in its most pernicious form, it would allow far more than what you've listed. And we don't have to go to any lengths enumerating all the things it could be (which would be as long as your arm and a waste of time). Assuming a fully compromised rogue device, it could act as a packet sniffer for your entire LAN, which means it would catch every login id and password you use. The average user does not encrypt their local LAN traffic, nor their NAS files, nor their local directories: so it's open season on all e-mails, stored files, financial records, medical correspondences, web passwords, you name it. In short, for the average user, it would be game over.

Consider the following scenario: a rogue device has complete access to your NAS files. It replaces a frequently accessed PDF with a Trojan. The next time anyone opens this file, it installs a keylogger into their local machine. Bingo. Everyone has just been pwned.

You are basically raising the issue of hardening your internal LAN. Most people set up a firewall and then assume that everything outside is evil, and everything inside is hunky-dory. Some amazingly stupid Fortune-500 companies act this way. This means that a single breach is enough to compromise the whole system. What is the point to using strange exotic attacks when a dead simple one can skim off everything of importance? Equifax, anyone? Subscribing to security feeds and getting the weekly reports of yet another dozen major organizations which have been compromised is, frankly, depressing.

To get a more refined answer, you need to specify what you mean by "rogue device". But as to the larger picture, it is truly pathetic how easy it is for bad actors to penetrate institutional defences and wreak havoc, either holding entire hospital groups to ransom, or stealing national or industrial secrets, or stealing entire bitcoin wallets worth millions, or simply upending your life through identity theft.

---

### Post by John_Patrick_Mason on 2019-03-08
[QUOTE=DuckHook]Assuming a fully compromised rogue device, it could act as a packet  sniffer for your entire LAN, which means it would catch every login id  and password you use. The average user does not encrypt their local LAN  traffic, nor their NAS files, nor their local directories: so it's open  season on all e-mails, stored files, financial records, medical  correspondences, web passwords, you name it. In short, for the average user, it would be game over.[/QUOTE]

OK, but how is this different from connecting to an open Wi-Fi network at your local Starbucks? I thought HTTPS was supposed to preclude these kinds of attacks, assuming you take the time to check the information on a certificate. Or is connecting to your home network fundamentally different from connecting to an open Wi-Fi network at your local public place?

---

### Post by DuckHook on 2019-03-09
See this: [https://medium.com/@veronica.yudina/https-weaknesses-4257828727a9](https://medium.com/@veronica.yudina/https-weaknesses-4257828727a9)

I sloppily conflated two issues in my initial response: https does indeed offer some protection for your web sessions and thereby your internet-facing IDs and passwords; but are those really the most sensitive stuff on your LAN?

How many of us use Samba or NFS on our NASes? Are those transmission protocols encrypted? Are the NASes themselves encrypted? The vast majority of users are hooked up to commercially purchased NASes like Western Digital MyBooks that serve files in the clear to any request from anyone on the LAN. Many users (if they back up at all) will back up the contents of their local machines to partitions on that primitive NAS, again, completely unencrypted and in the clear. I don't know about you, but my net IDs and passwords are not my most sensitive data. It's my financial data, my tax returns, my e-mails, my correspondences, my medical history, etc all of which reside on my NAS. A "rogue device" that is snugly embedded in your LAN has pretty much unfettered access to all of that. And what about my scenario:> **DuckHook said:**
> …a rogue device has complete access to your NAS files. It replaces a frequently accessed PDF with a Trojan. The next time anyone opens this file, it installs a keylogger into their local machine. Bingo. Everyone has just been pwned.

So, from a purely technical perspective, a "rogue device" will not break https without a lot of esoteric strategies that you describe in your first post. But my point remains: why bother to go to such trouble? Once a "rogue device" makes it into your LAN, you've basically given away the keys to your house.

---

### Post by John_Patrick_Mason on 2019-03-09
[QUOTE=DuckHook]I sloppily conflated two issues in my initial response: https does  indeed offer some protection for your web sessions and thereby your  internet-facing IDs and passwords; but are those really the most  sensitive stuff on your LAN?[/QUOTE]

I don't use any form of network attached storage, so am I basically safe, except for the types of attack mentioned in my first post?

---

### Post by DuckHook on 2019-03-09
> **John_Patrick_Mason said:**
> …am I basically safe…?
Perhaps you should read the link in my sig: ***Security Basics***

---

### Post by John_Patrick_Mason on 2019-03-09
[QUOTE=DuckHook]Perhaps you should read the link in my sig: ***Security Basics***[/QUOTE]

OK, but nevermind about outside threats for second. Let's go back to my first post for a sec. Suppose I forgot to change the default password to my Wi-Fi, and some pesky teenager gains access to my wireless network. What can they realistically do while on my network, going back to my first post? I just want to know what they can do while on your network.

---

### Post by DuckHook on 2019-03-10
Your question is like asking: "what can a bad guy do if he breaks into my home/bank account/business?"

Dunno. I'm not telepathic, so can't read his mind.

If you want to know more ways that a scumbag can leverage a compromised network, you will have to do your own research. Here are a few of the sources that I subscribe to. Be prepared for some depressing reading:

[LIST]
[*][https://nakedsecurity.sophos.com/](https://nakedsecurity.sophos.com/)
[*][https://www.theregister.co.uk/security/](https://www.theregister.co.uk/security/)
[*][https://www.sei.cmu.edu/about/divisions/cert/index.cfm](https://www.sei.cmu.edu/about/divisions/cert/index.cfm)
[*][https://www.sans.org/](https://www.sans.org/)
[/LIST]
The problem with your question is that:

[LIST]
[*]Your restriction "nevermind about outside threats" makes no sense. With the single&#8212;but significant&#8212;exception of employees gone bad, all threats are by definition from outside.
[*]Therefore, what would an outsider do with full network access? The possibilities are endless; certainly far too numerous and varied to list. So much depends on the topology of the network, the internal security measures, the savvy and malice of the black hat versus the savvy and cunning of the white hat&#8230;
[*]You seem to think that there are just a handful of actions open to such scumbags. This is a grossly erroneous assumption. I'm not prepared to pick off what can only be a small sampling. This would be incomplete and misleading.
[*]What about stuff we don't even know about? Zero day exploits? Who can "explain" those to you?
[/LIST]
You need to do your own research and come to your own conclusions. As already suggested, taking the measures that I've already linked you to will go a long way to hardening your system against all sorts of breaches. If you are interested in more obscure, theoretical risks, I've already provided those links too.

---

### Post by John_Patrick_Mason on 2019-03-11
Please don't get mad. I'm just trying to understand. When you said an attacker could gain access to everything, because of the way you phrased your response, I thought that would only be the case if you used some form of network-attached storage on your network. Obviously, I know all threats come from "outside", what I really meant when I asked that question was what could an attacker do if they can't get into your system.

And to be fair, my original question was mainly about ways to get around HTTPS. Of course, if an attacker is able to breach your computer's defenses, what's the point of using esoteric attacks like HTTPS Punycode, but that wasn't clear in your response. It might have been clear to you, but it wasn't clear to me. It's not like I don't mind doing research, after all, I did read the book version of LinuxCommand.org, which you link in your signature. That doesn't mean I don't have gaps in my knowledge, I most certainly do, even after reading all 500+ pages.

---

### Post by DuckHook on 2019-03-11
Apologies coming across as angry. I wasn't angry at all. The problem with a print medium like these forums is they don't convey body language, which would have been more indicative of shrugs than anger.

The link in my first post describes very elementary ways in which a packet sniffer can decipher very private aspects of our lives merely by seeing which sites we visit. If you follow the further articles in that link, there are further descriptions of what a bad actor can do without ever breaking HTTPS. In my case, knowing details like where I bank, which websites I regularly visit (thereby gaining knowledge of the sites on which to focus brute force password attacks), which e-mail servers I use, what my private tastes are, whether I am a social media person and if so, which ones&#8212;are enough to give me the heebie-jeebies. From there to identity theft is not a big step.

Example: do you have *ssh* activated? Is it the default install and merely password protected? How about VNC? If so, a scumbag who has compromised a "rogue device" could simply take his time cracking the password to your admin account. Once that is done, game over. So, the answer to your question involves a million different ways that people configure their system and their network: hence what appears like my exasperated non-answer to your question.

---

### Post by John_Patrick_Mason on 2019-03-12
I still don't get why security experts consider open Wi-Fi networks,  like the ones you find in an airport, insecure. Assuming you carefully  review the info belonging to a website's certificate when you visit say, your banking site, what can an  attacker really do, except try to infect your computer with malware through a redirect.

Assuming you don't visit a misconfigured website referenced in paragraph 4) of my first post, assuming that's really what paragraph 4) is, it's not like they can steal your login credentials.

Sure they can find out  which websites you visit, even if they can't find out which particular  page you're on, but I can live with that, since I would never visit a  sensitive website on an open Wi-Fi network. If I was connected to my  private home network, and there was a rogue device (think script kiddie) on my network, that'd be different, since I might visit a sensitive site when connected to my home network. And since I also use complex  passwords on the sites for which I have an online account, they can't just brute force any of my online accounts, even if they know which websites I have an online account with.

As for setting up my system as an ssh server, I've used ssh in the past, mainly when I was learning how such connections are established, with a public/private key, of course, but the openssh-server package has long been purged from all of my systems, with all ports now blocked by default.

So why do security experts consider open Wi-Fi networks unsafe?

---

