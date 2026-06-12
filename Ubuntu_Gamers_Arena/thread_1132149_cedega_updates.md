---
title: "cedega updates"
date: 2009-04-21
forum: Ubuntu Gamers Arena
---

### Post by pi.theta on 2009-04-21
while initializing cedega it gives error regarding EOF end of file:

Sorry, there seems to be a problem while trying to read the manifest file. Please contact us at [http://www.cedega.com/support/](http://www.cedega.com/support/) to notify us of this error:

URL: [http://downloads.cedega.com/files/cedega_manifest/manifest.standard](http://downloads.cedega.com/files/cedega_manifest/manifest.standard)
EOF when reading a line

No further updates will take place until this is fixed.


thnx for any help in advance

---

### Post by Perfect Storm on 2009-04-23
You might try ask at Cedega forum, they might know something about update problems with current release plus solution.

---

### Post by kaicrr77 on 2009-04-25
You can find the fix on [ubuntu-inside.me]("http://www.ubuntu-inside.me/")

Here are the instructions:

[I]Download cedega package "cd" to the directory where you downloaded cedega debian package (for example : cd /home/yourusername/Desktop/)

Now we will create folders :[/I]

```
$mkdir -p cedega_000133_all/DEBIAN
```

*This will create cedega_000133_all folder and inside that DEBIAN folder.Now let's edit the packages, rebuild it and get things working :*

```
$ar p cedega_000133_all.deb data.tar.gz | tar zx -C cedega_000133_all/
$ar p cedega_000133_all.deb control.tar.gz | tar zx -C cedega_000133_all/DEBIAN/
$mv cedega_000133_all.deb cedega_000133_all.prerebuild.deb
$perl -pi -e 's/python2.4-dbus/python-dbus/' cedega_000133_all/DEBIAN/control
$dpkg-deb --build cedega_000133_all
$rm -rf cedega_000133_all
$sudo dpkg -i cedega_000133_all.deb

```

---

