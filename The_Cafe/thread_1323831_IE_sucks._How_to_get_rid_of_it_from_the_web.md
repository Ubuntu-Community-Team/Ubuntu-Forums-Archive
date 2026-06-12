---
title: "IE sucks. How to get rid of it from the web?"
date: 2009-11-12
forum: The Cafe
---

### Post by LepeKaname on 2009-11-12
If you are a web developer, as me, please participate!

The ideal situation is that we (developers) can do our job following an standard, and if the browser can not render it correctly, then is the browser's fault (which will lead to a better improvement of the engines).
But with IE around, and unfortunately the most used one, if it is not rendered correctly, then it seems to be our fault!! and then we need to hack our code to make it work in IE (yea... IE SUCKS!, chech [Acid Test 3]("http://en.wikipedia.org/wiki/Acid3") to see what I'm talking about). ( **[this image]("http://www.iesucks.info/wp-content/uploads/2009/04/ie7sucksjp.jpg")** is really funny for me )

How can we take out to IE of being the #1 most used browser on the web?

It is well known that IE is the most used browser on Internet and according to some statistics they show usage percentages between 50% and 80%. However, if you search on Internet for public polls about which browser you use/like, you will see that there is not even ONE in which IE is ahead Firefox. I checked around 20 polls and Firefox rates were usually around 70% vs. 20% of IE (10% others). Try asking your friends about what browser they use/like, and I can be sure that you will get almost the same result 70/20. What does this means??? 

The reason I can think about is that people that uses Internet more often (like social networks, blogs, games, etc.) will tend to use a better browser (not only Firefox but Opera, Chrome, Safari ,etc... as well), this also may applies to new generations, which enjoy being "connected". 

If that is true, then, who is using IE? Many public places (libraries, coffee places, schools, etc.) will use only Windows (because of compatibility) and IE (because it is pre-installed), which features can be blocked to prevent a mis-use of the computer. Additionally, as we know many companies seems married with MS (or just ignorants) and will not let their employees to install any other application (for security and control reasons). Beside those cases, we still have all the people (including my grandmother) that have a reduced knowledge of computer utilization which got a new PC from the shop (of course with pre-installed Windows), and thus will not know how to install any program at all (I saw a video in [www.iesucks.info](www.iesucks.info) in which a person can't even recall what she uses to connect to internet... she said: "I just click in a blue [e]"!)

According to the **[statistics published in Wikipedia]("http://en.wikipedia.org/wiki/Usage_share_of_web_browsers")**, Google Chrome have achieved in one year more than what Opera have achieved in 10 years!. Why? its pretty obvious that Google is a pioneer in internet technology and thus it is wide used by many people. I can imagine that Chrome will raise even more the next few years and my bet is that by 2012 it will have more than the 15% of the share. 

If you see **[this chart]("http://en.wikipedia.org/wiki/File:Usage_share_of_web_browsers_%28Source_Net_Applications%29.svg")**, you will see that if things continue in the same direction, someday around 2012 firefox will tide with IE (at least in that chart).

If my bet about Google Chrome is correct, then we could expect that tide even before 2012, however this is not totally true... as I explained before, many companies, schools, coffee places, noobies, etc will not change their habits and will continue using IE until Linux (e.g. Ubuntu) could gain more acceptance in such areas.

Other important point are the web site builders like dreamweaver or frontpage which generate IE only codes, and not W3C standard code. Unfortunately many people are used to those applications (and many university courses teach those tools) and their pages are not rendered correctly in W3C compliant browsers (letting them think that only IE can do the job well done). I think better open sourced web site builder applications are required to push out those IE only generators.
(BTW, I never use web site builders, but not all people knows how to manually code a webpage :P)

Finally, I think that adding banners/messages for IE only users to recommend replacing their browser may help but it may not solve everything. 

I attached a GIMP (2.7) file and a PNG of a small banner that you can freely use in your website if you want to help in this matter. I didn't include Epiphany, Konqueror, etc. as the main idea is to replace IE (in Windows).

Just use it like this:
```
<!--[if IE]>
    <img src="img/browsers-high.png" alt="Change your browser!" />
<![endif]-->
```

Please upload here your new ideas of banners to promote "NO IE" (you can use the attached GIMP file if you want). 

(sorry about my English and for writing too much, but I'm really interested in your opinions).

Thank you for reading, Waiting for you comments...

---

### Post by Penguin Guy on 2009-11-14
[URL="http://en.wikipedia.org/wiki/File:Usage_share_of_web_browsers_(Source_Net_Applications).svg"][IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/7/7b/Usage_share_of_web_browsers_%28Source_Net_Applications%29.svg/500px-Usage_share_of_web_browsers_%28Source_Net_Applications%29.svg.png[/IMG]
[/URL]
Below are the [Acid3 Test]("http://acid3.acidtests.org/") results for the main web browsers (they're supposed to look like [this]("http://acid3.acidtests.org/reference.html")). It took me ages to find a repo' for chromium, so here's a link: [Chromium]("http://www.google.com/linuxrepositories/apt.html").

I also had a go at a banner, it still isn't perfect so any suggestions or improvements are welcome - just send me a message. Click the banner to download.

[[IMG]http://dl.dropbox.com/u/1217030/switch-from-ie.png[/IMG]]("http://dl.dropbox.com/u/1217030/switch-from-ie.tgz")

---

### Post by headbuster on 2009-11-14
My friends and I have a website for betting tips. I made the site and they fill it with content. And they don't know nothing about HTML and stuff nad both are using the damn IE.
They tell me about errors and bugs that don't appear on the other browsers:
Mozilla, chrome, opera etc.
And when I get rid of the problem in EI something else shows up on the other browsers... :@
IE is selfish!

---

### Post by SunnyRabbiera on 2009-11-14
> **Penguin Guy said:**
> I think chrome is going to be the main browser soon, they have a lot more advertising power than firefox. The only way firefox beats chrome is it's addon/plugin system.

And the matter of firefox being cross platform, screw chrome as we were supposed to have OSX/ Linux ports by now.

---

### Post by Shpongle on 2009-11-14
> **SunnyRabbiera said:**
> And the matter of firefox being cross platform, screw chrome as we were supposed to have OSX/ Linux ports by now.

well they have to get a market share first , so getting it right on win systems is crucial!!! , be patient , im using chromium now and it runs grand!!!

---

### Post by SunnyRabbiera on 2009-11-14
> **DillByrne said:**
> well they have to get a market share first , so getting it right on win systems is crucial!!! , be patient , im using chromium now and it runs grand!!!

Yeh but chromium is like a version behind and not really intended to be a regular browser.
And how much bloody market share they want, it wont help if they leave out a good portion of computer users.
Hey it was open source software users who got firefox this far, they cant take a lesson?

---

### Post by Shpongle on 2009-11-14
> **SunnyRabbiera said:**
> Yeh but chromium is like a version behind and not really intended to be a regular browser.
And how much bloody market share they want, it wont help if they leave out a good portion of computer users.
Hey it was open source software users who got firefox this far, they cant take a lesson?

yea good point , but im sure google knows what theyre doing!!

---

### Post by The Real Dave on 2009-11-14
And onto my webpage doth go that banner :) 

IE sucks, its as slow as sh*t. Firefox is my personal favourite, and most of my friends/family use Firefox. Alot use Chrome too, for its simpler interface :) Personally, I can't imaging anything faster than Firefox :)

EDIT- Think I'm actually gonna make an image map of a banner similar to yours, so that people can click the Firefox Icon, and be taken to the download page :)

---

### Post by Ray() on 2009-11-14
I couldn't agree more. But the thing is that most people who use IE absolutely don't care about their browser nor do they want to know anything about other browsers. If you tell them that IE sucks and give them many true but complicated and technical reasons they just don't care. All they want is something simple and easy to use to access the web. In my view the only way this could be changed is either by Windows not using IE as a default browser (never gonna happen unless microsoft buys mozilla or something like that), a strong advertising campaign about another browser (chrome - probably the only solution right now) or another negative advertising campaign about IE which would tell people how horrible and dangerous it is to use IE (microsoft will never let that happen).... so there you have it. 

I mean it's nice to shout how horrible and stupid IE is but the people that will listen don't use IE and never used it anyways so they will agree but it won't change much. Others who have IE simply won't listen because most of the time it's absolutely not important to them and they don't want to loose time by installing another browser what they a) don't know how to do and b) wouldn't know how to use, didn't like the new UI and probably went back to IE after a while. I've seen this many times. Some people are just glad they can do something on the computer and the fact that they would change something so fundamental like "the internet" as they call internet explorer :-D is just a scary thought for them.

---

### Post by pwnst*r on 2009-11-14
> **The Real Dave said:**
>  Alot use Chrome too, for its simpler interface :) Personally, I can't imaging anything faster than Firefox :)

i'm going to bite my tongue to prevent a browser war.

OP: i think it's a good initiative, so great post.

---

### Post by The Real Dave on 2009-11-14
> **pwnst*r said:**
> i'm going to bite my tongue to prevent a browser war.

OP: i think it's a good initiative, so great post.

Lol, it is for me anyway :) I no other people find Chrome to be faster, and on startup yes, it is, but for me, in operation, Firefox wins :)

---

### Post by NoaHall on 2009-11-14
I'm not in on this. I'm not going to frustrate my customers.

---

### Post by StarLab on 2009-11-14
I've been dabbling in web development for over 12 years. From day one IE has always been a pain to design for. 

Granted, IE8 seems to be best of the series so far when it comes to rendering pages, but it's still not perfect. 

It's not so much the users of IE that bother me (as a web developer) but users who run IE5.5 or IE6 and refuse to upgrade. It's even worse when a new website client runs one of these versions. Trying to find a good balance for the client and the rest of the world is tricky at best. 

Personally, I've given up on polishing sites for users of these older browsers. If they can't be bothered to upgrade, then I can't be bothered to design for them. Besides, they are likely well used to sites not working quite as expected. I'm sure they come across them all the time.

---

### Post by beercz on 2009-11-14
I think it's up to the users to use what they want.  After all we all drive different cars of different standards (simple example are the wiper and indicator stalks are a different on different car models).

I am a web application developer (amongst other things) - and I have to adapt my code accordingly.

Like it or not IE is out there, an awful lot of people use it, so, write your code accordingly!

