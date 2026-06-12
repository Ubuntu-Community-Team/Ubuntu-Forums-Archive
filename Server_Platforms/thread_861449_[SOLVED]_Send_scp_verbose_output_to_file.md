---
title: "[SOLVED] Send scp verbose output to file"
date: 2008-07-16
forum: Server Platforms
---

### Post by gniltaws on 2008-07-16
As part of a backup procedure I am trying to send the verbose output of scp (scp -v) to a text file.  I know that normally, one would accomplish this by entering: ```
scp -v file1 file2 >> output.txt
``` For some reason it does not work with scp.  The above will create a new document called output.txt, but it is blank.  I don't think this should matter, but I'm working on Fedora 9.  Thanks in advance.

---

### Post by RealPSL on 2008-07-16
Have you tried

```
scp -v file1 file2 2>&1 >> output.txt
```

---

### Post by gniltaws on 2008-07-17
I hadn't tried that, but it does not work either.  The output shows on the screen, but I still have a blank output.txt.

---

### Post by RealPSL on 2008-07-17
Oops other way around:

```
scp -v myfile myfile2  > output.txt 2>&1
```

---

### Post by gniltaws on 2008-07-18
It's working perfectly! Thanks.

---

### Post by MJN on 2008-07-18
The key point here is that with your original configuration you were only redirecting the 'standard' output to a file whereas what you were seeing on-screen was your 'error' output. RealPSL's solution redirected both to file.

Mathew

---

