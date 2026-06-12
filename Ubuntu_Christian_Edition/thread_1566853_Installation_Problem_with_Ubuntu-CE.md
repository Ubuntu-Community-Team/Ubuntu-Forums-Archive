---
title: "Installation Problem with Ubuntu-CE"
date: 2010-09-02
forum: Ubuntu Christian Edition
---

### Post by julri764 on 2010-09-02
Hi, I was in the process of installing Ubuntu-CE when I had to abort the process prematurely. I was at about 75% of the installation. I have gone back and tried to restart the installation and I keep getting the following message:

[INDENT]*Some packages could not be installed. This may mean that you have*
*requested an impossible situation or if you are using the unstable*
*distribution that some required packages have not yet been created*
*or been moved out of Incoming.*
*The following information may help to resolve the situation:*

*The following packages have unmet dependencies:*
*  ubuntu-ce: Depends: xiphos but it is not going to be installed*
*             Depends: wine-christian-repos but it is not going to be installed*
*E: Broken packages*

[/INDENT]I am relatively new to linux and am not really sure how to either remove what had been installed and start over or how to finish the installation. Any help would be appreciated.

---

### Post by julri764 on 2010-09-02
Never mind, I was using the installation command listed on the Ubuntu-CE website that was giving me that error. After some trial and error I found that the following command solved my problem.
sudo wget [http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/lucid_amd.list](http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/lucid_amd.list) -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce

---

