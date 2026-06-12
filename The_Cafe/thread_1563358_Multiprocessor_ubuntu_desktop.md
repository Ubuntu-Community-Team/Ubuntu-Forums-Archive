---
title: "Multiprocessor ubuntu desktop"
date: 2010-08-29
forum: The Cafe
---

### Post by GanShun on 2010-08-29
I was wondering if it would be possible to do this, and would like to bounce ideas off you people:

1 Desktop, 1 RAID disk array at raid level 0
multiple motherboards and processors, each with their own ram, 512 mb for example.

install ubuntu on the raid array, and have all the processors boot up from the same raid array at startup,

Use ssh to pass processes between processors, so for example, if i startup openoffice writer, it may be running on processor 1 using ssh and X forwarding back to the main board that interfaces with all the peripherals, and if i start another process, it will run on another processor that has less load. However, everything should be automated, i.e you dont have to choose which processor to run the process on. However everything should be running on the same filesystem so as to avoid having to duplicate data.

Basically, the idea is to simulate a multiprocessor system with ssh and X forwarding.

Its not for a server though, just want it for a home desktop so it should be able to run all programs in this manner, rather than just apache and php and stuff. 

For simplicity's sake, assume all models of processors and motherboards are identical, and they have a simple internal intel graphics card built in on each motherboard

oh yeah, and the raid array should probably be a network drive. so that all motherboards can interface it. They must be able to boot from the network drive. I suppose its fine if its a not a raid level 0, but this may slow down the system when multiple processors are trying to write to it.

Any ideas?

---

### Post by toupeiro on 2010-08-29
[B]Answer 1:
[/B]

