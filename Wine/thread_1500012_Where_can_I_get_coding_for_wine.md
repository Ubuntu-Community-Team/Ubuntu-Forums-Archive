---
title: "Where can I get coding for wine?"
date: 2010-06-02
forum: Wine
---

### Post by Zerocool Djx on 2010-06-02
I'm not sure how to do it, but I don't everything else,.. What comp languages to I need to learn to improve wine? And where do I get the coding?

I guess I'm looking for the 101 on program development...

I know for legality reasons people cannot release certain things,.. but if someone could be like if you take this, that, and the other thing, and put it together, wine would work flawlessly. I would certainly like to know how to do it for "my own benefits" (Sorry Bill, not a fan of you). I mean, What's the biggest thing? Making the Drivers work for individual computers? Databases are good for that...

---

### Post by cogadh on 2010-06-02
Wine development is not exactly a hobbyist endeavor. There are literally thousands of programmers worldwide working on individual aspects of Wine and have been for over 15 years now. I don't want to discourage you from contributing, but it is really not the kind of thing you can just pick up and easily modify to suit your needs. If you want to know more about Wine development, the best place to start is [Wine's own website]("http://www.winehq.org/").

BTW - drivers are not really a concern in Wine since it does not use drivers within Wine itself. Wine takes the "calls" normally made to Windows drivers through the API and translates them into instructions to be used by Linux's own drivers.

---

### Post by Zerocool Djx on 2010-06-02
That's fine,... I don't mind learning,.. I gotten several hardware experiments to work before. However this is vastly different... I'll take a look..

---

### Post by asdfoo on 2010-06-02
> **Zerocool Djx said:**
> That's fine,... I don't mind learning,.. I gotten several hardware experiments to work before. However this is vastly different... I'll take a look..

You need to have grasp of C programming, probably over a years experience is helpful.

If you want to start learning or need a reference, I can recommend this one personally  [http://publications.gbdirect.co.uk/c_book/](http://publications.gbdirect.co.uk/c_book/) or if you have a dead tree version of The C Programming Language by K&R that is just as good.

There are a lot of bad C books which should be avoided so it's best to stick to these recommendations.

In addition to understanding the basics of C, you need some experience with windows programming in C, for this you can follow the winprog tutorial [http://www.winprog.org/tutorial/](http://www.winprog.org/tutorial/)

In addition to the above, you should be familiar with using linux to edit files, compile and so on through the shell.

---

