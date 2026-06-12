---
title: "No hibernation allowed anymore?"
date: 2008-02-19
forum: Windows
---

### Post by Zdravko on 2008-02-19
I needed to remove temporarily hyberfil.sys in order to do some partitioning under Vista. Now I want it back. The power options no longer allow me hibernating. How to fix that?
Btw, is there a big forum dedicated to Windows like this one? I feel uncomfortable posting here... :(

---

### Post by LaRoza on 2008-02-19
> **Zdravko said:**
> I needed to remove temporarily hyberfil.sys in order to do some partitioning under Vista. Now I want it back. The power options no longer allow me hibernating. How to fix that?
Btw, is there a big forum dedicated to Windows like this one? I feel uncomfortable posting here... :(

What do you mean you "removed" it? Did you delete it? Copy it elsewhere?

You can post here, many here are very familiar with Windows.

If you shrunk your Vista partition to a small size, you might not be allowed to hibernate.

---

### Post by Zdravko on 2008-02-19
Hmm, I followed the guide of someone here during shrinking of Vista's partition. I didn't delete anything manually. I disabled temporarily the virtual memory from the advanced performance settings.
Btw, there is no such option like what you described.

---

### Post by LaRoza on 2008-02-19
> **Zdravko said:**
> Hmm, I followed the guide of someone here during shrinking of Vista's partition. I didn't delete anything manually. I disabled temporarily the virtual memory from the advanced performance settings.
Btw, there is no such option like what you described.

It may be there is not enough room to enable it.

(Sorry, instructions were for XP)

I am not on Vista now, but you can move the page file to another partition or disk if it is NTFS. Do you have another partition you can use?

---

### Post by Zdravko on 2008-02-19
No, I don't have another FREE partition. Or do you want me to remove my precious Fedora?

---

### Post by LaRoza on 2008-02-19
> **Zdravko said:**
> No, I don't have another FREE partition. Or do you want me to remove my precious Fedora?

No, I don't know the size of your disks, or the size of the partitions.

What I do for dual booting:

* Shrink Vista to a small size
* Have a small Linux partition
* Have a large NTFS partition
* Have a 512 MB swap

I use the large NTFS partition for the Vista page file, and for storing all documents and files.

(This isn't my setup, but it would be what I would do for dualbooting Linux and Vista with one disk)

---

### Post by Zdravko on 2008-02-19
I have the same configuration. 45 GB are free on C:.

---

### Post by Zdravko on 2008-02-21
> **Zdravko said:**
> I have the same configuration. 45 GB are free on C:.
Bump!

---

### Post by sayakb on 2008-02-22
To enable hibernation, type this in cmd:

powercfg -h ON

---

### Post by Zdravko on 2008-02-22
I tried it. Dunno whether it works... yet...

---

### Post by sayakb on 2008-02-22
> **Zdravko said:**
> I tried it. Dunno whether it works... yet...

Tried it but dunno if it works?? I'm Confused :(
Anyway, this should work..

---

### Post by Zdravko on 2008-02-24
There is now a hibernate option during shut down window. But I haven't tried it yet.
Why are you confused?

---

### Post by Kernel Sanders on 2008-02-24
[http://www.msfn.org/board/forums.html](http://www.msfn.org/board/forums.html)

They are pretty good there :)

---

### Post by Zdravko on 2008-02-24
Nice to have a link for M$!

---

### Post by Zdravko on 2008-04-13
Now it seems that I don't have the hibernation option anymore. Where did it go? Can anyone help me?

---

### Post by Chiko2008 on 2008-04-15
> **Zdravko said:**
> Now it seems that I don't have the hibernation option anymore. Where did it go? Can anyone help me?

Do you already tried to activate the hibernate option on the control panel? Control Panel > Power Options > Hibernate (tab): (x) activate hibernation.

---

### Post by Chiko2008 on 2008-04-15
If the hibernation tab isn't available. I found this article on M$ support website: [http://support.microsoft.com/kb/255182](http://support.microsoft.com/kb/255182)

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

### Post by Zdravko on 2008-04-15
I am using Vista. There is no such option there. The article is about win2000.

---

### Post by Chiko2008 on 2008-04-15
Sorry. I didn't read all the post :(

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

