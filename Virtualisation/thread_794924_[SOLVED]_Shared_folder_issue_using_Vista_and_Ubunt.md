---
title: "[SOLVED] Shared folder issue using Vista and Ubuntu"
date: 2008-05-15
forum: Virtualisation
---

### Post by Damien Kane on 2008-05-15
I've looked around but can't seem to find a definite answer to this issue.

I have Vista installed as my native OS and Ubuntu 8.04 as a guest with Virtualbox, with the guest addons installed. Both machines work well.

I have shared a drive (E_Personal) in Windows Vista and nominated that drive to share with Ubuntu guest. I have two issues if anybody knows:

(a) Although the GUI with Virtualbox states that E_Personal is shared, it doesn't show up in Ubuntu guest. How do I get it to mount?

(b) How do I get it to mount on booting the guest Ubuntu?

Any help will be appreciated.

I FOUND THE ANSWER:

Before starting, let's say we've allocated a share drive in Virtualbox called Personal. Terminal commands start with #, but don't use it when in terminal:
- Go into Terminal
- We need to create a share point (Let's call it Personal)
#sudo mkdir /mnt/Personal

Then, we need to edit a file which loads on boot
#sudo gedit /etc/rc.local
enter your password
Go to the last line, and above where it says exit 0, use the format:
#sudo mount.vboxsf Personal /mnt/Personal

Reboot the machine, and at least for me, it works like a charm. Go to the /mnt directory, then the Personal directory, and you should see your shared files.

I'm a bit of a newbie, so any questions, open a new thread because I probably won't be able to answer!

---

