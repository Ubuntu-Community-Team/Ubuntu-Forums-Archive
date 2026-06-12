---
title: "Installed Wine, but I can't find it anywhere"
date: 2010-09-27
forum: Wine
---

### Post by Can Fly on 2010-09-27
Hello everyone.


I installed Wine a few weeks ago. Then, I removed it and removed its remaining from Apllications>right click>Edit Menu. But when I installed it again tonight, I can't find it anywhere! 

When I click on .exe files, the installation window appears but I didn't install anything for the moment. How am I supposed to use them after installing them if I can't find Wine in 'Applications' or anywhere else?

---

### Post by flick on 2010-09-27
To make sure that wine is really cleanly gone and then cleanly installing it fresh :

In a Terminal window :

sudo apt-get purge wine

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install wine

Look for it in the Applications menu.

---

### Post by Can Fly on 2010-09-27
Thanks, I tried that. 

But I tried this as well before checking your solution and the menu is back. 

[http://ubuntuforums.org/showpost.php?p=4596406&postcount=4](http://ubuntuforums.org/showpost.php?p=4596406&postcount=4)

Thanks to both of you.

By the way I am new here, can I edit the thread prefix to add [SOLVED] to the title or only mods are able to do that?

---

### Post by flick on 2010-09-27
Nice find by akimatsu123!

If your problem is solved, could you please edit your original post and add the word "solved" to the beginning. That way other wannabe helpful forum lurkers like myself know that your problem is no longer a problem. :)

---

