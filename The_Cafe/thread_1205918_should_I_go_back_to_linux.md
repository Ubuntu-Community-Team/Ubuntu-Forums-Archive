---
title: "should I go back to linux?"
date: 2009-07-06
forum: The Cafe
---

### Post by kashey_be on 2009-07-06
hey,
I have been using linux for 2 years, then went to xp because of game support.
recently "downgraded" to vista64, though hell I'll try it and see what happens.
well shi*t happened and now i'm thinking of either trying win7 or putting back linux (since i don't game so much nowdays).
I'll need some software replacement , and ask for your recommendation:

mathtype
java IDE ( eclipse should do i assume )
c++ IDE ( ??? heard eclipse has plugin for cpp support ??? )
oh and someone please recommend some good pdf viewer ( not that crap gnome is provided with  - and not okular it sucks)

thanks in advance!

---

### Post by dragos240 on 2009-07-06
> **kashey_be said:**
> hey,
I have been using linux for 2 years, then went to xp because of game support.
recently "downgraded" to vista64, though hell I'll try it and see what happens.
well shi*t happened and now i'm thinking of either trying win7 or putting back linux (since i don't game so much nowdays).
I'll need some software replacement , and ask for your recommendation:

mathtype
java IDE ( eclipse should do i assume )
c++ IDE ( ??? heard eclipse has plugin for cpp support ??? )
oh and someone please recommend some good pdf viewer ( not that crap gnome is provided with  - and not okular it sucks)

thanks in advance!
Please don't say that word here. But it's up to you, you can come back any time you want, we'll welcome you back with open arms.

---

### Post by Bölvaður on 2009-07-06
> **kashey_be said:**
> 
java IDE ( eclipse should do i assume )
c++ IDE ( ??? heard eclipse has plugin for cpp support ??? )
oh and someone please recommend some good pdf viewer ( not that crap gnome is provided with  - and not okular it sucks)


Eclipse might be an overkill.
Eclipse with plugin for c++ was an overkill for me, try Geany for small and "medium" size projects.
brb

---

### Post by RiceMonster on 2009-07-06
> **kashey_be said:**
> hey,
mathtype
java IDE ( eclipse should do i assume )
c++ IDE ( ??? heard eclipse has plugin for cpp support ??? )

Netbeans can handle java (well duh) and C++ as well. I recommend you give it a try. It's pretty nice.

---

### Post by camper365 on 2009-07-06
Most Linux developers don't need an IDE for C++. Most of them just use a text editor and a terminal with g++. However, I have heard of anjuta, which is a c++ ide in the repos.

---

### Post by Tibuda on 2009-07-06
> **kashey_be said:**
> oh and someone please recommend some good pdf viewer ( not that crap gnome is provided with  - and not okular it sucks)

I prefer the "crappy" Evince, but what about Adobe Reader or Foxit Reader? Both have native Linux versions.

---

### Post by Pogeymanz on 2009-07-06
There are plenty of IDE options, which were mentioned already. What were you using in Windows?

And I use ePDFview. It's in the repos. You can always use Adobe Reader also as they do have a Linux version.

Welcome back.

---

### Post by kashey_be on 2009-07-06
thanks all, i guess i'll install 9.04 and just roll with it
checked some stuff on my virtual machine (good old 7.04)
-eclipse is excellent for java
-i tried anjuta, but it's not so great, will try other alternative
-camper365, i coded on vim and gedit before, but it's impossible to debug large scale projects using these, you need more advanced tools.
-still no replacement for mathtype though, a friend recommended "latex", anyone had any experience with it?

---

### Post by rockcrawler on 2009-07-06
> **kashey_be said:**
> 
-still no replacement for mathtype though, a friend recommended "latex", anyone had any experience with it?

What about OpenOffice's Formula.  It comes with the oo that is packaged with Ubuntu.  You just need to add it to the menu to access it directly.  Seems pretty comparable to me.  Though I have not used it extensively.

---

### Post by kashey_be on 2009-07-06
it's similar to office math tools.
it can't be compared with mathtype, this tool simply surpasses every other i know.
it would be silly to run wine + office + mathtype on linux..
i'm sure there something as good in linux, but i just haven't found it yet :|

---

### Post by Pogeymanz on 2009-07-06
LaTeX is what REAL MEN use.

---

### Post by kashey_be on 2009-07-06
:D okey, i'll check it out
thanks

---

### Post by Daisuke_Aramaki on 2009-07-06
Just a question mate. If mathtype is extremely important for you, would it be ok to assume you focus a lot in writing reports, or may be in a stage where you are writing your thesis or something like that. Personally, nothing beats Latex in that regard. Sure it requires a bit of getting used to, but I personally cannot imagine doing documentation without Latex. So my question is have you tried Latex?

---

### Post by Idefix82 on 2009-07-06
> **kashey_be said:**
> it's similar to office math tools.
it can't be compared with mathtype, this tool simply surpasses every other i know.
it would be silly to run wine + office + mathtype on linux..
i'm sure there something as good in linux, but i just haven't found it yet :|

If you are prepared to learn something new then go for LaTeX. It's actually the only piece of technology that can be taken seriously when you want to typeset more than five pages of formulae (believe me, I know what I am talking about). Even for less than that, it's by far the best solution. There are several very good Latex editors/addons under Linux, the most popular being Vim with Latex plugin, EMacs with Latex plugin, GEdit with Latex plugin, Kile under KDE, Texmaker,... there are many others.

Edit: I see lots of people have beaten me to it :)

---

### Post by Daisuke_Aramaki on 2009-07-06
i would also suggest TeXmacs. Its a little easy to get used to LateX when you are a beginner. Once you are used to it, you can use emacs, or like me vim with the latex plugin!

---

### Post by Tibuda on 2009-07-06
LaTeX is used for scientific papers, perfect to create high-quality math formulas, but you need to learn the syntax. Here are some reference:

[http://ctan.tug.org/tex-archive/info/lshort/english/lshort.pdf](http://ctan.tug.org/tex-archive/info/lshort/english/lshort.pdf) (PDF)
[http://web.reed.edu/cis/help/latex/](http://web.reed.edu/cis/help/latex/)
[http://www.andy-roberts.net/misc/latex/index.html](http://www.andy-roberts.net/misc/latex/index.html)

To install it on Ubuntu, see [https://help.ubuntu.com/community/LaTeX#TeX%20Live](https://help.ubuntu.com/community/LaTeX#TeX%20Live). There are some frontends for LaTeX, like Kile or LyX, but you can use any text editor.

---

### Post by kashey_be on 2009-07-06
ok this is exactly what i need.
does it have direct plugin to work with OO?

---

### Post by Daisuke_Aramaki on 2009-07-06
> **kashey_be said:**
> ok this is exactly what i need.
does it have direct pluging to work with OO?

There is oolatex, a set of macros that can be used in OO as well. But when you use Latex for typesetting, OO can be completely forgotten!

---

### Post by kashey_be on 2009-07-06
Thanks everyone for the replies!
This is exactly the reason I like linux - excellent community.
At these moments 9.04 is being downloaded :D

---

### Post by skintythe1andonly on 2009-07-06
if you want to to do proper scientific writting, you should invest in Latex. It is relatively easy and does provide the best looking equations by far

---

