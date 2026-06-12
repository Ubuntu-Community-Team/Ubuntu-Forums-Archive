---
title: "The reason why it's better for only one Flash Player to exist"
date: 2008-05-21
forum: The Cafe
---

### Post by FFighter on 2008-05-21
While I agree that the more open, the better, I think it's better if Adobe keeps the Flash Player under its belt. Jessen has some words regarding this:

[http://jessewarden.com/2006/09/gnash-gives-me-nightmares.html](http://jessewarden.com/2006/09/gnash-gives-me-nightmares.html)

It's a very controversial subject, but in case of Flash Player's, fragmentation is really not good. 

I appreciate the work of gnash people, but I wouldn't like people complaining to me that my app doesn't work right because they are not using the official player. 

Some of you may argue that if adobe opens it completely, developers will be able to create versions for Linux that may be as good as the closed source one currently. But who would guarantee to me that my Flash/Flex app would work exaclty as I expect in these players?

Share your thoughts :)

---

### Post by eragon100 on 2008-05-21
I agree, for the sake of easy interoperability :wink:

---

### Post by Steveway on 2008-05-21
Good luck with your closed-source flash on a Sparc or on a PPC.
That article isn't worth the pixels it used to display on my screen, it doesn't give any real reasons.
And the author doesn't seem to understand why Gnash and Co exist.

---

