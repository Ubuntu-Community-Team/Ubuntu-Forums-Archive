---
title: "cannot find headers - vmware-server"
date: 2010-04-07
forum: Server Platforms
---

### Post by z0rt3p on 2010-04-07
Hi Guys,

Newb here.. I am trying to install vmware-server 2. I have followed the steps on; [https://help.ubuntu.com/community/VMware/Server/AMD64](https://help.ubuntu.com/community/VMware/Server/AMD64)

The problem I am facing is with installing the linux-headers. Here is the output of what happens.

```


$ sudo apt-get install build-essential linux-headers-`uname -r` xinetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package linux-headers-2.6.24-23-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-23-server has no installation candidate


```

I am running ubuntu 8.04 AMD 64.

Here is my `uname -r`

```


2.6.24-23-server


```

Please help!

---

### Post by deracled on 2010-04-08
You can try installing **"linux-headers-server"** package that should resolve to the currently used kernel and as a bonus you will automatically get the new headers with a new kernel installation.

Doros

---

### Post by HermanAB on 2010-04-08
When all else fails, install the kernel source, compile and install the kernel, then reboot.  After that, the whole software development environment is guaranteed to be correct and VMware will install.

Since I am forever tinkering, I always compile the kernel and then I have no problems from then on after.

---

### Post by z0rt3p on 2010-04-08
> **HermanAB said:**
> When all else fails, install the kernel source, compile and install the kernel, then reboot.  After that, the whole software development environment is guaranteed to be correct and VMware will install.

Since I am forever tinkering, I always compile the kernel and then I have no problems from then on after.

Thanks.. I ended up upgrading to 2.6.24-24-server and everything worked perfectly after that.

Can anyone explain why ```
sudo apt-get install build-essential linux-headers-`uname -r` xinetd
``` wasnt working out of the box? This was a fresh install...

Thanks again guys!

---

### Post by apitsos on 2010-07-03
Hello everyone!

I am sorry my stupid question, but I am pretty newbie on Ubuntu Server systems and I am facing EXACTLY the same problem, as I am trying to install **VMware Server 2** on **Ubuntu Server 8.04 LTS (hardy) 64-bit**.

Could you please let me know how to compile and install step-by-step the kernal, as HermanAB advised?

Again, excuse me for the "stupid" question, but I tried to find a way to do it. I used the directions from the page [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile), but with no luck... :-(

Looking forward for your kind help!

Thanks a lot in advance.

---

### Post by z0rt3p on 2010-07-03
I cant remember what I did to save my life... but my terminal does :)

Try this...

```
sudo apt-get install linux-image-2.6.24-24-server
```

---

### Post by apitsos on 2010-07-03
Hello z0rt3p!

Thank you very much for your reply. This installed the headers as expected. It is created a new directory: ```
/lib/modules/2.6.24-24-server
```

After that, I gave the path "/lib/modules/2.6.24-24-server" to the installation wizard of VMware Server 2, where it says:
```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /lib/modules/2.6.24-24-server
```

But it returns again:
```
The path "/lib/modules/2.6.24-24-server" is an existing directory, but it does
not contain a "linux" subdirectory as expected.
```

Any ideas?

Thanks a lot again for your time!

Best regards,
Angelos Pitsos

---

### Post by z0rt3p on 2010-07-03
Do this... then reboot and start the vmware installer again.

[CODE]sudo apt-get install linux-headers-2.6.24-24-server[CODE]

---

### Post by apitsos on 2010-07-03
I am doing this right now. What to give on that step as path, if the wizard ask me again?

---

### Post by z0rt3p on 2010-07-03
run ```
uname -r
``` and post your output.

---

### Post by apitsos on 2010-07-03
Hey!

That worked like a charm! Thank you so much for your kind help! hopefully not to have any problem after that...

You are brilliant!


Best regards,
Angelos Pitsos

---

### Post by z0rt3p on 2010-07-03
Awesome!

Enjoy the vmware server - ubuntu server duo... Its a great setup once its running.

---

### Post by apitsos on 2010-07-03
Great! I know it. I was working with this for more than 4 months, but an unexpected power shut down on my computer room made my system completely crashed. 

From this, unfortunately I lost my virtual machines and the system, too, as it never started properly again. I tried to fix it or even to backup the virtual machines, but unfortunately I couldn't, so I had to format the hard drive and install everything from the beginning.

I remember that I spent 3 days to make this system up and running, as I am following instructions and posts, because I am not a unix user! I hope you understand how difficult was for me to setup this.

Hopefully I am a systems administrator (Windows of course) and I belong to the "IT family", so that makes me keep trying (always)!

Anyway, I would like to thank you once again. Your instructions were just what I was needing!

I wish you all the best.

Angelos Pitsos

---

