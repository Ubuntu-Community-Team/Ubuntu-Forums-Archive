---
title: "OpenOffice.org Calc adds support for Excel VBA"
date: 2006-11-18
forum: The Cafe
---

### Post by newbie2 on 2006-11-18
> As an Excel user, you may have looked at OpenOffice.org and found that it doesn't support Visual Basic for Applications (VBA), the Microsoft Office macro language. If you've spent years building hundreds of Excel macros, the fear of losing them all could keep you locked in to Office. If so, it's time to look again; Novell has taken OpenOffice.org's source code and create a version of its own that supports Excel VBA.

Novell's Noel Power is the developer in charge of introducing Excel VBA interoperability into OpenOffice.org Calc. He says that the interoperability is achieved by:

    * allowing Excel VBA macros to run natively within OpenOffice.org;
    * providing a compatibility object model;
    * continuously improving the compatibility model by identifying and implementing the most useful and widely used APIs;
    * extending the symbols available to ooo-basic to include the compatibility API; and
    * modifying the core ooo-basic runtime to handle Excel VBA syntax.

[http://www.linux.com/article.pl?sid=06/11/08/1726205](http://www.linux.com/article.pl?sid=06/11/08/1726205)
:cool:

---

### Post by TheWizzard on 2006-11-18
cool! thanks for sharing this info.

---

### Post by H4rm0ny on 2006-11-18
Not necessarily cool at all. This code has been developed and entered by Novell employee Noel Power and Novell has just entered into a business partnership with Microsoft. There's a large and justifiable suspicion that this is a "poison pill" which will ultimately allow Microsoft to sue Open Office for patent infringement. It's certainly plausible that this functionality will allow it to do so. And it's without any doubt at all that Microsoft have a motivation to do so.

It needs to be thought about very carefully as to whether this should be included in the default Open Office builds.

-Harmony.

---

### Post by darkhatter on 2006-11-18
> **H4rm0ny said:**
> Not necessarily cool at all. This code has been developed and entered by Novell employee Noel Power and Novell has just entered into a business partnership with Microsoft. There's a large and justifiable suspicion that this is a "poison pill" which will ultimately allow Microsoft to sue Open Office for patent infringement. It's certainly plausible that this functionality will allow it to do so. And it's without any doubt at all that Microsoft have a motivation to do so.

It needs to be thought about very carefully as to whether this should be included in the default Open Office builds.

-Harmony.

please don't start that crap here. It is a good thing, thanks for the info

---

### Post by H4rm0ny on 2006-11-18
Why is it crap? Novell recently announced a partnership with Microsoft. Novell introduces VBA support into Open Office. Aside from whether VBA *should* be a standard for our marcos (I've used Open Office since the early days), it does sound like the sort of thing that Microsoft could use in a lawsuit. And I don't think anyone here thinks it would be too immoral for them.

I do _want_ it to be crap, but simply calling it such doesn't do anything to reassure me. Can you explain, please?

---

### Post by darkhatter on 2006-11-18
Novell said they we're going to work together with Microsoft to creat odt support for office, and doc for openoffice. Novell said that all changes they make are going to be GPL. If you combine the 2 I think its ok.

---

### Post by darkninja on 2006-11-18
It's not that I have a problem with Microsoft and Novell working together to improve interoperability and standards, I actually think that full VBA support will be incredibly useful.

However with both Novell and Microsoft spreading patent FUD together ("Microsoft can sue you if you're not running SuSE!") it's a little hard to be screaming praises for them.

---

### Post by pmj on 2006-11-18
While I think this is probably OK, something being GPL doesn't mean it's automatically safe to use. It could still infringe on patents, which is what this whole mess is about.

---

### Post by darkhatter on 2006-11-18
if it infringes on a patent then Red Hat will re-right it. They released a public statement, so I really don't care anymore.

---

### Post by Dr. C on 2006-11-19
> **pmj said:**
> While I think this is probably OK, something being GPL doesn't mean it's automatically safe to use. It could still infringe on patents, which is what this whole mess is about.

Yes but if it infringes on Microsoft patents, and it is distributed under the GPL by Novell, it will be very difficult for Microsoft to sue. How can Microsoft get around the defense that they acquiesced to Novell distributing software that infringes on their patents? 

This Microsoft Novell deal is starting to look like Microsoft jumped out of the GPL frying pan into the public domain fire.

---

### Post by Polygon on 2006-11-19
like my dad says, patents should be things that you can physically bring to the patent office, the patenting of ideas and code is really quite stupid.

if this addition is impossible for microsoft to bring up in a "linux uses intellectual property from us omgZ!!1elven" court case, then its great. But if this is indeed a "posion pill" from novell to support microsoft in their argument that linux stole things from microsoft, then that is quite bad.

---

### Post by AlphaMack on 2006-11-19
I'm surprised it hasn't been said here yet...

"IT'S A TRAP!!!111"

8)

---

### Post by H4rm0ny on 2006-11-19
> **darkhatter said:**
> if it infringes on a patent then Red Hat will re-right it. They released a public statement, so I really don't care anymore.

If it's a patent issue then they wont be able to do that. Copyright would be "You can't use this code, so you have to write it a different way." Patents are: "You can't have code that does this."

I'm concerned that they'll first establish Open Office as using VBA so it is popular, and then they'll bring litigation into it and you'll get a licensed version from Novell and a gimped version from everyone else. Home users might not care much, but businesses will go for the one called "Open Office Professional" or whatever other term they slap on it. And that will hurt the freedom and spirit of the Open Office project.

As to the inability to sue infringers of the patents, IANAL, but I suspect that it's possible to try. It is not Microsoft that has released the infringing code, but a separate company called Novell. The fact that Novell now has an agreement with Microsoft that they wont be sued for infringing on their patents, doesn't prevent Microsoft suing others. We here may be able to see what is morally wrong with Microsoft's behaviour, but it doesn't mean that a court will act accordingly. The fight alone will be damaging.

There's a side issue which is whether we want Open Office to support VBA? Obviously it fills a considerable need on the part of business which will make it far easier to migrate to Open Office in theory. However, the net result is to encourage VBA to be the default way of implementing macros in Open Office. After all, if you have the choice of your spreadsheet being compatible with both Excel and Calc, or Calc alone, isn't it more logical to make it compatible with both. But VBA is under Microsoft's control. No one else can expand it, modify it. And Microsoft products will always have the edge in implementation whilst Open Office will be the one with compatability problems and glitches. Basically, the interoperability in practice, could be one-sided enough that Open Office looks like a poor clone of MS Office. It isn't. In several ways it is more powerful, but when it plays on Mircosoft's turf, it looks bad. Novell may not see things this way, but then how many of Microsoft's previous partners are still around?

Reading this back, it comes across as anti-Microsoft paranoia, but everything here seems feasible to me and Microsoft is not run by idiots, but by highly intelligent people. And morality is certainly no restraint on the company's behaviour as we've seen countless times before. MS Office is critical to Microsoft's powerbase. Not merely because it's good and sells well, but because it's popularity helps them maintain a de facto file standard which is the biggest barrier to competitors establishing themselves. And perhaps more importantly, because if you need MS Office, you need MS Windows. If you're free of MS Office, then Linux becomes much more plausible for your company standard.

Open Office is a colossal threat to Microsoft. It can't be underestimated. And I think everything their new partners do and contribute has to be looked at a little more carefully. If any Novell engineer happens to be reading this, then I'm sorry but that now includes you and it certainly includes this VBA code in Open Office.

-Harmony.

---

### Post by lolocaust on 2006-11-19
Isn't GPLv3 meant to help stop patent issues within GPL'd code? As in, you're not allowed to distribute GPL'd code unless you lose all rights to a patent?

---

### Post by Sslaxx on 2006-11-19
Well, my view on this is that while it *might* have not been a "trojan horse" tactic against OO.o at first, it certainly has become one now...

---

### Post by darkghost on 2006-11-19
I posted this news yesterday :D :D :D (only joking)
[Here]("http://www.ubuntuforums.org/showthread.php?t=302280")

Dark :-P

---

