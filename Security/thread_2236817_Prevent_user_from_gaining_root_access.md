---
title: "Prevent user from gaining root access"
date: 2014-07-29
forum: Security
---

### Post by Jaman42 on 2014-07-29
Hi,
Just wonder if this is possible. A device running Ubuntu 14.04 which have some files that I don't want the user to change, the user shouldn't be able to install additional software either so I have already disabled sudo for the user. 

**Main Question:** When I have enabled the root account and set a password for it can the user still use "recovery mode" to somehow get access to the root account or change any permissions?

On a side note I wonder if there is any way to prevent the user from simply removing the hard drive and accessing it from another computer (not using glue:p)? I was thinking some sort of encryption that automatically decrypt the drive if it is in the unit it's delivered in. Using MAC address or something like that as the key. This doesn't have to be un-crackable, just want to make it a little bit harder so the users won't bother. 

Would this be possible?

How about using home folder encryption together with auto-login? The user doesn't have to enter a password and if the hard drive is put in another unit as a secondary drive the home folder is encrypted?

Run a script at boot that decrypts the folder and obfuscate the code as much as possible?

Edit: I would also like to add that I realize putting the key / keyfile or what not outside of the encrypted folder defeats the purpose a bit but not entirely. I am willing to compromise security for zero user interaction. I am only looking for a way to make it a bit harder, not simply plug it in another computer and browse all the files if you get what I mean.

---

### Post by bapoumba on 2014-07-29
Once someone has physical access to a machine, only encryption can make it difficult to access data on a hard drive. No real need to enable a root account on ubuntu for regular (even admin) tasks. 
I'm not quite sure about your use case though or what you are trying to achieve or whom you are trying to protect from whom or what :)

---

### Post by Jaman42 on 2014-07-29
Hi! Thanks for answering. Yeah I now that encryption is needed to make it close to safe but I only want to make it a bit harder not safe. So the user really have to put in some effort to view the source of the files. One idea I had was to scatter files around referencing each other, obfuscating the code in each of them. So when one file is reversed you find out that it is a reference to another file and so on. With enough files this would be quite time consuming, right? Another computer would solve this quite quick but a human plugging in the disk in another computer browsing the files won't. Do you get what I am after?

My friend and I are playing around a bit with the idea, he is gonna make a system as well and then we are going to try and solve each others, yeah I know to much spare time right? :) So I am looking for ideas and to get some inspiration and learn new ways of making this harder. The main rule is that the system must be able to execute the file and run the code with zero user interaction using crontab, with less then 10 sec execution time. So you know where to start, and then make it as hard as possible to get to the end, revealing the code. We are both fairly new to linux so it would probably going to take some time to find the code but we are set to learn more about it and came up with this challenge. I am absolutely confident he won't read this post, since he is a honest guy and we booth had the option to chose a forum to get help. And off course not allowed to read in each others forum. Perhaps we don't even find a way to solve it but then hopefully we will learn a lot on the way.

And as I said I am well aware of that it is impossible to make a system like this unbeatable, just want to make it really, really tough to solve as you can imagine :).

---

### Post by ajgreeny on 2014-07-29
You can easily remove recovery mode from the grub menu to stop non-experienced users from booting to that mode by uncommenting the ```
#GRUB_DISABLE_RECOVERY="true"
```
line in the** /etc/default/grub** file.  Anyone who really knows what they are doing will soon overcome that trip-wire, but it is an extra deterrent for the newer user.

You could also passwprd protect the BIOS/UEFI, but again that is generally easily overcome, for BIOS at least, not sure about the intricacies of UEFI in that respect.

Making the user a normal user as opposed to a member of the admin or sudo group will also deter them to some extent if you want to stop installing applications, but as bapoumba has said, anyone who has physical access to a machine or its disks can very soon find whatever they want, unless it is encrypted, but there is where I bow out of this discussion as Ihave never needed or used an encrypted system.

---

### Post by bapoumba on 2014-07-29
Is this some kind of a game ?

---

