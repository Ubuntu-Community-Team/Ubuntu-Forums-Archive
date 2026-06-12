---
title: "ubuntu-desktop on Ubuntu Server: gnome-bluetooth GUI"
date: 2011-09-06
forum: Server Platforms
---

### Post by nukleuzN on 2011-09-06
Hi,

I'm using Ubuntu Server 11.04 (from the Minimal CD) on one of my computers. On this "server" I want to connect a Bluetooth keyboard from Micro$oft (unfortunally). Microsoft Bluetooth Mobile Keyboard 6000 to be precisly.

It's no problem connecting it when I'm on my laptop (which is docked at my office - *anyway, that doesnt matter I think*) that have Ubuntu Desktop 11.04 installed.

- But as soon as i try to connect it to the server; it want. 

I'm able to pair it, but it want connect properly; so I cant use it. The "connect light" on the keyboard continues blinking - which indicates that the keyboard is not connected.

I have followed this instruction: [https://help.ubuntu.com/community/BluetoothSetup#Ubuntu_11.04_Install_via_the_command_line](https://help.ubuntu.com/community/BluetoothSetup#Ubuntu_11.04_Install_via_the_command_line)

Well... anyhow. Now I consider installing *[COLOR="DarkGreen"]ubuntu-desktop[/COLOR]* on my Ubuntu Server installation - to try to connect it with gnome-bluetooth gui, since that work greate on my desktop.

**But**: I dont want ubuntu-desktop to start automatically on boot; _only when i want to use it_. 

Anyone knows how? 

Will this command exclude the "bluetooth" settings that comes with the full desktop version:
```
sudo apt-get install --no-install-recommends ubuntu-desktop
```
?

---