get a multi-core CPU or a dual-socket motherboard, that is if you are having some sort of a problem with core-major multi-processing... (Because, if you are running dual or quad core CPU's, linux and windows are already load balancing across your cores for system operations and user operations so long as the software is capable of doing so.)  using programs like top or gnome-system-monitor will prove it to you. :)

[B]Answer 2:
[/B]
(which more directly focuses on your technical approach versus an alternative)

The problem is you are talking about CPU cycle and potentially memory page sharing across desktops.  You need more than ssh and X forwarding to pull this off.  First lets start on your terminology:

2 motherboards != one desktop

Because you are wanting to span motherboards, you need something that can share IO between them.  Whether you are doing this in one desktop case, or multiple, this is considered cluster computing.  Ideally, you want a path that can run at the frequency of the system bus between your CPU and RAM, but that is generally out of the average hobbiest's budget.

I suggest you look at projects like Beowulf and OpenPBS.

A form of this is also done, in Virtualization, VMWare vSphere has something called  VMWareFT the does the equivalent of "VM-SystemRAID", basically mirroring the total state of a given virtual machine on another physical machine.  Though this is to provide High Availability, not load balancing.  Load balancing is done by clustering multiple vmware nodes with a tolerance threshold where it will move the VM in its running state to a node that is being less utilized.  This is called Vmware DRS.

None of these virtualization options are free.

[B]Storage:

[/B]Your storage needs are easy.  
[http://en.wikipedia.org/wiki/FreeNAS](http://en.wikipedia.org/wiki/FreeNAS)
[http://www.nexenta.com/corp/free-trial-download?gclid=CJzbm9iE3qMCFRv4iAodrSQ-fA](http://www.nexenta.com/corp/free-trial-download?gclid=CJzbm9iE3qMCFRv4iAodrSQ-fA)

I was reading on slashdot the other day that anytime now there will be a native linux port of ZFS.  This is probably the best Filesystem you can freely use for inexpensive NAS IMO.  With OpenSolaris in very shaky ground, if you delve into a Nexenta/OpenSolaris solution for NAS, you may be rebuilding it at some point later.  FreeNAS and Nexenta both support iSCSI which would give you the ability to network boot off your NAS.  OpenFiler is another one that gives you a block layer which allows things like point-in-time snapshots, similar to what ZFS will give you, and more enterprise tier offerings like Netapp.

---

### Post by GanShun on 2010-08-29
Hmm, what if lets say i just want to take some load off my main cpu? assume that i have 1 cpu that has all the normal IO, but i choose to run openoffice for example on another processor. Since this can already be done using ssh with X forwarding. The other processors dont need to have their own IO right? most of the processes that are critical to the main cpu will be left there, but for the rest of the applications, ideally i should be able to run them on another processor right? So not all processes will be passed across.

something like this: when i click to play gnome-sudoku, instead of running it on the original cpu, have it do something like ssh -X cpu@com1 gnome-sudoku

---

### Post by mips on 2010-08-29
Have a look at Pacemaker but I have no idea if it does what you want.

---

### Post by ssam on 2010-08-29
probably possible. one motherboard connected to a monitor and acting as an [X terminal]("http://en.wikipedia.org/wiki/X_terminal"), the others acting as application servers, and some sort of load balancing.

but it will be slow. you are making each graphical action go through network. you loose direct rendering, futher slowing down drawing to screen.

applications will be stuck on the system they launched on. so if you start 10 apps on the 4 motherboards, and then are making heavy use of 2 that happen to be on the same board. unless you find a method to move a running application from one system to another. there is work on this in virtualisation, but to move an app would need to freeze it, and ship all its memory (hundreds of MB) over a network.

use to much power. 4 single core systems will use a lot more power than 1 quad core.

---

### Post by albandy on 2010-08-29
You can't run normal applications efficiently in a clusterized environment. You need aplications that uses mpi or pvm messages or you need something like openmosix.

Take a look at [http://www.rocksclusters.org/](http://www.rocksclusters.org/)

---

### Post by GanShun on 2010-08-29
The problem with MPI is that the program itself must be coded using mpi. Most desktop applications aren't. I understand the problem with power, as well as the network lag, but the thing is that if each of the servers are low end servers, i.e. old salvaged parts XD, it wont really be the network slowing it down. It'll still be slow though. One problem is making the shortcuts run through ssh instead of directly running it on the main cpu. Is there a way to make all programs pass to a shell script first instead of running directly on a computer? like when i click openoffice writer, instead of directly calling soffice -writer, have it call to a shell script and pass in soffice -writer as a string or something? This way one wouldn't have to manually run each program through a terminal whenever you need it, and it would work for all newly installed programs as well.

As for pacemaker, could you link me a guide or something? all i get on google searches is the heartbeat monitor XD thanks alot

---

### Post by albandy on 2010-08-29
> **GanShun said:**
> The problem with MPI is that the program itself must be coded using mpi. Most desktop applications aren't. I understand the problem with power, as well as the network lag, but the thing is that if each of the servers are low end servers, i.e. old salvaged parts XD, it wont really be the network slowing it down. It'll still be slow though. One problem is making the shortcuts run through ssh instead of directly running it on the main cpu. Is there a way to make all programs pass to a shell script first instead of running directly on a computer? like when i click openoffice writer, instead of directly calling soffice -writer, have it call to a shell script and pass in soffice -writer as a string or something? This way one wouldn't have to manually run each program through a terminal whenever you need it, and it would work for all newly installed programs as well

ssh -X user@domain /bin/application

you can add your user ssh public rsa key to other hosts in order to bypass the password

---

### Post by GanShun on 2010-08-29
erm i already know that. Its just how do i configure all my shortcuts to do that? unless i make new shortcuts that run that specific shell script, but i'd rather not have to create a new shortcut for every single application i install.

---

### Post by ssam on 2010-08-29
the menus are generated from the .desktop files for each app that live in /usr/share/applications/
eg
/usr/share/applications/openoffice.org-writer.desktop
you need to modify the "Exec=" line in each (you could write a script to do this)

---

### Post by GanShun on 2010-08-29
Awesome! will try it when i get home tonight, but it will probably take quite awhile. Thanks a lot for all your help! 

on another note, i still have no idea how to make multiple cpus boot from the same hard disk at the same time. I'll probably try out the Diskless Booting Howto, but will setting up a DHCP server mess with my current internet connection? I already have a DHCP router, and i'm wondering how having 2 DHCP servers would conflict or not conflict. though i suppose that it would be possible to have them assign different sets of IP...

---

### Post by GanShun on 2010-08-31
Heres an update:

I'm currently trying to find all the load averages over the past minute for all the ssh hosts, but i keep having problems
Heres my bash script as of now.

> #!/bin/bash
#counter for while loop
i=1
#reads in all the ssh servers from a file, format is in user@blah separated by newlines and ssh is working through passwordless login
cat /home/ganshun/bin/hosts | while read line;
do
    #For each server, run a command to find the uptime and extract the load average and store it in an array
    loadavg[$i]=`ssh $line "uptime | grep -o 'load average: [0-9].[0-9][0-9]' | grep -o '[0-9].[0-9][0-9]'"`
    echo ${loadavg[$i]}
    echo ${loadavg[1]}
    #increment the counter
    i=`expr $i + 1`
done
echo ${loadavg[1]}
Tt takes awhile to ssh everything, is there a way to parallelize it, i.e. use a fork command to have it ssh all the severs at the same time and then wait for a reply? and store the load average in its corresponding array? i tried putting an & behind the ssh line and having a wait ${!} immediately after it, but the array is now blank.

Thank you for all your help XD

---

