---
title: "TrueCrypt Existing Multi-Boot System"
date: 2010-08-02
forum: Security
---

### Post by opticyclic on 2010-08-02
I currently have the following setup:
Primary Partition - NTFS Vista
Primary Partition2 - NTFS Vista Home
Extended Partition
- EXT4 - Linux Mint9
- EXT4 - PinguyOS
- EXT4 - Data directory (sym-linked to from the Ubuntu home dirs)
- Swap

I regularly access the data on Windows from Linux and vice-versa.

Now, my company is bringing in a policy that all laptops must be full drive encrypted and they are recommending TrueCrypt (although they have no objections to using other software).

Does TrueCrypt support this sort of setup?
Can I do it retrospectively without reformatting?
What happens if I subsequently want to resize the partitions or add new ones?

I've spent hours reading lots of posts and blogs, but I'm still not sure as many seem out of date or refer to older versions (7.0 is out now) or don't refer to full-drive encryption.

Other posts seem to suggest dm-crypt as an alternative.
Can I do full drive encryption with dm-crypt and still access my Windows and Linux partitions from each other?

Not many laptops at work have Linux on them so the work IT dept. can't really help me much.

The key issues for me are:
Accessing my Windows and Linux partitions from each other
Not destroying my existing data/installations

---

### Post by FuturePilot on 2010-08-02
> Does TrueCrypt support this sort of setup?
Not under Linux. Truecrypt only supports full disk encryption for Windows.

> Can I do it retrospectively without reformatting?
Windows yes. As mentioned before, not supported under Linux.

> What happens if I subsequently want to resize the partitions or add new ones?
I don't know exactly how this works with Truecrypt.

Under Linux you should use LUKS for full disk encryption. The only issue is that this would require a reinstall. And considering how many OSes you have installed, this would turn into a very complex setup.

---

### Post by OpSecShellshock on 2010-08-03
Wait, so the workplace is insisting on some form of encryption? Who owns the device? The reason that's important is because it sounds like if they own it then it's their responsibility to provide the encryption solution (as well as maybe, oh I don't know, a standard image for their workstations?) and to take care of the installation, administration, and emergency passphrase archiving.

If, on the other hand, you own it, then just get any of their data off of it, insist on being provided with a separate work machine, and have them encrypt that. Another option would be to move the data off the local machine into remote storage that the company controls access to, and then have a single OS at boot and run the others as virtual machines as needed.

I don't really think there's any way around having to at least temporarily (and preferably permanently) migrate the locally stored data to alternate storage in order to implement effective encryption. You--or rather your company, since it's their stuff--should be prepared to run into a situation where every bootable OS partition has to have its own encryption. Not saying that will definitely be the case, but I wouldn't be surprised.

Honestly though, if the company is putting the implementation on their employees individually then they've got bigger things to deal with than encryption.

---

### Post by arjaydavis on 2010-08-03
I wrote some instructions about a partially complete triple boot installation. This might help you towards a complete solution.

[http://www.howtoforge.com/forums/showthread.php?p=184776#post184776](http://www.howtoforge.com/forums/showthread.php?p=184776#post184776)

---

### Post by opticyclic on 2010-08-15
OpSecShellshock: Its not as bad as all that :) 
They are being fairly flexible, saying you are allowed to have a different O/S to the standard image if you want to, but if you do, you have to do the implementation yourself.
Support is for the supported O/Ss!

arjaydavis: Are you able to access your Windows data from your Debian installation and your Debian data from your Windows install?

---

