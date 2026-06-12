---
title: "Looking for VB alternative"
date: 2009-11-11
forum: The Cafe
---

### Post by cdahmedeh on 2009-11-11
Hello,

I'm looking for an alternative to Visual Basic. I'm not looking for a clone, just something that will let me make programs in a BASIC type language. Gambas was really close, but the Qt3 interface really threw me off because it doesn't blend well with my GTK+ apps. MonoDevelop isn't an option because it lacks an interface designer for VB.net. 

So basically, I'm looking for :
-Uses BASIC type language like VB and VB.net
-Has a good interface designer.
-Uses a GTK+ interface for its IDE.
-Ideally, it should be in the Ubuntu repos or have a PPA.

Thanks

---

### Post by t0p on 2009-11-11
If you want a BASIC-type language, check out [FreeBASIC]("http://www.freebasic.net").  It's BASIC, and it's free.  What more could one want?

---

### Post by cdahmedeh on 2009-11-11
It doesn't have an interface designer for GTK+ nor a IDE for it. It's not what I'm looking for. FreeBASIC is just a compiler, I'm looking for a bit more than that, like I listed previously.

---

### Post by Tibuda on 2009-11-11
VB.NET in MonoDevelop?

---

### Post by cdahmedeh on 2009-11-11
> **cdahmedeh said:**
> Hello,

... MonoDevelop isn't an option because it lacks an interface designer for VB.net. ...

I already said that MonoDevelop isn't an option. It has no interface designer for VB.net, only C#. However, I'm also willing to learn Python. All I'm looking for is 'just for fun' programming. Something that let's me design an interface with the mouse, do some simple programming like in VB.net and that's it.

So what could be my option. Again, a GTK+ interface for the IDE. Remember, I'm not just looking for a compiler, but also a good interface for that compiler. 

Thanks Again

---

### Post by kalaharix on 2009-11-13
Hi

Gambas can use either GTK or QT. It is a choice when you define the project. That said the ide itself (written in Gambas) uses QT so it still may not suit you. 

rgds

---

### Post by Johnsie on 2009-11-13
I liked Gambas. I don't think there's a VB-like IDE for Linux that is as good as VB itself, but for rapid application development Gambas is pretty good.

---

### Post by hessiess on 2009-11-13
Python + any text editor. IDE's are pointless.

---

### Post by Nevon on 2009-11-13
Python + GtkBuilder will allow you to use whatever IDE you want, coupled with Glade as a visual interface designer.

---

### Post by t0p on 2009-11-13
> **hessiess said:**
> Python + any text editor. IDE's are pointless.


*We* may think IDEs are pointless, but the OP would disagree.  If he didn't value a pretty user interface so highly, my suggestion to use FreeBASIC may have met a better reception.  After all, FreeBASIC *is* BASIC - which is what the OP wants.

I know a lot of computer users feel they can't function without a GUI; so I shan't criticize the OP for that.  I'll just point out that Python has a nice IDE: **IDLE**.  I think it's in the repos.

```
sudo apt-get install idle
```At the end of the day, a text editor is just as good (Gedit does syntax-related highlighting and stuff for Python).  But IDLE has some of that integrated functionality and buttons to click that the OP needs.

---

### Post by mmix on 2009-11-13
your choice is only gambas latest version

[quote="[2.17.0 - 25 Oct 2009](http://gambas.sourceforge.net/en/main.html)"]
    *  BUG: The name property of newly created menus is correctly initialized now.
    * BUG: Changing the value of the Sorted property in TreeView, ColumnView, ListView and ListBox does not crash anymore.
    * BUG: Fix input method handling.
    * BUG: Do not crash when there is a keyboard event and no active control.
    * BUG: Using the quality argument when saving a picture or an image does not crash anymore.
    * BUG: Sorted editable combo-box correctly raise the Click event if their first item is selected.
    * BUG: Fix the behaviour of ComboBox again, so that it behaves the same way as in gb.qt.
    * BUG: TextBox.Insert() correctly deletes the selected text before inserting the new one.
    * BUG: Really fix the initialization of file dialog from Dialog.Path in the Dialog.Save() method.
    * NEW: Thanks to an hack based on a global event handler, disabled controls now answer events like in gb.qt.
    * NEW: Application_KeyPress global event handler has been implemented. 
[/quote]

---

### Post by forrestcupp on 2009-11-13
If you're willing to learn a different language, like Python, why not just learn C# and have exactly what you need with Mono?  Just because it has "C" in the name doesn't mean that it's hard.  C# is a great language, and it's not really any harder to learn than Python.

> **t0p said:**
> 
I know a lot of computer users feel they can't function without a GUI; so I shan't criticize the OP for that.
There is a third group of computer users who *can* function without a GUI, but we just don't want to because we live in the 21st century.  I could function with an old black and white tube TV, but I like my HDTV pretty well.

---

### Post by directhex on 2009-11-13
Or design your GUI manually, or with Glade or equiv (the way you'd be forced to with Python), rather than having the designer built into your GUI?

---

### Post by cdahmedeh on 2009-11-13
After lots of research, I have found Lazarus. It's based on FreePascal which is a very nice language. I am learning it right now and having a good time. It's not as easy as VB, but more flexible, and less scary than let's say C++. The best part, it's multiplatform, so everyone can enjoy my little useless apps !

Thanks for the suggestions though.

---

