---
title: "Software for Roman Catholics?"
date: 2009-09-21
forum: Ubuntu Christian Edition
---

### Post by reprobus on 2009-09-21
I found a virtual rosary program at [www.virtualrosary.org](www.virtualrosary.org) which is a windows program but it works fine in WINE and also GnomeSword has several Catholic versions of the Bible. I was wondering if anyone knows of any other software that may be of use to Roman Catholics? Also, I have a .txt of the Roman Ritual and I was wondering if anyone could tell me how to convert it into a GnomeSword module? Any help or comments would be greatly appreciate. Thanks!

---

### Post by koenn on 2009-09-21
> **reprobus said:**
>  ...  any other software that may be of use to Roman Catholics?  ...

email : Thunderbird
web browsing : Firefox 
spreadsheet : OpenOffice
IM : Pidgin, ...
...

---

### Post by reprobus on 2009-09-21
> <snip>

Your not funny...

---

### Post by Elfy on 2009-09-21
Moved to the Ubuntu Christian Edition forum.

---

### Post by reprobus on 2009-09-21
> **forestpixie said:**
> Moved to the Ubuntu Christian Edition forum.

I don't see why this was moved. This post has nothing to do with Ubuntu Christian Edition.

---

### Post by Elfy on 2009-09-21
It's less likely to turn into a discussion about religion here, thus more likely to stay open.

---

### Post by LowSky on 2009-09-21
> **reprobus said:**
> I don't see why this was moved. This post has nothing to do with Ubuntu Christian Edition.

Catholics are a form of Christians... and maybe you should take a look at that OS

[http://ubuntuce.com/features.htm](http://ubuntuce.com/features.htm)

---

### Post by beta.tester on 2009-09-21
> **reprobus said:**
> I don't see why this was moved. This post has nothing to do with Ubuntu Christian Edition.

Hmm Hi

I am a Christian who happens to also be a practising Roman Catholic. Yes I am also a follower of Jesus and class myself a Christian (One who follows Christ - we were first named at Antioch as Christians :)

    Perhaps we need to tread very gentler when we state "facts" that maybe inaccurate :)


"A soft answer turns away anger".

---

### Post by reprobus on 2009-09-21
I don't need a completely new OS just because I am a Christian. Seems like a cool project though but xubuntu is fine for me. I was just looking for a few cool programs.

---

### Post by Viva on 2009-09-21
CE has a collection of cool Christian-related programs, hence you're redirected here.

---

### Post by LowSky on 2009-09-21
I'm not suggesting a new install, but the software that CE comes with can be easily added to any verison of Ubuntu. knowing that my link points to some of the stuff it has availible and from there you can get some idea and google for results.

