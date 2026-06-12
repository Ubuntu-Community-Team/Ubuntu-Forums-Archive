---
title: "smaller file gets bigger when compressed"
date: 2019-09-19
forum: The Cafe
---

### Post by Skaperen on 2019-09-19
i have a large python file with some rather wide divider bars as comments.  they are all 160 characters wide and no source lines come anywhere close to that wide.  so i checked the width of the file with those comments removed.  125.  so i trimmed the width of the file to 128 characters.  for fun i decided to cut the width in steps of 8 and compress each (160, 152, 144, 136, 128).   i used "xz -9" to do the compression, the original sizes are: 50462, 49847, 49231, 48615, 47999.  the compressed sizes are: 9876, 9880, 9876, 9876, 9860.  the 2nd file is smaller but its compressed file is larger.  then the 3rd and 4th compressed files are the same size as the 1st.  is this odd?

that python file can be seen [here]("http://ipal.net/xfce/sfc.py") in the original width.

---

