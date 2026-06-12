---
title: "Downgrade from 64 bit to 32 bit Ubuntu?"
date: 2011-08-06
forum: System76 Support
---

### Post by azion1995 on 2011-08-06
I'd like to downgrade my system from 64 bit Ubuntu to 32 bit (various reasons). 2 questions:

1) Does 32 bit Ubuntu support 4 GB of RAM?

2) How should I do this? Just back everything up, do it w/a stock 32 bit Ubuntu CD, then restore, and finally add the System76 repository?

Of course, if I could convince a 32 bit Second Life client to play streaming audio on 64 bit Ubuntu, I wouldn't need to do this. But that's been a long, and unsuccessful, battle.

Thx,
-Z

---

### Post by Noah0504 on 2011-08-07
Ubuntu 10.04 and above do support 4GB+ when using the 32-bit version.  They detect this and install the PAE kernel which allows for all of the memory to be used.

I'm not sure you can exactly downgrade any other way than just reinstalling.  I would back up what you need and then reinstall.  Also, there may be some tools that will also help you backup your settings.  Just run a search for them.  After you're done installing, go ahead and install the System76 driver, launch it and select restore.  You can go to this page to see the details for that: [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

---

### Post by pqwoerituytrueiwoq on 2011-08-08
you can always dual boot 64bit/32bit

---

### Post by psusi on 2011-08-08
Yes and yes.

---

### Post by blueridgedog on 2011-08-09
Out of curiosity, what are your reasons for the downgrade?

---

### Post by azion1995 on 2011-08-09
> **blueridgedog said:**
> Out of curiosity, what are your reasons for the downgrade?

I really *don't* want to downgrade. But I've had precisely zero luck getting streaming audio to work w/a 32 bit Second Life viewer under 64 bit Ubuntu. I've tried ie32-libs, getlibs, you name it- nothing works.

This means that I'm limited to Imprudence- which isn't a 2.x viewer- or Snowglobe- which stinks- if I want streaming audio in SL. And, since I'm a SL musician, I can't very well do w/o streaming audio, can I?

Has anyone else had luck getting streaming audio working in SL in a 32 bit viewer on a Ratel Ultra system running 64 bit Ubuntu? B/c, if I can get that working while waiting for more true 64 bit options, that would be ideal.

Thx,
-Z

---

### Post by dBuster on 2011-12-02
Reviving this thread! 

I am currently running 10.04.02 LTS 64bit and when the next LTS comes out next year I am seriously looking at going to a 32bit install instead. 

Reasons for wanting to do such, well, to put it bluntly, flash and the websites that require it now a days.  I used to have no problems with flash and certain websites and now I can't get things to run.  Snapfish photo sharing site for example, I can not use the bulk uploader or create a project since flash is a bust.  However on my wife's 32bit netbook 10.04.02 install I have no problems.  That is just one example or my reasons...  There are more...

So with that in mind, back to the original question, back up data?  I have my home on a separate partition from the main install would I even need to do anything but a fresh install of a 32 bit version?  I know the software I have installed will more than likely all need to be re-installed with the corresponding 32bit versions I am sure.  

Any tips, insights, recommendations to make this a smooth transition.  I am starting to research this far enough in advance.

Oh and by the way, windows is a dirty word in my household as there are no windows computers not even a dual boot option...  So running windows for these things is out of the question.

---

### Post by isantop on 2011-12-02
Just reinstall the 32-bit version.

That said, there have been some awesome changes in Ubuntu in regards to 32-bit versus 64-bit. The multiarch platform actually allows running 32-bit code on a 64-bit installation. I doubt you'd have any of the troubles your having now with 12.04 LTS 64-bit.

---

### Post by oldfred on 2011-12-02
I liked the clean install so much when I went from 9.04 32 bit to 9.10 64 bit that I only do clean installs. As such I have installed a few times and my backup for a home system is all the data I would need just to reinstall a new system. You can easily export a list of installed applications, but may want to edit list (its just a text file). I found I was still adding python 2.5. Now with LibreOffice replacing OO you may want to edit out known duplicates before installing. It will not install obsolete packages.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

---

### Post by dBuster on 2011-12-02
> **isantop said:**
> Just reinstall the 32-bit version.

That said, there have been some awesome changes in Ubuntu in regards to 32-bit versus 64-bit. The multiarch platform actually allows running 32-bit code on a 64-bit installation. I doubt you'd have any of the troubles your having now with 12.04 LTS 64-bit.

So what your saying is that my problems with the flash and 64bit and 10.04.02 will not be a problem with the 12.04 64 bit???

Also, just install the 32 bit version and the 64 bit programs will work with it??  Please explain a little more...  As far as I knew or know 64 bit programs are not compatible with 32 bit O/S whereas 32 bit programs are or can be made to run on a 64 bit O/S.....

---

### Post by isantop on 2011-12-02
> **dBuster said:**
> So what your saying is that my problems with the flash and 64bit and 10.04.02 will not be a problem with the 12.04 64 bit???

Also, just install the 32 bit version and the 64 bit programs will work with it??  Please explain a little more...  As far as I knew or know 64 bit programs are not compatible with 32 bit O/S whereas 32 bit programs are or can be made to run on a 64 bit O/S.....

Nope, you've got that backwards. If you install the 64-bit version, 32-bit programs will run on it. 

And yes, I believe the problems you're having with flash in 10.04 will be gone in 12.04. In fact, they're already gone in 11.10 64-bit.

---

### Post by dBuster on 2011-12-02
> **isantop said:**
> Nope, you've got that backwards. If you install the 64-bit version, 32-bit programs will run on it. 

And yes, I believe the problems you're having with flash in 10.04 will be gone in 12.04. In fact, they're already gone in 11.10 64-bit.

I thought I had it right... that 32bit programs will run on 64bit O/S, but not the other way around.

So with 11.10 64bit you can use say the snapfish bulk uploader or work on a project?  Or how about that error 2046 or something like that when trying flash...  not there?!

If so then maybe I will go with the 64 bit 12.04.  Which by the way is code named what?  I am drawing a blank now...

---

### Post by ubuntu27 on 2011-12-02
> **dBuster said:**
> I thought I had it right... that 32bit programs will run on 64bit O/S, but not the other way around.

So with 11.10 64bit you can use say the snapfish bulk uploader or work on a project?  Or how about that error 2046 or something like that when trying flash...  not there?!

If so then maybe I will go with the 64 bit 12.04.  Which by the way is code named what?  I am drawing a blank now...

I use Ubuntu 11.10 64 bit and run Flash Player 64-bit beta without any problems. [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") is life and time saver.

Snapfish requires people to register for their site. Could you tell us another site which is not working for you?
I will like to test if it works for me.

Ubuntu 12.04's codename is "[Precise Pangolin]("http://www.markshuttleworth.com/archives/784")", you can see Pangolin's [schedule here]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule")

[http://www.omgubuntu.co.uk/2011/10/ubuntu-12-04-named-precise-pangolin/](http://www.omgubuntu.co.uk/2011/10/ubuntu-12-04-named-precise-pangolin/)

---

### Post by dBuster on 2011-12-02
What other sites don't work... if I was at home with my laptop I could easily tell you.

From work it is a matter of my failing memory.  I believe though some games sites give me an infamous code 2046 or something to that effect and will not load.  

I have tried the repo's 64bit flash, when I do that I can at least watch youtube videos.  When I try flashaid's beta, no youtube videos...  

I am sure there is another member of the forums who has a snapfish account.  Sure they make you sign up to use.

---

### Post by dBuster on 2011-12-03
WOW!  I tried the live version of the Alpha for 12.04!  Let me say impressive.  Just wish I could get flash installed on the live test drive in order to see if it will fix my issues.

---

