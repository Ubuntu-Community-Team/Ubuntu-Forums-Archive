---
title: "I downloaded 1 file. It copied 2 files automatically?"
date: 2022-04-16
forum: Ubuntu/Debian BASED
---

### Post by f23948 on 2022-04-16
Please I would like to know why it creates 2 files automatically? I am using Ubuntu 20.04 LTS and latest version Firefox ESR
[https://www.youtube.com/watch?v=nvHqJ1QPneU](https://www.youtube.com/watch?v=nvHqJ1QPneU)

---

### Post by &amp;KyT$0P# on 2022-04-16
Firefox creates the destination file where the download will eventually go, but then does the actual downloading to a separate file with name ending in .part.  Only when the download is complete does Firefox actually write the requested destination file (and remove the .part file).  After the download is completed you should have only the 1 expected file.

---

### Post by #&amp;thj^% on 2022-04-16
Type **about:config** into the location bar and press enter
Accept the warning message that appears, you will be taken to a list of preferences
In the filter box type **browser.download** to bring up a small number of preferences >> then check "**browser.download.folderList**"
it should only be set to 1
also clear your Download cache, see if it persists.

---

### Post by f23948 on 2022-04-16
I haven't go to about:config page yet.

After downloaded completed, it's stll showing
[https://www.youtube.com/watch?v=EGN7mg64UKU](https://www.youtube.com/watch?v=EGN7mg64UKU)

---

### Post by f23948 on 2022-04-16
In Linux Linux, after downloaded completed, it delete part file automatically. I am using Linux Lite 5.8 based on Ubuntu 20.04 LTS and latest version Firefox ESR
[https://www.youtube.com/watch?v=n5zHy0yNS3M](https://www.youtube.com/watch?v=n5zHy0yNS3M)

---

### Post by &amp;KyT$0P# on 2022-04-16
> **f23948 said:**
> After downloaded completed, it's stll showing

Does it show also if you right-click the desktop > "Show Desktop in Files"?
Is there some way to "refresh" the desktop display of files?

---

### Post by f23948 on 2022-04-16
> **halogen2 said:**
> Does it show also if you right-click the desktop > "Show Desktop in Files"?
Is there some way to "refresh" the desktop display of files?

[https://www.youtube.com/watch?v=aK_cJggLV9Q](https://www.youtube.com/watch?v=aK_cJggLV9Q)

---

### Post by wildmanne39 on 2022-04-16
Moved to Ubuntu/Debian BASED.

---

### Post by f23948 on 2022-04-16
update:
[https://www.youtube.com/watch?v=kfRMrUlawys](https://www.youtube.com/watch?v=kfRMrUlawys)

---

### Post by Claus7 on 2022-04-17
Hello,

I would like to verify that it is not only Ubuntu/Debian BASED, yet ubuntu specific as well: in my case, under ubuntu flashback, I 'm getting lately 3 copies, instead of 2 of the same file. One of the copies of the file has .download ending in its name, the others are as normal. This has taken place for a long time now. If I recall correctly, it started with 2 copies and now it shows 3. As the OP, when I open nautilus, only one copy of the file is shown. If I try to get rid of all the copies, a message appears to skip deleting 2/3 files because they cannot be deleted. If I log out and back in, they disappear from desktop.

I have not figured out a workaround for this issue. I attach a screenshot for a test pdf file.
[ATTACH=CONFIG]290296[/ATTACH]
Regards!

---

### Post by Claus7 on 2022-04-24
Hello,

using nemo desktop though under flashback, this problem vanishes. I do not face such a problem using regular ubuntu as the OP. I guess that since regular ubuntu uses extensions for handling desktop icons, changing the extension or removing it and placing it back anew might solve the problem.

Regards!

---

### Post by Claus7 on 2022-04-24
posted double, it can be deleted

---

