---
title: "jManga an app to download manga for mangafox i made"
date: 2014-08-18
forum: Ubuntu Application Development
---

### Post by pocisite on 2014-08-18
Hey guys i try to make an terminal apps to download manga from mangafox. i like the result but that's not the problem
> [IMG]https://a.fsdn.com/con/app/proj/jmanga/screenshots/Screenshot%20from%202014-08-17%2022:30:41.png[/IMG]
maybe the problem now is i don't know how to package so i try to make my own install script (because it just contain 3 file anyway) .  the install contain copying the main program to /usr/bin and copying 3 setting file to home folder :D is it good enough?
here is the script
```
#!/bin/bash
#this is the simple installation script
cp jManga /usr/bin/
mkdir ~/.jManga
chmod -R 777 ~/.jManga
cp setting.j  ~/.jManga
cp function.j  ~/.jManga
cp variable.j  ~/.jManga
```

the project link is [here]("https://sourceforge.net/projects/jmanga/") . or [https://sourceforge.net/projects/jmanga/](https://sourceforge.net/projects/jmanga/)
i also include the source and it's heavy commented so i think it'd be easy to you to read :)

---

### Post by ofnuts on 2014-08-18
In Linux, "installing" shouldn't put anything in the user's folders. When you install you are root(*)... and potentially install for several users. Putting stuff in the home folder at that point won't help. So, in decreasing order of desirability, either:

[LIST]
[*]have your code use default values when nothing is found in the user's directory
[*]create the defaults values when running for the first time, using data in the script (here-document or else)
[*]create file holding default values file in /etc at install, and manage non-default values for the user in his own folders
[*]create file holding default values file in /etc at install, and copy it to the user's folder if not found there
[/LIST]
  
(*) no really, on Ubuntu, but still true in the general case

---

