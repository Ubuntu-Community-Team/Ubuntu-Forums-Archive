---
title: "Don't like Docky's bold fonts?"
date: 2010-02-24
forum: The Cafe
---

### Post by Ubom on 2010-02-24
Quick guide to getting normal fonts in Docky, I couldn't find anywhere which had this information so I thought I would provide this information myself. So here it is:

First you need to get docky bzr, to do this simply open terminal and move to a directory you want to use (eg. cd Downloads). Then run the command: ```
bzr branch lp:docky
```Now minimize the terminal and go to the folder which you were using, there should now be a folder by the name of "docky" inside.

The next step involves editing some files, the first of which is found at:
> Docky.Items/Docky.Items/AbstractDockItem.csYou can use gedit or mono-develop or whatever text editor you like to do this. Find (ctrl+f usually) "Bold", use a capital "B" in the search as it might be case sensitive search. 
You should find 2 uses of "Bold" in the code in the form "Pango.Weight.Bold", simply replace the "Bold" with "Normal" so that it says "Pango.Weight.Normal". The line numbers for the occurances are 641 and 725.

The second file which needs to be edited can be found at:
> Docky/Docky/Menus/MenuItemWidget.csLike before find (ctrl+f) "Bold", still searching with a capital "B". This time you should find 3 uses of "Bold" in the code however you only need to edit the two which are in the form "Pango.Weight.Bold", simply replace "Bold" with "Normal" like before. The line numbers for the occurances you need to edit are 106 and 278.

In total you only change two words in each of the documents so that where it used to say "Pango.Weight.Bold" it now says "Pango.Weight.Normal".

Then just go back to your terminal window, move to the docky directory -cd docky - and run the following three commands in this order:
```
./autogen.sh
make
sudo make install
```Restart docky and you should no longer have bold text in your docky menus and tooltips. :D

If you have any problems just tell me, I have not put any dependances as I didn't need any but if someone could tell me what they were missing I could add it to this post.

---

### Post by Islington on 2010-02-24
Requesting this be moved to Tutorials and tips, since more people will see it there. :D

---

### Post by Ubom on 2010-02-24
Ooops, that's what I get for having too many tabs of Ubuntuforums open. Sorry about that.

---

### Post by Ubom on 2010-02-25
Any chance of a mod moving this to the Tutorials section?

---

