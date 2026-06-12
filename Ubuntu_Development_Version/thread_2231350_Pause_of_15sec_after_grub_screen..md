---
title: "Pause of 15sec after grub screen."
date: 2014-06-25
forum: Ubuntu Development Version
---

### Post by LastDino on 2014-06-25
Well, truth to be told, this developer version has been working pretty good on my machine with the exception of 2 things.

1. There is pause of about 15 seconds ''after'' the OS option is selected in grub menu. This is unique to Ubuntu 14.10 only as Ubuntu 14.04 gnome and manjaro installed on other partitions are booting just fine. 

2. I'm not able to drag and drop program windows from one workspace  to  another. When I try to do this computer screen just hangs as shown in  attachment. This is not hardware crash as I'm able to take screen shot  in even that situation and when I tried to reproduce the problem, my  resources were well below where I would expect a crash.


[ATTACH=CONFIG]254110[/ATTACH]

With no. 2 I could be wrong about function of the multiple workspaces as this is the only Ubuntu version I've actually tried this on. So, pardon me if that's the case.

No.1 does seem like a genuine issue though, where to look for possible explanation? Any ideas?

---

### Post by grahammechanical on 2014-06-25
I have experienced the second problem and it definitely should not happening. It never happened at all during the development cycle of Trusty. As regards the problem with Grub you could try running

```
sudo update-grub
```

from which ever OS you have in charge of the Grub boot menu. You may even need to Grub bit the command will depend on how many disks you have and from which OS you are running the command.

```
sudo grub-install /dev/sda
```

Grub may be having difficulty finding it way to Ubuntu. I am just guessing.

Regards.

---

### Post by LastDino on 2014-06-25
Ok, originally Fedora was my main OS and in-charge of grub, but I had it removed when I installed 14.10 and naturally there was trouble booting. So, I installed Grub using Live boot USB using following commands.

```
sudo mount /dev/sda(partition where Ubuntu 14.10 is installed) /mnt 
```
Then
```
sudo grub-install --root-directory=/mnt /dev/sda
```

So, I dunno, but just in case, I've made Manjaro in-charge now and its the same. Is it possible that it is happening because I've all my installs in extended partitions?

---

### Post by Cavsfan on 2014-06-29
> **LastDino said:**
> Ok, originally Fedora was my main OS and in-charge of grub, but I had it removed when I installed 14.10 and naturally there was trouble booting. So, I installed Grub using Live boot USB using following commands.

```
sudo mount /dev/sda(partition where Ubuntu 14.10 is installed) /mnt 
```
Then
```
sudo grub-install --root-directory=/mnt /dev/sda
```

So, I dunno, but just in case, I've made Manjaro in-charge now and its the same. Is it possible that it is happening because I've all my installs in extended partitions?

I wouldn't think that would be the problem. I have Windows 7 on sda1, Precise 12.04 on sda2, swap on sda3 and sda4 is an extended partition where logical partitions sda5 has Utopic 14.10 on, sda6 has Trusty 14.04, sda7 has Mint 13 Maya and sda8 has Mint 17 Quina on it.

```
cavsfan@cavsfan-MS-7529:~$ sudo blkid
[sudo] password for cavsfan: 
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" 
/dev/sda2: LABEL="Precise" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" 
/dev/sda3: UUID="e14dc02e-6ea8-4c95-b4d0-9dc04d32294d" TYPE="swap" 
/dev/sda5: LABEL="Utopic" UUID="7c76d1de-7439-4b55-b587-898f104235da" TYPE="ext4" 
/dev/sda6: LABEL="Trusty" UUID="d3281f82-3582-4081-b4d7-4769a2f427c5" TYPE="ext4" 
/dev/sda7: LABEL="Mint-Maya" UUID="77cf61db-2e8b-4531-9594-80f35ad4dc69" TYPE="ext4" 
/dev/sda8: LABEL="Mint-Quina" UUID="673f25f0-6149-4da7-98f8-4ebfe08a2188" TYPE="ext4" 

```

Have you tried booting 14.10 with systemd to see if that improves boot time?

You can add a line to grub to be able to choose 14.10 systemd as a boot option and leave the regular 14.10 boot option asis [_here_]("http://ubuntuforums.org/showthread.php?t=2224798&page=6&p=13059146#post13059146").
Or from this post [_here_]("http://ubuntuforums.org/showthread.php?t=2224798&page=2&p=13034320#post13034320") you can either temporarily boot 14.10 with systemd or permanently.
But, if you made the permanent change all of your Linux OSs would use systemd and I don't think you want to try that.

14.10 comes with systemd installed so there is no need to install anything to get it to work.

---

### Post by Bashing-om on 2014-06-29
LastDino; Hello,

Here is a thought, IF you have 30_os-prober enabled on the other non-primary operating systems such that there is 'recursion' going on that might account for that delay while grub makes up it's mind what to do.

I have multiple OS installed on two hard drives, the recursion factor was doing me a number - (and though I have tried several booting alternatives I have yet to come up with a completely satisfactory booting arrangement). As I am presently arranged for booting, I have all 30_os-prober's disabled on all but my primary booting system and am able to boot any of the OSs from that primary boot. You might try that - yeah a trial to turn off 30.os-prober and "update-grub" and as well reinstall grub as required for each and every OS installed, But eventually you will get rid of that recursion factor. If indeed this is what is taking place.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by Cavsfan on 2014-06-29
> **Bashing-om said:**
> LastDino; Hello,

Here is a thought, IF you have 30_os-prober enabled on the other non-primary operating systems such that there is 'recursion' going on that might account for that delay while grub makes up it's mind what to do.

I have multiple OS installed on two hard drives, the recursion factor was doing me a number - (and though I have tried several booting alternatives I have yet to come up with a completely satisfactory booting arrangement). As I am presently arranged for booting, I have all 30_os-prober's disabled on all but my primary booting system and am able to boot any of the OSs from that primary boot. You might try that - yeah a trial to turn off 30.os-prober and "update-grub" and as well reinstall grub as required for each and every OS installed, But eventually you will get rid of that recursion factor. If indeed this is what is taking place.[INDENT][INDENT]my little bit to try and help
[/INDENT]
[/INDENT]


I'm pretty sure that _only_ the partion that grub is installed on can look at any files in that partition's **/etc/grub.d/** directory.
If you re-install grub on each OS (**sudo grub-install /dev/sda**), the last one that you execute that command on will be the OS in control.

I have mine installed on Mint 17 Qiana and it cannot see the files on say Precise 12.04 for example. You can change the grub on any install and even update it **sudo update-grub** but unless you have also entered the grub-install command anything you do on that install is moot.

---

### Post by zika on 2014-06-29
Do You see any message(s) about soft reset while boot-ing?
Of course, without **quiet** switch in kernel boot line...

---

### Post by ventrical on 2014-06-30
> **grahammechanical said:**
> I have experienced the second problem and it definitely should not happening. It never happened at all during the development cycle of Trusty. As regards the problem with Grub you could try running



The second one is kind of baffling to say the least . Same here.

---

### Post by LastDino on 2014-07-12
To update the things, second problem seems to be gone after the updates. I haven't yet got around to trying out suggestions for first, but when I do, I'll come back with feedback.   Though, to add little something, new install of Win8.1 is having the same delay as well.

---

