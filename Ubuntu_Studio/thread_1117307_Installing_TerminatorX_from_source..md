---
title: "Installing TerminatorX from source."
date: 2009-04-05
forum: Ubuntu Studio
---

### Post by B4RR13N705 on 2009-04-05
Hi, i downloaded terminatorx's source from the web page:
> 
[http://www.terminatorx.org/](http://www.terminatorx.org/)

I installed all the requirements:
> 
LADSPA
LIBXML
LIBCAP
LIBLRDF
LIBAUDIOFILE
LIBVORBIS
OGG123
MPEG AUDIO DECODER
MPG321

When i run 
```

sudo ./configure

```
At the end it says:
```

configure: error: ** DGA not installed or broken **

```
In the web page it says:
> 
XFree86 with DGA/DirectMouse support. DGA should be available in all XFree86 releases after 3.3, but not every X-server provides DGA, so please check that your X-server has that feature. 

I don understand too well this DGA stuff, so please help me to install it!

---

### Post by Stochastic on 2009-04-06
Why don't you just install it from the repositories?
```
sudo apt-get install terminatorx
```
or use add/remove programs (or synaptic package manager).

If you really do have some need to rebuild the exact same version of the software, then you can get your build dependencies installed by installing all of these libraries: ```
sudo apt-get install mpg321 vorbis-tools sox ladspa-sdk libaudiofile-dev libvorbis-dev libglib2.0-dev libgtk2.0-dev libmad0-dev libxml2-dev libatk1.0-dev libpango1.0-dev zlib1g-dev libasound2-dev scrollkeeper liblrdf0-dev libjack0.100.0-dev libcap-dev  libxxf86dga-dev libxext-dev libxi-dev libx11-dev libsm-dev libice-dev libxt-dev
```
That listing was taken from the Hardy repository source package's build-depends listing.

I think the libxxf86dga-dev one is the specific package you're missing right now.

Hope that helps.

---

### Post by B4RR13N705 on 2009-04-06
Hi, I installed libxxf86dga-dev and i conpiled correctly thanx!

---

