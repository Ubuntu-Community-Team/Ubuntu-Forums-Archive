---
title: "How Fullscreen Is Fullscreen Supposed To Be?"
date: 2010-05-27
forum: Virtualisation
---

### Post by derekeverett on 2010-05-27
Hi Everyone.

I am running Windows 7(dual boot with Ubuntu 10.04 already) and trying to get Xubuntu 10.04 running in Virtualbox.

Everything installed nicely and is working fine, except my fullscreen isn't really FULLscreen. 

After installing the guest additions the Xubuntu screen did get bigger... but not fullscreen.

Two things that concern me. 
1) I am using a 24" hp widescreen monitor. Does virtualbox not work properly with widescreen perhaps?
2) The instructions for Virtualbox regarding installing guest additions walk you through some steps to "compile the guest additions kernel modules." I tried and it doesn't work, I get an unable to proceed-type error message. Any thoughts here?

However, I should note that I have watched a lot of youtube videos on adding guest additions now and they don't ever seem to do that step. Like I said, I appear to have guest additions installed... and the screen did get bigger, just not the whole-screen.

---

### Post by opacatica on 2010-05-27
Not sure how much of help that might be but...  I had similar problem with a fresh install of WinXP guest on Ubuntu 10.04 host.  I tried re-installing guest additions reboot etc.  Finnally I found out that "right-Ctrl + L" (seamless) followed by "right-Ctrl + F" (fullscreen) sometimes fixes the problem.  Probably because the seamless forces adjusting to host's resolution.

Anyway this not only did fix my problem, but VBox somehow seems to have remembered the correct resolution so I never had the problem afterwards.  Not really scientific but worth giving a try.

---

### Post by derekeverett on 2010-05-27
> **opacatica said:**
> Not sure how much of help that might be but...  I had similar problem with a fresh install of WinXP guest on Ubuntu 10.04 host.  I tried re-installing guest additions reboot etc.  Finnally I found out that "right-Ctrl + L" (seamless) followed by "right-Ctrl + F" (fullscreen) sometimes fixes the problem.  Probably because the seamless forces adjusting to host's resolution.

Anyway this not only did fix my problem, but VBox somehow seems to have remembered the correct resolution so I never had the problem afterwards.  Not really scientific but worth giving a try.

Thanks for the tip man, it was worth a shot. But it didn't work for me. I'm still stuck.

---

### Post by Simian Man on 2010-05-27
> **derekeverett said:**
> 
2) The instructions for Virtualbox regarding installing guest additions walk you through some steps to "compile the guest additions kernel modules." I tried and it doesn't work, I get an unable to proceed-type error message. Any thoughts here?


That's your problem.  You can't do fullscreen or seamless mode (or a few other things) without the guest additions installed.  What is the actual error you got?

---

### Post by derekeverett on 2010-05-27
> **Simian Man said:**
> That's your problem.  You can't do fullscreen or seamless mode (or a few other things) without the guest additions installed.  What is the actual error you got?

Here's a shot of the instructions, my error and the log file.

Everything in the instructions went fine up until the part I circled.

---

### Post by Simian Man on 2010-05-27
> **derekeverett said:**
> Here's a shot of the instructions, my error and the log file.

Everything in the instructions went fine up until the part I circled.

It looks like you need to install the header files for your kernel in order to build the kernel module.  In Fedora this is in a package called "kernel-devel".  I don't know what it's called in Ubuntu, but someone can surely answer that.

---

### Post by Perryg on 2010-05-27
You may need to make sure that you have the headers and that they match you kernel, but you also need to install the GAs as sudo.

---

### Post by derekeverett on 2010-05-28
> **Perryg said:**
> You may need to make sure that you have the headers and that they match you kernel, but you also need to install the GAs as sudo.

I did try to install them as sudo and got the exact same message.

Anybody know how to get the headers? Or where to point me anyways..I'm not even real sure what that means.

---

### Post by derekeverett on 2010-05-28
> **Ricechen said:**
> I found this link, that should help you out.

Awesome... except where's the link? :)

---

### Post by derekeverett on 2010-05-29
I guess this is a bump.

But for the record, I have now tried xubuntu 10.04, Ubuntu 10.04 and Ubuntu 9.10. This problem is identical in all 3 cases.

Anybody have a solution or idea?

---

### Post by Perryg on 2010-05-29
I don't use the OSE version from the Repo. I use the PUEL version from VirtualBox becuase of the USB support and vRdp, but the steps should be the same.  Steps are:

```
sudo -i <enter> password <enter>
apt-get install dkms <enter>
apt-get install linux-headers-generic <enter>
apt-get install build-essential <enter>
```
Then install the guest additions again and reboot.  After this you need to make sure that auto resize is enabled by using the (host+g) toggle to enable resize or look at the Machine tab at the top left of the window.  Then use the mouse click & drag to resize the guest window or the (host+f) toggle to go in and out of full screen.

---

### Post by derekeverett on 2010-05-29
> **Perryg said:**
> I don't use the OSE version from the Repo. I use the PUEL version from VirtualBox becuase of the USB support and vRdp, but the steps should be the same.  Steps are:

```
sudo -i <enter> password <enter>
apt-get install dkms <enter>
apt-get install linux-headers-generic <enter>
apt-get install build-essential <enter>
```
Then install the guest additions again and reboot.  After this you need to make sure that auto resize is enabled by using the (host+g) toggle to enable resize or look at the Machine tab at the top left of the window.  Then use the mouse click & drag to resize the guest window or the (host+f) toggle to go in and out of full screen.

Thank You! I wasn't able to get this to work in Xubuntu 10.04, same old problem there.. but it works perfectly with Ubuntu 9.10 and 10.04.

So thanks again and I'll mark as solved.

---

### Post by Perryg on 2010-05-30
Before you give up do you want to try one more thing?

For some reason I just could not get this out of my head and decided to install a new copy of xubuntu and remembered what the problem was that I needed to fix on my previous install.  Check the kernel version (uname -r) and it will be an older version then the headers.  They must be in sync so be sure to do an update and then (here is the kicker) you need to run update-grub in the terminal.  For some reason this does not get run when you update the kernel image like it does in regular Ubuntu.  Go figure!

Anyway after running update-grub the GAs installed without a hitch.

---

