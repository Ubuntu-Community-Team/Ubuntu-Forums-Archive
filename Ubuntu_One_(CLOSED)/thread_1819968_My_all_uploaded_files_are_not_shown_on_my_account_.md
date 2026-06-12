---
title: "My all uploaded files are not shown on my account on ubuntu one website!!!"
date: 2011-08-07
forum: Ubuntu One (CLOSED)
---

### Post by pavelexpertov on 2011-08-07
I used ubuntu 11.04 to upload files from my laptop to the website. I installed lubuntu 11.04 on a desktop and when i tried to download the files that i uploaded from my laptop, I could not see them!!!!! I have checked if i am logged in a right account, but that's not the case. Please help me to find these files....

---

### Post by duanedesign on 2011-08-11
> **pavelexpertov said:**
> I used ubuntu 11.04 to upload files from my laptop to the website. I installed lubuntu 11.04 on a desktop and when i tried to download the files that i uploaded from my laptop, I could not see them!!!!! I have checked if i am logged in a right account, but that's not the case. Please help me to find these files....


programs/services like Drop Box and Ubuntu One are file sync applications. Meaning they mirror on all your devices (and the cloud) changes you make locally. So if you are going to remove your OS or reinstall make sure that you disconnect or quit the file sync service before you begin removing/reinstalling things. With Ubuntu One you want to make sure you do not copy over from your old computer ~/.local/share/ubuntuone . The danger of copying ~/.local/share/ubuntuone from a backup to your new computer and then setting up Ubuntu One is that your files will be deleted. The Ubuntu One client will look for information about your local files in ~/.local/share/ubuntuone, see that there were files on the system and see that those folders are empty. 

Understanding that a lot of people would like to use Ubuntu One as a backup their is going to be integration between Deja Dup and Ubuntu One in the next Ubuntu release (Ubuntu 11.10). You will be able to upload a folder to your cloud storage and that folder will not be sync between devices. So the contents will be safe from accidental deletions.

@pavelexpertov please fill out [this form ]("https://one.ubuntu.com/help/contact/")and include the name of the folder you would like to try and recover and we can attempt to recover this for you.

---

