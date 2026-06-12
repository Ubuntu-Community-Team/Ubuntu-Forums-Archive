---
title: "Installing the play-framework on Ubuntu"
date: 2012-10-19
forum: Tutorials
---

### Post by kevinl on 2012-10-19
I thought I should share an experience I have had trying to install the play-framework on Ubuntu.  It is possible you may not know about the play-framework.  It is the means by which you can "simply" build interactive web-pages.  (For more details beyond that, go to [http://www.playframework.org/](http://www.playframework.org/)) I say "simply" because even the simple in this field of endeavour is confusing to a new-comer so don't for a moment think that simple=easy.

The documentation on the play-framework webpage is of little help to a newcomer.  If you google installation, you find others trying to be helpful who actually give you incorrect information and that makes the whole thing doubly confusing.  So I thought I would take the time to tell anyone who is interested my experience (which has consumed a morning), in the hope of saving you the same aggravation.

_Creating a Folder for the Play-Framework Application_To install the play-framework on Ubuntu 12.04 (and I suspect this would work with other earlier versions and may continue to work with future versions), you should firstly create a folder within your "home" directory. For a beginner, this is best done by opening the browser provided by Ubuntu's Unity Interface (the brown folder icon).  If you are comfortable using bash in the command line interface, then you will know how to do this.  For the beginner, having opened the file browser, you will see at the top left hand column, the home icon, and in the right column you will see a list of folders. (I would show you a screenshot but this editor doesn't make that easy so we'll just have to make-do with words. :() With "Home" highlighted, go to "File" (which is hidden from view along the top edge of your screen.  You have to move the mouse cursor up there and it will expose itself.) and select "Create New Folder".  Then, in the space provided, type "temp4play".

_Download the latest stable Play-Framework in a ZIP File_  Normally, Linux applications are presented in a tar file.  Windows applications commonly use ZIP.  Don't worry.  The file they are giving you is intended for Linux and will run on Ubuntu.
Go to [http://download.playframework.org/releases/](http://download.playframework.org/releases/) (or wherever they have subsequently chosen to put it. If it is not there, look at their documentation on how to install play to find out if they have changed it.).  In my case, I downloaded play-2.0.4.zip.  It is important you download the file into the new folder, "temp4play", you have created within your "Home" directory.  If you don't download it into your "Home" directory, you will have all sorts of issues running it and you really don't want that sort of pain at this moment in your learning experience!

_Unzipping the Play-Framework ZIP File_. Once the file is downloaded, locate and highlight it in your file browser, right click on it and select "Extract Here".  In my case, a new folder appears called "play-2.0.4" and beneath that folder are all sorts of lovely files and folders!  Success... Yeah!!:P... well almost:(

_Copying the folder "play-2.0.4" to the Home folder_.  Right-click on the "play-2.0.4" folder, located within the "temp4play" folder. Select "Copy" from the context-box.  Now right-click "Home" and select "Paste Into Folder" from its context box.  "play-2.0.4" and all the files and directory within "play-2.0.4", will appear in the list of folders within "Home".  Once that is done, highlight the "temp4play" folder by clicking once on it and then, holding down the shift key, press the delete key.  You will be asked if you permanently want to delete "temp4play".  Say "Yes" as you have previously copied "play-2.0.4" and all its contents to the "Home" folder.  

_Putting the "Play-Framework" Application in your Path_.  In order to check if you have properly installed the play-framework application you are advised in their installation instructions to go to a terminal window and type in "play help".  It won't work!!:confused: ...for a number of reasons!  The first relates to the fact that if you are not in the directory in which the executable file "play" exists, Linux, can't find it.  If you are in the folder in which "play" exists and you type "play help" it won't work either.  That's because our forefathers, the creators of UNIX, didn't know the word "user-friendly" when UNIX was invented.  Linux firstly looks to a thing called the "PATH" to see if it can find "play" anywhere on your machine (and there are evidently good reasons from the point of view of security why it does this!).  If you want to execute an executable file that is located in the directory _in which you are in_, typing "play" will not work!  Instead, you must type "./play" and then there is some prospect of it working. If you don't put the "./" in front of the file's name, LINUX goes firstly to its PATH definition and then gives up... maybe!!  In the case of a standard Ubuntu 12.04 distribution, LINUX might find "play" but this executable file, called "play", has nothing to do with the play-framework. It's to do with another application, called SoX, which is an audio application!  Now here is the really confusing thing. If you haven't installed SoX, Ubuntu helpfully suggests you can remedy the absence of "play" by installing SoX by executing, in the command line, apt-get install sox.  So by now you may well be getting just a little frazzled.:mad:

If you want to be able to run the play-framework from other places, you have to include the directory path in which the executable file, "play", exists.  In my case, it is in "/home/[myname]/play-2.0.4".  Another pitfall awaits you.  If you follow instructions provided by the play-framework installation page, you will use the "export" command (which is very poorly expressed by whoever wrote it) and it will place "/home/[myname]/play-2.0.4 at the end of the PATH specification.  Because there is a path before your path description in the path specification that contains an executable file called "play", the play you want to play won't play:confused::(.  You have to ensure the path to your play, is at the beginning of the PATH specification. LINUX executes the first instance of "play" if finds as it systematically goes through the directory listings provided in the PATH specification.

_Editing the .bashrc file_.  To "permanently" change the PATH specification, so that every time you log on you do not have to perform an export command, you have to edit the .bashrc file located in your home directory. You can either do this in a terminal window using a text editor, such as "nano", or you can do it using the graphical user interface by finding the file in the file browser and then editing it with "gedit".  The latter is the course I recommend for new-comers.  There is less chance of you making a mistake.  Do the following:
[LIST]
[*]Open up the file browser and go to the "View" command (hidden from view until you put the cursor in the top of your screen).
[*]Within "View" you will find "Show Hidden Files".  _Make sure this is ticked._  (The "." in front of the "bashrc" indicates this is a hidden file and not normally visiable in the directory browser).
[*]With "Home" highlighted in the left column, click on any folder in the right column and start typing ".bashrc".  The browser will helpfully find the ".bashrc" file for you.
[*]Right click on the file and select "Open with Text Editor".  Do not open it with another application unless you really do know what you are doing!!
[*]When the ".bashrc" file opens, go to the bottom of the listing and type in the following (Note: It is case sensitive - another delight of LINUX!! where I have [myname] insert the name of your home directory.. in Ubuntu, it will most probably be your name.) [COLOR="Navy"]**export PATH""/Home/[myname]/play-2.0.4:$PATH""**[/COLOR]
[/LIST]
The two sets of double quotes are necessary in this command.  My version of play is 2.0.4.  It is possible this could be different for you so make sure the name of the folder you specify is exactly the same as the name of the folder, which you previously copied to the "Home" folder, and in which the "play" executable file is located. For me, this command placed the path to the folder, "play-2.0.4", at the front of the PATH specification. (Now the downside of this is that, if you use the SoX application, it will most probably not work.  I'll leave that little drama to someone more knowledgeable.)

Once you have inserted the command, save the file by clicking, "File, Save".  Now you have to log out of Ubuntu and log back in again so that the ".bashrc" file takes effect.  Once you have done this, if you go to a terminal window and type "play help" the play-framework should run.:guitar:  

If it doesn't then please let us know and tell everyone how you solved your problem, thereby adding to the common-wealth of knowledge.

I hope this has been helpful to anyone faced with the same problem.  I looked at providing input into the play-framework website but found that was just too difficult and gave up! 

If anyone involved in the play-framework should read this, I hope you will make things easier for people who are not expert to contribute suggestions.  My friends tell me the play-framework is well worth the trouble to learn and it would be a shame if the introduction is so difficult it deters beginners.  Without beginners we will not have experts and that's not good for humanity or the things we love.  (Speaking of friends, I wish to thank a long-suffering colleague of mine, Wesley Young, for helping me with my enquiries as I muddled my way through this problem.)
KAL

---

### Post by cariboo on 2012-10-21
This really needs to be redone, for better readability. Perhaps when it is moved to the wiki, the op can reformat it.

---

### Post by kevinl on 2012-11-08
I would be very pleased if you were to amend this in anyway you feel would make it more readable.

By doing that I would learn what people find easy to follow and so improve on any future posts I make.   An "object example" is far better than a lengthy instruction. So use my post as an example if you wish. Please don't worry about my taking any offence. I won't.  

KAL

---

### Post by diegomagdaleno on 2012-12-10
KAL,

In first place, I'd like to thank you for the help. What you said about people giving incorrect information was true and your post is the best I have found for this issue.

But, with all the compliments, I had to make one little correction on the given command line to type in the .bashrc file:

```
export PATH**=**""/home/[myname]/play-2.0.4:$PATH""
```

I had to put the **=** (assignment operator) to get the wishing result.

Hope this can help others..

See ya!

---

### Post by karan.hiremath on 2013-07-02
For everyone who can't read all this/are looking to add play to their path entirely through terminal (as most people using play probably want to anyways):

1. Edit the .bashrc file (if it doesnt already exist this will add it as well):
```
vi ~/.bashrc
```

2. Add the following line to the bottom of the file
```
export PATH=""/home/[username]/play-[play version]:$PATH""
```

3. Sanity check to see if play is installed
```
play help
```

4. In any new directory run the following to create a new play application
```
play new [name of app]
```

---

