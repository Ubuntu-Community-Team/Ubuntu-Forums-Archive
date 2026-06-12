---
title: "parential controls in ubuntu"
date: 2010-05-18
forum: Security
---

### Post by Ceiber Boy on 2010-05-18
HI

I'm trying to implement parental control on my ubuntu box, i'm running firefox and have considered firefox add-ons but they want a fee for their implementation and feel that this is against the spirit of ubuntu. my router allows me to block specific sights but i'm looking to implement a forbidden word list, is their ant software i can use on ubunt to implement this?

thanks

---

### Post by pricetech on 2010-05-18
I'm not familiar with any filtering software, but Open DNS offers the ability to filter out certain content, based upon categories, or blocking specific sites.

I'd start there, then fine tune it with the router.

Someone may come along with a better solution in another post, but that's how I'd proceed.

---

### Post by uRock on 2010-05-18
You can use OpenDNS and use its lighter filter which will block porn and illegal sites. I use it for my daughter's box and have it at the strongest settings to block pretty much everything. She is 6, so her needs are simple, for now.

---

### Post by snkiz on 2010-05-18
I use the simplest solution of all, I watch my kids while they are at the computer. When my son (now 10.) gets too old for that I'm sure he'll be smart enough to defeat just about any filter I can implement.

---

### Post by Ceiber Boy on 2010-05-18
> **uRock said:**
> You can use OpenDNS and use its lighter filter which will block porn and illegal sites. I use it for my daughter's box and have it at the strongest settings to block pretty much everything. She is 6, so her needs are simple, for now.
How do i install this 'openDNS'?

sudo apt-get install openDSN

sorry this might need a bit more explaining

---

### Post by uRock on 2010-05-18
I apologize for telling the how of using it. Go to [OpenDNS site]("http://www.opendns.com/solutions/overview/") and set up and account. They will give you the DNS address to put in either your Network Manager or your router, whichever you choose. It sounds harder than it is. They will have directions to walk you through it.

Their free service is fine. They do have paid versions that offer much more manageability.

---

### Post by cariboo on 2010-05-18
You may want to have a look at [DansGuardian]("http:///dansguardian.org/"), it's in the repositories.

---

### Post by bodhi.zazen on 2010-05-19
This is how I do it :

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

So I use Opendns -> Privoxy = adblocking 

For the children Dansguardian -> privoxy.

The caveats I found with all this (I have tried several options) :

1. Using privoxy means you do not have to set up adblock on each and every browser for each and every user (neither opendsn or dansguardian have adblocking built in).

2. Using the iptables rules means Parents can have less restrictive access, children are more restricted. This works for all users regardless of browsers.

3. With all these tools you will find some websites are "broken", When that happens you will need to manually edit and review the config files to fix it. IMO privoxy and dansguardian are easier to manage then squid, but it will almost certainly take some time to fine tune.

4. These tools are fairly generic, which makes sense as I doubt you will find any consensus about each and every web site. But this means, as was pointed out, you will still need to keep an eye on your children.

---

