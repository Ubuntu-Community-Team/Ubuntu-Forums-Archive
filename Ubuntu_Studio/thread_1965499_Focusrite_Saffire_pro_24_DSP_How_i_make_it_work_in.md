---
title: "Focusrite Saffire pro 24 DSP How i make it work in ubuntu precise pangolin"
date: 2012-04-25
forum: Ubuntu Studio
---

### Post by Splashmania on 2012-04-25
Ok i gonna describe the steps what i did and tell me what is wrong and how make it better.

-The first thing i did is uninstall the ffado and jackd what i has following [http://subversion.ffado.org/wiki/AvoidingParallelInstallations](http://subversion.ffado.org/wiki/AvoidingParallelInstallations) to have a clean installation  

-The second is go to [http://packages.ubuntu.com/precise/libs/libffado2](http://packages.ubuntu.com/precise/libs/libffado2) and get manually the sources of [libffado_2.0.99+svn2019.orig.tar.bz2]<[http://archive.ubuntu.com/ubuntu/pool/main/libf/libffado/libffado_2.0.99+svn2019.orig.tar.bz2](http://archive.ubuntu.com/ubuntu/pool/main/libf/libffado/libffado_2.0.99+svn2019.orig.tar.bz2)>  

-After i've installed from synaptic all the packets related with ffado and then just uninstalled again just to have the packets in /var/cache/apt/archives/ then i've searched the ffado packets and opened the ffado-mixer-qt4_2.0.99+svn2019-1ubuntu1_all.deb with the compressor and edited manually the saffire-dice.py changing the line of:  ```
if self.configrom.getModelName() == "SAFFIRE_PRO_24"
``` to ```
if self.configrom.getModelName() == "SAFFIRE_PRO_24DSP"
``` 
(Really i was looking for the src's but discovered what aren't inside) anyway at the end nothing matters.  

-Then i go again to synaptic to install all the packets again, then as espected the command $ ffado-test Discover was giving the error of the firmware 04. ok  

-Now i come back to the svn downloaded and extract his files and searched for the  saffire_pro24.cpp file and edit the line of: ```
 « if (tmp[0] != 0x00010004 ) » to « if (tmp[0] != 0x00010008 ) »
```  Did the same with the file about the mixer.  -and install the sources over the original one with:  ```
$ cd libffado-2.0.99+svn2019;  scons PREFIX=/usr;  sudo scons install;  cd ..
```  
Ok, then i go to try if the quyck-fix is working  $ ffado-test Discover (and... Damm is working!!)  

-Then i tried open the ffado-mixer but fails (****) 

-i go to look for the mixer to the /usr/share/ffado-mixer-qt4/ffado/mixer/saffire_dice.py and edited again in the same way because was changed with the original i don't know why  
-Try again, and working (rules)  

-Then i've installed directly from the synaptic the qjackctl with all his dependencies (and haha is working perfect)  

-Now i go to try if work with a usually song with vlc player with the extra for jack but dont works (mmm...)  

-opened the connection tab in qjackctl to see if is detected and conected, but look pulse-audio is routed in jack (then i remember what i installed the packet to do it, great!)  -another try but now with rithmbox and damm it works its playing!! (with the hint i can't shut down jack because pulse is always connected) 

-Now i have full audio on the pc and i am writing this listening notorious big.  

PD. Excuse me about if i have poor english but i was wooried trying to remember the steps what i did. PD. I understand what is a little dirty fix but is the first time what i get this interface working in ubuntu and i suposse what also can help to be supported in the official way.  
Cheers fo reading =) 
Pepe Pérez 
Splashman

---

