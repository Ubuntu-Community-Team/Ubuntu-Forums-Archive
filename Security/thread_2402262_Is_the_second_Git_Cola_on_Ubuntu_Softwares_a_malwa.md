---
title: "Is the second Git Cola on Ubuntu Softwares a malware?"
date: 2018-09-28
forum: Security
---

### Post by navipe on 2018-09-28
Hi,

I use Ubuntu 18.04 LTS, and on trying to install Git Cola, I first saw only one version of it on Ubuntu Software Center that said it was not the official version of Git Cola. After installing, it crashed everytime I tried starting it. Moreover, it is 157.5MB in size, whereas the other "official" Git Cola is just 2.8MB. 

Do you know why there are two Git Cola's on Ubuntu Software Center and whether the unofficial one is malware?

---

### Post by oldos2er on 2018-09-28
I am only seeing one: [https://packages.ubuntu.com/search?keywords=git-cola&searchon=names&suite=bionic&section=all](https://packages.ubuntu.com/search?keywords=git-cola&searchon=names&suite=bionic&section=all)

Have you added a PPA or other external source recently?

Edit: Obviously my ignorance of snap led me astray. Thanks to all who replied constructively.

---

### Post by PaulW2U on 2018-09-28
> **navipe said:**
> Do you know why there are two Git Cola's on Ubuntu Software Center and whether the unofficial one is malware?
It's NOT malware. It's a snap version of the package.

If you read the description on the information page you'll see that it's been made available in the snap store. Ubuntu Software picks up those snaps and to the casual eye duplicates entries. The smaller package is the .deb version from the universe repository.

---

### Post by maglin2 on 2018-09-28
The 157.5 MB version is a snap.
(which you had already known for at least 30 seconds when I posted!)

---

### Post by deadflowr on 2018-09-28
A guess on the failure would be that since it's a snap it's under the default heavy confinement build structure.
Snap packages can be published (basically) in two ways.
1) It can be automatically uploaded and made available to all users, but the caveat is that it will be highly restricted within the confines of the system.
2) A developer can upload a snap with less restrictions, but then it automatically gets flag for peer and code review.
This takes far longer as it requires actual people to look at all aspects of the package.

Looking at the git cola's information page, it tells us straight away it's under the heavy confinement and also what you would need to do to expand it's reach.
(Full info page:
```
name:      git-cola
summary:   The highly caffeinated Git GUI
publisher: &#26519;&#21338;&#20161;(Buo-ren, Lin) (lin-buo-ren)
contact:   https://github.com/Lin-Buo-Ren/git-cola-snap/issues
license:   GPL-2.0+
description: |
  git-cola is a powerful Git GUI with a slick and intuitive user interface.
  
  INFORMATION REGARDING TO SECURITY CONFINEMENT
  
  User's global Git configuration is not accessible due to Snapd's current
  limitations.  You may change the in-snap configuration by editing
  $HOME/snap/git-cola/current/.gitconfig
  
  You need to connect the snap to the following core snap's interfaces
  manually in order to gain access to certain functionalities:
  
  * gpg-keys: For signing commits and tags
  
        sudo snap connect git-cola:gpg-keys
  
  * removable-media: For accessing Git repositories under `/media/*` and
  `/run/media/*`
  
        sudo snap connect git-cola:removable-media
  
  * ssh-keys: For remote operation via SSH protocol
  
        sudo snap connect git-cola:ssh-keys
  
  BUILD CONFIGURATION
  
  For `stable` channel the formal release of Git Cola is used, latest
  development snapshots are periodically published to the `edge` channel
  
  Information of other Git Cola's dependencies:
  
  * Blame Viewer: git-gui
  * Diff Tool: Kdiff3
  * Git: From Ubuntu 16.04 software archive
  * Git Annex: From Ubuntu 16.04 software archive
  * Git Large File system: Latest upstream release(only shipped in
  i386/amd64)
  * History Browser: gitk
  * Merge Tool: Kdiff3
  
  THIS IS NOT AN OFFICIAL DISTRIBUTION, FOR ANY ISSUE ENCOUNTERED DURING
  USING THIS SOFTWARE REFER TO:
  https://github.com/Lin-Buo-Ren/git-cola-snap/issues
snap-id: PXfuqn22GScJ9wUVqvGaDEhQv8a27nYI
channels:                                         
  stable:    3.2+pkg-570e             (136) 157MB -
  candidate: &#8593;                                    
  beta:      3.2+pkg-570e             (136) 157MB -
  edge:      3.2-36-g780e84b+pkg-b309 (140) 157MB -

```

All in all, if the "other 'Official' version runs as expected then by all means just use that.

---

