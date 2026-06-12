---
title: "Linux version of TrueCrypt Hidden OS"
date: 2010-10-07
forum: Security
---

### Post by Resist on 2010-10-07
I was wondering if there is a way of creating a hidden OS with Linux, similar to what TrueCrypt does in Windows.  Anyone know if it is possible?

Also found something interesting called LFDE (Linux Full Disk Encryption), it allows you to encrypt your whole HD and put the boot partition on a USB stick.  Seems pretty cool but still doesn't allow for plausible deniability.  

[www.lfde.org](www.lfde.org).

---

### Post by iponeverything on 2010-10-07
"plausible deniability"  

Is this something like "I didn't know my system had a hidden encrypted partition"?  It does not sound very plausible.

I use full disk encryption from the alternate disk. I like the unencrypted /boot partition with the key in my head for 2 reasons. First, I don't have worry about loosing the usb key and second -- when I travel, if my laptop gets lifted, it is probably even odds that usb key will be with it. 

I am really not that worried about loosing a $1500 laptop, I much more worried about someone gaining access to my banking and financial information..

---

### Post by Resist on 2010-10-07
Something like that, yes.  They wouldn't know you had a hidden partition though, you'd just show them the decoy partition/operating system.  When they analyse the HD and see there's something else there you'd just give them the password for the outer volume.

If you just encrypt with the full disk encryption on the alternate disk then any LE can make you give up the password.  In the UK you can get up to 5 years in prison for not giving your encryption passwords.

As for the USB being with the computer, the point is you'd always have it on you, e.g with keys.

---

### Post by jwhendy on 2010-10-07
LFDE sounds sketchy to me... Beta 0.2 release? I wouldn't go for it in place of more standard/proven systems: dm-crypt/LUKS, TrueCrypt, FreeOTFE, ecryptfs, etc.

I've heard *tons* of varying opinions on plausible deniability. Yes, supposedly TrueCrypt allows for it. You create an encrypted container and a hidden on inside of it. You have two passwords. Enter one and get the outer container; enter the other and get the inner/hidden container (*if* you specifically tell TrueCrypt to even look for a hidden container in the first place).

Whether it is possible to install a decoy OS to the outer container like described in their documentation when using Linux... I'm not sure.

I'm not sure if something like [TCHunt]("http://en.wikipedia.org/wiki/TCHunt") would see hidden volumes or not.

The discussions I've seen on places like [Schneier on Security]("http://www.schneier.com/blog/archives/2008/07/truecrypts_deni.html") have wildly varying opinions on whether plausible deniability is possible without using something like steganography (hiding files in jpeg containers). Some of the comments indicate that one could potentially see the "random" blob of data where there is supposed to be "free space" and conclude that there was another encrypted volume present. Whether that's the case or not... I don't know.

It probably comes down to what you're looking for. If you want to protect your data... encryption should be fine. If you need to hold up to some kind of interrogation... will plausible deniability really do it for you? For various things, it might be far better to simply use a live cd, store data on an encrypted USB disk and if the data were really valuable... keep the USB key in a safety deposit box or destroy it if in danger.

With respect to the US legal system, it seems that the case of [Boucher]("http://news.cnet.com/8301-13578_3-9834495-38.html"), one's 5th amendment rights *do* apply to providing an encryption passphrase from one's mind. In other words, you can't be compelled to provide it in order to testify against yourself. This apparently only works in *criminal* cases though (child pornography, treason, etc.), not *civil* ones (copyright infringement) per the [EFF]("https://ssd.eff.org/tech/disk-encryption").

Anyway... there's my thoughts. I'm evaluating encryption options right now and looking at probably a lot of the same options. While hidden encryption is slightly appealing, I'm not convinced that forensics couldn't figure out that what's made to look like "free space" in the end of an outer container can't be seen to be a hidden volume somehow.

I have limited knowledge of forensics and thus don't know if once you decrypt the outer volume of the "randomness" of the contents could be analyzed and found to be highly random, thus indicating a hidden drive. If powered off correctly, an image of the drive should look random (random encrypted hidden container overwritten with the random encryption of the outer container). It's what shows up once the outer container is decrypted that worries me.

---

### Post by Resist on 2010-10-08
You're right it does sound a bit sketchy.  However if you're forced to unencrypt your computer saying "I lost my USB key" sounds a lot better than "I forgot my password".

