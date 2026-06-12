---
title: "Need simple instructions to make a bootable flash drive for linu or ubuntu for windo"
date: 2017-09-15
forum: Ubuntu, Linux and OS Chat
---

### Post by rhondas on 2017-09-15
[COLOR=#000000]I want make a usb flash drive 8 GB with linux or ubuntu on it for my PC with windows XP . Im am totally lost to this new lite linux and more downloads when it comes to the part of getting an installer and then the lite linux for example . I tried to do this and it just dont go on the flash drive. I need a step by step simple instruction help like when do I put in the flash drive, before I download the installer ,and the lite linux and where does this download go and how do I get it onto the flash drive would I have to toggle F12 first before and set it to use the usb flash drive first or what? I even searched for a installation program and the lite linux ,even went to Youtube, no one explains just what sequence to do this in a step by step simple procedure . thank you if you can help me with this . rhondas[/COLOR]:confused:

---

### Post by mastablasta on 2017-09-15
1. donwload the linux image 
2. use image to USB "burning" application (you can use LinuxliveUSB, Yumi, Unetbootin, pendrive linux...)
3. after the image is transfered to USB using the app of your choice, reboot the PC with USB inside. yes the USB has to be used first (boot from USB), so set it like that in BIOS.
4. install linux. this will erase all data on disk, so make sure you back it up first. there are a few linux distributions that can help you and image the disk such as for example redo backup or clonezilla.

5. if you want dual boot you need to defrag the drive and then create emtpy disk space (informatted) first using windows disk manager.

if you only want to play with linux a bit you can also try virtualbox (if you have enough ram): [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by TheFu on 2017-09-15
Welcome to the** Ubuntu** Forums.

The Linux-Lite manual has a video showing what you are asking, I think:
[https://www.linuxliteos.com/manual/install.html#llusbwin](https://www.linuxliteos.com/manual/install.html#llusbwin) 

If F12 should be pressed or not is a question about your specific hardware.  Some use F2, others F10, still others ESC.  Just depends on the specific BIOS installed.  I call this the "Magic key."  F12 might be it or F10 or F8 or F2 or ESC or DEL or .... the motherboard manual should say.

I'd never heard of Linux Lite - it is NOT an official Ubuntu flavor.   If you want a low resource, Linux that **is** official from Ubuntu, then Lubuntu is probably what you want.  My Mom ran Lubuntu on a Pentium4 in 2010 and was very happy.

There is also the possibility that the flash drive and computer aren't compatible for this sort of operation.  Just last week, I ran into a cheap flash drive from a user at our LUG which wouldn't let my laptop create a bootable install, but did let someone with another laptop do it.  I've seen this with all sorts of flash drives. Usually they work fine for storing data, but booting is a different issue completely.

[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows) is the Ubuntu guide.
[https://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](https://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/) is from a reputable source too.

Sometimes nerds forget to say the obvious stuff. That is our failure.

Sorry, I cannot help more. Haven't used Windows for this in ... 5+ yrs, maybe longer.

Another option is to find your local Linux Users Group, LUG, contact them and see if they can help.  My LUG is having an "InstallFest" tomorrow with over 130 people signed up in collaboration with the local University.  Ours requires being signed up to ensure we had enough volunteer helpers for everyone during the day.  Just google "linux" and your town or local college or local university or metro area or makerspace name to see if they can help.

If you are creating a bootable flash drive from Windows, boot into windows, push the flash drive in, use the tool to "burn" the ISO to the flash drive. Close the flash maker down.  Leave the flash drive in the computer.  Reboot ... press the "magic key" to get into the boot device menu ... 

The flash device should show up in that menu, if it doesn't, there are a few possible problems.  If the flash drive does show up and you've correctly created the boot flash, select it.  that should flash the screen 1-3 times and some text might show up as it boots.

The older the computer, the more likely there will be issues.  If you can post the exact model, vendor, of the computer or motherboard, (or better google it with "ubuntu install",  any difficulties that others have solved might come up in the results.

---

### Post by ajgreeny on 2017-09-15
@ rhondas

Please note that I have merged the two duplicate threads you created and removed one of the duplicate posts as it is no longer needed.
**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help.

---

### Post by genericvii143 on 2017-09-16
Just download Rufus program is portable and works great.

---

### Post by rhondas on 2017-09-16
what am I doing wrong , this is what I get [IMG]http://imgbox.com/Co8pNwhT[/IMG]

---

### Post by rhondas on 2017-09-16
> **rhondas said:**
> what am I doing wrong , this is what I get [IMG]http://imgbox.com/Co8pNwhT[/IMG]

thanks for the help  maybe  I did something wrong   need more help  please here what I did get .


[http://imgbox.com/Co8pNwhT](http://imgbox.com/Co8pNwhT)

---

### Post by coffeecat on 2017-09-16
> **rhondas said:**
> thanks for the help  maybe  I did something wrong   need more help  please here what I did get .


[http://imgbox.com/Co8pNwhT](http://imgbox.com/Co8pNwhT)


That screenshot shows that you are running FreeDOS. I don't think you'll be able to prepare an Ubuntu or Linux USB from within FreeDOS. In your first post, you say that your computer is running Windows XP, which is not FreeDOS. Parts of the replies you have received so far tell you about software that you can run in Windows XP to create a Linux USB. Those mentioned applications are GUI ones, so I very much doubt they'll run in FreeDOS.

Perhaps you could clarify exactly what you are doing and with which operating system, and which Linux operating system you want on a USB device. Please note that Linux Lite has nothing to do with Ubuntu, so this forum is not the best place to get help with Linux Lite.

---

### Post by rhondas on 2017-09-17
do I instal both the installer  and the linux lite on the flash drive?

---

### Post by sudodus on 2017-09-17
Ubuntu desktop iso files contain software that can run a live session of the Ubuntu operating system, and it also contains an installer, that can install Ubuntu from the live session or from a special 'install session' to an internal drive of your computer.

I don't know about Linux Lite, but I would guess, that its iso files are similar to Ubuntu desktop iso files.

When you use a tool, for example Rufus in Windows, it will create a USB boot drive that you can use both to run a live session and to install the operating system into the computer's internal drive.

---

### Post by TheFu on 2017-09-17
> **rhondas said:**
> do I instal both the installer  and the linux lite on the flash drive?

If you don't answer the questions asked, nobody can help.
The image you posted doesn't show MS-Windows.  All the provided instructions so far assumed MS-Windows. FreeDOS is NOT Windows, so we haven't helped you at all. 

And it is not a good idea to attempt to install the OS onto the same flash drive you are running the installer from.  It might be possible, but I don't know anyone, anywhere, who has tried it and been successful.  I think it is a really bad idea.  

You can run from the Ubuntu Installer Live-Distro for every if you don't want to save anything.  Just be certain that you refresh it every month or so from using a fresh downloaded version to have the latest programs and security patches.  Most people find it is better and faster to install onto a hard disk or SSD.

So ... which OS is on your PC today?

---

### Post by oldos2er on 2017-09-17
> **rhondas said:**
> do I instal both the installer  and the linux lite on the flash drive?

Please provide the information you were asked for.

---

### Post by kurt18947 on 2017-09-20
> There is also the possibility that the flash drive and computer aren't  compatible for this sort of operation.  Just last week, I ran into a  cheap flash drive from a user at our LUG which wouldn't let my laptop  create a bootable install, but did let someone with another laptop do  it.  I've seen this with all sorts of flash drives. Usually they work  fine for storing data, but booting is a different issue completely.

I've found this as well, usually with 'brand name' drives. The SanDisk drives I've used seem okay but I've had the best luck with Micro Center branded USB3 devices. Plain vanilla, the USB3 drives seem a little faster (subjective on my part) even in USB2 ports. YMMV of course.

---

### Post by mastablasta on 2017-09-21
sometimes it helps if you redo the partition table on the drive. 

received one on a presentation. only showed data. then i removed the partition table and created a new one. then it all worked as it should. 
of course not something a beginner would like to fiddle with.

---

