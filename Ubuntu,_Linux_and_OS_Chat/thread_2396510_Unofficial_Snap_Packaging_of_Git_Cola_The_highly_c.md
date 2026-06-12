---
title: "Unofficial Snap Packaging of Git Cola: The highly caffeinated Git GUI"
date: 2018-07-17
forum: Ubuntu, Linux and OS Chat
---

### Post by buo-ren-lin on 2018-07-17
After weeks of development and testing, I am thrilled to announce that the packaging work of the Git Cola has finally reached its end.

 [https://snapcraft.io/git-cola](https://snapcraft.io/git-cola)

Git Cola is a graphical Git frontend developed by David Aguilar et. al., it provides easy access with core to advanced Git functionalities from staging, committing and history visualization to partial staging, interactive rebasing and integration with external Git applications like Git Large File System and Git Annex.

Git Cola is actively maintained and constantly improving with daily to weekly frequency, and with its dependency over a layer of Python Qt bindings makes it a viable target to be packaged as a snap that delivers an up-to-date and predictable user experience. This snap packaging ships (most, if not) all of Git Cola’s optional dependencies so it can also be used in Snap’s confined environment.

We are currently in the process of making this work upstream, which should happen shortly in the future. Stay tuned for more updates!

**How to Install**

```
# Install Snap
sudo snap install git-cola

# Connect the Snap to Optional Interfaces
## gpg-keys: For signing commits and tags
sudo snap connect git-cola:gpg-keys

## removable-media: For accessing Git repositories under `/media/*` and `/run/media/*`
sudo snap connect git-cola:removable-media

## ssh-keys: For remote operation via SSH protocol
sudo snap connect git-cola:ssh-keys
``` 

**Related Links**

 
[LIST]
[*]Packaging recipe source code
[https://github.com/Lin-Buo-Ren/git-cola-snap](https://github.com/Lin-Buo-Ren/git-cola-snap) 
[*]Upstream project
[https://github.com/git-cola/git-cola](https://github.com/git-cola/git-cola) 
[/LIST]

**Support**

Please refer our project’s issue tracker:
[https://github.com/Lin-Buo-Ren/git-cola-snap/issues](https://github.com/Lin-Buo-Ren/git-cola-snap/issues)
or create a new topic under snap category in the Snapcraft Forums
[URL="https://forum.snapcraft.io"]https://forum.snapcraft.io
[/URL]
 **Join Snapcrafters**

[https://forum.snapcraft.io/t/join-snapcrafters/1325](https://forum.snapcraft.io/t/join-snapcrafters/1325)

---

