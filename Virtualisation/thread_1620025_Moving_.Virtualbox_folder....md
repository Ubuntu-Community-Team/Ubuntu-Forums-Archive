---
title: "Moving .Virtualbox folder..."
date: 2010-11-12
forum: Virtualisation
---

### Post by roystreet on 2010-11-12
Hello,
   I have a situation that is causing some memory issues.  I have wubi installed - Working great!  I have WinXP running on (vm ose) running on a seperate .disk file.  Unfortunately, the .disk file is filling up quite quickly & I only have around 1 gb left. :(

   I have already moved the home once using "sudo sh wubi-add-virtual-disk /home..."  Now I've found that I need more room in my home.  When I try to run that great code again, it tells me that the /home already exists.  Of course, I know it does because I've done this once before.  Since I don't know of a way to fix this, my only fix that I can think of is totally moving the .Virtualbox folder to another partition.  I don't think it is, but am I able to simply copy/past that folder to the new location & simply run it from there?

    If yes, how would I tell VM to look in the new location for run from?  Do I simply update the shortcut to point to the new folder?  I have copied "cp -r" the whole folder over to the new location, but I'm not sure if I can run it.

I know I've said a lot here, but I don't even know how to move my home to another ".disk" file because that would pretty much solve this problem.

Thanks,
~roystreet

---

