---
title: "Emergency erase data"
date: 2012-08-23
forum: Security
---

### Post by Stonecold1995 on 2012-08-23
My laptop has two drives, a 32GB SSD and a 750GB HDD, and they're both fully encrypted with AES (through dm_crypt, I think).  I have a lot of sensitive data on my computer, but I often leave it on unattended overnight, etc.  I'd like to have a way to immediately erase the data with a remote command, but issuing a secure deleting command (like shred) would obviously be to slow.  Even DD would be way too slow.  So my thought was, why not simply overwrite the MBR (or whatever contains the master key)?  That would take less than a second, and would essentially destroy all the data because it couldn't be accessed even with my password.  So is there a program that can do that?  One where I can send a remote command, or maybe a dead-man's switch, to securely delete the data on my drive (or external device)?

---

### Post by Hungry Man on 2012-08-23
The data could still be accessed with a password, MBR or not. Not sure how best to go about remote wipes, sorry.

---

### Post by Cheesemill on 2012-08-23
If the drives are fully encrypted then why would you need to initiate a remote wipe?

Just issue a remote power down instead, without the correct password encrypted data is indistinguishable from the random data you end up with from using shred.

---

### Post by Stonecold1995 on 2012-08-23
> **Cheesemill said:**
> If the drives are fully encrypted then why would you need to initiate a remote wipe?

Just issue a remote power down instead, without the correct password encrypted data is indistinguishable from the random data you end up with from using shred.

What if an attacker were to gain direct memory access (e.g. through FireWire) and got the encryption key while the computer was on.  If I were to just power off wouldn't they be able to turn it back on and put in the key?  I know it's hashed and everything, but they might be able to get whatever else it uses.  That's what I'm worried about.

---

### Post by Ms. Daisy on 2012-08-23
I don't quite understand why you'd leave a computer on and unattended that has sensitive data on it.  

I suggest you encrypt the data folders.  Then you can mount them when necessary, which decrypts them.  And when you're going to walk away you can unmount them which will encrypt them.  

If you're really concerned about someone cracking the encrypted data, then control physical access to the machine.

---

### Post by CharlesA on 2012-08-23
> **Ms. Daisy said:**
> 
If you're really concerned about someone cracking the encrypted data, then control physical access to the machine.

This.

Even if you secure the machine and use encryption, not having a machine with sensitive data physically secured is a bad idea.

---

### Post by bodhi.zazen on 2012-08-23
> **Ms. Daisy said:**
> I don't quite understand why you'd leave a computer on and unattended that has sensitive data on it. 

I agree, this is the problem.

---

### Post by Stonecold1995 on 2012-08-23
> **bodhi.zazen said:**
> I agree, this is the problem.

I don't leave it on intentionally.  I mean sometimes I HAVE to leave it, or am away, but have to be away longer than I expected.  Plus sometimes I may even forget.

---

### Post by bodhi.zazen on 2012-08-23
Yea, but, how would you know to execute a command remotely ?

You are best off, IMO, changing your behavior.

---

### Post by angryfirelord on 2012-08-24
Why not use something like an external drive? That way, if you have to leave your laptop, you can just take it with you.

Personally, I'd be more concerned that someone would steal your laptop than trying to access your data. I'm not sure why you seem fine with leaving your laptop out in a public area.

The other option would be to keep a computer on at home and set up a VPN. That way, even if you have to use your laptop in a public area, you can still have an encrypted path for your data.

---

### Post by ooVoh9em on 2012-08-25
> **Stonecold1995 said:**
> My laptop has two drives, a 32GB SSD and a 750GB HDD, and they're both fully encrypted with AES (through dm_crypt, I think).  I have a lot of sensitive data on my computer, but I often leave it on unattended overnight, etc.  I'd like to have a way to immediately erase the data with a remote command, but issuing a secure deleting command (like shred) would obviously be to slow.  Even DD would be way too slow.  So my thought was, why not simply overwrite the MBR (or whatever contains the master key)?  That would take less than a second, and would essentially destroy all the data because it couldn't be accessed even with my password.  So is there a program that can do that?  One where I can send a remote command, or maybe a dead-man's switch, to securely delete the data on my drive (or external device)?

