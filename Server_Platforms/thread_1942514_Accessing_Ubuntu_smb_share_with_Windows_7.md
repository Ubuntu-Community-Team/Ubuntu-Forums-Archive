---
title: "Accessing Ubuntu smb share with Windows 7"
date: 2012-03-17
forum: Server Platforms
---

### Post by hozzaconners on 2012-03-17
Hi,

I've got a strange problem that I really could do with some help fixing, if you'd be so kind? This is my first post so please be gentle?!

I'm running Samba on Ubuntu Server 11.10. I've set up a share which I can see fine on a Mac, on an XP machine, and on a Win 7 professional virtual machine. I have a Win 7 pro laptop, but I can't see the share on it at all. To date I've:

Pinged the server, and get a reply.
Disabled firewalls, pinged the server and got a reply.
Gone to:
Control Panel > Administrative Tools, Local Security Policy > Local Policies > Security Options
and modified:
Network security: LAN Manager authentication level Send LM & NTLM responses
Minimum session security for NTLM SSP Disable Require 128-bit encryption
Then pinged the server and got a reply.
Despite all these the server doesn't appear in the "Network" section of Computer. And yet it's clearly there, pingable, and accessible from other machines.

Any ideas? Cheers.

---

### Post by darkod on 2012-03-19
And what happens if you open the Run... command and type \\ip-address-of-smb-srv and hit Enter.

Will it open the list of shares on that server?

If you know the IP I always prefer this as a fastest way to open shares instead of looking for the server in Network...

---

### Post by hozzaconners on 2012-03-19
Hey Darkod,

Thanks for your reply, much appreciated. I've now managed to fix the fault!
Run -> \\ip-address-of-smb-srv
gave me an error message saying "Network Path not found"

Expanding the window for more information gave me an error code 0x80070035. A bit of googling and various fixes seemed to be pointing to checking/reconfiguring the network interface. I then wondered if plugging a cat5 in (rather than WiFi) would make the drive appear. Immediately I connected the string it appeared in Computer. I logged into the drive and it was there for all to see, no worries. Unplugged the string and switched the Wifi back on...drive disappears. Turn off wifi, plug in string, drive appears. Turn on wifi with string plugged in, drive is still there. Remove string, drive stays. Turn off wifi, then on again, drive is still present. Reboot laptop, connect via wifi, drive is there. So i'm gonna call that a result!

Once again, thanks for your help...it was just the pointer I needed.

---

### Post by ifrisbie on 2012-10-22
For anyone that has this error - I did as well and solved it differently - so I suspect there are many ways to see this symptom: 

I resolved my problem connecting my Windows 7 box to my Ubuntu samba (11.10).  I Had the "Windows cannot access" error (0x80070035 - the network path was not found" when trying to access the server (or share).  I tried a lot of things, but when it came down to what actually solved it (all other items reversed) it was the "Microsoft Network client: Digitally sign communications (always)" setting that was causing my problem.  Once it was disabled, I could see the shares and map the drive.

---

### Post by sharkforce on 2012-10-23
> **ifrisbie said:**
> For anyone that has this error - I did as well and solved it differently - so I suspect there are many ways to see this symptom: 

I resolved my problem connecting my Windows 7 box to my Ubuntu samba (11.10).  I Had the "Windows cannot access" error (0x80070035 - the network path was not found" when trying to access the server (or share).  I tried a lot of things, but when it came down to what actually solved it (all other items reversed) it was the "Microsoft Network client: Digitally sign communications (always)" setting that was causing my problem.  Once it was disabled, I could see the shares and map the drive.

I have this problem as well, thread here: [http://ubuntuforums.org/showthread.php?t=2074576]("http://ubuntuforums.org/showthread.php?t=2074576")

and for the record, my "Microsoft Network client: Digitally sign communications"  is set to 0 in the registry.

---

