---
title: "What is the best virtualization software for Linux?"
date: 2007-03-11
forum: The Cafe
---

### Post by Quillz on 2007-03-11
The two that interest me most are VMWare Workstation and Parallels Workstation, both of which have editions available for Windows and Linux. Of those two, which is better? Also, which one do you think is the easiest to use, even if it sacrifices features?

---

### Post by Quillz on 2007-03-11
Also, on a somewhat related note, I can find VMWare Player in the repos, but not Workstation. Do I have to download it and install it on my own, or is there a way to get it to show up in the repos?

---

### Post by maniacmusician on 2007-03-11
The best in my opinion is VirtualBox ([http://virtualbox.org](http://virtualbox.org) ). For me, and most others, it completely outclasses VMWare Player/Server/Workstation.

As for downloading workstation, I'm pretty sure you have to pay for a license. Player and Server are free, but I don't think workstation is.

another advantage to VirtualBox besides it being faster and smoother;  it's free and Free.

---

### Post by Quillz on 2007-03-11
Hmm... I'll try VirtualBox, then.

And yes, Workstation is not free, but I thought it would still be in the repos.

---

### Post by LookTJ on 2007-03-11
Have you tried the vmware howto on here? I'll get link for you. I'll say vmware.

edit: here what I found: [http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

---

### Post by .t. on 2007-03-11
Qemu with KQemu, although harder to set up, is also a good Free alternative.

---

### Post by maniacmusician on 2007-03-11
> **.t. said:**
> Qemu with KQemu, although harder to set up, is also a good Free alternative.
Virtualbox is sort of based on those. It shares some of the code, but it implements some other techniques such as caching that greatly improve the speed of the VM

---

### Post by .t. on 2007-03-11
Yes. Indeed. And I'm very pro-VirtualBox (and, to be explicit, note that when I have virtualising to do, that's what I use, following SVN development). However, it's not in the repositories; whereas kqemu and qemu are.

Although, the V-Box code cannot be based too much from KQemu, as that was only recently open-sourced.

---

### Post by maniacmusician on 2007-03-11
> **.t. said:**
> Yes. Indeed. And I'm very pro-VirtualBox (and, to be explicit, note that when I have virtualising to do, that's what I use, following SVN development). However, it's not in the repositories; whereas kqemu and qemu are.

Although, the V-Box code cannot be based too much from KQemu, as that was only recently open-sourced.
yes, it's not too much code, but there is some.

I also understood that Virtualbox was supposed to be in the repos for Feisty. (or perhaps included by default) Even without that, it's a simple download away, but I totally understand your point.

---

### Post by Quillz on 2007-03-11
> **.t. said:**
> Yes. Indeed. And I'm very pro-VirtualBox (and, to be explicit, note that when I have virtualising to do, that's what I use, following SVN development). However, it's not in the repositories; whereas kqemu and qemu are.

Although, the V-Box code cannot be based too much from KQemu, as that was only recently open-sourced.
Will VirtualBox ever be in the repos?

---

