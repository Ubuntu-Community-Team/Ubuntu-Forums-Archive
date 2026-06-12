---
title: "Help Setting Up Backup/File Server"
date: 2009-12-23
forum: Server Platforms
---

### Post by zenarcher on 2009-12-23
I'm not sure if I'm posting this to the proper area, but hope someone can help point me in the right direction.

Here is what I want to do:

I just replaced one of my older computers with a new one, so have an old 32 bit box available to play with.  I would like to figure out how to set this older computer up to be used to automatically back up folders in Home on my six computers on my network.(wireless).  Likewise, if possible, I would like to use this box as a file server for the six systems, as well.  All six of my systems are running Kubuntu Linux 9.10, so there is no need of being able to backup, store nor share Windows files.  They will all be strictly Linux.

I have cleaned the old computer out and done a fresh install of Kubuntu 9.10, so think I am ready to begin.  I plan to put the server in my garage, where it will be accessible from my wireless network.  I would like to be able to have files on Home on my main systems backed up to this server automatically at regular intervals.  If possible, I would also like to be able to store files on the server, which would be accessible by the other computers on my network.

I'm extremely new on this server concept, not having any experience at all.  I am wondering if anyone could offer some pointers and possibly direct me to some reasonably easy to understand "How To," which might help me accomplish what I want to do.

Thanks in advance,
zenarcher

---

### Post by Girya on 2009-12-23
I use Backuppc to backup my home network. It is fairly easy to set up (I drive a delivery truck for a living, so if I can figure it out...), uses rsync as the backend which is a good thing for a wireless network because it's easy on resources, It pools identical files so it saves on disk space. Its automatic and has a web interface and uses compression to save on more space. 

Also check out LVM Its an abstraction layer between hard disks and file system that makes moving and expanding file systems trivial. So when you fill up your hard disk you install another disk and expand your fs on to the new disk. Its cool. 

Here is what i have backed up from my desktop: 2 full backups and 6 incrementals. the back-ups represent 46gb of data stored in 19gb of space due to pooling and compression.  

My server sits in a closet, is headless (I administer it from my desktop through ssh). So your garage is probably ok as long as its secure. It would be a huge bummer if someone snatched your server with all your stuff on it.   

As far as file serving goes I don't have a clue. 

Kevin

---

### Post by zenarcher on 2009-12-24
Thanks much for the information!  I really appreciate it.  I'll do some reading on Backuppc today.  I appreciate the other tips, as well.  It's sure not a critical project for me, but I'm retired so have a lot of time on my hands to play with things like this and while I'm sitting here looking at this older computer I pulled out of my network, it just seemed like something interesting to try.My garage will be fine, I'm sure, as it's completely closed as in "ready to finish off to become another room."  It's also just on the other side of the wall from my other systems and my wireless router.  The central heat and air conditioning maintain an even environment there too.  

I'll give it a shot with my test computer and the new server box.  That way, if I mess something up, it's not a big deal.  All I have to do is a fresh install and I'm good to try again!

Cheers,
zenarcher

---

### Post by bcn17 on 2009-12-24
Just today I made a tutorial for setting up a openssh-server. If you follow the tutorial at the end you should have no problem accessing your server with your other computers via ssh and sshfs. 

If you would like the garage-server to backup other computers then you can turn all of your other 6 computers into ssh servers as well, and have the garage-server access them and make backups using something like rsync. 

GL, and let me know if you use the tutorial/run into any problems. I just made it!

