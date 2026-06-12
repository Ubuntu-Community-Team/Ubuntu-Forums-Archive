---
title: "Files &amp; Folders Lens."
date: 2012-02-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by philinux on 2012-02-06
Just noticed something here. If you open the files and folder lens and click on a folder that is empty nothing happens. I would expect it to still open the folder even though it has no contents.

Anyone else expect this behaviour?

---

### Post by ibrahimtawbe on 2012-02-06
No , I clicked it and it open nautilus  - no contents of course

---

### Post by Gourgi on 2012-02-06
> **philinux said:**
> Just noticed something here. If you open the files and folder lens and click on a folder that is empty nothing happens. I would expect it to still open the folder even though it has no contents.

Anyone else expect this behaviour?

i can confirm this behaviour

---

### Post by mc4man on 2012-02-06
Can't see that here at all, plus - 
The behavior I've always seen is that folders aren't shown in the files lens until a file inside that folder has been opened. Easy to test - create a new, empty folder, open it in nautilus, then ck. the file lens

I've never seen it shown ..

If taking a folder that is shown in the lens & then emptying it out,  it will continue be shown &  be opened from the lens

---

### Post by philinux on 2012-02-06
> **mc4man said:**
> Can't see that here at all, plus - 
The behavior I've always seen is that folders aren't shown in the files lens until a file inside that folder has been opened. Easy to test - create a new, empty folder, open it in nautilus, then ck. the file lens

I've never seen it shown ..

If taking a folder that is shown in the lens & then emptying it out,  it will continue be shown &  be opened from the lens

Mine is vanilla install of alpha 2. Is this lens all the default home folders are shown. Most have no files in. Clicking on these does nothing and dash disappears.

---

### Post by effenberg0x0 on 2012-02-06
> **philinux said:**
> Mine is vanilla install of alpha 2. Is this lens all the default home folders are shown. Most have no files in. Clicking on these does nothing and dash disappears.

Philinux, I have managed to get what you described, but only for folders which I have no permission/ownership. Could that be the case there?

Regards,
Effenberg

---

### Post by mc4man on 2012-02-06
> **philinux said:**
> Mine is vanilla install of alpha 2. Is this lens all the default home folders are shown. Most have no files in. Clicking on these does nothing and dash disappears.

THat I can see, the 'Default' supplied folders won't open (Documents, Pictures, Music, Videos. Downloads) if empty

Actually here with an A2 updated the files lens won't open any of those folders at all, whether empty or not, though can files in them if there are any. 

However if I've opened a file in one of those folder = 
In that case they are then listed twice, the top row never works, 2nd listed instance does


(Hard to describe - in screen you'll see Documents listed twice - the top one does nothing, the 2nd instance works, same for all of the Default folders
It's like the top row are just 'dummies'

---

### Post by narkosen on 2012-02-06
I can confirm this behaviour in Alpha 2.
Right click on the Dash -> Files & Folders.  This displays the lens view with my home folders. Clicking on any of the default folders (empty or not) closes the lens view and does not open nautilus to display the folder contents.
I also have a second Documents folder which does work correctly!  This appeared after making some test documents in empty folders to check this behaviour.:confused:

---

### Post by philinux on 2012-02-06
Not at my pc but looks like big report needed.

---

### Post by mc4man on 2012-02-06
> **philinux said:**
> Not at my pc but looks like big report needed.

So if you open Documents & open a file inside you don't then see 2 Document Folders in the file lens?

If not do you have the latest lens package 5.2.0-0ubuntu1

---

### Post by PaulW2U on 2012-02-06
> **philinux said:**
> Just noticed something here. If you open the files and folder lens and click on a folder that is empty nothing happens. I would expect it to still open the folder even though it has no contents.


Yes, I'm seeing that too.

Additionally, if a folder contains other folders but no files then again nothing happens. Nautilus only opens for me when a folder contains just files or a mixture of files and folders.

Here's the bug report - [https://bugs.launchpad.net/unity-lens-files/+bug/921665](https://bugs.launchpad.net/unity-lens-files/+bug/921665)

---

### Post by philinux on 2012-02-07
> **PaulW2U said:**
> Yes, I'm seeing that too.

Additionally, if a folder contains other folders but no files then again nothing happens. Nautilus only opens for me when a folder contains just files or a mixture of files and folders.

Here's the bug report - [https://bugs.launchpad.net/unity-lens-files/+bug/921665](https://bugs.launchpad.net/unity-lens-files/+bug/921665)

Cheers for the link I've subscribed to that and ticked affects me.

---

