---
title: "Can't get permission to move old samba shares into my new smb server."
date: 2017-04-02
forum: Server Platforms
---

### Post by kristian152 on 2017-04-02
Hello.

I used to have a samba fileserver running on a debian system, but due to hardware failure i got stuck with only my shares on a disk. 
They all have their own permissions and users attached. 

I have been able to move them into my ubuntu system, but they are still locked. So I can't move them to my new fileserver, or even access them from where they are now.

-So my question is if there is a way to reset the permissions of the files or get into them? I'm pretty new to Ubuntu and filesharing etc. -But willing to learn!

I hope there is one that can help me, Thanks
___
System Ubuntu 16.04 LTS

---

### Post by howefield on 2017-04-03
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by darkod on 2017-04-03
I'm confused, is the ubuntu server the new fileserver? Or a third unrelated machine?

As root you have maximum permissions and you can move any data around and change ownership and permissions on files and folders.

So just use sudo to move/copy the data where you need, and then adjust permissions and ownership if needed.

---

### Post by kristian152 on 2017-04-03
Hi Darko, thanks for your reply.

I was running the samba off a debian server, now I am going to use a freenas instead. So at the moment the files are located on my ubuntu laptop. to be moved into the new freenas server when that is ready.

I am aware that I get full permission as root, but how do I change the file permissions? 
-as I wrote, I am new to this, and I am sorry if this a too simple a question for this forum. But google couldn't help me :(

So thanks again!!

---

### Post by darkod on 2017-04-03
In that case it is little tricky. FreeNAS has its own permissions assigned to the shares. I am not sure if these permissions will overwrite the existing ones after the copy or not.

But in any case, when you have the FreeNAS shares ready, mount them on your ubuntu laptop, and use either your own user (if the user has Write rights on the FreeNAS shares) or use sudo rights to copy to the shares.

Then after the data is on FreeNAS, you can try handling permissions on the mounted shares from ubuntu, or even better open ssh session as root to the FreeNAS and you can adjust permissions directly there. The data will be local to FreeNAS because it will already be copied to it. In many cases just reapplying the permissions of the shares will do the trick.

---

### Post by kristian152 on 2017-04-03
Ok, I will move in that direction..

Thank you so much!

---

### Post by darkod on 2017-04-03
Don't forget, you can do it easily this way:
1. While you are still preparing the data migration make the FreeNAS shares to have write access to all (public shares).
2. Copy the data. There should be no problems because everyone will have write permissions.
3. once the data is in the FreeNAS, modify the shares permissions for what you want them to be. At that moment the permissions will be re-applied to all files already copied into the shares.

I think that would be the easiest way.

---

### Post by kristian152 on 2017-04-05
Drake>
Thank you for your help, I finally did it this way:

After i moved the data from the old storage in the Debian via sudo> mv to the local storage of my ubuntu(I have it running external on a portable), I did the same again to move the files from my ubuntu to the local storage in my laptop, which Win10 is able to see. -So when it ended up there, I could enter the files, and move them to the new server storage. And attach them to the dirs they belong in and rebuild the permissions.

It was a long and 'with nerves out ratling' trip, but as far as I have been able to check up on the data, everything is there!

So i just wanted to give you a thanks and short update!!

THANKS

---

### Post by darkod on 2017-04-06
No problem. Glad you got it sorted out. Please mark the thread as Solved, you can do that in Thread Tools above the first post.

---

