---
title: "How to install Windows 7 inside Ubuntu"
date: 2012-03-02
forum: Virtualisation
---

### Post by wuasaby on 2012-03-02
Hello, thanks to everyone who helps in this forum, I always find the right fix to my problems here.

I have Ubuntu 64bit 11.10 and I need to install Windows 7 inside. I want to keep ubuntu as my main operative system but need windows to run some softwares like iTunes.

I downloaded Oracle VM Virtualbox...

Thanks in advance :)

---

### Post by mikewhatever on 2012-03-02
Well, create a virtual computer and boot from the W7 ISO. Do not hesitate to ask if you have a specific problem.

---

### Post by kurt18947 on 2012-03-02
What Mike said.  It was surprisingly easy to install VirtualBox on 11.10.  The only thing that was mildly tricky was enabling USB ports on Win7.  I don't recall the details but it was something about adding users to a certain group in 11.10.  Other than that it was pretty straightforward and even with 11.10 AND Win7 running I was using less than 1 Gb. of RAM.  One thing to check is to make sure visualization is enabled on your machine's BIOS.  Some machines have a means to enable or disable.

---

### Post by enjoijesus94 on 2012-03-02
> **kurt18947 said:**
> What Mike said.  It was surprisingly easy to install VirtualBox on 11.10.  The only thing that was mildly tricky was enabling USB ports on Win7.  I don't recall the details but it was something about adding users to a certain group in 11.10.  Other than that it was pretty straightforward and even with 11.10 AND Win7 running I was using less than 1 Gb. of RAM.  One thing to check is to make sure visualization is enabled on your machine's BIOS.  Some machines have a means to enable or disable.

Adding USB to virtual machines goes like this.

go to 
System > Administration > Users And Groups.

Then

Go To Manage Users

scroll down till you see 

Vbox_users or anything to do with vbox.

click Properties.

Now Check The Box In The Bottom To enable USB support inside virtualBox.:popcorn:

---

### Post by nikonian on 2012-03-02
You need to add your username to a group called "vboxusers" to enable USB. I don't recall how, on Ubuntu, as I now use Fedora 16.

---

### Post by kurt18947 on 2012-03-03
> **enjoijesus94 said:**
> Adding USB to virtual machines goes like this.

go to 
System > Administration > Users And Groups.

Then

Go To Manage Users

scroll down till you see 

Vbox_users or anything to do with vbox.

click Properties.

Now Check The Box In The Bottom To enable USB support inside virtualBox.:popcorn:

But the newer Ubuntu distros have "users" not "users and groups".  There's no way to join groups graphically as installed AFAIK, it must be done at the command line.  There is, however, a fix.  Install 'gnome-system-tools' from the repositories then look in applications.  The old style Users & Groups should be there.

---

### Post by bogan on 2012-03-03
Originally Posted by** kurt18947:** > But the newer Ubuntu distros have "users" not "users and groups".   There's no way to join groups graphically as installed AFAIK, it must be  done at the command line.  There is, however, a fix.  Install  'gnome-system-tools' from the repositories then look in applications.   The old style Users & Groups should be there.In my 11.10 installation 'Users and Groups' is shown in Dash, whether logged -in to Ubuntu or Gnome Classic.

Whilst with ClassicMenu Indicator, or when logged in to Gnome Classic, it shows in the Applications>Other menu.

It runs in a Window titled 'User Settings' and the option is 'Manage Groups' in both cases.

Chao!,** bogan**.

---

### Post by wuasaby on 2012-03-07
Ok, I have this problem:

[IMG]http://oi42.tinypic.com/4uj9fc.jpg[/IMG]

I downloaded DKMS but I still get the same error message.

---

### Post by TommyIreland on 2012-11-13
I had the same problem.  After much searching, I found that this fixed it.  

Run terminal and enter the following two commands

sudo apt-get install dkms build-essential linux-headers-generic

sudo /etc/init.d/vboxdrv setup

---

### Post by Bucky Ball on 2012-11-13
[I]Thread moved to [B]Virtualisation


@ wuasaby: [/B]Welcome to the forums. Please spare a thought for those with slow connections and remove the full-sized screenshot from the body of your post and attach a thumbnail. From the Code of Conduct:
[/I]> **Images:** Be prudent in your use of images; they may help to  explain something more clearly or indicate a problem you are  experiencing better but you have to remember that not everyone has the  same bandwidth. If an image is the best way of handling the information,  please use thumbnails or keep your image to a small size and less than  100kb.Cheers. ;)

---

