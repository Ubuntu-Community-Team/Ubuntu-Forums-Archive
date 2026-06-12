---
title: "Browser extensions can be harmful ... Be careful"
date: 2021-03-05
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2021-03-05
Read this >>>[https://krebsonsecurity.com/2021/03/is-your-browser-extension-a-botnet-backdoor/](https://krebsonsecurity.com/2021/03/is-your-browser-extension-a-botnet-backdoor/)
The only problem is the author of that article didn't mention which addons can be trusted & which cant be.

---

### Post by Paddy Landau on 2021-03-05
Thanks for the warning.

There's a lot of this going on. The best thing to do is stick with extensions from the official browser store (depending on which browser you use); always check reviews and star ratings; and when you install, check the permissions that it asks for before approving.

I hate these scammers and black-hat hackers. I wish that we had effective ways to combat them.

---

### Post by linuxyogi on 2021-03-05
@Paddy Landau
I use 2 browsers namely Firefox & Brave. I haven't added any addons under Brave coz I heard that its privacy respecting by default.
I am using the following addons under Firefox. (Please see attachment).

In case of Firefox even if a user sticks to the official browser store he will find 2 kinds of addons. Some are "recommended" while others say "not actively monitored". (Please see attachment)


[ATTACH=CONFIG]288065[/ATTACH]


[ATTACH=CONFIG]288066[/ATTACH]

---

### Post by Paddy Landau on 2021-03-05
> **linuxyogi said:**
> In case of Firefox even if a user sticks to the official browser store he will find 2 kinds of addons. Some are "recommended" while others say "not actively monitored".
That's interesting. Chrome's store doesn't have that distinction. It would be nice if it did!

---

### Post by Frogs Hair on 2021-03-05
> **Paddy Landau said:**
> That's interesting. Chrome's store doesn't have that distinction. It would be nice if it did!

If Chrome extensions offer no website or privacy information beware. All my firefox addons are recommended by or are developed by mozilla. I use the same extensions on Chromium based browsers with the exception of the mozilla extensions which aren't available for Chrome .

---

### Post by Paddy Landau on 2021-03-06
> **Frogs Hair said:**
> If Chrome extensions offer no website or privacy information beware.
Oh, they do indicate such information. But they're not monitored to the same extent as you show that Firefox does.

---

### Post by zebra2 on 2021-03-06
Just one more way that intrusions have found a backdoor to compromise a system.  Proof or not I've deleted them all. This sounds way too real to suit me. It is resonate of other posts on this site indicating similar activity through other processes.

---

### Post by Swan_DB on 2021-03-09
[Noob Question] - What prevents my browser/browser extension from writing to my hard-drive, or gaining access to my wifi network?  Specifically, hypothetically, ELI5, how would a malicious browser extension on my desktop that I am at right now, access my....   idk, my "smart doorbell security camera"?

My brain is saying they'd need the get into my OS from my browser, which seems like if I simply clicked a button on a website (or installed a malicious browser extension), it could happen via: That "button"/extension downloads a program that executes writing code that breaks my wifi network passwords or by-passes the passwords if that's possible?, then finds my "smart doorbell security camera" and starts sending that video data back through the wifi network, then back through my OS/desktop, then back to...  the web and the malicious browser extension's author can download my "smart doorbell security camera" video data.

Any input/details on this would be great, thanks in advance.

---

### Post by Paddy Landau on 2021-03-09
> **Swan_DB said:**
> [SIZE=4]… [FONT=arial][SIZE=2]Specifically, hypothetically, ELI5…[/SIZE][/FONT][/SIZE]
I think that the best place to ask this is in the [Security forum]("https://ubuntuforums.org/forumdisplay.php?f=338"). I suggest that you create a new thread there, asking exactly what you've just asked. Be aware that not everyone will know what the abbreviation ELI5 means.

---

### Post by ajgreeny on 2021-03-09
As this is not a support thread asking for an answer the current Ubuntu, Linux and OS Chat is the right place.

Please do not create a duplicate thread, though if you wish to ask a specific question feel free to start again.

---

### Post by DuckHook on 2021-03-09
> **Paddy Landau said:**
> That's interesting. Chrome's store doesn't have that distinction. It would be nice if it did!
I swore off Chrome a long time ago after just permitting myself to dabble with it. We are not supposed do slag any company on these forums, so let me put it this way: a "privacy" browser foisted on us by a trillion dollar company that makes its billions through user profiling and highly refined targeting is—how to put this delicately—a contradiction in terms? An oxymoron? Pushing on a rope? Simultaneously blowing and sucking?

Brave is awesome. FF is awesome. TOR-Browser is awesome. Chrome is…

---

### Post by DuckHook on 2021-03-09
> **Swan_DB said:**
> [Noob Question] - What prevents my browser/browser extension from writing to my hard-drive, or gaining access to my wifi network?  Specifically, hypothetically, ELI5, how would a malicious browser extension on my desktop that I am at right now, access my....   idk, my "smart doorbell security camera"?

My brain is saying they'd need the get into my OS from my browser, which seems like if I simply clicked a button on a website (or installed a malicious browser extension), it could happen via: That "button"/extension downloads a program that executes writing code that breaks my wifi network passwords or by-passes the passwords if that's possible?, then finds my "smart doorbell security camera" and starts sending that video data back through the wifi network, then back through my OS/desktop, then back to...  the web and the malicious browser extension's author can download my "smart doorbell security camera" video data.

Any input/details on this would be great, thanks in advance.
The single weakest point in a typical consumer install is their browser. In fact, it dwarfs all other risks combined. If I had to guesstimate a proportion, I would say that it alone makes up more than 75% of your total attack surface.

It holds this distinction mainly because, for most people, it is their primary interface with the big bad Internet (this is also why the mail client comes in second).

Consider: it has built&#8209;scripting. Scripting is a programming language. People split hairs about whether Javascript counts as a "programming" language, but I mean, c'mon—really? This is a debate?

So, you've got this programming language, built into a ridiculously massive app (FF weighs in at &#8776;20M lines of code), wide open to any of a million scumbags, that most users permit to access their cameras and microphones, play sound, display graphics, write to their filesystem, browse their network, run obscure and arcane mini&#8209;apps, do triple backward somersaults with three and a half twists, and must be installed into their system with sudo. … … …

What could go wrong?

You've got the question backwards. Your IP packets arrive in your browser by traversing through your firewall, navigating your LAN, arriving at your computer and finally being unpacked in your browser. They have already traversed the whole length and breadth of your network and your browser has to have access to that network to send and receive those packets. The question is not "how it can see my smart doorbell", but "what tiny, thin, delicate measures are in place to *stop* it from seeing my smart doorbell?" The default condition in a network is: everything is wide open. We fallible humans then erect flimsy walls that we hope will carve out no&#8209;go zones within that anything&#8209;goes default.

There are plenty of us who refuse to run any browsers outside of a full on jail. AppArmor is a good start and most Linux browsers already come with AppArmor profiles, but these tend to be too loose. And AppArmor is notoriously hard to work with. Even better is some form of sandbox. Some of us use specialty sandboxes like firejail. I contain mine within LXD instances. Perhaps the most hardened is a VM.

Even then, my FF is fenced in with NoScript, Ghostery, DoH and a cookie monster. I also run a number of browsers including one so primitive that it has no scripting, CSS or doohickeys with which to exploit. I use that one to visit sites that I'm not sure of. And I'm not sure of most sites.

All of these measures have drawbacks. They take away that convenience that everyone is so addicted to. And if you poke holes in your sandbox in order to bring back some of that convenience, then you've basically nullified the whole point of sandboxing in the first place.

There are no easy or simple answers when it comes to browsing.

---

### Post by zebra2 on 2021-03-19
I decided to install Brave and give it a try.  For some reason it seems to be the most reasonable choice for my Linux mindset. I tried it once before but didn't take time to learn how to use it. It has rapidly become my go to Browser. I think it is the right solution for the OP expressed in this thread considering that I have deleted all of my extensions.

---

### Post by DuckHook on 2021-03-20
> **zebra2 said:**
> I decided to install Brave and give it a try.  For some reason it seems to be the most reasonable choice for my Linux mindset. I tried it once before but didn't take time to learn how to use it. It has rapidly become my go to Browser. I think it is the right solution for the OP expressed in this thread considering that I have deleted all of my extensions.
Like people's infatuations with DEs, I don't get why people get infatuated with browsers either. I know I'm in a small minority, but I find that, from a usability perspective, most any browser is tolerable, even, in its day, MS IE(!)

What differentiates them is their security/privacy/anonymity. There's a huge world of difference between them when one takes the time to peek under the hood. I suppose that wrappings have never been of much interest to me; the guts on the other hand…

---

### Post by zebra2 on 2021-03-21
Yep, Like I said "more reasonable choice for my Linux Mindset". It really doesn't have much to do with the real nice desktop that Brave has. It is the fact that it has limited exposure without the extensions because the limits are programmed into the Browser, while at the same time it has a Brave designed DRM that gives digital media support.  While in the other browsers I have tried the extensions that are supposed to protect the user also block the digital media (and more). There are other reasons I discontinued the other Browsers that are based on the OP of this thread that I won't get into here because I don't know enough about the nature of the security risks in question. 
Most linux users are willing to do without visual trappings in exchange for security and that is where my where my infatuation lies with Brave browser. It actually works.  
So far as Browser Desktop goes, Microsoft Edge probably wins that contest but I don't trust its security even a bit.

---

### Post by DuckHook on 2021-03-21
> **zebra2 said:**
> &#8230;Most linux users are willing to do without visual trappings in exchange for security and that is where my where my infatuation lies with Brave browser. It actually works.  
So far as Browser Desktop goes, Microsoft Edge probably wins that contest but I don't trust its security even a bit.
I wasn't charging *you* with infatuation; quite the contrary. I was trying to agree with you. The fact that you were willing to make the change said to me that you were not infatuated with *any* browser.

I was addressing the larger community, many of whom are so focused on one browser that they are unwilling to try others. My experience with Brave is exactly like yours: it is marvellously secure right out of the box and the fact that it scrambles browser fingerprinting is a HUGE advantage.

---

### Post by zebra2 on 2021-03-21
> **DuckHook said:**
>  the fact that it scrambles browser fingerprinting is a HUGE advantage.

Thanks for the clarification on the infatuation point.  I'm like anyone else on this space ship. I can get lazy and this thread addresses an important issue. I don't know if you are familiar with this website "https:// [c]("https://coveryourtracks.eff.org/")over your tracks .org" but it gives some pretty good info on fingerprinting and other metrics. I'm getting some good marks off of the Brave browser.

---

### Post by DuckHook on 2021-03-21
> **zebra2 said:**
> …this website "https:// [c]("https://coveryourtracks.eff.org/")over your tracks .org"…
Yes, it's a great site and a useful tool. It's very instructive to put a series of different browsers through that test. Try, as part of this discussion, Chrome. A very eye&#8209;opening though sobering experience. I find that almost everything EFF gets involved in is worthy of serious consideration.

---

### Post by zebra2 on 2021-03-21
> **DuckHook said:**
> Yes, it's a great site and a useful tool. It's very instructive to put a series of different browsers through that test. Try, as part of this discussion, Chrome. A very eye&#8209;opening though sobering experience. I find that almost everything EFF gets involved in is worthy of serious consideration.

Thanks, this thread is getting to be an eye opening experience.

---

### Post by linuxyogi on 2021-03-22
> **zebra2 said:**
> I decided to install Brave and give it a try.  For some reason it seems to be the most reasonable choice for my Linux mindset. I tried it once before but didn't take time to learn how to use it. It has rapidly become my go to Browser. I think it is the right solution for the OP expressed in this thread considering that I have deleted all of my extensions.

I am no longer using Brave. I used it for like 2 months. The only reason I used Brave is to browse Youtube while logged in so that I get notifications for new videos that I have subscribed for. The problem was if I then searched anything on Google it was a serious privacy issue coz as I mentioned I was logged in with my Google account.

Now things have changed. I am no longer using Google for searching. I am using startpage & even if I decide to use Google for a specific search I use the "private window" feature of Firefox which is my main browser.

I am extremely conservative about which extensions I install.

[ATTACH=CONFIG]288168[/ATTACH]
(Click to enlarge)

---

### Post by DuckHook on 2021-03-22
> **linuxyogi said:**
> …The problem was if I then searched anything on Google it was a serious privacy issue coz as I mentioned I was logged in with my Google account…
Here is a useful strategy for browser privacy:

[LIST=1]
[*]Sandbox all browsers using either jailing apps like firejail, or general purpose jails like VMs, Docker, LXD.
[*]One container advantage is they are easy to clone, then modify, for multiple instances of the same browser.
[*]Use only one of these jailed browsers for Google stuff like YouTube, accepting the fact that privacy does not exist with this browser.
[*]Similarly, devote another unique browser to highly sensitive stuff like banking. Don't use it for anything else.
[*]You can set up one container with VPN and a kill switch so that all of its transactions are automatically private.
[/LIST]
By confining non-private browsing to one sandboxed jail, the rest of your browsing is less compromised. This strategy has the added advantage of keeping your base install squeaky clean.

---

