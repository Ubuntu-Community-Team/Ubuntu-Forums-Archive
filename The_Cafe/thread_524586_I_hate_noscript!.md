---
title: "I hate noscript!"
date: 2007-08-13
forum: The Cafe
---

### Post by igknighted on 2007-08-13
What is the draw for this extension, I really don't understand.  All I see it doing is making my job as a web developer harder because javascript is an amazing tool that is being blocked by users... for what reason?  I mean, I avoid JS where I can because I prefer to use CSS and PHP where possible (I know them better), but there are some things that are simply best done with JS and everytime I use it I worry that users will needlessly block features of my website.

---

### Post by starcraft.man on 2007-08-13
Taken from [NoScript]("http://noscript.net/") Site:
> 
The NoScript Firefox extension provides extra protection for Firefox, Flock, Seamonkey and others mozilla-based browsers: this free, open source add-on allows JavaScript and Java execution only for trusted domains of your choice (e.g. your home-banking web site). **NoScript optionally blocks Flash and other potentially exploitable plugins too, and provides the most powerful Anti-XSS protection available in a browser.**

**NoScript's unique whitelist based pre-emptive script blocking approach prevents exploitation of security vulnerabilities (known and even not known yet!) with no loss of functionality...**

You can enable JavaScript/Java execution for sites you trust with a simple left-click on the NoScript status bar icon (look at the picture), or using the contextual menu, for easier operation in popup statusbar-less windows.
Watch the "Using NoScript" video kindly contributed by John Wilkerson.

Staying safe has never been so easy!

There you go. I use it even on GNU/Linux. The browser just may be the most insecure thing on most GNU/Linux desktops, it has already proven to be a serious vector for boat loads of trouble on the Windows side its best to head that trouble off. 

I don't see the problem, as said you can whitelist sites in two clicks. I do so when I trust sites (especially as you noted when JS functionality is blocked that I need). It's not going away so I suggest you deal with it.

---

### Post by juxtaposed on 2007-08-13
I don't use it, I see no point.

---

### Post by init1 on 2007-08-13
> **juxtaposed said:**
> I don't use it, I see no point. Neither do I.

---

### Post by M$LOL on 2007-08-13
It serves a useful purpose, blocking scripts is a very handy feature to have, especially on a Windows machine where you don't want anything malicious getting through.

---

### Post by Shazaam on 2007-08-13
Not a personal attack but my main reasons for NoScript are security and speed of page loading (along with AdBlock). I like to know what is loading in the background on a webpage.  What features do you need to load on your pages? Pop-ups, flashy banners, ad tracking? I have yet to see any advantages for the end user with js. Oh, and NoScript blocks CSS too.

---

### Post by runningwithscissors on 2007-08-13
> **igknighted said:**
> What is the draw for this extension, I really don't understand.  All I see it doing is making my job as a web developer harder because javascript is an amazing tool that is being blocked by users... for what reason?  I mean, I avoid JS where I can because I prefer to use CSS and PHP where possible (I know them better), but there are some things that are simply best done with JS and everytime I use it I worry that users will needlessly block features of my website.
I do some web development too at work, and I absolutely loathe javascript. People have abused it to make it do stuff it wasn't intended to do.
I usually block javascript too. Cut down on the 'features' and concentrate on the content. If it's important enough to be included, it should probably be on the server side.

---

### Post by a12ctic on 2007-08-13
Noscript is my favorite, and one of the few ff plugins I actualy find to be a necessity.  JS is annoying and so are little flash videos all over the place...

---

### Post by M$LOL on 2007-08-13
> **Shazaam said:**
> Oh, and NoScript blocks CSS too.
I haven't noticed that.
> **runningwithscissors said:**
> I do some web development too at work, and I absolutely loathe javascript. People have abused it to make it do stuff it wasn't intended to do.
I usually block javascript too. Cut down on the 'features' and concentrate on the content. If it's important enough to be included, it should probably be on the server side.
Javascript has its place and is very useful. I allow sites I trust to use it, because it can really add to the page, and there are some things you can't do on the server side. Not to mention that the whole AJAX concept depends on it.

However, I also think that sites should be designed to work perfectly well without javascript because some people block it, and others use browsers that don't support it.

---

### Post by igknighted on 2007-08-13
> **Shazaam said:**
> Not a personal attack but my main reasons for NoScript are security and speed of page loading (along with AdBlock). I like to know what is loading in the background on a webpage.  What features do you need to load on your pages? Pop-ups, flashy banners, ad tracking? I have yet to see any advantages for the end user with js. **Oh, and NoScript blocks CSS too**.

Haha, I doubt that greatly.  Try viewing ANY website without CSS, I highly doubt you would recognize it.

JS uses: form validation (making sure required fields, like a valid email, are filled out before allowing the submit to go through), dynamic effects (as simple as a mouse-over image change that was not well enough supported by CSS, or pretty much ANY web 2.0/AJAX site), and much much more.  Please, so some research before you rip apart technology that you do not understand.

> I do some web development too at work, and I absolutely loathe javascript. People have abused it to make it do stuff it wasn't intended to do.
I usually block javascript too. Cut down on the 'features' and concentrate on the content. If it's important enough to be included, it should probably be on the server side.

I agree that js has been used in ways not intended, and I hate coding js compared to php or CSS.  But there are many things that need to be done client side, if for nothing else then to take unnecessary loads off the server.  My webserver is decent, but not great (its really just a converted desktop), so there are things that just make sense to do client-side.

---

### Post by vexorian on 2007-08-13
> What is the draw for this extension, I really don't understand. All I see it doing is making my job as a web developer harder because javascript is an amazing tool that is being blocked by users...

Javascript is inherently insecure for users, I could crash an user's computer as long as he visited my javscript page with any browser supportive of it.


Don't be lazy always make your pages able to survive lack of javascript or at least show a message like "this page requires javascript" . Users will certainly not stop using noscript.

And no, noscript does not block CSS.

