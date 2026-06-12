---
title: "Intel Pro-Wireless 2200BG (problem)"
date: 2013-02-21
forum: Texas Team - US
---

### Post by teprac on 2013-02-21
[COLOR="Red"]I wasn't sure where to post this, but I have a toshiba satellite laptop m55-s325 with an Intel Pro-Wireless 2200BG wireless card that I cannot get working.[/COLOR] 

so i did a search and found this:

Intel Pro/Wireless 2200BG [Resolved]
/http://ubuntuforums.org/showthread.php?t=309041&highlight=intel+Wireless+2200BG
Enable WPA Wireless access point in Ubuntu Linux
/http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html

So i ran the following command and get this:
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


i followed this tutorial: Enable WPA Wireless access point in Ubuntu Linux

To update the source list run the following command

1. sudo apt-get

2. sudo apt-get install wpasupplicant

3. sudo apt-get install network-manager-gnome network-manager

4. sudo gedit /etc/network/interfaces

5. Comment out everything other than “lo” entries in that file and save the file

6.Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file

7. sudo touch /etc/default/wpasupplicant

[COLOR="Red"]I think i messed up here on step 5, so how can i delete and redo step 5?

And also when i run step 7 nothing happens, I don't get any feedback in the terminal

is there anyway to do the whole process over?[/COLOR]

---

