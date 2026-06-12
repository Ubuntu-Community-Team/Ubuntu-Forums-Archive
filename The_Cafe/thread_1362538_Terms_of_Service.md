---
title: "Terms of Service"
date: 2009-12-23
forum: The Cafe
---

### Post by ged25 on 2009-12-23
Here are the Terms of Service of Google and Yahoo.

Google:

> 
**5.	Use of the Services by you**

5.3	You **agree not to access (or attempt to access)** any of the Services by any means other than **through the interface that is provided by Google**, unless you have been specifically allowed to do so in a separate agreement with Google. You specifically **agree not to access (or attempt to access)** any of the Services through any **automated means (including use of scripts or web crawlers)** and shall ensure that you comply with the instructions set out in any robots.txt file present on the Services.


Yahoo:

> 
**18. YAHOO!'S PROPRIETARY RIGHTS**

In Paragraph 2, line 10: 

You **agree not to access** the Yahoo! Services by any means other than **through the interface that is provided by Yahoo!** for use in accessing the Yahoo! Services.


How is it that you have email clients able to access mails and contact info etc from them ? Doesn't it violate the TOS ?
Don't multi-protocol IM apps like Trillian, Pidgin, Meebo etc also violate it ?

---

### Post by p_quarles on 2009-12-23
I don't know about Yahoo, but Google gives explicit instructions for how to use both mail and chat with a wide variety of third-party clients, which seems like permission to do so. In any event, they specifically don't want scrapers/crawlers, so that would seem to be the intent of that rule, rather than preventing you from using Gmail with Evolution.

---

### Post by speedwell68 on 2009-12-23
I know for a fact that Yahoo provide instructions to configure a mail client for use with their email service, so I guess it doesn't.  I have no idea and couldn't care less about IM clients.

---

### Post by RiceMonster on 2009-12-23
Since google does allow using email clients, I'm going to guess that POP3 and imap are included in interfaces provided to you.

---

### Post by jwbrase on 2009-12-23
I think basically what they're saying is "Don't use our services by hacking our servers, and don't use search bots that generate really high traffic". 

Somebody might be able to get priority over other searches by hacking into the servers and accessing the search databases directly, rather than sending a more typical search request to the search engine. This could cause quite a slowdown for other users. And if you had multiple entities hacked into the servers and not being able to search as fast as they wished, you might see them trying to kick each other off the servers. I'm pretty sure Google and Yahoo don't want their servers becoming battlegrounds for competing entities that want really fast searches and don't want to wait their turns. They also don't want their databases edited, which could happen if somebody hacked the servers and used the engine via their own software interface. It's the interface between their software and your software that they're worried about, not the user interface that your software uses.

Also, when they're talking of "automated means", I think they're talking about how you're generating searches. If humans are sitting there saying "search for this" every ten seconds or a minute, that's not a problem. If you've got a bunch of bots, each one running a shell script and sending in multiple search requests per second, there's a danger of the search engine being DDOSed even if that wasn't the intention of any of the bots or their operators.

---

### Post by JimInLakeland on 2009-12-23
It's just legaleeze. So long as how you access isn't harmful to the service, it won't bother them.

---

### Post by jwbrase on 2009-12-23
> **JimInLakeland said:**
> It's just legaleeze. So long as how you access isn't harmful to the service, it won't bother them.

Pretty much. It's just that people often don't recognize the potential harm to others in their actions.

I've managed to trigger captcha's from Google in the past with similar queries to Google calculator made in close succession. Apparently my behavior and speed was close enough to a bot running a script to raise alarms.

Also, when Michael Jackson died, the software on Google's servers mistook the incoming flood of queries for "Michael Jackson" for a DDOS attack.

---

### Post by User3k on 2009-12-23
I honestly think all ToS's are just bad jokes. They don't need to be but all companies use them so freely and without restriction or even conformity of some sort that they turn them into jokes.

My favorites are the places that actually break their own ToS. I could get into those but that is another thread for another time.

---

### Post by Frak on 2009-12-23
> **User3k said:**
> My favorites are the places that actually break their own ToS.

It's impossible to break your own ToS.

As for the chat clients, you can just go through the interfaces that the normal clients use. For instance with YMSG, while the login is a bit complicated, the normal chat is nothing other than shipping binary streams (last I recall) over 5050 or HTTP(80) if 5050 is blocked. The Yahoo! server sends a ping keepalive to the clients every 30 seconds to ensure they are still connected.

Since this *is* Yahoo's interface, it's fine.

---

### Post by jayze on 2009-12-23
> **speedwell68 said:**
> I know for a fact that Yahoo provide instructions to configure a mail client for use with their email service, so I guess it doesn't.  I have no idea and couldn't care less about IM clients......Please can someone give me more info as I have tried to marry Yahoo Mail with Evolution but I came away with the understanding that its only possible if you pay for a super duper version of Yahoo Mail. ? thanx:popcorn:

---

### Post by Frak on 2009-12-23
> **jayze said:**
> .....Please can someone give me more info as I have tried to marry Yahoo Mail with Evolution but I came away with the understanding that its only possible if you pay for a super duper version of Yahoo Mail. ? thanx:popcorn:
I go through AT&T, which gives me a premium Yahoo! Mail account. That's the only way I have POP3 through Yahoo Mail.

---

### Post by jayze on 2009-12-23
Jayze is a dunce! lol....have IM'd Frak for help!:(

---

### Post by ged25 on 2009-12-24
So basically, the interface they are talking about is their Application Programming Interface and not the user interface ?

