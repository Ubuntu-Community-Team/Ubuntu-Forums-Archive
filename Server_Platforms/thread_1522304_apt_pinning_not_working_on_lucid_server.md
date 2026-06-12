---
title: "apt pinning not working on lucid server"
date: 2010-07-02
forum: Server Platforms
---

### Post by Brazen on 2010-07-02
I want to pull a couple of packages from Debian Testing, but I can not get apt pinning to lower the testing repo's priority

I add the testing repo to the bottom of /etc/apt/sources.lst

I then add this in /etc/apt/preferences
```
Package: *
Pin: release a=testing
Pin-Priority: 400
```

but when I do 'sudo aptitude update' and then 'sudo aptitude full-upgrade', it wants to upgrade all packages to the versions in debian testing.

Any ideas?

---

### Post by sh1ny on 2010-07-02
Just get the source for those packages and compile them into debs. Or get the packages and try to install them.

Are those packages not in ubuntu at all, or just newer version of things ? Have you tried looking at launchpad for those packages ?

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

### Post by Brazen on 2010-07-02
> **sh1ny said:**
> Just get the source for those packages and compile them into debs. Or get the packages and try to install them.

Are those packages not in ubuntu at all, or just newer version of things ? Have you tried looking at launchpad for those packages ?

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

it's for a newer version of virtualbox-ose
I tried compiling the source, but ran into an incredible amount of build-dependencies.

I'd like to install the binaries this way, anyway, so I get updates whenever I upgrade with aptitude.

---

### Post by sh1ny on 2010-07-02
That won't be a wise idea ( having debian testing and installing from there - even if it's only virtualbox ). You can try getting the sources from debian and putting them up on launchpad ( which will compile them for you ). It will require a little more effort tho.

---

### Post by Brazen on 2010-07-09
Why is that not a wise idea?  It seems to be a clean install and Virtualbox runs without any problems.  What would be the advantage to recompiling?

---

### Post by toobuntu on 2010-07-15
Change > Pin: release a=testing to ```
Pin: origin http.us.debian.org
```
and for good measure:
```
sudo cp /etc/apt/preferences /etc/apt/preferences.d/debian
```

Take a look at the result of ```
apt-cache policy | grep debian
```
For me, it was not returning any archive names for Debian, so pinning to an archive name (release a=) could not work. Nor was debian-archive-keyring installing any Debian keys, but I digress. Pinning to the origin website worked.

---

