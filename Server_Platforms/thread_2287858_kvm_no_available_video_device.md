---
title: "kvm no available video device?"
date: 2015-07-22
forum: Server Platforms
---

### Post by Higgins909 on 2015-07-22
Fresh install of a minimum server with the packages virtual host machine and open ssh.
This happens on either ssh or logging in directly.
```

admin-ben@Langweiler:~$ sudo kvm
[sudo] password for admin-ben:
Could not initialize SDL(No available video device) - exiting
admin-ben@Langweiler:~$

```

What do I need to install? (i'm guessing not selecting basic ubuntu server package left some stuff out)
I just want it to run really light, as I'm going to have 3 VM running on it. (limited ram)

Thanks,
    Higgins909

---

### Post by TheFu on 2015-07-22
virsh, libvirt (might be libvirtd), qemu-kvm - almost forgot bridge-utils.

Of course, this assumes VT-x support in the CPU/BIOS.
Then you virsh locally to create VMs.

Or from any other Linux workstation running X/Windows and ssh, you can install virt-manager + libvirt and create VMs with a nice GUI. I assume you don't want any GUI running on the KVM-host - good.  virt-manager is a nice GUI similar to virtualbox or VMware Player/Workstation, except that with libvirt, we gain both local and remote control over VMs.

BTW - you cannot use SDL as the graphics driver on a server not running a GUI.  You should choose VNC or VGA for now and consider using spice if higher performance is needed but security isn't a concern.  For the remote connections, choose qemu+ssh as the connection type.  On both systems, have your normal userid in the libvirtd group - no need to ever use root/sudo for virtualization.

Also, manually configure the linux bridge - the built-in bridges created by libvirt just aren't as stable. I don't know why.

To get the best performance, with the least hassle, [http://blog.jdpfu.com/2012/07/30/improving-kvm-performance](http://blog.jdpfu.com/2012/07/30/improving-kvm-performance) - if you are in a business and need the greatest possible performance, talk to the HW vendors - especially about storage and NIC passthru using VT-d.

Hope this helps.

How limited is the RAM and what guests do you plan to run - what is the workload for each?  Basically, you should leave about a Gig of RAM just for the hostOS to manage the VMs.  Graphical guests use more resources than pure servers too.  For servers, avoid using the virtual console logins - always use ssh connections whenever possible.

---

### Post by Higgins909 on 2015-07-22
I'm totally new to setting up a virtual host on a ubuntu server.
I've only ever used oracle VM virtualbox.
I've got a total of 4gb and planned to have 1 virtual server for each thing.  One for proxy, another for samba, and another for ts3 + maybe game servers.
I was also hoping that I could have multi virtual hdd on real multi hdd.
example: I have a 80gb and a 200gb.  I want to have a 50gb squid cache on each one and was wanting to use virtual drives? so I could back just that drive file up and move it around to another VM.
I need to get my VM samba up and make a Vdrive and then put my cache files on it and then transfer that Vdrive to my squid VM.  Thats the idea atleast.
I was also hoping I'm able to limit how much cpu an what cores of the real cpu they can use? I wanted to have proxy and samba both on core 1 or maybe 1 + 2 and then use the rest for ts3/game.

This is a bit confusing to me, but for now I need to install those 4 programs?
I remember seeing something in my bios about virtualisation in the cpu menu... its allways been on.
Both of these virt-manager + libvirt are windows compatible? and what version of libvirt to get as there is ftp and http or maybe thats just where its being downloaded from?

---

### Post by Higgins909 on 2015-07-23
I think I got it now, with Xming, putty and virt-manager installed on the hosting server.
I like to normally use MTputty but didn't know how to get the x11 forwarding thing to work on it.
I'm not quite sure how adding different Vdrive in different locations on the host will work out.

It seemed I had most of those packages but I did end up installing libvirt.bin for the heck of it.
Also no idea if the VM server will startup when host restarts.

---

### Post by TheFu on 2015-07-23
Nothing I said works with Windows.  A "workstation" is Linux/Unix.  You didn't mention Windows, so I didn't assume it. Sorry  If you don't want bloat, but still run Windows, you have a different issue. ;)  virt-manager + libvirt do not run on Windows, to my knowledge. They are installed through the normal package manager process. I have them on workstations to control multiple VM servers. I do not use these to access VM clients. If you are this new, [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) and know that you have a very steep learning curve to reset expectations and gain the knowledge to do the stuff you want.  It will be hard AND fun.

For a squid proxy 80G is complete overkill unless you are running an ISP or college network.  I've run a squid proxy on just 384MB of RAM for the house and 2G of cache storage. It worked well.

Don't think I'd virtualize any storage servers - sure, people do it, but I disagree about that - at least in a home environment. At work, with PCI passthru - that's a different question completely and introduces some maintenance nightmares which are best avoided. For partition/storage passthru, you'll need VT-d and a dedicated controller card. I suppose people use LVM lvs for a single VM too - that could work.

Can't help with any gaming stuff, sorry. Haven't run a TF server since 2000-ish.  My servers do email, project management, wikis, remote desktops, media centers, CRM, ... 

I've never heard of a "Vdrive" - sorry.

Of course, you can control which CPUs and how many timeslices each VM gets, provided you have the correct hardware for that. Not all CPUs support it equally. [NUMA pinning]("http://redhatstackblog.redhat.com/2015/05/05/cpu-pinning-and-numa-topology-awareness-in-openstack-compute/"), for example is for server CPUs/MBs.

BTW - X/Windows doesn't have any security, so using Xming as an X/Server probably isn't the best idea. I'd rather see you setup x2go on the server (use their PPA) and use the x2go client from Windows (they have a SETUP.exe - be certain to get the fonts packages too).  Of course, you can do whatever you want and there are 5 other ways to solve this.

If you want a VM to start at VM host boot, there is a setting on the "boot" tab in virt-manager for each VM.  Or you can add the setting using **virsh edit** to each VM.

---

### Post by Higgins909 on 2015-07-23
I did virsh autostart hostname and it worked, but now I want to turn it off, as I'm trying to troubleshoot.
I shut it down last night as I didn't have anything that needed to run overnight.  This morning when tying to use xmin and x11 with putty, it would work but every time I -
would virt-manager it would popup
```

admin-ben@Langweiler:~$ virt-manager
admin-ben@Langweiler:~$
** (virt-manager:1156): WARNING **: Couldn't connect to accessibility bus: Faile                                                                                                                     d to connect to socket /tmp/dbus-EmcqWWUZtT: Connection refused
^C

```
I think its done this from the start but it used to work.  When I try to open a VM thought it, xming windows close out.
I also noticed something similar to this picture when starting up the VM manually, but this image is right after host startup with VM autostart. (not best quality)

[IMG]http://s17.postimg.org/iqjhg6s0f/20150723_154124.jpg[/IMG]

I can still reach the VM servers through ssh.
I make use of that squid cache as its mainly long term cache.  I used it to cache some huge game files and then build my new computer and seen download speeds x4 my real speed.
(the drives are slow could be faster)

All tho, I got a thread going on how I only know how to setup part of the squid config.
By Vdrive I meant the VM virtual drive files that seems to be qcow2 format in /var/lib/libvirt/images of the host
I know how to setup my game servers, wont need you're help there.
Just having issues with KVM setup and Squid setup.  I had a basic setup of samba going on my desktop with oracle but because I'm having issues with KVM its holding me back from adding my other Vdrives to my new host server... to start config samba. (Just focus on KVM related for this thread)

I'm on windows 7 64bit home premium and the server + VM servers are ubuntu server 64bit 15.04

---

### Post by Higgins909 on 2015-07-23
I got X2go and guess it works as I can login just like ssh... but how do I manage my virtual servers?  Do I still need virt-manager?  what is the proper/full way to remove it?  I've never known how to do that and that was a struggle with trying to remove samba about a month ago.  I tried to run virt-manager though it and it just disconnects. maybe a port needs to be allowed though the server firewall? (I'm doing this over lan)

---

### Post by Higgins909 on 2015-07-24
I guess I got everything almost running now.  I made 1 more VM and got my ts3 server up.
I  just need a better way to manage them.  Xming stopped working so I  somehow ended up using x2go and putty and logging in on both and typing  virt-manager on the putty session and it worked...
really confused on why that even worked.
Got all my Vdrives in the correct real hdd locations... sounds confusing.
One  thing I noticed with the minimal virtual machine install of ubuntu  server 15.04 is that there is no firewall... every port is open.   Not  sure if it depends on the host firewall or what.  I'm also using the  bridge from the virt-manager as that was easiest, will keep it like so  till I run into a problem.

---

### Post by TheFu on 2015-07-24
There are a few different ways to have a remote desktop or a remote GUI window or remote access. This can be confusing. I've tried to explain those options [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) .  

virt-manager is just a GUI program like any other GUI tool, except that it has VNC+ssh connections built-in to access VM consoles.  You can use x2go through ssh, to virt-manager, then use vnc through ssh from that other machine to control VMs.  IMHO, virt-manager should only be used when "console access" is required. The VNC+ssh tunnel it provides is just too slow for anything except console use.  

Physical or virtual servers should be managed through ssh, IMHO. Others disagree.  The GUI is **not** the OS.

Firewall - if there isn't anything listening on a port, then a firewall isn't needed. Can't hack it if there isn't any listener.

---

