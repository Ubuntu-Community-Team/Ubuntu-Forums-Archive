---
title: "Found a bug in my mainline kernel update script"
date: 2013-04-19
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-04-19
**Edit:**
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)
newer version with more features aka options

[FONT=courier new]-----------ORIGINAL POST BELOW-----------[/FONT]

I have posted this script in several of the kernel testing threads since the previous dev cycle of qunatal, I found a bug recently here is the fix, I am posting this here to make sure everyone using it gets the update.

there is a mistake on line 29 of [FONT=courier new]/usr/local/bin/KernelUpdateScriptGenerator[/FONT]
before:
[FONT=courier new]$name2=substr($name,0,strpos($name,_**'-q'**_));[/FONT]
after:
[FONT=courier new]$name2=substr($name,0,strpos($name,_**"-$r"**_));[/FONT]
I underlined the change on the line

This should patch the file for you:
```
sudo sed "s/'-q'/\"-\$r\"/" -i /usr/local/bin/KernelUpdateScriptGenerator
```

i think i put the '-q' in there while testing qunatal so the q was for quantal and i guess i forgot to make it dynamic
i have attached a copy of the installer with the fix for those who are wondering what this is

---

### Post by pqwoerituytrueiwoq on 2013-04-28
I have recently added lot of features for advanced usage feature, I know most of us here have use for at least some of them, you could add a cronjob to install new kernels automatically
It also has nice and fancy info output when you go to install a kernel
[[img]http://www.zimagez.com/miniature/screenshot-04282013-093814pm.php[/img]](http://www.zimagez.com/zimage/screenshot-04282013-093814pm.php)
better handling of only 3 debs for new kernels while still supporting the old kernels that need 4 debs, without asking for any confirmation (eg assume one is missing if there are 3)

---

