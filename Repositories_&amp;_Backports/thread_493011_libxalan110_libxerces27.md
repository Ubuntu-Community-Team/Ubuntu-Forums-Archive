---
title: "libxalan110 libxerces27"
date: 2007-07-05
forum: Repositories &amp; Backports
---

### Post by stekole on 2007-07-05
OS: Ubuntu Edgy
Alright so I have looked around a bunch. GOOGLED and GOOGLED and I cannot find a fix for this. I have even followed a few tutorials on how to install virtualbox. When I go to install or run the
sudo dpkg -i virtualbox_1.4.0-21864_Ubuntu_edgy_i386.deb
command it says i am missing these two files too. libxalan110 libxerces27 
i did a apt-get install libxalan110 libxerces27 they are not there
I also did a apt-get -f install after trying the package.... any help
I cannot seem to install the libraries or find the depositories for it. Could someone help me out please?

Thanks

---

### Post by tgm4883 on 2007-07-05
Did you add the virtualbox repos to your sources.list?

did you try apt-get install virtualbox?

---

### Post by stekole on 2007-07-05
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) edgy non-free
was added yes.
and yes i did and it still needs those files

---

### Post by bapoumba on 2007-07-05
libxalan110 and libxerces27 are in the universe repositories. Have you enabled these?

---

### Post by tgm4883 on 2007-07-05
Add the other repo's then
sudo apt-get install libxalan-c libxerces-c libstdc++

---

