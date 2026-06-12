---
title: "[Solved] Truecrypt + Nautilus + Copying specific files = System Hangs"
date: 2009-06-10
forum: Security
---

### Post by hsiyao on 2009-06-10
Hi,
I wanted to share how I solved my problem with a hanging system using truecrypt and nautilus when copying specific files... first I try to outline how the problem occured:
- I set up an 1Tb Harddrive as encrypted partition with truecrypt and started filling it with data, not at once but more and more over time

- I copied some stuff in a temporary folder on the drive and moved it later

- After moving it to a different location on the same drive and then trying to copy it to a thumb drive or whatever the performance went down till 1mb/s, whole system hang

- investigating the problem, I found out that not truecrypt but nautilus created a system load of 100%, killing the nautilus process made everything nice again, but I had to do it everytime I tried to copy some of the files, which were moved within this drive

- investigating a bit more I saw that when using commandline to copy or midnight commander I got 20 mb/s and the drive also created much less noise, without anything hanging... same thing when copying with konqueror 

- just to give it a try I deleted all thumbnails in the ~/.thumbnail folder, because the searching sound of the drive when the performance went down anyhow brought me to the idea, that it pretty much sounded like when you access a folder e.g. with a lot of pictures for the first time

- after deleting all thumbnails nautilus again copies with maximum speed ;)

hope this can help some people, who had the same problem and thought they have to ditch truecrypt.... I still can't really say, how this problem is created but in fact now that it is solved by deleting the thumbnails, which make this more a workaround than a real solution ;)

greetings

jens.

---

