---
title: "quantal refuses to use latest kernel"
date: 2013-05-30
forum: Ubuntu Studio
---

### Post by youWho on 2013-05-30
Hi all,

I'm using ubuntu studio quantal 64 bit. I've recently realized that for some time now the only kernel that's being used is Kernel Linux 3.5.0-27-lowlatency even though Software Updater has been installing updates on a regular basis; the latest that's installed is 3.5.0-31-lowlatency

```
dpkg --list | grep linux-image
ii  linux-image-3.5.0-26-generic              3.5.0-26.42                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-26-lowlatency           3.5.0-26.28                               amd64        Linux kernel image for version 3.5.0 on x86/x86_64
ii  linux-image-3.5.0-27-generic              3.5.0-27.46                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-27-lowlatency           3.5.0-27.30                               amd64        Linux kernel image for version 3.5.0 on x86/x86_64
ii  linux-image-3.5.0-28-generic              3.5.0-28.48                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-28-lowlatency           3.5.0-28.32                               amd64        Linux kernel image for version 3.5.0 on x86/x86_64
ii  linux-image-3.5.0-30-generic              3.5.0-30.51                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-31-generic              3.5.0-31.52                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-31-lowlatency           3.5.0-31.34                               amd64        Linux kernel image for version 3.5.0 on x86/x86_64
ii  linux-image-extra-3.5.0-26-generic        3.5.0-26.42                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-27-generic        3.5.0-27.46                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-28-generic        3.5.0-28.48                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-30-generic        3.5.0-30.51                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-31-generic        3.5.0-31.52                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic                       3.5.0.31.47                               amd64        Generic Linux kernel image
ii  linux-image-lowlatency                    3.5.0.31.29                               amd64        lowlatency Linux kernel image

```
I don't understand this. If it should be using only 3.5.0-27 then why would Software Updater keep installing newer versions? Or could somebody please explain what's going on here?? Seems to me it should be booting into the latest version.
I should add that I had tried to change the grub2 startup menu about a week and a half ago by editing /etc/default/grub; I had changed the line that reads:
```
GRUB_DEFAULT=0
```
to be:
```
GRUB_DEFAULT=saved
```
and then had run a command that I have now forgotten(!) (sorry) which was intended to establish what was "saved", as I understood it (incidentally there had been no apparent effect on which version of ubuntu studio the computer would use; I have, for complicated reasons that I think are not relevant here, 2 / partitions, one with quantal and the other with precise). Those ideas were based on searches of ubuntuforums. But I've changed that back to be as it was before ("GRUB_DEFAULT=0") and still ubuntu studio keeps using Kernel Linux 3.5.0-27-lowlatency (quantal).

Thanks for any help!!

---

### Post by jejeman on 2013-05-30
Give
```
uname -a
```
GRUB default should be "0".
Give
```
cat /boot/grub/grub.cfg | grep Ubuntu
```

---

### Post by youWho on 2013-05-30
Thanks, and:

