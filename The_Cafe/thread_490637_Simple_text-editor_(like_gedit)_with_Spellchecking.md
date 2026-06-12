---
title: "Simple text-editor (like gedit) with Spellchecking?"
date: 2007-07-02
forum: The Cafe
---

### Post by Kimm on 2007-07-02
I was just woundering if there is such a thing?? Preferably with several languages (using myspell or aspell?). Sometimes when I feel like writing something, I don't want to fire up a big application like OpenOffice (or even AbiWord for that mather), something small like GEdit does the  job nicely! But I do miss spellchecking...

Tips? :-)

---

### Post by Rui Pais on 2007-07-02
> **Kimm said:**
> I was just woundering if there is such a thing?? ... something small like GEdit does the  job nicely! But I do miss spellchecking...

Tips? :-)

ahh... F7? 
;)

---

### Post by ynnhoj on 2007-07-02
i'm pretty sure kate does spell checking -- not sure if you want to install all the kde stuff though.

oh, and gedit appears to have a spell check plugin (which rui pais alluded to).  are you looking for something that will underline/highlight mis-spelled words too?

---

### Post by Kimm on 2007-07-02
> **Rui Pais said:**
> ahh... F7? 
;)

Aaah, thank you! I had missed that function :P

---

### Post by Rui Pais on 2007-07-02
No problem :)

Note that besides F7 (Check Spelling), you got, on menu under Tools, a 'Autocheck Spelling' and a 'Set Language' options.

Have fun 
:D

---

### Post by quixotic-cynic on 2007-10-26
Thanks for starting/contributing to this thread - it saved me from making a new one.

Is there a simple GUI text editor with spell check that does not rely on any Gnome or KDE dependencies?

I know about Kate, but I'm trying to avoid it. I know about Nano, but it is a little *too* basic for what I am looking for. On-the-fly spell checking would be useful, etc.

So, under those constraints, could someone possibly suggest something?

---

### Post by LaRoza on 2007-10-26
> **quixotic-cynic said:**
> Thanks for starting/contributing to this thread - it saved me from making a new one.

Is there a simple GUI text editor with spell check that does not rely on any Gnome or KDE dependencies?

I know about Kate, but I'm trying to avoid it. I know about Nano, but it is a little *too* basic for what I am looking for. On-the-fly spell checking would be useful, etc.

So, under those constraints, could someone possibly suggest something?

You want simple, yet you want complex. Spell checking is not a feature of simple text editors in most cases.

---

### Post by quixotic-cynic on 2007-10-26
I knew someone was going to do that... >.<

Perhaps I should have tried harder to be more specific.

An editor with a simple interface, not necessarily simple features, I guess. I think most people will know what I mean. If not... like mousepad but with spellchecking is an approximation.

---

### Post by Kimm on 2007-10-26
> **quixotic-cynic said:**
> I knew someone was going to do that... >.<

Perhaps I should have tried harder to be more specific.

An editor with a simple interface, not necessarily simple features, I guess. I think most people will know what I mean. If not... like mousepad but with spellchecking is an approximation.

Take a look at Tea ([http://tea-editor.sourceforge.net/](http://tea-editor.sourceforge.net/)).
I dont know if it's what you are looking for... but atleast it shouldnt have any gnome dependencies

---

### Post by quixotic-cynic on 2007-10-26
> **Kimm said:**
> Take a look at Tea ([http://tea-editor.sourceforge.net/](http://tea-editor.sourceforge.net/)).
I dont know if it's what you are looking for... but atleast it shouldnt have any gnome dependencies

Thank you very much for the reply. It looks promising. From trying to install from the repo I get ```
The following NEW packages will be automatically installed:
  gnome-mime-data libavahi-glib1 libgnomevfs2-0 libgnomevfs2-common 
  libgtksourceview-common libgtksourceview1.0-0 tea-data
```

However, the link you gave me suggests compiling with --enable-legacy to avoid the gnomes, so there is hope yet. :)

Edit: Unfortunately when trying to compile it asks me for gtk+2 (which I have?). I think it may want the -dev file but that pulls in >40mb of dependencies so I really don't want to do that...

---

### Post by quixotic-cynic on 2007-10-28
I couldn't get TEA to compile in the end. However, they have an up-to-date RPM via their website so I installed that using alien (and libgtksourceview-2.0 via aptitude) and it seems to be working more or less. Thanks again for the recommendation. It seems overly complex, but complex with spellchecking is better than leafpad etc with no spell checking.

---

### Post by NevarMaor on 2008-03-13
Don't know if you're still looking but another program to try for non-Gnome text editing with spell check is cream, a gui frontend to vim

---

