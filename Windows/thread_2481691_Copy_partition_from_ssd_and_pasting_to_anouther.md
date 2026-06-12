---
title: "Copy partition from ssd and pasting to anouther"
date: 2022-12-06
forum: Windows
---

### Post by valeryf2 on 2022-12-06
Hello,

I bought new external ssd for dual boot.
I want to copy Win10 partition from the old SSD to the new SSD, and the i need the pc to recognize the new SSD as normal drive with Win10 installed on it.


is it possible? or i will need to install manually on the new SSD the Win10 OS and the do the file transfer?

---

### Post by oldfred on 2022-12-06
Moved to Windows sub-forum since Windows issue.

Do not know Windows.
If UEFI, you must copy entire drive as every gpt partition,partition table & backup partition table must all match.
Will new drive totally replace old drive or will use use both. You cannot have duplicate UUIDs.
Is new drive same size in sectors or larger?

---

### Post by valeryf2 on 2022-12-06
> **oldfred said:**
> Moved to Windows sub-forum since Windows issue.

Do not know Windows.
If UEFI, you must copy entire drive as every gpt partition,partition table & backup partition table must all match.
Will new drive totally replace old drive or will use use both. You cannot have duplicate UUIDs.
Is new drive same size in sectors or larger?

the new one will be booted from to UEFI system (win10) and will used as first booting option but only whe it pluged.
the new drive is 500GB the old partition is 200 GB

---

### Post by TheFu on 2022-12-06
> **valeryf2 said:**
> Hello,

I bought new external ssd for dual boot.
I want to copy Win10 partition from the old SSD to the new SSD, and the i need the pc to recognize the new SSD as normal drive with Win10 installed on it.


is it possible? or i will need to install manually on the new SSD the Win10 OS and the do the file transfer?

Best to ask MS-Windows questions on MS-Windows forums.  Different storage devices have different native block sizes which could be an issue if they aren't aligned the same.  It is more of an issue for HDDs, since blocks are very important for performance.  Misaligned blocks on HDDs can cause a 20-30% performance reduction. I can't imagine that being important with any SSD. They are so fast, even SATA SSDs.

Anyway, when you ask this question on an MS-Windows forum, be certain to list the exact SSD devices so someone can look up the block sizes.

Use MS-Windows tools when dealing with MS-Windows stuff and file systems.
Use Linux tools when dealing with Linux stuff and file systems.
Never forget those two rules.

---

### Post by oldfred on 2022-12-06
You say when plugged in.
Windows does not boot from removable devices. It is licensed to one system only & checks if USB boot.

---

### Post by mIk3_08 on 2022-12-07
> **valeryf2 said:**
> Hello,

I bought new external ssd for dual boot.
I want to copy Win10 partition from the old SSD to the new SSD, and the i need the pc to recognize the new SSD as normal drive with Win10 installed on it.

is it possible? or i will need to install manually on the new SSD the Win10 OS and the do the file transfer?
I prefer to clone drives. copy and paste will not work. Cloning will use your new ssd same as your old ssd. Regards and cheers

---

### Post by VMC on 2022-12-07
Yes, and you can clone that drive using free version of [Macrium]("https://www.macrium.com/reflectfree")

---

### Post by mIk3_08 on 2022-12-08
So far the tool I use for cloning is the clonezilla. Many says its hard to use but if you carefully read the instructions and read the steps you are into for me, it is so easy then. The performance is magnificent. Speed, can reach to 5.5 Gig up per minutes and its already better fast to me. But if you hesitate of using it. There are a lot of tools you can used. Just search around the internet. You'll see a lot. Regards and cheers.

---

