---
title: "First time Wine user needs a little guidance"
date: 2010-12-12
forum: Wine
---

### Post by jwaclawsky on 2010-12-12
I "think" I just installed wine Version 1.3.9 properly. Using the terminal I installed wine on Ununtu 10.10 using the three commands given at ([http://www.multimediaboom.com/install-wine-1-3-8-in-ubuntu-10-10-maverick-ppa/](http://www.multimediaboom.com/install-wine-1-3-8-in-ubuntu-10-10-maverick-ppa/))  They are:
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3

Everything worked fine as far as I can tell. No error messages. But I can't seem to get any windows programs installed and running ...and how do I even know if WINE is installed properly? When I go to applications pull down wine does show up (see attached screen shot below) and I am able to use "config wine" (see next screen shot) and it looks like I have installed "Daimond DA40 G1000 Tra....exe" but I can not figure out how to get it to run. It isn't showing up under "Applications > wine > programs" (see the first screen shot - which shows only "accessories" under programs). I tried running from the terminal and I get 
"wine: cannot find L"C:\\windows\\system32\\Diamond.exe" see last screen shot of the terminal window. I have tried placing the exe file for the application on my desktop and tried running it from there and I get the same error shown in the terminal window screen shot a little further down. When I browse c: the application program is not showing up under program files (see third screen shot). My thoughts are that either wine is really not installed correctly or the application did not get installed from the Wine configuration menu. 

I used the wine configuration applications menu and clicked the add application button which opened a "select an executable file" window.Then I navigated up to dosdevices and selected the Z: drive which finds the application located on the DVD/CD drive. It "appeared to work correctly because it starts reading the disk for several minutes and then it puts the application name in the application settings window. Also there doesn't appear to be anything to click on to start it running in the wine configuration windows. Any help would be appreciated.
[ATTACH]178254[/ATTACH]

[ATTACH]178255[/ATTACH]

[ATTACH]178257[/ATTACH]

[ATTACH]178260[/ATTACH]

Thanks

---

### Post by SuperXDE on 2010-12-12
I suggest that you install [Winetricks]("http://wiki.winehq.org/winetricks") , which is a script to install all the required stuff for the programs to work in a windows environment ( Like Dot Net Framework , and visual C++ runtime and directX , if it rings a bell )

To install Winetricks , simply hit CTRL ALT T ( Hotkey to open terminal , if it is activated ) , and write

```
wget http://www.kegel.com/wine/winetricks 
```

*where wget refers to the downloader , and that URL ( aka link ) refers to the location of the file to be downloaded.*

After it downloads Winetricks , you'll have to set its permissions , you can do that by opening the Home folder ( Click on Places , in the Top Bar , then go to Home Folder ) then right clicking winetricks , then go to permissions tab , and tick the "allow executing as a program" , then hit Ok.

Now , after you have set the permissions , you just install the stuff required , like - for example :

```
./winetricks d3dx9
``` which installs DirectX 9 , according to the script.

[Check the official wine page about winetricks for more option]("http://wiki.winehq.org/winetricks")s to install , and make yourself as if you are on windows , downloading the required perquisites for its programs.

Hope I helped ... When I was looking on how to run Games on Wine , thinking that Wine was just useless crap - And I was wrong - , Didn't see anything about it , till late... and now its working , and Wine is more than just AMAZZZZZZZIIIIIIIINNNNNNG!! :D

Enjoy~! :popcorn:

---

### Post by 8Kuula on 2010-12-12
$ cd Desktop
$ wine ./Diamond\ DA40\ G1000\ Trainer\ v8.01.exe

or
$ cd Desktop
$ wine ./"Diamond DA40 G1000 Trainer v8.01.exe"

---

### Post by cwwilson721 on 2010-12-12
To install an application in wine (A bit easier to understand, with explanations)

Open a Nautilus windows and navigate to where the file you wish to install is located. (Places > <Wherever>)

Right click on the file, and choose "Open With Wine Windows Program Loader"

That should do it. If 'nothing' happens, open a terminal window, cd to where the file is, and try ```
wine FOO.exe
``` Replace FOO with program name.

Then watch the text go by.

---

### Post by jwaclawsky on 2010-12-12
Thanks 8kulla for the command syntax. When I typed it into the terminal window ($ wine ./"Diamond DA40 G1000 Trainer v8.01.exe"), it looks like it installed the application. It is now listed under applications > wine > programs  ...see the first screen shot. I "assume" the program is now correctly installed. It is also now listed in the C: directory under "Program Files".
[ATTACH]178282[/ATTACH]
But when I click on the program name at the top of the last panel shown in the screen shot, I get a "starting Diamond DA...." on the bottom Ubuntu launcher panel bar but then it goes away and nothing happens. Is there something else I need to do?

To SuperXDE: I installed winetricks and made the shell script executable and then ran it in a terminal as you directed. I got the "Select packages to install" list shown in the screen shot below. I stopped here because I am not sure what packages I should be checking. It looks like there are over 200 of them. Should I be installing all of them?  BTW I did the ./winetricks d3dx9 in a terminal and this ran correctly with lots of "All done, no errors" messages ...but the application still doesn't run? ...is that because I need to be installing packages from the list of "Select packages to install"?
[ATTACH]178286[/ATTACH]

Further advice is appreciated. Thanks!

BTW, I also did what cwwilson suggested and was able to do an install by navigating through Nautilus to where the program is located and right click and select "Open With Wine Windows Program Loader"! That works fine, no errors. ...but once installed the application still doesn't run.

---

### Post by 8Kuula on 2010-12-12
It may be it just do not agree with wine.

[http://appdb.winehq.org/](http://appdb.winehq.org/)
There is wine application database, if someone has tested and get it to work.

<edit>
But run that program on terminal like:
$ cd to/where/program/is/located
$ wine ./exefile.exe

So you can see what error messages it gives and maybe someone can help.
</edit>

---

### Post by jwaclawsky on 2010-12-12
ok, I did try to run it in a terminal and look for error messages. But, how do I get to the C: drive (used by wine) in the terminal???  hopefully I can then do a cd to the Program directory in c: and try to run the program from there? and look for error messages. Thanks! 

...BTW. I did do a cd .wine and a cd drive_c but I can't do a cd Program Files. I get an error message.

---

### Post by jwaclawsky on 2010-12-12
I did do a cd .wine and then a cd drive_c but I can't do a cd Program Files from the terminal window. I get an error message (see screen shot). The error message seems to indicated that it only sees the word "Program" and not the whole directory name "Program Files". Can you do a cd to a directory with two words with a space between them as a name? 
[ATTACH]178292[/ATTACH]

...or is there another way to get to the program directory for Wine applications using the terminal window? Thanks

---

### Post by Soulcage on 2010-12-13
cd ~/.wine/drive_c/Program\ Files/Blah/

---

### Post by jwaclawsky on 2010-12-13
Thanks soulcage. You have moved me a little further along. I am now able to get to the Program Files directory but I need to go one more directory further. Can you or someone tell me the syntax I need in the terminal window to next do a cd to the directory called "Diamond DA40 G1000 Trainer v8.01" which has 5 words in the directory label separated by blanks (please see the screen shot from the "ls -l" command). I am still with my original problem that the program won't run but I hope to start the program in the terminal and finally see what error messages etc I get.   
[ATTACH]178310[/ATTACH]

---

### Post by mastablasta on 2010-12-13
have you tried puttin the folder in quotes ? "folder with long name"

---

### Post by jwaclawsky on 2010-12-13
Thanks mastablasta. The directory name in quotes worked. Now back to getting the application running...

---

### Post by jwaclawsky on 2010-12-13
I am trying to run a airplane GPS/navigation trainer under Wine. I tried running the program in a terminal and got some error message so I will open another thread for the sake of clarity. This thread is closed and my new wine user issues are solved. Thanks!

---

