---
title: "web hosting question"
date: 2011-02-27
forum: Server Platforms
---

### Post by ex_isp on 2011-02-27
Let's say you just purchased 250 web hosting clients from "Joe's  Hosting" and you've moved them all over to your servers.. and there's  only one thing left to do..

At the bottom of **200** of the 250 websites that Joe created there's a couple lines you'd like to replace:

**Host At Joe's!**
**Proudly hosted by Joe's Hosting**

You'd like to replace it with:

**Hosted by Sam's Internet**
**Visit: [www.SamsInternet.com]("http://www.samsinternet.com/")**

All of the sites live in /home/joes/hosting/
They're all a mismatch of different types of sites - so the footers will be in different filenames..

How would this best be solved?

---

### Post by aeiah on 2011-02-28
there are loads of ways to do this, obviously. a quick google turned up [this discussion](http://forums.devshed.com/unix-help-35/unix-find-and-replace-text-within-all-files-within-a-146179.html)

so you could use perl and do ```

perl -e "s/FIND/REPLACE/g;" -pi.save $(find path/to/DIRECTORY -type f)

```

now i dont know perl.. i dont know if '-type f' means it'll only search text based files or if you may run into problems when it tries to search through images, for example.

it goes without saying that whatever you do, make sure you have a backup before blasting through 200 client websites :p

---

### Post by SeijiSensei on 2011-02-28
[http://ubuntuforums.org/showthread.php?t=1683766](http://ubuntuforums.org/showthread.php?t=1683766)

---

### Post by ex_isp on 2011-02-28
Great info guys!  Thanks as always!

---