```
uname -a
Linux sa-qua 3.5.0-27-lowlatency #30-Ubuntu SMP PREEMPT Wed Apr 3 18:26:33 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

and

```
cat /boot/grub/grub.cfg | grep Ubuntu
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-31-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-31-lowlatency-advanced-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-31-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-31-lowlatency-recovery-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-31-generic-advanced-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-31-generic-recovery-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-30-generic-advanced-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-30-generic-recovery-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-28-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-28-lowlatency-advanced-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-28-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-28-lowlatency-recovery-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-28-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-28-generic-advanced-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-28-generic-recovery-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-27-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-27-lowlatency-advanced-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-27-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-27-lowlatency-recovery-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-27-generic-advanced-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-27-generic-recovery-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-26-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-26-lowlatency-advanced-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-26-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-26-lowlatency-recovery-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-26-generic-advanced-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
    menuentry 'Ubuntu, with Linux 3.5.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-26-generic-recovery-75dd094a-4f6f-4ee1-91f1-6bd370ee5ea4' {
menuentry 'Ubuntu 12.04 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-ff4bc27f-f62f-4f5e-8ff9-ce8a454f49d5' {
submenu 'Advanced options for Ubuntu 12.04 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-ff4bc27f-f62f-4f5e-8ff9-ce8a454f49d5' {
    menuentry 'Ubuntu, with Linux 3.2.0-23-lowlatency (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-lowlatency--ff4bc27f-f62f-4f5e-8ff9-ce8a454f49d5' {
    menuentry 'Ubuntu, with Linux 3.2.0-23-lowlatency (recovery mode) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-lowlatency-root=UUID=ff4bc27f-f62f-4f5e-8ff9-ce8a454f49d5 ro recovery nomodeset-ff4bc27f-f62f-4f5e-8ff9-ce8a454f49d5' {

```

---

### Post by youWho on 2013-05-31
anybody???

---

### Post by jejeman on 2013-05-31
If you manualy choose latest kernel will it load?

---

### Post by youWho on 2013-06-03
Sorry for the delay. To be honest I don't know how to manually select a specific kernel anymore since they show up in the grub2 menu (during boot) as one item that's intended to represent the latest version, as I understand it. But let me try restarting and double check... (I'll be back in a moment)

---

### Post by youWho on 2013-06-03
...No I spoke too soon. Yes it's possible to manually select a kernel version, and yes it does boot into the selected version. The problem seems to be that the highest version that is shown in the grub2 menu is 3.5.0-27-lowlatency, the one that it automatically boots into. When I tried manually selecting another I had to try selecting a lower version number---I don't know how to make it reveal higher versions if they are indeed being recognized by grub. Thanks again, and you have any further thought please let me know.

(Sorry for the duplicate; I don't know how to delete it now.)

---

### Post by jejeman on 2013-06-03
Purge all kernels exept  3.5.0-31 and 3.5.0-30. Then, it has to boot one of them. ;)

---

### Post by youWho on 2013-06-03
Are you serious??! I worry that it might just not boot at all! Which would be worse! But do you seriously think that's not a possible outcome?? If it didn't boot at all then is there a way to install a kernel without being able to boot??

---

### Post by youWho on 2013-06-03
I'm waiting for a replacement backup drive (for the one that was defective from the start(!!)) and my idea was that when that arrives (in maybe a week or so) I'd try upgrading to Ringtail and see if that solved it.

Thanks for your help by the way!

---

### Post by jejeman on 2013-06-03
You will boot, don't worry. Just don't purge all kernels.
Before purging, give
```
cat /etc/default/grub
```

---

### Post by youWho on 2013-06-03
"You will boot, don't worry."
Amazing. But to be honest I'd prefer to try this after I get this replacement drive because I was planning to explore the possibilities for backing up the root partition, taking a snapshot somehow, I don't know yet how that works. Anyway after that I'd be less inclined to worry about not being able to boot at all. It's only that the machine is used for stuff that I have to do, so not being able to boot at all would be a major issue. But I'll try it; should be fun ;-) and when I do I'll post back.

Thanks again, and:

```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by howefield on 2013-06-03
Just a thought, have you tried updating grub on precise to find the installed kernels from quantal.?

```
sudo update-grub
```

---

### Post by jejeman on 2013-06-03
GRUB configuration is okay.

How I know that you will boot?
First, you have menu entries for all kernels.
Second, your manual selection & booting works.

But, It is okay. If you are not comfortable, then don't purge.

---

### Post by youWho on 2013-06-06
amazing!! howefield your idea worked!

I rebooted into precise and just ran
```
sudo update-grub
```
then rebooted into quantal and 

```
uname -r
3.5.0-31-lowlatency
```

For good measure I ran "update-grub" in quantal too.

Thanks really a lot to both jejeman and howefield for all your help. Apparently the circumstances were kind of unusual. The story is essentially this, I think:

I'm obliged to use a USB dongle for internet access and for some time this particular dongle (Huawei E303) had refused to connect at all, or rather it would be convinced that it was connectiing but the OS disagreed---I never quite figured it out. But when I installed Precise fresh from the installer disc all of a sudden the dongle was working. Then, I happened to boot the computer one day with the dongle already plugged in, and from that moment on it wouldn't work anymore, even after I tried every variation on restarting. Since I had only recently installed Precise I decided that probably the least labor intensive way to get the dongle working again would be to just reinstall Precise (trying to debug that, constantly booting into WIndowz to search the interwebs, rebooting to try something, etc. was hella slow). So I reiinstalled Precise, followed by upgrading it to Quantal. Then maybe a month or so ago again the dongle went nuts, and to try to restore it I had the idea to install Precise on the free partition I happen to have, which worked (actually I think it wasn't necessary; Quantal also can restore the dongle, and anyway I think it turned out to be the telecom provider's fault in that case, but I hadn't realized that at the time). But the gist of all this is that through this unusual turn of events I had an install of Quantal on one partition, and then a *newer* install of Precise on another, and I'm guessing that somehow this is where things got mangled. This is my own theory; you might know better (I wouldn't be surprised), but it's perhaps useful info if anybody else runs into this strange problem.

I'll mark this as solved finally!! Thanks again!

---

### Post by jejeman on 2013-06-06
Oh, you got two Ubuntu installations that share one GRUB - I didn't know that. Now I know why the grub.cfg is okay, but "give" strange results. ;)
Yes, you need to update GRUB which is in MBR, obviosly it is GRUB from precise.


Hahaha. Yes, if you were to purge kernels as I said, you would be bootles. Because, the GRUB which is in MBR would not be updated... :rolleyes:

---

### Post by youWho on 2013-06-06
Hmm, I'm not quite understanding how this works. But I'd like to ask about this if I may, because what I'd like to do is to eliminate that partition that at the moment has the precise install on it. I didn't do it yet because I'm waiting for the replacement backup drive (I'd like to back everything up before modifying partitions), but then I plan to divide the space on that partition between the quantal partition and home.

I'm not sure what the implications of this are now. If I delete the precise partition then could I somehow get the GRUB that's in MBR to be one installed by quantal? Or maybe I should ask it like this: is there something I should do now in order to update the GRUB that's in the MBR (and tie it to quantal)??

Thanks again.

---

### Post by jejeman on 2013-06-06
Yes, you can install GRUB from quantal in MBR.
Boot quantal. Install GRUB in MBR with command
```
sudo grub-install /dev/sdX
```
update GRUB
```
sudo update-grub
```

**note
sdX - you should enter the name of you hardisk sda, sdb... etc.

---

### Post by youWho on 2013-06-07
Thanks, I'll do that.

...

Just now did it and seems to be all good; just booted into quantal, and it's using the latest version number kernel and the grub2 menu in the boot was the newer one too, which I prefer.

Thanks again.

---

