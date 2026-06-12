---
title: "Two css tricks"
date: 2007-01-19
forum: The Cafe
---

### Post by Nonno Bassotto on 2007-01-19
I'm learning how to design web pages, and I like the pure html+css standard. However there are two tricks I'd like to be able to do, but I couldn't find how with a bit of experiment. I gues they should be quite standard.

1) I'd like to have a fixed layout for everything but themain text. So I'm thinking something like that. The header should be fixed when the page scrolls, as well as a left column with the navigation buttons. The text itself should be in a central column, and when you scroll it, it should go behind the header.

2) I'd like to have some links over images. If a user doesn't want images, then he should be able to use textual links. In other words I want a link where images are over, and not behind, the text.

Is there a way to do this?

---

### Post by po0f on 2007-01-19
Nonno Bassotto,

1)  There's probably a way to do this in CSS, but I can't think of any way to do it.  It'd be much easier to use frames.  (I didn't say that.)

2)  I know Netscape had a way to layer different parts of the page, and I believe that CSS implemented it as well.  [Click](http://www.yourhtmlsource.com/stylesheets/csslayout.html), this will probably help you. Google CSS and "z-index" for more info.

---

### Post by geek_Man on 2007-01-19
What do you mean by "In other words I want a link where images are over, and not behind, the text."? Are you trying to make pic links?

---

### Post by po0f on 2007-01-19
geek_Man,

Yes, but with the image *over* the text.  That way, if the user has images disabled (or they can't see them, like from a console web browser) there is text underneath that also serves as a link.

---

### Post by geek_Man on 2007-01-19
What if he gave it a title attribute or maybe... dang, there's some other attribute... it's like some backup in case the link to the pic is broken... whatever. I don't know if that will work though, but maybe.

EDIT: A-HA! What if you gave it an *alt* attribute? THAT'S the one I couldn't remember!

---

### Post by po0f on 2007-01-19
geek_Man,

It wouldn't be wise to rely on the fact that because browser X substitutes the alt tag for the image, browsers Y and Z do as well.  It's what it was created for, but unless Firefox *and* Internet Explorer both support replacing the image with the alt text, I would be hesitant to implement it.  Then there's Opera, etc.  Command-line browsers factor into the decision as well (at least they should in my book; if it looks good in lynx, roll it out!).

---

### Post by geek_Man on 2007-01-19
Well, I didn't say it would work for sure, it was just a suggestion.

---

### Post by DirtDawg on 2007-01-20
> **Nonno Bassotto said:**
> 
1) I'd like to have a fixed layout for everything but themain text. So I'm thinking something like that. The header should be fixed when the page scrolls, as well as a left column with the navigation buttons. The text itself should be in a central column, and when you scroll it, it should go behind the header.

I think what you're asking for is something similar to what I set up on [my site]("http://www.weeklyhilarity.com"). Feel free, of course, to browse/borrow code (but none of the actual content, thank you). Also check out the [master-css]("http://www.weeklyhilarity.com/master.css") file and the [navigationbar-css]("http://www.weeklyhilarity.com/navbar.css") file. I hope this helps. It's a bit tricky.

Good decision, sticking with CSS and avoiding giant table layouts, IMO. Good luck.

EDIT: 2 delicious cappuccinos in my beancount!

---

### Post by macogw on 2007-01-20
> **po0f said:**
> geek_Man,

It wouldn't be wise to rely on the fact that because browser X substitutes the alt tag for the image, browsers Y and Z do as well.  It's what it was created for, but unless Firefox *and* Internet Explorer both support replacing the image with the alt text, I would be hesitant to implement it.  Then there's Opera, etc.  Command-line browsers factor into the decision as well (at least they should in my book; if it looks good in lynx, roll it out!).
put alt and title as the same text, and you're safe in IE, FF, O, and Safari, from what I recall

as to #1...
set header and nav as z-index: 1, text as z-index:0, header and nav are fixed, text is absolute, i think

---

### Post by po0f on 2007-01-20
macogw,

[quote=macogw]put alt and title as the same text, and you're safe in IE, FF, O, and Safari, from what I recall ...[/quote]

That's good to know, thanks.

---

### Post by Nonno Bassotto on 2007-01-20
Thank you all for your advice. The scrolling thing works perfectly, laying everything fixed but the main text which is absolute (I had thought of this, but stick to make it relative ](*,) ).

