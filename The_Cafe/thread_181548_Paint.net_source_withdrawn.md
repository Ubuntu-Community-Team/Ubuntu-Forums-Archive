---
title: "Paint.net source withdrawn"
date: 2006-05-24
forum: The Cafe
---

### Post by bruce89 on 2006-05-24
I wonder if this has anything to do with the fact is is being ported to mono? - [http://paintdotnet.12.forumer.com/viewtopic.php?t=1403](http://paintdotnet.12.forumer.com/viewtopic.php?t=1403) and [http://tirania.org/blog/archive/2006/May-19.html](http://tirania.org/blog/archive/2006/May-19.html)

---

### Post by Lord Illidan on 2006-05-24
So the devs of Paint.Net withdrew the source code because it was being ported to Mono? Shame on them.

We need such apps on linux... and can do without obstacles being put in our path.

---

### Post by bruce89 on 2006-05-24
Well, not really; it's available on request.  Funny thing is that the developers work for microsoft themselves...

---

### Post by INMCM on 2006-05-24
I find it hard to believe that being ported to Mono is the reason for new restriction. A search of the forum shows no antagonism towards Mono or Linux, just reinforcements that only windows releases will be done.

Additionaly, this interview [http://www.betanews.com/article/Interview_A_Look_Inside_PaintNET/1141071978](http://www.betanews.com/article/Interview_A_Look_Inside_PaintNET/1141071978)
shows a very open attitude towards remaining open source. From the interview:

[I]BN: Open source and Microsoft are not usually synonymous. What was behind the decision to make the product's code open?

RB: Paint.NET started as a university senior design project, and part of the spirit of that was building something that other people could learn from. If you're curious how we've implemented Gaussian Blur, for instance, just download the source code and poke around in the BlurEffect.cs file.

We just haven't seen any reason to discontinue this, and having a large C#/.NET application with source code available has far reaching benefits. For example, if you're a company that wants to create a product for obfuscating .NET assemblies (DLL's), or for auto-generating unit tests, Paint.NET is a great program to throw at your new tool. It's over 100,000 lines of code, it's not some small sample app, and it's something that real people use. Those are not two contrived examples, by the way -- I've seen websites with both of those where they used Paint.NET as a test case for their tools. We also use it internally at Microsoft for various purposes.[/I]

---

### Post by bruce89 on 2006-05-24
After somebody tries to get the source to 2.5, the lead developer says
> aafuss, what were you planning on doing with the source code, if I might ask?A bit suspecious, mabye?  Also on somebody asking if the source is still available they reply
> [making it a request only thing is] a temporary measure while we reevaluate and investigate some things. I can't say more, sorry.
I'm willing to say they are trying to stop its mono port.  Not absolutely sure why, but it is a Microsoft project.

---

### Post by INMCM on 2006-05-24
[QUOTE=bruce89]I'm willing to say they are trying to stop its mono port.  Not absolutely sure why, but it is a Microsoft project.[/QUOTE]

Actually no it's not a Microsoft project. The guys who wrote Paint.net work at Microsoft on other things  and do Paint.net it their spare time (they started it as a senior project while still in college). So unless MS has an unseen hand in the project and pressure came down from above (which is completly possible), the ties to microsoft don't matter that much. It also possible that the developers got "take our ball and go home" syndrome where they don't like that Mono is basically forking their work into a linux port.

OR someone might have been found to have been rebranding Paint.net and selling it as a commercial product without giving credit.

OR it could be a lot of things. We don't know and hopefully we will get some full discolsure soon.

---

### Post by bruce89 on 2006-05-24
> someone might have been found to have been rebranding Paint.net and selling it as a commercial product without giving credit.
They would be asking for it a bit by using the MIT licence?

---

### Post by BoyOfDestiny on 2006-05-24
[QUOTE=bruce89]They would be asking for it a bit by using the MIT licence?[/QUOTE]

Seems so. That's why I prefer the GPL. Nobody can close the code up (well unless they don't distribute it at all) and not share changes. 

I can only wonder how BSD devs feel competing against their own work that has now been closed (yes talking about os x's base)... 

I can say that would bother me....

---

### Post by INMCM on 2006-05-24
[QUOTE=bruce89]They would be asking for it a bit by using the MIT licence?[/QUOTE]
 
While researching a reply for that, I something interesting here: [http://www.eecs.wsu.edu/paint.net/download.html](http://www.eecs.wsu.edu/paint.net/download.html)

Paint.NET
Copyright (C) 2006 Rick Brewster, Chris Crosetto, Dennis Dietrich, Tom Jackson,
Michael Kelsey, Brandon Ortiz, Craig Taylor, Chris Trevino, and Luke Walker.
**Portions Copyright (C) 2006 Microsoft Corporation. All Rights Reserved.**

(emphasis mine)

Perhapes Microsoft IS behind this after all. This whole Mono port might not work well with their We Like Open Source/We Hate Open Source disinformation campaign.

edit: grammer, spelling

---

### Post by BoyOfDestiny on 2006-05-24
[QUOTE=INMCM]While researching a reply for that, I something interesting here: [http://www.eecs.wsu.edu/paint.net/download.html](http://www.eecs.wsu.edu/paint.net/download.html)

Paint.NET
Copyright (C) 2006 Rick Brewster, Chris Crosetto, Dennis Dietrich, Tom Jackson,
Michael Kelsey, Brandon Ortiz, Craig Taylor, Chris Trevino, and Luke Walker.
**Portions Copyright (C) 2006 Microsoft Corporation. All Rights Reserved.**

(emphasis mine)

Perhapes Microsoft IS behind this after all. This whole Mono port might not work well with their We Like Open Source/We Hate Open Source disinformation campaign.

edit: grammer, spelling[/QUOTE]

This corroborates what you are saying.

"Paint.NET includes code for Skybound's VisualStyles. This apparently involves some serious hacking to get user interface features to work right, so interface designers might want to learn from Paint.NET how it is done. Skybound's Web site does not allow for open disclosure of its source code. It could be that WSU negotiated a license beyond what is available to the public, but a license to release Skybound's hacks nonconfidentially would remove any trade secret restrictions Skybound placed on its code.

Looking closely, I noted that the Paint.NET source code does not actually include Skybound's source code. Instead, it just includes a DLL file. For those who are not familiar with the Windows operating system, or Linux users pretending to forget, a DLL (Dynamic Linked Library) file is a Windows-compiled object file that is not human-readable. As far as I know, DLLs can only be used on computer systems running the Windows operating system. In other words, Paint.NET is not as open as one would expect.

Paint.NET also includes the Windows Image Acquisition (WIA) Library v2.0, which Microsoft licenses under a EULA that allows for redistribution but not combination with GPL-ed code. Of course, the source for WIA is not included with Paint.NET."

[http://www.linuxinsider.com/story/39352.html](http://www.linuxinsider.com/story/39352.html)

EDIT: Just worth mentioning, I'm sure MS and apple love open source (especially BSD licensed). They can take it and close it up. MS dislikes the viral GPL ;)

---

### Post by bruce89 on 2006-06-08
Sorry about reposting to a dead thread, but they withdrew the source, as it is actually the famous aafuss, who steals code and claims it is his own - [http://en.wikipedia.org/wiki/Babya_logic](http://en.wikipedia.org/wiki/Babya_logic) see [http://paintdotnet.12.forumer.com/viewtopic.php?t=1331](http://paintdotnet.12.forumer.com/viewtopic.php?t=1331) for the forum topic.

---

### Post by pyros on 2006-07-17
well, just so anyone who cares knows, I just downloaded the source for version 2.64, right from the download page here:
[http://www.eecs.wsu.edu.nyud.net:8080/paint.net/files/zip3/pdn_src_2_64.zip](http://www.eecs.wsu.edu.nyud.net:8080/paint.net/files/zip3/pdn_src_2_64.zip)

now, if only I could get it to run...

---

### Post by %hMa@?b&lt;C on 2006-07-17
hmmm... I just downloaded it.

---

### Post by gummibaerchen on 2006-12-11
We need that for Linux, it's so great.

Any latest news?

---

### Post by dbbolton on 2006-12-11
i actually never liked that program, personally...

---

### Post by gummibaerchen on 2006-12-11
For windows it was at least very nice.

But the development is very closed :(

---

### Post by pyros on 2006-12-14
> **gummibaerchen said:**
> For windows it was at least very nice.

But the development is very closed :(

If I'm not mistaken, and it's not that unusual, the source is freely available. However, the program depends on a closed source dll file to do... well much of anything. that's not something created by the pain.net folks, but a third party.

---

### Post by DoctorMO on 2006-12-14
It also has clauses in the licience which prohibit forking so it's not open source or free software.

Hail to the gimp.

---

### Post by pyros on 2006-12-14
> **DoctorMO said:**
> It also has clauses in the licience which prohibit forking so it's not open source or free software.

Hail to the gimp.


I don't think so, but I'm no lawyer. It follows the standard mit license with a clause about the artwork:
> 
Paint.NET

Copyright (C) 2007 Rick Brewster, Chris Crosetto, Tom Jackson, Michael Kelsey, Brandon Ortiz, Craig Taylor, Chris Trevino, and Luke Walker. 

Portions Copyright (C) 2007 Microsoft Corporation. All Rights Reserved.



This software is licensed as per the MIT License below, but with one exception:



* The Paint.NET logo and icon artwork are Copyright (C) Rick Brewster. They are covered by the Creative Commons Attribution-NonCommercial-NoDerivs 2.5 license which is detailed here: [http://creativecommons.org/licenses/by-nc-nd/2.5/](http://creativecommons.org/licenses/by-nc-nd/2.5/) . Permission is granted to use the logo and icon artwork in ways that discuss or promote Paint.NET (e.g. blog and news posts about Paint.NET, "Made with Paint.NET" watermarks or insets).



MIT License: [http://www.opensource.org/licenses/mit-license.php](http://www.opensource.org/licenses/mit-license.php)



Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software **without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so**, subject to the following conditions:



The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.



THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
{emphasis added}

So whether or not they want people to fork is irrelevant; the license allows it. But like I've said, it depends on a closed-source, third-party lib, so not so hot for the portability. 

I think the real stigma attached to this project, and perhaps the reason for so much (apparently) incorrect (and generally negative) information about it stems from it's support by microsoft. It's no photoshop, and it certainly lacks the power of the gimp, but some excellent work can be done with this program. 

However, for the foreseeable future, porting paint.net to run in a true gnu/linux environment is not practical, and it is my opinion that all energies spent towards that purpose would be better used to improve the usability of the gimp... Nyea.

---

### Post by gummibaerchen on 2006-12-16
[http://tirania.org/blog/archive/2006/Dec-16-1.html](http://tirania.org/blog/archive/2006/Dec-16-1.html)

So Paint.Net for Linux is not too far :D

Hopefully someone will fork it...
(and also merge the official features, hugh)

---

### Post by ernstblaauw on 2007-02-26
At the moment, it is (again) possible to download the source code. See [http://www.getpaint.net/download.html]("http://www.getpaint.net/download.html").
Is there any news on the port to linux? I'm interested, but I couldn't find any news.

---

### Post by pyros on 2007-03-13
I don't think a port is going to happen, While I'm sure it is possible, someone is going to have to create a replacement for the portions of the program that are not open source. Not sure anyone is spending the time to do it.

---

### Post by karellen on 2007-03-13
well, it's their program, their source code, they can do whatever they want with it. I like paint.net, I use on xp instead of photoshop which I find it to be a little too much for me

---

