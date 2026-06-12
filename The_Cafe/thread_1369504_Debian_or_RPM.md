---
title: "Debian or RPM"
date: 2010-01-01
forum: The Cafe
---

### Post by Khakilang on 2010-01-01
I notice there is a lot Distro that is base or derive from Debian like Ubuntu and RPM like Fedora. I am not comparing both of them. Just trying to get an idea how they perform and why Distro choose them? Is there a lot of difference between the two?

---

### Post by inclusivedisjunction on 2010-01-01
DEB and RPM files are slightly different methods for packaging programs. The exact differences between them are negligible for most people, and they do not directly influence how a system performs or behaves.

---

### Post by mmix on 2010-01-01
IMHO, about few years ago, .deb is much better than .rpm.
But, these days, both are good.

---

### Post by premamotion on 2010-01-01
I use Fedora also, and I see no difference when using .rpm packeges...

---

### Post by Exodist on 2010-01-01
> **inclusivedisjunction said:**
> DEB and RPM files are slightly different methods for packaging programs. The exact differences between them are negligible for most people, and they do not directly influence how a system performs or behaves.

> **mmix said:**
> IMHO, about few years ago, .deb is much better than .rpm.
But, these days, both are good.

> **premamotion said:**
> I use Fedora also, and I see no difference when using .rpm packeges...
I agree with all 3 above.

The key comes into the package manager, not the package its self (deb or RPM).
Apt for debs has just been a solid contender, where as some using RPMs has had some serious road bumps. But its not the packages fault, its either the packaging persons or the package management system used.

Deb was traditionally the way Debian built their packages.
RPM was traditionally the way Redhat built theirs and many other distros piggybacked on this.
Fedora is opensource RedHat, so it makes sounds sense that theirs isnt screwed up and should in no doubt be just as solid as Debians.

[Here is a line graph breakdown of distros for everyones records showing what distros came from where.]("http://lh5.ggpht.com/_04pMYWw39X4/SrkPu43kLYI/AAAAAAAAAKY/bCkJPiG6rC0/distros.jpg")


Cheers,
Exo

---

### Post by handy on 2010-01-01
Sometimes (rarely) in Arch the installation package is in .rpm or .deb format; in such cases there are little programs that are automatically used to unpack/convert them & then Arch (via yaourt the pacman wrapper used for the AUR) just carries on & installs according to the PKGBUILD file.

NeroLinux is in .rpm format (from memory). 

It seems that these days package management in Linux has become quite well polished, thankfully.

---

### Post by szymon_g on 2010-01-01
> **Koh Kook Loon said:**
> I notice there is a lot Distro that is base or derive from Debian like Ubuntu and RPM like Fedora. I am not comparing both of them. Just trying to get an idea how they perform and why Distro choose them? Is there a lot of difference between the two?

