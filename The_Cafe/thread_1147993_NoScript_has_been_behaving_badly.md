---
title: "NoScript has been behaving badly"
date: 2009-05-03
forum: The Cafe
---

### Post by Foster Grant on 2009-05-03
I was going to say it has been misbehaving, but this goes beyond that.

The Firefox extension NoScript has been very quietly adding its own whitelist exceptions to AdBlock Plus. Obviously, nothing runs on charity but it seems kind of evil to go behind the user's back to ensure a revenue stream ... in fact, it seems kind of like malware to me.

Here's a blog post from AB+ developer Wladimir Palant: [http://adblockplus.org/blog/attention-noscript-users](http://adblockplus.org/blog/attention-noscript-users)

> For years, NoScript has been using a trick to prevent Adblock Plus from working on its domains. Fixing this issue was never particularly high on my list of priorities (though I finally came around and fixed it after the recent events) so at some point I suggested that EasyList should be extended by a filter to block ads specifically on NoScript’s domains. This finally happened two weeks ago.

What followed was a small war — the website would add various tricks to prevent Adblock Plus with EasyList from blocking ads, EasyList kept adjusting filters. Then, a week ago a new NoScript version was released. A few days later I noticed first bug reports — apparently, Adblock Plus “glitches” were observed with this NoScript version, especially around NoScript’s domains (but not only those). When I investigated this issue I couldn’t believe my eyes. NoScript was extended by a piece of obfuscated (!) code to specifically target Adblock Plus and disable parts of its functionality. The issues caused by this manipulation were declared as “compatibility issues” in the NoScript forum, even now I still didn’t see any official admission of crippling Adblock Plus. Clearly, NoScript is moving from the gray area of adware into dark black area of scareware, making money at user’s expense at any cost.

It's also in violation of [_Mozilla's add-ons policy_](https://addons.mozilla.org/pages/policy).

All in all, very not cool — to the point that I've uninstalled it on the  principle that if it *seems* like malware, it might *be* malware at some point. Doesn't hurt me a bit (I only rarely used it and found it slowed me down more than helped me) but like I said/typed ... it's the principle of the thing, and apparently the NoScript developers don't have any.

---

### Post by Favux on 2009-05-03
Not good, but at least:
> Update (2009-05-02): Apparently, thanks to some pushing from AMO yet another NoScript version was released. This one supposedly no longer adds a filter subscription to Adblock Plus and also removes the one added by the previous versions. Also, a change to AMO policy is under discussion. Big thanks to everybody who made that happen!

---

### Post by yoasif on 2009-05-03
thankfully, the copy in the repos was never updated with the malware. that copy is still safe, if you want to use it. 

plus, the copy in the repos does not auto-open the noscript page when updated.

---

### Post by Foster Grant on 2009-05-04
Nonetheless, are you sure you can trust it?

And are you *sure* the version in the Ubuntu repos doesn't have that function? As noted by the AB+ developer, NoScript has been doing this for years. I would have to have proof that the version of NoScript in the repos does not alter Easylist or other functions without my permission.

I had to go back and resubscribe to Easylist; I'm not certain why, but I would bet NoScript disabled the Easylist subscription while keeping whatever filters were in place at the time for appearance's sake (presumably so I wouldn't notice that the subscription itself was gone).

It comes down to trust and honesty. It *says* it's going to do something that's supposedly good, but at the same time it goes behind my back and does something else that I consider to be bad. I can't accept that.

---

### Post by Polygon on 2009-05-04
noscript is gpl. If it gets bad, someone will fork it, and all will be well.

---

### Post by mc4100 on 2009-05-04
It does seem, I think, to have been blown a little out of proportion, I'm hearing the M-word being slung around ...
Anyway here's [the rebuttal]("http://hackademix.net/2009/05/04/dear-adblock-plus-and-noscript-users-dear-mozilla-community/") to Wladimir's post by Giorgio Maone.

---

### Post by steeleyuk on 2009-05-04
> The development of NoScript is sustained both by donations and advertisements published on a few related web sites in four domains (noscript.net, flashgot.net, informaction.com and hackademix.net).

I always wondered why those domains were on the whitelist immediately after installing. They were always the first thing I removed form NoScript... along with live.com, yahoo, etc.

---

### Post by Orlsend on 2009-05-04
I am on the latest version of No-script, I was never able to experience the problems some of you may have.

---

### Post by kerry_s on 2009-05-04
don't use it and don't think i will ever use it again.

---

### Post by bodhi.zazen on 2009-05-04
First, thank you Foster Grant for bringing this issue to our attention.

Second, this issue has been discussed on many many locations and if you wish to add to the discussion I would direct you there.

I also urge everyone to "go to the source".
[B]
[/B]Wladimir Palanthttp (adblock developer) : [http://adblockplus.org/blog/attention-noscript-users](http://adblockplus.org/blog/attention-noscript-users)

Giorgio (NoScript developer) : [http://hackademix.net/author/ma1/](http://hackademix.net/author/ma1/)

IMO: This is how opensource works , people examine the code and it works.

I still use NoScript but would be willing to consider an alternate (sorry, my browser has been hijacked once too often to give up NoScript).

Edit: On second thought I will leave this thread open for now. but please keep the conversation on topic ;)

---

### Post by yabbadabbadont on 2009-05-04
You could always just disable all active content in your browser directly instead of relying on add-ons to do it for you.  If a web site doesn't work that way, politely inform them that their site is inaccessible to the blind using a Braille terminal.

---

### Post by Polygon on 2009-05-04
thats good and all, too bad no website would care if you claim that their site is not very functional without at LEAST javascript. even this forum uses javascript for stuff.

and noscript: he got owned for his mistakes, apologized, and revered the bad stuff. I forgive him.

---

