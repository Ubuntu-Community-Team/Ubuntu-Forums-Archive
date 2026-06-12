---
title: "Pin_Menu problem"
date: 2006-09-16
forum: Ubuntu System Panel
---

### Post by limaunion on 2006-09-16
Hi there, I've unchecked the pin_menu setting from the gconf-editor. 
My problem with this configuration is that when I click the menu (from gnome's toolbar) and the main USP window is opened if I move the mouse in some way slowly, the USP window is automatically closed before I reach any part of the USP window. I don't know if my explanation is clear, I'm not a native english speaker. How can I solve this problem or impose a delay in order to avoid this ?

One more question, before using USP I used to move the icons that I was interested for from the original gnome menu to my gdesklets starter-bar using a drag & drop style. Now I want to do the same since I want to add an icon to my starter-bar but it seems that USP doesn't support this, right ? Is there any plan to support drag & drop in a future ?
Thanks.
JC

---

### Post by limaunion on 2006-09-16
Thanks in advance for any answer.

---

### Post by chanders on 2006-09-16
Drag and drop is planned for a future release. I understand your problem with the menu. This occurs because you are using follow mouse focus and USP has a 1px space between it and the panel so it loses focus when the mouse is over the space..

I am aware of this problem and it will not be there in the next release (this coming week)..

---

### Post by Uncle Spellbinder on 2006-09-17
> **chanders said:**
> the next release (this coming week)..



=D> \\:D/ :D

---

### Post by limaunion on 2006-09-17
Yes, you're right that I'm using a follow mouse focus style, will wait till next version.

Thanks for your answer and work in USP.
JC.

---

