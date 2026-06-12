---
title: "Hateing on KVM"
date: 2009-06-19
forum: Virtualisation
---

### Post by Inuyaga on 2009-06-19
Ok so I have been trying to use KVM for some time now and so far have gotten all of about nowhere. Now I have not posted any system specifics because I don't expect anyone to be able to help me fix the problem (I explain why later). In all honesty I don't think I really care that much and if and when I do I will spend the time to work it out my self. Basically I just want to rant about this *D!@#*@!# block of fail.

My life with KVM or lack there of.

I first met KVM while trying to install VMWare Player. Up to this point I had been using VMWare Sever 2.0 with little event and was basically happy. However I did not like the console nor did I need the VMs running all the time so why waist the cycles. So while installing I get an error - Cant install while KVM is installed. "What is this KVM thing I wonder? - I think I remember installing it a while back..." I start poking around and decide well this VM thing looks good enough Id rather use OS stuff then not. So the wedding happens and for the most part goes fairly well - I get Win XP Pro installed.

Here is where the fun begins. So I decide that since I have this Vista BIZ cd lying around I might as well install it too. Vista installs without too much trouble. The only problem is the window will NOT FIT on my screen and jumps all over the place each time I click on it. But hey since when do relationships not have quirks.

While I was installing Vista I had VC Express and the Platform SDK installer running on the XP box...

It runs out of space.

Well crap! So I start looking around for a way to resize the partition. It seems the only way is to convert my nice qcow2 images to raw, attaching them to loop devices, and doing some magic with a hex editor. And as to be expected Fails. Though by no fault of the process or linux - windows just does not like getting resized.

So by now i'm stuck with two unusable images and a lot of wasted time. I cant blame KVM for much yet, it has crashed my whole system a few times but nothing too serious yet.

After giving up on the resize route I delete the XP domain and try to start anew. I set up the new domain in the virt manager and click apply... System CrAsH! WOOOOOO. I hard restart my laptop and nothing too much has changed. For some reason my Firefox has reset all of its config but thats not hard to fix... I try following the same steps... click apply SYSTEM CRASH! WHAT THE HELL!? I do this like 4 more times! By this point my desktop looks like a large fat man rolled around in it not to mention fsck is starting to get very very mad with me. So I finally get it working once I switch disk images. I DON'T KNOW WHY THIS WORKED the disk image I was using worked fine in the beginning. Hmm maybe it was corrupted!?

So finally I get XP setting up again and I try to start my Vista VM. SYSTEM LOCKUP!

*Restarts

I open the virt manager AND ALL THE DOMAINS ARE GONE! GONE GONE GONE! I dont know why they are gone they are just GONE! So I go to recreate the new domains and guess what SYSTEM CRASH! Do this several more times and finally for somehow I get both domains set back up.

At this point I run virtsh dumpxml <domain name here> > domainname.xml and SAVE THE DOMAINS! Then I RESTART to assure the files have been written to disk before I continue.... BLOCK OF FAIL.

So I set XP back up and get all the stuff install on it. Woot! I then proceed to start installing Vista. I start the Vista vm - SYSTEM CRASH! After restarting I go to start the XP VM - BOOT FAILURE! WHYYYYYYYYY!?. So I drop that task and start back with Vista. I decided this was the best route because after setting up the XP VM I realized that it was using 100% of the cpu. Seems this is a problem with virtmanager and the no-acpi option.

So I start the Vista VM and begin installing and vista tells me it needs to shutdown to continue. I shut it down and then start it again so it can finish installing... SYSTEM CRASH! GOD JESUS D*ASD*

After restarting I go to continue to install vista and get back to the install screen and get an error... "You thought you could keep installing me!? WRONG! HAHAHAHAHAHAHAHA" You remember that part where the computer locked up before I could restart. WELL it seems Linux had not gotten around to writing the files to the disk image AND THEY ARE GONE JUST GONE! START OVER! AGAHHHHHHHHHHHHHHHHHHH!

And this leaves me where I am now - on another computer using windows. 

Lesson - KVM IS A BLOCK OF FAILLLLLLL AVOID IT! Use something else ANYTHING ELSE! AHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHhhhh....

Anyway IMHO - Kvm looks like it could eventually be a good system but right now its too buggy / unstable to work. And when something that can lock up you whole system is this unstable its best to stay away and let it corrupt other peoples computers. Seriously how hard is it to do basic sanity checks on the images you are about to execute!? If something is wrong enough to lock the system it has to be pretty friggin wrong. For now I recommend VMWare its stable and so far has never crashed my system EVER.

There are a list of issues I could raise with KVM however, since I never intend to fix them I'll not go into them. 

To thoes using KVM - Good luck!

---

### Post by bodhi.zazen on 2009-06-20
Sorry you had such a bad experience with KVM , hope you have better success with another platform.

Have your tried virtualbox ? If not I suggest you try it, it is IMO both faster and easier then VMWare.

If you wish to stay with vmware you may wish to consider server 1.x (I find server 2.x to be buggy and ironically 1.x has more features then 2.x).

The description of your problem is quite unusual, were you by chance using your physical partition rather then a virtual disk ? I can not understand why your system is locking up like that from what you are posting. Are you low on RAM ?

I would also point out, your experience was with virt-manager and virsh, both front ends for KVM and not necessarily KVM.

virt-manager and virsh are in rapid development and there is a lot of variability across versions of Ubuntu (I do not think the Ubuntu wiki has kept up on these changes).

I also have problems with virt-manager and personally I still run KVM from the command line. I used qemu years ago and kvm is similar enough it is easy.

To run kvm directly, simple :

```
kvm -m 512 -cdrom ~/ubuntu-desktop.iso -usb -usbdevice tablet
```From there you really need to read the man pages or online qemu documentation (which is both very solid and very technical).

Yes, it is a bit technical, and that is a bit of a disadvantage. But to be honest Virtualization is a technical endevor and even with vmware there are courses and certification so none of these platforms are so simple under the hood.

virt-manager is in rapid development and if you would like to see some improvements, try KVM (virt-manager) on Fedora 11. 

The other variable here is you are running Windows. KVM is probably not the best platform for windows. Running Linux guests on Linux hosts works well.

---

