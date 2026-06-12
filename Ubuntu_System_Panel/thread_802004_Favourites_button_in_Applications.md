---
title: "Favourites button in Applications"
date: 2008-05-21
forum: Ubuntu System Panel
---

### Post by CAE2685 on 2008-05-21
Hello, all. Is there a way for those of us on the other side of the Atlantic to change the spelling of "Favourites" to "Favorites"? I changed the spelling everywhere, in every file I could find that referenced the word, but no luck.

Thanks!

---

### Post by Malac on 2008-05-22
> **CAE2685 said:**
> Hello, all. Is there a way for those of us on the other side of the Atlantic to change the spelling of "Favourites" to "Favorites"? I changed the spelling everywhere, in every file I could find that referenced the word, but no luck.
 
Thanks!
Localisation isn't available at the moment but I will put this on my list too.
 
I think this is setup from applications.glade file, try opening that in gedit and replace all then save, if not try same thing on applications.py.
 
Hope this helps.

---

### Post by CAE2685 on 2008-05-22
I searched for "favourite" in every .glade and .py file, and changed every instance to the American spelling... no luck. 

Oh, well. I guess I'll have to read English the English way for a bit :-P

---

### Post by Malac on 2008-05-22
> **CAE2685 said:**
> I searched for "favourite" in every .glade and .py file, and changed every instance to the American spelling... no luck.
Be careful doing this as some functions are also called xxxxxx_favourites or similar.

This is definitely in the applications.glade file, I'm looking at it now.
```
sudo gedit /usr/lib/python2.4/site-packages/usp/plugins/applications.glade
```Line 34:
```
<property name="label" translatable="yes">&lt;span weight="bold"&gt;**Favourites**&lt;/span&gt;</property>
```Line 188:
```
<property name="label" translatable="yes">&lt;span size="small"&gt;**Favourites**&lt;/span&gt;</property>
```Line 672:
```
<property name="label" translatable="yes">Add to **favourites**</property>
```Line 840:
```
<property name="label" translatable="yes">Remember Last Shown [Applications/**Favourites**]</property>
```This won't appear in the menu unless you reboot or even, failing that working, try remove/add USP to panel after making changes.

Hope this helps.

P.S. Keep a note of these line numbers as you will need to make the change every time you update.

---

