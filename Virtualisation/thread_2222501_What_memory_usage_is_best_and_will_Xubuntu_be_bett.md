---
title: "What memory usage is best and will Xubuntu be better ?"
date: 2014-05-06
forum: Virtualisation
---

### Post by hebdave on 2014-05-06
Hi I am currently running Ubuntu on a 100 Gb hard disk and added vitualbox to this as well to run with Ubuntu also. It is rather slow. My processor is only dual core and I had to use 100 GB for Ubuntu as windows takes up the rest of the hard disk. I allocated 40 Gb hard disk space to Ubuntu in vitualbox and have no other virtual operating systems as well. 

I cannot remember exactly if the memory is the issue in making it faster and whether the disk size determines memory availability.

To cut a long storey short will Ubuntu or Xubuntu (the latter for old computers) be best ? And also - What would be the sizes you'd recommend for virtual hard disk and memory allocation. 

I am not that techie minded but have enough aptitude to do things with advice on the subject. Many thanks. :)

---

### Post by CharlesA on 2014-05-06
I run Ubuntu on a 25GB drive with 1 GB of RAM. You might be able to get away with using 512MB but it will probably be very, very slow.

---

### Post by TheFu on 2014-05-07
My standard answer for slow virtualbox: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) Follow those instructions.
Xubuntu can be very happy with 10G. Wasting storage **inside** a VM is just ... er ... a waste. Unless you are doing something special, think of the VM as a place for the OS, settings and properly installed programs - NOT for large data. Put large data on your network somewhere else and access it from inside the VM using nominal remote storage access methods like NFS or CIFS.

If you like to install lots-and-lots of GUI programs, 15G is fine for a VM.

Old dual-core processors can be slow. If you post the exact processor model, we can properly set expectations.  A Core2Duo E6600 will show nice VM performance - 90% of native, provided the GUI "cheese" is turned off.

For memory allocation - it depends.  It depends on the total RAM available, the hostOS, the clientOS and the workload on each.  Also, if you will run multiple VMs concurrently - that makes a HUGE difference.  Nothing impacts RAM use as much as having a GUI, however. If you can dump the GUI, then RAM requirements drop significantly.

---

### Post by hebdave on 2014-05-10
My memory is 2.8 GB
Processor AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ x 2
Graphics Unknown (which often causes problems in above the 12.04 LTS distro)
OS type 64-bit ( although the .ISO in VBox that works on my PC is Intel x86 desktop CD )
Hard Disk 94.9 GB

Above specified in system details from Ubuntu.

Also the standard instructions are for a 4.1xx in the blog you gave me. He at that 
point of writing had not checked 4.2 and above Vbox versions as he said the settings may be different.

My memory is below the 6 Gb he also mentioned that his friend had struggled with. Mine is only 2 GB memory - I assume this is the RAM that Ubuntu details is giving under its memory subtitle. To note my PC was running faster than his friends who had more memory which confuses me. Mine did have a lag though that was more significant on webpages which had more pictures and graphics. 

My intention is to use the internet mainly with the VM for safe surfing not much else. I don't have the ability to set up apparmor or those things and prefer a VM for snapshot reasons.

Am I still able to continue with the blog. Sorry it has taken a while to get back to you.

Thanks very much.

---

