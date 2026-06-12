---
title: "Beginner-friendly ubuntu, has it already been discussed?"
date: 2006-08-04
forum: The Cafe
---

### Post by user1397 on 2006-08-04
I was just wondering, has there ever been talk of making a fork of ubuntu, but beginner-friendly?  As in ex-windows user firendly? I'm talking about adding all proprietary codecs, all the popular propritary software, such as skype and flash, all of that stuff in an install disc, and naming it something like "Simply Ubuntu"?  I'm just asking because it would be nice to have something like this, especially when trying to convert windows users.  Not having to take all the steps of the ubuntu-guide everytime you install ubuntu or want to show it to somebody would be nice.  

So, has anyone heard of any talk like this?  In the ubuntu forums or anywhere else?

---

### Post by Tomosaur on 2006-08-04
They wouldn't be allowed to distribute propietary codecs and stuff like that within a free OS. The user has to want the functionality they provide, and play like the creators want them to.

---

### Post by Brunellus on 2006-08-04
it's called SimplyMepis.

---

### Post by _simon_ on 2006-08-04
You'd need to decide what ***type*** of windows user you were aiming to convert.

My parents are in their 50's and still learning how to use windows. They won't even consider Ubuntu even with my offer to fully set it up for their needs. This is even though they are fed up with how slow their windows machines are running and how often they have to check for spyware etc,

---

### Post by aysiu on 2006-08-04
> **Brunellus said:**
> it's called SimplyMepis.
I agree.

