---
title: "How can USB memory sticks be made secure?"
date: 2006-05-23
forum: Server Platforms
---

### Post by jonrkc on 2006-05-23
I started using a 2GB USB memory stick today but it doesn't seem a safe place to put my /home files, which contain ALL of my personal data--everything.  

Since Linux for whatever reason does not provide password protection that can be applied to files or directories, the only thing I could think of for safety was to encrypt a tar archive of my files and store that encrypted archive on the stick.  But that makes it impossible to access files from the stick as I can from other media.  

Is there any other way to safeguard data on a little device that's so easy to lose or have stolen, and still have the data readily accessible by authorized persons? Of course on my system, I can lock out any users from accessing the files on the device.  But if somebody else obtains the memory stick, won't it be easy as can be to access the files on another Linux system, as root?

---

### Post by Engnome on 2006-05-23
I dont know how to do it in Linux but I know a method to do it with a windows program, with it you can create an encrypted partition wich you can mount from the tray. I think the program was based on pgp but Im not sure.  I dont know if there is a Gnu/Linux counterpart for it though. 

Please post back here if you find one, I've searched for it but cant find it.

---

### Post by jonrkc on 2006-05-23
There's no way that I would call easy for Linux users like me.  Here's a description of one method:  [http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS](http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS)
but this is the kind of thing that I'm not ready for, and may never be.

When I used Windows it was really easy to encrypt and make invisible directories, files, partitions, you name it...  I hope someday someone will make that possible in Linux, too.  It looks like that day hasn't come yet.

Meanwhile, it just isn't practical at all to make a tar archive and then encrypt it and have that on the flash drive.  It takes forever to encrypt and decrypt, and it's just not worth the time and trouble.  I've had an offer to buy the flash drive for me--from a Windows-using friend--and I may just reformat it for Windows and take him up on it...  :(

[QUOTE=Engnome]I dont know how to do it in Linux but I know a method to do it with a windows program, with it you can create an encrypted partition wich you can mount from the tray. I think the program was based on pgp but Im not sure.  I dont know if there is a Gnu/Linux counterpart for it though. 

Please post back here if you find one, I've searched for it but cant find it.[/QUOTE]

---

### Post by Engnome on 2006-05-23
While searching for a better way you can always put it on youre keyring (if you have one) that way you might be a little more careful with it.  Even though it feels like you are being paranoid. Files on youre computer are not protected by passwords, boot acess = root acess. And if youre dekstop/laptop gets stolen and youre dokument are not encrypted he will have acess to them.

Edit: found this [http://ubuntu.wordpress.com/2006/01/24/use-an-encrypted-usb-drivepartition/](http://ubuntu.wordpress.com/2006/01/24/use-an-encrypted-usb-drivepartition/)

---

### Post by jonrkc on 2006-05-23
I'd be afraid I'd lose my keys and with it all my personal data for anybody to see (that knew enough to try the thing on a *nix system).  I think maybe a temporary solution would be to hide it in a "safe" (ha...) place--easy since it's so small--when I'm not home.  I'm thankful I never have felt paranoid, but I do feel reasonably concerned about somebody, especially a thief, having ALL my personal data (bank account stuff, insurance, Social Security, addresses and phone nos., etc.)

I lost a cell phone last year and though I canceled its use at once and didn't lose any money, I hated the thought of the person who found it (and didn't return it, making him or her a thief) having all those phone numbers stored in it.  I felt like I'd let my friends down by allowing their personal data to be stolen.

I agree about the desktop thing.  There's just no such thing as real security plus convenience.  Even if I lock the BIOS with a password and epoxy the little DIP switch that bypasses it shut, or break it off--there are still plenty of ways around that.  The simplest being just to yank the hard drives and put them in another machine.

I think keeping data on a computer still beats having it only on paper, though; you can't easily back up paper records.  And they are very stealable.  (Though they also last far longer than any magnetic or optical storage medium!)

Thanks for the Ubuntu link.  I think I've already read that, but I'll give it a look again.  I appreciate your help.

---

### Post by Engnome on 2006-05-23
No problem, I'm interested in a solution aswell... To bad that "cryptsetup" is terminal only. Im not good enough to code a gui to it, yet anyway. 
Maybe theres some way to suggest it as a project? If ubuntu put a bounty on it someone might do it.

---

### Post by jonrkc on 2006-05-23
[QUOTE=Engnome]No problem, I'm interested in a solution aswell... To bad that "cryptsetup" is terminal only. Im not good enough to code a gui to it, yet anyway. 
Maybe theres some way to suggest it as a project? If ubuntu put a bounty on it someone might do it.[/QUOTE]I don't mind doing things in a terminal, but I'm stymied by the luksFormat part of the instructions.  This is apparently something that cryptsetup provides (though this is not clear) but I don't know how to invoke it. I couldn't find the answer here on Ubuntu forums or with a Google search.  Apt-get reported no such package.  Trying the command with it anyway, resulted in no such program.  

