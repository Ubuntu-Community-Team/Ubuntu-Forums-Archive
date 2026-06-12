---
title: "OpenBSD website hacked"
date: 2008-07-08
forum: The Cafe
---

### Post by Luke has no name on 2008-07-08
[http://tinyurl.com/57n7ny](http://tinyurl.com/57n7ny)

Pretty insane, isn't it? :)

---

### Post by Luffield on 2008-07-08
Yeah, pretty insane. The person who did it didn't choose the most subtle way to make their point, did they? :-\

---

### Post by jonabyte on 2008-07-08
```

http://www.openbsd.org/cgi-bin/cvsweb/src/?sortby=%22%3E%3Ch1%20style=%22position:absolute;top:10px;font-size:72pt%22%3E%3Cblink%3ENetBSD%20is%20more%20secure%3C/blink%3E%3C/h1%3E

```

That's not a hack, well at least not on the web server.

---

### Post by PmDematagoda on 2008-07-08
Remove the:-
```
?sortby=%22%3E%3Ch1%20style=%22position:absolute;top:10px;font-size:72pt%22%3E%3Cblink%3ENetBSD%20is%20more%20secure%3C/blink%3E%3C/h1%3E
```
after /src and it all becomes normal, I think that link was just specially made to fool people.

---

### Post by x0as on 2008-07-08
[http://www.microsoft.com/en/us/default.aspx?pf=true&navGroupName=Ubuntu%20is%20more%20secure](http://www.microsoft.com/en/us/default.aspx?pf=true&navGroupName=Ubuntu%20is%20more%20secure)

So did microsoft :lolflag:

---

### Post by keiichidono on 2008-07-08
I saw an obvious use of HTML in the URL to make it display on page, it's tom foolery. @Above post, i think you mean to link [here]("http://www.microsoft.com/en/us/default.aspx?pf=true&navGroupName=Ubuntu%20is%20a%20better%20operating%20system%20than%20Windows%20in%20every%20way").

---

### Post by eragon100 on 2008-07-08
Well it's certainly nice of them to admit it, but eh... I am a bit :confused:, anyway :lolflag:

---

### Post by Luke has no name on 2008-07-15
> **CalvinB said:**
> I saw an obvious use of HTML in the URL to make it display on page, it's tom foolery. @Above post, i think you mean to link [here]("http://www.microsoft.com/en/us/default.aspx?pf=true&navGroupName=Ubuntu%20is%20a%20better%20operating%20system%20than%20Windows%20in%20every%20way").

Looks like the hole was closed here.

---

### Post by fatality_uk on 2008-07-15
Hacked :lol:
That's not even a script baby, never mind a script kiddie!!!

> method="post" solves numpties messing about like that.

---

### Post by fluteflute on 2008-07-15
[QUOTE=fatality_uk]method="post" solves numpties messing about like that.[/QUOTE]

Oh course you can achieve a similar effect, but just not by a simple link. :)

---

### Post by Le-Froid on 2008-07-15
> **Luke has no name said:**
> Looks like the hole was closed here.

Nice bump :p

---

### Post by cardinals_fan on 2008-07-15
> **Luke has no name said:**
> Looks like the hole was closed here.
What hole?

---

### Post by aaaantoine on 2008-07-15
> **fatality_uk said:**
> Hacked :lol:
method=post solves numpties messing about like that.

Validating the query string would be more useful in this case.

This isn't exactly a useful hack, other than a proving that some dangerous things can potentially be done via querystring.

Now, if you used that URL to store text in a database, you'd have a real dangerous vulnerability.

---

### Post by _DD_ on 2008-07-15
Its simple XSS/injection/whatever.

Rule #1 of scripting... never trust any variable.

---

### Post by D-EJ915 on 2008-07-15
> **Luke has no name said:**
> Looks like the hole was closed here.
there never was a hole :P

---

