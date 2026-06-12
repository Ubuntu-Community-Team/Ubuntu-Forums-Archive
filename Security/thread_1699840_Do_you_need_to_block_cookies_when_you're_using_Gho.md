---
title: "Do you need to block cookies when you're using Ghostery?"
date: 2011-03-04
forum: Security
---

### Post by Dry Lips on 2011-03-04
I've got a little question. I use Ghostery to block bugs
 and the cookies associated with the bugs. In addition
 I also use a cookie-blocker. Now, is it an overkill to 
block normal cookies if I use Ghostery?
 (I'm not thinking of flash cookies).

---

### Post by wacky_sung on 2011-03-04
What you actually need is just using bleachbit which can clear all your system junks and many more.

---

### Post by handy on 2011-03-05
I use Addblock plus, Beef Taco, Better Privacy, NoScript & Grease Monkey. Grease Monkey allows me to run a script called googlePrivacy (which I & everyone else can look at so I trust it) that handles more than Ghostery (who I no longer trust).

The other things I do to Firefox are via about:config as follows:

By setting **network.http.sendRefererHeader** in Firefox preferences (about:config) to zero, then whenever you visit a link from one site, the destination site doesn't know the original site you were referred from.

This in effect makes the Firefox add-on RefControl redundant.

Also, by setting **network.prefetch-next** to false it brings about the following:

Link prefetching is when a web page hints to the browser that certain pages are likely to be visited, so the browser downloads them immediately so they can be displayed immediately when the user requests it. This preference controls whether link prefetching is enabled.

I prefer this disabled personally, for a variety of reasons.

As far as cookies are concerned, I have Firefox set to accept all cookies & I have Firefox ask me about every cookie. Which all but a few that I need for some forums & such I block telling Firefox to remember what I said & to do it for all cookies on that site. If need be I can go in & delete a cookie if I find that I need it for that site for some reason.

As time goes by you gain a large list of sites that you have permanently black listed & a small list that you have white listed. Which also means that as time goes by you aren't being asked what to do with cookies for any sites that you regularly visit.

Works for me. :)

---

### Post by Dry Lips on 2011-03-05
**wacky_sung**:

Thank you for your suggestion... I'm definitively going to check BleachBit out!

---

### Post by Dry Lips on 2011-03-05
**handy** wrote:

> I use Addblock plus, Beef Taco, Better Privacy, NoScript & Grease  Monkey. Grease Monkey allows me to run a script called googlePrivacy  (which I & everyone else can look at so I trust it) that handles  more than Ghostery (who I no longer trust).I currently use AdBlock Plus, Better Privacy, 
CS lite (for cookie-blocking), Ghostery and NoScript.
 (Plus other additions not related to privacy.) 
My initial question was whether or not it is necessary
 to block all cookies at every page you visits when 
you already got an add-on that blocks what we're 
really worried about, namely trackers invading your privacy.
 Are there trackers around that Ghostery/googlePrivacy
 don't block? Is googlePrivacy some how related
 to the search engine Google, (personally I use Ixquick)
 or is it a tracker blocker? You do also state that you
 no longer trust Ghostery... Please feel free to elaborate!
 
 Thanks for the tip about **network.http.sendRefererHeader.**
I promptly set it to naught!  
 
When it comes to **network.prefetch-next**, do you 
disable this for security or other reasons?
 
Cheers!

---

### Post by handy on 2011-03-05
> **Dry Lips said:**
> 
I currently use AdBlock Plus, Better Privacy, 
CS lite (for cookie-blocking), Ghostery and NoScript.
 (Plus other additions not related to privacy.) 
My initial question was whether or not it is necessary
 to block all cookies at every page you visits when 
you already got an add-on that blocks what we're 
really worried about, namely trackers invading your privacy. 

As previously mentioned, I manually block cookies in Firefox. My listed add-ons cover the hard to block cookies. These are the cookies that I wouldn't be asked by Firefox how I want them added to my permanently allow or block list. 

I too am concerned about my privacy & think that it should be unlawful for people to invade with out our permission.

> **Dry Lips said:**
> 
 Are there trackers around that Ghostery/googlePrivacy
 don't block? Is googlePrivacy some how related
 to the search engine Google, (personally I use Ixquick) 

