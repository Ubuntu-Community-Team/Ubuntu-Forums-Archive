---
title: "Slow scrolling in Ubuntu 10.04 LTS Server"
date: 2010-06-19
forum: Server Platforms
---

### Post by deltatux on 2010-06-19
Hey guys,

I just installed Ubuntu Server 10.04 LTS and I immediately notice something's not right. It seems like text is scrolling very slowly down my screen when I do directory listings or if it's printing lines of text on my screen. It used to be butter smooth in 9.10 but now it feels like Ubuntu's having some rendering issues rendering the bash shell on Ubuntu Server 10.04 LTS smoothly.

Is there a way to fix this?

Thanks,
deltatux

---

### Post by mörgæs on 2010-06-20
Sounds like a problem regarding the graphics driver. Have you tried changing or tweaking the driver?

---

### Post by denarced on 2010-06-20
You're talking no-GUI, just the terminal?
Directly on the server or through SSH?
When you say smooth you mean in a blink of an eye?

Sorry I'm a bit confused since smooth is usually used when you're talking about GUIs and basic server installation doesn't come with X

---

### Post by deltatux on 2010-06-20
> **mörgæs said:**
> Sounds like a problem regarding the graphics driver. Have you tried changing or tweaking the driver?

I don't think there's drivers for the bash shell since the X server isn't involved.

> **denarced said:**
> You're talking no-GUI, just the terminal?
Directly on the server or through SSH?
When you say smooth you mean in a blink of an eye?

Sorry I'm a bit confused since smooth is usually used when you're talking about GUIs and basic server installation doesn't come with X

Just the terminal just like what most server admins use. Not an X environment, just standard shell. I'm not logged in through SSH though.

I just tried SSHing to the Ubuntu Server box, and it seems like this issue doesn't affect SSH so there must be a driver or display error. Does anyone know what controls the display output for a standard CLI? I know how to fix X server driver errors but not for standard CLI.

Could this be a VirtualBox specific issue? I am indeed running it in VirtualBox but never had this issue with Ubuntu 9.10 nor any other Linux installations that I have.

Thanks,
deltatux

---

### Post by kevin11951 on 2010-06-20
> **deltatux said:**
> I don't think there's drivers for the bash shell since the X server isn't involved.



Just the terminal just like what most server admins use. Not an X environment, just standard shell. I'm not logged in through SSH though.

I just tried SSHing to the Ubuntu Server box, and it seems like this issue doesn't affect SSH so there must be a driver or display error. Does anyone know what controls the display output for a standard CLI? I know how to fix X server driver errors but not for standard CLI.

Could this be a VirtualBox specific issue? I am indeed running it in VirtualBox but never had this issue with Ubuntu 9.10 nor any other Linux installations that I have.

Thanks,
deltatux

It is a VirtualBox specific problem, as I have been plagued by it as well... I dont know how to fix it off the top of my head...  Have you tried installing the guest extras?

sudo apt-get install build-essential

select the guest extras from the VBox menu.

mount -t auto /dev/cdrom /mnt

run the linux file for your architecture in /mnt

---

### Post by CharlesA on 2010-06-20
Happens in VBox for me as well, no idea how to fix it either. I don't think installing Guest Additions did anything.

---

### Post by deltatux on 2010-06-20
> **kevin11951 said:**
> It is a VirtualBox specific problem, as I have been plagued by it as well... I dont know how to fix it off the top of my head...  Have you tried installing the guest extras?

sudo apt-get install build-essential

select the guest extras from the VBox menu.

mount -t auto /dev/cdrom /mnt

run the linux file for your architecture in /mnt

Thanks for your suggestion but it doesn't do a single thing.

I thought of this as a solution but it doesn't seem to resolve the issue.

Cheers,
deltatux

---

### Post by Tamás Kiss on 2010-12-03
Hi!

I know this topic is outdated, but the problem still exists and I found the answer:

The module-init-tools package installs the **/etc/modprobe.d/blacklist-framebuffer.conf** file, in which it blacklists all the console framebuffer modules. For some reason the **vga16fb** module is not on the list, and (at least for me) it is loaded during startup and causes the slow scrolling. Try to blacklist it and reboot!

---

### Post by leezenz on 2011-10-08
@Tamás Kiss
I also had the trouble with slow scrolling in text-mode inside virtual box. Blacklisting the vga16fb module did the trick, now scrolling is back to normal. Thanks a lot for the solution!

---

