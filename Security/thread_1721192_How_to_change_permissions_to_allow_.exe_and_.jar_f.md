---
title: "How to change permissions to allow .exe and .jar files?"
date: 2011-04-04
forum: Security
---

### Post by Awzold on 2011-04-04
Hello, I've been using Ubuntu for a few years, but I am still a noob, and I am having issues trying to load .jar files and .exe files in Wine. I keep getting an error message that says my computer doesn't have permission to load these files. I've done some research and found people saying to enable the file as executable in the files properties, to enable executable in the permissions folder, and to allow source code on the Ubuntu Software screen, but whenever I try to check these boxes, they immediately revert to having a line through them instead.  I remember when I was running Ubuntu a few years ago I was able to completely disable this restriction in terminal, but I can't remember what I did. Can someone please help me?

---

### Post by vlaar on 2011-04-04
> **Awzold said:**
> Hello, I've been using Ubuntu for a few years, but I am still a noob, and I am having issues trying to load .jar files and .exe files in Wine. I keep getting an error message that says my computer doesn't have permission to load these files. I've done some research and found people saying to enable the file as executable in the files properties, to enable executable in the permissions folder, and to allow source code on the Ubuntu Software screen, but whenever I try to check these boxes, they immediately revert to having a line through them instead.  I remember when I was running Ubuntu a few years ago I was able to completely disable this restriction in terminal, but I can't remember what I did. Can someone please help me?

for setting a file as executable:
sudo chmod +x filename

to set permissions in wine (not a wine user myself) I bet you have to start wine as super-user.

---

### Post by Morbius1 on 2011-04-04
*exe and *.jar files both fall prey to something called "cautious launcher". What it does is checks to see if the file has a Linux executable bit set before it allows Wine or Java to execute it. It has nothing to do with Wine or Java itself.

To remedy this just circumvent "cautious-launcher" with your own file association:

_Wine_
Open Nautilus and right click an *.exe file. Then select Properties  -> Open With -> Add -> Use a custom command > Then type in:  [COLOR=Blue]**wine**[/COLOR]
Back in the "Open With" tab mark the "wine" [COLOR=#0000ff]you just added[/COLOR] as the default.

_Java_
Open Nautilus and right click an *.jar file. Then select Properties  -> Open With -> Add -> Use a custom command > Then type in:  [COLOR=Blue]**java -jar**[/COLOR]
Back in the "Open With" tab mark the "java" [COLOR=#0000ff]you just added[/COLOR] as the default.

---

### Post by IWantFroyo on 2011-04-04
```
sudo chmod +x filename
```I second vlaar's post.

---

### Post by Morbius1 on 2011-04-04
The only problem with a "chmod +x" is that it won't work on an NTFS or Fat32 partition or on a CD. Besides, Wine for example doesn't care if it has a Linux executable bit set. Wine itself is incapable of determining if a file has a Linux executable bit set.

Doing the following in a terminal will work because it bypasses "cautious-launcher":
```
wine /path/to/exe/file
java -jar /path/to/jar/file

```

---

### Post by monko909 on 2011-06-18
If you install NTFS-Config and give yourself read/write permissions, that should do it.

---

