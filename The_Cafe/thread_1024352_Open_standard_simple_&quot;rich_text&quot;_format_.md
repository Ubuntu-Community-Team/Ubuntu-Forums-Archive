---
title: "Open standard simple &quot;rich text&quot; format?  (like RTF)"
date: 2008-12-28
forum: The Cafe
---

### Post by misGnomer on 2008-12-28
Most of the text documents I create (or save from the web) are in plain text format and the ones needing proper formatting or printing are formatted with OpenOffice.

Yet I often find myself hoping that there would be a simple, open and widely-supported RTF-like rich text format for very simple formatting tasks like bold or italics for those times when I'd like to highlight important passages or keywords in the text.

Perhaps something like a truly standards-based subset of the old RTF format (by that windows company), or perhaps even a tiny but easily supportable subset of the .ODT OpenDocument text format...

Yes, something very similar to the most elementary HTML/XML markup, made fully usable with an optional toolbar (simplified version of the editor toolbar in this and many other web forums) that could be e.g. implemented in Gedit as a plugin.

Would there be any point in considering a very lightweight rich text format as the "new, open RTF format" that could easily be supported by any open (or even non-open) apps from editors to xterminals, with the simple formatting also saved during copying and pasting?

---

### Post by mikjp on 2008-12-29
Wouldn't it be better to have good support for .odt in the first place?

There are of course some lightweight markup languages that partly fill the niche (except for the cross-application cut & paste). Try for example txt2tags.

Greetings,

mikko

---

### Post by misGnomer on 2008-12-29
A tiny subset of .odt tags would certainly do the trick.

It'd even be neat to be able to open .odt documents in Gedit or Leafpad etc. and have *some* basic formatting retained. Or alternatively I could do the all basic text entry and formatting with Gedit and later just open the file in OO.o or Abiword and have the simple formatting still there.

The key would be in making the "Simple Rich Text" (".srt"?) format universally and easily implemented in existing text tools, including x-terminals and even with cut/copy/paste-ability between ubiquitous browser entry boxes like this reply editor I'm in right now. Think copying simply formatted web page text and pasting it in Gedit as either plain text or with some formatting intact.

A slightly more versatile alternative to the ASCII/Unicode .txt format.

---

### Post by geoken on 2008-12-29
I don't understand why you would need a new format. Your post mentioned HTML, what's wrong with using that and just obfuscating the tags below a toolbar?

The editor toolbar in this and many other forums is itself working with HTML.

---

### Post by misGnomer on 2008-12-30
Geoken, you're right. A subset of HTML would behave very much like RTF or stripped-down .odt OpenDocument Text format.

Perhaps my personal aversion to HTML stems from its abuse in email...? But even there the unwanted tags are easily stripped.  ;-)

Whichever format was adopted - and properly stripped down to most basic layout/formatting functionality - I wouldn't really care that much, as long as everyone would agree to adopt it as a standard (at least within the OSS community).

Not everyone needs or even cares about the "ASCII/Unicode text+basic formatting" functionality, but I believe lot of people would benefit from it. Those who wouldn't care could simply leave their "phasers not to stun", i.e. just ignore the formatting and continue using plain text as before.

Initially some old unix apps expecting ASCII might groan, but everything within the living Linux ecosystem could be easily patched. In fact the "enhanced text exchange" should involve a new "non-secret handshake" without which the transmitting app would default to plain text. Yet within my GPL'd Linux environment more and more apps would start understanding richer text.

Btw. as just another example I usually have Gnome Terminal open in one corner for various quick tasks or real time scrolling, and it gives me nice formatted information with colour highlights etc.

Now, if I want to copy some of that screen data or redirect it to a log file the formatting will be lost unless the viewer app was using the same set of highlight parameters.

Yet I might like the ability to keep that minimal highlight formatting (with ignoring it being optional) when I copy text from terminal to elsewhere (like right here or to email etc.).

Full HTML or .ODT file format standards are both very large and relatively fast-moving targets too (not to mention problems with cross-platform adoptation), but a tiny subset of markup tags would work just fine.

The OpenDoc standard of the 1990s by Apple and IBM went way beyond "simple rich text", but I am not suggesting offering video containers or spreadsheet viewers inside x-term windows (really potentially everywhere!) but simply enhancing plain text data exchange between all apps dealing in text presentation or manipulation.

The MIME/filetype suffix would also be a usability factor since no one would like their system full of .htm or .odt files (default action being open with Firefox or OpenOffice!) when in reality they're just .txt with minor formatting applied.

---

### Post by AnRa on 2008-12-30
> **misGnomer said:**
> Geoken, you're right. A subset of HTML would behave very much like RTF or stripped-down .odt OpenDocument Text format.[Enriched text](http://en.wikipedia.org/wiki/Enriched_text)

---

### Post by misGnomer on 2008-12-30
> **AnRa said:**
> [Enriched text](http://en.wikipedia.org/wiki/Enriched_text)

Excellent! This [RFC for text/enriched MIME Content-type](http://www.rfc-editor.org/rfc/rfc1896.txt) specification is very much what I was after.

The authors were thinking about enhanced email text (without the relative bloat of HTML and related security problems) but obviously the same principles apply to most of today's text presentation and manipulation.

It also looks like this specification was intended to mesh transparently with plain ASCII/Unicode text in .txt files. In practise this would mean that enriched-text-aware apps would automatically display .txt files with enhanced formatting while the apps yet to adopt the standard would default to good old plain text like today.

With a text/enriched plugin with an optional simple "word processing-style toolbar" for Gedit (et al), users could choose to be much more expressive with their "plain text" and later when system-wide data interchange mechanisms were updated (by Freedesktop.org) one could also simply copy text from any text-presenting app and paste it to another with basic formatting intact (or stripped if so desired)!

I wonder if Ubuntu developers would consider looking at this proposed text/enriched MIME Content-type RFC specification with an eye for slightly updating it for today's needs and then further proposing it as a common Open Software standard via Freedesktop.org?

---

### Post by Vadi on 2008-12-30
PDF's if you need them read-only ;)

---

### Post by misGnomer on 2009-01-01
Nah. I'd like to have this enriched text format specifically for better editing and cross-application exchange. :-)

As it happens Apple took PostScript/PDF and tailored it (royalty-free) for their own (private) purposes; for composing stuff on the screen.

What I'd hope to see is the OSS developer community taking an existing RFC (initially cross-platform idea for email use) proposal and using it to enhance the scope (optional formatting) of the common plain text just a little bit.

Why should the proprietary companies get all the fun creating new and useful file formats (or minor adaptations to plain .txt)?

Here the Free Software groups could kick that ball downhill and set an open standard that could displace the proprietary and increasingly bloated .rtf!!

---

