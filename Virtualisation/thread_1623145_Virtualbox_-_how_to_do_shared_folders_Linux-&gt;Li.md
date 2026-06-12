---
title: "Virtualbox - how to do shared folders? Linux-&gt;Linux"
date: 2010-11-16
forum: Virtualisation
---

### Post by riksia on 2010-11-16
I have Ubuntu 10.10 and OpenSUSE 11.3 installed on VBOX. I don't know how to do shared folders... I installed guest additions.

[http://img707.imageshack.us/img707/682/zrzutekranuav.png](http://img707.imageshack.us/img707/682/zrzutekranuav.png)

---

### Post by lmarmisa on 2010-11-16
These intructions only apply to your Ubuntu 10.10 guest system (virtual machine). You have to find a similar solution for the case of Fedora guest system.

Create this folder in the Ubuntu 10.10 guest system:

```

sudo mkdir /media/dokumenty

```Edit the file /etc/rc.local

```

sudo gedit /etc/rc.local

```and add this command:

```


# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR=Red]mount.vboxsf -w -o fmode=0777,dmode=0777 Dokumenty /media/dokumenty
[/COLOR]
exit 0

```Save and exit

Reboot the virtual machine.

The shared folder for your Ubuntu 10.10 system will be located at /media/dokumenty.

---

### Post by koperry on 2010-11-16
All I did was create a folder in my Home directory called Shared, went into Virtualbox and under my windows appliance settings under shared folders found the folder I created. 

I have imported and exported the Virtualbox appliance between Ubuntu and Fedora and never had an issue, I have a copy of XP installed in Virtualbox, in network places I see the Shared folder in my Home directory, very simple and straight forward. 

It may not work for all but works great for me.

---

