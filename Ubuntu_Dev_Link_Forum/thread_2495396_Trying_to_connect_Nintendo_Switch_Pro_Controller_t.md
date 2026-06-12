---
title: "Trying to connect Nintendo Switch Pro Controller through /dev/hidraw*"
date: 2024-02-17
forum: Ubuntu Dev Link Forum
---

### Post by medpatel on 2024-02-17
Hello!

This is my first post! some insight into my issue would be greatly appreciated.

First and foremost, I am a novice with Linux so please be patient with me.

I know that there are drivers out there for connecting the pro controller; however, I am trying to make a wired connection through USB and I want to read and write to /dev/hidraw* file instead. This is for my own learning purposes.

When I connect to the controller through USB there, is a new /dev/hidraw* file created.

I am trying to imitate the solution in this forum:
[URL="https://gbatemp.net/threads/reverse-engineering-the-switch-pro-controller-wired-mode.475226/"]https://gbatemp.net/threads/reverse-engineering-the-switch-pro-controller-wired-mode.475226/
[/URL]
Now, I am thinking that I should be able to open the /dev/hidraw* file and use read and write system calls to connect and get raw data for the button states on the controller. However, so far, when I read from the controller I'm not able to get anything.

For reading and writing bytes, I use python3:
For reading: file = open("/dev/hidraw*", "r")
For writing: file = open("/dev/hidraw*", "wb")

I did create a rules.d file called 50-pro-controller.rules with the following text:
```
# Nintendo Switch Pro Controller over USB hidraw
KERNEL=="hidraw*", SUBSYSTEM=="hidraw", ATTRS{idVendor}=="057e", ATTRS{idProduct}=="2009", MODE="0666", TAG+="uaccess"
```

Any advice for what I should do?

---

