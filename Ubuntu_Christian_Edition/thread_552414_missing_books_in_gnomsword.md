---
title: "missing books in gnomsword"
date: 2007-09-16
forum: Ubuntu Christian Edition
---

### Post by Hendrixski on 2007-09-16
I have the World English Bible (WEB) installed in GnomeSword, but it seems to be missing a few books: Machabees, Ecclesiasticus, Wisdom, Baruch, and  parts of Daniel and Esther are missing.

Those are books that are usually excluded from most Protestant Bibles, though all the Orthodox faiths as well as the Catholics still have them in their Bibles.

On the WEB website they claim to have these deuterocanonical texts included, however they do not appear in GnomeSword.  Is there a way to modify GnomeSword for the Greek Orthodox, Coptic, or Catholic readers?

Thank you :-)

---

### Post by tak1150 on 2007-09-16
I have no doubt in my mind that those books do not belong in the cannon. But I know that e-Sword has KJV and a couple of other translations that come with deuterocanonical books.
e-Sword is also included in Ubuntu CE. You might give that a try.

Tak

---

### Post by simosx on 2007-09-16
I would put higher priority for Greek in Greek Polytonic (Ancient Greek). The current Greek Bible available in sword ommits all accents.

Is there a Coptic Bible for Unicode?

---

### Post by jonathonblake on 2007-09-17
[QUOTE=Hendrixski]I have the World English Bible (WEB) installed in GnomeSword, but it seems to be missing a few books: Machabees, Ecclesiasticus, Wisdom, Baruch, and  parts of Daniel and Esther are missing.[/quote]


AFAIK,GnomeSowrd does not support deuterocanonical material, yet.

> Is there a way to modify GnomeSword for the Greek Orthodox, Coptic, or Catholic readers?

I *think* that that is still on their "to do list".   There are a couple of major issues that have to be fixed, before that can be done.

xan

jonathon

---

### Post by jonathonblake on 2007-09-17
[QUOTE=simosx]I would put higher priority for Greek in Greek Polytonic (Ancient Greek).[/quote]

I'm not sure what happened to the Greek Polytonic Bibles.   I've got a couple of topical files in Polytonic Greek.

> Is there a Coptic Bible for Unicode?

I've seen either a PDF or HTML of _The Coptic Canon of Eighty One_.  I don't know how complete it was. I didn't check to see if it used Unicode.  It was either a link from a site, or link within one of the Coptic lists on Yahoogroups.

I've been using the Live CD for the last month, so I can't bookmark things when I find them. :(     

xan

jonathon

---

### Post by Hendrixski on 2007-09-17
> **tak1150 said:**
> 
I know that e-Sword has KJV and a couple of other translations that come with deuterocanonical books.
e-Sword is also included in Ubuntu CE. You might give that a try.

Nice.  I'll give that a try.

> **jonathonblake said:**
> AFAIK,GnomeSowrd does not support deuterocanonical material, yet.
I *think* that that is still on their "to do list".   There are a couple of major issues that have to be fixed, before that can be done.


ah,  Ok.  I ran across a SWORD forum from 2004 that said a fix was on the way, but then there was no followup so I didn't know what to think.
I'll check out e-sword first, let's see if that has it.  :-)


> **tak1150 said:**
>  those books do not belong in the cannon. 


well... They're old testament books written about 100 BC, right when Israel was being restored as a kingdom, and they talk about (among other things) how the messiah was going to be coming soon (and what do you know, he did).  They're not in the tanakh because the Jews don't see those prophesies as having been fulfilled... we do.

They were in all the Bibles of early Christians and still are in the Bibles of the Orthodox (including Coptic, Greek, Russian, Antiochian and Assyrian) and Catholic churches.  We just had a reading from the Book of Wisdom in my church this Sunday.

---

### Post by Hendrixski on 2007-09-17
:-) it looks as though e-sword has what I'm looking for... except the bible text doesn't show up.  photo attached.
I installed a bible from the module manager, but nothing shows up when I select any bible passages.  Is there something else I need to do to make this work?

---

### Post by jonathonblake on 2007-09-17
> **Hendrixski]:-) it looks as though e-sword has what I'm looking for... except the bible text doesn't show up. [/quote]

