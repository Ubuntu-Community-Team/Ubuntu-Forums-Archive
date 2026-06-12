---
title: "MITM in our local coffee shop"
date: 2012-05-22
forum: Security
---

### Post by babdah on 2012-05-22
My friend and I were study at our local coffee house and when he noticed a guy using something called "Cain and Able". I have very little knowledge about these types of programs because I am still learning but my friend told me that there is no real way to be able to protect your self from these types of attacks. From the little that i have read about this types of software, i was wondering if there was a in Ubuntu to be able to encrypt all data though the port so that even if these types of programs do intercept them they would not be able to crack the encryption? Or is there any way to protect ones self from this, other then reporting them to the network admin?

---

### Post by wilee-nilee on 2012-05-22
Chances are that this is illegal in a public space, in most parts of the world, I would call the police, and wait to see what is done.

I have no experience in this area, but with a quick google search it seems this may the case.

This seems to just be a efficient packet sniffer with cracking tools for hashes on passwords at least that is what I saw, probably other tools as well.

---

### Post by babdah on 2012-05-22
Well, did not think of that. He just told the network admin that was there about it. It occurred in the US , NC to be exact. I just figured there was a way in Linux to be able to encrypt DNS traffic between the computer and the router so that they could not sniff it out.

---

### Post by wilee-nilee on 2012-05-22
> **babdah said:**
> Well, did not think of that. He just told the network admin that was there about it. It occurred in the US , NC to be exact. I just figured there was a way in Linux to be able to encrypt DNS traffic between the computer and the router so that they could not sniff it out.

In the US that is illegal as far as I know, get them questioned by law enforcement, or at least get them on law enforcements radar. This is a slippery area in general, as the laws I believe are behind the technology, but in a public place I would default to a 911 call if it was me.

Most people would not have a clue what that is I would not recognize it that is for sure never heard of it before.

---

### Post by roelforg on 2012-05-22
Use something like the tor project.
It encrypts the data on your pc and then sends it through a chain of tor-nodes (don't worry, it defaults to client only so you're not a node unless you tell it to make you one) before sending the data to the web.

---

### Post by IWantFroyo on 2012-05-22
> **roelforg said:**
> the tor project.

+1. Either that or a VPN.

I've heard of Cain and Abel, but haven't seen it mentioned in a long time.

From their website: "Cain & Abel is a password recovery tool for Microsoft Operating  Systems.        It allows easy recovery of various kind of passwords by sniffing  the network,        cracking encrypted passwords using Dictionary, Brute-Force and  Cryptanalysis        attacks,  recording VoIP conversations, decoding scrambled  passwords, recovering wireless network keys, revealing password boxes,  uncovering        cached passwords and analyzing routing protocols."

In other words, if used maliciously, it's pretty nasty and a real thing to watch out for.

---

### Post by computeratin on 2012-05-22
What the guy was doing is illegal in the US. At the minimum he was a butthead; more likely a thief. But, good luck with calling 911.  

1) 99.999999999% of dispatchers and officers will have no idea what you&#8217;re talking about. I know; I was MilPo. 


2) With what&#8217;s going on with the economy most cities don&#8217;t have a broad enough tax base to be able to afford to hire enough cops to keep up with the murders; much less stuff like this. And, if you can convince them that they need to come the likeliest scenario is that they&#8217;ll be so shorthanded and the call given such low priority that it will be 2-4 hours before they show. People like this usually don&#8217;t get busted until they come to the attention of the FBI. 

And good luck with the &#8220;admin&#8221; at a coffee shop. It will be the manager. He/she probably has a degree in art history and their IT knowledge will probably be limited to what they picked up from that nerd they dated that one time in college on a dare.

In other words: You&#8217;re on your own.

I highly advise that you stay out of TOR unless you are very computer savvy. Don&#8217;t get me wrong; it&#8217;s a wonderful project. The founder has his heart in the right place and so do the greatest majority of people who set up nodes. It has helped untold oppressed people make contact with the outside world. But, like anything else it can be abused. There are nodes that are set up by intel agencies, data thieves and crackers. And as an end user you&#8217;ll never know whose node you&#8217;re being routed through. Besides, it&#8217;s slow.

