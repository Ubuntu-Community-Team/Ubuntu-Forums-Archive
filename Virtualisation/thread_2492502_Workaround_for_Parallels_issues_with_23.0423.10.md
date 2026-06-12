---
title: "Workaround for Parallels issues with 23.04/23.10"
date: 2023-11-13
forum: Virtualisation
---

### Post by masterrabbit on 2023-11-13
I would like to post this in the Parallels forums, because there's a lot of consternation over a bug in the Parallels software that causes the VM to break after upgrading to 23.04/23.10. However, I can't seem to find a button that would allow me to post. So, I'm doing it here. I hope it's  within the proper context for the subforum.

I realized that Parallels CAN run Ubuntu 23.04/23.10 if it's installed over Ubuntu Live Server.

So, the workaround is to 

(1) Download an .iso image for Ubuntu Server at [https://ubuntu.com/download/server](https://ubuntu.com/download/server) for Intel Macs, or [https://ubuntu.com/download/server/arm](https://ubuntu.com/download/server/arm) for M1/2/3 (Apple Silicon, since 2020) Macs. Download the 22.04 version, and you can upgrade later OR just download the 23.10 image and save time.

(2) Create a new VM in Parallels, using the .iso image you just downloaded.

(3) Setup Ubuntu Live Server. Select the option to update the installer. I'm not sure whether this is necessary, but when prompted, I create a bond connection, setting the device to enp0s5 (which should be the only one available), then select it again, choose IP4, and set it to "automatically." Then create your user account, server name, passwords, encryption, etc.

(4) When the Ubuntu Server is installed and you've rebooted, type in "sudo apt install ubuntu-desktop." Let it install, may take an hour or two, depending on connection.

(5) After it's installed, hit "sudo reboot." (If you installed the Ubuntu Server 22.04 image, there's an additional step of entering "sudo do-release-upgrade -d". Reboot again.) You will now boot into Ubuntu Mantic Minotaur (Ubuntu 23.10) and Parallels will work fine with it.

(6) Install Parallels Tools. (Action > reinstall Ubuntu Parallels Tools).

(7) Transfer the contents of your home directory to the new VM.

---

