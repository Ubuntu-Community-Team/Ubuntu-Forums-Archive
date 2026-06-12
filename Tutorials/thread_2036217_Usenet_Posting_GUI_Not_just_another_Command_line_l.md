---
title: "Usenet Posting GUI Not just another Command line lesson!!"
date: 2012-08-01
forum: Tutorials
---

### Post by Ultra Cronic on 2012-08-01
Older Linux pop-cultist mindsets are not going to appreciate my attitude on this.
GUI for usenet posting binaries is now a success.!!!!

Being the social type that I am, I can't help but notice how many people out here would like me to share my victory on Graphic User Interface for the DOS programs buried in the bowls of our Linux machines that we will never memorize the stupid spelling of them. How many times have we “googled” Ubuntu OS ver= * dos command programs [terminal program runs] just to find a program we know we have ------somewhere-----


My apologies about my musings on GUI controller for the usenet ignorance and arrogance, but I was P1$$yPout at this major VOID in the Linux distros.


Well I have had enough of this tug of war between the cult mindsets. I am guilty of having the Microsoft[in the head] GUI driven mindset and so aren't 70% of new Linux converts in the past 5 years. I work in IT at a college so I know what the new kids in town want. The new Linux generation is pushing for this change and old folks don't appreciate it, though I am 56 years old myself; LoL. And I HAVE Carpi-tunnel syndrome. Another reason for the GUI.


Yes I admit I got used to a crappy OS over loaded with Capital greed police and antivir slowing even a rocket speed computer down to a crawl. Now I must admit the CLI; apt-get install has much better results than Synaptic Package Manager. Sort of reminds me of Microsoft Foundation MOLASSES!!! I don't recommend abandoning the command line skill set all together.
After all this JbinUp gui will make no sense to you at all if you don't understand some command switches and programs like rar etc...
---------------------------------enough of the Intro and emotional musing----------------------


OK; lets get a Usenet uploader GUI for binaries posts on our Linux box.
I am running Ubuntu 11.0 on a Dell latitude D620 Centrino duo CPU.


