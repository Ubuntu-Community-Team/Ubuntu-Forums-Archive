---
title: "Cloud Newbie Getting Started"
date: 2011-06-02
forum: Ubuntu Cloud and Juju
---

### Post by ptmuldoon on 2011-06-02
I'm doing some google searches, but its best to ask as well as I learn more...

Currently, I'm using Ubuntu Server at home to store all of my various media; movies, music, family photo's, etc.   And I can access that information remotely via shared/mapped drives.

But I'm interest now in taking that 'next step', and setting up a cloud, but am unsure exactly how its done, and if i'll benefit much from it or not.

Thus some questions as I continue the learning process.

1.  Can I setup a cloud on a existing Ubuntu Server setup? 

2.  Are there any good, accurate how-to's are setting that up?  Does this tutorial apply? [https://help.ubuntu.com/community/UEC/](https://help.ubuntu.com/community/UEC/)

3.  After the cloud is installed and setup on your server, can any device connect to it?  Can I access it via a droid smart phone or similar?  Can a window's machine connect to it?

I have lots of other questions, but thats some of the early one's as i continue searching around.

Thanks
PT

---

### Post by diablofatt on 2011-06-04
I would like some info on this as-well. *Bump*

---

### Post by kim0 on 2011-06-04
Hi,
Trying to answer your questions:
1- Well you can setup UEC on an existing server with
[https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)
However UEC needs two physical servers as a minimum

2- Yes that link is updated. If you find any inaccuracies, please step in to help fix them

3- Hmm, UEC (or openstack) clouds really focus on offering you virtual machines (instances) .. not really "storage" for your photos that you can access via phone ...etc .. Of course once you get the instances, you can setup dropbox on them or use them for storage and so on, but that's not the primary target. For the use case you're mentioning, I wouldn't you setup your own home cloud
Instead check out Ubuntu One
[https://one.ubuntu.com/](https://one.ubuntu.com/)

---

