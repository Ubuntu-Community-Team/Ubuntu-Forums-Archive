---
title: "Tool for deploying multiple (+12) VM instances at once?"
date: 2023-11-29
forum: Virtualisation
---

### Post by Drone4four on 2023-11-29
What is that tool used for launching +12 bare-bone VM instances where each is a different prepackaged *nix operating system automatically deployed in their own terminal emulator simultaneously?&#8203; 

I've seen Michael Larabel over at [Phoronix]("https://www.phoronix.com/") use this tool from time-to-time featured in his articles. He uses it to host the VM's locally, not in the cloud. In the screenshot of his desktop workstation, there are at least a dozen different nix shells, each showing screenfetch/neofetch demonstrating all their specs. In contrast, Docker and K8's is for deploying containers to the cloud but Mike deploys and hosts locally I believe.

[I asked on the Phoronix forums 2 days ago]("https://www.phoronix.com/forums/forum/phoronix/general-discussion/1424585-12-shell-vm-instances-tool-that-mike-uses"). No one has replied yet. So I thought I would ask here too.

---

### Post by #&amp;thj^% on 2023-11-29
Are you thinking about Mutipass?
It's a snap package if so.

---

### Post by Drone4four on 2023-11-29
Hi **1fallen**! Thank you for your reply.

I looked into [Ubuntu Multipass]("https://multipass.run/"). That's kind of in the general direction. But Multipass is as far as I can tell is used for hosting and launching many simultaneous Ubuntu instances. In the screenshot I saw on Phoronix showed 12 different Linux distros. 

Is Multipass used for launching Ubuntu instances only? Or does it support a sprawling network of other *nix distros?

---

### Post by #&amp;thj^% on 2023-11-29
> **Drone4four said:**
> Hi **1fallen**! Thank you for your reply.

I looked into [Ubuntu Multipass]("https://multipass.run/"). That's kind of in the general direction. But Multipass is as far as I can tell is used for hosting and launching many simultaneous Ubuntu instances. In the screenshot I saw on Phoronix showed 12 different Linux distros. 

Is Multipass used for launching Ubuntu instances only? Or does it support a sprawling network of other *nix distros?

I wish I knew for sure, but by all looks "Ubuntu instances only". I could be wrong though.
Now you mention it I remember  seeing something else on Phoronix site my self (Maybe a year or so back)...If i remember it I'll post back.

---

### Post by MAFoElffen on 2023-11-29
Launching or deploying? There is a big difference between those two terms.

Launching, I just use Network Manager (see attached) I have VM's, LXC Containers, etc. running under that...

Are you talking about a recent article like this that he did on Canonical Microcloud? [https://www.phoronix.com/news/Canonical-Ubuntu-MicroCloud](https://www.phoronix.com/news/Canonical-Ubuntu-MicroCloud)

---

### Post by Drone4four on 2023-11-29
Hi **MAFoElffen**. Thank you for your comment.

You said:

> **MAFoElffen said:**
> Are you talking about a recent article like this that he did on Canonical Microcloud? [https://www.phoronix.com/news/Canonical-Ubuntu-MicroCloud](https://www.phoronix.com/news/Canonical-Ubuntu-MicroCloud)

...not quite this article. The now vague memory I have of the Phoronix article goes back longer than two weeks. I think I have seen it more than once too. The screenshot Larabel shared that I have in mind I don't think was cloud focused. So I shouldn't have mentioned 'cloud' to begin with. If I recall correctly, it looked more closely like launching (not deploying) local guest VM pre-configured easy-access images perhaps through QEMU or Xen or a wrapper thereof. I believe it may have even been IoT focused designed for small memory footprints without big GUI/DE packages installed. Just the bare-bones.

> 
Launching, I just use Network Manager (see attached) I have VM's, LXC Containers, etc. running under that...


That's an interesting screenshot. We're getting closer because your Network Manager shows VM performance metrics in a panel - - you have CentOS, OpenSolaris, PopOS, Fedora. Not only did he have have those, Michael Larabel even had FreeBSD and DragonFly BSD and more. If you could launch a single terminal emulator for each instance showing the output of `$ screenfetch`, then this might be the answer to my original inquiry.

---

### Post by MAFoElffen on 2023-11-30
So do I, among a lot of others, as well as Win OS'es, MAC OSX, VMware vSphere, React... amd64, x86, arm64, ppc64, RISC64, IBM S390X, etc.

I do a lot of testing... I beta test Win NEXT & Insiders, VMware VSphere & the Ubuntu DEV Cycles... VCenter is nice, but it is commercial.

What I like with KVM is that I can scale to a specific system's CPU capabilities, it's memory and such to replicate what the target test case needs to be. It is very flexible and adaptable.

What I do to spin up test cases, is I will setup VM templates of a machine type, say with an install of a certain Distro and run virt-sysprep on it... Then I'll clone it, and make it unique. Then do whatever to it. Takes less than a minute to clone and spin it up. Some of My VM templates are just blank machines that I clone to test the Daily install images for QA. Attach an ISO and off I go. Or I have scripts to dl and prep the pre-installed images for testing.

That technique saves me a lot of time in what I do routinely.

I've looked at VM Management "systems" and I haven't found anything that really fits all my needs. I keep looking though.

When i was working as a contractor... To deploy a companies systems, I used Fog Server. Make so many variations of images. PXE boot into it. Deploy the compressed system image. Expand the partitions to where they needed to be... Wash, rinse, repeat. I've unboxed, setup, installed OS'es (with their apps), and configured over 200 computers in less than 2 hours.

---

### Post by TheFu on 2023-11-30
I use bash to control the order and delays that multiple VMs require .  Call me old fashioned. Underneath, they are all KVM, libvirt, virsh controlled.  

For Linux Containers, I use bash, just with lxc commands instead. I know virsh can control lxc and lxc can control KVM VMs. Never bothered looking further.  There's always something new and if my current method has solved the issue, I don't quickly jump to "new".  I may need to be beaten about the head a few times before "new" gets my attention.

"New" is the enemy of "stable."  There are always people spending time on "new".

---

### Post by Drone4four on 2024-03-10
@**1fallen** , @**MAFoElffen** , @**TheFu**

I sent Mike an email and he replied and was able to successfully identify the tool! It's called Distrobox:
[LIST]
[*][https://www.phoronix.com/news/Distrobox-1.7*](https://www.phoronix.com/news/Distrobox-1.7*)
[*][https://github.com/89luca89/distrobox](https://github.com/89luca89/distrobox)
[/LIST]

---

### Post by MAFoElffen on 2024-03-10
Thank you. I was very curious about that. 

I'm going to have to check that out.

---

