---
title: "Hello.... Introducing myself and my script (Wallpaper rotator)"
date: 2010-12-25
forum: The Cafe
---

### Post by JCarlin6 on 2010-12-25
Hello my name is James and I would like to introduce myself. I manage multiple Linux servers but only recently did I switch my desktop environment to Ubuntu.... I noticed there wasn't A banner rotator like in Windows so I decided to go one step further. I wanted to make a script that would download wallpapers without having to do it yourself. Thus was born my baby. "WallArt". It Grabs wallpapers at random from wallbase.net based on your specifications. Just run the install script and your done. Simple. Easy and quick. If by some chance you do not like my script run it again to uninstall it. ;) I would really like your input as a community. Thank you. 

**PS: LOCAL SUPPORT WAS ADDED YOU CAN USE YOUR OWN WALLPAPERS NOW =)**


I encourage you to test it out yourself look at the code. Do whatever =)
Only thing I must say is I only started commenting half way through it so I will finish that up and any other suggestions are MORE than welcome.
> [http://sourceforge.net/projects/wallart/](http://sourceforge.net/projects/wallart/)

Hopefully the opensource community will love my idea. And adopt it maybe not in my way but in yours.

---

### Post by ki4jgt on 2010-12-25
Love it!!! Would like to see it expanded. Maybe fetch using a search term and include Deviant Art.

**EDIT: Also when the user clicks cancel at any time, the program doesn't need to continue with the installation. Other than those two things. I love it!! :-)

---

### Post by VastOne on 2010-12-25
Very nice..  A great idea and the install. options and setup are done very well.  Once I figure out which ratio option gives me the perfect wide/full screen, I will be set...

Thanks for this!

---

### Post by JCarlin6 on 2010-12-25
> **ki4jgt said:**
> Love it!!! Would like to see it expanded. Maybe fetch using a search term and include Deviant Art.

**EDIT: Also when the user clicks cancel at any time, the program doesn't need to continue with the installation. Other than those two things. I love it!! :-)

I will look into that thank you =) Glad you both like my script =D

---

### Post by Jechem on 2010-12-25
Maybe you could give the user an option if they want to use their own set of wallpapers. Other than that it was nice. Great Job!

---

### Post by JCarlin6 on 2010-12-25
> **Jechem said:**
> Maybe you could give the user an option if they want to use their own set of wallpapers. Other than that it was nice. Great Job!



That may be in the next  version actually

---

### Post by matt_symes on 2010-12-25
It's great. You've been more productive than me recently ;)

Needs more choice as to where to get the wallpaper from though..

---

### Post by asifnaz on 2010-12-25
well done . I was looking for something similar . thank you so much

---

### Post by inhiway on 2010-12-25
As I prefer to use my own set of wallpapers, I've subscribed to this thread to watch for future developments.  Thanks for your contribution.

---

### Post by JCarlin6 on 2010-12-25
> **inhiway said:**
> As I prefer to use my own set of wallpapers, I've subscribed to this thread to watch for future developments.  Thanks for your contribution.

> **Jechem said:**
> Maybe you could give the user an option if they want to use their own set of wallpapers. Other than that it was nice. Great Job!

I have added it in the new version either download it from Sourceforge or run the latest script and it will update. ;) Local Support has been added... Interesting I uploaded the file yet on sourceforge it shows its not the latest... any Ideas on how I update that on sourceforge? I just deleted the last version on the site to make it work... So its good now =)

---

### Post by JCarlin6 on 2010-12-25
Sorry it posted twice... Local support added

---

### Post by Jechem on 2010-12-25
Thanks for the script and sharing it with us.
Merry Christmas!

---

### Post by JCarlin6 on 2010-12-25
you are very welcome merry christmas to you!

---

### Post by ki4jgt on 2010-12-26
Just wondering, but where does the program store the wallpapers locally? and can they be removed? Can you add a cache size limit so if the folder contains over so many files the oldest will be deleted. (If you haven't already done this of course)

**EDIT: Found it LOL :-) Now I feel dumb. I was expecting a .wallofart but yeah, I'm using 1_5 right now. It great! I just wanted to make sure it cleared the folder every now and then of files which may load and load and load until the folder becomes huge. Again great work and I look forward to seeing 1_6

