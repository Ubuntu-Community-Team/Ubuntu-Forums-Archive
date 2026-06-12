---
title: "ubuntu encrypt"
date: 2010-06-01
forum: Security
---

### Post by Drenriza on 2010-06-01
How can i encrypt my entire system (laptop) so if it gets stolen, the thief cant use it.

Thanks on advnace.
Kind Regards.

---

### Post by new_tolinux on 2010-06-01
As far as I know: you can't. You can however encrypt your home-directory.

Besides that it's pretty useless. As soon as I format the drive and install any operating system the encryption really doesn't bother me to use the laptop anymore.

The most secure way is to set a boot-password in the BIOS, although with a little knowledge that can be removed in some way on most brands. Although, this is assuming that I'm interested in the hardware (e.g. to sell it), not the data on it.

---

### Post by Drenriza on 2010-06-01
I see. So if i encrypt my home directory, where i have loads of work files.

Then the pc gets stolen. Can the thief then encrypt it back to usable data? How strong is the encryption?

I want to encrypt my work files since i have sensitive data.

Also, how easy is it go get around the ubuntu-login-password?

thanks on advance.

---

### Post by new_tolinux on 2010-06-01
No encryption is unbreakable. Even if it's "unbroken" yet, it can be broken if you'll put enough effort (brute force) into it. That will take days/weeks/years depending on the encryption-system and the chosen password.

Besides that it's really easy to get around the Ubuntu login password, since Grub allows you to jump to a root-prompt where you can simply reset the user-password.

---

### Post by Drenriza on 2010-06-01
Okey. How do i enable a strong encryption on my home directory.

Can you brake the encryption besides brute-force? like reset it or something else. I dunno, so asking.

---

### Post by new_tolinux on 2010-06-01
> **Drenriza said:**
> Okey. How do i enable a strong encryption on my home directory.

Can you brake the encryption besides brute-force? like reset it or something else. I dunno, so asking.
As far as I remember (but I did not check that again) you don't have to break anything.
When you reset the user-password, you are able to login and with that your home-directory is decrypted.

Resetting the user password really is a <5 minute-job.

What I've read is that truecrypt is a much better way to secure your sensitive data, but afaik it's impossible to put your home-directory in a truecrypt volume.

---

### Post by Grenage on 2010-06-01
You have a couple of options:

Encrypt the whole disk.
Encrypt the area containing your work.

Option one would require something like the alternate install CD and LVM encryption, I believe.  Option two can be done easily by installing Truecrypt.  Either way, you don't want to forget or lose your password.

---

### Post by new_tolinux on 2010-06-01
> **Grenage said:**
> Option one would require something like the alternate install CD and LVM encryption, I believe.
It does. I installed 9.04 and later 9.10 that way. It will ask you for a password before you'll even get to the login-screen.

Even if someone manages to reset the user password, that's not granting them access to the encrypted LVM-partitions.

Edit: It would stop nobody from formatting the drive and install another OS.

---

### Post by Drenriza on 2010-06-01
Okey if i want to encrypt my whole disk, if possible. What is the best way to do this?

Im only intersted in this saloution if the data cant be decrypted easily, by resetting something. But by brute-force the password.

Also that you cant do something and go in and spoof the encryption password. Since then its useless. 

How is this done?

And how does it work? Does it ask for my password before my login password? to decrypt the HDD.

---

### Post by new_tolinux on 2010-06-01
> **Drenriza said:**
> Okey if i want to encrypt my whole disk, if possible. What is the best way to do this?

Im only intersted in this saloution if the data cant be decrypted easily, by resetting something. But by brute-force the password.

Also that you cant do something and go in and spoof the encryption password. Since then its useless. 

How is this done?

And how does it work? Does it ask for my password before my login password? to decrypt the HDD.
If you install your system with the "Alternate"-disc that can be downloaded, you'll be given the choice to use the whole disk, using LVM and ecryption. For what I know you can not do this on an existing install, so you'll have to reinstall your laptop.

