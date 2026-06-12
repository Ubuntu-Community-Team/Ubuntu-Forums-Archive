---
title: "New business website, html5 or no?"
date: 2011-09-23
forum: The Cafe
---

### Post by BandD on 2011-09-23
My wife, her family and I are in the final planning stages of a new business.  I've been appointed the 'techie' and I'm thinking about the business website.  I've seen some sites (goolge included) do some pretty cool things with html5.  Performance wise is seems much snappier and dependable than  flash.  Most people I know use firefox and most of those firefox users are running at least 6.0.  If one does have a site coded in html5 there will obviously be people with older browsers that won't be able to interact with the site properly.  Is it a good idea to find a web developer to code a page in html5 at this point in time?  I hate flash and would really like to be a relatively early adopter.  If you were starting a business would you go html5 at this point in time?

---

### Post by undecim on 2011-09-23
How about neither?

HTML 5 is too new, so a lot of browsers won't support it. Flash is... well it's flash. It sucks. It's also bad for SEO. (Google can't read text in flash)

Think about what you want your site to accomplish. Is your entire point with the website to impress your customers with your web design skills? Unless you're starting a web design business, probably not. No, the point of the website is to get information to your customers. i.e. When someone visits your website you want to:

1) explain what your business does
2) explain how visitors can become customers (e.g. where you're located, how to order a product)
3) persuade visitors to become customers.

