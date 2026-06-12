---
title: "Installing VMware server onto my Ubuntu Server"
date: 2009-01-01
forum: Server Platforms
---

### Post by Heeter on 2009-01-01
Hi guys,

I would to know how to install VMware server 2 onto my Ubuntu 8.10 command line server. I control it with putty.

Thanks

Heeter

---

### Post by trmentry on 2009-01-01
> **Heeter said:**
> Hi guys,

I would to know how to install VMware server 2 onto my Ubuntu 8.10 command line server. I control it with putty.

Thanks

Heeter

Pretty easy. :)

```

sudo apt-get install build-essential linux-headers-`uname -r`

```

Once that is done...extract the archive you downloaded from VMware.

```

tar zxvf VMWare-server-2*

```

then go into the 'vmware-server-distrib' directory it will create where you extracted it and run the installer.

```

sudo ./vmware-install.pl

```

You should be able to take defaults for most of the questions... for the question on the admin user make sure to change that to your user logon.

Also search the forums...there is a guide on here for it as well.

[http://ubuntuforums.org/showthread.php?t=973729](http://ubuntuforums.org/showthread.php?t=973729)

---

### Post by RealPSL on 2009-01-01
[http://howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-8.10]("http://howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-8.10")

The instructions at the URL above work fine. You will need to use a system with a GUI to download VMware Server 2.0 and get your free license as well as manage the VM instances once the installation is complete. Are you having a specific problem that you can share?

---

### Post by Heeter on 2009-01-01
Hey guys thanks for your input.

I am having a problem completing the install:

1- I cannot install the linux-headers-'uname -r'
```

E: Could not find the package linux-headers-'uname -r'

```

I forgot to mention this is Ubuntu8.10Server 64bit Server tower. I am using vmware-server-2.0.0-122956.x86_64.tar.gz

Heeter

---

### Post by Heeter on 2009-01-01
Here is another:

2- I cannot recompile the kernel about halfway through the vmware install
```

What is the location of the directory of the C header files that match your running 
kernel? [/usr/source/linux/include]

the path "/usr/source/linux/include" is not an existing directory


```

3- Why cannot I copy'n'paste into/out of putty?

BTW, all the guides I found while I searched here are for desktop installs, not server installs.

Thanks again guys


Heeter

---

### Post by joebeasley on 2009-01-02
Your error, "E: Could not find the package linux-headers-'uname -r' " is caused because you are not using the backtick `.  

Look to the left of the number 1 on the keyboard.  You should use linux-headers-`uname -r`.

---

### Post by Heeter on 2009-01-02
DOH!!!!!


Never saw that key.


Thanks for pointing that out


Heeter

---

### Post by trmentry on 2009-01-02
> **Heeter said:**
> Hey guys thanks for your input.

I am having a problem completing the install:

1- I cannot install the linux-headers-'uname -r'
```

E: Could not find the package linux-headers-'uname -r'

```

I forgot to mention this is Ubuntu8.10Server 64bit Server tower. I am using vmware-server-2.0.0-122956.x86_64.tar.gz

Heeter


it's not a '  its a `   

the ` is above my tab key with teh ~ key

---

### Post by Heeter on 2009-01-02
Update:

Now when I put in that I get:

```

E: Could not find package 2.6.27-7-server

```


Thanks

Heeter

---

### Post by RealPSL on 2009-01-03
Most likely you have a space between the "-" and the "`". To make things easier I suppose you could just run ```
sudo apt-get install linux-headers-2.6.27-7-server
```

However the original way suggested ensures that after kernel levels change the instructions will still work. The command above will get it done for what appears to be your current kernel level.

---

### Post by Heeter on 2009-01-03
Hey Guys,

Thanks for all your input,

I got it up and running!!!!!!!!!

Thanks again to all on this thread.

Heeter

---

### Post by zenmatrix on 2009-01-03
I can never do it that way either what works for me is linux-headers-$(uname -r)

---

