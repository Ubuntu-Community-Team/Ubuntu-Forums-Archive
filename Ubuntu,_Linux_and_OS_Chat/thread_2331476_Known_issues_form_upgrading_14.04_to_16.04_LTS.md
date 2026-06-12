---
title: "Known issues form upgrading 14.04 to 16.04 LTS"
date: 2016-07-22
forum: Ubuntu, Linux and OS Chat
---

### Post by henryhollow on 2016-07-22
Are there any known issues when upgrading from 14.04 to 16.04 LTS Desktop version? I soon need to upgrade and I'm a bit afraid that something could potentially break.

---

### Post by howefield on 2016-07-22
You could start with the release notes which can be found here...

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

---

### Post by oldfred on 2016-07-22
As noted in Release notes, if you have AMD video you may want to wait a bit, depending on what driver you currently use. 
Supposedly by fall issues should be resolved and 14.04 is still supported for years.

If you have installed any proprietary drivers, best to uninstall before upgrade.
Same with ppa as if a ppa is not available for 16.04 then upgrade stalls and causes major issues.

Best to download new 16.04.1 and have available the live installer to make repairs if needed.

And, as always, you need to have good backups.
       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)

With new larger hard drives (and even my new SSD), I prefer to have smaller / (root) partition and larger data partition (or /home). Then I can install another / partition and see if it works before I convert to it as my main working install. My first SSD was 60GB and it had 12.04 and various short term versions and then 14.04 installed along side the 12.04 install.

---

### Post by grahammechanical on 2016-07-22
Based on observations of the problems that people come on this forum and ask for help for, I would say that there are precautions that should be taken when doing any online upgrade from one version of Ubuntu to another. I will list some that come to mind.

1) It is best to run the upgrade using a wired connection.
2) It is best to run the upgrade when confident that the power supply will not fail part the way through the upgrade process.
3) Back up all important data. If necessary create another partition to store the data in.
4) Revert to using the open source video driver.
5) Revert the desktop to as default a desktop as possible. Do not expect the official upgrade process to take into account any alternative desktop that was installed or software that was download from some web site.
6) Do not leave the upgrade unattended as the process might require user interaction.
7) If the machine is a laptop, do not close the lid.
8) Disable any Personal Package Archives (PPA). Do not expect software installed through a PPA to be upgraded as part of the upgrade process. The maintainer of the PPA may not have move their PPA onto the new Ubuntu release.
9) Allow sufficient time for the upgrade. Stopping the upgrade part the way through will cause problems.

Regards.

---

