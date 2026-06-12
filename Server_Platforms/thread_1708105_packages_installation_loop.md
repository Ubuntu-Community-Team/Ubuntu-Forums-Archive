---
title: "packages installation loop"
date: 2011-03-16
forum: Server Platforms
---

### Post by Rui Esteves on 2011-03-16
Hi
I needed to install package g++ (g++-4.4_4.4.3-4ubuntu5_i386) and it gave an error saying that there is a dependency error: need libstdc6-4.4-dev
I tried to install this last package and it gives an error saying it depends on g++-4.4

So, I am in a loop and unable to install any of them.
Any idea on how to get things installed?

Thanks in advance

---

### Post by wongo888 on 2011-03-16
What error are you getting from:

```
sudo apt-get install g++-4.4
```

Copy and paste it here. Also, what are you running?

```
$ uname -a
$ lsb_release -a
```

---

