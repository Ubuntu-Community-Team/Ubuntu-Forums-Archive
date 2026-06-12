---
title: "What laptop PC specs do I need to Virtualize Windows 10 with Lubuntu as host?"
date: 2023-06-03
forum: Virtualisation
---

### Post by AbleTassie on 2023-06-03
Hello Virtualization Forum:

I want to stop using Windows 10 as my primary Operating System and move back to Lubuntu LTS. (I stopped using Lubuntu on my newest PC about 5 1/2 years ago.) My present "newest" PC is  an ACER E5-575-33BM that is about 6 years old with Windows 10 Home Edition; **Processor** Intel(R) Core(TM) i3-7100U CPU @ 2.40GHz 2.40 GHz, **RAM** 4.00 GB (3.87 GB usable), **System Type**: 64-bit operating system, x64-based processor. 

I will probably get a newer, but refurbished PC laptop and I want to run that latest version of Lubuntu LTS with Windows 10 running on a Virtual Machine with Lubuntu as the host. (I would rather not spend unnecessary money on Windows 11.) Information from a previous post on Ubuntu Installation & Upgrade Forum [here]("https://ubuntuforums.org/showthread.php?t=2487011&page=2") suggested that I should really have more than 4GB of RAM and also that there may be other requirements to be able to run Windows 10 as a virtual machine with Lubuntu as the host, see this [later page]("https://ubuntuforums.org/showthread.php?t=2487011&page=3") of the same thread. In addition, apparently Lubuntu may have changed in that in 2020 it switched from being GTK-Gnome based to being based on Qt (which what KDE is based on). So maybe going back to Lubuntu will seem significantly different.

(I used to use Lubuntu LTS all the time on a different older PC (a Lenovo Ideapad Y510 about 10 years old) and in fact ran Windows XP on Virtualbox (with Guest additions) with Lubuntu as the host. But I had some problems connecting the Virtual Machine to the internet and also to the CD Disc reader. As I recall I eventually got the Virtual Machine with Windows XP to connect (at least to some extent) to the internet and the CD Disc reader. But, I also ended up creating a "Shared Folder" that allowed me to transfer files back and forth between the regular real Lubuntu Machine and the VM with Windows XP. And that worked pretty well.)

I would like to be able to connect the Windows 10 Virtual Machine (on my new, yet to be bought, PC laptop) to the internet and also the DVD/CD reader on the new laptop.

QUESTIONS: 

Does anybody have any suggestions as to the specs a PC laptop should have to run the latest Lubuntu LTS as the OS with Windows 10 running in a Virtual Machine (Lubuntu as host)? 

How much RAM should I have?

Do you think that another version of Ubuntu or Linux that is similar to Lubuntu LTS would work better for me because of the switch from GTK-Gnome to Qt in2020?

Any other comments or advice will be welcomed.

Thank you,

A.

---

### Post by lammert-nijhof on 2023-06-04
I run a Windows 10 VM on Ubuntu 22.04 LTS on my laptop with a i5-2520M and 8 GB of DDR3. I assign 3GB to Windows 10. Buy a laptop with at least 8 GB and if you want to run more than 1 VM go for at least 16GB,
I see no reason to use Lubuntu, better move to Ubuntu, it has maintenance for 5 years with a free extension to 10 years, instead of the 3 years for Lubuntu. 
For Virtual Machines I prefer Virtualbox, since I had no problems with it in the past 14 years.

Nowadays you have to forget using the laptop DVD in a Virtual machine. If you have DVDs you could copy the content to the HDD using Ubuntu. It is easy for music, photos, videos, programs and OSes. Those folders on the HDD with the DVD content you can share between Host and the VM using the Shared Folders menu. For e.g Windows 10 you can download an ISO file from Microsoft and use that to install Windows. If you want to reuse the activation code, install and activate the Windows VM on your current laptop.  With a lot of patience and a little bit of luck it just works in 4GB (3GB for Windows and 1GB for Ubuntu). Later you can copy that VM to your new laptop.  Otherwise you have to phone Microsoft for the favor of transferring the license.

---

### Post by ajgreeny on 2023-06-04
A few years ago I tried Windows 10 in VBox 6.1 but found it dreadfully slow even with 4G ram allocated to the VM.

Soon after that I moved from VBox to KVM/QEMU and the difference between the hypervisors was astounding with Windows running more or less as I've seen on bare metal installs.
VBox 7 is much better then version 6 in my experience and Windows 10 runs OK but still not as fast and smoothly as in KVM/QEMU. 

It's your choice obviously but if you've never tried or seen KVM/QEMU I suggest you have a look and try it out by installing virt-manager which by default will I think pull in that's needed. 

I will come back when I'm on my real computer, rather than this tablet, with a few links for you to look at which may help you if you want to try out my suggestion..

---

### Post by SeijiSensei on 2023-06-04
Memory matters more than anything else. I'd go with a minimum of 8 GB if you can. I usually allocate 4 GB of memory to Windows VMs. Linux VMs can run in much less depending on whether you're using a GUI window manager. A text-only VM, like a server, can easily run in 1 GB or less.

