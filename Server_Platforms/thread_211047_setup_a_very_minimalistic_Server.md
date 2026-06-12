---
title: "setup a very minimalistic Server"
date: 2006-07-07
forum: Server Platforms
---

### Post by mht on 2006-07-07
is there any way to install a very minimal ubuntu server ? just kernel and bash and iproute and apt ?

any idea ? dont have enough time to purge and remove package and its headaches ](*,)

---

### Post by christhemonkey on 2006-07-07
You can do a server-expert install from the server cd i believe, in which you can select exactly what you want.

---

### Post by lamego on 2006-07-07
The default ubuntu server install is already minimalistic ...

---

### Post by mht on 2006-07-08
well , what do you mean by minimalistic ? :D 
its very big , what i need is a server optimized kernel and bash and common binaries like iproute2 also apt-get to install latest ssh server , it should be something about 30-40 MB and this is what i name "minimalistic" , and ubuntu server default install is not minimalistic

i've tested expert mode and also alternative Cd , but both of them installing lots of packages without my permission ! yes i can ask them to install or not to install some extra packages , but the base install is very big ,

any hint ?

---

### Post by falcon15500 on 2006-07-08
Wouldn't really be Ubuntu then, would it?  Ubuntu is a distribution - a collection of packages to make a whole.  Sounds like what you want is not Ubuntu, just a kernel etc etc etc.

falc

---

### Post by nagilum on 2006-07-08
You can get a base system which is quite small when using the tool deboostrap. It installs a very basic minimal system into a directory and lets you fine-tune the packages that are to be installed. Although depedencies are still resolved so a minimum set of packages remains (quick check for dapper: ~ 110 MB). Deleting some locales and documentation will give you an extra of ~ 20 MB of saved space.
Debootstrap does not configure this base system in any way, it's up to you to setup the networking, make it bootable or even install the kernel (no kernel is installed by default). After a successful bootup into the minimal system the base-config tool will take care of the rest (if you installed it).

For even smaller systems the dependency checking of debootstrap can be disabled. But this essentially breaks dpkg, whenever you choose to install packages later it will complain and try to install the missing packages. To get a really slim system there's no way around setting everything up manually, like LinuxFromScratch or the like.

---

### Post by mht on 2006-07-08
so what whould you guys do ?
is there any compact and small yet clean distro ready for server ?
i cannot make a LFS , and want to use a debian , ubuntu or even gentoo based , and dont know how .

as said before , i want a server ready kernel and some basic binary utils and iproute2 , any entry point ?

---

### Post by lamego on 2006-07-08
The ubuntu install is "minimalistic" for a server install, you are looking for a minimal linux system which is not typically used for servers, its more like for embedded systems.
Probably something like "damn small linux" fits best your needs.

---

### Post by clparker on 2006-07-08
> **lamego said:**
> The default ubuntu server install is already minimalistic ...

I would have to agree...

---

### Post by Iowan on 2006-07-08
Depending on how small you want/need, there is DSL (Da** Small Linux) or you could check FREESCO (a single floppy router).

---

