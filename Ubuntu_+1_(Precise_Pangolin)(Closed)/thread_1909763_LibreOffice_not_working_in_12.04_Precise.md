---
title: "LibreOffice not working in 12.04 Precise"
date: 2012-01-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Hazzabin on 2012-01-15
Sorry guys don't know if this the right place, and yes I do know 12.04 is less than 'Alpha'

there seems to be an issue within the package/files, so anyone that is playing with 12.04 have they come across this and any help appreciated

regards

Hazz

---

### Post by sffvba[e0rt on 2012-01-15
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*


404

---

### Post by cap10Ibraim on 2012-01-16
works fine here , are you updating your system , because > it's "more" than alpha
and can you be more specific what's is exactly the error 
getting it ? 
or opening a document ? ... ?

---

### Post by Hazzabin on 2012-01-16
I have not been able to get the error message to come back up

Office flashes up the green bar starts to move as in starting to open then it all closes

I'll keep trying to get the error message to return

thanks

---

### Post by kaldor on 2012-01-16
All's working well here. No custom PPA's, and fairly vanilla setup.

---

### Post by cap10Ibraim on 2012-01-16
do you have a custom java (JRE) installation ?

---

### Post by Hazzabin on 2012-01-16
the only thing extra I have is cairo-dock, I am not aware of any java stuff

oops there is a 'default-jre' and 'default-jre-headless' showing as being installed when I looked in synaptic    sorry

and openjdk-6-jre-lib also and I dont no where or how they got there, there is a few others too

---

### Post by kevpan815 on 2012-01-16
> **Hazzabin said:**
> Sorry guys don't know if this the right place, and yes I do know 12.04 is less than 'Alpha'

there seems to be an issue within the package/files, so anyone that is playing with 12.04 have they come across this and any help appreciated

regards

Hazz

Actually, 12.04 is now post Alpha 1 and pre Alpha 2, which comes out in the first week in Febuary. in the future please make sure that you post all issues about Alpha's and Beta's in the Ubuntu + 1 forum. Now as to Libre Office, I am currently not having any problems with the integraded version of it that came with Alpha 1, keep in mind however that i have not installed any updates to it due to my bandwith limits and the fact that I have to use a sort of slow 3G wifi connection from my cell phone when using Ubuntu, your Alpha experience can change very quickly once you start adding updates on to the system or if you try a Nightly Build of Ubuntu, I have found that most of the time that over sized Nightly Build CD's won't even run on my two Dell's that I use for testing Ubuntu. Post Script: The reason why I like testing Prereleases of Ubuntu is the fact that unlike Microsoft where you have to be invited to test Prerelease versions of Windows on Microsoft Connect, Ubuntu lets anyone who wants to try out a Prerelease version of Ubuntu access the Prerelease download server at [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) :-)

---

### Post by kevpan815 on 2012-01-16
> **kevpan815 said:**
> Actually, 12.04 is now post Alpha 1 and pre Alpha 2, which comes out in the first week in Febuary. in the future please make sure that you post all issues about Alpha's and Beta's in the Ubuntu + 1 forum. Now as to Libre Office, I am currently not having any problems with the integraded version of it that came with Alpha 1, keep in mind however that i have not installed any updates to it due to my bandwith limits and the fact that I have to use a sort of slow 3G wifi connection from my cell phone when using Ubuntu, your Alpha experience can change very quickly once you start adding updates on to the system or if you try a Nightly Build of Ubuntu, I have found that most of the time that over sized Nightly Build CD's won't even run on my two Dell's that I use for testing Ubuntu. Post Script: The reason why I like testing Prereleases of Ubuntu is the fact that unlike Microsoft where you have to be invited to test Prerelease versions of Windows on Microsoft Connect, Ubuntu lets anyone who wants to try out a Prerelease version of Ubuntu access the Prerelease download server at [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) :-)
Update: Acccording to the post from Cariboo: Alpha 2 comes out on Febuary 2nd, 2012.

---

### Post by kevpan815 on 2012-01-16
> **kevpan815 said:**
> Update: Acccording to the post from Cariboo: Alpha 2 comes out on Febuary 2nd, 2012.

Although this is a little off topic, I forgot to mention that Febuary 2nd is Ground Hog Day here in the U.S.A. and that Algonquin, IL is not too far away from Woodstock, IL where they filmed the Movie Ground Hog Day, and that every year on Febuary 2nd they wait to see if the Ground Hog sees his shadow in Woodstock, IL, just like they do in Pensylvania.

---

### Post by Hazzabin on 2012-01-16
I've also enjoy testing, I do not have a bandwidth problem

My install of ubuntu 12.04 is 'daily'dated 09-01-2012' sorry we write our dates different

but right from the initial  install, nothing else added, Libre-office failed to start.

---

### Post by dino99 on 2012-01-16
open synaptic and purge all the related libreoffice installed packages and thier dependencies (might need to purge ubuntu-desktop too), then reinstall libreoffice & ubuntu-desktop.
Here on i386 LO is running fine.

---

### Post by Hazzabin on 2012-01-16
Thanks Dino, 
wasn't what I wanted to have to do. Though maybe the only answer, is strange because I had similar problem with Libre Office with the first install I did Ubuntu 12.04 back b4 xmas. That was a "Daily" build too

regards

Hazz

PS, Many thanks once again Dino, I had done a re-install b4, this time I went for complete removal, re-booted
installed again and bingo worked a treat

thanks mate

---

### Post by dino99 on 2012-01-16
> **Hazzabin said:**
> Thanks Dino, 
wasn't what I wanted to have to do. Though maybe the only answer, is strange because I had similar problem with Libre Office with the first install I did Ubuntu 12.04 back b4 xmas. That was a "Daily" build too

regards

Hazz

PS, Many thanks once again Dino, I had done a re-install b4, this time I went for complete removal, re-booted
installed again and bingo worked a treat

thanks mate

Yes i know, the method is rough but its my favorite when things goes wrong: fastest & easiest to repair. Glad you fixed it :)

---

### Post by philinux on 2012-01-16
I had the package errors on Friday. I left it till now. 

Anyway this worked.

```
sudo apt-get -f install
```

All fixed after that.

---

