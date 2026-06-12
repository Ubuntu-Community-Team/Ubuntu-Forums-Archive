---
title: "I never suspected it would be this bad."
date: 2009-03-24
forum: The Cafe
---

### Post by BuffaloX on 2009-03-24
I just started making my own homepage, using Bluefish and Quanta.
I Tested it with Firefox Konqueror Opera Chrome Safari and IE.
Guess which one was the **ONLY** one to not render my site correctly.
You get **ONE** try.

It's not so much that it was rendered incorrectly, it totally trashed my site!

If you don't like guessing games, follow the link in my sig, navigate to "computers" then to "Nightmare".

If only one browser out of the six most popular cannot render a page even
remotely decently, and this on a site that uses only the most **basic standards.**, would you support that browser?

A popular slogan comes to mind. JUST SAY NO!

Am I wrong not wanting to support this browser? The users are completely innocent, only the maker is to blame.

---

### Post by Dr Small on 2009-03-24
I don't even try coding for IE, it's so horrid.

---

### Post by uc50_ic4more on 2009-03-24
> **BuffaloX said:**
> Am I wrong not wanting to support this browser? The users are completely innocent, only the maker is to blame.

Wrong? Heavens, no. You'll just have to balance your desire to use the type of code that you are able to generate (which obviously does not play nicely with IE), and your desire to accommodate users of all sorts who use a variety of browsers.

Trust me, IE compliance takes up a good portion of most web site's creative time. It is a *major* pain in the back side, but for those of us designing sites for paying clients who wish *not* to be offputting to the ~85% of users using some verion of IE, it is a necessary pain in the back side.

There are two bits of good news, however: 1) Most issues you'll run across in web development have some type of IE workaround. Some are quick and efficient; while others are pretty ugly. 2) IE6 is by far the most egregious of the IE family of browsers still in common use today. IE7 and 8 have been considerable steps forward in terms of usability and standards compliance; and IE will, over time, fade into the deep oblivion where it belongs.

---

### Post by jespdj on 2009-03-25
This is exactly why making HTML / CSS / JavaScript web applications is not fun - because different browsers work differently, and especially because the world's most used browser (IE) is so poor in supporting standards.

