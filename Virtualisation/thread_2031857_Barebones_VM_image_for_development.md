---
title: "Barebones VM image for development"
date: 2012-07-22
forum: Virtualisation
---

### Post by vmboss on 2012-07-22
Hi : I'd like a barebone Ubuntu VM image for development and production use. The goal is to not have any extras in this image but only sufficient components to run a web app server in it, possibly in Amazon EC2. 
The image will be used for enterprise app development. I'd like to customize / refine the barebone image to suite my app's purposes. 
How can I download or create such an image using the latest Ubuntu release? Any references to documentation will be great.

Thanks in advance!
Mike

---

### Post by uRock on 2012-07-22
Hello and welcome to the forums,

Ubuntu server will have extras, which may be uninstalled. You may also want to look at the ubuntu minimal installer.

[Ubuntu Server]("http://www.ubuntu.com/download/server")

[Ubuntu Minimal Installer]("http://https://help.ubuntu.com/community/Installation/MinimalCD/")

Edit: Moved to ***Virtualization*** sub-forum.

---

### Post by Cheesemill on 2012-07-23
When you get to the attached screenshot, hit F4 and select 'Install a minimal virtual machine'.

This will give you the smallest system possible to start off with (202 packages, 659MB disk used).

---

### Post by josephmills on 2012-07-23
Ubuntu Core is also a option 
[https://wiki.ubuntu.com/Core/InstallationExample](https://wiki.ubuntu.com/Core/InstallationExample)
[https://wiki.ubuntu.com/Core](https://wiki.ubuntu.com/Core)

Hope that this helps

---

### Post by uRock on 2012-07-23
> **Cheesemill said:**
> When you get to the attached screenshot, hit F4 and select 'Install a minimal virtual machine'.

This will give you the smallest system possible to start off with (202 packages, 659MB disk used).

I have learned something new today! That is neat!

---

### Post by Cheesemill on 2012-07-23
> **uRock said:**
> I have learned something new today! That is neat!
It used to be available as a separate download under the JeOS (Just enough OS) moniker before it was rolled into the server ISO.
[https://help.ubuntu.com/community/JeOS](https://help.ubuntu.com/community/JeOS)

---

### Post by sandyd on 2012-07-23
> **vmboss said:**
> Hi : I'd like a barebone Ubuntu VM image for development and production use. The goal is to not have any extras in this image but only sufficient components to run a web app server in it, possibly in Amazon EC2. 
The image will be used for enterprise app development. I'd like to customize / refine the barebone image to suite my app's purposes. 
How can I download or create such an image using the latest Ubuntu release? Any references to documentation will be great.

Thanks in advance!
Mike
Have you taken a look at bitnami?
[http://bitnami.org/stack/lampstack/#cloudImage](http://bitnami.org/stack/lampstack/#cloudImage)

---