I guess I'll keep prodding around, as this sounds like a moderately simple way to get what I want.  

Yes, a GUI would be good.  I prefer them most of the time, except for things I can accomplish faster using a command line--I'd say I do about 60% command-line operation, and 35% GUI, and 5% breaking out in a cold sweat not knowing what to do next.

---

### Post by Kelvin on 2006-05-23
Hi all,

It seems like encfs should work on a USB stick...perhaps? Anyone with more experience know the answer to this?  :-k 

Here's the Ubuntu Wiki page for normal setup...
[https://wiki.ubuntu.com/encryption_with_encfs_and_pam-encfs?highlight=%28encfs%29](https://wiki.ubuntu.com/encryption_with_encfs_and_pam-encfs?highlight=%28encfs%29)

I'll try it tonight and see if I can get it to work. Unless someone posts a definitive no before then.

---

### Post by jonrkc on 2006-05-23
I thought I'd give encfs a try, as it appears to be simple to implement.  But apparently the package encfs is not available for Hoary, which is what I use.  So much for that.

I'm eager to see if you get it working under Dapper, which I intend to move up to fairly soon after its release, though I hate like anything upgrading my system--I can never remember how to get lmsensors working with gkrellm, and things like that, and have to figure it all out again, despite notes I've taken!

---

### Post by Kelvin on 2006-05-23
I understand your reluctance to upgrade and go through the configuration/customization dance all over again. I just upgraded last week myself.

I'll let you how it goes with encfs on the USB stick. I'm heartened by this article though... sounds not only doable but a best practice, at least for this author.

[http://www.linuxdevcenter.com/pub/a/linux/2005/04/14/encfs.html](http://www.linuxdevcenter.com/pub/a/linux/2005/04/14/encfs.html)

---

### Post by jonrkc on 2006-05-23
It does sound like the easiest way I've read about yet.  But I couldn't locate the package to download using "sudo apt-get install encfs/universe".  And I note that I'd have the FUSE module in the kernel--getting it in is easy, but if it's something I have to compile...well, I have success with about 1 out of 20 programs or libraries I try to compile.

If you get it working well, maybe you can post step-by-step instructions, even if it doesn't work for Hoary and thus not for me.  It could be a help to a lot of USB flash users.  Thanks for the research!

[QUOTE=Kelvin]I'll let you how it goes with encfs on the USB stick. I'm heartened by this article though... sounds not only doable but a best practice, at least for this author.

[http://www.linuxdevcenter.com/pub/a/linux/2005/04/14/encfs.html](http://www.linuxdevcenter.com/pub/a/linux/2005/04/14/encfs.html)[/QUOTE]

---

### Post by Kelvin on 2006-05-24
No problem. I got part way through last night before needing to stop. I'll tackle it again and try to piece together a how-to, for dapper at least.

---

### Post by Engnome on 2006-05-25
Maybe this [http://www.shimari.com/dm-crypt-on-raid/](http://www.shimari.com/dm-crypt-on-raid/) can be helpful, just skip the raid part.

---

### Post by jonrkc on 2006-05-25
[QUOTE=Engnome]Maybe this [http://www.shimari.com/dm-crypt-on-raid/](http://www.shimari.com/dm-crypt-on-raid/) can be helpful, just skip the raid part.[/QUOTE]
I'm afraid that one's too complex and scary for this poor guy, but the article led me to some interesting security links, and it could be just the right thing for somebody more advanced than I am.  (Disclaimer: I *am* good at some things, but securing files doesn't appear to be one of them.)

---

### Post by vratnica on 2007-12-13
well jonrkc

what are u afraid of, has just happened to me

I lost my memory stick, and although I had not my home partition on it, I had there planty of privat pics

so thats something that upsets me very much (althought the pics are nothing to be shamed ofm but still I dont like MY pictures being someone elses ownership)

my stick wasnt fastned to the keys, but in the same pocket, so that was possibly the crucial mistake.

so now I want to by a new stick, I want to bind it to the keys, to get some pass for it, if possible, and still, i think I m never again going to put some private date on my stick, but only onto a CD

this was a big school for me

---

### Post by chewearn on 2007-12-13
> **vratnica said:**
> well jonrkc

what are u afraid of, has just happened to me

I lost my memory stick, and although I had not my home partition on it, I had there planty of privat pics

so thats something that upsets me very much (althought the pics are nothing to be shamed ofm but still I dont like MY pictures being someone elses ownership)

my stick wasnt fastned to the keys, but in the same pocket, so that was possibly the crucial mistake.

so now I want to by a new stick, I want to bind it to the keys, to get some pass for it, if possible, and still, i think I m never again going to put some private date on my stick, but only onto a CD

this was a big school for me

Do you realised you are answering to a thread that is one and a half years old?

Anyway, a "well known" solution to your problem (since you are encryting data files only, instead of home directories) is TrueCrypt:
[www.truecrypt.org](www.truecrypt.org)

---