When programming in JavaScript (or JScript - Microsoft's own variant :rolleyes: ) you have to be really careful not to use constructions that lead to the horrible bugs and memory leaks in IE.

---

### Post by JackieChan on 2009-03-25
> **jespdj said:**
> This is exactly why making HTML / CSS / JavaScript web applications is not fun - because different browsers work differently, and especially because the world's most used browser (IE) is so poor in supporting standards.

When programming in JavaScript (or JScript - Microsoft's own variant :rolleyes: ) you have to be really careful not to use constructions that lead to the horrible bugs and memory leaks in IE.
Yeah.

---

### Post by Marco A on 2009-03-25
.

---

### Post by bvanaerde on 2009-03-25
With the newer versions of IE, it's a bit better.
I think it's time to leave the IE6 and lower users behind...

---

### Post by CrazyArcher on 2009-03-25
> **bvanaerde said:**
> I think it's time to leave the IE6 and lower users behind...

Agreed. IE7 is at least usable, IE6 is an abomination.

---

### Post by x33a on 2009-03-25
i feel if web designers stop accomodating IE users, and instead everyone boycotts IE, then the IE users will have to switch to a different/better browser. i am not a web designer, but i really pity the designers who have to waste precious hours to tweak their code for Internet Explorer.

---

### Post by Pogeymanz on 2009-03-25
I'm glad you tried to redirect IE users to find something better, but I suggest you make it less verbose. Just a few lines about why you don't support IE, then a few links to its shortcomings, then links to better browsers.

All that reading and preaching will put people off. That is not to say that you shouldn't mention that Microsoft is attempting to monopolize the internet, because they are and it's wrong.

Just my two cents.

---

### Post by Eisenwinter on 2009-03-25
> **x33a said:**
> i feel if web designers stop accomodating IE users, and instead everyone boycotts IE, then the IE users will have to switch to a different/better browser. i am not a web designer, but i really pity the designers who have to waste precious hours to tweak their code for Internet Explorer.
I agree with this, but go tell that to many other web developers, I doubt they will listen.

---

### Post by Dies on 2009-03-25
> **Pogeymanz said:**
> I'm glad you tried to redirect IE users to find something better, but I suggest you make it less verbose. Just a few lines about why you don't support IE, then a few links to its shortcomings, then links to better browsers.

All that reading and preaching will put people off. That is not to say that you shouldn't mention that Microsoft is attempting to monopolize the internet, because they are and it's wrong.

Just my two cents.


I agree. 

This was my version when I ran into that problem on a site I did for fun

[http://redcellso.com/browsersucks.html](http://redcellso.com/browsersucks.html)


I found IE7 did an OK job so I excluded 6 and under by using

<!--[if lt IE 7]>
<script language="javascript"><!--
location.replace("browsersucks.html")
//-->

on the main page.

Anyone can feel free to copy that page while it's still up. ;)

---

### Post by s.fox on 2009-03-25
> **Dr Small said:**
> I don't even try coding for IE, it's so horrid.

Wish I could just do that.  :)

Unfortunately most of the clients of the company I do web development for only use Internet Explorer.  :(

---

### Post by uc50_ic4more on 2009-03-25
> **x33a said:**
> i feel if web designers stop accomodating IE users, and instead everyone boycotts IE, then the IE users will have to switch to a different/better browser. i am not a web designer, but i really pity the designers who have to waste precious hours to tweak their code for Internet Explorer.

It's not the web developer's choice!

Web developers work for people who *do* care about the ~80% of people using one incarnation of IE or another.

Also, I cannot help but think that *forcing* users to use one software of our choosing rather than their own is contrary to both the letter and spirit of software freedom; and freedom in general.

---

### Post by Dr Small on 2009-03-25
> **uc50_ic4more said:**
> It's not the web developer's choice!

Web developers work for people who *do* care about the ~80% of people using one incarnation of IE or another.
But then again, not all web designers design for customers, either.

---

### Post by uc50_ic4more on 2009-03-25
> **Eisenwinter said:**
> I agree with this, but go tell that to many other web developers, I doubt they will listen.

Wow, folks... It's *not the web developers*!

It's the bed and breakfasts, the construction companies, the banks, the charities that *hire* web developers to make web sites. So very often, they're NOT interested in spending their money making a site that only works perfectly for ~20% of their users. You know what they really, really, really don't care about? Software activism. They just want their sites to work for their users, most of whom use Windows + IE.

---

### Post by uc50_ic4more on 2009-03-25
> **Dr Small said:**
> But then again, not all web designers design for customers, either.

*Absolutely*!!!!

... But the complaints about "web developers" not taking a "stand" about this are not directed solely at the (tiny minority) of personal sites designed and maintained by the person behind the site.

---

### Post by Martje_001 on 2009-03-25
Internet Explorer 8 is standard complaint (even better than Firefox in some areas)!

---

### Post by uc50_ic4more on 2009-03-25
> **Martje_001 said:**
> Internet Explorer 8 is standard complaint (even better than Firefox in some areas)!

Although it is a huge improvement over earlier versions, to call it "compliant" might be somewhat optimistic... It stills fails the ACID3 test pretty badly.

---

### Post by Thelasko on 2009-03-25
Remember this:
> This page is best viewed in Microsoft Internet Explorer
It's time for this:
> This page is best viewed in a standards compliant browser
Problem solved!

---

### Post by uc50_ic4more on 2009-03-25
> **Thelasko said:**
> Problem solved!

You know, that's not a bad idea at all. I could see a header at the top of the page, visible only to IE using visitors, that politely pointed out that their browser is not standards compliant - and their experience at this site may not be as intended, blah blah blah; with links to Firefox, Opera, etc. The "error" message would have to be crafted carefully, as calling out IE as not standards-compliant, then linking to other browsers that are not entirely compliant themselves is a little hypocritical.

Properly done, though, tt's the kinda of idea that could even be "sold" to web development clients, as it operates under the auspices of improving user experience.

In fact, I think I'll get working on it: a simple script, perhaps jQuery-based, that'd sniff out IE users, slide down a relatively unobtrusive (and skinnable, to integrate with a site's existing colour schemes) header with the links, logos and verbiage pre-populated (but editable as well).

---

### Post by -grubby on 2009-03-25
> **uc50_ic4more said:**
> Although it is a huge improvement over earlier versions, to call it "compliant" might be somewhat optimistic... It stills fails the ACID3 test pretty badly.

The Acid3 test is not a measure of web compliance. Does IE8 accept XHTML 1.1 mimetypes? Can it render pages according to w3 specs? Those are the questions you should be asking.

---

### Post by uc50_ic4more on 2009-03-25
> **nathangrubb said:**
> The Acid3 test is not a measure of web compliance. Does IE8 accept XHTML 1.1 mimetypes? Can it render pages according to w3 specs? Those are the questions you should be asking.

Certainly not: It is a measure of CSS compliance, which is page one from book one of Web Compliance For Dummies. 

Not adhering to the other standards aforementioned would render (pun intended) the browser unusable rather than just annoyingly weird.

---

### Post by geoken on 2009-03-25
> **nathangrubb said:**
> The Acid3 test is not a measure of web compliance. Does IE8 accept XHTML 1.1 mimetypes? Can it render pages according to w3 specs? Those are the questions you should be asking.

No it can't. I haven't spend too much time with it but I can verify that it still doesn't support the :hover psuedo class on block level elements and it also incorrectly parents absolutely positioned divs.

---

### Post by miggols99 on 2009-03-25
Well it looks like your page isn't standards compliant anyway :rolleyes:

[http://validator.w3.org/check?uri=http%3A%2F%2Fwww.buffalox.dk%2Fcomputers-ie-nightmare.html&charset=(detect+automatically)&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.buffalox.dk%2Fcomputers-ie-nightmare.html&charset=(detect+automatically)&doctype=Inline&group=0)

Anyway, I hope people move over to IE 8 at least, because I hate having to code for IE 6/7..

---

### Post by BuffaloX on 2009-03-26
Wow that's a lot of responses thanx. All your input is much appreciated.

[COLOR="Blue"]@miggols99
Seems I have some things to iron out, still it doesn't explain why out of 7 browsers ONLY IE6 and IE7 renders my site incorrectly.[/COLOR]

I haven't had much time to work on my site the last couple of days, and frankly the IE bug is somewhat demotivating. Excluding 2/3 of users is A LOT.

I've been thinking of an alternative to my current way of handling the problem, and have come to the conclusion that the best way is probably a line inserted at the top of each page, that only appear for users of IE.
Saying something like this this:

"**Warning!** Internet Explorer renders this page Incorrectly. Click _[COLOR="Blue"]here[/COLOR]_ to solve this problem."

Then if people click the link, they will see something along the lines of what I already do, but with slightly shorter text.

What do you think guys, Is this the way to go?
Or do you have any alternative/better ideas?

---

### Post by joshdudeha on 2009-03-26
I don't want to get killed by saying this.
But does it really matter, for a personal website?

---

### Post by oasmar1 on 2009-03-26
[http://www.buffalox.dk/ie/stop-using-ie.html](http://www.buffalox.dk/ie/stop-using-ie.html)
How childish. This is the worst possible thing to do. 
I suggest most people just put a small DIV somewhere (best near the top) telling the user that their browser is not supported and that they may recieve some issues with the site.
I also only ever put a message to people using <IE7. IE7 and IE8 both tend to render well (IE7 might need a seperate style sheet with small modifications, usually a padding issues). Blocking out a user and spreading false information is just terrible.
 
[LIST]
[*]better security
[*]better internet experience
[*]faster page renderings
[*]MUCH faster javascript
[*]100% free.
[/LIST]

IE8 is free, IE8 renders pages fast and can infact beat firefox and even chrome in some cases. Better Security? Well, IE8 has been praised as having better security than Firefox and better at blocking malware than all other browsers.
Internet experience is an opinion.
The only one I agree with is the javascript.

---

### Post by BuffaloX on 2009-03-26
> **joshdudeha said:**
> I don't want to get killed by saying this.
But does it really matter, for a personal website?

It doesn't affect my livelihood if that's what you mean.

But of course it matters, and I think it matters to a great many people who are in the same position of not wanting to support IE, but want friends and family or people with common interests to be able to use ones site.

If nobody ever saw my site, why would I want to maintain it?
If it's successful it is more fun.
Cutting off 2/3 of user = less successful = less fun.

I hope this answers your question.

---

### Post by BuffaloX on 2009-03-26
> **oasmar1 said:**
> [http://www.buffalox.dk/ie/stop-using-ie.html](http://www.buffalox.dk/ie/stop-using-ie.html)
How childish. This is the worst possible thing to do. 
I suggest most people just put a small DIV somewhere (best near the top) telling the user that their browser is not supported and that they may recieve some issues with the site.
I also only ever put a message to people using <IE7. IE7 and IE8 both tend to render well (IE7 might need a seperate style sheet with small modifications, usually a padding issues). Blocking out a user and spreading false information is just terrible.
 
[LIST]
[*]better security
[*]better internet experience
[*]faster page renderings
[*]MUCH faster javascript
[*]100% free.
[/LIST]

IE8 is free, IE8 renders pages fast and can infact beat firefox and even chrome in some cases. Better Security? Well, IE8 has been praised as having better security than Firefox and better at blocking malware than all other browsers.
Internet experience is an opinion.
The only one I agree with is the javascript.

Your input is appreciated, but could maybe have been a bit more sensitive.

If you read just 2 posts up from your own, you will see I decided to do almost exactly what you suggest.

About IE versus other browsers:
Security: IE8 hacked within 2 days of its release. Plus MS track record for IE7 of being quite slow to close security holes. But i did simplify this a bit, since Safari is probably as insecure as IE.

Faster page rendering: I don't know about IE8, but I tried IE7 and it was horrible. Especially when resizing the browser window. MS claim IE8 is as fast as Firefox, but is probably still beaten by Chrome Opera and Safari.
Again I simplified a little.

Javascript: We Agree yea. :)

100% free is a fact (as in beer) Firefox and Chrome truly free, which IE is NOT. IE8 is also free as in beer, and I never said otherwise. Again a slight simplification.

The above combined would to most equal better Internet Experience.

Simplifications was done in an attempt to keep the message relatively short, according to some it's too long as it is.

---

### Post by oasmar1 on 2009-03-26
Ok, sorry about that, it is just I am coming across an increasing number of sites which do this and it really annoys me because (I know it is strange) I actually like to use IE8 when using Windows (which I do a bit because I do a lot of design work on Windows and Mac).
Also, you should try maybe reinstalling IE8, because my computer loads pretty much every browser other than IE6 in milliseconds.

---

### Post by Tomosaur on 2009-03-26
I'm a software engineer, and I have to develop web apps for businesses. Guess what 99.99% of them still use?

Why, our old friend IE6!

The one good thing MS has done for me is supported conditional comments. It's still more work for me, but at least it lets me seperate IE specific code from 'normal' code.

Added to this - they all want Web 2.0 websites these days with Ajax and flashy nice rounded corners etc - things which IE6 does NOT make easy to achieve in a timely and / or well designed fashion.

---

### Post by Redache on 2009-03-26
I would like to Point Something Out:

---

### Post by BuffaloX on 2009-03-26
> **oasmar1 said:**
> Ok, sorry about that, it is just I am coming across an increasing number of sites which do this and it really annoys me because.

Actually I think that's cool, that is people finally taking a stand against IE. IE8 may be OK for now, but MS kept us with the ugly and incompatible IE6 for FIVE years!

> **Tomosaur said:**
> I'm a software engineer, and I have to develop web apps for businesses. Guess what 99.99% of them still use?

Why, our old friend IE6!


It's a mystery to me, why those companies don't upgrade, if not for anything else, then for the improved security.

> **Redache said:**
> I would like to Point Something Out:

Cool thanks, I don't have access to IE8 testing, so I really appreciate your posting the picture. I wanted to be able to test with the most used version which is 7.
Only one part of the rendering is off, but that's a minor issue which can be easily corrected.

---

### Post by Redache on 2009-03-26
IE 8 does appear to be less idiotic in its rendering. I still don't like the UI though.

I'd just make it run under IE8 if possible, I don't see why people don't upgrade to new versions of Internet Explorer if they INSIST on using it. The only reason IE6 has so much proliferation is probably down to people using pirated copies/aren't aware of Windows Update, since I think IE7 is a forced update and I'm sure IE8 will be at some point as well.

---

### Post by bvanaerde on 2009-03-27
For testing with multiple browsers, I suggest:
[http://browsershots.org](http://browsershots.org)

It makes a screenshot of the webpage for every browser you need.

---

### Post by geoken on 2009-03-27
> **Tomosaur said:**
> I'm a software engineer, and I have to develop web apps for businesses. Guess what 99.99% of them still use?

Why, our old friend IE6!

The one good thing MS has done for me is supported conditional comments. It's still more work for me, but at least it lets me seperate IE specific code from 'normal' code.

Added to this - they all want Web 2.0 websites these days with Ajax and flashy nice rounded corners etc - things which IE6 does NOT make easy to achieve in a timely and / or well designed fashion.

You should add an individual line item in the invoice for IE6 support. That's what I do.

ie. 

Internet Explorer 6 support ----- x hours ------ $xxx

---

### Post by HavocXphere on 2009-03-27
Microsoft.com is one of 2400 major sites not being rendered correctly by the new IE8.:lolflag:

If they can't even sort their own #$%^ out then I'd say its little surprise that your site isn't being rendered correctly.

[http://www.neowin.net/news/main/09/02/19/2400-major-sites-that-ie-8-cant-render-correctly](http://www.neowin.net/news/main/09/02/19/2400-major-sites-that-ie-8-cant-render-correctly)

---

### Post by mihai.ile on 2009-03-27
> **HavocXphere said:**
> Microsoft.com is one of 2400 major sites not being rendered correctly by the new IE8.:lolflag:

If they can't even sort their own #$%^ out then I'd say its little surprise that your site isn't being rendered correctly.

[http://www.neowin.net/news/main/09/02/19/2400-major-sites-that-ie-8-cant-render-correctly](http://www.neowin.net/news/main/09/02/19/2400-major-sites-that-ie-8-cant-render-correctly)

Actually this is good news you know... It means that IE8 is more standards compliant and microsoft's site is using mor of their's standards. When Microsoft fixes it's page for IE8 it means that the page is a step closer in better integration with the rest of the browsers out there...

And while I noticed that some just come by to say "yeah IE, M$ is bad" as a web developer I can say that IE8 is a great improvement. Many of us would wish just having to support this version of IE instead of v.6/7

---

### Post by LowSky on 2009-03-27
My company still uses IE6, Companies lock into verisons for long periods of time. Its to maintain stability regardless of how crappy the app may be.

---

### Post by Tomosaur on 2009-03-28
> **geoken said:**
> You should add an individual line item in the invoice for IE6 support. That's what I do.

ie. 

Internet Explorer 6 support ----- x hours ------ $xxx

Not a bad idea - but we're only a small company so we have to be VERY careful about annoying customers :P

---

### Post by MikeTheC on 2009-03-28
Not that I've ever had an urge to get into web site development, but this sort of thing would completely put me off if I did...

Desktop Publishing FTW!!! :)

---

### Post by Uruz2012 on 2009-03-28
> **Tomosaur said:**
> Not a bad idea - but we're only a small company so we have to be VERY careful about annoying customers :P

Well, you don't have to add any extra charges to the bill. Just break the cost of supporting IE6 down into it's own line. You're clients might decide that it's not worth the extra cost. This would free you up to do more constructive things for them than supporting an outdated app. Presented to them this way  it would be a good decision for them to drop IE6 support.

---

### Post by tsali on 2009-03-28
> **HavocXphere said:**
> Microsoft.com is one of 2400 major sites not being rendered correctly by the new IE8.:lolflag:

If they can't even sort their own #$%^ out then I'd say its little surprise that your site isn't being rendered correctly.

[http://www.neowin.net/news/main/09/02/19/2400-major-sites-that-ie-8-cant-render-correctly](http://www.neowin.net/news/main/09/02/19/2400-major-sites-that-ie-8-cant-render-correctly)


FUD. I just started at the top of the list and IE8 has rendered the first twenty perfectly.

Do people just make this crap up?

---

### Post by jacob01 on 2009-03-28
i have been taking a html course and this makes me wonder if the same would happen to Firefox or another browser if a page was written optimized for ie or would the other browsers render the page the same as ie?

haven't tried it with Firefox yet

---

### Post by airtonix on 2009-03-29
> **jacob01 said:**
> i have been taking a html course and this makes me wonder if the same would happen to Firefox or another browser if a page was written optimized for ie or would the other browsers render the page the same as ie?

haven't tried it with Firefox yet

depends.

there are some fundamental differences in how a w3c compliant browser and IE choose to interpret the javascript, html & css code.

One of the primary examples is the box model and how the various aspects of spacing are applied.

The other is that there are many attributes that only IE understands (attributes which are not part of the w3c specification), so using & relying on those attributes for major aspects of your site layout will only result in failure for non IE browsers.

I found that many of the problems associated with developing for IE can be overcome in two ways : 
 + for javascript, use a library like mootools in order to streamline your javascript methodology in to one format. scripts created using the mootools framework operates the same in both browsers.
 + code for w3c first, then as previous people have mentioned set aside time to use conditional tags to superimpose attributes and styles that refactor how the code is interpreted for IE. This allows you to sector away your time spent on IE specific tatsk for your invoice.

---