### Post by maniacmusician on 2007-03-11
> **Quillz said:**
> Will VirtualBox ever be in the repos?
[http://virtualbox.org/wiki/News](http://virtualbox.org/wiki/News) 

Look particularly at February 12th.  I am not sure if this news  is accurate, but it should at least make it into the repos at **some** point.

---

### Post by baobab68 on 2007-03-13
I don't see it in the repos, but it has turned up in recent releases of Automatix, if that helps.

---

### Post by mips on 2007-03-13
> **Quillz said:**
> Also, on a somewhat related note, I can find VMWare Player in the repos, but not Workstation. Do I have to download it and install it on my own, or is there a way to get it to show up in the repos?

Workstation is NOT free. Player & Server are though. If you are looking at the vmware products get the Server version.

Another option is KVM if your cpu supports it.

---

### Post by afljafa on 2007-03-13
I tried KVM over the past week. It`s not really there yet (Which is unsurprising) but one to look forward to for the future. 

Have not tried VirtualBox in the nix environment but if it`s anything like the Windows version I will give it a big miss. An awful buggy mess.

My preference is for Vmware Server. A very polished and well supported package.

---

### Post by Onyros on 2007-03-13
I've had a few friends saying the exact same thing of the Virtualbox Windows client, it does suck, and is in no way to comparable to VMWare on that platform (Windows).

BUT, on Linux... it's a whole different story. It is THE best, it beats any of the VMWare products by a lot in terms of speed and functionality.

---

### Post by Quillz on 2007-03-13
> **baobab68 said:**
> I don't see it in the repos, but it has turned up in recent releases of Automatix, if that helps.
How recent are the builds that include it? I've been trying to install Automatix on Feisty Fawn Herd 5, but I don't think it's supported yet.
> **mips said:**
> Workstation is NOT free. Player & Server are though. If you are looking at the vmware products get the Server version.

Another option is KVM if your cpu supports it.
Yes, I know Workstation is not free. I use it on my Windows box. But I thought it might still be in the repos since there are non-free channels.

---

### Post by maniacmusician on 2007-03-13
> **Quillz said:**
> How recent are the builds that include it? I've been trying to install Automatix on Feisty Fawn Herd 5, but I don't think it's supported yet.

Yes, I know Workstation is not free. I use it on my Windows box. But I thought it might still be in the repos since there are non-free channels.
you can install the edgy version on Feisty for now. It compiles stuff during the installation, so it doesn't really **have** to be release-specific. Just make sure you have the kernel headers installed, and then download the edgy version from their site. I'm using it on feisty as well.

---

### Post by Quillz on 2007-03-13
> **maniacmusician said:**
> you can install the edgy version on Feisty for now. It compiles stuff during the installation, so it doesn't really **have** to be release-specific. Just make sure you have the kernel headers installed, and then download the edgy version from their site. I'm using it on feisty as well.
I am using Kubuntu and it never worked. Is it only for Ubuntu?

---

### Post by maniacmusician on 2007-03-13
> **Quillz said:**
> I am using Kubuntu and it never worked. Is it only for Ubuntu?
I'm using Kubuntu as well. What do you mean it didn't work? You have to have your kernel headers installed, of course. 

And when you downlaod and try to run it, it will complain about a couple of dependencies. (like libxalan or libxerces or something like that), so you just install those and you're good to go. 

It's working perfectl for me on Kubuntu Feisty. I have 3 VM's running simultaneously right now using VirtualBox

---

### Post by dannyboy79 on 2007-03-13
anyone tried xen yet?

---

### Post by Quillz on 2007-03-13
> **maniacmusician said:**
> I'm using Kubuntu as well. What do you mean it didn't work? You have to have your kernel headers installed, of course. 

And when you downlaod and try to run it, it will complain about a couple of dependencies. (like libxalan or libxerces or something like that), so you just install those and you're good to go. 

It's working perfectl for me on Kubuntu Feisty. I have 3 VM's running simultaneously right now using VirtualBox
I followed the instructions on the wiki, from adding the header files to sources.list to downloading the software itself. It installed, but never loaded.

---

### Post by maniacmusician on 2007-03-13
...adding the sources.list? what? 
[http://virtualbox.org/download/1.3.6/VirtualBox_1.3.6_Ubuntu_edgy_i386.deb](http://virtualbox.org/download/1.3.6/VirtualBox_1.3.6_Ubuntu_edgy_i386.deb) <---that's the file for Edgy. Download it, and install it.  

You don't have to make any modifications to sources.list....where would you get that idea?

---

### Post by Quillz on 2007-03-13
> **maniacmusician said:**
> ...adding the sources.list? what? 
[http://virtualbox.org/download/1.3.6/VirtualBox_1.3.6_Ubuntu_edgy_i386.deb](http://virtualbox.org/download/1.3.6/VirtualBox_1.3.6_Ubuntu_edgy_i386.deb) <---that's the file for Edgy. Download it, and install it.  

You don't have to make any modifications to sources.list....where would you get that idea?
I was talking about Automatix, not Virtualbox. But thanks for the .deb... I was looking for it.

---

### Post by maniacmusician on 2007-03-13
> **Quillz said:**
> I was talking about Automatix, not Virtualbox. But thanks for the .deb... I was looking for it.
Oh, you should have been a little clearer :) As I said in the other thread (the one about Automatix), there's no version for Feisty, and there probably won't be until Feisty is released. If you're using Feisty, you really shouldn't need Automatix anyways :)

---

### Post by afljafa on 2007-03-13
> **Onyros said:**
> I've had a few friends saying the exact same thing of the Virtualbox Windows client, it does suck, and is in no way to comparable to VMWare on that platform (Windows).


Good to hear.

> **Onyros said:**
> 
BUT, on Linux... it's a whole different story. It is THE best, it beats any of the VMWare products by a lot in terms of speed and functionality.

In the desktop environment I would agree (even though I had problems with it, it was very quick from what I could see) - but in the server environment (which is my only interest) Vmware Server is by far the better choice.

---

### Post by aretei on 2007-03-13
Well Virtualbox is licensed under GPL whereas no other programs aren't so I'd suggest using Virtualbox.
(oddly enough virtualbox asked me to agree with their terms of use PUEL or something)

---