First of all, leaving your computer turned on and unattended completely defeats the point of full-disk encryption in the first place. If the computer is turned on, then that means the volume is currently decrypted, and the key is stored somewhere in memory. You should really try to get in the habit of powering down the machine when you're not going to be around.

Honestly, there is only so much a regular user can do when it comes to implementing physical security policies, so I won't go into great detail about how a secure environment is essential. Instead, let's assume - for our purposes - that your computer is located in a somewhat hostile environment, and work from there.

I would recommend following each one of the suggestions I list below. Implementing these recommendations can really help safeguard your information, even under not-so-optimal conditions, similar to your current needs.

1) In addition to full-disk encryption (Which, like I said earlier, is only meaningful when the computer is powered down) you should create a second encrypted partition (You could also create an encrypted container with TrueCrypt which is very simple to do) and store your most sensitive information there. That way when you're not explicitly using this sensitive information you could unmount the partition, which ensures that this information remains secure - even if you happen to leave your computer unatttended while you step out.

2) If you are out running errands and happen to realize you left your computer on, you could simply power it down remotely. Now, since your real sensitive information is on a separate encrypted partition - which is unmounted and encrypted - if an attacker was using the system before you had a chance to power it down, it would at least ensure they will not compromise this specific data. However, in this legnth of time, they could have installed a keylogger or other malicious software to ultimatley steal your data.

2a) If you happen to be away at roughly the same time of the day, you could create an automated task that will automatically shut the machine down at set times. 

2b) You could also write a small script that checks for the precense of a special hash key located on removable media. If the key is located successfully, then the script would do nothing. if the key was not located (Meaning the removable media is disconnected or unmounted) then it could power the machine down. Do this using a USB thumbdrive, and attach it to your house or car keys. Set the interval to check every hour or however long you wish. The beauty of this is that if you wanted to leave your computer on to finish a task, and knew it would take 2 hours, then you could use CRON to run your verification script in 2 hours and 10 minutes, giving you a more secure alternative to just leaving it on and walking away for much longer than expected.

2c) Restrict your normal account so it cannot compile software, install software, or anything else meaningful that an attacker would use to drop malicious software on your computer before it is shut down.

2d) When coming back to use the machine, inspect it for hardware which does not belong. An attacker could have attached a hardware keylogger when you were away.

2e) Keep up-to-date and encrypted backups of your important data on removable media. Now, if you remotely suspect that an attacker was using this machine while you were away, and you truly need to keep this information completely confidential, securely erase all of the hard drives, reinstall your operating system, re-implement all of your security/policies, and reload your sensitive information from your secure backup.

3) Disable the ability to reboot from removable media and set a BIOS password. This would at least make it more difficult to compromise the physical security of your computer. They could physically remove the drives, but it at least makes it more difficult.

3a) Instead of storing an unencrypted partition for /boot, use a USB thumbdrive that you keep on your person at all times. This prevents you from being tricked into loading malicious content which would then be used to steal your information.

The single most important thing here is to store your truly sensitive information in a serparate storage container that is encrypted, and only decrypted when you're actually using the information it is protecting. This makes it far less likely that you would accidently leave this important information exposed for long periods of time.

Also, please ensure you use a different complex password to encrypt the partition or container. This way, if you left the machine on and someone extracted your key from memory, they still would not have access to the encrypted partition or container which is actually housing your sensitive information.

In addition to all of this, find other ways to increase your physical security where possible and applicable. Lock the computer case, store it in a secure (locked) cabinet, lock the door to your room, keep all of the doors/windows locked in your home, et cetera.

Implement these strategies, and forget about some ultra-fast secure wipe you could possibly perform remotely. It is better to use the existing security technologies you have in place versus trying to complicate things that likely won't work as you intended them to anyway.

---