[http://bryanroller.com/computers/openssh-server.html]("http://bryanroller.com/computers/openssh-server.html")

---

### Post by Girya on 2009-12-24
ZA, If you end up settling on backuppc there's a good tutorial on howto forge and another one lurking on this forum. 

I suscribed to this thread so if you need some help post here and I'll try to help. Just be patient because I only get to my desktop in the mornings end evenings.

---

### Post by zenarcher on 2009-12-24
Thanks much to both of you for the suggestions and offer for help.  I'm sure I'll need it!  I'll get started reading as soon as Christmas Day is over and things are calm and quiet here again.

Cheers,
zenarcher

---

### Post by zenarcher on 2009-12-27
> **bcn17 said:**
> Just today I made a tutorial for setting up a openssh-server. If you follow the tutorial at the end you should have no problem accessing your server with your other computers via ssh and sshfs. 

If you would like the garage-server to backup other computers then you can turn all of your other 6 computers into ssh servers as well, and have the garage-server access them and make backups using something like rsync. 

GL, and let me know if you use the tutorial/run into any problems. I just made it!

[http://bryanroller.com/openssh-server.html]("http://bryanroller.com/openssh-server.html")

Well, I'm trying your tutorial, which seems pretty clear.  I've run into a problem, however, before getting along very far.  Perhaps you can help me with this one.  I've opened a terminal on the client machine and here's the error I'm getting:

zenarcher@stantest:~$ ssh stan@192.168.1.30
ssh: connect to host 192.168.1.30 port 22: No route to host

Thanks much!
zenarcher

---

### Post by ephmanjmm on 2009-12-27
What is the ip address of the server? You used the one listed in the tutorial but as the tutorial states that address is "The last byte, 30, is arbitrary and is set by my router".

---

### Post by zenarcher on 2009-12-27
Ah, thanks for pointing that out!  I had missed it.  I'll give that a try!

Regards,
zenarcher

---

### Post by zenarcher on 2009-12-27
Okay, I have that working right now.  Now, I'm a bit confused with the following instructions:

Mounting the server filesystem onto the client machine

Mounting a filesystem in linux is the act of insterting some storage device into the folder tree of the computer doing the mounting. It can be done with a usb drive or over the network. If I create an empty folder on my computer called server I can mount my server onto it and it will be as if the server was part of my computer.

sshfs user@hostname:/ /home/my.user.name/server/

Above, the / after user@hostname is the directory I am mounting, which is the root directory /, which is the entire computer. I am putting it in the folder on my client machine /home/my.user.name/server/. 

On the "sshfs username@host" should this be the username and host of the server, or the regular computer?  I'm assuming the remainder of that command is referring to the regular computer, but not sure as to the first part of the command.

Thanks,
zenarcher

---

### Post by ephmanjmm on 2009-12-28
username at the server and the server name or ip address, i.e. admin@serverhostname:/ /home/my.user.name/emptydirectory/

One point on which I am unclear is this:

If you are backing up your client computer to the server and you have mounted the remote file system onto the system you want to back up, aren't you creating a loop?

Have you considered using rsync over ssh?  [http://oreilly.com/pub/h/38](http://oreilly.com/pub/h/38)

I use it for some servers where I work.

---

### Post by zenarcher on 2009-12-28
Well, to be honest, I'm a bit confused, as well.  I'm a total newbie, so far as this server stuff goes.

All I'm trying to do is set up a server here at home, which will back up specific folders in Home on four different computers I have here.  I'm trying to get something easy to set up, which will run an automatic backup, say every hour....I'd guess an incremental backup, only updating whatever has changed since the previous backup.  All the computers...on my network, including the server, are Linux only.  No Windows systems at all.

I'm also trying to use the same server to set up a file server I can use for the four computers on the network, as well.

Cheers,
zenarcher

---

### Post by bcn17 on 2010-01-02
Sorry I've been MIA guys- I'll be checking a bit more frequently just so you know.


> **ephmanjmm said:**
> 
One point on which I am unclear is this:

If you are backing up your client computer to the server and you have mounted the remote file system onto the system you want to back up, aren't you creating a loop?



It depends on how you set it up. If you have the client machine mount the server in, for instance, /home/client.user/server/ and the server backs up all folders except /home/client.user/server then you will be fine. No loops will be made. Although you make a good point, this could cause problems. 


Also, ephmanjmm already answered your question zenarcher, but just to make sure I'll give the same answer in different words. 

Using the ssh command, or sshfs- 
```
sshfs server.username@server.ip.address.or.hostname:/directory/on/server/machine /home/client.username/any.folder/
```

So from the client machine you use the sshfs command, and tell it to connect to the server using the server's ip adress or hostname and a username of an acccount on the server. The directory after the ":" is a directory on the server. You may well only want to mount a specific partition or folder rather than the hole thing. The second directory is the folder that the server will be placed into on the client machine. This could be any folder as well. However, if you try and mount it in a folder that is not in /home/your.username/any.folder/ then you may run into problems with file permissions. File permissions are a great tool to understand but no need to make your task harder than it is at first! When your ready to learn those google the "chmod" and "chown" commands. 

Oh, and also- many programs, like ssh and sshfs will have manual pages that you can access from the terminal. Sometimes this really helps with the syntax of different commands. Try and type ```
man ssh
```
or 
```
man sshfs
```

GL!

---

