---
title: "Boot and recover disk"
date: 2012-11-30
forum: Server Platforms
---

### Post by MakOwner on 2012-11-30
I configure my servers using the minimal install, and add packages as needed, and the servers never have a GUI desktop.  

OS critical files go on local disk and data files go on external disk - disk that's easily disconnected so that I wipe the internal drives, reinstall and add the needed packages for that partiucalr configuration - web, nfs, zone-minder server, etc.

Is there a mksysb type program that will create a recovery disk ISO that when booted will recreate the exact configuraiton?  

It's been a while since I have last looked a tthis since the minimal install disk has worked well enough, but I'm thinking improving recovery time might be nice.  

Thanks goodness this hasn't happened to me too many times.  
I'm looking at a base OS upgrade on a webserver  and thought I might revisit this again, just in case somethig had come along since the last time I asked.

---

### Post by sudodus on 2012-11-30
I think you might use Remastersys to do what you describe.

Another method is to clone the drive and simply replace the used drive with the cloned copy and run again. Clonezilla is a good tool to clone drives.

If you don't want to clone it, you can make an image file on some external media, and restore from it. Also here Clonezilla would do the job.

---

### Post by Vegan on 2012-11-30
i use the usb stick of clonezilla, definitely a handy tool

fits even an old 1 gb stick fine

---

### Post by jamesr on 2012-12-02
I would also make a suggestion of looking at MondoRescue.

---

