---
title: "Daru2 rebooted this morning to no networking"
date: 2009-08-15
forum: System76 Support
---

### Post by imhavoc on 2009-08-15
I rebooted my Daru2 this morning, and no networking came up. 

Running ifconfig shows only lo, vmnet1 and vmnet8. No LAN, no Wifi.

Tried booting under recovery mode, still nothing.

Any ideas?

---

### Post by imhavoc on 2009-08-15
Is is possible that the network card could have 'cooked off?' If so, how much is a replacement card?

---

### Post by jdb on 2009-08-15
> **imhavoc said:**
> I rebooted my Daru2 this morning, and no networking came up. 

Running ifconfig shows only lo, vmnet1 and vmnet8. No LAN, no Wifi.

Tried booting under recovery mode, still nothing.

Any ideas?

Could you have accidentally hit the network button?
It's just right of the P2 button.

jdb

---

### Post by imhavoc on 2009-08-15
jdb, I should have included that in my message.

No, I did not turn off wireless from the wireless button. The light is even on! (How weird is that?)

Added to that is the fact that both the WLAN and LAN are missing from the system information.

---

### Post by jdb on 2009-08-15
> **imhavoc said:**
> jdb, I should have included that in my message.

No, I did not turn off wireless from the wireless button. The light is even on! (How weird is that?)

Added to that is the fact that both the WLAN and LAN are missing from the system information.

What is the output of these:

```
ifconfig
iwconfig
```

Try:

```
sudo /etc/init.d/networking restart
```

If it doesn't work, what is the output?

What do you get when you run:

```
lsmod | grep iw
```


jdb

---

### Post by jdb on 2009-08-15
> **jdb said:**
> What is the output of these:

```
ifconfig
iwconfig
```

Try:

```
sudo /etc/init.d/networking restart
```

If it doesn't work, what is the output?

What do you get when you run:

```
lsmod | grep iw
```


jdb
I re-read your original post, no eth or wlan entries is odd.

You might try:

```
sudo dpkg-reconfigure network-manager
```


If that doesn't work:

```
sudo apt-get --reinstall install network-manager
```

jdb

---

### Post by imhavoc on 2009-08-19
jdb,

When I run iwconfig, I get...
wlan0 .... <stuff>

I do get some information on a wireless device, but everything is at '0'.

(I'm too lazy to type it all.)

when I run ifconfig, I get ONLY lo.

I ran
```
sudo dpkg-reconfigure network-manager
```

Everything was found in-place.

I can't run 
```
sudo apt-get --reinstall install network-manager
```

because I have no network

---

### Post by imhavoc on 2009-08-19
Does anyone know if that network card will play well with Linux?

[http://www.antonline.com/p_MSI-Computer--MS-6890-010--WIRELESS-N-11B-G-N-1T2RX-PCIE-MINI-CARD-FOR-NOTEBOOK-PC-_608170.htm](http://www.antonline.com/p_MSI-Computer--MS-6890-010--WIRELESS-N-11B-G-N-1T2RX-PCIE-MINI-CARD-FOR-NOTEBOOK-PC-_608170.htm)

I think this one is the original card:
[http://www.antonline.com/p_Intel--WM3945AGM1WB--Intel-Pro-wireless-3945ABG-Network-Connection---Network-Adapter---Mini-pci-Expre-_210515.htm](http://www.antonline.com/p_Intel--WM3945AGM1WB--Intel-Pro-wireless-3945ABG-Network-Connection---Network-Adapter---Mini-pci-Expre-_210515.htm)

---

### Post by jdb on 2009-08-19
> **imhavoc said:**
> jdb,

When I run iwconfig, I get...
wlan0 .... <stuff>

I do get some information on a wireless device, but everything is at '0'.

(I'm too lazy to type it all.)

when I run ifconfig, I get ONLY lo.

I ran
```
sudo dpkg-reconfigure network-manager
```

Everything was found in-place.

I can't run 
```
sudo apt-get --reinstall install network-manager
```

because I have no network

I don't think it's hardware, but you might try it from a live CD.

I would hate to do a re-install for something like this but it's always a last resort if it works from a live CD.

I don't even like to reboot to fix things if I can figure out what to restart :)

Just this type of thing is the reason I changed to Archlinux, configuration is not the mystery it is in Ubuntu.

jdb

---

### Post by imhavoc on 2009-08-19
jdb,

I HATE it when I'm wrong!

On your recommendation, I booted off a stick I had from another project. The system came up and found the wireless device.

eth0 and wlan0 both appear.....

Now, how did my installed Ubuntu get broken, and how can I fix it?

---

### Post by PatrickVogeli on 2009-08-19
Have you checked if and older kernel is working?

---

### Post by imhavoc on 2009-08-19
PatrickVogeli,

I tried booting the older kernel on the system, and networking still fails.

---

### Post by jdb on 2009-08-19
> **imhavoc said:**
> PatrickVogeli,

I tried booting the older kernel on the system, and networking still fails.

These are a few files I would look at:

/etc/network/interfaces
These are the only 2 uncommented line you should have:
 auto lo
 iface lo inet loopback

/etc/udev/rules.d/70-persistent-net.rules
/etc/udev/rules.d/75-persistent-net-generator.rules
Mainly check that these are there.

It's really odd that eth0 is missing.

jdb

---

### Post by imhavoc on 2009-08-20
jdb, everything was in place.

backed up the /home /etc directories and downloaded 9.04 last night. Burned and rebooted onto the install disk this morning. Networking came up just fine, so I repartitioned and installed.

Now, the pain of reinstalling my weird and wacky assortment of packages over the next couple of weeks.

---

### Post by jdb on 2009-08-20
> **imhavoc said:**
> jdb, everything was in place.

backed up the /home /etc directories and downloaded 9.04 last night. Burned and rebooted onto the install disk this morning. Networking came up just fine, so I repartitioned and installed.

Now, the pain of reinstalling my weird and wacky assortment of packages over the next couple of weeks.

Were you on 9.04 before?
If so, this might be interesting.
Restore the old /etc stuff to some sub-directory, tmp would do.

Install meld.

meld /etc /tmp/etc

the green up & down arrows take you to the next differing file & double clicking a file opens a new pane that compares the files.

Whatever got hosed is probably somewhere in the etc tree.

jdb

---

### Post by imhavoc on 2009-08-20
unfortunately, i was running 8.10.

The only thing I can think of that would have hosed the system is that the last thing I did before going to bed the night before was to install Adobe's AIR installer so that I could run an AIR app.

I will not be messing with AIR again for a while.

---

### Post by jdb on 2009-08-20
> **imhavoc said:**
> unfortunately, i was running 8.10.

The only thing I can think of that would have hosed the system is that the last thing I did before going to bed the night before was to install Adobe's AIR installer so that I could run an AIR app.

I will not be messing with AIR again for a while.

Ha Ha, I have a bad habit of doing things that trash my system.
I back my data up continuously & my system every few days.
I've had enough practice, I can reformat & reload in about 5 or 10 minutes, LOL.

jdb

---