My ideal setup would be having my OS installed on a USB stick, like you described with the LiveCD.  I tried this but am having problems with it now, it won't boot up for some reason.  As well as that it is pretty damn slow, well compared to using a HDD any way.

I too will look into different encryption methods and see what is best for my needs

---

### Post by jwhendy on 2010-10-08
Agreed -- losing a USB key sounds more plausible than losing the passphrase!

Re. the USB bootable system... it's tough! You could try one of those programs like usnetbootin (something like that) or pendrive Linux. I wanted a real-live distro (just like running from a regular drive) and thus did that. You can read through my documentation of that if you want ([LINK]("http://wiki.zenwalk.org/index.php?title=Bootable_usb_flash_drive")). There were a lot of oddities like what to tell the bootloader to call the drive (sda1? sdb1? or if you use Grub hd0 or hd1?? When you're running from hd0 the drive is hd1... but what about when you boot from it? Technically there's no other drive), what modules needed to be built in the kernel, how to install the bootloader properly, and I ended up needing to put a pause in my boot options because if it tried to load the kernel too fast, apparently the USB stick wasn't read soon enough and it wouldn't even detect the partition!

In any case, good luck. 

Regarding the speed, the *write* speed makes a *huge* difference. I started with a Walmart SanDisk Cruzer 8gb drive and my system would lag several times every few minutes. Any time it needed to write to the disk it would lag. Horrible!

I bumped up to this: [OCZ Rally2]("http://www.amazon.com/OCZ-Rally-Channel-Memory-OCZUSBR2DC-8GB/dp/B000RZ8WIK"). It made all the difference in the world. The SanDisk was like < 5mb/s write speeds and I got into the high teens with the Rally2 (17mb/s at the very top end) and the read speeds were also fantastic (28-30ish mb/s?). I didn't notice any lag after that whatsoever. That drive was about $26 with shipping included when I bought it a year ago and the WalMart SanDisk was like $18. For $8 more it's unbelievably worth it.

---

### Post by Resist on 2010-10-08
Thanks for the link. Your method seems complicated, however if it works well, then great.  Do you think it would work with Ubuntu?  I installed the full version of Ubuntu 10.04 alternate on directly on the the USB stick as you would install it on a HDD.  It worked for a couple of days then wouldn't boot again.  My USB stick is a SuperTalent Pico-C 8GB, reads at 35MB/s but writes at only 8MB/s, that was probably causing the slowness.

I'm new to Linux, only just migrated from Windows so not familiar with all the commands at all.

I'm on the hunt for a fast ultra small USB stick now :)

---

### Post by jwhendy on 2010-10-08
I'm not sure if it would work. If it already worked for you a couple of days, I'd say you probably did everything right. My main issue was having to build a custom kernel with uhci/ehci support built in -- I kept hitting a wall because the Zenwalk kernel has them as modules but you need them at boot time to use a USB drive for the HD!

What errors were you getting with the USB Ubuntu install?

I wonder if passing the "rootdelay=10 rootwait" option in grub would work for you? I kept having intermittent boots. Once every 8 times or so it would work. I was so puzzled. That option worked perfectly for me. I think in the end it just needed to be "rootdelay=5" and I was set. Just a thought.

The fact that it worked already makes me suspicious that you did anything wrong outrightly. Some update? Something else? If I were you, I'd just start with the same drive and try again. Low investment and the install will go fast. See what you get. Maybe do it without encryption first to see how that goes.

---

### Post by psusi on 2010-10-08
If they can force you to tell them the password for one volume, they can do the same for the other.

---

### Post by jwhendy on 2010-10-08
@psusi:

Agreed for the most part. I think this whole idea rests on the assumption that one won't be beaten for either password. The idea is more like a *voluntary* providing of one password in hopes that the need for a second password is *never even contemplated*.

If the mind of the searcher only thinks that it's now able to see what was encrypted... they'll never seek to "force" one to reveal what they don't even consider exists.

If they think there *might* be a hidden partition... sure, one's going to have issues.

---

### Post by psusi on 2010-10-08
I'm sure if the police cared enough to seize your computer and inspect it, that they wouldn't have any old idiot analyzing it.  You may as well just keep any sensitive files buried in a hidden directory in .Trash or something if that were the case.

---

### Post by jwhendy on 2010-10-08
@psusi:

It's not about whether the inspecting individual is an idiot or not. That's the whole point of plausible deniability. Take these two examples:

