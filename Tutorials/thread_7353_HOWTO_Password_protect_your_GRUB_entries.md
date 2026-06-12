---
title: "HOWTO: Password protect your GRUB entries"
date: 2004-12-06
forum: Tutorials
---

### Post by HungSquirrel on 2004-12-06
If you don't want someone booting your machine without permission, you can add a password to your GRUB entries.  You can add a password only to specific entries if you wish; this will require a user to enter a password before loading only those boot entries you protect.  This can be useful when done on your Recovery Mode entries, which bring up a passwordless root login by default.

To get started, let's first encrypt the password we want to use.  Open up a terminal and enter the *grub* command.  This brings up a grub shell.  In this shell, enter the *md5crypt* command.  When prompted, type in the password you want on your grub entries.  (Don't worry, this won't write anything to your files!)  After pressing Enter, you will be given an encrypted password string.  Copy the string to your clipboard.  Enter *quit* to exit the grub shell and return to bash.

```

    GNU GRUB  version 0.95  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub> md5crypt

Password: *************
Encrypted: $1$w7Epf0$vX6rxpozznLAVxZGkcFcs.

grub>

```

Now that we have an encrypted password, it's time to add it to grub.  Using sudo, open up /boot/grub/menu.lst using your favorite text editor.

After the "initrd" line for each entry you want to password protect, start a new line beginning with *password --md5 * and paste in your newly-encrypted password.  Using the above example password on the i386 recovery entry, this:
```
title Ubuntu, kernel 2.6.8.1-2-386 (recovery mode)
        root (hd1,2)
        kernel /boot/vmlinuz-2.6.8.1-2-386 root=/dev/hdb3 ro single
        initrd /boot/initrd.img-2.6.8.1-2-386
```


Becomes this:
```
title Ubuntu, kernel 2.6.8.1-2-386 (recovery mode)
        root (hd1,2)
        kernel /boot/vmlinuz-2.6.8.1-2-386 root=/dev/hdb3 ro single
        initrd /boot/initrd.img-2.6.8.1-2-386
        password --md5 $1$w7Epf0$vX6rxpozznLAVxZGkcFcs.
```

You must add such a line after every entry you want to password protect.  As I mentioned earlier, I password protected my recovery mode entries out of sheer paranoia.  :)

Save the file, and reboot.  (The first time you try this, I suggest only doing it to one entry so you can test it to make sure it works, and you can still use another entry to boot your machine in case something went wrong.)

For a bit of added peace of mind, you can prevent everyone except root from reading /boot/grub/menu.lst by doing:

```
sudo chmod 600 /boot/grub/menu.lst
```

---

### Post by jdong on 2004-12-11
Let's add a few disclaimers:

WARNING #1: This is **not failproof**. Duh, nothing ever is. It doesn't take much effort to pull out a LiveCD and bypass this.

WARNING #2: Don't use an 'important password' for this! The password can be read through a LiveCD and such. Yes -- even if you do chmod it. And you can't store GRUB on an encrypted partition, either! LOL.

---

### Post by poptones on 2004-12-11
Don't leave it alone.

If you want to make sure your information is reasonably secure when you're not around, move /home, /var, /tmp and /root into /usr and encrypt /usr. If you want to make sure no one can even boot it, setup a bios password and lock the case.

Oh... and make sure you always turn the machine off when you're not around.

Anything else is just adding inconvenience for nothing.

---

### Post by Ramses de Norre on 2007-01-26
> **jdong said:**
> 
WARNING #2: Don't use an 'important password' for this! The password can be read through a LiveCD and such. Yes -- even if you do chmod it. And you can't store GRUB on an encrypted partition, either! LOL.

They can only read the md5sum, don't they? And as far as I know it's almost impossible to retain the password from a dirty md5 hash like the ones created by md5crypt (dirty means there are random characters inserted).

---

### Post by zasf on 2007-04-21
> **jdong said:**
> Let's add a few disclaimers:

WARNING #1: This is **not failproof**. Duh, nothing ever is. It doesn't take much effort to pull out a LiveCD and bypass this.

WARNING #2: Don't use an 'important password' for this! The password can be read through a LiveCD and such. Yes -- even if you do chmod it. And you can't store GRUB on an encrypted partition, either! LOL.

what if you also password protect BIOS settings and you don't allow the comp to be booted via CDROM? I think the combination of grub and bios password protected is a good solution.. if you assume that nobody would steal your comp and mount the hard disk on another machine :)

