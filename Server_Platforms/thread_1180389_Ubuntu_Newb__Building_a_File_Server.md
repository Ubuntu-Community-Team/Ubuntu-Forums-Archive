---
title: "Ubuntu Newb:  Building a File Server"
date: 2009-06-06
forum: Server Platforms
---

### Post by cg49me on 2009-06-06
Let me preface this by saying I'm a complete greenie with Ubuntu. I've seen others' machines that use it, but I myself have effectively no experience with it. I have been doing my homework, though, so I know (read: think I know) some of what's going on. As far as my first-hand Linux useage goes, my school's servers were all Unix, so I had to learn some simple command line operation, and ended up playing around a bit on computers with RedHat installed on them.
 
Long story short, I'm a fresh college grad and want to expand my computer knowledge with the intention (so I tell myself) of expanding my career. I've got an electrical engineering degree, but my employer has me doing coding... Go figure.
 
Anyway, I'll have a fair amount of disposable income, and have set the task before myself of creating a Linux file server, which will hopefully expand into other things (media server, gaming server, home automation, who knows). The ultimate goal of my current project is a computer in my Jeep which I'll be able to wirelessly transfer media and other files to, but I digress. The server will be interfacing with Windows machines (of course).
 
I haven't even begun to look at the networking challenges that will befall me, but I'm aware that Ubuntu, and Linux in general, is pretty easy to get to talk to... Well, just about anything else.
 
The area that I've been researching so far is storage (hard drives). I want to implement a RAID array (something else I've never done), mainly just to say I've done it, but the protection is a factor as well. Right now I'm thinking a RAID5 setup across four 150GB Raptors. I reiterate: disposable income.
 
The last week has been spent learning about RAID setups in general, and looking for hardware (and software) that will do what I want. With my limited knowledge of RAID, I began looking for a mobo that supported RAID5 in Linux, but was dissappointed to find very few that did so. Some research revealed that many of the RAID controllers that come integrated on mobos are actually sofware implemented ("FakeRAID"), and aren't generally the most efficient solution. I then came across the wonder of software implemented RAID, but it appears that the only RAID configurations that Ubuntu will boot from are 0 and 1. Granted, through appropriate partitioning, I could have a RAID0/1 array to boot from, and a RAID5 array for files, but I didn't like the sound of it.
 
So then I started looking at dedicated RAID controllers. At first I was weary of dropping $200+ just to implement a RAID array, but then I reminded myself: disposable income. Another advantage of a dedicated controller is that drive rebuilding is instantaneous (doesn't have to be initiated), and can occur even if something goes wrong during the OS booting. After some searching, the controller I (think) I've settled on is the [Areca ARC-1210]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816131003") ([Areca site]("http://www.areca.us/products/pcie.htm")).
 
Now, this puppy says it'll work with RedHat and SuSe, so I figure it shouldn't have any problems with Ubuntu. It's got its own "BIOS" interface that you can boot up before anything else to set up your array. Thus, from what I gather, I should be able to assemble my RAID5 array when I first power on the system, then install Ubuntu on what will appear to be a single massive drive.
 
My question is this: Am I right, or will I run into more complicated issues? During my browsing while contemplating the software RAID setup, I came across several pages that talked about modifying system files, and that's what ultimately steered me toward getting a controller. Any input is appreciated, even if it's to recommend a different setup, or even to tell me there's no reason to do what I'm doing (which there really isn't, other than to prove I can).
 
I'm really looking forward to learning more about Linux! What everyone around here has done is great!

---

### Post by noway2 on 2009-06-07
In my humble opinion, you are putting the cart before the horse with your focus on the RAID.  Implementing a RAID is only one small step in the creation of a reliable server.  

Based on the comments of your post, I would recommend that you spend some time getting to know and using (your) linux system.  

First, read up on and experiment with the installation process.  Figure out how you want to partition the drives and directories.  Try a few small project, write a few programs for it, etc.  Create a basic network, get SAMBA running (to allow it to interface to windows boxes), build and run apache, etc.  For starting out, you won't need a high end PC and you will have a much better idea of what you need and want after you have used it for a while.  

As an aside, I would like to comment on your statement, "electrical engineering degree, but my employer has me doing coding... Go figure".  I TOO am an EE who's first engineering job was in software.  Don't underestimate the opportunities of this.  The software that runs on any mission critical equipment, and how it interfaces to the hardware, is as important, if not more so, than the hardware that it runs on.

---

### Post by cg49me on 2009-06-07
Good advice, all around.  I'll probably throw Ubunto onto my notebook, just to play around with things.

---

### Post by papenpj on 2009-06-23
What got me started with my file server a few years ago was this guide
[$80 file server in 45min]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html") it might be worth checking out if you havn't configured a system yet. For a strict file server/media server, IMO headless is better.  Mine was 600MHz with 128MB of ram and still able to stream 3 movies at once.

Most of the guides I have seen about ubuntu and raid mainly deal with RAID 0,1,1+0,0+1
I do remember reading somewhere that running a software based raid 5 does causes a significant amount of overhead on the CPU.  So for a good raid 5 you probably need a special card that supports it.
But if you go with one of the less CPU intensive raid levels that are software implemented it might give you more experience in Linux. Also, depending on how big your case is adding the raid later.

My server started out with only a 20GB drive. That drive is still in my computer and only runs the swap and operating system.  I added a 320GB drive that has all of my files.  Which I am looking to do a simple RAID 1 to Mirror it. If my 20GB drive dies, i do happen to have a semi-monthly ghosted image to fallback on.  Note: I don't tend to change the operating system alot or add new features. 

One final thing you may want to consider with that disposable income is using different drives. The probability of 4 identical drives failing at around the same is significantly higher than spreading it among several manufacturers, ie, haveing all your eggs are in one basket not a good idea. So, if you were to get similar size drives from different brands whos problems hopefully don't appear at the same time it might make a stronger raid.  The last thing you want is to experience a second failure before your array is rebuilt.
ALso, your four 150GB drives in raid 5 i assume would be 300GB useable with a hot-spare?
You could do raid 0 + 1 and have striping and mirroring of useable 300GB.... Another thing external hard-drives and enclosures aren't to expensive, neither are firesafes. So with a 500GB external you could easily perform periodic backups. In that situation your house could burn down and hopefully some of the data would survive.

I just figured I would give you some options because I assume with raid 5 you were intending on protecting your data. Im paranoid about mine and have an external that is either backuping up my important files or locked in a firesafe.

---