There are very pages I got whitelisted by default, noscript is awesome actually, it also functions as a great popup blocker (one that's actually effective...)

---

### Post by igknighted on 2007-08-13
> **vexorian said:**
> Javascript is inherently insecure for users, I could crash an user's computer as long as he visited my javscript page with any browser supportive of it.


Don't be lazy always make your pages able to survive lack of javascript or at least show a message like "this page requires javascript" . Users will certainly not stop using noscript.

And no, noscript does not block CSS.

There are very pages I got whitelisted by default, noscript is awesome actually, it also functions as a great popup blocker (one that's actually effective...)

How about an extension that restricts what js can do, or gives you a notification that a popup was attempted but doesn't open it without permission, or something along these lines.  Blocking entire features (and all the good that comes with them) to weed out a little bit of bad is like using a bazooka to kill a squirrell.  It's a blunt tool that, in the end, dilutes the richness that the web could have.

And yes, my site is fully usable without js, what I am protesting is that there is a need to avoid using what in many cases is THE BEST tool for the job.

---

### Post by starfry on 2007-08-13
I'm going to install noscript tonight. I think being able to control javascript, etc, on a per site basis is an excellent idea.

I think a web site should work without Javascript. It may only offer a sub-set of functions, perhaps reducing to "basic" mode, but it should still work.

I use Javascript to encrypt data for users not on SSL. If Javascript is disabled the user can choose to enable Javascript or continue authenticating in clear text.

---

### Post by OffHand on 2007-08-13
> **igknighted said:**
> What is the draw for this extension, I really don't understand.  All I see it doing is making my job as a web developer harder because javascript is an amazing tool that is being blocked by users... for what reason?  I mean, I avoid JS where I can because I prefer to use CSS and PHP where possible (I know them better), but there are some things that are simply best done with JS and everytime I use it I worry that users will needlessly block features of my website.

Cry me a river....

---

### Post by vexorian on 2007-08-13
noscript is the only reason I use firefox on linux and not epiphany since firefox's integration with gnome is terrible

---

### Post by distroman on 2007-08-13
“Wax off crap, wax on crap” “Wax off crap, wax on crap” “Wax off crap, wax on crap” Noscript is Kung Fu

---

### Post by igknighted on 2007-08-13
> **OffHand said:**
> Cry me a river....

And what use would you have for said river?  Or would you just make some unecessary, snide comment about that too...

---

### Post by Xzallion on 2007-08-13
Personally, I hate Javascript, and everything that can be done with it can be done server side.  Your annoyed that your users are blocking it and trying to tell them its the best tool, when you should realize that they apparently don't like Javascript and are going out of their way to avoid it.  Your complaining about web 2.0 making things like this necessary, when the only thing that has ever been necessary on the web is the ability to adapt.

So quit worrying, the users that like your site will whitelist it, design your sites without Javascript, or find another way to do what you want that doesn't get blocked.  Your not going to change your users minds.

---

### Post by ThinkBuntu on 2007-08-13
"Personally, I want to set JavaScript on fire. But my web experience would be dull and drab without it. But still!"

Please, people. How do you expect to navigate through tabbed content inside a webpage if it depends on a script? That is a legitimate use of JavaScript to save space and improve usability, assuming the underlying HTML is semantic and accessible.

I'm a full-time web developer, and while I do avoid using scripts when I can, it's a very valuable tool that is great for enhancing websites without having to resort to something ten times worse than JavaScript: **Flash!!**

Luckily for us designers and developers, 95% of the browsing population has never heard of JavaScript except in passing, and only 1% or fewer know that it can create security vulnerabilities.

---

### Post by OffHand on 2007-08-13
> **igknighted said:**
> And what use would you have for said river?  Or would you just make some unecessary, snide comment about that too...

Nah - what user want to do with their machines/browsers is none of your business.

---

### Post by FuturePilot on 2007-08-13
[S]I hate it too. I don't see any use in it. It just makes surfing around more difficult. I don't use it.[/S]

[http://ubuntuforums.org/showpost.php?p=8358165&postcount=69]("http://ubuntuforums.org/showpost.php?p=8358165&postcount=69")

---

### Post by LaRoza on 2007-08-13
ECMAScript is the last layer of content, style and behavior. Sites should degrade gracefully, if script is not working, style is not working, the content should still work.

ECMAScript is a tool, use it, but don't rely on it.

---

### Post by Shazaam on 2007-08-13
Cascading Style Sheets or Cross Site Scripting? If the former I apologize; if the latter, from the FAQ-
4.1
Q:   What is XSS and why should I care?
A:   XSS stands for Cross site scripting, a web application vulnerability which allows the attacker to inject malicious code from a certain site into a different site, and can be used by an attacker to "impersonate" a different user or to steal valuable information. This kind of vulnerability has clear implications for NoScript users, because if a whitelisted site is vulnerable to a XSS attack, the attacker can actually run JavaScript code injecting it into the vulnerable site and thus bypassing the whitelist. That's why NoScript features unique and very effective Anti-XSS protection functionality, which prevents untrusted sites from injecting JavaScript code into a trusted web page via reflective XSS and makes NoScript's whitelist bullet-proof.

[http://noscript.net/features#xss](http://noscript.net/features#xss)

---

### Post by starcraft.man on 2007-08-13
> **igknighted said:**
> **How about an extension that restricts what js can do, or gives you a notification that a popup was attempted but doesn't open it without permission, or something along these lines.**  Blocking entire features (and all the good that comes with them) to weed out a little bit of bad is like using a bazooka to kill a squirrell.  It's a blunt tool that, in the end, dilutes the richness that the web could have.

And yes, my site is fully usable without js, what I am protesting is that there is a need to avoid using what in many cases is THE BEST tool for the job.

No Script already does this, it filters out all JS by default and shows you what domains are originating it (i.e. the website and third parties). If I need a feature, I click the no script bar at bottom find your domain and whitelist it for session or indefinitely. This system emphasizes security over convenience and IMO I'd rather be secure. What could possibly be improved on this model of security with JS? Would you rather your site being white/black listed was in the hands of a third party instead of the end user? I've heard horror stories from some black listing services, I don't find that to be better...

> **ThinkBuntu said:**
> 
Please, people. **How do you expect to navigate through tabbed content inside a webpage if it depends on a script?** That is a legitimate use of JavaScript to save space and improve usability, assuming the underlying HTML is semantic and accessible.


Push no script icon and whitelist. Problem solved. No one who installs no script need cut all JS from their life, just what they don't trust/approve of. It is snap to filtering and can be changed on the fly. I don't see the problem with empowering the user with the ability to ensure security of his/her system, it is their system after all not a web developers.

> I'm a full-time web developer, and while I do avoid using scripts when I can, it's a very valuable tool that is great for enhancing websites without having to resort to something ten times worse than JavaScript: **Flash!!**

**Luckily for us designers and developers, 95% of the browsing population has never heard of JavaScript except in passing, and only 1% or fewer know that it can create security vulnerabilities.**

Excuse me but I really don't like that statement you just made. First of all I think the number is a lot larger than you stated. No Script has [floated at the top of popular extensions]("https://addons.mozilla.org/en-US/firefox/browse/type:1") (in the top 5) on the addon page for ages, even speculating on a 50% (or less) retention rate for downloaders given the massive number of regular firefox users (estimated at 20-25% overall and over 30-50% in Europe) it is considerably larger than 1% of Firefox users I'd say.

Secondly, condoning and wishing for the perpetuity of ignorance (as your post inferred) of a population on the topic of security when browsing is a heinous thought IMO. People get viruses and other malware because they don't know better about securing themselves (i.e. router set up, firewalls, AVs, etc... even JS). Ignorance is never something that should be promoted, rather education on all sides of the matter and allow the end user to decide what is best. It is the end user's desktop and computer after all and empowering them to take control of their desktop is one of the core aims of the OSS movement I think.

I never thought it was so controversial. I am not sure why you two are taking such stances on this JS matter (against no script), it allows for JS when the _user approves_, nothing wrong with user control. Have you misunderstood how it works?

Oh and I've no idea where this "No Script stops CSS" (mentioned by others) comes from. CSS (Cascading Style Sheets) for sites works fine, XSS (Cross Site Scripting) is what is targeted (unless I've been reading wrong information). Let's not have any more confusion on that point.

---

### Post by LaRoza on 2007-08-13
> **Shazaam said:**
> Cascading Style Sheets or Cross Site Scripting? If the former I apologize; if the latter, from the FAQ-


I was refering to Cascading Style Sheets.

My point was that a site should not rely on CSS and ECMAScript (or multimedia). A script should degrade gracefully.

So the OP frustration was unfounded, as noscript should not make the site unusable.

---

### Post by ThinkBuntu on 2007-08-13
> **starcraft.man said:**
> No Script already does this, it filters out all JS by default and shows you what domains are originating it (i.e. the website and third parties). If I need a feature, I click the no script bar at bottom find your domain and whitelist it for session or indefinitely. This system emphasizes security over convenience and IMO I'd rather be secure. What could possibly be improved on this model of security with JS? Would you rather your site being white/black listed was in the hands of a third party instead of the end user? I've heard horror stories from some black listing services, I don't find that to be better...



Push no script icon and whitelist. Problem solved. No one who installs no script need cut all JS from their life, just what they don't trust/approve of. It is snap to filtering and can be changed on the fly. I don't see the problem with empowering the user with the ability to ensure security of his/her system, it is their system after all not a web developers.



Excuse me but I really don't like that statement you just made. First of all I think the number is a lot larger than you stated. No Script has [floated at the top of popular extensions]("https://addons.mozilla.org/en-US/firefox/browse/type:1") (in the top 5) on the addon page for ages, even speculating on a 50% (or less) retention rate for downloaders given the massive number of regular firefox users (estimated at 20-25% overall and over 30-50% in Europe) it is considerably larger than 1% of Firefox users I'd say.

Secondly, condoning and wishing for the perpetuity of ignorance (as your post inferred) of a population on the topic of security when browsing is a heinous thought IMO. People get viruses and other malware because they don't know better about securing themselves (i.e. router set up, firewalls, AVs, etc... even JS). Ignorance is never something that should be promoted, rather education on all sides of the matter and allow the end user to decide what is best. It is the end user's desktop and computer after all and empowering them to take control of their desktop is one of the core aims of the OSS movement I think.

I never thought it was so controversial. I am not sure why you two are taking such stances on this JS matter (against no script), it allows for JS when the _user approves_, nothing wrong with user control. Have you misunderstood how it works?

Oh and I've no idea where this "No Script stops CSS" (mentioned by others) comes from. CSS (Cascading Style Sheets) for sites works fine, XSS (Cross Site Scripting) is what is targeted (unless I've been reading wrong information). Let's not have any more confusion on that point.
OK, thank you William H. Harrison.

P.S. That would be the lengthiest US Presidential inaugural speaker. 8,500 words, count 'em baby!

---

### Post by M$LOL on 2007-08-13
What's wrong with stylesheets? Apart from the fact that pretty much every modern site used them, they're a lot better than coding everything directly into the html file. Unlike JS, they can't actually *do* anything...

---

### Post by LaRoza on 2007-08-13
> **M$LOL said:**
> What's wrong with stylesheets? Apart from the fact that pretty much every modern site used them, they're a lot better than coding everything directly into the html file. Unlike JS, they can't actually *do* anything...

If you are refering to my posts, nothing is wrong with them, in fact, I use CSS for all layout, no tables except for actual tables.

When designing a site, it is important to make sure the content, which is the most important, does not rely on anything that could be blocked or not work. In terms of importance, content is first, style is second and behavior is third (last). Each ENHANCES the site, and should degrade gracefully if it fails.

I seperate markup, style and script. No Script and CSS are mixed in my markup.

---

### Post by igknighted on 2007-08-13
> **LaRoza said:**
> I was refering to Cascading Style Sheets.

My point was that a site should not rely on CSS and ECMAScript (or multimedia). A script should degrade gracefully.

So the OP frustration was unfounded, as noscript should not make the site unusable.

not unusable != not annoying.

Imagine if the US Gov recommended everyone walk around with welding goggles because the suns rays are dangerous and could hurt your eyes.  Sure you would make do, and be safer, and even could take them off at will.  But wearing them would make you miss a lot that the world has to offer.  Same with no script.  Blocking site content by default is just a bad idea.  Limit the access to the local machine, OK.  Warn before allowing a pop-up, OK.  But default limitation of features is just a bad policy, IMO.

---

### Post by starcraft.man on 2007-08-13
> **ThinkBuntu said:**
> OK, thank you William H. Harrison.

P.S. That would be the lengthiest US Presidential inaugural speaker. 8,500 words, count 'em baby!

Uh, that's not that funny...

Anyway, it's already been firmly established that I'm long winded in my posts (when involved in serious discussion). That is because I like to be correct in my statements/assertions rather than just saying things like "your wrong". Nothing else to add?

---

### Post by DigitalDuality on 2007-08-13
d

---

### Post by starcraft.man on 2007-08-13
> **igknighted said:**
> not unusable != not annoying.

Imagine if the US Gov recommended everyone walk around with welding goggles because the suns rays are dangerous and could hurt your eyes.  Sure you would make do, and be safer, and even could take them off at will.  But wearing them would make you miss a lot that the world has to offer.  Same with no script.  Blocking site content by default is just a bad idea.  Limit the access to the local machine, OK.  Warn before allowing a pop-up, OK.  **But default limitation of features is just a bad policy, IMO.**

And that's x person's choice to listen or not to the recommendation. Your preference is convenience (as indicated, or a lesser restriction). Other end user's believe security is more important than convenience. Your both free to make your own decisions with regard to No Script, that's the freedom of choice and that freedom it appears to me is an integral value that the GNU/Linux community tries to promote. People are also free to promote what they believe is the best policy to others, it's up to the individual to evaluate what he/she knows and what their told and make the best decision.

Edit:
Oh and if you want NoScript's default policies changed, then I suggest you [contact it's authors.]("http://www.informaction.com/index.php?page=contacts") The only other course of action it seems to me is to make your own project that functions how you like and release it as an addon for firefox. This whole discussion is likely to net very little in actual effect on people and browsing (I'm sure there are a lot more Windows users using no script than there are Linux users, that is just a guess though).

---

### Post by Darkhack on 2007-08-13
I find it very odd everyone is arguing over NoScript while missing the most important thing about this entire discussion.

**Browser security is NOT the user's responsibility.**

Oh my god!  What did he just say?!  NO?!  Yes, I said it.  When it comes to security the user does have a responsibility.  Their responsibility is to not give out passwords and avoid phishing sites.  There are other things as well that I can't think of at the moment but it always makes my blood boil to see advanced users miss the entire point of a computer.

**My computer is supposed to work for me... not the other way around.**

I should have to worry as little as possible about security.  This is one of the reasons that people flame Windows and switch to Linux.  It is because of the poor security that Windows provides.  Linux solves this by having a firewall built in and being written in a secure fashion so that viruses are almost non-existent.  Same with hardware even.  A lot of hardware works out of the box on Linux because the drivers are built into the kernel unlike Windows where I have to install drivers manually through a CD or from an executable I downloaded off the manufacturer's website.  Things should "just work".

If you have any security problems with javascript, check Bugzilla to see if it exists and if not, file a new bug report.  Javascript does serve a purpose.  That purpose is to be able to alter HTML on the fly, interact with the server without reloading the page (AJAX), and overall provide a smoother and more interactive experience.  If javascript is not meeting that goal and is instead causing a security issue, then it is a bug.

I assume that all those who have posted thus far are just normal users.  However, if anyone here happens to have commit access to Firefox and you are a developer.  Please, quit now!  You have missed the entire point of software and are not worthy to work on the source code for my primary browser.  Firefox is open source and we should strive to make it as perfect as possible.  As soon as we start settling for less, it won't be long before Firefox becomes just as bad as Internet Explorer.

---

### Post by starcraft.man on 2007-08-13
> **Darkhack said:**
> I find it very odd everyone is arguing over NoScript while missing the most important thing about this entire discussion.

**Browser security is NOT the user's responsibility.**

Oh my god!  What did he just say?!  NO?!  Yes, I said it.  When it comes to security the user does have a responsibility.  Their responsibility is to not give out passwords and avoid phishing sites.  There are other things as well that I can't think of at the moment but **it always makes my blood boil to see advanced users miss the entire point of a computer.**


I think your definition of a computer must be different from mine. A computer (as I see it) is designed to do what the _user wants_, if said user wants to assume responsibility for security of his browser (and by extension ensuring more security for his desktop) then that's his choice (as I've stipulated countless times before). Freedom to do what you want with your computer is the most fundamental principle that the computer is based on (some proprietary companies would disagree wanting to limit what you can do with some features). That's how I see it.

Now as to your point, your free to rely on the browsers security (beyond securing password and phishing sites), but it has been proven countless times that (Firefox, IE and Opera) all had undiscovered exploits that allowed malicious execution (some for weeks/months before fix). Said exploits often used XSS and or JS on sites, NoScript prevents those. There's the logical path, you can choose to rely on your browser or you can be proactive about security (like having an AV on Windows) and try extra hard to stop said problems before hand.

Your right, security should be as simple and hassle free as possible. That doesn't mean the user can't take it in his own hands to be more secure if he so chooses, and no one should force him/her to pick one way or another, it's his choice. That is why NoScript is an add on, you have to _choose_ to install it.

> **My computer is supposed to work for me... not the other way around.**

I should have to worry as little as possible about security.  This is one of the reasons that people flame Windows and switch to Linux.  It is because of the poor security that Windows provides.  Linux solves this by having a firewall built in and being written in a secure fashion so that viruses are almost non-existent.  Same with hardware even.  A lot of hardware works out of the box on Linux because the drivers are built into the kernel unlike Windows where I have to install drivers manually through a CD or from an executable I downloaded off the manufacturer's website.  Things should "just work".

If you have any security problems with javascript, check Bugzilla to see if it exists and if not, file a new bug report.  Javascript does serve a purpose.  That purpose is to be able to alter HTML on the fly, interact with the server without reloading the page (AJAX), and overall provide a smoother and more interactive experience.  If javascript is not meeting that goal and is instead causing a security issue, then it is a bug.


Your right, things should be simple and easy (and require little effort from the user). That doesn't however mean that a user shouldn't be able to proactively head off exploits and other malicious problems (which have and still likely do exist) with his browser if he so chooses.

Your arguments are moot, companies try their best to code fixes (and new features) and ensure security and they aren't perfect. NoScript is an extra step users can take if they wish to as a preventative. If there were no new exploits ever then no script wouldn't be needed. It's not a perfect world though.

Oh and this:
> I assume that all those who have posted thus far are just normal users.  **However, if anyone here happens to have commit access to Firefox and you are a developer.  Please, quit now!  You have missed the entire point of software and are not worthy to work on the source code for my primary browser. ** Firefox is open source and we should strive to make it as perfect as possible.  As soon as we start settling for less, it won't be long before Firefox becomes just as bad as Internet Explorer.

was very childish IMO. Defending NoScript doesn't make you a bad developer, it is a choice and people should be free to use it.

Editorial:
Frankly, I don't get any of your arguments against NoScript. It is an [_add-on_,]("https://addons.mozilla.org/en-US/firefox/addon/722") people choose to install it, that's a choice their free to make (based on what they know). Just like their free to choose any distribution of GNU/Linux they like. People can easily permit JS to be run when using no script. And using no script doesn't stop developers from coding security fixes, it is a preventative tool to try and stop them when they aren't fixed but used to exploit your system. It requires a few extra clicks from a user, and if they don't want those extra clicks they don't install it.

---

### Post by jrusso2 on 2007-08-13
> **igknighted said:**
> What is the draw for this extension, I really don't understand.  All I see it doing is making my job as a web developer harder because javascript is an amazing tool that is being blocked by users... for what reason?  I mean, I avoid JS where I can because I prefer to use CSS and PHP where possible (I know them better), but there are some things that are simply best done with JS and everytime I use it I worry that users will needlessly block features of my website.

Javescript has become a major attack vector.  Most of the fixes to Firefox have been security issues caused by java script and CSS attacks.

Developers should stop using Javascript so we don't have to block it to be secure.

---

### Post by starcraft.man on 2007-08-13
> **jrusso2 said:**
> Javescript has become a major attack vector.  Most of the fixes to Firefox have been security issues caused by java script and **CSS** attacks.

Developers should stop using Javascript so we don't have to block it to be secure.

Just a friendly note jrusso but when referring to Cross Site Scripting best to use the abreviation XSS, so as not to have confusion with CSS (as was done previously in the thread). Cascading Style Sheets are fine far as I know.

I do agree, most new exploits and serious threats have had a JS or XSS component either to exploit information from the browser (a la secure log in info) or have malicious software installed (a la remote code execution). I'm sticking to NoScript.

---

### Post by Atreus12 on 2007-08-13
Noscript is the second addon I install, everytime I have to set up firefox (The first being adblock). 

The point is, if I want a website to run scripting, then I allow it. Otherwise it can't run scripting. It just makes sense.....

-Andrew

---

### Post by Altarbo on 2007-08-13
> **igknighted said:**
> not unusable != not annoying.

Imagine if the US Gov recommended everyone walk around with welding goggles because the suns rays are dangerous and could hurt your eyes.  Sure you would make do, and be safer, and even could take them off at will.  But wearing them would make you miss a lot that the world has to offer.  Same with no script.  Blocking site content by default is just a bad idea.  Limit the access to the local machine, OK.  Warn before allowing a pop-up, OK.  But default limitation of features is just a bad policy, IMO.You would not be able to see at all with welding goggles on.  Shades four and five are usually used for lower heat cutting.

I do not take a risk by walking around without any type of goggles on.   I _would_ be taking a risk if I stared at the sun (or a weld pool) so I don't.  This is exactly like noscript.  By putting on goggles to cut (or weld) I'm blacklisting metal working.  

Asking users to keep javascript on all the time because you've made your website reliant on it, is like marking lines on metal to be cut in some dull reddish chalk (Soapstone is normally used because it is unaffected by heat and very visible.) and then demanding that your employees/coworkers/whatever not use goggles ever, to make your job easier.

---

### Post by userundefine on 2007-08-13
> **ThinkBuntu said:**
> Please, people. How do you expect to navigate through tabbed content inside a webpage if it depends on a script? That is a legitimate use of JavaScript to save space and improve usability, assuming the underlying HTML is semantic and accessible.
Then you don't visit that page.  ANY website that relies **solely** on javascript to deliver or navigate content is absolutely **un**accessible and is poorly designed.

I use noscript, AND I like javascript and develop with it a bit.  It can be pretty cool.  For sites that I trust, I whitelist their sites and allow the javascript to execute.  But just browsing the web does not mean I have to put up with all the crap or poorly coded javascript that's out there.

OP, your javascript may be just great and your visitors will whitelist you.  If not, I hope your site doesn't whitepage because it can't use getElementById.  Seriously, ever heard of unobtrusive javascript?

---

### Post by super breadfish on 2007-08-13
The whole point of NoScript is to allow Javascript on the sites you trust, and block it on the ones you don't. If a web designer is making a site that people don't trust, well, that's their problem, not mine.

NoScript increases security, privacy and stops a lot of the irritating crap on websites. I use Firefox and a NoScript/Adblock combo on all my computers.

---

### Post by Darkhack on 2007-08-13
> **starcraft.man said:**
> I think your definition of a computer must be different from mine. A computer (as I see it) is designed to do what the _user wants_, if said user wants to assume responsibility for security of his browser (and by extension ensuring more security for his desktop) then that's his choice (as I've stipulated countless times before). Freedom to do what you want with your computer is the most fundamental principle that the computer is based on (some proprietary companies would disagree wanting to limit what you can do with some features). That's how I see it.

