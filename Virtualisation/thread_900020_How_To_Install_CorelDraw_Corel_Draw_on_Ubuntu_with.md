---
title: "How To: Install CorelDraw/ Corel Draw on Ubuntu with VirtualBox [Tutorial]"
date: 2008-08-24
forum: Virtualisation
---

### Post by u18b on 2008-08-24
I wrote this for future Corel Draw users Searching the Forum and Archives-----

When I was making the switch to Unbuntu, giving up Corel Draw (sometimes called CoreDraw) for Windows was my last major commitment to the Microsoft operating system.   If I could just find a way to do Corel Draw adequately in Ubuntu, then I would be a 98% Unbuntu user- and I would be happy, happy, HAPPY!

So after searching the Unbuntu archives and Googling, I found I was not alone.  LOTS of people use Corel Draw.  What I discovered after MUCH searching was there was no easy answer in the archives-  lots of people asked questions, but I could find no adequate answer.  

Well, as a dedicated Corel Draw user, my persistence paid off.  I'm now running Corel Draw as I always did.   And since I found a wonderful answer, I wanted to make this tutorial so others searching could find this and receive help.  If you're reading this, I assume you also are a dedicated Corel Draw user and want to get it running in Ubuntu.

First- Others will say, &#8220;try the Linux options.&#8221;  But as of the time of this writing, they are NOT ready for prime time- at least not for Corel Draw files.  I have spent YEARS making Corel Draw files and publishing many of them in magazines (I've published almost 100 articles in magazines).  I'm not ready to give up on all my Corel Draw files yet.  Please don't tell me how good Linux art programs are.

There are some very good vector art programs for Ubuntu, but they don't read Corel Draw files.

