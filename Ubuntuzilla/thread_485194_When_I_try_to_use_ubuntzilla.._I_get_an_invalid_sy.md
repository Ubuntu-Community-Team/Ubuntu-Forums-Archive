---
title: "When I try to use ubuntzilla.. I get an invalid syntax error."
date: 2007-06-26
forum: Ubuntuzilla
---

### Post by Depressed Man on 2007-06-26
vforviktor@vendetta:~$ python ~/ubuntuzilla.py -a installupdater -p thunderbird
  File "/home/vforviktor/ubuntuzilla.py", line 1
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    ^
SyntaxError: invalid syntax
vforviktor@vendetta:~$

---

### Post by nanotube on 2007-06-26
> **Depressed Man said:**
> vforviktor@vendetta:~$ python ~/ubuntuzilla.py -a installupdater -p thunderbird
  File "/home/vforviktor/ubuntuzilla.py", line 1
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    ^
SyntaxError: invalid syntax
vforviktor@vendetta:~$

hi,
that line (<doctype stuff) does not exist in ubuntuzilla.py
you must have dowloaded an incorrect file, or it got screwed up by your browser... go to the ubuntuzilla homepage (link in my sig), and get the latest ubuntuzilla.py from the sourceforge fileservers, and try again.

actually, for your convenience, here's a direct link to download the latest:
[http://easynews.dl.sourceforge.net/sourceforge/pykeylogger/ubuntuzilla_4.1.1.py](http://easynews.dl.sourceforge.net/sourceforge/pykeylogger/ubuntuzilla_4.1.1.py)

ok, try that, and please report how it goes. :)

---

### Post by Depressed Man on 2007-06-27
Thanks it works! I seem to have downloaded the first one from the Wiki..usually it worked for me. Though I guess not this time lol. Thanks for the help!

---

### Post by nanotube on 2007-06-27
> **Depressed Man said:**
> Thanks it works! I seem to have downloaded the first one from the Wiki..usually it worked for me. Though I guess not this time lol. Thanks for the help!

hi,
aha, i see, i'm guessing you right clicked on the link and chose "save as"... but the link now links to the sourceforge fileserver page, where you can select a file for download, it doesn't point directly to the actual file.
anyway, glad it all worked out. :)

---