### Post by Stonecold1995 on 2012-08-25
> **troopa said:**
> 1) In addition to full-disk encryption (Which, like I said earlier, is only meaningful when the computer is powered down) you should create a second encrypted partition (You could also create an encrypted container with TrueCrypt which is very simple to do) and store your most sensitive information there. That way when you're not explicitly using this sensitive information you could unmount the partition, which ensures that this information remains secure - even if you happen to leave your computer unatttended while you step out.

I do that.  I have several layers of encryption.  My / partition is encrypted, and my /home partition is encrypted with a different (and much longer) password.  Then I have a TrueCrypt partition for my sensitive data, and another TrueCrypt volume within *that* which contains the most sensitive stuff (although I don't have any hidden partitions because I worry about the data being overwritten accidentally, plus I don't know what convincing data I'd put there for plausible deniability).

> **troopa said:**
> 2b) You could also write a small script that checks for the precense of a special hash key located on removable media. If the key is located successfully, then the script would do nothing. if the key was not located (Meaning the removable media is disconnected or unmounted) then it could power the machine down. Do this using a USB thumbdrive, and attach it to your house or car keys. Set the interval to check every hour or however long you wish. The beauty of this is that if you wanted to leave your computer on to finish a task, and knew it would take 2 hours, then you could use CRON to run your verification script in 2 hours and 10 minutes, giving you a more secure alternative to just leaving it on and walking away for much longer than expected.

That's really brilliant, I'll try that!

> **troopa said:**
> 2c) Restrict your normal account so it cannot compile software, install software, or anything else meaningful that an attacker would use to drop malicious software on your computer before it is shut down.

I never log in as root, and my account has all sensitive features disabled (although I am in the sudoers group, which I might change).

> **troopa said:**
> 2d) When coming back to use the machine, inspect it for hardware which does not belong. An attacker could have attached a hardware keylogger when you were away.

That's one of the reasons I didn't buy a desktop, too much room inside to hide spying hardware.  My laptop is custom built and I don't think it could really fit anything else in it.

> **troopa said:**
> 2e) Keep up-to-date and encrypted backups of your important data on removable media. Now, if you remotely suspect that an attacker was using this machine while you were away, and you truly need to keep this information completely confidential, securely erase all of the hard drives, reinstall your operating system, re-implement all of your security/policies, and reload your sensitive information from your secure backup.

I keep encrypted backups for that very reason.

> **troopa said:**
> 3) Disable the ability to reboot from removable media and set a BIOS password. This would at least make it more difficult to compromise the physical security of your computer. They could physically remove the drives, but it at least makes it more difficult.

The ability to boot from removable media is not disabled, but it's locked with a BIOS password.  I also have a power-on password.  I'm guessing it would be pretty hard to reset the BIOS password because it's a laptop so the CMOS chip is safely locked inside.  As for removing the drives, I don't think that would be possible without me noticing, because the drives aren't easily removable.

> **troopa said:**
> 3a) Instead of storing an unencrypted partition for /boot, use a USB thumbdrive that you keep on your person at all times. This prevents you from being tricked into loading malicious content which would then be used to steal your information.

I've thought about doing that (maybe I'd use a recordable CD instead, because it can't be re-written like a flash drive could), but I decided instead to use a script which checked my /boot partition for changes.  The script checks the md5sums (I'm thinking of changing it to use sha1sum, or maybe even something like Whirlpool) of all files in /boot, along with the inodes they are on (to detect a file somehow being moved), and also checks the MBR to make sure it wasn't modified.  Unfortunately the script doesn't do anything about fixing the issue, but it does alert me when KDE starts of the boot changes, and gives me the option to either fix it or accept the changed state as the new standard.  I'll probably modify the script so that it'll alert me after / is mounted but *before* /home mounts.  Because I didn't make the script myself (I did make quite a few changes though) and it's public, I'm thinking of creating an extra script which will try and make sure the first two scripts (their are two, one for detecting changes and one for reporting them) haven't been modified at all (if an attacker knew I had that script, they might use a bootkit which deletes any file under its name and in its location).  I also manually check the /boot partition every once in a while.

> **troopa said:**
> The single most important thing here is to store your truly sensitive information in a serparate storage container that is encrypted, and only decrypted when you're actually using the information it is protecting. This makes it far less likely that you would accidently leave this important information exposed for long periods of time.

