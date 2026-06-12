---
title: "grub-emu is displaying garbage text"
date: 2019-03-04
forum: Server Platforms
---

### Post by JoyceBabu on 2019-03-04
I have a remote server running Ubuntu 18.04. When I ran apt upgrade today, I got an error message from grub that original boot device is not found, asking me to select the disk for installing boot loader. As per the suggestion on the prompt, I selected all listed devices. But I still got some error messages when installing the boot loader.

I tried to run grub-emu to verify that the bootloader is installed correctly. I am getting the following screen, with lots of garbage text. What is wrong?

[IMG]https://i.stack.imgur.com/tOrK8.png[/IMG]

I am connected to the remote server via SSH, from a Mac OSX terminal.

---

### Post by howefield on 2019-03-04
Thread moved to the "*Server Platforms*" forum.

---

### Post by JoyceBabu on 2019-03-09
Can someone please help me with this?

---

### Post by Doug S on 2019-03-09
I had never heard of grub-emu before.
I installed it on my test server and got the same as you from both remote via ssh and local at the terminal.
I installed it on a test Ubuntu 18.04 desktop and it worked fine (albeit annoying to use), opening an independent window when launched.

Conclusion: It isn't for servers, only desktops with fancy GUI stuff.

---

### Post by JoyceBabu on 2019-03-09
It did work on my local server running Ubuntu Server 18.04. 

[https://i.ibb.co/W0Nt2gM/Screenshot-2019-03-10-at-12-13-48-AM.png](https://i.ibb.co/W0Nt2gM/Screenshot-2019-03-10-at-12-13-48-AM.png)

It did not open any new windows. I had to press 'c' to go to command mode, and type 'exit' to quit the program and go back to the bash shell.

---

