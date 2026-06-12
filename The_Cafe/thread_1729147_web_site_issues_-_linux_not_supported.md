---
title: "web site issues - linux not supported"
date: 2011-04-14
forum: The Cafe
---

### Post by bradhaack on 2011-04-14
I use firefox & ubuntu and 99% of the websites work just fine.  Occasionally I'll find one that doesn't work and if I follow up they usually say something like linux is not supported because it is less than 2% market share.  I'm pretty sure that if they followed the html standards it would work.  What's the best way to communicate this to them?   I was hoping to find some way to quickly check if they were following the rules and I found this:  [http://validator.w3.org/](http://validator.w3.org/),  but almost every link I check has errors, including ubuntuforums.org.   I'm not a web geek so I don't know what standards they should be following.

---

### Post by bodhi.zazen on 2011-04-14
Standards are guidelines that should be followed if possible.

Reality is browsers do not meet the standards or have different methods of rendering the standard. So the same code, even if it meets all the standards, will render differently on different browsers.

Then there are the hand held devices ...

In addition the web sites in question may use features on the server that are not implemented in Linux (cough silverlight).

Sure you can try mono/moonlight in Linux, but it may or may not work.

Silverlight is not the only example of poorly supported web things , but is the most common.

Some sites will not work with Firefox even if you are running Firefox in Windows.

If you visit my site

[http://bodhizazen.net/](http://bodhizazen.net/)

with IE 7 and write me an email telling me the menus are broken I will tell you I do not support IE7 =)

Such is modern web browsing. You do what you can to support as much as you have time and interest to support.

The webmasters are telling you they like the site the way it is and that they are not going to change =)

Probably not much you can do about it. Some people are going to be more open to cross browser / cross platform then others.

---

### Post by Spice Weasel on 2011-04-14
A lot of sites support Firefox in Windows and Mac but not on anything else, even if they don't use Silverlight. It's a bit stupid. There's not much you can do apart from complain.

