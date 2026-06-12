---
title: "Howto: Compile Pulseaudio from git"
date: 2014-03-11
forum: Tutorials
---

### Post by Milos_SD on 2014-03-11
To compile Pulseaudio from git, you need to follow this few steps.

1) First we will need to install some dependencys (deps in the rest of the text). So, open terminal and paste this:
```
sudo apt-get build-dep pulseaudio && sudo apt-get install checkinstall git libpulse-dev
```

1.1) This should install all the deps you need to compile pulseaudio. If there is some missing deps after configure (step 4), then open Synaptic and find -dev package of the missing lib.

2) Now we will get pulseaudio from git repo:
```
git clone git://anongit.freedesktop.org/pulseaudio/pulseaudio
```

3) Go into new pulseaudio directory where the source code is:
```
cd pulseaudio
```

4) Now paste this into terminal:
```
./autogen.sh
```

- And when that is finished, then paste this:
4.1) ```
CFLAGS="-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -Wall" CXXFLAGS="-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -Wall" CPPFLAGS="-D_FORTIFY_SOURCE=2" LDFLAGS="-Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,--no-as-needed -lxcb" $HOME/pulseaudio/./configure --build=x86_64-linux-gnu  --prefix=/usr --includedir="\${prefix}/include" --mandir="\${prefix}/share/man" --infodir="\${prefix}/share/info" --sysconfdir=/etc --localstatedir=/var --libexecdir="\${prefix}/lib/pulseaudio" --srcdir=. --disable-maintainer-mode --disable-dependency-tracking --disable-silent-rules   --enable-x11 --disable-hal --libdir=\${prefix}/lib/x86_64-linux-gnu --with-module-dir=\${prefix}/lib/pulse-5.0/modules --disable-oss-wrapper
```

If this finishes without any error, you can continue with step 5, but if there is an error of missing deps, then follow 1.1 step.

5) Now we initiate a compile:
```
make -jX
```

**Clarification:** The X in "-jX" is a number of CPU cores your computer has +1. So if you have 4 cores CPU you use -j5, and if that CPU has Hyperthreading, then it would be -j9. I hope you get the picture. :)

If all goes well, next step will be installing:

6) ```
sudo make install
```

6.1) This step is optional. It will create a .deb file, and install it.
```
sudo checkinstall[code]

- The first thing you will get is this question:
[code]Should I create a default set of package docs?  [y]: 
```

Answer it with [n] ( just press letter n )

- Next will be some warrning, just ignore it and press ENTER
- Now you have few options to pick.
- Press number 1 and ENTER - in there write something like "pulseaudio from git" and press ENTER.
- Now press number 3 and ENTER - there you will write a version like this: 6:5.0 and press ENTER again.
- Now you can continue with creating a .deb package - so press ENTER.
- Wait for it to finish, and now you have created and install .deb package of new pulseaudio you compiled.

7) Now you can go to some system monitor and kill pulseaudio process, so the new version starts, or you can just logout and log back in.

If you have any problems with this, just write it here, and I will help you with it.

---

### Post by QDR06VV9 on 2014-03-11
Spoke to soon error after step.4
```
bash: /home/sdcafe/Kompajlirani_programi/Pulse_Audio/pulseaudio/./configure: No such file or directory


```

---

### Post by Milos_SD on 2014-03-11
Oh, yea, sorry for that. I forgot to edit that part. :D
I will fix it now. :D

Edit: Fixed. :)

P.S. BTW, that is the directory where I keep pulseaudio source.

---

### Post by QDR06VV9 on 2014-03-11
> **Milos_SD said:**
> Oh, yea, sorry for that. I forgot to edit that part. :D
I will fix it now. :D

Edit: Fixed. :)

P.S. BTW, that is the directory where I keep pulseaudio source.
Sorry for what?;)
I thought that was the case but I did not want to assume.
But still had no .configure file found so went into /home/usr(me)/pulseaudio
and just doubled clicked "autogen.sh" and then the "configure" file was present.
All went well after that:):guitar:

