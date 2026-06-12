---
title: "Webmin and Virtualmin"
date: 2011-07-28
forum: Server Platforms
---

### Post by NetDoc on 2011-07-28
I have a 10.4 Ubuntu server with Webmin 1.550 and I want to add Virtualmin to help me with virtual hosting. I can't seem to figure out how to install it. I tried the emboldened portions: > Installing Virtualmin
If you have a fresh system running CentOS 5 or Debian 4.0 and want to install the full Virtualmin GPL stack (including Webmin, Apache, Postfix and other dependencies), the easiest way is to use the Virtualmin GPL install script. [B]Otherwise, you should add it to an existing Webmin install, as described here.
First download the Virtualmin module in the format that matches your Webmin install :[/B]
Virtualmin module in RPM format (for Redhat or Fedora Linux) :
[http://download.webmin.com/download/virtualmin/wbm-virtual-server-3.87.gpl-1.noarch.rpm](http://download.webmin.com/download/virtualmin/wbm-virtual-server-3.87.gpl-1.noarch.rpm) (1.3 MB)
[B]Virtualmin module in Debian Package format (for Debian and Ubuntu Linux) :
[http://download.webmin.com/download/virtualmin/webmin-virtual-server_3.87.gpl_all.deb](http://download.webmin.com/download/virtualmin/webmin-virtual-server_3.87.gpl_all.deb) (1.3 MB)[/B]
Virtualmin module in Webmin format (for FreeBSD, MacOS and Solaris) :
[http://download.webmin.com/download/virtualmin/virtual-server-3.87.gpl.wbm.gz](http://download.webmin.com/download/virtualmin/virtual-server-3.87.gpl.wbm.gz) (1.3 MB)
You should also install the Virtualmin theme, again in the appropriate format for your operating system :
Virtualmin theme in RPM format (for Redhat or Fedora Linux):
[http://download.webmin.com/download/virtualmin/wbt-virtual-server-theme-8.1-1.noarch.rpm](http://download.webmin.com/download/virtualmin/wbt-virtual-server-theme-8.1-1.noarch.rpm) (2.3 MB)
[B]Virtualmin theme in Debian Package format (for Debian or Ubuntu Linux):
[http://download.webmin.com/download/virtualmin/webmin-virtual-server-theme_8.1_all.deb](http://download.webmin.com/download/virtualmin/webmin-virtual-server-theme_8.1_all.deb) (2.2 MB)[/B]
Virtualmin theme in Webmin format (for FreeBSD, MacOS and Solaris):
[http://download.webmin.com/download/virtualmin/virtual-server-theme-8.1.wbt.gz](http://download.webmin.com/download/virtualmin/virtual-server-theme-8.1.wbt.gz) (2.2 MB)
**You can install the module by going to the Webmin Configuration module, clicking on Webmin Modules and use the first form on the page to install the downloaded file. Or install it directly from the above URL. After installation the module will show up in the Servers category.**

First I did a wget (link) and downloaded the package and then the theme into /home/pjmu/. Then I went to Webmin>configuration>modules>install and used the "From Local File" option and pointed it to /home/pjmu/webmin-virtual-server_3.87.gpl_all.deb. This is the output:   

> Failed to install module from /home/pjmu/webmin-virtual-server_3.87.gpl_all.deb : Not a valid module file : tar: This does not look like a tar archive tar: Skipping to next header tar: Exiting with failure status due to previous errors 

---

### Post by smeyers on 2011-07-28
> **NetDoc said:**
> First I did a wget (link) and downloaded the package and then the theme into /home/pjmu/. Then I went to Webmin>configuration>modules>install and used the "From Local File" option and pointed it to /home/pjmu/webmin-virtual-server_3.87.gpl_all.deb.To install a *.deb package, ssh to the server and run the following command:
sudo dpkg -i WHATEVER_PACKAGE.deb

---

### Post by NetDoc on 2011-07-30
> **smeyers said:**
> To install a *.deb package, ssh to the server and run the following command:
sudo dpkg -i WHATEVER_PACKAGE.debThat was as simple as it was effective. Thanks.

---

