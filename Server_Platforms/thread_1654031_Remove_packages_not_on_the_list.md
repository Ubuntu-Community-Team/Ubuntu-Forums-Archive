---
title: "Remove packages not on the list"
date: 2010-12-27
forum: Server Platforms
---

### Post by karmakowski on 2010-12-27
I have a list of packages installed on one machine (acquired with dpkg --get-selections) and would like to REMOVE all packages that are not on the list from another machine. 

So... there's a list of packages in /root/packages.txt:
```

[...]
base-passwd                    install
bash                        install
bind9-host                    install
bind9utils                    install
binutils                    install
bsdutils                    install
busybox-initramfs                install
byobu                        install
bzr                        install
bzrtools                    install
ca-certificates                    install
comerr-dev                    install
console-setup                    install
console-terminus                install
coreutils                    install
[...]

```and I want to remove every package that is installed but on this list.

What is the recommended way?

---

### Post by kidders on 2010-12-28
Hi there,

One simple option would be to combine both lists, pull out the unique package names, & uninstall them. In other words, you'd be removing everything except the intersection of both package lists. For example, you could try something along the lines of ...```
sort list1 list2 | uniq -u | cut -d" " -f1 | xargs apt-get remove
```

Not very elegant ... but effective. Just be careful to strip lines that reference operations other than "install" (eg "deinstall") from both files.

I hope that helps.

---

