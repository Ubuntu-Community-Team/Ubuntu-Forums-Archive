---
title: "Shared Source Liscensing"
date: 2006-07-18
forum: The Cafe
---

### Post by KingBahamut on 2006-07-18
"Microsoft has posted a shared source version of its device emulator (which ships with Visual Studio 2005) for download. Primarily meant for academia to experiment with and build upon, it is licensed under the Microsoft Shared Source Academic License. Since it emulates the ARM processor, it can run all modern Windows Mobile and Windows CE operating systems. Barry Bond, the architect behind the emulator (and also Rotor, one of Microsoft's previous shared source offerings) has a blog post on the release."

External Links
[http://www.microsoft.com/downloads/details.aspx?FamilyID=faa8c81d-7316-4461-a0ed-6c95b261ddcd&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=faa8c81d-7316-4461-a0ed-6c95b261ddcd&DisplayLang=en)
[http://msdn.microsoft.com/vstudio/license/de_academic.aspx](http://msdn.microsoft.com/vstudio/license/de_academic.aspx)
[http://blogs.msdn.com/barrybo](http://blogs.msdn.com/barrybo)
[http://blogs.msdn.com/barrybo/archive/2006/07/17/668492.aspx](http://blogs.msdn.com/barrybo/archive/2006/07/17/668492.aspx)

I have been interested in the shared source lisc. since MSFT released their SourceForge wannabe the Codeplex. This seems almost a classic "build upon" type of development more than it is an actual program per se. What do you guys/gals think?

---

### Post by ComplexNumber on 2006-07-18
> it can run all modern Windows Mobile and Windows CE operating systems. given the number of complaints about WM5(windows mobile 5) on all the forums, i'm surprised anyone would want to bother to write anything for WM5. people think windows on the desktop is bad,  but WM5 must be one of the most inefficient and unstable OS's available for any mobile. it must be why their smartphone market share presently stands at approx 2.5%(and dwindling), whilst linux has 25%+(and growing) and symbian has 66%(and dwindling).

---

### Post by Brunellus on 2006-07-18
Will someone explain to me what MS is trying to achieve with the "shared source initiative" anyway?

From what i can see, there are 3 licenses at play-- the "permissive" license, which reads to my (as yet untrained) eye like a classic BSD license, the "community" license, which looks like it might even be close to GPL-compatible (?), and the "reference" license, which seems like it might be total arse (here's the source. Don't use it!).

Why?

---

### Post by KingBahamut on 2006-07-18
My concern centers on the community liscense. Is it possible that code developed under such a liscense that intermingles with GPL could would become suspect? 

The primary worry of Proprietary developers seems centered around the idea that Proprietary and OSS code has clear seperate boundaries. This is done primarily in affect to stop from -- and proprietary developers use similar words -- infecting code. 

What happens when Community liscense code and GPL code clash?

---

### Post by ComplexNumber on 2006-07-18
> Will someone explain to me what MS is trying to achieve with the "shared source initiative" anyway? i don't know exactly, but from past experience, anything micosoft does seems ominous to me. perhaps they are just trying to get along with linux because they know that they can't kill it, although i suspect that it is their way of crushing linux (eventually) by fighting fire with fire (they know that they can't win by using propriatary vs open source). i would bet that it is their 'embrace and extend' of the GPL.  [here]("http://www.microsoft.com/resources/sharedsource/licensingbasics/sharedsourcelicenses.mspx") is microsfts explanation for their motives.

---

