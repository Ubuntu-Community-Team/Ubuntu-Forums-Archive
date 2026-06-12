---
title: "Firewall Configuration."
date: 2009-01-08
forum: Security
---

### Post by TayfuN on 2009-01-08
People, I'am new in firewall's, so can someone help me to configure it ? All I need is:

All incoming connection is closed, only some of them open for some ip adresses.:

SSH(22) for 3 ip adresses
FTP(21) for 3 ip adresses
HTTP(80) for all incoming traffic.

Thanks, and Ubuntu Server 8.10

---

### Post by theinnercityhippy on 2009-01-08
> **TayfuN said:**
> People, I'am new in firewall's, so can someone help me to configure it ? All I need is:

All incoming connection is closed, only some of them open for some ip adresses.:

SSH(22) for 3 ip adresses
FTP(21) for 3 ip adresses
HTTP(80) for all incoming traffic.

Thanks, and Ubuntu Server 8.10

There are various ways to do this of varying complexities. I would sugggest as you said you are new to this using a graphical firewall manger to do this.

The underlying system which controls your firewall is called iptables, and all of the gui versions simply tweak the settings for this. You can use iptables direct from the command line to do this but you may find it difficult to adjust it at a later date if your needs change without learning it thoroughly.

Two of the most popular firewall utilities for Ubuntu are Guarddog and GUFW, of which the latter i smy personal favourite, and I believe it would suit your needs better.

Either install it through your package manager 

Applications > Add/Remove Software

and search for gufw, check the box and press apply, or open a terminal

Applications > Accessories > Terminal

and type the following

```
sudo apt-get install gufw
```

Enter your password when prompted and when it has done so, go to

System > Administration > Firewall Configuration

To open the program and add it to your taskbar.

Here you will see a setting on the first screen to deny all incoming/outgoing traffic, enable and disable the firewall, and create exceptions as you require.

Hope this of help to you. If it does not open automatically when you restart, go to 

System > Settings > Sessions

And add a new entry with the name "Firewall Utility" and the command "gufw". This is the way to get software to start on bootup in Ubuntu.

-JimDog-

---

### Post by TayfuN on 2009-01-08
Thanks for such fats reply, but I don't use GUI, I need to config that by iptables and through command-line. I don't want to install GUI.

---

### Post by cdenley on 2009-01-08
```

sudo ufw enable
sudo ufw default deny
sudo ufw allow from [ip1] port ssh
sudo ufw allow from [ip2] port ssh
sudo ufw allow from [ip3] port ssh
sudo ufw allow from [ip1] port ftp
sudo ufw allow from [ip2] port ftp
sudo ufw allow from [ip3] port ftp
sudo ufw allow http

```

---

### Post by cdenley on 2009-01-08
Double post. These proxy errors I keep getting are very annoying. I'm starting to think ubuntu may not be as stable as I had thought.

---

### Post by bodhi.zazen on 2009-01-08
See also :

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

