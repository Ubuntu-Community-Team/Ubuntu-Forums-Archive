---
title: "Editing my /etc/network/interfaces to obtain a static IP"
date: 2010-01-25
forum: Server Platforms
---

### Post by terrapin893 on 2010-01-25
So I cant figure out how to edit and save this file using Vim-noX. (connected via putty)

I have the file loaded up and Ive inputed the needed data for my static IP, but I cant for the life of me figure out how to close and save my settings.  At the bottom of the command line I have "INSERT" which toggles with "REPLACE" and I just cant figure this out.  

Help would be much appreciated, so I can move past this barrier.

---

### Post by stlsaint on 2010-01-25
assuming you are referring to Vim...

1. Open document in vim
2. Press i to insert data
3. When ready to save use hit: ESC (this will drop the cursor down to bottom left of screen)
4. hit, :w (and give it path of saving with name...so...
:w /home/terrapin/Desktop/nameoffile
5. Enter

to close use 
:q

---

### Post by terrapin893 on 2010-01-25
OK, so I did insufficient research.  My apologizes.  

[http://www.unix-manuals.com/tutorials/vi/vi-in-10-1.html](http://www.unix-manuals.com/tutorials/vi/vi-in-10-1.html)

[http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)

:rolleyes:

---

