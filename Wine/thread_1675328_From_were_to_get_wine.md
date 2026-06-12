---
title: "From were to get wine"
date: 2011-01-25
forum: Wine
---

### Post by wowman09 on 2011-01-25
HI im new on ubuntu, i need help to get wine to can execute .exe files.
I have Ubuntu 9.10 from were i can take wine?
pls help me !!

---

### Post by owaiskhan11 on 2011-01-25
In the system --> administration tab select synaptic package manager.Under the settings tab select repositeries and enable all of the.In the terminal type sudo apt-get install update.the after the update type 
sudo apt-get install wine

---

### Post by Joe of loath on 2011-01-25
Even easier - 

Applications -> Ubuntu software center

Search for WINE

click 'install'

Done :D

---

### Post by Kirboosy on 2011-01-25
Or! :D (try the other people's suggestions first)

In a terminal type the following (copy and paste works too ;) )

```
*sudo add-apt-repository ppa:ubuntu-wine/ppa*
```Adds the most recent version of WINE
```
sudo apt-get update
```Updates your repositories

```
sudo apt-get  install wine1.3
```The newest version of WINE works the best. 


~Caboose

---

### Post by Halzen on 2011-01-25
> **Caboose885 said:**
> ```
sudo apt-get  install wine1.3
```The newest version of WINE works the best. 


~Caboose

Slow down there, tiger. The development version of a program isn't the safest recommendation for a new Linux user. 1.2.2 stable will do just fine.

---

### Post by Kirboosy on 2011-01-25
> **Halzen said:**
> Slow down there, tiger. The development version of a program isn't the safest recommendation for a new Linux user. 1.2.2 stable will do just fine.

Depends on what he is trying to run. I don't have stability issues with Wine. (And I'm by no means a wine Guru) I guess if he installs 1.2.2 and that doesn't work he can try upgrading to the development

---

### Post by Halzen on 2011-01-25
> **Caboose885 said:**
> Depends on what he is trying to run. I don't have stability issues with Wine. (And I'm by no means a wine Guru) I guess if he installs 1.2.2 and that doesn't work he can try upgrading to the development

That's precisely how I look at it: if stable works for you, ducky. If stable is missing something that development offers, and you need it, THEN go after it. I'm all for strongly supported beta software, but not for something as essential as Wine unless absolutely necessary. Just my wonky philosophy at work. :p

---

