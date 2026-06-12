---
title: "A dream of improvement.  Can anyone implement it ?"
date: 2020-06-27
forum: Ubuntu, Linux and OS Chat
---

### Post by Innernet on 2020-06-27
Seen too frequently...

"A web site is slowing down your browser.  What do you want to do ?"
O  Stop it
O  Wait

What would it take to have these options implemented and working :

O  Tell me which is the web site and how to block it forever from being accessed
O  Block it forever from being accessed, whatever it is.
 
---------------------------------------------------------------------------------------------------------

Sometimes it shows :
"A script is slowing down your browser.  What do you want to do ?"

O  Stop it
O  Wait

What would it take to have these options implemented and working ?

O  Do not ask; delete it and resume what got halted
O  Show the offending script and instruct me how to prevent from happening in the future.

Just keep in mind there is a brutal unresponsiveness delay of keyboard, mouse when the above messages show up.

---

### Post by CelticWarrior on 2020-06-27
I think you proposed changes make no sense.

There are many situations that can trigger those alerts.

In the first situation why would you want to "block it forever", the "it" being a website that YOU opened?
Likewise, in the second situation, it also refers a website that YOU opened and has a script running (javascript, probably) that is slowing down the browser. Nothing was halted so nothing to "resume". There are extensions and settings in any web browser to prevent scripts from running but you should be aware that most of the websites running scripts WON'T WORK without them.

The root cause seems to be not enough RAM, rather than an issue with the websites themselves.

---

### Post by Innernet on 2020-06-27
Thank you.
If the web site I opened halts my browser, I do not want to be there again.
If the web site I opened pumps scripts I did not ask for, I do not want to go back to it again.

If not enough ram, and at limit of the upgrade, why should I succumb to a website dictating that I must buy another computer with the features and ram (or ram upgradeability) they want to please their pusher mode ?

I want control of my computer, not from pusher websites. 
What a wonderful thing the internet was in 1995 !

---

### Post by Frogs Hair on 2020-06-27
Not a Ubuntu specific problem, moved to UL&OS Chat.

---

### Post by exploder on 2020-06-27
Why not just install the UBlock Origin extension in your browser?

---

### Post by CelticWarrior on 2020-06-27
> If the web site I opened halts my browser, I do not want to be there again.
Again, it isn't halting but even if it was there's a very good solution for that "problem": Do not visit those websites.

> If the web site I opened pumps scripts I did not ask for, I do not want to go back to it again.
So don't. 

> If not enough ram, and at limit of the upgrade, why should I succumb to a  website dictating that I must buy another computer with the features  and ram (or ram upgradeability) they want to please their pusher mode ?
You don't have to if you don't want to. But why should the rest of the world be limited just because you don't want to evolve with the times/requirements? Should we also create a special highway lane with a 5mph speed limit to accommodate your 1925 Ford model T?

> I want control of my computer, not from pusher websites.
You are in control of your computer.
You AREN'T in control of mine.
You AREN'T in control of websites you don't own, let alone their requirements. Your only option is to NOT used them.

> What a wonderful thing the internet was in 1995 !
No, it was HORRIBLE. The requirements were too much for my 1984 8-bit computer. This should be outrageous in your logic.

Yes, obsolesce always wins in one way or another.

---

### Post by TheFu on 2020-06-27
I don't think this can be implemented in a secure way, especially without any details, like the browser, addons, and plugins in that browser. Unix system settings would need to be altered by a user running without any elevated permissions.  Running something like a browser with elevated permissions is asking, begging, to be hacked.

There are techniques that I use which prevent things like that happening very often, but they cannot be prevented completely because the internet is constantly changing so the included page source for any website can change from second to second.

A few ideas:
[LIST]
[*]Implement lots of blocking for internet downloads included in webpages that aren't helpful to you. This can be done using many different ways. Which would be the quickest depends completely on your use, your network, how many computers and other devices to be protected and how mobile those devices are.
[*]Don't allow tracking or advertising networks any access to the browser. Blocking system-wide can be implemented too.
[*]Don't let javascript run by default.  Setup a whitelist for sites where Javascript is ok.
[*]Don't allow random media to run by default.  Whitelist.
[/LIST]

