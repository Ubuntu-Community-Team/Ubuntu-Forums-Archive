---
title: "confused with Xen install into existing ubuntu"
date: 2023-09-27
forum: Virtualisation
---

### Post by doc1623 on 2023-09-27
I'm trying to learn docker through a course. During the course you need  VMs. I know the easiest way is Virtual Box, but I know that Xen is the  basis of all container technology (if I understand it correctly). So if I  can do it that way, I would like to. My machine, is a few years old but  has plenty of processing power. Less disk space than I would like.
I've  read a little bit about how a hypervisor works, but at the practical  use level, I'm confused. Is Xen headless, I know it can be, but does it  force it? I can't follow the instructions exactly from that link,  because I'm already on Ubuntu. It came that way from Dell. I don't want  to bother doing a full reinstallation of everything right now. I want to  complete my course, preferably with Xen.
I can't do "During  installation of Ubuntu"... I did install Xen and tried to reboot, and  got the no signal. Is that normal, or because I missed something in the  order of operations? I did go through and enable everything I saw in the  bios for virtualization. When googled I found  ([https://askubuntu.com/questions/1317599/xen-hypervisor-boots-to-a-black-screen-after-installation](https://askubuntu.com/questions/1317599/xen-hypervisor-boots-to-a-black-screen-after-installation))  which had no useful responses. 
I've been reading various web pages, but I'm a bit confused. Most say just install, reboot, then 

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

I've been trying to check somethings from other pages, but I'm still confused. 


```
%sudo apt search grub|grep "^grub"|grep "installed" 
grub-common/jammy-updates,now 2.06-2ubuntu7.2 amd64 [installed,automatic] 
grub-efi-amd64/jammy-updates,jammy-security,now 2.06-2ubuntu14.1 amd64 [installed,automatic] 
grub-efi-amd64-bin/jammy-updates,jammy-security,now 2.06-2ubuntu14.1 amd64 [installed] 
grub-efi-amd64-signed/jammy-updates,jammy-security,now 1.187.3~22.04.1+2.06-2ubuntu14.1 amd64 [installed] 
grub-xen-bin/jammy-updates,now 2.06-2ubuntu7.2 amd64 [installed,automatic] 
grub-xen-host/jammy-updates,now 2.06-2ubuntu7.2 amd64 [installed,automatic] grub2-common/jammy-updates,now 2.06-2ubuntu7.2 amd64 [installed,automatic]

% sudo apt search grub|grep xen
grub-xen/jammy-updates 2.06-2ubuntu7.2 amd64 
grub-xen-bin/jammy-updates,now 2.06-2ubuntu7.2 amd64 [installed,automatic] 
grub-xen-dbg/jammy-updates 2.06-2ubuntu7.2 amd64 
grub-xen-host/jammy-updates,now 2.06-2ubuntu7.2 amd64 [installed,automatic]

```

boot directory 