```
Example 1:
/------------------------\
|                        |
|                        |
| Encrypted Container    |
|        [2GB]           |
|                        | 
\------------------------/


Example 2:
/--------------------------------------------------\                   
|                            /-------------------\ |
| Encrypted Outer Container  |  Encrypted Inner  | |
| Container [2GB Tot]        | Container [500MB] | |
|                            \-------------------/ |
\--------------------------------------------------/
```

The point is that an examining individual will image the disk and look at the bits. An encrypted single container appears no differently than an encrypted outer container with a hidden inner container; it just all looks random.

Hence the key is that upon revealing the outer container with some data that *appears* sensitive, one is able to provide a plausible display of having revealed all there is to reveal.

Again, if suspicion of a hidden partition exists, things might get complicated. Without being able to detect it, however, plausible deniability remains intact. Read TrueCrypt's documentation. They cover all this stuff and how to maintain plausible deniability. For example, they state that if an examiner is taking regular images of the drive over a prolonged period of time, they will be able to note (perhaps) that the hidden partition's bits change (if you use it). This creates suspicion because it supposedly looks like free space in an encrypted container... but the bits changed. This leads to investigators wondering if it's *not* free space but a hidden volume.

And lastly, if there is a chance of beating... no: plausible deniability is probably not much of a concern. One is better being able to simply destroy the USB drive that held the only key.

---

### Post by jwhendy on 2010-10-08
[deleted]: forums were lagging and led to posting twice in a row.

---

### Post by bodhi.zazen on 2010-10-08
"plausible deniability" is nothing more then a crypt within a crypt. You can do the same thing with any encryption, if you "need" to boot another OS, which I doubt, use KVM.

---

### Post by jwhendy on 2010-10-08
> **bodhi.zazen said:**
> "plausible deniability" is nothing more then a crypt within a crypt.

I've wondered about this. Can you verify this somehow? If the "crypt" within a "crypt" shows up as any kind of partition in the table, would your statement be false? Same goes for a "crypt" (TrueCrypt file) inside a "crypt" (an "outer" TC file). If one decrypted the first container, the second file could be found.

I'd actually love for your statement to be the case. I just haven't heard anyone show how it's the case. You need to have a situation where there's no possible way to see the second/inner encrypted blob. It needs to be indistinguishable from, essentially, the random free space of the parent crypt.

Perhaps an easy way would be for someone to write out the steps to create this so we know what's involved. How does it work with respect to the partition table and LVM at installation time?

---

### Post by bodhi.zazen on 2010-10-08
> **jwhendy said:**
> I've wondered about this. Can you verify this somehow? If the "crypt" within a "crypt" shows up as any kind of partition in the table, would your statement be false? Same goes for a "crypt" (TrueCrypt file) inside a "crypt" (an "outer" TC file). If one decrypted the first container, the second file could be found.

I'd actually love for your statement to be the case. I just haven't heard anyone show how it's the case. You need to have a situation where there's no possible way to see the second/inner encrypted blob. It needs to be indistinguishable from, essentially, the random free space of the parent crypt.

Perhaps an easy way would be for someone to write out the steps to create this so we know what's involved. How does it work with respect to the partition table and LVM at installation time?

Try it yourself. Make a crypt and add a crypt within it. Take a look at the raw data from the disk.

---

### Post by jwhendy on 2010-10-08
> **bodhi.zazen said:**
> Try it yourself. Make a crypt and add a crypt within it. Take a look at the raw data from the disk.

I don't even know how to do that yet... I'm just getting into encryption and haven't "taken the plunge yet." All the tutorials I've read for dm-crypt/LUKS, though, refer to applying encryption to a partition. If you mean "create a partition and another partition inside of it" then I don't think it will be plausibly deniable. Being able to identify from the output of fdisk that two partitions exist in which one is the Extended "container" and another is a logical partition inside shows that something exists in there. I don't think this is what TrueCrypt or FreeOTFE are doing when they discuss hidden partitions.

Again, could you briefly describe what you mean by "a crypt." Volume/partition (primary, extended/logical)? An encrypted file?

---

### Post by psusi on 2010-10-08
"Plausible deniability" = "I swear, that 200gb file of random garbage is just random garbage.  Doesn't everybody keep large files of random data around?  Pay no attention to that link on the desktop that says decrypt random garbage file".