a) e-Sword has partial support for:
* The Song of the Three Young Men said:**
> I installed a bible from the module manager, but nothing shows up when I select any bible passages. 

That is a glitch caused by some versions of wine.
Highlight the page and see what happens.

xan

jonathon

---

### Post by tak1150 on 2007-09-17
Hi Hendrixski,

What version of wine do you have?
Type
```
wine --version
```
in your terminal.

---

### Post by simosx on 2007-09-18
> **jonathonblake said:**
> I'm not sure what happened to the Greek Polytonic Bibles.   I've got a couple of topical files in Polytonic Greek.


An ODT version (Unicode) is available at
[http://planet.ellak.gr/misc/%CE%91%CE%B3%CE%AF%CE%B1%20%CE%93%CF%81%CE%B1%CF%86%CE%AE.odt](http://planet.ellak.gr/misc/%CE%91%CE%B3%CE%AF%CE%B1%20%CE%93%CF%81%CE%B1%CF%86%CE%AE.odt)
I am not aware of individual files suitable for sword.

> **jonathonblake said:**
> 
I've seen either a PDF or HTML of _The Coptic Canon of Eighty One_.  I don't know how complete it was. I didn't check to see if it used Unicode.  It was either a link from a site, or link within one of the Coptic lists on Yahoogroups.


There is a group at [http://kame.danacbe.com/](http://kame.danacbe.com/)

---

### Post by Hendrixski on 2007-09-19
> **tak1150 said:**
> Hi Hendrixski,

What version of wine do you have?
Type
```
wine --version
```
in your terminal.

wine-0.9.33

I tried the selecting with my mouse as well, but there isn't even a while space on which to select... it's just gray, as shown in the picture above.  Did I perhaps install packages in the wrong order?

Also, the post above about the deuterocanonical texts of the anglican, coptic, etc. that was pretty informational.  Thanks :-)

---

### Post by tak1150 on 2007-09-19
> I tried the selecting with my mouse as well, but there isn't even a while space on which to select... it's just gray, as shown in the picture above. Did I perhaps install packages in the wrong order?

You didn't install things in the wrong order from what I can tell.
Your wine is just old (I have 0.9.45 now and it's great!). If you have Internet access, do:
```
sudo apt-get update
sudo apt-get upgrade

```

But if you don't have internet, let me know; there are other ways. Thanks.

---

### Post by refdoc on 2007-09-19
The problem with deuterocanonical/apocryph books etc is that the sword engine ( the underlying library libsword) is currently not set up to accept differnent versification schemes.

There is talk on the mailing list about changing this - i.e. take out the hardcoded versification scheme and introduce a modular system where new/divergent versifications can be specified in a module configuration.  This would allow for all sorts of new variations.

Wrt polytonal greek - while I have no clue what this is supposed to mean, I think on ftp.kleinpaste.org/pub/sword are a number of  interesting and new modules including Greek ones which have not yet made their way into the main repositories.

It is also useful to look at the beta repository of Crosswire.

---

### Post by JFonseka88 on 2008-03-27
> **tak1150 said:**
> I have no doubt in my mind that those books do not belong in the cannon. But I know that e-Sword has KJV and a couple of other translations that come with deuterocanonical books.
e-Sword is also included in Ubuntu CE. You might give that a try.

Tak

Your opinion on whether the books should be in the Bible or not is irrelevant here.

---

### Post by JFonseka88 on 2008-03-27
Bah this is ridiculous. The DRC which is a Catholic Bible doesn't have the deuterocanonicals? Ridiculous, someone has removed them on purpose

---

### Post by tayroni on 2008-12-04
According to this post, sword accepts other versification schemes:

[http://www.internettablettalk.com/forums/showthread.php?p=237967](http://www.internettablettalk.com/forums/showthread.php?p=237967)

The problem is *either* the gnomesword *or* the version of bibles.

If is the version of DRC has not the deuterocanonical books is a very complicated situation.

---

### Post by jonathonblake on 2008-12-05
> **tayroni said:**
> According to this post, sword accepts other versification schemes:


I did not see anything in that post, or thread, that implied that *The Sword Project* could now handle the Catholic Deuterocanonical material.

> 
The problem is *either* the gnomesword *or* the version of bibles.


I'd say you are back to dealing with the issue of when *The Sword Project* will support either add Catholic deuterocanonical material to the v11n scheme that it now uses, or allow for variable v11n schemes.

jonathon

---

### Post by ransom1982 on 2009-02-11
I am a developer of GnomeSword (now known as Xiphos). It **does not** have support for non-KJV versifications at this time. Some of the Bibles mentioned, including the DRC, actually do have that content embedded in the module, but the libsword engine does not yet provide us a way to access that. Having said that, support for non-KJV versifications is the current focus of the development work in libsword, and we are adding support to Xiphos as those options become available. Please do not read the lack of current support as a slam to non-Protestants. It is a technical issue, **not** a theological one.

Matthew Talbert
[http://xiphos.org](http://xiphos.org)

---

### Post by blendenzo on 2009-02-19
> **ransom1982 said:**
> It **does not** have support for non-KJV versifications at this time.Aren't the deuterocanonical books part of the original KJV versification, though?  I have a copy of *The Apocrypha: KJV* from World (ISBN: 0-529-10183-1), and it includes this quote in the jacket sleeve:> ...the translators of the 1611 King James Version translated the Apocrypha right along with the canonical books...Additionally, [replica 1611 KJV Bibles]("http://www.christianbook.com/Christian/Books/product?item_no=631609&netp_id=316580&event=ESRCN&item_code=WW&view=covers#curr") also contain the deuterocanonical material.

While I completely believe you that this is not a theological statement, it seems inaccurate to me to prefer the altered American Protestant KJV versification over the original, and then to call the original KJV versification "non-KJV."

---

### Post by jonathonblake on 2009-02-19
> **blendenzo said:**
> Aren't the deuterocanonical books part of the original KJV versification, though? 

Yes, and no.


The term "Dueterocanonical Books" refers to the following:
[LIST]
[*]Judith
[*]Wisdom
[*]Baruch
[*]1 Maccabees
[*]2 Maccabees
[*]Greek Esther
[*]GreekDaniel
[*]Sirach
[/LIST]


The 1611 KJV included those books, as well as:
[List]
[*]1 Esdras
[*]2 Esdras
[*]Prayer of Manasseh
[*]Epistle of Jeremiah
[/List]

The *Anagignoskomena* includes the following:

[List]
[*]Judith
[*]Wisdom
[*]Baruch
[*]1 Maccabees
[*]2 Maccabees
[*]Greek Esther
[*]GreekDaniel (Prayer of Azariah, Song of the Three Young Men, The Story of Susanna, Bel and the Dragon.)
[*]Sirach
[*]1 Esdras
[*]2 Esdras
[*]Prayer of Manasseh
[*]Epistle of Jeremiah
[*]Psalm 151
[*]3 Maccabees
[*]4 Maccabees --- this is listed as Apocryphal
[/list]

Ideally, The Sword Project would support the Anagignoskomena.

> it seems inaccurate to me to prefer the altered American Protestant KJV versification over the original, and then to call the original KJV versification "non-KJV."

What term would you suggest be used?

jonathon

---

### Post by tayroni on 2009-02-27
> **tak1150 said:**
> I have no doubt in my mind that those books do not belong in the cannon. But I know that e-Sword has KJV and a couple of other translations that come with deuterocanonical books.
e-Sword is also included in Ubuntu CE. You might give that a try.

Tak


Your OPINION on these books belong or not to the biblical cannon is totally irrelevant here.

Only as a mention, the Gutemberg Bible, which IS a version of Vulgata Latina had the deuterocanons, and the Gutemberg bible was released ~50 years before the Protestant Revolution.

So, your OPINION can be perfectly contested.

---

### Post by tayroni on 2009-02-27
> **jonathonblake said:**
> I did not see anything in that post, or thread, that implied that *The Sword Project* could now handle the Catholic Deuterocanonical material.

jonathon

I read again the post and seen that Sword supports versification themes with only 31102 verses with corresponds to protestant bibles, that is the secret! This cannot be altered on the verification files, only on sword source code. There's a request feature on Sword to support other versification schemes.

---

