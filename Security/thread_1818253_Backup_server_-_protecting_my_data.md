---
title: "Backup server - protecting my data"
date: 2011-08-04
forum: Security
---

### Post by metalix on 2011-08-04
Hi,

I am building a small backup server, for backing up *my own* data and client projects. I think I have decided against using it to store backups of client data.

The server is a small PC sitting next to me in my home office. It has a removable hard-drive and a tape backup drive.

I am reluctant to use it to support backups as a commercial service (to small businesses), but I think it will come in handy for backing up my projects and other important stuff, and my own database.

My plan was to only boot it up on a certain night, when I would be doing backups, and then powering it down and removing the disk and tapes and storing them in a safe. That way, the risk of having the data stolen is much lower. But, there would be a cost to convenience, reliability and utility. I would love to leave it on every night to do daily backups.

My questions are:

1. Is there a way to encrypt the hard-disk, without having to rebuild the system?

2. What is the best way to ensure that everything stored on my tapes is encrypted?

3. Assuming that: a) the hard-disk was encrypted; b) the data on the tapes was encrypted; c) I had a strong fire-wall policy; d) I always logged out after use; do you think my data would be safe enough to warrant my computer being left running each night?

---

### Post by Beacon11 on 2011-08-04
Okay, I have a couple of questions in response.

1. You make it sound like you want to encrypt the entire hard disk. Is this indeed the case? I would suggest that the entire hard drive does not need to be encrypted-- just encrypt the parts you'd like to protect (e.g. a TrueCrypt volume). This would not require a reinstall, and TrueCrypt is pretty decent ([http://www.webcitation.org/query?url=g1.globo.com/English/noticia/2010/06/not-even-fbi-can-de-crypt-files-daniel-dantas.html](http://www.webcitation.org/query?url=g1.globo.com/English/noticia/2010/06/not-even-fbi-can-de-crypt-files-daniel-dantas.html)).

2. I would say use rsync over ssh, and have a TrueCrypt volume on each for the data. I would actually highly recommend this: [https://github.com/philcryer/lipsync](https://github.com/philcryer/lipsync) . Related is this: [http://fak3r.com/geek/howto-build-your-own-open-source-dropbox-clone/](http://fak3r.com/geek/howto-build-your-own-open-source-dropbox-clone/) .

3. Well, I guess that depends on what encryption you used, how secure your home office is, and what kind of data you secure. If you're encrypting, most important (and not present in your list) is KEY MANAGEMENT. This is really a question for you to answer since only you can put value on your data.

---

### Post by bodhi.zazen on 2011-08-04
> **metalix said:**
> Hi,

I am building a small backup server, for backing up *my own* data and client projects. I think I have decided against using it to store backups of client data.

The server is a small PC sitting next to me in my home office. It has a removable hard-drive and a tape backup drive.

I am reluctant to use it to support backups as a commercial service (to small businesses), but I think it will come in handy for backing up my projects and other important stuff, and my own database.

My plan was to only boot it up on a certain night, when I would be doing backups, and then powering it down and removing the disk and tapes and storing them in a safe. That way, the risk of having the data stolen is much lower. But, there would be a cost to convenience, reliability and utility. I would love to leave it on every night to do daily backups.

My questions are:

1. Is there a way to encrypt the hard-disk, without having to rebuild the system?

What do you mean "rebuild the system" ? If you want to encrypt the entire hard drive and installation, yes you need to re-install.

You do not need to reinstall to use encryption, you can use any number of encryption tools, my preference would be LUKS.

> 2. What is the best way to ensure that everything stored on my tapes is encrypted?

Are you sure you need to encrypt the backups ? They are locked in a safe and encryption adds a layer of complexity here. If the encryption fails you will loose your data.

Probably easiest thing to do is make an archive (tar, zip, etc) of your data and encrypt the archive, you can do this with gpg.

> 3. Assuming that: a) the hard-disk was encrypted; b) the data on the tapes was encrypted; c) I had a strong fire-wall policy; d) I always logged out after use; do you think my data would be safe enough to warrant my computer being left running each night?

No. If the entire installation is encrypted, or just the data partition, if it is running / in use it is decrypted. You need to shut it off.

---

### Post by Beacon11 on 2011-08-04
> **bodhi.zazen said:**
> No. If the entire installation is encrypted, or just the data partition, if it is running / in use it is decrypted. You need to shut it off.

Unless only home is encrypted (which is encrypted upon logout), or you have some encrypted volume (e.g. TrueCrypt) that should be locked when not in use.

EDIT: This might be useful metalix, if you're interested in encrypting your home directory: [https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome) . Make sure you read the caveats (e.g. encrypt swap, etc.).