Seriously, it isn't any more deniable just because it's encrypted twice.

---

### Post by jwhendy on 2010-10-08
@psusi:

This is frustrating. You really aren't getting it.

Perhaps [Wikipedia]("http://en.wikipedia.org/wiki/Plausible_deniability#Use_in_cryptography") will help?

> In cryptography, deniable encryption may be used to describe steganographic techniques, **where the very existence of an encrypted file or message is deniable in the sense that an adversary cannot prove that an encrypted message exists.**

...The owner of the encrypted data may reveal one or more keys to decrypt certain information from it, and then deny that more keys exist, a statement which cannot be disproven without knowledge of all encryption keys involved. The existence of "hidden" data within the overtly encrypted data is then deniable in the sense that it cannot be proven to exist.

In other words (as I've already said), the *entire point* is that the investigator never gets to the point where he/she asks, "What's that 200gb file laying there?" One decrypts *one thing* and no matter what tools are used, no *second thing* can be detected. Look at the graphic above. Only *you* know that there is a nested volume/container hidden there. To any analysis tool, however, it just looks like one lump of random bits.

To think of it another way... imagine that a partition existed on your disk and *no record of it existed... anywhere*. Not in fstab, not detectable by any analysis tools, not shown with any fdisk or parted tools... *nothing can detect it*. But *you* know it exists and by simply typing "mount /dev/sd15 /mnt" you can mount it whenever you want. *That's* plausible deniability. Without specifically knowing it exists... there's no way of finding out otherwise.

Again, the whole point is that plausible deniability only works if these two look *identical*
- 1 encrypted container
- 1 encrypted container with another container (not file) inside

---

### Post by psusi on 2010-10-08
Stenography involves things like subtly altering every xth pixel of an image.  If you don't know what to look for, then it just looks like an image.

When you have a large file that appears to contain random data, that is pretty obviously an encrypted file.  If you can mount it by clicking an icon on your desktop, then typing in a password, then there pretty good record of its existence right there.

Just because the container is in another container makes no difference; if you can see that there is a container there, you're going to wonder what's inside.

---

### Post by jwhendy on 2010-10-08
Agreed re. stenography... but you keep making the assumption that the hidden volume will be a visible *file* that is in some way differentiated from the "non-hidden" volume.

This is wrong.

You should just install TrueCrypt and go through the process of setting up a hidden volume yourself. I did just so I could verify my sanity in this conversation.

Here's how it works:
- create a hidden volume
- *one* file is created; I called it "hidden"
- the size of the total volume is set: I chose 10mb
- you set password #1
- you copy something into the *outer* volume and click next in TC
--- I copied a 4.3mb picture into it
- you set the size of the inner/hidden contain based on what you copied into the outer one
--- I had about 5mb left so I set it to 4mb
- you set *another* password (#2)
- you're done

Remember. There is *one* visible file. *That's it*.

Now, here are the possible scenarios:
-> 1) Select the file called "hidden" and click "mount" and enter password #1 for the *outer* volume, and it mounts and I can see that picture I copied into it.

-> 2) Select the file called "hidden" and click "mount" and enter password #2 for the *inner* volume, and it mounts the inner one, which is empty

So, plausible deniability is obtained because the investigator cannot prove that the file "hidden" contains anything more than one volume. You click "mount" open it and that's it. *One* file, no more. But really there are two present. You can plausibly deny that a second exists because there is no way the investigator can actually prove that the file "hidden" is, in reality, two containers. But *you* know and can tailor which is opened via your choice of password.

---

### Post by psusi on 2010-10-08
After reading the description from their web site, the plausible deniability makes a bit more sense, since both volumes are mounted at once using the same path, and the hidden one is stored in free space.  Using free space still seems to present a problem though: you can't stop writes to the non hidden volume from overwriting it.  They say they just deny attempts to do so as long as the hidden volume is mounted, but that would result in that area being flagged as bad, and if you ever mount with the dummy password, then the hidden volume could be trashed.

I suppose at that point it is up to you using a sufficiently complex password, say at least 10 characters and using upper and lower case letters, numbers, and symbols.  That and them NOT deciding to spy on you before you are aware that you are being investigated, and catching you entering the real password.

---

### Post by jwhendy on 2010-10-08
> **psusi said:**
> After reading the description from their web site, the plausible deniability makes a bit more sense, since both volumes are mounted at once using the same path, and the hidden one is stored in free space.

