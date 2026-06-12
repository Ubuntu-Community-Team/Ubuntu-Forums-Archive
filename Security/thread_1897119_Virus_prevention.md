---
title: "Virus prevention"
date: 2011-12-18
forum: Security
---

### Post by joey00 on 2011-12-18
I am becoming concerned. It seems that memory sticks (flash drives) are increasingly becoming the vehicle for the spread of virusses.

I am increasingly using memory sticks. So I feel I should start to take preventative measures.

The main vulnerability seems to lie in the auto-run on a newly inserted medium. (Reminds me of the directory read on the old floppys). Or am I the only one that remembers that?  :)

I  am looking for any information /suggestions /advice in this direction.

Anybody?

---

### Post by Dangertux on 2011-12-18
> **joey00 said:**
> I am becoming concerned. It seems that memory sticks (flash drives) are increasingly becoming the vehicle for the spread of virusses.

I am increasingly using memory sticks. So I feel I should start to take preventative measures.

The main vulnerability seems to lie in the auto-run on a newly inserted medium. (Reminds me of the directory read on the old floppys). Or am I the only one that remembers that?  :)

I  am looking for any information /suggestions /advice in this direction.

Anybody?


Well hopefully I can provide an answer that is less vague than the question.

Basically in terms of Ubuntu (this is an Ubuntu support forum, if you're asking for another OS then...yeah.) However, auto-run is pretty tightly controlled under Ubuntu. It's going to ask you at least twice before auto-running anything.

If you need Anti-virus/malware solutions unfortunately there aren't many good alternatives available under Linux (at least not for free). You can try ClamAV, or Avast, AVG also has an alternative for CLI scanning.

Hope this is helpful.

---

### Post by CharlesA on 2011-12-18
I use BitDefender for scanner Samba shares, it has had a few false positives but nothing major.

I think DT covered pretty much everything else.

---

### Post by c.cobb on 2011-12-18
This is a concern of mine also. I boot Ubuntu off a Live USB, but keep some Windows tools on the memory sticks as well. On a Windows PC that you don't control, I don't think there is a way to temporarily disable the AutoPlay feature -- for a while you could hold down the [shift] key when inserting a USB stick, but I read that *enables* AutoPlay on other Windows versions. If true, that's pretty lame.

What I do is to place a very basic autorun.inf file in the root dir of my USB sticks so I can at least know if/when another PC has messed with it. Since I also like to give various drives unique icons, I made [this page]("http://ccobb.net/ubuntu/volume_icons_en.html") which allows a quick drag'n'drop setup. The icons are then used on Linux, Windows, and OS X systems, and this also work nicely with TrueCrypt data volumes.

---

### Post by needhelppeeps on 2011-12-19
I use an sdcard, they can hold quiteabit ofstorage and can be set to readonly. To me an external media which cannotbe hardwarewrite protected is not something I'd want to use between systems.

---

### Post by joey00 on 2011-12-20
> **Dangertux said:**
> Well hopefully I can provide an answer that is less vague than the question.

Basically in terms of Ubuntu (this is an Ubuntu support forum, if you're asking for another OS then...yeah.) However, auto-run is pretty tightly controlled under Ubuntu. It's going to ask you at least twice before auto-running anything.

If you need Anti-virus/malware solutions unfortunately there aren't many good alternatives available under Linux (at least not for free). You can try ClamAV, or Avast, AVG also has an alternative for CLI scanning.

Hope this is helpful.

The last part of your message is indeed helpful.

Since this thread is marked [ubuntu] [Virus prevention]("http://ubuntuforums.org/showthread.php?t=1897119")
I did not think it necessary to repeat the Ubuntu designation. 

As far as the auto-run, that is a problem. I need to be able to boot from some USB sticks. And I need to be able to just access the contents of others. The prospect of a boot sector virus being transmitted doesn't make me happy.

Is there, perhaps, any way of adding any warning to the use of a stick either for read or write?  Say a prompt along the lines of: Do you want to write to the device? y/n

I do not see where the question is vague. I use several different flavours of Ubuntu, and expect to encounter several different virusses, so it is correct not to specify. Perhaps you can point out my mistake, so I may avoid it in future?

[LEFT]
[/LEFT]

---

### Post by CharlesA on 2011-12-20
There are no virii in the wild for Linux. You'd be scanning for Windows viruses if you installed one of those. Is that what you want?

---

### Post by OpSecShellshock on 2011-12-20
Are you primarily concerned about the USB drive writing to the computer's disk or about the computer writing to the USB drive?

Do you own all of the systems that the USB drives will be plugged into? Do you own all of the USB drives that will be plugged into the computers? Will compatibility with other operating systems be necessary, or are you only using Ubuntu?

---

### Post by joey00 on 2011-12-21
> **CharlesA said:**
> There are no virii in the wild for Linux. You'd be scanning for Windows viruses if you installed one of those. Is that what you want?

I thought there were few not no linux virusses around. Are you sure there are none?

And yes, I am concerned about Doze virusses too - many machines have dual boot.

---

### Post by joey00 on 2011-12-21
> **OpSecShellshock said:**
> Are you primarily concerned about the USB drive writing to the computer's disk or about the computer writing to the USB drive?

Do you own all of the systems that the USB drives will be plugged into? Do you own all of the USB drives that will be plugged into the computers? Will compatibility with other operating systems be necessary, or are you only using Ubuntu?

As long as the USB drive is clean, I am concerned to keep it so. But, should it become infected, I do not want to complicate life by spreading the infection to other hardware. It just makes the search and destroy task messy!

I do not own (most of) the systems that the drives will be plugged into. I do own (most of) the USB drives.

There is often a windows something sitting as a dual boot. I would need to be able to manipulate (copy, move, delete, view) files on that format too. Other than that I do not need to access files via, say, windows.  

I use (usually) branches of the debian family when using Linux.

---

### Post by OpSecShellshock on 2011-12-21
OK, so it seems then that to whatever extent risk of malware enters the picture, it does so in the circumstance of copying a file from a system you don't own to a drive that you do own. Malware written for Windows won't run on Linux even if it does manage to propagate, so the spread is already sort of contained. As others have stated, malware for Linux (at least the modern kind) is not known to exist in the wild (which is not to say that it isn't there, just that no one has come forward with a sample of any). If someone were to surprise us all then there wouldn't be any protection for it right away, so there's not going to be much help in terms of detection software.

If the Windows system has AV software, you can of course scan everything before copying it over. You can also account for available disk space on the USB drive prior to connecting to a computer, the size of the files being copied, and the available space after the files have been transferred and/or edited. Once you've used the removable drive to take files from where they were to where they're going, you can reformat the drive to wipe everything out, then manually copy back exactly what you expect to be there. It's tedious, but a good way to know.

The chances that malware would propagate from a drive that you own (and have formatted yourself and saved specific files to yourself) to another computer are pretty low. Not zero, but very close.

---