Your right, security should be as simple and hassle free as possible. That doesn't mean the user can't take it in his own hands to be more secure if he so chooses, and no one should force him/her to pick one way or another, it's his choice. That is why NoScript is an add on, you have to _choose_ to install it.

Fair enough.  I concede.  You are correct in that the user should have the right to choose if they want to.  My point was that the user shouldn't **have to** rely on NoScript for security, but you are correct in that it is a good extension for those who like more control.

> **starcraft.man said:**
> Defending NoScript doesn't make you a bad developer, it is a choice and people should be free to use it.

True, but with one exception.  It makes them a bad developer if they think that NoScript is the solution to javascript exploits instead of fixing them in the source code.  Otherwise, you are correct.  NoScript is a good choice for those who wish to have it.

---

### Post by Polygon on 2007-08-13
i love noscript. it blocks annoying crap that i see websites trying to run when im just visiting it temporarily

if its a site that i know that is safe, then i set it to allow. simple as that.

if your a web developer, simply make it so that if javascript is diabled (noscript), then display a message that javascript is required to display everything correctly on the page. problem solved..

---

### Post by starcraft.man on 2007-08-13
> **Darkhack said:**
> Fair enough.  I concede.  You are correct in that the user should have the right to choose if they want to.  My point was that the user shouldn't **have to** rely on NoScript for security, but you are correct in that it is a good extension for those who like more control.


