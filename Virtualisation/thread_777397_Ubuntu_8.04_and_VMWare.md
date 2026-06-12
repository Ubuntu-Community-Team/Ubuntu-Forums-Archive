---
title: "Ubuntu 8.04 and VMWare"
date: 2008-05-01
forum: Virtualisation
---

### Post by Fratm on 2008-05-01
I recently installed the new Ubuntu (8.04) and so far I like it..  But
I ran into one issue.. I downloaded the latest VMWare, and downloaded
the latest any-any patch (This is requred to get it to run in ubuntu),
and got it all compiled and running all nice and happy.   So I went to
install XP Pro into a 8Gig Virtual Machine, and it seemed to be okay,
until it tried to format the virtual disk, this took FOREVER, I even
rebooted and trued the fast format option.. and it took just as long..

So I tried to move on forward.. Well it seemed any time the installer
was writing to disk it would take forever.. The progress bar would
move real slow, and things just took way to loong.. It took about an
hour to get from start of install to first reboot, and then when it
was loading the XP Pro splash screen, you know how the screen fades in
nice and smooth, and the loading progress bar zips on by.. This was
REAL REAL slow, like several seconds for each gradient of the fade in
process and the progress bar was barely moving..

Next after a couple minutes it finally gets to where it is installing
drivers and such, and the little progress bar in the lower right
barely moved.. So, I clicked into the virtual machine, and noticed
that when I moved my mouse around (USB Logitech Trackman trackball)
that it would cause the progress bar to advance, and seemed to make
the disk I/O work faster.. still not fast as I expected..  But it did
make a major difference..

After about 2 hours of this BS, I just shut the VM down and deleted
it, and tried again, thinking maybe something was screwy, and also
wondered if there was an issue between reading from the CDRom and
writing to the disk, so I made an ISO image of the CDRom and mounted
that as the CD Drive in VMWare.. Same exact results..

Anyone have any ideas why this would be happening?  I have VMWare
installed on my Ubuntu 7.10 box, and installed XP Pro from the same CD
just the other day with out ANY problems (Not pirated here, my work
has a site wide license, I can legally install the same copy on 2
machines.) the disk I/O was fast, and I'm quite happy with it..  The
only difference is that this machine is Ubunto 7.10 and the new
install in Ubuntu 8.04, oh and I think the VMWare versions are
different.. It's been so long since I installed it on the 7.10 machine
that I am not sure if I did it from the VMWare download, or if I
installed it via apt.  I'm thinking it is an apt install..   There is
no package for 8.04 for vmware anymore, so I had no choice but to
install it from the vmware's download site.

Any help on this would be greatly appreciated.  I rarely need Windows,
but I do need it for school and work at times, and my goal was to not
have to duel boot anymore.

The computer having the problem is  Dell XPS M1210,  Core2 Duo, 2Gigs
Ram, 130G HD (or 120G i cant remember) NVidie 7400Go Video card.  It
runs Linux like a champ!  it runs Windows like a champ! :)

Thanks.

-Steve

---

### Post by Fratm on 2008-05-02
Well, I gave up on this.. I did get one piece of advice, I was told that the beta version of VMWare runs perfectly, and that this issue I am seeing with the stable version is real common.

So my solution, after reading these forums was to give VirtualBox a try.. So far I like it, and it runs perfectly.

-Steve

---

### Post by fjgaude on 2008-05-02
From what I read it seems you are trying to fomat the virtual disk... that is not to be done in WinXP. You exit the VM and from within vmware you click on the options to defrag the disk. Once that is done, and you use only one core, your WinXP will be just about as fast as it is dual-boot.

---

### Post by Fratm on 2008-05-02
> **fjgaude said:**
> From what I read it seems you are trying to fomat the virtual disk... that is not to be done in WinXP. You exit the VM and from within vmware you click on the options to defrag the disk. Once that is done, and you use only one core, your WinXP will be just about as fast as it is dual-boot.


No, I do not believe this is the problem.. Because the slowdown is not only during the initial XP Formatting of the partition (It wants to do it, no matter what on a fresh install) but even after it finishes the format and tries to copy the windows system files to the partition is real slow too.

It's all cool now, I am happy with VirtualBox :) OSS to the rescue ;)

-Steve

---

### Post by The_Big_D_GFK on 2008-05-02
Hi Fratm,

I wonder if you have ever seen the following problem with installing Windows XP on a Kubuntu virtual machine using VMware server? I use the VMware Server console to create an 8 GB virtual machine. It comes out to be IDE (0,0). I then power on the virtual machine, with my Windows XP Professional disk in my CD drive. Windows setup starts, as I would expect. However, once all the drivers and other files have loaded, and the installation wants to begin, the system tells me that it cannot find a hard drive installed. Have you ever seen this problem? If so, how did you solve it? Thanks in advance for your help.



Warm regards

---

### Post by Fratm on 2008-05-02
Nope, can't I have ever run into that problem.. Sorry can't help ya with that.

-Steve

---

### Post by anukoolr on 2008-08-16
Even I had a lot of trouble installing vmware. Finally I found one thread that helped me successfully install it. I now have no issues with that. Check this out. [http://ubuntuforums.org/showthread.php?t=788169](http://ubuntuforums.org/showthread.php?t=788169).

But I am not able to install another OS in the same vmware.

Basically I am using VMware server 1.0.6 on Ubuntu 8.04. My guest OS in my VMware is win XP. I wanted to test out kubuntu and see how it works. I am trying to install it and I have successfully failed doing that. i have created a thread for that too. Here is the link.

[http://ubuntuforums.org/showthread.php?t=889720](http://ubuntuforums.org/showthread.php?t=889720)

Can anyone help me on this??

Thanks
Anukool

---

