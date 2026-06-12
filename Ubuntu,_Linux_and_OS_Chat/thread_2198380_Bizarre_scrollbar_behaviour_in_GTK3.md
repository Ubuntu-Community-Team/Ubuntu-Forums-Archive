---
title: "Bizarre scrollbar behaviour in GTK3"
date: 2014-01-08
forum: Ubuntu, Linux and OS Chat
---

### Post by asmith16 on 2014-01-08
I've filed this [bug 721047]("https://bugzilla.gnome.org/show_bug.cgi?id=721047") on the Gnome bugzilla a while ago and though I wasn't expecting immediate attention from the developers I'm really surprised there's no reaction at all. I'll copy-paste the bug report here:

> When I have a page with a lot of content (in my example the credits in the
about box) there is no way to move up or down a page. My only options are:

1) Use the mouse wheel, which is very slow
2) Click somewhere below or above the slider, which results in the content
jumping to that point. As opposed to what it used to do, and still does on
every other platform I know including GTK2: go up or down one page at a time.

I've googled this for a while and found that apparently the old behaviour can
be restored using gtk-primary-button-warps-slider = false in
~/.config/gtk-3.0/settings.ini

I was finishing up migrating one of my projects (Asunder) from GTK2 to GTK3
when I found this bug, which is significant enough that I'm going to roll back
to GTK2.

Also as a user I find this extremely annoying in the programs that were ported
to GTK3: specifically evince and synaptic come to mind. Clicking on the
scrollbar results in the content view jumping to some completely undefined
location in the document. It is pretty much impossible to guess what you're
going to get or how to return to the previous location in the document.

I looked at these documents:

[https://wiki.gnome.org/Design/OS/Scrolling](https://wiki.gnome.org/Design/OS/Scrolling)
[https://wiki.ubuntu.com/Ayatana/ScrollBars](https://wiki.ubuntu.com/Ayatana/ScrollBars)

And this behaviour is not even in the designs. A mouse-controlled scrollbar is
the only type affected by this "feature" and in this environment it doesn't
work as expected, so as far as I know this change has been introduced
accidentally without thinking it through.

Am I missing something? Is this not clearly a bug that should be fixed? I can't come up with a use case where the scroll bars behaving the way they do would be a good thing.

---

### Post by ssam on 2014-01-09
Thanks for finding that. Its been annoying me as well. (I am using MATE but programs are gradually switching to gtk3)

I need to put
```

[Settings]
gtk-primary-button-warps-slider = false

```
in ~/.config/gtk-3.0/settings.ini

---

### Post by Copper Bezel on 2014-01-09
That behavior doesn't seem problematic for long documents with full-size scrollbars, but it would seem a bit batty for small, scrollable frames in something like Synaptic. I actually used Gnome Shell for a month or so on one of my machines recently, and I didn't notice this, but I suppose it's consistent with slider behavior.

Every time these topics come up, I'm more astounded that people use scrollbars. Then again, I suppose the page up / page down and home / end aren't exactly intuitive, and I did have to get one of those mice with the free-spinning scroll wheel as soon as I found out about them.

---

### Post by asmith16 on 2014-01-13
Sorry, I'm not sure I understand what you mean by "consistent with slider behavior". What else behaves that way?

It's bad for all kinds of documents. I had the problem in Evince as well, where I had a full-length scrollbar but several hundred pages, and I constantly clicked on the scrollbar to go down a page and instead jumped down a few hundred pages.

I haven't tried it but I expect it'd be a similar problem with shorter documents. How can you know where in the document you'll end up?

---

### Post by Copper Bezel on 2014-01-13
I guess that if I was jumping, I would be more likely to scrub, and if I was just jumping a page up or down - well, I wouldn't be using the scrollbar. But yes, the longer the document, the more a problem it would be.

GTK sliders work this way - see your volume control in the sound indicator.

---

