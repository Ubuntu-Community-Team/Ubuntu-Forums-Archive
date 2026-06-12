---
title: "Clear browser cache with a command - czkawka"
date: 2024-04-09
forum: The Cafe
---

### Post by Nikolai D. on 2024-04-09
Hello,
I was searching for the info how can I clear browser cache / cookies with a single command. A double click would be even better but if i have a command then I can make an exe out of it possibly.
So I have found this tool for the life of me can’t figure out what the command would be:
[https://github.com/qarmin/czkawka](https://github.com/qarmin/czkawka)
Anyone any suggestions?
Thx
:)

---

### Post by TheFu on 2024-04-09
I don't know anything about that, but I use browsers inside a **firejail --private** environment. 

Doing that makes them appear to be 100% brand new, never run before, so there aren't any cookies saved, ever.  When the program is closed, there's no left-over crumbs from the program of any kind remaining.

Firejail --private doesn't allow a program to touch any local storage at all unless you want to pull/push a saved file in/out of the firejail container manually.  I also limit the amount of RAM that firefox can have using some firejail constraints and I force my own specific DNS server, regardless of what a browser may desire in their claimed "security".  More and more, browsers are ignoring our system settings for DNS and calling it "security".  Mozilla and Google do this.

---

### Post by Nikolai D. on 2024-04-11
Also, I don’t know why I didn’t take a look at it earlier, maybe because I didn’t want to install anything beforehand and wanted to use a portable tool, and maybe even command line only tool,
But here it goes this seems to me like maybe a simpler option:
[https://docs.bleachbit.org/doc/command-line-interface.html](https://docs.bleachbit.org/doc/command-line-interface.html)

---

### Post by TheFu on 2024-04-11
Bleachbit was great 10 yrs ago. Since Gnome3 and Gnome4, I've heard of some issues with it.  I can only say, "be careful" using it.  

I've never used it.  Since it is a 3rd party tool, and not part of any browser company, I'd expect browsers to feel free to change how they do and store stuff whenever they like.

Be careful.

---

