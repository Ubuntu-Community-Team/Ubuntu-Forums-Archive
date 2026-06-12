---
title: "What cool stuff can you do with Ubuntu and a Bluetooth phone?"
date: 2008-01-02
forum: The Cafe
---

### Post by Bou on 2008-01-02
I have never been a heavy bluetooth user, in spite of having a bluetooth enabled phoned. Now I have been given a bluetooth adapter for my laptop and would like to impress my girlfriend so... what exactly can you do with Ubuntu and a bluetooth enabled phone?

I know you can browse the phone's contents -which is pretty cool- and I've read you can use it as a remote, but I haven't been able to make that work. Any cool stuff YOU got working? Anything in the repos?

---

### Post by FuturePilot on 2008-01-02
I'm able to browser my phone through Nautilus with gnome-vfs-obexftp. I would recommend installing [Blueman]("http://blueman.tuxfamily.org/"). It's an awesome GTK Bluetooth manager. There's a repo on that page. 
As for a remote this is how I got it working.
```
gksudo gedit /etc/init.d/bluetooth
```
Change HIDD_ENABLED=0 to =1
Restart the Bluetooth services
```
sudo /etc/init.d/bluetooth restart
```
Now make sure your phone has Bluetooth activated and is discoverable. Then scan for your phone
```
hcitool scan
```
You should get a MAC address. Something like ```
00:11:22:AA:BB:CC     PhoneName
```
Now take the MAC address that you got from above and use it to connect
```
sudo hidd --connect 00:11:22:AA:BB:CC
```
Now you should be able to control the mouse from your phone. I'm not sure if your phone has a built in bluetooth remote so you'll have to see how that is done.

---

### Post by Bou on 2008-01-02
> **FuturePilot said:**
> I would recommend installing [Blueman]("http://blueman.tuxfamily.org/")

I noticed it allows you to "bond" your phone to the computer. What's that for?

---

### Post by King_Critter on 2008-01-02
[http://getdeb.net/app.php?name=BlueProximity](http://getdeb.net/app.php?name=BlueProximity)

Blue Proximity. From the above page:

> This software helps you add a little more security to your desktop. It does so by detecting one of your bluetooth devices, most likely your mobile phone, and keeping track of its distance. If you move away from your computer and the distance is above a certain level (no measurement in meters is possible) for a given time, it automatically locks your desktop (or starts any other shell command you want).

---

### Post by rowanparker on 2008-01-02
Can bluetooth devices measure distance?
Or does it do it on signal strength or something?

Edit: I see, you just get a number, it must be signal strength.
BlueProximity is really useful. Although can be annoying if you forget, lol.

---

### Post by FuturePilot on 2008-01-02
> **Bou said:**
> I noticed it allows you to "bond" your phone to the computer. What's that for?

In order to communicate between the phone and the computer you need to bond (sometimes called pairing) the phone to the computer. Basically all it is is you're telling the computer you trust this bluetooth device and you will allow it access to the computer. And vice versa.

---

### Post by sumguy231 on 2008-01-02
If you're a Kubuntu user you can use KBlueLock, part of KBluetooth, which is the same thing but for KDE.

---

### Post by Spike-X on 2008-01-03
Take over the world, probably!

[IMG]http://my.opera.com/kaylinq/homes/blog/pinkybrain.jpg[/IMG]

---

