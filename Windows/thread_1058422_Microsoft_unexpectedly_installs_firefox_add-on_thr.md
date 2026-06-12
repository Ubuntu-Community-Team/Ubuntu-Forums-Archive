---
title: "Microsoft unexpectedly installs firefox add-on through Windows Update"
date: 2009-02-02
forum: Windows
---

### Post by Grant A. on 2009-02-02
[http://tech.slashdot.org/article.pl?sid=09/02/01/2143218]("http://tech.slashdot.org/article.pl?sid=09/02/01/2143218")

All I can say is this: I didn't buy an expensive-*** Windows license just so that Microsoft could do what they want with my computer.

BTW- I like Slashdot's view on this:

---

### Post by cardinals_fan on 2009-02-02
What the...?

---

### Post by Grant A. on 2009-02-02
> **cardinals_fan said:**
> What the...?

My thoughts exactly. Btw, wouldn't the add-on being uninstallable be against U.S. and E.U. Anti-Trust laws? I mean, afterall, isn't that what EA was sued for with SecuROM?

---

### Post by TBOL3 on 2009-02-02
What?

And no, I disagree. An add-on not being uninstallable isn't really against anti-trust laws.  It's just poor engineering on MS's part, by making an ad-onn an integral part of the system.

---

### Post by Firestem4 on 2009-02-02
this is complete and utter crap..Thanks for showing this. It turns out I had it installed on my system and my moms laptop. I am sure to remove it on my friends computers too.

---

### Post by Kopachris on 2009-02-02
> **TBOL3 said:**
> What?

And no, I disagree. An add-on not being uninstallable isn't really against anti-trust laws.  It's just poor engineering on MS's part, by making an ad-onn an integral part of the system.
I think that an add-on not being uninstallable is essentially forcing the consumer to do business with the company.  I'm not sure which way it would go in court; it could go either way.  Either way it's ruled (if someone sues) would be a very touchy subject.

BTW, it's two 'd's and one 'n'. ;) (You know, they need a grammar police emote...)

---

### Post by Gramps on 2009-02-02
This is just WRONG, FF does not belong to MS and they have no business adding anything to it without the owner's permission.

I could not tell you the last time that my 1 Win XP machine was updated, I DON'T do automatic updates on anything period! I will check it to make sure MS hasn't snuck one by one me.

Thanks for bringing this to our attention.

One more reason to use Linux

---

### Post by Skripka on 2009-02-02
What a nicely slimeballish thing to do.

---

### Post by -grubby on 2009-02-02
I'm not going to say the addon is necessarily bad, but installing stuff on MY computer without MY permission is not cool. And not allowing me to remove it without firing up regedit seems somewhat malicious.

---

### Post by SunnyRabbiera on 2009-02-02
what an underhanded tactic, Mozilla should do something

---

### Post by pirate_tux on 2009-02-03
> **SunnyRabbiera said:**
> what an underhanded tactic, Mozilla should do something

This only demonstrates I was right, when I said Windows is a Virus!

---

### Post by Polygon on 2009-02-06
how do i get rid of this? even if i disable it it still edits my user agent string to have (.NET CLR 3.5.30729) at the end.

EDIT: silly me, google is full of solutions

how to remove:

go to regedit (start > run > type in 'regedit'

go to &#8220;HKEY_LOCAL_MACHINE\SOFTWARE\Mozilla\Firefox\extensions&#8221;  (or &#8220;HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Mozilla\Firefox\extensions&#8221; if your running 64 bit)

you will see a key named &#8220;{20a82645-c095-46ed-80e3-08825760534b}&#8221;

right click > delete

then to get rid of the user string:

type in "about:config" into the url bar

click ill be carefull

search for 'useragent"

you will see "general.useragent.extra.microsoftdotnet"

right click and select "reset"

restart firefox.

---

### Post by Ripfox on 2009-02-06
This one is dedicated to all the people who stick up for them and ride peoples butts when they mention that MS is an underhanded company run by people who could give a crap less about your privacy.

Home run!

---

### Post by Polygon on 2009-02-06
to be fair, it could be something useful, but:

the fact that microsoft is using their near monopoly status to force their new clickonce technology on users is slimy buisness practices

there is no opt out for not installing the addon (this goes for other programs, such as skype, adobe, etc)

no easy way to remove it

and no prompt that this was going to even be installed. I always check the updates before i install them, i did NOT see a 'clickonce addon for firefox' anywhere in there.

so therefore i shall be removing this addon from my computer and all of the computers of my family. I will not be a part of microsoft's unfair forcing of technology down people's throats

---

### Post by Kopachris on 2009-02-06
> **Polygon said:**
> I will not be a part of microsoft's unfair forcing of technology down people's throats
Neither will I.  'Tis a good day to run Linux!

---

### Post by Izek on 2009-02-08
> HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Mozilla\F irefox\extensions
I don't see it in there, which means I probably have never done the update :o

---

