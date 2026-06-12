---
title: "Virtualbox OSE not working on Ubuntu8.04"
date: 2008-08-16
forum: Virtualisation
---

### Post by 7raTEYdCql on 2008-08-16
When i tried to install VBox from the add or remove program list, and after running it i get an error message with regard to kernal-modules not being supported. Any help???

---

### Post by circlemaster on 2008-08-16
Are you running 2.6.24-20 kernel? Search Synaptic for "virtualbox" and install the virtualbox-ose-modules for your kernel.

---

### Post by 7raTEYdCql on 2008-08-16
I dont know which kernel i am using. How do i find that out.

---

### Post by dje on 2008-08-16
post the output of this from a terminal (applications >> accessories >> terminal):
```
uname -a
```

dje

---

### Post by aceole on 2008-10-02
Ok this is the same trouble that I was having. till I found the answer
> sudo chmod 666 /dev/vboxdrv
and you shoulb be all set and ready to go. I was unable to continue the install I made at the start, when I came across the error so i removed that one, started a new and Wam. All worked Great.
Hope it works

---

