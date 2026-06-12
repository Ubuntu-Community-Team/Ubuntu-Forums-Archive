---
title: "VirtualBox copy and paste between host and guest"
date: 2009-01-27
forum: Virtualisation
---

### Post by carfield on 2009-01-27
Can virtualBox copy and paste between host and guest? I find this is not the default behaviour for my setup...

---

### Post by Dedoimedo on 2009-01-27
Hello,

Copy files? Or clipboard? Files, you can use the guest additions + shared folder feature to move data back and forth between guest and host.

Clipboard ... don't remember at the moment, will test tomorrow ...

Dedoimedo

---

### Post by HotShotDJ on 2009-01-27
> **carfield said:**
> Can virtualBox copy and paste between host and guest? I find this is not the default behaviour for my setup...Yes.  I just gave it a try.  I copied a URL from Firefox running on the Ubuntu host and was able to paste it just fine in IE running on the Windows Vista guest.

Next, I opened a document in OpenOffice on the Ubuntu host and copied a portion.  I was able to paste it to a document opened in Microsoft Word 2007 running on the Windows Vista guest.  I have the Guest Additions installed.  I don't know if they are required for this feature or not.

So, if Dedoimedo's interpretation of your question was correct OR if my interpretation of your question was correct, the answer is YES. :)

---

### Post by carfield on 2009-01-28
Oh, after I installed VirtualBox Guest additions, my copy and paste working, sorry, haven't check through.

---

### Post by balta2ar on 2010-02-05
> **carfield said:**
> Oh, after I installed VirtualBox Guest additions, my copy and paste working, sorry, haven't check through.

Is it possible to use clipboard without Xorg running? My host OS is Windows and guest OS is Ubuntu. I've turned Xorg off but copying to clipboard from console in Ubuntu is still necessary.

---

### Post by tipiglen on 2010-02-05
Helpful hint for using Guest Additions:
[http://ubuntuforums.org/showpost.php?p=8781322&postcount=12](http://ubuntuforums.org/showpost.php?p=8781322&postcount=12)

I run a 9.10 host with a 9.10 guest and an xp guest.  With guest additions installed, I can copy and paste between all three.  

Enjoy!

---

### Post by mech7 on 2010-03-18
umm I have installed win7 and ubuntu server guest... and installed guest additions but cannot paste to the console x_x

---

### Post by sahabcse on 2010-03-18
I have shared one common folder for access the file over the vbox. Let me test for the guest addition packge

---

### Post by AlexanderDGreat on 2011-09-19
You can copy and paste clipboard but NOT FILES! Be careful.

---

### Post by Elfy on 2011-09-19
Old thread closed.

---

