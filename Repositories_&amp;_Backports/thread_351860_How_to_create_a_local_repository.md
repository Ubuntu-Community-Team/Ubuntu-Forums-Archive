---
title: "How to create a local repository"
date: 2007-02-02
forum: Repositories &amp; Backports
---

### Post by nozey on 2007-02-02
Im trying to make a local repository for my lan. I followed these docs:

[http://www.ubuntuforums.org/showthread.php?t=267837&highlight=local+repository](http://www.ubuntuforums.org/showthread.php?t=267837&highlight=local+repository)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Personal_Apt_Repository](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Personal_Apt_Repository)
[https://help.ubuntu.com/community/Repositories/Personal?action=show&redirect=PersonalRepositories](https://help.ubuntu.com/community/Repositories/Personal?action=show&redirect=PersonalRepositories)

After i made the repository, i changed the apache.conf and tried to use the repository. For my surprise the whole thing didint worked. 

In a client machine sources.list i have:

```
deb http://ip binary/
```

When i run apt-get update the Packages.gz file is found and everything looks ok.

```
# apt-get update
Ign http://ip binary/ Release.gpg
Ign http://ip binary/ Release
Ign http://ip binary/ Packages
Atingido http://ip binary/ Packages
Lendo Lista de Pacotes... Pronto  (something like: reading packages list ... ready)
```

But when i run dist-upgrade, for example, some files are not found. The error:
```
....
Err http://ip binary/ xfonts-100dpi 1:1.0.0-2ubuntu1
  404 Not Found
Err http://ip binary/ xfonts-75dpi 1:1.0.0-2ubuntu1
  404 Not Found
...
Falha ao baixar http://192.0.0.239/apt/binary/xserver-xorg-driver-all_1%3a7.1.1ubuntu6.2_i386.deb404 Not Found
..
Falha ao baixar http://192.0.0.239/apt/binary/xserver-xorg-video-chips_1%3a1.1.1-0ubuntu1_i386.deb 404 Not Found
```

I think that apt is using a wrong file name . Example:

Using my browser i can see that a package filename is:
 xfonts-100dpi_1**%253**a1.0.0-2ubuntu1_all.deb (wget can download it)

But apt tries to download: xfonts-100dpi_1**%3**a1.0.0-2ubuntu1_all.deb

After the "dpi_1%"  apt is changing the number 253 for 3. Thats why he never find the packages.

Does somebody know whats wrong? Can it be my locale? Or some apache configuration files?

---

