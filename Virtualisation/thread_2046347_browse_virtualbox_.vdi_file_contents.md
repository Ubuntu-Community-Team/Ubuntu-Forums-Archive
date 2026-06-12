---
title: "browse virtualbox .vdi file contents?"
date: 2012-08-22
forum: Virtualisation
---

### Post by bobmct on 2012-08-22
:confused:
I'm running standard ubuntu 12.04 with virtualbox installed and a vm running Windoze XP Pro.  Is there a *nix mechanism to allow the host to open and browse/access the vm's .vdi file?  Searches on many forums as well as google provide some (older) ideas none of which seem to work. 

The reason is that I need to rename one of the startup files in the Windoze instance PRIOR to it starting.

Just wondering if anyone has had success with this?

Thanks -

---

### Post by Cheesemill on 2012-08-23
[http://bethesignal.org/blog/2011/01/05/how-to-mount-virtualbox-vdi-image/](http://bethesignal.org/blog/2011/01/05/how-to-mount-virtualbox-vdi-image/)

---

### Post by Rebelli0us on 2012-08-27
You can "attach" the .vdi to another VM and access it normally. Or you can temporarily "clone" it and access it from the cloned OS.

---

### Post by techBarns on 2013-07-02
[COLOR=#333333][FONT=Helvetica Neue]Use VMXRay [/FONT][/COLOR][([http://www.vmxray.com](http://www.vmxray.com))]("http://www.vmxray.com/")[COLOR=#333333][FONT=Helvetica Neue] to explore your virtual disk image (vdi) inside your browser. You can view the content and extract files from the virtual machine disk with simple browser clicks. VMXRay's new version is super fast and is powered by emscripten [/FONT][/COLOR][([https://github.com/kripken/emscripten/](https://github.com/kripken/emscripten/))]("https://github.com/kripken/emscripten/")

> **Rebelli0us said:**
> You can "attach" the .vdi to another VM and access it normally. Or you can temporarily "clone" it and access it from the cloned OS.

---

