---
title: "Two passwords, 1st normal, 2nd triggers system format ?"
date: 2011-01-17
forum: Security
---

### Post by remi_2 on 2011-01-17
Hi, 

I'd like to know if something like this already exists : 

have an ecryptfs encrypted user account on a laptop that accepts two logins, 1st logs normally, the second triggers a system format ?

Best regards

---

### Post by Joe of loath on 2011-01-17
I know truecrypt can give you two passwords for an encrypted disk, one to open a secure OS and one to open your regular OS. Any use?

---

### Post by endotherm on 2011-01-17
ultimately, the only way to really destroy data in realtime is either mechanical or electromagnetic. there are several portable devices that claim to be able to do this, but you do need a combo of specialized hardware and software to make it happen. 

in your circumstances, the likely hood is that as soon as the attacker realizes what is happening they will just kill the machine to stop the data loss. since you are obiviously worried that your encrypted data will be analyzed and decrypted, that doesn't help you much. second, formatting is not a secure operation and can be undone unless the disk surface is scrubbed (which can take days on large volumes).

additionally, your criteria requires an event to occur, resulting in an action, and for that to happen, software has to be listening for that event. all the attacker has to do is move the data to another device that does not have software waiting for the event (perhaps a custom version of the libs for encryptfs), using something like a live CD or just physically moving the drive.

in the long run, check out the intro sequence to the (terrible, yet funny) movie "The Core". the "Hacker" character uses modified difibulator paddles (changed to an EM feild generator) to erase all his drives in about a minute. no idea if the physics actually backs that up however. intriguing idea.

---

### Post by remi_2 on 2011-01-25
Haha didn't know about the defibrillator technique :). Well you're right it seems like anyone with the will to hack into a system will succeed unless you really use the most advanced machinery, so I think I'll just stick with ecryptfs. At some point I was also think of having something that dependending on the password, woudl either mount an ecryptfs home (the real one) or another home folder used as a deterrent, in which sensitive files would be unavailable. Like having two systems in one without anyone knowing about it. So under pressure you would give away the deterrent.

thanks.

---

### Post by Joe of loath on 2011-01-25
> **remi_2 said:**
> Haha didn't know about the defibrillator technique :). Well you're right it seems like anyone with the will to hack into a system will succeed unless you really use the most advanced machinery, so I think I'll just stick with ecryptfs. At some point I was also think of having something that dependending on the password, woudl either mount an ecryptfs home (the real one) or another home folder used as a deterrent, in which sensitive files would be unavailable. Like having two systems in one without anyone knowing about it. So under pressure you would give away the deterrent.

thanks.

What you are describing here is similar to truecrypt's 'Hidden OS' feature. I believe they call it 'Plausible deniability'.

---

### Post by remi_2 on 2011-01-25
> **Joe of loath said:**
> What you are describing here is similar to truecrypt's 'Hidden OS' feature. I believe they call it 'Plausible deniability'.

that's the idea, except I wanted to take it one step further and trash the data in case something goes wrong.

---

### Post by raspb3rry on 2011-01-27
If you use Truecrypt's hidden OS-function, you could install Ubuntu as the hidden one, and something like tinycore as the ordinary. Then you would have to make tinycore run in ram, which would allow you to run a script when tinycore is booting that would wipe your entire harddrive. 
I'm using tinycore as an example, because it is the smallest and fastest OS I know. 
But since the truecrypt-encrypted partitions is already encrypted, it might would be easier/faster to simply just wipe the encryption-headers and the backup of these (See [http://www.truecrypt.org/docs/volume-format-specification](http://www.truecrypt.org/docs/volume-format-specification)). 
  To the best of my knowledge it would be impossible to decrypt a volume, if the encryption headers are missing. (Unless you crack the algorithm itself, I suppose).

---

