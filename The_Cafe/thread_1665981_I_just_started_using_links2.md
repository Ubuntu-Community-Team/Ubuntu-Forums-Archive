---
title: "I just started using links2"
date: 2011-01-13
forum: The Cafe
---

### Post by jordanae on 2011-01-13
Or is it just links and links2 was just the package name? Anyway, I just started using links2 which is a command line web browser. I love using anything in the CLI, but I've gotta wonder: is there any point in using a CLI based web browser instead of Chromium or Firefox? Just for fun? Or maybe just in case the X Window System crashed (or is just not used)? Or is there something that is does better than a GUI based browser?

---

### Post by koleoptero on 2011-01-13
> **jordanae said:**
> Or is it just links and links2 was just the package name? Anyway, I just started using links2 which is a command line web browser. I love using anything in the CLI, but I've gotta wonder: is there any point in using a CLI based web browser instead of Chromium or Firefox? Just for fun? Or maybe just in case the X Window System crashed (or is just not used)? Or is there something that is does better than a GUI based browser?

Less bandwidth usage in case you need it?
More focus on the text content of the site?

But it's certainly not suitable for everyday usage imho.

---

### Post by Nytram on 2011-01-13
I find the CLI browsers to be faster than GUI ones. Also I'd guess they are less vulnerable to web-based exploits/hacks, as they don't use scripts/flash/plugins etc. I still prefer a GUI browser tho.

---

### Post by nothingspecial on 2011-01-13
Have you tried links2 -g

Then you get to see the pictures

[ATTACH]180928[/ATTACH]

I tend to use elinks though, because of the custom searches and link numbering. If I`m browsing a forum, searching for info, even looking up a recipe I`ll use a text browser......

.....youtube on the otherhand......

Text browsers are like firefox with flashblock + addblock x 1000

---

### Post by Spice Weasel on 2011-01-13
Also check out [Dillo]("http://www.dillo.org/") if you are interested in this sort of thing. I think it aims to have the same rendering capabilities as Firefox or Chromium but with little or no scripting and to be a really lightweight program. I'd say it's getting pretty damn close, they just need to implement Float (CSS).

[IMG]http://i52.tinypic.com/315mvcj.png[/IMG]

(I'm using an older version here, but still 2.*)

So basically:

Lightweight
Great rendering capabilities
No scripting, flash, or java (though you can post on forums, and download flash video from Youtube). No distractions.
Simple interface. (you can't see the tab support in the screenshot).
It also has a neat little button in the corner that checks for HTML errors, great for developers.

**Don't install the version in the Ubuntu repository.** AFAIK it's a terrible old glitchy version. You can find debs and rpms on the interwebz.

---

### Post by aeiah on 2011-01-13
only thing i really use it for is a .bashrc function that checks [http://www.downforeveryoneorjustme.com](http://www.downforeveryoneorjustme.com)

```

#usage eg: down google.com

function down () {
links -dump downforeveryoneorjustme.com/$@ | head -n 1
}

```

---

### Post by RiceMonster on 2011-01-13
If you are a masochist who doesn't like being able to view most web pages, CLI browsers are for you.

---

### Post by Johnsie on 2011-01-13
I use wget soemtimes... Especially if I just want to download a file and then parse it.

---

### Post by koleoptero on 2011-01-13
> **nothingspecial said:**
> Have you tried links2 -g

Then you get to see the pictures

That spoils all the fun!

Also if it doesn't show the tooltip message then it's unsuitable for xkcd.

---

### Post by nothingspecial on 2011-01-13
> **koleoptero said:**
> That spoils all the fun!

The fun is seeing images in the console

> **koleoptero said:**
> Also if it doesn't show the tooltip message then it's unsuitable for xkcd.

You have a point. Slightly more suitable than links2 without the -g though.

---

### Post by Spice Weasel on 2011-01-13
elinks > links without -g. Always.

---

### Post by nothingspecial on 2011-01-13
> **Spice Weasel said:**
> elinks > links without -g. Always.

Absolutely. :D

---

### Post by genjix on 2011-01-13
try Midori (gtk) or Arora (Qt)

---

### Post by Spice Weasel on 2011-01-13
> **genjix said:**
> try Midori (gtk) or Arora (Qt)

lol wat

---

### Post by nothingspecial on 2011-01-13
> **Spice Weasel said:**
> lol wat

Maybe you can use them in the framebuffer :rolleyes:

@ the op

Try elinks

Press . (full stop/period) Every link will now have a number next to it. To select that link, just  type the number and press enter. You will follow that link.

Press G, a search box will appear. You can type a url in it, but that`s rubbish.

Instead type 

```
g ubuntu
```

That will search google for ubuntu.

or try

```
wiki linux
```

That will search wikipedia for linux

Type ```
sd kubuntu
```

That will search slashdot for kubuntu

or

```
sf wubi 
```

that will search sourceforge for wubi

Full list here

[http://playingwithsid.blogspot.com/2008/01/smart-url-s-in-elinks.html](http://playingwithsid.blogspot.com/2008/01/smart-url-s-in-elinks.html)

elinks is amazing

---

### Post by ilovelinux33467 on 2011-01-13
> **Spice Weasel said:**
> elinks > links without -g. Always.

Most definitely :D

---

