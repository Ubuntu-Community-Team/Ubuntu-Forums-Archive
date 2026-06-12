---
title: "Simple Text Editor for Stripping HTML?"
date: 2016-03-24
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2016-03-24
i'm a little frustrated lately. Seems that every Linux "Notepad" I try, like leafpad, knote, Kate, etc... is preserving metadata. My habit, if I'm copying something from the web into Writer, is to use Leafpad to strip any metadata. 

It's stopped working consistently.

Is there a simple text editor that will brutally strip everything from the text (so I can paste into and out of it) that ya'll can recommend?

---

### Post by vasa1 on 2016-03-24
> **VTPoet said:**
> ...
It's stopped working *consistently*.
...
Meaning? What exactly happens? Are there certain characters that misbehave?

---

### Post by sudodus on 2016-03-24
I think you have to check different text editors (and maybe it depends on how you copy it too).

Try geany :-)

---

### Post by neu5eeCh on 2016-03-24
> **vasa1 said:**
> Meaning? What exactly happens? Are there certain characters that misbehave?

For example, text color, size and other sundry HTML specific codes will be preserved despite pasting into and out of LeafPad or Kate.

**EDIT: **Another example would be preserving foreign country code. This is really weird (and the Libre devs don't consider it a bug) but if you paste a word from a French language website into LibreOffice (let's assume your default language is English) it will change all the autocorrect features (for that paragraph) into French. So, for example, instead of getting a smart quote, you will get the French version, something like this: >> or <<. It does this because the French language meta-attribute isn't stripped by Leafpad and when you post the text into LibreOffice, Libre's autocorrect suddenly assumes you have switched your citizenship and are now French.

---

### Post by neu5eeCh on 2016-03-24
> **sudodus said:**
> I think you have to check different text editors (and maybe it depends on how you copy it too).

Try geany :-)

Nope. Just installed and tried Geany. No satisfaction. I suppose I could paste into terminal but that's just a PITA. There *has* to be a no frills text editor that will do this.

---

### Post by vasa1 on 2016-03-24
I'm sorry I still don't get it :(

Here, I've pasted into Mousepad. ctrl+c, ctrl+v.

---

### Post by sudodus on 2016-03-24
> **VTPoet said:**
> Nope. Just installed and tried Geany. No satisfaction. I suppose I could paste into terminal but that's just a PITA. There *has* to be a no frills text editor that will do this.

Which version and flavour of Ubuntu are you running, when you are affected by this problem?

I have been using the method you describe for years to get clean text.

Please tell us which web page you copy from, and which method you use *mark and middleclick* or *ctrl C and ctrl V* or some other method!

-0-

I guess you can try nano. It should be 'dumb enough'. But the problem might not be the editor, but the copying method.

---

### Post by neu5eeCh on 2016-03-24
> **sudodus said:**
> Which version and flavour of Ubuntu are you running, when you are affected by this problem?

15.10 Ubuntu


> **sudodus said:**
> I have been using the method you describe for years to get clean text.

Me too. I think devs have been fiddling with some text editors ("adding features"). Hey, I just got Mousepad to work. :)

> **sudodus said:**
> Please tell us which web page you copy from, and which method you use *mark and middleclick* or *ctrl C and ctrl V* or some other method!

Okay, but it's kind of random (for a fictional story I'm working on). The following is the website:

[http://www.jews-for-allah.org/jewish-mythson-islam/muslims-worship-stone.htm](http://www.jews-for-allah.org/jewish-mythson-islam/muslims-worship-stone.htm)

I was being lazy and copying the following into Libre (for editing):

[COLOR=#ff0000]"If Islam is so against any form of idol worship, why do they bow to the kaaba? Why do they call it God's House? Do they believe He lives there?"

See how it changes everything I type? This is after passing it through Leafpad. Ctrl-C ---> Ctrl-V ---> Ctrl-C. Probably a warning to stay away from this subject matter. But Mousepad worked.

[/COLOR]

---

### Post by sudodus on 2016-03-24
I'm in Lubuntu Xenial now (at Beta 2), and have no problem with leafpad pasting from that page. I'll try in Ubuntu 15.10 ...

---

### Post by sudodus on 2016-03-24
I'm testing in a Wily live system, not up-to-date (no update/dist-upgrade).

It looks good here too. I'm using the default editor, gedit.

I don't know, maybe your problem is caused by some upgrade in Wily or some glitch in your particular system. But it does not affect my Xenial, so you will get rid of this problem soon I think.

Have you tried to reboot? Maybe it starts to behave normally again.

Anyway, I'm glad mousepad works for you. I think it matches leafpad pretty well.

---

### Post by neu5eeCh on 2016-03-24
You know, in hindsight, it's possible that the copy/paste feature of ubuntu was being flaky. I've had that happen before.  

And once the metadata gets into Libre, even erasing the pasted text doesn't eliminate the metadata, so that even if I tried a different text editor the results were the same because the metadata was still stuck in Libre. 

Anyway, if you want to try out that other Libre bug I was telling you about. Visit this page:
[URL="http://https://translate.google.com/#auto/fr/horseradish"]
https://translate.google.com/#auto/fr/horseradish[/URL]

Copy and paste the French translation "raifort" directly into libreoffice, then hit the quote key. See what happens. :)

---

### Post by sudodus on 2016-03-24
No problems for me (in Xenial Beta 2)

***Edit:*** Now I know what you mean - it changed the keyboard (but only inside Libre Office), not for all keys, but clearly for the 'double-quote' key.

---

### Post by vasa1 on 2016-03-24
Bringing LibreOffice into the picture complicates things a bit. The thrust of this thread, IMO, was that copying stuff from a web page and pasting into Leafpad generated colored and formatted text in Leafpad. Quoting from the 4th post:> For example, text color, size and other sundry HTML specific codes will be preserved despite pasting into and out of LeafPad or Kate. I have never seen that and wonder, even now, how that is possible with any self-respecting text editor.

One the other issue: LibreOffice has a default "feature" of converting simple quotes into smart quotes. I turn that off.

---

