---
title: "Trying to install newest freebob...wont work"
date: 2008-05-17
forum: Ubuntu Studio
---

### Post by TheDriller on 2008-05-17
hi, im trying to install the latest Freebob.
libfreebob-1.0.11

when i type ./configure i get :

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.


i've checked the dependancies and it seems to be fine but no matter what i do this always happens??

what do i need to do to get this to work??

---

### Post by robeast on 2008-05-17
sudo?

---

### Post by Stochastic on 2008-05-18
where are you checking your dependencies against?  do you have gcc installed?  You shouldn't need sudo to do ./configure

Edit: A quick warning if this is the first time you've compiled from source (i.e. you don't have gcc installed) then you should really consider going through the process a few times with less critical software.

---

### Post by TheDriller on 2008-05-18
> **Stochastic said:**
> where are you checking your dependencies against?  do you have gcc installed?  You shouldn't need sudo to do ./configure

Edit: A quick warning if this is the first time you've compiled from source (i.e. you don't have gcc installed) then you should really consider going through the process a few times with less critical software.

i checked the listed dependancies in the readme file against what i see in the Synaptic Package Manager. although i could be wrong due to n00bism.

i'll check the gcc when my updates finish :)

---

### Post by Stochastic on 2008-05-18
Quite often the readme file will assume you have a compiler installed and since a specific compiler isn't needed, calling gcc a dependency is kinda inaccurate.  Once again I should warn you not to use your sound driver as a first-time compiling experience.  Start by compiling an end user app.

---

