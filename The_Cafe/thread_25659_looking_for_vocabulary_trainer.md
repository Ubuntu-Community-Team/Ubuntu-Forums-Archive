---
title: "looking for vocabulary trainer"
date: 2005-04-10
forum: The Cafe
---

### Post by occy8 on 2005-04-10
Hi, I'm looking for a vocabulary trainer for Gnome
It needs to be able to use or import text-csv files and have Unicode UTF-8 support.
I have googled a lot but found only KDE or windows versions
 :x

---

### Post by kassetra on 2005-04-10
[QUOTE=occy8]Hi, I'm looking for a vocabulary trainer for Gnome
It needs to be able to use or import text-csv files and have Unicode UTF-8 support.
I have googled a lot but found only KDE or windows versions
 :x[/QUOTE]

I'm unsure if these do exactly what you want... but you might want to check them out:
[http://www.gnomefiles.org/subcategory.php?sub_cat_id=133](http://www.gnomefiles.org/subcategory.php?sub_cat_id=133)

---

### Post by occy8 on 2005-04-10
> I'm unsure if these do exactly what you want... but you might want to check them out:
[http://www.gnomefiles.org/subcatego...?sub_cat_id=133](http://www.gnomefiles.org/subcatego...?sub_cat_id=133)

granule looks like it but uses a strange format 
I just found one in Ubuntu can you believe it its called langdrill and seems to be allright I can copy and past my wordlists in one of theres it uses UTF-8 characters but...

I can't enter anything from the keyboard in 'Simple quizz'
Any idea why this is happening?

---

### Post by kassetra on 2005-04-10
[QUOTE=occy8]I can't enter anything from the keyboard in 'Simple quizz'
Any idea why this is happening?[/QUOTE]

I forgot I had langdrill installed (*note to self, study more, tinker less) - 
No, I can't type in the simple quizz box either... but I can paste into it.

This is the only thing I could find, so far, as to why it doesn't allow input:
```
(langdrill:16323): Gdk-CRITICAL **: file gdkfont-x11.c: line 288 (gdk_font_from_description_for_display): assertion `font_desc != NULL' failed
``` 
So I'll need to look into it more...  It's obviously a bug though, and the langdrill devs might already have it fixed or they might not even know about it.

---

### Post by james_mad on 2005-04-10
Excuse me, but what exactly is a vocabulary trainer?  I am guessing that it is to expand your vocabulary of a certain language, but I am curious as to how it works?  Is it like a flashcard game of match definition to word?  Or how exactly does it work?  Thanks

---

### Post by kassetra on 2005-04-10
[QUOTE=james_mad]Excuse me, but what exactly is a vocabulary trainer? I am guessing that it is to expand your vocabulary of a certain language, but I am curious as to how it works? Is it like a flashcard game of match definition to word? Or how exactly does it work? Thanks[/QUOTE]

Yeah, vocabulary trainers are for language learning... they usually have lots of components, like flashcards, quizzes, listening->typing practice, that kind of stuff.  :)

---

### Post by occy8 on 2005-04-13
> So I'll need to look into it more... It's obviously a bug though, and the langdrill devs might already have it fixed or they might not even know about it.

Hi Kass, 
great I edited a language file already to the language I'm learning and using the multiple choice test.
Hope you get an answer...
I noticed as well that you can't close it you need to kill it and the language column names are always japanese - english

cheers
occy

---

### Post by Eremit on 2005-04-23
Hallo I tried to convert the required libs for granule with alien, but I ran into unfulfilled dependences.

Have you had any luck with it?

I tried Languagedrill either, but it's functionality is limited and I want a flashcard system.

---

### Post by occy8 on 2005-04-23
Hello Eremit,
no I don't want to use Granule because the wordlists are a little complicated
In Langdrill its so much easier to add lists  
Language1 = language2 
I like that if I only could use the keyboard ](*,) 

I noticed there is a new version 0.3.4 
I installed it but the same problems

let me know if you get it working or find something else
cheers

---

### Post by sethmahoney on 2005-04-23
Langdrill looks pretty cool.  Anybody know where I could get a Russian configuration file for it?

---

### Post by Eremit on 2005-04-24
sethmahoney is right about language drill.

What I do know is, write my word-list in a CSV File.
Import it with kvoctrain, save it as a kvoctrain-file and import it with ksalomon.

Although these are applications for kde they work well with gnome.

kvoctain is in the ubuntu tree and ksalomon can be downloaded in .deb format.

ksalomon has this nice flash-casd system

---

### Post by occy8 on 2005-04-24
Yeah thought about kvoctrain, but its a rediculous 30mb download with all the kde stuff. Besides I'm not sure if the importation works, does it?


> Langdrill looks pretty cool. Anybody know where I could get a Russian configuration file for it? 

You can edit one of the existing ones. I'm learning portuguese. So I opened one in the texteditor. changed for example french to portuguese, then deleted the french english words and pasted my word list in there.

When you put a word in the [   ] it creates a folder, so you can study different subjects

---

### Post by Eremit on 2005-04-25
[QUOTE=occy8]Yeah thought about kvoctrain, but its a rediculous 30mb download with all the kde stuff. Besides I'm not sure if the importation works, does it?[/QUOTE]

Well 30mb are not that much. Yes the importation works, in the way as I have described it.
.csv -> kvoctrain -> kvoc-file -> ksalomon

---

