---
title: "After installing ubuntu server happened nothing"
date: 2012-12-15
forum: Server Platforms
---

### Post by Raafat1991 on 2012-12-15
Hi guys....simply after installing ubuntu server all what i got is a black screen with prompt to username and password after that.



any an idea thank you...

---

### Post by steeldriver on 2012-12-15
Um... what exactly are you expecting to happen? 

Can you log in at that prompt? 

The Ubuntu server edition is just that... a server, no GUI

---

### Post by Raafat1991 on 2012-12-15
> **steeldriver said:**
> 

The Ubuntu server edition is just that... a server, no GUI


Whaaaat  :oops:? i was expected to be GUI !! okay thank you hhhh that's forested .


Are all type of ubuntu server like my friend (no GUI) ?

---

### Post by Cheesemill on 2012-12-15
> **Raafat1991 said:**
> Are all type of ubuntu server like my friend (no GUI) ?

Yes.

Ubuntu Server has always been a command-line only system.
It is possible to install a GUI on top of Ubuntu server though.

---

### Post by Raafat1991 on 2012-12-15
> **Cheesemill said:**
> Yes.

Ubuntu Server has always been a command-line only system.
It is possible to install a GUI on top of Ubuntu server though.


How ?

---

### Post by alfa16vjtd on 2012-12-15
Login into your server using the username and password you gave in during the installation

Then do

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Cheesemill on 2012-12-15
> **alfa16vjtd said:**
> Login into your server using the username and password you gave in during the installation

Then do

```
sudo apt-get update
``````
sudo apt-get install ubuntu-desktop
```

If you are going to do this then there is no point in installing Ubuntu Server, you may as well have just installed Ubuntu Desktop to start off with (you end up with exactly the same system).

As far as I am concerned there is no need to install a GUI on Ubuntu Server, all of the configuration is done by editing text files which is just as easy from the command line. Installing a GUI just uses up resources unneccasarily and provides a larger attack surface for hackers.

If you must install a GUI then go for something lightweight like LXDE but without the applications you would usually get by installing Lubuntu:
```
sudo apt-get install --no-recommends lubuntu-desktop
```

---

### Post by Raafat1991 on 2012-12-25
Thank you everyone what you said to me is nice...thank you again

---

