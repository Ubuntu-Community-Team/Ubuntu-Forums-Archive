---
title: "Locking website photos"
date: 2005-04-13
forum: The Cafe
---

### Post by Jason-X on 2005-04-13
Hi All

Does anybody know of a way to protect photos on a webpage? Basically so that you can't right-click and save the photo to your hardrive.

Will it just be a bit of code or is it a bit more complicated than that?

It's for a charity site I'm doing and they really want this to work.

Thanks
Jason

---

### Post by dataw0lf on 2005-04-13
You can prevent hot linking, but you can't fully protect against straight up downloads.  Reference this [site](http://apache-server.com/tutorials/ATimage-theft.html) for more information.

---

### Post by localzuk on 2005-04-13
You can't really do this - because if the image is displayed in the webpage then it has been downloaded to the local machine for viewing. You could try some javascript (look for right click disable javascript in google) to stop right clicks, but this can be disabled by disabling javascript.

So your best bet is to put some sort of watermark on the files, so they are of no use to anyone if they copy them.

---

### Post by Jason-X on 2005-04-13
Thanks for the quick responses :smile: 

I tried some java-script to disable the right-click. It worked in Firefox, but suprise, suprise it did not work in IE. I know what your saying about the image already downloaded to the drive if the browser is displaying it. I've trying to explain this to the person I am doing it for :roll: .

I checked out the link dataw0lf posted. I take it you need your own server for this sort of thing to work?

Cheers Jason

---

### Post by dataw0lf on 2005-04-13
Correct. Those are Apache configurable values.

---

### Post by jdong on 2005-04-13
Put on a license agreement :)


"You may only view this picture if you position your head such that your left eye forms a pi/4 radian angle with respect to the magnetic field coming from your monitor. Violators will be prosecuted and subject to 6 months of a Microsoft OS"

---

