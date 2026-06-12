---
title: "linbread: daily bible verse when login"
date: 2009-06-25
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-06-25
I have found linbread [here]("http://thelinuxlink.net/l4c/programs.html"), but it is only to be run in terminal, no gui interface.

I edit the script a little, replacing gawk with awk (as awk shipped with ubuntu but not gawk), and also add gui.

Now it could use to display bible verse every login, just add it on startup application. The resulting package is very small, just 30 kb packaged, or 100 kb installed.

I will add this package to ubuntu-ce metapackage as well.

I also found verse in ubuntu repository, but it is also meant to use in terminal, either command line or dialog. Even worse, dialog is not included in standard ubuntu so as it will pull additional software.

So, this repackage linbread should be far superior than verse. You could download it [here]("http://ubuntuforums.org/attachment.php?attachmentid=118888&stc=1&d=1245909170").

DK

---

### Post by jonathonblake on 2009-07-03
> **david_kt said:**
> 
I also found verse in ubuntu repository,

gverse can be found at  [http://sourceforge.net/projects/gverse/](http://sourceforge.net/projects/gverse/)
That is the Gnome GUI for verse.

jonathon

---

### Post by Wiebelhaus on 2009-07-03
Thanks! That's awesome.

---

### Post by david_kt on 2009-07-03
> **jonathonblake said:**
> gverse can be found at  [http://sourceforge.net/projects/gverse/](http://sourceforge.net/projects/gverse/)
That is the Gnome GUI for verse.

jonathon

Thanks. But the problem with verse and gverse is I could not find the code. I still could pack it in debian, but I would prefer if I could see the source code before I pack it.

DK
Edit: I have found source code for verse. I appreciate if someone could show me the source code for gverse. Anyway, this would be a duplication of linbread, so I will include either gverse or linbread, but not both.

---

### Post by eldews on 2009-10-17
What do I type or how do I add linbread to Preferences > Startup applications? I click on 'Add' and it asks for  Name:   Command:   Comment:

I would like linbread to appear automatically when I log in.

Thanks

---

### Post by david_kt on 2009-10-17
> **eldews said:**
> What do I type or how do I add linbread to Preferences > Startup applications? I click on 'Add' and it asks for  Name:   Command:   Comment:

I would like linbread to appear automatically when I log in.

Thanks

Command: linbread
Name and comment whatever you like

DK

---

### Post by user333 on 2009-10-17
:) I couldn't get another program just like this to work, but I really wanted it. Thanks a lot!
um... how did you do the attachment? :confused:

---

### Post by david_kt on 2009-10-17
> **user333 said:**
> :) I couldn't get another program just like this to work, but I really wanted it.

What is the program?

> **user333 said:**
> um... how did you do the attachment? :confused:

What attachment and where?
Edit: I think what you meant was attachment on this forum. Just click "Manage Attachments" button and follow the instruction. If there is no "manage attachments" button, click "go advance".

DK

---

