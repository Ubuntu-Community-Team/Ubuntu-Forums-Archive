---
title: "Tutorial on installing and building software"
date: 2008-06-23
forum: The Cafe
---

### Post by ventsyv on 2008-06-23
Hi guys. I'm looking for tutorial on how to install/remove/upgrade and build software from source on the command line. 
I'm familiar with the shell (bash cshl kshl whatever) as I've used System V and I've also played with *nix in general. I've used make files under windows, but I'm a bit rusty and I'm not familiar with the different package files (.run or whatever it is). 
I would appreciate if you can point me in the right direction. I would also appreciate if you point me to Ubuntu specific tutorial that goes over on the specific areas of Ubuntu that differ from other distros. 

Much obliged :-).

V.

---

### Post by LaRoza on 2008-06-23
> **ventsyv said:**
> Hi guys. I'm looking for tutorial on how to install/remove/upgrade and build software from source on the command line. 
I'm familiar with the shell (bash cshl kshl whatever) as I've used System V and I've also played with *nix in general. I've used make files under windows, but I'm a bit rusty and I'm not familiar with the different package files (.run or whatever it is). 
I would appreciate if you can point me in the right direction. I would also appreciate if you point me to Ubuntu specific tutorial that goes over on the specific areas of Ubuntu that differ from other distros. 

Much obliged :-).

V.

It depends on how you get the source. You'll need the building tools (build-essential) at the very least.

All source packages have guides in them, with instructions, so you can always follow them.

Typically, it is a simple process.

Source is typically in a tarball, a .tar.gz archive. You have to extract it:

```

tar -xvvzf foo.tar.gz

```

After extracting, you navigate into the directory:
```

cd foo

```

Next, you configure it (normally, you don't have to do anything)
```

./configure

```

Make it:
```

make

```

Install:
```

make install

```

As said before, source packages come with instructions.

---

### Post by RiceMonster on 2008-06-23
I would reccomend checkinstall instead of make install. checkinstall creates a .deb package which you caqn remove later with dpkg -r.

```
sudo apt-get install checkinstall
```

---

### Post by ventsyv on 2008-06-23
Thanks for the help. That makes sense. I found some pretty good 
tutorial and I'm reading my way through those.

> **LaRoza said:**
> It depends on how you get the source. You'll need the building tools (build-essential) at the very least.


I'll be writing it. The one of the other two guys that was working on this project with me was doing all the compiling and building and stuff, now I'll have to learn. 

We used Qt on Suse (as far as I can remember) and the app ran fine with KDE. Now I'm re-writing the back end. 

How about creating an installable package ?? Does anyone know what should I use to create a package that can be easy for the user to install ?

---

