---
title: "kernel panic - can't boot"
date: 2023-10-21
forum: Server Platforms
---

### Post by shinku443 on 2023-10-21
[IMG]https://lh3.googleusercontent.com/pw/ADCreHdH47DB0XFD36UaPszyfTDbHK_sgTsDjbSEPHE1qssfu7YcDPXTxIWkbS0qihbvIrd2zq9eLNKX3ZJB5l8mLL5v2bj-ml1bKnTpeHVvcCxf4riARjrGxP91onS_S8xEx5OGXwWOqAxBr-bu1m9epMw59eKDoGpN8Lf2F-vTloN1jU9zPwUz8U3d80AY3u7f7rRUuwAOyLdmS31xePjbpwxQrMvGW23HcDwsoRRZkZC6rthAGuDKOAQXtyuycptLFQ4lsWrxBwq_rG3Jgp6SXZrPupSlt_OXTMPcDc6sO6TFWLCbT7QgA3G3KUVtc1932XQws52KaQ9fK2OVYe676zWrPB5hHrY40IWdLHLxcRIBmAhHNAIOriqyyu1Hb5gqYg6HjbkXvYLZITJ4jMps9gE8Z3CPQlhnU91hbRM0zARSKN_MithnlNy_DyYAjDH4lZSAltQ-TlTXVPL3x8bNP-VA3EgiI8-Lnv_bq7g-vrnFOBk5SmI2c0_DmMVOEh5tVeP0XIizeHh2Qev01JubmabtpkV4z8K6ybt-bJOH9Ky43YTq5irDhJ_08TkJlo9AGG1Xq_hhkVm9Y0DJIEcin4EfIDIQm_A8kjsR4FdTNz5l2zeh7dyFmb0h8Qh2WF5v1kUQ1tTt7vmok29nEPpSy_EbKOHQd_BhsnYQWpzG9TwOUkMZTCq1juJdTZyl6dV9zgRieY2ylpi7PUvD2ZSpRmHgsLXyFbn2fPx26d1ROZT1MT6-mHsZOnO-X4bJDjVMxDk_m3uQBYpcvEB_TLapa36Z0ep8jICCL9Fd6QNOCt0Gh8SYdiooRaPaXSQ-6SXDku9zBxm8uW_zGSohC94Piu_IK4V_axHbydCED5f1diF6uysL5lnUPFPfkakMZNszoIq5SfRCcCNticgNlu6d-UJE1jAjcGZNHQ2oeHgjm85jpQoheEQ8y1e9ScL1=w1753-h1315-s-no-gm?authuser=0[/IMG]


