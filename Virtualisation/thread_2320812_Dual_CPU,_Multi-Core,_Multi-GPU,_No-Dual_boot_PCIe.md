---
title: "Dual CPU, Multi-Core, Multi-GPU, No-Dual boot PCIe pass VM build feedback"
date: 2016-04-17
forum: Virtualisation
---

### Post by billy34 on 2016-04-17
Okay, I've read lots and lots and lots of posts regarding VM passthrough, the collection of this information has left me with a lot of questions.

I don't know if I'm insane or not so please feedback would be great!

The intent is to run a Ubuntu 16.04 build with a Windows 10 VM for gaming. I understand 16.04 isn't quite done yet but it will be by the time my motherboard finally gets here. 

So here's what I'm building, the collection of parts hasn't all come in yet but it's already been purchased:

*Motherboard*
Asus Z9PA-D8 Motherboard which I plan to fully update the bios. Confirmed that Vt-d support won't be an issue with Asus using Ubuntu.
I'll be running Dual Xeon 2670's, (8-cores each, 16 threads). In an ideal world I'd like to be able to dedicate an entire processor to the VM when running it?
(According to Asus I'll be able to run these slightly overclocked in a way that will force turbo always on)

*Ram*
I have 64gb (8x8gb) ECC Registered Quad Channel DDR3 @ 1600 (Matches processor specs). The only thing special I did for the ram is because of putting it in this board I purchased heat spreaders for the chips because I know how Asus boards are with OC. The plan here is to give 32gb to the VM but not sure, can I dedicate the specific 32gb tied to the quad channel on the processor I want to give it? Can I make these sort of specific dedications?

*Graphics*
For GPU's I'll be running an EVGA 960 SC 4GB (I can still take back to Fry's and change this) and an XFX Radeon HD 6990 4GB
I don't like AMD Linux drivers so I plan to use the 960 as my Ubuntu card and pass the 6990 to Windows.
The theory is this will make it easier to blacklist the AMD drivers?
The 6990 however is a dual GPU crossfire card and has only ever been used in Windows, not sure if this presents any issues?

*Audio*
With all the hardware I'm trying to dedicate when using the VM, what about sound? I've got a pretty good PCIe sound card, will that work fine for both Windows and Ubuntu or will I need to dedicate sound too? If so, would dedicating a USB sound card work? If I need to do this the thought would be to tie the audio output of the USB card into the input of the PCIe card and making it always playback that audio so I won't need another second set of speakers.

*Storage*
Right now I've got a ton of drives, trying to figure the best configuration to use for them...

I've got a 512gb Toshiba Q series pro SSD and a 480gb PNY XLRE SSD. I planned to use One to boot Ubuntu and to have one used as dedicated for the VM.
I've got my old 240gb OCZ Agility 3 SSD I'd like to use as a shared drive so I can exchange any files I need between Windows and Ubuntu.
(I've noticed some crazy permission errors like files vanishing with NTFS, is there a better format for shared storage?)
I do have a 960gb OCZ Trion 100 that I intended to use in this build but I heard the performance for it wasn't so great so right now it's in my tablet.

Now I have another storage concern. I've been using a 600gb Raptor as a "game only" drive in a Windows build but it's out of space, I need bigger. Should I be dedicating a 2nd HDD for Windows? If so, what should I be dedicating that won't turn into a bottleneck? I've read a lot about SSD's performance taking a hit when filling up and my 600gb Raptor is full. I thought about buying 4x 1TB Toshiba 7.2k SAS drives (I can get all 4 for $120) and running them in Raid 5 but I've read this is worse than 1 SSD? Not even sure how the VM would treat this?

I've got a couple of 3TB WD greens, a 2TB blue I tried sharing on this computer but I'm having issues with Windows and Ubuntu not sharing well on NTFS, I'd love to know a file system they can share nicely and not have permission / ownership lockouts?

My end goal for storage is to have a good OS SSD for both Ubuntu and Windows, a good storage solution for games that I don't care how well the two share files. I don't plan to play my Windows games on Ubuntu or vice versa. NTFS seems fine for this because it does seem to let me store both on the same drive but not let each other see them. (Will this cause any long term problems?) I'd like to have a "universal transfer" drive in case one system can't read a file I need on the other so I can put it in neutral space. The rest of my storage now that I think about it I'd prefer to be whatever is best for Ubuntu. I'd rather not have M$ scanning, spying and reading everything I have on both systems. I also have a drop box account I share between the two, it's not "huge" but I've collected some decent used space and figured I should put this on the 240g SSD? It's really important this works well with Windows and Ubuntu but I'd rather not have the same space duplicated if it's possible to avoid? An example of this is that there is game development software I use that's Windows only but I create/edit the graphics, audio, and video within Ubuntu. The development software needs ready access to the files and sometimes I edit them "on the fly" while I'm testing. This is why I use Dropbox so I can edit from whatever computer I happen to be on and test as easily. Right now the only delay is "sync" for dropbox, it would be GREAT if locally they were the same file so I didn't have that delay. I've been considering trading off Dropbox for a WD Mycloud locally but I'm undecided. Waiting for a blowout deal on a 4TB+ one before I take the plunge.

*Networking*
I'd like both to share a network. Despite having multiple onboard lans I want to be able to use Ubuntu to watch what the VM is transmitting so I can intercept M$ spyware on the VM. If possible I also would like to be able to share the VM. To have my computer do the power to run it locally and access it from other computers on my network. For example I have a Dell Inspiron 13, 7000 2-in-1 tablet I often use around the house (this build computer is in my shop). I'd like to be able to install Ubuntu on that but access the VM if I need to get some work done from inside the house (it's on the same network). It would be amazing if I could even use it to carry the load for games so I could play them on a networked device? 

I know this may seem insane to some people but I do a LOT with my computer and there are things it's always doing all the time. My home security cameras use my computer for a server to my mobile app. I buy all my movies digitally and my PC acts as a video server for 5 smart TV's in my house. I do video and audio editing, game developing, and have massive amounts of stored data. I have tons of concerns when it comes to M$ and privacy. I don't like the idea of a company scanning my computer and using my data for commercial purposes when I use my computer to develop commercial software. I also do CAD work and am attempting to transition into FreeCAD. Not only do I develop Windows games, I play them, so I don't want to give up my gaming. Keep in mind I'm not a crazy gamer that expects my computer to play the best games on max settings at amazing FPS. However if I want to play an MMO at medium settings I still want a decent frame rate. I convert a lot of people to Linux distros from Windows. I'm a tech and it would be a lot easier for me to convince customers they don't need Windows as an OS if I didn't have to struggle with dual booting or multiple machines for various jobs. I'd like to switch every computer I have to Ubuntu but that's all riding on my success with this new machine.

I know this is a lot, there's so many questions and may be various answers. I am okay with and would like opinion based feedback too, hopefully I can get that without mods closing the thread. My situation is different from most average users and I don't expect there's a lot of people out there that can answer many of my questions so on that note even ideas to try out for myself are more than welcome to me.

Thank you in advance for any feedback you can give.

Edit: I'm currently using Ubuntu 14.04, I am perfectly Okay with building upon Ubuntu 14.04 and later upgrading to 16.04 after any changes that would impact this build have been figured out. Because 16.04 isn't even released yet I am pretty much expecting 14.04 feedback which is fine with me.

---

### Post by KillerKelvUK on 2016-04-18
Hey billy, that's one mammoth post!

*Motherboard*
You can define the architecture of the vCPU assignment i.e. socket, core and thread and you can also pin specific physical CPU cores to the guest.

*RAM*
I'm not aware of a way to select the specific RAM/Channels as you've asked, maybe something in the NUMA stack?  I'd recommend you also consider memory Hugepages for guest optimization.

*Graphics*
Blacklisting either the nouveau or radeon modules will likely be a requirement so you can accurately trap the hardware to the vfio-pci module at host boot, not really seeing how your preference of host GFX makes a dint here unless I'm not understanding you?  I'd be more concerned over guest driver installation, if you go nvidia you'll need to apply the guest modifications to hide KVM which to be fair is pretty simple stuff.  I've no experience with radeon cards although I recent thread here suggested the AMD drivers or specifically the audio portion of the drivers may not function correctly...I'd suggest you research this a little further.

*Audio*
There maybe some horrible way to use a virtual sound card and route the audio back through the audio backend on your host and have a combined host/guest audio output...I suspect this (if possible) would be horrible and a cheap/nasty fudge in comparison to the money you've obviously laid out for this rig.  Regards your PCIe card...you can't have this working for both host and guest at the same time so dedication is your only real option in my opinion...you could go the USB audio route, considered this myself but USB assignment is still buggy code.  If you have the spare PCI slots I'd dedicated a card for guest...that said I actually assign (post guest boot) a USB bluetooth adapter and use the A2DP profile for sound streaming to 
my headcans :-)

*Storage*
Dude you really need to get this together...how many different drives and options!  For me I've put a LVM across 2 Sandisk SSD's and created my storage pool on top of that so all guest OS's run out of qcow2's from here, I've then got 4x 4TB NAS drives raided from the host (R5)...another storage pool carved out here where I run separate vHDD's from for games installation.  Unless your disk IO workloads are massive in general you shouldn't get too much bother from this for games play within the guest.  You could map a disk directly into the guest i.e. no host use of the disk at all...you could passthrough a raid controller and let windows run the disks...for games however I'd suggest this is just overkill.  And regards wanting a shared drive for exchange between host/guest...just use a file server on the host i.e. a samba server...nothing fancy then needed in Windows just a mapped drive/share.

*Networking*
Unless I'm missing something here you are simply looking for a network bridge so your guests are assigned an IP from the same subnet your physical devices operate from i.e. same DHCP server etc.  This type of network is pretty much standard for kvm/qemu's...in fact the ubuntu installation scripts for KVM create this for you automatically using the bridge-utils package.  This way you could then, for example, run Steam Streaming from within your Windows guest to a Steam client elsewhere on the same network...I do the reverse of this using my Xbox One i.e. use the Xbox app in my Windows guest and steam my Xbox games into it all on my home network.

Hope the above helps.

---

### Post by MAFoElffen on 2016-04-18
16.04 should be feature locked at any moment. It's release is the 22nd (this Friday).

Networking<-- One NIC is used for the Host. Can do a Host & NAT on the same card. If you want to bridge a VM Net to the same network that the host is on, then that requires another NIC. That is what I do with my VM Hosts.

You wanted it all, so--

My latest gamer is dual Opteron 6386 SE's (16 core CPU's) with GTX 980ti's. I haven't needed to pin cores. VM and game Installs are fast. Witcher 3 pegs my son's gamer on startup (his= high-end i7 with SLI 980ti's). Mine just flies. No notice. 

For Local disk: Linux I do LVM. Windows I do storage spaces. For Shared storage I have One server as a storage Manager with Fiber attached storage. That is what I attached most Virtual Host Server to via Fiber.. My Gamer is just for my own sanity release.

What I did need it was lots fast disk and lots of USB ports!!!

Here goes. I "did" passthrough. There was lag. I expected that from connecting to a VM... (Even with fiber to my VM Hosts. Even with being the VM Host.) But it is SO much faster doing a dual boot (or native) and bringing it up native. So I undid the pass through and reconfigured it.

---

