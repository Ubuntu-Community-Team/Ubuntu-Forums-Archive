---
title: "Quickly (program) development for different OSes"
date: 2013-04-11
forum: Ubuntu Application Development
---

### Post by gameguy on 2013-04-11
I am just about to start work on a program that I wanted to make, and was planning to use quickly. However, I would also like to release this program for Windows (and mac, if it's no extra effort). I'm not sure whether quickly will allow to develop for windows. Could someone confirm whether it works for Windows, and if it doesn't, does anyone have any suggestions. I am happy to use Python, C++, or C (in that order of preference) to develop the application, and need  something like glade to develop the UI.

Thanks

---

### Post by karlhaines on 2013-06-21
Just make sure that all OSes you're hoping to support are able to use the language you chose to build the application in. Python would be a good choice. You can use Glade to develop the user interface, and then use a GtkBuilder object in your code to load the XML that Glade produced into your new application. Hope this helps. Let me know if you have any other questions, and I would be glad to help!

---