Having said all of this, it would be helpful if IE was W3C compliant - but it isn't, so we have to live with it.

---

### Post by The Funkbomb on 2009-11-14
You're not going to get rid of IE.  No way, no how.  It's one of life's necessary evils.

---

### Post by Paqman on 2009-11-14
> **beercz said:**
> 
Having said all of this, it would be helpful if IE was W3C compliant - but it isn't, so we have to live with it.

It's a chicken/egg problem. Microsoft have no incentive to make their browser work as long as designers/developers are hacking their sites to make them work OK on IE. But not including the IE hacks when IE has a biggest market share is commercial suicide.

We're stuffed, really.

---

### Post by dragos240 on 2009-11-14
This works too:
[http://www.devin.com/ieblock_howto.shtml](http://www.devin.com/ieblock_howto.shtml)

---

### Post by The Funkbomb on 2009-11-14
Blocking IE from your site will not get rid of it from the web.  I can guarantee there is nothing so important on your site that people are going to switch browsers just to see what your site has to say.

Plus, there are people who can't switch.  A lot of IT departments get REALLY mad when you install any software on their computers.

---

### Post by NightwishFan on 2009-11-14
I use Firefox, but that is mainly because it is the first browser that actually worked for me. IE was intensly slow on 128mb RAM Windows XP. I dislike Chrome and Safari, but I like and use Konqueror and Epiphany. I prefer Gecko over Webkit.

Down with Trident, may we never hear the internet refered to as the E ever again.

---

### Post by Frak on 2009-11-14
When I do commercial projects, I don't have a choice. Nowadays, I can at least opt for [Chrome Frame]("http://code.google.com/chrome/chromeframe/") if I reeeaaaallly need it.

Other than that, I use [SevenUP]("http://code.google.com/p/sevenup/").

---

### Post by supermelon928 on 2009-11-14
[FONT="Courier New"]In a world without walls or fences, who needs Gates or Windows?

I agree IE sucks, but I'd say the wheels are already turning for Chrome to destroy it.

[/FONT]

---

### Post by LepeKaname on 2009-11-15
> **StarLab said:**
> If they can't be bothered to upgrade, then I can't be bothered to design for them.

Exactly! that is how it should work! We (developers) should not care about those who don't care about what we have to say. 

> **Funkbomb said:**
> Blocking IE from your site will not get rid of it from the web.

I totally agree! We must not block IE!, just we should treat it as it is: a very basic browser.

> **Ray said:**
> But the thing is that most people who use IE absolutely don't care about their browser nor do they want to know anything about other browsers. If you tell them that IE sucks and give them many true but complicated and technical reasons they just don't care.


Here is where we can do some difference. Let's be creative! for example, show a small image of how your site would look without IE and prepare a basic design for IE users. 

Last month I made a FAQ system. It is not a big deal but it was designed with a nice looking and easy to use interface. It doesn't work in IE6 (of course) and some bugs in IE8. So, I decided to add a button that says: "ADVANCED mode", available only for IE users. When they click in it, I show them a message, that IE may present some problems and that I recommend them to use a BETTER browser (Firefox, Chrome, Opera, Safari, etc.), and I ask them: "do you want to continue anyway?".
So if they really need to do things fast, they would need to change at some point.

> **Paqman said:**
> It's a chicken/egg problem. Microsoft have no incentive to make their browser work as long as designers/developers are hacking their sites to make them work OK on IE. But not including the IE hacks when IE has a biggest market share is commercial suicide.
> **beercz said:**
> Having said all of this, it would be helpful if IE was W3C compliant - but it isn't, so we have to live with it.

Yes paqman, that is the problem, and sorry beercz, but no... we don't have to live with it... and that's the point with this post. I think we (developers) have the power to reduce the number of IE users. We don't need to take it completely out, but just to loose its privileged #1 place. If IE could become #2, then you would have a very important reason to create your sites for W3C complaint browsers. Then your boss will support you.

Last week I finished a system for a big corporation in Japan (with more than 300 branches). They want me to enable support for IE6 (as all those branches uses IE6) but, I'm pushing hard to let them know why I want to drop support for that browser. The result is coming soon, but based in the last talks, they will agree. I'm including a BIG banner  (attached in this message) to suggest to upgrade to use any other browser or to upgrade to IE8. Of course I want them to use Firefox if possible. If I succeed, 300+ offices may change browser in less than one week. This is how we can make the difference!

> **Frak said:**
> Other than that, I use SevenUP.
I like the Google Chrome Frame approach for systems. SevenUP may be better for public sites (I think).

> **supermelon928 said:**
> I agree IE sucks, but I'd say the wheels are already turning for Chrome to destroy it.

We really hope so! cross your fingers! ;)

---

### Post by beercz on 2009-11-15
> **LepeKaname said:**
> ..... sorry beercz, but no... we don't have to live with it... and that's the point with this post. I think we (developers) have the power to reduce the number of IE users. We don't need to take it completely out, but just to loose its privileged #1 place. If IE could become #2, then you would have a very important reason to create your sites for W3C complaint browsers. Then your boss will support you.

First of all, I don't have a boss (I work for myself), just customers.

In the real world, it's my customers who pay my wages.  If they want to use IE (that came supplied with their windows machines) then so bit it!  I haven't got the time, patience or money to get all my customers (and in turn their customers if it's an e-commerce site for example) to switch to another browser.

Having my customers' sites not working for their customers because of a dogma to force them (my customers' customers) to use another browser (ie switch from IE) because I hadn't bothered writing code to work round IE's flaws is a no-no - my customers will take their business elsewhere! They (my customers) don't want to hassle their own customers visiting their site suggesting that "you should change your browser" as their customers will take their business elsewhere.

I don't think Amazon, for example, suggests users change their browser to use their site (at least last time I looked).

I bet there are 1,000s of other developers around the globe in a similar position.

And that's the rub.  As much as I, or you or anyone else doesn't like it, and it may be right or it may be wrong - it makes no difference - that's the way it is.  Therefore we have to live with it - at least for the time being.

---

### Post by sledge73 on 2009-11-15
Could you imagine Firefox or something similar being the default browser for windows????

I would love to remove every image of that little blue E from the entire net, but then again how would non-linux or non-oss people figure out how to check their Email??

It's just too bad that the annoying E introduced the world to the web!!

---

### Post by Tipped OuT on 2009-11-15
> **beercz said:**
> First of all, I don't have a boss (I work for myself), just customers.

In the real world, it's my customers who pay my wages.  If they want to use IE (that came supplied with their windows machines) then so bit it!  I haven't got the time, patience or money to get all my customers (and in turn their customers if it's an e-commerce site for example) to switch to another browser.

Having my my customers' sites not working for their customers because of a dogma to force them (my customers' customers) to use another browser (ie switch from IE) because I hadn't bothered writing code to work round IE's flaws is a no-no - my customers will take their business elsewhere!  I bet there are 1,000s of other developers around the globe in a similar position.

And that's the rub.  As much as I, or you or anyone else doesn't like it, that's the way it is.  Therefore we have to live with it - at least for the time being.

Well said beercz, well said.

---

### Post by Frak on 2009-11-15
> **beercz said:**
> First of all, I don't have a boss (I work for myself), just customers.

In the real world, it's my customers who pay my wages.  If they want to use IE (that came supplied with their windows machines) then so bit it!  I haven't got the time, patience or money to get all my customers (and in turn their customers if it's an e-commerce site for example) to switch to another browser.

Having my my customers' sites not working for their customers because of a dogma to force them (my customers' customers) to use another browser (ie switch from IE) because I hadn't bothered writing code to work round IE's flaws is a no-no - my customers will take their business elsewhere! They (my customers) don't want to hassle their own customers visiting their site saying you "must change your browser" as their customers will take their business elsewhere.

Amazon for example doesn't suggest users change their browser to use their site.

I bet there are 1,000s of other developers around the globe in a similar position.

And that's the rub.  As much as I, or you or anyone else doesn't like it, and it may be right or it may be wrong - it makes no difference - that's the way it is.  Therefore we have to live with it - at least for the time being.
Absolutely. It is the designers job to complete the clients job to the fullest degree possible. I am in that situation in just about every job I get.

---

### Post by beercz on 2009-11-15
I must admit, I am getting rather fed up with all the Microsoft bashing that seems to go on in these forums.

---

### Post by Frak on 2009-11-15
> **beercz said:**
> I must admit, I am getting rather fed up with all the Microsoft bashing that seems to go on in these forums.
You see where I'm coming from now?

---

### Post by starcannon on 2009-11-15
*grumble*

---

### Post by Dharmachakra on 2009-11-15
Hmm... from what I've heard, Explorer is becoming more standards compliant with each new version. I'm not an expert so I'll leave some of you guys to confirm or deny that.

But this idea of blocking IE from accessing websites... that's probably the lamest thing I've ever heard.

---

### Post by Tipped OuT on 2009-11-15
> **beercz said:**
> I must admit, I am getting rather fed up with all the Microsoft bashing that seems to go on in these forums.

Yeah, you should see what happens when I post a Windows 7 screenshot. :lolflag:

---

### Post by The Funkbomb on 2009-11-15
> **Dharmachakra said:**
> Hmm... from what I've heard, Explorer is becoming more standards compliant with each new version. I'm not an expert so I'll leave some of you guys to confirm or deny that.

But this idea of blocking IE from accessing websites... that's probably the lamest thing I've ever heard.

I don't know if this is true but "more standards compliant" is unacceptable.  They're the most used browser in the world.  They're not new to the internet and it's not like the people behind it are slackjawed idiots.

If a majority does not abide by the standards, then you have to question what the standards really are.  This isn't just against microsoft, it's against anyone.

---

