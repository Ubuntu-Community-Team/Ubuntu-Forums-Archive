---
title: "Steghide reversal"
date: 2011-01-27
forum: Security
---

### Post by duke.tim on 2011-01-27
okay i'm wondering if it's possible to restore the original image file that you have hidden data in with steghide. The basic Idea is you have a photo using gpg sign it and then embed the signature. then remove the signature at a later time and check it with the signature. I hope another "inverse" algorithm doesn't need to be written to undo the first (if a "inverse algorithm is possible).
This assume you already have the pass phrase or that there is no pass phrase.

I already know how to retrieve the original file just want to remove the hidden data from the Image and restore it's attributes.

---

### Post by HermanAB on 2011-01-28
Hmmm, you cannot restore data that isn't there anymore, but you could run a filter to blur/sharpen the image and destroy the embedded data that way.

---

### Post by nitrogensixteen on 2011-01-29
steghide documentation reveals no function to restore the original image.
you need to review the source code to determine if it is feasible to remove the embedded data. i have a feeling it is not.

i think you should find a different solution for what you're trying to do, without restoring the original data, the signature is worthless.

---

