---
title: "[SOLVED] Website &amp;amp; HTML Page creation"
date: 2008-11-27
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2008-11-27
What software for Ubuntu can make websites/webpages? I am being asked by a friend to make a website. I have no idea of where to start. He has a MAC and can get some Adobe software if there is nothing for Linux. Any opinions most(ly) welcome.

---

### Post by Idefix82 on 2008-11-27
Do you know any html? If not then that's what you should start learning first. You will be able to learn the basics within one or two days and there are thousands of tutorials on the web.

Once you know html, your best tool will be a simple text editor with syntax highlighting and some useful functionality, e.g. Gedit with a couple of plugins.

Be warned that even with a very sophisticated WYSIWYG editor you are unlikely to produce anything decent without knowing any html at all.

---

### Post by celavi on 2008-11-27
try bluefish, quanta, kompozer or screem. i have those html editors installed right now as i don't know myself which one suites me best. should all be in the repository

---

### Post by miggols99 on 2008-11-27
I recommend you learn HTML and CSS, the major building blocks of website creation. The best website for learning these is htmldog.com :) And it's good for refering to tags and what they do.

---

### Post by mr.propre on 2008-11-27
In real bad situations, notepad, gedit, vi, ... is all you need.
Personally I use Geany and Dreamweaver CS3. The last one is Windows/MAC but hey, I'm ad designer and developer. I still need windows and when it comes to programming or designing you should choose an environment (OS and software) that fits you best. If that means windows, than you should use windows. I use both windows and Linux, depending on the task.

You are vague with the term 'making a website'. Do you mean a layout, an application or both.

When you are making the layout (the looks) you need to know xhtml and CSS, it's quite easy to learn, but you will only make static pages (aka: not a blog or forum, ...)

When you make an application (blog, forum, ...) you need to learn some sort of program code and SQL. If you love the opencource way, PHP and MYSQL are the way to go.

However, to style an application (the looks) you will need to know xhtml and CSS. Learning this will take time and I would recommence some sort of book, not just tutorials. More perfect was to take some sort of lessons in the evening.

Alternative you could also use out-of-the-box solutions like wordpress, phpBB, Joomla!, ... Easy and quick and the perfect solution if you only planning to make one website.

