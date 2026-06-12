---
title: "BBC - Security failings in home routers exposed"
date: 2014-02-22
forum: Security
---

### Post by Edward_B on 2014-02-22
Please see the full story at:   [http://www.bbc.co.uk/news/technology-26287517](http://www.bbc.co.uk/news/technology-26287517)


Could anyone help explain to me whether the type of data and encryption through Ubuntu/Mint will vary to Windows when sending it through a router?

I suspect the answer is no. I'm guessing that servers hosted elsewhere need to understand a universal language when it comes to data requests from internet users such as you and I.

The reason why I ask this is because one of the main attractions to me for using Ubuntu/Mint was the security it offers us users.  This article suggests to me that this could be rendered useless if one were to have a buggy or inadequete router.

Could anyone expand on my thinking?

Thanks in advance

Ed

---

### Post by mikewhatever on 2014-02-22
Sounds like you mix up the security of a router with that of a PC operating system, such as Ubuntu or Windows. The article, in fact, does not suggest anything about the security of the latter, nor does it say the two are connected. If a Windows or Ubuntu system behind a router is uptodate, and properly configured, the compute should be safe.

---

### Post by Edward_B on 2014-02-22
"T[COLOR=#000000]he article, in fact, does not suggest anything about the security of the [PC operating system]"

Really? What's this sentence then: "[/COLOR][COLOR=#333333][FONT=Arial]Earlier this month, many users of Asus routers who remotely connect via the gadget to hard drives in their homes, perhaps to watch DVDs they have ripped, found that someone had used the same feature to upload a text file urging them to do more to make the device safe."
[/FONT][/COLOR][COLOR=#000000]
Where is the harddrive? On someones PC? How is that PC run, using an OS or from Fairyland?  Can someone less condescending and with some proper analysis help guide me to the answer for my question?

Basically, if all online data sent/received goes from a PC-Router-Server and the router is compromised, does it make any difference what OS you have on your computer as to whether the data is more or less secure i.e the format of transmitted data? 

Secondly, what if my router was compromised and I decided to do online banking using Ubuntu.  Would the security of my PC make any difference if my router was hacked?

This is big news to me because it means that it doesn't matter how safe your PC is if your router is hacked.  If you have a popular router, the chances are there are people constantly trying to hack and take control of it.  This means less safety for dealing with sensitive information = I shouldn't do stuff like online banking all the time.[/COLOR]

---

### Post by mikewhatever on 2014-02-22
Well, I don't know why you are so upset. Routers are not perfect - that's life. That said, it's often less of a deal, then you might be led to think.
...but, apparently, you don't seem to want my advice, so I'll let others handle it. Please don't yell at them, it's not nice.
Good bye.

---

### Post by Don_Stahl on 2014-02-22
> Edward_B: [COLOR=#000000]Where is the harddrive? On someones PC? How is that PC run, using an OS or from Fairyland? Can someone less condescending and with some proper analysis help guide me to the answer for my question?[/COLOR]

The BBC doesn't really say anything about the OS. Now, I can pretty much guarantee if you find a way to connect a bare hard drive to a router you're not going to have any joy. So the Beeb is glossing over the technical details. Where the users connecting to a smart TV? A Windows box, an XBox, a Mac? Given Linux's fat 1% user share, odds are they *weren't* using Linux. But that's just the odds.

So, maybe this is one way to look at it: if your PC has a firewall and it's configured well, then a compromised router will not be able to infect your system. But all outbound traffic goes through the router, and so -- in theory! -- if a hacker manages to capture that data stream then he can watch everything you're sending. The BBC article did not say the router exploit was capable of doing that, and I don't know that such an exploit currently exists in the wild.

But I think this is a very limited, very trivial example. To fully answer the question "what are the threats posed by all possible router exploits" would require a lot more knowledge than exists in my tiny brain.

---

### Post by bashiergui on 2014-02-22
> **Edward_B said:**
> Could anyone help explain to me whether the type of data and encryption through Ubuntu/Mint will vary to Windows when sending it through a router?


I suspect the answer is no. I'm guessing that servers hosted elsewhere need to understand a universal language when it comes to data requests from internet users such as you and I.


The reason why I ask this is because one of the main attractions to me for using Ubuntu/Mint was the security it offers us users. This article suggests to me that this could be rendered useless if one were to have a buggy or inadequete The security risk you would have if someone hacked your router is that they would be a "man in the middle" (MITM) and could read all the traffic you send over the internet and to other computers in your private network. Your operating system is irrelevant, Mac, linux, windows, solaris, etc. all are equally vulnerable to this.


Generally the encrypted traffic won't be readable by a MITM- it will be gibberish to him.  What you would be concerned about would be the unencrypted traffic, which is normal HTTP traffic. A MITM would be able to read all your HTTP traffic. MITM could also inject malicious packets into your traffic, or redirect you where ever he wanted. To defend against that you can use a VPN- there are free and cheap services all over. An easier, less effective solution is to force all traffic over HTTPS (browsers have add-ons that do this). 


Now I'll ramble on about encryption, as your question demonstrates that you don't have an understanding of it.


There are various types of encryption. For instance you can encrypt your linux home directory or drive. You can also encrypt a Windows drive using the same general concepts. You can encrypt files like zips and MS Office documents. There are a ton of encryption methods with varying degrees of security. Regardless, these are completely unrelated to and unaffected by your router.


I think the encryption you're concerned about is related to sending and receiving traffic over the internet. And yes, there are universal protocols used to accomplish this.


When you log into your bank website, then the encryption is initiated by the web page using a certificate over HTTPS. Your browser, regardless of your operating system, checks that the website is using a valid certificate. Then all the traffic between your computer and your bank is encrypted as it travels, then decrypted on either end. If someone hacks your router then they would have to trick a certificate authority into giving them a valid certificate in order to see your traffic. It's possible but quite unlikely. It is irrelevant whether you're using windows or linux, the likelihood is the same. 


Then there's ssh encryption. It uses private and public keys to create an encrypted tunnel between you and the ssh server. An attacker would have to steal the private & public keys in order to see your ssh traffic, and he'd either need to break into your computer or solve an unsolvable mathematical equation to do it.  This is also independent of operating system. 


Then you have VPN encryption. There are a variety of implementations, but they all create a secure tunnel between you and the server similar to ssh. VPNs use additional protocols to maintain the encrypted traffic. Someone that hacks your router has a ton of work to do if they want to see inside a VPN tunnel, both on Windows and linux, making it extraordinarily unlikely.

---

### Post by dry crust on 2014-02-22
> Where is the harddrive? On someones PC? How is that PC run, using an OS or from Fairyland? Can someone less condescending and with some proper analysis help guide me to the answer for my question?
When you look at that article from the BBC, it has very few facts in it, it is also talking about two separate articles (a blog about security flaws in Linksys and Asus routers, and a report on the security of routers bought over the internet) and the few facts look more intended to create alarm than be useful to someone trying to protect themselves or fix a security flaw. The fact that it is talking about two different articles that aren't on exactly the same issue just makes this article more confusing, and tends to make one even more suspicous that the writer wants to create alarm and not actually be helpful. 
For example, we have an unnamed "gang" based in Poland stealing cash only from Linksys and Asus routers. Now straight away we start getting suspicious the writer has very few facts to go on. I have no doubt there are hackers in Poland who hack into computers and steal credit card details, just as there will be hackers in the UK, France, America, Russia, China, etc wanting to do the same, but those are hackers and what they stole was credit card numbers, and they steal from any computer they can get into, not just from Linksys and Asus computers. Or do they just hate Linksys and Asus computers? To me, a gang is a group of thugs. Now that would be a far more interesting story: a group of thugs from Poland that hate Linksys and Asus so much that they learnt how to hack into them, but we aren't told their name. Why not? Next we have this gang stealing cash, but why just cash, why not credit card numbers as well? To me "cash" is currency in its hard form (i.e. notes and coins), so this sounds like this gang is taking money out of an ATM using stolen account and PIN number information, but then why not say that? My bank doesn't display to me my PIN number when I access my account online, and as far as I know no other bank does either, so how is it this gang is able to get the PIN number unless they either get it from the user's card or from the bank? Are the gang able to hack a bank computer? Which bank? And why are they only hacking into Linksys and Asus routers? 
As you quite rightly point out, they don't mention what operating system is being used on the router, and without knowing that then the home user is unable to asses whether they need to worry or not. One can even argue this article is intended to discredit Linksys and Asus. Are there any similar articles from other sites? If not, then I think this report from the BBC is one you should put in the "pass" basket. It may be true, but there are so many unknowns that it isn't worth the effort to even try and get to the bottom of what it is about. The internet has about a million better and more factual reports written every day.

---

### Post by Cavsfan on 2014-02-22
As long as your router is configured to use AES WPA-PSK (previously shared key) and a decent password you are fine. 
This is the safest currently available I'm pretty sure. The password changes every 10 minutes and I've never had any problems.

[ATTACH=CONFIG]250584[/ATTACH]

If you are just using WEP anyone can purchase some software and just be near your house and steal anything they want.

---

### Post by lisati on 2014-02-22
> **Edward_B said:**
> 
Really? What's this sentence then: "Earlier this month, many users of Asus routers who remotely connect via the gadget to hard drives in their homes, perhaps to watch DVDs they have ripped, found that someone had used the same feature to upload a text file urging them to do more to make the device safe."

The article also said that the vulnerability was only there if the remote management feature was turned on. There's a simple solution: turn off remote management of both your router and your computer if you don't need them.

---

### Post by bashiergui on 2014-02-22
> **lisati said:**
> The article also said that the vulnerability was only there if the remote management feature was turned on. There's a simple solution: turn off remote management of both your router and your computer if you don't need them.
+1
That workd for this particular vulnerability, not necessarily every router vuln out there.

---

### Post by CharlesA on 2014-02-22
> **Don_Stahl said:**
> The BBC doesn't really say anything about the OS. Now, I can pretty much guarantee if you find a way to connect a bare hard drive to a router you're not going to have any joy. So the Beeb is glossing over the technical details. Where the users connecting to a smart TV? A Windows box, an XBox, a Mac? Given Linux's fat 1% user share, odds are they *weren't* using Linux. But that's just the odds.

It affected anyone who had attached a USB hard drive to their router.

Have a read:
[http://arstechnica.com/security/2014/02/dear-asus-router-user-youve-been-pwned-thanks-to-easily-exploited-flaw/](http://arstechnica.com/security/2014/02/dear-asus-router-user-youve-been-pwned-thanks-to-easily-exploited-flaw/)

> **lisati said:**
> The article also said that the vulnerability was only there if the remote management feature was turned on. There's a simple solution: turn off remote management of both your router and your computer if you don't need them.

Indeed. There were reports of the same thing happening with AiCloud off, but the vulnerability should have been fixed in any case.

Makes me glad I haven't hooked up a USB drive to my router and are running a build of DD-WRT on it to boot.

---

### Post by Don_Stahl on 2014-02-22
Thanks for the correction, CharlesA. I shouldn't have responded without knowing a lot more about routers and drives than I do!

---

### Post by CharlesA on 2014-02-22
No worries there. :)

---

### Post by Edward_B on 2014-03-04
Thank you all so much, I now have a basic understanding of my problem and some work arounds. A very good community you guys have here.
 
Bashergui, I am extremely grateful you took the time out to explain more thoroughly some key concepts to me and you explained them very well.  I hope there are others that will eventually learn from it.

---

