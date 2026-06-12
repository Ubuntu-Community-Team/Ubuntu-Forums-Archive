---
title: "x11 graphic not rendering properly"
date: 2016-12-03
forum: Virtualisation
---

### Post by edstevens on 2016-12-03
This may seem like a "why are you posting that here?" issue but please bear with me.  I'll try to be brief. 
Running Ubuntu 16.0.4 LTS on a brand new System76 laptop. Running Cinnamon, but issue exhibits also with Unity and Gnome.
I installed Oracle Virtual Box and created a guest VM running Oracle Linux 6, 64 bit.  This is something I've done scores, if not hundreds, of times on Windows several different Windows hosts.  After the guest vm is installed and configured, I run the Oracle database installation program, which runs an x11 GUI interface.  When doing this on a Windows machine I run xMing as the x-server on the host desktop.  Of course, on a linux host, that is not necessary as the host desktop itself is x11.

Now the problem is that doing this on the Linux host, the GUI doesn't render completely.  I'm attaching two screen shots.  vboxissue_OUI_lnxhst.png shows what I'm getting.  By way of comparison, vboxissue_OUI_winhst.png shows what I get on Windows hosts .. and is what I should get.  Since both VM's were built exactly the same, I'm guessing this has to do with some font package on the host machine, and that's where I'm hoping some here might be able to help.  I've also posted on the VirtualBox forums, but so far they haven't been very helpful.

---

### Post by edstevens on 2016-12-07
I posted about this in the General forum, but after several days and no replies, I thought I'd try here.

I frequently have to connect from my laptop to a remote database server that is running Oracle Linux (derivative of RHEL).  I use either native ssh or putty to make that connection.  Once connected I execute a program that produces a GUI interface, projected back to my laptop via x11 with port forwarding.  For quite a few years I've been doing this with a Windows laptop, but have recently moved to Ubuntu.  Doing exactly the same operation, the GUI interface appears, but a lot of text is missing.  I'll attach two images, one (oracle_oui_windows.png)  showing the fully formed output on my Wndows laptop, and the other (oracle_oui_linux.png) showing the same GUI on my Ubuntu laptop.

My guess is that some fonts are missing from the ubuntu machine, but I'm rather out of my expertise at that point.

The ubuntu system is as follows:
System76 Gazelle
Ubuntu 16.04 LTS
Intel i3-6100H 2.7 GHz x 2
8gb memory
Intel Skylake Integrated Graphics

I'm typically running the Cinnamon desktop, but the issue also exhibits with Gnome and Unity.

---

### Post by slickymaster on 2016-12-07
Merged the two threads and move them to ***Virtualisation**.*

Please do not create duplicate threads, it dilutes the community&#8217;s efforts to provide support and causes confusion

---

### Post by edstevens on 2016-12-07
I normally wouldn't cross-post.  However, (1) the initial post - in Virtualization - had gone 4 days without a response, and 2) on further testing and research I'm pretty well convincded that it's not a virtualizaiton issue, but simply x-11 issue between my Ubuntu laptop and an Oracle (RedHat) Linux server, where said server is just coincidentally a VM running on the Ubuntu host.  So I thought I'd reduce the complexity of the initial question, and post to a forum space that seemed more aligned to what I feel is the root problem.

---

### Post by edstevens on 2016-12-10
ok, I've done some additional configuration and testing.  Here's the setup . . .

Two physical laptops.  For brevity, let's call them lnxhost and winhost.

Lnxhost running Ubuntu 16.04, as described earlier in the thread.
Winhost running Win 7 Home Premium, as described earlier.

On each machine, I've created a vm running under VirtualBox.  Both VMs are configured identically, running Oracle Linux 6 (same as RHEL 6).  
Each host system (winhost and lnxhost) is able to establish an ssh session on BOTH vm's. 

With that setup, the task at hand is to connect to a vm (using ssh) and execute a program that presents a GUI interface, using x11 port forwarding back to the host desktop that is running the ssh session.
Results:
At the winhost desktop, the GUI is correct and complete from ether vm.  See the file vboxissue_OUI_winhost.png, attached to my original post.
At the lnxhost desktop, the GUI is INcorrect from both vm's.  See the file vboxissue_OUI_lnxhost.png, attached to my original post.

From this I conclude the issue has nothing to do with the configuration of the vm.  It has nothing to do with the host system on which the vm is running.  All results point to something on the Ubuntu system that is rendering the GUI.  From that point I'm out of my expertise, but would strongly suspect some missing font package, but don't know what it would be.

All that said, the 'virtualization' space is probably the wrong place for this thread.  But if I were to post it in another space, it would just be another case of crossposting.

---