Personally I never open a TOR tunnel unless it&#8217;s **through **a VPN.

Which is what you need.

There are several solutions available:
1) Buy a dedicated hardware / software combo. (~$150 for one that will handle 5 machines).
2) Get an old machine from the pawnshop, etc and use any of the many, many free tools that are available to build your own.
3) Subscribe to a service.
4) Use a free one.

They all have their pros and cons; including security and privacy, do some research before you just jump in to one. Some (not all) of each of the various types have been cracked at one point or another; HideMyAss not that long ago.
 
Welcome to the information age.

---

### Post by haqking on 2012-05-22
Using cain and abel is not illegal anywhere.

It depends what the person was doing with cain and abel, it does many things.

Also if you want to encrypt your traffic for security, DO NOT use the tor project for that purpose either.

Get a Secure VPN or something similar. Or dont do anything sensitive from a public network.

Peace

---

### Post by computeratin on 2012-05-22
> **haqking said:**
> It depends what the person was doing with cain and abel, it does many things.
 
Name one good thing that it will do in a coffee shop full of strangers?

---

### Post by wilee-nilee on 2012-05-22
> **haqking said:**
> Using cain and abel is not illegal anywhere.

It depends what the person was doing with cain and abel, it does many things.

Also if you want to encrypt your traffic for security, DO NOT use the tor project for that purpose either.

Get a Secure VPN or something similar. Or dont do anything sensitive from a public network.

Peadce

Tough one with the law for sure, but a oops I spilled my gallon container of coca cola on your laptop, oh my what will we do now, might work. 

But I'm a pretty big guy so never do I fear another, and assault is punishable, if the user decides to do it. Not the safest way to negotiate life, but oh well.

Personally I would probably act in some manner if I knew they were there sniffing.

---

### Post by haqking on 2012-05-22
> **computeratin said:**
> Name one good thing that it will do in a coffee shop full of strangers?

Well i could be sat in a coffee shop with cain and abel, cracking a password from my local SAM, auditing my own passwords, generating a secure password for my own use etc etc

My point is a tool does not imply illegal activity, it may have been but does not imply it.

example: Using bittorrent does not mean you are downloading illegal content.

My point stands, posessing and using cain and abel anywhere is not illegal.

I use my backtrack laptop in coffeeshops many times, doesnt mean i am doing something illegal, or that the police would know anything about it or be able to do anything about it either ;)

Peace

---

### Post by haqking on 2012-05-22
> **wilee-nilee said:**
> Tough one with the law for sure, but a oops I spilled my gallon container of coca cola on your laptop, oh my what will we do now, might work. 

But I'm a pretty big guy so never do I fear another, and assault is punishable, if the user decides to do it. Not the safest way to negotiate life, but oh well.

Personally I would probably act in some manner if I knew they were there sniffing.

I dont think its a tough one at all, i think most law enforcment wouldnt bother turning up, if they did what they gonna do ?

excuse me sir do you have a piece of free software for password auditing on your laptop ? yes i do so what ? oh ok thanks.

LOL

---

### Post by computeratin on 2012-05-22
> **haqking said:**
> My point stands, posessing and using cain and abel anywhere is not illegal.
 
I use my backtrack laptop in coffeeshops many times, doesnt mean i am doing something illegal, or that the police would know anything about it or be able to do anything about it either ;)
 
Peace
 
That would depend on some of the scarier interpretations of the NDAA. You can argue it from Gitmo if you want. Personally I don&#8217;t take those kinds of chances, when I want to play with those kinds of toys I do it in the (I hope) privacy of my own home.

And I&#8217;ll even give you the benefit of the doubt: I&#8217;ll accept on face value that **you** are a saint, most people aren&#8217;t. I know. I'll run my data through a VPN.

---

