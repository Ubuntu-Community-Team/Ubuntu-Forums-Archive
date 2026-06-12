---
title: "[HOW-TO] Install Virtualmin GPL on Ubuntu 7.10"
date: 2008-04-17
forum: Server Platforms
---

### Post by solcott on 2008-04-17
I wrote this script for myself a while back and I decided to clean it up some and release it, just in case there are other people who want to get Virtualmin running on Ubuntu without having to either spend money on the pro version or do a ton of configuration.

[COLOR="Red"]**DISCLAIMER:**[/COLOR] Although I have tested this on a Ubuntu 7.10 Server (x86 and ADM64) and the Ubuntu 7.10 Desktop (x86 and ADM64) installations and it worked fine, it comes with NO WARRANTIES and is to be used at your own risk.  (mostly because this is the first shell script I have ever written, and I don't know if side effects from use include your server / dog / cat busting into flames from use.)

:KS**What this script does:**:KS
Installs the packages needed to run a Virtualmin hosting system, removes packages that will conflict with it, and make changes to the config files in these packages that Virtualmin will bark at you about but not point you in the right direction to fix.

:KS**What this script doesn't do:**:KS
Install a Virtualmin hosting system with anywhere near the awesomeness  of the official install script for Debian/CentOS or the professional packages.  It will create a more basic install for people like me who would rather run Ubuntu than Debian.

:KS**Step 1, Running the script:**:KS
From a terminal or over SSH, do
```
wget http://www.olcottfamily.com/virtualmin/virtualmin-ubuntu-install.sh
```
and then make it executable
```
chmod +x virtualmin-ubuntu-install.sh
```
now it's time to run the script
```
sudo ./virtualmin-ubuntu-install.sh
```
 
Let the script run until it finishes, and then restart your server.
 
 
:KS**Step 2, After running the script:**:KS
Log into your installation at [https://yourhostname:10000](https://yourhostname:10000) and click on 'Servers' and then 'Virtualmin Virtual Servers (GPL)'

Click the re-check configuration button, and it will tell you that you do not have MySQL configured.  Click the link in the error message to go to the MySQL configuration page and enter the account name 'root' and whatever password you provided before.

Click on 'Servers' / 'Virtualmin Virtual Servers (GPL)' again, and re-check the configuration again.

Thats it! You can now create new domains to host with Virtualmin.

If you want, you can go to the Webmin Configuration page within webmin, and change the theme to the Virtualmin Framed Theme, a redesigned theme meant for use in Virtualmin, but that's up to the user if they prefer the Virtualmin theme or the Webmin theme.

[COLOR="Red"]**UPDATE:**[/COLOR] The script is now attached to this post, as well as available from the address in the instructions.

[COLOR="Red"]**UPDATE 2:**[/COLOR] Updated a problem with the script not allowing Dovecot to allow remote connections.

---

