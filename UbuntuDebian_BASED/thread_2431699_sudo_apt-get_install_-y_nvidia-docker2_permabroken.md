---
title: "sudo apt-get install -y nvidia-docker2 permabroken"
date: 2019-11-20
forum: Ubuntu/Debian BASED
---

### Post by poisonknife on 2019-11-20
[SIZE=2]Keep in mind I am really not familiar with "advanced" computer. I ran into a problem attempting to use my local GPU on [RunwayML]("https://runwayml.com/")
Here are some screenshots of the error messages.

[IMG]https://i.imgur.com/vZcNCiG.png[/IMG]

[IMG]https://i.imgur.com/e0ljmFH.png[/IMG] [/SIZE]

---

### Post by brannondorsey on 2019-11-21
Hey there &#55357;&#56395;, Brannon from RunwayML here. 

Local GPU support with Runway is untested on Ubuntu 19.10, so I'm not sure exactly what the issue is, but I can try and provide some pointers and maybe help you through it. The root of the problem seems to be that nvidia-docker2 doesn't want to install over your existing installation of nvidia-container-runtime, correct?

[FONT=courier new][SIZE=2]dpkg: error processing archive /var/cache/apt/archives/nvidia-docker2_2.2.2-1_all.deb (--unpack):
 trying to overwrite '/etc/docker/daemon.json', which is also in package  nvidia-container-runtime 3.1.4-0pop1~1569270714~19.10~2ea45f8


[FONT=arial][/FONT][/SIZE][/FONT]Nvidia-docker2 is recently deprecated, but required for Local GPU to  work with RunwayML. Both nvidia-container-runtime and nvidia-docker2  SHOULD be compatible though. I've tested installing both on Ubuntu 18,  so I'm not sure what's up here. You could try force removing nvidia-container-runtime and any old versions of nvidia-docker2 you might have ([as suggested in this post]("https://askubuntu.com/questions/693735/broken-package-error-when-trying-to-install-kubuntu-desktop-in-ubuntu-15-10")), or if you are up for it, re-installing docker (although I'm not sure that will fix the issue). 

You could also try this:

[FONT=courier new]sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade #(this could have an effect on other packages)[/FONT]Finally, Nvidia's instructions for installing nvidia-docker2 are [here]("https://github.com/nvidia/nvidia-docker#upgrading-with-nvidia-docker2-deprecated") and [here]("https://github.com/nvidia/nvidia-docker/wiki/Installation-(version-2.0)"). Cheers and best of luck, let me know if that works for you, or if there are any other details about your install that could be helpful in pinning this down.

---

### Post by poisonknife on 2019-11-30
EDIT: 20191130 0710
Thanks for the reply!! I'm running PopOs-19.10. Dist-upgraded-from-19.04

 I came across a few web page instructions [here]("https://docs.nvidia.com/deploy/driver-persistence/index.html#persistence-mode") -- [https://docs.nvidia.com/deploy/driver-persistence/index.html#persistence-mode](https://docs.nvidia.com/deploy/driver-persistence/index.html#persistence-mode) 
which in turn brought me to [here]("https://devblogs.nvidia.com/gpu-containers-runtime/") -- [https://devblogs.nvidia.com/gpu-containers-runtimej/](https://devblogs.nvidia.com/gpu-containers-runtimej/)

Scrolling all the way down to the "Installation", I follow the steps up until sudo apt-get install -fy nvidia-docker2

[https://i.imgur.com/e5tnRCE.png](https://i.imgur.com/e5tnRCE.png)


sudo apt-get install -y nvidia-docker2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-docker2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,948 B of archives.
After this operation, 18.4 kB of additional disk space will be used.
(Reading database ... 410476 files and directories currently installed.)
Preparing to unpack .../nvidia-docker2_2.2.2-1_all.deb ...
Unpacking nvidia-docker2 (2.2.2-1) ...
dpkg: error processing archive /var/cache/apt/archives/nvidia-docker2_2.2.2-1_all.deb (--unpack):
 trying to overwrite '/etc/docker/daemon.json', which is also in package nvidia-container-runtime 3.1.4-0pop1~1569270714~19.10~2ea45f8
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-docker2_2.2.2-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

So, I thought that this was some how related to using 19.10, **I reinstalled to Ubuntu 18.04**, and used this [convenience script]("https://lambdalabs.com/blog/set-up-a-tensorflow-gpu-docker-container-using-lambda-stack-dockerfile/"). Fast forward to the **bottom of step 1 **and I received a familiar error code:
 

The following NEW packages will be installed:
  nvidia-docker2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,948 B of archives.
After this operation, 18.4 kB of additional disk space will be used.
(Reading database ... 234496 files and directories currently installed.)
Preparing to unpack .../nvidia-docker2_2.2.2-1_all.deb ...
Unpacking nvidia-docker2 (2.2.2-1) ...
dpkg: error processing archive /var/cache/apt/archives/nvidia-docker2_2.2.2-1_all.deb (--unpack):
 trying to overwrite '/etc/docker/daemon.json', which is also in package nvidia-container-runtime 3.1.4-0pop1~1569270714~18.04~2ea45f8
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-docker2_2.2.2-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Another issue--> [https://github.com/NVIDIA/nvidia-docker/issues/726](https://github.com/NVIDIA/nvidia-docker/issues/726)
which brought me here:[this post]("https://github.com/docker/for-linux/issues/409"); downgraded docker to the lowest version I could using apt-cache madison (18.03)
[img]https://i.imgur.com/sFKVnOS.png[/img]

sudo apt-get install -f nvidia-docker2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  docker-ce docker-ce-cli
The following NEW packages will be installed:
  docker-ce-cli nvidia-docker2
The following packages will be upgraded:
  docker-ce
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/65.3 MB of archives.
After this operation, 111 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 234451 files and directories currently installed.)
Preparing to unpack .../docker-ce_5%3a19.03.5~3-0~ubuntu-bionic_amd64.deb ...
Unpacking docker-ce (5:19.03.5~3-0~ubuntu-bionic) over (18.03.1~ce~3-0~ubuntu) ...
Selecting previously unselected package docker-ce-cli.
Preparing to unpack .../docker-ce-cli_5%3a19.03.5~3-0~ubuntu-bionic_amd64.deb ...
Unpacking docker-ce-cli (5:19.03.5~3-0~ubuntu-bionic) ...
Preparing to unpack .../nvidia-docker2_2.2.2-1_all.deb ...
Unpacking nvidia-docker2 (2.2.2-1) ...
dpkg: error processing archive /var/cache/apt/archives/nvidia-docker2_2.2.2-1_all.deb (--unpack):
 trying to overwrite '/etc/docker/daemon.json', which is also in package nvidia-container-runtime 3.1.4-0pop1~1569270714~18.04~2ea45f8
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-docker2_2.2.2-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by howefield on 2019-11-30
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

