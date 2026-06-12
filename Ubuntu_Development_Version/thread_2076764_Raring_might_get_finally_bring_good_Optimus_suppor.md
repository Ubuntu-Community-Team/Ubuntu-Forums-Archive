---
title: "Raring might get finally bring good Optimus support"
date: 2012-10-26
forum: Ubuntu Development Version
---

### Post by Starks on 2012-10-26
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-hybrid-graphics](https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-hybrid-graphics)

Hopefully this gets a few minutes during the X meeting.

---

### Post by grahammechanical on 2012-10-27
[http://bumblebee-project.org/]("http://bumblebee-project.org/")

For those who need to know.

---

### Post by ELD on 2012-10-28
> **grahammechanical said:**
> [http://bumblebee-project.org/]("http://bumblebee-project.org/")

For those who need to know.

Works well but it would be good to get more native support.

---

### Post by Starks on 2012-10-29
> **grahammechanical said:**
> [http://bumblebee-project.org/]("http://bumblebee-project.org/")

For those who need to know.

```
eric@gensokyo:~$ glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 9.1-devel
OpenGL shading language version string: 1.30
OpenGL extensions:
eric@gensokyo:~$ DRI_PRIME=1 glxinfo | grep OpenGL
OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NVC3
OpenGL version string: 3.0 Mesa 9.1-devel
OpenGL shading language version string: 1.30
OpenGL extensions:
```

Works right out of the box with 12.10

---

### Post by ELD on 2012-10-31
> **Starks said:**
> ```
eric@gensokyo:~$ glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 9.1-devel
OpenGL shading language version string: 1.30
OpenGL extensions:
eric@gensokyo:~$ DRI_PRIME=1 glxinfo | grep OpenGL
OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NVC3
OpenGL version string: 3.0 Mesa 9.1-devel
OpenGL shading language version string: 1.30
OpenGL extensions:
```

Works right out of the box with 12.10

That's open source drivers, you currently wouldn't be able to use the closed drivers without something like Bumblebee.

---

### Post by Starks on 2012-11-04
I updated the spec I linked earlier.

There is now a supplemental spec for the UI.

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-hybrid-graphics](https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-hybrid-graphics)
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-hybrid-graphics-user-experience](https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-hybrid-graphics-user-experience)

---

### Post by Starks on 2013-02-14
Nvidia's PRIME helpers are pretty much guaranteed for Linux 3.9

All of the necessary code has landed in the needed for-next trees

[http://cgit.freedesktop.org/~airlied/linux/commit/?h=drm-next&id=89177644a7b6306e6084a89eab7e290f4bfef397](http://cgit.freedesktop.org/~airlied/linux/commit/?h=drm-next&id=89177644a7b6306e6084a89eab7e290f4bfef397)

[http://git.linaro.org/gitweb?p=people/sumitsemwal/linux-dma-buf.git;a=commit;h=90b6e90cb03352a352015ca213ac9f4fab3308f3](http://git.linaro.org/gitweb?p=people/sumitsemwal/linux-dma-buf.git;a=commit;h=90b6e90cb03352a352015ca213ac9f4fab3308f3)

If nothing else is in the way, Nvidia will be able to use dma-buf through these helpers for Ubuntu 13.10 Sharting Shrew.

---

