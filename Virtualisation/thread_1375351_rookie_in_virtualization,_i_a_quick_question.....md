---
title: "rookie in virtualization, i a quick question...."
date: 2010-01-07
forum: Virtualisation
---

### Post by phawnex on 2010-01-07
i have ubuntu 9.10 on my imac (dual booted with refit)  i was curious if i were to download and install a vm machine or vmware player or something (w.e. it may be) will i be able to access and run osx (on my native drive) at the same time as being logged in my ubuntu? sure would save a lot of time of having to log in and out of linux to access some folders and use some programs on mac osx that my linux doesnt have?

any help in this field would be greatly appreciated, as i do not like to log in and out all of the time, so if i am able to access the other OS then it would definitely make my life easier.

thanks

---

### Post by geekshlby on 2010-01-07
yessir.  it will be just another open window you can switch to :)

---

### Post by phawnex on 2010-01-07
which virtual software would you recommend that would be easiest for a newb?

---

### Post by AlexandreP on 2010-01-07
I don't know of any virtualization software that allows you to easily virtualize Mac OS.

I know it's *technically* possible, because I've already seen pirated and modified Mac OS X running as guest OS in some virtualization software (VMWare, I think) and I heard of some companies claiming they succeeded in virtualizing Mac OS X in closed test environment. But Apple won't let you install Mac OS X in a virtual machine nor boot a physically installed Mac OS X in a virtualization software, because the virtual machine is no more the original Mac.

---

### Post by phawnex on 2010-01-07
damn, it would be better if i run the virtualization on macOSX then. is it possible to run ubuntu on it without having to totally reinstall it all over again (and lose my current settings, etc?) and will the performance of the linux running on virtualization be considerably slower?

if i am stuck on having to reboot its ok, not like im doing a cold boot everytime to get into ubuntu.  

or is there a way to give my ubuntu 100% access to the mac hd, cuz it shows it on my file browser, and even lets me access it. . .. but when i click my user folder (with all music, etc inside) it has an "x" by it and when i double click on it - it says i do not have permissions to access it. does anyone know a way around this.  that would help a lot and would require less of me to have to log out nearly as often.

any advice of what i should do or think of doing would be appreciated. 

thanks guys!

---

### Post by fouadatmeh on 2010-01-08
Hello,
I believe the best solution for your case is to install ubuntu inside the VM as guest and keep the mac as the host..
As for the performance, if your cpu has VT-x then there will be very little difference in performance (except for 3d as it is still slow).. 
I am sure there is a way to move your ubuntu installation to make it as guest but i don't know how..:(

As for accessing your files from inside the VM, you can either use file sharing (called shared folders in virtualbox); or mount your hdd partition inside VM and have native access to it. I recommend the first solution as it is safer and easier.

---

### Post by phawnex on 2010-01-08
Hey thanks for the advice bro I'm going to try running the virtual machine within inside mac osx (gonna download when I get home from work)  does anyone know how to move my current installation of ubuntu into the virtual machine without having to reinstall and lose all of my settings? Or shOuld I create a new thread asking that quesion lol?

---

