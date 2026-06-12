---
title: "Hardware testing program or something idk"
date: 2017-08-21
forum: Server Platforms
---

### Post by khhh on 2017-08-21
so...
i recently bought an old dell (from 2004!) and installed ubuntu server on it for... testing purposes.
that dell doesen't work as smooth as i would like it to, and i went looking for a whole-system test so i can see if everything is ok.
does something like that exist?
(command line!)

---

### Post by Bashing-om on 2017-08-21
khhh; Hello; Welcome to the forum .

What I use to stress out the system is the tool ' stress ' .
See:
[https://askubuntu.com/questions/835386/cpu-stress-testing-with-stress](https://askubuntu.com/questions/835386/cpu-stress-testing-with-stress)
[http://manpages.ubuntu.com/manpages/trusty/man1/stress.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/stress.1.html)

The tool is in our software repository.
To install:
```

sudo apt update
sudo apt upgrade
sudo apt install stress

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by mastablasta on 2017-08-22
i use ultimatebootcd for troubleshooting. it comes loaded with various tools. 

other good options are Hiren boot cd or Falcon4 boot cd for windows based (not sure how well these freedos tools support UEFI secure boot) and System rescue cd for linux based troubleshooting

---

