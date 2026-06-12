---
title: "Setting up a Private cloud via. UEC"
date: 2011-03-02
forum: Ubuntu Cloud and Juju
---

### Post by me_sujeet84 on 2011-03-02
[SIZE=2][FONT=Verdana]Hi,
     I am new to Cloud Computing World and very passionate to learn it. To start with, I did some research on net and gathered some theoretical background about it. More specifically, I am currently concentrating on setting up a private cloud using UEC referring: [/FONT][/SIZE][SIZE=2][FONT=Verdana]https://help.ubuntu.com/community/UEC/PackageInstall (Link 1) and further I am planning to upgrade this private cloud to  a Hybrid Cloud. I guess by the time I complete this set up process, I would get good starting base and confidence in Cloud world. 

[/FONT][/SIZE][SIZE=2][FONT=Verdana]As UEC is powered by Eucalyptus, I found private cloud installation process also at Eucalyptus portal:
[http://open.eucalyptus.com/wiki/installing-eucalyptus-source-16](http://open.eucalyptus.com/wiki/installing-eucalyptus-source-16) (Link 2)

I wanted to know that considering my plans to set up a hybrid cloud after setting up a private cloud first...  whether installing private cloud using UEC via. Link 1 would be better or I should follow steps in Link 2. 

Any help would be highly appreciated.
[/FONT][/SIZE]

---

### Post by raymdt on 2011-03-02
just use Link-1. UEC is easier to install than eucalyptus from source.

---

### Post by me_sujeet84 on 2011-03-04
Thanks raymdt.

I have one more query. I am setting up a private UEC and then I wish to make an interface to a public cloud Amazon EC2. So basically, I wish to use this public cloud on demand basis. If I need more resource that I have in my private cloud, I will get some from public cloud and vice versa..... Can you suggest any existing model, refernces where such kind of interfacing is explained or used?

Thanks,
Sujeet

---

### Post by Rusty au Lait on 2011-03-04
Take a look here: [https://help.ubuntu.com/community/EC2StartersGuide](https://help.ubuntu.com/community/EC2StartersGuide)

---

### Post by raymdt on 2011-03-05
me_sujeet84,
you can use the amazon virtual private cloud to extend your private cloud infrastructur.
Just look at this 
[http://aws.amazon.com/vpc/](http://aws.amazon.com/vpc/)

---

