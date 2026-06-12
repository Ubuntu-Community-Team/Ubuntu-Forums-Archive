---
title: "Editing Sources List"
date: 2005-06-13
forum: Repositories &amp; Backports
---

### Post by manofsteel on 2005-06-13
Ok, I have no idea on how to add other repositories to my list  ](*,)  is there any way anyone can show me step by step?

---

### Post by N'Jal on 2005-06-13
1) open the program terminal
2) type "sudo gedit /etc/apt/sources.list
3) Enter your user password

At this point Gedit will open up showing you the apt repository list, lines that begin with the hash (#) sign are commented out lines and ignored by apt. Every line that has a deb in it means its a binary program repository. Every line with deb-src is a source repo these allow you to edit or tweak the programs before they are installed.

Look for a commented out line saying that below are the universe and multiverse repo's and remove the # sign and space so it looks like this

#Universe & Multiverse
deb [http://www.etcetcetc](http://www.etcetcetc)
deb-src [http://www.etcetcetc](http://www.etcetcetc)

Or the like, save and exit then your done

---

### Post by Xian on 2005-06-13
Read the How-To at the Wiki: [Adding Repositories to Apt](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto)

---

### Post by manofsteel on 2005-06-13
Thank you both very much, been scratching my head over this one, and didnt want to mess the system up, didnt know it was so easy. thanks again.

---

