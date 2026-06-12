---
title: "Server Edition 9.04 Wireless?"
date: 2009-09-12
forum: Server Platforms
---

### Post by Naitogunjin on 2009-09-12
Ok I have a dell desktop computer with plenty of ram and at least 80gb of memory and im installing ubuntu 9.04 server edition. 
I want to make this a server with a wireless connection.
The connection is strong enough, when i had ubuntu installed i could get 100% connectivity with the addition of my Pringle's can antenna. lol
So basically all that stuff is good.
I just cant get it to pick up my usb wireless adapter. I know it can be done. I just need the code to get it working. 
I have a Belkin G Wirless USB Network Adapter.
Any information would be helpful thanks.

(p.s. the adapter is a Belkin F5D7050v4 if that helps you any)

---

### Post by ugm6hr on 2009-09-12
Work your way through this:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by Naitogunjin on 2009-09-12
This is what it shows for inconfig and iwconfig if this helps thanks.

---

### Post by volkswagner on 2009-09-12
Since you wlan0 is listed I think the drivers are loaded.

You will want to edit interfaces file to give the necessary info.

Backup your file first.

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

Now edit.

```
sudo nano /etc/network/interfaces
```

You will want to add info such as the following (I was using WEP).  I would try to use DHCP to get it working, then try to set your static ip.

Here is an example:

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys
wireless-key 1971238AE1
wireless-channel 8
wireless-mode managed
```

Restart networking to apply changes after saving file.

```
sudo /etc/init.d/networking restart
```

---

### Post by Naitogunjin on 2009-09-12
after typing
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
i get

cp: accessing ' /etc/networks/interfaces.bak' : Not a directory

---

### Post by volkswagner on 2009-09-12
You have a typo it is network not networks.

---

### Post by Naitogunjin on 2009-09-12
oh ok. lol

---

### Post by Naitogunjin on 2009-09-13
Im confused.
How do you work GNU nano 2.0.9?

---

### Post by Java6 on 2009-09-13
Once it is opened up, you can edit the file like normal, using the arrow keys, delete,backspace and so on. To save the file, hit Ctrl+O, to Exit, hit Ctrl+X. At the bottom of the screen you see all the keyboard shortcuts. the ^ thing tells you to press Ctrl and the button next to it.

---

### Post by Naitogunjin on 2009-09-13
After i typed in the code saved and restarted it i got this.

Does this mean that my wireless is working?

---

### Post by cariboo on 2009-09-13
No you aren't getting an ip address.

You seem to be missing a few steps, try this again:

[list=1]
[*] sudo ifconfig wlan0 down
[*] sudo dhclient -r wlan0
[*]sudo ifconfig wlan0 up
[*]sudo iwconfig wlan0 essid "ESSID_IN_QUOTES", the essid is the name you have given your router, for instance if you have a Linksys and you haven't changed the essid, it would be Linksys
[*]sudo iwconfig wlan0 mode Managed
[*]sudo dhclient wlan0
[/list]

If you could set up a wired connection to the server and do this remotely, it sure would be a lot easier for you.

---

### Post by Naitogunjin on 2009-09-13
everything works until i get to

sudo iwconfig wlan0 mode Managed

then it says:

Error for wireless request "Set Mode" (8B06) :
      SET failed on device wlan ; No such device.


if i had a wired connection could i come back and fix it easier?

---

### Post by cariboo on 2009-09-13
Have you got encryption turned on in the router, if so try the commands again.

If you set up wireless remotely, you could paste the output of a command directly in your post, instead of having to take a picture of the screen.

Are you sure you are using the correct driver for your wireless device?

Also a wired connection is faster and more reliable, which is what you want when running a server.

---

### Post by Naitogunjin on 2009-09-13
This time it didnt stop me on the command:
sudo iwconfig wlan0 mode Managed

but it gave the same result here it is.

---

