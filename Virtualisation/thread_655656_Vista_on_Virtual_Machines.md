---
title: "Vista on Virtual Machines"
date: 2008-01-01
forum: Virtualisation
---

### Post by eagledrc on 2008-01-01
I have Windows Vista Home Premium installed on an HP Pavillion a6130n with 3GB RAM and a 2.6 ghz AMD processor and a Nvidia video card.  Vista came installed on the machine.  Because I do not like Vista, I want to switch to Ubuntu (but keep the dual-boot).  However, I have Adobe CS3 Design Premium, and it does not work on wine very well.  Because I have 3GB of RAM, I figure I can run Vista and Photoshop and all that on a Virtual Machine on Ubuntu.  How do I burn a Vista ISO from Vista?  I have the serial #.  Or can I access the hard drive that I am dual-booting off of from Ubuntu?  

Thanks

~Ocean~

---

### Post by |2eason on 2008-01-01
Do you mean to say your machine didn't come with a Vista disk? It should have come with at least a repair disk. Some repair disks can be booted from and allow for clean installs. If you have neither, then your only option is to download an OEM copy from the net. So long as you use your key you should stay above the law.

---

### Post by Steveway on 2008-01-01
But don't forget that you are only allowed to run Vista _Ultimate_ on a Virtual Machine!
> You may use the software installed on the licensed device within a virtual (or otherwise emulated) hardware system on the licensed device.
You are not allowed to do this with the other ones (Home, Office, Chocolate etc...)
> You may not use the software installed on the licensed device within a virtual (or otherwise emulated) hardware system.
(I'm not sure what applies to the Business-version)

---

### Post by SRP on 2008-01-01
I haven't tried this with Vista, but have with other Windows OS... download the free version of the VMware Converter application and install onto you current Vista machine.  Use Converter to create an image of the local machine.
Even if you did have a OEM Repair Disk I'd doubt it would work with a virtual machine - it'll look for certain hardware which it won't find.

---

### Post by eagledrc on 2008-01-03
That sounds good...No, my HP did not come with any discs.  I can burn system recovery discs, but I don't know if those are ISOs or not...I have heard that only Ultimate will work, but I also heard that that was simply a rumor.  I will also look for an OEM copy if this doesn't work.  I will keep y'all updated.  

Thanks!

---

### Post by eagledrc on 2008-01-03
How do I make a image (ISO) from the VMware Converter? It seems to need an ISO...

---

### Post by dpj23 on 2008-01-03
Vista will run in VMware...  However, not all the fancy graphical effects will work... VMware is currently working on this driver for video support...  Don't know off the top of my head when they are scheduled to release it...  

With that said; I currently run Vista as a virtual machine...  It runs...  That's all I'm going to say about that... 

*** doing graphic design in a virtual machine is not the best strategy...

O.K., but if you have too or want too I would recommend that you allocate at least 2GB of RAM towards this virtual machine...

---

### Post by eagledrc on 2008-01-08
I can't figure out how to burn a vista iso.  Can't VMware run vista off of the hard drive? I can see my vista system files from ubuntu.  No where on the internet can I find how to get a iso.  I have also heard that VMware can run the programs on the linux desktop instead of the windows desktop.  That is what I want to do.  So should I burn system recovery discs from Vista and use them to install vista on VMware?

---

### Post by popch on 2008-01-08
Post #4 says it all. Run the converter to convert your Vista partition into a virtual machine. For doing that, you won't need a CD or ISO.

[http://ubuntuforums.org/showpost.php?p=4054992&postcount=4](http://ubuntuforums.org/showpost.php?p=4054992&postcount=4)

---

### Post by eagledrc on 2008-01-08
will that erase the dual-boot vista? will i still be able to dual boot?

---

### Post by popch on 2008-01-08
That ***should*** not touch your partition; it merely should copy the contents of the partition into a disk file.

Read the instructions carefully. Do not touch anything until you fully unterstand what it is going to do.

---

### Post by eagledrc on 2008-01-08
by disk file file, you mean a DVD that I insert and VMware burns on, right?  Then I take that DVD and insert it on Ubuntu and run the VMware machine on there.

---

### Post by popch on 2008-01-08
> **eagledrc said:**
> by disk file file, you mean a DVD that I insert and VMware burns on, right? 

That is exactly what I do ***not mean***.

Once you have a partition with a windows installed in it (such as you have for dual booting), there are two ways of  using that partition with a virtual machine:

1. You could modify the windows in that partition so that it still is in that partition but able to run in a virtual machine.

or

2. You can run the aformentioned (in post 4) utility provided by VMWare which reads the contents of your partition and copies most of it into a disk file. VMWare then uses that disk file in lieu of your original partition. To the virtual machine then uses what it 'thinks' is a fixed disk but what in reality is only a disk file.

In either case, you do not install Windows, but you use the windows which already has been installed. Thus, both procedures work quite fine without having the installation CDs or DVDs.

---

### Post by eagledrc on 2008-01-08
I understand.
I think I want to take option #1.  How can I do that?  I am running VMware but not sure what I am doing so I don't wanna mess anything up.
If that is too hard, #2 would work as well...

---

### Post by popch on 2008-01-08
> **eagledrc said:**
> I understand.
I think I want to take option #1.  How can I do that?  I am running VMware but not sure what I am doing so I don't wanna mess anything up.
If that is too hard, #2 would work as well...

If you don't know what you're doing, take #2. Then, you are always working with a copy of your original partition, and there's nothing that can really go wrong.

#1 might seem to be simpler but is not. It has the disadvantage that you are working on the original and thus put your existing installation at risk.

If you do choose #1, please please backup your partition first and make sure you understand how to restore it before you do anything damaging.

---

### Post by eagledrc on 2008-01-08
Okay, I will do #2.  How do I go about that?  I have a DVD and VMware running.

---

### Post by popch on 2008-01-08
As I have said before, the post #4 in this thread points the way: [http://ubuntuforums.org/showpost.php?p=4054992&postcount=4](http://ubuntuforums.org/showpost.php?p=4054992&postcount=4)

I can tell you in broad terms how it works. I can not give you detailed instructions. You should fetch those from VMWare's web site.

And you won't need a DVD, I believe.

---

### Post by eagledrc on 2008-01-08
oh okay
THANKS

---

### Post by eagledrc on 2008-01-08
that post #4 isnt detailed enough but i'll look on the website.

---

### Post by eagledrc on 2008-01-08
but i have one more question:
The machine is 169GB.  So I have to have room on my HD for 169x2 + (ubuntu) and all my files?
I have a 400GB HD with a 100GB linux partition.

---

### Post by popch on 2008-01-08
The size of the partition which holds Vista is not relevant. What's relevant is the amount of space actually used. 

Open 'my computer' or the Windows Explorer (if they still are called that in Vista). You can see hoch much of the space of the partition is used. VMWare needs at least that much for a copy of your partition.

---

### Post by eagledrc on 2008-01-08
yeah that's what im saying...The min size is 169GB...most ppl can't do that im surprised - most people dont have that much space free
Well i am doing it...
    03:46:06 PM                Step 1 : Connecting to VMware Converter Agent on localhost
    03:46:06 PM                Step 2 : Creating target virtual machine and importing data
    03:46:06 PM                        Configuring parameters for the target virtual machine...
    03:46:07 PM                        Creating target virtual machine...
    03:46:13 PM                        Formatting target volume c:...
    03:47:16 PM                        Taking a snapshot of the volume...
    03:47:38 PM                        Cloning source volume c: into target virtual machine...
its copying onto my desktop, and when i boot onto ubuntu, i point VMware to that file(folder), right?
and will i be able to delete that large file (folder) later?

---

