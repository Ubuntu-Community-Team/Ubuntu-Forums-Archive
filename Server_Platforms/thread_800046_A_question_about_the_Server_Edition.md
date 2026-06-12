---
title: "A question about the Server Edition"
date: 2008-05-19
forum: Server Platforms
---

### Post by Cotsuma on 2008-05-19
I am looking into converting one of my old computers into a small server. I like ubuntu and their linux systems but if i download the linux server edition is there a way i can make it so that when it is a server it i can run stuff as if i am looking at a normal desktop. (This may not sound very clear and that is because i don't know the right words to describe it).

---

### Post by bluefrog on 2008-05-19
install "normal" ubuntu and use it as a server.

---

### Post by cdenley on 2008-05-19
Ubuntu can have all sorts of desktop configurations. Choose one.
```

sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop

```

Also, ubuntu desktop can have any server configuration
```

sudo tasksel

```

---

### Post by Cotsuma on 2008-05-19
Thank You and i will try these out and get back to you guys in a couple of days. Thank you.

---

### Post by ginjabunny on 2008-05-19
installing "ubuntu-desktop" will install everything that comes on the desktop edition, this maybe a bit slow on an older PC.

I install the server edition, but you get no gui then I add gnome using

sudo apt-get install xorg gdm gnome-core synaptic

boot into gnome (it complains that some bits are missing) then you can use synaptic to add packages later, 

If you don't want gnome to run all the time, I think that if you change the default startup runlevel it will not start gnome at boot then you can use startx to get into gnome.

---

### Post by ginjabunny on 2008-05-20
my comment about runlevels in Ubuntu is incorrect, runlevels 2-5 all start a gui (like gnome) if configured, apparently you can use sysv-rc-conf to change this behaviour.

---

### Post by Cotsuma on 2008-05-24
Ok i have the server installed but i need to install my wireless adapter from my cd but i don't know the code to access the cd drive. Any help? Sorry i am new at the whole linux server commands.

---

### Post by ArrantSquid on 2008-05-24
```

cat /etc/fstab

```

you should see entries that say /media/cdrom or the such... That'll be it!

then you'll just cd into wherever the cdrom is supposed to be (I have two listed cdrom0 and cdrom1)
```

cd /media/cdrom0

```

---

### Post by Cotsuma on 2008-05-24
Ok i need help connecting to the internet...I skipped the WIFI adapter and cd installation and just plugged the server to my ethernet hub. How do i get the server to connect to the internet because it currently isn't connected to anything (My network and the internet).

---

### Post by ArrantSquid on 2008-05-25
Do you have more than one network adapter? Does your hub have DHCP enabled or do you have to get a static ip? Is it a router or a switch? These are all usefil tidbits that help out for next time.

If you've got more than one network adapter try both. I know that I've mistakenly plugged my ethernet into eth0 when I'm configuring eth1, so try both to see which one works. If you don't have DHCP disabled on your (I'll assume router) router then you need to enable it so you can get an ip through that. And if you have a limit on DHCP users check to see that you haven't leased out too many ip's. HTH.

---

### Post by Cotsuma on 2008-05-25
Ok i am connected to the internet and i try and do sudo apt-get update
and after that it tells me "W: Failed to fetch http://" with every single url.
I want to be able to put gnome on the server so i can go thru it as if it were a desktop so i don't have to enter in commands but nothing i seem to try works.

If it helps any, I do have ubuntu-desktop installed as a second OS and when i also try and update that i run into the same Failed Error.

---

### Post by molotov00 on 2008-05-25
> **Cotsuma said:**
> Ok i need help connecting to the internet...I skipped the WIFI adapter and cd installation and just plugged the server to my ethernet hub. How do i get the server to connect to the internet because it currently isn't connected to anything (My network and the internet).

When you say it doesn't work, how do you know? have you found the config GUI or are you doing this through the command line? A bit more information would be useful here. I know you're just trying to figure it out though.

M

---

### Post by ArrantSquid on 2008-05-26
Whats the output of the following commands:

```

ping -c 3 google.com
sudo ifconfig -a

```

That will help a bit.

---