### Post by qazwsx on 2008-05-21
[http://www.adobe.com/openscreenproject/](http://www.adobe.com/openscreenproject/)
[http://blogs.adobe.com/penguin.swf/2008/04/licensefree_spec.html](http://blogs.adobe.com/penguin.swf/2008/04/licensefree_spec.html)

So...

Specs are free.

---

### Post by howlingmadhowie on 2008-05-22
> **qazwsx said:**
> [http://www.adobe.com/openscreenproject/](http://www.adobe.com/openscreenproject/)
[http://blogs.adobe.com/penguin.swf/2008/04/licensefree_spec.html](http://blogs.adobe.com/penguin.swf/2008/04/licensefree_spec.html)

So...

Specs are free.

have a look here:
[http://www.youtube.com/watch?v=VXBQRpg11bg]("http://www.youtube.com/watch?v=VXBQRpg11bg")

if you have ever installed flash, the license prohibits you from ever working on another client.

FFighter: do you complain that there are a number of different libraries for encoding and decoding jpegs too? and btw, adobe flash is not backwards compatible and looks different on "linux" machines than it does on windows.

---

### Post by K.Mandla on 2008-05-22
> **FFighter said:**
> Share your thoughts :)
My thoughts? That post is almost two years old, that's what I think. Gnash works great for me, and if I'm the only one using it, that's reason enough for it to be around. Just my $0.02.

---

### Post by Erik Trybom on 2008-05-22
Replace "Flash Player" with "Web Browser" and you realize how faulty his reasoning is.

The specs should be open, like HTML or PDF, so that there can be multiple clients to choose from. If you like Firefox and Acrobat Reader, I may prefer Opera and Kpdf.

The standard, on the other hand, is another thing. There should only be one standard way of doing the same thing, such as "transferring hypertext through the Internet" (HTML does that). For a recent example of multiple standards, check out the HD-DVD/Blu-ray fight which has stalled next-generation video for years.

Here's Mark Shuttleworth's thoughts on the subject (written before the OOXML vote): [http://www.markshuttleworth.com/archives/date/2007/08](http://www.markshuttleworth.com/archives/date/2007/08)

---

### Post by FFighter on 2008-05-22
You can't compare the Flash Player with web browsers. 

If you develop a web sites with (X)HTML and CSS for the presentation layer, you have to pull you hair off multiple times... why? Multiple browsers. One of the main advantages of developing for the Flash Platform is knowing that your application will run exactly the same regardless of which platform you are running it, that's how adobe markets it and it actually happens to be like this.

---

### Post by howlingmadhowie on 2008-05-22
> **FFighter said:**
> You can't compare the Flash Player with web browsers. 

If you develop a web sites with (X)HTML and CSS for the presentation layer, you have to pull you hair off multiple times... why? Multiple browsers. One of the main advantages of developing for the Flash Platform is knowing that your application will run exactly the same regardless of which platform you are running it, that's how adobe markets it and it actually happens to be like this.

Multiple browsers meaning microsoft and "all others". And the differences between microsoft ie5.5 and ie6 and ie6.1 and ie7 and ie8...

interestingly the difference between flash7 and flash8 and flash9 is at least as large. then there are the inconsistencies so that sites with flash under linux x86 look different to under windows. 

so basically, no. adobe has not created a landscape where a flash programmer can be sure his/her work looks the same in all browser/operating system combinations. moreover it is not in adobe's interest to do this, so don't expect them to start any time soon. constantly changing actionscript specifications keeps people buying software.

---

### Post by geoken on 2008-05-22
> **howlingmadhowie said:**
> Multiple browsers meaning microsoft and "all others". And the differences between microsoft ie5.5 and ie6 and ie6.1 and ie7 and ie8...

interestingly the difference between flash7 and flash8 and flash9 is at least as large. then there are the inconsistencies so that sites with flash under linux x86 look different to under windows. 

so basically, no. adobe has not created a landscape where a flash programmer can be sure his/her work looks the same in all browser/operating system combinations. moreover it is not in adobe's interest to do this, so don't expect them to start any time soon. constantly changing actionscript specifications keeps people buying software.

Can you give an example of the rendering differences between flash on different platforms? (note: performance != rendering difference).

I'm a Flash/Flex developer. I do all my development on Linux, but do crossbrowser/cross OS testing of everything and I've never seen a rendering inconsistency.

---

### Post by howlingmadhowie on 2008-05-22
on linux flash applets often overdeck things like ajax menus, so making some sites unuseable.

---

### Post by FuturePilot on 2008-05-22
> **geoken said:**
> Can you give an example of the rendering differences between flash on different platforms? (note: performance != rendering difference).

I'm a Flash/Flex developer. I do all my development on Linux, but do crossbrowser/cross OS testing of everything and I've never seen a rendering inconsistency.

Find a site that uses wmode=transparent. You will quickly see the problem.
Heh, Adobe's own page doesn't even work right.
[http://www.adobe.com/]("http://www.adobe.com/")
Try the pulldown menus at the top.
That problem does not exist on Windows platforms.

---

### Post by madjr on 2008-05-22
> **FFighter said:**
> While I agree that the more open, the better, I think it's better if Adobe keeps the Flash Player under its belt. Jessen has some words regarding this:

[http://jessewarden.com/2006/09/gnash-gives-me-nightmares.html](http://jessewarden.com/2006/09/gnash-gives-me-nightmares.html)

It's a very controversial subject, but in case of Flash Player's, fragmentation is really not good. 

I appreciate the work of gnash people, but I wouldn't like people complaining to me that my app doesn't work right because they are not using the official player. 

Some of you may argue that if adobe opens it completely, developers will be able to create versions for Linux that may be as good as the closed source one currently. But who would guarantee to me that my Flash/Flex app would work exaclty as I expect in these players?

Share your thoughts :)

that article is from 2006.

anyway i don't care who has problems with gnash.

if they want people to use flash than fix the **DAM BUGS**!

**look at my sign**

---

### Post by howlingmadhowie on 2008-05-22
> **FuturePilot said:**
> Find a site that uses wmode=transparent. You will quickly see the problem.
Heh, Adobe's own page doesn't even work right.
[http://www.adobe.com/]("http://www.adobe.com/")
Try the pulldown menus at the top.
That problem does not exist on Windows platforms.

adobe's site works fine for me (using gnash)

---

### Post by Erik Trybom on 2008-05-22
> **FFighter said:**
> You can't compare the Flash Player with web browsers. 

If you develop a web sites with (X)HTML and CSS for the presentation layer, you have to pull you hair off multiple times... why? Multiple browsers. One of the main advantages of developing for the Flash Platform is knowing that your application will run exactly the same regardless of which platform you are running it, that's how adobe markets it and it actually happens to be like this.
Well, I can agree that there are problems for the web designer. He or she has to check the site multiple times to make sure every browser renders it correctly. 

On the other hand, I think this is a small price to pay for the plethora of web browsers out there. There are browsers for almost any platform, for different window managers and for different hardware specs. There are browsers that run on cellphones or in a terminal or in kiosk mode. I don't think one single company could create all this choice and customization, no matter how big it is.

It doesn't take much imagination to figure out the possibilities of custom flash interpreters.

---

### Post by geoken on 2008-05-22
> **FuturePilot said:**
> Find a site that uses wmode=transparent. You will quickly see the problem.
Heh, Adobe's own page doesn't even work right.
[http://www.adobe.com/]("http://www.adobe.com/")
Try the pulldown menus at the top.
That problem does not exist on Windows platforms.

Wmode and ajax layering issues don't have anything to do with actual content rendering. They're issues between the browser and the flashplayer. All content within the flash player looks identical. The fileReference class also functions differently on Linux but nobody would consider that a rendering issue.

---

### Post by zmjjmz on 2008-05-22
So I tale it you're also against choice, FFighter? We should all drive the same car and use the same tires and have the same weight so that the roads stay perfect? We should all use the same JDK? Mind you, the SWF and FLV specs are open, and chances are they will do their best to comply with the specs, like web browsers try to comply with javascript and CSS (IE excluded).

---

### Post by howlingmadhowie on 2008-05-22
> **zmjjmz said:**
> So I tale it you're also against choice, FFighter? We should all drive the same car and use the same tires and have the same weight so that the roads stay perfect? We should all use the same JDK? Mind you, the SWF and FLV specs are open, and chances are they will do their best to comply with the specs, like web browsers try to comply with javascript and CSS (IE excluded).

the swf and flv specs are soft of open. if you have ever used a flash plug-in from adobe, the license for the specs prohibits you from working on a different implementation (clean-room engineering). this means that the programmers of gnash, for example, are not allowed to view youtube in adobe flash but instead have to guess if they are implementing it correctly. for this reason, feedback is very welcome (it's the only way they can learn of problems).

---

### Post by zmjjmz on 2008-05-22
Wait, but didn't Adobe remove that EULA from the FLV/SWF specs like a month ago?

---

### Post by howlingmadhowie on 2008-05-23
> **zmjjmz said:**
> Wait, but didn't Adobe remove that EULA from the FLV/SWF specs like a month ago?

nope: [http://www.youtube.com/watch?v=zoNvsiBTQDE]("http://www.youtube.com/watch?v=zoNvsiBTQDE")

---

### Post by geoken on 2008-05-26
> **howlingmadhowie said:**
> nope: [http://www.youtube.com/watch?v=zoNvsiBTQDE]("http://www.youtube.com/watch?v=zoNvsiBTQDE")

Just digging this one up.

I watched the video but that doesn't seem to jive with the EULA itself. The EULA only mentions decompiling the player itself or making a derivitive work. Reading the spec, then making an application based on that spec does not seem to violate any portion of the EULA since any work you produce is based on an interpretation of the spec and not reverse engineering the player.

---

### Post by mister_pink on 2008-05-26
> **howlingmadhowie said:**
> adobe's site works fine for me (using gnash)
Banter. Doesn't work with Adobe's flash player in Firefox. Maybe gnash should become the standard.

On to the discussion. That original article seems to misinterpret what gnash is anyway. He compares it to some open source compilers of actionscript but gnash is a viewer. Doesn't really make any real points at all either. I don't see the problem at all.

Edit: BTW, I think someone earlier meant to link this vid, not the kubuntu dev one! [http://www.youtube.com/watch?v=zoNvsiBTQDE](http://www.youtube.com/watch?v=zoNvsiBTQDE)
Edit edit: Weird, they did post the right link, I must've clicked off it straight away by accident.

---

### Post by geoken on 2008-05-27
He doesn't think it's a compiler. No one cares about rendering inconsistencies in compilers because that is a direct choice the author made and doesn't affect the viability of the platform.

Basically, this is the point the articles trying to make;

People code into a Flash format because they are building sites/web apps with advanced functionality. These devs witness, on a daily basis, the issues that arise when trying to code HTML with 1/5th the complexity of their web app (see latest Digg.com redesign and Opera crashing issues for an example of this). With Flash, the designer/developer knows that they can place and dynamically animate 100 vector shapes and have them look identical on every single platform, with HTML you can run into problems by just trying to place 2 rectangles beside each other. When this consistency is removed through alternate players with small rendering inconsistencies, the author believes flash will become less viable.



As for the video, I'll ask again for someone to show me where in the EULA it says you can't work on a piece of software capable of decoding the open SWF spec if you've installed the flash player.

---

### Post by mister_pink on 2008-05-27
Urgh. The entire point of HTML is that it's a markup language and appearing differently in different browsers is by design. The reason so many things break is because people are obsessed with things appearing identically in different browsers. Microsoft have of course done their bit to make the issue more difficult.

I understood the point he was making, but he was confusing the issue by talking about compilers which are as you say unrelated. 

The point is that if people choose to use gnash and things appear differently to them then that's their problem really. And so what if flash becomes less viable because of this? Maybe then a decent, open format could be used. Afterall, people only use flash because everyone else does - if everyone stops using it then everyone wins.

---

### Post by saulgoode on 2008-05-27
> **geoken said:**
> As for the video, I'll ask again for someone to show me where in the EULA it says you can't work on a piece of software capable of decoding the open SWF spec if you've installed the flash player.

The person being interviewed did not state that. He stated that you couldn't work on Gnash if you've installed the Adobe Flash player. This is his choice to make as the project lead -- and is a wise one considering that the Adobe licensing agreement **does** place restrictions on reverse-engineering and decompiling the software (see Section 2.7 of the Player Distribution License).

---

### Post by geoken on 2008-05-27
> **mister_pink said:**
> 
The point is that if people choose to use gnash and things appear differently to them then that's their problem really. And so what if flash becomes less viable because of this? Maybe then a decent, open format could be used. Afterall, people only use flash because everyone else does - if everyone stops using it then everyone wins.

People use flash because it can render advanced vectors, pretty fast, and animate them while maintaining great consistency across platforms. The open source alternative, SVG, has proven unable to do this. The two main SVG creation applications (Inkscape and Karbon) can't even succesfully render/edit each other's SVG's 100% of the time. And we're talking static SVG's with minimal filters. I can't even Imagine what would happen if they needed to render animated SVG's, with advanced filters and dynamic data sources from binary socket connections. And even then it would only be a subset of Flash until it seamlessly integrated Music and Video.

---

### Post by geoken on 2008-05-27
> **saulgoode said:**
> The person being interviewed did not state that. He stated that you couldn't work on Gnash if you've installed the Adobe Flash player. This is his choice to make as the project lead -- and is a wise one considering that the Adobe licensing agreement **does** place restrictions on reverse-engineering and decompiling the software (see Section 2.7 of the Player Distribution License).

Well the person who posted the video was using it to imply that the open screen project means nothing because anyone who has ever installed the flash player is not allowed to work on a Flash player. If the message of the video was that the Gnash project leader decided that, of his own accord, then he should make that clear.

Basically:
1. Adobe allows anyone to read the SWF specs and create a SWF player
2. Adobe (via the EULA) does not allow anyone to decompile their own proprietary player
3. Gnash decided to only accept devs who have not signed the EULA mentioned in #2

The person who posted the video was insinuating that somehow point #3 (and by extension point #2) somehow invalidate point #1. He stated multiple times that anyone who has installed flash can't work on an alternative flash player. That is untrue. They can not work on Gnash in specific (due to decisions that project has made), but there is nothing in the EULA which bars them from reading the SWF spec then creating an application which can render that file format. Here is the exact quote of what they said (half way down page 2);

*the swf and flv specs are soft of open. if you have ever used a flash plug-in from adobe, the license for the specs prohibits you from working on a different implementation (clean-room engineering). this means that the programmers of gnash, for example, are not allowed to view youtube in adobe flash but instead have to guess if they are implementing it correctly.*

---

### Post by mister_pink on 2008-05-27
The adobe EULA says:

> 2.5.1  You may not modify, adapt, translate or create derivative works based upon the Software. You may not reverse engineer, decompile, disassemble or otherwise attempt to discover the source code of the Software except to the extent you may be expressly permitted to decompile under applicable law, it is essential to do so in order to achieve operability of the Software with another software program, and you have first requested Adobe to provide the information necessary to achieve such operability and Adobe has not made such information available. Adobe has the right to impose reasonable conditions and to request a reasonable fee before providing such information. Any such information supplied by Adobe and any information obtained by you by such permitted decompilation may only be used by you for the purpose described herein and may not be disclosed to any third party or used to create any software which is substantially similar to the expression of the Software. Requests for information should be directed to the Adobe Customer Support Department.

What this actually means I don't know, but I get the impression that the restriction on not having installed flash in order to work on gnash is either not just a gnash policy, or is because they would consider themselves on dodgy legal grounds if they did allow it.

---

### Post by saulgoode on 2008-05-27
> **geoken said:**
> Basically:
1. Adobe allows anyone to read the SWF specs and create a SWF player 
This may be the case now, but it was not the case for the past five years.  The Adobe and Macromedia EULAs for Flash documentation and SDKs have always prohibited using the information for creating an alternative player.

> 2. Adobe (via the EULA) does not allow anyone to decompile their own proprietary player
Correct. It also prohibits reverse engineering the Flash player. Using the player then developing a player which performs the same thing is by definition, reverse engineering.
> 3. Gnash decided to only accept devs who have not signed the EULA mentioned in #2
And this is because Gnash chose a reasonable interpretation of what the EULA prohibited.

> They can not work on Gnash in specific (due to decisions that project has made), but there is nothing in the EULA which bars them from reading the SWF spec then creating an application which can render that file format.
There are separate licenses for the specification documents as opposed to the player's EULA. There have been many alterations made to the Flash player documentation and SDK licensing over the past two years, but all of them prohibited using the information to create an alternative player.

---

### Post by geoken on 2008-05-27
> **saulgoode said:**
> 


There are separate licenses for the specification documents as opposed to the player's EULA. There have been many alterations made to the Flash player documentation and SDK licensing over the past two years, but all of them prohibited using the information to create an alternative player.

Not any more. You can directly view the swf spec without viewing any EULA (like you had to before)

Also, this: "Using the player then developing a player which performs the same thing is by definition, reverse engineering." is completely false. Reverse engineering has a very specific definition. Using something does not constitute reverse engineering it.

---