well... rpm's spec files are really nice compared to debian's rules... also building or rpm's is easier and more logic (like: scripts running ldd on every binary, logging results in package's depedencies- in debian you write name of package that suppose to have all necessery binaries), also adding new macros to rpm aren't so hard- and, which is quite important for end-user- rpm's of all important distros supports delta-packages- which is great, it can save ~80% of bandwith (i.e. instead of downloading 100mb updates, it downloads 20mb).
so- for me- RPMs are superior. The biggest drawback of them (well... not exactly of them, its rather fault of developers) is 'depedency hell' (usually when someone tries to install rpm from one distro in another- in Debian situation like that is less common, due to more compatible distros using debs (ubuntu, debian, knoppix), and because of Debian Policies.

@handy
NeroLinux exists in both formats: deb and rpm (same as most closed source applications)

---

### Post by handy on 2010-01-01
> **szymon_g said:**
> 
@handy
NeroLinux exists in both formats: deb and rpm (same as most closed source applications)

I know; I was referring to the way NeroLinux is installed on Arch.

---

### Post by alakazam on 2010-01-01
Does'nt RPM have the advantage of being standardised?

---

### Post by wulfgang on 2010-01-01
I recently went from ubuntu to opensuse(just for change) and the main thing I miss is the deb. package system.

---

### Post by RiceMonster on 2010-01-01
I have never really built a .deb, but I've built a few rpms and I found creating the spec file fairly straight forward. I've heard some people complaining about building debs before, but that's really just what I heard, so it doesn't mean anything at all.

As for using them, I don't find any major differences, talking strictly about dpkg and rpm, rather than yum, apt, etc. However, one nice feature going for rpms right now is delta rpms which really speed up the download time for updates. Delta rpms only contain the part in the rpm that has changed, rather than downloading the entire thing again.

---

### Post by szymon_g on 2010-01-01
> **alakazam said:**
> Does'nt RPM have the advantage of being standardised?

yes- and no: if you would like to install a closed-source package, you will (probably) find it packet in LSB-compatible way- and, therefore, it can be installed on every LSB-compatible distribution. and no- because distros vary- they use different versions of libraries (with doesn't have to be compatible with each other), also they may use different tools after installation (like: adding daemon to default runlevel- should it be done by chkonfig /fedora, centos/ or other tools? or by just creating 'raw' symlinks /where? in /etc/rc.d/* or in different direcotries? etc etc). But, in most cases- packages are compatible in SRC level, i.e- you can, usually without great effort- compile and install (as RPM, not by the 'traditional way') package from one distro in another. And, after all- you can always check (before installation) what sort of script it run- so you can check it and do it by yourself (if rpm's script arent compatible with your distro)- and, after it- you can extract rpm binary content into proper directories and use it as 'normal package'.


> **wulfgang said:**
> I recently went from ubuntu to opensuse(just for change) and the main thing I miss is the deb. package system.

may I ask what was so special in apt-get/aptitude that you miss so much? i found them inferior to zypper (or to poldek /which isn't really popular, but has some really great features/).

> **RiceMonster said:**
> As for using them, I don't find any major differences, talking strictly about dpkg and rpm, rather than yum, apt, etc. However, one nice feature going for rpms right now is delta rpms which really speed up the download time for updates. Delta rpms only contain the part in the rpm that has changed, rather than downloading the entire thing again.

well... rpm has rpm -V ('V' for 'Verification', not for 'Vendetta') feature- thanx that you can quickly verify all packages governed by rpm (i.e. all files that were created by rpm)- and, in case of troubles, you can even apply them /from previously copied DB/ into system that lost them /because you have made mistake with permissions etc/.

---

### Post by blueshiftoverwatch on 2010-01-01
> **wulfgang said:**
> I recently went from ubuntu to opensuse(just for change) and the main thing I miss is the deb. package system.
Same here, kind of. I tried OpenSUSE but went back to Ubuntu because I didn't like the package management. Ubuntu's just works and I don't have tons of problems. But to be fair, I only used it for a few days and didn't really give the system a chance. Also, I'd rather stick with something I know.

---

### Post by k64 on 2010-01-01
It's hard to choose, but YUM is a really crippled package manager. APT has a much cleaner and more organized interface - not to mention that YUM has about 5 GUI frontends. Ubuntu Software Center will fix Apt-Get's clobber - and the reason for YUM to begin with.

---

### Post by RiceMonster on 2010-01-01
> **k64 said:**
> It's hard to choose, but YUM is a really crippled package manager.

In what way?

> **k64 said:**
> APT has a much cleaner and more organized interface

Uhh... yum has FAR cleaner output than apt, and almost identical syntax. Have you even used it?

> **k64 said:**
> not to mention that YUM has about 5 GUI frontends. Ubuntu Software Center will fix Apt-Get's clobber - and the reason for YUM to begin with.

See: PackageKit, which was already aiming to solve this problem while being independent of any package format before software center came along. It's also the only GUI package manager in Fedora. It handles updates as well.

---

### Post by Queue29 on 2010-01-01
> **k64 said:**
> It's hard to choose, but YUM is a really crippled package manager. APT has a much cleaner and more organized interface - not to mention that YUM has about 5 GUI frontends. Ubuntu Software Center will fix Apt-Get's clobber - and the reason for YUM to begin with.

I don't know what you're smoking, but you should probably stop. Try actually using what you're talking about before making fallacious remarks about them.

---

