---
title: "sfill NTFS"
date: 2010-07-15
forum: Security
---

### Post by ndstate on 2010-07-15
Hello,

Does anyone know of sfill can be used on a NTFS file system?

Thanks for your help!

---

### Post by CharlesA on 2010-07-15
You'd probably be better off just using DBAN if you are wiping a whole drive, or something like shred if you are wiping files.

---

### Post by doogy2004 on 2010-07-15
shred can also wipe drives.  In linux everything is a file.

---

### Post by ndstate on 2010-07-15
I am just looking to overwrite free space.  I have my data on NTFS so it can be shared with windows.

---

### Post by drsmooth on 2012-02-18
You must first mount your windows partition. Then open a terminal.

In the terminal, I typed in 

> watch -n 5 df -hm



From the terminal, I copied my windows partition.
which looked something like this.

> /media/06106DD0106DdhF1

After copying the location of my windows partition. I opened a second  terminal. In the second terminal, I typed in... 

> sudo sfill

After typing in sudo sfill. 

I then added > /media/06106DD0106DdhF1 

Immediately after sudo sfill. In my case it read like this..

> sudo sfill /media/06106DD0106Dh6F1


[SIZE="3"]For those unsure which partition is their windows partition[/SIZE]

> 
type " watch -n 5 df -hm " into a terminal before mounting the windows partition. 

Take note of what appears in the terminal. Then press ctrl-c with the terminal active to exit cleanly. Do not close the terminal.... 

Now, Mount your windows partition......

Go back to the terminal...... 

Then type into the terminal " watch -n 5 df -hm " . The new partition should now show up.

[SIZE="3"]
If you would like to see the progress of sfill[/SIZE]

Open a second terminal. type the command
> watch -n 5 df -hm

It shows you sfill's  progress It updates every 5 seconds.

Sfill can take many hours.

---

### Post by nothingspecial on 2012-02-18
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

