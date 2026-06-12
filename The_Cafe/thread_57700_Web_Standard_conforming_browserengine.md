---
title: "Web Standard conforming browser/engine"
date: 2005-08-17
forum: The Cafe
---

### Post by Buffalo Soldier on 2005-08-17
Out of curiosity is there any effort to create a Web Standard (I mean the standards set by [http://www.w3.org/](http://www.w3.org/)) browser or engine under GPL?

If not, I would like your opinion on why isn't this happening. I am no programmer and I don't have the smallest idea how hard it is to create a web browser.

Is there any big obstacle in getting all the GNU/Linux distribution to gather their resources to create one webstandard comforming engine (something like Gecko). And then use that engine for what ever browser they like, Galeon, Epiphany and etc.

Even perhaps making the engine the official/supported engine of World Wide Web Consortium. If that is not possible, how about working very closely with them so that to ensure the engine is 100% strictly to their standards. Or perhaps working closely with [http://www.webstandards.org/](http://www.webstandards.org/)


And then perhaps create a browser that uses that same engine for Mac and MS Windows.

That way it would help to solve 2 problems.[list]
[*] Getting a standard conforming browser
[*] minimizing IE monopoly (IE may still be the majority on Windows platform, but we can surely minimise its market share accross all platform
[/list]

am i making any sense? or am i talking nonsense? someone please give me a good smack if i'm talking mumbo jumbo.

---

### Post by BWF89 on 2005-08-17
Isn't Firefox standards compliant?

---

### Post by Lowe on 2005-08-17
[QUOTE=BWF89]Isn't Firefox standards compliant?[/QUOTE]

Yes, as is opera and many others.

---

### Post by az on 2005-08-17
Gecko?

Mozilla uses the Gecko rendering engine.

---

### Post by BWF89 on 2005-08-17
[QUOTE=Lowe]Yes, as is opera and many others.[/QUOTE]
Then why do we need to create a W3C standards compliant engine when we allready have several?

---

### Post by Buffalo Soldier on 2005-08-17
[QUOTE=BWF89]Isn't Firefox standards compliant?[/QUOTE]
 I **could** be wrong. I hope I am wrong. But I'm lead to believe Firefox is not 100% compliant.

Firefox support for webstandards is a lot better than IE. But I think there's still work to do.

I am **not** saying the [Acid2 Test](http://www.webstandards.org/act/acid2/) by [WebStandards.org](http://www.webstandards.org/) is the ultimate yardstick in measuring the compliance of a web-browser/engine. But it can give be use as a rough measure. Is there any browser that pass this test anyway?

And I'm not suggesting this new engine to be use as the default for all distro. But just a another alternative that can be easily install tru apt-get or any other methods.

I believe the there are 3 things that MS is terrified about:[list=1]
[*] Any other web-browser besides IE (especially if it's more / 100% standard compliant than IE)
[*] GNU/Linux
[*] Google
[/list]

I don't know how to put this exactly into words. What I'm trying to say is that if we can somehow make:[list=1]
[*] Any other web-browser besides IE (especially if it's more / 100% standard compliant than IE), **and**
[*] GNU/Linux
[/list]to work/exist/integrate closely together, maybe we'll have a better fighting chance against MS monoopoly. (or in the other hand, it could paint a bigger bullseye target for MS to shoot GNU/Linux)

---

### Post by BWF89 on 2005-08-17
[QUOTE=Buffalo Soldier]I **could** be wrong. I hope I am wrong. But I'm lead to believe Firefox is not 100% compliant.[/QUOTE]
From what I've heard no browser is 100% compliant.

---

### Post by BWF89 on 2005-08-17
[QUOTE=Buffalo Soldier]I **could** be wrong. I hope I am wrong. But I'm lead to believe Firefox is not 100% compliant.[/QUOTE]
From what I've heard no browser is 100% compliant. But Firefox is pretty close. Alot closer than IE.

But I don't think you need to be 100% to be able to view every website on the internet. Most sites are configured to display best on IE (i think) but I've been useing FF for quite awhile and have yet to stumble on one that hasn't worked because of that. Except for the MSN Gaming Zone which requires that you have ActiveX.

NOTE TO SELF: To avoid double posting make sure you have everything you want to say written down before you hit Post Message and then click stop to add something.

---

### Post by drizek on 2005-08-17
[QUOTE=BWF89]From what I've heard no browser is 100% compliant. But Firefox is pretty close. Alot closer than IE.

But I don't think you need to be 100% to be able to view every website on the internet. Most sites are configured to display best on IE (i think) but I've been useing FF for quite awhile and have yet to stumble on one that hasn't worked because of that. Except for the MSN Gaming Zone which requires that you have ActiveX.

NOTE TO SELF: To avoid double posting make sure you have everything you want to say written down before you hit Post Message and then click stop to add something.[/QUOTE]
 KHTML in konqueror CVS is AFAIK the most standards compliant rendering engine(other than maybe khtml in safari).it can pass acid2(ive tried it) as well.  but even khtml is still not 100% compliant. 

If you dont like that, and you know how to program, join the khtml dev team. wed all love to have a 100% compliant browser.

---

### Post by Kvark on 2005-08-17
[QUOTE=Buffalo Soldier]I **could** be wrong. I hope I am wrong. But I'm lead to believe Firefox is not 100% compliant.[/QUOTE]
It takes time to adapt to standards. Eventually firefox will become 100% compliant with the standards there is today. But by then there will be some new standards out there which it will need time to adapt to. The web browsers will always be one step behind the standards. Or sometimes one step before and implement something in their own way before the standard for it is finalized. In which case they have to eventually support both the standard and their own implementation.

To support strict standards isn't first priority for a web browser since the wast majority of the web pages out there does not follow the standards anyway. The web browsers spend most of their time working around shabby markup. So it is more important to be able to figure out what a web page that is full of errors is supposed to look like then what a strictly error free page looks like.

---

### Post by Buffalo Soldier on 2005-08-17
[QUOTE=BWF89]From what I've heard no browser is 100% compliant. But Firefox is pretty close. Alot closer than IE.

But I don't think you need to be 100% to be able to view every website on the internet.[/QUOTE]Yes, that's a good point there.

Anyway, I hope ppl don't see this thread as trolling/fud/creating ripples in the water or things such like that.

It's just that reading things like:[list][*]"While such modifications would normally limit Debian's rights to use the Firefox name, the Mozilla Foundation is willing to give Debian special permission to use the Firefox trademark in its releases. However, some members of the Debian community feel that a Debian-specific license would not be acceptable under the terms of the Debian Free Software Guidelines because it would not give 'downstream' users of Debian the same rights as the Debian Project itself." at [Mozilla Zine](http://www.mozillazine.org/talkback.html?article=6801),
[*] MPL listed as GPL-incompatible at [http://www.gnu.org/licenses/license-list.html](http://www.gnu.org/licenses/license-list.html),
[*] Mozilla Foundation to ban Firefox derivative browsers? at [http://www.theinquirer.net/?article=23427](http://www.theinquirer.net/?article=23427)[/list]kind of make me think whether MPL and Mozilla "licence" will some how bite GNU/Linux "rear" sometime in the future.

> Out of curiosity is there any effort to create a Web Standard (I mean the standards set by [http://www.w3.org/](http://www.w3.org/)) browser or engine under **GPL**?

But I really do hope my fears and assumptions are wrong.

---

### Post by Kerberos on 2005-08-17
Half the time its not the browsers fault for being non-compliant.  If a webpages HTML is fundamentally broken (I'd say thats ~70%+ of websites) featuring unclosed and non existant tags and parameters as well as doing things the 'wrong way' then its up to the browser to a: not display it at all or b: display it the best it can.  Since most often it goes for the latter then pages do display differently as different browsers ways of dealing with dodgy code differ.  Leave out a </p> and the browser has to make an educated guess where to put it back in, and this varies.  Its like having a C++ compiler than will compile with errors, it'll just try to fix it.

Slashdot.org's response to complaints about the quality of the code is to block the w3c.org verifier from checking it (go on and try, it'll 403).  [http://openbsd.org](http://openbsd.org) fails to even pass the 4.01 Trans Standard*, so until making proper, standards compliant sites is actually taken seriously theres no point.  ubuntulinux.org almost passes and is pretty decent (they just need to know when to use class and when to use div :)) but as a whole the quality of HTML is so bad a standards compliant browser is a bit useless.

I think the best approach is to use Firefox and if you do encounter a render bug, report it.  The quality of the web is what needs improving.  And until people stop using HTML 4.01 and concentrate on creating standards compliant sites its not going to happen.

** I'm not picking them out for any reason, they were just the first I checked.  You dont often see a site validate properly, let alone validate as XHTML.*

---

### Post by TestDummy! on 2005-08-17
[QUOTE=KerberosSlashdot.org's response to complaints about the quality of the code is to block the w3c.org verifier from checking it (go on and try, it'll 403).][/QUOTE]

Doesn't stop you from just copying the page source and using the "Validate by direct input option" . I just did it and got this

[quote="W3C Markup Validation"]Result:  	 Failed validation, 66 errors
File:	upload://Form Submission
Encoding:	utf-8
Doctype:	HTML 3.2

No Character Encoding Found! Falling back to UTF-8.

This page is not Valid HTML 3.2![/quote] 

Eh, HTML 3.2? Sounds like something from a long time ago.

---

### Post by Kerberos on 2005-08-17
[QUOTE=TestDummy!]Eh, HTML 3.2? Sounds like something from a long time ago.[/QUOTE]
lol yeh.  a dark, dark time for web designers (what with frontpage 'n' all).  Generally though the DTD has little bearing on what the code actually is.  I've seen sites that are blatantly HTML 4.01 with a XHTML DTD, and even valid XHTML that uses a table based layout (defeating the objective lol).

XHTML is just HTML but with all the crap tags accumulated through the dotcom boom removed (and a seperate style sheet).  Once you seperate style from content it makes it trivial to enable everything from fridges to mobile phones as web access devices as then you dont have to view the site 'in 1024x768 with IE5+' if you dont want to - it'll work on anything!

---

### Post by Davepet on 2005-08-18
Ever hear of Amaya?

[http://www.w3.org/Amaya/](http://www.w3.org/Amaya/)

I suspect that the w3 produced browser is as standards-complient as they get.

Dave

---

### Post by npaladin2000 on 2005-08-18
What about Epiphany?

I've been messing with it and it integrates nicely into GNOME, and it uses the Gecko engine also.

---

