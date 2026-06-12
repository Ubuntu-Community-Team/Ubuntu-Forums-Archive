---
title: "apt-get stalls"
date: 2005-06-10
forum: Repositories &amp; Backports
---

### Post by cdk on 2005-06-10
i hope this is the right place as this could be a nic issuse too.

i noticed the problem when i removed open office using synaptic.  now for some reason apt-get stalls all the time and my connection seems to be REALLY slow.  I dont know if there is any connection between the two.  But i have been having problems ever since i tried out some of those stupid unstable gdesklets.  so heres the the exact problem.

i want to install abiword.  so i used synaptic to find the program and i selected it and told clicked to install.  Now the first package will usually download right away at good speed if im lucky but almost for sure the next file will not download but rather stall.  my network monitor shows the network recieving over and over the progress of the file stays the same.  Eventually it stalls out and gives me an error about not being able to download the package.  i have a ubuntu server on the same network/internet connection and i was able to install abiword fine.  I have tried gaim and several other programs but they always stall.  i also noticed that my internet browsing has slowed too.

so if any one has any helpful info shoot

cheers,

---

### Post by Ubuntu Warrior on 2005-06-23
I am experiencing similar problems although we haven't installed the unstable apps you mention. The apt-get updates used to happen without glitch and still go pretty smoothly at home but at work we almost always have problems. The problem seems to occur when trying to download updates - the system will typically download a small percentage of the total payload and then timeout back to the shell prompt. Running sudo apt-get upgrade again seems to solve the problem. I am wondering whether our DNS lookups are too slow but surely they cannot be so slow as to timeout the file transfer process???

---

### Post by msch on 2005-06-24
i'm stalling here as well.  

i've upgraded to hoary from debian testing to get at the xorg packages.  the change over went fairly smoothly (i'm running all ubuntu packages now) but apt chokes up on every install.  i run from the command line, apt-get update && apt-get upgrade as root and i always stall out on one of the first few packages.  it also happens when i apt-get install xxx.  a simple "<ctrl> c" and rerunning the command usually results in the downloading finishing and the install completing.

i find this so unbelievably annoying that i might have to move back to debian and get at xorg another way... ](*,) 

anybody with any tips??

---

### Post by cdk on 2005-06-24
i never did figure out the problem. i spent many hours but in the end i found it more profitable to just reformat and install again.  It wasnt too much of a task since i installed my /home on a seperate drive.  now its all working quite well.  good luck m8s hope you find an answer.

cheers,

---