---

### Post by AbleTassie on 2023-06-05
Thanks to everybody for their replies; they are food for thought and will enter into my thinking. A couple more questions: 

**1)** I don't understand the last post by TheFu on this forum thread [page]("https://ubuntuforums.org/showthread.php?t=2487011&page=3") that seems to indicate I will need special hardware to run a virtual machine. **The post says:**[I] " I definitely remember cheap Acer machines with CPUs that could support  VT-x or AMD-v (those are the hardware virtual machine instructions) also  having no way to enable those features in the BIOS.  That means you  should check the BIOS for your computer and verify that "Virtualization"  can be enabled. I double-checked that the i3-7100U CPU does support VT-x.  [https://ark.intel.com/content/www/us...-2-40-ghz.html]("https://ark.intel.com/content/www/us/en/ark/products/95442/intel-core-i37100u-processor-3m-cache-2-40-ghz.html") . You need to check the BIOS yourself.  [https://community.acer.com/en/discus...virtualization]("https://community.acer.com/en/discussion/498060/acer-aspire-e-15-e5-575-33bm-virtualization") is encouraging. It says that recent Acer BIOSes have VT-x enabled, even if there's no way to enable it in the BIOS.  YMMV."

[/I][B]Is it really true that I should be sure that a PC that I buy has the hardware to allow a virtual machine? 
Any more comments on this issue will be appreciated.

2) Will I need to have the Virtual Machine connected to the internet to install Windows in the Virtual Machine (VM)?[/B] Since the license number for the Windows OS is now burned into the BIOS or UEFI, it seems like that it would be necessary to connect the VM to the internet. (I am willing to accept that notion that DVD/CD readers really generally are not connected within the VM, but I wonder about the internet connection for the reason of installing Windows. I will need Windows for Tax Software at least.). 

**3)** I appreciate the suggestion to use Ubuntu, especially since the support lasts longer. But, I tried Ubuntu about 15 years ago and my PC just did not have the fire power to use it; it was just too slow. So I was advised (by this forum as I remember) to switch to Lubuntu and that has worked well for me. I just use email, cruise the web, use the Libre Office Writer program and watch youtube videos. I don't play games online or otherwise, and I don't have a bunch of photos or music that require a lot of speed and storage space. So I am wondering if my next refurbished PC has less RAM, and a slower CPU if I might run into the same type of problems with Ubuntu that I did before. **Maybe I should use a different Ubuntu flavor, like maybe Xubuntu (dawn to dusk) like AJGreeny for example?** See my original post, I was cautioned that Lubuntu changed in 2020 from GTK-Gnome based to being based on Qt (which what KDE is based on); I am not sure how that change would affect me. I think I fooled around with Xubuntu for a while and liked it.
[B] 
Any more comments on this issue will also be appreciated.
[/B]
Thank you,

Able

---

### Post by tea for one on 2023-06-06
> **AbleTassie said:**
> Is it really true that I should be sure that a PC that I buy has the hardware to allow a virtual machine?
Yes, you need to be sure. Generally, there is a UEFI setting to enable/disable Virtualisation.
> **AbleTassie said:**
> Will I need to have the Virtual Machine connected to the internet to install Windows in the Virtual Machine (VM)?
No, you can install Windows in a VM using a local user account.

---

### Post by AbleTassie on 2023-06-06
**In answer to my question:** *"Is it really true that I should be sure that a PC that I buy has the hardware to allow a virtual machine?"* Tea for One wrote: 
> **tea for one said:**
>  Yes, you need to be sure. Generally, there is a UEFI setting to enable/disable Virtualisation.

**QUESTION:** So how can I be sure? **Do I check the specs of the CPU chip?** For example, the specs of the Intel® Core&#8482; i3-7100U Processor (link in previous post) seems to indicate ability to virtualize by saying: 

*"Intel® Virtualization     Technology (VT-x) [SUP]&#8225;[/SUP] Yes ; Intel® Virtualization     Technology for Directed I/O (VT-d) [SUP]&#8225;[/SUP] Yes;  Intel® VT-x with Extended Page Tables (EPT) [SUP]&#8225;[/SUP]     Yes"*   
[B]
Do I need to check the BIOS of any PC I want to buy as well? What should I look for?[/B]

**In answer to my question:** *"Will I need to have the Virtual Machine connected to the internet to install Windows in the Virtual Machine (VM)?"* Tea for One wrote:

Tea for One wrote: > **tea for one said:**
>  No, you can install Windows in a VM using a local user account.  

Any more comments from anybody else will be welcomed.