```
$ ls -larth /boot/
total 355M
drwx------  4 root root 4.0K Dec 31  1969 efi
-rw-r--r--  1 root root 8.0M Apr 29  2019 vmlinuz-4.15.0-1037-oem.efi.signed
-rw-r--r--  1 root root 181K Feb  6  2022 memtest86+_multiboot.bin
-rw-r--r--  1 root root 181K Feb  6  2022 memtest86+.elf
-rw-r--r--  1 root root 179K Feb  6  2022 memtest86+.bin
-rw-r--r--  1 root root 1.2M Nov 26  2022 xen-4.16-amd64.gz
-rw-r--r--  1 root root 2.7M Nov 26  2022 xen-4.16-amd64.efi
-rw-r--r--  1 root root 2.2K Nov 26  2022 xen-4.16-amd64.config
-rw-------  1 root root 6.0M Aug 14 04:05 System.map-5.15.0-83-generic
-rw-r--r--  1 root root 256K Aug 14 04:05 config-5.15.0-83-generic
-rw-------  1 root root  12M Aug 14 04:07 vmlinuz-5.15.0-83-generic
-rw-r--r--  1 root root 154M Sep  5 06:32 initrd.img-5.15.0-83-generic
-rw-------  1 root root 6.0M Sep  5 08:31 System.map-5.15.0-84-generic
-rw-r--r--  1 root root 256K Sep  5 08:31 config-5.15.0-84-generic
-rw-------  1 root root  12M Sep  5 11:57 vmlinuz-5.15.0-84-generic
lrwxrwxrwx  1 root root   25 Sep 20 06:38 vmlinuz.old -> vmlinuz-5.15.0-83-generic
lrwxrwxrwx  1 root root   25 Sep 20 06:38 vmlinuz -> vmlinuz-5.15.0-84-generic
lrwxrwxrwx  1 root root   28 Sep 20 06:38 initrd.img.old -> initrd.img-5.15.0-83-generic
lrwxrwxrwx  1 root root   28 Sep 20 06:38 initrd.img -> initrd.img-5.15.0-84-generic
drwxr-xr-x  5 root root 4.0K Sep 20 06:39 grub
-rw-r--r--  1 root root 154M Sep 25 11:13 initrd.img-5.15.0-84-generic
drwxr-xr-x  4 root root 4.0K Sep 25 11:13 .
drwxr-xr-x 23 root root 4.0K Sep 27 13:04 ..

```

Sorry didn't paste right

```
# # Automatically generated file; DO NOT EDIT. # Xen/x86 4.16.0 Configuration # CONFIG_CC_IS_GCC=y CONFIG_GCC_VERSION=110300 CONFIG_CLANG_VERSION=0 CONFIG_CC_HAS_VISIBILITY_ATTRIBUTE=y CONFIG_X86_64=y CONFIG_X86=y CONFIG_ARCH_DEFCONFIG="arch/x86/configs/x86_64_defconfig" CONFIG_INDIRECT_THUNK=y CONFIG_HAS_AS_CET_SS=y  # # Architecture Features # CONFIG_64BIT=y CONFIG_NR_CPUS=256 CONFIG_PV=y # CONFIG_PV32 is not set CONFIG_PV_LINEAR_PT=y CONFIG_HVM=y CONFIG_SHADOW_PAGING=y # CONFIG_BIGMEM is not set CONFIG_TBOOT=y CONFIG_XEN_ALIGN_DEFAULT=y # CONFIG_XEN_ALIGN_2M is not set # CONFIG_XEN_GUEST is not set # CONFIG_HYPERV_GUEST is not set # end of Architecture Features  # # Common Features # CONFIG_COMPAT=y CONFIG_CORE_PARKING=y CONFIG_GRANT_TABLE=y CONFIG_ALTERNATIVE_CALL=y CONFIG_HAS_ALTERNATIVE=y CONFIG_HAS_COMPAT=y CONFIG_HAS_EX_TABLE=y CONFIG_HAS_FAST_MULTIPLY=y CONFIG_HAS_IOPORTS=y CONFIG_HAS_KEXEC=y CONFIG_HAS_PDX=y CONFIG_HAS_SCHED_GRANULARITY=y CONFIG_HAS_UBSAN=y CONFIG_MEM_ACCESS_ALWAYS_ON=y CONFIG_MEM_ACCESS=y CONFIG_NEEDS_LIBELF=y  # # Speculative hardening # CONFIG_SPECULATIVE_HARDEN_ARRAY=y CONFIG_SPECULATIVE_HARDEN_BRANCH=y CONFIG_SPECULATIVE_HARDEN_GUEST_ACCESS=y # end of Speculative hardening  CONFIG_HYPFS=y CONFIG_HYPFS_CONFIG=y CONFIG_IOREQ_SERVER=y CONFIG_KEXEC=y CONFIG_XENOPROF=y # CONFIG_XSM is not set CONFIG_SCHED_CREDIT=y CONFIG_SCHED_CREDIT2=y CONFIG_SCHED_DEFAULT="credit2" CONFIG_CRYPTO=y CONFIG_LIVEPATCH=y CONFIG_FAST_SYMBOL_LOOKUP=y CONFIG_ENFORCE_UNIQUE_SYMBOLS=y CONFIG_CMDLINE="" CONFIG_DOM0_MEM="" CONFIG_TRACEBUFFER=y # end of Common Features  # # Device Drivers # CONFIG_ACPI=y CONFIG_ACPI_LEGACY_TABLES_LOOKUP=y CONFIG_NUMA=y CONFIG_HAS_NS16550=y CONFIG_HAS_EHCI=y CONFIG_HAS_CPUFREQ=y CONFIG_HAS_PASSTHROUGH=y # CONFIG_IOMMU_QUARANTINE_NONE is not set CONFIG_IOMMU_QUARANTINE_BASIC=y # CONFIG_IOMMU_QUARANTINE_SCRATCH_PAGE is not set CONFIG_HAS_PCI=y CONFIG_HAS_PCI_MSI=y CONFIG_VIDEO=y CONFIG_VGA=y CONFIG_HAS_VPCI=y # end of Device Drivers  # CONFIG_EXPERT is not set # CONFIG_UNSUPPORTED is not set CONFIG_ARCH_SUPPORTS_INT128=y  # # Debugging Options # # CONFIG_DEBUG is not set # end of Debugging Options

```

