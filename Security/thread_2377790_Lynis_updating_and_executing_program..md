---
title: "Lynis updating and executing program."
date: 2017-11-16
forum: Security
---

### Post by pointy2 on 2017-11-16
After installing Lynis via* sudo aptget install Lynis*, I executed the program via "lynis -c" command throught the terminal. An initial run shows that the program is over 4 months old and to update Lynis. 
Command "lynis update check" in terminal outputs "*/usr/sbin/lynis: 201: .:Can't open /usr/share/include/consts*"
 
I'm doing some searching and can't seem to get beyond the possibility that Lynis was incorrectly installed. 

I'd like to uninstall the program ands re-install from git. 

Any suggestions or advice for reinstalling or updating Lynis? I'm on 17.10 AA.

---

### Post by oldos2er on 2017-11-17
You can remove it with ```
sudo apt remove lynis
```

It appears they maintain their own repositories, see [https://packages.cisofy.com/community/](https://packages.cisofy.com/community/)

---

### Post by pointy2 on 2017-11-17
> **oldos2er said:**
> You can remove it with ```
sudo apt remove lynis
```

It appears they maintain their own repositories, see [https://packages.cisofy.com/community/](https://packages.cisofy.com/community/)

Thanks for this. I wanted to verify the remove code before I installed Lynis from their website.

EDIT> After uninstall and reinstal via git, I am getting the same results. Followed the instructions per above link.

---

### Post by cariboo on 2017-11-18
To completely remove a package, use:

```
apt purge <package_name>
```

---

