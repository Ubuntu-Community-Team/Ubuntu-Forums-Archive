---
title: "Permission to shut down while other users are logged in?"
date: 2009-11-22
forum: Security
---

### Post by stalkee on 2009-11-22
Just now when I went to log out, I got this "Permission to shut down while other users are logged in" message, prompting me for my password. This was after a few hours of it sitting on while listening to the Rythmbox radio station while I was drawing(on paper, not on the system). This is the first time this has ever happened, any advice?

---

### Post by CharlesA on 2009-11-22
Do you have it set for remote access with SSH or telnet? If so then check /var/log/auth.log to see if anyone has tried to access the machine remotely.

Other then that, if it's serving files to other machines, that might be the cause of the message.

---

### Post by stalkee on 2009-11-24
Thanks for the reply, but now I can't get into Ubuntu at all...I went through Synaptic and removed some things like Remote Access that I didn't think were important or necessary going by the package descriptions, and one of them might have been that telnet thing. 

So after that my browser wouldn't work, So I just moved over to the PS3 browser(this is all on a PS3). But now I can't get back into Ubuntu, at the kboot prompt it says:

/init: eval: 1: /boot/vmlinux: not found

I don't know if this is because of an intruder/hacker or things that I deleted. Just before I did the Synaptic thing, I installed and ran the RK Hunter package, and it did come up with some warnings but I wasn't sure what to do about them yet.

It's not a big deal since the PS3 browser seems to support sites now  that it didn't before like my yahoo email, which was the main reason that I had Ubuntu in the first place. However, on here I can't put up photo's of my items for ebay and I need to get some things printed out so it is kind of a problem. I guess I will just try to reinstall it...if I can find where that CD went off to, that is! Unless there is something else that I can do from the kboot prompt, that would be great since if I have to install, that means reformatting my 250GB(I bought a 80GB PS3, which arrived w/ 40GB drive so I got a $10 refund from the guy and bought a 250GB haha) and losing all of my PS3 demos and will have to back up and restore my save files etc, so would like to avoid that if possible, even though I barely play the thing anymore.

---

### Post by cariboo on 2009-11-24
You must have removed a lot more than just vino and vinagre, as it seems you also removed one of the kernels. Do have an older kernel you can boot from in the grub menu list?

Depending which version of Ubuntu you are running, for pre 9.10 version press esc when you see the grub menu. For 9.10 press the shift key to see the grub menu.

---

### Post by stalkee on 2009-11-25
> **cariboo907 said:**
> You must have removed a lot more than just vino and vinagre, as it seems you also removed one of the kernels. Do have an older kernel you can boot from in the grub menu list?

Depending which version of Ubuntu you are running, for pre 9.10 version press esc when you see the grub menu. For 9.10 press the shift key to see the grub menu.

I don't know what vino and vinagre are? I don't think that I took anything out of the v's in Synaptic, but I did find my installation CD. Is there anything I can do to restore the missing files without having to reformat, reinstall Ubuntu, and set everything up again? Such as booting from a kernel like you mentioned...That would be ideal since then I would not have to lose everything on both sides, like my bookmarks and demo's. I was able to open the grub menu but I was not sure what to do from there.

I started it up with the CD inserted, but it just began to install everything again. It is not the live installation CD, it is the PS3 alternate install(Jaunty Jackalope). I tried the esc menu on the CD but most of the options just bring me to the partitioner.

---

### Post by CharlesA on 2009-11-25
> **stalkee said:**
> 
I started it up with the CD inserted, but it just began to install everything again. It is not the live installation CD, it is the PS3 alternate install(Jaunty Jackalope). I tried the esc menu on the CD but most of the options just bring me to the partitioner.

There should be an option to "recover a broken system" from the boot menu.

---

### Post by stalkee on 2009-11-25
> **CharlesA said:**
> There should be an option to "recover a broken system" from the boot menu.

The only thing like that that I can find is a "rescue mode" option in the menu when I start up the system with the CD inside. When I start it though, I get this:

"The installer could not find any partitions, so you will not be able to mount a root file system. This may be caused by the kernel failing to detect your hard disk drive or failing to read the partition table, or the disc may be unpartitioned. If you wish, you may investigate this from a shell in the installer enviroment."

However, when it does bring me into the partitioner, I can see that the two original partitions are there. If there is not any commands that I can give to fix it from within the shell, I am guessing that I will have to completely reinstall?

---

### Post by orawax on 2010-02-04
> **stalkee said:**
> Just now when I went to log out, I got this "Permission to shut down while other users are logged in" message, prompting me for my password.

A friend got the same message the other day. He's a basic desktop user who definitely hasn't set up any remote connections. I went through his auth.log for that day, but can't figure out if there's anything suspicious in it. Could this have something to do with a gksudo application running when shutting down?

---

### Post by movieman on 2010-02-04
I got that message a few days ago as well, and there was no-one else logged in.

---

### Post by cariboo on 2010-02-04
IT may be the the users are logged into  console, the best way to find out, when that happens is to open a terminal and type: 

```
w
```

The results will look something like this:

```
w
 18:57:34 up 10:47,  2 users,  load average: 0.00, 0.02, 0.04
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
me     tty7     :0               08:10   10:47m  2:25   0.19s gnome-session
me     pts/0    :0.0             18:57    0.00s  0.13s  0.01s w
```

---

