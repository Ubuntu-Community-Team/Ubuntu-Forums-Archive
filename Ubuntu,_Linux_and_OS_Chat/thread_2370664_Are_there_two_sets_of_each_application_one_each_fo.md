---
title: "Are there two sets of each application one each for Wayland and X session."
date: 2017-09-06
forum: Ubuntu, Linux and OS Chat
---

### Post by kagashe on 2017-09-06
I am trying to learn about Wayland Display Server.

I understand that each application has to be compiled for Wayland otherwise it runs on Xwayland.

But if I chose X session the same application can be used.

I would like to know whether an application which is compatible for Wayland has two sets the other one to run on X session.

or it could be as follows:
The application which is compatible for Wayland when run on X session detects that there is no Wayland and could also run on X.

Which way it is?

Kamalakar

---

### Post by kc1di on 2017-09-07
It's my understanding that not all packages need to be repackaged, only those such as drivers and some video, Etc. most package won't care if your using x.org or wayland. 
I may be wrong about that but someone will most likely be along that will know for sure.

---

### Post by grahammechanical on 2017-09-09
Do not consider me an expert, but I think that the initial concern was with certain applications that interacted directly with the Xserver. I think that Libreoffice falls into this category.

As far as I can tell Ubuntu is still using the XServer up to the login screen. Which from 17.10 onwards will be provided by GDM. The switch to a Wayland compositor comes after we login.

At some point in the future XServer will be completely replaced. Developers of applications that at present interact directly with the XServer will have to bite the bullet and recode the application to interact with the Wayland compositor. If they have not already done so.

Just my thoughts on this matter.

Regards

---

### Post by lammert-nijhof on 2017-09-11
What about the existing video legacy drivers from e.g. Nvidia?

---

