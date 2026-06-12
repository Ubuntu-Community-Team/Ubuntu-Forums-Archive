---
title: "LUKS, dm-crypt and encrypted partition at boot"
date: 2010-02-22
forum: Security
---

### Post by MJBoa on 2010-02-22
Hi guys, I'm trying to have a LUKS encrypted partition mounted at startup and to have GDM ask for my key so it will decrypt. Now I followed
[http://gentoo-blog.de/ubuntu/encrypted-home-and-swap-partition-on-ubuntu-9-10-karmic/](http://gentoo-blog.de/ubuntu/encrypted-home-and-swap-partition-on-ubuntu-9-10-karmic/)
to the letter.
Except for now, I have it just mounted into /mnt/cryptohome so I'm not messing with my system.
My problem is the one everyone mentions in the comments, ubuntu isn't asking for the LUKS key in the X display, it's asking in the first terminal (Ctrl-Alt-F1). This will not do. I need it to ask to mount my drive before I'm even asked to login, so eventually I can encrypt my /home.
Any ideas or has anyone else successfully done this?

---

### Post by bodhi.zazen on 2010-02-23
Perform an encrypted installation using the alternate CD.

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

[http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

The tutorials are written for 8.04, but it is the same for 8.10, 9.04, and 9.10

---

### Post by MJBoa on 2010-02-24
Really? I can't and honestly shouldn't have to reinstall to get this working. I'm doing exactly what he does in the article anyway, making a dm-crypt partition and making a mapper. I'm just doing it post-install. I don't think those tutorials would work correctly on 9.10 either. If you look at the link I posted, the comments would indicate that worked too on 9.04, but at 9.10 it stopped. 
There seems to be very little documentation on the various steps the system goes through to mount an encrypted partition at boot, I've been searching my machine for some indication of what's happening. It seems to be a problem specifically with getting a prompt for the LUKS key through GDM rather than the terminal. 
It seems like no one really know what Ubuntu does when you set this up at install time. Everybody just says, "let ubuntu perform its sorcery, don't try to figure it out." Completely obfuscating the inner workings of the system seems to be Ubuntu's new MO, more and more with every release. It's really frustrating.

---

### Post by MJBoa on 2010-02-24
It seems unable to stop the boot process. What happens is, during the boot messages, where it says "SSH starting.... mysql starting...", it will say "cryptohome starting..." as the last item and then it will prompt for the login and password. I enter my username, it prompts for my password and then after hitting return, it unhides the password and prompts twice for the password, waits a few seconds and says it can't find a key, no matter what I type.
So it looks like ubuntu won't let cryptsetup stop the boot process so it can ask for the key.

So it looks kinda like
login: <username>
password: <password>Enter your luks passphrase: Enter your luks passphrase: <few seconds later>No luks key found for this passphrase.

Clearly, the prompt is messing with the login process.

Say I wanted to write an init-script, how would I pause the boot process and make a prompt?

---

### Post by bodhi.zazen on 2010-02-28
It works here.

Are you wanting LUKS or ecryptfs ? I ask because you are asking about /home

For Luks it is straight forward.

Step 1 -> Fill your partition, /dev/sda13 in this example, with random data.

Step 2 -> Set up the Crypt

```
cryptsetup -y --cipher aes-cbc-essiv:sha256 --key-size 256 luksFormat /dev/sda13
```Step 3 -> Open the crypt

```
cryptsetup luksOpen /dev/sda13 test
```Step 4 -> Format the crypt

```
mkfs.ext4 /dev/mapper/test 
```Step 5 -> Edit /etc/crypttab , add

```
test /dev/sda13 none luks,retry=1
```Step 6 -> Edit fstab

```
/dev/mapper/test /mnt/tmp ext4 defaults 0 2
```Step 7 -> Edit  /etc/initramfs-tools/modules, add these lines if needed:

```
aes-i586
dm-crypt
sha256
```Step 8 -> update your initrd

```
update-initramfs -k all -c
```That's if, reboot and you will be asked for a password when booting.

If you are having problems, post /etc/crypttab , /etc/fstab , and /etc/initramfs-tools/modules

---

### Post by MJBoa on 2010-02-28
I don't think changing what my ramdisk loads will matter since I've loaded the kernel by the time the mounting happens.

Relevant fstab lines:

```
#cryptohome
/dev/mapper/cryptohome  /home           ext4 noatime,nodiratime,errors=remount-ro 0 0
```

crypttab

```
#cryptohome     /dev/sde6       none            luks
```

I've also been having a similar problem with fsck. Where when it checks my disk, it doesn't actually pause the boot process, everything else keeps going and it creates a weird display problem where fsck is showing that progress bar but it also starts the login prompt and finishes booting.

This is a more general bug, I think. All of the people commenting on that blog post I linked also had this problem after switching to 9.10. The blog post, the one you should read because it's vital to my topic, explains it the exact same as you did. And this seemed to work up until 9.10.

For now, I've just written a script that asks for the keys, unencrypts and mounts all the drives I need. Less than ideal, but until I find out what's happening with the boot process in 9.10, it's my only solution.

---

### Post by bodhi.zazen on 2010-02-28
Your crypttab looks wrong as your line is commented out, with a # in the front of the line.

Should be :

```
cryptohome     /dev/sde6       none            luks
```

(no # in the front)

As I indicated, it is working for me in 9.10 as expected.

If you feel there is a bug, I advise you file a bug report.

---

### Post by MJBoa on 2010-02-28
It actually stops the boot process and asks for a key when you start up? Surprising. No one else seems to have this working. You really followed those exact lines?

It's commented out so I can actually boot my computer, I know what a hash mark does.

I guess I'll try adding those modules to /etc/modules. And if that doesn't work I'll add them to the initrd for no actual reason.

EDIT:
Neither of these things worked.

---

### Post by bodhi.zazen on 2010-02-28
Yes it is working as expected, the partition in encrypted, and Ubuntu 9.10 asks for a password as I boot.

Bt that I mean, Ubuntu asks for a password. I have not seen (nor have I looked) for a tutorial showing LUKS asking for a key file during boot.

I have only seen tutorials where the key file is more or less hard coded into crypttab

[http://ubuntuforums.org/showthread.php?t=837416](http://ubuntuforums.org/showthread.php?t=837416)

and people usually then keep the key on a USB drive.

the tutorial you linked to:

[http://gentoo-blog.de/ubuntu/encrypted-home-and-swap-partition-on-ubuntu-9-10-karmic/](http://gentoo-blog.de/ubuntu/encrypted-home-and-swap-partition-on-ubuntu-9-10-karmic/)

is not using keys.

Do you have a tutorial you are using that also uses keys and is behaving as you describe (asking for a key file during boot) ?

---

### Post by MJBoa on 2010-02-28
Sorry, I meant passphrase or password or whatever, no files. I have that exact set up from the article.

---

### Post by hawklion on 2010-03-16
Hi All,

Is there any solution for this problem. I am experiencing close behaviour. Boot process (graphical) asks LUKS password when my system loads. However, if I just wait for 5 seconds it continues to boot. Even when I'm able to enter password and press "enter" within 5 seconds no device appears in device-mapper.

---

### Post by bodhi.zazen on 2010-03-16
I can not reproduce your errors as it is working on my end as outlined in my posts.

I suggest you file a bug report perhaps someone else has a similar problem ?

---

### Post by hawklion on 2010-03-16
I forgot to mention that my system is amd64 . Do you have 64 or 32bit CPU?

> **bodhi.zazen said:**
> I can not reproduce your errors as it is working on my end as outlined in my posts.

I suggest you file a bug report perhaps someone else has a similar problem ?

---

### Post by bodhi.zazen on 2010-03-17
> **hawklion said:**
> I forgot to mention that my system is amd64 . Do you have 64 or 32bit CPU?

Both

---

### Post by hawklion on 2010-03-17
I found a couple of bug reports as well as similar posts on the forum. After performing update suggested by the bug report [#454898]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/454898") and adding bootwait to fstab I have exactly the same behaviour as described in the forum post [#8980208]("http://ubuntuforums.org/showthread.php?p=8980208#post8980208")

---

### Post by Nokia on 2010-03-17
> **hawklion said:**
> Hi All,

Is there any solution for this problem. I am experiencing close behaviour. Boot process (graphical) asks LUKS password when my system loads. However, if I just wait for 5 seconds it continues to boot. Even when I'm able to enter password and press "enter" within 5 seconds no device appears in device-mapper.
Same behaviour here too.

**@bodhi.zazen**

Could you please explain the need for the three kernel modules in Step #7 ? I mean, my setup works just fine when doing it all manually. It's just the boot thing that's strange. So I was wondering, if those three modules were needed will I still be able to use luksOpen without having errors ?

Thanks.

P.S. Did I...see you talking in `another` thread regarding a certain distro updates policy ?

---

### Post by Nokia on 2010-03-17
Seems solved, in a strange way:```
modprobe --list |grep -e dm-crypt -e sha256 -e aes-i586
kernel/arch/x86/crypto/aes-i586.ko
kernel/crypto/sha256_generic.ko
kernel/drivers/md/dm-crypt.ko

cat /etc/initramfs-tools/modules 
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
#aes-i586
#dm-crypt
#sha256

nokia@nokia-desktop:~$ cat /etc/fstab |grep mapper
/dev/mapper/luksHDD    /mnt    ext3    defaults,[COLOR=red]bootwait[/COLOR]    0    0

nokia@nokia-desktop:~$ cat /etc/crypttab 
# <target name>    <source device>        <key file>    <options>
#luks-learningHDD c6bfbb74-8f9a-49e4-a9ee-66a92ab7600e none luks
luksHDD    /dev/sdb    none    luks

```The good:
Boot stops asking for a passphrase.

The bad:
I entered the pass once, the prompt returned asking the pass again. (OK, I admited it could have been a typo [NOT])
I entered it twice, boot resumes, success.
Yet, the prompt returned again, asking for a pass. Eventually it got swept away by X/GDM. Now that's not good IMO.
Also, I'm guessing the three modules are not needed in Karmic, but YMMV.

---

### Post by bodhi.zazen on 2010-03-17
> **Nokia said:**
> Same behaviour here too.

**@bodhi.zazen**

Could you please explain the need for the three kernel modules in Step #7 ? I mean, my setup works just fine when doing it all manually. It's just the boot thing that's strange. So I was wondering, if those three modules were needed will I still be able to use luksOpen without having errors ?

To be honest, I am not sure, those kernel modules are listed as required, and I have not tried to reduce or eliminate them. 

Which is a ling winded way of saying I do not know, you may be correct.

> Thanks.

P.S. Did I...see you talking in `another` thread regarding a certain distro updates policy ?

Aye, and a poor job I was doing at it I might add =)

---

### Post by yoyocol on 2010-03-20
The solution does not work for me. I never get ask for a passphrase. I tried several times. I had encrypted partitions under SuSE and several Ubuntu versions. But with karmic it is just not working.

Really disappointing.

---

### Post by fargle on 2010-04-14
Just throwing this out there - if you're okay with the password on the volume being your login password, consider using pam-mount.   I've used it in the past nicely.  It just uses your login password to decrypt the volume and mount it with no fuss.

---

### Post by förbannat on 2010-05-03
I'm new to ubuntu (want to give 10.4 a try after a couple of years with OpenSuSe). And I have a problem as discussed here: 
During boot I am not prompted to enter my luks password for my /home partition.   

I recall that I had the same issue with Suse a few years ago, when they introduced a faster boot procedure: During boot several processes were started in parallel and they all display their output on the console. Any boot prompt was overwritten by the messages from the other processes (not sure if the text was even treated as attempts to enter a password). 

The solution was to manually switch off the parallel processing of tasks in the boot phase - making booting pretty slow. But when the luks prompt came the machine waited for my input! 
I think, ubuntu is doing the parallel booting, too ("Launched"???). Is it possible to disable this - just to give it a try?  
Unfortunately I do not remember, how I did this in Suse back then...

---

### Post by bodhi.zazen on 2010-05-03
> **förbannat said:**
> I'm new to ubuntu (want to give 10.4 a try after a couple of years with OpenSuSe). And I have a problem as discussed here: 
During boot I am not prompted to enter my luks password for my /home partition.   

I recall that I had the same issue with Suse a few years ago, when they introduced a faster boot procedure: During boot several processes were started in parallel and they all display their output on the console. Any boot prompt was overwritten by the messages from the other processes (not sure if the text was even treated as attempts to enter a password). 

The solution was to manually switch off the parallel processing of tasks in the boot phase - making booting pretty slow. But when the luks prompt came the machine waited for my input! 
I think, ubuntu is doing the parallel booting, too ("Launched"???). Is it possible to disable this - just to give it a try?  
Unfortunately I do not remember, how I did this in Suse back then...

Just wanted to ask - are you sure you are using LUKS ?

If you went with an encrypted home, the defaults, then you are using ecryptfs.

In that case you will NOT be asked for any password when you boot and your $HOME is automatically decrypted when you log in.

I see people are having problems, but I could not re-produce the problem at all, LUKS works for me on several boxes as outlined in my previous posts.

---

### Post by förbannat on 2010-05-04
Thanks for your reply.
> **bodhi.zazen said:**
> Just wanted to ask - are you sure you are using LUKS ? 
Pretty sure. 
My System:
sda1: WinXP
sda5: **/** for OpenSuSe
sda6: **/** for ubuntu 10.4 (all, incl. **/home**)
sda7: **/home** for OpenSuSe (encrypted, later to become home for ubuntu?)

Currently, with ubuntu I just want to mount sda7 under /mnt - for testing.

With OpenSuSe I prepared sda7 with something like:
[FONT=Courier New]...
# cryptsetup --verbose --verify-passphrase luksFormat /dev/sda7
# cryptsetup luksOpen /dev/sda7 cr_sda7
...[/FONT]

OpenSuSe's **/etc/crypttab** contains:
[FONT=Courier New]cr_sda7 /dev/disk/by-id/ata-[...blah...]-part7 none luks[/FONT]
with an according entry in** fstab**:
[FONT=Courier New]/dev/mapper/cr_sda7  /home ext3 noauto,commit=60 0 0[/FONT]

I'm quite sure, that it is LUKS, I'm using.

The above works fine with OpenSuSe, but no more with ubuntu. I also tried alternative entries in ubuntu's crypttab, e.g.
[FONT=Courier New]cr_sda7  /dev/sda7  none  luks[/FONT]
but this does not work either. 
Neither can I see a prompt when I boot with "splash=silent". Unfortunately, ubuntu's boot log (/var/log/boot.log) is not really informative (file size: <1kB), in OpenSuSe I can see almost anything that happened, incl. the password prompt (file size: 55kB). 
Here my Linux-knowledge ends... Next thing I want to try is bringing me back to my original question:
**Is it possible to disable the fast/parallel boot process ("Launched"?) in ubuntu?**

---

### Post by bodhi.zazen on 2010-05-04
> **förbannat said:**
> Thanks for your reply.

Pretty sure. 
My System:
sda1: WinXP
sda5: **/** for OpenSuSe
sda6: **/** for ubuntu 10.4 (all, incl. **/home**)
sda7: **/home** for OpenSuSe (encrypted, later to become home for ubuntu?)

Currently, with ubuntu I just want to mount sda7 under /mnt - for testing.

With OpenSuSe I prepared sda7 with something like:
[FONT=Courier New]...
# cryptsetup --verbose --verify-passphrase luksFormat /dev/sda7
# cryptsetup luksOpen /dev/sda7 cr_sda7
...[/FONT]

OpenSuSe's **/etc/crypttab** contains:
[FONT=Courier New]cr_sda7 /dev/disk/by-id/ata-[...blah...]-part7 none luks[/FONT]
with an according entry in** fstab**:
[FONT=Courier New]/dev/mapper/cr_sda7  /home ext3 noauto,commit=60 0 0[/FONT]

I'm quite sure, that it is LUKS, I'm using.

The above works fine with OpenSuSe, but no more with ubuntu. I also tried alternative entries in ubuntu's crypttab, e.g.
[FONT=Courier New]cr_sda7  /dev/sda7  none  luks[/FONT]
but this does not work either. 
Neither can I see a prompt when I boot with "splash=silent". Unfortunately, ubuntu's boot log (/var/log/boot.log) is not really informative (file size: <1kB), in OpenSuSe I can see almost anything that happened, incl. the password prompt (file size: 55kB). 
Here my Linux-knowledge ends... Next thing I want to try is bringing me back to my original question:
**Is it possible to disable the fast/parallel boot process ("Launched"?) in ubuntu?**

So you are trying to mount your OLD encrypted /home partition ?

Disabling the boot scripts in Ubuntu is very different then SUSE. Ubuntu uses Upstart and most of the init scripts are fairly unique.

Are you booting Ubuntu without a splash screen ?

At any rate, I have never seen the behavior you describe, where the boot process does not stop and wait for a password, with Ubuntu and LUKS.

Before you go doing that, what exactly did you do to prep Ubuntu ? Did you install all the required packages and update your initrd as described in my previous posts ?

If so please describe exactly what you did.

---

### Post by förbannat on 2010-05-04
It works now! And shame on me. I WAS SO STUPID!: 

What went wrong: The mount point you want to mount your encrypted drive on MUST EXIST. It is NOT created during the mount process. If the mount point does not exist, there is no error message during the attempt to mount, luks does not even ask for the password... 

My own explanation/excuse is, that I changed the mount point during my setup, so I had an unused folder somewhere but the defined folder in fstab did not exist...

> **bodhi.zazen said:**
> So you are trying to mount your OLD encrypted /home partition ?
This was the cause of my problem, I copied the command from my other crypttab to ubuntu and changed the mount point, but I did it wrong...

> **bodhi.zazen said:**
>  Are you booting Ubuntu without a splash screen ?
I did both. Now that I have my problem solved, I can tell that I still had smaller problems with both methods:

The text version asks for a passphrase, but with every digit entered, a complete new line is added on the display, saying something like "plase enter luks passphrase (/dev/sda7):" Entering one letter always results in a new line with the same text. No big deal, just a minor security issue and not really nice...

The splash screen was more problematic: Somehow the bios(?) did not get/tell the correct display resolution (Dell Latitude E6400 notebook with 1400x900). The splash screen was far too big, having a large "ubuntu" text in the middle of the display (33% of total width and height), so I could not see the password prompt on the bottom of the page. But I did not  know how it has to look like - I never used ubuntu before... 
After hours I found out what was wrong - and a boot parameter (vga=0x361, stands for 1280x800...), that resized the splash screen in a way that I now can see the password-prompt at the bottom of the page.  

> **bodhi.zazen said:**
> At any rate, I have never seen the behavior you describe, where the boot process does not stop and wait for a password, with Ubuntu and LUKS.
Yeah, you probably never used the wrong mount point...

I am very sorry for taking so much of your time. But you forcing me to go through the whole thing one more time (as you described earlier) helped me discovering my mistake. So a big "Thank You!" (And I have a slight feeling that my "solution" might also be applicable to others in this post...)
Kind regards, 
  Chris

---

### Post by bodhi.zazen on 2010-05-04
AWESOME :guitar:

Glad to learn you got it sorted out.

---

### Post by kalamot on 2010-05-07
Hi,
I have successfully  managed to encrypt my partitions with LUKS and dm-crypt on Ubuntu 8.10 and now I would like to do the same with 10.04 Unfortunately  previously i had problems when i tried to do that with Ubuntu 9.10 ( [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/386976](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/386976) )

In my case i am storing passwords in a keyfile on my external usbstick and i want to keep it this way. Entering passwords every time i reboot is not an option for me.

Is there a tutorial on how to do it with the latest Ubuntu ?
Is there anyone who managed to encrypted their HDD, boot with keyfiles on a USBstick with 10.04 ?

Any help would be appreciated.

---

