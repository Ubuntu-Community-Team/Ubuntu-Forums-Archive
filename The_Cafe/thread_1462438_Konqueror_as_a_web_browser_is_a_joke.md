---
title: "Konqueror as a web browser is a joke"
date: 2010-04-25
forum: The Cafe
---

### Post by kavon89 on 2010-04-25
Version tested: Kubuntu 10.04 RC, I believe it includes Konqueror 4.2.0

#1: Konqueror fails and crashes in Acid3. It normally says JavaScript needs to be enabled for the test, but it certainly is on. (so there must be a be a problem with JS detection). Sometimes when refreshing the test it will actually run and get to 42% with rendering issues before segfaulting!

#2: Facebook doesn't work, it asks if you'd like to open a file instead and the URL of it starts with m.facebook.com. Why is it being detected and redirected to a mobile site? I wouldn't think the guys over at facebook broke things. I googled around and found that going to facebook.com/?w2m will allow konq to load it properly... and it's rendered entirely wrong. (hence my trying Acid3)

---

### Post by x-shaney-x on 2010-04-25
I can't comment on the acid test thing but regarding facebook, not sure what the problem is for you but it loads fine here.

And like virtually every other browser I have tried, it still loads web pages about twice as fast as firefox <sigh>

---

### Post by jrusso2 on 2010-04-25
I prefer Firefox or Chrome to Konqueror has never been very good.

---

### Post by Untitled_No4 on 2010-04-25
Re: Facebook and Konqueror, it's not Konqueror's fault but Facebook's since they don't acknowledge the existence of Konqueror they redirect it to their mobile site.
To fix this go to Settings -> Configure Konqueror -> Browser Identification and set Konqueror to Identify as Firefox (or whatever else Facebook do support) to Facebook.

It doesn't change the fact that Konqueror can hardly compete with browsers made by companies and foundations with a much bigger budget. And let's not forget that deep inside both Safari and Google Chrome has some of Konqueror inside of them since Webkit is a fork of KHTML.

---

### Post by kavon89 on 2010-04-25
> **Untitled_No4 said:**
> Settings -> Configure Konqueror -> Browser Identification and set Konqueror to Identify as Firefox to Facebook

I'll probably do that and see how it goes because I dislike having more than one browser installed. Thanks.

---

### Post by texaswriter on 2010-04-26
Konqueror> I use dual-browsers because if I go away from my computer for long time [like if it goes to screensaver], if I try to use sound in Firefox, it sounds stuttered and some things get into a loop. Really weird. So, instead of closing all my browsers and restarting [and sometimes relogging], I just open up a konqueror windown and watch my videos [etc] in there. 

Well, Konqueror usually works fine for me. The only thing I've really noticed that is annoying is when you are on a website with flash, occasionally all the dialog boxes on the ENTIRE window [including the address bar and search bar] suddenly don't accept keyboard input [of any kind]. This happens if I goto youtube. Opening another window and other things seems to fix this temporarily. 

Otherwise though, Konqueror isn't bad at all. 

I can't say that I have ever used it as my main browser though... Firefox gets the majority of my use on any installation I have.

---

### Post by RickyCodes on 2010-04-26
Dont like KonQueror myself. Prefer Firefox, Opera, and Chrome.

---

### Post by v1ad on 2010-04-26
love chrome. stupid fast

---

### Post by 23meg on 2010-04-26
Moved to Community Cafe, as this seems to be more of a rant than a support request regarding testing in Lucid.

---

### Post by NightwishFan on 2010-04-26
I like Konqueror, it is practically it's own desktop environment. It has a beautiful logo as well. Though I have to say I prefer Epiphany as a web browser, they both are fairly poor at rendering some stuff. (Such as Ubuntu Forums)

---

### Post by krazyd on 2010-04-26
> **kavon89 said:**
> I'll probably do that and see how it goes because I dislike having more than one browser installed. Thanks.

You might like to try rekonq. It's under heavy development, but is very usable and is the first browser I have found that comes close to being a full firefox replacement (has good adblock & cookie management).

It uses the KDE subsystems for storing passwords and bookmarks so all those you have saved in Konqueror are automatically available. It's also based on webkit (like Chrome, Safari) so is very fast.

