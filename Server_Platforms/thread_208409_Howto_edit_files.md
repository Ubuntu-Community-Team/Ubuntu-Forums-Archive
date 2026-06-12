---
title: "Howto edit files?"
date: 2006-07-03
forum: Server Platforms
---

### Post by amaab on 2006-07-03
Just installed Ubuntu server and I'm trying to edit the sources.list but don't know how to do that. Is there a edit program or... 
I'm realy stuck her. 

-amaab

---

### Post by jakez on 2006-07-03
sudo vi /etc/apt/sources.list

 with the **i **you can insert data, after inserting data you can save it by pussing the esc-button and then **:wq!**
I'll hope i'm clear enough, otherwise this page might help: [http://xyz.pp.se/~thnov/vi.html](http://xyz.pp.se/~thnov/vi.html)
greetz.

---

### Post by gborzi on 2006-07-03
The default editor in ubuntu is gedit, so to edit sources.list use this command
> sudo gedit /etc/apt/sources.list
AFAIK, gedit is a graphical editor, i.e. you need to use it from an X-window terminal.

---

### Post by amaab on 2006-07-03
Thanks. Used "vi" but how do I save or don't save or exit?

---

### Post by atoponce on 2006-07-03
[quote=amaab]Thanks. Used "vi" but how do I save or don't save or exit?[/quote]
 
To save, hit 'Esc', then ':w'.
To save and exit, hit 'Esc', then ':wq'.
To exit without saving, hit 'Esc', then ':q!'.

All without quotes, of course. :)

---

### Post by jakez on 2006-07-03
save and exit: puss the _esc-button_ and then _:wq!_
exit and don't save: puss the _esc-button_ and then _:q!_

---

### Post by amaab on 2006-07-03
Thanks, worked like a charm.

---

### Post by houstonbofh on 2006-07-03
I know you are done, but for the next poor sap who finds this... :)  "nano" is another simple text editor.  It is also much more intuitive for the new user than vi.  Lastly, it includes a key at the bottom for saves and writes!  *sudo nano /etc/apt/sources.list*

---

