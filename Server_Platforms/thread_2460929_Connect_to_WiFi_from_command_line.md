---
title: "Connect to WiFi from command line"
date: 2021-04-21
forum: Server Platforms
---

### Post by imWACC0 on 2021-04-21
I'm trying to set up a (VS?)FTP server to share files with a friend ~600km away, also a Samba for LAN.

Right now the server (HP Z220, 7tb HDD) is sitting on my kitchen table* for set up and testing. When set the way I like, I'll remove the WiFi, move it to the rack, attach ethernet, and go headless.

But right now I need WiFi. I found a guide [https://linuxconfig.org/ubuntu-20-04-connect-to-wifi-from-command-line](https://linuxconfig.org/ubuntu-20-04-connect-to-wifi-from-command-line)

I'm doing something wrong**... [https://photos.app.goo.gl/pzd4sEu9E8SVH9oe6]("http://photos.app.goo.gl/pzd4sEu9E8SVH9oe6")

When I first tried to #sudoedit /etc/netplan/****.yaml  I got the first image. Friend pointed out that I need the "quotes". The 2nd image shows the layout of /etc/netplan/****.yaml but I did add the quotes. Third image shows the #sudo netplan --debug apply after I added quotes.

I note that the ^ has moved, but I don't know what that means or how to fix any of this.

I've added and removed spaces, and still get the same error.


*Flat space is at a premium around here <shrug> it works
**Sorry about the images, but I wanted to show exactly what I had. Also, I'm not sure how to save it for sneaker net.

---

### Post by TheFu on 2021-04-21
I use an older wifi/network TUI program (the name escapes me now), but there is **nmcli** too. [https://www.tecmint.com/nmcli-connect-wi-fi-from-linux-terminal/](https://www.tecmint.com/nmcli-connect-wi-fi-from-linux-terminal/)

To share files with a friend, I prefer "magic wormhole".  Encrypted, peer-to-peer connection.
[https://www.omgubuntu.co.uk/2017/06/wormhole-fast-secure-way-send-files-users-cli](https://www.omgubuntu.co.uk/2017/06/wormhole-fast-secure-way-send-files-users-cli)  Used it with a friend a few weeks ago for 31GB download.  We both run web servers, but for a 1-off share, wormhole is just easier. There are both apt and snap packaged versions so anyone on Linux can use it.  I've had issues with the snap due to snap restrictions on NFS and non-standard HOME directory locations that Canonical doesn't think are issues - but they are HUGE issues in corporate environments.  The .deb package installed via APT works great.

For sharing lots of files where I don't want to setup an sftp-only account for a friend, I'd setup a little web-server with an SSL-cert. Actually, I have a number of those running already, so I'd just make a few random, hidden, directories on the web server and only tell the few people about the location.  Then I'd use the 'at' command to delete the files in a few weeks, automatically.

Plain FTP should have died out in 2002 and there's no need for a separate server. Just use the built-in **sftp-server** that comes with ssh-server. There are guides to set it up inside a chroot environment, if you need that extra security.

IMHO.

I hope the wifi issues aren't due to drivers.  Then you have a chicken/egg problem - can't fix the networking until you have networking working.  I have a 100ft CAT5e ethernet cable for those times. It can reach from a switch or router somewhere in the house to anywhere else. Cheap investment to avoid hassles.

BTW, I don't see any image. Best to post plain text here, not images.

---

### Post by xpl01t on 2021-04-21
Netplan is finicky about indentation.
If you want your config to look readable, just replace tabs with spaces, and make sure your indentation is consistent on every line.
Also, your main issue is that you've forgotten to add semicolon after AP name.
Should look something like this:
```

wifis:
  wls3:
    dhcp4: yes
    access-points:
      "WACCo 2.4G":
        password: "supersecretpassword"

```

---

### Post by imWACC0 on 2021-04-21
@[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685") Yes, I agree... plain FTP should have died quite a few years back. I plan to use VSFTP or Pure-FTP. However the guy who needs files is rather a L-user, so I need something I can set up and it'd be hard for him to F up. Yes, that means I have to remote into his system to set it up for him.



> **xpl01t said:**
>  you've forgotten to add semicolon after AP name.
@[**[COLOR=#000000]xpl01t[/COLOR]**]("https://ubuntuforums.org/member.php?u=2159039") Thank you so much for catching my typo. I still F'ed something up but I'm a little further along.  [https://photos.app.goo.gl/iKS8gJHNLPL8YDgv7](https://photos.app.goo.gl/iKS8gJHNLPL8YDgv7)  Got any ideas about this?

---

### Post by TheFu on 2021-04-21
If you can remote into his system, just push the files. I assume you are using ssh for that?

---

### Post by imWACC0 on 2021-04-21
> **TheFu said:**
> If you can remote into his system, just push the files. I assume you are using ssh for that?

Not yet, and I know he's using Windows, that means TeamViewer. And that's fine to push the first time, but after 7 or 8... No, I need a set and forget


Right now, the question is not about FTP or how to get files to him. I can't even get to that part because I can't get on the internet yet.

---

### Post by imWACC0 on 2021-04-21
Ok, I have a WiFi USB and a PCIe card. One is wls3 and the other is wlx0026f2b3eec9. I tried adding the second to the config file...   [https://photos.app.goo.gl/7djd2C5vwoBdQvPo8](https://photos.app.goo.gl/7djd2C5vwoBdQvPo8)

Something is not working. Or I guess more accurate, there's a lot that's not working.

---

### Post by TheFu on 2021-04-21
> **imWACC0 said:**
> Not yet, and I know he's using Windows, that means TeamViewer. And that's fine to push the first time, but after 7 or 8... No, I need a set and forget

Right now, the question is not about FTP or how to get files to him. I can't even get to that part because I can't get on the internet yet.

First, need to check how far the connection is getting.  If it can't ping the LAN router using the IP, then no connection is being made.  I use wicd-cli to do that. It has a nice TUI. nmcli should be able to do that too. I've not used NM in about 10 yrs. It used to have problems with non-trivial connection and I just never bothered to learn it. wicd-cli was easier for me.

If no connection is being attempted at all, check the drivers.  Commands for that:
```
lspci -vk |egrep --after-context=8 'Ethernet|Network'
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
sudo lsusb -v  |egrep 'Ether|Network'
lsmod |grep usbnet
inxi -N
sudo lshw -C network
```
Only 1 of those should be needed, but USB network devices sometimes hide. For example, on a laptop here:
```
$ inxi -N
Network:   Card: Intel Wireless 8265 / 8275 driver: **iwlwifi**
```
only shows the wifi networking, but not the USB one.  That can be see with
```
$ sudo lsusb -v  |egrep 'Ether|Network'
Bus 002 Device 014: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
  idProduct          0x1790 AX88179 Gigabit Ethernet
      iInterface              4 Network_Interface
```
Both work. We need to see the driver and the USB output from lsusb doesn't show it, while the Wireless 8265 does - iwlwifi.
So get the USB NIC driver, I use:
```
$ lsmod |grep ax
ax88179_178a           24576  0
usbnet                 45056  1 ax88179_178a
mii                    16384  2 usbnet,ax88179_178a
```
The 'ax' works because I know the driver-name follows the device name, *AX88179 Gigabit Ethernet*. That isn't guaranteed.
**lshw -C network** shows all network devices, but isn't normally installed. Chicken/egg problem, but that command does show the device name, chip, bus, and driver. Very useful to have it installed on all systems.

BTW, Win10 supports sftp.  I've used it on someone else's system. It supports ssh-key-based credentials. Just use the ssh-
Or install **WinSCP** as the sftp/scp client.  Drag-n-drop - 2-panel setup. Supports going between Explorer and WinSCP via drag-n-drop too.  Also, Filezilla on Windows has an incompatibility with some sftp servers that should have been fixed, but wasn't last time I checked.

---

### Post by xpl01t on 2021-04-21
I think something is wrong with your wireless NIC names. I don't think you should have a MAC address in a name for your Netgear adapter.
What do you see in "*ip link show"*?

---

### Post by TheFu on 2021-04-21
> **xpl01t said:**
> I think something is wrong with your wireless NIC names. I don't think you should have a MAC address in a name for your Netgear adapter.
What do you see in "*ip link show"*?

Systemd device setup puts the MAC into some device names.  That is expected since a version of systemd released into 16.04 and later.

---

### Post by imWACC0 on 2021-04-21
Sorry, I am working on it, but Grandson is here

---

### Post by imWACC0 on 2021-04-22
Ok, maybe I'm asking the wrong question. Not how can I fix this, but how can I get one of these WiFi to connect to the internet? The guide I found uses netplan & yaml.

What is the right/better way? I sux at installing from sneaker net*. What program comes preinstalled on Server to use WiFi?











*Yes, I've been doing this for 35 years, but I still sux at command line. BASIC was a real &%@ to me. I'm a hardware person, give me a soldering iron, or stakes of parts... I'll work magic.

P.S. Sorry for dropping out, I don't get to see my grandson vary often (thanks COVID). But we did have a interesting day <evil_laugh>as the prophecy foretold</evil_laugh>[FONT=arial][/FONT]

---

### Post by TheFu on 2021-04-22
> **imWACC0 said:**
> What is the right/better way? I sux at installing from sneaker net*. What program comes preinstalled on Server to use WiFi?

Servers don't use wifi. They use wired ethernet connections. Heck, that USB-to-GigE adapter I show above had to get drivers from the desktop install. Server didn't have any.

I don't know how to install updated packages over sneaker-net. Sorry. Without networking, I'd be lost too. Basically, I'd fumble around checking things related to the drivers and try to get a .deb driver file for my kernel, my release, that doesn't have any outside dependencies. Lacking that, I'd swap in a different ethernet card that "just works."

---

### Post by imWACC0 on 2021-04-22
> **TheFu said:**
> Servers don't use wifi.


Ok, maybe the long way around? Set up a "router" that hooks into the WiFi of my network. Hard line to that, and just let the "router" do the magic part of getting on the network???<shrug> Might be easier than getting the WiFi to work with Server

---

### Post by kevdog on 2021-04-22
A little off topic -- however why the heck does Ubuntu even use netplan.d since it relies upon systemd-networkd below...why not configure networkd directly?  I never understand the rationale for this.

---

