---
title: "Questions Abount Ubuntu One"
date: 2011-03-18
forum: Ubuntu One (CLOSED)
---

### Post by nogoodnamesleft on 2011-03-18
Hi!

I would like to use Ubuntu One for backup

1) Is it able to automatically copy my files according to a schedule, or do I need to click to upload them via web each time?

2) If it does do it automatically, how does it handle changed files? Does it keep the last few versions of a file?

---

### Post by mr_luksom on 2011-03-19
I can't answer your second question, however as for syncing it happens automatically as files are changed (well, for me anyway). The proviso is that the files you want synced are placed in the directory nominated by Ubuntu One.

---

### Post by r-senior on 2011-03-19
> **nogoodnamesleft said:**
> I would like to use Ubuntu One for backup
I'd suggest you make sure you test it thoroughly before you start relying in it for backups.

It doesn't keep multiple versions of files that you can restore back to. One service I know that does that is Dropbox. This is specifically a cloud-based file mirroring service and doesn't have the additional sync services that Ubuntu One has.

Have a look at other threads in this sub-forum.

---

### Post by kendi on 2011-03-19
hey guys, I would like to jump in to this topic, to not open a new one, I hope it's not a problem.

My question is very simple; 
"How secure is our privacy of files we have on UbuntuOne storage?"

---

### Post by duanedesign on 2011-03-22
> **kendi said:**
> hey guys, I would like to jump in to this topic, to not open a new one, I hope it's not a problem.

My question is very simple; 
"How secure is our privacy of files we have on UbuntuOne storage?"

[https://one.ubuntu.com/privacy/](https://one.ubuntu.com/privacy/)

---

### Post by kendi on 2011-03-22
> **duanedesign said:**
> [https://one.ubuntu.com/privacy/](https://one.ubuntu.com/privacy/)
 
Hey, thanks for reply :)
So our files on ubuntuone storage are safe and encrypted ?
 
kind regards!

---

### Post by r-senior on 2011-03-22
> **kendi said:**
> So our files on ubuntuone storage are safe and encrypted?
That's not quite how I interpret it:

"We have security measures, including administrative, physical and electronic measures, to protect against the loss, misuse or alteration of information that we have collected from you in the use of the Ubuntu One service. These measures include SSL data encryption to transmit your data securely to Ubuntu One as well as technical architectures and systems to prevent unauthorised internal employees, contractors and affiliated organizations from accessing your data."

I take that to mean access is controlled, data is backed up and transmission of data is encrypted. But not necessarily that data is held on the servers in an encrypted form. My understanding is that it is not, although I believe I read somewhere that this has been proposed.

---

### Post by imblack on 2011-03-23
Dont know why but I always feel creeps while thinking of saving my data on cloud services.

---

### Post by kendi on 2011-03-23
> **r-senior said:**
> That's not quite how I interpret it:
 
"We have security measures, including administrative, physical and electronic measures, to protect against the loss, misuse or alteration of information that we have collected from you in the use of the Ubuntu One service. These measures include SSL data encryption to transmit your data securely to Ubuntu One as well as technical architectures and systems to prevent unauthorised internal employees, contractors and affiliated organizations from accessing your data."
 
I take that to mean access is controlled, data is backed up and transmission of data is encrypted. But not necessarily that data is held on the servers in an encrypted form. My understanding is that it is not, although I believe I read somewhere that this has been proposed.
 
Yeah, well my English is a bit poor :P
I was asking this question, cause I was thinking few days ago, "is there a place on web to store some "private" data ?" - probably not, to be **really **sure the data is safe :/
 
Thanks for the help and replys people :)
Kind regards!

---

### Post by Docaltmed on 2011-03-30
I would not suggest using U1 for a backup. The security issues are one. The second issue is a performance issue, as U1 has the habit of grabbing CPU by the handfuls to sync even small amounts of data. The transfer rate is pretty slow, regardless of network speed, so if you have a nominally large amount of data -- say, 14G -- it will seize your CPU and hold it hostage for days on end until the syncing is done.I once had a laptop lockup on me for 4 days straight while U1 tried to sync. Even after I stopped the sync, I had to rip U1 out by the roots to keep it from eating every slice of CPU that it could get its grubby paws on.

I think it makes more sense to backup to a secondary local disk, or a USB disk if you need offsite storage, and just use U1 as a secondary backup for a few super-critical-can't-lose-a-byte files. For this type of use, U1 ought to work perfectly well. But as an overall backup, I don't recommend it.

---

### Post by kendi on 2011-04-01
> **Docaltmed said:**
> 
I think it makes more sense to backup to a secondary local disk, or a USB disk if you need offsite storage, and just use U1 as a secondary backup for a few super-critical-can't-lose-a-byte files. For this type of use, U1 ought to work perfectly well. But as an overall backup, I don't recommend it.

Seems so, yeah. Just it would be nice to store somewhere on the web where everything is reachable anywhere. Having your data on 1 external drive is risky with 2 is less, and you need to have them with you to restore data you may need :)
Don't get me wrong, I really like Ubuntu 1, and for my little files it works great, that is what I need it covers it.

Kind regards!

---

### Post by victorhugo289 on 2011-04-04
> **Docaltmed said:**
> I would not suggest using U1 for a backup. The security issues are one. The second issue is a performance issue, as U1 has the habit of grabbing CPU by the handfuls to sync even small amounts of data. The transfer rate is pretty slow, regardless of network speed, so if you have a nominally large amount of data -- say, 14G -- it will seize your CPU and hold it hostage for days on end until the syncing is done.I once had a laptop lockup on me for 4 days straight while U1 tried to sync. Even after I stopped the sync, I had to rip U1 out by the roots to keep it from eating every slice of CPU that it could get its grubby paws on.

I think it makes more sense to backup to a secondary local disk, or a USB disk if you need offsite storage, and just use U1 as a secondary backup for a few super-critical-can't-lose-a-byte files. For this type of use, U1 ought to work perfectly well. But as an overall backup, I don't recommend it.

I agree with Docaltmed, I have synced 25 MB using the Ubuntu One folder in Ubuntu 10.10, and when I put the files it all worked very well, but it so happens that every time I log onto Ubuntu I see the CPU very high for a few minutes and the weird thing is that apparently Ubuntu One is not only syncronizing my files again but actually uploading them again! That's so bad. I am thinking that my next syncronization of files is gonna be done directly uploading files to the Ubuntu One website, not using the folder on /home/user, no way!

---

### Post by duanedesign on 2011-04-06
> **victorhugo289 said:**
> I agree with Docaltmed, I have synced 25 MB using the Ubuntu One folder in Ubuntu 10.10, and when I put the files it all worked very well, but it so happens that every time I log onto Ubuntu I see the CPU very high for a few minutes and the weird thing is that apparently Ubuntu One is not only syncronizing my files again but actually uploading them again! That's so bad. I am thinking that my next syncronization of files is gonna be done directly uploading files to the Ubuntu One website, not using the folder on /home/user, no way!

It should not be re-uploading files. When you first start Ubuntu One it scans your synced directories to see if any changes need to be uploaded. You can see the files in your queue by running the following commands. (this should show you if it is actually re-uploading files)

```
u1sdtool --waiting-metadata | wc -l
```

```
u1sdtool --waiting-content | wc -l
```

There are two queues content and metadata.

---

