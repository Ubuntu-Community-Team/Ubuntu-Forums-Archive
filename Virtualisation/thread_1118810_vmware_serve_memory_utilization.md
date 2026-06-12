---
title: "vmware serve memory utilization"
date: 2009-04-07
forum: Virtualisation
---

### Post by bugginmiami on 2009-04-07
I have dug around but havent really found what Im looking for.

I am running dell 1950's with 16 gigs of ram and dual quad core's. It is now running 8 production vm's with perfect usability, not slow, etc. It is running 7.10 64 bit ubuntu desktop and vmware server 1.07. It has been in this role for about a 2 years, and I have 2 more just like it, no problems. They arent really hammered, lightly used, but production machines.

 However the one question I have is now that i have upped one of them them from 6 to 10 vm's (mostly server2003 instances with 500-850 megs of ram), i am puzzled why in system monitor it only shows 1 gig total ram in use.  Obviously I put 64 bit, and 16 gigs of ram to give them some breathing room.

 I went to the host settings, set it to use host ram which is set to 14 gigs, and same difference. Runs great, only uses 1 gig. I have tried all three options (page some, page all, use host) with same results.  Am i just really really lucky it runs as good as it does?(or threw a good enough box at it!). 
 If anyone can lead me in the right direction to make it use the physical ram, or if it simply doesnt do that, thats ok too as it runs good.   We have already commited to buying some esx servers to replace these and get the vm's on the san, but I couldn't be happier with the job ubuntu did for us. And we will actually be using these to virtualize machines at some satelite offices.

 One more thing, it may just be the way im reading the system monitor, correct me if im wrong -  it says:
 User Memory 1 gig of 15.7  6.5%
 Swap   37.6 mb of 11.1 gb  .3 %

 Then When you go to processes -  There are 6 vmware-vmx processes, Virtual memory - 1.2gb  shared memory 1 gb, that last row under memory says 0 bytes. (these are the same, theres 2 more on this box but smaller than 1 gig ram)

 Thanks for any help on this.  Im not too versed in linux and think i what i have been able to utilize here is due to luck and a great set of products that are ubuntu and vmware!

---

### Post by HermanAB on 2009-04-07
What kernel are you using?  You need either a 64bit kernel or the 32bit kernel-server to be able to use more than a few gigabytes of RAM.  

Since your system is old, it may really be using a 1GB capable kernel!

---

### Post by AlanP123 on 2009-04-07
I recently started looking at ESXi, certainly not an expert, and still getting my head around it.  

But it seems to me that the hypervisor is a virtual-memory operating system (now there's a surprise!), and even though the guest OSs are also virtual memory operating systems, and thinking they have XXMB of RAM... in fact they might not - that physical memory they think they command might be virtual...

--overcomittment--

Just a thought....

---

### Post by veloce on 2009-04-07
At close to the other end of the spec spectrum, I have a multi-core Dell box with 2Gb ram with Ubuntu Ibex Server (32bit). Currently 4 vms are running under vmware server 2, 3 with 512Mb, 1 with 384Mb.

Server reports that it is currently using:

292Mb of the 2Gb
149Mhz of 6GHz

The vms are a bit lightly loaded today but the usage seldom goes above 50%.

I assume from all this that vmware is quite good at managing shared resources.

---

### Post by bugginmiami on 2009-04-14
I got some more information via sysinfo.   I double checked and the host settings define, and requst the virtual machines use 14 of the 16 gigs of ram, but total utilization is still below 1 gig.  It works well, relly well considering its paging everything.  Any help appreciated. I use the desktop version instead of server as I am a point and clicker, if this is my problem I will work on redoing the server with server (and add the desktop) and see if that solves it, on a test machine first.
thanks for any help!



SYSTEM INFORMATION
	Running Ubuntu Linux, the lenny/sid release.
	GNOME: 2.20.1 (Ubuntu 2007-10-19)
	Kernel version: 2.6.22-16-generic (#1 SMP Mon Nov 24 17:50:35 GMT 2008)
	GCC: 4.1.3 (x86_64-linux-gnu)
	Xorg: 1.3.0 (13 June 2008)
	Hostname: vmhost01

CPU INFORMATION
	GenuineIntel, Intel(R) Xeon(R) CPU           E5310  @ 1.60GHz
	Number of CPUs: 6
	CPU clock currently at 1596.040 MHz with 4096 KB cache
	Numbering: family(6) model(15) stepping(11)
	Bogomips: 3194.65
	Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm

MEMORY INFORMATION
	Total memory: 16071 MB
	Total swap: 11327 MB

---

### Post by veloce on 2009-04-14
> **bugginmiami said:**
> I got some more information via sysinfo.   I double checked and the host settings define, and requst the virtual machines use 14 of the 16 gigs of ram, but total utilization is still below 1 gig.  It works well, relly well considering its paging everything.  Any help appreciated.


Why do you think you have a problem?

It won't be swapping anything to disk as it has plenty of memory, it's just that the vms aren't using the memory - but it's reserved if they do need it. Unless, of course, you have turned swapping on - then it's not necessarily reserved.

If you have a test machine try doubling the number of vms and turning on swapping.  I suspect that the portfolio effect will mean that you still get good performance from them all.

---

### Post by bugginmiami on 2009-04-14
You are right, i don't necessarily have a problem. I just would like to think the 16 gigs i asked the boss for were necessary, when the server shows its using 1, well, it doesn't look like it!
(the new hosts i asked for have 32 gigs)

I found this on the vmware forum:

Re: VMWare Server Memory Issue Jul 19, 2006 9:27 AM
Click to view kingneutron's profile Master kingneutron 

1. Re: VMWare Server Memory Issue Jul 19, 2006 9:27 AM
--Vmware, by default, does not allocate Host RAM to the guest(s) unless it is needed. [This is actually a Good Thing(TM).]

--Start $big-program in one or more of the Guests, and you will see the host allocated-memory increase. 

 So i will continue giving the guest os's what they ask for and hope for the best.

 My new problem is we are going to esx and i really prefer my ubuntu hosts. Im used to just copy and pasting machines all over the place. I have decommisioned one of my original hosts (and simply copied its servers to another one) and installed demo esxi on it until we get our esx hosts, but i have a feeling tomorrow it's getting 8.10 and vmware server 2 on it to play as i dont want to build new servers just to test.  The converter sends ptv's to it no problems, but id like to put some of my existing vmware server machines on it rather than do new ones. Haven't figured that out yet. Ubuntu is great as you just go to the desktop and copy the machines from some network location and you are good to go. More to learn.

---

### Post by Dedoimedo on 2009-04-15
You can use VMware Converter to convert from VMware Server to VMware Infrastructure machines. ESX also has ssh console, so what you're used to now won't changed that much.
Dedoimedo

---

