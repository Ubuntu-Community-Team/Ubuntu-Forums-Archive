---
title: "Unity-Rotated"
date: 2012-01-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Brandel Valico on 2012-01-20
Has anyone been able to get this working on Precise yet?

>     sudo add-apt-repository ppa:paullo612/unityshell-rotated

    sudo apt-get update && sudo apt-get install unityshell-rotated libnux-1.0-0 compizconfig-settings-manager

The above is what I have tried. It adds the PPA fine but is unable to locate the unityshell-rotated. Have tried the repository on both precise and oneiric (Changing the distr via synaptic) Neither way found it? 

Its a minor issue just prefer my launcher at the bottom and curious if anyone has gotten it to do so.

---

### Post by mc4man on 2012-01-20
Not too interested in a bottom launcher so haven't tried - you should read thru here, (meaning read completely
[http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html](http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html)

---

### Post by xyzzyman on 2012-01-20
The PPA only has oneiric and the version of unity it is based on is 4.24.0 from back in November. The regular repository for precise is up to 5.0.0-0ubuntu2. Because of all the changes in other deb's, I think even forcing the 4.24 will break your system most likely. You always could take a look at what he changed in the source and try porting it yourself?

---

### Post by Brandel Valico on 2012-01-21
Thanks for the responses will give porting it myself a try.

---

