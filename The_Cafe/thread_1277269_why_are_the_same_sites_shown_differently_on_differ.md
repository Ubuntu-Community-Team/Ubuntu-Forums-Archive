---
title: "why are the same sites shown differently on different browsers?"
date: 2009-09-28
forum: The Cafe
---

### Post by chriskin on 2009-09-28
i created a blog yesterday that shows perfectly on chrome chromium and firefox but internet explorer seems to hate it (or the blog hates internet explorer?)

i know that you might want to say "that's another reason not to use internet explorer" but many do, so if i plan in the future to actually use the blog, i will have to have it show correctly there too

can you tell me why this happens and whether i am able to change it?

---

### Post by bruno9779 on 2009-09-28
Is the page written in HTML5? IE doesn't support that.
M$ is still refusing to comply with that.

Anyway, browsers are applications that display what is in a web page. How they do it, with what resources and on what OS can influence the outcome.

---

### Post by ErikEhlert on 2009-09-28
I know some sites will not "support" certain browsers due to the way they work, or they will simply only work with specified browsers. Other sites can detect what browser you are using and will totally re-arrange how it looks just to tell you you should "upgrade to a more recent browser"

a prime example would be going to Yahoo on Konqueror.

---

### Post by chriskin on 2009-09-28
> **bruno9779 said:**
> Is the page written in HTML5? IE doesn't support that.
M$ is still refusing to comply with that.

Anyway, browsers are applications that display what is in a web page. How they do it, with what resources and on what OS can influence the outcome.

it is html but i seriously doubt it's html5, it's a simple blogger theme :P anyway, it's too nice to change it back :)

are there any other browsers not good enough for html5 by the way?

---

### Post by Viva on 2009-09-28
IE is notorious for poor standards support, especially with the style sheets and tables. Your sites will more or less look the same in other browsers except in some rare occassions as long as your code is standards complaint.

---

### Post by ErikEhlert on 2009-09-28
I believe it is possible to edit your blog to simply include, in fact, may even make it your main sub-title "DON'T USE IE IN MY BL... IN FACT, DONT USE IE" in large bold letters on the header :P

---

### Post by chriskin on 2009-09-28
> **ErikEhlert said:**
> I believe it is possible to edit your blog to simply include, in fact, may even make it your main sub-title "DON'T USE IE IN MY BL... IN FACT, DONT USE IE" in large bold letters on the header :P

hehe i was thinking of putting a small image on the top saying that internet explorer won't work as it should

---

### Post by v8YKxgHe on 2009-09-28
Majority of the time, the issues are directly down to the author of the HTML+CSS, but due to peoples ignorance they just decide to blame MSIE. I've had sites not work in Konqueror before, but do in every other browser, yet you don't see people claiming that Konqeuror with KHTML is crap.

Anyone can write HTML + CSS, but not everyone can write it correctly. I'm not talking about having it validate, as that means very little. You can write perfectly validated code, and it can still be semantically wrong and doing your CSS the wrong way, which will be the cause of your issues (yes, in *your* code)

> Is the page written in HTML5? IE doesn't support that.
M$ is still refusing to comply with that.
You are aware that HTML5 is still in draft stages? Be thankful that some browsers support what HTML5 they do, since supporting something that can be ever changing will not be easy.

---

### Post by -grubby on 2009-09-28
> **bruno9779 said:**
> Is the page written in HTML5? IE doesn't support that.
M$ is still refusing to comply with that.


You can't blame "M$" for not supporting an incomplete specification.