Of course, the [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") might work.

---

### Post by Johnsie on 2011-04-14
Here's what I send to websites that don't support web standards:


> 
Dear Sir/Madam

Your website wont work on my computer because it isn't standards compliant.

The code of your site did not pass the html validity test at [http://validator.w3.org/](http://validator.w3.org/) so may have been written badly to begin with.

A website that is written properly using the internationally recognised web standards should work on any standards-compliant browser, regardless of operating system. This is the reason web standards were introduced in the first place. Websites should not be restricted to only Microsoft customers as that is anti-competitive and ignorant of the fact that many people choose to purchase or use alternative non-Microsoft products which are still web standards compliant. Web standards are governed by a whole myriad of companies working together to ensure that the Internet is accessible to as many people as possible, including users who have physical disabilities. For more information about web standards please visit the site at [http://www.w3.org/standards/](http://www.w3.org/standards/)

Here are some useful links about web standards:

Wikipedia Page:
[http://en.wikipedia.org/wiki/World_Wide_Web_Consortium](http://en.wikipedia.org/wiki/World_Wide_Web_Consortium)

Purposes of Web Standards:
[http://www.w3.org/Consortium/](http://www.w3.org/Consortium/)

All the major tech companies use web standards:
[http://www.w3.org/Consortium/Member/List](http://www.w3.org/Consortium/Member/List)


Please rectify your website to ensure that it meets modern web standards. I look forward to hearing from you to find out how you are progressing with making your site more standards compliant. Please respond in a timely manner with information about how and when your development team plan to fix the irregularities within your website. I will also be forwarding this email to other staff members and management in your company to make sure these changes are actioned.


---

### Post by donkyhotay on 2011-04-14
> **Spice Weasel said:**
> Of course, the [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") might work.

I hate sites that give me messages stating my OS/browser isn't supported and then I use UAS to report different system and it works just fine. I appreciate the warning on a site that won't work with my system when it really is incompatible but when it won't work because they simply deny using the site even though it would work I get frustrated. I mean if you don't really want to worry about support then just have a disclaimer stating it *might* not work and allow a "let me use it anyways" button.

---

### Post by hunterkasy on 2011-04-14
> **Johnsie said:**
> Here's what I send to websites that don't support web standards:

I like it,  Can I use it also when I find websites that don't support web standards?

---

### Post by CharlesA on 2011-04-14
> **bodhi.zazen said:**
> Standards are guidelines that should be followed if possible.

Reality is browsers do not meet the standards or have different methods of rendering the standard. So the same code, even if it meets all the standards, will render differently on different browsers.

+1. I coded my site to XHTML strict, and it passes fine, but it doesn't render the same in every browser.

---

### Post by bodhi.zazen on 2011-04-14
> **Johnsie said:**
> Here's what I send to websites that don't support web standards:

I think that response is quite demanding actually. If I received a similar response asking for support of IE on my web site, I would probably respond with a healthy dose of ignore.

I would substantially soften the tone and ask if they would consider reviewing the code and including support they are lacking.

Not all problems are due to the standards you cite (html / css standards are a small part, and there are no standards for php, java, etc. Some servers / back ends may never be compliant).

Aslo, most, if not all, now html / css compliant web pages will actually render in most browsers, so the problem is unlikely to be in the standards you cite. Try it, make a file "hello.html". Put in some text

> <b>It works !</b>

Now open that file with firefox, what do you see ?

Now run that file through the standard checkers and see how many errors you get, yet it renders just fine :p

XHTML was designed to close that loop hole (rendering a non-compliant page). If you are truly using xhtml strict on your web server, and you have an error, the page will not render. This is probably one of the leading reasons XHTML is a dead project and html 5 is in development, web developers did not like the terminal errors.

In addition, although you can code pages xhtml strict, apache does not serve them as xhtml strict unless you configure it to do so (check your mime types):

[http://protempore.net/~calvins/howto/xhtml-apache/](http://protempore.net/~calvins/howto/xhtml-apache/)

There is a reason for this, it is a real pain to [s]use[/s] enforce such strict standards when one small typo will kill your page =).

The web standards you cite in your letter are simply not that strictly enforced and the incompatibility is elsewhere. As a result, your letter comes across as, for lack of a better word, uninformed (no offense intended).

Keep in mind , you do not want to argue with these people or come across as a "fanboi" seeking to cause problems.

Websites are complex creatures and if the site meets their needs they are unlikely to do anything more then dismiss your demanding tone.

You should probably not argue with them Linux vs Windows but rather browser compatibility and it is easy to demonstrate that IE is loosing market share fast.

So while their "old model" may have served them well in the past, it is unlikely to continue to do so in the future.

You also need to understand their needs, where the incompatibility is generated, and their time and expense to upgrade their web page, which may be substantial.

---

### Post by wrtpeeps on 2011-04-15
> **Johnsie said:**
> Here's what I send to websites that don't support web standards:

To be honest with you, if I received an email like this I'd be inclined to agree with bodhi.zazen and ignore it (either that or email you back and tell you where to shove it). Your email comes across as smug, know it all (implying that the person doesn't know about standards).


"Does not support" is just company terms nowadays for "it might work, but we don't really test it and we won't spend money fixing it if it doesn't work". At the end of the day they can only afford to fix things if it improves their bottom line, and at times that just isn't going to happen.

---

### Post by slackthumbz on 2011-04-15
> **wrtpeeps said:**
> To be honest with you, if I received an email like this I'd be inclined to agree with bodhi.zazen and ignore it (either that or email you back and tell you where to shove it). Your email comes across as smug, know it all (implying that the person doesn't know about standards).


"Does not support" is just company terms nowadays for "it might work, but we don't really test it and we won't spend money fixing it if it doesn't work". At the end of the day they can only afford to fix things if it improves their bottom line, and at times that just isn't going to happen.

Same here, I try to keep all my code standards compliant and I do test on Chromium, FF and Opera but as I have no access to any machines running any version of windows I do not test on IE, nor do I make any pretence about supporting IE. Instead I have a javascript popup on my front page that only goes off if the user is on some version of IE. It explains that IE is not supported, that older versions of IE are known to be non-standards compliant and recommends any other browser on the market ;)

Unfortunately my site is down at the moment :/

---

### Post by Giant Speck on 2011-04-15
> **Johnsie said:**
> Here's what I send to websites that don't support web standards:
That e-mail sounds awfully condescending and snobby, to be honest.

---

### Post by RiceMonster on 2011-04-15
> **Giant Speck said:**
> That e-mail sounds awfully condescending and snobby, to be honest.

But some random person on the internet sent them an angry email! They'd better listen!

---

### Post by jerenept on 2011-04-15
> **ricemonster said:**
> but some random person on the internet sent them an angry email! They'd better listen!

or else!

---

### Post by RiceMonster on 2011-04-15
> **bodhi.zazen said:**
>  and there are no standards for php, java, etc.

However, php on its own is not responsible for the resulting HTML and CSS, or any the JavaScript on the site, which is what gets rendered and processed by the browser. It's up to the developer of said website to make the html and css work correctly, as php is essentially just processing text and responding to http requests.

---

### Post by handy on 2011-04-15
So does using a user agent string such as:

*Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.1; WOW64; Trident/6.0)*

Fool the website?

---

### Post by CraigPaleo on 2011-04-15
> **slackthumbz said:**
> It explains that IE is not supported, that older versions of IE are known to be non-standards compliant and recommends any other browser on the market ;)



I'd love to see that - especially if it's worded that way. "We recommend ***any other*** browser." Ha ha!

---

### Post by jerenept on 2011-04-15
> **CraigPaleo said:**
> I'd love to see that - especially if it's worded that way. "We recommend ***any other*** browser." Ha ha!

Opera 6, Mozilla 1.2 and iCab 3 all supported!

---

### Post by CraigPaleo on 2011-04-15
> **jerenept said:**
> Opera 6, Mozilla 1.2 and iCab 3 all supported!

[IMG]http://fc07.deviantart.net/fs71/i/2010/092/e/6/Best_Viewed_Without_IE_by_zellfaze.png[/IMG]

---

### Post by RiceMonster on 2011-04-15
> **CraigPaleo said:**
> [IMG]http://fc07.deviantart.net/fs71/i/2010/092/e/6/Best_Viewed_Without_IE_by_zellfaze.png[/IMG]

So lynx would work better than IE?

---

### Post by jerenept on 2011-04-15
> **RiceMonster said:**
> So lynx would work better than IE?

```
curl $url | html2text 
```
is better than IE.

---

### Post by CraigPaleo on 2011-04-15
> **RiceMonster said:**
> So lynx would work better than IE?

If it doesn't, we can always get Johnsie to send an email. :D

---

### Post by SeijiSensei on 2011-04-15
> **wrtpeeps said:**
> "Does not support" is just company terms nowadays for "it might work, but we don't really test it and we won't spend money fixing it if it doesn't work". At the end of the day they can only afford to fix things if it improves their bottom line, and at times that just isn't going to happen.

+1

This is almost always a pragmatic decision, not something driven by technical standards at all.  The site's owner(s) don't want to staff up to cover complaints from people using something other than Windows or OS X.  Ignoring the couple percent of Linux users often makes financial sense.

What will change this attitude, I suspect, is the growth of mobile devices. 

Just use [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") to tell the site you're running Windows.

---

### Post by bradhaack on 2011-04-15
> **SeijiSensei said:**
> +1

Just use [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") to tell the site you're running Windows.

That won't help if they're using Silverlight or some incompatible Flash.  

From the comments it sounds like in the web developer world the standards are generally ignored and we're lucky that w our <1% market share that anything works at all.

---

### Post by tlcstat on 2011-04-15
Greetings,
There is nothing new about this problem it even existed with the old IE releases and MS is terminating support for IE6 for that reason. 
I personally have a hosts file blocklist with thousands of blocked websites. I have reserved my right as a user to block any site or content that I don't wish to have access to my computer.  Just makes sense that any website also may support or not support any platform that they choose.  Open and free doesn't mean absolute guaranteed access. I haven't personally found a non-supported website but my attitude would be "dust off my boots and move on!  Its a big world and I don't have time to fight with a small part of it.
tlcstat

---

### Post by rg4w on 2011-04-15
> **bradhaack said:**
> I use firefox & ubuntu and 99% of the websites work just fine.  Occasionally I'll find one that doesn't work and if I follow up they usually say something like linux is not supported because it is less than 2% market share.  I'm pretty sure that if they followed the html standards it would work. 
Making platform-specific web sites is antithetical to the spirit and nature of the Web.  Intranets asides, such a practice may be an indication of drug use in the work place. ;)

---

### Post by bradhaack on 2011-04-15
> **rg4w said:**
> Making platform-specific web sites is antithetical to the spirit and nature of the Web.  Intranets asides, such a practice may be an indication of drug use in the work place. ;)

I like that, I'm going to start emailing that to the developers and the bosses.  Maybe the fear of drug testing will get them motivated ;)

---

### Post by Spr0k3t on 2011-04-15
There are few sites out there that I've run into like this.  More often than not I change my UserAgent manually to something like this:

Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0; // LINUX

Once I complete whatever I need on the site, I then send a message to the webmaster stating their site has been tested compliant on my system giving them the real UserAgent string (Mozilla/5.0 (X11; Linux x86_64; rv:2.0) Gecko/20100101 Firefox/4.0)

---

### Post by CraigPaleo on 2011-04-15
> **Spr0k3t said:**
> There are few sites out there that I've run into like this.  More often than not I change my UserAgent manually to something like this:

Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0; // LINUX

Once I complete whatever I need on the site, I then send a message to the webmaster stating their site has been tested compliant on my system giving them the real UserAgent string (Mozilla/5.0 (X11; Linux x86_64; rv:2.0) Gecko/20100101 Firefox/4.0)

I like this!

---

### Post by Paqman on 2011-04-15
> **bradhaack said:**
> 
From the comments it sounds like in the web developer world the standards are generally ignored

Not at all. Web designers and developers would *love it* if they could just work to the standards and have everything work everywhere. But in real life you have to insert all sorts of fudges to deal with various browser quirks. Folks building websites are very pro-standards in my experience.

---

### Post by bradhaack on 2011-04-15
> **Spr0k3t said:**
>  More often than not I change my UserAgent manually to something like this:

Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0; // LINUX


How do you do this?

---

### Post by jerenept on 2011-04-15
> **SeijiSensei said:**
> 
Just use [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") to tell the site you're running Windows.

> **bradhaack said:**
> How do you do this?

See, ma? No hands!

---

### Post by bodhi.zazen on 2011-04-15
> **Paqman said:**
> Not at all. Web designers and developers would *love it* if they could just work to the standards and have everything work everywhere. But in real life you have to insert all sorts of fudges to deal with various browser quirks. Folks building websites are very pro-standards in my experience.

+1

There are simply too many browsers and it is an exercise in futility to try to code a webpage that is compatible with each and every browser.

This is why web developers support standards, but frankly it is the browsers who ignore standards.

Look at html5 , some outstanding features, but support is browser - by - browser.

IMO we really need to ask the browsers become compliant, or at least standardized in how they render compliant code.

IMO a compliant strict xhtml page should render the same in all browsers, and it is the lack of such standardization in browsers that more often then not is the source of the problem.

---

### Post by handy on 2011-04-15
I use this method courtesy of tjwoosta:

[i]To override the useragent via about:config you just need to add a new key general.useragent.override (assuming you dont already have it from in the past) and set it to whatever string you want to use. You should be able to find one here:

[http://www.useragentstring.com/pages/useragentstring.php](http://www.useragentstring.com/pages/useragentstring.php)
[/i]

I don't do this for web page access, but (amongst other things) to make this machine less of an individual re. tracking.

---

### Post by earthpigg on 2011-04-15
> **Johnsie said:**
> ...Web standards are governed by a whole myriad of companies working together to ensure that the Internet is accessible to as many people as possible, including users who have physical disabilities. For more information about web standards please visit the site at [http://www.w3.org/standards/](http://www.w3.org/standards/)

holy crap, my wordpress blog fails the heck out of that with 
> Result: 	33 Errors

and i've always made efforts to ensure it was as accessible as possible.

bodhi.zazen's, by contrast, passed with no errors and only 1 warning.

EDIT: I will take solace from the fact that the "[RSS feed]("http://ctmason.wordpress.com/feed/")" seems to pass, and that a blind person told me the blog was more accessible than the official blog of Guide Dogs for the Blind. Moving forward, ill run future blog posts through that and see what can be addressed.

I need to look and see the cause of the errors. In order of my suspicion...
-the social networking stuff that i'm not educated enough to have coded or implemented myself?
-something inherent about how i post stuff?
-could it be as simple as the theme?
-wordpress.com's implementation of wordpress itself?
-wordpress itself?

---

### Post by bodhi.zazen on 2011-04-15
> **earthpigg said:**
> bodhi.zazen's, by contrast, passed with no errors and only 1 warning.

:twisted:

Thank you for visiting my site and taking the time to validate it.

The "warning" is only because I am using html5 , and there is no standard for html5 yet, thus the warning.

> Info Using experimental feature: HTML5 Conformance Checker.

    The validator checked your document with an experimental feature: HTML5 Conformance Checker. This feature has been made available for your convenience, but be aware that it may be unreliable, or not perfectly up to date with the latest development of some cutting-edge technologies. If you find any issues with this feature, please report them. Thank you.

Just citing that explanation ^^ in case people do not visit my site, take the time to look at the warning, or know html5.

And yes, I did clean up WP and it is a custom theme, although it is based on the default.

Mind you, not all my pages validate, I would have to clean up a ton of wordpress code, but they mostly validate.

---

### Post by CraigPaleo on 2011-04-15
> **bodhi.zazen said:**
> :twisted:

Thank you for visiting my site and taking the time to validate it.



I visited your site and had enough faith that I didn't have to validate it. ;)

---

### Post by earthpigg on 2011-04-15
> **CraigPaleo said:**
> I visited your site and had enough faith that I didn't have to validate it. ;)

I used it as a bar for comparison. :)

To answer the question "Well, mine fails. Are standards so high that virtually ***all*** web pages fail, though?"

The fact that this was the ***first*** question to pop into my head is telling of just how arrogant I am. Not that I have a problem with arrogance, to clarify.

---

### Post by earthpigg on 2011-04-15
I made a new blog for the purpose of attempting to introduce errors in an effort to discover from whence they come.

[http://masonplayground.wordpress.com/](http://masonplayground.wordpress.com/)

It will probably be more useful to read the posts from oldest -> newest so one can sequentially track what I did and if it introduced any errors.

---

### Post by CraigPaleo on 2011-04-15
I didn't run them through the validator but in both blogs, the text is larger in my Webkit browser. 

In the blog in your sig, I didn't even know there were blue borders on the left and right of the column when viewed with FF. I only saw them when viewing it with Rekonq (Webkit).

---

### Post by earthpigg on 2011-04-15
> **CraigPaleo said:**
> I didn't run them through the validator but in both blogs, the text is larger in my Webkit browser. 

In the blog in your sig, I didn't even know there were blue borders on the left and right of the column when viewed with FF. I only saw them when viewing it with Rekonq (Webkit).

yes, something I did seems to have messed with that theme. when i used that exact theme on my little playground above, it displayed correctly on ff.

---

### Post by earthpigg on 2011-04-15
ok, now I am making progress!

> Bad value 100% for attribute width on element img: Expected a digit but saw % instead.

```
<img src="http://url.of.png.image.here" alt="alt text is here." ***width="100%"*** /></a></p>
```

What am I supposed to use? I don't know the screen resolution or zoom level or windows size of the user's web browser and computer, so I use this relative percentage and it seems to render correctly. Sometimes I use 65%, sometimes 100%.

EDIT: ya know what, I'm gonna make a thread in the support section of ubuntuforums.org for the chit-chatting relevant to this experiment of mine - to allow this thread can get back on topic as laid out by its creator.

---

### Post by CraigPaleo on 2011-04-15
> **earthpigg said:**
> ok, now I am making progress!



What am I supposed to use? I don't know the screen resolution or zoom level or windows size of the user's web browser and computer, so I use this relative percentage and it seems to render correctly. Sometimes I use 65%, sometimes 100%.

EDIT: ya know what, I'm gonna make a thread in the support section of ubuntuforums.org for the chit-chatting relevant to this experiment of mine - to allow this thread can get back on topic as laid out by its creator.

Let us know where it is. I knew someone who had a site that looked good in both my Linux browser and my iPhone, when I had it. It was rare that I had seen that before and when I asked, she said it was because she used percentages. That's all I know.

Edit: I found it. [http://www.salvonix.us/](http://www.salvonix.us/)  The CSS is [http://www.salvonix.us/salvonix.css](http://www.salvonix.us/salvonix.css)

It looks kind of old now but it does scale well from a phone on up. The very top doesn't but the body does.

---

### Post by SeijiSensei on 2011-04-15
> **earthpigg said:**
> What am I supposed to use?

For images, the width and height should be specified in pixels.  In Firefox, use View Image, and you'll see the dimensions in the top of the window frame.

---

### Post by scott-ian on 2011-04-15
I think it's just that they don't care enough to test their site in Linux and change their user agent detector script accordingly.

---

### Post by earthpigg on 2011-04-15
once i make the thread, ill link to it in this one.

> **SeijiSensei said:**
> For images, the width and height should be specified in pixels.  In Firefox, use View Image, and you'll see the dimensions in the top of the window frame.

i know that is how it used to be done, and how i learned dabbling around with html in middle school when 90% of people had 14 inch 640x480 or 800x600 displays... i just thought that percentages was the modern way, to accommodate the diverse displays ranging from the 800ish by 600ish browser window up to being maximized on my own 28 inch display.

guess i was mistaken.

---

### Post by CraigPaleo on 2011-04-15
> **earthpigg said:**
> once i make the thread, ill link to it in this one.



i know that is how it used to be done, and how i learned dabbling around with html in middle school when 90% of people had 14 inch 640x480 or 800x600 displays... i just thought that percentages was the modern way, to accommodate the diverse displays ranging from the 800ish by 600ish browser window up to being maximized on my own 28 inch display.

guess i was mistaken.

I remembered her site and edited my last post. She still uses %. The CSS validates as well as all the web pages except for the "contact us" page. It does scale, I swear, from an iPhone to a large desktop monitor, 1680 x 1050. 

Horizontally shrink the window and you'll see what I mean. You don't have to scroll horizontally to read it on a phone.

---

### Post by CharlesA on 2011-04-15
You can do % for widths as long as they aren't images. You'd use CSS for that sort of thing, not HTML.

---

### Post by Ji Ruo on 2011-04-16
I'm sure there will be less and less websites that require a particular browser or operating system as time goes on. The web is changing rapidly, and increasingly being accessed from portable platforms which bring their own challenges. Which makes life fun for web developers. As to the future, who knows what the interfaces for the web will look like in 10 years? Short of any quantum leap in web interface design (3d virtual websites anyone?) the trend is going to be multiple devices, multiple oses and multiple browsers. Which means moves towards standardisation are highly likely to continue.
</aimlessrant>

---

### Post by earthpigg on 2011-04-16
> **Ji Ruo said:**
> As to the future, who knows what the interfaces for the web will look like in 10 years? Short of any quantum leap in web interface design (3d virtual websites anyone?) the trend is going to be multiple devices, multiple oses and multiple browsers. Which means moves towards standardisation are highly likely to continue.
</aimlessrant>

as many of us spend more and more time in our browser, i suspect that the web portal concept will come back in a big way with walled gardens all over the place.

facebook wants to be that, and so does google. pair that with things like Opera Unite & Link, and your OS/Device will become trivial.

part of me is surprised we haven't seen a facebook web browser, though SkyFire could make that claim. best app of 2010 bla bla bla.

my netbook is already little more than LXDE and Chromium on top of an encrypted /home and cursory login screen.... edit: attached. chromium starts at login, and i mostly consider it to be my desktop. ssh and pidgen also get some use.

once 11.04 comes out, im probably going to do a minimal install + openbox + chromium + pidgin and not ever update anything but chromium.

---

### Post by Johnsie on 2011-04-16
lol, my email is a little harsh, but the links in it were pretty good for pushing the whole standards thing. If somebody wants to reword it to something more friendly/appropriate rather than just writing it off and trolling me on these forums then that would be great. That's the beauty of open source You can change things to suit your own style. Sadly there will always be people who have nothing positive but some of the more positive suggestions in this thread are quite good.

Oh and if you're a professional programmer the last thing you want is for your boss to think your programming is shabby. That's why people tend not to ignore 'snobby' emails that are also cc'd to superiors ;-)

---

### Post by fdrake on 2011-04-17
try to validate a simple page like Google's page [http://google.com](http://google.com)
you find to have 36 Errors, and 2 warning(s) .
for a webmaster is almost impossible to make every  browser make look a complex page the same way. css are making  the work easier but not competly possible yet since many web browsers like ie do not respect w3c standards.

---

### Post by DoubleClicker on 2011-04-17
> **SeijiSensei said:**
> +1

This is almost always a pragmatic decision, not something driven by technical standards at all.  The site's owner(s) don't want to staff up to cover complaints from people using something other than Windows or OS X.  Ignoring the couple percent of Linux users often makes financial sense.

What will change this attitude, I suspect, is the growth of mobile devices. 

Just use [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") to tell the site you're running Windows.

Don't do that!!!!   If people change their user-agent string to say they are using windows, then web developers with greatly underestimate the number of linux users, making the problem even worse. The better approach is to email the webmaster of every website that doesn't support linux.  if everyone did that, webmasters would be more inclined to consider linux compatibility a worthwhile investment.

---

