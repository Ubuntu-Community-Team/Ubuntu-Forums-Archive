---
title: "could and infected Windows machine affect mounted linux volumes?"
date: 2006-09-20
forum: Server Platforms
---

### Post by jnoreiko on 2006-09-20
I dual-boot with Windows 2000 and Dapper, and I'm also looking into running a file server.

If Windows were to get infected with the sort of virus that wipes files, then the files on the ubuntu volumes would be affected, whether they're mounted in Windows, or shared on a separate server.
What's the best way to prevent this, above good antivirus on Windows?

---

### Post by JanvL on 2006-09-20
Make them read-only!

---

### Post by The Warlock on 2006-09-20
> **jnoreiko said:**
> I dual-boot with Windows 2000 and Dapper, and I'm also looking into running a file server.

If Windows were to get infected with the sort of virus that wipes files, then the files on the ubuntu volumes would be affected, whether they're mounted in Windows, or shared on a separate server.
What's the best way to prevent this, above good antivirus on Windows?

Either make your Linux mounts under Windows read-only (probably a good idea in any case, as ext3fs drivers for Windows are still a little sketchy with writing), or, y'know, the obvious "don't mount your Linux partitions under Windows".
[SIZE="0"]or don't use Windows at all, but I know that can be tricky[/SIZE]

---

### Post by rgeide on 2006-09-22
It might be a pain, but I usually make a small FAT32 partition that is mounted in both Linux and Windows.   You can read/write to that partition to trans files between either OS and if anything were to go wrong on either end (most likely Windows due to virus or a scripting oops in Linux) then your not up the creek without a paddle.

---

### Post by andb on 2006-09-24
Windows supports access to ext3 drives as ext2, meaning it doesnt use journaling. [http://www.fs-driver.org/](http://www.fs-driver.org/) these drivers are excellent and have worked flawlessly for me read/write. I suggest that you use the driver to access the linux drive only when needed, otherwise, dont assign a drive letter. When the driver is there, yes, windows can do whatever it wants to the drive, it accesses with full root permissions.

---

### Post by MrHorus on 2006-09-26
> **jnoreiko said:**
> I dual-boot with Windows 2000 and Dapper, and I'm also looking into running a file server.

If Windows were to get infected with the sort of virus that wipes files, then the files on the ubuntu volumes would be affected, whether they're mounted in Windows

As stated previously, if this is a concearn for you then mount them read only, otherwise get a decent virus scanner and look into your security situation.

---

### Post by jnoreiko on 2006-09-26
It's not a huge concern, as the Windows machines have antiviruses on them.

It's just that I was about to go into the usual spiel of 'no viruses on linux' when talking about setting up a fileserver running linux, and I suddenly thought 'hang on....' and saw the obvious vulnerabilty. It's the old story about the chain and its weakest link :)

---

### Post by MrHorus on 2006-09-26
> **jnoreiko said:**
> It's not a huge concern, as the Windows machines have antiviruses on them.

It's just that I was about to go into the usual spiel of 'no viruses on linux' 

Interesting concept.

I suppose you could in theory place a hostile binary on a ext3 volume whilst mounted under Windows but the scope for propagation would be quite narrow as that's a very specific vulnerability.

---

### Post by jnoreiko on 2006-09-26
> **MrHorus said:**
> I suppose you could in theory place a hostile binary on a ext3 volume whilst mounted under Windows but the scope for propagation would be quite narrow as that's a very specific vulnerability.

I wasn't thinking of anything that technical, just this:

Windows machine has volume from linux fileserver mounted
Windows machine gets infected
Virus wipes any files it can get its sweaty hands on
Linux volume erased :(

---

### Post by MrHorus on 2006-09-26
> **jnoreiko said:**
> I wasn't thinking of anything that technical, just this:

Windows machine has volume from linux fileserver mounted
Windows machine gets infected
Virus wipes any files it can get its sweaty hands on
Linux volume erased :(

Well if you want to just destroy the filesyste and/or data then yeah, that would work :)

---

### Post by airtonix on 2006-10-02
> **jnoreiko said:**
> I wasn't thinking of anything that technical, just this:

Windows machine has volume from linux fileserver mounted
Windows machine gets infected
Virus wipes any files it can get its sweaty hands on
Linux volume erased :(

This is a good reason to put your home and system files on seperate partitions....

Which allows you to only mount your home folder under windows....

Thus leaving your linux system files alone....
:D

---

### Post by honda on 2006-10-07
As I understand it, there is nothing stopping a windows virus to mount any linux partition and infect root, read passwords or whatever. The virus could even bring it's own ext3 driver to do that. Or am I wrong?? Please tell me I'm wrong...

---

### Post by tht00 on 2006-10-07
> **honda said:**
> As I understand it, there is nothing stopping a windows virus to mount any linux partition and infect root, read passwords or whatever. The virus could even bring it's own ext3 driver to do that. Or am I wrong?? Please tell me I'm wrong...

Possible?  I guess...  Likely to happen?  Not at all.  Until Linux gets to be 'big', viruses will be non-existant (whether through native infection or through another OS).

---

### Post by PvSinNL on 2006-10-07
> **honda said:**
> As I understand it, there is nothing stopping a windows virus to mount any linux partition and infect root, read passwords or whatever. The virus could even bring it's own ext3 driver to do that. Or am I wrong?? Please tell me I'm wrong...
No, I'm afraid you're right. As soon as a process (a virus, trojan, etc.) is running with full privileges on a system, it can essentially do anything it wants. It doesn't even need an ext3 driver, it can just mess up the partition table, write zero's to random locations on disk, or whatever.

---