Actually, hey look, IE 8 supports some parts of it: [http://www.sdtimes.com/content/article.aspx?ArticleID=31806](http://www.sdtimes.com/content/article.aspx?ArticleID=31806)

Truthfully speaking, IE 8 has come a long way as far as web standards go, and it's not that hard to get your site working in IE 8 these days. I can't wait for IE 9.

EDIT: On another note, are you talking about IE 6? Because if you are, how are you to blame an 8 year old web browser for displaying your modern web page incorrectly?

---

### Post by GeneralZod on 2009-09-28
> **AlexC_ said:**
> I've had sites not work in Konqueror before, but do in every other browser, yet you don't see people claiming that Konqeuror with KHTML is crap.


Plenty of people claim precisely this.

---

### Post by bruno9779 on 2009-09-28
> **-grubby said:**
> You can't blame "M$" for not supporting an incomplete specification.


:lolflag:

you are always ready to stand up for Redmond's queen.

Nothing wrong, just surprising, given your 1000 something posts on Ubuntu forum

---

### Post by Skripka on 2009-09-28
> **AlexC_ said:**
> Majority of the time, the issues are directly down to the author of the HTML+CSS, but due to peoples ignorance they just decide to blame MSIE. I've had sites not work in Konqueror before, but do in every other browser, yet you don't see people claiming that Konqeuror with KHTML is crap.

I do.  The sooner the KDE/Konqueror devs read the writing on the wall, that KHTML is done, and go over to the Webkit backend-the better.  Konqueror runs great on Webkit,  Konqueror's biggest flaw is KHTML.

---

### Post by RiceMonster on 2009-09-28
> **Skripka said:**
> I do.  The sooner the KDE/Konqueror devs read the writing on the wall, that KHTML is done, and go over to the Webkit backend-the better.  Konqueror runs great on Webkit,  Konqueror's biggest flaw is KHTML.

I like Konqueror but it's KHTML that keeps me from fully adopting it. How do you get Konqueror to use Webkit?

---

### Post by Bachstelze on 2009-09-28
> **bruno9779 said:**
> :lolflag:

you are always ready to stand up for Redmond's queen.

Nothing wrong, just surprising, given your 1000 something posts on Ubuntu forum

What does that have to do with anything? HTML5 *is* incomplete, that's a fact. Saying otherwise would be lying, regardless of one's postcount.

---

### Post by Skripka on 2009-09-28
> **RiceMonster said:**
> I like Konqueror but it's KHTML that keeps me from fully adopting it. Do you know if Konqueror's going to be switching to Webkit full time? Also, what did you do to use Konqueror with Webkit?


Teeeheeee.  I used voodoo :)

I've heard of plans to officially move Konqueror over to Webkit, but they keep getting pushed back.

1) To get Konqueror on Webkit (in Arch) you need to go o'er to AUR and get [THIS]("http://aur.archlinux.org/packages.php?ID=25929")

2)  After installing it, you simply need to tell  Konqueror to default to it by doing

```

keditfiletype text/html

```

And in the dialogue that appears, move "Webkit (Kpart)" to the top of the list in the embedding tab.


The other option for basically doing the same thing is a lightweight Webkit browser in heavy development called [Rekonq]("http://aur.archlinux.org/packages.php?ID=22846") (There is also a non-git build available, that is FAR more stable, but out of date quite a ways) .  It is designed to integrate with KDE-unlike Arora (another lightweight QtWebkit browser), KDE is a full depend for Rekonq, and uses Konqueror's settings/bookmarks etc.  I like it over Konqueror because it has a much more elegant interface.  Be warned Rekonq MAY eat you cat, call the Nazgul down upon you, or set fire to your house.

---

### Post by bruno9779 on 2009-09-28
> **Bachstelze said:**
> What does that have to do with anything? HTML5 *is* incomplete, that's a fact. Saying otherwise would be lying, regardless of one's postcount.

It is a bit out of topic, but i was referring to more than just this post.

-grubby's posts have surprised me several times in the past for being quite strongly pro M$.

Maybe I should have PM him, but since i found it funny and harmless, I thought I'd share with the community.

I hope no harm is done, and if anyone feels offended by my posts, please take it easy and with a little humor.

---

### Post by RiceMonster on 2009-09-28
> **Skripka said:**
> Teeeheeee.  I used voodoo :)

I've heard of plans to officially move Konqueror over to Webkit, but they keep getting pushed back.

1) To get Konqueror on Webkit (in Arch) you need to go o'er to AUR and get [THIS]("http://aur.archlinux.org/packages.php?ID=25929")

2)  After installing it, you simply need to tell  Konqueror to default to it by doing

```

keditfiletype text/html

```

And in the dialogue that appears, move "Webkit (Kpart)" to the top of the list in the embedding tab.


