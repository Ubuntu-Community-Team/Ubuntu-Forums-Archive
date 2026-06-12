---
title: "Firefox 3.2a1pre acid 3 score 100"
date: 2009-02-03
forum: The Cafe
---

### Post by vikrant82 on 2009-02-03
Well, opera 10 alpha achieved a perfect ACID 3 score of 100 in December. I wondered when firefox would join the fun.

Today I got a new firefox alpha build (Gecko/20090129 Minefield/3.2a1pre) on windows which scores 100 too. Waiting for updates to Shiretoko on my Jaunty too.

---

### Post by ghindo on 2009-02-03
That's the reference rendering. :|

---

### Post by vikrant82 on 2009-02-03
:p , LOL! Ya Damnn, its still 92! :|

---

### Post by imlinux on 2009-02-03
> Today I got a new firefox alpha build (Gecko/20090129 Minefield/3.2a1pre) on windows which scores 100 too. Waiting for updates to Shiretoko on my Jaunty too.
can you please provide the link from where you downloaded firefox 3.2

---

### Post by PmDematagoda on 2009-02-03
> **imlinux said:**
> can you please provide the link from where you downloaded firefox 3.2

You don't download it, you need to build it from source obtained from the Mozilla mercurial servers.

---

### Post by zika on 2009-02-03
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/)

---

### Post by PmDematagoda on 2009-02-03
> **zika said:**
> [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/)

Or you can get it from that, I didn't see that before:). Nice timing as well;).

---

### Post by Sealbhach on 2009-02-03
Any idea when the mext release of Firefox will be? 

I've been using 3.2a1pre and it's smokin hot but I would like to get some more add-ons available. 


.

---

### Post by zika on 2009-02-03
> **Sealbhach said:**
> Any idea when the mext release of Firefox will be? I've been using 3.2a1pre and it's smokin hot but I would like to get some more add-ons available.

next release will be 3.1 (Shiretoko branch) this is an ongoing branch that will produce Minefield (3.2) branch and go on ... ;) it is great. I try Shiretoko once in a week but always return to Minefield next day ... ;)
just to be OK with the thread, last-night's 3.2a1pre gets 92/100 in metacity, 93/100 in compiz.

---

### Post by imlinux on 2009-02-03
> I've been using 3.2a1pre and it's smokin hot but I would like to get some more add-ons available. you can use nightly tester tool to over ride compatibility --->[https://addons.mozilla.org/en-US/firefox/addon/6543]("https://addons.mozilla.org/en-US/firefox/addon/6543")

---

### Post by Tomatz on 2009-02-03
> **Sealbhach said:**
> Any idea when the mext release of Firefox will be? 

I've been using 3.2a1pre and it's smokin hot but I would like to get some more add-ons available. 


.

You can hack most extensions by downloading the extension and opening the .xpi in file roller. Then just change the **"max version"** number in **install.rdf** (with gedit) to match or be higher than the version (of ff) you are using.

E.g

```
 <em:targetApplication>
      <!-- Firefox -->
      <RDF:Description em:id="{ec8030f7-c20a-464f-9b0e-13a3a9e97384}"
                       em:minVersion="2.0"
                       em:maxVersion=[COLOR="Red"]**"3.1b2pre"**[/COLOR] />
    </em:targetApplication>
  </RDF:Description>
</RDF:RDF>
```

;)

---

### Post by Sealbhach on 2009-02-03
Brilliant! Thanks guys! 


.

---

### Post by Colonel Kilkenny on 2009-02-03
> **vikrant82 said:**
> Well, opera 10 alpha achieved a perfect ACID 3 score of 100 in December.

Opera actually achieved 100/100 on March 2008. But that doesn't necessarily mean that the result is perfect, it has be smooth as well.

---

### Post by andrewabc on 2009-02-03
It seems acid has become some sort of standards test. I'm not exactly sure why, as I havn't noticed it being used on any websites. Why is it some important standards test for web browsers to compete against? What makes it so important? Aren't there other web standards more important than the always cited acid test?

Can someone point me to a website that uses acid3?

Maybe I'm ignorant, but I havn't gone to any websites and said "damn this website uses acid and my browser is not fully acid compatible."

---

### Post by crimesaucer on 2009-02-03
I get a 93% with FF 3.1b2 PGO.

Midior-git with libwebkit-git (Arch AUR packages) gives 100% pass.

---

