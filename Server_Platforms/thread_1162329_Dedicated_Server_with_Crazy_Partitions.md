---
title: "Dedicated Server with Crazy Partitions"
date: 2009-05-17
forum: Server Platforms
---

### Post by Gremmie on 2009-05-17
I've been a customer of 1&1 hosting for over a year now. I have a dedicated root server that is currently running Fedora Core 6. I've been wanting to upgrade for some time. Recently I saw that 1&1 now offers a number of linux distros, including Ubuntu 8.04. So I took the plunge and got a 2nd server, intending to migrate to it and leave my first one behind. I had the server re-imaged to Ubuntu from my 1&1 control panel (the new default is CentOS 5). It seemed to go well but when I took a look at the partitions I see this:

```

/dev/md6              4.7G  228M  4.5G   5% /var
/dev/md7              221G   83M  221G   1% /home
```

It seems like those should be reversed for a server configuration. All the logs, databases, and www data go under /var by default. But /var is only 4.5 gigs and /home is 221 gigs.

Now I'm not planning on using Plesk or any other control panel, so I suppose I could put stuff wherever I wanted to, but could that be a problem for future upgrades?

I've asked 1&1 for advice, but I have a feeling I'm on my own. As I see it I have 3 choices:

1) Somehow repartition to more sensible sizes for a server. The problem is, I don't know how to do this. Can someone point me at a guide or something?

2) Just put all my databases and website data under home somewhere.

3) Give up and go back to their default Centos 5. I'd rather not do that, but its not the end of the world I guess. I really wanted to use Python 2.5 for some web apps, and Ubuntu 8.04 will do this for me with less hassle.

Thanks for any advice.

---

### Post by andrewc6l on 2009-05-17
If you want bigger things under /var, I'd be tempted to use symbolic links in /var to an appropriate /home/user directory.

I'm guessing 1&1 is configuring things based on old timesharing assumptions that your machine will have multiple users, each of which will need space on /home/ - something that doesn't happen now that machines are so cheap.

---

### Post by Gremmie on 2009-05-17
Thanks for that idea. Symbolic links might work for me. Off the top of my head, I really only need my mysql data and website space on a big partition. I'd have to keep an eye on my log sizes I guess.

The thing is, 1&1 is offering dedicated servers, primarily for hosting websites. Their other distributions they offer (or offered in the past), like Fedora and CentOS seem to have huge /var partitions. Perhaps they didn't take the time to customize the image accordingly, I don't know.

Please keep any and all ideas coming. Is there a re-partition guide somewhere?

---

### Post by andrewc6l on 2009-05-17
Most of what I've seen recommends the gparted live CD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)). But that probably won't work if you have a server located remotely.

If you're lucky, /var and /home are partitions right next to each other - in that case, there's a chance you can boot to single user mode / recovery mode, unmount /var and /home, resize /var and /home with fdisk (by deleting /var and /home and then creating new partitions with the sizes you want) and then going back to multiuser mode. Be sure to back up things that are in /var and /home to somewhere useful like /var.orig and /home.orig on the root partition. You probably want to use cpio to copy so you preserve all the permissions / sticky bits / etc.

Doing this isn't too bad, but you can make your machine nonbootable if you make a mistake.

---

### Post by hictio on 2009-05-18
Is there a fee involved if you ask them to re-install reversing the partitions?
I don't know but if it is going to be your new server, I guess it is better to start with the right setup from the get-go.

---

