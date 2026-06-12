---
title: "Best Encryption Software?"
date: 2010-06-10
forum: Security
---

### Post by GrantStoner on 2010-06-10
I'm looking for a great encryption tool WITH a GUI and that can encrypt my entire hard drive, including /boot (so I have to input a password before Ubuntu even starts to load). TrueCrypt does this, but only in Windows. What is the strongest encryption software like this for Linux?

---

### Post by FuturePilot on 2010-06-10
You can do that using the alternate install CD. The only thing is it won't encrypt /boot since that needs to be accessible by Grub to boot. However, everything else is encrypted and you get prompted for a password when you boot up.

---

### Post by GrantStoner on 2010-06-10
Doesn't that just encrypt the /home directory? And does the CD install the encryption software so I can manage it from within Ubuntu after I log in, but without the CD?

---

### Post by FuturePilot on 2010-06-10
> **GrantStoner said:**
> Doesn't that just encrypt the /home directory? 
That is one of the options. There is another to set up full disk encryption.

> And does the CD install the encryption software so I can manage it from within Ubuntu after I log in, but without the CD?

Yes.

---

### Post by GrantStoner on 2010-06-10
Awesome, thanks this sounds like exactly what I'm looking for, minus the /boot issue. This includes the swap space partitions too correct?

---

### Post by FuturePilot on 2010-06-10
> **GrantStoner said:**
> Awesome, thanks this sounds like exactly what I'm looking for, minus the /boot issue. This includes the swap space partitions too correct?

Yes.

---

### Post by GrantStoner on 2010-06-10
With this CD will I have re-install Ubuntu as well? And by any chance, do you know if it uses on-the-fly-encryption?

---

### Post by rookcifer on 2010-06-10
> **GrantStoner said:**
> Awesome, thanks this sounds like exactly what I'm looking for, minus the /boot issue. This includes the swap space partitions too correct?

With *software* encryption there is really no possible way to encrypt the /boot directory.  You would need a drive with built-in hardware encryption (or something that uses a TPM) for that.