---

### Post by JCarlin6 on 2010-12-26
> **ki4jgt said:**
> Just wondering, but where does the program store the wallpapers locally? and can they be removed? Can you add a cache size limit so if the folder contains over so many files the oldest will be deleted. (If you haven't already done this of course)

It stores it in your home folder more specifically (/home/user/wallpapers/) It does not contain a size limit yet but it will soon... A uninstall feature is included which removes the entire directory and a reinstall is pretty quick but its not gonna be too big of a problem especially since you can do a max of 1 per minute... It is VERY easy to remove all the wallpapers manually as well just select everything but the main wallpaper file and the py file and your good. Its clean. Is that something you would want before you installed it or something I can add in sometime this week? as a side note the uninstall also removes the cron jobs and reinstalling does not add more.

---

### Post by inhiway on 2010-12-26
> **JCarlin6 said:**
> I have added it in the new version either download it from Sourceforge or run the latest script and it will update. ;) Local Support has been added... Interesting I uploaded the file yet on sourceforge it shows its not the latest... any Ideas on how I update that on sourceforge? I just deleted the last version on the site to make it work... So its good now =)

Thank you very much.  Now that's speedy service.  :D

---

### Post by JCarlin6 on 2010-12-26
> **inhiway said:**
> Thank you very much.  Now that's speedy service.  :D

You are very welcome... If there is anything else I can do I would be more than happy to help... Just do me a favor as well and spread the word ;)

---

### Post by ki4jgt on 2010-12-26
> **JCarlin6 said:**
> You are very welcome... If there is anything else I can do I would be more than happy to help... Just do me a favor as well and spread the word ;)

You should try Softpedia. They give you a nice little widget to place on your site telling your visitors it's malware free and everything. :-)

---

### Post by lemmy999 on 2010-12-27
@James

Nice job! Only problem for me is uninstalling the app. Trying to uninstall sends my CPU up to 100% and then crashes the machine.

---

### Post by JCarlin6 on 2010-12-27
> **lemmy999 said:**
> @James

Nice job! Only problem for me is uninstalling the app. Trying to uninstall sends my CPU up to 100% and then crashes the machine.

I find that VERY hard to believe as I have uninstalled with ease every time on 3 of my own computers and with many of my friends... As you can see from my script it basically does a few things to uninstall... first command is... "rm -rf /home/$ON_USER/wallpapers" which removes the wallpaper folder then it runs "crontab -l | grep -Ev "background.py" >> oldcrontab " which grabs any lines with background.py in the crontab it then proceeds to install the crontab by using the command "crontab oldcrontab" then finally removes the old one with the background.py in it with rm ./oldcrontab and then does the same for local.py........ Out of curiosity what version of ubuntu are you on and could you provide a link to a video of this occuring? Maybe it is something else in your system. take a screen shot using the "top" command before running it and during the uninstall... we can narrow the problem down from there. Email me at [email]JCarlin6@yahoo.com[/email] so we can get this resolved or reply in this thread although I am fairly 100% certain it wasnt the script as it has a very small memory footprint. If anyone else is having this issue please let me know.
```

if [ -e /home/$ON_USER/wallpapers ]
	then 
		while true; do
			echo -e $RED"WARNING 'UNINSTALLING' WILL REMOVE ALL WALLPAPERS IN DIRECTORY"$ENDCOLOR
			read -p "Not first Installation... Do you wish to ReInstall (R) or Uninstall (U)? <r or u> " ru
   			case $ru in
		        [Rr]* ) echo -e $BLUE"Continuing"$ENDCOLOR; break;;
		        [Uu]* ) 
			echo -e $BLUE"Uninstalling"$ENDCOLOR
			rm -rf /home/$ON_USER/wallpapers
			crontab -l | grep -Ev "background.py" >> oldcrontab 
			crontab oldcrontab
			rm ./oldcrontab
			crontab -l | grep -Ev "local.py" >> oldcrontab 
			crontab oldcrontab
			rm ./oldcrontab
			echo -e $BLUE"Removed"$ENDCOLOR
			echo -e $BLUE"Closing in 10 seconds..."$ENDCOLOR
			sleep 10
			exit
			;;
		        * ) echo "Please answer 'r' or 'u'.";;
   		 esac
	done
```

