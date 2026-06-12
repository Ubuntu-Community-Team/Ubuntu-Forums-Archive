---
title: "text editor, tabs and autowrap"
date: 2012-01-11
forum: The Cafe
---

### Post by bonfire89 on 2012-01-11
Hey all,

I was wondering if there was a text editor out there that will preserve indentation when a line wrap occurs?

I know libre/open office does this, but, those apps are a bit heavy for my liking since this is just for class notes.


Thanks!


edit: it is starting to look like VIM might be able to do this, if so, I might just end up being a convert. I'm still researching.

[http://vim.1045645.n5.nabble.com/Wrapping-relative-to-current-indent-td4709860.html](http://vim.1045645.n5.nabble.com/Wrapping-relative-to-current-indent-td4709860.html) I'm too much of a newb to know how to apply this though

---

### Post by sffvba[e0rt on 2012-01-11
When I have to update a wiki I found the same issue. So far I haven't found a light weight editor that does what I need, so I use the "fold" command in terminal to wrap the text for me.


404

---

### Post by ilovelinux33467 on 2012-01-11
I think Kate will do what you need. I have attached a screenshot showing an example in it. Is this kind of what you wanted or am I thinking of the wrong thing?

---

### Post by bonfire89 on 2012-01-11
@ilovelinux33467 58.8MB of new archives later, and yep, kate works the way I want! Thanks!

@not found, which editor were you using?

---

### Post by sffvba[e0rt on 2012-01-11
> **bonfire89 said:**
> @ilovelinux33467 58.8MB of new archives later, and yep, kate works the way I want! Thanks!

@not found, which editor were you using?

I would use any text editor, save the file in plain text then in terminal:

```
fold -s filename.txt > newfile.txt
```

Then the new file would be nice and wrapped.


404

---

### Post by Copper Bezel on 2012-01-11
Smashing. I've been wishing gedit had soft indents like that for quite some time, as it *is* particularly necessary with note-taking. Thanks both to bonfire89 for asking the question and ilovelinux33467 for knowing the answer. = ) I used to be afraid of Kate, but with a few tweaks, it's simpler than gedit, and the only thing I miss is gedit's overlay scrollbars.

---

### Post by bonfire89 on 2012-01-11
@not found, oh cool, I learned about a new program! I didn't know that exists. Surely it will come in use but seems a bit cumbersome. 

@Copper Bezel, the last year or two I have spent a lot of time doing manual line breaks and lots of tabbing while taking class notes. Then I by accident stumbled upon [http://www.sublimetext.com/2](http://www.sublimetext.com/2) which has the line wrap functionality I want and decided I couldn't deal with the manual work of gedit anymore. But, then I found out sublime was $60USD which is too much for me since I'd only be utilizing a fraction of its capabilities and because fully featured word processors come at $0, and because as a student my monthly income is $0.

---

### Post by trivialpackets on 2012-01-11
Currently, Sublime-Text-2 has no time limit for their testing however, so if you want to continue to try it out or use it for the time being, you are certainly able to.  Personally, I am absolutely ready to fork over the $ when the time comes.  It's also a terrific code editor.

---

### Post by Copper Bezel on 2012-01-11
[QUOTE=bonfire89]@Copper Bezel, the last year or two I have spent a lot of time doing manual line breaks and lots of tabbing while taking class notes.[/QUOTE]
Exactly - and then, I imagine, spent several frustrated seconds fixing indentation when you needed to jump back and add something. This topic has ever-so-slightly improved my quality of life. = )

---

### Post by bonfire89 on 2012-01-11
@Copper Bezel, haha, oh yep

@eric.proctor, yeah I know, but nags you from time to time when saving and says unregistered up at the top. I don't think I'd ever buy because I am literally only making jot notes. No code completion, no snippets, no syntax highlighting.

---

### Post by ilovelinux33467 on 2012-01-12
> **Copper Bezel said:**
> Smashing. I've been wishing gedit had soft indents like that for quite some time, as it *is* particularly necessary with note-taking. Thanks both to bonfire89 for asking the question and ilovelinux33467 for knowing the answer. = ) I used to be afraid of Kate, but with a few tweaks, it's simpler than gedit, and the only thing I miss is gedit's overlay scrollbars.

> **bonfire89 said:**
> @ilovelinux33467 58.8MB of new archives later, and yep, kate works the way I want! Thanks!

@not found, which editor were you using?

You're welcome. :)

---

