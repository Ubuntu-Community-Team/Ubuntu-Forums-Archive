---
title: "What's the deal with Epiphany and privacy?"
date: 2007-09-25
forum: The Cafe
---

### Post by keyboardashtray on 2007-09-25
I'd really like to use Epiphany - love GNOME, and I just like the idea of using the official GNOME browser. I like things to be integrated, a similar style across the board.

I just can't get over the fact that I can't whitelist cookies (and pop ups) in Epiphany. Geez, doesn't everyone do this? 

It should really be in there by default. But barring that, they should at least offer an extension. 

It doesn't help that the "middle of the road" option (only accept from sites you navigate to) is so vague. At first, I thought - ok, that might make sense. It accepts cookies from sites that you directly type the address of. Or are in a bookmark. Hey, I thought, that might actually be a convenient way of whitelisting, without the throwing in of the dreaded "unnecessary preference". Nope. It pretty much lets anything through, guess it blocks image cookies or something from 3rd party sites.

Epiphany really needs at least the basic fundamentals of online privacy. Cookie/popup management, history management, an option to not remember what I type and an option to clear all private data at the end of the session. Script blocking whitelist/blacklist would be nice too, but I realize I might be on the fringe on that one.

Like I say, I love Gnome, and I hate to add to the negative stereotype. But it's extreme decisions like this that create the stereotype. 

I understand they want to avoid confusing options, but sacrificing so many basic privacy options for the sake of avoiding confusion crosses the line from keeping it simple to insulting my intelligence.

---

### Post by bash on 2007-09-25
I agree. Something along the lines of the Firefox extension "Cookie button in the status bar" would be great.

I miss that feature and maybe even more importantly I miss a NoScript like extension for Epiphany. That for me is the real reason I still use Firefox. 

Maybe Epiphany with Webkit rendering engine will direct some attention towards this broswer and increase its popularity and the extensions available for it.

---

### Post by keyboardashtray on 2007-09-25
> **ubun-two said:**
> I agree. Something along the lines of the Firefox extension "Cookie button in the status bar" would be great.

I miss that feature and maybe even more importantly I miss a NoScript like extension for Epiphany. That for me is the real reason I still use Firefox. 

Maybe Epiphany with Webkit rendering engine will direct some attention towards this broswer and increase its popularity and the extensions available for it.

You may be right there...I guess I'll have to adopt a wait & see approach.

---

### Post by htor on 2007-09-25
Epiphany intended for professionals - those guys that just can't fall victim to phishing scams. If you are n00b or just like outdated technology then I recommend you to stay with FF.

---

### Post by Mr. Picklesworth on 2007-09-25
> Hey, I thought, that might actually be a convenient way of whitelisting, without the throwing in of the dreaded "unnecessary preference".Wow, that would actually be really cool!

I'm working on a design for lighter feeling bookmarks, and that sounds like a great thing to set it apart from the pack. The idea with my project is that the current interface for web bookmarks causes people to hesitate upon adding them, because they waste space in a very visible way, so that convenient white-listing would actually not work with the current behaviour.

If bookmarks were instead just "places you are interested in" (combined with integration of web History), working in a way that is not space consuming but still offers the other bonuses of bookmarks (address bar searching, for example, and eventual rediscovery of a bookmarked page), that would make a lot more sense.

---

### Post by Wolki on 2007-09-25
> **keyboardashtray said:**
> I just can't get over the fact that I can't whitelist cookies (and pop ups) in Epiphany. Geez, doesn't everyone do this? 


Whitelisting popups should work fine, it's in the view menu. It will enable it per site.

