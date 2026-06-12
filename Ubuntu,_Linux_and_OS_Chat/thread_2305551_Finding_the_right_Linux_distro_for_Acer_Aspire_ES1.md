---
title: "Finding the right Linux distro for Acer Aspire ES1-131"
date: 2015-12-06
forum: Ubuntu, Linux and OS Chat
---

### Post by myron.schultz01 on 2015-12-06
If you purchased an Acer Aspire ES1-131, and you want to load Linux, this may be worth a read. 

I recently purchased an Acer Aspire ES1-131,which can be purchased in Germany with Linpus Linux.I was quite surprised when most of the usual Linux suspects would not work on this laptop (even though it came pre-load with Linous Linux!).

After some experimentation, on distro that I have found to work is Ubuntu 14.04.

Has anyone else had similar issues?

Hope this helps.

---

### Post by oldfred on 2015-12-07
Acer in UEFI mode needs supervisor password and then setting trust on Ubuntu/grub2's efi boot files.

 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

      
 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09](http://members.iinet.net/~herman546/2014_02_09) - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop.html

---

### Post by myron.schultz01 on 2015-12-08
Hi Olfred,

Thank you for this! Would have saved me plenty of time if I had found this first.

Question:  If I managed to install Ubuntu 14.04 without a supervisor password and  then setting trust on Ubuntu/grub2's efi boot files...and all appears to  work fine...although a little sluggish...would it still make sense to  go through this exercise...with reference to possibly improving  performance?

Thanking you,

Myron

---

### Post by oldfred on 2015-12-08
If it is working, I do not think that is the issue.
You may need another boot parameter.
And if a new system 15.10 and then 16.04 next year will work better.  It takes a while before kernels support software & drivers are updated. And then they have to be included in a new distribution. But 14.04.3 is somewhat newer also.

Often some driver some where is complaining or not loading.
With 14.04 you still have upstart.
 Older systems with Upstart. so want to look at dmesg and see if you have errors or long times between time stamps. Not all errors or warnings are vital.

gksudo gedit /var/log/dmesg
sudo grep -E -i "error|warning" /var/log/dmesg

---

### Post by myron.schultz01 on 2015-12-08
Much appreciated Olfred!

---

