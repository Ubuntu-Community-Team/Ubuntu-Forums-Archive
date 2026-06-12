---
title: "Ask to re-enable 3rd-party repositories after upgrade"
date: 2008-10-31
forum: Ubuntu Brainstorm
---

### Post by Megatog615 on 2008-10-31
After a successful reboot into a new version of Ubuntu, a popup should appear and ask the user if the user wants to re-enable some 3rd-party repositories the user may have set up. A selection window with all 3rd-party repositories should be shown for the user to select. After clicking next, the popup application should check if the chosen repositories are ready for the version of Ubuntu they are using(say, Intrepid).

For example, I set up the medibuntu repository in Hardy. After the upgrade to intrepid, the popup should check if the medibuntu repository has a version for Intrepid, and modify the apt line if it does.

This way, we don't have to re-enable(and change the ubuntu version) and test repositories if the maintainers have created a version for the new Ubuntu. This means less time spent setting up your environment after the upgrade.

---

### Post by smartboyathome on 2008-11-01
I don't agree with this. Since 3rd party repos are unsupported, why should we support them after upgrading? I think it would actually cause more trouble than it would help people, since the 3rd party repos might not have a repo for the new version yet, or may be unstable on that version since they might not be fully tested.

---

