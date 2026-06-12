---
title: "Free Antivirus"
date: 2016-05-05
forum: Security
---

### Post by Christian_Smith on 2016-05-05
I'm installing Ubuntu 16 on some computers at my work and my boss wants them to have antivirus. Now I know, you are much less prone to malware threats on linux, I still need to find something. I've been messing with it for awhile and so far I can't get one that's free that does what I want it to do. 

I tried ClamAV. But after I installed it, I went to eicar.org and downloaded their test virus and clam didn't stop it.

I found somewhere that said you can use avg but I cant find the .deb for it

I tried installing bitdefender and couldn't get it to work. 

Any suggestions?

---

### Post by Bucky Ball on 2016-05-05
*Thread moved to **Security**.*

Post a support thread for help with one of the ones you can't get to work? The apps you've mentioned are widely used and work fine for many so you've scratched them off the list pretty quickly. Sure there's plenty of potential help around.

---

### Post by Christian_Smith on 2016-05-05
> **Bucky Ball said:**
> *Thread moved to **Security**.*

Post a support thread for help with one of the ones you can't get to work? The apps you've mentioned are widely used and work fine for many so you've scratched them off the list pretty quickly. Sure there's plenty of potential help around.

Well it was sort of a 2 part question. I guess if you all recommend a certain one I've scratched off my list, I'd focus in on that one and figure it out. But my attempts so far have failed so I figured I'd better at least ask which is the most recommended before I give myself too much head ache.

---

### Post by howefield on 2016-05-05
This isn't necessarily a vote for clamav but it does detect the eicar test virus.

```
hugh@wily-laptop:~$ clamscan --infected --remove --recursive ~/Downloads
/home/hugh/Downloads/eicar_com.zip: Eicar-Test-Signature FOUND
/home/hugh/Downloads/eicar_com.zip: Removed.
/home/hugh/Downloads/eicarcom2.zip: Eicar-Test-Signature FOUND
/home/hugh/Downloads/eicarcom2.zip: Removed.
/home/hugh/Downloads/eicar.com: Eicar-Test-Signature FOUND
/home/hugh/Downloads/eicar.com: Removed.
/home/hugh/Downloads/eicar.com.txt: Eicar-Test-Signature FOUND
/home/hugh/Downloads/eicar.com.txt: Removed.

----------- SCAN SUMMARY -----------
Known viruses: 4305913
Engine version: 0.98.7
Scanned directories: 120
Scanned files: 413
Infected files: 4
Data scanned: 81.72 MB
Data read: 79.07 MB (ratio 1.03:1)
Time: 14.169 sec (0 m 14 s)
hugh@wily-laptop:~$ 
```

---

### Post by maglin2 on 2016-05-05
I think the OP is looking for a free AV with On-Access protection as well (from the way he says 'I went to eicar.org and downloaded their test virus and clam didn't stop it.').

The only such I know of is Sophos free for linux. It has no GUI though - terminal control only.

---

### Post by howefield on 2016-05-05
> **maglin2 said:**
> I think the OP is looking for a free AV with On-Access protection as well (from the way he says 'I went to eicar.org and downloaded their test virus and clam didn't stop it.').

Yes, quite possibly he is, I believe clamav does have an on access feature, it just needs configuring and for best results probably the current version.

---

### Post by Christian_Smith on 2016-05-05
I'll be honest, I didn't know what on access was. But I just googled it and yes. This will be for computers that are going out in the building and thus I can't rely on people checking things themselves.

---

### Post by Christian_Smith on 2016-05-05
So this may be wordy but this may clear up my situation... 

I work for a small company as something of the "local IT" guy among other things. The whole building is Windows XP and I'm trying to get us away from that. 
We are trying to go to Win10 but I've been pushing Ubuntu as an alternative for systems that only need Internet access and that's about it (to save us money)

We are currently running Sophos but it is maintained by another party. I would bet the "best" option would be to figure out how to get sophos on these ubuntu computers in a way that the enterprise can manage it but I'm assuming that was complicated. So I guess I was cheating and trying to just get a basic anti-virus on them so they have something and my boss is happy. 

But I'm starting to think I need to figure out sophos.

Edit: Well boss-man just shut me down. He'd rather just buy the licenses than deal with a different operating system in the building.

---

### Post by howefield on 2016-05-05
> **Christian_Smith said:**
> But I'm starting to think I need to figure out sophos.

That's easy enough, navigate through the [Sophos]("https://www.sophos.com/en-us/products/free-tools/sophos-antivirus-for-linux.aspx") and download the install file (about 409MB large), extract the downloaded file and run the following command (from the folder containing the extracted folder or use the path to it)

```
sudo sh install.sh
```

It will launch the install wizard and ask you several questions, once complete it will auto start. You will have on access scanning. Seriously easy. 

> Edit: Well boss-man just shut me down. He'd rather just buy the licenses than deal with a different operating system in the building.

Even easier....

---

### Post by maglin2 on 2016-05-05
> **Christian_Smith said:**
> 

Edit: Well boss-man just shut me down. He'd rather just buy the licenses than deal with a different operating system in the building.

I can understand that.

In the days when IBM were completely dominant they ran an Ad which just said:

'Nobody ever got fired for buying another IBM'

---

### Post by Christian_Smith on 2016-05-05
> **howefield said:**
> That's easy enough, navigate through the [Sophos]("https://www.sophos.com/en-us/products/free-tools/sophos-antivirus-for-linux.aspx") and download the install file (about 409MB large), extract the downloaded file and run the following command (from the folder containing the extracted folder or use the path to it)

```
sudo sh install.sh
```

It will launch the install wizard and ask you several questions, once complete it will auto start. You will have on access scanning. Seriously easy. 



Even easier....

Well I'm installing it anyway... haha. I've come this far

---

### Post by maglin2 on 2016-05-05
On my system Sophos uses about 430MB in normal operation (630MB during scans) - just to note in case those are machines without much RAM.

---

### Post by Habitual on 2016-05-06
I installed it for "grins and giggles" on two hosts.
Some of us 'forgot' to run rkhunter --propupd after doing so...

---

