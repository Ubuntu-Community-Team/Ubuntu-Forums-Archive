---
title: "Does Ubuntu 20.04.4 work with XRDP?"
date: 2022-06-27
forum: Ubuntu, Linux and OS Chat
---

### Post by fran_3 on 2022-06-27
I've got Ubuntu 20.04.4 running on Windows 10 via WSL Windows Subsystem for Linux and it's working great at the command line via ...

In an effort to get it to work with a GUI Desktop I installed xfce4 like this...
sudo apt install -y xfce4
sudo apt install -y xfce4-goodies
 
Then I installed XRDP Remote Desktop it like this ...
sudo apt install xrdp

and launched it via ...
sudo /etc/init.d/xrdp start

To see if it actually started I ran ...
xrdp.service - xrdp daemon

and got this response ...
xrdp.service: command not found

The questions...
1 - Is xrdp still supported in Ubuntu?
2 - Can anyone verify the steps outlined above to help me be sure that I did everything correctly.

Thanks for any help.

---

### Post by grahammechanical on 2022-06-27
It is my understanding that Ubuntu on Windows Subsystem for Linux is a Linux terminal environment. I am not sure that the purpose includes running a Linux Desktop Environment (DE). I have read that it is possible to run GUI apps on WSL. Here is how you do it.

[https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps](https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps)

I think the issue you are experiencing is caused by not having the X-Server installed. 

> Support for GUI apps on WSL does not provide a full desktop experience.  It relies on Windows desktop, so installing desktop-focused tools or  apps may not be supported. To request additional support, you can file  an issue in the [WSLg repo on GitHub]("https://github.com/microsoft/wslg/issues").

[https://www.helpwire.app/blog/xrdp-linux/](https://www.helpwire.app/blog/xrdp-linux/)

> Setting up a Linux remote desktop with xrdp requires that the X Window System is installed on your computer.

Does installing Ubuntu on WSL install the X-Server?

Regards

---