The other option for basically doing the same thing is a lightweight Webkit browser in heavy development called [Rekonq]("http://aur.archlinux.org/packages.php?ID=22846") (There is also a non-git build available, that is FAR more stable, but out of date quite a ways) .  It is designed to integrate with KDE-unlike Arora (another lightweight QtWebkit browser), KDE is a full depend for Rekonq, and uses Konqueror's settings/bookmarks etc.  I like it over Konqueror because it has a much more elegant interface.  Be warned Rekonq MAY eat you cat, call the Nazgul down upon you, or set fire to your house.


Thanks. I'll try both of those out when I get home tonight.

---

### Post by Bachstelze on 2009-09-28
> **bruno9779 said:**
> 
-grubby's posts have surprised me several times in the past for being quite strongly pro M$.

I would rather say "not anti-MS", which is not the same as "pro-MS".

---

### Post by RiceMonster on 2009-09-28
> **Bachstelze said:**
> I would rather say "not anti-MS", which is not the same as "pro-MS".

According to a lot of people on here it is.

---

### Post by Paqman on 2009-09-28
IE is the spawn of satan when it comes to rendering pages properly. Just ask anybody who works in web design. Total pain in the butt.

---

### Post by Bachstelze on 2009-09-28
> **RiceMonster said:**
> According to a lot of people on here it is.

Then may I suggest those people are wrong?

---

### Post by Groucho Marxist on 2009-09-28
> **chriskin said:**
> i created a blog yesterday that shows perfectly on chrome chromium and firefox but internet explorer seems to hate it (or the blog hates internet explorer?)

i know that you might want to say "that's another reason not to use internet explorer" but many do, so if i plan in the future to actually use the blog, i will have to have it show correctly there too

can you tell me why this happens and whether i am able to change it?

It has to do with coding and the philosophies of the companies creating said code/sites. Microsoft prefers to code one way, Mozilla another, and Google prefers their own style (to name but a few browsers available). Being cross-browser compatible is tricky, as some codes that will work in, say, Firefox, will not display 100% correctly in an IE based browser. I would recommend adding a message graphic or text near your banner or at the top of the page which states that the blog "...is best viewed in Firefox v3.0." That way, IE users will not be completely confused when certain page attributes or functions do not display as they would in Firefox.

---

### Post by wojox on 2009-09-28
Simple answer: The way margins and padding are rendered.

---

### Post by RiceMonster on 2009-09-28
> **Bachstelze said:**
> Then may I suggest those people are wrong?

Yes, because they are.

---

### Post by carnagex420x on 2009-09-28
Browsers are build differently, and provide different support. The best you can do is use [http://validator.w3.org/](http://validator.w3.org/) to make sure you coding is valid. Also, as I said some can support other options that others dont to provide additional functionality. It is good to start with valid code and add additional tags or options on a per browser basis if it doesnt display the way you want it. One example of this is the fav icon, if IE sees a fav icon tag that isn't a "type="image/vnd.microsoft.icon"" it doesnt like it, but firefox is fine with it. Additionally some browsers provide internal workarounds that if it reads bad code it tries to fix it with, what it knos as good code. All you can do is test it with several browsers and make sure it works everywhere, its all in the code man!

---

### Post by bruno9779 on 2009-09-28
> **RiceMonster said:**
> Yes, because they are.

We thank thou, God Almighty for having bestowed your Divine judgement upon us!!

In this post people spoke about freedom several times, while the freedom of opinion is being stomped upon.

While bashing is an uncivilized action, as long as a post is polite and not slanderous, also negative opinions should be welcome.
So welcome, that if some M$ developer would read these forums more often, maybe Win-dose wouldn't suck so badly.
I am not directly anti-M$. I am against all those mega-multi-corporations that make my (and your) life more miserable than it has to be.

Examples?:

Nestlé bought the 2 local office water-dispenser suppliers a while ago. 
Now the bottles and the dispenser have a more modern design, the plant produces 5 times more bottles than before, and the water is horrible and musty.

I am going to keep talking bad about this and other companies, but only based on my personal experience

---

