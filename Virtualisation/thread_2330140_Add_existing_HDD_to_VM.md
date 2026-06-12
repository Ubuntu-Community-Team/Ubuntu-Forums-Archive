---
title: "Add existing HDD to VM"
date: 2016-07-08
forum: Virtualisation
---

### Post by warren55 on 2016-07-08
I have a Virtualbox with Ubuntu desktop 14.04 running in windows 7.  The computer has an additional HDD with a single partition that has Ubuntu 14.04 installed but not running at this time.  I would like to access some files that are on it from the Ubuntu VM.  Thanks

---

### Post by Bucky Ball on 2016-07-08
[That]("https://www.virtualbox.org/manual/ch04.html#idm1967") oughtta get you going. But [read this first]("https://www.virtualbox.org/manual/ch04.html#additions-windows") as it is pretty much the same and you'll probably need to refer to it anyhow.

You don't want to access a physical drive exactly, rather the partitions on it, so to share partitions (folders) you might [try this]("http://askubuntu.com/questions/32990/accessing-partition-inside-virtualbox-running-ubuntu"). Although it's the other way around, might be pretty much the same and will get you started. Good luck.

I just did all this on my wife's machine a week ago; Xubuntu-core host with WinXP guest. You'll find it's all fairly straightforward once you get the guest additions in. Took me about 20-25 mins of nutting out from go to whoa to get the additions in, LAN network printer working and access to desired partitions. No WAN access required for XP! Took a bit to make sure I was only getting it on our local network and not the wider one. Ouch! But luckily, it's a virtual machine and snapshot taken. :)

---

### Post by warren55 on 2016-07-08
Bucky Ball
I'm not sure but I think the problem is that the Ubuntu physical HDD that I want to access doesn't show up in the windows 7 system so I can't share a folder/partition.

---

### Post by QDR06VV9 on 2016-07-08
I do not use windows but I have had friends that use this method of viewing Linux Files (Partitions)
[http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)
And they also create a Shared Folder (In windows 7) and copy to or from that folder as needed...As Bucky Ball shows in his links.
But I have no first hand experience with this..So read carefully!

---

### Post by warren55 on 2016-07-08
Thanks runrickus, I was just reading that page.  Will give Ext2Fsd a try

The drive shows up now in windows and I have assigned it a drive letter and can see the files.  I'm not sure how to add it to the VM.  I tried creating a shared folder in the Virtualbox setup but I must not be referring to it correctly.  Any idea what the correct syntax is?

it now shows as sf_backups in the file manager.  How do I refer to that in the CLI?

---

### Post by squirrel3 on 2016-07-08
You can try the Ext2Fsd program. It lets you mount your Linux partition so you can retrieve files.

[http://www.linuxandubuntu.com/home/how-to-access-linux-files-in-windows-when-dual-booting-linux-ubuntu-linux-mint-and-windows-10-81](http://www.linuxandubuntu.com/home/how-to-access-linux-files-in-windows-when-dual-booting-linux-ubuntu-linux-mint-and-windows-10-81)

---

### Post by QDR06VV9 on 2016-07-08
This is pretty straight forward: [http://www.howtogeek.com/187703/how-to-access-folders-on-your-host-machine-from-an-ubuntu-virtual-machine-in-virtualbox/](http://www.howtogeek.com/187703/how-to-access-folders-on-your-host-machine-from-an-ubuntu-virtual-machine-in-virtualbox/)
Give it try...I will also,  to see if i can aide you if you get stuck.
But probably tomorrow...past my bed time:D

---

### Post by squirrel3 on 2016-07-08
Also, it sounds almost as simple as using a USB stick to copy some files, then transfer them to your VM.

---

### Post by Bucky Ball on 2016-07-09
> **squirrel3 said:**
> You can try the Ext2Fsd program. It lets you mount your Linux partition so you can retrieve files.

You are a bit behind on this thread. Been there, doing that. Please read all previous posts before posting. Thanks. ;)

Also, the OP is not wanting to transfer files using a USB stick (and that would be tiresome, as you will understand once you've read the next bit). This thread is in the Virtualisation forum and they have Ubuntu as a guest running as a virtual machine inside Windows as the host. They are wanting to access partitions owned by the host with their guest. That is what we're helping with. :)

---

### Post by warren55 on 2016-07-09
the files are located at /media/sf_backups.  Thanks for the help

---

### Post by squirrel3 on 2016-07-09
> **Bucky Ball said:**
> You are a bit behind on this thread. Been there, doing that. Please read all previous posts before posting. Thanks. ;)

Also, the OP is not wanting to transfer files using a USB stick (and that would be tiresome, as you will understand once you've read the next bit). This thread is in the Virtualisation forum and they have Ubuntu as a guest running as a virtual machine inside Windows as the host. They are wanting to access partitions owned by the host with their guest. That is what we're helping with. :)

This is ok. I was merely thinking of alternatives. This IS the virtualization forum and I have used VMs before (things worked for me in the past). Best of luck.

---

### Post by MAFoElffen on 2016-07-10
@squirrel3

You mistook what he said and did not understand. What you recommended in your post was not an alternative to ... The same was already recommended as a solution previous to your initial post, and that's exactly what they did. So what you recommended was a duplicate suggestion to DuckHook's previous ... but just a bit later on ... as if you hadn't read the previous posts.

So, is that enough info for you to understand his comment now? Do not take it personal.

---

### Post by Bucky Ball on 2016-07-10
> **MAFoElffen said:**
> Do not take it personal.

+1. :)

---

