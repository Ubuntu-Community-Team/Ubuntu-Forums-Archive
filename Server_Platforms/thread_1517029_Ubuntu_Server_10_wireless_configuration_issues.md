---
title: "Ubuntu Server 10 wireless configuration issues"
date: 2010-06-24
forum: Server Platforms
---

### Post by MacKz0r on 2010-06-24
I'm running a home server (nothing serious, just to mess with) with a old IBM T30 laptop.

I can run 'iwconfig' and get 'eth0' and 'wifi0' to show up with my network info but they both say "Acess Point: Invalid"

This is my config: 
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wireless-mode managed
wireless-essid MacKsHouse
wireless-key (key, really long)

```

I'm using WPA-PSK and TKIP. 

I tried a lot of combinations of configurations for it, nothing seems to work. I tried:
```

sudo iwconfig eth0 essid "MacKsHouse"
sudo iwconfig eth0 key (mykey)
```

Nothing I do seems to work. Any help? :)

---

### Post by MacKz0r on 2010-06-26
> **MacKz0r said:**
> I'm running a home server (nothing serious, just to mess with) with a old IBM T30 laptop.

I can run 'iwconfig' and get 'eth0' and 'wifi0' to show up with my network info but they both say "Acess Point: Invalid"

This is my config: 
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wireless-mode managed
wireless-essid MacKsHouse
wireless-key (key, really long)

```I'm using WPA-PSK and TKIP. 

I tried a lot of combinations of configurations for it, nothing seems to work. I tried:
```

sudo iwconfig eth0 essid "MacKsHouse"
sudo iwconfig eth0 key (mykey)
```Nothing I do seems to work. Any help? :)

Bump. No one knows? :X

The error I get is:
Error for wireless request "Set Encode" (8B2A): 
    SET failed on device wifi0 ; Invalid argument

Using:
sudo iwconfig essid MacKsHouse key 5e35c0de0922b917516fe55897011c26e9cb53cc9cbcd7cc98c83ca16b6a039c[COLOR=#000000][FONT=Times New Roman][FONT=Arial][/FONT][/FONT][/COLOR] channel 1

---

### Post by tgalati4 on 2010-06-26
Does the server have wireless drivers?

Post the output of:

lsmod

---

### Post by MacKz0r on 2010-06-26
> **tgalati4 said:**
> Does the server have wireless drivers?

Post the output of:

lsmod

I disabled security on my wireless configuration and it connected with no problem.

So yes, it does have the wireless drivers and they are working. 

But I obviously don't want a unsecured network. Any ideas?

---

### Post by volkswagner on 2010-06-26
Some drivers only support certain security protocols.  You **may** find what supported security your device has in dmesg.

You can try some leaner choices like wep to see if that is the case.

---

### Post by tgalati4 on 2010-06-26
Since the T30 is a few years old, it's possible that the wireless card doesn't support WPA.  Try WEP with either an open key or a shared key.

---