---

### Post by lemmy999 on 2010-12-28
@James

I am using 10.4. Here are the screenies you asked for
1.Prior to running install.sh

[[img]http://ompldr.org/tNnI4Mg[/img]](http://ompldr.org/vNnI4Mg)
2. Immediately after starting the script
 [[img]http://ompldr.org/tNnI4NA[/img]](http://ompldr.org/vNnI4NA)

---

### Post by JCarlin6 on 2010-12-28
> **lemmy999 said:**
> @James

I am using 10.4. Here are the screenies you asked for
1.Prior to running install.sh

[[img]http://ompldr.org/tNnI4Mg[/img]](http://ompldr.org/vNnI4Mg)
2. Immediately after starting the script
 [[img]http://ompldr.org/tNnI4NA[/img]](http://ompldr.org/vNnI4NA)

Would you please give me your system specs... Also is anyone else experiencing these problems

---

### Post by lemmy999 on 2010-12-29
James
I am running a AMD Athlon 64bit twin core processor, 3 gb of RAM, a 1tB Samsung hdd. Video is from a Nvidia GT6600 card.

---

### Post by JCarlin6 on 2011-01-02
I honestly couldnt tell you what is wrong I will keep looking into it. But I ask everyone to try it out themselves and see if you get the same problem. It would be of great help. Thank you.

---

### Post by ki4jgt on 2011-01-02
No probs here with the uninstall.

---

### Post by lemmy999 on 2011-01-03
I'll try and manually uninstall then then re-install.

---

### Post by JCarlin6 on 2011-01-05
Did it end up working out? Also what version of the script were you using at the time... I forgot to ask.

---

### Post by yetiman64 on 2011-01-06
Hi JCarlin6,

Firstly I'd like to say "Thank You" for posting this here, it's fantastic, works great.

Been testing it for about 4 or 5 days now and so far I've had very little problem with it. I am having no problems with installing/uninstalling here.

No problems with using Wallbase.net, as has already been mentioned the addition of other download sources to choose would be great.

I mainly use it for local files and am using links to local files in the wallpaper folder, which work. However in doing this I noted the scripting can't handle spaces in filenames when the system adds "Link to" to the filename (though this can be avoided by linking using middle mouse button drag and drop - no "Link to" added to those links). However many of my wallpapers I've created over the years also contain spaces and would be a horrid task to rename them all manually - I'm not good enough to write a script to do it automatically, yet. **Would it be possible to allow for spaces in filenames with this program ?** That would be very convenient when used locally :-).

Just noted while updating to WoA0_1_6 that the base folder for WoA0_1_6 is unzipped to within the WoA0_1_5 folder rather than to the home folder when updating from the older version in terminal. This causes errors which are dropping out the updating. I had to cut and paste the base folder to the home folder to get it working. Just to make sure, I cleaned out the lot and redownloaded from sourceforge, all OK now. **Is this something you need to fix for automatically updating from within the terminal ?**

If it matters I had launched WoA0_1_5 in terminal by navigating to the /home/<username>/WallofArt0_1_5/wallpapers and inputted "./install.sh". I tried to let sourceforge update it automatically when everying went wrong.

Once again thanks for releasing this program/script on the forum, great effort :-). A new wallpaper to look at every 10 minutes has made me very happy :lol: .

Regards from yetiman64.

**Edit**: Spaces issue now fixed here by extracting from and adjusting a shell script found in post #3 at  [noparse]http://www.computing.net/answers/unix/how-to-remove-spaces-in-filenames/8204.html[/noparse] and tested on a copy of one of my image directories copied to my desktop. (Note: URL is disabled, copy and paste to address bar if anyone needs to see it). I disabled the link as the script required several runs to completely do the job and may not be suitable for everyone.

---

### Post by JCarlin6 on 2011-01-06
> **yetiman64 said:**
> Hi JCarlin6,

Firstly I'd like to say "Thank You" for posting this here, it's fantastic, works great.

Been testing it for about 4 or 5 days now and so far I've had very little problem with it. I am having no problems with installing/uninstalling here.

No problems with using Wallbase.net, as has already been mentioned the addition of other download sources to choose would be great.

I mainly use it for local files and am using links to local files in the wallpaper folder, which work. However in doing this I noted the scripting can't handle spaces in filenames when the system adds "Link to" to the filename (though this can be avoided by linking using middle mouse button drag and drop - no "Link to" added to those links). However many of my wallpapers I've created over the years also contain spaces and would be a horrid task to rename them all manually - I'm not good enough to write a script to do it automatically, yet. **Would it be possible to allow for spaces in filenames with this program ?** That would be very convenient when used locally :-).

Just noted while updating to WoA0_1_6 that the base folder for WoA0_1_6 is unzipped to within the WoA0_1_5 folder rather than to the home folder when updating from the older version in terminal. This causes errors which are dropping out the updating. I had to cut and paste the base folder to the home folder to get it working. Just to make sure, I cleaned out the lot and redownloaded from sourceforge, all OK now. **Is this something you need to fix for automatically updating from within the terminal ?**

If it matters I had launched WoA0_1_5 in terminal by navigating to the /home/<username>/WallofArt0_1_5/wallpapers and inputted "./install.sh". I tried to let sourceforge update it automatically when everying went wrong.

Once again thanks for releasing this program/script on the forum, great effort :-). A new wallpaper to look at every 10 minutes has made me very happy :lol: .

Regards from yetiman64.

**Edit**: Spaces issue now fixed here by extracting from and adjusting a shell script found in post #3 at  [noparse]http://www.computing.net/answers/unix/how-to-remove-spaces-in-filenames/8204.html[/noparse] and tested on a copy of one of my image directories copied to my desktop. (Note: URL is disabled, copy and paste to address bar if anyone needs to see it). I disabled the link as the script required several runs to completely do the job and may not be suitable for everyone.

Any script you update past 0_1_7 should be dumped in the home/user folder.... The latest script 0_1_9 has a problem with running the script after updating... for some reason it doesnt create the folders or copy the python files... I will fix this today. I have also added in the option to ask the user if they want to remove spaces from files if they choose to use it locally. I appreciate your input and assistance. Although I used a perl command to change the names of the files I appreciate your input. Thank you. =)

---

### Post by yetiman64 on 2011-01-06
> **JCarlin6 said:**
> Any script you update past 0_1_7 should be dumped in the home/user folder.... The latest script 0_1_9 has a problem with running the script after updating... for some reason it doesnt create the folders or copy the python files... I will fix this today. I have also added in the option to ask the user if they want to remove spaces from files if they choose to use it locally. I appreciate your input and assistance. Although I used a perl command to change the names of the files I appreciate your input. Thank you. =)

