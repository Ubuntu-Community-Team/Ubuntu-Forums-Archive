---
title: "Build custom deb from Unity source code"
date: 2012-07-27
forum: Ubuntu Application Development
---

### Post by DvKrane on 2012-07-27
I downloaded the full source code of Unity from launchpad, and modified some of the files. It works fine on my Ubuntu system, but I want to make a deb file that's distributable onto other Ubuntu installs. The problem I'm having is that for some unknown reason, my build of the modified source code is 1.4 GB in size when it shouldn't be anymore than 7 MB. Could anyone explain to me the possible reasoning behind this?

---

### Post by DvKrane on 2012-07-27
Nevermind. It was the source I had downloaded. It was outdated and had extra files that weren't needed. Now I'm running into a build problem. It finishes the build but messes up at the very end of the process.

```

make[4]: Leaving directory `/home/iiquili/Downloads/unity-5.14.0/obj-i686-linux-gnu'
make -f tests/CMakeFiles/check.dir/build.make tests/CMakeFiles/check.dir/build
make[4]: Entering directory `/home/iiquili/Downloads/unity-5.14.0/obj-i686-linux-gnu'
make[4]: *** No rule to make target `../tests/test-gtest', needed by `tests/CMakeFiles/check'.  Stop.
make[4]: Leaving directory `/home/iiquili/Downloads/unity-5.14.0/obj-i686-linux-gnu'
make[3]: *** [tests/CMakeFiles/check.dir/all] Error 2
make[3]: Leaving directory `/home/iiquili/Downloads/unity-5.14.0/obj-i686-linux-gnu'
make[2]: *** [tests/CMakeFiles/check.dir/rule] Error 2
make[2]: Leaving directory `/home/iiquili/Downloads/unity-5.14.0/obj-i686-linux-gnu'
make[1]: *** [check] Error 2
make[1]: Leaving directory `/home/iiquili/Downloads/unity-5.14.0/obj-i686-linux-gnu'
dh_auto_test: make -j1 check ARGS+=-j1 returned exit code 2
make: *** [build] Error 29
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```

---

### Post by mjuhasz on 2012-08-01
To rebuild a package which is in the repository you can follow these steps:

```
#get the source code
apt-get source <packagename>
#get the build dependecies
sudo apt-get build-dep <packagename>
#enter the source folder
cd <packagename>
#make your changes
#write changelog and set version
debchange -i
#build binary
dpkg-buildpackage -b
```


You can of course upload your source into a ppa on launchpad (create one for yourself if you don't have one). Then you don't pollute your system with build dependencies and you can add that ppa to other computers if you want to.
Then this is what you would want to do:

```
#get the source code
apt-get source <packagename>
#make your changes
#write changelog and set version
debchange -i
#build source package (sd instead of sa if alternative package)
debuild -S -sa -kC15BEEE2
#upload to your ppa
dput ppa:your_lp_account/your_ppa <source.changes>
```

---

