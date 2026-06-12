---
title: "UEC Setup Problems"
date: 2011-01-20
forum: Ubuntu Cloud and Juju
---

### Post by ashishrevar on 2011-01-20
Hello there,
I am working with two machines to implement cloud using UEC 10.10.
I've installed the UBUNTU server and CC,CLC,SC,Walrus on one machine and on another machine I've installed NC.
But at the time of installation I've avoided to add proxy settings. At this moment I am not able to perform UEC image operations because I can't access the outside world.

**How to setup the proxy settings now?**

I need to run an PHP application on this cloud, so am I going on a right path or not?
Is there any extra package do I need to install or configure for the same PHP purpose?

Please reply me fast as I am working on the deadline to submit my project in institute.

Ashish
[EMAIL="ashishrevar@gmail.com"]ashishrevar@gmail.com[/EMAIL]

---

### Post by ashishrevar on 2011-01-20
I want to know that is it possible to get an GUI based screen for this UEC setup .
I am getting totally command line console which is not suitable for work.

I read the blog of Dustin Kirkland who is a Core Developer of the [Ubuntu Server]("https://launchpad.net/%7Ekirkland") for [Canonical]("http://www.canonical.com/"), whose post shows that we can get GUI for the same.

[http://blog.dustinkirkland.com/2010/06/cloud-in-your-pocket-uec-liveiso.html](http://blog.dustinkirkland.com/2010/06/cloud-in-your-pocket-uec-liveiso.html)

[URL="http://blog.dustinkirkland.com/2010/06/cloud-in-your-pocket-uec-liveiso.html"]
[/URL]

---

### Post by kim0 on 2011-01-20
Regarding network connectivity, can you please try executing the 2 following commands on the CLC/CC node

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

I am assuming eth0, is the "outer" interface connecting to the internet. if it's not, change the name to the appropriate one. No need for gui on the NC nodes (really). You can try a tool like elastic-fox to manage your cloud. But I prefer you get it working with command line tools first

---

### Post by ashishrevar on 2011-01-20
The first command is working but the second one is producing error.
It shows

**-bash: /proc/net/ipv4/ip_forward: No such file or directory.**

After checking of directory structure, I found out that there is no such directory ipv4.
All the directories are related to ipv6, waht to do?

Where can I enter my proxy address (my institute's [https://10.1.19.27:4100)?](https://10.1.19.27:4100)?)

---

### Post by ashishrevar on 2011-01-21
Can you please describe these two commands?
How they will solve the networking problem?

If I run the command
**euca-describe-availability-zones verbose**

it shows the default configuration for the two machines, but free/max column remains the zero.
Is it showing such zeroes because there is some network error or what?

---

### Post by kim0 on 2011-01-21
If both free/max are zeros, that means the node controllers have not registered correctly. Thus the cloud cannot run any VMs. Can you try following those installation instructions closely

[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

For accessing the internet, try this
sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'

It's /proc/sys, don't drop the sys

---

### Post by ashishrevar on 2011-01-22
Thanks for your support.
Now these two command are working, but still facing the same problem.
I am not able to load images(Can't access outside world) as well as now my server shows all zeros in the field of free/max when I discover the nodes with verbose option.

Any solution for this?

---

### Post by kim0 on 2011-01-22
hmm not sure, I suggest posting full details (machines, network, IPs...) to the ubuntu-cloud mailing list

[https://lists.ubuntu.com/mailman/listinfo/Ubuntu-cloud](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-cloud)

---

### Post by ashishrevar on 2011-01-25
Hello there, I've configured UEC in single system, using the post from 
[http://kiranmurari.wordpress.com/2010/03/19/uec-cc-nc-single-machine/](http://kiranmurari.wordpress.com/2010/03/19/uec-cc-nc-single-machine/)

Everything works fine, I've uploaded two images which is visible through euca-describe-images.

But to run them I need to create keypairs, this is where I got the problem. 

if [ ! -e ~/.euca/mykey.priv ]; then
    touch ~/.euca/mykey.priv
    chmod 0600 ~/.euca/mykey.priv
    euca-add-keypair mykey > ~/.euca/mykey.priv
fi

this command is executed successfully but I am not able to find my keypairs to run instances.
How to set keypairs?

---

### Post by kim0 on 2011-01-26
Just use "euca-run-instance -k mykey ...."

mykey is now on the server, it will insert the public key for you inside the image

---

### Post by ashishrevar on 2011-01-26
Hi Kim,

I've used the same commands which does not return any error, but if do like below....
euca-describe-keypairs

then returns empty. If I do with euca-run-instances -k mykey  then error shows that there is no mykey.

What to do?

---

### Post by kim0 on 2011-02-02
Hi,

I think you need to do the following

if [ ! -e ~/.euca/mykey.priv ]; then
    mkdir -p -m 700 ~/.euca
    touch ~/.euca/mykey.priv
    chmod 0600 ~/.euca/mykey.priv
    euca-add-keypair mykey > ~/.euca/mykey.priv
fi


For more info, read step-7 on [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

---

### Post by raymdt on 2011-02-04
Hey,
this is a funny story :lolflag:.
your key( mykey.priv ) should be stored  in the  "/home/<youruser>/.euca" directory.
Change into that directory and post the result of 
```

cat  mykey.priv

```
Here

I guess that, the command **euca-add-keypair mykey > ~/.euca/mykey.priv **was not successful ( even if you didn't get some error  message)

the file  mykey.priv file should contain something like

```

  ---- BEGIN SSH2 PUBLIC KEY ----.
   AAAAB3NzaC1kc3MAAACBAPY8ZOHY2yFSJA6XYC9HRwNHxaehvx5wOJ0rzZdzoSOXxbET
   W6ToHv8D1UJ/z+zHo9Fiko5XybZnDIaBDHtblQ+Yp7StxyltHnXF1YLfKD1G4T6JYrdH
   YI14Om1eg9e4NnCRleaqoZPF3UGfZia6bXrGTQf3gJq2e7Yisk/gF+1VAAAAFQDb8D5c
   vwHWTZDPfX0D2s9Rd7NBvQAAAIEAlN92+Bb7D4KLYk3IwRbXblwXdkPggA4pfdtW9vGf
   J0/RHd+NjB4eo1D+0dix6tXwYGN7PKS5R/FXPNwxHPapcj9uL1Jn2AWQ2dsknf+i/FAA
   vioUPkmdMc0zuWoSOEsSNhVDtX3WdvVcGcBq9cetzrtOKWOocJmJ80qadxTRHtUAAACB
   AN7CY+KKv1gHpRzFwdQm7HK9bb1LAo2KwaoXnadFgeptNBQeSXG1vO+JsvphVMBJc9HS
   n24VYtYtsMu74qXviYjziVucWKjjKEb11juqnF0GDlB3VVmxHLmxnAz643WK42Z7dLM5
   sY29ouezv4Xz2PuMch5VGPP+CDqzCM4loWgV
   ---- END SSH2 PUBLIC KEY ----


```

---

### Post by ashishrevar on 2011-02-16
Hello there,

I am dealing with an unexpected error in my web console. 
[https://10.1.3.34:8443/](https://10.1.3.34:8443/) is the address of my laptop in which I've installed the cloud, but I am not able to open my web console. It prompts the error like below.

[B]Security Error

Invalid Server Certificate
A request failed because the server's certificate was invalid.
[/B]

What's the problem here?

---

### Post by ashishrevar on 2011-02-17
Hello there,
I am facing another problem in my implementation.
After the installation, when I shutdown my laptop and then I start it again, but I am getting error of EC2 Access key.

I executed command, euca-describe-availability-zone verbose...
but it prompts the error,
EC2_ACCESS_KEY muse set....
what's wrong with it?

---

### Post by kim0 on 2011-02-17
Did you forget to source ~/.euca/eucarc ? You need to source this in every new shell you want to use to control your cloud

---

### Post by ashishrevar on 2011-02-17
Hi Kim0,
I am following those steps, but not working.
I have sourced that thing....~/.euca/eucarc

But not working at all.
what's d problem?

---

### Post by raymdt on 2011-02-18
How did you souce ~/.euca/eucarc ??

Please check the ~/.euca directory and the ~/.euca/eucarc file exist.

Try this to source the eucarc file.
```

$ .  ~/.euca/eucarc

```

Don't forget the " . "

---

### Post by ashishrevar on 2011-02-27
Thanks raymdt, it works.

But at this point I am not able to get Images from the internet.

My web console is showing several images which I am not able to download, as well as I am not able to get Extras menu.
The error is shown like below.

Eucalyptus-certified Images
Failed to load the list of images (visit the repository)
Eucalyptus-compatible Tools
Failed to load the list of images (visit the repository)

Does it mean any kind of network problem?
If I do,
$ sudo euca_conf --no-rsync --discover-nodes

then it list out several errors,
ssh: could not resolve hostname fe80: Name or service not known
lost connection
failed.

If I try to do,
$ sudo apt-get update

then it prompts error,
connection failed.
several other tons of error code...

What's wrong with this?

---

### Post by kim0 on 2011-03-01
hostname fe80, strikes me as something related to ip6, which I don't know what it's trying to do! If you get stuck, reinstall and try the mailing list

---

