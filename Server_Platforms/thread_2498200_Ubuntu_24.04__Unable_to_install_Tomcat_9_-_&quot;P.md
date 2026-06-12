---
title: "Ubuntu 24.04 | Unable to install Tomcat 9 - &quot;Package 'tomcat9' has no installation c"
date: 2024-06-04
forum: Server Platforms
---

### Post by mdmonirul on 2024-06-04
[COLOR=#1A1C1E][FONT=&amp]Hi everyone,[/FONT][/COLOR]
[COLOR=#1A1C1E][FONT=&amp]I'm trying to install Tomcat 9 on my Ubuntu system using [FONT=&amp]sudo apt-get install tomcat9[/FONT], but I keep running into the following error:[/FONT][/COLOR]
[COLOR=#E36209]monirul@[/COLOR]nitacl-Veriton-Series:~$ sudo apt-[COLOR=#D73A49]get[/COLOR] install tomcat9
Reading [COLOR=#D73A49]package[/COLOR] lists... Done
Building dependency tree... Done
Reading state information... Done
Package tomcat9 [COLOR=#D73A49]is[/COLOR] not available, but [COLOR=#D73A49]is[/COLOR] referred to [COLOR=#D73A49]by[/COLOR] another [COLOR=#D73A49]package[/COLOR].
This may mean that the [COLOR=#D73A49]package[/COLOR] [COLOR=#D73A49]is[/COLOR] missing, has been obsoleted, or
[COLOR=#D73A49]is[/COLOR] only available from another source
E: Package [COLOR=#032F62]'tomcat9'[/COLOR] has no installation candidate

[COLOR=#1A1C1E][FONT=&amp]**Here's what I've tried so far:**[/FONT][/COLOR]

[LIST]
[*][FONT=&amp]sudo apt update[/FONT]
[*]Searching for alternative package names (e.g., [FONT=&amp]tomcat9.0[/FONT], [FONT=&amp]tomcat-9[/FONT]) using [FONT=&amp]apt-cache search tomcat[/FONT]
[/LIST]
[COLOR=#1A1C1E][FONT=&amp]**System Information:**[/FONT][/COLOR]

[LIST]
[*]Ubuntu version: 24.04 LTS
[*]Architecture: LAMP (Linux, Apache, MariaDB and Perl, PHP)
[/LIST]
[COLOR=#1A1C1E][FONT=&amp]Could anyone please point me in the right direction? Is there a specific repository I need to enable or a different approach to installing Tomcat 9?[/FONT][/COLOR]
[COLOR=#1A1C1E][FONT=&amp]Thanks in advance for your help![/FONT][/COLOR]

---

### Post by Morbius1 on 2024-06-04
Is tomcat10 not backward compatible to tomcat9 because that is the only one in the repository.

---

### Post by vmayorow on 2024-06-09
> **Morbius1 said:**
> Is tomcat10 not backward compatible to tomcat9 because that is the only one in the repository.

Unfortunately Tomcat 10 is NOT backward compatible to Tomcat 9, and most web apps working on Tomcat 9 will not work on Tomcat 10. Therefore, Tomcat 9 is still supported by Apache and new versions of Tomcat 9 are regularly released.

There is still an option to manually install Tomcat 9, but absence of Tomcat 9 package in the apt repository of Ubuntu 24.04 is an annoying problem for Tomcat 9 users.

I wonder if there's somewhere an option to suggest packages to be added to Ubuntu 24.04?

---

### Post by LHammonds on 2024-06-09
Sounds like you will need to manually install the application.

I found this tutorial for [Installing Tomcat 9 on Debian 10]("https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-9-on-debian-10") which should be very similar to the steps necessary on Ubuntu...with the exception of the step to install curl which is already installed on Ubuntu.

Keep in mind that Tomcat 9 will NOT receive updates automatically because it was not installed using apt.  You will need to re-download the latest package again, stop the Tomcat service and install/overwrite the current installation.  However, once you have it installed, much of the initial setup steps do not need to be repeated such as creating a user, configuring systemd and firewall rules.

But make sure you have a backup of any configuration files you modified that came with the package because extracting another package would overwrite all the files it came with....which is why you typically create files that will be included by the main config to avoid this situation (this is general info...I am not familiar with exact specifics of Tomcat)

If I were you, I'd document exactly how you install Tomcat on the server (preferably with a slightly older build version) and then document exactly how you should update the system with a new version.  There won't be much to the documents kinda like the one I linked above but it will be critical to ensure that you or someone else will know how to update the system with security patches/fixes over time.

LHammonds

---

### Post by vmayorow on 2024-06-18
I was able to resolve this by running this command (add the Ubuntu 22.04 repository):


```
add-apt-repository -y -s "deb http://archive.ubuntu.com/ubuntu/ jammy main universe"

```
After that, I was able to install Tomcat 9 on Ubuntu 24.04 via apt.

Not sure if there could be any bad consequences after adding a legacy repository, though.

---

### Post by eraknix on 2024-06-23
Sorry wrong post... I don't know how to delete...

---

### Post by jha-santosh on 2024-10-13
Thanks a lot! It helped in solving my problem.

---

