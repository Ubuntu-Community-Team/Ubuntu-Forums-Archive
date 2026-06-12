---
title: "Subclipse Integration for Mylyn 3.x (Optional) requires"
date: 2011-05-23
forum: Server Platforms
---

### Post by thoufiq on 2011-05-23
Hi All,
          I had installed eclipse in my ubuntu server 10.10 and it is working fine but while trying to install eclipse subversion, i got a error that can't complete the install.
I clicked the menu [COLOR=Red]HELP > Install new software and [COLOR=Black]added the link[/COLOR] Subclipse_1.6.x - [http://subclipse.tigris.org/update_1.6.x](http://subclipse.tigris.org/update_1.6.x)[/COLOR] then i got [COLOR=Red]core SVNkit library, Optional JNA library and subclipse [/COLOR]to install, then i marked all the three items and proceed to [COLOR=Red]NEXT[/COLOR], after that it shows error like this.....

> [B][COLOR=Red]Cannot complete the install because one or more required items could not be found.
Software being installed: Subclipse Integration for Mylyn 3.x (Optional) 3.0.0 (org.tigris.subversion.subclipse.mylyn.feature.group 3.0.0)
Missing requirement: Subclipse Integration for Mylyn 3.x (Optional) 3.0.0 (org.tigris.subversion.subclipse.mylyn.feature.group 3.0.0) requires 'org.eclipse.mylyn.tasks.core [3.0.0,4.0.0)' but it could not be found[/COLOR][/B]Anyone help me to fix this issue..


Thanks

---

### Post by thoufiq on 2011-05-24
I un-marked the Mylyn and installed other components but after installing subversion, svn perspective is not present in the [COLOR=red]WINDOW > Show view > other [/COLOR]and also in [COLOR=Red]WINDOW > Open perspective > other[/COLOR]. I think plugins are not installed but i dont know the actual cause for this issue.

Anybody suggest me to fix this issue.



Thanks

---

### Post by thoufiq on 2011-05-25
Anybody help me........



Thanks

---

### Post by subclipse on 2011-11-15
Hi,

i know its an old thread, but i think there are many others who are searching for a solution to this problem:
First of all the following line shows that there is a dependency which has to be fulfilled:
> 
[COLOR=Black]requires 'org.eclipse.mylyn.tasks.core [3.0.0,4.0.0)' but it could not be found[/COLOR]
In order to get the required packages you have to enable the Mylyn update site by simply adding it in the "Install New Software" dialogue and select "Contact all update sites..." while installing Subclipse. 
The Mylyn update site is located here: 
[http://download.eclipse.org/mylyn/releases/latest](http://download.eclipse.org/mylyn/releases/latest)

After that a new dependency occurs: 
> 
requires 'org.eclipse.draw2d 3.2.0' but it could not be found
Same solution as above: Add the following update site: [http://download.eclipse.org/tools/gef/updates/releases/](http://download.eclipse.org/tools/gef/updates/releases/)

Best Regards

subclipse

Links to the sites that helped me solve this problem:
[http://www.eclipse.org/forums/index.php/m/752575/](http://www.eclipse.org/forums/index.php/m/752575/)
[https://aptanastudio.tenderapp.com/discussions/problems/3279-subclipse-installation-problem](https://aptanastudio.tenderapp.com/discussions/problems/3279-subclipse-installation-problem)

---

### Post by psychok7 on 2011-11-28
> **subclipse said:**
> Hi,

i know its an old thread, but i think there are many others who are searching for a solution to this problem:
First of all the following line shows that there is a dependency which has to be fulfilled:
In order to get the required packages you have to enable the Mylyn update site by simply adding it in the "Install New Software" dialogue and select "Contact all update sites..." while installing Subclipse. 
The Mylyn update site is located here: 
[http://download.eclipse.org/mylyn/releases/latest](http://download.eclipse.org/mylyn/releases/latest)

After that a new dependency occurs: 
Same solution as above: Add the following update site: [http://download.eclipse.org/tools/gef/updates/releases/](http://download.eclipse.org/tools/gef/updates/releases/)

Best Regards

subclipse

Links to the sites that helped me solve this problem:
[http://www.eclipse.org/forums/index.php/m/752575/](http://www.eclipse.org/forums/index.php/m/752575/)
[https://aptanastudio.tenderapp.com/discussions/problems/3279-subclipse-installation-problem](https://aptanastudio.tenderapp.com/discussions/problems/3279-subclipse-installation-problem)

thanks... it worked for me

---