For cookies, is [http://www.0d.be/2007/09/25/new-in-epiphany-2.20/](http://www.0d.be/2007/09/25/new-in-epiphany-2.20/) an option for you?

> It should really be in there by default. But barring that, they should at least offer an extension. 


If I remember correctly, there are problems with accesing cookie stuff from extensions because they need to access stuff in gecko.

> Epiphany really needs at least the basic fundamentals of online privacy. Cookie/popup management, history management, an option to not remember what I type and an option to clear all private data at the end of the session. Script blocking whitelist/blacklist would be nice too, but I realize I might be on the fringe on that one.


If you want your epiphany not to store all these things, how about using a private session? [http://live.gnome.org/Epiphany/FeatureDesign/PrivateBrowsing](http://live.gnome.org/Epiphany/FeatureDesign/PrivateBrowsing)

Nozte that this was the specification, it has been implemented for 2.16. Access it via a command line parameter(--private-instance I think, see the manpage).

---

### Post by keyboardashtray on 2007-09-27
Thanks for the ideas :)

I guess I just don't see myself working in the command line everytime I browse the net. I mean, I could configure a seperate launcher for that, but I'm thinking then that it would probably interfere with features that do require, for example, cookies, and would interfere with the convenience options cookies enable for the web sites I trust. So I'd have to set up two, and juggle between them.

As far as the cookies whitelisting through that option you linked to me, that was interesting - I didn't see any articles about that (although I don't know why they have to bury it in some config file). Even that, though, would mean getting nagged with a warning message at almost every website, and if its similar to the similar option here in FF (last time I tried it) it will often mean getting the nag 3-4 times in one site, once for every cookie I deny.

I appreciate the idea though, those three options are all news to me!

---

### Post by quixotic-cynic on 2007-10-07
Yes, this annoys me too...

* no cookie whitelist (why would anyone remove this?!?!?)
* no javascript whitelist (noscript)
* no easy block image without adblock plus

* can't close tabs on middle click, cant get rid of the tab-close icons (despite editing about:config), and (I found out just now) that I can't right click and correct spelling errors.

* also cannot put all my menus on one row anymore.

I *want* to use it - but it just seems like "Browsing For Dummies" at present.

> **htor said:**
> Epiphany intended for professionals - those guys that just can't fall victim to phishing scams. If you are n00b or just like outdated technology then I recommend you to stay with FF.

I really hope that is sarcasm. ^_^ Webbugs, script exploits and tracking cookies - the list goes on.

> **keyboardashtray said:**
> Even that, though, would mean getting nagged with a warning message at almost every website, and if its similar to the similar option here in FF (last time I tried it) it will often mean getting the nag 3-4 times in one site, once for every cookie I deny.

It's unworkable... it drives you nuts after about 3 sites and is very inefficient. The best option I have found is to disable cookies and have a hostperm.1 file from firefox that contains your cookie whitelist. The drawback is that you would have to put cookie prompt on and reload the site, enable the cookie, and then disable cookies again every time you want to enable a new cookie.

> **keyboardashtray said:**
> I understand they want to avoid confusing options, but sacrificing so many basic privacy options for the sake of avoiding confusion crosses the line from keeping it simple to insulting my intelligence.

Perhaps they should just build in a much more convenient way of using the whitelist and make it the default. With a few lines explanation it is not a difficult concept to grasp - FFx just puts it in a really stupid hard-to-get-to place. You could have one of those messages at the bottom of the screen show by default to help less experienced users.

---

### Post by keyboardashtray on 2007-10-07
> **quixotic-cynic said:**
> Yes, this annoys me too...

* no cookie whitelist (why would anyone remove this?!?!?)
* no javascript whitelist (noscript)
* no easy block image without adblock plus

* can't close tabs on middle click, cant get rid of the tab-close icons (despite editing about:config), and (I found out just now) that I can't right click and correct spelling errors.

* also cannot put all my menus on one row anymore.

I *want* to use it - but it just seems like "Browsing For Dummies" at present.

Exactly - I really like GNOME from a style perspective, and I like the integration. So much of computers is web browsing, and I think an area that even the beginning user becomes at least semi knowledgeable about - I think if a preferences menu mentions cookies, then it assumes some knowledge from the user about what cookies are. The fact that the interface allows them or forbids them suggests that they sometimes serve a function, and sometimes are negative. It therefore stands to reason that there should be some function that achieves a middle ground - and whitelisting is the ideal way.

> **quixotic-cynic said:**
> I really hope that is sarcasm. ^_^ Webbugs, script exploits and tracking cookies - the list goes on.

Yeah, I didn't know what to think of this either.

> **quixotic-cynic said:**
> Perhaps they should just build in a much more convenient way of using the whitelist and make it the default. With a few lines explanation it is not a difficult concept to grasp - FFx just puts it in a really stupid hard-to-get-to place. You could have one of those messages at the bottom of the screen show by default to help less experienced users.

GNOME's default response to a complicated but extremely useful feature shouldn't be "lets just take it out", it should be "how can we make this easier?" 