### Post by wilee-nilee on 2012-05-22
> **haqking said:**
> I don&#8217;t think its a tough one at all, I think most law enforcement wouldn&#8217;t bother turning up, if they did what they gonna do ?

excuse me sir do you have a piece of free software for password auditing on your laptop ? yes i do so what ? oh ok thanks.

LOL

These are all as if strawman arguments anyway, kinda fun though. ;)

---

### Post by computeratin on 2012-05-22
> **wilee-nilee said:**
> These are all as if strawman arguments anyway, kinda fun though. ;)
 
IDK? The world is getting to be a spooky place. I got out of being a military cop b/c I didn't like the way the wind was blowing or some of the scenarios that we started training for.
 
I didn't sign up for that ....

---

### Post by haqking on 2012-05-22
NDAA or gitmo has little to do with packet sniffing on a public network or owning security auditing tools, especially when the person may be employed as pen tester.

Anyways the whole wiretapping thing on public networks is still a grey area i believe, i am no longer in the US so the law may have changed since the Google thing.

however it is not a violation of the law to packet sniff on public networks

"18 U.S.C. § 2511(2)(g)(i) permits "any person" to intercept an  electronic communication made through a system "that is configured so  that . . . [the] communication is readily accessible to the general  public."  &#8220;[T]he legislative history of  the ECPA suggests that Congress  wanted to protect electronic  communications that are configured to be  private, such as email and private  electronic bulletin boards,&#8221; as  opposed to publicly-accessible  communications. See Konop, 302 F.3d at  875, citing S. Rep. No. 99-541, at  35-36, reprinted in 1986  U.S.C.C.A.N. 3555, 3599. .&#8221;

Source: [SIZE=1]**18 USC § 2511 - Interception and disclosure of wire, oral, or electronic communications prohibited**[/SIZE]

[https://ilt.eff.org/index.php/Privacy:_Wiretap_Act](https://ilt.eff.org/index.php/Privacy:_Wiretap_Act)

That being said there is big difference between passive packet sniffing and ARP poisoning though...LOL ;-)

---

### Post by computeratin on 2012-05-22
Well, since the forum told me I can't send you a PM I guess this is the end of this one.

But, I didn't give up a career for no reason. And respect for the law ain't exactly what they're teaching the young guys now.

---

### Post by babdah on 2012-05-22
> **haqking said:**
> 
however it is not a violation of the law to packet sniff on public networks

"18 U.S.C. § 2511(2)(g)(i) permits "any person" to intercept an  electronic communication made through a system "that is configured so  that . . . [the] communication is readily accessible to the general  public."  “[T]he legislative history of  the ECPA suggests that Congress  wanted to protect electronic  communications that are configured to be  private, such as email and private  electronic bulletin boards,” as  opposed to publicly-accessible  communications. See Konop, 302 F.3d at  875, citing S. Rep. No. 99-541, at  35-36, reprinted in 1986  U.S.C.C.A.N. 3555, 3599. .”