You're welcome, Just a clarification though, the script I got from my previous link was to change all of my media files manually at my end, not to use with your programming. I wouldn't stand a chance with that style of scripting.:)

Eagerly awaiting the 0_1_9 fixes (it unzipped nicely though this time). Cheers again. yetiman64

---

### Post by JCarlin6 on 2011-01-06
> **yetiman64 said:**
> You're welcome, Just a clarification though, the script I got from my previous link was to change all of my media files manually at my end, not to use with your programming. I wouldn't stand a chance with that style of scripting.:)

Eagerly awaiting the 0_1_9 fixes (it unzipped nicely though this time). Cheers again. yetiman64

Thanks for your continued support... I definitely need help with this last part... I absolutely cannot get the script to automatically open without it having problems recognizing the py files. I will continue trying but for those willing to help... when it updates it downloads and extracts the zip folder it then should run the new install script in a new terminal using this command 'gnome-terminal -x ~/WallofArt$LATEST/wallpapers/install.sh' were I am running into so much trouble is ONLY when I try running the new updated one from a bash script does it break and it doesnt know were the background.py and local.py file is located... were it should be in the folder keep in mind I have it referenced as... 

pyfile="background.py"
dest="/home/$ON_USER/wallpapers"

the cp command... 'cp $pyfile $dest' for some reason this is were it breaks ONLY WHEN UPDATING it doesnt break when running directly... so anybody have an idea why it cant find the background.py file which is in the same directory when I use this method?