---

### Post by TheFu on 2023-09-28
Xen was the way that Amazon did virtual machines until around 2008, when they switched to KVM/Qemu.  Most of the world switched to kvm/qemu for their hypervisors too.  Pretty much all commercial VPS providers use KVM now, except companies who need to eat their own dogfood, like MSFT.

I used Xen XM for a few years at work.  We also used VMware ESX and ESXi.  When Amazon switched to kvm/qemu, I took a long look and tested it out myself. Kvm/qemu is part of the Linux kernel and maintained by the Linux Kernel team, unlike Xen.  Back in 2009-2010, I was having a few issues with Xen VMs refusing to boot if there were kernel changes. It wasn't an issue with every new kernel, but a few times a year, after I'd patch all my systems, the Xen hypervisor would refuse to boot one or more VMs.

In Linux, servers can be software and it is common for software to be created in layers with the GUI being a wrapper around the real programs that handle a specific task, like running and managing a VM.

If you want to learn the industry standard for hypervisors, learn kvm/qemu. There are some management wrappers to make that easier. These include virt-manager and libvirt libraries.  With those 2 additions, managing kvm/qemu VMs is nearly as easy as virtualbox, but with most of the enterprise virtualization capabilities we'd expect from a true enterprise VM system.

KVM/qemu is the more correct term, but you'll see people call it just "kvm".  This can be confusing, since KVM can also describe a piece of hardware that makes using multiple computers with single keyboards, single mouse, and single display possible.  I manage my KVM virtual hosts using a KVM. ;)

