---
title: "virt-install, configuring a text console"
date: 2010-11-23
forum: Server Platforms
---

### Post by sean1980 on 2010-11-23
Hey everyone,

Got something that's been kicking my butt for a few days now.  Quick rundown of what I'm trying to do:

I'm using Ubuntu 10.10 Server Edition for my host domain.  I'm using QEMU/KVM to provision VM(s).  I have not (and am trying to avoid at all costs) installed X windows.  I can provision a machine just fine, using the virt-install script.  The domain will start up, it says that I'm connected, verified through virsh.  However...whenever I try to console into the guest domain with virsh (even with sudo), I get nowhere.  It says I'm connected, but there is no prompt to enter commands.  

From my understanding of the virt-install manual, under the "--nographics" section, I need to "have a text console configured on the first serial port in the guest (this can be done via the --extra-args option)."  I looked at the "extra-args" option and it doesn't give a whole lot of guidance.

Any help will be greatly appreciated.

---

### Post by jake0391 on 2010-12-14
I have been fighting the same things with RHEL5 for about 3-4 days with issues. This line seemed to help:

--extra-args="text console=tty0 console=ttyS0,115200"

What I was having issues was that I was specifying and ISO image that I put local on the server. I mounted the ISO image then copied the files over locally. I then used the --location to point to the files instead of the --cdrom option to point to the ISO image. 

The issue that I am having now is that the text install is not reading the input correctly. I then tried to point to a Kickstart file put it did not seem to like the local location of the kickstart file. I have should be able to do it via our kickstart server, but have not figured out how to use the bridged network connection yet.  

Any feedback would be appreciated. 

-Tim

---

### Post by jake0391 on 2010-12-14
I finally got mine to work. This is what I ended up with:

virt-install    \
        --name timtest  \
        --hvm   \
        --ram 1024      \
        --file /u01/timtest.img        \
        --file-size 10  \
        --nographics    \
        --network bridge:br0 \
        --location=/u01/KS/RHEL5ISO    \
         --extra-args="ks=[http://kickstartserver/timtest.cfg](http://kickstartserver/timtest.cfg) text console=tty0 utf8 console=ttyS0,115200"

What worked best "text console=tty0 utf8  console=ttyS0,115200" The utf8 gives the color so you can see what you  are doing. I even added the the bridge network and was able to use the  kickstart server. I did find out that putting this in  the kickstart file helps you come up with the console correct after the  reboot:

bootloader --location=mbr --append="console=tty0 console=ttyS0,9600"

My issues turned out to be trying to use the ISO image that I was using. I loaded it locally and things started to work. I may try going straight to the kickstart server tomorrow. SHould work, I hope.

---