My power went out last night and my NUC which has ubuntu server on it (kernel: 5.4.0-165-generic), now won't boot. I've tried going into the recovery mode and that fails as well
[error : failure reading sector 0x1a4390 from `hd0']

. I am able to boot from an Ubuntu live usb but not sure how to fix the kernel or whatever is causing it to not mount properly. I am very new to anything kernel related. Would appreciate any guidance on the matter thanks!

---

### Post by Bashing-om on 2023-10-21
Hello shinku443 - Welcome to the Forums :D

Power cut leaves the installed file system in a corrupted state.
First thing to try - that often corrects - is a file system/check-repair tool; fsck.

From the liveUSB run terminal commands:
```

sudo fdisk -lu #determine the name of the target
sudo fsck /dev/sda2

```
where in fdisk we look for * under the boot heading to know which partition contains the boot code. Here in this fsck example is the 1st drive (sda) and the 2nd (2) partition. *Adjust* the command syntax as required for the actual target.

[INDENT]hey, it could happen
[/INDENT]

---

### Post by shinku443 on 2023-10-21
hi thanks for the tip, so I tried that and then rebooted and still same thing. my /dev/sda3 is  Linux LVM, and also theres /dev/mapper/ubuntu--vg-ubuntu--lv which i tried running the scan on. it said that it found an error and fixed it, and all subsequent runs of fsck doesn't throw anything.

---

### Post by Bashing-om on 2023-10-21
shinku443; Yukkie Ouch

Sorry but LVM is out of my knowledge base.
Await others here to chime in who do have that skill set.

-a knowitall I am not-

---

### Post by MAFoElffen on 2023-10-21
I am not a know it all, but I do know some 'stuff"... LOL

To check LVM volumes are done with the following steps, booted from a recent Ubuntu Installer LiveUSB. 

First we can see our drive layout with lsblk:
```

sudo su   # Because most of the command will be as root 
lsblk -e7 -o name,label,size,fstype,model
## Example Output:
#NAME                 MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
#sda                    8:0    0    20G  0 disk  
#&#9492;&#9472;sda1                 8:1    0    20G  0 part  
#  &#9492;&#9472;ubuntu--vg-root 253:0    0    19G  0 lvm   / 
#sr0                   11:0    1  1024M  0 rom   

```
As we can see in that example, the LVM volume is named ubuntu--vg-root, but we cannot run fsck on this name as it will not find it. We need to get the whole name of the volume. To do this we are going to run the lvm lvscan command to get closer to having the whole addressable LV name so we can run fsck on it.

You will still be root...
```

lvscan
## Example output
#  inactive          '/dev/ubuntu-vg/root' [<29.04 GiB] inherit
#  inactive          '/dev/ubuntu-vg/swap_1' [2.00 GiB] inherit

```
As we can see our whole name is /dev/ubuntu-vg/root... We will use that whole name to activate the volume so we can address it as a volume, so we be able to run fsck on that, by using that whole name. LV /dev/ubuntu-vg/root is not ACTIVE at this point of time (shown in that 1st column of that output), and we need to make it active so that we can run the check on it. We do that by using lvchange.
```

lvchange -ay /dev/ubuntu-vg/root
lvscan          # Recheck the output to ensure it is active...
## Exampe output:
#  ACTIVE            '/dev/ubuntu-vg/root' [<29.04 GiB] inherit
#  inactive          '/dev/ubuntu-vg/swap_1' [2.00 GiB] inherit

```
Now we can run the fsck on the root LVM LV volume.
```

fsck /dev/ubuntu-vg/root

```
Post at any time if you have any errors that come up, or have other questions. Stop at that point. Do not just get an error and continue on. That would not make sense right?

---

### Post by MAFoElffen on 2023-10-21
It will not let me edit my last post to fix that last code tag... But you get the idea right?

---

### Post by shinku443 on 2023-10-21
ok so mine was
```

                                                  #type
#sda                                                                ST_HardddriveModel
### sda1                                       #vfat
### sda2                                       #ext4
### sda3                                       #LVM2_member
##### ubuntu--vg-ubuntu--lv          #ext4
#sdb # FLASH DISK
#### sdb1                                     #vfat

```




my /dev/ubuntu-vg/ubuntu-lv was already active, running fsck on that said clean - no error. still can't boot ubuntu.

---

### Post by MAFoElffen on 2023-10-21
Now do 
```

sudo fsck /dev/sda2

```
That looks like it might be a separate boot partition which would contain the vmlinux and intramfs images... If the filesystem there is corrupted, that also would cause kernel panic on boot...

---

### Post by shinku443 on 2023-10-21
Also says clean

---

### Post by MAFoElffen on 2023-10-22
How does it do if at the Grub2 menu > Advanced options... If you boot from an earlier kernel?

---

### Post by shinku443 on 2023-10-22
same thing it wont boot from any of the 4 entries

---

### Post by MAFoElffen on 2023-10-22
Do you know how to chroot into the installed system from an Ubuntu Desktop Installer LiveUSB? 

Summarized plan: Mount the installed system volumes > Backup everything that is there!!! > chroot into the installed system > reinstall linux-image-generic > update-intramfs image > update-grub...  

If you need help, I will help with instructions for that.

---

### Post by shinku443 on 2023-10-22
> **MAFoElffen said:**
> Do you know how to chroot into the installed system from an Ubuntu Desktop Installer LiveUSB? 

Summarized plan: Mount the installed system volumes > Backup everything that is there!!! > chroot into the installed system > reinstall linux-image-generic > update-intramfs image > update-grub...  

If you need help, I will help with instructions for that.


i do not,

i have a windows desktop, is it possible to just throw the drive in my windows desktop and grab everything or are the file systems not compatible?

---

### Post by MAFoElffen on 2023-10-22
Is your Windows OS Professional Edition and do you have WSL2 installed and working on it? If so, then: [https://devblogs.microsoft.com/commandline/access-linux-filesystems-in-windows-and-wsl-2/](https://devblogs.microsoft.com/commandline/access-linux-filesystems-in-windows-and-wsl-2/)

If not, then it won't understand the ext4 filesystem...

If so, then copy the /home, /root (user), /etc folders... 

From there you have two choices:
1) Try to chroot in and repair the old system

You said your existing layout was
```

                                       #type
#sda                                                        ST_HardddriveModel
### sda1                               #vfat
### sda2                               #ext4
### sda3                               #LVM2_member
##### ubuntu--vg-ubuntu--lv            #ext4

```

```

sudo su
lvscan
# Adjust the following LVM device names based on your output
lvchange -ay /dev/ubuntu-vg/root
lvscan
ls /dev/mapper
# adjust the following based on what it says in the output
mount /dev/ubuntu-vg/root /mnt
cd /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env bash --login
mount -a
apt update
apt install --reinstall linux-image-generic
# After this, you may want to list the boot directory and reinstall any kernels you have there...
# This is recommended. That timing of that, is to do it before updating the initramfs images...
apt install --reinstall grub-efi-amd64 grub-efi-amd64-signed linux-image-generic shim-signed
update-initramfs -c -k all
update-grub
grub-install --target=x86_64-efi --efi-directory=/boot/efi  --bootloader-id=ubuntu --recheck --no-floppy
exit
umount /mnt
exit 
sudo reboot

```
No guaranty's, but a good faith effort.

2) Install fresh and migrate what you had to it.

Install new, reinstall the service it had installed... Then restore the user data of the users and root user, then restore the modified configs. That is what you usually do for a migration, and would take about 30-40 minutes to do the migration + any data restore time.

To make migrations faster, I separate out my home and data drives/partitions so they are not affected in a migration and makes that process so much faster. If you choose to do that, when you install fresh, that is the time to change the layout to make things easier on yourself in the long run. Then you just restore your data to that new layout.

---

### Post by shinku443 on 2023-10-22
yep, so probably easier to do it that way then, was hoping to avoid wiping it but i guess ill just backup personal files, and then wipe the drive and reinstall latest ubuntu server. and then move files back on. thanks!

---

### Post by shinku443 on 2023-10-23
So I'm trying to follow the steps to mount the drive on my windows system using wsl. it's partitioned as so
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAABA8AAABhCAYAAAC58YjiAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAABhaVRYdFNuaXBNZXRhZGF0YQAAAAAAeyJjbGlwUG9pbnRzIjpbeyJ4IjowLCJ5IjowfSx7IngiOjEwMzksInkiOjB9LHsieCI6MTAzOSwieSI6OTd9LHsieCI6MCwieSI6OTd9XX3HTsJTAAAlhElEQVR4Xu2dbWwcR3rnn2E 7If9YHmBYHGALwgoUoZp5osWoWBSn86RvJIMmAus9JWjg0yKvluT3rOwkFc5YHNa8RI5p6Fz0StwpoALgnByMHNYkZHkjxYNyRER4GjuiUPzcjknWa8dk9rLy17uVn31dFfNPF1TXT2vZA/5/wGFmap/d0/PVP376a6urskdPHgwOHXqFN2/f58uX75Mjx8/JpANnnrqqXJ9zM3N0fDwcPgeAAAAAAAAAABoJ/Y1aJd BQAAAAAAAAAAAHCCzgMAAAAAAAAAAAB4wWMLGcZ bGFkZCR8DwDYem7evBm wocA7GzgdQAAALsRjn8c 2R/gP3YAjoPMoyr8yCX 0GYBwBsLTMzvxq sg 7un5AQRBmAQA7DOl1xFwAAAC7hXff/VXK5/2dB3hsAQAAAAAAAAAAAF7QeQAAAAAAAAAAAAAvTXUe/PSLzTB98eXj8PUnP/2S/vonX9Cnf/M5/eVffUZ/8b/ htb/51/R2v/4lFY/ Uu9FgAAAAAAAAAAADoJjDwAAAAAAAAAAACAl4Y7D3ikQb08WvsL/Y65S5N79tAeKx2 /AmV5yG7O1kuc7J hQ7zeocv07ouSuPu5B56es k nQAAAAAAAAAAADUQsOdBz/7h3 kz774W/rJ51/QX3/2efj607/9kr7Y2KQvNx/T5s/ N/3s7/6e/k4t9w8//zn9/J/ if7P//1/em3BwAV6qNbZ3NykpakB uitb9DTk3e02ErW6crhPXR8hiqdEwAAAAAAAAAAAEil4c6Dr3zlK3TtP16i3/sPv02///HU391m/SD859j85977v0ve9 h/7N6 M0 a9G6cSfv0z/euxf0muv5vWayXSPX6ULB3JEM2/TFR5KcKgQdirceW1vtEAT3J3cT2f7pmhqQBcAAAAAAAAAAACgJto658HnY5/TsdPH6LPTn mSNLrppeEBytEDesRPKsQeW7Aec5isfvCAH0kINcdjDIcKm7RZeEnnAAAAAAAAAAAAUCtt7Tz45Wu/TB9c/YC fvXruqR2Vtbil/93J4/TDA3Q1FL0iMNm4ZBWNHcnw0cSKF kjduvUXdUCgAAAAAAAAAAgCZpqvPge7/5W/Rvz/82nf dS/Q7hd nwuUb9Ps3Zuj6zB/Qf/rPf0Q3//CP6Y//xQL9QXGO/vC//Ff66le/qtdMp68nfvm/91l 3uABnd3vmkBxjk5zz8HAFC0VDlEup4sBAAAAAAAAAADQNA13Hvzzr3 t7rT3V/6ZXjuJdbo994ACytMxa2BB9/gd2ixG8yY8eOsbtOfwlcqjCQ9UCvsW3qPbtf7tAgAAAAAAAAAAAGqirY8t1AtPavjW/YAGLnyHrL6DiHACxSKdtIcWDAzT1atTNBCOTJikOwH TwEAAAAAAAAAAGgVuYMHDwanTp2i /fv0 XLl nx48daajc8ASLPYyAZoAsPb9Nre3XnAE YeHyGBi48pDOr34jmNAjhuQ/u0DhdocP7z9KDgQu0dOc1oiuHaf9ZHoaQp JmwdEBwX/XuJ/OPkjSs8VTTz1Vro 5ubnwFQAAAAAAAAAAaDUjIyOx/gC Bh0eHta5be08AGnYnQd2ZQIAthb4EIDdgemwf aZZ8JXAAAAYDfw4osvejsPMvXYAgAAAAAAAAAAALIHRh5kmLSRB bOCACgPbg8Bx8CsPNI8rUcefDpp5/qdwAAAMDOQca6tJEHxJ0HMzMzwfj4eMBsbm4iZSTJ uA6knlZBgBoHy7PucoAAJ2N7WtO77//fjn5vJ52HIAO3Qd06D6gQ/fRCl3GOsaOhzKPzoMMJ1kfpuKlntYYAADN4/KcqwwA0NnYvuYkT6iSvJ52DIAO3Qd06D6gQ/fRCp2TjHWMHQ9lHp0HGU6yPkzlS92UAQDah8tzrjIAQGdj 5qTPKFqxOtp60CH7gM6dB/QofuoVedXGesYOx7KfAOdB8XgZC4XEFE55Wc3HMulpKWpYIAGgqmHDay7S5KsD1PBUjdlAID24fKcqwwA0NnYvuYkT6jq9Xra8tCh 4AO3Qd06D7q0fm9jHWMHQ9lvsHOA3XRv6TzS1PBgVw KFYth9RskvVhKlnqsuIBAO3B5TlXGQCgs7F9zUmeUEmvp/keOnQf0KH7gA7dR6t1zstYx9jxUOab7zyoyiO1Ksn6MBUtdbvyAQCtx U5VxkAoLOxfc1JnlAZrzfr bT1oUP3AR26D jQfbh0LpOxjrHjocw333lQPBnk8sWyXjyZC3LmkQZVvrHB5UvB1ID9mEMxyMceW7CWKert7 Ik68NUttRdDQAA0FpcnnOVAQA6G9vXnOQJlSlrhrT1oUP3AR26D jQfSTpXC5jHWPHQ5lvwZwH WB2wzVvgegcKJ4MOxISdd1xMDC1FGzEltndSdaHqXCpJzUCAEDrcHnOVQYA6GxsX3OSJ1TNej1tfejQfUCH7gM6dB8 nTUZ6xg7Hsp8i Y8sEYi5EzHwkBwgTsHwskR7c4B0XkQ6pg3wU6yPkylS93XEAAArcHlOVcZAKCzsX3NSZ5QNeP1tHWhQ/cBHboP6NB91KLLWMfY8VDmWzDnwVIwdSAXPWZgJk8MRyLwaAIzsiBadmlqIHykoeqxBXQeOJOsD1PxUk9rDACA5nF5zlUGAOhsbF9zkidUjXo9bT3o0H1Ah 4DOnQfteicZKxj7Hgo860deVDMB7mBqeAhz3MQdgjEOw84LU0dCA5MPQy3g8cW/EnWh6l8qZsyAED7cHnOVQYA6GxsX3OSJ1SNeD1tHejQfUCH7gM6dB 16vwqYx1jx0OZb8GcB/rRhFCLRiGE5QP5IG9GHvCcB XlzRwJsvMg2m6 vAwmTOQk68NUsNRNGQCgfbg85yoDAHQ2tq85yROqer2etjx06D6gQ/cBHbqPenR L2MdY8dDmW g8wBpq5KsD1PJUpcVDwBoDy7PucoAAJ2N7WtO8oRKej3N99Ch 4AO3Qd06D5arXNexjrGjocyj86DDCdZH6aipW5XPgCg9bg85yoDAHQ2tq85yRMq4/VmPZ 2PnToPqBD9wEdug XzmUy1jF2PJR5dB5kOMn6MJUtdVcDAAC0FpfnXGUAgM7G9jUneUJlypohbX3o0H1Ah 4DOnQfSTqXy1jH2PFQ5tF5kOEk68NUuNSTGgEAoHW4POcqAwB0NravOckTqma9nrY dOg oEP3AR26D5/Omox1jB0PZR6dBxlOsj5MpUvd1xAAAK3B5TlXGQCgs7F9zUmeUDXj9bR1oUP3AR26D jQfdSiy1jH2PFQ5tF5kOEk68NUvNTTGgMAoHlcnnOVAQA6G9vXnOQJ1W71etr3hg7dB3ToPqBvv85JxjrGjocy31DnQfFk5a8aBy48DDZMeZ6CnCmfWtLLi79vVCk/u1FeXqalqYHyMvx3jsWqsooW/dWjtY2lqWBALjcwFSyFmv3XktE VK2fwSTrw1S 1E0ZAKB9uDznKgMAdDa2rznJEyp4vZq03wQ6dB/QofuAvjU6v8pYx9jxUObr7zxQF lTRZPnC/OBYOqhuhi3yvOkypei90VTrpY5kMsHRcfFP3c85NVyro4Fk7gzgTslqpYJOw7M50WpmI86IMr7aDSzD3q5LCdZH6aCpW7KAADtw U5VxkAoLOxfc1JnlDB63HSfg/o0H1Ah 4D tbp/F7GOsaOhzLf5GMLPKrgQNR5YJcPxC/mo8QX8kmdB67lZeIOCddFfzSygTse4uUmWZ0HVfnsJlkfppKlLiveUCoMBrmcGWUxGszr8pD50bDs1pMnuoCLKqNFBgslXSqZD8Z45MZobEtlos8bDKJV54NRvS2TeLXKpwHQebg85yqrQvvN7RxFqGvvXVrVhQpVbjzs9qSmVAgG9fphGrwUREtrzwpt9NYT BCAFGxfc5InVNLr5j3HUOMz6eOk2Jq0fAx5bLCOAZX1B4NLqwmurjo2FMrHBleMboTE454GOnQf0KH7gL61OudlrGPseCjzXSp4NMEntPrgOerp1tkyn9CjB33V5Xdv0czIMfoNUiE1xjqtrTygs/v30J49e jw5U90uUCtuzL1Oh3S2TLrt2nuwQgdqxISCPfhDI1X7fPOoLSySK/eekKq3lW6RkfC0jWaHspRbk5dyqhc ddfm6bV4YDU6Ydadp76J0doek1rMV6gweXzDm2BLk4uqnV1NmSQCqv680sFWj46RgvxBQDY4Si/Hewq 83NAo0dJVLn7aH3fu27ee2vqPzWL9hDHk8q7x7cN0snSrx lOZ/7b9TScvsWenDj18 DR8C0CJu3rxJIyMj5RgaeVD4OCm2Ji0fI35skMeAhdNddL6vpNe/R5O99rmUQn3GUK91bOhfEccGFaONZmK0Vmql/P0TgA4dOvQkoGdbr4lmRh7wowYDU5U5D8rlJ3NizgN 3OBA1MudLwYbG/Flq5NrZEDSSAaV DGEA2Z g jRhqi33yzP25N34RLmTMhgkvVheomkbvccMfOjPAog6R4j33UYDebFyIMKpaAwaEYQSPgu5mAwqrZbdReU746MjqptypEH6n35boidB6DzcHnOVVaN9pvOxZgfi43mKRWGIn FnpoPjEV5ZA Xxx2kvDqUC0cTuIk8K30YzwMAXNi 5iTvxpgyN zLIUcMTYqtCcvrY4DBHANCHw ZEQRJ8Gf5RhPomFzeiJ1PJ/n7R0CH7gM6dB/Qt0fnchnrGDseynyDIw/W6crhPXTx2SW6Pb5XjCNQ5S89TRf3/RndEbf2u8dvk/ow2jx2i772tcN0 RO jk/iEB3Nf0Tv3V7XecX6bXqvzzNa4MEjMmMVusfv0MZmkfI6H/HrNLWkPp/3YelZ t2vvURXxOZ3Dmu0urxIb/R2US6XoyHnLcskSrSy2E/7enTWou/MOeqfvCjuUKzR9PllKpwZFkMZLBbm6ProOXq9J2kBAHYna6vLNNjXq3NEPfv6aXGlVCnXljHlYdenYe0WFRdfpVeiYUXpsA9fhQ8BaAXJd2xK9OPF5x0xNCm2updPOjaEPn5 hS6q2M7xPTc0TSX7VEodG2YXR2m45mPDn4QxeiIh7ttk/Y4ZdOjQoScB3a/XQwOdB9xBME50dTPsIIh1HBw TXT5S1W V5dZHCrQbP4jWq3hwr1PPPOwfnuO pKeS juoT5aobVaOwO6X6LhgY/okePJiM6nhybu1fIYQjULY0dpuXBGP bg4ggNj16nuQV9HcMnKXSCjlWddCzS5L6o8yLHQy vHVHvtQQAaA2DfdSrj75r00PU1cUXFEPC7x/GfPijq9 EDwFoIxxD/9ulN6tiaFJsTVrey41l6tOPHMz3T1L ncrDCGXCY0PE2vTB6BgQOzaoGN3LZXxsUNtRMboWsn7iCx06dOhJQPfr9VJ/58Hd36O3nnuzehTA3XfobN8ZOt1tnaHevUt39VuVofmZX6dnw3Xv0uSew3TFHoWwfoXe5mXK/Q/rdHuORN7mEH3nQo7O7p8Un MhnCNBbn nwhf7izR7ay1207Ka6Plsfo7yXsrthyNnCrR8fprW1AYXLk5S/7kJ4jXiNS7nPOij83zSUnV7BADQFIv8DHPkq56Je/TkyTyNxYwo5zzoowu/dBA BKAtRHMKcQz9YKIyYiA5tiYtXwOvVkYJHBkepQ9XHHcHwmNDRM/EB GNhPjcK3LOAx2jU24yZP3EFzp06NCTgJ6u10vdnQfraytEM8fDiQ1N4gkOTfnTT4vyK sU7F2jt8tlxyn4o9t0eq99C4w7EvQy 8/Sc2qZSudE0qSMFcLHIopEx8021OesTF0V2/ioPBnjnv3v0St/Jre/s mvHisp4JMY1aDe/UVqx0FIzzE6QbM0vzBN55cLdCbthgUvP7hIPOISAFChPBRZY4Yq248p2I8xhPTso35aplKNo4rYh8cHP4QPAWg5OobeDMIYWrFpUmxNWr5C0rGhJvSxYbWOY0MtMTrrJ77QoScBHTr0xvVEmvurRqR2JlkfZpILqSdNfBES/lWTPRGSnsDNzMZmTc7mRk 2Zraj1snl5N9HSd2aINHsAyZqAx2My3OusmrsCRPF5GShN4wmPKTLo79TTZ7MjCdYzOXi25Y jE2QqLY5JPMAACe2rznJSaSqvG5NfFomKbYmLW 8zh61jg2VY4D0uJ4Y0TFpKk wGP L2Pg2YscUE6NNvk6Sj30R0KH7gA7dB/St0/m9jHWMHQ9lHp0HGU6yPkwlS11WfASfGIT3LMNUfY7Cujqp0Gc00UlGZXlO1TO7yxMWhmeITr5oif HdOMnJQBkBZfnXGXVaL/pXJQXnuALDO2V2EWA7qALy6s8LOALkbLX5H/GsyflP8x4/g8eAFDG9jUneUIlvc7vk2JoUvlqYchZXj42GJ/KY4M8BoQX 3pdV eEQazPSXb2typGJx/3IqBD9wEdug/oW6tzXsY6xo6HMo/OgwwnWR moqVuVz4AoPW4POcqAwB0NravOckTKuP13e75tO8PHboP6NB9QN96nctkrGPseCjzDf5VIwAAAADA7qLhZ0R3CNv9DC506NChJwG9Ob1W0HkAAAAAAFADrTjx6lSyfuILHTp06ElA9 v1gM4DAAAAAADgJe3EE3rjetYvLKBDh75z9XppvPPg7qT W8Qo8d8y1sZdeuPpwxQuvn6FXuL3n/DcPQAAAAAAAOwesn5hAR069J2t10tjnQd336A9x1doammTNjc5LdG33tsfdiDU1Q3QPU63N 7Q F7Xvx0DAAAAAACwM8nChQN06ElA3916Eg10HqzTlbdnKF9UF/3duoi6afzqFNHZd j9AKMIto8FGssN0XTJrgNdvqazdbFAp7uS1k36vPpYmz5IubEF9Y63l6OcSFwcOMqHwh3i8jFacLW5hdNi TGaz1y7tL9To/UjWJumoaTt LQaWRgzvzvwk QZ7ZeGfkLfuvrzWujD011dsbZZSNq2aVdNfnZztMdLB5OOey34zpGXSjoHOpckX ryhtqI3 uNH0MqrE0PhV4Pgjq84/PEllHH/taKLzb6tBpZON3ljZtZvnCADh367tV91N95sH6b5h6M0LFDOm/ofom NbBCa HTC3dpcs9hunKl8miD 7EG/QhD NiCXudywjrrV iwLt zZ1ItDbaeZk6IElDBOV88TqVrR3TBIBVWn6iTmiBMXByNS1Hl6nNN b2JnrDUCZ/kHAvCDoNw VIflf603tEtrTlJ81P5TqVCjiZHpqm j7P2sWeC7gX3KPppfFpjHLlWohOzI23 TUA6reksiFHlwxfKPiwViL6bf4ecH2faVe92jx6rHDd4f9lL9f08VoeP l4fPLG8ZDbYgu8ceql4El7qYPjEq/20IQ4pr4/Mngi9rq6/FTXGoZgntpMOi5tXVxuKm9t94QAdOvTdq6fR2GMLA8/SXv02zgN6pK73o1OsB3T20THa2NikTXWS9ODsOzVc8Kt1Vo/qdfJinbs0uf89 pZ5TKKYo4s1z7EAsszarVmi40eppecjpR/T4gt91KuzfAIwYa6JMkrPxPdpdHGWbtV5grG19NDEuX6avMh3rHQR2BGs3Som rBn4hyNfjhL82udUenh/iovZXt/lZe H3kJdB7NnnhtJ2HMPXEsweudEIcq7NS4ud0XDtChQ9 9ei001nnw4BF9ot/GGaBnu82d4gGaev1Q1LN96CjlyYxK8KHW Y5Z51hlnfU19e4Bnd2vRx4cf1ftgnsPQA2EQ/HMsL/KkH4eSlseDhgOX5Zwj/xRuk6LNLmvK66X3ilvj4fnBbRG00PRIwdlFsYoN2TfIVijqO gpV0HREdeURc7b9BIrKu/sk/l K33qRQo7WBlmPbY/DyNdR2Lvmsv/xbzUdC3frfo6 k7lvMVbWxe/QI8BFznhwql uYCUfBQR7N NLw0LA3vioyNDWlN14feR6NPr6nX2P6b4anijkrsu0T7HKGXK6jfRmtRnWp6 2hwebXOOz3AibM9qRpQPuwy5TETMVw/R lakOLDsM352rzOhygfhn0Htfgwah9RG R91u0l3KB v6C l37sgT87HCJt9kt4Mr2ND9FQTccRP 7jWuRb6aXwN9V MXroparjnvzOCttL5f3Vy03HvVSm9zl4qQNp6MQryetODxhU 6k6jmupVNle1Ka018vHcYXySldCzD1xrDavVzyivV4enaPbtox76kvF4p6IG ke1F5P3X8/WxE3D4pHunh/oz3Wy6m42dUVaY3Gze2 cIAOHfru1Wvm4MGDwczMTDA Ph4wm5ubKWkpmDqQC/JFq3xpKhigfFDc2FD5YpCngWBqyegyXwxO5qz3D8U64XtrHbNt Xm7IMn64DqSeVlWYT4Yja4THGkwKJSiZcZy5j1nRwN1oaEzBt6Oa3ldvvqEMzqvtj14KYjkUfU5o8GtJ0rn96Pz4VLM/CgFIqvh9UeDeV6 nJf7rDRnudmWvb6kFBQG9bK3ngThEnqfzOJmn57MjwW5qp3jbYvfyc6rdQbDDP8 udhvoM4bgsFLq5zTef2bxIhvr1QYUtsoRNuIoZcLf3N r7atVoq25ttHv8b7XP7KpUIwFKtj9buN3gql8DczdRoVKD3pN9 ZuDznKqug24Ruq/GUUD/l9iSJ11m8/tR74cPqNhj3YVWbj7IaXj/uQ7n9UmEwyKm2GWWj9sHtO1L1fon2ye04yo6F37n8vcK88bSkehvlNq7335B8HInvb3kfYujlyr9hTvzm jubbCwf3348H 1v TdVXhoUnxF5Se9w1fdn3fV7gO3C9jWn999/v5zqjbmXym1EtC3VphO9XrW8ta75PBMrZJti31d5xbRZA69vt8HK9uNxyOcRsx8y9sfjXjxuGOTnWduvef T9leilxMeLR9TrG3E836N95fPJ0JM3BSfwXEz/MpV35919btX/R5xqttXHOjQfUCH7sOnsyZjHWPHQ5lvYORBN42/maeZ43LeAX6s4CzR1Ov0G rKqeV091AfzeBRhZqoPPtbSfOkAlvE2iot04dRzzr3nh 9TvdWViON7 pxWdgzXyvq82YmoiGQR4bV5yxTibvX f31OYruMSzQ3HKBztT06IDc/2tUWaXynCOn8qPZifTQxD21bKlAH7/8S3Sa72joffrT8Nyusk85vgN441j8rqBN LvpOxLh73aNFlfMhGcvWL/BYOXOjvxNqqhsr3fyeZq/p7fBlCd8jOqC9zgi2nZTLgu/y6s0bH7Dngn6/uiHVP46/Fu/qcWq/e lvsFlWq3lFsquRrUJ0V6jZPswoT3xHbfw7lU9PrTbYNyHVW2el/OijhF8pz1sm/30ow9eJ7WrGl8bVG3n5kS0LI8AinmB86Lt1NLG9f6nH0fUbyn2l71U3t/E49oLlX1rlLAeR0MvhR nvHRudDH0UvR91O9hdtj /vDSDiEem6TXwzZR5fXrwutJHvAReSzyumhT7JUblle aUzgwxOHvB5R 1Fr3KvFgzXv//bGzVfM8cfEzbJ/1e h4qb6 OrvX4PXs35HEjp06DtXr5fGHls4dIk2i0THyxMYHicqbtKd8e7mDs6JHKLCEv bw379eSpNYsrExnm1Mpkgp2tHVWCcpiH1EpWXqDCoF22YI3SmsEzn1QV5afqHtJzwjGXbUQF 5tIg3fgTPiWJ9umH71j7pJb54MkTUtYKTzwqQxFtRq3fzXkVUwfypFN0lPDQyPKEj1FdtMdXjVCilcV 2rctlbnTcLQn7cMf/YI70Frnw6o2n0plwkRum0fDM IWUnMbr/U4orzk6nRs XGtlcBLuwe311t7nD9Cb176OPTK2vT50Cu1/Qt2QhxqFTV7sNb933lxM sXFtChQ9/Zer001nnAHCpEkxfqVIj9 4K62N Uf Uo84fo0ob1PowQeplytLC20T1Od8TnbcY/ENRKzz7qpxthgI5RWqHFQT3J4Notml0MS5ui59gJotmL9PZskHD3ok133hamK88o8jOexUV6oS aPjHcp Lbzn3qmbhHJXXG8bFrmED4u10Pf7fa7g41AdeFmfCxRXURQ7eBuegWT3jS9cPrYiSCD777otpJk/dwgGhPMco VL vVfeNXr/72nxELz03 PHW3gGvo42nH0c8tOG4FkPXI3spPC4oL52/LkYi NBeio5MYMeSFDvacJzvOXY89MpFPa9BdRvchtEudXgwff89tOH3jKHjZngfgtFx85Vv6rwPT9zMwoUDdOhJQN/dehKNdx6ADuUIXV29RDSpLk/C4X0q8aRBR85QgSapl/MjK9TvvDtwhIZHF kNe6K2JHgIb/91utH//YS/Ouqh8LpmXp7JVIYfc4pNOlQrR/bRj8vb6KXJ539EH7yuT9F5qGH/jfg LZwuT3LEQ57fep1DfPRdw GR4YSJR ha B9wvZ7J7FqEqotLuTdS6oKJ72McqdkTcUVtYPmo/h69s/TtR1dVaQ3wCVr/vhrvXoNkKu0paqe6DrUPn X26PHhK6Mf1uXDqjYfQ/mQB4/FfNhmam7jitTjiIeajmtM9Jsav8TxHfeiemQvhccF5aUTpRrv3vK/wsBLu4CE2FGTB3zHcQfaK9f7z3lj7uxW/j1BzR5UpO6/h5qPKc3FTX4MUsbNmkZleeJmli8coEOHvnt1L/VPmIi0VUnWh5noQuq yS ygnvSIwFPOjTkmvCofcyP8WSB/omLgAuehFJOJrU7cHnOVZZlUtv8NviwHlKPIx2H8tLQ0K7zUtaxfc1JTiIlvZ5V37snFRXwpJ7OSQazQer dxyNxc209gUdug/o0H3YOudlrGPseCjzGHkA2gcP4V0u0Ju SZt6JmjmeJF6q 7otQkearh8yb9PwMnCWC9NNnJHCGwvtbT5rfZhPdRyHOkw2EtvPP8WvNShNHXHpp1or3gnJ1Zev3liNvR66kiGraaW/e8wFk7vqztubvcdR jQoe9evSYw8iC7SdaH6SWSut1zlB3M3yRm6S51ZZ iv88CoDZcnnOVZY9Ob/NZPI6AnYzta07ybowpyx6RV3Id65VO3//Wkda oEP3AR26jySdy2WsY x4KPMYeQDagP6bxOBehu6sVfaJn2cEYOfT6W0 i8cRsNtJu6Pjo3165JV3Z0a9Xtm /YvYufsf0Qp9O 84QocOfffqdYGRB9lNsj5Mb5HUk3qQAACtw U5VxkAoLOxfc1J3o3xeT3tOAAdug/o0H1Ah 6jFbqMdYwdD2UenQcZTrI TMVLPa0xAACax U5VxkAoLOxfc1JnlAleT3tGAAdug/o0H1Ah 6jFTonGesYOx7KPDoPMpxkfZjKl7opAwC0D5fnXGUAgM7G9jUneULl8nqa/6FD9wEdug/o0H20SudXGesYOx7KPDoPMpxkfZgKlropAwC0D5fnXGUAgM7G9jUneUJlez3N 9Ch 4AO3Qd06D5aqfN7GesYOx7KPDoPMpxkfZhKlrqseABAe3B5zlUGAOhsbF9zkidU0utpvocO3Qd06D6gQ/fRap3zMtYxdjyUeXQeZDjJ jAVLXW78gEArcflOVcZAKCzsX3NSZ5QGa neR46dB/QofuADt1HO3Quk7GOseOhzKPzIMNJ1oepbKm7GgAAoLW4POcqAwB0NravOckTKlPmAzp0H9Ch 4AO3Ue7dC6XsY6x46HMo/Mgw0nWh6lwqSc1AgBA63B5zlUGAOhsbF9zkidUaV6HDt0HdOg oEP30U6dNRnrGDseyjw6DzKcZH2YSpe6ryEAAFqDy3OuMgBAZ2P7mpM8ofJ5Pe04AB26D jQfUCH7qMVuox1jB0PZR6dBxlOsj5MxUs9rTEAAJrH5TlXGQCgs7F9zUmeUCV5Pe0YAB26D jQfUCH7qMVOicZ6xg7Hso8Og8ynGR9mMqXuikDALQPl dcZQCAzsb2NSd5QuXyepr/oUP3AR26D jQfbRK51cZ6xg7Hso8Og8ynGR9mAqWuikDALQPl dcZQCAzsb2NSd5QmV7Pc370KH7gA7dB3ToPlqp83sZ6xg7Hso8Og8ynGR9mEqWuqx4AEB7cHnOVQYA6GxsX3OSJ1TS62m hw7dB3ToPqBD99FqnfMy1jF2PJR5dB5kOMn6MBUtdbvyAQCtx U5VxkAoLOxfc1JnlAZr6d5Hjp0H9Ch 4AO3Uc7dC6TsY6x46HMo/Mgw0nWh6lsqbsaAACgtbg85yoDAHQ2tq85yRMqU YDOnQf0KH7gA7dR7t0LpexjrHjocyj8yDDSdaHqXCpJzUCAEDrcHnOVQYA6GxsX3OSJ1RpXocO3Qd06D6gQ/fRTp01GesYOx7KPDoPMpxkfZhKl7qvIQAAWoPLc64yAEBnY/uakzyh8nk97TgAHboP6NB9QIfuoxW6jHWMHQ9lHp0HGU6yPkzFSz2tMQAAmsflOVcZAKCzsX3NSZ5QJXk97RgAHboP6NB9QIfuoxU6JxnrGDseynyOOw9OnTpF9 /fp8uXL9Pjx48JZIOnnnqqXB9zc3M0MjISqx/WAQDtRXoOPgRg52J7nXnmmWfCV bTTz/V7wAAAICdg4x1L774YlU8HB4e1jkidB5kmLTOAwDA1gIfArA7cHUeAAAAADudtM6DLv0KAAAAAAAAAAAA4ASdBwAAAAAAAAAAAPCCxxYyjP3YAgAAAAC2Bn5ECQAAANht B5bQOdBhrE7D2TFAQAAAAAAAAAA7QJzHgAAAAAAAAAAAKAu0HkAAAAAAAAAAAAAL7mXX345 Pa3v43HFjII5jkAAAAAAAAAALBdJM55cODAAV0MsgjmPAAAAAAAAAAAsPUQ/X A2oEKw ZzawAAAABJRU5ErkJggg==[/IMG]

I can mount partition 1 and 2 fine, but i get an error when trying to mount partition 3(which obviously has all my data)

```

PS C:\Users\---> wsl --mount \\.\PHYSICALDRIVE1 --partition 1The disk was successfully mounted as '/mnt/wsl/PHYSICALDRIVE1p1'.
Note: The location will be different if you have modified the automount.root setting in /etc/wsl.conf.
To unmount and detach the disk, run 'wsl.exe --unmount \\.\PHYSICALDRIVE1'.

PS C:\Users\---> wsl.exe --unmount \\.\PHYSICALDRIVE1
The operation completed successfully.

PS C:\Users\---> wsl --mount \\.\PHYSICALDRIVE1 --partition 3
The disk was attached but failed to mount: Invalid argument.
For more details, run 'dmesg' inside WSL2.
To detach the disk, run 'wsl.exe --unmount \\.\PHYSICALDRIVE1'.
PS C:\Users\--->
```

I'm assuming this is due to it being LVM, if so how would I access this now? i ran pvscan within the wsl environment and can see it 

root@DESKTOP----:/mnt/c/Users/---# pvscan
  PV /dev/sdd3   VG ubuntu-vg       lvm2 [222.06 GiB / 111.03 GiB free]
  Total: 1 [222.06 GiB] / in use: 1 [222.06 GiB] / in no VG: 0 [0   ]

---

### Post by MAFoElffen on 2023-10-24
Sorry. Forgot you had LVM volumes. I do not know of any way that WSL can mount LVM volumes.

There is still booting from a Linux Live USB, mounting the LVM volume and backing it up that way.

---

### Post by shinku443 on 2023-10-24
its ok i was able to mount it, i pulled what i could off of it, but im thinking maybe i should get a new drive. this is what CDI shows: [https://imgur.com/a/BzqwLI9](https://imgur.com/a/BzqwLI9)
i used victoria to remap the bad sectors but the health still shows as bad and its like $16 for a new 240gb NVME so i just went ahead and ordered that. in terms of disposing of this properly, i already formatted it do i just send it to an electronics heap or toss it in the trash

---

### Post by MAFoElffen on 2023-10-24
LOL. Yup. I wouldn't trust that one.

---

