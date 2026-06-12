---
title: "Problem with fftw3f when trying to install guitarix"
date: 2010-09-08
forum: Ubuntu Studio
---

### Post by Sylos on 2010-09-08
Hello again everyone.
I am having some trouble installing guitarix on my hardy Ubuntu Studio. I have got so far but cant seem to progress any further. Here is the output from trying to configure:

```
Checking for program g++ or c++          : /usr/bin/g++ 
Checking for program cpp                 : /usr/bin/cpp 
Checking for program ar                  : /usr/bin/ar 
Checking for program ranlib              : /usr/bin/ranlib 
Checking for g++                         : ok  
Checking for jack <= 1.8.0               : yes 
Checking for sndfile >= 1.0.17           : yes 
Checking for gmodule-export-2.0          : yes 
Checking for gtk+-2.0 >= 2.12.0          : yes 
Checking for gthread-2.0 >= 2.10         : yes 
Checking for gtkmm-2.4                   : yes 
Checking for giomm-2.4                   : yes 
Checking for fftw3f >= 3.1.2             : Package fftw3f was not found in the pkg-config search path.
Perhaps you should add the directory containing `fftw3f.pc'
to the PKG_CONFIG_PATH environment variable
No package 'fftw3f' found 
/home/ric/guitarix-0.11.1/wscript:311: error: the configuration failed (see '/home/ric/guitarix-0.11.1/build/config.log')

```

I have followed some guidance I found on a similar problem on the Hydrogen forum

[http://www.hydrogen-music.org/forum/?action=show_thread&thread=91&fid=0&page=1](http://www.hydrogen-music.org/forum/?action=show_thread&thread=91&fid=0&page=1)

but this hasnt worked. No matter how I try to direct it to the installed fftw it wont find it.

Any suggestions gratefully received.

*I have just found that after installing the fftw pack from source that there is no fftw3f.pc file - this is probabbly the problem but how do I solve it*

---

### Post by AutoStatic on 2010-09-08
Try guitarix 0.11.1 from my PPA, saves you from compiling it yourself ;)
[https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa)

But if you'd like to compile it yourself, you need the **libfftw3-dev** package.

---

### Post by Sylos on 2010-09-08
Hi Autostatic and thanks (again) for your help.
Sadly I cant seem to use your PPA as Im using Hardy 8.04 not Karmic or higher. I tried installing guitarix from a lucid.deb but gdebi complains that some dependcy cant be met (a package that apt-get says is installed).

I'll try and find the fftw3-dev and see if that helps.

cheers

---

### Post by AutoStatic on 2010-09-08
Ah, that's right.
I think you'll run into problems then because Guitarix probably won't build with the Hardy dev packages.

---

### Post by Sylos on 2010-09-08
I fear you may be right. I have got the libfftw3-dev package but I now get stuck with the following:

```
Checking for header boost/format.hpp     : not found
```

Im not sure what this requires me to install. Would libboost-dev be the solution. 

Sorry to be a blagger but Im really reluctant to upgrade to a newer version of Ubuntu studio as my computer is fairly old. Its a compaq amd athlon 2ghz with 1g of RAM and im afraid a more up to date OS will eat up the resources and leave me with a less useable set up.

Thanks

---

### Post by Sylos on 2010-09-08
Installed the libboost-dev apckage and that got me through the configure. However, I have now got the following errors when trying to build:

```
../src/gx_threads.cpp: In function ‘void* gx_threads::gx_signal_helper_thread(void*)’:
../src/gx_threads.cpp:176: error: ‘sigemptyset’ was not declared in this scope
../src/gx_threads.cpp:177: error: ‘SIGUSR1’ was not declared in this scope
../src/gx_threads.cpp:177: error: ‘sigaddset’ was not declared in this scope
../src/gx_threads.cpp:178: error: ‘SIGCHLD’ was not declared in this scope
../src/gx_threads.cpp:179: error: ‘SIG_BLOCK’ was not declared in this scope
../src/gx_threads.cpp:179: error: ‘sigprocmask’ was not declared in this scope
../src/gx_threads.cpp:181: error: ‘sigwait’ was not declared in this scope
Waf: Leaving directory `/home/ric/guitarix-0.11.1/build'
Build failed:  -> task failed (err #1): 
	{task: cxx gx_threads.cpp -> gx_threads_1.o}

```

Is this anything worth trying to fix or am I better not wasting my time?

Cheers

---

### Post by cchhrriiss121212 on 2010-09-08
> **Sylos said:**
> 
Sorry to be a blagger but Im really reluctant to upgrade to a newer version of Ubuntu studio as my computer is fairly old. Its a compaq amd athlon 2ghz with 1g of RAM and im afraid a more up to date OS will eat up the resources and leave me with a less useable set up.

Thanks
Not to derail the thread or anything but I don't think there will be much of a notable difference if you try out a newer version. If you are seeing it as slower then you could go with Lubuntu or another lightweight DE which will help free up some resources.

---

### Post by Sylos on 2010-09-10
Thanks for the suggestion. I am currently using remastersys to back up my current set up ready to try the 10.04 version. 

Is there any benefit in terms of resource consumption in using the Kxstudio system or is it much the same as Ubuntu Studio 10.04?

Thanks

---

### Post by cchhrriiss121212 on 2010-09-10
Have not tried out Kxstudio, but it uses KDE which is about the same resource consumption as regular Ubuntu.
Changing to a lightweight desktop environment can make a big difference, it will reinvigorate a slower machine and make a new machine fly.
Heavier DEs are Gnome and KDE
Lighter DEs are XFCE, LXDE, and any others that make use of window managers like Openbox, IceWM and Fluxbox. You can try out as many as you like on the same OS.

---

### Post by Sylos on 2010-09-12
Cheers for the help. I have now installed 10.04 Studio and am running into other issues. I'll put them in other posts. Fun, Fun, Fun.

Cheers everyone.

---

