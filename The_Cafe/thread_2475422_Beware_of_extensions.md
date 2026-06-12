---
title: "Beware of extensions"
date: 2022-05-26
forum: The Cafe
---

### Post by DuckHook on 2022-05-26
[https://nakedsecurity.sophos.com/2022/05/26/whos-watching-your-webcam-the-screencastify-chrome-extension-story/](https://nakedsecurity.sophos.com/2022/05/26/whos-watching-your-webcam-the-screencastify-chrome-extension-story/)

An informative and cautionary tale of the dangers in adding browser extensions. Most articles don't go into the depth that this one does.

---

### Post by zebra2 on 2022-05-29
This issue presented itself in a thread possibly over a year ago, can't remember.  In any case I dumped all my extensions and moved to a browser that didn't require them.  I don't understand why a user base that is as security minded as we have in FOSS would put up with this nonsense.  Thanks for bringing it up again. You won't be hacked if you don't click "I agree" and if you don't click "I agree" you can't install the extension.

---

### Post by DuckHook on 2022-05-29
> **zebra2 said:**
> This issue presented itself in a thread possibly over a year ago, can't remember.  In any case I dumped all my extensions and moved to a browser that didn't require them.  I don't understand why a user base that is as security minded as we have in FOSS would put up with this nonsense.  Thanks for bringing it up again. You won't be hacked if you don't click "I agree" and if you don't click "I agree" you can't install the extension.
+1

The fewer extensions the better.

It's a truism of the complexity in modern tech that this must be viewed as a rule of thumb and not something hard set. One of the first things I do on any new Firefox install is to add the NoScript extension, so that is an immediate exception to the no extensions rule. In fact, NoScript is so integral to my browser usage that it is indispensable. I wish NoScript were baked into the browser, but since it isn't, adding the extension is a necessary exercise.

I too have shifted a lot of my browsing to another browser that comes pre&#8209;hardened. But I've found that Firefox with NoScript is arguably safer than Brave with no extensions. That's because Brave still runs scripts&#8212;just a very restricted set&#8212;whereas FF+NoScript will disable *all* scripts altogether.

---

### Post by zebra2 on 2022-05-29
@DuckHook
The no script should be integral to Firefox with a "click" to turn it off.  Then the trust would be with Firefox and not NoScript. Making Firefox secure should not be a user responsibility.  Many users may not even know that NoScript exists much less what it does. 
But I concur with your post.  I just drew a line in the sand due to the previous discussion (back there in the past) and largely due to what you had posted at that time.

---

### Post by DuckHook on 2022-05-29
> **zebra2 said:**
> This issue presented itself in a thread possibly over a year ago, can't remember.
> **zebra2 said:**
> …I just drew a line in the sand due to the previous discussion (back there in the past) and largely due to what you had posted at that time.
Were you thinking of this thread? [https://ubuntuforums.org/showthread.php?t=2458864&p=14027123#post14027123](https://ubuntuforums.org/showthread.php?t=2458864&p=14027123#post14027123)
> **zebra2 said:**
> …The no script should be integral to Firefox with a "click" to turn it off.  Then the trust would be with Firefox and not NoScript.
Could not agree more. It would be great to have NoScript built into FF.

Actually, a lot can happen in a year and FF has evolved nicely during this time. Its biggest changes are what it learned from one of its offspring, TOR Browser. FF now implements some of the security measures that TOR Browser has and is the stronger for it.
> Making Firefox secure should not be a user responsibility.
I sympathize with what you are saying, but we can't ask the impossible of Mozilla either. The reality is that most users don't have the patience for proper security. Most have also been seduced into trading terribly lax security for the blandishments of convenience, eye&#8209;candy, bells and whistles. In fact, these superficialities have been turned into "necessities" through terrible user conditioning, and browser devs have no choice but to support all sorts of scripting, tracking and identifying hooks because websites require them.

I've lost count of the sites I've visited which return a pure white page because scripting is turned off. I mean, absolutely blank. You and I know that this is entirely due to horrifically bad website design, but 99 out of 100 users out there would blame the browser.

So, if browser devs want their browser to actually be used, how else can they design it but with all those little booby traps built in and active by default?
>   Many users may not even know that NoScript exists much less what it does.
I would say: "the vast majority of users do not know that NoScript exists and wouldn't care for it even if they did know." Among my family and friends, the sheer lack of even the most rudimentary security knowledge (or concern) is staggering and depressing. Some don't give a passing thought to security until they get compromised. Even then, they don't really educate themselves or change their bad habits, turning instead to magic unicorn solutions that they think will allow them to keep doing what got them into trouble in the first place.

A good friend was recently compromised. His whole corporate network was infested by malware. As such things go, he got off lucky. No network&#8209;wide encryption. No ransom. And the attempt to defraud him was stopped by a sharp&#8209;eyed bank clerk who managed to prevent a super serious virtual heist. But how much corporate data was stolen? How many customer and supplier details are now floating out there on the dark web? No one knows, least of all him. I hope that he learns from his close call. Most don't.

BTW, TOR Browser does indeed have NoScript installed by default (though not activated). If you are super concerned about privacy and anonymity, then you may want to add TOR Browser to your privacy toolset.

A caution though: it is a sad state of affairs that it is actually easier to fingerprint your browser when NoScript prevents scripting. This is because scripting has become so ubiquitous that those of us who turn it off constitute a very small minority and are thereby easier to identify through our lack of scripting support. Our attempt to enhance our privacy has actually been turned back against us. How's that for low cunning?

Still, I am convinced that it is better have scripting off by default than on. I increase my browser fingerprint a little but decrease my attack surface a lot. I think that's a decent trade, though it grinds on me that I have to make such a trade at all.

---

### Post by zebra2 on 2022-05-29
@DuckHook , Re: [COLOR=#000000]Were you thinking of this thread? [/COLOR][https://ubuntuforums.org/showthread....3#post14027123]("https://ubuntuforums.org/showthread.php?t=2458864&p=14027123#post14027123")

Indeed it is.  I have gone to every length to have a secure personal network.  However, all of this has to be passive for my wife.  She easily admits that she would not be using Linux if it were not for myself providing her experience. Hence you are on target with what you have posted.

I'm not suggesting that Mozilla do the impossible. I'm suggesting that Mozilla do the possible which means build in the defenses and also build in the option for the end user to turn the defense on or off, hence "the click".  However at some absolute bottom point the defenses cannot be circumvented.
 
Example: Brave blocks popups but I can turn them off for a site that I trust (like my bank) but at some bottom level I am still protected from my bank. This is just a fact of life with Brave Browser, there are two sites that I use where I can't pay my bill because Brave won't allow the popup for my information for reasons seen by Brave but not by myself.  I have to use a workaround for those two sites.  

I have the choice but Brave limits the choice based on what the website is demanding.  My wife doesn't understand any of this but is pleased with what she is using because she trusts Linux, Brave Browser and myself. She doesn't do the "click" unless she runs it by me. Brave takes responsibility for providing the safety, I take responsibility for it being used. The point it that everything is built in and not depending on extensions being installed by the user. The experience isn't perfect but it is as safe as my ability to tolerate inconvenience..
I require both my wife and myself to practice safe online behavior but we need software that provides that possibility.  

Bottom line is that this extension thing should not be an issue, because at least the important ones should not be needed. My opinion.

---

### Post by DuckHook on 2022-05-30
Ah. You are blessed with a techno&#8209;dependent spouse too. We must share a virtual beer over that sometime.

While I agree with basically everything you are saying, it is depressing to be confronted with the sheer inertia and don't&#8209;give&#8209;a&#8209;hoot attitude out there. In the larger picture, there's actually no need to change FF because an alternative already exists: you and I know it to be *Brave*.

Many of my friends and family rely on me for tech advice. During these conversations, I frequently sing the praises of Brave. I may have mentioned Brave to over a dozen friends by now. How many made the switch? Not a single one. The excuses run from "I'm too used to what I have" to "I don't want to lose my history/bookmarks" to "I can't be bothered" (at least this last is honest). Now—you've made the transition—how hard was it really?

So if an easy&#8209;peasy, free, complete, secure and private alternative called Brave already exists, yet manages to gain little traction or market share notwithstanding its many virtues, then what does that say about how much people actually care?

If Mozilla were to, say, buy NoScript and bundle it with FF from now on so that it could be turned on with one simple click, I predict the following:

[LIST=1]
[*]Millions of people who have been conditioned to think of privacy/security as magic unicorns will turn it on by reflex.
[*]They will instantly be struck with blank webpages and broken sites.
[*]They will blame their browser. Mozilla will take it on the chin for putting out a lousy product.
[*]In the best case, they will turn off the NoScript option and go back to loading all scripts by default.
[*]In the worst case, they will slag FF to all their friends and on public forums like this one, then switch browsers.
[/LIST]
I think the reason for FF leaving NoScript as a user initiated extension is to actually increase the barrier to entry so that only those who are serious about security and know what they are getting into will install it. That way, FF doesn't cheese off the dilettantes or the uninformed.

Maybe I'm being overly cynical, but I don't think so. The single biggest impediment to better security/privacy/anonymity on the Internet is the vast quantity of the public who just don't care. For a browser to be acceptable to the masses, it has to cater to their whims; not to the small rump who take privacy seriously.

---

### Post by zebra2 on 2022-05-30
@DuckHook, +1
In addition, opening a link in a text or email, or simply believing what is said in a phone call is more dangerous than anything we have discussed (basically data mining). There was a blurb in the news last week that Verizon had it's employee database file hacked and ransomed for 250k.  The entry point was a communication between an employee and another party on Facebook where the employee was convinced to give up a password.  Your entire post is really all about user vulnerability (stupidity) and there are more other manifestations of that then anything related to this extension problem, real or imaginary. Much of it is smartphone related. If we were to drink a virtual beer over every single one of these anecdotal deficiencies we would be virtually inebriated. I'll take a pass on the virtual beer but many thanks for your feedback and suggestions.

---