I don't do that because I'd often forget it and leave it somewhere, whereas I always know the location of my computer.  My most sensitive data is within a TrueCrypt volume within another one on my hard drive.

> **troopa said:**
> Also, please ensure you use a different complex password to encrypt the partition or container. This way, if you left the machine on and someone extracted your key from memory, they still would not have access to the encrypted partition or container which is actually housing your sensitive information.

Unfortunately my /home encryption key and my TrueCrypt encryption key are the same, but I know neither stores they actual plaintext password, it only stores the hash of it along with the result of the hash after being salted (hash(salt+pass), I think), so if someone where to get their hands on the decryption key (through a cold-boot attack or direct memory access attack) it wouldn't be valid for any other partition, even if it had the same original password.  The only way to be able to access both is to brute force one and get the key that way, which I think would be very hard because I use Serpent-Twofish-AES for my TrueCrypt volume and AES for my /home partition.  But those are the only two things I have the same password for and I'm planning on changing that soon.

> **troopa said:**
> Implement these strategies, and forget about some ultra-fast secure wipe you could possibly perform remotely. It is better to use the existing security technologies you have in place versus trying to complicate things that likely won't work as you intended them to anyway.

Thank you very much for such a complete response, it's very helpful.

Currently, these are my lines of defense:
-A power-on and BIOS administrator password
-Encrypted /, /home, and TrueCrypt partitions (plus encrypted external drives for backup)
-A script to make sure the contents of /boot or the MBR don't change

