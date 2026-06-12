---
title: "Kbfx new stable release out - is some generous folk able to provide debs? :)"
date: 2007-05-16
forum: Repositories &amp; Backports
---

### Post by Laervian on 2007-05-16
As the title goes - here is the announcement: [http://www.kde-apps.org/content/show.php/KBFX+Silk+(KBFX+0.4.9.3.1)?content=24898](http://www.kde-apps.org/content/show.php/KBFX+Silk+(KBFX+0.4.9.3.1)?content=24898)

If some generous and computer-proficient person is going to package it for ubuntu, I guess I would not be the only grateful user :D

---

### Post by uberushaximus on 2007-06-06
> **Laervian said:**
> As the title goes - here is the announcement: [http://www.kde-apps.org/content/show.php/KBFX+Silk+(KBFX+0.4.9.3.1)?content=24898](http://www.kde-apps.org/content/show.php/KBFX+Silk+(KBFX+0.4.9.3.1)?content=24898)

If some generous and computer-proficient person is going to package it for ubuntu, I guess I would not be the only grateful user :D

run

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get build-dep kbfx
```

```
wget http://www.kde-apps.org/content/show.php/KBFX+Silk+(KBFX+0.4.9.3.1)?content=24898
```

```
tar -xzf kbfx*.tar
```

```
cd kbfx*
```

```
./configure && make && sudo make install
```

;)

---

