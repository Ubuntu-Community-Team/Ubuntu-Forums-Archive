---
title: "Easy Ownership and file/sharing"
date: 2008-07-26
forum: Ubuntu Brainstorm
---

### Post by Neovos on 2008-07-26
I think Linux's greatest strength as a os is also one of it's greatest weaknesses as a user environment: file ownership and access to files. I think there should be some sort of way to use sudoer privileges, or passwords, or a guest account with a logging function to allow non-owners access to files. For example, in an ideal world, every computer has linux, and I have multiple external drives which I want to bring to work, school, and home. Instead of having to change ownership every time and specify all the little details, I want ubuntu to detect on plug in that the drive is of a different user then the one thats logged on. Once this happens, a screen pops up giving me the option to do a couple things:

1)Keep all other users files locked but allow me to create new folders and files. All I want to do here is just use the drive, not mess with other peoples stuff. 

2)Access the files and folders on the drive but not delete or edit them.

3)Access and edit all files and folders on the drive allowing me (the user thats logged on) full access and rights. This would require a gksudo prompt and that logged on user needs sudoer rights. 

then we could have a little check box that says "remember my preference for this drive" which can be determined by uuid.

My point here is that someone with sudoer rights can do this anyway, it's just cumbersome. So to the advanced linux users, its a nuisance. To the inexperience newb linux user (which a perfect version of linux should still be useful to without any security compromise) this prevents any use of this external drive and a potential switch back to windows. We want someone who's stupid at computers anyway, let alone linux, to be able to use it. Oh and this doesn't have to be for just usb drives, any new drive that gets detected, including perhaps cd's and dvds should have this popup. As it is, it's annoying to get a plug in usb to behave correctly even when it's just one user using it all the time.

edit: Another idea too is for the addition of a "Access status" for files and folders. Where files and folders can be locked with a password and possibly pre marked with one of the 3 options above. This info can be stored on the drive itself and travel with it. Obviously this can be hacked, but it's just a simple deterrent. It's more straightforward then switching the owner of a file for security, which is not security at all. Then this password can be part of that popup. So the question really becomes, to you want to have one password set by the data creator on that usb drive be the final say in it's editing/usage, or do you want any user with sudoer rights on any computer the ability to access it? Both can be done I think. Anyway, the point here is the addition of gui element to this whole process on drive detection.

---

