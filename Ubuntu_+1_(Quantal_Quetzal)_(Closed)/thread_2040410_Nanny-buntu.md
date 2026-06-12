---
title: "Nanny-buntu?"
date: 2012-08-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by critin on 2012-08-11
I installed a daily image of Quantal over Precise just now and was surprised to find I was forced to encrypt the hdd.  I tried to enter blank but it wasn't accepted.  
I've not read anything about this and the image of a few weeks ago didn't have it.

A case of protecting the users from their own lack of security?  I don't like it and hope it doesn't stay default.

---

### Post by ventrical on 2012-08-11
> **critin said:**
> I installed a daily image of Quantal over Precise just now and was surprised to find I was forced to encrypt the hdd.  I tried to enter blank but it wasn't accepted.  
I've not read anything about this and the image of a few weeks ago didn't have it.

A case of protecting the users from their own lack of security?  I don't like it and hope it doesn't stay default.

What .iso were you using. Alternate, desktop ?? Alternate gives you a <yes/no> option. First Iv'e heard of this one. Must be a new bug.

---

### Post by VinDSL on 2012-08-11
> **critin said:**
> I've not read anything about this and the image of a few weeks ago didn't have it.

A case of protecting the users from their own lack of security?
News to me, too...

---

### Post by critin on 2012-08-11
Downloaded from  [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

desktop i386  Aug 10--standard download

---

### Post by Lars Noodén on 2012-08-11
I've seen that problem, too.  There are many use cases where encryption is not desirable.  There appears to be no way around it in the desktop image, but if you go with the Alternate image, you can install without encryption.

---

### Post by ELD on 2012-08-11
Make sure you submit a bug for it.

---

### Post by ventrical on 2012-08-11
> **critin said:**
> Downloaded from  [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

desktop i386  Aug 10--standard download

  I have been zsyncing that .iso for ever and have not had the above mentioned problems.

I'll try it again.!

---

### Post by ventrical on 2012-08-11
There is no bug here .

[http://www.youtube.com/watch?v=7OtY9y2F_XI&feature=youtu.be](http://www.youtube.com/watch?v=7OtY9y2F_XI&feature=youtu.be)

 @critin

are you using USB or CD?

---

### Post by critin on 2012-08-11
> **ventrical said:**
> There is no bug here .

[http://www.youtube.com/watch?v=7OtY9y2F_XI&feature=youtu.be](http://www.youtube.com/watch?v=7OtY9y2F_XI&feature=youtu.be)

 @critin

are you using USB or CD?

USB.  it was a clean install if that makes a difference.
I think I'll download again, do another clean install and see if it's still there.
Oh--I used Rufus instead of unetbootin.  It's not ever caused a problem though. still...

---

### Post by ventrical on 2012-08-11
btw .. there is a random ubiquity bug with the quantal-desktop-i386 daily.

Just found it now.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1035698](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1035698)

---

### Post by Mr. Picklesworth on 2012-08-12
This is a known bug in Ubiquity. It's reported as bug #1035167, and the encryption doesn't seem to actually happen: the page is simply shown by accident.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1035167](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1035167)

(On a related note: disk encryption from Ubiquity! I'm excited :D)

---

