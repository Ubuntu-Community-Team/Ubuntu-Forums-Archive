---
title: "Ichthux Dependencies"
date: 2011-03-13
forum: Ubuntu Christian Edition
---

### Post by tumelo on 2011-03-13
Does anybody know what's up with Ichthux and all of its dependencies and broken packages? 
Is it just obsolete at this point or is it still possible to get Ichthux? If anybody knows how to bypass the dependencies then please let me know.

Same with ubuntu-ce, can't install it because of unmet dependencies and broken packages. Mainly opensong.

---

### Post by hoobuntu on 2011-03-18
I've been running into the same issue on both of those as well. Anyone have ideas?

---

### Post by tumelo on 2011-03-23
I'm slowly hacking away at the dependencies for ubuntu-ce one by one. I'll let you know if I have any success.

---

### Post by ubu777 on 2011-04-11
](*,)  is sad to say ichthux is broken.

---

### Post by daniel9876 on 2011-04-27
Hallo
I asked about the problems, Ralph Janke, who cares about Ichthux and he wrote :"I am not aware of any issue with the releases named. I had tested them before release and they worked at the time.
I need to check them out in a VM, but will not be able to do that until 
business tax season is over. "

greetings

---

### Post by jonathonblake on 2011-04-27
> **daniel9876 said:**
> 
"I am not aware of any issue with the releases named. I had tested them before release and they worked at the time."

The following is what I get, when I select "ichthux-desktop" for installation. (Xenix 9.10 updated to xubuntu 10.4 updated to kubuntu 10.10, with the Ubuntu Jewish, Ubuntu Christian, Sabily, and Edubuntu metapackages installed.)

> 
ichthux-desktop:
 Depends: foomatic-db but it is not going to be installed
 Depends: hotkey-setup  but it is not installable
 Depends: ichthux-docs but it is not going to be installed
 Depends: kde-printer-applet  but it is not installable
 Depends: kdebluetooth  but it is not installable
 Depends: kio-locate  but it is not installable
 Depends: kwin  but it is not installable
 Depends: usplash but it is not going to be installed
 Recommends: openoffice.org but it is not going to be installed

I'm not sure when "at the time" refers to. However, it has been at least since 10.4 was released, that Ichthux desktop has generated messages similar to the above.

To be fair, about a quarter of the packages in both the Ubuntu Jewish metapackage, and the Ubuntu Christian metapackage generate similar errors.

jonathon

---

### Post by daniel9876 on 2011-04-28
Yes, I tried it too with installed versions of ubuntu and kubuntu 9.04/ 9.10/ 10.04 and 10.10 but with no success.
I hope it will be work with 11.04.

---