Yess!! Now we're talking :)

[QUOTE=psusi]Using free space still seems to present a problem though: you can't stop writes to the non hidden volume from overwriting it.[/quote]

True. Though when you mount a hidden volume in TrueCrypt you can pull down a set of extra mount options that say something like, "protect hidden volume" or something like that (can't recall exactly). When you do that it has some way of judging the size of the hidden volume and making sure it stays "in bounds."

So, if one were to use a hidden volume regularly, they would use that special option for day-to-day usage, but if one were every interrogated, one would obviously not pull up that menu as it would be obvious one was protecting a hidden volume!


They say they just deny attempts to do so as long as the hidden volume is mounted, but that would result in that area being flagged as bad, and if you ever mount with the dummy password, then the hidden volume could be trashed.

[QUOTE=psusi]That and them NOT deciding to spy on you before you are aware that you are being investigated, and catching you entering the real password.[/QUOTE]

Absolutely. Encryption still seems vulnerable to "evil maid attacks" popping in a USB drive that puts some keystroke logging software in the bootloader or other ways of physically getting your password. Another interesting one is called the "watermark attack", I believe.

If investigators look at your computer regularly, say every 2 months, and take successive images, they can examine what sections of the disk changed from image to image. If you used a hidden image (so 2 total encrypted volumes exist) but said only one did, they would be able to see that bits were changing in the supposed "free space" of the encrypted volume. *Then* they would have reason to ask about the existence of a second encrypted volume residing in the supposed free space and call your bluff!

This stuff is just fascinating.

---

### Post by psusi on 2010-10-08
> **jwhendy said:**
> 
True. Though when you mount a hidden volume in TrueCrypt you can pull down a set of extra mount options that say something like, "protect hidden volume" or something like that (can't recall exactly). When you do that it has some way of judging the size of the hidden volume and making sure it stays "in bounds."

Right, but it can only do that if you use the super secret password and not the dummy password.  So as long as you always use the super secret password and only keep the dummy one around if someone forces you to reveal it, the worst that can happen is that you end up with some bad sectors flagged on the outer volume, which is a hint, but still not conclusive proof that you have a hidden volume.

---

### Post by jwhendy on 2010-10-08
> **psusi said:**
> Right, but it can only do that if you use the super secret password and not the dummy password.  So as long as you always use the super secret password and only keep the dummy one around if someone forces you to reveal it, the worst that can happen is that you end up with some bad sectors flagged on the outer volume, which is a hint, but still not conclusive proof that you have a hidden volume.

Yeah, not exactly sure all that would happen. They suggest that you try to use them both fairly regularly so that when you pop open the "dummy" outer volume there's not a bunch of crap that's been untouched for years :)

If you always used the super-secret hidden volume with the safe mount options, I don't think anything bad would happen to the outer container as long as you kept tabs on how big the volume was and didn't overwrite it. Actually... maybe the option is for opening the *outer* volume so it doesn't write into the "free space" that's actually the hidden volume. I'd have to go check again.

It's probably a good idea to know both passwords very well. I can't imagine it would be very believable to say, "Yup. Only one encrypted volume on my system. Hmmm. I haven't used the password in like 6 months and I just can't remember it."

---

### Post by Resist on 2010-10-09
Wow seems this thread has moved on nicely since I was here :)

> **jwhendy said:**
> I'm not sure if it would work. If it already worked for you a couple of days, I'd say you probably did everything right. My main issue was having to build a custom kernel with uhci/ehci support built in -- I kept hitting a wall because the Zenwalk kernel has them as modules but you need them at boot time to use a USB drive for the HD!

What errors were you getting with the USB Ubuntu install?

I wonder if passing the "rootdelay=10 rootwait" option in grub would work for you? I kept having intermittent boots. Once every 8 times or so it would work. I was so puzzled. That option worked perfectly for me. I think in the end it just needed to be "rootdelay=5" and I was set. Just a thought.

The fact that it worked already makes me suspicious that you did anything wrong outrightly. Some update? Something else? If I were you, I'd just start with the same drive and try again. Low investment and the install will go fast. See what you get. Maybe do it without encryption first to see how that goes.

