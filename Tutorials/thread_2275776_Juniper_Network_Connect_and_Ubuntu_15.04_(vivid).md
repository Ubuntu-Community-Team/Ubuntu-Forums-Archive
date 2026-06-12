---
title: "Juniper Network Connect and Ubuntu 15.04 (vivid)"
date: 2015-04-28
forum: Tutorials
---

### Post by onemorepash on 2015-04-28
Hi folks,

I've just upgraded to Kubuntu 15.04 64 bit and gotten through some nightmare of making Juniper Network Connect work. So let me post this short HOWTO in the hope that it will save someone a couple of nights. Long time passed since [madscientist's HOWTO]("http://ubuntuforums.org/showthread.php?t=232607&page=55") was posted  and many things have changed.

Actually I'd already had NC working on my Kubuntu 14.10 before I upgraded to 15.04, and among lots of other things broken, Juniper NC has also stopped to work. Let's assume we have a fresh install of Ubuntu 15.04 (I personaly use Kubuntu, but I don't believe there is much difference for Ubuntu/Kubuntu/Lubuntu/etc). Most of the recommendations will also work for 14.10 and some older versions (14.04, I believe, as well).

Couple of notes on how it all works. NC has several components: java-based installer that delivers NC to your PC and runs installation bash script, java applet that provides user interface, and a program called **ncsvs**, which is the VPN client itself and has nothing to do with java. In principle it can work in CLI with no java at all though it has a bit stupid logic and requires to enter password in the CLI. There are several alternative UI wrappers for **ncsvc** provided by the community. This **ncsvc** relies on kernel **tun** driver, that provides universal tunnel network interface machinery used to route your packets.

Earlier versions of Sun/Oracle 64 bit java didn't support applets. Because of this Juniper IVE 7.2 and lower could not work under 64-bit linux, so if your company runs outdated Juniper products like SA2000/4000/6000, this HOWTO is not for you, as these products are EoL and don't support IVE 7.3 and later, sorry. However, I believe, you can try Mad Scientist's java-free interface: [http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html) or one of the other **ncsvc** wrappers provided by the community.

OK. First read this Juniper KB article: [http://kb.juniper.net/InfoCenter/index?page=content&id=KB25230](http://kb.juniper.net/InfoCenter/index?page=content&id=KB25230)

Yes, you need two versions of java. In principle OpenJDK should also work but I haven't tested. If you want to try&#8212;see instructions in the Juniper KB. Let me know, if you manage to make it work.

My way is to remove OpenJDK, add the webupd8team's PPA and install 64-bit java8 as a packet.

```
sudo apt-get purge openjdk*
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer 

```

I also tried oracle-java9-installer, but it looks like Juniper NC doesn't work with it.

Than you go to java.com and download a tar.gz 32-bit bundle for Java Linux (32-bit version is named simply &#8220;Linux&#8221; on the download page). Here is how it should look like:
```
$ ls 
jre-8u45-linux-i586.tar.gz

$ tar xfs ./jre-8u45-linux-i586.tar.gz  

$ ls -lh
total 63M
-rw-rw-r-- 1 pash pash  63M Apr 28 16:02 jre-8u45-linux-i586.tar.gz
drwxr-xr-x 6 pash pash 4.0K Apr 10 20:53 jre1.8.0_45
```

Manually install it (you might want a better location but this is how I like it):
```
sudo mv ./jre1.8.0_45 /usr/lib32/
sudo chown root.root /usr/lib32/jre1.8.0_45/ -R
sudo ln -s /usr/lib32/jre1.8.0_45 /usr/lib32/java

```

Now you have two versions of java, but you need to tell the system about both and how to chose which one to use. A mechanism called **update-alternatives** is used to mantain different programs with same names.

```
$ sudo update-alternatives --install /usr/bin/java java /usr/lib32/java/bin/java 10
update-alternatives: using /usr/lib32/java/bin/java to provide /usr/bin/java (java) in auto mode

$ update-alternatives --display java 
java - auto mode
  link currently points to /usr/lib32/java/bin/java
/usr/lib/jvm/java-8-oracle/jre/bin/java - priority 1
  slave java.1.gz: /usr/lib/jvm/java-8-oracle/man/man1/java.1.gz
/usr/lib32/java/bin/java - priority 10
Current 'best' version is '/usr/lib32/java/bin/java'.

$ sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                     Priority   Status
------------------------------------------------------------
* 0            /usr/lib32/java/bin/java                  10        auto mode
  1            /usr/lib/jvm/java-8-oracle/jre/bin/java   1         manual mode
  2            /usr/lib32/java/bin/java                  10        manual mode

Press enter to keep the current choice
[*], or type selection number: 1
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/java to provide /usr/bin/java (java) in manual mode

$ update-alternatives --display java 
java - manual mode
  link currently points to /usr/lib/jvm/java-8-oracle/jre/bin/java
/usr/lib/jvm/java-8-oracle/jre/bin/java - priority 1
  slave java.1.gz: /usr/lib/jvm/java-8-oracle/man/man1/java.1.gz
/usr/lib32/java/bin/java - priority 10
Current 'best' version is '/usr/lib32/java/bin/java'.

```

This output means that you told **update-alternative** that 32-bit java is present but asked to use 64-bit version by default. When Juniper NC needs 32-bit version it will check the list and find the path.

Now you follow the Juniper's KB25230 and install the required 32-bit libs:

```

$ sudo dpkg --add-architecture i386
$ sudo apt-get update

$ sudo apt-get install libstdc++6:i386 lib32z1 lib32ncurses5 lib32bz2-1.0 libxext6:i386 libxrender1:i386 libxtst6:i386 libxi6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lib32bz2-1.0
E: Couldn't find any package by regex 'lib32bz2-1.0'

```

I believe **lib32bz2-1.0** was present in 14.10 but is missing in 15.04 for some reason. No problem, first skip it:

```
sudo apt-get install libstdc++6:i386 lib32z1 lib32ncurses5 libxext6:i386 libxrender1:i386 libxtst6:i386 libxi6:i386
```

I didn't check myself whether NC will work without lib32bz2-1.0 installed, as I simply got it from here: [https://launchpad.net/ubuntu/vivid/amd64/lib32bz2-1.0/1.0.6-5ubuntu5](https://launchpad.net/ubuntu/vivid/amd64/lib32bz2-1.0/1.0.6-5ubuntu5)

```
$ wget http://launchpadlibrarian.net/187844602/lib32bz2-1.0_1.0.6-5ubuntu5_amd64.deb
$ sudo dpkg -i ./lib32bz2-1.0_1.0.6-5ubuntu5_amd64.deb 
```

Very important thing here. As **ncsvc** needs root priviligies to work, when Network Connect installs into **~/.juniper_networks** folder, it sets **root:root** ownership and SUID bit for **nvsvc**. So you need to provide sudo password to the install script and, despite it's nowhere explicitly stated by Juniper, you need to install **xterm** first, because the install script is hardly coded to use **xterm** to ask you the password. Ubuntu comes without **xterm** installed by default, and several years ago I spent a lot of time to sort this out, as the NC install script just doesn't care and silently goes on if it can't run **xterm**.

So don't forget to run:
```
sudo apt-get install xterm
```

If you have already tried to run Netwrok Connet before (probably unsuccessfully, as you are reading this guide), first delete the current installation from your home folder:
```
mv ~/.juniper_networks ~/.juniper_networks-back
```

Now run firefox, log in to the Juniper SSL VPN portal and try to run NC. When you first run it, firefox will block java applet and ask whether you want to allow it. Yes, you do. Firefox has not really obviuos interface for such an alert (just below the address line) and I missed the question a couple of times.

First time you might see a java-based alert window asking about 32-libs and whether you are sure you've installed them, just press OK.

If your home folder is not encrypted, you're almost done. Othervise you need to perform some additional trics. As encrypted filesystem doesn't allow to run programs with SUID bit on, you want to move NC folder out of your home directory and create a symbolic link:
```
sudo mv ~/.juniper_networks /opt/.juniper_networks
ln -s /opt/.juniper_networks/ ~/.juniper_networks

```

You are almost done.

Try to run NC again. If NC applet starts and silently closes, it means it can't run **ncsvc** and most probably there is a problem with permissions. I could not figure out why it happened for me but I just tried to run **sudo firefox** (or maybe even **su -** and than **firefox**) and run NC with root permissions. After that NC started to work.

Now you're almost almost done. But not quite.

There is a bug in the default Ubuntu 15.04 kernel (3.19.0-15), that breaks **tun** driver. If your NC statrs but you can't send any traffic and byte counters are stuck, it's probably your case. Check out the ncsvc log.

```
$ cat ./.juniper_networks/network_connect/ncsvc.log | grep too
20150428003736.352448 ncsvc[p3118.t3118] adapter.warn IP Packet too small 0 (adapter.cpp:141)
20150428010024.767780 ncsvc[p4265.t4265] adapter.warn IP Packet too small 0 (adapter.cpp:141)

```

This mesages indicates you run into [**Bug 90901**]("https://bugzilla.kernel.org/show_bug.cgi?id=90901"). Here is some description: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1448942](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1448942)

If you're reading this HOWTO while the new kernel for 15.04 is not out, you possibly would like to download the kernel provided by [Joseph Salisbury (jsalisbury)]("https://launchpad.net/%7Ejsalisbury") in the bug discussion. Go here: [http://kernel.ubuntu.com/~jsalisbury/lp1448942/](http://kernel.ubuntu.com/~jsalisbury/lp1448942/) Download all the packagess and install them with **dpkg -i**. When you reboot, you need to press and hold** shift** key while **grub** is loading in order to get into the boot menu (sometimes more than one attempt is required). Select 3.19.0-14 kernel and boot.

If time is already passed and 15.04 is matured a bit, than a simple upgrade of the kernel should help:

```
sudo apt-get dist-upgrade
```

And reboot.

Well, by now you should have Network Connect working. You can see it is a simple, reliable and easy to use next-generation networking solution.

Comments and complains are welcome.

============
UPDATE August 10, 2015

The symilnk workaround for suid appears to not work if the symlink follows to a different folder name, e. g. ~/.juniper_networks -> /opt/juniper_networks. If it's the case for you, just use same name for the folder: ~/.juniper_networks -> /opt/.juniper_networks. By now it's working fine for me, though I can't fugure out what's the difference.

Here is a link to a forum topic, where I first discovered the idea of symlink workaround: [http://askubuntu.com/questions/210048/error-when-running-binary-with-root-setuid-under-encrypted-home-directory](http://askubuntu.com/questions/210048/error-when-running-binary-with-root-setuid-under-encrypted-home-directory)

---

### Post by gfxguy on 2015-05-06
Thanks for this how-to guide.  It ultimately worked for me, but as usual I ran into every possible problematic thing that could happen - so thanks for being so exhaustive in covering all the caveats.

I think there is one typo, where you wrote: "I also tried oracle-java8-installer, but it looks like Juniper NC don't work with it," that's the one the instructions say to install, so I think you may have meant "9?"

At the final steps, I had to install Joseph's fixes.  Dpkg would not install all of the packages, there seemed to be some weird circular dependencies with the tools and cloud tools, but it finally worked anyway.

Important to note that even newer kernels STILL do not work; I have to explicitly select the 3.19.0-14 kernel, despite there being new ones installed.

I don't like looking a gift-horse in the mouth, but there's really something wrong when things that were working break in revisions... and when someone offers a patch to fix it, it should be fixed.

But thanks again; without this I'd have to do development work in Windows, and nobody wants that.

---

### Post by mike319 on 2015-05-10
Yes, thanks for this. I was getting as far as the network connect window saying connecting but not connecting. Starting Firefox as root is what finally made it all work. I would love to find out why but at least it works. Thanks again.

---

### Post by onemorepash on 2015-06-03
My fault, actually.

My description about permissions fix was really messy.

What you need to do is to run 
```
cd /opt/juniper_networks/network_connect/
sudo chmod a+s ./ncsvc
```
after moving original ~/.juniper_networks folder to /opt/juniper_networks and creating the symlink.

I'll add a fix to the original post later.

---

### Post by onemorepash on 2015-08-10
I wrote an update on SUID issue workaround using symlink. See the bottom of the post.

---

### Post by bbj2 on 2015-10-21
Thank you for a very detailed guide. 

After doing everything correctly, NC kept saying that I was missing 32 bit JVM libs. 

I learned from this post ([http://askubuntu.com/questions/450369/how-to-install-juniper-vpn-on-ubuntu-14-04-lts](http://askubuntu.com/questions/450369/how-to-install-juniper-vpn-on-ubuntu-14-04-lts)) that NC uses update-alternatives to verify if a 32 bit JVM is installed, but it looks for update-alternatives in /usr/sbin. In recent Ubuntu versions, update-alternatives is installed in /usr/bin.

So a simple symlink fixed that issue.

```
sudo ln -s /usr/bin/update-alternatives /usr/sbin/update-alternatives
```

---

### Post by Schnellkochtopf on 2015-11-29
Thanks a lot. I tried some other approaches, all failed. It seems like console (ncsvc) connect is not possible (ncapp.error Failed to authenticate with IVE.) I used openJDK in my previous attempts, however.  Anyways, thanks a lot. I can't work from home without access to publication servers.

---

### Post by ErikT63 on 2016-01-01
Thank you very much. I followed your instructions on Ubuntu 15.10 and it worked! 

There was only one small difference along the way. Because I had installed java-8-openjdk-i386 when I was trying to get things to work, it showed up in the update alternatives step. For some reason the purge openjdk* command didn't get rid of it. So I used to the synaptic package manager to remove it. Everything else was exactly as you said. 

Thanks again!

---

### Post by Naruki_Biggleswort on 2016-01-12
I just installed a new Kubuntu 15.10 VM on my Windows 10 host using Virtual Box. Normally I find the old Mad Scientist page to figure out how to set up the VPN connection to my office, but this time I thought I would try something different. I came across your post here, followed it, and it worked perfectly! Never had that happen with the Mad Scientist guide (although maybe it did work perfectly with a particular version of everything a long time ago).

So thanks a lot. That was awesome. :KS


I do have a request (and it will probably be a noob question). Now that I can connect using the web page interface to my company's VPN, I would really like to go straight to the Network Connect application and connect from there without needing my browser.

Can you tell me how to do that?

Mad Scientist's script (msjnc) would pop up that little NetConnect app, but it had a slightly different set of options than this one has, so I guess  maybe he wrote his own GUI.

Regards,
~Naruki

---

### Post by onemorepash on 2016-03-28
Naruki, 

In theory you can run ncsvc directly from the CLI but in practice it's not really supposed to be run like this.

Try 

[FONT=courier new]~/.juniper_networks/network_connect/ncsvc --help[/FONT]

it requires to provide password in CLI and has many other clumsy features.

However you can use the madsientist's wrapper. It's a GUI-style java free program that just takes your parameters and runs ncsvc autonomously without the need to log in to the web-console.

---

