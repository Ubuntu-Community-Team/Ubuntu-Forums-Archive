---
title: "assualtcube in wine problems"
date: 2010-12-04
forum: Wine
---

### Post by masterrob213 on 2010-12-04
i try to run assaultcube on wine for linux and when it loads it starts normal but after so far my computer freezes and i have to restart my computer so what does that mean

---

### Post by cipherboy_loc on 2010-12-05
Just use the assaultcube that is in the repositories:

```
sudo apt-get install assaultcube
```

If you need to play multiplayer online, run:

```

mkdir ~/bin
cd ~/bin
wget http://sourceforge.net/projects/actiongame/files/AssaultCube%20Version%201.1.0.4/AssaultCube_v1.1.0.4.tar.bz2/download
mv download AssaultCube.tar.bz2
tar -xf ./AssaultCube.tar.bz2
mkdir AssaultCube
cd ./AssaultCube
tar -xf ../AssaultCube.tar.bz2
cd 1.1.0.4
./install_desktop_menu.sh

```


I think that should do it. To run assaultcube from the terminal:
```

~/bin/AssaultCube/1.1.0.4/assaultcube.sh

```

---

