---
title: "Installing Matlab with wine error code 9009"
date: 2013-05-05
forum: Virtualisation
---

### Post by umsamark on 2013-05-05
I am trying to install MATLABR2012a with wine and I came up with the error (see attached image).

"Command line returend OS error code '9009' for command."


When I install matlab it asks for a  path for destination folder which is default:
C:\Program Files\MATLAB\R2010a\

I thought this was weird because it looks like a windows directory, but it seems as though wine is installing it Z:\home\kasun\.wine\C:\Program Files\MATLAB\R2010a\ to make it look like windows for MATLAB installation. (note: "kasun" is my username). So I let it install and I got the above error.

I have a feeling it might have to do with the way i set up my  partitions, if you look at the attached image, sda1 is my windows boot loader,  sda2 is windows, and sda3 is windows recovery. My ubuntu is on the  fourth partition with and a seperate home partition sda7, sda5 is root  and sda6 is my ram.

Questions:
1. Is the error because my home is in a seperate partition from root?
I also tried installing in the path \home\MATLAB and I got the same error

Thanks

---

### Post by Cheesemill on 2013-05-06
I don't think you can use Wine to install Matlab 2012a, it doesn't appear in the list of supported applications....
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=49](http://appdb.winehq.org/objectManager.php?sClass=application&iId=49)

There is, however, a native Linux version of Matlab that you can use...
[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

---

### Post by umsamark on 2013-05-12
Sorry about the late reply. Thnks, I guess Wine wont work with my version of matlab. I will try vitrtual box see how it goes

---