For the images, the alt tag seems really what I'm looking for. I only have a problem: the same image repeats in various different places in the site (well it's actually a pdf symbol), so I'd rather not hardcode the image into the html, because then if I want to change design, I have to go through all the html to change it. Is there a way to do this with css, so that I have to change a single paragraph?

EDIT: I'm an idiot. I just have to change the actual file for the image...

---

### Post by macogw on 2007-01-20
> **Nonno Bassotto said:**
> Thank you all for your advice. The scrolling thing works perfectly, laying everything fixed but the main text which is absolute (I had thought of this, but stick to make it relative ](*,) ).

For the images, the alt tag seems really what I'm looking for. I only have a problem: the same image repeats in various different places in the site (well it's actually a pdf symbol), so I'd rather not hardcode the image into the html, because then if I want to change design, I have to go through all the html to change it. Is there a way to do this with css, so that I have to change a single paragraph?

EDIT: I'm an idiot. I just have to change the actual file for the image...

hehehe also, if you were using PHP to handle your navbar or something, then you could in the <div title="nav"> one just put a link to the PHP file and have it load the navbar from there, then you can edit the navbar and it'd change on every page, like if you added a new menu item.  i dont know php though.  i wanted to use it for that reason, but i never got around to learning

---

### Post by DirtDawg on 2007-01-20
> **macogw said:**
> hehehe also, if you were using PHP to handle your navbar or something, then you could in the <div title="nav"> one just put a link to the PHP file and have it load the navbar from there, then you can edit the navbar and it'd change on every page, like if you added a new menu item.  i dont know php though.  i wanted to use it for that reason, but i never got around to learning

I knew there must be a way to do this. I don't know php either, but it doesn't look too hard to learn. Thanks for the hint.

---

### Post by picpak on 2007-01-20
I personally like this method:

[http://codegrrl.com/!/scripts/view/nl_converttophp/](http://codegrrl.com/!/scripts/view/nl_converttophp/)

Your site is editable from one page and you can edit your header, menu and footer for every page.

---

### Post by po0f on 2007-01-20
```
[FONT="Courier New"]<?php include("menu.html") ?>[/FONT]
```
I use this for the header, menu, and footer on pages.

---

### Post by Nonno Bassotto on 2007-01-22
This PHP thing seems nice; but then do I need to install a LAMP server just to test my page, or there is a simpler way?

---

### Post by Grey on 2007-01-22
Yeah, you do.  But PHP hosting is fairly easy to come by.

I do both of the tricks you want on [my site](http://grey.drunkencoders.com/).  I don't care if you like the design or not, but have a closer look at the source code.  Then view the page without a style sheet (view->page style->no style).  It's some of the cleanest, most semantically meaningful HTML that I've ever written.  And there's NO JAVASCRIPT anywhere on the site.

The way I've done my navigation bar is just like this:

```

<div id="links">
	<h2>Navigation</h2>
	<ul>
		<li><a href="http://www.drunkencoders.com" title="Drunken Coders!">Drunken Coders</a></li>
		<li><a href="index.php" title="Home">Home</a></li>
		<li><a href="about.php" title="About me, and my resume">About Me</a></li>
		<li><a href="projects.php" title="My projects, ongoing and discontinued">Projects</a></li>
	</ul>
</div>

```

As you can see... it's just plain old hyperlinks, wrapped in an unordered list.  Which is really, what a navigation bar is.  But this basic structure gives you a LOT of power.  I didn't actually do this in this case, as I wanted plain text links.  I just wanted an icon for each one, so I styled the li to give me a box instead.

However, if I had wanted to use a picture, I might update the lis to be something more like this:

```

<li><a href="index.php" title="Home"><span>Home</span></a></li>

```

A small change.  But what it would allow me to do is to hide the li a span css property to display none.  Then I could give each link a background image, and specify the width and height.  In this way, the text in the anchor would not display to CSS enabled browsers, but an image would.  To text based browsers, or non-css compliant browsers, it would look just like a regular old link, since the span would do nothing.

Anyways, I hope it helps.

---

### Post by po0f on 2007-01-22
Nonno Bassotto,

You don't need the full LAMP stack.  For example, I have [lighttpd](http://packages.ubuntu.com/edgy/web/lighttpd) and [php5-cgi](http://packages.ubuntu.com/edgy/web/php5-cgi) working just fine.  It was also easy to set up.

---

### Post by Nonno Bassotto on 2007-01-23
@po0f: Is there any simple guide to set it up? I'm a complete noob.

EDIT: Don't mind. I followed the wiki for Apache+PHP

---

