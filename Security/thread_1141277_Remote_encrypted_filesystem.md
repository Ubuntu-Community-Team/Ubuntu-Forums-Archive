---
title: "Remote encrypted filesystem"
date: 2009-04-28
forum: Security
---

### Post by Xyem on 2009-04-28
Is is possible to have an encrypted filesystem on a remote machine which is mounted/decrypted on the local machine ( through ssh for example ), without it being mounted in any way on the remote one?

---

### Post by Cybie257 on 2009-04-28
Yes.

I've managed to mount the remote encrypted volume, which is encrypted via ENCFS, using sshfs. Then, on the local machine, I use ENCFS to mount the unencrypted volume on the local machine. 

Basically, you are just mounting the remote encrypted volume on the local machine. As you would expect, you will only see the encrypted file names on the local computer. So, in order to access it via the unencrypted view, you just mount it locally as you would if you were on the remote machine where the actual data resides. 

Does this make sense? If not, let me know and I will try to clarify a bit better. EncFS seems to be about the only way I was able to achieve this as the others didn't have any way to remotely mount without having the remote computer having the unencrypted data visible. 

-Cybie

EDIT: I added a makeshift diagram (attached JPG) of what I am talking about. If there are any questions, this might help you visually see what I did.

---

### Post by Xyem on 2009-04-28
I had a look at the EncFS homepage ( I'd not looked at EncFS previously ) and how you described your setup makes perfect sense.

In your experience, is it tolerant in regards to connection failures or is there a relatively high risk of corrupting the encrypted files?

Thanks for the very quick and concise reply :) ( And a diagram! You do spoil me )

---

### Post by Cybie257 on 2009-04-28
> **Xyem said:**
> 
In your experience, is it tolerant in regards to connection failures or is there a relatively high risk of corrupting the encrypted files?

On the job-site, we have a T1 line (yes, old technology, lol), and for our off-site backup plan, we have some files that are up to 9GB that are backed up over the weekend. I've noticed that SSHFS tends to have a lot of failures maintaining connections over periods of time, or rather when the network has a lot of traffic. In other words, during the weekend, it seems I have no drops in connection compared to weekdays as soon as the majority of users are here and using the network. This creates a lot of broken file transfers. It doesn't corrupt the data in any way, but it does force the transfer to start over the next time the script is run. (I use automated scripts that I created for many different backups). 

I am researching the use of a command/program that will resume the transfers by finding the end of the file and appending the data. Rsync has a resume feature, but it tends to compare data byte for byte, causing it to actually take the same amount of time, of not more, to finish the file. Better off just having it start the transfer over. 

The trick to EncFS, mainly if you use automated/scheduled scripts, is to have a check take place that the volume is correctly mounted. This way, you don't have a lot of files being copied locally (in our scenarios), that not only don't make it to the remote server, but also fill up the local drive. In other words, if you don't have the encrypted volume mounted to the unencrypted volume/folder, you can end up copying files to the local machine into the folder and not the encrypted volume. I hope that makes sense because it is kind of a confusing thing to explain to someone that may not be familiar with the ins and outs of EncFS. 

Overall, though, I have had good success and I don't see you ever having a problem with encrypted files getting screwed up. I use True Crypt at home for local backups and portability from Linux to Windows and have yet to lose any data because of so. The thing that is important with encryption is to NOT LOSE/FORGET your pass-phrase!! :) Once the pass-phrase is lost, your data is lost, so don't forget it. Other than that, the data has always been intact. 

> Thanks for the very quick and concise reply :) ( And a diagram! You do spoil me )

You're welcome. I love being able to share information whenever I can to help others. Especially when it's something I have direct (and possibly unique) experience with. 

-Cybie :guitar:

---

### Post by HermanAB on 2009-04-28
Howdy,

I believe you can do that with NFS.  If device partition /dev/sdb1 is an encrypted file system, then simply share the device node /dev/sdb1 with an appropriate line in /etc/exports.  

If /dev/sdb1 is encrypted and not mounted on the server, then a server user cannot access the file system, but a remote machine can mount the device using an entry in /etc/fstab and decrypt it.

---

### Post by Xyem on 2009-04-29
> The thing that is important with encryption is to NOT LOSE/FORGET your pass-phrase!!
Yeah. I have found that out recently. I had a ~160GB drive with a truecrypt volume on it and I took it out of my machine as I brought 2 * 500GB HDD. Now I don't remember the password ( in fact, I'm not even sure if I erased the encrypted data or not! ). It wasn't anything important as I was just playing with it but it is still annoying to lose some stuff :)
Thank you again for your insight

HermanAB, is it possible to mount NFS things via ssh? Also, same question as I put to Cybie, how tolerant is it to connection failures?

---