All of this can easily be done with safe, compatible HTML 4. Fancy animations (especially if implemented by someone who  hasn't studied website *design*, which is different from website *development*) can just get in the way of your customers who are looking for information.

P.S: Look into Joomla and Wordpress. They're both excellent platforms for managing a website, don't require a lot of technical knowledge to use (though you can get more out of them with more knowledge), and chances are your web host has install scripts built into your website control panel.

---

### Post by Dr. C on 2011-09-23
A lot depends on what the business is about. My personal rule is to maximize compatibility across operating systems and browsers.

That means compatibility with:

GNU / Linux including distributions that have no propriety software such as gNewSense
Microsoft Windows all the way back to Windows 9x or NT and IE6 or earlier. I still get visitors to my website that are running Windows 3.xx and IE5
Mac OS X  and earlier versions. 
Mobile platforms including Android, Blackberry and Apple IOS.
All major browsers Firefox, IE, Chrome, Safari, Opera etc and some of the minor ones 
Text based browsers such as Lynx.

Basically why shut the door on a paying customer because of their choice of operating system or browser?

---

### Post by nmaster on 2011-09-23
> **undecim said:**
> How about neither?
+1, although it depends on the business i suppose...

---

### Post by in·ter·punct on 2011-09-23
> HTML 5 is too new, so a lot of browsers won't support it.The HTML5 spec will reach [Candidate Recommendation]("http://www.w3.org/2004/02/Process-20040205/tr#RecsCR") stage during 2012.

The new semantic elements are supported in IE9+, FF4+, Safari 5+, Chrome 11+, Opera 11.1+. Your site visitors are using an older browser? No problem, use html5shim.

The audio and video elements are supported in IE9+, FF3.6+, Safari 4+, Chrome 11+, Opera 10.6+. Your site visitors are using an older browser? No problem, serve flash as a fallback or make the content available for download.

Are you using the new HTML5 form features, but some of your visitors are using older browsers? No problem, most of the features fallback gracefully.


Have this in mind: sites do not need to look pixel perfect in every browser nor will they be experienced the same in every browser.

What I'm trying to say is you can start using HTML5 today. You just have to be mindful about your choices and consider how visitors in older browsers will view your content. IE8 and under are really the only browsers to worry about.

---

### Post by Paqman on 2011-09-23
> **BandD said:**
> Most people I know use firefox

Firefox is current 27% of web users. Your biggest single browser is still IE at a little under 42% (of which about three quarters use IE8 or lower, which either have limited or no support for HTML5)

[http://gs.statcounter.com/](http://gs.statcounter.com/)

---

### Post by kaldor on 2011-09-23
> **Paqman said:**
> Firefox is current 27% of web users. Your biggest single browser is still IE at a little under 42% (of which about three quarters use IE8 or lower, which either have limited or no support for HTML5)

[http://gs.statcounter.com/](http://gs.statcounter.com/)

Sad, but true. If you want your business to reach the widest amount of people it needs to work with IE7 and IE8. I know too many people who are too scared to use anything beyond IE7. 

HTML5 is not supported in IE below IE9. It's pretty annoying at how people refuse to update their stuff. With businesses I can understand, but not on your own personal machines. All it does is slow the progress of the web.

---

### Post by Merk42 on 2011-09-23
Kind of mirroring what undecim said, **why** do you want to use HTML5 (or Flash for that matter).
What features do they have that you want to use on your website?
[quote="BandD"]Most people I know use firefox[/quote]
That doesn't matter, what matters is what the people **visiting this particular site** use.

---

### Post by Dangertux on 2011-09-23
I would think for a business you would want the most compatibility possible. You wouldn't want to chase off possible customers by using something that their browser may not support properly. Keep it simple.

Just my thoughts.

---

### Post by Paqman on 2011-09-23
> **Dangertux said:**
> Keep it simple.


+1

If you can, build it in a way that doesn't rely on any technology that isn't universally supported.

---

### Post by forrestcupp on 2011-09-23
For the people berating Flash because you can't understand why a business would want flashy animations that get in the way, that's not even the biggest use of Flash. Businesses use Flash to embed videos that describe what they're about. No one can say that a good, informative video is useless and gets in the way.

I recently found myself in the same boat as the OP. I could have set up an html5 player with Flash as a fallback, but it was much less of a hassle to just end up using Flash. html5 players don't support .flv files and Flash players don't support .mp4's or whatever. So you end up having to set it up for different video files and host twice the videos.

Everybody has Flash, and if they don't, they can get it without having to upgrade their browser. Sometimes in a work situation, upgrading a browser is a much, much bigger deal than it is for a home user.

The good thing about html5 is that it can be experienced in iOS, while Flash can't. But maybe that's a good reason for people to not use iOS. :)

---

### Post by Dangertux on 2011-09-23
> **forrestcupp said:**
> For the people berating Flash because you can't understand why a business would want flashy animations that get in the way, that's not even the biggest use of Flash. Businesses use Flash to embed videos that describe what they're about. No one can say that a good, informative video is useless and gets in the way.

I recently found myself in the same boat as the OP. I could have set up an html5 player with Flash as a fallback, but it was much less of a hassle to just end up using Flash. html5 players don't support .flv files and Flash players don't support .mp4's or whatever. So you end up having to set it up for different video files and host twice the videos.

Everybody has Flash, and if they don't, they can get it without having to upgrade their browser. Sometimes in a work situation, upgrading a browser is a much, much bigger deal than it is for a home user.

The good thing about html5 is that it can be experienced in iOS, while Flash can't. But maybe that's a good reason for people to not use iOS. :)

+1

Also very good points. I think it really comes down to the needs of the business. If you want that type of experience for your customers or your product is such that it would benefit from that, then it is a decision you have to weigh.

If it's a simple home cleaning crew, it might not need a video advertisement. It all depends on the customer base.

---

### Post by Merk42 on 2011-09-23
> **forrestcupp said:**
> Flash players don't support .mp4's or whateverYes they do. You can use the same mp4 file and directly feed it to the <video> tag for Safari/IE/Chrome<=14 or the swf for the flash version

(yes there's the whole ogv/webm thing but that's another thread)

---

### Post by doorknob60 on 2011-09-24
Don't use Flash, it's unneccesary (unless you need embedded videos or something). You can use HTML5 if you want, but I wouldn't make it a requirement for the site to function (as in make it compatible with older browsers, and maybe have extra cool features in HTML5 for the newer browsers).

---

### Post by forrestcupp on 2011-09-24
> **Merk42 said:**
> Yes they do. You can use the same mp4 file and directly feed it to the <video> tag for Safari/IE/Chrome<=14 or the swf for the flash version

(yes there's the whole ogv/webm thing but that's another thread)
That's good to know. I'll have to look more into an html5 player with Flash backup, then.

---

### Post by earthpigg on 2011-09-24
Good old HTML 4 would be ideal. But, if you are ***forced*** to choose between HTML 5 and Flash...

The wealthier the customer base, the more ideal HTML 5 becomes. 

I have absolutely no idea what the business is, so I'll assume for the sake of argument that the target demographic is folks with disposable income (ie, income that can be spent in the purchasing of goods/services offered by the business).

Things that are HTML 5 compatible are generally [superior goods]("http://en.wikipedia.org/wiki/Superior_good").

Things that are not HTML 5 compatible are generally [inferior goods]("http://en.wikipedia.org/wiki/Inferior_good").

An iPad 2, for example, is HTML 5 compatible out of the box. So is a 6 month old Windows laptop.

A 7 year old desktop with IE 6 is not HTML 5 compatible. 

Of those two groups, which do you think has more people able and willing to purchase on the goods/services being offered?

(People that cannot afford the product being offered are irrelevant for obvious reasons. We're painting broad strokes and trying to earn a buck, not trying to be 'fair' or 'unfair' to anyone. Not moral, not immoral, but amoral.)


Anyways, my initial assumption may be off. If this is a social or charity service being offered because your associates are acting out of the kindness of their hearts and not profit motive, then the discussion will necessarily need to be radically different.

---

### Post by forrestcupp on 2011-09-24
> **Merk42 said:**
> Yes they do. You can use the same mp4 file and directly feed it to the <video> tag for Safari/IE/Chrome<=14 or the swf for the flash version

(yes there's the whole ogv/webm thing but that's another thread)

I found out the video player I was already using was html5 and Flash both. I was playing an .flv, so I switched it to an .mp4. When I did that, it didn't play the video until it was completely loaded.

Back to .flv for now.

---

### Post by BandD on 2011-09-27
Thank you all for the opinions and info.  It is greatly appreciated. In case anyone is terribly interested, the business will be a family run micro brewery. You all have given me a lot to think about and research more thoroughly.

Again, thank you!

---

### Post by juancarlospaco on 2011-09-27
**Go here ---> [http://beetle.de/full/](http://beetle.de/full/)**

Think HTML5

Profit

---

### Post by wishyjr on 2011-09-27
> **Merk42 said:**
> Kind of mirroring what undecim said, **why** do you want to use HTML5 (or Flash for that matter).
What features do they have that you want to use on your website?

That doesn't matter, what matters is what the people **visiting this particular site** use.

totally agree, what needs to be understood is the audience viewing the site. 

What does you business do? Will you be having 'techies' viewing the website? If so then i wouldn't worry about HTML5 issues as those types of users will probably have a reasonably up to date browser.

If the business targets say, non-tech savvy people that are perhaps not interested or un-educated in the advantages of updating software (or just software in general) then they may be using an old browser.

To be honest, i would think that the majority of users now use a browser that supports HTML5 regardless of the browser type.

---

### Post by Merk42 on 2011-09-27
> **wishyjr said:**
> To be honest, i would think that the majority of users now use a browser that supports HTML5 regardless of the browser type.
QUITE A LOT of Browsing is still done on IE 6, 7 and 8, so no.

Of course that's worldwide, who knows what the visitors of BandD's future site use.

"Support HTML5" is such a misnomer anyway. All recent browsers support HTML5, but none of them support **all** HTML5 features. Some browsers support certain features and some support others.

---

### Post by SeijiSensei on 2011-09-27
I've never designed a site that requires anything like Flash or HTML5 video.  I hate sites that have big opening animations; I search all over the screen for the "skip this" option as quickly as possible.

The only exception to this is a site I worked on that offers executive training programs.  We recorded a couple of the instructors in action, put the videos up on a YouTube channel, then embedded the player into the web site.  

Start by asking yourself what information visitors are likely to be looking for and make sure you provide that information in as simple a format as possible.  I'd probably be interested in the lines of beers you offer, maybe a bit of information on the brewing process, your choice of hops, etc., and how and where to buy your products.  As an example, the [Samuel Adams](http://www.samueladams.com/) site has only a couple of video clips, taken from their television advertisements; the rest is text and static graphics.  (I found their requirement that I enter my age really annoying; is that a legal requirement of some kind?  What does it really matter if a 15-year-old wants to learn about brewing?)

---

### Post by Merk42 on 2011-09-27
> **SeijiSensei said:**
> (I found their requirement that I enter my age really annoying; is that a legal requirement of some kind?  What does it really matter if a 15-year-old wants to learn about brewing?)It is a legal requirement that any time you have a website for alcohol you must ask for the age of the individual.

It pretty much falls under [this](http://www.ftc.gov/opa/1999/09/alcoholrep.shtm)

So that's something BandD's website will need to do if it doesn't already, regardless of the language it's programmed in.

---

### Post by juancarlospaco on 2011-09-27
> **Merk42 said:**
> QUITE A LOT of Browsing is still done on IE 6, 7 and 8, so no.


I dont care, just suggest installing chrome frame, it dont need privileges to install.

---

### Post by forrestcupp on 2011-09-27
> **SeijiSensei said:**
> 
The only exception to this is a site I worked on that offers executive training programs.  We recorded a couple of the instructors in action, put the videos up on a YouTube channel, then embedded the player into the web site.
That's the thing. Some people benefit from having some kind of instructional or introductory video, but they would rather host their own video rather than have it on YouTube. In that case, this discussion applies.

And by "introductory video", I'm talking about a video that introduces what they're all about, and not an annoying auto-play video at the beginning page of a web site that everyone wants to skip.

---

### Post by Merk42 on 2011-09-27
> **juancarlospaco said:**
> I dont care, just suggest installing chrome frame, it dont need privileges to install.Watch as visitors would rather not go to your site than install some weird plugin (I say weird because they wouldn't know what it is).
If that doesn't bother you, fine. I **wish** I had that option in the sites I build.

---

### Post by juancarlospaco on 2011-09-27
I dont care, i code WITHOUT any FallBack intentionally,
i dont want a Web with 20 FallBacks for each Item,
i want the users see how the Browsers Fail...

---

### Post by forrestcupp on 2011-09-27
> **juancarlospaco said:**
> I dont care, i code WITHOUT any FallBack intentionally,
i dont want a Web with 20 FallBacks for each Item,
i want the users see how the users Fail...

Lol. That's why nobody looks at your web sites. ;)

---

### Post by fatality_uk on 2011-09-27
> **Merk42 said:**
> Kind of mirroring what undecim said, **why** do you want to use HTML5 (or Flash for that matter).
What features do they have that you want to use on your website?

That doesn't matter, what matters is what the people **visiting this particular site** use.

Totally correct. I would hazard a guess that 98.95% of all customers visiting a business web site couldn't give a crap about the technology behind it. HTML5, 4, 3, 2 or 1! Flash, no flash, DHTML, AJAX.

For a B2C site, build a site that works, gives your customers what they want within no more than 4 or 5 clicks and satisfies "their" needs.

You could spend months faffing about creating a great "techy" site, which all the other nerds will applaud you for and yet not make any money.

---

### Post by juancarlospaco on 2011-09-27
> **forrestcupp said:**
> Lol. That's why nobody looks at your web sites. ;)

You prefer a Web with 20 FallBacks per object?, Hiding the true design of the Web?, just a ton of Binary Blobs?

A person who code for Mozilla tell me: "Internet Explorer 9 its the best achievement of Mozilla"

[LIST]
[*]**If you think Flash is Cool, ask a person who uses Screen Readers**
[/LIST]

---

### Post by Merk42 on 2011-09-27
> **juancarlospaco said:**
> You prefer a Web with 20 FallBacks per object?, Hiding the true design of the Web?, just a ton of Binary Blobs?

A person who code for Mozilla tell me: "Internet Explorer 9 its the best achievement of Mozilla"

[LIST]
[*]**If you think Flash is Cool, ask a person who uses Screen Readers**
[/LIST]
If you have 20 fallbacks you're doing it wrong.

---

### Post by juancarlospaco on 2011-09-27
> **Merk42 said:**
> If you have 20 fallbacks you're doing it wrong.

[http://en.wikipedia.org/wiki/Irony](http://en.wikipedia.org/wiki/Irony)

EDIT: oh, i see your signature now, its true, not a replacement, but an overpowered replacement :)

---

### Post by forrestcupp on 2011-09-28
> **juancarlospaco said:**
> You prefer a Web with 20 FallBacks per object?, Hiding the true design of the Web?, just a ton of Binary Blobs?

You said you don't use *any* fallbacks, which is what I was referring to. There are a lot of people with browsers that aren't capable of html5. So if you don't use *any* fallbacks, those people won't be able to experience whatever you code in html5.

So if I want everyone to be able to see my site, then yes, I do prefer to at least have one fallback. When it comes to my website, I'm not on a civil rights freedom kick. I want people to be able to see what I have out there. If they can't, why even waste my time with it?

---

### Post by juancarlospaco on 2011-09-28
> **forrestcupp said:**
> You said you don't use *any* fallbacks, which is what I was referring to. There are a lot of people with browsers that aren't capable of html5. So if you don't use *any* fallbacks, those people won't be able to experience whatever you code in html5.

Nope..., 
you can make it pops up a thingy with "Install chrome frame, its libre and dont require admin"

---

### Post by forrestcupp on 2011-09-28
> **juancarlospaco said:**
> Nope..., 
you can make it pops up a thingy with "Install chrome frame, its libre and dont require admin"

Almost any time I go to a website that pops up and asks me to install something, and I don't think it's absolutely vital, I'm going to leave that site immediately.

You're free to do what you want, but my opinion is that I want to make my site welcoming to people, and not make them want to leave right away. The way you do that is by catering to them, not by forcing them to cater to you. If my only reason for Flash or html5 is to show one short video on my About page, I'm not going to make them install chrome frame just for that. I'll either just use Flash, or I'll use an html5 player that has a Flash fallback.

---

### Post by juancarlospaco on 2011-09-28
They need to install Adobe Flash anyways, which its not libre and need admin privileges :D

---

### Post by Merk42 on 2011-09-28
> **juancarlospaco said:**
> They need to install Adobe Flash anyways, which its not libre and need admin privileges :D
I'm going to guess the vast majority of (presumably IE 8 or lower) users would already have Flash installed.

...and a lot of them wouldn't know/care it's not libre.

---

### Post by juancarlospaco on 2011-09-28
> **Merk42 said:**
> the vast majority of (presumably IE 8 or lower) users would already have Flash installed.

Last time i checked IE doesnt have a built-in Flash renderization,
so it needs to be installed manually from Adobe.com ...

---

### Post by Merk42 on 2011-09-28
> **juancarlospaco said:**
> Last time i checked IE doesnt have a built-in Flash renderization,
so it needs to be installed manually from Adobe.com ...
Yes, and people will have most likely already done that LONG before visiting your site.

Take a survey of people with IE, find out how many of them already have it installed because of Facebook games, YouTube...

Now see how many of those have Chrome Frame installed.




It's fine, you're clearly set on possibly losing visitors to your webpage. Forrestcupp chooses not to risk that and there's no way my clients would let me risk it.

What does your site do that even 'requires' Chrome Frame anyway?

---

### Post by juancarlospaco on 2011-09-28
Iam not talking about you and me, iam talking about what the title says.

Its fine for me if you choose Flash and ActiveX and all that stuff :)

---

### Post by Paqman on 2011-09-28
Forcing people to install *anything* just to view your site is one of the cardinal sins of web design IMO (up there with resizing browser windows and hijacking mice). 

Remember back in the old days of the web when you had to install half a dozen plugins just to view any multimedia? And everything was served up in at least two different formats to cope? Yuk. These days we pretty much just have Flash, and everybody has it preinstalled. Don't turn back the clock to the bad old days.

---