The errors I was getting I posted in this thread: [http://ubuntuforums.org/showthread.php?t=1588041](http://ubuntuforums.org/showthread.php?t=1588041)

They were:

```

(process:356): GLib-WARNING **: getpwvid_r(): failed due to unknown user id (0)
```and now:

```
No init found. Try passing init= bootarg.
 BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
 Enter 'help' for a list of built-in commands.
 (initramfs)

```It's gets to the password stage, I enter the password and then get the second message above.  How do I go about changing the root delay?  I'll do a reinstall without encryption.

---

### Post by psusi on 2010-10-09
> **jwhendy said:**
> Yeah, not exactly sure all that would happen. They suggest that you try to use them both fairly regularly so that when you pop open the "dummy" outer volume there's not a bunch of crap that's been untouched for years :)

You should use the first filesystem, yes, but if you don't enter the second password, then it does not know about the second filesystem, so it can't protect it from being overwritten.

> **jwhendy said:**
> If you always used the super-secret hidden volume with the safe mount options, I don't think anything bad would happen to the outer container as long as you kept tabs on how big the volume was and didn't overwrite it. Actually... maybe the option is for opening the *outer* volume so it doesn't write into the "free space" that's actually the hidden volume. I'd have to go check again.

Yes, it has to know where the hidden volume is to stop it from being overwritten, but it can't figure that out without the super secret password.

> **jwhendy said:**
> It's probably a good idea to know both passwords very well. I can't imagine it would be very believable to say, "Yup. Only one encrypted volume on my system. Hmmm. I haven't used the password in like 6 months and I just can't remember it."

Obviously you have to actually remember it ;)

---

### Post by jwhendy on 2010-10-09
> The errors I was getting I posted in this thread: [http://ubuntuforums.org/showthread.php?t=1588041](http://ubuntuforums.org/showthread.php?t=1588041)

They were:

```

(process:356): GLib-WARNING **: getpwvid_r(): failed due to unknown user id (0)
```and now:

```
No init found. Try passing init= bootarg.
 BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
 Enter 'help' for a list of built-in commands.
 (initramfs)

```It's gets to the password stage, I enter the password and then get the second message above.  How do I go about changing the root delay?  I'll do a reinstall without encryption.

A few thoughts:
- First off... sorry to say but I think you got treated pretty poorly in that forum! A suggested allegation of potential criminal purposes, you simply defend yourself, and then are told to go debate in the cafe? Sheesh!

- You could add rootdelay if you can ever get to grub. You should be able to hit "tab" or press a key to edit the grub menu during boot and then you would add the rootdelay option to the list of options

- I'm thinking you're not even getting to the grub stage, though, are you? Maybe post a itemized list of everything that happens: (power on, see grub menu, bunch of normal boot text flashes by, then I'm asked for a password... for example. Change if different). Perhaps it has to do with what they mentioned in the post about needing lvm and crypt in the loaded modules? Check out the Arch Wiki on encryption and see if that helps at all? They're pretty specific and helpful about how to set this stuff up ([LINK]("http://wiki.archlinux.org/index.php/System_Encryption_with_LUKS_for_dm-crypt#Configuration")). That's a link to the configuration section, but feel free to check the rest.

Hope that helps?

---

### Post by Resist on 2010-10-10
Yeah they didn't seem to like me protecting my privacy, oh well.

I'm not sure if I can get to the grub stage, sorry I'm a Linux noob.  Here's what happens: Power on, Ubuntu loading logo, enter password, 'crypt_setup successful', wait for around 10 seconds with Ubuntu loading logo and then I get a black screen with the message above, No init found....

If I insert the USB when I'm running off my HDD I can get to a 255MB partition on the stick that has a folder named 'grub', 'lost+found' and some other files.  Would I be able to edit from there?  If so how do it to it?

I'll check out the link now.  Thanks for you help :)

---

### Post by jwhendy on 2010-10-10
Ok. That's helpful.

Here's an easy question for you: did you put /boot on it's own partition or is it all in one partition? The /boot directory needs to be on a separate unencrypted partition. If you only have one partition then you'll almost certainly have to wipe and reinstall.

Then again... you said it *was* working...

Try this post: [http://ubuntuforums.org/showthread.php?t=689541](http://ubuntuforums.org/showthread.php?t=689541)

Could that help? Maybe the initrd got messed up and you can tell it to use the backup one?

---

### Post by Resist on 2010-10-12
It's on a separate partition.  It's happened twice no on the USB stick and once on my HDD, I don't understand why it does it.

I'll try what you said above a bit later.  Thanks.

---