One thing you can do is put /boot on a flash drive and remove it from the machine whenever finished with it.  This would be equivalent to having /boot encrypted (although I see little value in having /boot encrypted at all.  Nothing of import is ever stored there.  As long as /, swap and /home are encrypted you're golden).


> **GrantStoner said:**
> With this CD will I have re-install Ubuntu as well?

Yes.

>  And by any chance, do you know if it uses on-the-fly-encryption?

On-the-fly encryption is only useful for instances where only certain directories are encrypted (as is often the case with Truecrypt containers).  What LUKS does is encrypt the *entire* drive (minus /boot).  Since the entire drive is encrypted, there is no need for "on-the-fly."  Remember, in either case, encryption is only useful when the drive is **not in use** or when the "on-the-fly" container is not unlocked.

---

### Post by GrantStoner on 2010-06-10
Alright thanks then, it looks like that is the route I'm going to take then.

---

### Post by FuturePilot on 2010-06-10
> **GrantStoner said:**
> With this CD will I have re-install Ubuntu as well? 

Yes you will have to reinstall.

> **rookcifer said:**
> With *software* encryption there is really no possible way to encrypt the /boot directory.  You would need a drive with built-in hardware encryption (or something that uses a TPM) for that.
There was some patches to Grub2 to give it support for booting a LUKS encrypted system that included /boot in the encrypted area. So it *is* possible.

> **GrantStoner said:**
> And by any chance, do you know if it uses on-the-fly-encryption?

> **rookcifer said:**
> On-the-fly encryption is only useful for instances where only certain directories are encrypted (as is often the case with Truecrypt containers).  What LUKS does is encrypt the *entire* drive (minus /boot).  Since the entire drive is encrypted, there is no need for "on-the-fly."  Remember, in either case, encryption is only useful when the drive is **not in use** or when the "on-the-fly" container is not unlocked.

No, LUKS is a form of on-the-fly encryption.

> is a method used by some encryption programs, for example, disk encryption software. "On-the-fly" refers to the fact that the files are accessible immediately after the key is provided, and the entire volume is typically mounted as if it were a physical drive, making the files just as accessible as any unencrypted ones.
[http://en.wikipedia.org/wiki/On-the-fly_encryption]("http://en.wikipedia.org/wiki/On-the-fly_encryption")

Basically anything that presents the data to the end user transparently is on-the-fly. This would include things like TrueCrypt, Ecryptfs, and Encfs in addition to LUKS. GPG would be an example of the opposite of on-the-fly encryption.

---

### Post by GrantStoner on 2010-06-10
You say it is possible to encrypt /boot? Karmic uses Grub2 correct? How would I go about encrypting /boot this way? Is it an obvious choice when I'm encrypting? Or is there some sneaky method to it?

---

### Post by FuturePilot on 2010-06-10
> **GrantStoner said:**
> You say it is possible to encrypt /boot? Karmic uses Grub2 correct? How would I go about encrypting /boot this way? Is it an obvious choice when I'm encrypting? Or is there some sneaky method to it?

The patches have not made it into a Grub2 release yet and I'm really not sure of their status at this point. So as of now, it's not possible unless you're willing to do some Grub2 hacking.

---

### Post by GrantStoner on 2010-06-10
Oh, haha, I'm only on my 6th month using Ubuntu, no Grub hacking for me yet. So to make sure I have things right, 1) download-->burn-->boot Alternate CD, 2) install as normal use encryption option (which will encrypt everything except /boot)? And then just finish the installation process as I normally would if I was using the Desktop CD?

---

### Post by FuturePilot on 2010-06-10
> **GrantStoner said:**
> Oh, haha, I'm only on my 6th month using Ubuntu, no Grub hacking for me yet. So to make sure I have things right, 1) download-->burn-->boot Alternate CD, 2) install as normal use encryption option (which will encrypt everything except /boot)? And then just finish the installation process as I normally would if I was using the Desktop CD?

No you have to do the whole thing from the alternate CD. I forget what the option says exactly but it should be something like "Set up encrypted LVM". It may still ask you if you want to encrypt your home directory later in the process but that's not necessary since you've encrypted the entire disk already.

---

### Post by GrantStoner on 2010-06-10
Alright, thanks. I'll post if I have problems with it.

---

### Post by rookcifer on 2010-06-10
> **FuturePilot said:**
> Yes you will have to reinstall.


There was some patches to Grub2 to give it support for booting a LUKS encrypted system that included /boot in the encrypted area. So it *is* possible.

Interesting.  I wasn't aware of these patches but I guess it is logical that GRUB could be hacked to do this.


> No, LUKS is a form of on-the-fly encryption.


[http://en.wikipedia.org/wiki/On-the-fly_encryption]("http://en.wikipedia.org/wiki/On-the-fly_encryption")

Basically anything that presents the data to the end user transparently is on-the-fly. This would include things like TrueCrypt, Ecryptfs, and Encfs in addition to LUKS. GPG would be an example of the opposite of on-the-fly encryption.

I suppose it depends on what the OP meant when he said on-the-fly.  I think he was referring to having an encrypted container (*not a whole partition*) that one is able to unlock *after* the machine has booted.  This is sort of like many people do with Truecrypt; instead of encrypting the whole drive, they encrypt a large container on the drive that can remain locked even after boot.  Once they open the container, data can be removed to and from the container and encrypted/decrypted "on-the-fly."  Very similar to encryptfs, except without having to encrypt the entire /home parition.

So, if the OP is asking whether LUKS can create an encrypted container on a drive (that is, a container that can be a single directory and not a whole partition), the answer is no (if it can be done, I am not aware of it).  If he simply meant does LUKS use an on-the-fly method of operation in general, then the answer is obviously yes.  As you pointed out, technically, WDE constitutes "on-the-fly" encryption.

OP,[ here]("http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/") is a nice guide for accomplishing WDE with the alternate CD.  The guide is for 8.04 but it works the same for 10.04.

---

### Post by FuturePilot on 2010-06-10
> **rookcifer said:**
> 
So, if the OP is asking whether LUKS can create an encrypted container on a drive (that is, a container that can be a single directory and not a whole partition), the answer is no (if it can be done, I am not aware of it). 

It can be done :). Basically you create a pre-defined size file for your container using dd, set it up with the loop device (/dev/loop0), set it up with cryptsetup, put a filesystem on it and mount it.

---

### Post by GrantStoner on 2010-06-10
Actually, rookcifer, I was talking about the encrypting the entire drive, including everything I can, not just encrypting a specific directory. Will encryptfs allow me to do that without having to reinstall Ubuntu? I don't want just a directory or container encrypted, I want everything except /boot encrypted.

---

### Post by rookcifer on 2010-06-11
> **GrantStoner said:**
> Actually, rookcifer, I was talking about the encrypting the entire drive, including everything I can, not just encrypting a specific directory. Will encryptfs allow me to do that without having to reinstall Ubuntu? I don't want just a directory or container encrypted, I want everything except /boot encrypted.

I guess the confusion came after I explained that LUKS encrypts your whole drive (except /boot) and then you asked whether it also did "on-the-fly."  From that I assumed you must have a different definition of "on-the-fly" than that of WDE.

At any rate, if you want everything encrypted you will have to reinstall with the alternate CD using the directions I posted in one of my previous posts.

---

### Post by GrantStoner on 2010-06-11
I understood that "on-the-fly-encryption" (OFTE) meant data was encrypted first, then written to your system. So basically it's encrypting everything in real time while it's being written to your system, so that nothing is ever temporarily unencrypted. Whereas other methods decrypt your drive when you input the password or key file, and then system is unencrypted until you power-down your computer? Am I wrong?

---

### Post by rookcifer on 2010-06-11
> **GrantStoner said:**
> I understood that "on-the-fly-encryption" (OFTE) meant data was encrypted first, then written to your system. So basically it's encrypting everything in real time while it's being written to your system, so that nothing is ever temporarily unencrypted. Whereas other methods decrypt your drive when you input the password or key file, and then system is unencrypted until you power-down your computer? Am I wrong?

If you encrypt your whole disk, everything will either be encrypted or unencrypted at the same time.*  That is, after you enter your LUKS password at boot, your system is no longer protected.  Likewise when you shut your machine off, the drive is encrypted and the files cannot be retrieved.

*And before someone objects, it is true that *technically,* LUKS is encrypting/decrypting on-the-fly while the machine is running, but it's completely transparent to the user since the key is in memory and unlocks/locks everything as needed.  I just figured if someone was asking the question OP is that they didn't need to know these details.  Unless you are a crypto developer, it's easier to think of it as a binary proposition -- that is, the drive is either encrypted or not.  On or off.  Technically it's not that simple, but it's good enough of an explanation for the curious end-user, especially considering that there is zero security for the files while the drive is booted.  It doesn't matter that most files are technically encrypted until they are accessed -- they can still be easily accessed by anyone behind the keyboard.

---

### Post by GrantStoner on 2010-06-11
> **rookcifer said:**
>  -- that is, the drive is either encrypted or not.  On or off.
This brings up another question I had. Say, for some reason, I booted and unencrypted my laptop and was using it like normal, but for whatever reason I needed to cut power to it immediately and instead of going through the normal shut-down option, I just popped out the battery? Would my drive still be encrypted if someone else turned it on? Or would it be unencrypted still from my last use?

---

### Post by FuturePilot on 2010-06-11
> **GrantStoner said:**
> This brings up another question I had. Say, for some reason, I booted and unencrypted my laptop and was using it like normal, but for whatever reason I needed to cut power to it immediately and instead of going through the normal shut-down option, I just popped out the battery? Would my drive still be encrypted if someone else turned it on? Or would it be unencrypted still from my last use?

It would still be encrypted.

---

### Post by GrantStoner on 2010-06-11
Awesome. Does anyone here know what encryption algorithm Ubuntu/LUKS will use then I'm setting up my new system? Do I have a choice? Or is there only one?

---

### Post by FuturePilot on 2010-06-11
> **GrantStoner said:**
> Awesome. Does anyone here know what encryption algorithm Ubuntu/LUKS will use then I'm setting up my new system? Do I have a choice? Or is there only one?

AES is the default but there are others to choose from.

---

### Post by GrantStoner on 2010-06-11
Thanks everyone, looks like I'm pretty set now.

---

### Post by GrantStoner on 2010-06-12
Alright everyone, crypt setup was successful. Thanks for the help. If possible, I was wondering where/how I could get a program or if there was a way to test the encryption now, just to make sure there's no holes or anything. And also, I was not presented with an option to change the encryption algorithm (or cascade), so I was hoping to be able to test the default now and make sure it's golden.

---

### Post by rookcifer on 2010-06-12
> **GrantStoner said:**
> Alright everyone, crypt setup was successful. Thanks for the help. If possible, I was wondering where/how I could get a program or if there was a way to test the encryption now, just to make sure there's no holes or anything. And also, I was not presented with an option to change the encryption algorithm (or cascade), so I was hoping to be able to test the default now and make sure it's golden.

You can change the algorithm from within the menu (I can't recall how off my head, but it can be done).  

In any case, the default is aes-256-cbc with SHA256.  This is extremely strong (probably too strong since your password likely is nowhere near 256 bits in strength).

---

### Post by GrantStoner on 2010-06-12
I'm not sure how many bits it is, but it's either 64 or 65 characters long, and includes capitals, lower case letters, and special characters. How would you tell how many bits your pw is? And you said you can change the algorithm from within the menu? Is this the menu as you're installing Ubuntu? Or is there some kind of menu within Ubuntu I can use to change preferences?

---

### Post by FuturePilot on 2010-06-12
> **GrantStoner said:**
> I'm not sure how many bits it is, but it's either 64 or 65 characters long, and includes capitals, lower case letters, and special characters. How would you tell how many bits your pw is? And you said you can change the algorithm from within the menu? Is this the menu as you're installing Ubuntu? Or is there some kind of menu within Ubuntu I can use to change preferences?

During the install there is a menu where you can choose what algorithm to use. I don't remember exactly where it is, but it's definitely there because I've used it before.

---

### Post by rookcifer on 2010-06-13
> **GrantStoner said:**
> I'm not sure how many bits it is, but it's either 64 or 65 characters long, and includes capitals, lower case letters, and special characters. How would you tell how many bits your pw is?

If you're using a truly *random* password of 64 characters in length that spans all 94 ascii printable characters (excluding whitespaces), then your password is much stronger than 256 bits.  It's more on the order of 420 bits.

Password entropy can be calculated with the following formula:

```
log2(n) * l

Where n = number of possible characters in password
Where l = length of password

```

Congratulations on having a phenomenal memory! :p

> And you said you can change the algorithm from within the menu? Is this the menu as you're installing Ubuntu? Or is there some kind of menu within Ubuntu I can use to change preferences?

You do it during the install.  I believe the options are AES, Twofish, and Serpent.  All offer 128, 192, or 256 bits, iirc.

---

### Post by GrantStoner on 2010-06-13
> **rookcifer said:**
> You do it during the install.  I believe the options are AES, Twofish, and Serpent.  All offer 128, 192, or 256 bits, iirc.

Does it allow you to cascade?

---

