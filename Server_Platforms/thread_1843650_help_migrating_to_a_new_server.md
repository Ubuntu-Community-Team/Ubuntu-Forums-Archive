---
title: "help migrating to a new server"
date: 2011-09-13
forum: Server Platforms
---

### Post by bone2006 on 2011-09-13
I have a weird situation here in that I have a server running that there was some sensitive information(ex social security numbers..etc) on that I'd like to completely remove everything from it that it can't be recovered.  So I am planning on nuking the system with DBAN live CD.

But I would like to move everything over to a new server without copying data that can be used in recovery tools like photorec.

So my question is if I use clonezilla to make a backup copy of the server to put in the server, would metadata or what ever it's called still be preserved or is that only on the physical drive the computer?

Hopefully I explained myself well, but I want to copy all my data over without the senestive stuff that's still hidden on the drive to another server so I can nuke the old drive.

---

### Post by arrrghhh on 2011-09-13
Clonezilla does bit-by-bit copying (similar to dd), so any information (including "hidden" data) will be transferred.

However, this "hidden" data doesn't have the same effect as it does on Windows.  If you "rm" something in Linux, it actually 0's that block on the HDD.  So it is truly gone.  In Windows, when you delete something, it only "marks" the block as usable.  It doesn't actually 0 the block out.

In other words, if you use rm to remove files, recovery is pretty much impossible anyways... So I wouldn't worry about it personally.

---

### Post by bone2006 on 2011-09-13
I'm not sure if I'm answering my own question, but am I better off doing something like this first?

sudo sfill -l -l -v / 

Or some tool that will actually remove have the free space being unrecoverable.

---

### Post by bone2006 on 2011-09-13
> **arrrghhh said:**
> Clonezilla does bit-by-bit copying (similar to dd), so any information (including "hidden" data) will be transferred.

However, this "hidden" data doesn't have the same effect as it does on Windows.  If you "rm" something in Linux, it actually 0's that block on the HDD.  So it is truly gone.  In Windows, when you delete something, it only "marks" the block as usable.  It doesn't actually 0 the block out.

In other words, if you use rm to remove files, recovery is pretty much impossible anyways... So I wouldn't worry about it personally.

Thanks for the reply, the situation is that we actually ran photorec and recovered stuff that we were surprised was still on there.  It was a machine that went from ubuntu desktop and then ubuntu server, which was reformatted but was ext3 both times if I'm not mistaken.

It's why at this point I'm starting to think maybe a tool that actually fills in empty space and then doing clonezilla would be the easiest way to go?

I've done so much to the server that I can't remember everything

---

### Post by arrrghhh on 2011-09-13
> **bone2006 said:**
> Thanks for the reply, the situation is that we actually ran photorec and recovered stuff that we were surprised was still on there.  It was a machine that went from ubuntu desktop and then ubuntu server, which was reformatted but was ext3 both times if I'm not mistaken.

It's why at this point I'm starting to think maybe a tool that actually fills in empty space and then doing clonezilla would be the easiest way to go?

I've done so much to the server that I can't remember everything

Eek...

Well, a format is different than rm... especially a 'quick' format.

Anyhoo, why don't you just backup the essential stuff and DBAN the disk...?  Seems Clonezilla is not for you if you want to rid yourself of other spiders on the disk.

---

### Post by bone2006 on 2011-09-13
> **arrrghhh said:**
> Eek...

Well, a format is different than rm... especially a 'quick' format.

Anyhoo, why don't you just backup the essential stuff and DBAN the disk...?  Seems Clonezilla is not for you if you want to rid yourself of other spiders on the disk.

I'm just not sure how to back everything up without going with clonezilla?  I'm also wondering about the time it will take to do all of this compared to just writing zeros to the empty space?

The only things I really have on there are openssh and samba, but the permissions on all the files and the access restriction is what is making me nervous.  There's about 8 users and each have different permissions and folders and files that I'd prefer not to spend a week trying to trouble shoot.

You don't think using something like sfill will be secure enough?  I just checked and the two drives on the server are ext4 from looking at fstab.

---

### Post by arrrghhh on 2011-09-13
> **bone2006 said:**
> I'm just not sure how to back everything up without going with clonezilla?  I'm also wondering about the time it will take to do all of this compared to just writing zeros to the empty space?

The only things I really have on there are openssh and samba, but the permissions on all the files and the access restriction is what is making me nervous.  There's about 8 users and each have different permissions and folders and files that I'd prefer not to spend a week trying to trouble shoot.

You don't think using something like sfill will be secure enough?  I just checked and the two drives on the server are ext4 from looking at fstab.

Well, if you do want to go that route, I am by no means an expert on the topic.  Perhaps sfill will do the trick for you... I apologize, but I am probably in over my head here :p.  Clonezilla probably will be easier in the end, assuming you can get rid of the 'extra' data...

---

### Post by Jonathan L on 2011-09-14
> **bone2006 said:**
> Thanks for the reply, the situation is that we actually ran photorec and recovered stuff that we were surprised was still on there.  It was a machine that went from ubuntu desktop and then ubuntu server, which was reformatted but was ext3 both times if I'm not mistaken.

It's why at this point I'm starting to think maybe a tool that actually fills in empty space and then doing clonezilla would be the easiest way to go?

I've done so much to the server that I can't remember everything

Hi ..

For exactly these kinds of things I recommend tar for moving the data and then a drill for wiping the disk.

It's more-or-less impractical to know the details of every kind of file system and its underlying block behaviour under format, delete, refill and failure modes.  Every few years we get a new filesystem format, and every few years someone discovers interesting things left behind by searching hard.  Normally a motivated bad guy has a lot more time to find something missed than a motivated good guy has to close everything off.

If you want to copy just user-visible data, use tar.  That way you know what's in you copy without having to think about all the metadata or possibily uncleared blocks or partial filenames or anything.

If you have something which you could be sued for if it leaked, or costly commercial data, then I really do use a drill (Bosch GSR 12-2, if you care, with 3 mm bit).  If you absolutely can't do that for reasons of ecology or economy, then I dd the raw disk from /dev/zero, check I have my 1 Tb of zeros, and then reformat it.

I have no experience of the special tools for wiping things, but fundamentally I prefer simple tools whose bugs will be visible to me rather than special ones which are very difficult to tell.  

Hope that helps
Jonathan.

---