I also have programs to detect intrusion:
-ClamAV, because I use Wine often and obviously I don't want a Windows keylogger
-Tiger, unhide, chkrootkit, and rkhunter (I plan on installing TripWire but I've heard it can cause incompatibility problems)
-The OSSEC HIDS, although I installed that only recently and I'm still getting use to using it
-AppArmor (I plan on switching to SELinux after I get use to using it on Fedora)
-A script I made myself (with some help from here) which will kill sensitive applications if my VPN ever disconnects (I have three VPNs, BTGuard, Anonine, and VPNTunnel, although I think there's something wrong with my Anonine account), and also logs when my IP or VPN changes, and when any sensitive applications, like KTorrent, KVIRC, Chromium, etc change state.

I plan on either setting up a cron job, or making a script to run as a daemon that monitors for the presence of anything plugged into the FireWire port, and if anything is it'll shut down the computer to prevent direct memory access attacks (I never use FireWire anyways).

I'm also thinking of buying a USB accelerometer.  I'll write a script so that if it's either removed, or if it detects movement indicative of the laptop being picked up without the password being entered, it'll do an emergency sync and unmount of all partitions, then play a really loud alarm (its a gaming laptop so it has ridiculously loud speakers), as well as send an e-mail to me (and my brother).  I'd use that for anytime I'd bring my computer to a public place (for example if I had to use the bathroom but my computer was in the middle of something where I couldn't shut it down without data loss).  I got that idea from someone who made a Python script that did something similar.

I tried setting up smem (from the secure-delete package) to run at shutdown, but I have 16GB of RAM so it takes WAY to long to do.  And the computer has a BIOS password so I can't simply get it to reboot and automatically run MemTest86+...

I *WOULD* set up a dead-man's hand, but I worry too much about it accidentally destroying all my data.


Is there anything else that I should have that I'm missing?  I have a tendency to completely forget about common-sense measures or obvious things to do...

Again, thanks for such a thorough answer. :)

---

### Post by ooVoh9em on 2012-08-26
> **Stonecold1995 said:**
> I do that.  I have several layers of encryption.  My / partition is encrypted, and my /home partition is encrypted with a different (and much longer) password.  Then I have a TrueCrypt partition for my sensitive data, and another TrueCrypt volume within *that* which contains the most sensitive stuff (although I don't have any hidden partitions because I worry about the data being overwritten accidentally, plus I don't know what convincing data I'd put there for plausible deniability).



That's really brilliant, I'll try that!



I never log in as root, and my account has all sensitive features disabled (although I am in the sudoers group, which I might change).



That's one of the reasons I didn't buy a desktop, too much room inside to hide spying hardware.  My laptop is custom built and I don't think it could really fit anything else in it.



I keep encrypted backups for that very reason.



The ability to boot from removable media is not disabled, but it's locked with a BIOS password.  I also have a power-on password.  I'm guessing it would be pretty hard to reset the BIOS password because it's a laptop so the CMOS chip is safely locked inside.  As for removing the drives, I don't think that would be possible without me noticing, because the drives aren't easily removable.



I've thought about doing that (maybe I'd use a recordable CD instead, because it can't be re-written like a flash drive could), but I decided instead to use a script which checked my /boot partition for changes.  The script checks the md5sums (I'm thinking of changing it to use sha1sum, or maybe even something like Whirlpool) of all files in /boot, along with the inodes they are on (to detect a file somehow being moved), and also checks the MBR to make sure it wasn't modified.  Unfortunately the script doesn't do anything about fixing the issue, but it does alert me when KDE starts of the boot changes, and gives me the option to either fix it or accept the changed state as the new standard.  I'll probably modify the script so that it'll alert me after / is mounted but *before* /home mounts.  Because I didn't make the script myself (I did make quite a few changes though) and it's public, I'm thinking of creating an extra script which will try and make sure the first two scripts (their are two, one for detecting changes and one for reporting them) haven't been modified at all (if an attacker knew I had that script, they might use a bootkit which deletes any file under its name and in its location).  I also manually check the /boot partition every once in a while.



I don't do that because I'd often forget it and leave it somewhere, whereas I always know the location of my computer.  My most sensitive data is within a TrueCrypt volume within another one on my hard drive.



Unfortunately my /home encryption key and my TrueCrypt encryption key are the same, but I know neither stores they actual plaintext password, it only stores the hash of it along with the result of the hash after being salted (hash(salt+pass), I think), so if someone where to get their hands on the decryption key (through a cold-boot attack or direct memory access attack) it wouldn't be valid for any other partition, even if it had the same original password.  The only way to be able to access both is to brute force one and get the key that way, which I think would be very hard because I use Serpent-Twofish-AES for my TrueCrypt volume and AES for my /home partition.  But those are the only two things I have the same password for and I'm planning on changing that soon.



Thank you very much for such a complete response, it's very helpful.

Currently, these are my lines of defense:
-A power-on and BIOS administrator password
-Encrypted /, /home, and TrueCrypt partitions (plus encrypted external drives for backup)
-A script to make sure the contents of /boot or the MBR don't change

I also have programs to detect intrusion:
-ClamAV, because I use Wine often and obviously I don't want a Windows keylogger
-Tiger, unhide, chkrootkit, and rkhunter (I plan on installing TripWire but I've heard it can cause incompatibility problems)
-The OSSEC HIDS, although I installed that only recently and I'm still getting use to using it
-AppArmor (I plan on switching to SELinux after I get use to using it on Fedora)
-A script I made myself (with some help from here) which will kill sensitive applications if my VPN ever disconnects (I have three VPNs, BTGuard, Anonine, and VPNTunnel, although I think there's something wrong with my Anonine account), and also logs when my IP or VPN changes, and when any sensitive applications, like KTorrent, KVIRC, Chromium, etc change state.

I plan on either setting up a cron job, or making a script to run as a daemon that monitors for the presence of anything plugged into the FireWire port, and if anything is it'll shut down the computer to prevent direct memory access attacks (I never use FireWire anyways).

I'm also thinking of buying a USB accelerometer.  I'll write a script so that if it's either removed, or if it detects movement indicative of the laptop being picked up without the password being entered, it'll do an emergency sync and unmount of all partitions, then play a really loud alarm (its a gaming laptop so it has ridiculously loud speakers), as well as send an e-mail to me (and my brother).  I'd use that for anytime I'd bring my computer to a public place (for example if I had to use the bathroom but my computer was in the middle of something where I couldn't shut it down without data loss).  I got that idea from someone who made a Python script that did something similar.

I tried setting up smem (from the secure-delete package) to run at shutdown, but I have 16GB of RAM so it takes WAY to long to do.  And the computer has a BIOS password so I can't simply get it to reboot and automatically run MemTest86+...

I *WOULD* set up a dead-man's hand, but I worry too much about it accidentally destroying all my data.


Is there anything else that I should have that I'm missing?  I have a tendency to completely forget about common-sense measures or obvious things to do...

Again, thanks for such a thorough answer. :)

Instead of writing a script to detect the precense of a firewire device, why not just disable it in the BIOS? That would prevent from anyone using it, and you could always enable it again if you needed to use it yourself. This would be the most secure option.

Don't allow removable media to be automaticlly mounted, and restrict your account so it cannot mount devices. When you need to use removable media, manually mount it with sudo, so it at least requires a password.

I would go into your BIOS, disable all onboard features that you're not using (FireWire, whatever) and that would cut down on potential attack vectors. If you only use some features every now and then, you could disable them and only enable the onboard feature when you want to use it.

Those are just a few added ideas that might help increase your security a little.

---

### Post by Stonecold1995 on 2012-08-26
> **troopa said:**
> Instead of writing a script to detect the precense of a firewire device, why not just disable it in the BIOS? That would prevent from anyone using it, and you could always enable it again if you needed to use it yourself. This would be the most secure option.

Don't allow removable media to be automaticlly mounted, and restrict your account so it cannot mount devices. When you need to use removable media, manually mount it with sudo, so it at least requires a password.

I would go into your BIOS, disable all onboard features that you're not using (FireWire, whatever) and that would cut down on potential attack vectors. If you only use some features every now and then, you could disable them and only enable the onboard feature when you want to use it.

Those are just a few added ideas that might help increase your security a little.

Sadly my computer's BIOS is extremely limited, and I can't do anything more than change boot order, set BIOS passwords, and change rapid-start.  Which is really retarded IMO, because this is a custom gaming laptop that cost over $3,000 and I should THINK they should at LEAST use a BIOS vendor that supports overclocking!  My computer has American Megatrends, and I hate everything about them except the Triforce they use as their logo. ;)

As for disabling auto-mount, is there any other privileges I should remove?  [This]("http://www.pictureshack.us/images/32898_priv.png") is currently what's active (I think it's the default).  And where can I find out what the effects of disabling/enabling specific ones are?  Like, if I were to disable "administer the system", would that prevent me from using sudo or prevent me from accessing system settings or what?

---

### Post by ooVoh9em on 2012-08-26
> **Stonecold1995 said:**
> Sadly my computer's BIOS is extremely limited, and I can't do anything more than change boot order, set BIOS passwords, and change rapid-start.  Which is really retarded IMO, because this is a custom gaming laptop that cost over $3,000 and I should THINK they should at LEAST use a BIOS vendor that supports overclocking!  My computer has American Megatrends, and I hate everything about them except the Triforce they use as their logo. ;)

As for disabling auto-mount, is there any other privileges I should remove?  [This]("http://www.pictureshack.us/images/32898_priv.png") is currently what's active (I think it's the default).  And where can I find out what the effects of disabling/enabling specific ones are?  Like, if I were to disable "administer the system", would that prevent me from using sudo or prevent me from accessing system settings or what?

You should read up a little on file permissions, access control lists, and other mechanisms that you can use to further secure your Environment.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://refspecs.linux-foundation.org/LSB_3.2.0/LSB-Core-generic/LSB-Core-generic/usernames.html](http://refspecs.linux-foundation.org/LSB_3.2.0/LSB-Core-generic/LSB-Core-generic/usernames.html)

To answer your questionL If you disable the administration functions, you would lose the ability to use sudo, and thus lose the ability access large critical parts of your system.

It is a good idea to have one extremely limited account with next to no real permissions, and simply allow it to do two things:

1) Access the Internet
2) Use some applications

Using the crippled account when in public would be ideal if you're just surfing the web. Then if someone were to use the computer, they would be using an extremely limited account.

Check the links I posted out, and you will better learn how to limit access to files and resources.

---

