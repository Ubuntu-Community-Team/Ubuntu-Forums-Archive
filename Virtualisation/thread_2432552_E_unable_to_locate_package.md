---
title: "E: unable to locate package"
date: 2019-12-04
forum: Virtualisation
---

### Post by gardnermarquis43 on 2019-12-04
unable to locate package by glob 
unable to locate package by regex
I have received both of these responses from the terminal when trying to download virtualbox. I did the sudo apt-get install update and still wasnt able to get these packages. I have not been able to successfully run VMware or virtualbox inside of ubuntu 18.04. LTS downloaded in the beginning of october. Any advice?

---

### Post by TheFu on 2019-12-04
Please show the exact commands used and the exact output. Use *code tags* so everything lines up.
Please don't make us guess what you actually did.  Copy/paste everything as text.

---

### Post by gardnermarquis43 on 2019-12-04
I went to virtualbox site and downloaded the latest version for linux ubuntu 18.04. Then i downloaded the supported platform extension both went smooth. Then I entered sudo apt-get install virtualbox-6.0_6.014-133895~Ubuntu~bionic_amd64.deb
Exactly that. This message came back:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package virtualbox-6.0_6.014-133895~Ubuntu~bionic_amd64.deb
E: Couldn't find any package by glob 'virtualbox-6.0_6.0.14-133895~Ubuntu~bionic_amd64.deb'
E: Couldn't find any package by regex 'virtualbox-6.0_6.0.14-133895~Ubuntu~bionic_amd64.deb'

that is exactly what happened.

---

### Post by &amp;KyT$0P# on 2019-12-04
Try
```
sudo apt install [COLOR="#FF0000"]/full/path/to/virtualbox-6.0_6.014-133895~Ubuntu~bionic_amd64.deb[/COLOR]
```

replacing [FONT=Courier New]/full/path/to/virtualbox-6.0_6.014-133895~Ubuntu~bionic_amd64.deb[/FONT] with the actual full path to the VirtualBox .deb you downloaded (you can probably also just drag&drop the VirtualBox .deb into the terminal to paste the full path).

---

### Post by TheFu on 2019-12-04
Thanks, that clarifies.

apt-get isn't used to install .deb files.  dpkg is, but it doesn't do dependencies.  apt-get installs packages which have been put into either repositories or PPAs.  This allows dependencies to be resolved and added to the installation.

Is there a reason that [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) instructions weren't used? Follow the **Debian-based Linux distributions**  instruction set. I see a bionic PPA there which **the instructions will have you add to your host APT configuration**. After that is done, a
```
sudo apt update
sudo apt full-upgrade
sudo apt install  virtualbox-6.0
```
should do it.  Doing it this way will integrate the PPA into your normal weekly system patching, so it will always have the current version of vbox upgraded and should automatically rebuild the kernel dependencies.  Installing .deb files is the 4th choice for handling package installs. There are 3 better methods.

BTW, *code tags* should look like mine above. Things inside the code tags are showing just like they would in a terminal, same spacing, so columns line up, which helps people used to using terminals see important aspects much quicker. That's why we ask for the copy/paste and code tags, so it is easier for us to see output we've seen many times before.

---

### Post by gardnermarquis43 on 2019-12-04
i had copy and pasted the name of the file but i didnt try full/path/to. will try thx

---

### Post by gardnermarquis43 on 2019-12-04
this is what happened when i ran the comman from the link you showed The Fu. Maybe i put the wrong thing but here it is exactly as it came

cashkidd@cashkidd-Aspire-E5-576:~$ sudo apt install [arch=amd64] [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) Xenial contrib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package [arch
E: Couldn't find any package by glob '[arch'
E: Regex compilation error - Unmatched [ or [^
E: Couldn't find any package by regex '[arch'
E: Unable to locate package [https://download.virtualbox.org/virtualbox](https://download.virtualbox.org/virtualbox)
E: Couldn't find any package by glob 'https://download.virtualbox.org/virtualbox'
E: Couldn't find any package by regex 'https://download.virtualbox.org/virtualbox'
E: Unable to locate package Xenial
E: Unable to locate package contrib

---

### Post by TheFu on 2019-12-04
Aren't you on 18.04?  Xenial is 16.04. You need to use the specific answers for YOUR bionic system.
Things in "brackets" are optional parameters. Either use the correct parameter or leave it out.  In this case, you can leave it out, but the rest of the command doesn't make any sense.

What is "comman"?  You shouldn't need to modify any network setup at this point.  Conman is usually part of SBC distros, not any Ubuntu distro.  Or did I guess what you meant incorrectly?  Correct, exact, details matter.

Back to the link with instructions.  Did you add the repo, keys and few other commands as the link requires?  It begins with the clear instruction to .... 
> Add the following line to your /etc/apt/sources.list. According to your distribution, replace '<mydist>' with 'artful', 'zesty', 'yakkety', 'xenial', 'trusty', 'stretch', 'jessie', or 'wheezy' (older versions of VirtualBox supported different distributions):  

Following the instructions in the link is required. They aren't optional.   All the 'sudo apt....." commands in my post above cannot be done before those others have been completed successfully.  The commands I put above are exact, complete, for use AFTER the PPA/repo is setup.

---

### Post by ajgreeny on 2019-12-04
Unfortunately you still keep on changing the commands that you have been told to run, which is why you are still seeing errors.
First run the commands suggested in the page at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)  for ***Debian based Linux distros***, ie,
```
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
```
Make sure you copy these commands accurately including the final - or they will fail.

Then as suggested by TheFu above in post #5 run the three commands 
```
sudo apt update
sudo apt full-upgrade
sudo apt install  virtualbox-6.0
``` and do not edit them in any way; copy and paste for assured accuracy and that will install VirtualBox version 6.0.14 at present.

---

