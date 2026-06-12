---
title: "Unknown command “setup.py” error in Raspberry"
date: 2018-09-17
forum: Ubuntu/Debian BASED
---

### Post by itechstr on 2018-09-17
I was installing this github project on my Raspberry Pi 3B+ and I keep getting the same error.




> (cv) pi@raspberrypi:~/Camerafeed $ pip setup.py develop
>
> ERROR: unknown command "setup.py"




I have pip installed already. Reply asap you find a solution
Thanks in advance.

---

### Post by joegry on 2018-09-19
Hello.  It looks like it's not able to find the setup.py file.  Try running that command from the directory that contains setup.py.  Or if you really want to run the command from ~/Camerafeed/ you can try $ pip /full/directorypath/to/setup.py develop

---

