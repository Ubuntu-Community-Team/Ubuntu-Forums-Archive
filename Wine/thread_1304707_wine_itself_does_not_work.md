---
title: "wine itself does not work"
date: 2009-10-29
forum: Wine
---

### Post by wlraider70 on 2009-10-29
So I can't get wine to work. 

I just installed it and went to Applications > wine > configure wine.

NOTHING.

I clicked on a windows .exe 

NOTHING.



I tried an older version and a reinstall i don't know what else to do?
Can you tell me where to start.


ps. the pre-installed notepad, you guessed it nothing.

---

### Post by beastrace91 on 2009-10-29
Can you open terminal and post the output of ```
wine --version
```

Also how did you install wine? Could you also use terminal to try to launch an exe via Wine for example: ```
wine myprogram.exe
``` and post what it out puts from trying this?

Thanks,
~Jeff

---

### Post by wlraider70 on 2009-10-29
I figured it out.

I was connecting to the box via VNC, which has NEVER caused an issue except sometimes a slow response.

I used a cli command for the wine config and that gave me a reply regarding X. 

so i went to the box and it worked just fine. I don't really get why it worked like that?

---

