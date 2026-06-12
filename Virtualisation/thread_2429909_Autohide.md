---
title: "Autohide"
date: 2019-10-24
forum: Virtualisation
---

### Post by danielsender on 2019-10-24
My host is 18.04.3 and my guest is Centos 7. In my guest I'm using Gnome-classic that is the same option that I have in my host that is gnome-flashback. While in my host I can set the top and bottom panel to "autohide" by alt->right_click on the panels and get to the "properties" I can not do the same on the guest. Is there any way to achieve in the guest the autohide feature for the panels?

Thanks

---

### Post by danielsender on 2019-10-26
Any ideas?

---

### Post by danielsender on 2019-11-04
Perhaps I should post this in another forum?

---

### Post by ajgreeny on 2019-11-04
I don't know CentOS-7 but I wonder if this autohide is available by default in the OS if it is run normally as a hard-metal install rather than as a VM.

It is also possible that the virtual hardware does not provide the necessary acceleration needed for the autohide, but I am not sure about that.

It may be worth searching in the VBox forums at [https://forums.virtualbox.org/](https://forums.virtualbox.org/)

---

### Post by uRock on 2019-11-04
Perhaps. You're missing some key information in your question. I know that would have to be configured in the VM software on my system, if it is even possible, but I do not know what VM software you're using.

---

### Post by danielsender on 2019-11-04
I think that Gnome-classic in Centos and Gnome-flashback on Ubuntu are the same thing. In the latter, choosing Metacity gives the lowest required acceleration so autohide is not a problem. Again, in Ubuntu is very simple: you just alt->right_button on the panels and configure the properties. I cannot do the same thing on Centos, I tried many key combinations to no avail. Perhaps there is a file that I have to edit to achieve that.

---

### Post by danielsender on 2019-11-08
I've been wondering around different forums and I think that in this one I will find the answer. I'm running VirtualBox on my 18.04.3 Dell, and my guest is Centos 7. On the host (18.04.3) I'm using the Gnome-flashback and on the guest I'm using Gnome-classic that are the same thing. I would like to configure the panels on the guest (e.g. autohide), but when I enter alt->right-button on top of the panel, that key combination is caught by the host, so I would need to do that directly on whatever file holds that setting. Can some guru please tell me what is the file that holds those settings?

Thanks

---

### Post by CatKiller on 2019-11-08
I don't use Gnome, so I can't tell you the exact setting, but Gnome stores its settings in structures that were called GConf and became dconf. Both approaches have a GUI *editor* application and a command-line *settings* application. They're just nested key/value pairs.

There is also gnome-tweak, which exposes a subset of the available keys.

---

### Post by uRock on 2019-11-08
Duplicate thread here [https://ubuntuforums.org/showthread.php?t=2429909](https://ubuntuforums.org/showthread.php?t=2429909)

Please do not open duplicate threads.

Merged.

---

### Post by danielsender on 2019-11-08
I came to this forum because I didn't get any response from the other forum.

---

