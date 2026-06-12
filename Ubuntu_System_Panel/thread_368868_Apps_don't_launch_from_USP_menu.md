---
title: "Apps don't launch from USP menu"
date: 2007-02-23
forum: Ubuntu System Panel
---

### Post by Jolly Roger on 2007-02-23
My USP is all setup and everything went well with the setup but when I tried to start an application from the menu nothing happens. I click on it and nothing ever opens up. The places menu will open up the places I click on. Clicking the power button will open the shutdown dialog. But the applications plugin doesn't open any applications. I ran USP in window and I get this error:

TypeError: ButtonReleased() takes exactly 5 arguments (4 given)

I'm using Edgy by the way.

Could anyone help me? Thanks!

EDIT: Also, how do I set favorite applications? My favorites list is empty and I can't figure out how to populate it.

---

### Post by Mateo on 2007-02-23
To set favorites right click on the application and it'll say set favorite (or something like that, can't recall).

Are you using USP1 or the alpha of SVN?

---

### Post by Malac on 2007-02-24
> **Jolly Roger said:**
> My USP is all setup and everything went well with the setup but when I tried to start an application from the menu nothing happens. I click on it and nothing ever opens up. The places menu will open up the places I click on. Clicking the power button will open the shutdown dialog. But the applications plugin doesn't open any applications. I ran USP in window and I get this error:

TypeError: ButtonReleased() takes exactly 5 arguments (4 given)

I'm using Edgy by the way.

Could anyone help me? Thanks!

EDIT: Also, how do I set favorite applications? My favorites list is empty and I can't figure out how to populate it.
This looks like you are using an out of date version of the SVN. This was a bug introduced by trying to allow launch in terminal apps to function (around Revision 141 I think) but was solved in later revisions.
You need to run usp_update update it should tell you that the revision is 161 as of today.
Right-click on the application and choose [Add to favourites] once you have updated.

---

### Post by Jolly Roger on 2007-02-24
Thanks! That fixed all the problems.

---

### Post by Malac on 2007-02-24
> **Jolly Roger said:**
> Thanks! That fixed all the problems.
You're welcome.
Could you mark this thread as [SOLVED] please. That way anyone with similar problems knows to read this one. Thanks.

---

