---
title: "Ubuntuzilla upgraded Firefox 3.5.2 wont' open PDF files anymore"
date: 2009-08-23
forum: Ubuntuzilla
---

### Post by wdli on 2009-08-23
Hi,
I used ubuntuzilla to upgrade my Firefox to 3.5.2. Now It doesn't open PDF files anymore. What happens after clicking on the PDF icon is a viewer window pops up but seems to hang without anything displayed. 

Same thing if I downloaded the PDF first and tried to view. 

I tried to play with the Applicaition Tab in the Preference but didn't work either.

Can anyone help? 

David

---

### Post by nanotube on 2009-08-24
hi

hmm, that's weird, maybe the pdf you were testing on was weird? have you tested on multiple pdfs from multiple sources?

since ubuntuzilla doesn't do anything to the pdf viewer, my best guess is that the pdf you were testing on was borked.

---

### Post by nomentero on 2009-08-31
I have the same trouble;I went to Firefox--Preferences, selected Applications, scrolled down to "Portable Document Format" and selected my version of Adobe. Now it opens the PDF in Adobe like it used too.

---

### Post by kansasnoob on 2009-09-03
Acroread never has liked me, try:

```
sudo apt-get install --reinstall evince
```

I've found evince to be much better!

---

