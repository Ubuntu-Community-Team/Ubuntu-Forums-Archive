---
title: "Permissions of files in a Deb package"
date: 2016-06-15
forum: Ubuntu Application Development
---

### Post by CantankRus on 2016-06-15
After a couple of days of ](*,) I managed to put together a Deb package for some scripts I use to 
create a snippets list using the unity quicklists.
The package is mainly bash scripts that install to /opt, basically because I'm not sure of 
the right directories to put content.

I followed this [**_[COLOR="#B22222"]guide[/COLOR]_**]("http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/") to make a basic personal deb package and built it as a normal user with...
```
dpkg-deb --build *[COLOR="#808080"]directory archive[/COLOR]*
```

The deb installs fine and everything works but lintian shows numerous file permission and ownership warnings.
How do you build with correct file ownership/permissions?

---

### Post by CantankRus on 2016-06-17
This builds unsigned debs with correct permissions.
```
dpkg-buildpackage -rfakeroot -us -uc
```

Something I came across that might help others when trying to use a gpg key to sign 
packages for upload to launch pad or if you can't decrypt pgp messages.

When trying to build a source package for Launchpad using...
```
debuild -S -rfakeroot
```
I was getting an error "can't find secret key" even though I could see it was there with...
```
gpg --fingerprint
```

The answer is to use the command gpg2 or export your secret key.
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://askubuntu.com/questions/771626/gpg-key-created-but-will-not-decrypt").

Now I just need to find out how the files in the source code work??? #-o:???:

---

