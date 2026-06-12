---
title: "using &quot;kvm -smp&quot; option slows guest OS performance"
date: 2009-10-18
forum: Virtualisation
---

### Post by bmullan on 2009-10-18
Just to experiment I added the QEMU option "-smp N" to my KVM command that starts up my Windows 7 VM

docs say...
 
[I][INDENT]-smp n[,maxcpus=cpus][,cores=cores][,threads=threads][,sockets=sockets]
                set the number of CPUs to 'n' [default=1]             
                maxcpus= maximum number of total cpus, including      
                  offline CPUs for hotplug etc.                       
                cores= number of CPU cores on one socket              
                threads= number of threads on one CPU core            
                sockets= number of discrete sockets in the system  [/INDENT][/I]   

I used "-smp 2" but it seems that using the -smp option with any number gives significantly less performance to the Windows 7 Guest than not using the option at all?

---

