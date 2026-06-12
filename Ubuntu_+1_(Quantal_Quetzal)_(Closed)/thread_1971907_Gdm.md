---
title: "Gdm"
date: 2012-05-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Miykel on 2012-05-03
G'Day;  If I want to install GDM should I purge lightdm first ??

Regards Miykel

---

### Post by effenberg0x0 on 2012-05-03
No, there's no need to remove lightdm. Ubuntu config will be set to use gdm automatically. 

Regards,
Effenberg

---

### Post by ventrical on 2012-05-03
What I did on a machine  right next to me that had  been working since a Natty install was install another desktop manager (and I forget now but I didn't choose GDM) from synaptic, but I had also downloaded Xubuntu-desktop previously. So I have this basic desktop manager and still have lighdm and untiy-greeter installed.

  Actually I forget what I did. I'll have to find out what desktop manager I have in there. It may have something to do with xubuntu. Sorry if I have confused this.

Edit: Ok I think what I have is some sort of lighdm fall back that looks like GDM, but it's not.

On a machine with Unity 3D and Nvidia GF210 I had just purged lightdm but I think unity-greeter will go with it.

 I'll check the history of my other installs.

---

### Post by meborc on 2012-05-03
> **ventrical said:**
> What I did on a machine  right next to me that had  been working since a Natty install was install another desktop manager (and I forget now but I didn't choose GDM) from synaptic, but I had also downloaded Xubuntu-desktop previously. So I have this basic desktop manager and still have lighdm and untiy-greeter installed.

  Actually I forget what I did. I'll have to find out what desktop manager I have in there. It may have something to do with xubuntu. Sorry if I have confused this.

I want some of what you have been eating :D :lolflag:

---

### Post by ventrical on 2012-05-03
> **effenberg0x0 said:**
> No, there's no need to remove lightdm. Ubuntu config will be set to use gdm automatically. 

Regards,
Effenberg


There it is .. thanks for the reminder.

---

### Post by ventrical on 2012-05-03
> **meborc said:**
> I want some of what you have been eating :D :lolflag:

  I live only a stone's throw away from the Fermi II reactor and I eat lots of Broccoli and Keen-Wah from Peru. So I am not sure exactly which one does it :)

---

### Post by Miykel on 2012-05-03
Thanks Guys.......I think.....maybe....damn.
Regards Miykel

---

### Post by grahammechanical on 2012-05-03
I remember early in PP when LightDM would not let us log in we had to stop lightDM and start GDM.

Correct?

Here are the codes/commands/whatever :)

```
sudo service lightdm stop
```

```
sudo service gdm start
```

Regards.

---

### Post by effenberg0x0 on 2012-05-03
> **grahammechanical said:**
> I remember early in PP when LightDM would not let us log in we had to stop lightDM and start GDM.

Correct?

Here are the codes/commands/whatever :)

```
sudo service lightdm stop
```

```
sudo service gdm start
```

Regards.

Yes, at a point we did had lightdm broken, installing / using gdm was a viable option. 

Regards,
Effenberg

---

