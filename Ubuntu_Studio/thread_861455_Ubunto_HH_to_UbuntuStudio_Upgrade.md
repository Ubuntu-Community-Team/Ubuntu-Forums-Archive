---
title: "Ubunto HH to UbuntuStudio Upgrade ???"
date: 2008-07-16
forum: Ubuntu Studio
---

### Post by whodatpat on 2008-07-16
I am a super nubie.  I just loaded Ubuntu HH to an old laptop.  (My very first Linux Experience.)  I have added Audacity but it is fairly limited.  I'd like to turn this thing into a laptop studio based 100% on freeware.  UbuntuStudio is a DVD iso, and I dont have a DVD for this laptop.  I saw a thread where an older version of Ubuntu GG could be "upgraded" to Studio GG  by entering some code in the terminal.  Does such an upgrade exist for HH?  Is there a HUGE pitfall i am heading for?  Will they find life on Mars?
Patrick

---

### Post by Kaneda187 on 2008-07-16
Good job! 100% freeware I love it!! as for your problem, im sure ther is a terminal command to do the upgrade(im a bit of a noob at this stuff too so i cant help you ther:( 
If you got your hands on a external DVD drive you could install it off that, just a thought good going with the freeware thing:) 

If any of this post helped dont forget to click the thank button on the bottom right! good luck! oh and welcome to the forum if your new! this place rocks!:guitar:

---

### Post by snowpine on 2008-07-16
> **whodatpat said:**
> I am a super nubie.  I just loaded Ubuntu HH to an old laptop.  (My very first Linux Experience.)  I have added Audacity but it is fairly limited.  I'd like to turn this thing into a laptop studio based 100% on freeware.  UbuntuStudio is a DVD iso, and I dont have a DVD for this laptop.  I saw a thread where an older version of Ubuntu GG could be "upgraded" to Studio GG  by entering some code in the terminal.  Does such an upgrade exist for HH?  Is there a HUGE pitfall i am heading for?  Will they find life on Mars?
Patrick

Hi and welcome to the forums! Ubuntu Studio is great--I recently installed it and am just scratching the surface of what is possible. 

All you need to do to install it to your existing Ubuntu is open a terminal window and enter the following lines, one at a time (and entering your password when prompted):

```

sudo apt-get update
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins linux-rt

```

That will install all of the audio software and the real time (rt) kernel, which helps your system run smoothly for audio production. If you want the video and graphics tools as well, just add 'sudo apt-get install ubuntustudio-video ubuntustudio-graphics' and if you want the dark ubuntu studio theme 'sudo apt-get install ubuntustudio-desktop'.

Good luck!

---

### Post by lapcat66 on 2008-07-16
You can also install Ubuntu Studio through the Synaptic (top menu: System, Administration, Synaptic Package Manager).  Click to install the linux-rt package and ubuntustudio packages.

---

### Post by Capoeira on 2008-07-16
no thats not all, perhaps you have to do some little configuration too. read all about it on the official site here: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by lapcat66 on 2008-07-16
Good point.  I think the real-time support settings are handled under 'studio controls' in Hardy.

---

### Post by plus on 2008-07-22
> **Capoeira said:**
> no thats not all, perhaps you have to do some little configuration too. read all about it on the official site here: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

hallo i dont know many things about ubuntu and have many questions.
i try to follow the above guide but cant figure out if my soundcard is supported.
[http://img392.imageshack.us/my.php?image=screenshotxc1.png](http://img392.imageshack.us/my.php?image=screenshotxc1.png)

thanks for any help.

---

### Post by Capoeira on 2008-11-05
> **plus said:**
> hallo i dont know many things about ubuntu and have many questions.
i try to follow the above guide but cant figure out if my soundcard is supported.
[http://img392.imageshack.us/my.php?image=screenshotxc1.png](http://img392.imageshack.us/my.php?image=screenshotxc1.png)

thanks for any help.

well, if it is working, it is supported i guess

Don't forget the following, wich is the most important for realtime:
(took me some time, until i realized that i have to include my user to audio-Group)

> All you have to do for this is give your audio group permissions to access the rtprio, nice, and memlock limits. To do this, you just need to run these commands, which will add some lines to the file /etc/security/limits.conf:

 sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'

The memlock line determines how much of your memory can be locked by audio processes. Some recommend setting this as half of your total memory (in K). See Florian Paul Schmidt's page.

In Intrepid, you have to create a user groupe named "audio" and add your user name (and other oser users of the workstation if needed) to this group. You can do that very simply in "System / Administration / User Group". Restart the workstation and it is ok.

And that is it! You're all set for real-time access! 

---

### Post by plus on 2008-12-01
ok,thanks for the reply,sorry if i asked something simple,but i asked because i wasnt sure and i think it is better to ask something when i am about to make such serious changes and maybe something could not be right or  proper.

---

### Post by markbuntu on 2008-12-04
Just getting UbuntuStudio is easy, setting it up can be easy too if you know what to do.You should read the jack section here and read all the links about setting up jack, etc.:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

