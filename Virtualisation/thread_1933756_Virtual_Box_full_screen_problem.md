---
title: "Virtual Box full screen problem"
date: 2012-03-01
forum: Virtualisation
---

### Post by GuyFawkes56 on 2012-03-01
Hi, 

I'm running Ubuntu on Virtual Box and I'm not able to expand the view to full screen. I realise there are other forums discussing this problem, and they solved it by running the VBoxGuestAdditions.iso. However, I've done this already but as soon as I updated Ubuntu the screen no longer displays at full screen (1920x1080). If anyone has any ideas it would be greatly appreciated!

---

### Post by QIII on 2012-03-01
When the kernel is updated, the guest additions need to be compiled into the kernel again.  This is not a problem with Ubuntu.  It happens with all distros when the kernels are updated.  

Simply go to the terminal and execute

```
sudo ./VBoxLinuxAdditions.run
```(or similar, depending on where the file is on your system. To make this less of a pain, I usually copy VBoxLinuxAdditions.run into my Home folder.)

You don't need to do this for all updates, only when the kernel is updated.

---

### Post by GuyFawkes56 on 2012-03-01
Thanks for replying so promptly! 

I've tried running the command, but I get an error back

sudo ./VBoxLinuxAdditions.run
sudo: ./VBoxLinuxAdditions.run: command not found

I also copied to my home directory.

any help?

---

### Post by QIII on 2012-03-01
You will need to add the complete path to the .sh file.  Mine is in my Home directory, so I can call it from there.

Hang on a minute and I'll fire up a vm and get you the file and path.


Edit:

Here you go.

Depending on your VBox version number, you will need to use something like this in the terminal IN THE VIRTUAL MACHINE, of course:

```
sudo /media/VBOXADDITIONS_4.1.8_75467/VBoxLinuxAdditions.run
```That may not be your version number, so check what you have and make changes accordingly.

(My apologies, by the way.  I did something I try not to do:  assume that you understand exactly what seems obvious to me.  I should have done a better job of explaining it in the first place.)

---

### Post by GuyFawkes56 on 2012-03-01
Thanks mate! 

That did the trick. 

I really appreciate your help :)

---

### Post by QIII on 2012-03-01
If you would, please mark this thread as solved so that the next guy with a similar issue will know there is a solution.

And you are certainly welcome!  I accept payment in unmarked bills in small denominations...

---

### Post by GuyFawkes56 on 2012-03-01
This is a really stupid question, I'm trying to mark it as solved, but how do you do it? :|

---

### Post by QIII on 2012-03-01
Not a stupid question, just stupid instructions again.  Doh!

In the upper right portion of the screen, look for "Thread Tools".  In the drop-down box, make the selection to mark as solved.

Getting late.  I'm getting even more stupid than I can account for because of my age.

---

### Post by GuyFawkes56 on 2012-03-01
Found it. Couldn't see it cause it logged me out. 

Thanks again :)

---

### Post by Bouvet on 2012-04-30
Hello All,
I was using Ubuntu 11.10 in VirtualBox.
One day it automatically prompted me to upgrade to 
Ubuntu 12 and to a new version of VB.
It works fine and all is well; except now, I cannot
get full screen! 
I followed the steps above, but alas, it didn't work.
I changed certain numbers to reflect my version of VBox.

Does anyone have any idea? I refuse to use Ubuntu now since
it is so tiny. I miss using it. Any tips?

---

### Post by dzizes on 2013-01-10
Hello, Did you managed to solve the problem?

Greets!

---