Yes it is specifically for Google, where it works incredibly well. I actually use Scroogle, which offers another layer of privacy protection even though it uses the Google search engine. I consider the Google search engine to be by far the most effective.

> **Dry Lips said:**
> 
 or is it a tracker blocker? You do also state that you
 no longer trust Ghostery... Please feel free to elaborate! 
 
Ghostery was bought by a marketing company, that makes all of the right noises, though I think that they are gathering anonymous information from their users & making money out of it through marketing it to other marketroids. I have no proof on the matter.

> **Dry Lips said:**
> 
 Thanks for the tip about **network.http.sendRefererHeader.**
I promptly set it to naught!  
 
My pleasure. :)

> **Dry Lips said:**
> 
When it comes to **network.prefetch-next**, do you 
disable this for security or other reasons? 

I consider prefetch to be a waste of resources. Having it turned off makes no noticeable difference to my surfing speed.

---

### Post by Dry Lips on 2011-03-06
> I consider the Google search engine to be by far the most effective.
It is probably quite effective, but I find Googles position
as something near a monopolist troublesome. The search
engines are our gateways to the web, and thus can influence
our use of the web. From wikipedia:

[I]“According to Net Marketshare. In December 2010, 
rankings the market share of web search engine, 
showed **Google is** **84.65%**, Yahoo is 6.69%, Baidu
is 3.39%, Bing is 3.29% and other is 1.98%. The 
Google's worldwide market share [B]peaked at 86.3%
in April, 2010[/B].”[/I]
[https://secure.wikimedia.org/wikipedia/en/wiki/Search_engine#Market_share_and_wars](https://secure.wikimedia.org/wikipedia/en/wiki/Search_engine#Market_share_and_wars)

The only way to remedy this is to get people to use other
search engines. Ixquick is good on privacy questions, 
but it is also a meta-search engine. I would very much like
to see an independent search engine that was as concerned
with privacy as ixquick. But when it comes to accuracy, 
I think meta-search engines are really good. I used 
Metacrawler exclusively before switching to ixquick.

> I too am concerned about my privacy & think that it should be unlawful for people to invade with out our permission.
I agree. We're straying off the topic, but I greatly fear that
in the future we'll see a development into the opposite
direction; less privacy and more control and surveillance. 
But I digress. 

> Ghostery was bought by a marketing company, that makes all of the right noises, though I think that they are gathering anonymous information from their users & making money out of it through marketing it to other marketroids. I have no proof on the matter.
Okay. Companies seldom buys stuff out of benevolence,
so I understand that you are sceptical. But aren't add-ons
such as Ghostery open-source? 
 [B]
network.prefetch-next[/B]:
> I consider prefetch to be a waste of resources. Having it turned off makes no noticeable difference to my surfing speed.
All right then, I'll toggle it too... Save the bandwidth ;)

---

### Post by handy on 2011-03-06
> **Dry Lips said:**
> .
It is probably quite effective, but I find Googles position
as something near a monopolist troublesome. The search
engines are our gateways to the web, and thus can influence
our use of the web. From wikipedia:

[I]“According to Net Marketshare. In December 2010, 
rankings the market share of web search engine, 
showed **Google is** **84.65%**, Yahoo is 6.69%, Baidu
is 3.39%, Bing is 3.29% and other is 1.98%. The 
Google's worldwide market share [B]peaked at 86.3%
in April, 2010[/B].”[/I]
[https://secure.wikimedia.org/wikipedia/en/wiki/Search_engine#Market_share_and_wars](https://secure.wikimedia.org/wikipedia/en/wiki/Search_engine#Market_share_and_wars) 

It is troublesome I agree.

In Google's defence, they are the largest supporter of FOSS software on the planet. They give an enormous amount back to the community. I can't forget how hard it was to find your desired information via the web, before Google came along & did it right.

As far as Google's influence on my surfing is concerned it is minimal, as googlePrivacy really limits the marketroid side of Google, apart from what Scroogle does to it. 

> **Dry Lips said:**
> 
The only way to remedy this is to get people to use other
search engines. Ixquick is good on privacy questions, 
but it is also a meta-search engine. I would very much like
to see an independent search engine that was as concerned
with privacy as ixquick. But when it comes to accuracy, 
I think meta-search engines are really good. I used 
Metacrawler exclusively before switching to ixquick. 

I'm personally happy to limit what Google puts in its database. What I'd like to see are international laws where users have to opt-in to "any" kind of tracking & are otherwise protected from it. Though that won't happen before we've seen three full moons in a month. 

> **Dry Lips said:**
> 
I agree. We're straying off the topic, but I greatly fear that
in the future we'll see a development into the opposite
direction; less privacy and more control and surveillance. 
But I digress. 

That day arrived a while ago. More so in some countries than others. It is currently moving fast in the States & England, it may have slowed a little in Oz(?).

Unfortunately the worst thing about computers is the reality that such technology is the primary tool used to create the Big Brother scenario...

> **Dry Lips said:**
> 
Okay. Companies seldom buys stuff out of benevolence,
so I understand that you are sceptical. But aren't add-ons
such as Ghostery open-source? 

No, Ghostery is not open, GPL or copyleft.

> **Dry Lips said:**
> 
**network.prefetch-next**:
All right then, I'll toggle it too... Save the bandwidth ;)

If you don't like it that way its easy to change.

Cheers,

handy

---

### Post by Dry Lips on 2011-03-06
> In Google's defence, they are the largest supporter of FOSS software on the planet. Really? I didn't know that. But it goes in the other direction too,
just think about google chrome and their new OS... 

> That day arrived a while ago. More so in some countries than others. It is currently moving fast in the States & England, it may have slowed a little in Oz(?).

Unfortunately the worst thing about computers is the reality that such technology is the primary tool used to create the Big Brother scenario...I believe things could easily become a lot worse than now. 
I don't know how much of the European debate that makes it to Oz,
but a lot of people are quite agitated here over the new data retention directive. 

[https://www.eff.org/issues/mandatory-data-retention](https://www.eff.org/issues/mandatory-data-retention)
[http://en.wikipedia.org/wiki/Data_Retention_Directive](http://en.wikipedia.org/wiki/Data_Retention_Directive)

Now we are waaay off the topic again. I think someone ought
to suggest that they make a new category on this forum specifically
for FOSS issues. I guess this security category primarily was 
meant for solving technical problems... I know they say you can
discuss FOSS-issues in the cafe, but the threads are quickly lost
among LOL-cats and similar trivia. I think FOSS-issues definitively
are relevant to the Ubuntu-experience, and deserves a category 
of its own. Frankly I'm a bit puzzled why there isn't such a category... :confused:
Do you know who to contact to make a suggestion like this?

---

### Post by handy on 2011-03-06
> **Dry Lips said:**
> Really? I didn't know that. But it goes in the other direction too,
just think about google chrome and their new OS... 

I believe things could easily become a lot worse than now. 
I don't know how much of the European debate that makes it to Oz,
but a lot of people are quite agitated here over the new data retention directive. 

[https://www.eff.org/issues/mandatory-data-retention](https://www.eff.org/issues/mandatory-data-retention)
[http://en.wikipedia.org/wiki/Data_Retention_Directive](http://en.wikipedia.org/wiki/Data_Retention_Directive)

Now we are waaay off the topic again. I think someone ought
to suggest that they make a new category on this forum specifically
for FOSS issues. I guess this security category primarily was 
meant for solving technical problems... I know they say you can
discuss FOSS-issues in the cafe, but the threads are quickly lost
among LOL-cats and similar trivia. I think FOSS-issues definitively
are relevant to the Ubuntu-experience, and deserves a category 
of its own. Frankly I'm a bit puzzled why there isn't such a category... :confused:
Do you know who to contact to make a suggestion like this?

Since the Backyard closed way back when, the CoC became more restrictive (which is understandable as this is a technical support forum) so once politics become involved, even when they are to do with the IT industry tensions start to rise.

When we lost The Backyard & the Other OS Talk sub-forums here. Some of us were motivated to create & take part in replacements elsewhere. As far as I know all have fallen by the wayside, except for our relatively young (born last May) little forum: Spiralinear.org . Which you are most welcome to join Dry Lips. 

The Spiralinear.org forum has been a little quiet over the last few days, which is normal, it has a life of varying intensity which is understandable with its very slowly growing membership of only 55 at the mo'. :) We don't go chasing members as we like the peace that our comfortable little backwater provides. 

There are some members who have very broad ranging technical knowledgeable, as well as a general community ambience that is both broad & open minded, the administration tends to lean to the left. I being an areligious, pinko, greeny. lol Though that is not completely true, I am interested in the psychology of religion.   

A couple of the admins are working on a project which we are hosting which you might find interesting:

[http://www.spiralinear.org/showthread.php?tid=412](http://www.spiralinear.org/showthread.php?tid=412)

Anyway, there you go.

---

### Post by aavas on 2011-03-07
> **handy said:**
> Since the Backyard closed way back when, the CoC became more restrictive (which is understandable as this is a technical support forum) so once politics become involved, even when they are to do with the IT industry tensions start to rise.

When we lost The Backyard & the Other OS Talk sub-forums here. Some of us were motivated to create & take part in replacements elsewhere. As far as I know all have fallen by the wayside, except for our relatively young (born last May) little forum: Spiralinear.org . Which you are most welcome to join Dry Lips. 

The Spiralinear.org forum has been a little quiet over the last few days, which is normal, it has a life of varying intensity which is understandable with its very slowly growing membership of only 55 at the mo'. :) We don't go chasing members as we like the peace that our comfortable little backwater provides. 

There are some members who have very broad ranging technical knowledgeable, as well as a general community ambience that is both broad & open minded, the administration tends to lean to the left. I being an areligious, pinko, greeny. lol Though that is not completely true, I am interested in the psychology of religion.   

A couple of the admins are working on a project which we are hosting which you might find interesting:

[http://www.spiralinear.org/showthread.php?tid=412](http://www.spiralinear.org/showthread.php?tid=412)

Anyway, there you go.
Adblock was the original extension from which ABP is derived. ABP  features improvements to the user interface, filter subscriptions, and  an element hiding extension. It has since become the most popular  extension for Firefox, with around 12 million daily users.[]("http://en.wikipedia.org/wiki/Adblock_Plus#cite_note-9")
 Adblock Plus for Google Chrome is available since Dec 2010.[]("http://en.wikipedia.org/wiki/Adblock_Plus#cite_note-10")[]("http://en.wikipedia.org/wiki/Adblock_Plus#cite_note-11")  The code for Adblock Plus for Google Chrome is largely based off the  now renamed "AdThwart". The former developer of AdThwart is a  contributor to the project.
Like Mozilla's built-in image blocker, Adblock blocks [HTTP]("http://en.wikipedia.org/wiki/HTTP") requests according to their source address and can block [IFrames]("http://en.wikipedia.org/wiki/HTML_element#Frames"), [scripts]("http://en.wikipedia.org/wiki/JavaScript"), and [Flash]("http://en.wikipedia.org/wiki/Adobe_Flash").  It also uses automatically-generated user stylesheets to hide elements  such as text ads on a page as they load instead of blocking them, known  as element hiding

[https://adblockplus.org/en/chrome](https://adblockplus.org/en/chrome) Download Adblock Plus for Chrome

---

### Post by handy on 2011-03-07
Thanks aavas.

Most of us use Adblock plus these days, it is certainly very well known. Those that use Chrome are naturally grateful that they have been taken care of in that regard too.

---

### Post by Dry Lips on 2011-03-07
> A couple of the admins are working on a project which we are hosting which you might find interestingI think any project that includes public domain books is interesting!

> “Since the Backyard closed way back when, the CoC became more restrictive (which is understandable as this is a technical support forum) so once politics become involved, even when they are to do with the IT industry tensions start to rise.”
 About the backyard: Being new to this forum,
I didn't know they had removed any categories...
I understand that the intention of this forum primarily is
helping people out with technical issues. I've certainly 
already received much help from friendly people here. 
I also understand the desire to keep the discussions free
from flamewars and unfriendliness. When it comes to ordinary
politics, I agree that this forum is better off without it,
but I do still think that a FOSS category under [B]Other Community
Discussions[/B] would be entirely in it's place. 

But I also take the hint, I'll come over to [http://www.spiralinear.org/](http://www.spiralinear.org/)
and post any FOSS-related threads in the cafe section on this board,
at least until we see a new FOSS sub-category here. 
(The threads in the cafe section disappears after a while, right?)

I'll mark this thread as solved!

Seeya!

---