I think one of the most helpful features but underused feature in any computer program is hover over help. Getting relevant information, even if it is a whole paragraph, when I hover over an option, etc., is so much easier than scanning through a manual. It sticks in your head better - like you said, a few lines of explanation in the right context is all it takes to teach a less experienced user about some feature. 

They come so close to getting it right is with Galeon. I am trying that out now, and it has excellent cookie handling. You can set it up to deny cookies by default, but there is a drop down menu to allow for site. There is also a drop down menu for allowing pop - ups. There is no script whitelisting, but there is an easy toggle that I can deal with (even Firefox needs NoScript I suppose). 

Galeon's bookmarks, though, leave a bit to be desired. There are some innovative features, but the interface is a little choppy. It takes a bit of time to get your bookmarks where you want them, and the smart bookmarks feature is unGNOME and a little messy. I much prefer Epiphany's cool bookmarking system.

I don't know what the work on Galeon is going to be, though - are they putting their efforts more behind Epiphany at the moment?

I think what could solve everything is to simply start with what Epiphany is now, and have a plethora of plugins solve the rest. I would *love* that - start with a pretty bare-bones browser, and just add in any features you want. Maybe if what Ubun-two was saying, that maybe  this whole webkit thing opens the door.  

Now if someone with the know how could just get cracking on a privacy plugin, I'd make the switch.

---

### Post by kadath on 2007-10-07
One of the biggest reasons I refuse to switch from Firefox is that I'd have to go without NoScript, CS Lite and Adblock Plus. **No thanks.**

---

### Post by quixotic-cynic on 2007-10-08
> **keyboardashtray said:**
> They come so close to getting it right is with Galeon. I am trying that out now, and it has excellent cookie handling. You can set it up to deny cookies by default, but there is a drop down menu to allow for site.

That sounds good - it is similar to what SeaMonkey does at the moment. Unfortunately, Galeon uses more resources than Firefox so I tend to prefer Firefox (Iceweasel actually, due to a few more privacy tweaks)(and a small speed boost, though I may be wrong since I can't see how that is possible).

> **keyboardashtray said:**
> There is no script whitelisting, but there is an easy toggle that I can deal with (even Firefox needs NoScript I suppose).

The latest version of NoScript is even better - seems like I am permanently stuck with a choice of FFx, SeaMonkey and IceWeasel unless someone pulls off a minor miracle.

> **keyboardashtray said:**
> I don't know what the work on Galeon is going to be, though - are they putting their efforts more behind Epiphany at the moment?

I got the impression that the Galeon team decided it was 'unsustainable' and gave up on Galeon to focus on extensions for Epiphany. I'm not sure if Galeon gets updated any more.

> **keyboardashtray said:**
> I think what could solve everything is to simply start with what Epiphany is now, and have a plethora of plugins solve the rest.

You should like the above comment then. I like modular stuff too.

> **keyboardashtray said:**
> Now if someone with the know how could just get cracking on a privacy plugin, I'd make the switch.

I had a look at the making-plugins page. They are made in python or C which is much better than anything with 'java' in the name (imho, of course). Looking at what you need to know i'm not sure i'd have a chance...

Edit: BTW - Epiphany with Privoxy would solve most of the problems, but it's a pain because it doesnt support compressed web page delivery (& it's one more piece of software to annoy you)..

Edit2: It does support compressed pages, it just stops one or two features. It is working much better than worrying about individual browser settings so I am using it now to solve the problem - no privacy leaks on any browser going through the proxy.

---

