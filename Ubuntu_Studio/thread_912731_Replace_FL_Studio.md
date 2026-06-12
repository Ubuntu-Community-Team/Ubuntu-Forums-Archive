---
title: "Replace FL Studio"
date: 2008-09-07
forum: Ubuntu Studio
---

### Post by latinoheat69 on 2008-09-07
I use a lot FL Studio to make reggaeton beats, which is a music genre similar to hiphop, which is very popular here in Puerto Rico. So I installed Ubuntu studio on my machine a while back but due to not being able to use FL Studio on it I switched back to Windows.  Is there a program similar to FL Studio for Ubuntu? I tried Ardour but I really didn't understand it.

Thanks.

---

### Post by BlackLLama on 2008-09-07
plenty of choices in the repository

---

### Post by paulmerchant on 2008-09-07
Try LMMS. It's a project that's similar to FL Studio. If you like it, you'll probably want to install the real time kernel (linux-rt in synaptec), set up the Jack Audio Server, and use the latest version of LMMS.

The project site can be found [here]("http://lmms.sf.net").

---

### Post by latinoheat69 on 2008-09-07
Thanks, I'm gonna try LMMS as soon as I can.

---

### Post by bolex100 on 2008-09-08
I found this thread and tried it but I'm such a newbie that i don't understand what I am typing yet.  I followed the instructions a couple of times (even installed cmake). the install instructions say type this:-

mkdir build
cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
make
sudo make install


 I get this:-


dave@dell-desktop:~$ mkdir build
mkdir: cannot create directory `build': File exists
dave@dell-desktop:~$ cd build
dave@dell-desktop:~/build$ cmake ../cdmake_install_prefix=/usr
CMake Error: The source directory "/home/dave/cdmake_install_prefix=/usr" does not exist.
Specify --help for usage, or press the help button on the CMake GUI.
dave@dell-desktop:~/build$ 


wassup?

---

### Post by latinoheat69 on 2008-09-08
> **bolex100 said:**
> I found this thread and tried it but I'm such a newbie that i don't understand what I am typing yet.  I followed the instructions a couple of times (even installed cmake). the install instructions say type this:-

mkdir build
cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
make
sudo make install


 I get this:-


dave@dell-desktop:~$ mkdir build
mkdir: cannot create directory `build': File exists
dave@dell-desktop:~$ cd build
dave@dell-desktop:~/build$ cmake ../cdmake_install_prefix=/usr
CMake Error: The source directory "/home/dave/cdmake_install_prefix=/usr" does not exist.
Specify --help for usage, or press the help button on the CMake GUI.
dave@dell-desktop:~/build$ 


wassup?

Try to make a new thread.  You can get more help that way I think.

---

### Post by Stochastic on 2008-09-08
just install LMMS from the repos rather than building from scratch

```
sudo apt-get install lmms
```

or do the same thing via Synaptic Package Manager.

---

### Post by OutOfReach on 2008-09-08
+1 for LMMS, you are trying to compile the latest BETA version which is not a good idea, and the LMMS in the repositories is outdated.
Goto [this]("http://www.getdeb.net/release/2845") site and download lmms and lmms-common, then click on lmms-common to install it and then click on lmms to finalize the install.

---

### Post by 080907k on 2008-09-09
&#12290;[**&#24405;&#38899;&#30005;&#35805;**](http://www.rp-cti.com/Chinese/index.html)&#38543;&#30528;&#29616;&#20195;&#36890;&#35759;&#19994;&#30340;&#36805;&#29467;&#21457;&#23637;&#65292;[**&#30005;&#35805;&#24405;&#38899;**](http://www.rp-cti.com/Chinese/index.html)&#30005;&#23376;&#21830;&#21153;&#23558;&#26159;&#19979;&#19990;&#32426;&#30340;&#28526;&#27969;&#12290;&#21628;&#21483;&#20013;&#24515;&#65288;CallCenter&#65289;&#27491;&#26159;&#36814;&#21512;[**&#24405;&#38899;&#21345;**](http://www.rp-cti.com/Chinese/index.html)&#26368;&#26032;&#28526;&#27969;&#30340;[**&#24405;&#38899;**](http://www.rp-cti.com/Chinese/index.html)&#20135;&#21697; &#12290; &#21628;&#21483;&#20013;&#24515;&#23601;&#26159;&#29992;[**&#24405;&#38899;&#30005;&#35805;**](http://www.rp-cti.com/Chinese/index.html)&#20316;&#20026;&#25509;&#20837;&#25163;&#27573;

---

### Post by digitalpulse on 2008-09-15
Cool will look at this lmms thingy, thanks

---

