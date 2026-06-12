---
title: "Weird graphics on windows"
date: 2022-11-01
forum: Virtualisation
---

### Post by morphee on 2022-11-01
I installed ubuntu-22.04.1-desktop-amd64 on VirtualBox-7.0.2 on my pc with Windows 10, following a tuto.
All went fine, except on some windows, for example the "save as" popup of Atom or other type of modals, which are completely unreadable :

Did you get this kind of problem already ?
What can I do to solve it ?

---

### Post by morphee on 2022-11-01
this is a screenshot :
[https://ibb.co/mhR0DHn](https://ibb.co/mhR0DHn)

---

### Post by MAFoElffen on 2022-11-01
Wow.

What are the video settings of the Virtual Machine in VirtualBox... And what are the Graphics settings in Ubuntu?

---

### Post by &amp;KyT$0P# on 2022-11-01
> **morphee said:**
>  on some windows, for example the "save as" popup of Atom or other type of modals, which are completely unreadable :

Are all the affected apps GTK4?

---

### Post by morphee on 2022-11-01
> **MAFoElffen said:**
> Wow.

What are the video settings of the Virtual Machine in VirtualBox... And what are the Graphics settings in Ubuntu?

VM :
128 MB video memory
1 screen
VMSVGA with 3D acceleration enable

Ubuntu :
whatever the screen resolution
I did not change any other parameters, do you need something more ?

> **halogen2 said:**
> Are all the affected apps GTK4?
How can I test that ?
(can you tell some software to try with ?)

For now, I noticed the problem with :
- Atom
- the installation modals of XAMP

I did not see (so far) the problem with :
- LibreOffice Writer or Calc
- Firefox (except on bookmark and historic popup title, but the inside is ok)
- Geary

---

### Post by &amp;KyT$0P# on 2022-11-01
> **morphee said:**
> How can I test that ?

How to check whether an app uses GTK 4 depends how you have the app installed.  Probably simpler to just say, if they are GTK 4 apps, I have seen similar and was able to work around it: open a Terminal and run
```
export LIBGL_ALWAYS_SOFTWARE=1
```
then run an affected app from that same terminal window.  Does this help the issue in your case?

---

### Post by morphee on 2022-11-01
> **halogen2 said:**
> Does this help the issue in your case?
Unfortunately, no... :(

---

### Post by morphee on 2022-11-01
> **halogen2 said:**
> How to check whether an app uses GTK 4 depends how you have the app installed
Do you mean that, if I installed Atom from Ubuntu app store, the problem may be there.
If so, if I uninstall it then install it from the terminal, that can solve the problem ?

---

### Post by morphee on 2022-11-09
After lot of tests on parameters and investigations, it seems that using ubuntu-20.04.5-desktop-amd64 solved my issue.

---

