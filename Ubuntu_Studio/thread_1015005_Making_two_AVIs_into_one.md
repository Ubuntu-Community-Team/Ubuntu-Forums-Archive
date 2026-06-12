---
title: "Making two AVIs into one?"
date: 2008-12-18
forum: Ubuntu Studio
---

### Post by jpeery on 2008-12-18
How can I combine two AVI files into one?
Thanks,
JP

---

### Post by unutbu on 2008-12-18
```
sudo apt-get install avidemux
```
File>Open the first avi, File>Append the second.

---

### Post by taurus on 2008-12-18
Or use avimerge.

```
sudo apt-get update
sudo apt-get install transcode
avimerge -o new_file.avi -i first_file.avi second_file.avi
```

---

### Post by jpeery on 2008-12-18
avimerge, that did the trick, thanks!

---