How to do these things? There are multiple ways.
[LIST=1]
[*]/etc/hosts for blocking access   [https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279](https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279)
[*]DNS filters like pi-hole provides [https://discourse.destinationlinux.network/t/pi-hole-in-canonical-lxd-container/1337](https://discourse.destinationlinux.network/t/pi-hole-in-canonical-lxd-container/1337)
[*]**NoScript** browser addon to selectively block Javascript 
[*]Use a reputable ad-blocking addon; I use *ublock-origin*
[*]Use a reputable tracker blocking addon; U use *Ghostery*
[*]Limit the use of addons that would counteract the addons above; Don't use shopping helpers, downloaders or coupon finder addons, as examples.
[/LIST]

Sometimes I run high-risk programs like browsers inside a sandbox environment like **firejail** provides. Sometimes sites we don't really use often will only work by allowing all the trackers and javascript enabled, but we don't want any trackers remaining when we are done getting a hotel or airline ticket.  **firejail --private** can help.  The --private option makes it seem like the first time the browser has ever been run and doesn't allow anything about that session to be saved. No downloads. No configurations. No cookies. No html5 or flash "local objects". No super-cookies. Basically, it is an incognito mode that actually works, unlike the incognito modes built into browsers which almost always have bugs and leaks.

If you want more ideas, consider using a paid VPN to change where all your traffic appears to originate. Don't use a VPN without using firejail --private if you are trying to be untraceable.  Any old cookies or reusing logins to sites that you may have used without firejail and the VPN will leak traceable information.  Security is hard. Privacy is harder.

---

### Post by kansasnoob on 2020-06-27
I see those a lot if I'm shopping on Amazon using Firefox. Best solution for me was to stop using Firefox. I did try various extensions and even editing config files but to no avail. I've gotten quite lazy in the past couple of years so I won't waste more than an hour or two trying to solve a problem if an alternative "just works out-of-box".

---

### Post by SeijiSensei on 2020-06-27
You might like Brave.  Follow the series of commands described here:

[https://www.ubuntuupdates.org/ppa/brave](https://www.ubuntuupdates.org/ppa/brave)

---

### Post by kansasnoob on 2020-06-29
> **SeijiSensei said:**
> You might like Brave.  Follow the series of commands described here:

[https://www.ubuntuupdates.org/ppa/brave](https://www.ubuntuupdates.org/ppa/brave)

I really did like Brave other than limitations on "speed dial" as compared to Opera, but I encountered problems displaying images properly when shopping on Ebay.

I tend to bounce from browser to browser every few months (sometimes much sooner) because of frustrations ranging from minor to downright maddening. I miss the days when Firefox "just worked" - gosh, that was a long time ago it seems. I used Firefox exclusively for probably 15 years - maybe longer? I started using it in Win ME and only gave up on it maybe two years ago. Now I just use Chrome or Chromium almost exclusively, but just encountered a video streaming issue since the last update.

---

### Post by TheFu on 2020-06-29
I use different browsers, for different purposes, under different situations, with different environments.

[LIST]
[*]Daily use, safe websites only = firefox in a firejail sandbox.
[*]Weekly use, banking accounts only = chromium-browser in a firejail sandbox.
[*]Dangerous use, where tracking is required to functionality = chromium-browser in a **private firejail** sandbox.
[*]Dangerous uses, when I want only a very simple browser without much support over images and html4 = dillo in a  **private firejail** sandbox.
[/LIST]
I don't trust most websites. Have a pi-hole running to block DNS lookups to advertising and tracking networks. Have some firewall rules to block outbound access to tracking subnets and specific companies based on past experiences.

All of us are different and have a different willingness to be hassled over tracking, advertising, and slow performance. Blocking ads and tracking javascript and DNS access really speeds up the internet. It also lowers the RAM abuse by websites.

---

### Post by Innernet on 2020-06-30
> **kansasnoob said:**
> ... I miss the days when Firefox "just worked" - gosh, that was a long time ago it seems...
Thanks. I feel the same.  Tried several browsers, not enough success. :(

TheFu...  yes, the RAM abuse and desperation to gain control of our screen and beyond from now too many pusher intruding websites.   Wish there was a solution.  They want our cookies and more, we cannot tell them we do not want our equipment impaired. [-X

---

### Post by zebra2 on 2020-07-01
Lots of good suggestions in this thread.  I use Opera which uses the Chrome engine.  In reality most people will accept a certain amount of exposure for ease of use. For the most part the exposure allows the developers to collect a paycheck. I don't see anything wrong with that. However there are times that I want to limit exposure for the sake of security. This is especially important where my own paycheck is involved.  As noted elsewhere in this thread Firejail does a pretty versatile job with protecting personal information and data. When I travel I take my USCellular hotspot with me so with the hotspot having no inbound ports I am able to avoid public wifi. I keep it on the back seat headrest in my car and plugged into the usb power port. Never have been without secure internet when I travel. Regarding Firejail the 'firecfg' cmd will setup most apps on your system. Beyond that it is very tweakable. So regarding the OP concerns, there are solutions. It's just that the millions of us have different needs and concerns. Bottom line is use the appropriate suggestions. Do something!

---

### Post by TheFu on 2020-07-01
How well does USCellular work in Chile, France, Thailand?

Most people just use a VPN when traveling that connects to their office, their home or some paid 3rd party service provider outside the current country they are in.  

Opera had (has?) built-in VPN [https://www.tomsguide.com/us/opera-vpn,review-4496.html](https://www.tomsguide.com/us/opera-vpn,review-4496.html) , but due to the current company ownership, it might not be the best choice. 

The same concerns apply to Mozilla's VPN offer. [https://vpn.mozilla.org/](https://vpn.mozilla.org/)

All-in-one solutions break the federated way that internet networking is supposed to work. That loose federation means no single entity gains too much knowledge or power (cough ... google, facebook, amazon, apple, microsoft, huge ISPs, some govts, excluded). Companies with too much power are bad for end-users.

IMHO.

---

### Post by sdsurfer on 2020-07-02
What you are seeing is the browser's way of coping with rendering a web page that was designed top down instead of least common denominator first, then graceful degradation for additional features if support is lacking. This concept is lost on publishers today. 

> If not enough ram, and at limit of the upgrade, why should I succumb to a  website dictating that I must buy another computer with the features  and ram (or ram upgradeability) they want to please their pusher mode ?

I know, right? See previous. From Tim Berners Lee,

> The power of the Web is in its universality. Access by everyone regardless of disability is an essential aspect.

Even if that disability is a 8 GB RAM 250 MB PC II from 1995 with a 9600 baud modem, users should be able to access your content without their browser crashing. Not happening a lot these days.

Anyway if you wish to suggest, suggest to the publishers of the browser you are using, because that is where your idea would have to be implemented.

---

### Post by zebra2 on 2020-07-02
It is all about "pay per click". There has to be a paycheck at the end of the rainbow.  If all else fails follow the money trail. That being said, a lot of the solutions available to the OP are built into the linux kernel.  Those built-in solutions can be either too techie or too bothersome to use so frontends like firejail are provided to smooth out the process. If I access a website that won't remove a popup window unless I allow cookies then I don't use the website. If they want my mouse clicks it will have to be on my terms. However if I want what their site is providing enough I may choose to put up with their data mining. In that case I can set my browser to delete cookies every 24hrs or similar option. The source of many of the problems lie in the fact the many want a ready to use computer experience. The linux crowd are pretty tech smart but linux trying to go main stream is diluting that. Hence the preloaded annoyances. They are an unchallenged part of the experience.

---

