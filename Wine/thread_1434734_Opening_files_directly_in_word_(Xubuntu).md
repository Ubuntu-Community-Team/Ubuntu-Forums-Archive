---
title: "Opening files directly in word (Xubuntu)"
date: 2010-03-20
forum: Wine
---

### Post by tehMalone on 2010-03-20
Hi, I'm pretty new at linux. I've installed Ms Office through Wine, and it runs pretty smoothly. But I can't open files by doubleclicking them, because it treats every space ' ' as the end of the file path. I've looked around, and can't find a solution. Found this script that i've tried, and chmod'ed, but it does nothing apparently:

```
#!/bin/bash
COMMAND=`echo $* | sed -e s#\/#\\\\\\\#g`
if [ ${COMMAND} ]; then
COMMAND='Z:'$COMMAND
fi
sudo wine "C:\Program Files\Microsoft Office\OFFICE12\WINWORD.EXE" "${COMMAND}" 
```

please help :)

---