---

### Post by Milos_SD on 2014-03-11
I am glad. Thank you for remainding me about autogen.sh. I forgot about it, becouse you need to use it just for the first time, and I did that few years ago. :D I added that step into the howto.

---

### Post by QDR06VV9 on 2014-03-11
> **Milos_SD said:**
> I am glad. Thank you for remainding me about autogen.sh. I forgot about it, becouse you need to use it just for the first time, and I did that few years ago. :D I added that step into the howto.
You Sir are a Gentleman and Scholar !
Kind Regards Rick

---

### Post by cpatrick08 on 2014-03-16
> **runrickus said:**
> Spoke to soon error after step.4
```
bash: /home/sdcafe/Kompajlirani_programi/Pulse_Audio/pulseaudio/./configure: No such file or directory


```
I still get the bash: /home/cpatrick08/pulseaudio/./configure: No such file or directory error messgae after step 4.1, nevermind had it in /home/cpatrick/source/pulseaudio and I changed the command, and now it works.

---

### Post by agemini68 on 2014-04-21
I made it all the way to the end and got this: (Reading database ... 221839 files and directories currently installed.)
Preparing to unpack .../pulseaudio_5.0-1_i386.deb ...
Unpacking pulseaudio (6:5.0-1) over (1:4.0-0ubuntu11) ...
dpkg: error processing archive /home/donna/pulseaudio/pulseaudio_5.0-1_i386.deb (--install):
 trying to overwrite '/etc/pulse/client.conf', which is also in package libpulse0:i386 1:4.0-0ubuntu11
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/donna/pulseaudio/pulseaudio_5.0-1_i386.deb

---

### Post by QDR06VV9 on 2014-04-22
That looks like a checkinstall error.

---

### Post by cpatrick08 on 2014-05-11
When I run command in step 1 on Trusty 64 bit i get following error message The following packages have unmet dependencies: libjack-dev : Depends: libjack0 (= 1:0.121.3+20120418git75e3e20b-2.1ubuntu1) but it is not going to be installed
E: Build-dependencies for pulseaudio could not be satisfied.

---

### Post by QDR06VV9 on 2014-05-22
> **cpatrick08 said:**
> When I run command in step 1 on Trusty 64 bit i get following error message The following packages have unmet dependencies: libjack-dev : Depends: libjack0 (= 1:0.121.3+20120418git75e3e20b-2.1ubuntu1) but it is not going to be installed
E: Build-dependencies for pulseaudio could not be satisfied.
Sorry Forgive me I have not been wacthing this thread better.
When you add a PPA, "Source" part is not added automaticaly. Go To  Software Sources and check the Source part of that PPA. Then it should  work.
Also see [here]("http://ubuntuforums.org/showthread.php?t=2210336&page=2")
Regards

---

### Post by tripflex on 2014-11-05
If anybody comes across this thread and has troubles using AirPlay or compiling from source (as I did with lib errors related to systemd), I found that raop2 solved all my issues with AirPlay:

[http://hfujita.github.io/pulseaudio-raop2/](http://hfujita.github.io/pulseaudio-raop2/)

---

### Post by Rajanmax on 2014-11-11
Hey this is kind of weird but its true.. Ubuntu is

---

### Post by jesselashcraft on 2014-11-18
> **Milos_SD said:**
> To compile Pulseaudio from git, you need to follow this few steps.

I'm a new guy.

I was down to step 5 of your instructions and waiting for a response to my question "how many cores do I have and is my CPU Hyperthreading" when I tried agemini68's Alsamixer fix which worked for me.  

If you wouldn't mind, what commands do I need to use to undo the first 4 steps of your instructions? 

Thanks

---

### Post by Satyajit_Sen on 2015-02-07
hi 

i am try with this commands. this is properly installed but i can't see in my sound and video menu.. so please help me what i do right now. and how to access pulseaudio 5

---