### Post by keyboardashtray on 2007-10-13
> **quixotic-cynic said:**
> That sounds good - it is similar to what SeaMonkey does at the moment. Unfortunately, Galeon uses more resources than Firefox so I tend to prefer Firefox (Iceweasel actually, due to a few more privacy tweaks)(and a small speed boost, though I may be wrong since I can't see how that is possible). 

> **quixotic-cynic said:**
> I got the impression that the Galeon team decided it was 'unsustainable' and gave up on Galeon to focus on extensions for Epiphany. I'm not sure if Galeon gets updated any more.

Yeah, running Galeon did seem to take a touch longer, there were a couple (minor) bugs too, if it looks like Galeon isn't going to be supported, I think I'll drop it. 
I'm very interested in Iceweasel, I've been reading a bit about it. I was going to try it when it is available in the repos, because it seems like its more GNU and I'm trying to go in that direction. I didn't get to try BurningDog; I downloaded the gNewSense LiveCD and I couldn't get connected. I thought I read something about Iceweasel having a couple more privacy tweaks than Firefox too. I hope it makes its way to the repos. I wanted to try Gobuntu when it comes out, but I'm guessing if gNewSense didn't work all the way for me, I might have some hardware issues with Gobuntu too. I guess the middle ground is slowly trimming out all the non-free I can.

> **quixotic-cynic said:**
> I had a look at the making-plugins page. They are made in python or C which is much better than anything with 'java' in the name (imho, of course). Looking at what you need to know i'm not sure i'd have a chance...

I don't know any programming, but I think I understand why Python or C would be better than Java - Sun still hasn't fully released Java as free yet, right? Well, that and maybe there are some technical advantages for the formers too? Heh, I still have a bit to learn, but it is all intriguing. 

> **quixotic-cynic said:**
> Edit: BTW - Epiphany with Privoxy would solve most of the problems, but it's a pain because it doesnt support compressed web page delivery (& it's one more piece of software to annoy you)..
Edit2: It does support compressed pages, it just stops one or two features. It is working much better than worrying about individual browser settings so I am using it now to solve the problem - no privacy leaks on any browser going through the proxy.

I checked out Privoxy's website. I've never set up a proxy before but it does seem like the way to go, even if a browser already has a lot of privacy features. 

Thanks for all the ideas man - I got a lot to go off of here. You have any idea how long until IceWeasel makes its way to the Ubuntu repos? I'm still new to a lot of this, I don't have a feel for how long projects take before they make it into the repositories.

---

### Post by Dr. C on 2007-10-13
One feature I really like in Firefox is the ability to set cookies to accept cookies but only keep them until I close Firefox regardless of the expiry date for the cookie. One can white list a few sites to allow permanent cookies.

I have found that this approach effectively deals with the privacy issues regarding tracking cookies since they only get to track for one session and can be reset at any time simply by restarting Firefox. The feature is present in Firefox and Opera but is lacking in Epiphany and Internet Explorer, and it was the main reason I left IE for Firefox when I was running Windows. Setting the cookies to prompt is not an option, been there done that with both IE 5 and 6.

I hate to say this but Epiphany is not in very good company when it comes to cookies.

---

### Post by quixotic-cynic on 2007-10-16
> **FineE said:**
> One feature I really like in Firefox is the ability to set cookies to accept cookies but only keep them until I close Firefox regardless of the expiry date for the cookie. One can white list a few sites to allow permanent cookies. The feature is present in Firefox and Opera but is lacking in Epiphany and Internet Explorer, and it was the main reason I left IE for Firefox when I was running Windows.

Selecting the "Allow cookies only from sites you visit" does more or less the same thing - since you never visit doubleclick.com etc then the tracking cookies will never get set... (it only allows cookies tied to the domain you are actually on to be set by the same site).

Going into about:config and changing network.cookie.enableForCurrentSessionOnly to true could achieve what you are trying (but for all cookies, which may be a problem) - provided that it is not one of the settings that Epiphany 'ignores'.

The universe repo of gutsy has **Iceape** in it - which has far far better settings than firefox w.r.t. privacy/paranoia. It is definitely worth checking out - though I have not been using it enough yet to tell for sure if i'm going to keep using it. (btw - IceApe ~= SeaMonkey ~= Mozilla). It's peformance does not seem as good as SeaMonkeys (/w browser element only installed) but it's all somewhat subjective really.

Edit: Iceape/SeaMonkey + NoScript + Privoxy seems the best combo for now.

Edit2: If you are trying to get rid of non-libre stuff (free is too damn confusing for me) the install and run vrms. It's not perfect but works pretty well. I installed gobuntu-desktop but it seems there are a few bugs to iron out yet w.r.t. it being completely free.

Edit3: Iceweasel is not in the repos yet but it is *really* easy to install anyway - just unzip it to a directory and run the 'iceweasel' file. Security wise it is probably best to do *sudo chown root DirectoryYouPutItIn* and then make the main file executable for your username (*sudo chmod u+x iceweasel*).

---

### Post by keyboardashtray on 2007-10-18
> **quixotic-cynic said:**
> 
Edit2: If you are trying to get rid of non-libre stuff (free is too damn confusing for me) the install and run vrms. It's not perfect but works pretty well. I installed gobuntu-desktop but it seems there are a few bugs to iron out yet w.r.t. it being completely free.

