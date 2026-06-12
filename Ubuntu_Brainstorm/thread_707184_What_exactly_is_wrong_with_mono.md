---
title: "What exactly is wrong with mono"
date: 2008-02-25
forum: Ubuntu Brainstorm
---

### Post by MaxCharge on 2008-02-25
Firstly, i wanted to split this out from that other thread which is a raging discussion on whether mono should be included in Ubuntu or not. If a mod thinks it really should be part of that discussion, i'll dump this thread and start the discussion in there. It's just i have a very specific question in mind and i don't want it to get swamped in that thread.

First, a few guidelines:
1) I do do not want to hear about how great Mono is or how great X is. Everyone has their own opinoin. Let's assume everything is great in a technical sense.
2) I do not want to hear anything that doesn't have a link to back it up. If you make a claim about something, make sure you can back it up. Links to rants in blogs aren't acceptable.
3) I do not want to hear that M$ is evil and is out to take over the world. I know they are a **convicted** monopoly, but that's not relevant to this question.
4) I do not want to hear about other issues you have with other applications/libraries that use Mono. For example, just because application X exists and it's bad doesn't mean mono should be removed.
My very specific question is:


*What **exactly** is it in mono that you want removed? Secondly, **why** do you want those **specific** components removed*


A) The JIT and .NET environment, [as standardised here]("http://www.ecma-international.org/publications/standards/Ecma-335.htm")
B) The C# language itself, [as standardised here]("http://www.ecma-international.org/publications/standards/Ecma-334.htm")
C) The ECMA'ed class libraries, which i believe [are also covered here]("http://www.ecma-international.org/publications/standards/Ecma-335.htm")
D) The non-ECMA'ed libraries such as Winforms
E) The .NET libraries which facilitate interop with native linux libraries such as GTK#, glib# etc
F) The third party applications such as Banshee, Beagle, Fspot etc

I think that covers all the obvious ways to split up the mono stack, so tell me (assuming you want mono removed from Ubuntu by default), why is it you want these components removed. What is your argument.

EDIT: Reworded point E to make my point clearer, 'proprietary' was the wrong word to use.

---

### Post by gnomeuser on 2008-02-25
E) The linux proprietary libraries such as GTK#??

GTK# is not proprietary, it is under an OSI license and entirely developed in the open.

> 
Proprietary indicates that a party, or proprietor, exercises private ownership, control or use over an item of property, usually to the exclusion of other parties.
en.wikipedia.org/wiki/Proprietary

---

### Post by MaxCharge on 2008-02-25
Hrmm... a bad choice of words perhaps. How about 'native to linux libraries'. The group of libraries i'm trying to include are ones that wrap native linux stuff like GTK, glib etc. I'm talking about libraries whose only function is to facilitate interop between existing linux libraries and .NET languages.

I'll edit the above to reflect more clearly what i was trying to say.

---

### Post by Simon G Best on 2008-02-26
> **MaxCharge said:**
> Secondly, **why** do you want those **specific** components removed[/I]

You ask "why", having already refused to allow whole categories of possible answers!

> ... so tell me (assuming you want mono removed from Ubuntu by default), why is it you want these components removed. What is your argument.

Asking that when, in the same post, you sought to disallow whole categories of arguments is plainly disingenuous.  Is that really what supporters of Mono have to resort to?

Update: I've reported this thread and requested its deletion or closure, as, at best, it's a redundant duplicate of the following, older thread:-

[http://ubuntuforums.org/showthread.php?t=594767]("http://ubuntuforums.org/showthread.php?t=594767")

---

### Post by PmDematagoda on 2008-02-26
This thread has been closed as it's title is satisfied by the content in the other Mono thread.

If the OP wishes to know what is wrong with Mono then just refer this [thread]("http://ubuntuforums.org/showthread.php?t=594767").

---

