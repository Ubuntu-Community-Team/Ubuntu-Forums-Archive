---
title: "AMD+NVIDIA Problem:"
date: 2011-12-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kuvanito on 2011-12-02
i want to try the alpha ver of precise in this HP Pavilion Desktop with an AMD processor and a  Nvidia GE Force 6150 SE but i am having problems after installation,i just get a blank screen.i switched the hard drive to my intel machine and it boots up no problem,how ever i get an ugly gnome 3 shell.i am wondering if any one else is having such a problem.thanks guys...

---

### Post by ronacc on 2011-12-02
dkms has been trying to install the wrong driver for me , at the blank screen use ctrl+alt+F1 to get to a terminal , login and run ```
 sudo apt-get install nvidia-current 
``` . if that don't do it download the 290.10 driver direct from nvidia and hand install it .

---

### Post by Redblade20XX on 2011-12-02
I have the same setup. Pavillion desktop, amd processor and nvidia 6150le card. Have you installed any other versions of Ubuntu and obtained the same results? I have. In order to get it past the black screen I had to pass the kernel command "nomodeset" even after installing the nvidia drivers for the card. Hopefully this helps!
:)

- Red

---

### Post by kuvanito on 2011-12-02
yes i have,oneiric actually works great but no the alpha pangolin.well at least i have ubuntu...:P

---

### Post by grahammechanical on 2011-12-02
You could try to get precise the way I did it. I already had 11.10 in a spare partition that I used for testing and I converted to precise with a few commands. My settings were picked up and my Nvidia driver was updated. Everything worked and was very stable.

This are the commands

```
sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
```

```
sudo apt-get update && sudo apt-get dist-upgrade
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

To verify that you have the Precise kernel installed you can enter:

```
lsb_release -a
```

Regards.

---

