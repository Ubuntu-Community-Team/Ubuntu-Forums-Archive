---
title: "Full disk encryption + encrypted home folder"
date: 2012-01-08
forum: Security
---

### Post by MadsRC on 2012-01-08
So, for some time I've encrypted my home folder on my private PC, and have been using LUKS/LVM2 to "fully" (all, but the boot parttion) encrypt my other pc, with sensitive data on it.

Now, I want to do the same to my private PC, but I was wondering does having a fully encrypted disk + encrypted home folder have any disadvantages?

From what I can gather, the more layers you have in security, the more secure you are. So from that point of view, having a full disk encryption with password X and then, when booted up, there's s a encrypted home folder with password Y.

But, is there any disadvantages?

---

### Post by tubbygweilo on 2012-01-09
As long as you remember the pass phrases then no real problem. 
As always remember to backup user created data and keep a not of pass phrases safe and sound.

---

### Post by Ms. Daisy on 2012-01-09
MadsRC, What is your goal? What threat are you securing against?

---

### Post by MadsRC on 2012-01-10
There's no obvious threats, I'm just gathering information regarding security (and the current subject in my head is encryption).

And I read somewhere that the best form of security is layers.
One layer can be broken, 2 layers can too. But 2 layers take longer.

I'm just wondering if there is any obvious drawbacks?

---

### Post by Ms. Daisy on 2012-01-10
Encrypting the drive will help for physical security.  If someone is able to sit down in front of it or if they steal the computer they won't be able to see anything.  

In Ubuntu when you encrypt the home folder, it mounts when you log in which makes it readable to anyone sitting in front of your computer.  Once you log out, the folder unmounts and is encrypted again.

Are you extremely concerned about the physical security of your computer? If you're living in a dorm full of computer science majors, then yeah, I might double encrypt.  Encrypting the disk will do nothing to protect you from on-line threats, just so you understand what it does & doesn't do.  Don't know if you've read the [documentation on encryption]("https://help.ubuntu.com/community/EncryptedHome").

The drawback to encryption is that if you lose the key, you won't be able to recover your data. (if it were easy to guess the key then you've defeated the point of encryption). It's harder to recover the encrypted data if your hardware starts to fail.

When you hear about a layered security approach, what is generally referred to is layering security techniques.  The [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity") will describe them in detail, but layers would be:

[LIST]
[*] use strong passwords
[*] don't elevate privileges unless necessary
[*] backup your data
[*] update the operating system
[*] know how to secure the services you run
[*] secure your browser (like limiting scripts & ads)
[*] use common sense when browsing
[*] use a firewall
[*] secure your router
[/LIST]
Encryption is one layer in this basic multi-layer example. The [security sticky ]("http://ubuntuforums.org/showthread.php?t=510812")covers slightly more advanced security on Ubuntu.  You can add more layers, like AppArmor, HIDS, snort... it's kind of endless.  IMO you should just decide what the risks are to your computer, figure out how to defend against those risks, and then implement those defenses.

So that was probably way more than you were looking for- sorry if that's the case. I'm actually going to add more to the encryption section of the basic security wiki because what it defends against seems to be pretty widely misunderstood. Your timing was serendipitous.

---

### Post by MadsRC on 2012-01-10
Thank you for taking time to write a detailed post :D

Well, I already encrypt my home folder on one pc, and am using FDE on a pen test pc. Uses UFW and am setting up AppArmor

And physical access? Nah, If someone steals my laptop, it's because they want to sell it, and then they'll reformat the drive(s).

I've read the documentation and the BasicSecurity (startet at those back when I got interestet in the subject) but I'll read them again. Never hurts to read up on those things :D

But it doesn't seem like there are any drawbacks exept:

1: Slower performance
2: Harder recovery incase of hardware failure

And those would still be there if you only used one layer encryption and not 2 layer encryption (FDE + home folder encrpytion).

---

