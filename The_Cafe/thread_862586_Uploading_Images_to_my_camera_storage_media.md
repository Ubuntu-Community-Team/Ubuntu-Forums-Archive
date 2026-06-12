---
title: "Uploading Images to my camera storage media"
date: 2008-07-17
forum: The Cafe
---

### Post by Silvernail on 2008-07-17
I have uploaded some images to the storage media on my Canon camera.
```

SilverNail:~# ls /mnt/sdc1/dcim/100canon
ballareina.jpg  goldtree.jpg  greentree.jpg   gulls.jpg    washerwoman.jpg beggingman.jpg  greenman.jpg greenwoman.jpg  suntree.jpg

```

And can verify that they are there using 'gimp' to view them directly from the camera.
```

SilverNail:~# gimp /mnt/sdc1/dcim/100canon/*jpg

```

However I can not view them with the display function of the camera. What is the difference between a jpeg created with 'gimp' and a jpeg created by the camera. Or does the camera write  a directory or some other file that is needed to view the images.

Am I approaching this from the right direction?
Thanks for any help/
Dave

---

### Post by FuturePilot on 2008-07-17
I'm guessing that most cameras must write some metadata to the file that it reads when loading the picture and recognizes that it was taken with that camera. Once you modify an image that metadata must get erased and then the camera does not recognize that image as one of its own as it seems most cameras cannot display an image if it was modified or taken with a different camera. At least that's been my experience. I've tried to put a picture on my camera that was taken with a different camera and it would not display it.

---

### Post by Silvernail on 2008-07-17
OK,,,,,,,,,,thanks for sharing the information.

I guess if I want to show my art work to this chick  she is going to have to get a laptop to view the flash drive.

---

### Post by freebeer on 2008-07-17
Just invite her back to your place to view your etchings.  :D

---

