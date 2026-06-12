---
title: "freecycle (beatslicer) - can't get it work"
date: 2008-07-10
forum: Ubuntu Studio
---

### Post by Capoeira on 2008-07-10
does anyone use freecycle in (x)ubuntu? it does't work here.
when i try to open a soundfile it always shows this message: "this file seems broken". i tried several files. all other audio-software is working fine.
i reported a bug already but no responses: [https://bugs.launchpad.net/ubuntu/+source/freecycle/+bug/246599](https://bugs.launchpad.net/ubuntu/+source/freecycle/+bug/246599)


i am using: Ubuntu 8.04.1 Release: 8.04 (with KDE 4.1 beta2)

i tried both versions, from official repositrie (hardy) which is "0.6.1alpha-2ubuntu1" and from intrepid-repositrie which is "0.6.1.1 alpha-1"

any help?

PS: does anybody use Recycle for windows with Wine? i can't get it to run too. i would prefer to use freecycle though

---

### Post by Stochastic on 2008-07-10
First, don't use any other repositories (such as intrepid) than the version of the system you're on!!!!!!  You will break things, that without the proper experience you won't be able to fix.

Second I just tried to open a wav file with Hardy's repository version, and had no troubles with it.  I'm guessing that your libsndfile package needs re-installation.  Go into Synaptic package manager, find libsndfile1 and mark it for re-installation (you may also want to do the same for freecycle at the same time).

---

### Post by Capoeira on 2008-07-10
> **Stochastic said:**
> First, don't use any other repositories (such as intrepid) than the version of the system you're on!!!!!!  You will break things, that without the proper experience you won't be able to fix.

didn't know that. perhaps thats why my libsndfile1 is broken !?
i added intrepid only to install newer version of Audacity because of the bug of hardy version (2 effects missing)

> **Stochastic said:**
> Go into Synaptic package manager, find libsndfile1 and mark it for re-installation (you may also want to do the same for freecycle at the same time).

i have already tried this before.
tried it again now with downgrading freecycle to hardy version too but still the same problem.
i had only 2 packages from intrepid installed: audacity and freecycle - i downgraded them to hardy version but still can't open any file.
all other programs that use libsndfile1 are working fine (audacity, rosegarden,....)

you think that the installing of audacity from intrepid broked anything?
i installed this before installing freecycle the first time (from hardy)

very strange

---

### Post by Stochastic on 2008-07-10
> **Capoeira said:**
> didn't know that. perhaps thats why my libsndfile1 is broken !?
i added intrepid only to install newer version of Audacity because of the bug of hardy version (2 effects missing)

To get a newer version of any software (for example Audacity), the best route is to go through the internet and compile from source.  Changing repositories (especially to a development repository) can deeply ruin your system, because one package may have various dependencies, all of which will be installed in order to install the mother package.  For instance freecycle depends on libsndfile1 (which happens to be the same version in both hardy and intrepid - right now anyways), but libsndfile1 depends on libc6 (core C libraries) that is a newer version in Intrepid.  Luckily, libsndfile1 in Intrepid still only requires libc6 >= 2.6-1 and Hardy's is 2.7-somthing, so chances are this wasn't upgraded (thank your stars for that).  But figuring out which packages were upgraded can be a nightmare to fix.

IF you are ABSOLUTELY SURE that the only two packages that were installed while you had Intrepid repositories were audacity and freecycle, then you can safely revert those packages and be glad this lesson didn't cause any permanent damage.  

HOWEVER, IF there's EVEN A SLIGHT CHANCE that when you did 'apt-get install audacity' apt-get told you that three other packages would be installed, and you said yes... well then you may have successfully borked your install (unless you can magically recall which packages those were, and revert them back to the hardy versions).  It may not be libsndfile1 that's messed, that was just an educated guess.  

You may want to jump onto the freecycle mailing list and ask them what could be causing that particular error (explain that you've been moving between repositories, and you're wondering what file(s) freecycle uses to do it's file check - that will most likely be the offending Intrepid package you need to downgrade).

---

### Post by Capoeira on 2008-07-10
> **Stochastic said:**
> 
You may want to jump onto the freecycle mailing list and ask them what could be causing that particular error (explain that you've been moving between repositories, and you're wondering what file(s) freecycle uses to do it's file check - that will most likely be the offending Intrepid package you need to downgrade).

i already contacted the mailing list. they told me that it is realy the libsndfile package who is sending the error message - this is what he wrote: "This error is displayed when libsndfile returns a null pointer upon file 
opening. Did you try to open those files with audacity ? (which uses 
libsndfile too) This would help to find out if the problem is 
ubuntu-libsndfile related .."
our mailings: [http://lists.nongnu.org/archive/html/freecycle-users/2008-07/index.html](http://lists.nongnu.org/archive/html/freecycle-users/2008-07/index.html)

> **Stochastic said:**
> 
IF you are ABSOLUTELY SURE that the only two packages that were installed while you had Intrepid repositories were audacity and freecycle

I AM absolutely sure. i can tell you why: i used Adept-Manager to install these. it shows me all the packages that it will install/update befor do so. AND i made sure that i didn't upgarde any other package just to not cause any damage to other programs wich use the same dependencies. also i can i can see all the dependencies and even dependencies dependencies in Adept-Manager and they are all hardy version. i even did reactivate the intrepid-repositry now just to mark those two programs for upgrade to see if it wants to upgrade any dependencies but NO - it only wants to upgrade freecycle and audacity packages. So - i am 100% sure

---

### Post by Stochastic on 2008-07-11
Okay here are a few questions at once, please answer all of them thoroughly:
-What system version are you running? (Kubuntu 8.04? Ubuntu 8.04? Xubuntu 8.04? UbuntuStudio 8.04? etc...)
-What kernel? (run the code: 'uname -r' if you're not sure)
-Are you running freecycle with JACK running, or just through alsa (via pulse audio?)?
-What output do you get from these two commands: ```
apt-cache policy freecycle
apt-cache policy libsndfile1
```

---

### Post by Capoeira on 2008-07-11
> **Stochastic said:**
> 
-What system version are you running? (Kubuntu 8.04? Ubuntu 8.04? Xubuntu 8.04? UbuntuStudio 8.04? etc...)

Kubuntu 8.04
> **Stochastic said:**
> 
-What kernel? (run the code: 'uname -r' if you're not sure)

2.6.24-19-generic
> **Stochastic said:**
> 
-Are you running freecycle with JACK running, or just through alsa (via pulse audio?)?
i tried both but with no succes.
anyways: when i run it with jack running its not shown up in jack
> **Stochastic said:**
> 
-What output do you get from these two commands: ```
apt-cache policy freecycle
apt-cache policy libsndfile1
```
capoeira@capoeira-desktop:~$ apt-cache policy freecycle                                    
freecycle:                                                                                 
  Instalado: 0.6.1alpha-2ubuntu1                                                           
  Candidato: 0.6.1alpha-2ubuntu1                                                           
  Tabela de versão:                                                                        
 *** 0.6.1alpha-2ubuntu1 0                                                                 
        500 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe Packages                           
        100 /var/lib/dpkg/status                                                           
capoeira@capoeira-desktop:~$ apt-cache policy libsndfile1                                  
libsndfile1:                                                                               
  Instalado: 1.0.17-4                                                                      
  Candidato: 1.0.17-4                                                                      
  Tabela de versão:                                                                        
 *** 1.0.17-4 0                                                                            
        500 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/main Packages                               
        100 /var/lib/dpkg/status  


-------

i found this thread; i get the same message as output in Konsole: "Oh, anyways we need no sound..Aren't we?":

[http://www.nabble.com/Freecycle----how-to-get-this-working-on-Ubuntu-Debian-td17558769.html](http://www.nabble.com/Freecycle----how-to-get-this-working-on-Ubuntu-Debian-td17558769.html)

---

### Post by Capoeira on 2008-07-13
só as nobody here can help me, nor launchpad nor freecycle developer;
anybody knows how to get ReCycle working with Wine?
Any other program i can use?

---

### Post by Stochastic on 2008-07-15
I'd say the next step for you would be to compile freecycle from source.

Those version numbers are the same that I have.  I am running the Linux-rt kernel and have an UbuntuStudio install, rather than your Kubuntu install, so it's also possible that some difference between your system and my system is what's causing your bug.

I did a little more testing of freecycle and I can't get it to play back anything, but it opens files fine, analyzes them well, splits them etc..  So I'd hench my bets on it being a poorly maintained package; thus compiling from source is a good bet (particularly if other libsndfile apps are working fine for you).

---

### Post by Capoeira on 2008-07-15
that no sound issue was a problem with alsa and was resolved with newer versions.

i am running the linux-rt Kernel now too but with same result.

perhaps i'll try compile it from source, thanks

---

