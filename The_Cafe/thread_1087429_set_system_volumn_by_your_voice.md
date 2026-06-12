---
title: "set system volumn by your voice"
date: 2009-03-05
forum: The Cafe
---

### Post by eexpress on 2009-03-05
setup your hotkey to active the bash

```
2009-03-05 13:47:12 &#22235; ~  
&#9742; g set-volum ~/.fvwm/f.action
Key v A 4 Exec set-volumn-by-record.bash
```

within 2 second after execute, you make some voice, loud or weak, then the script would change system volumn.
```
2009-03-05 13:47:30 &#22235; ~  
&#9742; dog set-volumn-by-record.bash
arecord -d 2 -t wav|lame - /tmp/sound.mp3
g=`mp3gain /tmp/sound.mp3|tail -n 1|cut -d'-' -f 2`0%
amixer set PCM $g
amixer set Master $g

```

---

