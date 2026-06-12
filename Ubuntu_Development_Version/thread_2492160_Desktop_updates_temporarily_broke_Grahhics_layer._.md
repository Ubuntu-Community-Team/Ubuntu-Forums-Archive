---
title: "Desktop updates temporarily broke Grahhics layer. (work-around)"
date: 2023-11-01
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2023-11-01
Yesterday there was 82 updates for Noble Desktop and 42 for Noble Server... The server updates were fine.

The updates from late yesterday broke the graphics layer for Noble Desktop. So when you reboot from those, it goes to GDM3 fine, but from there to the desktop, it will be a blackscreen.

If you do <Cntrl><Alt><F4> to toggle to vtty4, log in, and apply this morning's updates > reboot... Then the graphics layer is fine again. 

I think it was just a sync problem between the staged update packages.

If you didn't get those late updates, from yesterday, you will get all those packages at once this morning, you will not be affected, and not even notice. LOL

---

