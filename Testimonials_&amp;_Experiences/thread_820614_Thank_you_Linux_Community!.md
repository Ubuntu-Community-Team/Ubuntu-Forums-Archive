---
title: "Thank you Linux Community!"
date: 2008-06-06
forum: Testimonials &amp; Experiences
---

### Post by professorTHC on 2008-06-06
Lol, im goign to thank the linux community on these Posters behalf..i bet you guys have to deal with these XP-Ubuntu users real often adn i can imagine how old it can get, but thank you for sticking around and helping us out. i bet you dont get these posts too often =P


*edit* P.S. I figure i might as well throw in my issue with flsh videos not working like youtube. i have all the plugins i think i need installed, inlcuding the non free one, and it still says i need to install the latest one (which is installed)

---

### Post by ukripper on 2008-06-06
> **professorTHC said:**
> Lol, im goign to thank the linux community on these Posters behalf..i bet you guys have to deal with these XP-Ubuntu users real often adn i can imagine how old it can get, but thank you for sticking around and helping us out. i bet you dont get these posts too often =P


*edit* P.S. I figure i might as well throw in my issue with flsh videos not working like youtube. i have all the plugins i think i need installed, inlcuding the non free one, and it still says i need to install the latest one (which is installed)

You are most Welcome!

Have you enabled medibuntu repositories?
If not then try this link
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Fedz on 2008-06-07
professorTHC: did you manage to get your flash issue sorted? :-)

---

### Post by wolfen69 on 2008-06-07
> **professorTHC said:**
> i bet you guys have to deal with these XP-Ubuntu users real often and i can imagine how old it can get,

very much so. 

anyway, welcome!

---

### Post by professorTHC on 2008-06-08
unfortunately no, i havent figured it out. any help would be appreciated =)

---

### Post by ukripper on 2008-06-09
> **professorTHC said:**
> unfortunately no, i havent figured it out. any help would be appreciated =)

Follow the following steps:
1. For this,  use the medibuntu repository. 
 
```
sudo gedit /etc/apt/sources.list
```

   2. Add the following lines to it for hardy:

deb  [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

   3. Import medibuntu's key and update the local package list



```
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```

     
   5. Now install the codec we need:



```
sudo apt-get install non-free-codecs
```

---

### Post by hyper_ch on 2008-06-17
for watching DVDs also install libdvdcss2

---

### Post by stchman on 2008-06-17
> **professorTHC said:**
> Lol, im goign to thank the linux community on these Posters behalf..i bet you guys have to deal with these XP-Ubuntu users real often adn i can imagine how old it can get, but thank you for sticking around and helping us out. i bet you dont get these posts too often =P


*edit* P.S. I figure i might as well throw in my issue with flsh videos not working like youtube. i have all the plugins i think i need installed, inlcuding the non free one, and it still says i need to install the latest one (which is installed)

Watching YouTube using Firefox is a breeze.

```
sudo apt-get install flashplugin-nonfree
```

That is all you need.  YouTube videos work well using FF3.

---