so I definitely just figured it out but I'm not home right now so I'll fix it in a few hours but basically I think I need to change the directory before I executed I am sorry I was having a brain block

Wow easy fix. Done. Gonna work on other sites next... I HIGHLY suggest using the latest..

---

### Post by lemmy999 on 2011-01-07
@James

Got it working fine now. Using 0.23 and its brilliant!!

---

### Post by JCarlin6 on 2011-01-07
Thank you lemmy =) I am glad I could help. Now do me a favor and spread the word ;) when I hit 0_2_5 an article on slashdot would be cool lol

---

### Post by Dbays48 on 2011-01-10
WOOOOT!:popcorn:

---

### Post by JCarlin6 on 2011-01-10
I have added more functionality into the cron I soon hope to implicate anacron so I will be able to give the option for days weeks and months... Fixed the local support as it didnt remove spaces from image names properly now it works fine. 0_2_6

---

### Post by munnster on 2011-01-11
> **JCarlin6 said:**
> It stores it in your home folder more specifically (/home/user/wallpapers/) It does not contain a size limit yet but it will soon... A uninstall feature is included which removes the entire directory and a reinstall is pretty quick but its not gonna be too big of a problem especially since you can do a max of 1 per minute... It is VERY easy to remove all the wallpapers manually as well just select everything but the main wallpaper file and the py file and your good. Its clean. Is that something you would want before you installed it or something I can add in sometime this week? as a side note the uninstall also removes the cron jobs and reinstalling does not add more.

I emailed last night for help--I reinstalled it using images from wallbase.net and that works fine. I looked in /home/user/wallofart0_2_7/wallpapers folder to see if that was where the pictures were stored and they were not, so I knew I had it wrong and DID finally realize you did not say /home/user/*wallofart0_2_7/wallpapers*, so all is good. 

However I do have questions--is there a launcher for this that I am missing or must I reinstall if I want to change my options? Also is there a shortcut I can put in the folder so I don't have to move my pictures into the wallpapers folder, but lead the program to where my pictures are? 

Very good program though now that I have it working! Thank you so much for sharing with us!!

---

### Post by JCarlin6 on 2011-01-11
reinstall to change your options but thats a good idea I will keep that in mind.... Also I am glad you found out the problem. REMEMBER THOUGH if you uninstall then you will lose all images that are in that specific folder so take them out if you ever uninstall.

---

### Post by munnster on 2011-01-11
> **JCarlin6 said:**
> reinstall to change your options but thats a good idea I will keep that in mind.... Also I am glad you found out the problem. REMEMBER THOUGH if you uninstall then you will lose all images that are in that specific folder so take them out if you ever uninstall.

Thanks for the reminder! I will definitely keep that in mind!

---

### Post by JCarlin6 on 2011-01-11
I NEED IDEAS PEOPLE.... I have decided not to use deviantart as you cannot specify a resolution or ratio... Any other sites / Ideas?

---

### Post by munnster on 2011-01-11
[http://www.caedes.net/Zephir.cgi?lib=Caedes::Gallery&gallery=photography&page=3](http://www.caedes.net/Zephir.cgi?lib=Caedes::Gallery&gallery=photography&page=3)

This is a site I use for desktop backgrounds. I am not sure if this is the type of site you are looking for, but the pictures are amazing.

---

### Post by JCarlin6 on 2011-01-13
It needs a resolution and a ratio for an option.... Any others?

---

### Post by ki4jgt on 2011-01-13
How about Google Images? You can specify image sizes on that. I can't say the person will not get adult content there, but you can specify image size.

***EDIT: You could also try running DeviantArt through Google Images.

---

### Post by JCarlin6 on 2011-01-13
quick note... I added in a way to backup the original wallpaper so that if you uninstall then it is restored. And if you choose to use wallbase images can expire if you would like

---

### Post by JCarlin6 on 2011-03-07
FIXED.... Script updated and running...

---

### Post by JCarlin6 on 2011-12-24
Since I joined the military MONTHS ago I have had no time to update or keep my script going so if anyone wants to pick it up send me a pm or email me at [email]JCarlin6@gmail.com[/email] and let me know

---

### Post by zythaera on 2012-03-17
Hmm, maybe I might pick it up. Its friggin useful.

---

