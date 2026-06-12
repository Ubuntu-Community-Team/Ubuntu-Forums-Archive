---
title: "Virtual box on ubuntu 10.04 package issue"
date: 2010-05-10
forum: Virtualisation
---

### Post by Cool Breeze on 2010-05-10
Hi I am trying to install virtual box on my 10.04 install x64.

I have downloaded the Deb package from sun [http://download.virtualbox.org/virtualbox/3.1.8/virtualbox-3.1_3.1.8-61349~Ubuntu~lucid_amd64.deb](http://download.virtualbox.org/virtualbox/3.1.8/virtualbox-3.1_3.1.8-61349~Ubuntu~lucid_amd64.deb)

but when i try and run it I get this error Error: Dependency is not satisfiable: libqt4-network (>= 4:4.5.3)

I have no idea what this relates too

I am fairly new to this ubuntu stuff so go easy.

Cheers

---

### Post by Dougie187 on 2010-05-10
You could always just add their repository and have synaptic or something install it for you.

If you want to do this, follow these steps.

Open System->Administrator->Software Sources
On the tab entitles "Other Software" click the add button. Then in the text box, paste this
```
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
```

After this, Open up a terminal (Applications->Accessories->Terminal) and paste this
[code]wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -[code]

Finally, you can open up Synaptic and reload your sources, then search for virtualbox and you should be able to install it from that interface.

I would recommend doing this, as it will fix all dependencies for you. If you don't want to do this, then open up synaptic, and search for libqt4-network and install it. You may have to do other dependencies as well.

---

### Post by Cool Breeze on 2010-05-10
Cheers for the reply, i will try the last suggestion, trouble is with the other ones is I'm behind a proxy and I think its causing some issues

---

### Post by horde on 2010-06-30
Trying to install VirtualBox 3.2 (64-bit).  Have added the repos to my APT sources file as suggested above.  Have also downloaded the package directly and tried to do 'sudo dpkg -i', both with the same error:

> $ sudo apt-get install virtualbox-3.2 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  virtualbox-3.2: Depends: libc6 (>= 2.11) but 2.10.1-0ubuntu17 is to be installed
                  Depends: libqt4-network (>= 4:4.5.3) but 4.5.3really4.5.2-0ubuntu1 is to be installed
                  Depends: libqt4-opengl (>= 4:4.5.3) but 4.5.3really4.5.2-0ubuntu1 is to be installed
                  Depends: libqtcore4 (>= 4:4.6.1) but 4.5.3really4.5.2-0ubuntu1 is to be installed
                  Depends: libqtgui4 (>= 4:4.6.1) but 4.5.3really4.5.2-0ubuntu1 is to be installed
                  Depends: libssl0.9.8 (>= 0.9.8k-1) but 0.9.8g-16ubuntu3.1 is to be installed
E: Broken packages


Does anyone know how I might fix this?

---

### Post by hantms on 2010-10-30
I'm having the same problem on Maverick.  I have VirtualBox 3.2.8 already installed, but 3.2.10 fails to install due to a dependency issue.

This applies both when downloading the .deb file AND when using repository.

Errors:

virtualbox-3.2:
  Depends: libqtcore4 (>=4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
  Depends: libqtgui4 (>=4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
  Depends: libssl0.9.8 (>=0.9.8m-1) but 0.9.8k-7ubuntu8.2 is to be installed
 Recommends: libsdl-ttf2.0-0 but it is not going to be installed

NB: I should probably open a separate topic as this is now also an Ubuntu 10.10 issue.

---

### Post by josvanr on 2010-12-13
bump

---

### Post by hantms on 2010-12-14
Bump too.

---

### Post by tgm4883 on 2010-12-15
Simply put, your system doesn't have access to the required package. That could be because the mirror you are using isn't updated, or it could be because your sources.list is screwed up. 

Reading back over the last few posts, it seems to be a different packages for different people.  My thoughts are to do an rmadison on the package that isn't being installed/isn't available and to post your sources.list

---

### Post by thoemel on 2011-03-03
Note that the address of the public key has changed. It is now:
[code]http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc[code]

---

### Post by evenrelation on 2011-03-03
Similar problem I think.

Any idea why Oracle is making me download an update to VirtualBox named  [virtualbox-4.0_4.0.4-70112~Ubuntu~lucid_i386.deb] that conflicts with the package virtualbox-3.2 on a Maverick system?

I can't figure it out.

---

### Post by tgm4883 on 2011-03-03
> **evenrelation said:**
> Similar problem I think.

Any idea why Oracle is making me download an update to VirtualBox named  [virtualbox-4.0_4.0.4-70112~Ubuntu~lucid_i386.deb] that conflicts with the package virtualbox-3.2 on a Maverick system?

I can't figure it out.

Well 3.2 and 4.0 can't be installed at the same time I don't think.

Looking at the virtualbox download page, there are separate downloads for virtualbox for maverick and lucid, so you either A) clicked the wrong download link or B) have enabled the repository for lucid on your maverick system (if you have enabled the virtualbox repository) or C) the maverick repository has the lucid package (which would be wrong)

---

### Post by evenrelation on 2011-03-03
I just clicked the download link from the popup of the program itself. Naturally, the thought of checking their website for my OS version did not stream through my mind. But even with the correct Maverick version on their website, there is still a conflict between packages.

They don't really expect me to uninstall 3.2 before I install, 4.0, do they?

What am I not getting here? 

I've never had any issues with upgrading VirtualBox before.

---

### Post by CharlesA on 2011-03-03
You need to uninstall 3.2 before installing 4.0, since a totally new release.

---

### Post by evenrelation on 2011-03-03
But won't I have to reinstall the guest OS?

---

### Post by CharlesA on 2011-03-03
All your virtual machines will be fine even if you purge virtualbox :)

---

### Post by Powerbox on 2011-08-07
I have the exact same problem as cool breeze. I do not have any connectivity to the internet on my linux machine. How do I go about finding all the right packages such as libqt4-network and dependencies?

---

### Post by CharlesA on 2011-08-07
You can find the dependencies from any package by running this:

```
dpkg -I somefile.deb
```

It might be a bit of a pain to find the other files, but start here:
[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

---

### Post by Powerbox on 2011-08-07
I just tried that. The reply I get is as follows: dpkg -deb: failed to read archive 'virtualbox... [rest of file name]..' : no such file or directory

---

### Post by CharlesA on 2011-08-07
Did you download the virtualbox deb already?

---

### Post by ATMOS_SKY on 2011-08-11
Hey all,

dunno where you are in your install.

fyi: I installed the latest virtual box 4 series from the synaptic repository and it is working great in 10.04 lucid.

Go to their website and follow their instructions to add their key for validation and appending their repository to your "source list"

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

follow those directions lower down on the screen

---

