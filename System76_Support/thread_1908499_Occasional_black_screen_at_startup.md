---
title: "Occasional black screen at startup"
date: 2012-01-13
forum: System76 Support
---

### Post by cephalopoda on 2012-01-13
Hello,

I recently purchased a System76 Lemur notebook. Overall, I am very happy with it. However, occasionally when I start it, it fails to load. When this happens it will usually fail right before it gets to the login screen and all I will be left with is a black screen that often reads "[ok]".  I will then press ctrl+alt+del to restart it and usually it will then load all the way through.

It may be useful to know that I re-installed Ubuntu 11.10 from liveUSB, so this is not the System76 version of Ubuntu.

Any suggestions for fixing this problem would be greatly appreciated.

Thanks!

---

### Post by isantop on 2012-01-13
Next time it happens, try pressing Ctrl+Alt+F1 and logging in, then running this command:

```
sudo lightdm
```

Send me the output of that, or report on any other results.

---

### Post by cephalopoda on 2012-01-13
> **isantop said:**
> Next time it happens, try pressing Ctrl+Alt+F1 and logging in, then running this command:

```
sudo lightdm
```Send me the output of that, or report on any other results.

Ok, When I entered "sudo lightdm" it brought me back to the black "[ok]" screen. Then when I pressed ctrl+alt+F1 again it brought me back to the terminal screen and it read, "Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions?"

---

### Post by isantop on 2012-01-16
Can you perform a disk check on the USB drive you used to install Ubuntu? You'll want to put it in and begin to boot it up. When you get to the purple screen with the white symbols at the bottom, press a key to bring up the menu. Choose your language, then select "Check Disk for Defects".

---

### Post by cephalopoda on 2012-01-17
Ok, I did that and I got: "Disk check complete: No defects found"

---

### Post by cephalopoda on 2012-01-19
Any other suggestions? This still happens about once every 10 startups.

Thanks.

---

### Post by isantop on 2012-01-19
This is starting to sound like a one-off race condition. Can you try running this command to see if it will bump you to the desktop?

```
startx
```

---

### Post by cephalopoda on 2012-01-21
Yes, it does bump me to a desktop. Is there anyway I can start Unity and login to my account? Thanks.

---

### Post by isantop on 2012-01-23
Not from here, but there may be something we can do to fix this without a reinstallation.

Go ahead and establish a wired internet connection, then run these commands from the terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

It will ask you for your password, and may ask you to confirm with y (yes) or n (no). Go ahead and choose yes.

This will update your system, and ensure that everything is up to date. If it can be solved without reinstalling, this will do it.

---

### Post by cephalopoda on 2012-02-02
> **isantop said:**
> Not from here, but there may be something we can do to fix this without a reinstallation.

Go ahead and establish a wired internet connection, then run these commands from the terminal:

```
sudo apt-get update
sudo apt-get upgrade
```It will ask you for your password, and may ask you to confirm with y (yes) or n (no). Go ahead and choose yes.

This will update your system, and ensure that everything is up to date. If it can be solved without reinstalling, this will do it.

That appears to have done it. I haven't had the black screen problem since. Thanks a lot.

---