---

### Post by toxic-hero on 2007-04-25
what if i have a dual boot system with ubuntu & windoze? i set up a password to my ubuntu recovery mode boot. so, do i also have to set up a password to a windoze boot? and how to do that???

toxic

---

### Post by virx on 2007-05-09
Now I have to enter password every time I boot.

Is it possible to make GRUB ask for password only if somebody tries to edit GRUB lines during boot (wants to boot into single user mode) or disable GRUB editing during boot (disable 'e' key)?


EDIT: And the answere is:
If I put 
password --md5 $1$w7Epf0$vX6rxpozznLAVxZGkcFcs.
before kernels and titles (check menu.lst, where password is commented out),
I get what I want ;)

---

### Post by soul_rebel on 2007-05-23
This "guide" is really imprecise!
You don't need to manually add the password line to every boot stanza you want to lock!
Also in this way you don't secure the interactive prompt!

You add the password line before any boot stanza, just as showed in the file's comments.

Then you add a line that says:
```
lock
```
to any static entry you wish to password protect. Static entry are before the line
```
### BEGIN AUTOMAGIC KERNELS LIST 
```
and after
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
Any non-linux os as a static entry.

For recovery mode, you want to change the line:
```
# lockalternative=false
```
to:
```
# lockalternative=true
```
Leaving the initial comment.
After that you run ```
update-grub
```.
This way every time you update the kernel, the recovery entry will be locked automatically.

Please fix the first post.

---

### Post by ferthur_opensource on 2007-05-25
The last time I checked, most computers these days offer a "Hard Drive Lock" password option in their BIOS.  Using this means that even if your HDD is moved to a different computer, or a liveCD is used, the data still cannot be read from the drive.  That alone is a pretty decent measure to prevent people from booting your computer without your permission.:)  A little off topic as it doesn't cover GRUB, but all the same it does deal with boot-time security.

---

### Post by toxic-hero on 2007-06-02
does grub-md5-crypt use salt? i read that hashes without salt are much easier to crack.

toxic

---

### Post by windwalker78 on 2007-07-18
Soul-reaver is right in this case, but I have had numerous problems with stripped or broken config files in my conscious linux life. Thanks to both of you!

---

### Post by Christophe Vanlancker on 2007-07-29
Just want to remember you guys that Bios passwords can be skipped quite easily.... ofcourse it comes down to having fysical access to the box. One simply needs to open the case, locate the bios flat battery, pull it off, wait a few seconds and the bios will be reset, thus emptying it's memory where it keeps the save file for th](*,)e configurations and bios password.

---

### Post by windwalker78 on 2007-08-19
> **Christophe Vanlancker said:**
> Just want to remember you guys that Bios passwords can be skipped quite easily.... ofcourse it comes down to having fysical access to the box. One simply needs to open the case, locate the bios flat battery, pull it off, wait a few seconds and the bios will be reset, thus emptying it's memory where it keeps the save file for th](*,)e configurations and bios password.

Speaking the truth I have done this at least 10 times without needing physical access to the MB :) However window$ is needed :mad: I should have tried it with wine

---

### Post by raminv2 on 2007-11-09
you guys are great!
Thank you so much....
I'm all set for this issue.

---

### Post by john131971 on 2008-02-19
[http://ubuntusoftware.info/sum.html](http://ubuntusoftware.info/sum.html)

Seems to be the easy way out, for us NOOBS!

---

### Post by Crowder on 2009-06-22
I don't mean to be "THAT GUY," but I don't think all this crazy encryption & password stuff is really all that necessary. Truth be told, I found this thread only because I saw the password line in Grub while I was adding XP to my boot list and was curious about it. 

So here's the reason I'm posting - I have a question.

Why not just set a BIOS hardware password? That way, you have to enter a master password before the computer even begins the process of booting. I've heard it can be reversed by some kind of switch on the motherboard, but I really don't think anyone would ever go to the trouble of opening up my computer. I also don't think anyone will ever rip the hard drive out in order to see my data, so I see no point in encrypting it. I mean, this isn't the CIA (or is it?).

I don't mean to bust your balls, but if somebody knows some huge flaw with the BIOS thing I'd be interested to know.

---

### Post by crystaldart on 2009-08-13
Hi,
Isn't it more easier for a beginner to use the Start Up Manager to set Grub Password ?

Can you please tip me on how to configure the Grub using the Startup Manager ?

Is there any chance of complications/errors arising when using the Start Up Manger (I kind of feel comfortable at easy interface it provides).

What's the advantage using command lines over Start Up Manger?

Thanks friends.

---

### Post by riahc3 on 2009-08-29
> **virx said:**
> Now I have to enter password every time I boot.

Is it possible to make GRUB ask for password only if somebody tries to edit GRUB lines during boot (wants to boot into single user mode) or disable GRUB editing during boot (disable 'e' key)?


EDIT: And the answere is:
If I put 
password --md5 $1$w7Epf0$vX6rxpozznLAVxZGkcFcs.
before kernels and titles (check menu.lst, where password is commented out),
I get what I want ;)