Though, someone did propose something called [Nubuntu](http://www.ubuntuforums.org/showthread.php?t=194758).

---

### Post by user1397 on 2006-08-04
> **aysiu said:**
> I agree.

Though, someone did propose something called [Nubuntu]("http://www.ubuntuforums.org/showthread.php?t=194758").yep that's what i was looking for.  thanks aysiu.

---

### Post by atrus123 on 2006-08-04
I learned about Automatix recently.  With that, Ubuntu really is a completely n00b friendly distro.

---

### Post by user1397 on 2006-08-04
yea but people have to actually become aware of automatix before they install it, but it doesn't really solve everything, altho it does do quite an amazing job.  and, it changes your sources.list file, which is not so cool with me.  i personally dont use automatix. i config all the stuff i want by myself.  but thats just me.

---

### Post by Jucato on 2006-08-04
Ubuntu with out of the box proprietary stuff just isn't Ubuntu at all. It would probably share only the name, but not the spirit.

With regards to proprietary codecs/plugins, I think the best thing a "newbie friendly" Ubuntu derivative could do is to include Automatix or EasyUbuntu (or both) and make it easily accessible for newbies. That way, you stick to the spirit of Ubuntu (no non-free stuff by default), yet provide an easy way to access these much wanted/used codecs/plugins.

I think that some of the basic problems that most users new to Ubuntu/Linux encounter include:
1. Scattered/incomplete documentation/manuals. The offline documentation isn't that comprehensive, and the wiki is a bit disorganized for now.
2. No guided/visual tour for newbies. This would be nice. Advanced users may hate it, but I think the tour can have an option to dismiss/deactivate it easily.
3. like what erik1397 said, you have to be aware of Automatix or EasyUbuntu, or the forums, for that matter, before you can discover how to easily install proprietary/non-free stuff. A guided tour could easily include references to this. Although I'm not so sure that Canonical would approve of that.

---

### Post by confused57 on 2006-08-04
> **erik1397 said:**
> yea but people have to actually become aware of automatix before they install it, but it doesn't really solve everything, altho it does do quite an amazing job.  and, it changes your sources.list file, which is not so cool with me.  i personally dont use automatix. i config all the stuff i want by myself.  but thats just me.
After a new install, I use Automatix to add packages and programs and haven't had any problems...I probably should learn more about manually installing added functionality.
Automatix actually doesn't change your sources.list, unless you specify for it to...it warns you that allowing Automatix to change your sources.list may not be a good idea.
Nice links in your signature...

---

### Post by IYY on 2006-08-04
There are plenty of distros that do this already. Ubuntu = **F**ree software.

---

### Post by Jucato on 2006-08-04
AFAIK, Automatix does change your sources.list, otherwise it won't be able to download the necessary packages found in multiverse. But IIRC, it also restores your previous sources.list after it's done.

---

### Post by weatherman on 2006-08-04
is it actually illegal to make a script that allows a user to download certain software?

---

### Post by confused57 on 2006-08-04
> **Fenyx said:**
> AFAIK, Automatix does change your sources.list, otherwise it won't be able to download the necessary packages found in multiverse. But IIRC, it also restores your previous sources.list after it's done.
Good point, a beginner wouldn't know to enable the universe and multiverse repositories beforehand.

---

### Post by Jucato on 2006-08-04
> **weatherman said:**
> is it actually illegal to make a script that allows a user to download certain software?

Huh?? How come?

---

### Post by weatherman on 2006-08-04
> **Fenyx said:**
> Huh?? How come?
well I mean if it wasn't ubuntu would include something like automatix by default wouldn't it?

---

### Post by Jucato on 2006-08-04
If it was illegal, why would the forum set up a special section for it?

I think the only reason that Ubuntu doesn't include Automatix by default is because of its philosophy/commitment to Free/Open Source Software. Maybe for them, having those proprietary packages in the multiverse repositories is enough of a compromise on their part.

Of course, that's just my opinion. But I'm absolutely sure it isn't illegal in anyway.

---

### Post by weatherman on 2006-08-04
> **Fenyx said:**
> If it was illegal, why would the forum set up a special section for it?

I think the only reason that Ubuntu doesn't include Automatix by default is because of its philosophy/commitment to Free/Open Source Software. Maybe for them, having those proprietary packages in the multiverse repositories is enough of a compromise on their part.

Of course, that's just my opinion. But I'm absolutely sure it isn't illegal in anyway.

well so what about stuff like libdecss which is afaik free software?

---

### Post by aysiu on 2006-08-04
There are at least two kinds of "illegal" relevant to this discussion--illegal to use and illegal to distribute. I believe there are certain codecs you can legally use if you install them yourself, but that Ubuntu cannot legally distribute unless they pay a licensing fee.

That said, I agree with Fenyx--it mainly has to do with the Ubuntu commitment to free software.

---

### Post by Jucato on 2006-08-04
well, non-free packages are only part of the whole picture why Ubuntu doesn't include these things out of the box. Another is copyright/patent issues:

From [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

> 
Ubuntu strives to make every piece of software available under the licensing terms laid out in the [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] Ubuntu License Policy]("http://www.ubuntu.com/ubuntu/licensing"). Patent and copyright restrictions complicate a free operating system's ability to distribute software that will support proprietary or non-free formats. 
 Ubuntu's commitment to only include completely free software by default, means that proprietary media formats aren't setup 'out of the box'. This page will show you how to enable support for the most popular non-free media formats. 
 If all of this seems like a lot of work to get non-free media playback up and running, please remember that Ubuntu's hands are tied by patents and license restrictions in some countries. Look to the future and make sure that "Digital Rights Managent" (DRM) and similar restrictions are carefully monitored by you, the open source community and free software users. 
 See Ubuntu's [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] Free Software Philosophy]("http://www.ubuntu.com/ubuntu/philosophy") and the [FreeFormats]("https://help.ubuntu.com/community/FreeFormats") page for a more comprehensive discussion of these issues.  [LIST]
[*]**Legal Notice** *Patent and copyright laws operate differently depending on which country you are in. Please obtain legal advice if you are unsure whether a particular patent or restriction applies to a media format you wish to use in your country.*[/LIST]

---

### Post by TravisNewman on 2006-08-04
it's free software, but it violates software patents.

to people talking about nUbuntu, keep in mind that if you search for nUbuntu you might come up with the ORIGINAL nUbuntu, the one geared toward Network Security.

---

### Post by Jucato on 2006-08-04
Couldn't they rename it to Newbuntu? It's geared towards "new"-bies anyway. But it does sound a bit... cheesy (for lack of a better adjective).

---

### Post by user1397 on 2006-08-04
> **Fenyx said:**
> Couldn't they rename it to Newbuntu? It's geared towards "new"-bies anyway. But it does sound a bit... cheesy (for lack of a better adjective).i think newbuntu does the job, but what about simpleUbuntu?

---

### Post by Brunellus on 2006-08-05
debate about the naming is pointless. 

SimiplyMEPIS does everything the OP wants.  As of the current stable version, SimplyMEPIS uses an Ubuntu core.  For all intents and purposes, it is now an Ubuntu distro that has assumed the risks involved in redistributing the packages it does.

---

### Post by Jucato on 2006-08-05
Not completely true Brunellus.

The naming "debate" may be pointless, but not to those developing that project.

SimplyMEPIS no longer has out of the box MP3 support (you need to do an upgrade to fix that, but still not out of the box). There are many things where SimplyMEPIS and Ubuntu differ, both in appearance and under the hood. So given the choice between a) having an Ubuntu derivative with very easy access to restricted formats and b) using an Ubuntu derivative that has most restricted formats installed but where I have to install GNOME and tweak it, I'd prefer the former any time.

Of course, if something like a SimplyMEPIS-GNOME Edition comes out, then I could reconsider.

---

