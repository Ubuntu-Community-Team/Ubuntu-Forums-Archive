---
title: "Ultimate Edition 1.8  Newbie Review and How-To"
date: 2008-08-19
forum: Testimonials &amp; Experiences
---

### Post by cgdoc7 on 2008-08-19
The following is just my opinion of UE 1.8 as well as some fixes I used on issues I had with my system.  All solutions were found by either experimenting or by browsing the forums from Ubuntu and UE for articles and help created by other people.  My goal as a UE 1.8 newbie is to hopefully help others with some issues I found and how I fixed them.  I am not savvy with Linux code but I like to teach/experiment and I love the philosophy and drive behind the Linux/open source community whom I consider family.  I do not want to take anything away from Ubuntu as it is an amazing distro, without which UE 1.8 would not be possible.

I downloaded and installed UE 1.8 and am pretty impressed so far.  I had few issues right off the bat and I would like to share those in hopes of helping others with the same problems.

I downloaded the 1.8 Ultimate Edition version 1.3gb file from [http://ultimateedition.info/Ultimate_Edition_1.8/](http://ultimateedition.info/Ultimate_Edition_1.8/) which took around 4 hours on my slow Internet connection. Once I had the file I burned the .ISO to disk and restarted.  I was presented with a nice looking install screen which was pretty much exactly the same as Ubuntu's 8.04 install.  All the same features with the exception of some graphical changes.  After I was loaded into the Live CD I went about testing different things specific to my computer i.e. video graphics , sound etc.  All worked well and the theme was beautiful in my opinion.  Glossy, clean, well rounded.  Very nicely done.  SO time to get to it!

**Install**

  I clicked the install button and let her rip.  Everything seemed to mirror the 8.04.1 install so it was no trouble getting through the screens. Install took around 15 minutes total.  No issues, very smooth.

**First Log-in**
First log in was nice, just as aesthetically pleasing as the Live CD.  However this is where I started to run into a few minor issues.

**Issues**

You should first install all system updates BEFORE you activate your restricted video card drivers.  After the updates have been installed and your computer has been restarted then enable your restricted drivers.  To do this go to system/administration/hardware drivers and enable you video card driver.  The driver should automatically be downloaded and installed.  Restart your system then continue to the steps below, if they apply to you.

Issue #1

Theme
The theme was nice but when I went to system/preference/appearance to see the different themes I had available... my nice new UE theme disappeared and I was unable to relocate it.

   My Fix: 	1. Open system/preference/appearance.
		2. select the overglossed theme and press the customize button.
		3. On the Controls tab select overglossed.
		4. On the Window Border tab select overglossed.
		5. On the Icons tab select black-white.
		6. Enjoy the beauty of the overglossed theme goodness.
*The only issue I have with this theme is that when viewing some e-mails through evolution mail the background of the e-mail and the text seem to blend together.  Could be more of an issue with the mail program but at any rate not a show stopper.

Issue #2

Compiz (graphics)
I went to system/preference/appearance/visual effects and enabled extra effects.  When I did this the title bar at the top of each window disappeared and I could no longer access the menu/close/minimize buttons.

  My Fix:	1. go to applications/system tools/compiz fusion icon and open.
		2. You should now see  the icon in your "task bar".  
		3. Right click on the compiz fusion icon and go down to select window decorator and make sure emerald is selected.
		4. Right click on the compiz fusion icon again but this time select settings manager.
		5. Scroll down to the Effects section and look for the window decoration option.
		6. Enable window decorations by clicking the check box next to the window decoration button.  If it is already enabled then disable and re enable it.
*for some reason when I enable the extra effects in system/preference/appearance/visual effects I seem to keep running into the same title bar issue.  Sticking with the normal visual effects as opposed to the extra seemed to solve the issue (still using the steps above of course).

Issue #3

No 3D cylinder love?
One of the first things I wanted to try after install was the 3D cube and cylinder.  Of course it did not work right off the bat, but it was not hard to get it working.

  My Fix:	1. Ensure you have followed the steps in issue #2 as they are necessary to get your 3D cube or cylinder working.  
		2. Go to applications/system tools/compiz fusion icon and open (unless the icon is already on the task bar from issue #2).
		3. Right click on the compiz fusion icon on the task bar and select settings manager.
		4. Go to the desktop section and enable the desktop cube and rotate cube options.
		5. Go to the effects section and enable the 3D windows, animations and cube reflection and deformation options.
		6. You should now be able to rotate your cube/cylinder by pressing ctrl+alt+left click.  If you can not, or you are getting only a front and back page style window when you try and use your 3D cube/cylinder then move on to #7.
		7. Assuming you have not changed any of your panels, right click on the bottom panel, the one with you trash bin, and select add to panel.
		8. Scroll down and select workspace switcher and click add.
		9. Right click on the workspace switcher that we just added to your bottom panel and select preferences.
		10. Change the columns value from 2 to 4, leave the rows value set at 1,  press close.  This should now allow you to see a cube or cylinder as apposed to the 2d style sheet.  You might need to restart your computer.  You may also right click on the workspace switcher we created on the bottom panel and select remove from panel if you don't want it there.  Your 3D cube/cylinder will still work with out this item on you panel.

Issue #4

Sound
I had a weird sound issue that would allow me to hear sound on the Internet and with Dvd's/CD's but not system sounds.
  
  My Fix:	1. RESTART, RESTART, RESTART!  Such a frustrating thing to try and trouble shoot something when the end result is you just had to restart your computer after you updated it to fix the issue.  Lesson learned, restart your computer after you update it.  Problem solved!

**Repositories**

The repo's are both Ubuntu's and UE.  So far no conflicts but I just installed.  I did however get all the Ubuntu updates after install.  The only reason I know this is I just installed a fresh copy of Ubuntu 8.04.1 this week and from what I can tell they were the same updates.  This is a huge plus for me as I want the stability of Ubuntu with the UE flavor.

**Ultamatix**

This was formally known as Automatix.  I used this program awhile ago with ubuntu and never had any issues with it, but I know there were plenty of issues that others had.  I did a bit of researching before I installed UE on this topic alone and I have to say most of the things said were pretty negative.  I however have to try things for myself.  I grabbed it from [http://ultamatix.com/#Contents](http://ultamatix.com/#Contents) at the bottom of the page.
	
	Installation
		Easy enough to install.  I just downloaded the .deb file and opened it with the default GDebi Package Installer.  Installation was smooth and without errors.

	Use
		After install, it can be opened from applications/system tools/ultamatix.  The user interface is well put together and simple, an almost identical clone of Automatix.  As far as it being more stable than its predecessor, I am not yet sure.  I have installed applications and have yet to run into any issues.  It's a wonderful concept with great potential.  Especially for the layperson coming from windows/mac.

**DVD/CD's**

Worked after install and updates with no problems.  Great video/sound quality.  Only application I could use for both media types was VLC media player located in applications/sound & video/VLC media player.  All other players gave me some weird errors (I can post later).

**External Media**

Worked after install with both of my external hard drives.  This was rather surprising as only one of them worked after install in Ubuntu 8.04.  
*This might be from an error on my part.  When I installed Ubuntu 8.04 and plugged in my external hard drive it gave and error saying it was unable to mount and that it might have been improperly removed from a windows system.  It then gave me instruction as to plugging it back into a windows computer and safely removing it, then powering down the computer completely.  I unfortunately did not retry this in Ubuntu 8.04 but both hard drives worked in UE.  All that to say it might not have been UE that corrected the issue.  It could have very well been the tips I got from the Ubuntu OS that corrected it.

**Summary**

Impressed! All issues I had were the same with my install of Ubuntu 8.04.  UE does not feel bloated and is just as fast as Ubuntu 8.04.  I have to take my hat off to TheeMahn!  I know you did not create Ubuntu but you sure polished it up in a very pleasant package.  Congratz on a job very well done and I am looking forward to 1.9!  Keep up the good work!

Jason

---

### Post by Zero Prime on 2008-08-20
Great review man!

---

### Post by Sef on 2008-08-20
> Ultamatix

This was formally known as Automatix. I used this program awhile ago with ubuntu and never had any issues with it, but I know there were plenty of issues that others had. I did a bit of researching before I installed UE on this topic alone and I have to say most of the things said were pretty negative. I however have to try things for myself. I grabbed it from [http://ultamatix.com/#Contents](http://ultamatix.com/#Contents) at the bottom of the page.

Installation
Easy enough to install. I just downloaded the .deb file and opened it with the default GDebi Package Installer. Installation was smooth and without errors.

Use
After install, it can be opened from applications/system tools/ultamatix. The user interface is well put together and simple, an almost identical clone of Automatix. As far as it being more stable than its predecessor, I am not yet sure. I have installed applications and have yet to run into any issues. It's a wonderful concept with great potential. Especially for the layperson coming from windows/mac.


Ulatamatix is not recommended and not supported by Ubuntu.  To download flash, java, and the codecs needed follow these steps:

Applications > Accessories > Show: All Available Applications > Search: Ubuntu > click on top box > apply changes > apply > close.

Automatix was well-known for crashing systems and causing other problems.

---

### Post by eragon100 on 2008-08-21
I liked automatix, it helped me easily install dvd support when I first switched to ubuntu (with ultimate gamer's edition 1.4, actually)

---

### Post by cgdoc7 on 2008-08-21
> **Sef said:**
> Automatix was well-known for crashing systems and causing other problems.

I know, I have read post on this breaking peoples systems.  While I have not had a bad experience, I have no doubt that others have.  I have confidence that Ultamatix can break that reputation.  Only time and proof will tell.

---