Daily PPA: [https://launchpad.net/~rekonq/+archive/rekonq-daily](https://launchpad.net/~rekonq/+archive/rekonq-daily)
More info: [http://gitorious.org/rekonq](http://gitorious.org/rekonq)

---

### Post by autumnraine on 2010-04-26
> **Untitled_No4 said:**
> Re: Facebook and Konqueror, it's not Konqueror's fault but Facebook's since they don't acknowledge the existence of Konqueror they redirect it to their mobile site.
To fix this go to Settings -> Configure Konqueror -> Browser Identification and set Konqueror to Identify as Firefox (or whatever else Facebook do support) to Facebook.

It doesn't change the fact that Konqueror can hardly compete with browsers made by companies and foundations with a much bigger budget. And let's not forget that deep inside both Safari and Google Chrome has some of Konqueror inside of them since Webkit is a fork of KHTML.

I find Facebook to be unreasonably buggy in any browser - like it was coded by distracted children. 

I second the vote for rekonq - I think it has the potential for greatness :).

---

### Post by mockingbird on 2010-04-26
I got an 89% in Acid3 and a "you should not see this at all" in the top left corner.  Firefox gives me 94%.  Konqueror also fails Acid2.  The nose is not correct.

Firefox version: 3.6.3
Konqueror version: 4.4.2

It doesn't crash though.

---

### Post by swoll1980 on 2010-04-26
Konqueror renders every page I go to incorrectly. The biggest problem I see are objects on the pages  over lapping each other, especially input boxes.

---

### Post by RiceMonster on 2010-04-26
> **kavon89 said:**
> #1: Konqueror fails and crashes in Acid3. It normally says JavaScript needs to be enabled for the test, but it certainly is on. (so there must be a be a problem with JS detection). Sometimes when refreshing the test it will actually run and get to 42% with rendering issues before segfaulting!

I was not aware of this.

[img]http://omploader.org/vNGE2bA/2010-04-26-095825_3200x1080_scrot.png[/img]



Konqueror could definitely be better, however. I think most of the problems would be solved if they would get it over with and switch to WebKit.

---

### Post by krazyd on 2010-04-26
> **RiceMonster said:**
> Konqueror could definitely be better, however. I think most of the problems would be solved if they would get it over with and switch to WebKit.
KHTML is part of the KDE 4 platform, and so it is going to be with us at least until KDE 5.

If you want to try Konqueror with WebKit rendering rather than KHTML, try this:
```
sudo apt-get install kpart-webkit
```

Just remember that it is supposed to be for testing only and has no guarantees of stability! :P

---

### Post by chucky chuckaluck on 2010-04-26
There is a webkit kpart(Ithink that's what it's called) for konqueror.

---

### Post by Roasted on 2010-04-26
Agreed. Konqueror sucks.

Dear Kubuntu Devs - Let's wise up and include Firefox instead of a Firefox installer by default.

---

### Post by RiceMonster on 2010-04-26
> **krazyd said:**
> KHTML is part of the KDE 4 platform, and so it is going to be with us at least until KDE 5.

If you want to try Konqueror with WebKit rendering rather than KHTML, try this:
```
sudo apt-get install kpart-webkit
```

Just remember that it is supposed to be for testing only and has no guarantees of stability! :P

> **chucky chuckaluck said:**
> There is a webkit kpart(Ithink that's what it's called) for konqueror.

I'm aware you can use WebKit with konqueror, I meant if they officially switched to WebKit.

---

### Post by Danny Dubya on 2010-04-26
> **Roasted said:**
> Agreed. Konqueror sucks.

Dear Kubuntu Devs - Let's wise up and include Firefox instead of a Firefox installer by default.

Not a bad idea at all. Hey, openSUSE's made Firefox default since it gained some level of KDE integration on their end, and Kubuntu Lucid has those same changes as well, so Maverick would be a good time to at least include Firefox, if not make it default. I'm sure they can get around the Live CD free space issue by downloading Firefox on the first boot or something.

---

### Post by krazyd on 2010-04-26
> **Roasted said:**
> Agreed. Konqueror sucks.

Dear Kubuntu Devs - Let's wise up and include Firefox instead of a Firefox installer by default.

There's been talk of including rekonq. 0.5 will be out by 10.10.

---

### Post by lykwydchykyn on 2010-04-26
From what I've read on the situation, I think everyone pretty much acknowledges the problem, including the konqueror/khtml devs.  Nobody's really sure what the best solution is, though.

This is a pretty good overview of the situation:
[http://aseigo.blogspot.com/2009/07/webkit.html](http://aseigo.blogspot.com/2009/07/webkit.html)

---

### Post by Shpongle on 2010-04-26
I have always found konqueror to be a good browser. I hope the devs can put more work into it to get it on par with the others

---

### Post by beetleman64 on 2010-04-26
I find that Konqueror is a bit like IE. It does the job (just) but there are some needless issues and standards compliance is iffy at best. Give me Firefox any day.

---

### Post by Warpnow on 2010-04-26
Not great, but still better than Firefox.

---

### Post by agnes on 2010-04-26
About Rekonq... I don't know anything about WebKit, will Rekonq have (or soon be able to) make use of the Moonlight plugin? On the Rekonq site it says "Rekonq will never have tons of features like (some) other browsers." so one shouldn't have high hopes I guess.

For most people I know, not having it, would made them install Firefox immediately no matter how much Rekonq = Qt. (And, applying to Konqueror, no matter how much they enjoy it's a File Browser too.)

That is just an anecdote I know. But I've heard people say SilverLight is rarely used, but maybe this is a localization thing - on TV-broadcasting-corporations' websites here it is used a lot and sometimes the only option - don't know about all the other organisations and countries.

---

### Post by krazyd on 2010-04-28
> **agnes said:**
> About Rekonq... I don't know anything about WebKit, will Rekonq have (or soon be able to) make use of the Moonlight plugin? On the Rekonq site it says "Rekonq will never have tons of features like (some) other browsers." so one shouldn't have high hopes I guess.

rekonq can use mozilla plugins just like konqueror

---

### Post by nortexoid on 2010-07-08
Konqueror's not bad. It's noticeably slower (esp. java) than top browsers (Firefox, Chrome, Opera) but it's good enough. Some pages are rendered incorrectly, but it's hard to tell if the browser's fault or poor page coding. Having a super high acid3 score is not at all important.

Konqueror with webkit (via the kpart-webkit package) is too buggy to use and it won't get much or any better. Konqueror is too dependent on HTML. Either they redesign it from the base up with qtwebkit or forget a usable konqueror with webkit backend.

I don't mind Konqueror but it doesn't stand a chance against modern browsers. E.g. the lack of an intelligent url bar (e.g. an "awesome bar" or "omnibar") is sorely missing.

---