[FONT=Arial][SIZE=2]I have to disagree with you just about what is quoted because with out the persons consent then everyone has the inherent right to privacy, see 18 U.S.C. §2511(2)(a)(i) [5] **The Communications Assistance for Law Enforcement Act**, the FCC, and the US Patriot Act all state the the government can and will wiretap, webtap and monitor many networks if they want according to this [http://fjallfoss.fcc.gov/edocs_public/attachmatch/DOC-266204A1.pdf](http://fjallfoss.fcc.gov/edocs_public/attachmatch/DOC-266204A1.pdf)  

So i take it, it is best to just stay off your personal info in public places then. Just because there is secure way. 
[/SIZE][/FONT]

---

### Post by Hungry Man on 2012-05-22
There is no real way to protect yourself from MITM in these situations. I think anyone who says there is probably doesn't know how easy it is to use these tools.

MAYBE it's possible with HSTS but IDK if any sites actually use it.

---

### Post by mr-woof on 2012-05-23
Was the coffee shop wireless open or encrypted? I would of thought if it was encrypted (WPA etc), the person trying the mitm attack wouldn't be able to sniff the encrypted packers?

If you have an old machine at home, you can also redirect your web traffic over ssh to your home machine, I've done this before and it works well. Just remember to secure ssh before you start opening it up to the world.

[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

---

### Post by haqking on 2012-05-23
> **babdah said:**
> [FONT=Arial][SIZE=2]I have to disagree with you just about what is quoted because with out the persons consent then everyone has the inherent right to privacy, see 18 U.S.C. §2511(2)(a)(i) [5] **The Communications Assistance for Law Enforcement Act**, the FCC, and the US Patriot Act all state the the government can and will wiretap, webtap and monitor many networks if they want according to this [http://fjallfoss.fcc.gov/edocs_public/attachmatch/DOC-266204A1.pdf](http://fjallfoss.fcc.gov/edocs_public/attachmatch/DOC-266204A1.pdf)  

So i take it, it is best to just stay off your personal info in public places then. Just because there is secure way. 
[/SIZE][/FONT]

Disagree all you like, you cant disagree with a quote unless i misquoted...LOL

The fact is in the wiretap act (which you yourself referenced) it clearly states what i quoted, so my point stands.

Peace

---

### Post by haqking on 2012-05-23
> **mr-woof said:**
> Was the coffee shop wireless open or encrypted? I would of thought if it was encrypted (WPA etc), the person trying the mitm attack wouldn't be able to sniff the encrypted packers?

If you have an old machine at home, you can also redirect your web traffic over ssh to your home machine, I've done this before and it works well. Just remember to secure ssh before you start opening it up to the world.

[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

How the person initially connects to the router (wpa handshake or not) has nothing to do with packet sniffing if you are connected to the same access point in this example.  It has nothing to do with traffic going through the access point. WPA or WIFI protected access merely encrypts traffic on your segment which is you to the AP.

If i compromise a local access point in the coffee shop then redirect all DNS traffic to my little DNS server on my virtual machine sat on same network, WPA or WPA2 wont help you very much ;-)

To the OP, as already stated, use of Cain and Abel does not imply illegal activity though it may have been, if the person was merely sniffing traffic on the public network then again it is still a grey area but currently not illegal due to the wiretap act and public networks.

If the person was doing ARP poisoning for example then yes they could be considered doing something illegal though the chances of law enforcement understanding any of that or being able to do anything about it unlikely, they wont be calling the FBI forensics team to examine the machine, starbucks wireless sniffing is not high on their list of priorities when it comes to cybercrime...LOL

And to make things more secure for yourself, you could use a secure VPN such as airVPN which if you want to maintain some anonymity also you can pay in bitcoins, though there are many others also.

Tor is OK but dont rely on it for security or even for strong anonymity.

More to the point dont use public networks or at least dont pass any personal or sensitive traffic through it when connected.

Peace

---

### Post by Hungry Man on 2012-05-23
Sniffing packets on a public access point is not illegal nor should it be.

1) Your wifi card receives these packets regardless.
2) Public wifi is the equivalent of screaming what you're doing in another language. Anyone can hear it.

Your wireless signal is broadcasted for yards, sometimes hundreds of feet. If I yell in Spanish across the street is it illegal for you to pull out a dictionary and figure out what I'm saying? No. That would be idiotic.

---

### Post by haqking on 2012-05-23
> **Hungry Man said:**
> Sniffing packets on a public access point is not illegal nor should it be.

1) Your wifi card receives these packets regardless.
2) Public wifi is the equivalent of screaming what you're doing in another language. Anyone can hear it.

Your wireless signal is broadcasted for yards, sometimes hundreds of feet. If I yell in Spanish across the street is it illegal for you to pull out a dictionary and figure out what I'm saying? No. That would be idiotic.

+1

Exactly

Using a public network such as a coffee shop is the same as having a chat with a friend in the same coffee shop, if i am sat next to you it is not illegal for me to hear your conversation, the nature of sound makes that possible whether i am listening intentionally or not, if i choose to intently listen it is still not illegal, if i choose to sit down at your table and butt into your conversation then that is a little different but it is a public place, the most you could do is leave or get me thrown out for harassment.