Shortly after Grub you'll be prompted to enter the password that you've set during installation (I don't know how or if you can change that afterwards).

As far as I know that's a quite secure way, ofcourse one of the major variables is the strength of your password. Choosing "ubuntu", "laptop" or even "password" as a password will not really make it secure ofcourse ;)

---

### Post by Grenage on 2010-06-01
Bingo, it's all down to your password.  Remember - if you lose your password, you lose your data.

---

### Post by Drenriza on 2010-06-01
Will i be able to take my files/programs/system-settings from my "old" laptop and copy it over to the clean install. So i quickly can get my system backup and running.

Since a 100% clean install will take several hours.

---

### Post by new_tolinux on 2010-06-01
> **Drenriza said:**
> Will i be able to take my files/programs/system-settings from my "old" laptop and copy it over to the clean install. So i quickly can get my system backup and running.

Since a 100% clean install will take several hours.
You _can_ copy most of the config-files. However, you can't simply copy the programs.

Keep in mind that the drive is going to be emptied, so the place to backup your config-files is on a CD/DVD/usb-stick/network-share. Actually anywhere which is _not_ on the drive where you're going to install Ubuntu to.

---

### Post by Drenriza on 2010-06-01
Yes ofc. I was thinking of a network HDD temporarily. 

But i cant copy my programs? instead of installing them again on a "new" system?

---

### Post by Drenriza on 2010-06-01
i was thinking about this guide, to re-install programs if it cant be done any other way. What do you guys think. Is their a better way then doing it like this?



GUIDE:
First, let&#8217;s make the list. You&#8217;ll be doing all of this in a Terminal Session:
dpkg &#8211;get-selections | grep -v deinstall > ubuntu-files
NOTE: Wordpress interprets two dashes (- -) as one dash (&#8211;). When you&#8217;re putting this into your CLI, make sure it&#8217;s dropping two dashes &#8216;- -&#8217; without the space between them.
Now you&#8217;ve got a list of all of your installed debs in a fairly small file. In my case, I simply moved this file to a thumb-drive. You could also store it on a separate partition or on a disk somewhere. Heck, it&#8217;s not that big, email it to your gmail account.
So now you&#8217;ve got this list and all is well, until you&#8217;re Ubuntu install either dies or has to be reinstalled for some reason. Go ahead and do the base install.
Once you&#8217;ve got Ubuntu back up and running, copy your ubuntu-files back into your home directory and do the following:
sudo apt-get update
sudo apt-get dist-upgrade
dpkg &#8211;set-selections < ubuntu-files
NOTE: Wordpress interprets two dashes (- -) as one dash (&#8211;). When you&#8217;re putting this into your CLI, make sure it&#8217;s dropping two dashes &#8216;- -&#8217; without the space between them.
Now you&#8217;ve told your system what it needs to install, so let&#8217;s install it all.
sudo dselect
This will open up a dselect session. Type &#8216;I&#8216; and allow dselect to install of the the packages listed in your ubuntu-files document. When it&#8217;s finished, type &#8216;Q&#8216; and hit the ENTER key to exit dselect.
Now you&#8217;re a lot closer to where you were before.
EDIT: As fak3r points out, you can modify the fist dpkg command line to have it mail yourself the list after creatoin. Like so:
dpkg &#8211;get-selections | grep -v deinstall > ubuntu-files; cat ubuntu-files | mailx -s &#8220;ubuntu-files&#8221;my.mail@my.address

I have not spent alot of time looking at this guide. Just copyed it down for "future" use. Like now, prehaps. So what do you guys think.

---

### Post by new_tolinux on 2010-06-01
> **Drenriza said:**
> i was thinking about this guide, to re-install programs if it cant be done any other way. What do you guys think. Is their a better way then doing it like this?
The first thing I see is that this guide is dealing with a system upgrade, which is not the case.

The reason that you can't just copy a program is that most programs (for example Apache) has also files in /etc/init.d/ /etc/apparmor.d/ etc.

If I do a reinstall on my webserver, I only copy the contents of these folders and their subdirectories:
/home/user/
/etc/apache2/
/etc/php5/
/etc/mysql/
mysql datastore
/var/www/

Then, after an install I simply put the last 2 folders back on the places where I found them.
From the other folders I do select afterwards which file(s) I need to replace any existing file (for example my /etc/apache2/sites-enabled/files and my php.ini)

---

### Post by Drenriza on 2010-06-01
Okey. I will let it grubble a bit in my head. And see what i come up with.

anyone have a direct link to a working 10.04 alternative cd that i need to do the encryption?

---

### Post by new_tolinux on 2010-06-01
> **Drenriza said:**
> Okey. I will let it grubble a bit in my head. And see what i come up with.

anyone have a direct link to a working 10.04 alternative cd that i need to do the encryption?
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)
Then click on any desired location, for instance I just clicked on an university in Aachen (Germany).
After that I clicked the 10.04 link which brought me here: [http://ftp.halifax.rwth-aachen.de/ubuntu-releases/lucid/](http://ftp.halifax.rwth-aachen.de/ubuntu-releases/lucid/)
On that page I find a 32-bit installer (x86) [http://ftp.halifax.rwth-aachen.de/ubuntu-releases/lucid/ubuntu-10.04-alternate-i386.iso](http://ftp.halifax.rwth-aachen.de/ubuntu-releases/lucid/ubuntu-10.04-alternate-i386.iso)
And a x64-installer: [http://ftp.halifax.rwth-aachen.de/ubuntu-releases/lucid/ubuntu-10.04-alternate-amd64.iso](http://ftp.halifax.rwth-aachen.de/ubuntu-releases/lucid/ubuntu-10.04-alternate-amd64.iso)

But depending on where you live, another mirror (more in your area) may be better to use.

Edit: Denmark links:
[ftp://ftp.klid.dk/ubuntu-cd/](ftp://ftp.klid.dk/ubuntu-cd/) Denmark KLID
[http://mirrors.dotsrc.org/ubuntu-cd/](http://mirrors.dotsrc.org/ubuntu-cd/) Denmark dotsrc.org

---

### Post by Drenriza on 2010-06-01
Super.

Thanks for all guys.

Kind Regards.

---

### Post by GrantStoner on 2010-06-13
The best way is using the Alternate CD. You can find them all at resources.ubuntu.com they have them all. And using that to set up the encrypted LVM is much better than truecrypt. The default encryption algorithm used by Ubuntu on the Alternate CD is AES-256. The strongest truecrypt allows is AES-128, not even AES-192. And using this method you encrypt more than just the /home directory. You can encrypt everything except /boot. In any case, /boot never holds any data you'd want to protect anyhow, it just allows Grub to load, and Grub cannot be encrypted... yet. There's rumors that there has been tests on the new Grub2 which could make it possible to encrypt /boot.

---

### Post by Perkins on 2010-06-14
To save download time reinstalling your programs you can use AptOnCd to copy your apt cache onto a CD or DVD.  You can then put them back on the new install.  It won't necessarily get *all* of your programs, but it will have the ones that you've added since the last time your cache was cleared.

---

### Post by Keypel on 2010-07-25
> **GrantStoner said:**
> The best way is using the Alternate CD. You can find them all at resources.ubuntu.com they have them all.

I can't find the site "[resources.ubuntu.com]("http://resources.ubuntu.com")" I even googled it for simular results to no avail.

EDIT

I think maybe GrantStoner meant [releases.ubuntu.com]("http://ubuntuforums.org/releases.ubuntu.com"). I just happened to stumble upon it while reading something unrelated.

---

### Post by GrantStoner on 2010-07-25
Yeah, sorry, that's what I meant. They'll have everything there. Really all you need encrypted though should be your /home directory.

---

### Post by Perkins on 2010-07-25
That depends on how sensitive the data you have is.  For the average person, just the home directory is probably enough.  If you're dealing with classified information or corporate secrets or something, encrypt the entire drive, including the swap partition.  Otherwise bits of your data may get written to the temp folder, or to swap, or to logfiles, unencrypted.  A determined thief could then possibly recover pieces of it.  If you have enough memory the performance penalty for full disk encryption will be mostly negated by the cache.

---

### Post by stormzen on 2010-07-26
I've got an encrypted dual boot system.  We use PGP desktop ( which I think also encrypts the boot sector of the drive ), after logging in, I then hit the Grub menu.  After passing through that, I get the prompt to enter the password for the LVM encryption.  It's worked like a charm so far, though I've never attempted to suspend a login session.

I'm currently running Jaunty, and I'd like to upgrade to Lucid.  Can this be done from within Jaunty, or without touching the other partitions, or is a new installation my only option?

I noticed for 10.4 that encryption seemed to be an option in the installer itself.  Does that encrypt the swap as well as the file system?

---

### Post by Perkins on 2010-07-27
Theoretically I would expect that you could simply run a distribution  upgrade.  Occasionally there are complications to this, so be sure to  backup your system as thoroughly as though you were doing a fresh  install.

Your second question depends on to which encryption option you are  referring.  The alternate installer for the last several versions has  had the ability to set up LVM encryption for whatever partitions you  want, including swap.  The live CD installer really only gives the  option to encrypt your home directory.

---

### Post by FreedomOverdose on 2010-07-27
If you want a whole-disk encryption tool, I recommend you truecrypt:
[http://www.truecrypt.org/](http://www.truecrypt.org/)

Free, open source, an amazing GUI, and really powerful, from what I've read. It's definitely one of the most popular encryption tools out there

---

### Post by Perkins on 2010-07-27
Truecrypt whole disk encryption only supports Windows.

---

### Post by rpacker on 2010-07-27
I used this tutorial/walk thru which worked well:
[http://blog.nyxyn.com/2010/05/encrypted-ubuntu-104-on-dual-boot.html](http://blog.nyxyn.com/2010/05/encrypted-ubuntu-104-on-dual-boot.html)

However, I have not found out how to update the kernel yet. Probably a simple command, but when there are kernel updates it will bypass the pass phrase screen, which will then fail. Not a big deal unless maybe you're trying to use a pae kernel to support more memory.

---

### Post by Perkins on 2010-07-27
I'm not sure why updating the kernel would screw up the encryption...  Unless the new kernel doesn't support it...  Double-check the parameters in GRUB to make sure that the new kernel is being passed the same ones as the old one.  If it is, then double check to make sure that the kernel you're trying to use supports encryption.  It should, but one never knows.  You can always compile it yourself to get the precise list of options you want.

---

### Post by linux18 on 2010-07-27
Really you don't need encryption, if someone steals your computer they're trying to quickly check for personal data for identity theft and sell it before it gets reported stolen, they won't have a clue what linux is ( some kind of new drug? ) they aren't going to spend all their time learning linux, subverting password login, and look for personal data. they will just wipe the drive and pawn it for drug money.

---

### Post by earthpigg on 2010-07-27
the things discussed here will prevent the thief from accessing your data.

they will not prevent the thief from resetting your bios password and popping a pirated windows 7 install cd into the laptop.

if theft is a concern, here's what i would do:

1) encrypt your home partition as described above
2) create a guest account with no password and no encryption
3) hope the thief sees nothing funny about this and uses the laptop as-is
4) leave sshd and ddclient on the system, and a daemon that logs keystrokes and takes screenshots if anyone is logged in as the guest account.
5) have that daemon e-mail you the keylogs and screenshots whenever the laptop is connected to the internet.
6) give that personal information about the thief to the authorities.

basically, leave a trojan on the laptop. as long as you retain control of the trojan, it isn't a security concern ***for you***.

this would actually be a fun little project, and worth packaging as a .deb. hrm...

---

### Post by Perkins on 2010-07-27
Actually, there is such a project.  The name slips my mind at the moment however.

For the average person, home directory encryption is more than enough to keep personal information safe.  Full-disk encryption is primarily for people who deal with things where a thief might steal the machine *specifically* to get that information, and so won't give up after a cursory attempt.

Of course, unless you *need* every last FLOP of processing power out of your processor, there's no such thing as too *much* security.  Especially on portable devices.

---

### Post by earthpigg on 2010-07-28
> **Perkins said:**
> Actually, there is such a project.  The name slips my mind at the moment however.

Oh, my. 

Please post the project's name in this thread if you happen to remember. I'll see if I can google around a bit, and I'll post back here if I find it.

---

### Post by Perkins on 2010-07-28
[http://adeona.cs.washington.edu/index.html](http://adeona.cs.washington.edu/index.html)

---

### Post by earthpigg on 2010-07-28
> **Perkins said:**
> [http://adeona.cs.washington.edu/index.html](http://adeona.cs.washington.edu/index.html)

interesting, thank you.

im not sure if i buy into their emphasis on location. i'd focus more on identification of the individual, via logging keystrokes.

and i wouldn't bother with encryption of any form. if the thief doesn't want his online banking details published for the world to see, he shouldn't have stolen my laptop.

again, though, thank you.

---

### Post by Perkins on 2010-07-28
Identifying locations and patterns of movement is much more expedient for tracking down and recovering the hardware than identifying the person.  If you know where the machine is physically located, you can go find it.  If you know who has it, you still have to figure out where they are.  Ideally you would do both, but location is what you're most likely to be able to get before they wipe the machine.

The encryption is to keep *other* people from collecting the data it transmits and using it to track *your* movements and activities.  This is something of an oversight in some proprietary tracking schemes.

---

### Post by rpacker on 2010-08-06
> **Perkins said:**
> I'm not sure why updating the kernel would screw up the encryption...  Unless the new kernel doesn't support it...  Double-check the parameters in GRUB to make sure that the new kernel is being passed the same ones as the old one.  If it is, then double check to make sure that the kernel you're trying to use supports encryption.  It should, but one never knows.  You can always compile it yourself to get the precise list of options you want.
Since I don't see any posts on it, I suppose my problem is unique (awesome), anyhow, I can only use the kernel that came with install. I've checked grub and I don't see any difference. 
But like I said I don't get the passphrase screen for any other kernels that have since been installed with the updates. I get "ALERT! /dev/mapper/newbuntu-Main does not exist. Dropping to a shell!." Then is gives a prompt like:
(initramfs)

With the kernel that it came with it works great though.

---

### Post by Perkins on 2010-08-06
Ok, so somehow with the new kernels it's not mounting the encrypted root partition...  Check the grub configuration. The entries should be identical except for the kernel version.  Other than that I don't know what to suggest.  I've got an encrypted install on a thumbdrive that I carry around, and it always upgrades kernels just fine...

You might try updating to GRUB2 if you haven't already...  That might fix it...  Backup your system first.

---

