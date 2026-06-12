---
title: "Number of Processor supported &amp; other questions"
date: 2006-01-06
forum: Server Platforms
---

### Post by Nightwind on 2006-01-06
How many processors will Ubuntu support?
I have a test server set up with SME 6.5 but I'd like to try 5.10 on it.
Server has 4 Pent processors 8 SCSI drives, 3 Gig ram.
When I set it up with SME 6.5 I had to create a boot disk because the BIOS doesn't support booting from the SCSI CD drive.  Is there any special documentation that I need to read before I install 5.10? If so where?
Are there any special steps I need to take to install 5.10 from the A drive?
Thanking you in advance

---

### Post by LordHunter317 on 2006-01-06
An SMP kernel should support 4 processors no problem.
You'll probably have to build a boot disk as well, and I do not know the procedure for that, sorry.

---

### Post by Nightwind on 2006-01-06
[QUOTE=LordHunter317]An SMP kernel should support 4 processors no problem.
You'll probably have to build a boot disk as well, and I do not know the procedure for that, sorry.[/QUOTE]
Please pardon my ignorance but what is a SMP kernel?
Thanks

---

### Post by LordHunter317 on 2006-01-06
A kernel that can run on multiple CPUs.   The package will have 'smp' in it's name.

SMP stands for Symmetric Multi-Processing, FWIW.

---

### Post by Nightwind on 2006-01-06
[QUOTE=Nightwind]Please pardon my ignorance but what is a SMP kernel?
Thanks[/QUOTE]
Thanks, I kind of thought that was what it was but coming from a predominately MS world I wanted to be sure. To assume something well we all know how that breaks down.

---

### Post by dragonfyre13 on 2006-01-06
[QUOTE=Nightwind]Thanks, I kind of thought that was what it was but coming from a predominately MS world I wanted to be sure. To assume something well we all know how that breaks down.[/QUOTE]

If you are coming from an MS world, Dual Core processors are enchanced by SMP kernels too.

---

### Post by Nightwind on 2006-01-06
[QUOTE=dragonfyre13]If you are coming from an MS world, Dual Core processors are enchanced by SMP kernels too.[/QUOTE]
Yes I know in Windows that is true but I learned along time ago better to ask and admit uncertainty than to bull through the China shop and break everything. I break enough things with adding to the list :o)

---

### Post by dragonfyre13 on 2006-01-25
I also heard that hyper threading processors are enhanced by SMP kernels as well...

---