### Post by Jaman42 on 2014-07-29
Thanks for the additional suggestions. Yea kind of, we figure the best way to learn is if faced with a problem that you have to solve, often by trail and error. Also it's a bit fun to see who wins, that adds some more motivation to the equation.

---

### Post by bapoumba on 2014-07-29
*Thread moved to **Security Discussions**.*
There are many knowledgeable people here. Beware, you wont be able to fool them around should you be up to something bad or illegal. If this is a private challenge, I see no harm showing you how to disable or at least move around bios boot sequence (to make it more difficult to boot from a live environment), lock down auto boot to a guest account with real low privileges, encrypt stuff or anything along these ideas. I'm not the one to be able to answer you because I have never tested most of that. The only thing I encrypt are usb sticks that I carry around and can (maybe) loose :)

To be fair to users here, are you going to report what you 2 are up to somewhere ? They should know in advance before they chime in.

---

### Post by Jaman42 on 2014-07-29
Thanks, that's why I choose this forum, seems to be a lot of experienced users that perhaps want to help in explaining how some things can be done to get the result I am looking for. And as I said, I am fairly new to Linux and my intentions is to learn as much as possible during this little competition with my mate. I won't report this anywhere other then perhaps here in this thread if someone is interested finding out how it went, if one of us eventually solves the problem that is.

---

### Post by thnewguy on 2014-07-29
Personally, it sounds to me like you are making this exercise more complicated than it needs to be. You're talking about scrambling files and moving things around, etc. Why do all that? If you want to prevent someone from gaining access to your files, simply use home folder encryption and choose a complex password. If you want to prevent people from using revoery mode, disable recovery mode in GRUB (as someone above suggested). Everything else is just making a lot of extra steps for yourself without gaining any real security.

---

### Post by CharlesA on 2014-07-29
> **thnewguy said:**
> Personally, it sounds to me like you are making this exercise more complicated than it needs to be. You're talking about scrambling files and moving things around, etc. Why do all that? If you want to prevent someone from gaining access to your files, simply use home folder encryption and choose a complex password. If you want to prevent people from using revoery mode, disable recovery mode in GRUB (as someone above suggested). Everything else is just making a lot of extra steps for yourself without gaining any real security.

This, for the most part. Unless you want to encrypt the entire drive, they would still have access via a livecd...

Physical access = root access, like always.

---

### Post by Jaman42 on 2014-07-29
> **thnewguy said:**
> Personally, it sounds to me like you are making this exercise more complicated than it needs to be. You're talking about scrambling files and moving things around, etc. Why do all that? If you want to prevent someone from gaining access to your files, simply use home folder encryption and choose a complex password. If you want to prevent people from using revoery mode, disable recovery mode in GRUB (as someone above suggested). Everything else is just making a lot of extra steps for yourself without gaining any real security.

Just doing some brainstorming to try and get some further. I said earlier in the thread that the system needs to be able to execute the file using crontab without any user interaction. This isn't possible if I use a complex password to encrypt the home folder is it?

Yeah to disable recovery mode seems like a good idea, I took a note of that. I'm confident that there are more ways of making it harder to get to the information in the file without user interaction. I respect your opinion but I don't think I am making the exercise more complicated than it needs to be, I have just started making things complicated. And I need more ideas to make it even more complicated. Thank you so far for all the input, already learned a whole bit.

> **CharlesA said:**
> This, for the most part. Unless you want to encrypt the entire drive, they would still have access via a livecd...
Physical access = root access, like always.

That's why I was thinking about obfuscating and trying to hide the file, since he will have physical access to the unit and may remove the harddrive. But as I said, I am only brainstorming to try and come up with a solution to make it as hard as possible following the guidelines.

---

### Post by thnewguy on 2014-07-31
It sounds like you're saying root needs to have access to run a file, but at the same time you don't want someone with the root account to be able to access/read the file. That is a bit of a contradiction. You could do something where cron executables a script and that script checks to see if your user is logged in. Assuming your user is logged in (your home folder would then be unencrypted) then the script runs the file you are protecting. If you are not logged in then the file is encrypted and cannot be accessed. This would basically mean when you are at the computer the crontab job runs properly, but when you logout the cron job doesn't get run. Best of both worlds.

