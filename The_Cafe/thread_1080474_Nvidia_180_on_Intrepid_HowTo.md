---
title: "Nvidia 180 on Intrepid HowTo"
date: 2009-02-25
forum: The Cafe
---

### Post by tulambin on 2009-02-25
Just wanted to comment on my experience w/ installing the nvidia dvr that is downloaded from Nvidia Website.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

I installed the IA32 version not the IA64 so heads up!!

System Details
Intrepid install HP w/ onboard Nvidia GeForce 6150 running Repos Nvidia Dvr 177
Installed new Nvidia GeForce 260 card w/ Reops Dvr 177
Wanted to update to Newest Nvidia 180.29 Dvr not the 180.35 Beta


I first read a thread (Nvidia 180.xx Rocks!!!) that explains all the commands that you should do to install the dvr which I remember from long ago but just forgot. I was currently running the Repos Nvidia Dvr 177 so I followed the forum post and It wouldn't load the Kernel Modules cause I got an error when trying to boot in to GDM.

So I searched and found that I should have removed all the nvidia references in Synaptic and I mean ALL!!!!

So go to synaptic and press Ctl+f in brings up the search then just type in nvidia and remove all the references to nvidia like
nvidia-177-kernel-source
nvidia-180" "
nvidia-173" " etc....

also

nvidia-177-modaliases etc....

nvidia-glx-177 etc.... Removing all these will remove other things so just do it....!!!!

After you remove everything in Synaptic perform the commands to install the nvidia downlded dvr

Real Quick

1. Press Ctl+Alt+F1
2. type user name and password.
3. type $ sudo /etc/init.d/gdm stop It'll say [OK] and the edge of your screen
4. I downlded the Nvidia Dvr To /home/username/Downlds dir on my system.
commands: $cd /home/username/Downlds
$sudo sh ./NV press tab to autocomplete
answer and read all the Questions so say Yes to all and don't forget to chose to allow x.org to be auto configed!!!
5. $sudo reboot. and It worked beautifully.

So thats how it worked on my system. I'm no expert but feel free to ask questions if something goes wrong. I'm sure someone may have the answer. It's Ubuntu forum and thats how we role as ubuntu users helping others.



If at first you don't succeed skydiving is not for you!!!!

---

### Post by tulambin on 2009-02-27
I am currently running Nvidia Dvr 180.35 and It works great!!! 
I installed it by downlding it and switching to tty1 and performing the said commands.

Just a heads up!!!!

---

### Post by ktat on 2009-03-05
Thanks, this worked a treat for me! Now I can use desktop effects!

For others that may have been experiencing similar frustration with not being able to use this feature - despite having a 512Mb graphics card, I'm using a **Geforce 9400 GT** video card with **Hardy Heron** OS.

I downloaded the [COLOR="Red"]NVIDIA-Linux-x86_64-180.29-pkg2[/COLOR] driver and installed it as described above - except [COLOR="Red"]I did not have to remove any files with synaptic[/COLOR] - in fact, the 1st time through I did and the process didn't work so I reinstalled the removed file and tried again - all good :)

---

