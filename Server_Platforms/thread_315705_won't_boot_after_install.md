---
title: "won't boot after install"
date: 2006-12-09
forum: Server Platforms
---

### Post by kaelan on 2006-12-09
I need a little help... I'm trying to load server on a spare laptop (IBM thinkpad R50. I tried installing 6.10 server but got unknown interrupt or fault at EIP on boot up. I searched here and found that the kernel was the issue and the only suggestion was to use the alternate install CD.. I burned the 6.06 server CD and tried again with the older kernel. everything installs fine and on boot it stops at Uncompressing Linux...Ok, booting kernel.


then it's sits there at a flashing cursor. 

any help on getting this to install and boot would be great.. I really want to setup a LAMP here at home for testing websites before publishing them. 

Thanks

---

### Post by stell86 on 2006-12-10
I couldn't fnd exactly how to install/replace the 386-kernel for the 6.06 server install, so what I opted for was the following:
(I used [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades) as reference)

1. Install 5.10 server normally (although I'm not sure if there is an option to do a LAMP-install on the 5.10 install cd)
2. Edit the /etc/apt/sources.list file:
 2.1. Comment out the reference to the 5.10-CD
 2.2. Change all references of 'breezy' to 'dapper'
```
sudo nano /etc/apt/source.list
```

3. Update 'apt-get' and then do a 'dist-upgrade'
```
sudo apt-get update
sudo apt-get update && sudo apt-get dist-upgrade
```
From the guide:
> Extremely Important:
    * Enter the command exactly as above, so the  dist-upgrade  step will run only if the  update  step is successful. If the first step fails but you still attempt to run the second step, you will probably end up with a corrupted system.
    * Make sure you type  dist-upgrade  rather than  upgrade , because  upgrade  will totally hose your machine and render it completely unbootable. This is because a normal upgrade won´t upgrade packages with uninstalled dependencies, meaning your system will end up half Breezy and half Dapper.

4. And then installed my services: Samba & VSFTPD
```
sudo apt-get update
sudo apt-get install samba
sudo apt-get install vsftpd

```

and now the editing of the config files start.....:-k

HTH - I found the forums lacking in messages before Oct 2006 - don't know why....:confused:

---

