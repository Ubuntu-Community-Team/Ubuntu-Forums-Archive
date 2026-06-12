---
title: "How let VPN start at startup ?"
date: 2024-09-26
forum: Security
---

### Post by massimox on 2024-09-26
I was able to setup a VPN (openvpn) connection. Now I would let the VPN start just after have done the login. How to do that? Thanks for Your attention.     Massimo

---

### Post by 0f4d0335 on 2024-09-26
It depends on what application you're using and how immediate you want the connection. Without specifics, I can recommend using systemd for the automation connection at startup like this: [https://unix.stackexchange.com/questions/664748/automatically-connect-to-vpn-on-system-startup-using-systemd](https://unix.stackexchange.com/questions/664748/automatically-connect-to-vpn-on-system-startup-using-systemd)

>  Create a file named auto_vpn.service in ~/.config/systemd/user with the following content:

 [Unit]
Description=Connect to Proton-VPN
BindsTo=graphical-session.target

[Service]
Type=simple
ExecStart=/usr/bin/protonvpn-cli connect -f
ExecStop=/usr/bin/protonvpn-cli disconnect
Restart=on-failure
RestartSec=30
StartLimitInterval=350
StartLimitBurst=10
RemainAfterExit=yes

[Install]
WantedBy=xsession.target


 Now run:

 systemctl --user daemon-reload
systemctl --user start auto_vpn.service
Run `systemctl --user enable auto_vpn.service

 Thats it.
     


---

### Post by massimox on 2024-09-27
I thank You for Your kindness, but I'm not comfortable with commands directly sent to the operating system. My scarce knowledge stops me.

---

### Post by 0f4d0335 on 2024-09-27
Oh I see. Well, there are ways around that to learn how to use Ubuntu effectively. 

Look up "bash shell programming" on YouTube. Setup a test environment. This can be a virtualbox installation, gnome box installation, or a different PC. Use this environment to make shell scripts. You will learn about user and root access, and from there you can see what is possible.

This example is a user script, so it shouldn't negatively impact your machine. But I'm happy you are careful enough not to do something without learning about it.

The tool I'm using is called systemd. You can use systemd for all sorts of things. My favorite thing is to create a daemon with it.

Good luck.

---

### Post by massimox on 2024-09-27
Thanks again. I'll follow Your suggestions.

---

### Post by tea for one on 2024-09-27
Help > Your Desktop > Startup Applications (Choose what applications to start when you log in)

---

### Post by massimox on 2024-09-27
Impossible for me to point to the VPN

---

### Post by 1fallen on 2024-09-27
> **massimox said:**
> Impossible for me to point to the VPN

What DE is used here, I'll assume Gnome, and what VPN are you using/
All that will help us to help you.

---

### Post by massimox on 2024-09-27
Correct sorry.
Ubuntu 24.04.1 LTS, Gnome, Network Manager installed. Into Settings>Network I compiled the OpenVPN page.
After each session start I enter System Menu and press the VPN button. That's all.

---

### Post by 1fallen on 2024-09-27
Thought so a home brew VPN. ;)
Can you show us this please:
```
nmcli connection show


```

---

### Post by stephan4 on 2024-10-02
> **massimox said:**
> I thank You for Your kindness, **but I'm not comfortable with commands directly sent to the operating system**. My scarce knowledge stops me.

Why do you need an open-VPN ???

Usually, if you don't have the knowledge for that, you should ask your employer. In a private environment open-VPN is normally not needed, well, at least not from people who say that they have not even then basic knowledge at all.

---

