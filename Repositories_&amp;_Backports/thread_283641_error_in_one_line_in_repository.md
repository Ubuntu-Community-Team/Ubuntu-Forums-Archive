---
title: "error in one line in repository"
date: 2006-10-24
forum: Repositories &amp; Backports
---

### Post by yolloms on 2006-10-24
i went to click on my update button and i got an error.
i get it when opening synaptic package manager.

this is the error
E: Type 'http' is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


any ideas how i fix it

---

### Post by woedend on 2006-10-24
open terminal, do
gksudo gedit /etc/apt/sources.list

go to line 33(at the bottom, line number is indicated in gedit to make this easy...it say ln X, with X being the line number)...im guessing they left the word "deb" off the front of the line.  Every line should start with deb or deb-src.  save, then refresh synaptic.

---

### Post by yolloms on 2006-10-25
thanks. it was just a line in there that 'http' on it and nothing else

---

