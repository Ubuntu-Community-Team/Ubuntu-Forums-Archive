---
title: "[SOLVED] Which Server Options to use?????"
date: 2008-10-27
forum: Server Platforms
---

### Post by Kellemora on 2008-10-27
Hi Gang

Simply stated, the more I study, the more confused I'm getting!

What I WANT to do I thought would be fairly simple, BUT.

Looking at Edubuntu (and playing with it a little too), although it's still Ubuntu, its set-up is Thin Client Based.  I know NOW that that is NOT the direction I wanted to go.

Reading the Ubuntu server set-up on Linux Gazette by Shane Lazar is more like what I want, but the instructions end before getting to the point of actually doing it.

And I have read countless other documents, directions, and experimented with things as well.

What I want to do, should mean using my smallest computer to achieve the task at hand.  Other things like Edubuntu that makes all the computers Thin Clients requires the largest computer you can build.

Currently I have a very well running LAN, all computers (with a need to) have access to the Internet.
But, for doing the days work, they all have to look to each other for the files they need to get their work done.

So, perhaps using the term Server is WRONG for what I want to achieve here.  Would FILE SERVER be the proper term?

Here is what I WANT to happen:

I want each user to be able to access all the Public Files regardless of which computer they sit down at (although this normally does not change) and to be able to find those files easily.

We have great computers with plenty of storage, so going the Thin Client route would be a waste of good resources.

IF I dedicated ONE computer (worst or best don't matter until I learn which one would be best suited for the job) as a FILE SERVER so that all the rest of the computers LOOK TO this ONE LOCATION for ALL FILES, regardless of WHERE those files are located on the LAN.

I KNOW it can be done, but I don't know the RIGHT WORDS to look up to study how to do it.

If I'm at Desk 3, and I need files from the computers at Desk 6 and 7, Currently I have to know WHICH computer to look for those files on, just because of the way the Doze works.  But since switching to Ubuntu, I need only MOUNT those files on the computer I am working on.  Makes them like they are right there.  Until you have to reboot and remount all of them again.

What I want is for a FILE SERVER to be like a REDIRECTOR.  All the Hard Drives (regardless of where they are physically located, will be MOUNTED on the Server.  All the desks will LOOK TO the SERVER to obtain the files they need.
In other words, the USER will NOT NEED to go and find where the files are.  They would just look to the SERVER and the server will get them the files from where ever they are stored.

I know this is getting LONG, but I visualized something like this. /root and all the associated system files on the server to run the server, BUT /home/users would be on an entirely different computer and /home/public (the shared files) could be located on other machines since in Linux a Partition APPEARS to be on the machine it's mounted on.

So, if I had files like /home/public/clientgraphics on computer B; /home/public/clientpamphlets on computer C; and /home/public/clientfinishedjobs on computer D; and each of the users own home directories on computer E.  This seems plausible to me.  Except, you can't spread home around to each hard drive, or can you?????

See, what I mean, the more I study, the more confused I'm getting!

A simple LAN works great, but making a one location to look to for files, I cannot seem to figure out.

Any Input or point me to more things to read would be appreciated.

TTUL
Gary

---

### Post by koenn on 2008-10-27
look into NFS
imagine a bunch of servers exporting ('sharing') folders.
You can mount these shares on a central server, your repository.
if you mount them all under the same directory and share them again, your clients need only to look at one place.

With some creative use of mounts and symbolic links, you may even be able to (apparently, as seen by the clients) reorganise the 'files' independently of which server they're coming from.

don't know if this actually works, and you will have to work out all the permission issues correctly, but it's worth a try and pretty close to what you describe.



Yet an other way of doing this is by setting up a cluster, which is a collection of servers that presents itself as 1 single machine on the network. I don't know how well clusters are capable of deviding storage amongs them, but you might want to check that out.

---

### Post by Kellemora on 2008-10-27
Hi Koenn

You picked up very well on what I want to do!

My first look at a Server was through Edubuntu.  I thought by installing one that works out of the box so to speak, I could then see what they did to Ubuntu.  So I did learn a little from doing that.

I also read many files on doing the Cluster thing and honestly, right now in this point in time, it's still WAY over my head, hi hi.........
But I am VERY interested in the concept, since we do a lot of graphical work here.

I'm going to mark this OVERLY VERBOSE post Solved, because I posted a very short one, that points right to the area I'm stuck at.

Thanks for that WORD Repository, I already hit some great info on-line using that word instead of File Server, stuff I hadn't studied yet.

TTUL
Gary

---

### Post by koenn on 2008-10-27
> **Kellemora said:**
> Hi Koenn

You picked up very well on what I want to do!

...
Thanks for that WORD Repository, I already hit some great info on-line using that word instead of File Server, stuff I hadn't studied yet.

TTUL
Gary
Glad I could help.
You might also want to have a look at document management systems
They're usualy based on databases in stead of filesystems and file sharing, with a (often web-) user interface to let the users get to the files they need. 
Google Alfresco for an open source example; 

Good luck &
Have fun.

---

### Post by Kellemora on 2008-10-27
Hi Koenn

Thanks Again!  Will Do!

Did you see my post asking if this TREE was possible?  By any chance!

I've already done something similar to that on a single machine with two hard drives.  I'm just trying to figure out how to do it using drives on other machines.  If I can accomplish that, I may not need a server at all, hi hi........


My son says I should just throw away all my hard drives and get a couple of nice big terrabyte drive and a backup system for them.  Yeah, I could get a Raid 10 too, if'n I had that much money, hi hi.........

Thanks Again

TTUL
Gary

---

