---
title: "Co - running linux and windows"
date: 2015-08-07
forum: Ubuntu, Linux and OS Chat
---

### Post by rwe061 on 2015-08-07
With Windows 10 there are a number of articles in places like PCWorld magazine about dual boot systems, so some new interest in linux is generated.  Dual boot is a difficult way to switch OS, since you have to go through a shutdown and reboot.  That isn't very attractive if you are using an application that only runs under windows but you prefer to normally be in linux.    Is it possible to switch OS's live ?  Or to have both windows and linux running all the time ?    I am thinking how nice it would be if I could swap from windows to linux with a function key.  A suspend function essentially saves the state of the OS and restores it.  If both systems could boot and enter a suspend state could you switch from one to another ?  I realize this would be a complex project for someone to do.  I guess the first thought is to use a virtual machine, but it might have issues too.  In many cases we have the OEM version of windows running on our hardware, and it is probably difficult to transfer that OEM windows into the virtual machine.  Then you would run linux in the VM.    I guess there are some resource related problems that would be related to peripherals and drivers that are owned by one OS or the other.    I was just thinking how nice it would be nice if it could work.  Is it possible ?

---

### Post by TheFu on 2015-08-07
BTW - that is a big question for your first post here.
Welcome to these forums.

None trivial is putting it nicely. Not worth the effort is the correct answer, IMHO.  There always has to be 1 OS controlling everything at boot. Perhaps, one day, someone will make some firmware that does what you seek. Doubtful.

You will use a virtual machine and windows will run inside it, but to keep performance up, you need VT-d for direct hardware access.  The hardware that gets passed thru from the hostOS to the guestOS cannot be shared. That means you need 2 GPUs, 2 Disk controllers, 2 NICs.  Then it just comes down to sharing the CPU and RAM - which isn't really any issue for the last 10 yrs.

Shared networking works very well - so there really isn't any need to VT-d that for most applications.

Shared storage works very well too - just use LVM to create the storage for any VMs and spread the I/O load over multiple disks. It works.

Video is the real issue, so concentrate on that.  Xen and KVM do it, but it is very picky about the GPU versions that work. There are ongoing threads about this in the Virtualization sub-forum here.
There may be other VM technologies which can handle GPU passthru - bet they cost $150-$15K, however. Research VMware Workstation and VMware ESXi.

Oh - and forgetaboutit with an OEM Windows license. Won't work, IME - [https://superuser.com/questions/821251/can-i-transfer-my-windows-7-license-to-a-virtual-machine-running-on-the-same-c](https://superuser.com/questions/821251/can-i-transfer-my-windows-7-license-to-a-virtual-machine-running-on-the-same-c) says there is a way. I've never seen this work and the suggested answer is vague, non-specific, and doesn't provide details.

Many of the people here won't touch Windows any time in a month, so we may not be the best people to ask.  I touch it daily, but don't do anything beyond the 3 tasks I need it for. Have never seen Win8, 8.1 and don't plan to see Win10. When Win7 support ends, I'll look for something else to solve my 3 tasks. By then, hopefully there will be Linux alternatives. ;)

---

### Post by rwe061 on 2015-08-07
Thank you for mentioning VT-d, didn't know about it.  Also, the GPU issues.  I have played with VMs but maybe I should try again.

And, for mentioning Xen [ Xen is a hypervisor using a microkernel design, providing services that allow multiple computer operating systems to execute on the same computer hardware concurrently. ] from wikipedia.  And KVM (Kernel-based Virtual Machine) is a virtualization infrastructure for the Linux kernel that turns it into a hypervisor.  I'll do some reading.

I had not heard of the term hypervisor --- kind of a super kernel I guess.

And, I guess some peripheral hardware issues could be helped by creating a sort of server architecture - driver that can accept data from two OS's to resolve contention and sharing issues.

Meanwhile, I will put my "_seamless OS switcher_" wish on the same list as my warp drive intergalactic sports cruiser. Maybe it isn't worth the effort as you suggest.

---

### Post by NathanRodriguez on 2015-08-07
> **rwe061 said:**
> 
Meanwhile, I will put my "_seamless OS switcher_" wish on the same list as my warp drive intergalactic sports cruiser. Maybe it isn't worth the effort as you suggest.

Do you have some kind of beta of this warp drive ?
;)

---

### Post by rwe061 on 2015-08-08
beta ?  LOL  

No beta nor hope of success, however I am ready to start crowd-funding.

---

### Post by SeijiSensei on 2015-08-08
Install Virtualbox and run one OS in the VM. It can be Windows on the desktop and Linux in the VM or vice versa.

---

### Post by rwe061 on 2015-08-09
On the virtual machine approach, I tried this a few years ago and became frustrated due to a number of problems.  Maybe it is better now.

What happens when an OS is suspended and saved ?  Is the state of the hardware machine and OS saved ?  Is there an image that can be restored, quickly ?

If that is correct, can I (in theory) swap in a suspended windows image or swap in a suspended linux image ?  This might be reduced to several seconds.

That might not be as nice as co-running two operating systems, but better than a full shutdown and reboot.

Maybe I'm not thinking of something.  

Thanks for the comments.

---

### Post by mastablasta on 2015-08-10
> **rwe061 said:**
> 
What happens when an OS is suspended and saved ?  Is the state of the hardware machine and OS saved ?  Is there an image that can be restored, quickly ?
.
yes. I have very old Win XP machine, single core and only 4 GB ram. it takes only a couple of seconds to restore previous state. if I had more ram and new CPU it would be a lot faster.

> 
If that is correct, can I (in theory) swap in a suspended windows image or swap in a suspended linux image ?  This might be reduced to several seconds.
That might not be as nice as co-running two operating systems, but better than a full shutdown and reboot.


you can run multiple OS concurrently (one next to each other) or one inside the other. you need RAM. and CPU. you can then alt tab between them. you can use shared folder to share data between them. you can also do things like run virtual Windows inside Linux and inside that virtual Windows, run another Linux. 

a short how to: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

I usually use the premade Linux machines (like Turnkey Linux or Bitnami stack) to run a server for testing. server doesn't need as much ram or CPU/GPU power as desktop.
Forgot to mention that if you use one of premade images, then there is no install necessary - you just setup virtual PC machine and mount the image and you are good to go. deployed and ready within a minute or two in a new PC.

---

