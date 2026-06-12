---
title: "Someone remind me, what XML for comments/subtitles above or below web text is called?"
date: 2007-01-13
forum: The Cafe
---

### Post by SoloSalsa on 2007-01-13
I looked quite a bit, through lists of XML derivatives, and how-to-web articles I've used before, but I just can't find it!  I once read about an XML standard for putting translations above words and sentences on the web.  It could also be used for when you need superscript and subscript at the same time.  I think it had some name like ruby or opal or some other gem, but I searched for a bunch and could not find it.  It's syntax looks like this:

|<xml ladeda>
|<ladeda entry>
|  <ladeda word>Hello.</ladeda word>
|  <ladeda above>Hallo.</ladeda above>
|  <ladeda word>Goodbye.</ladeda word>
|  <ladeda above>Auf wiedersehen.</ladeda above>
|  <ladeda below>(caption for the entire entry, not just word)</ladeda below>
|</ladeda entry>

And rendered, looks like this: (underscored to force spacing)

[SIZE=3][SIZE=2]__Hallo.____[/SIZE][/SIZE]Auf wiedersehen.
[SIZE=5]Hello.  Goodbye.[/SIZE]
[SIZE=1](caption for the entry, not just word)

[SIZE=2]So has anyone seen this before?[/SIZE]
[/SIZE]

---

### Post by SoloSalsa on 2007-01-13
Or, does anyone know of a big list of XML based languages?

---

### Post by SoloSalsa on 2007-01-14
I found it!  It is [Ruby]("http://www.w3.org/TR/ruby/").  I never found it in searches before because it sounds like the programming language, Ruby.

---

