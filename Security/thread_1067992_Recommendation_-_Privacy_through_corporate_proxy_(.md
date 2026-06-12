---
title: "Recommendation - Privacy through corporate proxy (Squid)"
date: 2009-02-12
forum: Security
---

### Post by AccountJustForThisQ on 2009-02-12
Hi, fellow ubuntu users!

Where I work my access to the web is through a Squid server, and I am on a squidguard group which has no restrictions (as opposed to other groups in this office which are subject to white and black lists).

I've been reading about TOR but I just don't understand if it'll help me for what I need. What I'd like is for my visits to various websites to be anonymized; since I have to use the company proxy everything is logged, but maybe by using TOR only IPs that have no http service would show up?

If I use TOR would various IPs show up in the logs, or only one? Ideally my usage log would show many different IPs, IPs that don't respond to http requests.

If TOR isn't helpful in my case, is there any other setup you recommend?

[SIZE="1"]And before this thread goes off in the wrong direction, I guess you'll just have to take my word for the following: let me note that I'm not trying to circumvent company policy or "fool" the IT guys; that's just my point, there is no IT policy, written or otherwise, and the IT staff personally decides who to accuse whenever they feel like it. Like a police state, when nothing is expressly forbidden, technically any recorded action could be shown as culpable.[/SIZE]

---

### Post by cdenley on 2009-02-12
With tor, all your traffic will be encrypted on your LAN, and it will be going to a random tor node. You may cycle through different tor nodes. A LAN admin at your work may be able to see you're sending data to the tor network, but probably not with squid, and they wouldn't be able to see what you are sending or it's destination.

Anyone with access to the tor exit node would be able to read your traffic, unless you negotiate encryption with the destination server (https). They should not be able to trace it back to your work's IP, but they may be able to capture data you send which identifies you or your company.

To summarize, it would hide what specifically you are doing from your work. It would prevent sites you visit from knowing where your traffic is coming from. It would make your web browsing extremely slow. It would make sensitive but unencrypted data an easy target for hackers on the internet.

If you really want to hide your traffic from your work, the best way would be to set up an SSH server at home, then tunnel your traffic through ssh.

---

### Post by bodhi.zazen on 2009-02-12
Thread closed. This type of activity is not supported here.

You need to work with your IT department directly.

You should not be doing anything at work without the permission of your IT department.

---

