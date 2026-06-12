---
title: "Adobe to donate scripting engine code to Mozilla"
date: 2006-11-07
forum: The Cafe
---

### Post by SlugO on 2006-11-07
[CNET News.com]("http://news.com.com/Adobe+to+donate+script+code+to+Mozilla/2100-7344_3-6133052.html?tag=nefd.top"):> **Adobe will donate software to run JavaScript programs in the Firefox Web browser, the largest code contribution yet to the open-source Mozilla Foundation.**

On Tuesday, Adobe is expected to announce the donation in conjunction with the Web 2.0 Conference in San Francisco. The code will form the basis for a new open-source project called Tamarin, which will be governed and manned by developers from Adobe and Mozilla.

Adobe will provide the same software, called the ActionScript Virtual Machine, which it uses to run script code in the Adobe Flash Player 9.

This virtual machine is expected to be built into future versions of the Firefox browser by the first half of 2008, said Frank Hecker, the executive director of the Mozilla Foundation.

The scripting language for Adobe's Flash Player virtual machine runs programs written in ActionScript, which is based on an Ecma International standard called ECMAScript Edition 4. Widely used JavaScript and Microsoft JScript also comply with that standard, said Kevin Lynch, chief software architect at Adobe.

The latest version of Adobe's script "engine," released in June this year with Flash Player 9, uses a just-in-time compiler to run programs ten times faster than previous versions, he said.

Lynch said the deal with Mozilla is the biggest Adobe has done with open source. The move furthers the company's plan to allow developers to mix and match programming technologies, including AJAX-style Web development and Flash for media and animation, he said.

"We can bring together the broader HTML and Flash developer communities around this common language implementation," Lynch said. "Using the same language engine is a huge step."

Hecker said that having a high-quality script engine is "extremely important" to its open-source projects, which include both the FireFox browser and Thunderbird e-mail client. Much of Firefox and many extensions are written in JavaScript, he noted.

The Tamarin project code will form the basis for the next generation of SpiderMonkey, the existing JavaScript in the Firefox browser, Hecker said.[Adobe press release.]("http://www.adobe.com/aboutadobe/pressroom/pressreleases/200611/110706Mozilla.html")

Anyone heard the big news today? Adobe is open sourcing its Flash/JavaScript scripting engine and donating the code to Mozilla. This is the biggest and perhaps most important single code donation Mozilla has received yet.

So what does it mean? Well I'm not sure of all the details but most likely the JavaScript in Firefox will get much faster (faster AJAX apps etc). Mozilla and Adobe have already started an open source project called Tamarin which will put the code donation to good use.

I have to say that this is good move on Adobe's part. They're getting good publicity especially among open source advocates and are helping to shape the future of the web into better direction. Almost makes me forget that we still have to use the ancient Flash 7 on Linux. Almost :mrgreen:
(But thanks for the long overdue Flash 9 beta)

---

### Post by 3rdalbum on 2006-11-07
It's amazing. A couple of hours ago, I said that I hoped SVG and Javascript would be featured in an open-source multimedia authoring studio to rival Flash.

And now I find that Actionscript is basically going to be open-sourced. I mean, it looks like Adobe will be basically supporting an authoring technology that will be cross-platform.

However, one little quibble. Does it HAVE to be based around Actionscript? Sure it lets developers do things with animations in Flash, but it's so convoluted and finiky. At least with Javascript, everything feels logical and well-planned, and reasonable code always works the way you expect.

---

### Post by mostwanted on 2006-11-07
> **3rdalbum said:**
> However, one little quibble. Does it HAVE to be based around Actionscript? Sure it lets developers do things with animations in Flash, but it's so convoluted and finiky. At least with Javascript, everything feels logical and well-planned, and reasonable code always works the way you expect.

ActionScript and JavaScript are basically the same languages (I've used both extensively), only Macromedia started implementing the object orientation and strong type features of newer ECMAscript versions. What you're referring to is probably additional libraries (Flash's movieclip vs. HTML object model). not the languages themselves.

Anyway, I seem to remember something about SWF being an ugly proprietary thing (only Adobe/Macromedia is allowed to make an interpreter for it), so how does that work out when Adobe now open sources a hybrid SWF/ECMAscript interpreter?

---

### Post by mostwanted on 2006-11-07
Upon reading more about this, it seems that it's not an SWF interpreter, but solely a ECMAScript JIT compiler that supports the newest version of ECMAScript (essentially, what ActionScript looks like at the moment). It's not an open source Flash player, it doesn't JIT compile SWF (regular flash files).

[http://www.hecker.org/mozilla/adobe-mozilla-and-tamarin](http://www.hecker.org/mozilla/adobe-mozilla-and-tamarin)

---

### Post by DoctorMO on 2006-11-07
It'll be interesting to see if Gnash can make use of the code.

---

### Post by SunnyRabbiera on 2006-11-07
It would be about time, Adobe has not handled the flash issue well and I would like them be more active in non MS engagements.

---

### Post by Tomosaur on 2006-11-07
Forgive me if I'm wrong, but this doesn't look like Adobe is open-sourcing anything. It's allowing it's own (closed-source) interpretor to be used within an Open-Source project, which to me says more about the direction Firefox is taking than the direction Adobe is.

---

### Post by mostwanted on 2006-11-07
> **Tomosaur said:**
> Forgive me if I'm wrong, but this doesn't look like Adobe is open-sourcing anything. It's allowing it's own (closed-source) interpretor to be used within an Open-Source project, which to me says more about the direction Firefox is taking than the direction Adobe is.

You're wrong.

Read this to get an overview: 
[http://www.hecker.org/mozilla/adobe-mozilla-and-tamarin](http://www.hecker.org/mozilla/adobe-mozilla-and-tamarin)

---

### Post by Tomosaur on 2006-11-07
> **mostwanted said:**
> You're wrong.

Read this to get an overview: 
[http://www.hecker.org/mozilla/adobe-mozilla-and-tamarin](http://www.hecker.org/mozilla/adobe-mozilla-and-tamarin)

Hah, fair enough then ^_^

---

### Post by BWF89 on 2006-11-07
Good to see Firefox is gaining commercial acceptance.

---