---

### Post by earthpigg on 2009-12-24
> Don't multi-protocol IM apps like Trillian, Pidgin, Meebo etc also violate it ?

unlike Yahoo! chat, there is no such thing as gchat or gmail chat *as a standard* owned by google.

the standard is [jabber]("http://en.wikipedia.org/wiki/Jabber") -- gmail chat is merely one of many front ends for the jabber protocol.

much like there is no Adobe standard for the .pdf format. Adobe reader is just another .pdf reader. there is nothing special or magical about Adobe reader. people still seem to think Adobe 'owns' pdf for a variety of [historical reasons]("http://en.wikipedia.org/wiki/.pdf#History").

> So basically, the interface they are talking about is their Application Programming Interface and not the user interface ?

the interface they are talking about is ***any interface that lawyers can make serve the interests of google at any particular moment***.

presently, google's actions indicate that it is decided that it is in there best interests at present to ***not*** consider using 3rd party software to access gmail to be detrimental to the interests of google. this can change at any moment.

the case could be made in the future that "oh, this e-mail software that allows people to access their gmail without looking at our advertisements has ***always*** been in violation of the ToS... we just decided to let it slide for a while."

---

### Post by ged25 on 2009-12-25
Ok, so if a company decides that someone is violating its TOS, I'd assume that they would first ask the offending party to remove the product, failing which they would start legal proceedings.

Trillian had problems with Yahoo in the past and the only thing that Yahoo tried to do to block them was make changes to their protocol. Any reason why they didn't act on it aggressively ?

What I want to know is what happens if I'm selling an email software and then suddenly a company decides that all those softwares are violating their TOS ?

---

### Post by earthpigg on 2009-12-25
> Ok, so if a company decides that someone is violating its TOS, I'd assume that they would first ask the offending party to remove the product, failing which they would start legal proceedings.

that is usually how it works, if the 'someone' is a company with money. with things like pidgin, however, who can you file a suit against for money?

and even with things like Mozilla's e-mail client - ***Mozilla*** isn't the one violating Google's TOS... the ***user*** is.
> 
Trillian had problems with Yahoo in the past and the only thing that Yahoo tried to do to block them was make changes to their protocol. Any reason why they didn't act on it aggressively ?

they probably decided it wasn't worth the time and/or effort.

> What I want to know is what happens if I'm selling an email software and then suddenly a company decides that all those softwares are violating their TOS ?

you would need to hire an army of lawyers to sign agreements with a bunch of different people. that's one of the reasons why its so difficult to get into the proprietary software business - if you make a great product but skip the Army of lawyers, its only a matter of time until someone comes after you. See: TomTom GPS.

or you could simply make a bunch of money, enjoy it while it lasts, and then release it as Open Source right before your company declares bankruptcy. That's how we got Firefox from Netscape - if you can't compete on the enemies playing field (with Armies of lawyers and predatory business practices, etc).... then pick a new battlefield and make them fight there.

Microsoft would have crushed Netscape if they continued to play Microsoft's game. In fact, they did. A few months back, Netscape (owned by AOL) released their last version ever... though that conventional proprietary piece of software has died, no one can crush the Firefox guerrillas.

A decade after Microsoft "won" the browser wars, the risen Phoenix of Firefox is still bleeding them. Millions and Millions of dollars poured into IE, and still no direct profit. Mozilla, on the other hand, is quite profitable.

---

### Post by Frak on 2009-12-25
> **earthpigg said:**
> Millions and Millions of dollars poured into IE, and still no direct profit.

They make a crapload on advertising on MSN.

---

### Post by Exodist on 2009-12-25
> **ged25 said:**
> Here are the Terms of Service of Google and Yahoo.

Google:



Yahoo:



How is it that you have email clients able to access mails and contact info etc from them ? Doesn't it violate the TOS ?
Don't multi-protocol IM apps like Trillian, Pidgin, Meebo etc also violate it ?

Well mail wise on Yahoo you have to pay for the option to access your email via an external client. Which then you fall under a different term of service.

Not sure about the multi-protocol clients. Somewhere down the road I think there is a loop hole.

---

### Post by ged25 on 2009-12-27
Can you please tell me where I can information on the legalities involved when doing software or web related services ?

[QUOTE=earthpigg]or you could simply make a bunch of money, enjoy it while it lasts, and then release it as Open Source right before your company declares bankruptcy. That's how we got Firefox from Netscape - if you can't compete on the enemies playing field (with Armies of lawyers and predatory business practices, etc).... then pick a new battlefield and make them fight there.[/QUOTE]

This sounds like shifting ownership to somebody else when someone comes after you. You could send them on a wild goose chase like this. I dunno; it just sounds a bit dodgy to me but I guess I shouldn't comment without knowing stuff.

I'd like to thank you for your very informative posts; many things have been made clear to me. I appreciate it.

---

### Post by Primefalcon on 2009-12-27
Talking about Firefox, and Netscape the ironic part is Microsoft won the browser wars by using proprietary stuff like active X....... With the w3c and Firefox that's been lack of standards and activeX have been main weak points, now Firefox is getting up to a level playing field..... Talk about turning your opponents strengths into a weakness

---

### Post by earthpigg on 2009-12-27
> 
I'd like to thank you for your very informative posts; many things have been made clear to me. I appreciate it.

please keep in mind that i am no lawyer. this is basically what i have concluded by combining my cynical outlook with wikipedia and watching the news.

---