Edit3: Iceweasel is not in the repos yet but it is *really* easy to install anyway - just unzip it to a directory and run the 'iceweasel' file. Security wise it is probably best to do *sudo chown root DirectoryYouPutItIn* and then make the main file executable for your username (*sudo chmod u+x iceweasel*).

Yeah, I've had VRMS for a bit, hear it does something neato when you've got a clean system.

I'm definitely going to give Iceweasel a go, then. I'm going to hold off until I'm running Gutsy, since it's just around the corner here - and I'll burn a Gobuntu CD once they have a LIveCD, and give that a go too, although I'm guessing whatever issues I had with gNewSense will carry over.

---

### Post by quixotic-cynic on 2007-10-18
> **keyboardashtray said:**
> I'll burn a Gobuntu CD once they have a LIveCD, and give that a go too, although I'm guessing whatever issues I had with gNewSense will carry over.

I just removed ubuntu-desktop and installed gobuntu-desktop. Didn't seem to change too much atm. Anyway, that's side-tracking...

I still want to use Epiphany but it's just too dumbed-down. It's okay, sort of, but I had to install gnome-control-center just to change the proxy settings. The lack of NoScript or history controls remains annoying.

---

### Post by keyboardashtray on 2007-10-22
> **quixotic-cynic said:**
> 
I still want to use Epiphany but it's just too dumbed-down. It's okay, sort of, but I had to install gnome-control-center just to change the proxy settings. The lack of NoScript or history controls remains annoying.