Since my re-install of OS [actually a re-image from a clonezilla live cd from a file in an external usb drive.
I created the image 6 months ago so “Most” my programs where saved. CloneZilla rocks!!!!
It's the Linux version of Ghost or AcronisII. Acronis works if you have 8 hours to do this Backup.
CloneZilla did the whole drive fat tables MBR,bootloader, and partitions saved to a file in 1 hour.
No I am not drifting her before you install the particular JAVA from SUN version Backup your whole hard drive. One command line permissions goof or apt-get install poop and whammo!! You may just hose your whole system. I installed the wrong version of JAVA and set the properties
of the JAVA.jar to the wrong “Open With” path and whacked my OPENSHOT video editor and several java driven Internet tools. Turned my OS into a pile of digital bile :(.


If you don't do this do not come flaming me for your paperweight that once was a computer.
I was back up and running in an hour after the CRASH!!


Another thing, I had Updates shut off system wide to prevent codec upgrades from toasting Openshot
Movie editor. [blows away Microsoft-in the head] Movie Maker.
I am running two versions of JAVA on my system the GNU and the SUN.
JAVA updates can regurgitate this news posting GUI [JBinUp] and other programs if your not careful.






Credit#1 Himmelmann & Röbke webpage and owner of JbinUp for the download.
Thanks to this guy here <”http://superuser.com/users/107458/rodja”> for the command cut and pastes
that made it all work with NO dependency chasing.Thanks rodja.


I hope posting the website addresses of the helpful install commands is allowed here.
Go here for JbinUp download, <”http://forum.jbinup.com/viewtopic.php?f=4&t=511”> [cut and paste between brackets and quotes. Trying not to post an active link. Scroll down and download the link [JBinUp 0.90 - Beta 8 – All.zip]
   Download and extract to your /home/your-user-name/the root of your home folder this may not be the best choice but it is what I did and it worked so lets not change anything. I have file-roller for an archive manager and it worked fine.
Now go here for the command line install apt-get commands just cut and paste in the xterminal, it's a short task and not terribly deep and long this will take a minute to accomplish.
------> <”http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric-and-later-versions”> cut and paste to URL do not include Quotes or <> Brackets.

Heres a run down on the commands. Open a terminal emulator [dos box] Xterm or whatevr your system uses.



sudo apt-get install python-software-properties
sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin

If any of these things fail go to the webpage  <”http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric-and-later-versions”> 

   Read up, notice other linux and os instructions on that page, If your OS is not the same as mine they may have a solution.

This is one of the reasons I wont abandon a positive attitude towards learning Linux commands. Some things just work better that way. Now for the tweaks; 
Open xterminal emulator and type   sudo Thunar
This is File Manager's alias name I know I hate this part of Linux.
Go to the root of [your /home/username/JBinUp 0.90-Beta 8-all/ And right click on JbinUp.jar Now click on properties, The menu “open with” should equal java NOT SUN JAVA 6 runtime!!!! How bizarre is that!! My guess is the default system java calls up the SUN JAVA libraries as needed, I am guessing here. When I open a terminal and call the program JbinUp from there there are some hints at the rtty output in the terminal that a lot of flip flopping is going on with java under the hood.

So open it [double-click] You either
have a great GUI for binary uploads or
you have just hosed your system's
JAVA Dependant programs and are plotting my demise as I upgrade my life insurance policy. Remember to select ENGLISH during the first run, fear not the German website it came from.

WARNING!! On the step-2 button there will be a "Subject menu-bar" Don't touch a one character or type in that sucker it will hose the upload format for headers in the usenet group posting, those are code characters that automatically set the split-file and yEnc naming conventions correctly in the header subject line of the multi-part post.

WARNING; if this works for you immediately Open
“Applications-menu”/System settings/ software resources and stop all auto updates
don't delete or remove ppa links just untick everything especially the main repos
and tick them back on when a dyer need for an upgrade is needed, /XTerminal/sudo apt-get update
After re-ticking the sources. You'll have to close software resource center first.
 Now PAY ATTENTION to the Synaptic manager warnings on any “Removals” due to the nebulous upgrade taking place, Do not let an upgrade change your JbinUp or JAVA SUN versions without checking up on the webpage links I posted to ask the forum members if any upgrades on the two programs will $harts up the JbinUp GUI.

NOW HOLD ON!!! I know I am yelling I can't tell a new Linux convert how important it is to do a Full System Backup with CloneZilla Live cd and an external USB drive with at least 100 gig of available space. Though FAT32 will work;  a Linux ext3 drive for storage will allow CloneZilla to SMOKE the job in an hour or two. NTFS I have not tried.

          Now if an infamous upgrade turns your Ubuntu OS into a pile of digital bile, you can revert to the moment of time you made the backup in an hour with all your programs and settings in tact. At the end of the restore job [not backup job] if you should be asked to leave a bootloader that was found on the back up tick yes to the question. I hate google data mining so I USE [http://duckduckgo.com/?t=](http://duckduckgo.com/?t=) for a search engine similar and cleaner then google and get this NO cookies NO trackers no logging, search service and no messy resulting pages that have nothing to do with what you where asking for.

        The Undernet Freenet Piratebay type paranoia's mindset swear buy this site if you are not on the freenet underworld network, [I am} but I can't recommend it for anyone with a thin skin low tolerance of citizens a fowl or you have high religious standards. Search.geek is their search engine but only works on the freenet network. Otherwise they use [http://duckduckgo.com/?t=](http://duckduckgo.com/?t=)  For the above ground searches.

        
Search for lessons to make full hard drive backups from a live cd.
This is as important as learning to change a flat tire, it's a necessary evil DO IT!!

       Search CloneZilla FAQ or demonstrations In youtube there are a gazillion opportunities to learn this and a million reasons Tar and tar-balling,  your home folder is not good enough. It wont save you in a JAVA explosion or a network module screwup.

       Craplication upgrades can roast a lot of system programs and unintended consequences will prevail.

 I am not a fan of automatic upgrading and updating with blind ignorant faith the developers are sure nothing will break [or not]. 
  I will be editing this post because I am a layman and Linux was not built for laymen though it's moving towards that more and more every day. 
  I can't understand how anyone would endorse seven lines of xterminal typing over 1 click of a mouse, I certainly can't, 
  I'm a believer in using dos to make GUI's work!!! I'm an employer in a way, I would not want to pay people to type 7 lines over the short time it takes to click a mouse. Lets get real. The terminal in linux is there to take advantage of open source code to Alter or programs and especially create GUI's that save time.  It's just more productive.

        PLEASE NOTE!!  There are higher upgraded versions of JbinUp and JAVA-SUN. 
Don't mess with them yet. It seems all over the world this program is every newsgroup lovers hope for an uploader poster GUI but there is a 50% failure rate when anyone hap-hazardly installs the latest JAVA-SUN and JbinUp GUI it's a sensitive combination of both program versions of JAVA and JbinUp and your kernel version I believe mine is 2.6.?  that Harmonizes with each other that makes this GUI work. And of course I am using the oneiric/Cononical Ubuntu 11.0.? on an Intel chip. These things make a difference.

    Now test allot of your must have software programs and make sure they work, VPN, Net-tools, Net proxies, Video editors audacity etc...Visit a JAVA intense webpage and make sure java is working, google "Java Test Page" and the folks at Oracle will flash you a text widget report on your version DON'T ACCEPT AN UPGRADE !!
Make sure your video/audio editors are working too then;
Get out CloneZilla and your external USB drive and back up the whole drive to a secondary file, use the date as the save name, and always keep two restore points on hand. Linux is finally out of the barbaric cave and now user friendly to usenet binary uploads. Use Pan or Thunderbird to download and surf usenets.
 Have a nice day:D
Sincerely; Ultra Cronic   :popcorn::guitar:

---

### Post by oracle2b on 2013-02-26
Thanks for the info!

---

