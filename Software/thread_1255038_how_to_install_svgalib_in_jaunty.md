---
title: "how to install svgalib in jaunty"
date: 2009-09-01
forum: Software
---

### Post by suryakumar on 2009-09-01
i am using linux 9.04. i want to install svgalib. every time i give the command "make install" it gives the error message:"cannot create regular file `/usr/local/include/vga.h': Permission denied"....how can i resolve this problem?

---

### Post by Carlos C on 2009-09-01
you can try with "sudo make install".

---

### Post by stumbleUpon on 2009-09-01
svgalib is in the repositories. Install it with

```
sudo aptitude install svgalib-bin 
```

---