Here are some real basic stuff about websites you should know before you start:
[http://en.wikipedia.org/wiki/Website](http://en.wikipedia.org/wiki/Website)
[http://en.wikipedia.org/wiki/Website_Design_Process_Steps](http://en.wikipedia.org/wiki/Website_Design_Process_Steps)
[http://en.wikipedia.org/wiki/Web_design](http://en.wikipedia.org/wiki/Web_design)
[http://en.wikipedia.org/wiki/Web_development](http://en.wikipedia.org/wiki/Web_development)

---

### Post by zmjjmz on 2008-11-27
[http://w3schools.com](http://w3schools.com) is where I learned most of my HTML/CSS, and I use Notepad++ (in WINE) and KompoZer for website development.

---

### Post by Dr Small on 2008-11-27
Vim

---

### Post by handy on 2008-11-27
If all else fails & you want a really easy way out, use [***_Sandvox_***]("http://www.karelia.com/sandvox/") on the Mac, you have to pay for it but it costs $49- U.S.

---

### Post by Paqman on 2008-11-27
Dreamweaver 8 works perfectly in Wine, and knocks all the native Linux html editors into a cocked hat, IMO.

But yes, learn the html/css first. One handy thing to do when you're learning is to use the html editor in split screen mode, and watch what code it writes to do things. Be warned though, html editors often do weird things, like inserting &nbsp; on a blank line instead of using the <br/> tag. Always best to keep an eye on the output they generate.

---

### Post by Rokurosv on 2008-11-27
I don't recommend a WYSIWYG editor like Dreamweaver if you're a beginner, gedit is perfect, Geany is my favorite hands down, it's fast and has a lot of features, I don't recommend a simple editor like mousepad, it works and you can make pages in it, but the syntax highlight that some editors offer is very handy. 
I learned HTML in [http://htmldog.com/](http://htmldog.com/) and after that you might want to take a look at "Head First HTML with CSS and XHTML" from O'reilly media, it's a very good book for learning the basics and a little more.
[http://www.headfirstlabs.com/books/hfhtml/](http://www.headfirstlabs.com/books/hfhtml/)

---

### Post by -grubby on 2008-11-27
> **miggols99 said:**
> I recommend you learn HTML and CSS, the major building blocks of website creation. The best website for learning these is htmldog.com :) And it's good for refering to tags and what they do.

[http://w3schools.com/](http://w3schools.com/) is my favorite website to learn more about web languages. It helped me immensely in learning (X)HTML, CSS, and PHP. I do not recommend you use a wysiwyg editor to generate pages, as it tends to turn out with poorly written, non-cross-browser code

---

### Post by Saint Angeles on 2008-11-28
i have bluefish, but i always end up using gedit.

part of my job requires me to cleanup peoples' horrible dreamweaver code. its disugusting with hundreds of redundant empty table cells, centered divs with nothing in between tags, and really bad relative URLs with no standard (sometimes "./images", other times you'll see "images" in the URL path)...

bah!

on windows i used notepad. gedit is 100 times better.

---

### Post by hessiess on 2008-11-28
If you want effishent-standards complient sites then learn HTML and CSS. Pearsnally I find that wrighting websites in Vim is actualy *easier* than using bloated visual programs that vastly overcomplicate everything.

---

### Post by Paqman on 2008-11-28
> **hessiess said:**
> If you want effishent-standards complient sites then learn HTML and CSS. Pearsnally I find that wrighting websites in Vim is actualy *easier* than using bloated visual programs that vastly overcomplicate everything.

It's about more than just writing the pages in the first place. HTML editors are designed to simplify the maintenance as well. I'm sure someone could do a perfectly good job of maintaining a large site without an html editor, but they'd have to use a bag full of smaller apps to do it. Why not just use one app to do everything? I guess it's just personal preference at the end of the day.

---

### Post by mr.propre on 2008-11-28
> **Paqman said:**
> It's about more than just writing the pages in the first place. **HTML editors are designed to simplify the maintenance as well.** I'm sure someone could do a perfectly good job of maintaining a large site without an html editor, but they'd have to use a bag full of smaller apps to do it. Why not just use one app to do everything? **I guess it's just personal preference at the end of the day.**

That is so true, the only reason I use Dreamweaver is because the html and css editor gives you suggestions. For example, if you type "back" in a css file, it will give you the suggestion "background" and you just need to hit enter instead of typing the whole word. Tis is a large time saver. If people could suggest a similar function in a Linux program, I'm always happy to try different programs.

---

### Post by hessiess on 2008-11-28
> **mr.propre said:**
> That is so true, the only reason I use Dreamweaver is because the html and css editor gives you suggestions. For example, if you type "back" in a css file, it will give you the suggestion "background" and you just need to hit enter instead of typing the whole word. Tis is a large time saver. If people could suggest a similar function in a Linux program, I'm always happy to try different programs.

Actually that's one of the reasons why I hate Dreamwever, I end up accidentally adding code I don't want, which gets very annoying. each to his own I guess :popcorn:

---

### Post by marcusdwight on 2008-12-06
hi,
if anyone is still watching this thread, here's what i came up with.

as a beginner in web development that is learning xhtml and css, i *want* to become a strong web programmer. on the other hand, i am not the most "artistic" person, and so i would like the ability to play with my page layout visually. so i installed kompozer with the handcoder extension, and then assigned bluefish as my code editor. with both apps open, i can quickly flip back and forth between them (i spend about 90% of my time in bluefish, it's an incredible program).

any changes in bluefish automatically update in komposer. when tweaking my page layout in kompozer, i first save my changes in K, then use the "revert to saved" function in bluefish (i simply assigned a shortcut key to the function, so it's very quick). this updates bluefish to the latest saved version of the web page being worked on.

this combo gives me what i am guessing is the closest thing to DW you will find in free linux software. i have all the visual tweaking ability as well as powerful source coding with syntax highlighting and code completion ;). the best of both worlds... i don't see any reason why a person has to choose between one or the other.

hope this helps.

---

