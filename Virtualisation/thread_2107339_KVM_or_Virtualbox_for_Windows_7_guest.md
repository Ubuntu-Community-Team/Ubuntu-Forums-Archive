---
title: "KVM or Virtualbox for Windows 7 guest??"
date: 2013-01-21
forum: Virtualisation
---

### Post by daKoolaid on 2013-01-21
I want full internet access and preferably USB printing too so I know I need to use the Vbox from Oracle directly and not the Ubuntu repos.
 
But what difference in performance would I see between the two? I've used Virtualbox a lot so I know how to set it up well, but KVM I've only tried a few times. Can the screen resolution go beyond 1024x768 or whatever it is? 
 
What benefit is there to having KVM be part of the kernel? KVM seems like it's a lot more difficult to set up. The host will be 12.04.

---

### Post by archery on 2013-01-21
I can't fault Virtualbox with guest additions installed (for the features you want), it allowed me to make the switch from dual booting. I used it after reading a review in linux journal where virtualbox came out on top:

[http://www.linuxjournal.com/magazine/virtualization-shootout-vmware-server-vs-virutalbox-vs-kvm?page=0,2](http://www.linuxjournal.com/magazine/virtualization-shootout-vmware-server-vs-virutalbox-vs-kvm?page=0,2)

It's a little out of date now, granted. I guess for some users the lack of GNU GPL license for Vbox (with the extension pack) might be an issue unlike KVM. I'd like to hear the opinions of users of other solutions also.

---

### Post by archery on 2013-01-21
Just seen this:

[http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

That should answer a few of your queries (and mine).

---

### Post by daKoolaid on 2013-01-21
Thanks for the links guys.
 
From what I gather so far Virtualbox PUEL will be my best option. It seems the most polished for wide range of desktop use. KVM seems more like something you runa mail server in or something like that.
 
I also want to share files to desktop between host and guest and it seems KVM needs something like Samba or SSH for this to happen. I suppose that would also mean the guest must be in bridged mode, too. 
 
Any more input will be great.

---

### Post by Paddy Landau on 2013-01-22
Virtual Box directly from the Oracle website, with Guest Additions installed, will do as you want. The Guest Additions will allow you to run the guest in full screen, so you can have it running on one desktop by itself; very useful and easy to use.

Alternatively, you can run it in seamless mode, so It integrates into your host.

Sharing files and the clipboard are both enabled with Guest Additions (you must enable them in the settings).

Drag-and-drop between host and guest is a new feature; I'm not sure if it's working yet.

---

### Post by heiko_s on 2013-01-31
Depending on what you want to achieve, Xen might be another option. It's a bit more challenging than VirtualBox, but has quite good documentation.

Last not least, Xen offers good performance and lots of options. One of which is VGA passthrough to give Windows 7 direct access to a dedicated graphics card. This is what I do and it works nicely. It requires certain hardware features, though.

So if you're looking for near-native Windows 7 performance, particularly graphics, you may want to give it a try. Here two links that may help:
[http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine]("http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine") - it's written for Fedora, but gives a good overview and has lots of info in the long thread.
[http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013") - written for Linux Mint (an Ubuntu derivative) and should be easy to do in Ubuntu 12.04 and 12.10.

---

### Post by meteorrock on 2013-01-31
Depends if OP is tech savy. Xen is the fastest but the hardest to get up and operational. Its a bare "hypervisor," meaning ALL of your OSes will go through it, even your Host OS. 

I am using VMware here, if you got good specs on your battlestation it should work fine. All depends on your computer specs and how tech savy you are. VMware supports drag and dropping of files between the host and the guest OS, that is why I went with that choice. Whether your computer is a 32 bit or 64 bit makes a difference.

~~~~~~~~~~~~~~~

If you got an older computer, using 32 bit, VMware might be a better choice for you. If you are tech savy and do not want ANY sort of noticeable lag on your guest OS, and got decent hardware specs on your comp along with 64 bit, then go with Xen. If you got a midrange computer and know how to build an audio module in case of audio problems with your soundcard, you might give that Oracle virtualbox a try. Don't know much about KVM. 

Virtualbox has had audio issues using the included pulse audio module for it, it has been problematic for some users using even a year old audio card. I tried that hypervisor first and never could get audio to work right through it from my host OS. So keep that in mind. You have to fiddle around building an ASLA audio module on that hypervisor to get sound up if you have sound issues through Virtualbox.

~~~~~~~~~~~~~~~~~~~~~~~~`

Don't forget on some computers the processor can handle virtualization through changes in the BIOS for a speed boost on your hypervisor. Mine is like that. Some sort of AMD-v type setting for AMD processors and VT-D for intel processors. So check on that. Mine uses AMD-v as its an AMD processor.

---

### Post by heiko_s on 2013-02-01
@meteorrock: The OP mentioned KVM as an option, which is - in my opinion - not easier compared to Xen. KVM would probably be easier to setup if the documentation was clearer and more up-to-date.

KVM seems to offer less options, compared to Xen. Xen, on the other hand, has perhaps some too many options. I believe the Xen developers have recognized this and starting with Xen 4.2 they have streamlined a lot of stuff and focused on the xl toolstack. Unfortunately Ubuntu 12.10 still ships with Xen 4.1.3.

If the OP feels secure enough to takle KVM, it is my opinion that Xen would offer a good option. This is particularly true if the OP likes to squeeze out maximum performance from the Windows guest (or Linux guest).

Unfortunately some bad publicity and rumours about Xen's performance are flooding the web. There have been some benchmarks comparing Xen with KVM where KVM took the lead, for example those published at Phoronix. Some people have already pointed out the flaws of these benchmarks, but these benchmarks are still on the web unaltered, without any note to inform the readers about the limitations of the benchmarks (I'm putting it mildly).

About a year ago I was in a similar situation to the OP where I had to choose between virtualization options. I loved the ease and familiarity of VirtualBox (and its excellent documentation!), but also knew its limitations which, in the end, led me to look for alternatives. I even looked at commercial options such as Parallel Workstation and VMware. Initially KVM became my favorite, probably because of the reports on some benchmarking sites and other, perhaps biased information. Fortunately I soon discovered that the KVM documentation was a mess and that some of the features I was looking for either didn't exist, were in an experimental state, or nobody ever succeeded using them. Today I'm extremely happy with having chosen Xen, but it wasn't an easy start.

But then, KVM is evolving rapidly. On the performance side it seems to be comparable with Xen, though I still have to see proper benchmark comparisons where Xen is set up for optimal performance (this is not that difficult and the Xen documentation gives clear guidelines on how to achieve it). Perhaps one day I'm going to install KVM and give it a run to compare it with Xen.

Here the stuff I would be looking for under KVM:
[http://tavi-tech.blogspot.co.il/2012/05/vga-passthrough-kvm-fedora-17-and.html]("http://tavi-tech.blogspot.co.il/2012/05/vga-passthrough-kvm-fedora-17-and.html")
[http://www.linux-kvm.org/page/Windows7Install]("http://www.linux-kvm.org/page/Windows7Install")

---

