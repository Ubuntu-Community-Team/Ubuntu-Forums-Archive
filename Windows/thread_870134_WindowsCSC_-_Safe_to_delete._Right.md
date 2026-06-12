---
title: "Windows\CSC - Safe to delete. Right?"
date: 2008-07-25
forum: Windows
---

### Post by Roasted on 2008-07-25
At work (school district) whenever I see a computer that is somehow maximizing its hard drive space (down to the last few megabytes) I check the CSC...

Boot to safe mode.
Start - Run - CMD.
CD /Windows
CD /CSC
Dir

Bam... lots of files listed.

cd..
rd d1, d2, d3, etc to d8.

Always worked for me.

However... I've done this knowing if I screw it up, it's on me and I have to reinstall. K great.

A teacher just came up to me and asked how I fixed it. They have a decent sized LAN at home with 9 computers, and evidently her husband has a domain set up for it and some kind of a backup server. She was having the same issues with two of her computers at home that she had in her room when I fixed it.

So I gave her instructions on how to do it. However, since it's her doing her home computers, I figured I'd check and make suuuuuuure that it won't do any harm... Considering it's her computers and all. If it were mine, I'd do it, and deal with any problems. But I don't want to be giving people information unless I'm positive it's safe.

In this case, with the CSC (Client Sided Caching) in Windows XP, is it safe to delete those folders? D1-D8?

---

### Post by Battie on 2008-07-25
Isn't that where offline files are stored?  That's usually only useful for laptops that need connection to network drives (like the home directory) when they are not on the network.  I rarely see it used on desktops.

If they are unneeded, these files should be deleted properly under My Computer --> Tools --> Folder Options --> Offline Files -> Delete Files.  Optionally, you can disable offline files.

Another huge disk space hog is temporary files within the Local Settings folder in users' profiles.  Empty the temp folder and the Temporary Internet Files folder.  There is a super hidden file in there call Content.ie5 that can really swell up.  It can only be seen when accessed directly through the address bar or when viewed as another user.  This folder is NOT cleared when you run cleanup in Internet Options.  However, I do believe it is cleared when you run a Disk Cleanup.

Edit:  By the way, how much space does that CSC folder actually take up?  Most people don't have that much stuff in there, and it shouldn't be a problem unless there are many profiles on one computer.

---

### Post by fiddledd on 2008-07-25
I thought that CSC was where other clients on the Network may store/cache files. In which case 9 on the LAN, so  D1-D8 might be the other 8 boxes. This is a guess and I've just realised doesn't actually help you.

---

### Post by fiddledd on 2008-07-25
OK, here's an idea. Rename the csc folder to wascsc or something, reboot, and if all is ok delete it. If other clients on the LAN complain rename it back to csc.

---

### Post by Roasted on 2008-07-25
Meh. She already left. I just know I was taught to do that at my internship, a neighboring school district. Then when I ran into the problem here at my job, I deleted it, and bam everything worked.

The computers I worked on were student computers... so who knows HOW many profiles were on them. 

We've never had a problem when deleting the CSC, because it just regenerates itself and builds up the cache again.

And we don't use synchronizing here like we used to. Instead, we just map their my documents folder to the server... so whatever goes in the my documents folder is their actual storage folder.

I have no idea what kind of setup this teacher has at home. I just know she came right to me and asked the question, so I told her. I just wanted to double check here and verify that if deleting them was safe...

---

