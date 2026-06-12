---
title: "safe browsing and bill paying firefox"
date: 2009-09-03
forum: Security
---

### Post by tankyank on 2009-09-03
I have a question ? I open firefox so I can stream sirius and surf . Then I need to pay a bill but still want to listen to my music . I ctrl-n to open another window . Now like they say when you are done with a secure site you should close your browser so I close the window I was working the bill in . Now the question ? I look at system monitor with both windows open and it shows only 1(one) occurrence of firefox . Do I have to close both firefox windows to be safe ?

Thank You ahead of time .

---

### Post by scorp123 on 2009-09-03
> **tankyank said:**
> Do I have to close both firefox windows to be safe? In theory ... Yes.

But I'd assume that your online banking requires some form of secure authentication? Like one-time passwords, or maybe a SecureID token card or something like that? So in that case even if a malicious web site somehow managed to kidnap the memory locations containing valuable info that were left behind by your browser session ... without those one-time passwords (or whatever additional mechanism you use) it's all useless.

There are various ways to work around this if you want:

- use two different browsers, e.g. Opera and Firefox. Or perhaps Google's Chromium? So you'd listen to your music in one browser (e.g. Opera), and any online banking takes place in the other browser (e.g. Firefox). That way you can close Firefox completely and yet won't get interrupted with your other activities

- You could use two different user accounts: one for your every-day activities and the other for banking ... and only for banking, nothing else.

- You could combine the two above: Two user accounts, two browsers. One account and one browser is only used for banking, the other account and the other browser is used for all the rest.

I personally do nothing of the above. Because I tend to do my online banking stuff in the evening, shortly before going to bed. So when I am finished paying the bills and what not, I'd soon afterwards power down my desktop anyway, so I am not really in a hurry to close any browser windows. The soon-to-follow poweroff will do.

But hey, it's your money, your account, and you have to feel safe. So if you're a "I'd rather be paranoid than sorry" type of guy then using two browsers and two accounts is not such a bad idea. Thanks to Linux strict memory protection (one user and his processes can't snoop around in other user's processes and memory locations) whatever you do in the one account and the one browser that are used for banking would definitely stay there, and whatever you do in the normal account and in the normal browser won't be able to grab any sensitive infos even if you were to fall for a malicious phishing web site.

Absolute safety doesn't exist, but 2 accounts + 2 browsers is not so bad and you could try that maybe?

---

### Post by bear24rw on 2009-09-03
You can do Tools > Clear Recent History to clear your cache and cookie if you want..

---

### Post by SuperSonic4 on 2009-09-03
Can you not use something like VLC to stream music?

---

### Post by tankyank on 2009-09-03
Thank You scorp123 Looks like the double browser theory is the one .

---

### Post by chandru155 on 2009-09-04
To [scorp123]("http://ubuntuforums.org/member.php?u=109288")

    Hi. So you are saying that even when some attacker is hacked my one account, I can safely pay my bill online with another user account?

[my payment portal site uses 128 bit encryption and VeriSign is used)[FONT=verdana, helvetica, arial, sans-serif][SIZE=1][COLOR=#333333]
[/COLOR][/SIZE][/FONT]

---

### Post by sasho_zl on 2009-09-05
Just remember to never ignore certificate warnings from your browser. The so called Man In The Middle attack is very good way to steal your data when you think that you have a safe connection.
About the warning - yes it's  a good idea to use different browser because that will reduce the risk of cross site scripting.

---

### Post by scorp123 on 2009-09-05
> **chandru155 said:**
>  Hi. So you are saying that even when some attacker is hacked my one account  ...  Let me repeat again: Absolute safety doesn't exist. But then again ... what are the chances of a home user really coming under a hacker attack right in the moment when you're doing your online banking? The most likely scenario where this might occur is when and if you (accidentally?) get lured onto a malicious web site that tries to exploit some (still unknown?) security holes in your web browser. And because it's very hard to predict what would happen then we have to assume the worst case: The malicious web site is able to access everything the web browser has in its memory locations ... and there is the problem: If the same web browser running under the same account was doing online banking in the moment this happens then chances are that the remote attacker might all of a sudden see far more about your finances then you'd really want them to ...

I remember one such security hole a few years back: A remote attacker was able to access large chunks of the browser's cache + whatever you recently had in your clipboard! Too bad if you were doing "copy & paste" with something important such as banking codes, account numbers, passwords or something like that. Thanks to that exploit it was possible for the remote attacker to read all that.

That security hole has been patched ages ago, sure. But what do you know? Software will never ever be perfect. Hence my recommendation: 

- Use one user account + one web browser for your every-day activities
- Use another user account + another web browser for your banking activities

Why:

A running program that you started only has access to stuff your user account has acccess to.

So in the event that a remote web site manages to hijack your browser session that you used for your normal activities then the other browser session running under the other account would still be rather safe because the strict separation between user accounts should make it impossible for the attacker to use your compromised account to read out data from the user account that you use for banking.

Of course: if ever someone finds a working "root" exploit than all bets are off. "root" powers are unlimited, and "root" can do whatever he wants, including but not limited to reading whatever location he wishes from the entire system RAM ...

But "root" exploits are extremely rare; remote "root" exploits even more rare than rare (someone correct me but IMHO it has been years since the last working remote "root" exploit was found on Linux, right?) and for a malicious web site to be able to remotely exploit "root" powers ... oh well: you'd have to be so infinitely and incredibly stupid and run a web browser as "root" and then access a malicious web site ...

But with all the user education the forum admins are doing here I doubt anyone will be so daft? Just so we mention this:  [B][COLOR="Red"]DON'T RUN STUFF AS "ROOT" !!!!  ESPECIALLY NOT DESKTOP APPLICATIONS !!!
[/COLOR][/B]


> **chandru155 said:**
> I can safely pay my bill online with another user account?  "Safely" is a bit relative. See my scenario above: In case a malicious web site caught you with your pants down and your banking session still running but --thank the Gods-- under another user account: then yes. Chances are they were not able to exploit the banking session, only your normal session. But I definitely would recommend you instantly disconnect your system from the network, do a major clean-up (e.g. remove the account that got compromised?) and not re-use the banking account again until you're sure your system is clean when you reconnect it again to the network.

> **chandru155 said:**
>  my payment portal site uses 128 bit encryption and VeriSign is used See above: my story about the remote clipboard exploit that was around a few years back. If ever something like this happens again then all the 128-bit encryption won't help: if by chance you happened to have passwords and login information in your clipboard buffer or if by chance such info was somewhere in the RAM locations the remote attacker managed to snatch from your system (e.g. by hijacking the browser), then you can bet that the hackers on the other end of the network will recognise the jackpot soon enough. They will kill your network connection by triggering a "denial of service" against you and then login into your bank posing as you ...

That's why a good banking solution should have a second mechanism of authentication that is independent of the computer, e.g. one-time pads, one-time passwords, or TokenID or SecureID cards that use a "Challenge + PIN + Response" system.

---

### Post by phillw on 2009-09-05
Hi,

Yeah, i've been watching this thread - I think the idea of two seperate browsers is a real good idea, having them both under AppArmour is a real good idea, finding a bank that uses the likes of Verisigns security token
is also a really good idea.

As noted, nothing is 100% - but you can sure reduce the risks. 

To get at my e-bay or pay-pal accounts I need my little dongle. 6 digit code, changes every 30 seconds.

My bank ? I need my bank card, that is chip & PIN, insert it into the reader, enter my own PIN and then get an 8 digit code to enter into their on-line site.

100% secure ? Probably not, but it sure does reduce the odds.

Phill.

---

