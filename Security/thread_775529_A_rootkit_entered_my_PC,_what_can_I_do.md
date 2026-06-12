---
title: "A rootkit entered my PC, what can I do?"
date: 2008-04-30
forum: Security
---

### Post by Cookie503 on 2008-04-30
Hi everyone!

I think I did a bubu. I wanted to install something that needed root permission...so I googled it and found out how to install it through root. Only after that I realised what I had done:

Now when I try to run updates I get this error: Executing usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '37748739' '--update-at-startup' as root user has failed.

When I try unlocking the "user and groups" I get this error: "An unexpected error has ocured"

Plus, I can't do much...it seems I don't have anykind of permission now...I think this is all because I did that sudo thing. 

What should I do next? Is there a way fixing it without having to reinstall? 

Thank you guys!

---

### Post by shearn89 on 2008-04-30
can you clarify what you did to install it - maybe a link to the page? Did you just do "sudo <command>", or something  else?

---

### Post by PmDematagoda on 2008-04-30
What exactly did you install using root? If it was a rootkit you were installing then you may not have much hope of a good recovery.

---

### Post by Cookie503 on 2008-04-30
It must have been some package I didn't manage to install using the synaptic package administrator. I don't remember though. The latest application I've instaled is Virtual Box, only after I installed it and had to do the "user and groups" modification I noticed something is wrong.

---

### Post by PmDematagoda on 2008-04-30
> **Cookie503 said:**
> It must have been some package I didn't manage to install using the synaptic package administrator. I don't remember though. The latest application I've instaled is Virtual Box, only after I installed it and had to do the "user and groups" modification I noticed something is wrong.

Well, can you at least remember the link/web site you got the package from?

---

### Post by shearn89 on 2008-04-30
What user and groups modification? Do you have a link to the page?

Edit: I keep saying exactly what PmDematagoda is saying...

---

### Post by Cookie503 on 2008-04-30
> **PmDematagoda said:**
> Well, can you at least remember the link/web site you got the package from?

No, unfortunately I don't. I instaled many packages that night.

> **shearn89 said:**
> What user and groups modification?

After installing virtual box I have to assign my user the vbox group...


Is there a log I can check or anything I can do? I searched the forum before making this thread and I found someone else who had the problem, he fixed it by using the live cd and editing "hosts" file in /etc/ - but  I can't do that from the live cd, acces denied or something like that, don't have permission.

Here's what my "hosts" file says

127.0.0.1	localhost
127.0.1.1	mihai-desktop

'mihai' is my username.

Any ideas guys? Thank you!

---

### Post by shearn89 on 2008-04-30
Do you know how you added your user to the vbox group?

---

### Post by Cookie503 on 2008-04-30
I didn't shearn89, I didn't manage to do that, because I couldn't unlock the "user and groups" menu. When I hit 'unlock' that 'An unexpected error has ocured' pops out.

I was going to assign my user to the virtual box group but that error popped out, and I realised something is wrong, after that I noticed some menus are missing, I tried adding them back, but when I tick their name (to add them) they just don't show up...

---

### Post by PmDematagoda on 2008-04-30
Did you try adding yourself to the vbox group manually using:-
```
sudo usermod -a -G vbox username
```

---

### Post by Cookie503 on 2008-04-30
I tried now, here's what I got:

mihai@mihai-desktop:~$ sudo usermod -a -G vbox username
[sudo] password for mihai: 
mihai is not in the sudoers file.  This incident will be reported.

---

### Post by PmDematagoda on 2008-04-30
That looks terrible, I'll be moving this thread to the Security Discussions section along with a new title, hopefully the people there can help you get over this attack.

In any case, what I know is, the best thing you can do right now is to do a clean reinstall.

---

### Post by shearn89 on 2008-04-30
> **Cookie503 said:**
> I tried now, here's what I got:

mihai@mihai-desktop:~$ sudo usermod -a -G vbox username
[sudo] password for mihai: 
mihai is not in the sudoers file.  This incident will be reported.

that just means sudo hasn't installed properly. There's no way to change that without logging in as root, which you can't do...

the only thing i can think of is booting with the livecd and chrooting, which isn't simple...

I'd go for a reinstall.

---

### Post by PmDematagoda on 2008-04-30
Oh and one more thing, get off the internet and shut the thing down to prevent further damage, just get online with another PC until you fix this problem.

---

### Post by Cookie503 on 2008-04-30
I'm dualbooting, I have a windows installed on my other hard drives...it's ok if I use it? O, will I have to reinstall my windows too?

Thank you guys! Uhhhm, any advices so this won't happen in the future?
I'm going to log in my windows, and delete the ubuntu partition along with the swap, and reinstall ubuntu.

---

### Post by JPorter on 2008-04-30
The correct advice is one you won't want to hear...

Don't download random packages from all over the internet and install them haphazardly without knowing what you're doing!  And certainly don't compromise the security of your system to get those packages installed.  It shouldn't be necessary to take such a brute-force approach to getting some software set up and running.

Wipe the partition and start from scratch.

---

### Post by Bothered on 2008-04-30
I'd agree that a clean install looks to be your only option.

Have you tried looking at your ~/.bash_history to see what command you might have entered?

---

### Post by Cookie503 on 2008-04-30
Bothered, I'll keep that command in mind, it's too late now, I already wiped out everything.

Thanks again guys!

---

### Post by Cookie503 on 2008-04-30
I tried wiping everything this way: restarting the pc, entering windows and deleting the ubuntu and swap partition...restarted the pc, entered the windows setup repair console, fixmbr...restarted the pc again, installed ubuntu, everything went great. But now, when I changed my screen resolution a part of the screen was using the wallpaper before I wiped ubuntu. 

My question is:
Is it possible that some of the configs, settings didn't get deleted? Or are they stored anywere else besides the ubuntu '/' and swap partition?

---

### Post by Bothered on 2008-04-30
That depends - do you have any other partitions, e.g. a partition mounted to /home?

---

### Post by Cookie503 on 2008-04-30
> **Bothered said:**
> That depends - do you have any other partitions, e.g. a partition mounted to /home?

Uhhm no. 

2 NTFS partitions for windows.
1 ext3 partition for ubuntu
1 for swap.

I used exactly the same configuration before wiping out ubuntu.

---

### Post by shearn89 on 2008-04-30
the best way to remove the partition is to boot up with the livecd, hit alt-f2 and type "gksudo gparted", then use that to delete the partition. Select it, delete it, hit apply. Job's a good'un.

---

### Post by Bothered on 2008-04-30
Unless you restored your personal configuration files (files in /home), have configuration files on your Windows partitions that you have in some way set up to be used, have some unformatted partition (e.g. mounted to /home), or some other similar way in which files remain or are recovered from backups, it really shouldn't be possible for settings to remain after a clean install.

---

### Post by Cookie503 on 2008-05-02
I did as you said Shearn and after reinstaliing ubuntu, I tried to change the resolution and guess what? The same thing happened, it working fine now, but it's just odd.


Here's a screenshot:
[[IMG]http://img29.picoodle.com/img/img29/4/5/2/t_Capturecranm_a478306.png[/IMG]](http://www.picoodle.com/view.php?img=/4/5/2/f_Capturecranm_a478306.png&srv=img29)

---

### Post by shearn89 on 2008-05-02
hmmm. Looks like xorg isn't quite configured correctly - the panel at the top is duplicating everything... Maybe try "dpkg-reconfigure xserver-xorg"? Backup up /etc/X11/xorg.conf first though.

---

### Post by Cookie503 on 2008-05-02
Seems to be working fine now, thank you!

---

