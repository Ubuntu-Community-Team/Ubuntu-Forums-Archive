---
title: "Corebird"
date: 2017-12-27
forum: Ubuntu/Debian BASED
---

### Post by kvn-mcmns on 2017-12-27
How do you install corebird 1.7.3 in ubuntu !!!!!!

---

### Post by slickymaster on 2017-12-27
*Thread moved to **General Help**.*

---

### Post by slickymaster on 2017-12-27
Open a terminal window and run the following commands, one at a time```
sudo add-apt-repository ppa:ubuntuhandbook1/corebird
sudo apt-get update
sudo apt-get install corebird
```

---

### Post by kvn-mcmns on 2017-12-27
That will not get you 1.7.3 just 1.5.1 which i already have.

---

### Post by howefield on 2017-12-27
```
snap install corebird
```

What version of Ubuntu are you using ?

---

### Post by kvn-mcmns on 2017-12-27
I am using peppermint 8 respin.So if i do not use snaps i can not get latest corebird in ubuntu.(GREAT NEWS).It's no wonder that i use a arch based distro on my main computer.

---

### Post by slickymaster on 2017-12-27
Download the source file [https://github.com/baedert/corebird](https://github.com/baedert/corebird) to your desktop

Then in a terminal window run```
cd ~/Desktop
unzip corebird-master.zip
cd corebird-master
./autogen.sh --prefix=/usr
make
make install
```

---

### Post by slickymaster on 2017-12-27
> **kvn-mcmns said:**
> I am using peppermint 8 respin.So if i do not use snaps i can not get latest corebird in ubuntu.(GREAT NEWS).It's no wonder that i use a arch based distro on my main computer.

Being so, Moved to **Ubuntu/Debian BASED** sub-forum

---

### Post by kvn-mcmns on 2017-12-27
Thanks for your help.

---