for instance
Xiphos 
[http://xiphos.org/download/debian-ubuntu/](http://xiphos.org/download/debian-ubuntu/)

---

### Post by david_kt on 2009-09-21
> **reprobus said:**
> I found a virtual rosary program at [www.virtualrosary.org](www.virtualrosary.org) which is a windows program but it works fine in WINE and also GnomeSword has several Catholic versions of the Bible. I was wondering if anyone knows of any other software that may be of use to Roman Catholics? Also, I have a .txt of the Roman Ritual and I was wondering if anyone could tell me how to convert it into a GnomeSword module? Any help or comments would be greatly appreciate. Thanks!

You could try software at ubuntu ce:

[http://www.ubuntuce.com/convert.htm](http://www.ubuntuce.com/convert.htm)

After that, you could install virtual rosary by:

```
sudo apt-get install virtual-rosary

```

DK

---

### Post by david_kt on 2009-09-21
> **reprobus said:**
> I don't need a completely new OS just because I am a Christian. Seems like a cool project though but xubuntu is fine for me. I was just looking for a few cool programs.

You could do add ubuntu ce software packages to xubuntu, just follow steps in the link I post earlier.

DK

---

### Post by koenn on 2009-09-22
> **david_kt said:**
> You could try software at ubuntu ce:

[http://www.ubuntuce.com/convert.htm](http://www.ubuntuce.com/convert.htm)

I would advise AGAINST that. 

The instructions on the page you link to are apparently meant to **convert** a plain Ubuntu into Ubuntu CE, i.e the result will be quite similar to installing Ubuntu CE from scratch.

The OP clearly stated that this is not what he's looking for. 


Further more, last time I checked, "converting" to CE also included having your entire firefox preferences, bookmarks, etc wiped and other stuff along those lines. I don't know if that's still the case (last time I checked was actually  several releases ago), but maybe you can verify this, since you advised this approach. 


The correct approach would be to find out what packagas are included in CE (and the repo's that provide them) and then install the desired packages individually, eg with synaptic or something like
```
apt-get install name_of_package
```

---

### Post by jonathonblake on 2009-09-22
> **reprobus said:**
> This post has nothing to do with Ubuntu Christian Edition.

Once upon a time, _Virtual Rosary_  was included in Ubuntu Christian Edition.

I haven't checked Xiphos, but GnomeSword did _not_ provide  Catholic versions of the Bible. (For starters, it dropped the deuterocanonical material.)

The simplest way to obtain help on converting the Roman Ritual to _Sword Project_ format, is to ask on #Xiphos  IRC channel  ---  assuming that the lead developer doesn't drop in and write detailed instructions for you here.

I don't know what currently is being done, in terms of providing Catholic texts in _Sword Project_ format.  

The main sites for (English language)  Catholic orientated resources for e-Sword are:
[http://www.esnips.com/web/CatholicEsword](http://www.esnips.com/web/CatholicEsword)
[http://www.esnips.com/web/CatholicApolegetics](http://www.esnips.com/web/CatholicApolegetics)

For online Catholic Bible Study, _Biblia Clerus_ is probably the best currently available site: 
[http://www.clerus.org/bibliaclerusonline/en/index.htm](http://www.clerus.org/bibliaclerusonline/en/index.htm)

jonathon

---

### Post by david_kt on 2009-09-22
> **koenn said:**
> 
Further more, last time I checked, "converting" to CE also included having your entire firefox preferences, bookmarks, etc wiped and other stuff along those lines. I don't know if that's still the case (last time I checked was actually  several releases ago), but maybe you can verify this, since you advised this approach. 


The correct approach would be to find out what packagas are included in CE (and the repo's that provide them) and then install the desired packages individually, eg with synaptic or something like
```
apt-get install name_of_package
```

1. Firefox would be untouched with the convert.
2. You have the chance to see what are the packages it would install, if you do not like it you could answer no, but the repository is already there. Take note packages you want to install.
3. Only then you could select to install using sudo apt-get package

DK

---

### Post by meeples on 2009-09-22
i cant think of any software that would be of use to a roman catholic..or any one of any specific religion actually.

but what do i know.

---

### Post by david_kt on 2009-09-22
> **meeples said:**
> i cant think of any software that would be of use to a roman catholic..or any one of any specific religion actually.

but what do i know.

Bible software, bible trivia, linbread are specific for Christian (including Roman Catholic)
Virtual Rosary is specific for Roman Catholic
Al Quran software is specific for muslim.
You could search more software specific for religion

DK

---

### Post by jonathonblake on 2009-09-23
> **meeples said:**
>  any one of any specific religion actually.
but what do i know.

Muslims want programs that tell them when it is time to pray.
Muslims also want a program that tells them which direction Mecca is in.

Jews like programs that tell them when it is appropriate to light candles just before the Shabbath.

Thelemites find software that tells them when the sun and moon rise, site, are at the zenith, and at the nadir useful as a reminder for when to do Liber Resh.

All of the above also find software that guides their prayer for that specific time of day to be very useful. 

"Hard core pagans" find astronomical software (with slight modifications) useful, because it helps them schedule when their ritual _should_ begin, and end.

I've seen a program that functions as a virtual prayer wheel for Buddhists to spin, or have spin for them.

Many people find it easier to study their Holy Texts using as computer, than hard copy.

Many religiously-orientated people make a practice of keeping a spiritual journal. Something that contains an outline of every homily they have heard.  Every ritual/worship service they attended. Every insight they obtained as a result of their daily study of their sacred text.  Every prayer that they have ever said.  The outcome of those prayers.   etc.

Then there are the more mundane things. 
* Organizing audio collections for which service/ritual they are most appropriate for;
* Organizing video collections for which service/ritual they are most appropriate for;
* Keeping track of group membership data;
* Organizing one's (religious) library;
* Tools for learning the original language(s) of one's sacred texts;
* Tools that enable one to communicate in the original language(s) of one's sacred texts;

Finally, parents may want to prevent their children from accessing  "undesirable sites", or only allow access to "work safe" sites.

The other thing to remember, is that some users like themes for their software to reflect their religious beliefs. 


jonathon

---