The user **doesn't have to** rely on NoScript though, in the same way said user doesn't have to use an AV/spyware (or other services similar) on Windows (I don't on my XP installs, both VM and actual. I actually believe I have more chances of getting hit by code through NoScript than a virus from other means.) That has to do with my behaviour though and being very careful. XP now comes with a firewall in SP2 and above and for some that is enough security, for others the need for one AV and one spyware cleaner is essential. Some others want even more.

It's all about degree of security and how protected you need to be. Firefox in itself is pretty darn secure I think. Firefox + NoScript (and a few other enhancements I like) = nearly rock solid (barring a new exploit not anticipated or blocked by NoScript and the other extensions).

> True, but with one exception.  **It makes them a bad developer if they think that NoScript is the solution to javascript exploits instead of fixing them in the source code. ** Otherwise, you are correct.  NoScript is a good choice for those who wish to have it.

That isn't how they think though (least from what I see). NoScript was started as and likely will be for a long time, an add-on (unless Firefox 3.0 plans have changed to include it). As such, it's never been endorsed or otherwise pushed on users by Mozilla (any of it's embodiments to my knowledge, simply uploaded as one of the many add-ons to choose from). It has been promoted (as all other add-ons, and Firefox itself was) as a security enhancement that can protect said end user from unpatched exploits in Firefox itself that are triggered or executed via JS or XSS. It's always been the same, and I don't think any Developer would ever rely on a third party to fix vulnerabilities in their code, they still fix those for everyone.

---

### Post by original_jamingrit on 2007-08-13
This is a very multisided issue.

> **igknighted said:**
> ...All I see it doing is making my job as a web developer harder because javascript is an amazing tool that is being blocked by users...  but there are some things that are simply best done with JS ...

> **userundefine said:**
> ...It can be pretty cool.  For sites that I trust, I whitelist their sites and allow the javascript to execute.  But just browsing the web does not mean I have to put up with all the crap or poorly coded javascript that's out there...

> **starcraft.man said:**
> ...most new exploits and serious threats have had a JS or XSS component ...

> **Darkhack said:**
> ...When it comes to security the user does have a responsibility.  Their responsibility is to not give out passwords and avoid phishing sites.  There are other things as well that I can't think of at the moment but it always makes my blood boil to see advanced users miss the entire point of a computer.

**My computer is supposed to work for me... not the other way around.**

I should have to worry as little as possible about security...

> **super breadfish said:**
> The whole point of NoScript is to allow Javascript on the sites you trust, and block it on the ones you don't. If a web designer is making a site that people don't trust, well, that's their problem, not mine.

Let's focus on some things that are solid facts.
[COLOR="Red"]
FACT:  Javascript and concepts like AJAX are changing the way people browse the Internet and the way designers write website.[/COLOR]

You see Javascript all over the place these days.  It's powerful enough, it's popular enough.  Using javascript to send AJAX transactions can turn webpages into full on applications.  They have word processors on websites now, that behave like normal text editors except that your files are being saved and backed up on a server somewhere, so you can access it from any computer that can connect to that server.  They have AJAX-controlled databases, AJAX-controlled spreadsheets, even Facebook is heavy in AJAX now.  Why would anyone want to turn their back on such beauty??? 
[COLOR="Red"]
FACT:  Javascript was not engineered to have a conscience.[/COLOR]

A few years back, most browsers experienced most of their growing pains because of stupid attacks.  I was in high school during this time, and we always had fun with such classics as [COLOR="Blue"]The Infinite Confirmation Prompt[/COLOR], and the [COLOR="Blue"]New Hidden Browser Windows[/COLOR] that loaded somewhere not noticeable to deliver popups, and my favourite; the [COLOR="Blue"]Javascript PNG Comment[/COLOR], because silly IE6 can't tell the difference between an HTML page and a PNG image untill it's already run the javascript inserted in the PNG's comment element.

These days, browsers are smarter, and recognize infinite loops and such before running them.  But Javascript is still capable of malicious activity.  If it weren't, it would not be as powerful or as useful as it is.  Those features of Javascript are also sometimes its bugs.  I don't know enough about Javascript to know if it's possible to crash your (non-ie6) browser with it, so I won't talk about System Security, but I do know that confidential information is not always kept safe.  *Sometimes* accessing some information can be just as easy as stealing ornaments off of your neighbours lawn,  when they're left right there in easy reach and not in a secure place on your system.  Or maybe the javascript usage is like the myspace thing, where that guy [Samy]("http://en.wikipedia.org/wiki/Myspace#Security") used XSS to automatically friend everyone who visited his page, and then everyone who visited *thier* page, and everyone who visited etc; (Myspace was filtering the phrase that he needed, but he could do it because he broke up the phrase and got it through their filter that way).
[COLOR="Red"]
FACT:  It's called Noscript, not Neverscript.[/COLOR]

Okay, the basic answer is that Noscript does NOT kill all of the Javascript in the world.  That would be like killing all the puppies in the world.  The whitelist system allows you to allow Javascript only on websites you trust, with no weird security holes involved.  No chance of your browser being tricked into running javascript on from someone not white-listed.  If Noscript disabled Javascript completely, it's be no different that manually disabling it in your firefox preferences yourself.

So what do you do, when people do not trust your code?  Well you can A: Alienate people who don't know you well enough to trust your website, or your can B: let your site degrade a little more gracefully.

Here's a good idea, maybe insert a warning in plain HTML [COLOR="Blue"](This site uses Javascript, please enable Javascript for this page for the full experience)[/COLOR].  It's simple enough to just write that as plain text on your page, and then use javascript to remove that line when javascript has been enabled.  If they don't trust you enough, or maybe if for some reason they simply can't use javascript (think backwards-compatible), then let your website at least be usable, and maybe even still keep some visual apeal while you're at it.  That what makes the difference between a web designer and a code monkey, being able to keep it simple and elegant when you can't have it made of awesome.

[/long lengthy spiel]

---

### Post by starcraft.man on 2007-08-13
> **original_jamingrit said:**
> This is a very multisided issue.


Not so much, mostly paraphrasing. It really just seems to be mostly the same old debate, convenience vs. security (with a few variations on the conveniance side). Been going on for ages.

> Let's focus on some things that are solid facts.
[COLOR="Red"]
FACT:  Javascript and concepts like AJAX are changing the way people browse the Internet and the way designers write website.[/COLOR]

You see Javascript all over the place these days.  It's powerful enough, it's popular enough.  Using javascript to send AJAX transactions can turn webpages into full on applications.  They have word processors on websites now, that behave like normal text editors except that your files are being saved and backed up on a server somewhere, so you can access it from any computer that can connect to that server.  They have AJAX-controlled databases, AJAX-controlled spreadsheets, even Facebook is heavy in AJAX now.  Why would anyone want to turn their back on such beauty??? 
Agreed. AJAX can be mighty cool. :D

> [COLOR="Red"]
FACT:  Javascript was not engineered to have a conscience.[/COLOR]
It should have been!!!! :p
> 
A few years back, most browsers experienced most of their growing pains because of stupid attacks.  I was in high school during this time, and we always had fun with such classics as [COLOR="Blue"]The Infinite Confirmation Prompt[/COLOR], and the [COLOR="Blue"]New Hidden Browser Windows[/COLOR] that loaded somewhere not noticeable to deliver popups, and my favourite; the [COLOR="Blue"]Javascript PNG Comment[/COLOR], because silly IE6 can't tell the difference between an HTML page and a PNG image untill it's already run the javascript inserted in the PNG's comment element.

These days, browsers are smarter, and recognize infinite loops and such before running them.  But Javascript is still capable of malicious activity.  If it weren't, it would not be as powerful or as useful as it is.  Those features of Javascript are also sometimes its bugs.  I don't know enough about Javascript to know if it's possible to crash your (non-ie6) browser with it, so I won't talk about System Security, but I do know that confidential information is not always kept safe.  *Sometimes* accessing some information can be just as easy as stealing ornaments off of your neighbours lawn,  when they're left right there in easy reach and not in a secure place on your system.  Or maybe the javascript usage is like the myspace thing, where that guy [Samy]("http://en.wikipedia.org/wiki/Myspace#Security") used XSS to automatically friend everyone who visited his page, and then everyone who visited *thier* page, and everyone who visited etc; (Myspace was filtering the phrase that he needed, but he could do it because he broke up the phrase and got it through their filter that way).
Mostly agreed. Many problems with JavaScript trace back to the fact that it was designed without security as the utmost top priority (at least it seems so from everything I've read/seen, could be wrong), it was about getting extra functionality on the web. It was created in 95-96 for those who don't know... things were basic on the web back then. Had a little more care been taken in how the language itself worked and how it was handled/interacted in/with browsers and how browsers interacted with the OS, it's likely we would have had a hell of a lot less problems than IE6 was. Course, some of that was just plain complacency and asking for it...

Oh and yes, you can (at least in the past) crash (to my knowledge) non-ie6 browsers with JavaScript. Certainly seen things done to Firefox, and to a slightly smaller extent Opera. Mostly I think it really just has to do with which browser most people are using, it then gets banged on the most by script kiddies who in turn want to hit the largest target and may the quick money off of it.

> [COLOR="Red"]
FACT:  It's called Noscript, not Neverscript.[/COLOR]

Okay, the basic answer is that Noscript does NOT kill all of the Javascript in the world.  That would be like killing all the puppies in the world.  The whitelist system allows you to allow Javascript only on websites you trust, with no weird security holes involved.  No chance of your browser being tricked into running javascript on from someone not white-listed.  If Noscript disabled Javascript completely, it's be no different that manually disabling it in your firefox preferences yourself.

So what do you do, when people do not trust your code?  Well you can A: Alienate people who don't know you well enough to trust your website, or your can B: let your site degrade a little more gracefully.

Here's a good idea, maybe insert a warning in plain HTML [COLOR="Blue"](This site uses Javascript, please enable Javascript for this page for the full experience)[/COLOR].  It's simple enough to just write that as plain text on your page, and then use javascript to remove that line when javascript has been enabled.  If they don't trust you enough, or maybe if for some reason they simply can't use javascript (think backwards-compatible), then let your website at least be usable, and maybe even still keep some visual apeal while you're at it.  That what makes the difference between a web designer and a code monkey, being able to keep it simple and elegant when you can't have it made of awesome.
I've been trying to get this bloody fact across the whole thread, is there a reason no one's been listening to me saying sites can be whitelisted? Hopefully you highlighting in red will make it clear. :)

> [/long lengthy spiel]
HA! And they say I'm long winded. :p

---

### Post by runningwithscissors on 2007-08-14
> **igknighted said:**
> JS uses: form validation (making sure required fields, like a valid email, are filled out before allowing the submit to go through), dynamic effects (as simple as a mouse-over image change that was not well enough supported by CSS, or pretty much ANY web 2.0/AJAX site), and much much more.  Please, so some research before you rip apart technology that you do not understand.
If you depend upon client side validation of data, you're busted anyway. Anyone can modify javascript sent to the client-side. If you're storing data into your filesystem/database without server side validation, it's just asking for trouble.
Also, mouseover image changes and stuff are hardly must-have features.

And oh, Web 2.0 (whatever that is) and AJAX can lick my balls.

---

### Post by Darkhack on 2007-08-14
> **runningwithscissors said:**
> If you depend upon client side validation of data, you're busted anyway. Anyone can modify javascript sent to the client-side. If you're storing data into your filesystem/database without server side validation, it's just asking for trouble.
Also, mouseover image changes and stuff are hardly must-have features.

He didn't mean to depend upon javascript for validation.  He just meant that it can be used to warn the user ahead of time instead of having to hit submit before seeing that they messed up.  For example, I can use javascript to gray out the submit button until all the forms have been filled out.  I can also have javascript detect if a password field (on a registration form) has enough characters in it and if not display a message in red saying "Password is too short" when the field loses focus, but has text in it.  Also, no one said mousovers were must have features.  It looks nice though and adds on to the style.  We might as well use Gopher if we are only depending on the necessary stuff.

---

### Post by runningwithscissors on 2007-08-14
> **Darkhack said:**
> He didn't mean to depend upon javascript for validation.  He just meant that it can be used to warn the user ahead of time instead of having to hit submit before seeing that they messed up.  For example, I can use javascript to gray out the submit button until all the forms have been filled out.  I can also have javascript detect if a password field (on a registration form) has enough characters in it and if not display a message in red saying "Password is too short" when the field loses focus, but has text in it.  Also, no one said mousovers were must have features.  It looks nice though and adds on to the style.  We might as well use Gopher if we are only depending on the necessary stuff.
I understand, but when you put the script on the user's machine, it's their choice whether to use it or not. For important functionality, javascript cannot be a consideration at all.

About the style, I couldn't really care any less. I am not a designer and don't care for their efforts. Load up your site with funky effects and whatnot. I am not interested. Of course, there is a legion of mouth-breathing youtube addicts who'll love it. So you don't need my patronage anyway.

EDIT: the 'you' in the above sentences is generic.

---

### Post by M$LOL on 2007-08-14
> **runningwithscissors said:**
> 
And oh, Web 2.0 (whatever that is) and AJAX can lick my balls.

So you don't even know what it is, but yet you think it's crap? Stop trolling and educate yourself before ridiculing a technology that is actually one of the most awesome things in web design.

And there are minors here, this site shouldn't have to be degraded to the level of "suck my w/e".

---

### Post by runningwithscissors on 2007-08-14
> **M$LOL said:**
> So you don't even know what it is, but yet you think it's crap? Stop trolling and educate yourself before ridiculing a technology that is actually one of the most awesome things in web design.It's not "one of the most awesome things in web design". I do web development. One of the worst things about it is when some Web-too-point-oh! crazed web designer dreams up a convoluted dynamic interface and I'm the one that actually has to write code to make it work with the database/programming logic.

Theis Web 2.0 stuff is neither new or revolutionary. And as a web developer I can only say that it is a real pain in my backside.
Idiots with no idea of web technologies are the ones on this web 2.0 bandwagon. CSS and XHTML have been around for years. So has javascript and XmlHttpRequest.

> And there are minors here, this site shouldn't have to be degraded to the level of "suck my w/e"Well my offer to ajax and co. was only to service my nuts. But it's no problem if they want to suck my w/e either.

---

### Post by M$LOL on 2007-08-14
Yes it is awesome. No, the individual technologies are not new, but the concept is. It is starting to gain ground, and that's a good thing. It's not the easiest thing in the world to program, but it's not the hardest either. It can be very useful, I admit it can  also be grossly overdone, but on the whole it's a good thing.

---

### Post by aysiu on 2007-08-14
I don't *hate* NoScript, but I finally got tired of it.

It made me feel safe at first. There were a lot of Firefox JavaScript-related vulnerabilities popping up at the time (even though Mozilla had those patched within a week or two usually). Nevertheless, I was paranoid.

Then, after years of using NoScript (it's felt like years at least... I don't remember the exact date I started using it), I realized that I had been whitelisting just about every site I visited. Truth be told, I don't visit "untrusted sites." And in this one case, I value convenience over security. It's always tough finding that good balance between C and S, but C won out this time for me.

---

### Post by Darkhack on 2007-08-14
> **aysiu said:**
> I realized that I had been whitelisting just about every site I visited. Truth be told, I don't visit "untrusted sites." And in this one case, I value convenience over security. It's always tough finding that good balance between C and S, but C won out this time for me.

That is the primary reason I don't use it.  I know all the sites I visit and I trust them.  I would rather see Adblock Plus update the filter subscriptions to sites which are known to have dirty javascript.  Much more convenient that way.

---

### Post by ice60 on 2007-08-14
maybe this video will help you understand why scripting can be dangerous
[http://video.google.com/videoplay?docid=6147596885524966661](http://video.google.com/videoplay?docid=6147596885524966661)

---

### Post by ice60 on 2007-08-14
probably no one cares but i use proxomitron to filter web pages if i ever allow JS, it's a windows app so runs with wine, but it's the best web filter there is, it can even filter SSL connections.

---

### Post by Darkhack on 2007-08-14
> **ice60 said:**
> maybe this video will help you understand why scripting can be dangerous
[http://video.google.com/videoplay?docid=6147596885524966661](http://video.google.com/videoplay?docid=6147596885524966661)

It was a good video.  But like the guy said, there is actually a lot that can't be done.  Most XSS vulnerabilities can be fixed though, that's just a matter of doing input validation but then you get into things like AJAX and cookies.  So long as you are logged into a service like UbuntuForums, Facebook, MySpace, or even your email account, and then you visit an evil page.  That evil page can run Ajax requests as if it was you.  All those services won't know the difference between you posting a legitimate post on UbuntuForums and an AJAX request doing it from a third party because your browser sees the POST data going to UbuntuForums and thus allows the cookie data to be used.  The only thing that even comes close to stopping this is a URL referrer which can tell which domain the AJAX was executed from, but if someone is using a proxy (also talked about in the video) it's basically worthless.

The problem with NoScript is that it is all or nothing.  Most users (myself included) do not want to have to read the source code to each and every page we visit to decide whether we trust it or not.  Plus that page could change at a future date and NoScript wouldn't know the difference.  If it is on the whitelist, then it is allowed through.

Firefox needs a security setting to request permission for AJAX requests to send GET or POST data from a third party site to the original.  Let's be realistic.  How often is such a circumstance used legitimately in the real world?  Almost never.  Firefox should either block it by default or give a warning dialog asking me to allow or deny the action.

---

### Post by ice60 on 2007-08-14
i suppose it comes down to how you use NoScript. i find it useful because 90% of sites i go to i don't care that scripts are disabled and waste no time thinking about it.

when i do run JS it's filtered through proxomitron, i haven't looked at all the filters, but i know when i was more in to security and did look through the filters a few years a go it stopped all known exploits from running. i have an up-to-date security pack filter set mixed in with my filters so i hope it works lol

a layered approach is the way to go with security :D

---

### Post by bash on 2007-09-02
Im surprised that noone else has stated this in this thread. I use NoScript for one plain reason: My privacy. 

I don't want that every second Ad company knows when, where, for how long, with what username and so on I surfed/visits a page.

If you take a look at the Javascripts included I would have to say that about 50% of the bigger websites you visit contain google-analytics and/or google adsense Scripts. Even the forum here does. I understand the reason for putting up ads or wanting to have statistical information about your website user. But at least for the user information part do it on your own server. 

Im not particular keen that Google (that is known for its dataloggin frenzy) creates personalised profiles about me, "watching" me whenever I acces a page with google-analytics Scripts on them. 

That doesn't just apply for Google. Most or all Webcompanies love to collect whatever little piece of information they can find. And (at least) I am not really liking this. So when I have a small piece of code that can more or less stop quite bit of data collection, then I think its a good piece of code, that im glad about that it exists.

---

### Post by fuscia on 2007-09-02
some of the sites i frequent load faster since i've been using noscript. i can let in content if i want. where's the down side in that for me?

---

### Post by htor on 2007-09-02
noscript is for porn and warez sites - just don't visit this crap.

I just use epiphany - the best browser in this universe.

---

### Post by kerry_s on 2007-09-02
> **htor said:**
> noscript is for porn and warez sites - just don't visit this crap.

I just use epiphany - the best browser in this universe.

good 1, epiphany is for people who can't handle a real browser.

---

### Post by fuscia on 2007-09-02
> **htor said:**
> noscript is for porn and warez sites - just don't visit this crap.

I just use epiphany - the best browser in this universe.

i think dild...uh, dillo is better for porn than epiphany.

---

### Post by kerry_s on 2007-09-02
> **fuscia said:**
> i think dild...uh, dillo is better for porn than epiphany.

yep, dillo is way better. turn off the cookies and your all set.

---

### Post by htor on 2007-09-02
> **kerry_s said:**
> good 1, epiphany is for people who can't handle a real browser.
Wake up man !
Epiphany is for people that can see the difference between reality and fantasy and in the real world firefox is browser of choice only for people who** live in the past** and want feel like on windows OS. Gnome users should forget windows and **use epiphany**.

Epiphany is more advanced than FF - Dbus is the keyword.

---

### Post by starcraft.man on 2007-09-02
> **htor said:**
> **noscript is for porn and warez sites - just don't visit this crap.**

I just use epiphany - the best browser in this universe.

Your insightful and deep commentary is simply breathtaking. Besides stating something rather silly, you completely missed the point of this thread and have what appears to be a complete lack of understanding of the intended purpose/function of noscript. I never ceased to be amazed by brilliant posts.

> **htor said:**
> Wake up man !
Epiphany is for people that can see the difference between reality and fantasy and in the real world firefox is browser of choice only for people who** live in the past** and want feel like on windows OS. Gnome users should forget windows and **use epiphany**.

Epiphany is more advanced than FF - Dbus is the keyword.

There's nothing wrong with my perceptions of reality and I use Firefox. Can we keep the unfounded rants unrelated to the discussion for blogs?

If you've nothing else substantive to contribute, I guess that's it. Read the first few pages if your interested in the real talk.

---

### Post by Tankerdog2002 on 2009-11-20
I don't care too much for NoScript's new "more tinkering is better" configurations; but it's better than getting 'Jacked.

The problem I have with it is that's it becoming quite user unfriendly.

Sometimes I think my browser actually loads slower even though I know that NoScript blocks flash and ads.

What really ticks me off about NoScript is that when you click "Allow all this page", nothing happens. You have to re-click the option several times before it takes. No excuse for that.

NoScript has become so bloated it now has bugs of its own.

But....it stops 'Jackers and that what really matters.

---

### Post by Ewingo401 on 2009-11-20
Old thread is old.

---

### Post by wilee-nilee on 2009-11-20
> **Tankerdog2002 said:**
> I don't care too much for NoScript's new "more tinkering is better" configurations; but it's better than getting 'Jacked.

The problem I have with it is that's it becoming quite user unfriendly.

Sometimes I think my browser actually loads slower even though I know that NoScript blocks flash and ads.

What really ticks me off about NoScript is that when you click "Allow all this page", nothing happens. You have to re-click the option several times before it takes. No excuse for that.

NoScript has become so bloated it now has bugs of its own.

But....it stops 'Jackers and that what really matters.

The best way I have found to use noscript is to use the toolbar buttons FF addon it has the per-session allow and block in it's button list

---

### Post by FuturePilot on 2009-11-20
> **FuturePilot said:**
> I hate it too. I don't see any use in it. It just makes surfing around more difficult. I don't use it.

I retract this statement. Can't live without NoScript now. :D

---

### Post by slumbergod on 2009-11-20
I wouldn't surf the net without it. If I want a site's script to run I will allow it to; otherwise let me see the site safely.

---

### Post by cariboo on 2009-11-20
[IMG]http://i112.photobucket.com/albums/n165/cariboo907/thread_necromancer.png[/IMG]

this thread is closed

---

