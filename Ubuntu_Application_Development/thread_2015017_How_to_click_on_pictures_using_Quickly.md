---
title: "How to click on pictures using Quickly"
date: 2012-07-02
forum: Ubuntu Application Development
---

### Post by Tiddens on 2012-07-02
Is there a way to make pictures "clickable"?  I'm willing to revise the Python or Glade code directly if needed (although I am just starting to learn).  As an alternative, I've tried to use a Button, but there doesn't seem to be a way to put a picture on the Button?  Under General it says "Label with optional image", but there doesn't seem to be an option to use an "optional image" -- only to use text.  Guess I could try to add all of my images to the "Stock Button" images somehow, but I would prefer to just make pictures clickable.

---

### Post by diesch on 2012-07-02
In Glade create a button, Then on the button's properties go to the "General" tab, scroll down and activate "Add custom button content". Now place an Image widget inside the button and make it display whatever picture you want.

---

### Post by Tiddens on 2012-07-02
Thank you for the fast response!  This is embarrassing because I just didn't scroll down far enough to see the option.  I hate the new Unity scroll bars, and it's not so obvious if you have scrolled to the bottom!  I turned them off on my other machine...

---

