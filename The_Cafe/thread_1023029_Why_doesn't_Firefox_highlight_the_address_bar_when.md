---
title: "Why doesn't Firefox highlight the address bar when I click it in Linux?"
date: 2008-12-27
forum: The Cafe
---

### Post by pytheas22 on 2008-12-27
This has long been a mystery to me and I'm wondering if anyone here has an explanation:

In Windows, in both Internet Explorer and Firefox, if I left-click once in the address bar, the whole URL gets highlighted.

In every Linux distribution that I've ever used, of course, clicking in the address bar in Firefox (and Konqueror too I think) doesn't cause the URL to be highlighted.

I know I can change this behavior in about:config, etc., etc., but I'm not looking for instructions on how to do that.  I just want to know if there's any particular reason *why* this default behavior is different between Linux and Windows, even in cross-platform applications like Firefox.  Is there an historical reason?  Does it have to do with X11, for example?

If anyone can shed any light on this, I'd be interested.

---

### Post by Dr Small on 2008-12-27
It annoys me to death when I use Firefox on my parent's system (running windows) that when I click the address bar, it hightlights the entire address. To me, this is extra work, because 90% of the time, I click to change the address, not select to copy it.

---

### Post by smartboyathome on 2008-12-27
Because, in Linux, highlighting copies text to a second clipboard, which then can be placed via the middle click.

---

### Post by saulgoode on 2008-12-27
If a left-click automatically highlighted the entire location field, it would be impossible to use the X11 "middle-click copy-n-paste" -- the highlighting would mean that middle-clicking would insert the existing URL text into that same text, resulting in a garbage URL.

What I should like to see, however, is a button which cleared the location field (permitting middle-click to insert a new URL without having to backspace over the previous one), and a button to "go" to the URL enterred. This would allow much easier mouse-only navigation under X11.

---

### Post by walkerk on 2008-12-27
> **smartboyathome said:**
> Because, in Linux, highlighting copies text to a second clipboard, which then can be placed via the middle click.

I had no idea.

---

### Post by Sand &amp; Mercury on 2008-12-27
> **walkerk said:**
> I had no idea.
Neither did I. I noticed you could paste via middle-click but always thought it was just a Firefox thing, so I never bothered with it. Handy.

---

### Post by Jose Catre-Vandis on 2008-12-27
See this:

[http://ubuntuforums.org/showthread.php?t=228930](http://ubuntuforums.org/showthread.php?t=228930)

will sort it out for you :)

---

### Post by RiceMonster on 2008-12-27
If you want that, hit Ctrl-l. that will take you right to the address bar and highlight the text.

But yeah, the reason is the middle click thing. I never use that though.

---

### Post by pytheas22 on 2008-12-27
Thanks for all of the responses.  It makes sense now, and it's nice to know that there really is a logic behind it.

I actually prefer the Linux behavior, because, as someone else said, 90% of the time when I click the address bar, it's to modify the URL, not copy it to the clipboard.  If I want to copy I can just press alt-D>control-C without having to touch my mouse (I think control-L is equivalent to alt-D in Firefox 3, but I think that this was not always the case in earlier versions and in other browsers).

---

### Post by GCG199 on 2008-12-27
I ran into this "problem" too. Part of it comes down to learning the keyboard shortcuts to make using the computer quicker &#8212; don't just depend on the mouse.

Like mentioned above, one keyboard shortcut for highlighting the URL bar is the Control [Ctrl] and "L" keys. [Works best right-handed, but then one has to move their hand off the mouse to use it.]

Another one is the Alternate [Alt] and "D" keys. Then press the "delete" key to clear it. [This works better left-handed and can leave the right hand on the mouse.]

One normally has to double-click the mouse pointer on the URL bar in Linux to highlight it.

One more tip: Do a web search with your favorite search engine for keyboard shortcuts for various software and Operating Systems. 

Also, some of the tech websites for Linux have articles about this. Some of them offer .pdf documents of these too.

---

### Post by Dr Small on 2008-12-27
Well, since I am running vimperator anyhow, I never see the address bar, so no clicky-clicking. I just press <shift>+o to edit the address. Meerly pressing "y" yanks the address to the clipboard :D

Vimperator + Dvorak + Lefthanded Mouse = 1337! ;)

---

