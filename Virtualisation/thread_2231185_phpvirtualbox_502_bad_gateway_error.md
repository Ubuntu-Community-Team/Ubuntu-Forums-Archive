---
title: "phpvirtualbox 502 bad gateway error"
date: 2014-06-23
forum: Virtualisation
---

### Post by glenak1911 on 2014-06-23
[FONT=arial]Hi everyone,
We had a thunderstorm the other day that knocked the power out. When I started my server up there were a few network errors which I was able to resolve. I soon realized there was a problem with my virtual machine when I couldn't ssh, or ping it. I use phpvirtualbox as my gui interface, but when I navigated to the server via the url, "mediabox/phpvirtualbox", I was greeted with a 502 bad gateway error. When I navigate via the IP address, "192.168.2.11/phpvirtualbox", [/FONT]I was greeted with a[FONT=arial] "Could not connect to host (http://127.0.0.1:18083/)"[/FONT] Error. When I try to run[FONT=arial] [/FONT][COLOR=#393939][FONT=arial] "[/FONT][/COLOR]VBoxManage startvm LampServer -type headless", [FONT=arial]I get the following error:[/FONT]

VBoxManage: error: Failed to create the VirtualBox object!
VBoxManage: error: Start tag expected, '<' not found.
VBoxManage: error: Location: '/home/vboxuser/.VirtualBox/VirtualBox.xml', line 1 (0), column 1.
VBoxManage: error: /home/vbox/vbox-4.2.24/src/VBox/Main/src-server/VirtualBoxImpl.cpp[525] (nsresult VirtualBox::init())
VBoxManage: error: Details: code NS_ERROR_FAILURE (0x80004005), component VirtualBox, interface IVirtualBox

Has anyone seen this error before, and if so, what steps did you take to resolve it? I have verified that the vdi file for the server is still intact, but my VirtualBox.xml file is empty.

---