So this makes editing GRUB lines impossible without a password? Great :) Was looking for this. Thanks.

---

### Post by ubudog on 2009-12-17
Seems secure if you disable booting from cd.  Good tutorial.

---

### Post by supertails on 2010-01-07
What if I don't have menu.lst?

---

### Post by noah++ on 2010-02-02
I've found that if you set bootsplash to an invalidly formatted image, GRUB will produce a blank screen until it boots the OS. That hack, combined with a password, provides plausible deniability similar to what the TrueCrypt Windows-only bootloader features.

> **supertails said:**
> What if I don't have menu.lst?
Then you have either **grub.conf** or **grub.cfg**. The latter's format differs from menu.lst, but it is similar enough to work.

---

### Post by ubudog on 2010-02-02
Yeah to change your grub config do: ```
gksu gedit /boot/grub/grub.cfg
```

---

### Post by Crowder on 2010-03-14
> **Crowder said:**
> I don't mean to be "THAT GUY," but I don't think all this crazy encryption & password stuff is really all that necessary. Truth be told, I found this thread only because I saw the password line in Grub while I was adding XP to my boot list and was curious about it. 

So here's the reason I'm posting - I have a question.

Why not just set a BIOS hardware password? That way, you have to enter a master password before the computer even begins the process of booting. I've heard it can be reversed by some kind of switch on the motherboard, but I really don't think anyone would ever go to the trouble of opening up my computer. I also don't think anyone will ever rip the hard drive out in order to see my data, so I see no point in encrypting it. I mean, this isn't the CIA (or is it?).

I don't mean to bust your balls, but if somebody knows some huge flaw with the BIOS thing I'd be interested to know.

Anybody? No?

---

### Post by satish_j on 2010-03-15
Thank you for such a useful post..i was really looking for a mechanism to protect the recovery mode option.An md5 hash as password,is definitely very good and strong approach towards securing my system..

---

### Post by noah++ on 2010-03-15
> **Crowder said:**
> but if somebody knows some huge flaw  with the BIOS thing I'd be interested to know.

Anybody? No?

You should determine the necessity of any security measure by the importance of what's being protected and the likelihood of its loss. In case you simply want to keep your kids off the computer, a BIOS password should be enough. Your kids probably aren't sophisticated or determined enough to break that protection; and even if they did, you would incur no great loss.

I use disk encryption because my computer contains vital passwords and personal data. I know that even in the presence of typical application-level security measures, such as a web browser master password, this data tends to propagate to insecure areas like swap space. 

I know it is relatively unlikely that my computer will be stolen *and *that the thief will be sophisticated and determined enough to mount my hard drive from outside the operating system it hosts. But the data is so important, because it could damage me so much in the wrong hands, I take the measure of encrypting it. (Anyway, the sophistication required to read my unencrypted hard drive is becoming ever less rare.)

---

### Post by Crowder on 2010-03-15
I see your point, but I just have an encrypted file container (via Truecrypt) for that kind of stuff, not the whole drive. Safer, no?

---

### Post by noah++ on 2010-03-16
> **Crowder said:**
> I see your point, but I just have an encrypted file container (via Truecrypt) for that kind of stuff, not the whole drive. Safer, no?
 
No, because some applications may write sensitive data to unsecured areas. Or even if the data starts in a protected area, it's prone to propagate to unsecured areas like swap and temp.

---

### Post by michaelzap on 2010-04-27
> **noah++ said:**
> No, because some applications may write sensitive data to unsecured areas. Or even if the data starts in a protected area, it's prone to propagate to unsecured areas like swap and temp.

