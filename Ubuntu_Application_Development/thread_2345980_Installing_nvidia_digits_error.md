---
title: "Installing nvidia digits error"
date: 2016-12-09
forum: Ubuntu Application Development
---

### Post by lkes on 2016-12-09
I was installing nvidia digits and came among these errors:

(when installing nvidia digits package from nvidia install instructions)

[FONT=arial]administrator@l-digits:~$ sudo apt-get install digits[/FONT]
[FONT=arial][sudo] password for administrator: [/FONT]
[FONT=arial]Reading package lists... Done[/FONT]
[FONT=arial]Building dependency tree       [/FONT]
[FONT=arial]Reading state information... Done[/FONT]
[FONT=arial]Some packages could not be installed. This may mean that you have[/FONT]
[FONT=arial]requested an impossible situation or if you are using the unstable[/FONT]
[FONT=arial]distribution that some required packages have not yet been created[/FONT]
[FONT=arial]or been moved out of Incoming.[/FONT]
[FONT=arial]The following information may help to resolve the situation:[/FONT]

[FONT=arial]The following packages have unmet dependencies:[/FONT]
[FONT=arial] digits : Depends: python-caffe-nv (>= 0.13) but it is not going to be installed[/FONT]
[FONT=arial]          Depends: caffe-nv (>= 0.13) but it is not going to be installed[/FONT]
[FONT=arial]          Recommends: torch7-nv but it is not going to be installed[/FONT]
[FONT=arial]E: Unable to correct problems, you have held broken packages.[/FONT]
[FONT=arial]administrator@l-digits:~$ 

[/FONT]then i tried to install the needed dependencies as some other tutorials said and got these errors:

[FONT=arial]administrator@l-digits:~$ sudo apt-get install caffe-nv[/FONT]
[FONT=arial]Reading package lists... Done[/FONT]
[FONT=arial]Building dependency tree       [/FONT]
[FONT=arial]Reading state information... Done[/FONT]
[FONT=arial]Some packages could not be installed. This may mean that you have[/FONT]
[FONT=arial]requested an impossible situation or if you are using the unstable[/FONT]
[FONT=arial]distribution that some required packages have not yet been created[/FONT]
[FONT=arial]or been moved out of Incoming.[/FONT]
[FONT=arial]The following information may help to resolve the situation:[/FONT]

[FONT=arial]The following packages have unmet dependencies:[/FONT]
[FONT=arial] caffe-nv : Depends: libboost-python1.54.0 but it is not installable[/FONT]
[FONT=arial]            Depends: libboost-system1.54.0 but it is not installable[/FONT]
[FONT=arial]            Depends: libcaffe-nv0 (= 0.15.13-1+cuda7.5) but it is not going to be installed[/FONT]
[FONT=arial]            Depends: libgflags2 but it is not installable[/FONT]
[FONT=arial]            Depends: libgoogle-glog0 but it is not installable[/FONT]
[FONT=arial]            Recommends: caffe-nv-tools but it is not going to be installed[/FONT]
[FONT=arial]E: Unable to correct problems, you have held broken packages.[/FONT]
[FONT=arial]administrator@l-digits:~$


[/FONT]any help would be greatly appreciated as i am at a loss currently.

system information
core i7 3770
16gb kinston ddr3
nvidia quadro k2000
nvidia tesla m1060 4gb

---

