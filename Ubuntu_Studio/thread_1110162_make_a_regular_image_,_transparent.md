---
title: "make a regular image , transparent"
date: 2009-03-29
forum: Ubuntu Studio
---

### Post by chriskin on 2009-03-29
might not be the best place to ask but, do you know if there is a way to make a part of a regular png transparent?
for example everything that is white in the image to turn transparent

any help will be appreciated  :)

:popcorn:

---

### Post by sekinto on 2009-03-29
1.) Open image
2.) Go to the channels pallet and see if it has an Alpha channel (if it does skip to 4)
3.) Layer > Transparency > Add Alpha Channel
4.) Click the Select By Color tool (hand pointing to a rectangle with blue, red and green squares) [shift+o]
5.) In the tool's options set the threshold to 0
6.) Click on a white spot
7.) Edit > Clear [delete]
8.) Select > None [control+shift+a]
9.) Check your results, if there is still some residue around the image then press control+z (edit > undo) until you get back to where you after step 4 and increase the threshold slightly until you get the result you want
10.) Save result

---

### Post by chriskin on 2009-03-29
> **sekinto said:**
> 1.) Open image
2.) Go to the channels pallet and see if it has an Alpha channel (if it does skip to 4)
3.) Layer > Transparency > Add Alpha Channel
4.) Click the Select By Color tool (hand pointing to a rectangle with blue, red and green squares) [shift+o]
5.) In the tool's options set the threshold to 0
6.) Click on a white spot
7.) Edit > Clear [delete]
8.) Select > None [control+shift+a]
9.) Check your results, if there is still some residue around the image then press control+z (edit > undo) until you get back to where you after step 4 and increase the threshold slightly until you get the result you want
10.) Save result


i will check this first thing tomorrow
thank you :)

---

### Post by Stochastic on 2009-03-29
Just to point out the obvious for anyone who might not understand: sekinto's advice is for gimp.

---

### Post by chriskin on 2009-03-30
edit : i made it :)
thank you again :)

---

