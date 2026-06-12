---
title: "why does MS call their .docx .pptx (etc.) formats 'Office Open XML'?"
date: 2010-09-06
forum: The Cafe
---

### Post by Dustin2128 on 2010-09-06
just wondering. It makes them sound like an open office thing when half the original point was to break interoperability. I was pleasantly surprised, by the way, to see that OO now supports saving in those formats.

---

### Post by valbaca on 2010-09-06
> **Dustin2128 said:**
> just wondering. It makes them sound like an open office thing when half the original point was to break interoperability. I was pleasantly surprised, by the way, to see that OO now supports saving in those formats.

It comes down to Microsoft trying to get rush their new Office formats to be an ISO standard and thus block out OpenOffice.org

The real "answer" will probably be the subject of Stallman's next book (lol) but here's some info in the meantime.

[http://en.wikipedia.org/wiki/Office_open_xml](http://en.wikipedia.org/wiki/Office_open_xml)

[http://en.wikipedia.org/wiki/OpenOffice.org](http://en.wikipedia.org/wiki/OpenOffice.org)

[http://www.fsf.org/campaigns/opendocument/](http://www.fsf.org/campaigns/opendocument/)

---

### Post by Dustin2128 on 2010-09-06
I'm quite happy that open document formats are the the actual standard for office documents. Yet another reason to give those lazy office 07 (supports saving to open document) users.

---

### Post by KiwiNZ on 2010-09-06
[http://www.microsoft.com/standards/openxml/](http://www.microsoft.com/standards/openxml/)

---

### Post by Dustin2128 on 2010-09-06
> **KiwiNZ said:**
> [http://www.microsoft.com/standards/openxml/](http://www.microsoft.com/standards/openxml/)
That was a bit informative, thanks, but I tend not to trust company documentation :)
On a side note, does anyone know how good docx compatibility is between OO and MSO?
The reason I'm kind of skeptical, by the way, is because if they want an open standard so much, why are they pushing their new one and not the established, already standard open document format? Its not like its going to profit them; its open!

---

### Post by borth92 on 2010-09-06
> **Dustin2128 said:**
> That was a bit informative, thanks, but I tend not to trust company documentation :)
On a side note, does anyone know how good docx compatibility is between OO and MSO?
The reason I'm kind of skeptical, by the way, is because if they want an open standard so much, why are they pushing theirs and not open document format? Its not like its going to profit them; its open!

they make money off of forcing people to buy M$O because they have the standard and nobody else supports it.

---

### Post by valbaca on 2010-09-06
borth92's signature about sums up the Microsoft Office/OpenOffice.org issue

---

### Post by Dustin2128 on 2010-09-06
> **borth92 said:**
> they make money off of forcing people to buy M$O because they have the standard and nobody else supports it.
if its an open standard, everyone else can support it. That's what's confusing me...
EDIT: or are you talking about ignorant upgraders?

---

### Post by Spr0k3t on 2010-09-07
Microsoft's use of the word Open is not in the same sense of the term Open.  It's a marketing hatchery... not much else.

---

### Post by mendhak on 2010-09-07
It's an ISO/ECMA standard.  It doesn't matter where it came from.  Or how much controversy surrounded it.

The suites that support OOXML so far are OpenOffice, SoftMaker Office, KOffice, JOffice, iWork, Lotus Notes, WordPerfect and Google Docs.

A lot argue in favor of ODF because it was there first, and wonder why MS didn't simply work with Oasis to extend ODF.  Oasis doesn't want to extend ODF for Microsoft.  It's the usual technopolitics.  

Both are as 'free' and 'open' as the other, but it's the association with Microsoft that may prevent some from seeing past it.  What I'm saying is, there are politics on both sides here.  *Nobody* is innocent.

---

### Post by earthpigg on 2010-09-07
> **mendhak said:**
> Both are as 'free' and 'open' as the other, but it's the association with Microsoft that may prevent some from seeing past it.  What I'm saying is, there are politics on both sides here.  *Nobody* is innocent.

ODF isn't encumbered by patents.

If you implement the .docx standards *differently that the specification outlined by Microsoft*, you are liable to be sued for patent infringement. 

[Source]("http://www.microsoft.com/interop/osp/default.mspx"):

> Microsoft irrevocably promises not to assert any Microsoft Necessary Claims against you for making, using, selling, offering for sale, importing or distributing any implementation ***to the extent it conforms to a Covered Specification*** (“Covered Implementation”) ... To clarify, “Microsoft Necessary Claims” are those claims of Microsoft-owned or Microsoft-controlled patents that are necessary to implement only the required portions of the Covered Specification that are described in detail and not merely referenced in such Specification. “Covered Specifications” are listed below. 

So, for example, if you add a feature to one of the specifications ... well, you had better have your lawyers ready.

An example feature would be adding the ability to embed Theora video in a presentation or document and ***save the presentation/document in an Office Open XML format***. You can't even save it as a different file extension indicating a modified implementation of the standard, as modifications of the standard in any way are prohibited. If you do this, then the promise not to assert patent infringement is void.

---

### Post by red_Marvin on 2010-09-07
There is no point in having a standard if everybody makes their own small additions/changes to it. The same argument has been made against MS and that people should be weary of when MS says they are supporting a standard (embrace extend extinguish).

It is only fair that this reasoning should go both ways.

However I don't approve of the patent rattling, and I think that the inclusion of an open codec in the standard at hand would only be positive.

But standards should be treated as standards because they are *standards*.

---

### Post by kamaboko on 2010-09-07
This is the nice thing about standards; there are so many of them.

---

### Post by zekopeko on 2010-09-07
> **earthpigg said:**
> ODF isn't encumbered by patents.

This is patently untrue.

From [http://www.oasis-open.org/committees/office/ipr.php](http://www.oasis-open.org/committees/office/ipr.php) :

> Sun irrevocably covenants that, subject solely to the reciprocity requirement described below, it will not seek to enforce any of its enforceable U.S. or foreign patents against any implementation of the Open Document Format for Office Applications (OpenDocument) v1.0 Specification, or of any subsequent version thereof ("OpenDocument Implementation") **in which development Sun participates** to the point of incurring an obligation, as defined by the rules of OASIS, to grant (or commit to grant) patent licenses or make equivalent non-assertion covenants.


The part in bold is very problematic since any extension that OASIS does to ODF without Sun/Oracle is at risk.

So please stop exalting ODF since it's a poorer standard then OOXML and has even more legal ambiguity and problems then OOXML.

---

### Post by forrestcupp on 2010-09-07
> **earthpigg said:**
> 
An example feature would be adding the ability to embed Theora video in a presentation or document and ***save the presentation/document in an Office Open XML format***. You can't even save it as a different file extension indicating a modified implementation of the standard, as modifications of the standard in any way are prohibited. If you do this, then the promise not to assert patent infringement is void.

But if you're going to change how it works and even change the file extension, why would you go that route in the first place?  The only reason I see to even use OOXML is for MS Office compatibility, and if you break that, what's the point?

---

### Post by Hagar Delest on 2010-09-08
Some hints also here: [MS Office 2007 OOXML file format (docx, xslx, pptx, ppsx)]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=5&t=4542") (see first links, especially the groklaw site).

ODF has been ISO certified in 2006 IIRC, 3 years before OOXML. "Open" is a rather nice marketing tag nowadays, hence its use to fake some promise of interoperability. The format is not completely documented IIRC, and there are some bugs. If the format had been a real plus, why would have been so much lobbying (I'm kind with this word) from MS on each national bodies? Even in France, the AFNOR said 'no' in September for the first round ballot and then to the general surprise, said 'yes' for the second round in May for final approval. And this is indeed a matter of politics. Some high ranking decision has been mentioned...

---

### Post by zekopeko on 2010-09-08
> **Hagar de l'Est said:**
> Some hints also here: [MS Office 2007 OOXML file format (docx, xslx, pptx, ppsx)]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=5&t=4542") (see first links, especially the groklaw site).

ODF has been ISO certified in 2006 IIRC, 3 years before OOXML. "Open" is a rather nice marketing tag nowadays, hence its use to fake some promise of interoperability. The format is not completely documented IIRC, and there are some bugs. If the format had been a real plus, why would have been so much lobbying (I'm kind with this word) from MS on each national bodies? Even in France, the AFNOR said 'no' in September for the first round ballot and then to the general surprise, said 'yes' for the second round in May for final approval. And this is indeed a matter of politics. Some high ranking decision has been mentioned...

ODF is also shrouded in politics and technically is/was far less refined then OOXML.

---

### Post by earthpigg on 2010-09-08
> **forrestcupp said:**
> But if you're going to change how it works and even change the file extension, why would you go that route in the first place?  The only reason I see to even use OOXML is for MS Office compatibility, and if you break that, what's the point?

the point would potentially be whatever the point is of any fork.

---

### Post by MrNatewood on 2010-09-09
If it's such an open standard, why isn't there any proper support for reading it's document formatting in any linux office app?

Is it that nobody bothered to implement it? I find that hard to believe as a a lot of people stay with microsoft because they can read documents sent to them in doc/docx properly.

---

### Post by ssam on 2010-09-09
ODF is built on existing standards as much as possible, to make it easy to implement. for example it uses the existing SVG for vector graphics.

MS OOXML, is based on the doc format. it has awkward things like multiple date formates to retain compatibility with bugs in old excel version, and tags like "autoSpaceLikeWord95, footnoteLayoutLikeWW8, lineWrapLikeWord6".

i guess that microsoft's choice of name was to increase confusion. it would be like openoffice.org choosing the name "OO micro soft format"

the speed at which the MS format got through ISO despite objections was very strange.

this is worth a read.
[http://www.freesoftwaremagazine.com/articles/odf_ooxml_technical_white_paper?page=0%2C0](http://www.freesoftwaremagazine.com/articles/odf_ooxml_technical_white_paper?page=0%2C0)

---

### Post by Hagar Delest on 2010-09-09
> **zekopeko said:**
> ODF is also shrouded in politics and technically is/was far less refined then OOXML.
Do you say that because the OOXML specification is 6000 pages long whereas ODF is about 600? Maybe the 6000 are also to confuse whoever tries to implement it.

The strange MS names for functions refer to proprietary features (not documented), hence a hardly open format at all!

Note that ODF has been designed to create a standard that can be implemented by any application. It's not dedicated to a specific application (like OOXML clearly is). It's a good thing that OOo hasn't a specific format but uses a true standard.

---

### Post by zekopeko on 2010-09-09
> **Hagar de l'Est said:**
> Do you say that because the OOXML specification is 6000 pages long whereas ODF is about 600? Maybe the 6000 are also to confuse whoever tries to implement it.

I suggest you read up on ODF before commenting. Their spreadsheets specification was especially horrible. There were a few posts on planet.gnome.org from developers of Gnumeric about it.

Those 6000 pages are a good thing since it's generally better to have a nicely defined standard then not. IIRC it even isn't 6000 pages but less if you remove the huge margins, font size and other thins that bloated the page size.

> The strange MS names for functions refer to proprietary features (not documented), hence a hardly open format at all!

This is certainly a valid criticism if true. 

> Note that ODF has been designed to create a standard that can be implemented by any application. It's not dedicated to a specific application (like OOXML clearly is). It's a good thing that OOo hasn't a specific format but uses a true standard.

This is incorrect. Thanks to the above mentioned lack of good specification (those 600 pages you mention) ODF has been hard to implement since parts of the ODF format, that aren't defined in the specification, are implemented in OpenOffice.org code while they should be in the specification. This means that bugs in OO.org code get translated into being bugs in the ODF specification.

OOXML was FUD-ed extremely well while it is in a far better shape then ODF. I have no doubt that MS wanted to standardize OOXML to profit from it and used some underhanded tactics in the ISO voting process, but that still doesn't make OOXML suck.

---

### Post by Hagar Delest on 2010-09-10
I can't argue further since I'm not a specialist enough. I've picked up some information on the Groklaw site at the ballot time but haven't followed it very closely. So anyone wanting to get the details should go to that site and the noooxml one.

---

### Post by zekopeko on 2010-09-10
> **Hagar de l'Est said:**
> I can't argue further since I'm not a specialist enough. I've picked up some information on the Groklaw site at the ballot time but haven't followed it very closely. So anyone wanting to get the details should go to that site and the noooxml one.

If you want a clearer picture you shouldn't get your news from a single source. Groklaw is a biased source (they do have good articles but have an extremely pro-FOSS/IBM agenda which tends to blind them).

---

