---
title: "Evolution 3.4 on Ubuntu 12.04"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by terrykiwi83 on 2012-04-06
Just doing some testing and noticed that 12.04 ships with Evolution 3.2. However am looking at upgrading to the current stable of 3.4.0.1

I have downloaded the source, then invoked the following command:

```

./configure

```

To be presented with the following error

```

configure: error: glib-compile-schemas not found.

```

Am I doing something wrong here? or does anyone know of a PPA for Evolution that contains 3.4.0.1?

Cheers

---

### Post by terrykiwi83 on 2012-04-07
Bump, anyone any suggestions?

---

### Post by NHclimber on 2012-04-07
Building evolution from scratch is too difficult for casual use. I'm pretty sure no one has done a PPA. I'm not going to redo the PPA of evolution-ews until after 12.04 launch.

---

### Post by jbicha on 2012-04-07
The problem with trying to put Evolution 3.4 into a PPA like the GNOME 3 PPA is that there are a lot of reverse-depends that would need to be rebuilt for evolution-data-server 3.4. And any time any of those packages get updated, it would need to be built again for the PPA so it's a whole lot of work.

What is so critical in Evolution 3.4 that you can't just wait for Ubuntu 12.10?

And if you want to build stuff from source, it's easier to use the already existing Ubuntu packaging.

---