The fact is you chose to hold a conversation in public, my ears are allowed to listen, if you chose to have a private conversation then dont do it in a public place if you know what i mean.

Peace

---

### Post by HermanAB on 2012-05-23
Real men use netcat and grep for fun and profit.

It is easy to turn the table on a coffee shop sniffer.  Look at his MAC address and hijack his session.

---

### Post by Hungry Man on 2012-05-23
> **haqking said:**
> +1

Exactly

Using a public network such as a coffee shop is the same as having a chat with a friend in the same coffee shop, if i am sat next to you it is not illegal for me to hear your conversation, the nature of sound makes that possible whether i am listening intentionally or not, if i choose to intently listen it is still not illegal, if i choose to sit down at your table and butt into your conversation then that is a little different but it is a public place, the most you could do is leave or get me thrown out for harassment.

The fact is you chose to hold a conversation in public, my ears are allowed to listen, if you chose to have a private conversation then dont do it in a public place if you know what i mean.

Peace

It's not even just like talking to a friend. It's like screaming to a friend so that everyone in the coffee shop and most people out on the street can hear what you're saying.

---

### Post by computeratin on 2012-05-23
You guys can debate the legality all you want. That&#8217;s not the world we live in anymore; at least not in America. I walked away from my pension when an instructor told me that the proper response to the phrases &#8220;My constitutional rights&#8221; and &#8220;Posse Comitatus&#8221; was to split someone&#8217;s skull open.

Now DHS is making even the legitimate use of such tools reason enough for second thought with their new &#8220;terrorist spotting&#8221; guidelines (like its friggin bird watching or something). 

The latest guidelines lump all &#8220;privacy software&#8221; under one big umbrella, both software that can be used to maintain or violate privacy. Either one can get you slapped with the T label. Technically, under the new guidelines using a VPN qualifies you for the T label.

And once labeled as such they have the &#8220;right&#8221; to drop you down the rabbit hole; do not pass go, do not collect $200, poof, bye bye. 

I&#8217;m no slouch on endpoint security; but there are those here who know far more than I do. I will concede to their expertise on those points. I will say that a VPN is a very important part of it, but that there is also no such thing as perfect security. And you&#8217;re security should be multi-layered and never rely on a single point of failure.

The locals most likely would never show for something like this: they&#8217;re too shorthanded and probably wouldn&#8217;t understand any way. The nationals won&#8217;t show unless some moron drops the T word. Then they're libel to show with Bradley&#8217;s and Wart Hogs.
 

As for the rest: Unless or until you have participated in training exercises on how to conduct **warrantless** searches / seizures / home invasions (for all intents and purposes) and how to send US citizens out of the country to a military interrogation outpost without anybody catching on to what&#8217;s up (at least not right away) or how to confiscate firearms from law abiding citizens after a natural disaster or during a national emergency then I&#8217;ll keep my own counsel on what is and is not illegal. 
 
FYI: Simplest practical / functional definition of what&#8217;s illegal = Anything that will show me just how deep the rabbit hole goes.

---

### Post by haqking on 2012-05-23
> **computeratin said:**
> You guys can debate the legality all you want. That&#8217;s not the world we live in anymore; at least not in America. I walked away from my pension when an instructor told me that the proper response to the phrases &#8220;My constitutional rights&#8221; and &#8220;Posse Comitatus&#8221; was to split someone&#8217;s skull open.
 

Now DHS is making even the legitimate use of such tools reason enough for second thought with their new &#8220;terrorist spotting&#8221; guidelines (like its friggin bird watching or something). 
 

The latest guidelines lump all &#8220;privacy software&#8221; under one big umbrella, both software that can be used to maintain or violate privacy. Either one can get you slapped with the T label. Technically, under the new guidelines using a VPN qualifies you for the T label.
 

And once labeled as such they have the &#8220;right&#8221; to drop you down the rabbit hole; do not pass go, do not collect $200, poof, bye bye.
 

