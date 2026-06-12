---
title: "Behaviour of the &quot;New&quot; menu item in Leafpad"
date: 2013-01-04
forum: The Cafe
---

### Post by purjuntu on 2013-01-04
Are there any plans to normalize Leafpad's strange behaviour when choosing "New" in the File menu?

All normal editors give a blank page in the current window. But Leafpad opens a new window with a blank page. This is the most annoying thing I've encountered in LXDE.

Yes, I could just close the old window, but then the windows won't be in the intended order anymore, and I will have to search around for the correct window each time I'm moving to another of the open documents.

And yes, I could download gedit (and I did) but it doesn't fit my colour scheme (menu items being black on black in gedit).

Any plans to normalize Leafpad? Or does somebody know why they have made the editor behave so strangely?


I intended to ask this on the LXDE forum, but it was impossible to register.

---

### Post by Gremlinzzz on 2013-01-06
:popcorn:Why is it impossible to register? 

[http://forum.lxde.org/ucp.php?mode=register&sid=f386e60bfa1291123eeafa6063c0f787](http://forum.lxde.org/ucp.php?mode=register&sid=f386e60bfa1291123eeafa6063c0f787)

---

### Post by vasa1 on 2013-01-06
> **purjuntu said:**
> Are there any plans to normalize Leafpad's strange behaviour when choosing "New" in the File menu?

All normal editors give a blank page in the current window. But Leafpad opens a new window with a blank page. ...

In other words, you want Leafpad to provide tabbed Windows?

---

### Post by Copper Bezel on 2013-01-06
Well, no - some some other editors close the current file and open a new one, so he's probably hoping for something like that. (I don't think that that behavior is useful or consistent, and I think the current behavior makes the most sense, because it's simply creating a new document, without additionally closing the current one. But I'm guessing that that's what he means. MS Notepad does this, I think. Apps like LibreOffice or Gimp don't, of course.)

---

### Post by vasa1 on 2013-01-06
> **Copper Bezel said:**
> ... But I'm guessing that that's what he means ...
We'll wait patiently for a clarification :)

---

### Post by purjuntu on 2013-01-20
Thank you for your answers.

To Copper Bezel and Vasa1:
Yes, that's just what I would have wished for; the good old MS Notepad way of closing the current file and replacing it with a blank page.
I thought this was the normal way of functioning, and that Leafpad was an exception.
But maybe it is rather MS Notepad which is the exception. OK.

To Gremlinzzz:
It was impossible to register, because it always said that my answers were incorrect, although I'm pretty sure they weren't.
I answered "File Roller" to the question about which archiver is used in LXDE.
And I answered "Audacious" to the question about the music player.
Still it kept saying that my answers were incorrect.
But now I got my answers here instead.

---

### Post by Copper Bezel on 2013-01-20
> I thought this was the normal way of functioning, and that Leafpad was an exception.
But maybe it is rather MS Notepad which is the exception. OK.
I think it was the typical behavior at the time MS Notepad was first released. Since then, there was that shift to MDIs, and then to a Macish the-window-is-the-document trend while other apps took on tabs instead of full MDIs. (And now most mobile and and web apps have gone straight back to one-document-at-a-time like Notepad. Oy.)

---

### Post by purjuntu on 2013-03-08
I happened to find the perfect solution!
 Ctrl+W does exactly what I want; closing the document but not the window.
So one can have the best of two worlds. Linux, but with a Notepad-ish editor.

---