### Post by LepeKaname on 2009-11-15
> **beercz said:**
> In the real world, it's my customers who pay my wages.  If they want to use IE (that came supplied with their windows machines) then so bit it!  I haven't got the time, patience or money to get all my customers (and in turn their customers if it's an e-commerce site for example) to switch to another browser.

I have been there so many times that I just don't want to continue all my life in the same situation... I rather change of career... 

Because we tweak the codes so it "works" in IE, then the customers are happy... (and all people think IE is great! ) but if there is a bug is our problem and we then need to spend hours trying to fix it, or dropping the idea and implement it different (so much time wasted! ). 

If the customer wants round corners here and there, resize elements, drag and drop capabilities, and advanced stuff that IE6 wont like, what do you do? If you say... "sorry I can't", they will think you are not capable to do it, or if you say: "sorry IE6 does not support this and that... if you want to have that, use other browser", they will think you are not capable to do it for IE (because IE is great! ). The final result: basic stuff only. 

So I have the feeling that IE is pushing many people's effort back (I mean all the people involved in SVG web projects, HTML5 and CSS3 specifications, etc). It doesn't make any sense to me to spend hours in order to use round corners or transparent PNG's (just as a common example)... unless they are paying you also that precious time.

We are the developers here, we are the ones who know this stuff, we are the professionals, the experts. We are suppose to make recommendations to our customers, not just to do what they want even it does not make any sense. But of course, they are paying... they have the power. That is how Microsoft works. That is how this world works...

The whole point is... if we can help to move IE to be #2, then we can say to our customers: "wait... this browser is #1, we don't care about that #2", or something similar... even it doesn't make so much sense. That is the main reason we are still developing for IE... because everyone knows that IE is the most important client.

A small note at the bottom of the page like: "your browser is outdated, please change it" will not harm anyone, not even your customers. Remember there are so many sites that said: "IE only", "Best view with IE", and some don't let you continue, or are completely useless with any other browser (because are done with MS products). 

Get some ideas, take notes and talk to your customers... anything could help.

---

### Post by LepeKaname on 2009-11-15
> **Dharmachakra said:**
> Hmm... from what I've heard, Explorer is becoming more standards compliant with each new version. I'm not an expert so I'll leave some of you guys to confirm or deny that.

But this idea of blocking IE from accessing websites... that's probably the lamest thing I've ever heard.

Check the Acid3 Test here: [http://en.wikipedia.org/wiki/Acid3](http://en.wikipedia.org/wiki/Acid3)

You can see how "standard" is IE8.

IE8 has just mostly implemented CSS 2.1 Where Opera has almost finished implementing the not-yet released CSS3.

IE DOM support is awful!

No, blocking IE from websites is not a good thing to do. A minor warning is enough.

---

### Post by pwnst*r on 2009-11-15
> **Tipped OuT said:**
> Yeah, you should see what happens when I post a Windows 7 screenshot. :lolflag:

lol, i noticed

---

### Post by witeshark17 on 2009-11-15
Very cool idea! I hope it works!

---

### Post by pwnst*r on 2009-11-15
> **witeshark17 said:**
> Very cool idea! I hope it works!

it won't.

---

### Post by The Funkbomb on 2009-11-15
Once we accomplish this, let's work on getting all the trolls off of youtube. :P

For the record, windows 7 is pretty good.

---

### Post by Tipped OuT on 2009-11-15
> **The Funkbomb said:**
> Once we accomplish this, let's work on getting all the trolls off of youtube. :P

If you do that, then there won't be anymore YouTuber's. ;)

---

### Post by starcannon on 2009-11-15
> **tipped out said:**
> if you do that, then there won't be anymore youtuber's. ;)
+1
[[IMG]http://img200.imageshack.us/img200/7563/youtroll.th.jpg[/IMG]](http://img200.imageshack.us/i/youtroll.jpg/)

---

### Post by LepeKaname on 2009-11-16
Something from: [http://www.jankoatwarpspeed.com/](http://www.jankoatwarpspeed.com/)

> Code is tested in Firefox, Safari and IE7. If this doesn't work in IE6, I simply [don't care]("http://www.jankoatwarpspeed.com/post/2009/02/26/Grow-up-already-and-throw-IE6-away!.aspx"). 

Which points to: [http://www.jankoatwarpspeed.com/post/2009/02/26/Grow-up-already-and-throw-IE6-away!.aspx](http://www.jankoatwarpspeed.com/post/2009/02/26/Grow-up-already-and-throw-IE6-away!.aspx)

Very good BTW!

---

### Post by Paqman on 2009-11-16
> **beercz said:**
> I must admit, I am getting rather fed up with all the Microsoft bashing that seems to go on in these forums.

Bashing one Microsoft product for specific technical reasons is not Microsoft bashing.

Bashing Microsoft for their reluctance to adhere to the web standards is, but it's a constructive and (IMO) valid bashing. If people were posting a lot of stupid "Y4h! Macro$ux b00!" posts, then fair enough. But what I see is a bunch of knowledgeable pros discussing an actual issue (inflammatory thread title notwithstanding...)

---

### Post by Dullstar on 2009-11-16
I have reasons to bash Microsoft, but only 40% is technical now.

---

### Post by beercz on 2009-11-16
> **Paqman said:**
> Bashing one Microsoft product for specific technical reasons is not Microsoft bashing.

Bashing Microsoft for their reluctance to adhere to the web standards is, but it's a constructive and (IMO) valid bashing. If people were posting a lot of stupid "Y4h! Macro$ux b00!" posts, then fair enough. But what I see is a bunch of knowledgeable pros discussing an actual issue (inflammatory thread title notwithstanding...)
Hmmm.  So "IE Sucks" is ok because it's a valid technical reason then.

---

### Post by beercz on 2009-11-16
> **LepeKaname said:**
> I have been there so many times that I just don't want to continue all my life in the same situation... I rather change of career... 

Because we tweak the codes so it "works" in IE, then the customers are happy... (and all people think IE is great! ) but if there is a bug is our problem and we then need to spend hours trying to fix it, or dropping the idea and implement it different (so much time wasted! ). 

If the customer wants round corners here and there, resize elements, drag and drop capabilities, and advanced stuff that IE6 wont like, what do you do? If you say... "sorry I can't", they will think you are not capable to do it, or if you say: "sorry IE6 does not support this and that... if you want to have that, use other browser", they will think you are not capable to do it for IE (because IE is great! ). The final result: basic stuff only. 

So I have the feeling that IE is pushing many people's effort back (I mean all the people involved in SVG web projects, HTML5 and CSS3 specifications, etc). It doesn't make any sense to me to spend hours in order to use round corners or transparent PNG's (just as a common example)... unless they are paying you also that precious time.

We are the developers here, we are the ones who know this stuff, we are the professionals, the experts. We are suppose to make recommendations to our customers, not just to do what they want even it does not make any sense. But of course, they are paying... they have the power. That is how Microsoft works. That is how this world works...

The whole point is... if we can help to move IE to be #2, then we can say to our customers: "wait... this browser is #1, we don't care about that #2", or something similar... even it doesn't make so much sense. That is the main reason we are still developing for IE... because everyone knows that IE is the most important client.

A small note at the bottom of the page like: "your browser is outdated, please change it" will not harm anyone, not even your customers. Remember there are so many sites that said: "IE only", "Best view with IE", and some don't let you continue, or are completely useless with any other browser (because are done with MS products). 

Get some ideas, take notes and talk to your customers... anything could help.
This is all very well, but at the end of the day my point still stands - like it or not we have to live with Internet Explorer.  Just write browser agnostic code where possible.  If you can get people like Amazon, NASA, BBC etc. to get them to write their sites to persuade their users to change their browser then I might make the effort.  Until then I will do what these sites do - write their sites so that they will run in any browser, they don't really care which browser the end user uses, as long as their sites work.  If it's good enough for the likes of Amazon, NASA, BBC et. al. it's good enough for me!!

PS Do people still use IE6?

---

### Post by Frak on 2009-11-16
> **beercz said:**
> This is all very well, but at the end of the day my point still stands - like it or not we have to live with Internet Explorer.  Just write browser agnostic code where possible.  If you can get people like Amazon, NASA, BBC etc. to get them to write their sites to persuade their users to change their browser then I might make the effort.  Until then I will do what these sites do - write their sites so that they will run in any browser, they don't really care which browser the end user uses, as long as their sites work.  If it's good enough for the likes of Amazon, NASA, BBC et. al. it's good enough for me!!

PS Do people still use IE6?
It's more about resetting your styles down to the bare minimum. There are quirks with IE6. At the time, they really didn't matter. Now, it does. One such is the clearfix bug, another is the png handling, and others like the click-through div.

Yes, people still use IE6.

---

### Post by squilookle on 2009-11-16
The company I work for uses IE6 and are not going to change any time soon. I have to take this into account with everything I write, and I'm used to it. 

I agree that for the time being IE is a necessary evil that we have to live with, and I'm not sure if it will be Firefox or Chrome or anything else that overtakes IE. 

I believe the market share of IE will decline naturally and I believe there are three factors that are going to bring this about: 

1. People changing their OS and using either different browsers, or atleast updated versions of IE if they buy a new computer with newer version of Windows and IE installed. Linux Netbooks and Chrome OS may help. 

2. Reviews of alternative browsers on mainstream media such as the BBC: telling people about the benefits of the other browsers (and not telling people that by using IE they are doing something wrong or stupid). Coverage of alternative software on the BBC is improving: I remember as recently as one to two years ago being annoyed there was only coverage of Microsoft and Apple on there. I have recently seen articles on Ubuntu and Linux Mint on there, as well as articles on Firefox, Chrome and Chrome OS.

3. People being introduced to other browsers on devices where Microsoft do not dominate. From my own experience, I have a Wii with the Internet Channel (which states it is "Powered by Opera") and an Android Phone with its webKit browser. I suppose the iPhone and Safari may have the same effect. I'm not saying people are going to go and download the browsers for their PC straight away, but it may make people AWARE that there are other browsers out there, or make them recognise the names and logos of the other browsers when they see them about. Instead of disregarding them, in time, they might read a good review and give it a try.

---

### Post by LepeKaname on 2009-11-16
> **beercz said:**
> This is all very well, but at the end of the day my point still stands - like it or not we have to live with Internet Explorer.  Just write browser agnostic code where possible.  If you can get people like Amazon, NASA, BBC etc. to get them to write their sites to persuade their users to change their browser then I might make the effort.  Until then I will do what these sites do - write their sites so that they will run in any browser, they don't really care which browser the end user uses, as long as their sites work.  If it's good enough for the likes of Amazon, NASA, BBC et. al. it's good enough for me!!

PS Do people still use IE6?

I just feel its unfair for all those people (the people involved in developing good browsers, the W3C specifications and in general any new web technology) that are working hard to make OUR job easily, that we just sit there and wait. 

Many of these new technology can not be used only because IE does not support it. Its a shame.

It seems that IE is loosing its power, but we know the MS marketing, so it could increase again. I wish we could do something to prevent that to happen.

At the end we are free to do what ever we think its the best in our own situation, but I'm just asking to try.

Have a nice day.

---

### Post by LepeKaname on 2009-11-16
> **squilookle said:**
> 1. People changing their OS and using either different browsers, or atleast updated versions of IE if they buy a new computer with newer version of Windows and IE installed. Linux Netbooks and Chrome OS may help. 

2. Reviews of alternative browsers on mainstream media such as the BBC: telling people about the benefits of the other browsers (and not telling people that by using IE they are doing something wrong or stupid). Coverage of alternative software on the BBC is improving: I remember as recently as one to two years ago being annoyed there was only coverage of Microsoft and Apple on there. I have recently seen articles on Ubuntu and Linux Mint on there, as well as articles on Firefox, Chrome and Chrome OS.

3. People being introduced to other browsers on devices where Microsoft do not dominate. From my own experience, I have a Wii with the Internet Channel (which states it is "Powered by Opera") and an Android Phone with its webKit browser. I suppose the iPhone and Safari may have the same effect. I'm not saying people are going to go and download the browsers for their PC straight away, but it may make people AWARE that there are other browsers out there, or make them recognise the names and logos of the other browsers when they see them about. Instead of disregarding them, in time, they might read a good review and give it a try.

I agree. Mainly the "portable" browsers, which is very good that MS is not dominating there.

Can you post the URL of a good BBC article about alternative browsers you have read? 

Thank you.

---

### Post by -grubby on 2009-11-16
[img]http://www.geekstir.com/wp-content/uploads/2009/06/ie6comic2.jpg[/img]

---

### Post by beercz on 2009-11-16
> **LepeKaname said:**
> I just feel its unfair for all those people (the people involved in developing good browsers, the W3C specifications and in general any new web technology) that are working hard to make OUR job easily, that we just sit there and wait. 

Many of these new technology can not be used only because IE does not support it. Its a shame.

It seems that IE is loosing its power, but we know the MS marketing, so it could increase again. I wish we could do something to prevent that to happen.

At the end we are free to do what ever we think its the best in our own situation, but I'm just asking to try.

Have a nice day.
Yes, I think you are right, it is unfair, and makes it damned awkward for us developers.  That's life I suppose, and I along with many others, would like the situation to change, and it is - slowly - I think we have the almighty powerful Google to thank for that.  I think Microsoft seem to be worried by Google.

---

### Post by Praxicoide on 2009-11-16
I fully support putting an imperfect browser notice on webpages for users of IE. If it were to theoretically catch on, MS might have to accept that it doesn't comply with certain standards and do something about it.

---

### Post by squilookle on 2009-11-16
> **LepeKaname said:**
> I agree. Mainly the "portable" browsers, which is very good that MS is not dominating there.

Can you post the URL of a good BBC article about alternative browsers you have read? 

Thank you.

Heres a few in no particular order, I think there are alot more on there - probably some critical ones too:

[http://http://news.bbc.co.uk/1/hi/technology/8177829.stm]("http://http//news.bbc.co.uk/1/hi/technology/8177829.stm")
[http://http://news.bbc.co.uk/1/hi/technology/7456151.stm]("http://http//news.bbc.co.uk/1/hi/technology/7456151.stm")
[http://http://news.bbc.co.uk/1/hi/8231184.stm]("http://http//news.bbc.co.uk/1/hi/8231184.stm")

---

### Post by MiCK.ca on 2009-11-16
I second the IE sucks motion! As far as the movement to rid the web of IE is for other browsers like Opera, Chrome and Firefox themselves to start pressuring Banks, Ticket buying agencies (ticketmaster etc) to start opening the doors the more "standard coding". 

Microsoft unfortunately has helped develop a web that is non-standard and because most of the world is MS...the web sucks because of it. Microsoft seems to always come up with something exclusive to their platform, everyone  (web developers) jump on that bandwagon and the ball just keeps rolling on.

---

### Post by Eagles18 on 2009-11-16
IE,indeed, does suck.
LOL @ picture.

---

### Post by chillicampari on 2009-11-16
When I see a browser notice on a page I think of the old Geocities era. :p

I just shoot for something that works and doesn't degrade too poorly on non-target (non-major) browsers nowawdays. Most people (general public) visiting a non-technically oriented site aren't going to care about the specifics of Acid 3 results (however, they will notice if something looks "broken on their web").

---

### Post by LepeKaname on 2009-11-16
> **squilookle said:**
> Heres a few in no particular order, I think there are alot more on there - probably some critical ones too:

[http://news.bbc.co.uk/1/hi/technology/8177829.stm]("http://news.bbc.co.uk/1/hi/technology/8177829.stm")
[http://news.bbc.co.uk/1/hi/technology/7456151.stm]("http://news.bbc.co.uk/1/hi/technology/7456151.stm")
[http://news.bbc.co.uk/1/hi/8231184.stm]("http://news.bbc.co.uk/1/hi/8231184.stm")

Thank you squilookle for the links (however "http" was duplicated).

From the first link:

> Microsoft is currently in talks with the European competition regulators, which ruled in January that pre-bundling Internet Explorer with the company's Windows operating system hurt competition.

The firm recently made a proposal that would offer European buyers of its new Windows 7 operating system a list of potential browsers when they first install the software. 

I hope they do it, and not just in Europe. 

From the last link: 

> Sony personal computers are now available with Google's Chrome internet browser following a deal struck between the two technology giants this summer.

These are really good news!


BTW. We just updated a computer from IE6 to IE8 (with Firefox in it) and Firefox stopped to work (crash frequently). However it do not happen with IE7. Something interesting is that when you install IE8 it display a dialog to import your bookmarks from Firefox!! first time I see that.

---

### Post by supermelon928 on 2009-11-17
> **beercz said:**
> Hmmm.  So "IE Sucks" is ok because it's a valid technical reason then.

see:

> **Paqman said:**
> (inflammatory thread title notwithstanding...)

---

### Post by neojames on 2009-11-17
> **Dharmachakra said:**
> Hmm... from what I've heard, Explorer is becoming more standards compliant with each new version. I'm not an expert so I'll leave some of you guys to confirm or deny that.

But this idea of blocking IE from accessing websites... that's probably the lamest thing I've ever heard.

While it is becoming more standards complaint, it's to the standards that all the other browsers adopted years ago. When i'm doing transparency I want to use rgba but thats HTML5 only so I cant on IE. Awhile ago I was helping out on a forum for a evony aliance and we needed a transparent bg. I wrote a fix in seconds but it took me days to get it working in IE.

---

### Post by NightwishFan on 2009-11-17
Competition is good for progress. I doubt IE would have even made this much progress if it did not have to.

---

### Post by RabbitWho on 2009-11-17
I remember the first time I installed Firefox on our computer my mom freaked out because she couldn't connect to the internet.. somehow having a different icon and name made her think that she no long had to go through the normal dial up procedure.. and when she clicked on the browser and didn't connect to the internet (we had a dial up connection) she got annoyed.. it didn't make any sense.. I had to sit down with her and show her how to do the same thing she'd already done 100 times.. first you click on the Eircom (telecom company) icon to connect to the internet.. then you click on the browser... 

In the future no one will use IE. It's just some people are very confused by change and by computers in general. It took my mom weeks to get the hang of maximizing and minimizing. She's only in her 40s!

(i should mention in the interest of balance: Dad is worse.)

---

### Post by pwnst*r on 2009-11-17
> **RabbitWho said:**
> 
In the future no one will use IE. 

lol

---

### Post by Frak on 2009-11-17
> **pwnst*r said:**
> lol
Also lol'd

---

### Post by NightwishFan on 2009-11-17
Almost everyone I know uses Firefox. My friend's mom used Firefox almost a year longer than I did. (Back in Xp days, I used IE.)

So lol.

---

### Post by pwnst*r on 2009-11-17
> **NightwishFan said:**
> Almost everyone I know uses Firefox. My friend's mom used Firefox almost a year longer than I did. (Back in Xp days, I used IE.)

So lol.

almost everyone you know = lol.

---

### Post by koleoptero on 2009-11-17
> **Tipped OuT said:**
> Yeah, you should see what happens when I post a Windows 7 screenshot. :lolflag:
:tongue:

---

### Post by NightwishFan on 2009-11-17
One man, and I know a LOT of everyday people who use computers. ;)

No more lol because it gives me a headache. I say enjoy whatever browser you will, and good day sirs.

---

### Post by blur xc on 2009-11-17
> **starcannon said:**
> +1
[[IMG]http://img200.imageshack.us/img200/7563/youtroll.th.jpg[/IMG]]("http://img200.imageshack.us/i/youtroll.jpg/")

BroadcASSt Yourself?

anyway, I actually did the acid3 test in ie8 and ff3.5.5 on my win xp machine, and I have to say, I was amused by the results.

BM

---

### Post by pwnst*r on 2009-11-17
> **NightwishFan said:**
> One man, and I know a LOT of everyday people who use computers. ;)

No more lol because it gives me a headache. I say enjoy whatever browser you will, and good day sirs.

you're living in dreamland. as long as the general public is using windows, they'll continue to use IE.  it'll never go away in your lifetime.

---

### Post by Frak on 2009-11-17
> **pwnst*r said:**
> you're living in dreamland. as long as the general public is using windows, they'll continue to use IE.  it'll never go away in your lifetime.
This.

It's also a very surprising thing that a lot of Mac users use Safari and a lot of Ubuntu users use Firefox. It may be out of choice, but I think we'll never know the true cause...

---

### Post by blur xc on 2009-11-17
I'll admit that I have not read every word of every post- but could Google, not necessarily the Chrome browser, but Google itself, but a hurt on IE?  As much as I don't like it, I'm pretty certain that cloud computing will only get more and more popular, and Google is already in the lead on that front, w/ Google docs and office applications...  As Google Chrome OS picks up steam, which I think will happen, as big as Google is, could Google start limiting efforts to make their cloud apps work 100% perfect w/ IE?  Kind of like how MS killed Wordperfect, but not giving the Wordperfect developers complete access to the dos api, making their product more buggy than MS Word.  Either MS would have to adopt standards (Oh- the horror), or get passed up by browsers that do.

BM

---

### Post by LepeKaname on 2009-11-17
> **blur xc said:**
> I actually did the acid3 test in ie8 and ff3.5.5 on my win xp machine, and I have to say, I was amused by the results.

Yes, this is one of "my ace up my sleeve" when trying to convince someone that IE is a total fail.

Yesterday, my Wife (She is a language teacher) asked her "older" (50+ years old) students of which browser they used, for example, IE, Firefox, etc... One of them said: "NTT"... :confused: (NTT is the ISP company), after explaining him, the "blue e" came up. She commented about Firefox and it seems all of them (around 20) will try it this week (that was the homework ;) )...hehe

Yesterday I found some thread similar to this one, so excuse me if I post here some of those comments, but I think they are really interesting for this matter.

This one is funny:  [http://www.saveie6.com/](http://www.saveie6.com/)

> I went to the career center in Bangor Maine a few months ago and the woman giving a presentation was using IE6 on a Windows 98 to show us what interweb site pages would help us find a job. It made me dumber just being there. I asked her why she doesn't use firefox, she says... What's a.. what's firefox? I actually wanted to do a facepalm right there, but out of respect I told her it was a more secure browser than IE6.
This woman didn't understand the difference between the internet and a browser. I would have to sit her down and give her a class on computers for her to grasp it. As far as she knew, "the internet" was something that happens when you click the blue "E" button

> When my sister was 6, she associated "the internet" with the blue 'e'. Now she is 9, and uses Firefox on GNU/Linux. Some people should just grow up. ;)


> As a web developer, i charge an extra 25% - 50% for total compatibility with IE6. i will make it look half decent if i feel like it but if you want it perfect you have to give me extra money for alcohol and for the things i break in my office due to the ***** that is IE... :)


> Still using IE6 is caused by 1 of 2 things: Ignorance (end-users), laziness (IT staff) and nothing more. Stop hobbling your site by using the IE6 workarounds. Let the page be broken in IE6 or just give them a redirect page.


> IE6 does not support web standards. If it's not working for you, then it really is Microsoft's problem and *not* the web developers. You don't design web pages for specific browsers. The web was designed to get away from proprietary platforms, not embrace multiple incompatible platforms. We may as well go back to distributing binary software with that attitude of portability...


> IE6, IE7, and IE8 combined are steadily losing share to Firefox and Chrome. IE6 is the oldest of the three and is used by < 15% of all users according to W3C (or < 13% according to Wikipedia). I wouldn't say that IE6 "needs to die," I would say that it's already dead. If you're a web developer, just detect IE6 and display a "please upgrade" message, just like Facebook does. Or just let the page display incorrectly. That 13% will just upgrade that much faster when the pages they view are broken.


> With the continual problems with IE8, one of which included blocking me from accessing a university login to download tech class lectures, I finally threw in the towel and moved to FireFox as my main browser. I don't see IE8 as progress -- unless regularly having to restart and having your browser control your access is what you are looking for.

>Firefox, which I'd used a bit before, has been great. Thanks MS, I would never have made the transition had you not produced such a backwards product as IE8.

> ignore IE6 with one line of text:  getfirefox.com

References: 
[http://digg.com/tech_news/IE6_Must_Die_for_the_Web_to_Move_On](http://digg.com/tech_news/IE6_Must_Die_for_the_Web_to_Move_On)
[http://digg.com/tech_news/Microsoft_IE6_Cannot_Die](http://digg.com/tech_news/Microsoft_IE6_Cannot_Die)
[http://digg.com/tech_news/CRASH_IE6_with_one_line_of_code](http://digg.com/tech_news/CRASH_IE6_with_one_line_of_code)
[http://blogs.computerworld.com/heres_why_ie8_crashes](http://blogs.computerworld.com/heres_why_ie8_crashes)

---

### Post by NightwishFan on 2009-11-18
.

---

### Post by supermelon928 on 2009-11-18
Brothers, I say we use the power of open source to create a new Internet Explorer that is exactly the same but without all the bad things, and then we infiltrate Microsoft and replace their software with ours, and no one will ever know.

;)

---

### Post by t0p on 2009-11-18
> **beercz said:**
> 
PS Do people still use IE6?

You call yourself a web developer and still have to ask this question?  And to think I was trying to take your opinions seriously!

Jeez...

---

### Post by t0p on 2009-11-18
> **pwnst*r said:**
> you're living in dreamland. as long as the general public is using windows, they'll continue to use IE.  it'll never go away in your lifetime.

Well that is a silly comment, isn't it?  Let's be conservative and assume NightwishFan will live just another 50 years.  Do you really think the situation cannot change radically in that time?  Do you really think we'll be using web browsers in 50 years?  Do you think that networking technology will not have progressed far beyond the concept of a "World Wide Web" by then?

Think about what networking technology was like in 1959.  Now factor in the explosive progress we've experienced over the last couple of decades, and imagine what networking technology will be like in 2059.  Do you still think we'll be using IE?

Looking at things in the short term: The EU is putting Microsoft under serious pressure to stop bundling IE with its OSes.  I don't use 7, so I don't know if IE comes with it.  But if Microsoft is forced to stop bundling in the near future, Google Chrome will be a serious contender.  Now think about how many computer users there are in the EU.  An awful lot.

Right now, IE is *the* web browser.  In the near-future, that may change.  In the far-future, there might very well not even be a *web*, never mind web browsers.

---

### Post by neojames on 2009-11-18
On note, despite microsoft's promise to stop bundling IE, it still is on my fathers windows7 pc.

---

### Post by NoaHall on 2009-11-18
> **neojames said:**
> On note, despite microsoft's promise to stop bundling IE, it still is on my fathers windows7 pc.

I never did get that "choose your web browser" thing. I'm glad really, it might have deleted my settings/24 browsers I have installed.

---

### Post by pwnst*r on 2009-11-18
> **t0p said:**
> Well that is a silly comment, isn't it?  Let's be conservative and assume NightwishFan will live just another 50 years.  Do you really think the situation cannot change radically in that time?  Do you really think we'll be using web browsers in 50 years?  Do you think that networking technology will not have progressed far beyond the concept of a "World Wide Web" by then?

Think about what networking technology was like in 1959.  Now factor in the explosive progress we've experienced over the last couple of decades, and imagine what networking technology will be like in 2059.  Do you still think we'll be using IE?

Looking at things in the short term: The EU is putting Microsoft under serious pressure to stop bundling IE with its OSes.  I don't use 7, so I don't know if IE comes with it.  But if Microsoft is forced to stop bundling in the near future, Google Chrome will be a serious contender.  Now think about how many computer users there are in the EU.  An awful lot.

Right now, IE is *the* web browser.  In the near-future, that may change.  In the far-future, there might very well not even be a *web*, never mind web browsers.

not bundling it with it, is a bit silly.  i DO agree however that it shouldn't be HOOKED into the OS where it's almost impossible to remove completely.  again, near future, no. distant, maybe.

---

### Post by Frak on 2009-11-18
> **pwnst*r said:**
> not bundling it with it, is a bit silly.  i DO agree however that it shouldn't be HOOKED into the OS where it's almost impossible to remove completely.  again, near future, no. distant, maybe.
Which is why you are free to remove it. Though, watch any and all .NET applications that rely on embedded web instances to instantly fail. I'm looking at you, Steam.

---

### Post by xuCGC002 on 2009-11-18
> **LepeKaname said:**
> 
No, blocking IE from websites is not a good thing to do. A minor warning is enough.

This.

---

### Post by beercz on 2009-11-18
> **t0p said:**
> You call yourself a web developer and still have to ask this question?  And to think I was trying to take your opinions seriously!

Jeez...
It was tongue-in-cheek!!

Although I have to admit that I tend not to come across many IE6 users these days....

---

### Post by Tux.Ice on 2009-11-18
I take it to a personal level. I have done web development since 9, (14 now). I have a job as IT manager at a company in Toronto, Ontario. Anyway, I mandated Firefox/chrome on all computers connecting to the network. 

As it is an aviation maintenance company, many employees bring in personal computers such as laptops. We enforce a policy, that for security reasons, IE is not allowed to be used.

I also make a javascript alert to tell users to get rid of IE on any website I make.

---

### Post by SteveHillier on 2009-11-18
> **Penguin Guy said:**
> I think chrome is going to be the main browser soon, they have a lot more advertising power than firefox. The only way firefox beats chrome is it's addon/plugin system.

One, I hope not and
two, it doesn't work for everything.

I recently had to do some online work on a customer machine who had Chrome as the default browser.  It would allow you to fill in the form correctly but would not submit the form properly.  Had to revert to IE for this job.

From preference I use Firefox.  I agree with the OP but I don't see how we can shift behaviour.  Like Ray() said, most people just don't give a s... what browser they use because they are not techies like most of us and they outnumber us big time.

---

### Post by LepeKaname on 2009-11-18
> **supermelon928 said:**
> Brothers, I say we use the power of open source to create a new Internet Explorer that is exactly the same but without all the bad things, and then we infiltrate Microsoft and replace their software with ours, and no one will ever know.

That's a great idea! any volunteer? ;) Without going that far, just install firefox in your (mother, father, friend, etc.) computer. Then just use IE icon to start FF and set an IE theme for FF (like this one: [https://addons.mozilla.org/en-US/firefox/addon/4129](https://addons.mozilla.org/en-US/firefox/addon/4129)). I'm pretty sure most of the IE users will never notice the change (mainly those people that can't say the difference between a IE and Internet). 

> **Tux.Ice said:**
> I take it to a personal level. I have done web development since 9, (14 now). I have a job as IT manager at a company in Toronto, Ontario. Anyway, I mandated Firefox/chrome on all computers connecting to the network. 

As it is an aviation maintenance company, many employees bring in personal computers such as laptops. We enforce a policy, that for security reasons, IE is not allowed to be used.

I also make a javascript alert to tell users to get rid of IE on any website I make.

This is what I mean by taking some actions here. BTW are you 14 years old?

---

### Post by -grubby on 2009-11-18
> **Tux.Ice said:**
> I take it to a personal level. I have done web development since 9, (14 now). I have a job as IT manager at a company in Toronto, Ontario. Anyway, I mandated Firefox/chrome on all computers connecting to the network. 

As it is an aviation maintenance company, many employees bring in personal computers such as laptops. We enforce a policy, that for security reasons, IE is not allowed to be used.

I also make a javascript alert to tell users to get rid of IE on any website I make.

No you don't, no you don't, and no you don't!

---

### Post by phrostbyte on 2009-11-18
Microsoft announced IE9 today. Their announcement consisted of showing off a breakthrough new feature (rounded corners), failing the CSS selectors test, trash talking Acid 3 (calling it something that tests "working drafts", which is inaccurate), showing off that they are still last in JavaScript performance, claiming that no browsers do hardware acceleration (wtf)? Oh and blurring font rendering for the third time (when will they ever get it "right"?). And other shenanigans. No word if IE9 will support SVG, Canvas, or anything from the last century, including Windows XP. 

Ultimately, the web community was not impressed, as you can see by the commentary on the blog:

[http://blogs.msdn.com/ie/archive/2009/11/18/an-early-look-at-ie9-for-developers.aspx](http://blogs.msdn.com/ie/archive/2009/11/18/an-early-look-at-ie9-for-developers.aspx)

I think the consensus is everyone wants Microsoft to switch to Webkit. I wouldn't be surprised if they did it.

If not, maybe the EU will do the world a favor and force Microsoft to bundle Chrome Frame with IE9. :) Who knows.

---

### Post by Praxicoide on 2009-11-18
Hilarious! Sad too.

---

### Post by The Funkbomb on 2009-11-18
> **phrostbyte said:**
> Microsoft announced IE9 today. Their announcement consisted of showing off a breakthrough new feature (rounded corners), failing the CSS selectors test, trash talking Acid 3 (calling it something that tests "working drafts", which is inaccurate), showing off that they are still last in JavaScript performance, claiming that no browsers do hardware acceleration (wtf)? Oh and blurring font rendering for the third time (when will they ever get it "right"?). And other shenanigans. No word if IE9 will support SVG, Canvas, or anything from the last century, including Windows XP. 

Ultimately, the web community was not impressed, as you can see by the commentary on the blog:

[http://blogs.msdn.com/ie/archive/2009/11/18/an-early-look-at-ie9-for-developers.aspx](http://blogs.msdn.com/ie/archive/2009/11/18/an-early-look-at-ie9-for-developers.aspx)

I think the consensus is everyone wants Microsoft to switch to Webkit. I wouldn't be surprised if they did it.

If not, maybe the EU will do the world a favor and force Microsoft to bundle Chrome Frame with IE9. :) Who knows.

Sorta like how they blatantly lied about linux vs Win7?  lol

---

### Post by pwnst*r on 2009-11-18
> **-grubby said:**
> No you don't, no you don't, and no you don't!

lol

---

### Post by LepeKaname on 2009-11-18
**phrostbyte**, thank you for the link and the info!...

> IE and Microsoft rocks. Firefox and Open Source are pathetic losers.
> Now that we know IE9 is getting more advanced than other browsers (for now) when will we see IE9 in beta?
> IE9 is the beginning of the end of Firefox and Google Chrome.

LOL!!! more advanced??? how come? (Acid Test 30/100) ):P

Its good to see that not all people get impressed with those poor modifications (IMO).

---

### Post by LepeKaname on 2009-12-01
Just to add a possibly end note to this thread, I want to discuss 2 points:

1) I commented in my starting post that IE is used by a majority of public places like: Internet cafe, schools, libraries, etc.

One of the main reasons why this happen is that with the combination IE+Win they can restrict the users (in some cases), so they can't do anything else but browse the web.

Now with "Chrome OS", Google will start having a very good chance in those sectors. Just imagine, you go to an Internet cafe and login (in Chrome OS), as all your data is in the "cloud", those machines do not even require a HDD! This reduce some IE users worldwide :)

2) Let's face it, IE would never be on time with the W3C standards (because they can't or just don't care about it). We would have to support IE even it lacks of implementation of the most recent technology. I think MS would never leave "Trident" and IE would never adopt webkit or become OSS. So we have no so many options.

I came with an *idea* some time ago, which may sounds crazy, but it could work: 

I have heard some comments of people who defend IE and state that *"following standards slows the creativity*". In some sense that is true. What we are looking now, is that the same things are being implemented by webkit, gecko, presto and other engines. We could said it is a waste of efforts (mainly if the most used engine (trident) does not follow).

So, here is the idea: Lets suppose we could separate the engines from the browsers, this is, that browsers would not be embedded with their engine. In the same way video codecs and video players work: You don't have to care if your movie was encoded with DivX, Xvid or whatever, in order to watch it correctly.  

You could specify in your HTML code (for developers) which engine you are using, like:

```
<meta engine="presto" version="2" />
```

Then, the engine could be installed/updated in-demand by the browser.
The browsers then would have the task of rendering your code with the selected engine. That way, browsers would not care about how things are rendered but will focus in user interaction (bookmarks, search in page, navigation, themes, etc). 
This idea is somehow influenced by Google Frame and how it works inside IE. 

**What engines gain?** creativity. I think this way each engine could add as much features as they want without having to stick to a common manual. This could lead to very cool things and faster technology changes. Also, engines would be focused in provide developers and end-users the best experience.

**What developers gain?** developers could choose among the engines the one which fits better in their project (even per page basis). For example, lets suppose webkit could specialize in 3D web experience. So if you want to develop a 3D web game, then webkit could be the way to go. In the other side, if you want to develop a .NET application for an intranet system which will interact with other WIN systems, then "Trident" would be the way to go, and so on. 

**What Microsoft gain?** With this (even MS win!), they would never have to worry again about acid tests and standards. They could focus in giving support just for trident features and even more, embed Silverlight with DirectX (2D+3D), etc. MS could save millions of USD in support! No more IE sucks!

**What common people gain?** Best user interfaces, no more broken pages or "IE only" or "NO-IE sites".

**Possible problems:**

Maybe the main problem here could be to make MS to agree with it. 
It is possible that W3C consortium may not like this proposition. 

Developers would have to learn about each engine they decide to use (which I don't see a really problem).

I'm not sure of the "higher" technical difficulties to make this possible. So it is just a dream...

I want to thank to all the people that posted in this thread, I think I got really valuable information. 

Thank you.

---

### Post by BuffaloX on 2009-12-02
Obviously (to anyone who know my standpoint) I agree with the sentiment of this thread, and I already took steps against IE all versions.
I'm planning to change my policy towards IE, but it is not yet implemented, as I'm rebuilding my site to use PHP.

I'm considering pulling the same stunt on IE as MS did on DR, which is to pop a false error message, making IE look bad, then let them browse the site, but slow it down till it gets very annoying.

Even if IE 9 is fully W3C compliant, I will block it, MS need to leave the browser market, they have done too much harm already to deserve a second chance.

I'm sick of reading guides about web development, and then have to read loads of cr4p about how to make it work for IE, or you shouldn't use this standard, since IE hasn't implemented it yet.

I was really happy to read this news story from "Spiegel online", which states that Firefox with a 45.6% market share has surpassed IE with 44.4%, according to market researcher Fittkau & Maaß.
Spiegel onlines own numbers show an even greater lead 49% for Firefox and 37% for IE. In weekends the number is an astounding 55% for Firefox and only 27% for IE.

I suppose even the IT admins that install IE for all their users, use FF when they go home.

Here's the link:
[http://www.spiegel.de/netzwelt/web/0,1518,664475,00.html]("http://www.spiegel.de/netzwelt/web/0,1518,664475,00.html")

---

### Post by Penguin Guy on 2009-12-02
> **LepeKaname said:**
> IE would never be on time with the W3C standards (because they can't or just don't care about it)
I think you are mistaken; they *could* keep up with W3C standards if they wanted to, but they don't: They have a monopoly - incompatibility is a wise business tactic.

---

### Post by whiskeylover on 2009-12-02
Plus, they would not want to break backward compatibility with older web apps using non standard HTML. That would piss off a lot of corporate clients (who happen to be the biggest customers of MS).

So, in short, no, you can't get rid of IE. Big companies, like Amazon and ebay will keep supporting non-standard features of IE, or else they risk losing 80-90% of user base. It doesn't make business sense.

---

### Post by zagz on 2009-12-02
IE would be to risky for me given the line of work I am in.

---

### Post by neojames on 2009-12-02
I've heard on a few forums that Netscape Classic does better in acid tests than IE8

---

### Post by marco123 on 2009-12-02
> **neojames said:**
> I've heard on a few forums that Netscape Classic does better in acid tests than IE8


[http://www.webdevout.net/browser-support-summary?IE7=on&IE8=on&FX1=on&FX2=on&uas=CUSTOM](http://www.webdevout.net/browser-support-summary?IE7=on&IE8=on&FX1=on&FX2=on&uas=CUSTOM)

Even Firefox 1 is better overall according to the chart on that site.:lol:  Now if that's not an epic fail I don't know what is.

---

### Post by LepeKaname on 2009-12-02
> **neojames said:**
> I've heard on a few forums that Netscape Classic does better in acid tests than IE8

For today, Internet Explorer 9 scores 32/100 in the Acid 3 and Internet Explorer 8 scores 20/100 ([http://en.wikipedia.org/wiki/Acid3](http://en.wikipedia.org/wiki/Acid3))

According to this screen, Netscape 7.01 (Nov, 2002 !!!!) scores 35/100:

[http://farm4.static.flickr.com/3134/3233720701_f6a5c015c1_o.png](http://farm4.static.flickr.com/3134/3233720701_f6a5c015c1_o.png)

I can't believe my eyes :shock:

---

### Post by Maheriano on 2009-12-03
Looks like Germany was successful. Probably something to do with the fact computers don't ship with Internet Explorer in many parts of Europe.

[IMG]http://www.spiegel.de/images/image-37258-galleryV9-huyx.jpg[/IMG]

---

### Post by Diluted on 2009-12-03
You can't get rid of IE's brokenness, not without a gradual process, which seems to be the approach the IE team is taking with standards.

---

### Post by UltimateAnon on 2010-06-17
Haha! I thank that within 5 years IE's user percentage will drop below 40%. As much as I like FireFox, I don't think that it will be the dominant browser. I think that chrome will be, as Google is producing an OS. Here's my prediction. 

1. Google releases OS.
2. Google gets a major deal with a computer company, ie. HP, emachines, etc.
3. Google OS soon becomes the dominant OS with 40% or more of computers have the Google OS on it.
4. Note, the Google OS would have Chrome as the installed browser.

I really think that IE is going down the tubes. Microsoft, too. Besides Windows, what do they have? 


Small side note: Google is going to take over the world. :lolflag:

---

### Post by Ranko Kohime on 2010-06-17
Way back when IE had a 95%+ market share, a lot of web greasemonkey's were coding strictly for IE, to the point of putting up browser-detection pages which shunned other browsers and told visitors to get the latest copy of IE...

Maybe we can do something similar?  It's a tad drastic, I know, but perhaps worth the heartache?

On a related note, having just checked the stats for my website, in no month has IE risen above 62% share, and it's currently only at 48%.  I would not lose much by blocking it.

---

### Post by Penguin Guy on 2010-06-17
> **Ranko Kohime said:**
> On a related note, having just checked the stats for my website, in no month has IE risen above 62% share, and it's currently only at 48%.  I would not lose much by blocking it.
I think blocking IE is a bit harsh, you could always put up a message saying that says IE doesn't properly support W3C HTML and suggest the reader uses a different browser.

---

### Post by McRat on 2010-06-17
Do like the Browser companies do:

Check the browser type.
If it's IE, insert art and link for your preferred browser along with:

"This site is better with Firefox."

If you really want to be a PITA, then put a delay loop on each page if viewed in IE.

---

### Post by UltimateAnon on 2010-06-17
> **McRat said:**
> Do like the Browser companies do:

Check the browser type.
If it's IE, insert art and link for your preferred browser along with:

"This site is better with Firefox."

If you really want to be a PITA, then put a delay loop on each page if viewed in IE.

Hahahaha! That is truly cruel and beautiful. People who use IE, I think, are impatient and not very knowledgeable when it comes to coding... They'd never know what hit them. Plus, unlike a normal banner, it wouldn't disturb the other traffic.

---

### Post by Frak on 2010-06-17
> **UltimateAnon said:**
> I really think that IE is going down the tubes. Microsoft, too. Besides Windows, what do they have?

The entire gaming market.

---

### Post by NightwishFan on 2010-06-17
I do not want Microsoft to die. They are not evil, just disappointing at times. The 'do bad on purpose vendor lock in' thing is in the past I hope. I really do.

---

### Post by UltimateAnon on 2010-06-17
> **Frak said:**
> The entire gaming market.

Hmmmmmmmmmmmmmmmmmm... What are the Xbox and the Xbox 360 notorious for?
A circle of death. Yes, the Xbox is known for breaking. Computer games... those can be modified for other OS.

Small note: any who wants to discourage IE users, I made a small code for it.
[HTML]<div id="IEinform" style="visibility: hidden; width: 230px; height: auto; border: 1px solid black; text-align: center; font-size: 10px; font-family: verdana; padding: 3px; position: fixed; top: 90%; background-color: white;">
This page runs best in Mozzilla Firefox.<br><a href="http://www.mozilla.com/en-US/products/download.html">Download it here!</a>
</div>
<script language="JavaScript" type="text/javascript">
if (navigator.appName.match("Microsoft") == "Microsoft")
 {document.getElementById("IEslow").style.visibility="hidden";
  var delay=setTimeout("IEdelay()", 4000); // 4 seconds is the amount of time it's delayed for.
    }

else
 {document.getElementById("IEslow").style.visibility="visible";
  document.getElementById("IEinform").style.visibility="hidden";
  }    
    
function IEdelay()
   {document.getElementById("IEslow").style.visibility="visible";
      document.getElementById("IEinform").style.visibility="visible";
        }
</script>[/HTML]Note: The body tag must have this in there. [HTML]<body id="IEslow" style="visibility: hidden;">[/HTML]

---

### Post by Frak on 2010-06-17
> **UltimateAnon said:**
> Hmmmmmmmmmmmmmmmmmm... What are the Xbox and the Xbox 360 notorious for?
A circle of death. Yes, the Xbox is known for breaking. Computer games... those can be modified for other OS.

Only to you. Everybody I know, knows the Xbox for Halo and Gears of War.

> **UltimateAnon said:**
> Small note: any who wants to discourage IE users, I made a small code for it.
[HTML]<div id="IEinform" style="visibility: hidden; width: 230px; height: auto; border: 1px solid black; text-align: center; font-size: 10px; font-family: verdana; padding: 3px; position: fixed; top: 90%; background-color: white;">
This page runs best in Mozzilla Firefox.<br><a href="http://www.mozilla.com/en-US/products/download.html">Download it here!</a>
</div>
<script language="JavaScript" type="text/javascript">
if (navigator.appName.match("Microsoft") == "Microsoft")
 {document.getElementById("IEslow").style.visibility="hidden";
  var delay=setTimeout("IEdelay()", 4000); // 4 seconds is the amount of time it's delayed for.
    }

else
 {document.getElementById("IEslow").style.visibility="visible";
  document.getElementById("IEinform").style.visibility="hidden";
  }    
    
function IEdelay()
   {document.getElementById("IEslow").style.visibility="visible";
      document.getElementById("IEinform").style.visibility="visible";
        }
</script>[/HTML]Note: The body tag must have this in there. [HTML]<body id="IEslow" style="visibility: hidden;">[/HTML]

You can't just slow down your problems. We professionals can't just "discourage" IE users. We have to accommodate.

---

### Post by Frak on 2010-06-17
> **UltimateAnon said:**
> Hmmmmmmmmmmmmmmmmmm... What are the Xbox and the Xbox 360 notorious for?
A circle of death. Yes, the Xbox is known for breaking. Computer games... those can be modified for other OS.

Small note: any who wants to discourage IE users, I made a small code for it.
[HTML]<div id="IEinform" style="visibility: hidden; width: 230px; height: auto; border: 1px solid black; text-align: center; font-size: 10px; font-family: verdana; padding: 3px; position: fixed; top: 90%; background-color: white;">
This page runs best in Mozzilla Firefox.<br><a href="http://www.mozilla.com/en-US/products/download.html">Download it here!</a>
</div>
<script language="JavaScript" type="text/javascript">
if (navigator.appName.match("Microsoft") == "Microsoft")
 {document.getElementById("IEslow").style.visibility="hidden";
  var delay=setTimeout("IEdelay()", 4000); // 4 seconds is the amount of time it's delayed for.
    }

else
 {document.getElementById("IEslow").style.visibility="visible";
  document.getElementById("IEinform").style.visibility="hidden";
  }    
    
function IEdelay()
   {document.getElementById("IEslow").style.visibility="visible";
      document.getElementById("IEinform").style.visibility="visible";
        }
</script>[/HTML]Note: The body tag must have this in there. [HTML]<body id="IEslow" style="visibility: hidden;">[/HTML]

Former: Everybody I know, knows the Xbox for Halo and Gears of War.

Latter: Nothing like getting streams of emails telling me my site is slow. Don't be childish with it.

---

### Post by whiskeylover on 2010-06-17
> **UltimateAnon said:**
> Hmmmmmmmmmmmmmmmmmm... What are the Xbox and the Xbox 360 notorious for?
A circle of death. Yes, the Xbox is known for breaking. Computer games... those can be modified for other OS.

Small note: any who wants to discourage IE users, I made a small code for it.
[HTML]<div id="IEinform" style="visibility: hidden; width: 230px; height: auto; border: 1px solid black; text-align: center; font-size: 10px; font-family: verdana; padding: 3px; position: fixed; top: 90%; background-color: white;">
This page runs best in Mozzilla Firefox.<br><a href="http://www.mozilla.com/en-US/products/download.html">Download it here!</a>
</div>
<script language="JavaScript" type="text/javascript">
if (navigator.appName.match("Microsoft") == "Microsoft")
 {document.getElementById("IEslow").style.visibility="hidden";
  var delay=setTimeout("IEdelay()", 4000); // 4 seconds is the amount of time it's delayed for.
    }

else
 {document.getElementById("IEslow").style.visibility="visible";
  document.getElementById("IEinform").style.visibility="hidden";
  }    
    
function IEdelay()
   {document.getElementById("IEslow").style.visibility="visible";
      document.getElementById("IEinform").style.visibility="visible";
        }
</script>[/HTML]Note: The body tag must have this in there. [HTML]<body id="IEslow" style="visibility: hidden;">[/HTML]

Good luck finding a new job when  your client finds out you've slowed down his website for your own vendetta against IE, and pissed off a majority of his customers.

---

### Post by UltimateAnon on 2010-06-17
> **Frak said:**
> Only to you. Everybody I know, knows the Xbox for Halo and Gears of War.

You can't just slow down your problems. We professionals can't just "discourage" IE users. We have to accommodate.

If you haven't noticed, the thread is about removing IE, not helping it. I code as a hobby, and IE takes tons of fun out of coding. I agree with you, but my hatred for IE tends to over rule my professional attitude.  
I have nothing against Microsoft. I just feel that they've been leading the crusade for far too long.

Note: Halo and GoW are NOT the entire gaming market.

---

### Post by McRat on 2010-06-17
> **whiskeylover said:**
> Good luck finding a new job when  your client finds out you've slowed down his website for your own vendetta against IE, and pissed off a majority of his customers.

Apple is good with it.  I went to their site to set up an appointment, and they told me I had to use Safari.

[https://onetoone.apple.com/WebObjects/RRSPortal.woa](https://onetoone.apple.com/WebObjects/RRSPortal.woa)

Guess it depends on the employer.

---

### Post by Frak on 2010-06-17
> **UltimateAnon said:**
> If you haven't noticed, the thread is about removing IE, not helping it. I code as a hobby, and IE takes tons of fun out of coding. I have nothing against Microsoft. I just feel that they've been leading the crusade for far too long.

Yay, bash thread! Anyways, I don't like IE either, but that doesn't permit me to be irrational in my practices.

> **UltimateAnon said:**
> Note: Halo and GoW are NOT the entire gaming market.

You're right, I forgot WoW and CoD:MW2.

---

### Post by UltimateAnon on 2010-06-17
> **McRat said:**
> Apple is good with it.  I went to their site to set up an appointment, and they told me I had to use Safari.

[https://onetoone.apple.com/WebObjects/RRSPortal.woa](https://onetoone.apple.com/WebObjects/RRSPortal.woa)

Guess it depends on the employer.

Agreed. Plus, I never intended to have that for a professional site. Maybe just for people with blogs, fan sites, forums and things like that.

> **Frak said:**
> Yay, bash thread! Anyways, I don't like IE either,  but that doesn't permit me to be irrational in my practices.

You're right, I forgot WoW and CoD:MW2.

Haha, I wouldn't call it irrational, just prejudiced.

---

### Post by Penguin Guy on 2010-06-18
> **Frak said:**
> I don't like IE either, but that doesn't permit me to be irrational in my practices.
They're you're practices, you're permitted to do what you like with them.

The more developers who refuse to accommodate for IE, the less popular it will become. Refusing to go out of your way to support IE compatibility - yes. Putting up a 'change browser' banner for IE users - yes. Sabotaging IE by deliberately slowing it down - no.

I think some people here are fighting a holy war.

---

### Post by Frak on 2010-06-18
> **Penguin Guy said:**
> I think some people here are fighting a holy war.

.

---

### Post by puzzler995 on 2010-06-18
> **McRat said:**
> Apple is good with it.  I went to their site to set up an appointment, and they told me I had to use Safari.
Yes, then Apple is also the biggest bunch of control freaks on the internet.

---

### Post by McRat on 2010-06-18
When I posted about putting delay loops in, I said if you want to be a PITA.  Being a PITA is not a good thing, and should be looked at like deliberate flatulence in public.

However, it's something that's been going on a very long time in various forms by large software companies, like the Safari Only message at Apple, or the irremovable version of IE.

IE came to dominate the market because of such tactics.  Ditto for MS Office.  Neither product was the best in it's market when released, so MS did "dirty tricks" to push them to the top.

If you get bored, a dumb little story about dirty tricks:

 I pulled a "dirty trick" a long time ago.  I came up with a way to do checking for math errors from inside the DOS version of WordPerfect, before Office came out.  My employer did their tech reports in WP, and they often had math errors.  I said I could fix it, and they said "No, we just need the employees to make fewer mistakes or fire them".  So I wrote the "Report Checker" at home in my spare time, and brought it to work.  I asked if they would like to see a demonstration, and they said OK.  They liked what they saw.  I told them it took 100 hours of research and experimentation to get it right, so I wanted $900 for it per facility that used it times 5 facilities.  They agree.

Six month later, they had not paid me yet.  And suddenly the program stopped working.   In fact, the first time people ran WP that day, they found the program was not even there anymore.  

They weren't very happy with me.  But I told them I could make it start running again in less than 1 minute if they kept up their side of the deal.  3 days later they agreed.  All I had done was put a routine in that moved the app core to another directory and set the Hidden attribute.  So I faxed over a short BAT file to be ran, and it fixed it.  Later I found that the 3 days was spent trying to get the program to run from backups.  They tried changing the system date and reinstalling but as soon as they ran the program it vanished.  I keyed the timebomb to the last file saved date, not the system time.  The minute the program ran, it looked at the Most Recent File's date and if it was too late, it moved and hid the EXE.  

I had to "move and hide" because it would take 24 hours to fix using a floppy disk and UPS Red.  Hide just made it a little harder on them to figure out why it would not run and let them know subtly that an EXE can delete files.  In the BAT file was a line to create a new file PAID.TXT.  The program looked for this file to override the timebomb.

They didn't fire me, but they certainly would have been justified.  Luckily I was their top CMM technician and was pretty valuable to them.   I left shortly afterwards and started my own business.

People have been prosecuted successfully for doing software boobytraps against their employer, so you should be careful not do such things.

---

### Post by Penguin Guy on 2010-06-18
> **McRat said:**
> People have been prosecuted successfully for doing software boobytraps against their employer, so you should be careful not do such things.
It's illegal to protect your program from being 'stolen'?

---

### Post by McRat on 2010-06-18
> **Penguin Guy said:**
> It's illegal to protect your program from being 'stolen'?

If somebody doesn't pay you, it's a civil matter.  If you boobytrap somebodies computer, it's a criminal case.  In my case, I doubt it I could have been prosecuted since I only disabled my program, I didn't actually remove it.  But letting them know that "files can disappear" was probably wrong.

So in theory, you could use the money to post bail.  It sucks, but that's how the decisions have been going.

Sidebar - They only paid $900 for the one facility I worked at.  It was up to the managers at the other facilities to authorize the payment, and they refused.  My boss was a bit of a weasel.

---

### Post by alphaniner on 2010-06-18
> **Penguin Guy said:**
> It's illegal to protect your program from being 'stolen'?

I wouldn't be surprised.  A friend of my father who owned a restaurant got sued by a burgular who tried to break in through the oven vent, because he fell right on to the hot grittle.  There is a state or city law mandating your ventilation is designed such that this wouldn't happen.  So the douchebag burgular won.

---

### Post by Penguin Guy on 2010-06-18
> **alphaniner said:**
> I wouldn't be surprised.  A friend of my father who owned a restaurant got sued by a burgular who tried to break in through the oven vent, because he fell right on to the hot grittle.  There is a state or city law mandating your ventilation is designed such that this wouldn't happen.  So the douchebag burgular won.
Fair enough - you can't burn people or delete files without permission. But if someones tries to steal your stuff or your software then I'd say call it quits.

---

### Post by McRat on 2010-06-18
Something else you should be aware of if you are a technical employee.

Many companies have pre-employment agreements that indicate any innovation you come up with on your own time, patents, software, art designs, and such, belongs to your employer.

Sometimes the agreement is rejected by the courts, and sometimes the intellectual property is assigned to the employer WITHOUT a written agreement.  It just depends on your job scope.

---

### Post by puzzler995 on 2010-06-18
> **McRat said:**
> Many companies have pre-employment agreements that indicate any innovation you come up with on your own time, patents, software, art designs, and such, belongs to your employer.
Thats why you always read the fine print. If it says that, slap the guy, call him a greedy idiot, and walk out.\\:D/ ):P

---

### Post by McRat on 2010-06-18
> **puzzler995 said:**
> Thats why you always read the fine print. If it says that, slap the guy, call him a greedy idiot, and walk out.\\:D/ ):P

I signed a few of those, including two that said telling people what I'm working on could land me in Federal prison or even executed.  And gave rights to the DOD and FBI to search without a warrant.

Some employers are pretty strict.  :D

---

### Post by Frak on 2010-06-18
> **puzzler995 said:**
> Thats why you always read the fine print. If it says that, slap the guy, call him a greedy idiot, and walk out.\\:D/ ):P
I bet you don't have a job, then. If you use company resources, the innovation belongs to them. The most tyrannical of companies that do this is Google. They just rip ideas off of their employees, and selfishly promote those members to managerial positions for overseeing it. How terrible.

---

### Post by puzzler995 on 2010-06-18
> **Frak said:**
> I bet you don't have a job, then. If you use company resources, the innovation belongs to them. The most tyrannical of companies that do this is Google. They just rip ideas off of their employees, and selfishly promote those members to managerial positions for overseeing it. How terrible.

No I don't have a job. I'm in high school XD

---

### Post by Frak on 2010-06-18
> **puzzler995 said:**
> No I don't have a job. I'm in high school XD
When you get a job at a corporate chain, that'll be in the contract. If you work for anybody on small scale and invent something, that person can still claim rights to it because it was developed on their time.

---

### Post by Penguin Guy on 2010-06-19
> **McRat said:**
> Many companies have pre-employment agreements that indicate any innovation you come up with **on your own time**, patents, software, art designs, and such, belongs to your employer.
> **Frak said:**
> If you work for anybody on small scale and invent something, that person can still claim rights to it because it was developed **on their time**.
We are talking about having your idea stolen if you invent something while you're **not** at work.

P.S. Makes you see the advantage to being self-employed.

---

### Post by Frak on 2010-06-19
> **Penguin Guy said:**
> We are talking about having your idea stolen if you invent something while you're **not** at work.

P.S. Makes you see the advantage to being self-employed.
Nobody here will argue that self employment is better, but it's not possible for a lot of people. Plus, you'll realize that your company sweeps through a lot of paperwork for you.

And while you're not at work, the company can't claim anything.

---

### Post by UltimateAnon on 2010-07-02
> **McRat said:**
> Many companies have pre-employment agreements that indicate any innovation you come up with on your own time, patents, software, art designs, and such, belongs to your employer.

In other words: We live in a society that lives off the common man's work. It takes a clever person to protect their work. Sometimes a coupla lawyers, too...

Lesson Learned: Avoid business. At all costs.

---

### Post by RiceMonster on 2010-07-02
> **UltimateAnon said:**
> Lesson Learned: Avoid business. At all costs.

Let me know how you make out with that.

---

### Post by Timmer1240 on 2010-07-02
Gosh darnit Im really lovin google chrome for some reason just love it its fast and good interface likin it!

---

### Post by EricDP on 2011-10-23
In order to accomplish this you have to understand why IE behaves the way it does. It's not because Microsoft doesn't care. It was a very deliberate choice by Microsoft which stems back to the very beginning of the Internet.

Before there were web browsers there was something called the "application barrier to entry". This means that an operating system can't compete if nobody makes any apps for it. And nobody would make any apps for an OS that didn't have a big customer base. Therefore, catch-22: nobody would ever challenge the monopoly that MS had.

Then the internet came along, and all you needed was a browser to make an OS viable. Microsoft saw this as a significant strategic threat to their market so they did three things:

[LIST]
[*]They created a web browser that was intentionally not standard
[*]They made their broken browser the default browser on their OS
[*]They created a set of web development tools (WebDAV, Frontpage) that would default to authoring code compatible only with their browser
[/LIST]
Since they had control of >95% of desktops, they also had control of most web developers, and many bought the MS tools to develop web pages. Suddenly the vast majority of web pages served up code that was only compatible with IE. And since >95% of people already had IE, often running alongside other browsers, they could compare. In most cases, IE rendered properly (because the pages themselves were broken) and the other browsers appeared broken. Eventually, the other browsers fell out of favour and all but disappeared.

The result: operating systems that didn't run IE also appeared to be broken. And MS continued to hold their monopoly for many more years.

Of course, this couldn't last forever. The other vendors figured out what MS was up to and started implementing MS "extensions" into their browsers. So now we're seeing what MS most feared: several alternatives that are equally viable.

So, knowing this, what's the next step?

---

### Post by krapp on 2011-10-23
> **UltimateAnon said:**
> In other words: We live in a society that lives off the common man's work.

We've known this since the 1840s!

---

### Post by Sef on 2011-10-24
Locked. Necromancing.

---