---

### Post by Jaman42 on 2014-08-01
Hi, thanks for the input.

"[COLOR=#000000]It sounds like you're saying root needs to have access to run a file, but at the same time you don't want someone with the root account to be able to access/read the file"
[/COLOR]Then perhaps I explained it wrong, the user isn't going to have access to the root account. The user is going to have a basic account removed from the sudo group.

If I use a encrypted home folder as you suggest, it isn't possible to use auto login is it? I need it to work without user input, otherwise I would just encrypt the whole system.

*Edit: This is more of a programming approach but I must also think about what programming language to use, if the end file is a compiled obfuscated file (perhaps C) then it would off course make things harder then for example Python.

---

### Post by Jaman42 on 2014-08-01
I got another idea that I need some help with to pull off. I couldn't quite let go of the encryption idea so i was reading up on it. I understand some parts of what I read and I know what I want to do but I am not sure how to do it. I want it to work like when you encrypt the entire drive but I want to use a keyfile on a USB stick to unlock the partitions. Since I need to give him the unit and the USB stick in this case I read something about hiding the keyfile between the MBR and the first partition. I was planning on doing this and make the rest of the partiton into a usb installer for Ubuntu. That would probably be quite deceptive for a beginner and would buy me quite some time I hope.

I also came across this quote "Security through obscurity is bad" a couple of times :). It's just one of the steps I want to do, buying me some extra time.

So where do I start?

Thanks everyone for reading and giving me advice.

---

### Post by ian-weisser on 2014-08-01
If you put the keyfile in a foolish place on the hard drive, the OS (or partitioner or bootloader) may not realize it's vital data and may happily overwrite it. Or you may happily overwrite it yourself when you repartition the drive to make more room for games or porn or whatever, or when you run a disk utility with the wrong options. Then your encrypted data is *gone*. Forever.

You can use a keyfile on a USB stick...but what happens when you lose the stick, or send it through the laundry? Then your encrypted data is *gone*. Forever.

You can keep a backup copy of the cleverly-hidden key somewhere...but how will you secure it? If someone gets hold of your backup, they have your key and all your data is theirs. Or, worse, the day you need the backup you discover it's corrupt (or overwritten) after a year sitting forgotten in the drawer. Then your encrypted data is *gone*.

Look back through the myriad old threads here: "Hey, I lost/deleted/overwrote my key; how do I recover all my encrypted data?" You don't. It's random gibberish now.

---

### Post by Jaman42 on 2014-08-01
Hi, thank you for your input. In my case it doesn't really matter if I loose the keyfile or not, I am trying to do this to learn how it all works. What can be done and how to do it, I fully understand that using a strong pass phrase that you can remember and don't write down anywhere with your encryption is the way to go. However I can't do it like that this time because the system needs to be automated as per previous posts.

But if your worried about loosing the keyfile can't you just use a strong password in another slot? So you can decrypt and perhaps make a new keyfile, that way if you loose your keyfile you can remove it and make a new one?

Found this blog post but its pretty old so I don't know if it is applicable for Ubuntu 14.04? [http://blog.andreas-haerter.com/2011/06/18/ubuntu-full-disk-encryption-lvm-luks](http://blog.andreas-haerter.com/2011/06/18/ubuntu-full-disk-encryption-lvm-luks)

Any other input?

*Edit: Realized I posted the wrong link, can't find the one I meant atm but I'll have to try some and see if I can figure it out, been doing some more reading today and it doesn't seem to complicated.

---

### Post by Jaman42 on 2014-08-03
So I have generated a keyfile with random data, added the keyfile with luksAddKey and got it working when just storing the keyfile plain on a USB and that's fine for a start.

I edited /etc/crypttab to unlock with the keyfile stored on the usb, now to the new question. 

Is it possible in /etc/crypttab to read from sectors on the USB instead of specifying a path to a file?

Thanks for reading

---

