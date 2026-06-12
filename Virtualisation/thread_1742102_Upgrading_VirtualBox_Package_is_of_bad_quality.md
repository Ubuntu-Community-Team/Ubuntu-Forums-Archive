---
title: "Upgrading VirtualBox: Package is of bad quality"
date: 2011-04-28
forum: Virtualisation
---

### Post by Dry Lips on 2011-04-28
When I downloaded the latest version of Virtual Box, and tried to upgrade it
 I got this error message:
  > 
**The package is of bad quality**
 
The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath.

Should I go ahead and install it anyway?
 
Another thing, after installing 11.04, my guest OS disappeared from 
Virtual Box...? Is this normal after an upgrade?

---

### Post by slooksterpsv on 2011-04-28
> **Dry Lips said:**
> When I downloaded the latest version of Virtual Box, and tried to upgrade it
 I got this error message:
  

Should I go ahead and install it anyway?
 
Another thing, after installing 11.04, my guest OS disappeared from 
Virtual Box...? Is this normal after an upgrade?

Sounds like the package is corrupt, try redownloading VirtualBox again, mine installed just fine, no errors.

Your Guest OS may have disappeared for a few reasons:
1. You reformatted the drive, which deleted the Guest OSes
2. Your under a new username which doesn't have the Guest OSes from the previous username - which you would need to move it from the old user account to the new one.
3. The Guest OS is on a different partition, which you would need to mount it, then go to Machine -> Add... and add the machine back to your list

---

### Post by Dry Lips on 2011-04-28
At first I thought the the problem was that I had downloaded the wrong deb, 
(which I also did the first time, since I upgraded from clicking on a link within
VirtualBox); however getting the deb for Natty doesn't solve this, I get the
 same error message.

    I'm running Ubuntu classic instead of Unity, could this be the cause of this?
 
> **slooksterpsv said:**
> 
Your Guest OS may have disappeared for a few reasons:
1. You reformatted the drive, which deleted the Guest OSes

 
 Errrr... Actually you could be right about this one. I did a reinstall a couple of
 weeks ago, I must have forgotten to install the guest OS...[B] :oops:


---

[/B]Edit: here are the details of the error message:
```
Lintian check results for /home/user/Desktop/Link to Downloads/virtualbox-4.0_4.0.6-71344~Ubuntu~natty_amd64.deb:
E: virtualbox-4.0: maintainer-script-removes-device-files prerm:27
```

---

### Post by slooksterpsv on 2011-04-28
Are you installing with dpkg or Ubuntu Software Center?

You may need to try and install with dpkg or gdebi I installed mine with:

sudo dpkg -i ~/Downloads/virtualbox*.deb

As I only had 1 virtualbox deb download

---

### Post by CharlesA on 2011-04-29
Could try just adding the repo and apt-getting it.

---

### Post by Dry Lips on 2011-04-29
[LEFT]@slooksterpsv & CharlesA
I was trying to install it through Ubuntu Software Centre.

I'm tried what CharlesA suggested, and it WORKED! 
although I'm sure slooksterpsv's suggestion would
have worked as well.

Thank you guys!


[/LEFT]

---

### Post by aranaea on 2011-04-29
I was having the same issue and went with slooksterpsv's suggestion.  

[INDENT]sudo dpkg -i virtualbox-4.0_4.0.6-71344~Ubuntu~natty_amd64.deb[/INDENT]

Also, the md5sum check passed so I don't think the package is corrupt.  In any case in seems to install and run fine like this.  I suppose I could have just told Software Center to ignore the issue and it would have been fine, too.

---

### Post by noworldorder on 2011-04-29
I am having thiis error and when I install it it does NOT work

no idea what to do

---

### Post by noworldorder on 2011-04-29
I tried to update ond this happened

> Check if you are using third-party repositories. If so, disable them, because they are a common source of problems.
Furthermore, run the following command in a Terminal: apt-get install -f

details

The following packages have unmet dependencies:

> virtualbox-4.0: Depends: libcurl3 (>= 7.16.2-1) but it is not installed
                Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is installed
                Depends: libpython2.6 (>= 2.6) but it is not installed
                Depends: libqt4-network (>= 4:4.5.3) but 4:4.7.2-0ubuntu6 is installed
                Depends: libqt4-opengl (>= 4:4.5.3) but it is not installed
                Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6 is installed
                Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6 is installed
                Depends: libstdc++6 (>= 4.4.0) but 4.5.2-8ubuntu4 is installed
                Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is installed

what does this mean

---

### Post by CharlesA on 2011-04-29
It means the dependencies aren't satisfied.

Try running this:

```
sudo apt-get install -f
```

---

### Post by noworldorder on 2011-04-29
thanks but that didn't resolve it


> chris@chris-HP-G60-Notebook-PC:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libpython2.6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by CharlesA on 2011-04-29
Hrm.

Try just installing libcurl3.

```
sudo apt-get install libcurl3
```

---

### Post by noworldorder on 2011-04-29
thanks but...

that didn't do it

???

---

### Post by slooksterpsv on 2011-04-29
Did you install it with:

sudo dpkg -i ~/Downloads/virtualbox-4.0_4.0.6-71344~Ubuntu~natty_amd64.deb

***IF you only have one virtualbox downloaded and in the downloads directory.

Then do: 

sudo apt-get install -f

And that should do it, if not do this then:

sudo apt-get install libgcc1 libcurl3 libpython2.6 libqt4-network libqt4-opengl libqt4core4 libqtgui4 libstdc++ build-essential dkms

Then do:

sudo dpkg -i ~/Downloads/virtualbox-4.0_4.0.6-71344~Ubuntu~natty_amd64.deb

---

### Post by Canaryguy on 2011-05-01
I'm using Ubuntu x32 with Unity

I tried slooksterpsv solution and it worked.


In accessories > Terminal:
sudo dpkg -i ~/Downloads/virtualbox*.deb

I only had to change Downloads for Desktop since it's there were I downloaded Virtalbox.

After that I open the Software Center and it offered me to repair the broken packages. I click "Repair" waited some time for to to finish and that's all. I could open Virtualbox.

---

### Post by rfs1970 on 2011-05-02
To install the latest VirtualBox in Ubuntu 11.04, 
I've first to install the following dependencies:

sudo apt-get install libqt4-network libqt4-opengl

After that, you will be able to install it without any issue.

---