---

### Post by bodhi.zazen on 2011-08-04
> **Beacon11 said:**
> Unless only home is encrypted (which is encrypted upon logout), or you have some encrypted volume (e.g. TrueCrypt) that should be locked when not in use.

True, but I do not get the impression that is what the OP means. I think the OP means the computer is on and the crypt is open so backups can be transferred. The computer is then left "on" with the data decrypted.

---

### Post by metalix on 2011-08-06
Thanks everyone for your useful replies.

@Beacon11, in response to your three points/questions:

1. Having an encrypted partition sounds great, and TrueCrypt does look like an impressive piece of software, but I was just reading a white paper by Bruce Scheier ([http://www.schneier.com/paper-truecrypt-dfs.pdf](http://www.schneier.com/paper-truecrypt-dfs.pdf)) which seems to suggest that having the entire hard disk encrypted makes more sense, as it protects against leackage.

2. I took a look at lipsync and it seems to be an excellent package for two way synchronisation. I am simply looking to do one-way synchronisation; that is, I was to maintain a remote image on my backup server of my production server (and other servers later) that I can backup onto my tapes. Rsync seems more suitable to this; what do you think? While I am on this subject, can rsync be used to maintain separate images that are synced at different times. I want to be able to maintain seven copies of the server which are rsynced on different days, so that I have quite a good window for spotting and fixing errors, before they overwrite all the "good" backups.

3. I've downloaded and printed this to read: [http://csrc.nist.gov/publications/nistpubs/800-57/SP800-57-Part2.pdf](http://csrc.nist.gov/publications/nistpubs/800-57/SP800-57-Part2.pdf). It is from 2007, do you think it is obsolete? 

This also brings up something else: in order to get data from my production server, I will be using a password-less private key for SSH. Although I will create a very limited account for the backup server to use, I am aware that if my backup server were to be compromised, my production server would be too. What other ways might there be to negate this risk?

@bodhi.zazen,

Would you recommend LUKS over TrueCrypt? If so, why?

I get your point about the added layer of risk to corruption of the data by encrypting the backups, though the safe that I am using is only a small (easily removable) one and could be opened with an angle grinder. Therefore, I do not want to rely on it for protecting my data. Also, I would like to be able to keep my tapes in the system whilst data is being backed up, safe in the knowledge that if it were to be removed by a burglar, that the data would be encrypted anyway. Is it common for encryption to fail? Does encrypting an archive make the data safer that simply encrypting the data itself?

I accept your point about the data being decrypted whilst the PC is running, regardless of whether I encrypt a volume or the whole disk. However, my rationale is:

1. The decrypted data is stored in RAM(?); if the disk was removed then all they would have is encrypted files (?). Are decrypted temp files and a decrypted swap partition also stored?

2. Locally, no users will be logged into the machine. In order to get in and look at the files, they would need to use SSH using the Ethernet port used for local access (all other incoming access is blocked)

My thoughts so far:

a. Encrypt the entire disk, to protect against leakage (only if the PC has been shut-down properly.

b. Have a volume for storing backed-up data (I want to have separate "images" for each day of the week, with an image rsynced on each day). The volume will be locked after use, so that even if the PC is stolen whilst in use, unless a backup was in progress, the actual data being backed up will be encrypted.

c. Because my home office offers almost no physical security, I should move the PC to the most secure location that is practical, i.e., near where I sleep, or in a loft area. When not in use for whatever reason, the hard disks should be locked in a safe (though the safe is not very secure either).

d. Archives, which will be encrypted, should be stored on the tapes. Backups onto tape will be done on one day each week, whilst I am sleeping (and in the building). When not in use, all tapes should be stored in a safe, maybe even off site.

With all this in mind, do you think I might just be better configuring a VPS with a reputable company and storing all my backups on there in an encrypted format. What are your thoughts on that?

Thanks for your advice so far, and sorry for this long post!

---

### Post by Beacon11 on 2011-08-06
You sir, have put thought into this. Good man!

Allow me to respond to your points.

1. That paper was about TrueCrypt's implementation of deniable file systems, not encryption. The only thing he mentioned about encryption was that Word saves backups and indexing software, well, indexes, which are two ways to leak. These are two things you shouldn't have to worry about on a dedicated server, where you aren't really doing such operations. Ignoring all this, TrueCrypt has come a long way since that paper was written.

2. Haha, how closely did you look at lipsync? It utilizes OpenSSH, rsync, and lsyncd. You can use it for one- or multi-directional backups. Basically, whatever you change at one location is picked up by lsyncd and is rsync'd over SSH to the others. So whatever you do on your laptop will automatically be backed up to your server. If for some reason you change stuff on your server, it will automatically be propagated to your laptop.

3. No man, that stuff won't go out of style for a long time. That's a great paper. I'll have to read all of it and think on your question.

One more thing: I need to refute something bhodi.zazen said earlier (please chime in bhodi.zazen if I misspeak):

> No. If the entire installation is encrypted, or just the data partition, if it is running / in use it is decrypted. You need to shut it off.

For TrueCrypt, please reference [http://www.truecrypt.org/docs/](http://www.truecrypt.org/docs/).

> Files can be copied to and from a mounted TrueCrypt volume just like they are copied to/from any normal disk (for example, by simple drag-and-drop operations). Files are automatically being decrypted on the fly (in memory/RAM) while they are being read or copied from an encrypted TrueCrypt volume. Similarly, files that are being written or copied to the TrueCrypt volume are automatically being encrypted on the fly (right before they are written to the disk) in RAM.

I can't imagine LUKS is different, or any other method of full-disk encryption. I'm still looking for sources there. EDIT: Here you go: [http://blog.andreas-haerter.com/2011/06/18/ubuntu-full-disk-encryption-lvm-luks](http://blog.andreas-haerter.com/2011/06/18/ubuntu-full-disk-encryption-lvm-luks) . Looks like LUKS is also on-the-fly.

Data on your hard drive isn't just sitting in clear-text. It's encrypted/decrypted as you need it in RAM and swap, even if you've mounted the encrypted partition. If you're booted up and I pull your hard drive, I won't be able to read a thing as long as you also encrypt swap (which you should obviously do).

---

### Post by bodhi.zazen on 2011-08-06
> **Beacon11 said:**
> Looks like LUKS is also on-the-fly.


Well, that is somewhat technical nitpicking. Sure secret_file is encrypted and decypted "on the fly".

But if the partition is mounted, cat will just as easily access the data.

```
cat secret_file
cp secret_file /media/flash_drive
scp secret_file some_server
```

So while technically the data may be "encrypted" it is easily accessible unless you unmount the partition.

---

### Post by Beacon11 on 2011-08-06
> **bodhi.zazen said:**
> Well, that is somewhat technical nitpicking. Sure secret_file is encrypted and decypted "on the fly".

But if the partition is mounted, cat will just as easily access the data.

```
cat secret_file
cp secret_file /media/flash_drive
scp secret_file some_server
```

So while technically the data may be "encrypted" it is easily accessible unless you unmount the partition.

Ah okay, we're looking at it from different angles. You from a software intrusion point of view, and me from a physical security point of view. I guess I assumed that's what the OP was worried about since he was talking about removing hard drives and putting them in safes. If he's worried about it being hacked it shouldn't even be on the network :P .

---

### Post by bodhi.zazen on 2011-08-06
> **Beacon11 said:**
> Ah okay, we're looking at it from different angles.

Indeed =)

I did not intend to be dismissive you your perspective, my intent was to point out a potential flaw.

You can leave the computer running, just unmount the crypt.

---

### Post by metalix on 2011-08-07
Thanks for the replies. Yes, this project is important to me. I am having a bit of an information audit over the next week to make sure everything is water tight.

@Beacon11,

Thanks for your thoughts. The swap, home volume and root volume are encrypted. In fact, I have a question about this: I've noticed that when encrypting the disk, there are 8 different key slots. Are any of these keys used for the encryption? I use a twenty character key (is that enough these days?), but if none of the keys are used to encrypt the data, then that it to some extent a waste of effort, right? I would be better just using a password I can remember. What do you think?

In addition, it will still be worth me making a TrueCrypt volume, too right?

In regards to using lipsync to backup my laptop's data. My laptop runs Windows 7 and will be connected to my backup server by Ethernet. Both the laptop and the server also have Internet connections too, but both will also have dynamic IP addresses, so I think it will be best to backup the laptop over local ethernet, as I can fix the IP addresses. Will this be workable do you think? Not ideal if I work away, but it's a start for now (in the future I will have a proper hosted backup server).

One thing is important though - if something does change on my server, I DO NOT want it updated to the production server or laptop. This is possible with lipsync, right?

@bodhi.zazen,

Thanks for your reply. Indeed, I was originally looking at it from a physical point of view. However, I am not questioning whether my box is adequately protected from intrusion. At the moment, I have iptables set up to only allow established incoming connections from the internet, and to only allow SSH going out across the internet. The internal LAN only allows SSH packets in, and established connections out. Obviously, I will modify this policy as I add additional services required.

Information security certainly isn't easy, is it!

This is certainly a very interesting discussion to me, and I want to thank you both for giving me your points of view.

---