I&#8217;m no slouch on endpoint security; but there are those here who know far more than I do. I will concede to their expertise on those points. I will say that a VPN is a very important part of it, but that there is also no such thing as perfect security. And you&#8217;re security should be multi-layered and never rely on a single point of failure.

The locals most likely would never show for something like this: they&#8217;re too shorthanded and probably wouldn&#8217;t understand any way. The nationals won&#8217;t show unless some moron drops the T word. Then they're libel to show with Bradley&#8217;s and Wart Hogs.
 

As for the rest: Unless or until you have participated in training exercises on how to conduct warrantless searches / seizures / home invasions (for all intents and purposes) and how to send US citizens out of the country to a military interrogation outpost without anybody catching on to what&#8217;s up (at least not right away) or how to confiscate firearms from law abiding citizens after a natural disaster or during a national emergency then I&#8217;ll keep my own counsel on what is and is not illegal. 
 
FYI: Simplest practical / functional definition of what&#8217;s illegal = Anything that will show me just how deep the rabbit hole goes[FONT=Calibri][SIZE=3].[/SIZE][/FONT]

I wasnt debating anything, i was pointing out the law based on the thread talking about it being "illegal" it is not.

Legal and illegal and whats morally right or wrong are different subjects.

The fact remains in reference to the OP, it is NOT ILLEGAL to sniff on public networks.

legal and illegal refers to the LAW which changes based on where you are.

And i am fully conversant with military LAW and the things you refer to, and it has nothing to do with sniffing on a public network with cain and abel...LOL

We live in a dystopian future and without getting political as it is forbidden i dont disagree with everything you are saying, however the fact remains in the context of this thread, it is not ILLEGAL to sniff on public networks.

And you should change your posting font....LOL ;-)

Peace

---

### Post by CharlesA on 2012-05-23
If someone is sniffing packages off a public network, it is a good idea to encrypt your traffic via tunneling over SSH or VPN.

Tunneling traffic over SSH or VPN is a good idea whenever you are on a public network - you never know if there is a sniffer or what on that network.

Don't use TOR for that - TOR is for anonymity not security.

---

### Post by roelforg on 2012-05-23
> **CharlesA said:**
> If someone is sniffing packages off a public network, it is a good idea to encrypt your traffic via tunneling over SSH or VPN.
 
Tunneling traffic over SSH or VPN is a good idea whenever you are on a public network - you never know if there is a sniffer or what on that network.
 
Don't use TOR for that - TOR is for anonymity not security.
 
I know, but tor encrypts the network traffic as well (though you should only use it for anonimity) and vpn auth can be snooped as well.

---

### Post by rookcifer on 2012-05-23
> **babdah said:**
> My friend and I were study at our local coffee house and when he noticed a guy using something called "Cain and Able". I have very little knowledge about these types of programs because I am still learning but my friend told me that there is no real way to be able to protect your self from these types of attacks. From the little that i have read about this types of software, i was wondering if there was a in Ubuntu to be able to encrypt all data though the port so that even if these types of programs do intercept them they would not be able to crack the encryption? Or is there any way to protect ones self from this, other then reporting them to the network admin?

One thing you can do is use SSL/HTTPS.  But when you have a potential MITM, you have to be *really* careful that you have the site's right certificate.  One good way to do that is to use the Firefox plugin known as Convergence.  

The site you connect to must support SSL, or else he can sniff pretty much all your traffic.  But using SSL will mitigate these attacks, as will using an SSH tunnel or a VPN like tor.  Tor is safe as long as the site you're connecting to is SSL enabled and you check certs.  Again, you have to verify the cert is the right one -- it's important but easy to do with Convergence.

---

### Post by Hungry Man on 2012-05-24
I wonder how SSLStripper deals with Convergence.

---

### Post by kevdog on 2012-05-26
I'm getting the sense this thread has run its course.

---

### Post by haqking on 2012-05-26
> **kevdog said:**
> I'm getting the sense this thread has run its course.

yet you revived it ;-) LOL

Peace

---

