---
title: "Tango Generator: An icon compilation script"
date: 2007-12-12
forum: The Cafe
---

### Post by mejy on 2007-12-12
Hi all.

I'm the author of the fairly well known script/hack/app known as the Tango Generator.  It's been offline for a while now since I was fed up with how buggy it was becoming (mostly because I'd been hacking on features for about 6 months) but should be back within a few weeks.  I'm aiming for Christmas, but don't want to make any promises I can't keep.

I'm posting now because I feel having a small group of interested people could help make the release of a much higher quality when it arrives.  I've started work on a very simple drupal website at [http://mejogid.ohallwebservices.com/site/](http://mejogid.ohallwebservices.com/site/), but haven't really get much further than playing round with the CMS.  If anyone is willing to lend experience with PHP, drupal administration or drupal theming that'd be hugely appreciated.

If anyone familiar with the app would like to test it at any of a variety of levels of brokenness, then I'll make it available when it's actually functional. I'm interested in hearing any suggestions based on this or the previous version.  In fact, I'm sure any of you with interest in this project or any relevant skills (python, inkscape, packaging, PHP, css, html) can help.

Finally, here's a brief list of new features that should be available in a few weeks:

[LIST]
[*]About 10 more icon themes
[*]Many more custom drawn icons
[*]Easily extensible application specific themes
[*]Application themes which adapt to the chosen icon theme
[*]Much improved theme selection process - drag and drop support, saving and loading of themes etc.
[*]Support for the new emblem structure introduced in Gnome 2.20
[*]Support for distribution icons (mostly original icons)
[*]Automatic detection of necessary tools (since nobody really seems to read READMEs nowadays)
[*]A generally more robust and extensible core
[*]Greater use of XML
[/LIST]

EDIT: Oh, and if anyone can think of a more imaginative name that may well come about.

---

### Post by lapega on 2007-12-15
Hi!, i can code the HTML/CSS you need, the only problem is i can do it in this week, because I go to vacations until january 10. If you want, you can send me a draft to pgauna at gmail dot com

Bye

---

### Post by rZn on 2007-12-16
Hi
I can mirror the core release if you need, I have a 100/100 connection.
Maybe some drupal help, it depends how much experience with drupal you need. (I haven't done any theming or css)
I have my drupal playground here  -->  [http://tuxus.org]("http://tuxus.org")

Send me a mail to rzn at tuxus.org with your demands ;)

P.S. I can help with Beta testing also D.S.

Regards rZn

---

### Post by kryth on 2007-12-26
I hang after I tell it to compile icons. The progress bar gets almost to end and stops. Any ideas or help?

---

### Post by mejy on 2007-12-26
> **kryth said:**
> I hang after I tell it to compile icons. The progress bar gets almost to end and stops. Any ideas or help?

Try redownloading - I've recently fixed a regression that crept in that may have caused that.  If that fails, try running it from the terminal (double click Tango-Generator.sh and select 'Run in Terminal').

---

### Post by niekez on 2008-01-08
Hello,

I installed Tango Generator 3, and then used the Foxy configuration. But is doesn't look like the screenshot on your website. I think it are just the icons in nautilus that stay the same. What am I doing wrong?

---

### Post by mejy on 2008-01-10
I don't quite understand what you mean - can you post a screenshot?

---

### Post by TeKniKal on 2008-01-15
> **mejy said:**
> I don't quite understand what you mean - can you post a screenshot?

I found out that the foxtrot theme hogs all the attention and I also found a pointer where the cause might lay. My workaround is quite simple: **always uncheck foxtrot**.

All other packages use NxN for their resolution folders. foxtrot uses just N which causes Gnome to flip: so all themes created with Foxtrot enabled do end up with the Foxtrot icons where possible.

I also found another bug: when I created a configuration file with certain packages (foxtrot and some others) left out, I noticed that upon reloading those packages were reselected and put at the top. My current workaround is unchecking the ones at the top (as the first package is mostly the same and quite recognizable).

---

### Post by Ferdil on 2008-03-30
Hey, the website is down, and I cannot download anything. This is really strange, because the day before yesterday it was working, and I downloaded and used the utility -_-.

Could you please check your site and fix it?

[Here is a screenshot of the error it gives.]("http://img296.imageshack.us/img296/3849/schermatamx4.png")

---

### Post by mejy on 2008-04-04
Unfortunately the growing population of the generator has sucked up a fair bit of bandwidth and has overrun a 10GB quota.  It should be up again within a month.

---