I'd say this (or using Ubuntu's encrypted home directory system) is somewhat safer, yes. But noah++ is right that it's easy for data to leak outside of your encrypted container and you can then have the illusion of security without the reality (which is probably worse). This is the danger of using any partial system to encrypt your data, and the flip side is that if you have a problem with your system it will be easier to repair it if you haven't encrypted your entire drive.

If you are really concerned about the security of your data, use full-disk encryption. You may not feel that this is necessary in your case, but I've set it up for a number of people with very real needs for it. A couple examples are a Mexican human rights organization that records testimony of victims and witnesses on laptops in the field and then needs to store that data safely and protect the identities of these people, and a web developer's laptop that he travels with a lot and which contains a great deal of login and banking information for various corporate clients.

So use whatever level of security you think is necessary for your situation, but don't extrapolate from your situation and assume that the needs of others will be as lax (or as comprehensive) as your own.

---

### Post by alphaamanitin on 2010-07-16
Even more important than overwriting data sections in a TrueCrypt (TC) volume is the fact that TC uses pseudo-random headers at the beginning and end of TC volumes.  If this headers are ever damaged-overwriting, corrupted, ad nauseum) the volume can no longer be decrypted PERIOD.  Even if you supply the correct passphrase the volume cannot be salvaged without those headers.  Even trying to recreate the headers with the correct passphrase will not result in the correct header as it is pseudo-random.  It is far better to buy a small extra drive (internal or external) and encrypt the entire drive.  Please read the TC manual for a overview of why encrpyting only part of a SSD may not give the security needed.

AlphaA

---

### Post by ubudog on 2010-07-16
Yes, the alternate install with encryption is what I use, and it is perfect for me.  All my data can't be touched for about a 11 million years of cracking on the world's most powerful supercomputer.  A good option.

---

### Post by Jordy_224 on 2010-12-05
Did not work...sigh...unexpected?
 

grub -v 
```
grub (GNU GRUB 0.97)
```

Password entered 
```
 
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
password --md5 $1$MMs0t/$hOKcWtXNu21A529riQJWr/
```

Locked the grub
```
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
 lockalternative=true
```

grub boot screen did not include the p option to input password. What am i doing wrong? 

Thanks.

---

### Post by muralysunam on 2011-07-25
[SIZE=3]I found to two posts of about grub password. But I dont get a good answer for my problem.
I want to block strangers from passing through Grub menu.
My /boot/grub/menu.1st is shown below[/SIZE]

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=90dc8506-967b-4a33-b1e8-b3e46559fbb9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ff03d393-b4f7-4e41-9b32-a0a7d7a7f900

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.10, kernel 2.6.35-30-generic-pae
uuid        ff03d393-b4f7-4e41-9b32-a0a7d7a7f900
kernel        /vmlinuz-2.6.35-30-generic-pae root=UUID=90dc8506-967b-4a33-b1e8-b3e46559fbb9 ro quiet splash 
initrd        /initrd.img-2.6.35-30-generic-pae

title        Ubuntu 10.10, kernel 2.6.35-30-generic-pae (recovery mode)
uuid        ff03d393-b4f7-4e41-9b32-a0a7d7a7f900
kernel        /vmlinuz-2.6.35-30-generic-pae root=UUID=90dc8506-967b-4a33-b1e8-b3e46559fbb9 ro  single
initrd        /initrd.img-2.6.35-30-generic-pae
password --md5 $1$3SCpC0$MCX6qgaWkHwDvNqHup7jD.

title        Chainload into GRUB 2
root        ff03d393-b4f7-4e41-9b32-a0a7d7a7f900
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        ff03d393-b4f7-4e41-9b32-a0a7d7a7f900
kernel        /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST




Now the password protection is not working. What should I need to do for  preventing others from accessing grub or OS. I need to ask a password  when we press enter in grub menu. [SIZE=4]_**Please Help. **_[/SIZE]
[SIZE=3]
Thanks for anyone who helps[/SIZE]

---

### Post by ubudog on 2011-07-25
Try this:
[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

---

### Post by FrostBlue on 2012-02-05
I wish to password protect my GRUB loader on Kubuntu 11.10 which guide shud I follow ? I dont have a menu.lst in the /boot/grub/

grub --version

gives me 

grub (GNU GRUB 0.97)

---

### Post by FrostBlue on 2012-02-06
Right I read thru the whole thread and tried to edit grub.cfg which is what I have but the menuentry I tried with simply disappeared.

---

