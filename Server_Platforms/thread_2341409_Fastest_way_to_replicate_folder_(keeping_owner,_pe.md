---
title: "Fastest way to replicate folder (keeping owner, permissions, special files etc)?"
date: 2016-10-27
forum: Server Platforms
---

### Post by timonoj on 2016-10-27
Hi guys,

I'm trying to fully replicate a folder I have in a NFS path to a backup path within the same drive. So...just a copy. But I want to keep all the files timestamps, permissions etc identical to the source, as these files belong to the Seafile DB. The server is...a Banana Pi. It's a huge folder, around 700GB. But somehow with rsync I'm getting very crappy speeds of around 4MB/s read and another 4MB/s write...I know the Banana can do much faster than this, and so does the NAS, as they reached much faster speeds in normal copy tasks before. All the network is gigabit. Is there a faster way to fully replicate a folder within the same drive?

Thanks!

---

### Post by alsoeric on 2016-10-27
man cp. I think you want "cp -a"

---

### Post by timonoj on 2016-10-27
Hm...I thought cp didn't have a way to keep timestamps etc. I'm going to give it a shot, thank you!

---

### Post by ajgreeny on 2016-10-28
From man cp you will see the **-p** option, which sounds as if it is just what you want, but if you have any links in the folder it could certainly be the **-a** option will be better.
```
-p     same as --preserve=mode,ownership,timestamps
-a     --archive               same as -dR --preserve=all
```

---

### Post by Speculos on 2016-10-30
Try to use rsync, I use it to backup my 19 Tb data to a distant server.

```
rsync -avzn /source_folder/ /destination_folder/
```

Always try with the **n** options, this is a dry run it will tell you what it will backup, then remove it when you sure.

---

### Post by timonoj on 2016-10-30
Thanks for all the replies. Actually cp didn't have very good performance...Rsync does perform much better, now. I just realized I stupidly used the -z option. In a local to local copy. So...there's that.

Now, after a couple of failed attempts (my Banana Pi crashed, so I ran the command again, assuming it would resume the copy where I left), it finally finished. Original folder weights 705GB. Copied folder sits at 712GB. I reckon some files in the DB might have been touched or slightly modified, and rsync made a new copy preserving the old one...with a different name? Or the new one is the one with the different name?

I'd like to perform a new rsync, that basically cleans any old copies, and updating any new changes, leaving a literally exact replica of the current state in the original source. What would be the options I'd need to run on my rsync?

---

### Post by dudumomo on 2016-10-31
Hi,

Rsync is indeed recognized as the fastest tool to sync a folder / remote server. In some cases, you might want to run parallel Rsync. (If the network is too crowded, high ping, etc...)
-z will compress the files. Helpful on slow network, but will require high IO / CPU on the host. In your case, on local network, -z should not be used.

Normally, a simple rsync -av --delete is enough.

Facing some issues with it?

Thanks

---

### Post by timonoj on 2016-10-31
Seems now it's working fine...After I realized how dumb was to zip the files in a local copy, I just copied the command from a forum without checking each modifier. Copying now with -aP --delete...hopefully it shouldn't take as long as before.

---

### Post by dudumomo on 2016-11-01
You can use --verbose to get more info (size, speed, ...). It should help you assess the performance.

---

