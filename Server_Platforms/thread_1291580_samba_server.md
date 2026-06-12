---
title: "samba server"
date: 2009-10-14
forum: Server Platforms
---

### Post by Msingh on 2009-10-14
so I have a samba server, and I got a 2TB hard drive, and I want to make it available to other users accessing the server. I was thinking either mounting the samba folders on to the hard drive or mounting the hard drive in the home folder, not really sure how to do either of those, or if there is any other alternative, can anyone help? I'm running jaunty server edition X86, and installed samba from the repositories.

Also is it possible to allot a certain amount of space for certain users?

---

### Post by Jive Turkey on 2009-10-14
> **Msingh said:**
> so I have a samba server, and I got a 2TB hard drive, and I want to make it available to other users accessing the server. I was thinking either mounting the samba folders on to the hard drive or mounting the hard drive in the home folder, not really sure how to do either of those, or if there is any other alternative, can anyone help? I'm running jaunty server edition X86, and installed samba from the repositories.

I would set up the drive in your fstab file to a folder in / and add folders to it based on the specific types of permissions you want to give your users, and possibly the type of content. Then use samba to publish the folders as separate shares.  Make sure your user has full permissions on the folders.  I would leave the top level folder /shares owned by root, but own the subfolders myself i.e. /shares/myownedsharedfolder/   not sure if it matters though.  If you have your home folder encrypted, definitely don't mount it there.

> Also is it possible to allot a certain amount of space for certain users?
I think so, "Disk Quotas" is the search term you want to use.  There are linux disk quotas too, but samba has the compile option set for them on your installed packages if they are the same as mine. I've never used them but this guide might help you: [http://portfolio.itas.ca/~schewet/257T/mini3.html]("http://portfolio.itas.ca/~schewet/257T/mini3.html")

---

### Post by Msingh on 2009-10-15
Ok thanks, but I'm going to need folders for about five people because I created the server for my whole family, and I only need to make the drive space available to them at the least, and I'm pretty new to ubuntu only a couple weeks now, so sorry, but I'll need a bit more help on how to set stuff up specifically, sorry for the trouble #-o

---

### Post by bab1 on 2009-10-15
> **Msingh said:**
> so I have a samba server, and I got a 2TB hard drive, and I want to make it available to other users accessing the server. I was thinking either mounting the samba folders on to the hard drive or mounting the hard drive in the home folder, not really sure how to do either of those, or if there is any other alternative, can anyone help? I'm running jaunty server edition X86, and installed samba from the repositories.

Also is it possible to allot a certain amount of space for certain users?

...

... I'm going to need folders for about five people because I created the server for my whole family, and I only need to make the drive space available to them at the least, and I'm pretty new to ubuntu only a couple weeks now, so sorry, but I'll need a bit more help on how to set stuff up specifically, sorry for the trouble


Samba can be as simple or as complex as you want to make it.

If you are going to manually configure Samba, then you would use /etc/samba/smb.conf.  The folders are regular Ubuntu (Linux) and *shared* across the network by Samba.  You can use already available folders or create now Linux folders specifically to share.

I have a 1TB drive that has one partition that is mounted at /smb (created by me) in the file system. All the folders below /smb are on the 1TB drive.

If you want folders dedicated to each user, Samba can do that.  In the smb.conf file there is a section called [homes] just for that.

If you use the GUI (Nautilus) and right clicking to make shares, this is handles by the GVFS (virtual file system) and all the configuration files are stored at /var/lib/samba.  The only thing you will need the smb.conf file for is to set the workgroup.

I suggest taking the time to read the [**_documentation_**]("http://www.samba.org/samba/docs/") at samba.org.

In particular the ["by example"]("http://www.samba.org/samba/docs/man/Samba-Guide/") document.

Howto's are fine also, but it helps to understand why you do things, not just what to do.

Edit: As far as user quotas, they are implemented on a partition wide basis.  This is an good reason to use a dedicated partition for all the Samba shared data.  Maybe even splitting the drive into multiple partitions.

---

### Post by Msingh on 2009-10-15
Thanks, I was able to to go into the conf file and create the share for the hard drive, just copy pasted a different profile and changed some settings :P and it works perfectly though

---

