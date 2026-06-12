---
title: "Win10 WSL Ubuntu Miniforge3  - installing Sagemath - How toSet PATH in .bashrc"
date: 2024-11-01
forum: Virtualisation
---

### Post by shaussie on 2024-11-01
I am a newbie in Ubuntu. In Win10, I have installed WSL2, then Ubuntu and now I need to install Sage Math on top.

On running this cmd:              [COLOR=#b22222]$bash  Miniforge3-$(uname)-$(uname -m).sh  ---(1)[/COLOR]

I get this display:              Welcome to Miniforge3 24.9.0-0  (so it is installed OK)

Next, I need to run this:         [COLOR=#b22222]$conda create -n sage sage python=3.11  ---(2)
[/COLOR][COLOR=#000000]
but run into this problem:[/COLOR][COLOR=#b22222]        conda:  command not found  [/COLOR][COLOR=#000000]and[/COLOR][COLOR=#b22222] command "mamba" not found

[/COLOR]The contents of the miniforge3 directory are the following:

=2.17        _conda  compiler_compat  condabin  etc      lib      man   sbin   shell  x86_64-conda-linux-gnu
LICENSE.txt  bin     conda-meta       envs      include  libexec  pkgs  share  ssl    x86_64-conda_cos6-linux-gnu

Can you provide some idea how I can execute (2).  Command "conda" is not here but "_conda" is.
I am unfamiliar with Linux / Ubuntu file system to correctly set a PATH command.  I can move to
the miniforge3 directory and execute(2) from there?

Thanks for your help or ideas.

---

### Post by TheFu on 2024-11-03
WSL is not normal Ubuntu.
If you want a normal Ubuntu experience, install a hypervisor, like virtualbox, and install one of the Ubuntu flavors of 24.04 into a virtual machine.  

As for Sage Math, there are installation instructions here: [https://doc.sagemath.org/html/en/installation/index.html](https://doc.sagemath.org/html/en/installation/index.html) for developers and non-developers.

PATH is an environment variable on Linux/Unix/MacOS just like it is on MS-Windows.  Typically, it would be set in your ~/.bashrc file. You can modify it there.
Typically, you'd want to append a directory to the end of the existing PATH, but only if it wasn't already added.  Say we want to add /home/joe/sagemath/bin to our PATH.  Assuming username "joe" has a HOME directory of /home/joe, then the easy answer is:
```
export PATH="$PATH:$HOME/sagemath/bin"
```
Put that line at the end of your ~/.bashrc file, logout and login again. Check that it was added with ```
echo "$PATH"
```  You can get fancy, if needed.  

If you want to see all environment variables, run **env**

You'll find that many manually installed things that easily work on full Ubuntu systems have slight issues under WSL. When you are new to all this, best to avoid WSL completely.  That's my advice.  It never feels quick enough like Linux for non-server programs.

I don't think **conda** is part of any Linux default install.  You might need to install it. IDK how. I've never installed it myself.

You don't want to relocate manually installed programs.  Mixing package manager default locations with manually installed programs/libraries is a really bad idea.  In general, /usr/local/ is where manually install things would go, if not in your HOME directory.  

There are standards for what goes where on Unix systems.  While the document describing everything is long, what you and I need to know is easily covered in a two page table on wikipedia.  [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by shaussie on 2024-11-08
Many Thanks, TheFu, for your help.  I have decided to take an older Lenovo M71e PC with Win10 Pro (Build 17134) and go for a dual boot with Ubuntu 22.04.  After getting a USB stick (128G) and Rufus , I found that [WSL --install]   requires a Windows Build later than 19041.  So this will not work in this case.

Is there a simple, fool-proof way to install a working Ubuntu (early version) on a 60Gb partition so that it will work cleanly in this case.  Thanks again.

---

### Post by TheFu on 2024-11-08
Only install supported LTS releases. If you don't know what that means, take the time to look it up now.

I'm pretty much against most people using dual boot. There are lots of problems and MSFT had a habit of breaking the boot stuff for any non-MSFT OSes.  Consider yourself warned.  BTW, when it breaks, it will never be at a convenient time.

The best answer is to install a hypervisor, then create a new virtual machine, and perform a normal install of any version of Ubuntu except the Gnome or KDE DE versions. All the others are lighter and will run well.

The only times NOT using a VM for a Linux desktop makes sense is when the machine is from 2008 or earlier (really old CPU that isn't vt-x), only has 4GB of RAM, or if the purpose of the machine is to run FPS games or to do video editing or other GPU-intensive workloads.  Besides that, use a VM and be happier.

6t0G is more than sufficient.  Running from flash storage is more a problem.  If that external storage was an SSD - go for it.

---

### Post by shaussie on 2024-11-11
Many thanks TheFu for your help and advise.  I have been able to install Ubuntu (after several attempts) on my older win10 PC using VirtualBox 7.1.4.  Ubuntu22.04 was installed later and it works OK.

Please tell me how to indicate on the thread that the query has been satisfactorily answered.

Kind regards.

---

### Post by TheFu on 2024-11-12
> **shaussie said:**
>  Please tell me how to indicate on the thread that the query has been satisfactorily answered.

Top right if the webpage, there's a "Thread Tools" button.  There's a "SOLVED" option. Select that.  As you know, it helps the entire community concentrate on what they seek.

---

