---
title: "Firefox62 super fast!"
date: 2018-09-07
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2018-09-07
Just updated FF to 62 I am really impressed by the speed up. I have 558 tabs on the small toshiba laptop (6G of ram). It used to take about 40 secs for FF to load so I have to use a different profile when I don't need to access the tabs to speed things up,  but now it loads in 3 secs! It is faster than Chrome and Opera (there are a lot fewer tabs on these two)

---

### Post by poorguy on 2018-09-07
I just did a clean install of*** Lubuntu 18.04.1*** and noticed ***Firefox62 ***was installed.

Seems to be working good and*** I ain't got no complaints*** but it's hard to say with ***Firefox***. 

It seems like for awhile every other ***Firefox update crapped out*** and then the next ***Firefox update work fine***.

All working good on my 10 year old Dell Optiplex 380.

I'm happy. :)

---

### Post by walts48 on 2018-09-08
I also got the update to Firefox 62 released by Mozilla on Sept. 5th  and it is great!

Now where is Thunderbird 60 which was released by Thunderbird on Aug. 6, 2018?

---

### Post by Ramom_Flores on 2018-09-10
> **poorguy said:**
> I just did a clean install of*** Lubuntu 18.04.1*** and noticed ***Firefox62 ***was installed.
Seems to be working good and*** I ain't got no complaints*** but it's hard to say with ***Firefox***. 


Well, I have a little complaint. I write in several languages, not too well, so I use spellcheckers often. That's why I have dictionaries (hunspell) for different languages installed on my computer (lubuntu 18.04). Before, Firefox recognized the dictionaries installed in the system, and used them for spellchecking out-of-the-box.

After updating firefox, to 62.0, the spellchecker shows one dictionary only.
I have been searching and it seems that this is because Mozilla [has stopped using]("https://bugzilla.mozilla.org/show_bug.cgi?id=1460600") the hunspell engine of the system.

As an alternative it is possible to utilize the dictionaries installed in the system using the spellchcker.dictionary_path variable, for example setting:

```
spellchecker.dictionary_path = /usr/share/hunspell
```

So in [COLOR=#008000]about:config[/COLOR] it is necessary to add this variable and to set it. 

Not too complicated, once you know how to do it, but less convenient than before.

---