Since I haven't used Xen in many years, you should realize that there is a webapp interface full of management cheese with the normal install. It is very impressive.  There are webapps to manage KVM as well, but I'm less familiar with those since I generally manage my KVM hosts remotely using **virt-manager** (or **virsh**), which supports the full life cycle of a VM over a remote connection.  A webapp to manage KVM would be **Cockpit** [https://www.tecmint.com/manage-kvm-virtual-machines-using-cockpit-web-console/](https://www.tecmint.com/manage-kvm-virtual-machines-using-cockpit-web-console/) or **proxmox**, which generally will take over a system completely to ensure you get all the enterprise capabilities like VM snapshots at the volume manager layer and with the ability to have multiple proxmox servers joined to a cluster for centralized management.  Of course, we can always do cluster management manually using whatever clustering system we prefer, but that's a much more complex task and requires specific skills with the different clustering methods.

Whenever posting terminal output, please wrap it in forum 'code tags' so all the columns line up correctly. Otherwise, it is just too hard to read.  Please edit your post above, use the "Advanced" editor and the '#' key works just like a bold, italics, quote tags, just for "code-tags".  ZERO formatting should be needed when pasting output from a terminal, then wrapping them in these 'code-tags' for the nice columns to be maintained.

1 very important thing.  If you are aren't an expert with Linux and loading/unloading kernel modules, you'll want to have just 1 hypervisor installed on a physical system. So, if you decide to follow my suggestion to use KVM rather than Xen, then you'll need to remove Xen first or bad things will happen.  These hypervisors need exclusive access to specific motherboard and CPU capabilities, that's why.  If you look through these forums, you'll see many people here have been changing to KVM for the hypervisor requirements.  KVM is what OpenStack uses too, so ... the knowledge won't be useless when it is time to stand up a 5-2500+ physical server farm.

Of course, if you are planning to stand up a 100+ physical server farm, you'll likely want to research MAAS from Canonical and consider their juju tools. I've never needed those myself. Corporations often choose 1 vendor OR they choose to be vendor agnostic, which MAAS and Juju most definitely are not.

---

### Post by MAFoElffen on 2023-09-28
I'm a big +1 with TheFu's recommendation on using KVM for any VM's, but...

Let's back up a bit...

Before I saw anything, beware of reading things on the internet, and always check the dates of when they were written, and last updated. If you look at the links that were in your first post, the Ubutnu Xen wiki page was last updated in 2015. That is why, in AskUbuntu question you linked to, that user used the same outdated wiki page, ad the only responses he got, were asking him "Are you serious?" And were probably laughing.

When I was a Moderator here, years ago, I used to support Xen Server, which got bought up by Cintrix, and they turned it completely into closed source in 2017. That is when I stopped supporting it. It never was my preference of Hypervisors. In fact, it was in the bottom of my list. I still had it installed on one of my machines to help me support it, but it was a PITA. Fortunately, not many people who used Virtual hosts really used Xen as their host. There was another fork by the original founders of that is opensource, which is XCP-ng. You can read the history of that here: [https://en.wikipedia.org/wiki/XCP-ng](https://en.wikipedia.org/wiki/XCP-ng)

Now my questions and comments:
Which "course" are you trying to learn Docker from? Why do they say to use XEN. And if they are, what is the date of that course? Because Citrix never did have a very big market share as a VM Hosting system. 

You know that you can easily install Docker directly onto Ubuntu right? Or to keep things isolate, as a safe virtual test area, install it to an Ubuntu VM as a nested virtualization. Which you would be running a VM, which would be running Docker containers.

That VM Host system can be anything that supports Nested Virtualzations. Even VirtualBox supports Nested Virtualizations these days. My preference is KVM, along with TheFu. I believe we both have used KVM for over a decade.

If you want to learn Docker, you do not want distractions from a high learning curve of a virtual host system, just to host your VM, which you will be installing Docker to. I feel that the learnig curve of Xen Server was high, compared to other virtual hosts. 

I first installed Docker back in 2014. That was when Docker and Canonical were in the press, because they were working on a few things together. Then MS and Canonical were working on a few other things... It's actually pretty easy to install, spin up a Docker template and start using. Then it got boring for me after that.  I still keep getting invited to Docker's training events and conferences... Docker does have good marketing.

It only takes 6 commands to install Docker on Ubuntu 22.04:
```

sudo apt update
sudo apt install docker.io
sudo systemctl start docker.service
sudo systemctl enable docker.service
sudo usermod -aG docker $USER
reboot

```
The you are ready to go
```

sudo docker pull hello-world
sudo docker run hello-world

```
But as a member of the docker group, you can also omit the 'sudo' in those...

That's it. Search for some Docker images to pull and run. Play with templates. Learn to build your own and how to configure 'things'.

I'm not going to discuss other products. I was going to, but the OP didn't bring them up, and he is just wanting to learn.

---

### Post by TheFu on 2023-09-28
Yeah, I didn't touch on docker. I don't like it and don't use it.  Played with docker a few times over the years to confirm the things I don't like (privileged containers suck!).  I prefer other Linux Container solutions.  Docker is the MSFT of the container systems, so I understand why someone might want to use it.

There are 2 types of linux container users.
- purely end users who will trust whatever they find on the internet and run that self-contained code on their computers, on their network, on their storage, doing who knows what?
- people who learn to build a docker container from the ground up and can nearly assure that nothing nefarious is added to a container, since they built the layers. "assure" is a bit loaded, since we each can't really review all the software on our Ubuntu systems, but there is a trust factor from different distros and project teams.

Learning docker is a reasonable thing, so when you graduate to other tools, you'll have a baseline for comparison.

---

### Post by doc1623 on 2023-09-28
Wow, lots of answers. Thank You. So much more than what I was asking, but that gives me the latitude to ask further :P questions. First, the docker course is cloud academy. I've already taken the regular docker portion but I'm aiming for their cert. It's not the official one but I need career help. I've never done certs, I'm middle age and I've been out of work for a while. Because of my sporadic resume, and mediocre interview skills... I've had trouble. I'm trying to go the DevOps/SRE route and or IAM (as I've done some of the, but just two years using different software). I love coding, especially on Linux, but I only get to do a bit. I try to go the Linux/open source route because that knowledge transfers more easily than a single proprietary app or suite. I've played with containers before, but I understand the encapsulation and security, but I've not been able to grasp the home use, or for the future of Linux or open source. I've tried clear linux and it was a mess as far as I'm concerned (but that's been some time ago). Some programs had missing functionality, some didn't even work and there wasn't any configuration. As a person who's used both FreeBSD and Gentoo, that was too much.  Even with Ubuntu and the Snap package made my usual Linux management harder and slowed the computer too much... and again the lack of functionality sometimes... ps -ef or ps aux... was a mess. I'm a firefox user but now, if I close the last window. Something is still running, sometimes not under the "firefox" name. I think we're going to need new tools to manage linux (maybe they are there, and my aging a** just doesn't know them).   (okay full disclosure, as this is a bit all over.... it's my ADHD, that I only learned I had recently :P)

I'm learning for both for getting work and it helps my "burnout" in the industry as I get very tired of the "game" sometimes..and all the proprietary "stuff" (brown) 

Back to the real (off of my adhd ramblings)
Anyway, in this course, it said that all docker/container technology is/was based on zen and it's layer/api tech. I thought both were now kernel [supported]("https://en.wikipedia.org/wiki/Xen#cite_note-mtffd-48") . This portion is an orchestration section of the course, first swarm, then Kubernetes) You may be right for me to use kvm, but honestly, I was just trying to learn more and not use Virtual Box. I've used Qemu before only to play around, but it's been awhile... I swear, at this point, I've forgotten more than most collage grads. Part of that may be bragging, but it's also a lament, as my memory doesn't retain it. (also my job problem, I can learn anything quickly, as I probably did it or something like it before, but ask me questions like I'm just did is yesterday ... and I lose)

So, I guess I can use either Xen or KVM (xenproject, not proprietary). Xen has paravirtualization, but I've already forgotten what I read yesterday about that, probably because my focus was trying to get going. 

I won't do it right now, but I've thought of trying qubes, but along with ubuntu it uses systemd (which isn't my fav) not trying to start a debate, just personal pref. It's xen based... (idunno)

So, I'm all over the place, trying to learn for job, trying to learn for me (and my home net for enjoyment to push back on burnout and enjoy) and I'm trying to understand where containers work and where they don't and when they do what tools on the use on the host to understand ... like top,htop...with snap or firefox ... the tree of processes.. makes it hard to know what's running and what's not, what's using the resources. I sure hope linux isn't moving to the andriod model of background running! Yuck! 

I need to troubleshoot my firefox as it locks up. I will use it because I love it isolating cookies per domain, but now I have performance issues, I'm unsure of how to troubleshoot. (I can't look at its task manager because when it locks, it's completely unresponsive)

Thanks for all the response, This may not be very coherent, as it's allot, all in one disorganized mess! 

P.S. another complaint, I try to get recent info, but sites have learned to update the date, so even if I just search last month I can get articles years out of date. I thought Amazon was still using xen. 

From the wiki this [article ]("https://www.theregister.com/2017/11/07/aws_writes_new_kvm_based_hypervisor_to_make_its_cloud_go_faster/")broke the news. It looks like a large portion of the reason they switch has something to do with custom xeons they ordered? I'm more confused.

---

### Post by MAFoElffen on 2023-09-28
I feel you on the job front and on trying to document your skills. 

I am a disabled veteran. I was laid-off at the time, and I had heard that I qualified for VA Vocational Rehab, and that the VA would pay for me going back to college. I was in my mid-50's. Shortening the story, I wanted to get certs and document my past skills. 2 weeks after starting, the college hired me as a Student Tudor for Computer Science to teach students on courses I hadn't even taken there yet, but they could see I had the experience already. LOL. 

I was once put on a "not answer status"... That I was not called on to answer questions asked in classes, to give other students a chance to answer. If they did not know, then I was given the chance to answer. They hated when you told them something they said was not possible, was possible, if you did it "this way..." In 3 years, I completed 4 Computer Science degrees, 4 college proficiency certifications and almost a 4.0 average... I was on either their President's or Vice-President's List every term. I did all that in just 3 years. I took it on just like a job, taking over 20 credits each term.

During my time there, I updated their code examples for JAVA and Python (so they actually worked) for instructors to use in their lectures, taught an instructor how to use Eclipse IDE (so he could teach his students to use it for their course), taught instructors how to get their VM Hosts bridged to their class network (for their IT class projects), wrote tutorials for their Infrastructure Admin's and their course students. I installed the College's main SQL Server database on it's own VM Server... I wrote SQL scripts to create course dB's and to add student access to them... I wrote their proposal and course plan to convert their Object Oriented Programming Course from being JAVA to Python, as well as the Python Classes code for their lecture examples, and their Final Course Project. And in my Technical Writing course, my final project was adopted by the college as their real-world project to get their college website in compliance for federal Section 508 WCAG compliance. The video of my presentation for that was required to be viewed by all college staff.

Always good to be able to add things to your resume.

Further-- If you really need Xen (as a requirement for your course), then look into XCP-ng. That "is" what Xen Server was, and was intended to be. And it is free / opensource. Not a paid product trial version, like you might get from Cintrix, that is going to be short-sheeted in it's features, and then time-out on you after the trial period. Personally, I would install that as a VM Guest in KVM, so you keep your host system fresh and clean. That, and it will add experience and skills to various VM Host platforms, that you can add to your resume. Remember that KVM based systems have the largest share of that market.

Tip... write to the course Admin's and get their recommendation. I'm sure they will understand the background behind that.

---

### Post by doc1623 on 2023-10-02
Wow, thank you for that. Mine is a little different but yes very similar in many respects. At, this point I'm only on the 10% so I didn't qualify for the VA classes, from what my VRE lady said. The most she's done was an initial email of other resources. She told me I had no points. I looked it up and I do, they aren't at the same level as if I had a higher percentage, but I have them. I have a meeting with her tomorrow, but I may just resign from her "program". I started with her and so far it took months to be accepted and she has done nothing. I've completed a couple of assignments that weren't really relevant to me, but I did them. When I signed up, it was for classes, but later she put something in an email or something about financial aid. That would be wonderful, but she's pushed that back. I've had a meeting with her every 1.5 or so months for 30 minutes ..nothing. It's been at least 6 months, if not longer. She wants me to complete "other" crap. Which I've done, but none has been helpful. 

The classes are self-paced cert classes online. I have a bachelor's in Computer Information Systems, but that's it. I really don't have the financial resources to go back to school. I'm taking a Docker and a CISSP course and doing my best. The CISSP is being paid for by a program outside the VA.  I have anxiety, adhd, etc... It's hard, but I'm trying. Not the course material, but staying motivated. The course doesn't require Xen or KVM but doing that type of thing, learning for _me_, rather than for a just for a job, where I may or may not get to use what I've learned. So to keep from pure burnout, I learn what I enjoy e.g. opensource, linux, coding as well. It adds to the workload but keeps me motivated, and I learn, more as long as I can stay on track. 

Thank you for the reply. I'll go back and reset the bios settings remove zen and go to KVM, it'll be easier and I already had Qemu installed, from some previous self learning .... that I may not have completed, but I never had the cert goals before. I removed it but not purged, so I'll see when I reinstall what's there. 

Sorry for the late response, but I really appreciate your reply. I just now saw it. I may PM you if ok. 

Thanks Again,

---

### Post by MAFoElffen on 2023-10-03
Maybe. I would stick with it. Doing it shows her that you are somewhat willing to jump through her hoops, which might open up more for you. You never know. Not that much to ask right?

---

### Post by TheFu on 2023-10-03
> **MAFoElffen said:**
> Maybe. I would stick with it. Doing it shows her that you are somewhat willing to jump through her hoops, which might open up more for you. You never know. Not that much to ask right?

One of those TV news magazine shows did a story about how people with military backgrounds were being taken advantage of through financial aid by training companies.  Almost always, similar studies can be completed using a local community or state "tech" college for 1/10th the cost.  Just something to consider.  

I'm unconvinced about online-only classes, but I've never done any.  When I've taught at the local university, it was clear to me that if people didn't actually show up to the class, they'd end up dropping it. Some things that are very important aren't in books.

---

### Post by MAFoElffen on 2023-10-03
> **TheFu said:**
> Almost always, similar studies can be completed using a local community or state "tech" college for 1/10th the cost.  Just something to consider.
That's what I did. A local Community College that had a very good reputation for their Computer Science Department..

---

### Post by doc1623 on 2023-10-04
Things always change. I've been learning on my own for many years. College classes would be great, but I'm already without a financial margin. So even if they were free.... not really the time e.g. Mortgage, car payment, etc... I'll get certs from these. One is through a university, and it's sort of self-paced. It's the CISSP, which is being paid for through a veteran grant program at Syracuse University. It's not completely self-paced, as there is a finish time/date. Which should help. The other is Docker. I won't get the official cert to begin with, but if I'm comfortable, I may shell out the money for the official test. I couldn't afford the official class. This is through cloud academy, which bought out the Linux academy. I never used them, while they existed, I'm thinking I should have now. It's much cheaper, and they would guarantee I could do the exercises/labs on my Linux machines, as I don't have a windows and/or mac. 

I had a meeting with the councilor yesterday. I'll get some money in November, I hope. The details [here]("https://www.reddit.com/r/Veterans/comments/16y3rk0/need_help_meeting_with_councilor_again_tomorrow/"), on Reddit. I wasn't put on a track that included classes. It's supposed to be "rapid access to employment" track, but besides the links of other programs, so far fairly standard resume templates and mock interview (after 6–9 months from initial contact)

I'm just back working on this today. I finished a "class" in the CISSP course yesterday. I need to really get those vids done, because then the real studying begins. I'm uninstalling xen. Correct me if wrong, but I'm thinking Xen is the programming equivalent of C. Great if it works, but will crash with a very loud bang when it doesn't and the learning curve is too high (C I had a guy with 20 years experience tell me he was still working on the Malloc/Free.. ). I've had qemu installed before, again for self training, but not for exercising to get a cert. I do think they are more valuable and respected than they used to be. For years, I didn't even consider them because originally, too many years ago, I would have only done Microsoft, and they were ridiculously expensive. I've self learned on most everything. FreeBSD/Gentoo to coding, but most of it I didn't get to use. I'll try and see if these certs work, as having done something. I think, they will. Cert test for somethings aren't too bad now, and you can take other courses to prepare. 

Anyway, long way round but regardless, I have enough invested that I need to finish both of these. 

Thank Everyone very much.  

I'll keep this thread updated for a bit. :)

---