**Then I discovered SK1.**  
[COLOR="Blue"][http://sk1project.org/](http://sk1project.org/)[/COLOR]

WOW!!!!!!     I'm excited!  SK1 is a program being developed for Linux that will open Corel Draw files.   WhoooHooooo!!!!    But at the time of this writing (summer 2008}, SK1 is still a promise and developing (and too slowly for my taste- the last updated minor build revision was February &#8211; six months ago).  SK1  is not finished.    It must be compiled.  At this date, there is no version that I know of that one may find in a Ubuntu repository.  Downloading source code and compiling it is just not for me.  (I know, call me a wimp).  That's OK for experienced users, but not OK for newbies.  For now, SK1 remains on the &#8220;one day hopefully&#8221; list.

Second- That left Windows emulators where you can actually install Corel Draw inside of Ubuntu.  I tried Wine, but that was a total bust.  It was useless with Corel Draw.  It may work with other programs, but I totally failed with Corel Draw 6.  I saw where one guy said in the Ubuntu archives that he got Corel Draw 9 to work with Wine, but that was it.  One person.  Not a good track record!


My solution finally came with the program called **_VirtualBox_**.   The British magazine PC Plus reviewed it in issue 271 (a few weeks ago- summer of 2008} and I decided to try it.     With VirtualBox, you actually install a copy of Windows (or another OS) in a virtual file and run it in a VirtualBox from Ubuntu.
[COLOR="Blue"][http://www.virtualbox.org/](http://www.virtualbox.org/)[/COLOR]

It's FREE, Open Source, and I love it!

This was the solution I needed for Corel Draw since I would be installing Corel Draw into a REAL copy of Windows!  You need a licensed copy of Windows- but I had one of those.  I had an old copy of Win2k Pro.

I couldn't get VirtualBox to work properly at first.  So I went to the good old Ubuntu forum, and sure enough, there is GREAT help tutorial (what a great forum!).

I won't repeat that great stuff here.  Go and read the following WONDERFUL tutorial.

**How To: Install VirtualBox on Ubuntu 8.04LTS (Hardy Heron) [Tutorial]**
**[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=770745&highlight=vboxdrv](http://ubuntuforums.org/showthread.php?t=770745&highlight=vboxdrv)[/COLOR]**

Make sure you get VirtualBox up and running properly first.  _[COLOR="Red"]Pay attention to the USB instructions.[/COLOR]_

Once VirtualBox is up and running properly,  then you can install Corel Draw.

That just leaves one last thing.  How to get access to your other Corel Draw files that you have.

This is discussed in the tutorial above, but it is a bit buried further down in the many pages of posts.  So I'll give my shortened version here.


_So at this point in MY tutorial, I'm assuming:_
1. You've installed VirtualBox (following the other tutorial)
2. You've installed a copy of Windows and gotten a VirtualBox with Windows to work in Ubuntu (following the other tutorial)
3. You've installed a copy of Corel Draw in that same copy of Windows and gotten it to work (if you have problems, I can't help you there.  There are lots of versions of Windows and lots of versions of Corel Draw.  I installed Corel Draw version 6 on Windows 2000 Pro and it worked flawlessly).

OK,  Now you have a working copy of Corel Draw inside of Ubuntu!  But now you need it to be **_productive_**.

4.  To be productive, you need to be able to copy and move files, right?  I mean, your operating system of choice is Ubuntu.  So we want to be able to get our Corel Draw files to move around in Ubuntu.  Unfortunately, that's where VirtualBox is a little bit complicated and where an extra tutorial might be helpful.

VirtualBox works in two ways.  It carves a protected memory space out of your RAM,  giving it to Virtual-Windows,   and it creates a file on your Ubuntu drive which &#8220;becomes&#8221; the C: drive for Virtual-Windows.

But here's the problem-- it's not really a hard drive.  It's just a trick.  It's just a file.  So when you're not running a VirtualBox, you can't get    ANY    files off of it!  So if you do any productive work in there, you would not want to store it on the virtual C: drive if you ever had a need to move those files anywhere.  Did you get that?  If you make any Corel Draw drawings, you don't want to save them and store them on the C: drive of the copy of Windows in your VirtualBox, because is VIRTUAL!!!!  It's not real.   The drawind are locked away in a file, and once you shut down Windows, you can't get to the drawings anymore from Ubuntu.

And furthermore, when you are running your VirtualBox,  this VirtualWindows C:-drive-file can't really "see" any other hard drives _as a hard drive_.

Now what VirtualBox CAN do is see SHARED folders on a Virtual-network.  So Ubuntu is a potential &#8220;network&#8221; drive where you can share folders with this Virtual-Windows environment.

Sorry for this long explanation, but this is [COLOR="Red"]_important_[/COLOR] for understanding how this all works- and for understanding how to get the most out of all of it- and it's limitations.


So let me explain how I have my laptop set up as a real-world example.

I have four partitions.  The laptop came from the factory with Vista and a Vista Recovery partition.
I researched how to free up empty space on the Vista partition to cut it about in half.  I then used a Ubuntu 8.04 Live CD  with the stock partitioner to create a new partition in most of that space for my data formatted for NTSF (so Vista could see it).  In the remaining empty space I installed Ubuntu.

So not counting my Recovery partition (which I never use for day-to-day computing), I have three  partitions:

1. Ubuntu
2. Data
3. Vista

And now, I have a new &#8220;partition&#8221; that is virtual.  So let's add- 

4. Win2k VirtualBox on Ubuntu

Now, all my years of Corel Draw files are on the Data drive.   And my new working copy of Corel Draw is in the Win2K VirtualBox.   Now VirtualBox is going to let me designate some folders on my Ubuntu drives and list them as Shared.  So I need a plan.   So here's my strategies. 

_**A. I need a shared folder in Ubuntu itself.**_  I call it &#8220;Ubuntushare&#8221; and I placed it in my user name directory.  So when I start a Ubuntu file manager, I click on my Username folder and there is the Ubuntushare folder.  That's a pretty easy place to find it.  

_**B. I also have to decide a target for jumping to my data on the Data drive.**_  In my case, I have a folder on the Data drive called &#8220;Drawings&#8221; where I keep all of my Corel Draw files in various sub-folders.  So I want to share the Drawings folder.

_**C. I also want to go ahead and share the whole Data drive itself. **_  The strategy here is that when you are in a VirtualBox and you click on a shared folder and jump &#8220;out&#8221; of the virtual box and open up a file manager window,  you can go DOWN a file manager path, but you can't go UP.  So to save time, I want to go right to the Corel Draw files.  They are organized in various sub-folders.  No problem.   But I want to share the whole drive so that if I need to open up a MicroSoft Word document with Open Office, and it resides in another folder somewhere else, I need to be able to get to it.  So jumping to the top of the whole drive allows me to go anywhere in the whole drive.

_**D.  My last strategy is that whenever I create something from a Win2K VirtualBox, I will always save it [COLOR="Red"]somewhere else[/COLOR]- **_like in the Data drive or in the Ubuntushare folder.  I will generally [COLOR="Red"]avoid[/COLOR] saving productive work on the virtual drive since it will be trapped in there once the virtual OS is closed down.

_**E.  Now, there is a CONSEQUENCE to this strategy.  The consequence is that however you set up sharing for your virtual box is how the virtual Windows [COLOR="Red"]MUST[/COLOR] be set up every time.**_  So in my case, when I want to start up Win2K, it will ALWAYS look for the Data drive, which is not automatically mounted in my Ubuntu configuration.  So I have to click on the file manager and click on the Data drive to mount the drive before I start up Virtual Win2K- which is not a big deal to me.

The real reason I need to point this bad limitation out is [COLOR="Blue"]**USB drives**[/COLOR].    This is the reason why sharing with a USB flash drive is [COLOR="Red"]**_not such a great idea_**[/COLOR] with VirtualBox.  Obviously, no one would want to install a flash drive EVERY time (hey!-  unless you wanted to use it like a key).  So if I ever needed to get a Corel Draw file on a flash drive, I'd move it to Ubuntushare or the Data drive, and THEN copy the file to the Flash drive.



_**Alright, time to [COLOR="Blue"]SHARE[/COLOR] these folders.**_   

1. If you have a Hard Drive partition dedicated to data (like I do) then I strongly suggest that you [COLOR="Red"]NAME[/COLOR] that drive partition.  Whether it is Windows or Linux or whatever, I suggest that you name it something clear so that you can easily know that this is where your data sits.  Heck, why not just call it DATA.  That's what I do.  In Windows, you can just simply right click on the drive and choose &#8220;rename&#8221; or choose properties.  You'll then see a spot for naming the drive.

2.   Now, in Ubuntu, you should mount the drive where the Data resides (if it is a different drive).

3. Start VirtualBox.  (but don't start Windows).

4. On the right side, Click on Shared Folders (it's almost the last option).

5.  A settings box pops up.  In the virtual box settings page, Click on the folder with the green plus sign to add a shared folder choice.

6.  An Add Share box pops up.    Click on the folder button with the blue up arrow. 

7.  Now you're probably on familiar territory.  A file manager box pops up.  Navigate to the folder you want to share.  Hint/Suggestion:  At the top, it says &#8220;Look In&#8221; and then a box.  Click the drop-down arrow on that box and you'll get a second choice.  That second choice will be the folder with your user name!

See, I told you it would be easier if you chose that spot for &#8220;Ubuntushare.&#8221;

If you have not already created that folder, you can do it now by clicking the top right folder with the sparkle on it that has the bubble that says &#8220;Create New Folder&#8221;.   Enter the name  (like Ubuntushare) and then be sure and hit ENTER.   This creates the folder but does not select it.  You must then click on the new Ubuntushare folder and click OK.

8.  You're now back at the Add Share box.  Click OK again.  And the folder should appear in the setting list when the box goes away.

9. Now for sharing the whole (entire) Data drive.  This is where the unique name helps.

Once again, Click on the folder with the green plus sign to add a shared folder choice.

10.  An Add Share box pops up.    Click on the folder button with the blue up arrow. 

11.  Double click on the Media folder.  Linux treats drives as folders.

12.  If you have a CD-ROM, you'll probably see a folder called CD-ROM.  But hopefully you'll also see a folder called DATA (or whatever you called your data drive).  Click on it once and then click OK.  The addition is added to the list.

13.  Now if you want to add a more specific place to jump to on your data drive (like I wanted to jump right to my Corel Draw files) then repeat steps 9-12.  Except, when you get to step 12, just double click on the data drive to open it up and keep moving deeper into the directory tree until you get where you want to go.  Click OK when you are finished.

14.  When you are totally finished choosing shared folders, then click OK to save the settings and return to the main VirtualBox configuration window.  


**_You're ready to go to work._**

15.  Fire up VirtualBox Windows.   You'll be able to see those shared folders as network shared folders.  



I use Win2K Pro and here's how I get to my shared folders.  Your version of Windows may vary.


Click (double click) on My Network Places (Network Neighborhood) on the desktop.  
Click (double click) The Entire Network.  
Then Click (double click) &#8220;view entire contents.&#8221;   

At that moment,  I can see two folders.  One is useless- Microsoft Windows Network.  The other is- _**[COLOR="Purple"]Virtual Box Shared Folder[/COLOR]**_.  Inside this second one is my shared folder choices!

Therefore, what I like to do is go back up to the previous view of Microsoft Windows Network and Virtual Box Shared Folder.  I then right click on  Virtual Box Shared Folder to make a Shortcut to this folder.  It won't let me,  but will then offer to make a shortcut on the desktop.  Great!  That's what I want.

So now, I have one shortcut to all of my shared folders.


OK, now when I start Corel Draw and work on a drawing, I'm ready to save my work.  Well, in the Save dialog box,   look at the Save In  drop-down list at the top.  Choose Entire Network.  Aha!  There is Virtual Box Shared Folders again!  If you double click on that, you can see all of the folder options you entered.  Choose the one you want and save.

That's it!


**_Printing_**.

One last topic.  Of course there is one last element of being productive with Corel Draw- and that's printing.  You must be able to print your work.

Well, I'm sure this is a potentially complex subject that I'm sure I'm not qualified to help people solve.

But I will tell you my experiences.  I wasted hours upon hours and finally met with some success.

I have a modern laptop with no parallel port.  It is all USB.

I had mixed results installing USB printers.

I FAILED to install an old HP Photosmart P1000.  I downloaded the Win2K driver file from HP and installed it, but just could not get Win2k to &#8220;see&#8221; the P1000.  I think this is older USB plug and Play technology.

But I was SUCCESSFUL at installing a new HP Photosmart D7460.  


But there were a few things I had to do/figure out to get that D7460 to work.

1.  Get USB working properly at all.  The previous tutorial describes this well.

2.  Plug the USB printer in, start up VirtualBox (but not Windows) and create a FILTER.  In this case, filters let thing IN.  The default action of VirtualBox is to keep things OUT.  So if you want Windows to see the USB printer, you have to create a filter for it to let it IN. And make sure there is a check mark in the box.

3.  Here is something I found by trial and error.  When you click on the USB settings,  up at the top,  there are two settings for USB.   The first is &#8220;Enable USB Controller&#8221;  and the other is   &#8220;Enable USB EHCI Controller&#8221;.   I found on my HP laptop that I needed to check the first but NOT the second.  I don't know what the EHCI controller is, but the printer and other USB devices would not work if it was checked.

Well, that's it.
I can't tell you how happy I am to be able to use Corel Draw under Ubuntu.  Even if it has some minor limitations, I'm still thrilled.

And I hope this tutorial helps to walk someone else through it too.

I confess my hopes are that one day we will have a full fledged mature  SK1 program sitting in the Ubuntu repository.

Another possibility would be that VirtualBox could overcome the limitations of 
--not being able to &#8220;see&#8221; other disk drives natively.
--not being able to see and deal with flash drives natively

If these limitations were gone, then Corel Draw could run at it's native best.

U18B

Ron B.

---

### Post by Mahogan on 2008-12-08
Thanks for sharing this post, it is very  helpful.  I am an avid Corel Draw user, and tried to get X4 installed in  Ubuntu 8.10 that is installed within Windows XP, a virtual install, just the opposite of what you are explaining here.  X4 crashed and would not install, so I tried my old version of Corel Draw 11 and installed Wine in Ubuntu then  11, it worked flawlessly.  I am a  signmaker and use Corel to print to wide format printers and vinyl plotters.  It is my goal to experiment with  Ubuntu and see if I can get it to work with my equipment.  Ideally  I would want to  get X4 working in Ubuntu.  My goal is not to have to buy Windows and instead have Ubuntu as my  primary and only OS and be able to have it work with my equipment.  But for now, having Corel 11 working in Ubuntu 8.10 is awesome!  Only thing is that the clipboard does not work.  Thanks again for your  post, I may experiment with it just for fun.  ~Mahogan

---

### Post by pietjanjaap on 2008-12-08
You could also check virtualisation with seamless. I do not know if it works.

---

### Post by keithwwalker on 2009-02-02
Great tutorial!  Any update on SK1 since your initial post?

---

### Post by cristian.brinzariu on 2009-05-16
**:)) I'm sow happy**

**sK1 0.9.0 First public release (Montreal release) rev.716 **

[http://sk1project.org/modules.php?name=Products&product=sk1&op=download](http://sk1project.org/modules.php?name=Products&product=sk1&op=download)
 
Now let se if is working :P

---

### Post by stani on 2009-05-20
I've made packages for Jaunty and Intrepid in my PPA repository (including 64 bit):
[http://pythonide.blogspot.com/2009/05/sk1-vector-graphics-editor-is-now.html](http://pythonide.blogspot.com/2009/05/sk1-vector-graphics-editor-is-now.html)

---

### Post by black scorpio on 2009-11-02
any update on karmic koala?

---

