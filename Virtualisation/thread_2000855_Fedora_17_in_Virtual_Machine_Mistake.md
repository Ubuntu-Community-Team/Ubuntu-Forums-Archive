---
title: "Fedora 17 in Virtual Machine Mistake"
date: 2012-06-10
forum: Virtualisation
---

### Post by Bouvet on 2012-06-10
Hello.):P
I am wanting to install **Fedora 17 **in Virtual Box and I have run into a snag. I have correctly installed the iso and everything works but I cannot 'register' myself. 
I *cannot get to the attached screen shots*. Every time I boot up, I am prompted with the same screen of "Try" and  "Hard drive". What have I done wrong?

---

### Post by CharlesA on 2012-06-10
Umount the ISO and then have it boot from the hard drive.

---

### Post by Curtis6767 on 2012-06-10
If it was me, I'd just delete your current Fedora install and start over.

This time boot from the ISO rather than trying to install from a CD/DVD.

Once you go through the initial setup steps and you get back to the VB main menu, then highlight Fedora.

Then go to Settings/Storage and look at Storage Tree.

You should see an image of a CD and next to it it should say Empty.

Click on Empty .

Attributes will fade in. 

Click on the CD image .

A drop down menu will appear.

Look for Fedora ISO in the list and if it's there, click on it. And you're done.

If you don't see the Fedora ISO in the list, then click on Choose Virtual CD/DVD disk file.

From there navigate to where your ISO is and select it. And now you're really done.

Click Fedora in the main VB menu and VB will find and load the Fedora ISO.

If something goes wrong again, just repeat the steps until you get it right. That's the nice thing about a virtual install.

Hope this helps.

---

### Post by Bouvet on 2012-06-10
In case you didn't know, I'm still very wet behind the ears with Linux.

I'm going to try the above tips if I can figure out what to do. 

Thanks!

---

### Post by Bouvet on 2012-06-10
Thanks Curtis and Charles: SOLVED

I really just poked around like you two suggested and clicked on the
CD image and removed it, then rebooted and I was prompted. 
So glad you two answered my plea. THANKS!

---

