---
title: "Can't change resolution on VirtualBox"
date: 2015-07-11
forum: Virtualisation
---

### Post by dave_h2 on 2015-07-11
I'm testing out Ubuntu desktop on a Windows VirtualBox (I don't have another computer) but I'm unable to up the resolution beyond 640x480. When I go to Settings > Display, it's the only thing to select in the drop-down, and many things just won't fit on the screen, and there's no horizontal scrollbar even for display settings. I've tried everything I can to get it to increase, but I'm not sure what to do.

[B]What can I do in Ubuntu to get this work or find out why it doesn't?

[/B](screenshot)

[IMG]http://imgur.com/wZpVtD5[/IMG]

[http://imgur.com/wZpVtD5](http://imgur.com/wZpVtD5)

---

### Post by Frogs Hair on 2015-07-11
*Moved to **Virtualisation ***

---

### Post by ajgreeny on 2015-07-11
Install the VBox guest additions and you should be able to run fullscreen and also have shared clipboard and folders from guest to/from host.
[http://download.virtualbox.org/virtualbox/5.0.0/Oracle_VM_VirtualBox_Extension_Pack-5.0.0-101573.vbox-extpack](http://download.virtualbox.org/virtualbox/5.0.0/Oracle_VM_VirtualBox_Extension_Pack-5.0.0-101573.vbox-extpack)

Note this link will take you to a very recent update of VBox to version 5 which I don't yet have; it must have updated at some point today.

EDIT:
I have just this minute updated to the new VBox 5 direct from Oracle, but found that it gave a very dark screen as though running at about 20% brightness, which was not possible to change.

Your situation my be different, of course, but if the version 5 is unsuccessful for you, I suggest you stick with the older version available from the repos, or get it from [https://www.virtualbox.org/wiki/Download_Old_Builds_4_3](https://www.virtualbox.org/wiki/Download_Old_Builds_4_3) along with the appropriate version of the guest additions.

---

### Post by cantorum on 2015-07-20
I've had the same problem running Virtualbox 5 on Yosemite, but installing Virtualbox Extension Pack didn't help &#8212; Ubuntu 14.04.2 LTS just stuck at 640x480.

I've changed to Parallels 10 &#8212; where it runs like a charm &#8212;, but I think the following thread might be of help. It seems you have to apt-get some guest packages.

[http://askubuntu.com/questions/3205/higher-screen-resolution-in-virtualbox](http://askubuntu.com/questions/3205/higher-screen-resolution-in-virtualbox)

---

### Post by sudodus on 2015-07-20
***Do all these things inside the virtual machine***

Try to change the following setting:

Remove the #-sign from the following line (which makes the command active)

```
[COLOR="#FF0000"]#[/COLOR]GRUB_TERMINAL=console
``` to ```
GRUB_TERMINAL=console
```

with the following command (run the text editor nano)

```
sudo nano /etc/default/grub
```

Save and exit.

After that, run the following command

```
sudo update-grub
```

and reboot the virtual machine. I think this will release the selection of graphics modes, and you should be able to get at least the resolution 1024x768

---

