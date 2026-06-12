---
title: "GPG best practices"
date: 2010-07-24
forum: Security
---

### Post by Umang on 2010-07-24
Hi,

I'm not sure whether I've treated my gpg keys in the safest way possible, so I'd like to know what you think I should do and advise for the future.

I generated two key pairs in 2008 and haven't treated them as best as I should have. However,  I've not yet really used them for anything terribly important (and really have only used one of the two for the few things I've used it for - signing things for LP, etc), so I'm only asking my question to get some advice for the future.

I've simply copied my ~/.gnupg directory onto a CD every time I've needed to transfer my keys and don't really have the raw private key on a CD in a safe/locker. I've not been super careful with the CD either (however, I do still have it and I know for sure that nobody else has touched it). I don't have a revocation key. On a few occasions, I may have sent a tarball of my ~/.gnupg directory to myself by email. However, both my email password and gpg passphrase are randomly generated with a mix of lowercase, uppercase and numeric characters.

I've read about how careful you should be with your gnupg keys and I'm just wondering whether I've been careful enough.

Also, should I generate a new key now, what should I do to the old key? Do I need to treat the need key more carefully than I have until now?

Thanks

---

### Post by Bachstelze on 2010-07-24
If you sent your keys as a tarball to yourself via unencrypted email, there is a possibility that someone got them (I personally always use scp to transfer keys between machines).  What I would do is just revoke your keys and create new ones.  It's not urgent since no one apparently has your passphrase, but do it when you can.

What I do is: use the "encrypted home directory" feature of Ubuntu so that my keys aren't leaked if the computer is stolen, and use an encrypted channel (FTPS, HTTPS, scp/sftp, encrypted email...) when I need to copy them to another machine.

---

### Post by Umang on 2010-07-24
Thanks! I'm not very afraid of my keys being stolen in transit (my IMAP and SMTP are both through SSL)

So what you are saying is it is OK to just keep your ~/.gnupg directory and not have to go through getting the raw private key (unprotected by passphrase), putting it in a locker, keeping a revocation key also in a safe place, etc?

---

### Post by noway2 on 2010-07-24
One of our forum members, rookcifer, has one of the best posts on GPG key management and security that I have read.  Here is a link: [http://rookcifer.blogspot.com/](http://rookcifer.blogspot.com/)

One option, that is covered in the blog, is to create a secured volume on removable and mountable media such as a USB stick or CD.  Then you can put your keyring in there and mount it when needed.  Another option, once it has been sufficiently encrypted is to put it in cloud storage so you can access it when needed.

---

### Post by Bachstelze on 2010-07-24
> **Umang said:**
> 
So what you are saying is it is OK to just keep your ~/.gnupg directory and not have to go through getting the raw private key (unprotected by passphrase), putting it in a locker, keeping a revocation key also in a safe place, etc?

No, I'm saying that I personally don't do it (I must have the revocation certificate somewhere, but I'd have to look for it).  As with all security measures, it depends what you want to protect against.  I don't keep safe copies of my keys because they are on 5 different computers, and I don't think anyone would go through the trouble of stealing all of them (one being in a datacenter over 9,000 miles away from here) just to keep me from using them.

---

### Post by Umang on 2010-07-24
Alright, so it seems keeping it reasonably encrypted implies it is safe enough to store on the cloud. So I haven't done anything really unsafe here. Of course, it would be foolish to use the same password for the tarball and the gpg key because a chain is only as strong as its weakest link.

Thanks for the link and the suggestions both of you!

---

