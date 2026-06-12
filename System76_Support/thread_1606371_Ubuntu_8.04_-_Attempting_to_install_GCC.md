---
title: "Ubuntu 8.04 - Attempting to install GCC"
date: 2010-10-26
forum: System76 Support
---

### Post by Jordyboy on 2010-10-26
Hello all, Iv'e tried installing GCC for a while now (following things people have said on these forums).

[PHP]configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
root@myvps:~/Unreal3.2# cd
root@myvps:~# apt-get gcc gcc++
E: Invalid operation gcc
root@myvps:~# apt-get gcc
E: Invalid operation gcc
root@myvps:~# apt-get gcc++
E: Invalid operation gcc++
root@myvps:~# apt-get install gcc++
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc
root@myvps:~# apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc
root@myvps:~# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essential
root@myvps:~# sudo aptitude install build-essential
sudo: aptitude: command not found
root@myvps:~# apt-get install gcc-4.0
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-4.0
root@myvps:~# sudo apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc
root@myvps:~# sudo apt-get install gcc++
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc
root@myvps:~# sudo apt-get install gcc-4.0
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-4.0
root@myvps:~# sudo apt-get install gcc build-essential
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc
root@myvps:~# sudo apt-get intall build-essential
E: Invalid operation intall
root@myvps:~# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essential
root@myvps:~#[/PHP]

As you can see, iv'e tried everything. Can anybody help

Thanks,
Jordan.

---

### Post by isantop on 2010-10-26
Build-essential should definitely install fine on your system, so I'm guessing an issue with apt. First, make sure all of your repositories are enabled. Go to System > Administration > Synaptic Package Manager. You may need to enter your password. Then, in Synaptic, click Settings > Repositories. On the "Ubuntu Software" tab, make sure all of the checkboxes are checked, then close that window and Synaptic.

Next, open a terminal and run:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo apt-get install build-essential
```

This should get build-essential, which includes gcc, installed.

I should also point out, however, that Ubuntu should include gcc installed by default. It may not support many languages, but you will have C/C++, and possibly some others.

---

