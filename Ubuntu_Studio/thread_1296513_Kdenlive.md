---
title: "Kdenlive"
date: 2009-10-20
forum: Ubuntu Studio
---

### Post by Oiolosse on 2009-10-20
I am making a slideshow from pics shot from different cameras and also some scanned pics. When kdenlive reads the pics from the folder it rotate's some of them, namely from a certain camera..however when I view the picture it looks just fine! Is there anyway to 'tell' kdenlive to leave the orientation of my pictures alone?

Thank you in advance!

---

### Post by jaygo on 2009-11-06
I believe this is due to a problem with the EXIF orientation tag in your pictures. Somehow, different cameras save it differently, so the vertical photos from one camera will look fine and the vertical photos from another camera look rotated. Image viewers handle them fine but some programs don't.

I had this issue while making a slideshow in videoporama. Photos from one friend's Canon rebel had no issues, photos from another friend's point and shoot did -- again, only with the vertical photos.

The solution for me was to open the files in digikam (if you're using ubuntu, it will install a lot of KDE stuff), select all of the problem photos, right click & batch edit > rotate > make sure "Use EXIF orientation" is checked > process or run. It will prompt you to replace each file. I had no issues and changing the EXIF orientation does not recompress your photos.

It's a hassle to setup but very fast to do.

---

