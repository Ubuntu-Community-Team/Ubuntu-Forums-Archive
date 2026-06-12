---
title: "Blender does not launch"
date: 2010-03-10
forum: Ubuntu Studio
---

### Post by jogome on 2010-03-10
Hello!

I have a problem with Blender on my Ubuntu Studio 9.10, 32 bits. I can't work with Blender because it does not start. When I click on the program icon nothing happen and when I try to start it by command line I have the following message: 

"Compiled with Python version 2.6.4.
Checking for installed Python... got it!
Segmentation fault"

Do someone here have an idea how to fix this problem?

---

### Post by ecatodarcus on 2010-05-06
i have the same problem. i think that it has to do with my graphic card. i have ati radeon X1600 but i am not sure if i have installed it well.
can anyone help us with the blender?
thank you

---

### Post by 23dornot23d on 2010-05-06
Can you run any 3D software at all ...... what happens if you run Wings3D or k3dsurf

do you get an error .......

if you type glxgears in a console window does it run the animation .....

Which version of Blender are you trying to use ..... is it ..... 2.49b ......

and did you install it from Synaptic Package Manager or some other way

Mine comes up with this
Compiled with Python version 2.6.5.
Checking for installed Python... got it!

and runs ok ....

---

### Post by ecatodarcus on 2010-05-06
i just installed Wings3D but that doesn't start either.
blender is 2.49.2 version.

i have generally problems with 3d programms. for instance i cannot run google earth or a game called "heroes of newerth". i have trierd to install my graphic cards driver but i think i didn't managed to do it successfully.
Do you think that this cause me, my problem?

thank you for your answer

---

### Post by 23dornot23d on 2010-05-06
Sounds like its the graphics drivers not working fully yet .....
 - it sounds like its only working in a limited way  ...

search on .... ati radeon X1600 linux solved
______________________________________

Yes is the answer ...... to your question .... 

  After searching a little I cannot see a suitable solution ...... for this yet ....... 

Have you ever managed to get this card running before in a previous version.


Do you have a xorg.conf file

it should be in this directory

etc/X11/

if so then what is in it ..... can you copy it here ...... and post it .....

[IMG]http://i44.tinypic.com/ra6xxi.jpg[/IMG]

---

### Post by ecatodarcus on 2010-05-06
> **23dornot23d said:**
> Sounds like its the graphics drivers not working fully yet .....
 - it sounds like its only working in a limited way  ...

search on .... ati radeon X1600 linux solved
______________________________________

Yes is the answer ...... to your question .... 

  After searching a little I cannot see a suitable solution ...... for this yet ....... 

Have you ever managed to get this card running before in a previous version.


Do you have a xorg.conf file

it should be in this directory

etc/X11/

if so then what is in it ..... can you copy it here ...... and post it .....

[IMG]http://i44.tinypic.com/ra6xxi.jpg[/IMG]

i managed to get it work with 9.10 but it wasn't full operating.
now that i have 10.4, tried to install my card through this link [http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx") and i think that i have installed it correctly but the problem continues.

  how do i check if i have xorg.conf?
i tried by typing the same orders as you have done in your terminal (as seen in the photo) but i couldn't find it.
thank you for your patience  :)

---

### Post by 23dornot23d on 2010-05-06
Ok the xorg.conf may not exist yet then ..... 

if you type 
glxinfo
in a terminal do you get any output from it ...... or not ?

also try to create the xorg.conf

( this line will create a new xorg.conf file ..... )
sudo Xorg -configure
( this line just makes a copy of it ...... in case you have to delete it - I want to have a look at what it created ) 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.oldcopy

( If you reboot - and it does not work .... to get back to how it was go into console mode ..... 
and just write down / remember this command or print this off  )
rm /etc/X11/xorg.conf 

It will just remove the xorg.conf file that you created ....... but only do this if it goes wrong ,,, then reboot

then have a look for it in the directory as before and post it ..... it should appear once you run the above command in a terminal window

what kernel are you running too it should be  2.6.32-21-generic
type

uname -r

to find it out .......

---

### Post by ecatodarcus on 2010-05-07
hello if i type "glxInfo" in a terminal i get 
"name of display: :0.0
Segmentation fault"

i used the command you told me to check my kernel heads and i saw that i have 2.6.32-22-generic. I suppose that these are the last one.

I am a bit afraid to do the other things you told me. So before using them i d like to be sure that i have understood well what i have to do (english is not my mother language, i am from greece!). So first of all i type 
"sudo Xorg -configure"
in order to create a a new xorg.conf file
then i will post here what the new file has inside.then make a copy of the new file. then paste it somewhere i can easily find it.
i reboot and if everything works ok i am fine, but if i have a problem i insert the live cd, open a terminal and type 
"rm /etc/X11/xorg.conf"

i think that i have something misunderstood, sorry i am a "linux basic user"
thank you again :)

---

### Post by 23dornot23d on 2010-05-07
CHECK WHAT I FOUND OUT AT THE BOTTOM FIRST - THERE SEEMS LITTLE CHANCE OF SUCCESS HERE .......


Ok what may happen is that you could lose the graphics but with xorg.conf it only takes effect when the GDM (Gnome Display Manager) tries to start ..... therefore your boot options will still be there and show when you boot up ..... 

As this process takes effect a bit further along the start up sequence .....

So therefore you will still have your boot options - and the live CD should not be needed

You have an Option at boot that allows for recovery mode ....... if you need to use this option ..... then you can get to the console ....  thats if anything should go wrong ..... hopefully it will not and we will have a better chance to adjust things ..... a little more later on .... 

So ...... the recovery mode ....  this may also ask you some questions about setting up your graphics card etc ...... when in recovery mode .... if this happens - just exit from here ..... by pressing ESC .... or its EXIT in the menu ..... 

Then once you are at the console .... you can use the command that I gave you ..... and then reboot .....

Ok hope to see the xorg.conf file sometime ..... thats if you do this ......

There are no hard and fast rules with this ..... once I am happy with the way my computer runs I tend to stick ...... 
I am not sure that we can get yours to work any better, but if you want to continue its your choice .....

(You can always use the Live CD of course if things really went bad for any other reasons ..... but we should not need to use it  .....)

[COLOR=Red]__________________________________________________________________________________________

After reading this Thread ..... this does not look as if we are going to get any success with the ATI - X1600[/COLOR] [COLOR=Red]

[http://ubuntuforums.org/showthread.php?p=8378266](http://ubuntuforums.org/showthread.php?p=8378266)[/COLOR]   [COLOR=Red]


Its basically saying that this X1600 Card will not work on the later editions of UBUNTU .... 

[COLOR=Navy]Although the GUY does say it WORKS with 9.04 (he wrote 9.06 maybe he got mixed up he only has 2 posts on here so we cannot contact him to check) 
he was using BLENDER with the installed drivers !!!  according to what he wrote 

The user was called [/COLOR][/COLOR][JayTribe]("http://ubuntuforums.org/member.php?u=963204")[COLOR=Red]




I think by the sound of it most people are recommending a NVIDIA Card ,,,, for BLENDER ...... too .........

___________________________________________________________________________________________


[COLOR=Purple]Interesting Bug Report ..... Lamer has some ideas[/COLOR] [Bug Report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/484157")

Which leads to this .... [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_karmic_mesa&num=1") ...... But still no solution ....... 

[/COLOR]

---

