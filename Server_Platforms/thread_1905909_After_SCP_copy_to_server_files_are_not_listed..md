---
title: "After SCP copy to server files are not listed."
date: 2012-01-07
forum: Server Platforms
---

### Post by frankjath on 2012-01-07
Hi I need help. I used "SCP copy command to copy a zip file via SSH to my Ubuntu server from my mac. However after it says it successfully uploaded the file I navigate to the directory where I uploaded the file I use "ls" command to list whats in that directory but the file is not listed. I have also used "pwd" command while in the directory to get it's full path to make sure I putting the file in the right directory. Help would be much appreciated as to why the file isn't showing up.

---

### Post by jsra on 2012-01-08
Hi,
are you sure that you set the destination correctly? Maybe you cold post the command itself.
Also you can try:
```
sudo ls -a
```

jsra

---

### Post by doas777 on 2012-01-08
could you please post the copy command you used, and '**ls -al**' as jsra suggested?
are you using the same user for both your scp and your 'ls'?

---

### Post by frankjath on 2012-01-08
Thanks so much for the reply but I figured it out. It was a permission problem with that directory. I instead uploaded my files to a new directory and then used "CP" to copy the files over.

---