**Edit added about 13 hours after post:** Here are a couple of good free online articles that describe how to determine if your PC's hardware supports virtualization:
[U]
How To Check If Your Pc Supports Hardware Virtualization[/U] at [https://www.alibabacloud.com/tech-news/virtualization/2cw-how-to-check-if-your-pc-supports-hardware-virtualization](https://www.alibabacloud.com/tech-news/virtualization/2cw-how-to-check-if-your-pc-supports-hardware-virtualization)

and _Does My Motherboard Support Hardware Virtualization_ at [https://www.alibabacloud.com/tech-news/virtualization/2nr-does-my-motherboard-support-hardware-virtualization](https://www.alibabacloud.com/tech-news/virtualization/2nr-does-my-motherboard-support-hardware-virtualization)

I continue to welcome further advice and comments --- I thought all PCs allowed for virtualization until reading the forum.

Thanks,

A.

---

### Post by lammert-nijhof on 2023-06-08
What you are talking about are ancient times, today Virtualbox is comparable with respect to performance.

---

### Post by DuckHook on 2023-06-09
> **tea for one said:**
> …you can install Windows in a VM using a local user account.

> **AbleTassie said:**
> …Any more comments from anybody else will be welcomed.
With all due respect, this is true of W10 but not quite the case for W11 (which I know you are not interested in). However, for the sake of any lurkers out there…

The newest Windows 11 will not install out of the box without access to the Internet and the creation of an account with Microsoft. Whether this is just part of the overall tracking culture of our times is a matter that I will leave for you to judge.

There is a workaround to allow for installation without W11 reporting home to mothership, but it involves firing up a powershell, then changing a registry entry, then rebooting. Many instructions all over the Internet, but be forewarned that this sort of hoop&#8209;jumping will be necessary.

You will also need to install/activate a special virtual widget that fools W11 into thinking that the VM has a security chip. W11 won't install without it.

I managed to successfully install W11 in a KVM VM with the above tricks, but it left a distinctly sour taste in my mouth. Better to stick with W10 if you can.

---

### Post by AbleTassie on 2023-06-10
> **DuckHook said:**
> With all due respect, this is true of W10 but not quite the case for W11 (which I know you are not interested in). However, for the sake of any lurkers out there&#8230;

The newest Windows 11 will not install out of the box without access to the Internet and the creation of an account with Microsoft. ......There is a workaround to allow for installation without W11 reporting home to mothership, but it involves ....a powershell, ..... changing a registry entry.... rebooting.  .... be forewarned that this sort of hoop&#8209;jumping will be necessary. ....... need to install/activate a special virtual widget that fools W11 .... I managed to successfully install W11 in a KVM VM with the above tricks, but it left a distinctly sour taste in my mouth. Better to stick with W10 if you can.

Thanks for the caution DuckHook. I will keep that in mind and it is a good caution; I appreciate it.

 A couple more QUESTIONS: 

1) Is Windows in a VM with an Ubuntu flavor as the host any more or less vulnerable to Windows viruses than Windows running "normally" in a PC (as a non-virtual machine)?

2) Have people in general found that older versions of Windows are OK for running most/essentially all "Windows Necessary" software, like tax software?

Thanks again.

I think we are getting close to marking this thread [SOLVED].

A.

---

### Post by AbleTassie on 2023-06-15
Thanks to everybody for their replies. I am marking this thread as  SOLVED. I just want to say that there are several articles online that  address the question of which Ubuntu flavor you might want to try and  ultimately install. Here are some example articles: [Lubuntu vs Xubuntu &#8211; What is the difference?]("https://www.linuxfordevices.com/tutorials/ubuntu/lubuntu-vs-xubuntu") and another [How to Choose Between Ubuntu, Kubuntu, Xubuntu, and Lubuntu]("https://www.howtogeek.com/718012/how-to-choose-between-ubuntu-kubuntu-xubuntu-and-lubuntu/")  . I have gone with Lubuntu at this point, but I just learned that there  is no Software Center for Lubuntu, but Xubuntu has one. So I may have a  little "buyer's remorse" but I can remedy that easily enough if I  decide it's really an issue.

Thanks again to everybody,

A.

---

### Post by DuckHook on 2023-06-17
Apologies for the late reply. Life has been crazy lately.

> **AbleTassie said:**
> 1) Is Windows in a VM with an Ubuntu flavor as the host any more or less vulnerable to Windows viruses than Windows running "normally" in a PC (as a non-virtual machine)?
Windows is Windows and is just as vulnerable running in a VM as on bare metal. However, it should do less damage if it catches something because it is sandboxed and won't escape the VM (if VM is configured properly). It is also easy to roll back to a clean snapshot when using a VM, provided that you made one and know it to be clean. This is a further advantage against Windows malware. However, if you are infected and then use Windows browser to visit, say, your banking site, then of course you will be compromised. A VM is not a fire&#8209;and&#8209;forget strategy, nor is it a panacea. Proper security is complicated and resists easy answers. But, used properly, VM confinement offers more protection than running Windows on bare metal.
> 2) Have people in general found that older versions of Windows are OK for running most/essentially all "Windows Necessary" software, like tax software?

Again, the answer is: it depends. If you are referring to something still in support like W10, then you should have no problems. But if you are referring to XP, then all bets are off. I don't know much about Windows anymore, but I've heard of some apps that will only work on W11 and won't run on W10. Just hearsay though and I can't help thinking that would be very odd.

---