Yeah - I definitely dig the GNOME, got Balsa running and enjoy it, GNOME office is good enough for my needs (although it'd be nice to have a simple presentation viewer), a GNOME browser would sweeten the deal.

Guess I'll just have to cross my fingers that they'll add a few more tweaks to Epiphany in time.

---

### Post by keyboardashtray on 2007-10-22
> **FineE said:**
> One feature I really like in Firefox is the ability to set cookies to accept cookies but only keep them until I close Firefox regardless of the expiry date for the cookie. One can white list a few sites to allow permanent cookies.

I have found that this approach effectively deals with the privacy issues regarding tracking cookies since they only get to track for one session and can be reset at any time simply by restarting Firefox. The feature is present in Firefox and Opera but is lacking in Epiphany and Internet Explorer, and it was the main reason I left IE for Firefox when I was running Windows. Setting the cookies to prompt is not an option, been there done that with both IE 5 and 6.

I hate to say this but Epiphany is not in very good company when it comes to cookies.

Right, the clean slate when I close Firefox, I forgot when they added that but it was a big deal to me. I haven't really used IE in years, last time I was on it for a sec seems they went with tabbed browsing too. Wonder how far they've come in the privacy department? *shudders*

---

### Post by Ehtetur on 2007-10-23
> **keyboardashtray said:**
> Yeah - I definitely dig the GNOME, got Balsa running and enjoy it, GNOME office is good enough for my needs (although it'd be nice to have a simple presentation viewer), a GNOME browser would sweeten the deal.

Guess I'll just have to cross my fingers that they'll add a few more tweaks to Epiphany in time.

Same here... tried epiphany a few times with dapper, edgy, and feisty... haven't tried yet with gutsy... Don't want to be let down so soon after a successful install...
Give it noscript and adblock (for image and iframes) support, and epiphany would be my browser.

side note: Here's a list of Top 10 FF extensions to avoid.. I use about 1/2 of them:
[http://www.computerworld.com/action/article.do?articleId=9015599&command=viewArticleBasic]("http://www.computerworld.com/action/article.do?articleId=9015599&command=viewArticleBasic")

---

### Post by keyboardashtray on 2007-10-23
> **Ehtetur said:**
> 
side note: Here's a list of Top 10 FF extensions to avoid.. I use about 1/2 of them:
[http://www.computerworld.com/action/article.do?articleId=9015599&command=viewArticleBasic]("http://www.computerworld.com/action/article.do?articleId=9015599&command=viewArticleBasic")

Wow, nice read. I use 3 or 4 of those too. I know where they are coming from on NoScript, but I just happen to fall into that paranoid group. And I tend to go to the same few sites that need script, so they get whitelisted. And you get used to whitelisting sites, as a matter of habit - video not working? Quick sweep and its up. It's easy enough to get used to.

I had to laugh when I saw "Track Me Not" - because I think I might have to pick that one up, even if it is on a worst-of list. Sounds pretty good to me - that AOL story pissed the hell out of me, and I've been using ixquick.com ever since. But the bottom line is I don't think the search is as powerful. It gets the job done most of the time, but this Track Me Not might let me get back on the Google. I'll have to see how it affects my resources, this might sound callous but I'm not too sympathetic to the search engines' needs, that profile building is one of the most devious things happening on the net that no one cares about.

I am slightly sympathetic to business with the whole Ad blocker thing though, not many of the really bad ads were slipping by the way it was. But it only takes one "ZAP THE MONKEY AND WIN AN IPHONE!" to sully the reputation of all ads. 

Cool link.

---

### Post by quixotic-cynic on 2007-10-26
Ehtetur, I saw that a while ago, but it is pretty amusing. :)

> **keyboardashtray said:**
> I had to laugh when I saw "Track Me Not" - because I think I might have to pick that one up, even if it is on a worst-of list. Sounds pretty good to me - that AOL story pissed the hell out of me, and I've been using ixquick.com ever since.

Please don't use that plugin - it's a lame 10-year-old type of thing (you know what I mean)(sorry to 10 year olds) and I'm not sure it would work anyway.

Try [http://www.scroogle.org/scraper.html](http://www.scroogle.org/scraper.html) or [http://www.blackboxsearch.com/](http://www.blackboxsearch.com/) if you are worried. Scroogle is probably the more reliable (that guy reallllyyy doesn't like Google).

A better setup is to use a PAC file or Privoxy to route connections to just the search sites and leave everything else. It's not that difficult but I gave up on doing that a while ago - I don't care *that* much.

---

### Post by keyboardashtray on 2007-10-27
> **quixotic-cynic said:**
> 
Please don't use that plugin - it's a lame 10-year-old type of thing (you know what I mean)(sorry to 10 year olds) and I'm not sure it would work anyway.

:lolflag: OK I suppose you're right: it is a bit drastic. But you gotta admit, they are kind of asking for it with the profile building. From what I've read, Google, for example, keeps the data permanently. Now, it doesn't matter what their policy is regarding what they do with it, at some point some *will* get out. Whether it is a slip up, theft, or a government demand (all the more likely every day), at some point, even if it is years down the line, some people's data is going to get out there in nice tidy searchable format. And no amount of "don't be evil" is going to compensate after the fact. Once it's on the net, it's there forever. So in my opinion, they are either naive or reckless.

> **quixotic-cynic said:**
> Try [http://www.scroogle.org/scraper.html](http://www.scroogle.org/scraper.html) or [http://www.blackboxsearch.com/](http://www.blackboxsearch.com/) if you are worried. Scroogle is probably the more reliable (that guy reallllyyy doesn't like Google).


I like the looks of Scroogle, I'll keep it handy for when I really need Google's power. In the meantime I'll continue to patronize ixquick.com - they have a good privacy policy, and don't hang on to the records.

---

### Post by quixotic-cynic on 2007-10-27
> **keyboardashtray said:**
> But you gotta admit, they are kind of asking for it with the profile building. From what I've read, Google, for example, keeps the data permanently.

It is pretty lame. They keep personal data for 18 months and then it goes into aggregate afaik. Still really bad anyway.

> **keyboardashtray said:**
> ...  or a government demand (all the more likely every day)

It's not exactly a future thing, more like a past thing. [http://www.nytimes.com/2006/01/20/technology/20google.html?_r=1&oref=slogin](http://www.nytimes.com/2006/01/20/technology/20google.html?_r=1&oref=slogin) / [http://blog.searchenginewatch.com/blog/060119-060352](http://blog.searchenginewatch.com/blog/060119-060352)

I'm not sure if Google caved, but the others did. To be honest, I'm more annoyed about the 'consumer profiling' side to get people to buy more stuff. But whilst I have nothing against the present govt. where I live that's not to say that won't change in the future.

> **keyboardashtray said:**
> In the meantime I'll continue to patronize ixquick.com - they have a good privacy policy, and don't hang on to the records.

I quite like ixquick, though I'm not sure if one really gets anything out of search engines anyway - most the sights you find are spam or a waste of time (i.e. youtube, break.com, etc - funny but, oh, look, 3 hours gone).

---

