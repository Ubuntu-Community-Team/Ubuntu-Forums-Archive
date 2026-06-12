---
title: "NeverNote, an Evernote clone for Linux!"
date: 2010-07-03
forum: The Cafe
---

### Post by L4U on 2010-07-03
I just stumbled across this:

> Welcome to NeverNote.

This is an incomplete clone of Evernote designed to run on Linux.

You can download NeverNote [here](http://www.evernote.com/pub/baumgarr/nevernote). 

[http://nevernote.sourceforge.net/](http://nevernote.sourceforge.net/)


Fantastic!  :)

---

### Post by L4U on 2010-07-03
If someone can write an easy install guide for noobs, that would be much appreciated!  ;)

---

### Post by NormanFLinux on 2010-07-04
Evernote 3.1 will install and run with no issues under WINE.

---

### Post by doublewitt on 2010-07-04
> **NormanFLinux said:**
> Evernote 3.1 will install and run with no issues under WINE.

For some - yes, and others - no
Would like to be able to install this file (NEVERNOTE)...!

---

### Post by Lucradia on 2010-07-04
lol, it's written in JAVA?

Good work, a lot of people actually don't use or have JAVA installed on linux.

---

### Post by juancarlospaco on 2010-07-04
[I]lol, Java, it needs the Oracle Virtual Machine installed, 
Evernote runs on Wine that is not a Virtual Machine.[/I]

---

### Post by L4U on 2010-07-04
Anywho, can someone write a noobs guide to install Nevernote?

---

### Post by doublewitt on 2010-07-09
I downloaded the required files and all I need to know now, is how to get Nevernote to work...

---

### Post by HelloIndustries on 2010-07-12
I use EverNote on my work PC (win7), my iPhone and both my Ubuntu and WinVista installs at home.

I find that using Prism to run the web version of EverNote is good enough for me.

---

### Post by MrPok on 2010-07-14
> **L4U said:**
> I just stumbled across this:



Fantastic!  :)

Wow that *is* fantastic! I came across this thread while googling on how to install the Windows Evernote 3.5 on Ubuntu under Wine; that is supposedly problematic.

I will definitely try it out when I find the time..!

---

### Post by soro2005 on 2010-07-16
For those asking for installation instructions: They are in the Install.txt that you can find inside the nevernote-VERSION-NO.tar.gz that you currently have to download from the author's Evernote shared notebook. Roughly, you have to:

1. Make sure you have a java runtime installed (Sun Java Runtime Environment or OpenJDK Java Runtime should both do)
2. Download QT Jambi Binary for your architecture from [http://qt.nokia.com/downloads](http://qt.nokia.com/downloads) (direct links are currently [32bit](http://get.qt.nokia.com/qtjambi/source/qtjambi-linux32-lgpl-4.5.2_01.tar.gz) and [64bit](http://get.qt.nokia.com/qtjambi/source/qtjambi-linux64-lgpl-4.5.2_01.tar.gz). It's quite a chunky download!
3. Extract the QT Jambi stuff by double-clicking on it. Extract the entire directory to some location where it is out of the way.
4. Also extract the nevernote-xyz.tar.gz to some location from where you want to run it.
5. Locate the file nevernote.sh inside the directory that you have just extracted. Open it with Gedit or the text editor of your choice.
6. Pretty much at the top of the file, there are four lines starting with "export". In the first two of these, you have to replace the example paths with the ones that reflect the places to which you have just extracted Nevernote and QT Jambi respectively. The Jambi Version should currently not need to be changed, and in the line with Jambi Platform, you may have to replace linux32-gcc with linux64-gcc if you have a 64bit system. Save nevernote.sh after you have edited it.
7. Right click on nevernote.sh and select "Properties," then the tab called "Permissions." Check "Allow executing file as program."
8. Double-click on nevernote.sh and select "Run" in the dialog that opens.
9. If 8 doesn't work, try opening a terminal, navigating to the place where you have extracted nevernote, and starting the script from the terminal. Like this:
```
cd /home/yourusername/directory-that-contains-nevernote.sh
./nevernote.sh
```
I agree with those comments above who suggest that a Java app is not precisely what everybody was hoping for, and the QT Jambi stuff is a heavy dependency. It's the author's decision, though, and we should be grateful for his work. In the end, it's Evernote who shun their Linux users. Shame on them!

---

### Post by dziemecki on 2010-07-27
This is a pretty good app.  One less reason to use Windows.  If this guy could set up a repository and a deb package so that the install wasn't so manual, it would be just about perfect.

---

### Post by MrPok on 2010-07-27
> **dziemecki said:**
> This is a pretty good app.  One less reason to use Windows.  If this guy could set up a repository and a deb package so that the install wasn't so manual, it would be just about perfect.
Yeah about that, he doesn't seem to keen on doing all that -- when I asked where to send *bug reports* (as the sourceforge bugtracker for the nevernote project was empty) he stated something which I could only interpret as that I should send them in manually/forum-post(?), he would close-down the sf bugtracker, and all of this was not appropriate for "*a project this size*". The latter struck me as a bit odd, since Nevernote doesn't seem that trivial a project. I wonder why he is doing this project? hmm I wonder... 

Perhaps anybody over here could *offer him* to take care of the deb packaging. Eventhough installation instructions are pretty simple..still getting the installation as low-entry as possible could lead to a faster increase of people using Nevernote, which in turn might persuade him to get a repository up etc. etc. etc. </ speculation mode>

Then again, personally I would rather see the guys at Evernote put more development in the web app, so I don't have to keep installing clients..

imho...

---

### Post by dziemecki on 2010-07-28
> **MrPok said:**
> I wonder why he is doing this project? hmm I wonder...

I'm guessing he likes Evernote and uses Linux.  I've been willing to do as much to scratch what I thought was probably an itch very few others felt.

> **MrPok said:**
> Then again, personally I would rather see the guys at Evernote put more development in the web app, so I don't have to keep installing clients..

... or at least a native client.  Maybe they'll catch wind of the project and take it off his hands.  Hell - since it's in Java, they could even use it as the basis of a single code base.

One can dream...

---

### Post by doublewitt on 2010-09-06
I got this working...!
Looks good (promising...).

Is anyone "happy" with this application...?
So far I have no problems with it...
hope it stays that way!

---

### Post by rjgonza on 2010-09-06
I just stumbled across this as well, I think its great!  As for the java haters, I don't know why you would think that is an issue, Java is seriously eveywhere, I am sure that everyone installing linux and everyone that is at the point of looking for evernote to be installed on linux already has java.

From the forums and the site it looks like the guy is asking for help from anyone willing to give it.  Does anyone have evidence to the contrary?  I would like to get involved in this project and help it out, this would be my first development project for linux :D

But overall I think this thing is AWESOME!

---

### Post by doublewitt on 2010-09-07
To add more tools, you can download the web clipper for firefox here:

[http://linux.softpedia.com/get/Internet/Firefox-Extensions/Evernote-Web-Clipper-Firefox-40713.shtml](http://linux.softpedia.com/get/Internet/Firefox-Extensions/Evernote-Web-Clipper-Firefox-40713.shtml)

you can run this extension on linux as well...

now you have nevernote + the web clipper...!


there is also an evernote webclipper extension for the chromium browser...

so far I like this APP - Nevernote. I think it's a great start...

---

### Post by baumgarr on 2010-09-15
Wow.  I stumbled across topic this by accident.  I'm the one who has written about 99% of NeverNote, so I can answer some of the questions.


[LIST]
[*]The most common question I get is why Java?
[/LIST]
There are a few reasons.  First, Evernote provides a working sample so it was easy to start.  Second, I'm stuck using Windows a good deal of the time and it helps being able to cross-develop.  Third (and probably the biggest) is that I never intended to do this or distribute it when I started. This whole thing began as an idea that later proved impractical.  By the time I realized how impractical it was I was a good deal of the way through the back end logic for a full client.  Honestly, I figured someone else would have developed a native Linux version long before now.  

Writing it in Java was probably the hardest decision.  I'd have preferred a C/C++ app, but Java allowed me to be lazy & get it done more quickly.  In reality, Java has worked out much better than I imagined it would.


[LIST]
[*]Why use Jambi?
[/LIST]
I initially didn't.  I wanted something that appeared as close to a native looking application as possible and (IMHO) Swing apps never truly look or act quite right.  I started with SWT, but ran into issues.  Qt's toolkit was easier & there were a ton of examples so I took the easy way out.  I also figured that if I ever needed to rewrite it to C++ a lot of the Qt logic would remain the same and I could do it in chunks since (in theory anyway) you can easily tie the two together. 


[LIST]
[*]Why not use Wine?
[/LIST]
I did initially, but since Evernote's 3.5 version won't run under Wine I was afraid they'd eventually break compatibility & I'd be stuck.  I REALLY dislike the web app.


[LIST]
[*]Why not a deb or install program?
[/LIST]
It was always on the list of things to do, but mainly time kept it from being done.  Up until recently there were only a few people using it and my time isn't unlimited so I focused mainly on getting features completed.  Spending time on something that 5 people would use once just didn't seem practical considering there was definite work needed to make the program as a whole usable.  Most Linux people are comfortable enough with command files that I thought the instructions were "good enough" for the time being.  Since enough people have started using it, I've created some debs & they will be available for the next release.

The lack of an easy install is also what has been preventing me from asking it to be added to Evernote's "Trunk".  


[LIST]
[*]Why don't I use bug tracker or why use the forum to report bugs?
[/LIST]
I've re-enabled the bug tracker so it is available now, but I initially disabled it because I didn't want to have people post the same bug multiple times in multiple places.  The forums were easy enough for a novice person and provide an easy way to help someone if a workaround exists.  I also thought a formal bug tracker was a bit overkill since I was the only person doing any coding at the time.  I had a list & that was enough for me to know what was broken.  I still think it is a bit more than I need, but since a couple of people have begun to help a little with the work, it helps keep things from falling under the radar.  

Anyhow, sorry for the long post & I'm glad people like it.

---

### Post by Nisuspi on 2010-09-19
Just a small note to add my appreciation for baumgarr's work here. Evernote is an incredibly valuable tool for me, and Nevernote is working flawlessly on 10.04 here. Much better than the Wine or web clients.

---

### Post by doublewitt on 2010-09-20
> **Nisuspi said:**
> Just a small note to add my appreciation for baumgarr's work here. Evernote is an incredibly valuable tool for me, and Nevernote is working flawlessly on 10.04 here. Much better than the Wine or web clients.

I agree, this is working very well...! The deb package is great! So far, the application is very stable. I appreciate having an Evernote clone for Ubuntu. NEVERNOTE is really good... wow - I'm so happy I got this...

---

### Post by pheidrias on 2010-09-22
There is a .deb now!

[http://sourceforge.net/projects/nevernote/files/](http://sourceforge.net/projects/nevernote/files/)

Works fine with me (Lucid Lynx 10.04)!

Only thing I'm missing now is a "minimize to tray" functionality to keep the panel clean...

Thanks a lot!

---

### Post by alexrb on 2010-09-29
I'm getting "Syncronization thread has died" error last two days.
Installed from deb.
Any ideas how to fix?

---

### Post by baumgarr on 2010-09-29
Under Edit/Preferences set the debugging level to extreme then synchronize.  Look under ~/.nevernote/logs.  The syncrunner.log should contain more information.

---

### Post by baumgarr on 2010-09-29
Something else.  Please run it from a terminal and give any console output.  The startup is /usr/share/nevernote/nevernote.sh

thanks.

---

### Post by alexrb on 2010-10-02
terminal writes:
> Exception in thread "Synchronization Thread" java.lang.NullPointerException
	at org.apache.thrift.protocol.TBinaryProtocol.writeString(TBinaryProtocol.java:174)
	at com.evernote.edam.type.Note.write(Note.java:1542)
	at com.evernote.edam.notestore.NoteStore$updateNote_args.write(NoteStore.java:29859)
	at com.evernote.edam.notestore.NoteStore$Client.send_updateNote(NoteStore.java:2843)
	at com.evernote.edam.notestore.NoteStore$Client.updateNote(NoteStore.java:2833)
	at cx.fbn.nevernote.threads.SyncRunner.syncLocalNotes(SyncRunner.java:492)
	at cx.fbn.nevernote.threads.SyncRunner.evernoteSync(SyncRunner.java:334)
	at cx.fbn.nevernote.threads.SyncRunner.run(SyncRunner.java:175)
	at java.lang.Thread.run(Thread.java:636)
	at com.trolltech.qt.QThread.run(QThread.java:164)


---

### Post by alexrb on 2010-10-02
this is syncrunner.log
> 2010-10-02 09:38:42.268 getting user from userstore
2010-10-02 09:38:42.541 Saving user information
2010-10-02 09:38:42.549 Getting sync state
2010-10-02 09:38:44.468 Full Sequence Before: 1217764921000
2010-10-02 09:38:44.469 Last Sequence Date: 1285997977426
2010-10-02 09:38:44.470 Update Count: 184
2010-10-02 09:38:44.472 Last Update Count: 184
2010-10-02 09:38:44.473 Uploading changes
2010-10-02 09:38:44.474 Entering SyncRunner.syncExpunged
2010-10-02 09:38:44.475 Entering DeletedTable.getAllDeleted
2010-10-02 09:38:44.480 Leaving DeletedTable.getAllDeleted
2010-10-02 09:38:44.488 Leaving SyncRunner.syncExpunged
2010-10-02 09:38:44.489 Entering SyncRunner.syncLocalTags
2010-10-02 09:38:44.494 Getting remote tags to compare names with the local tags
2010-10-02 09:38:44.819 Entering SyncRunner.findNextTag
2010-10-02 09:38:44.822 Leaving SyncRunner.findNextTag - no tags returned
2010-10-02 09:38:44.823 Leaving SyncRunner.syncLocalTags
2010-10-02 09:38:44.824 Entering SyncRunner.syncLocalNotebooks
2010-10-02 09:38:44.826 Getting remote notebooks to compare with local
2010-10-02 09:38:45.132 Getting local dirty notebooks
2010-10-02 09:38:45.134 Leaving SyncRunner.syncLocalNotebooks
2010-10-02 09:38:45.135 Entering SyncRunner.syncNotes
2010-10-02 09:38:45.212 Active dirty note found - non new
2010-10-02 09:38:45.213 Active dirty found - new note
2010-10-02 09:38:45.214 Creating note : 1285573903069 <title>&#1085;&#1086;&#1084;&#1077;&#1088; MTS </title>
2010-10-02 09:38:45.613 *** EDAM User Excepton syncLocalNotes EDAMUserException(errorCode:BAD_DATA_FORMAT (BAD_DATA_FORMAT),$
2010-10-02 09:38:45.619 EDAMUserException(errorCode:BAD_DATA_FORMAT (BAD_DATA_FORMAT), parameter:Note.title)
2010-10-02 09:38:45.620 Active dirty note found - non new
2010-10-02 09:38:45.622 Updating note : 3f3a7723-3737-4659-883a-3ebd95e32a31 <title>&#1052;&#1086;&#1083;&#1080;&#1090;&#1074;&#1072; &#1076;&#1077;&#1074;&#1091;&#1096;&#1082;&#1080; &#1086; &#1079;&#1072;&#1084;&#1091;&#1078;&#1077;&#1089;&#1090;&#1074;&#1077;</title>

---

### Post by sdowney717 on 2010-10-02
how interesting. 
I just synced nevernote with my evernote web account and it worked.
Thank you for doing this programming.

adding it syncs fine both ways

---

### Post by sdowney717 on 2010-10-02
> <title>&#1052;&#1086;&#1083;&#1080;&#1090;&#1074;&#1072; &#1076;&#1077;&#1074;&#1091;&#1096;&#1082;&#1080; &#1086; &#1079;&#1072;&#1084;&#1091;&#1078;&#1077;&#1089;&#1090;&#1074;&#1077;</title>  

any trouble with unicode perhaps?

you got an error on the title, bad format
> 2010-10-02 09:38:45.613 *** EDAM User Excepton syncLocalNotes EDAMUserException(errorCode:BAD_DATA_FORMAT (BAD_DATA_FORMAT),$
2010-10-02 09:38:45.619 EDAMUserException(errorCode:BAD_DATA_FORMAT (BAD_DATA_FORMAT), parameter:Note.title)

---

### Post by baumgarr on 2010-10-02
It looks like Evernote is rejecting the note with the title of "&#1085;&#1086;&#1084;&#1077;&#1088; MTS "  I'm wondering if there is some type of non printable character at the end of the note that is causing the problem.

There is a large unicode problem with this last release that a couple of people came across, but it deals with garbling the text in the note and not the title.  Once I have confirmation from one of those people I'll push out a 0.91 release that should correct the unicode problem.

This type of error also shouldn't cause the thread to die.  You should just see an error message that an error has happened.  The null pointer makes me think that something is wrong with the content of the note itself.  

Here are some things you might want to try.

Try changing the title of the note.  The Evernote error says something is wrong with the title.

You may want to try changing the note (just add a space somewhere) and see if the problem is gone.  

If you are using non-english characters in the note it could be that the unicode bug I mentioned above is impacting you.  If so, try 0.91 when it is out in a day or two.  You might need to delete & recreate the note or copy the note contents to a new note.

Let me know if anything helps.

Thanks.

---

### Post by MuseFan on 2010-10-02
Awesome! Finally a worthy substitute for Evernote on Linux :)

---

### Post by baumgarr on 2010-10-03
I've uploaded 0.91, so hopefully that should correct any unicode problems.

Thanks.

---

### Post by kmajor on 2010-10-06
I just want to say THANKS SO MUCH!!!!!!
The wine version, was pretty flaky and now finally I have a native app that works GREAT.  Thank you thank you thank you.

-kev

---

### Post by TSJason on 2010-10-06
I just wanted to comment and say how much I appreciate nevernote for linux. It is much more elegant than running evernote 3.1 in wine. Thanks for all your hard work on this!

---

### Post by kurtpete on 2010-10-06
Just wanted to join the "me too" crowd in thanking you for this application.  Your work is very much appreciated!

---

### Post by baumgarr on 2010-10-06
Your all welcome.  I'm glad to know you find it useful.

---

### Post by pteglia on 2010-10-07
I just wanted to say that I appreciate the work as well.  I got out here to look to see if Evernote had yet gotten around to a Linux port, and nope, but I came across this.  Thanks, a lot.

Pat

---

### Post by Carnwaj on 2010-10-07
Thank you very much for producing this app. Fantastic piece of work.

---

### Post by Zorael on 2010-10-08
**@baumgarr**;

First of all, lovely program. Some questions and notes though.

How do I create a note and attach a pdf? The only way I found so far was to right click -> copy the file in a file browser (Dolphin) and then Paste it in a new Note in Nevernote. But then it refuses to display it inline for some reason, and only shows a small box with a question mark instead. I couldn't find an Attach button, or better yet, something like "post file as note".

Also, if you're using Ubuntu why not create a PPA to host your debs? It would make it easy for the rest of us to just '**sudo add-apt-repository ppa:baumgarr/nevernote**' and let our package managers monitor for updates. :3

On a separate note, I really wish Java programs had a native Oxygen look-and-feel. Cleanlooks seems the least horrible, but still has that KDE 2 feel to it.

---

### Post by baumgarr on 2010-10-08
You should be able to copy a file into a note the way you described.  

To display a PDF inline, there is an option under Edit/Preferences.  If it is checked the PDF will display inline as an image, otherwise it should show a PDF icon.  

The blue question mark typically means a missing image, which indicates a problem.  The PDF library I'm using doesn't display every PDF perfectly but if it has a problem it should fall back to the generic PDF icon, not a question mark.  My guess is that the image isn't being created properly.  Have you tried it with multiple PDFs?   

When you are displaying it in a note, the actual image for the preview is stored in ~/.nevernote/res/.  Can you see an image in that directory that looks like the first page of the PDF?

Try running from a terminal and set the debugging level to extreme (under Edit/Preferences) and paste it again.  Look under ~/.nevernote/logs for any problems.  I'd look in the nevernote.log and the saverunner.log.

A potential workaround would be to setup an automatic import folder (look under the Tools menu).  Then, copy the PDF to that folder.  It should create a note with that PDF automatically.  

Why I don't create a PPA... are ignorance & lack of time a good enough excuse?  I only started creating a deb a few weeks ago. I haven't had time to think about things like that.  I've been trying to fix bugs & add enough stuff to get to version 1.0 before Christmas of 2033.  :)

As for the look & feel, you can install style sheets under /usr/share/nevernote/qss.  I've never been any good at things like that (rather obvious from the feel of the program as a whole) but if you come up with something good I'll be more than happy to include it in future releases.  You just need to rename it to "default.qss" and restart.  I haven't integrated any sort of online dialog to change them since there are only two (and the other is even uglier).

Thanks for debugging & sorry to hear about your cat.

---

### Post by doublewitt on 2010-10-08
> **baumgarr said:**
> A potential workaround would be to setup an automatic import folder (look under the Tools menu).  Then, copy the PDF to that folder.  It should create a note with that PDF automatically.
I appreciate the "automatic folder import option" - *nice...!*

---

### Post by BungleFeet on 2010-10-10
Lovely stuff! I've been waiting an age for a Linux Evernote app. Well done.

Cheers,

Bungle

---

### Post by xannaxprozaxx on 2010-10-14
Thanks a million

---

### Post by BCingyou on 2010-10-16
I made an ubuntuforums account for the sole purpose of saying thanks.  Evernote is probably the only absolutely indispensable application in my daily life and I was never able to quite get it working satisfactorily with Wine or the other hacks.  This is beautiful, thanks a lot!

---

### Post by timbo-lino on 2010-10-27
Hi, I just installed NeverNote using the 64bit deb package:
[http://sourceforge.net/projects/nevernote/files/Current/nevernote-0.92.1_amd64.deb/download](http://sourceforge.net/projects/nevernote/files/Current/nevernote-0.92.1_amd64.deb/download)

When I start NeverNote I just get some error messages
```

user@machine:~$ /usr/share/nevernote/nevernote.sh
Exception in thread "main" java.lang.ExceptionInInitializerError
    at com.trolltech.qt.QtJambiObject.<clinit>(QtJambiObject.java:60)
Caused by: java.lang.RuntimeException: Loading library failed, progress so far:
Unpacking .jar file: 'qtjambi-linux64-gcc-4.5.2_01.jar'
Checking Archive 'qtjambi-linux64-gcc-4.5.2_01.jar'
 - skipping because of wrong system: trying to load: 'linux64', expected: 'linux32'
Loading library: 'libQtCore.so.4'...
 - using 'java.library.path'

    at com.trolltech.qt.internal.NativeLibraryManager.loadNativeLibrary(NativeLibraryManager.java:431)
    at com.trolltech.qt.internal.NativeLibraryManager.loadQtLibrary(NativeLibraryManager.java:355)
    at com.trolltech.qt.Utilities.loadQtLibrary(Utilities.java:140)
    at com.trolltech.qt.Utilities.loadQtLibrary(Utilities.java:136)
    at com.trolltech.qt.QtJambi_LibraryInitializer.<clinit>(QtJambi_LibraryInitializer.java:56)
    ... 1 more
Caused by: java.lang.UnsatisfiedLinkError: /usr/lib/libQtCore.so.4.6.2: /usr/lib/libQtCore.so.4.6.2: wrong ELF class: ELFCLASS64 (Possible cause: architecture word width mismatch)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1803)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1699)
    at java.lang.Runtime.load0(Runtime.java:770)
    at java.lang.Runtime.load(Runtime.java:758)
    at com.trolltech.qt.internal.NativeLibraryManager.loadLibrary_helper(NativeLibraryManager.java:478)
    at com.trolltech.qt.internal.NativeLibraryManager.loadNativeLibrary(NativeLibraryManager.java:426)
    ... 5 more
Could not find the main class: cx.fbn.nevernote.NeverNote.  Program will exit.
/home/user

```

Does someone has an idea what is going wrong here?

Thanks!

---

### Post by juancarlospaco on 2010-10-27
**[http://www.giuspen.com/cherrytree/](http://www.giuspen.com/cherrytree/)**

*See the screenshots, its really nice, save the file to U1 and ready to go...*

---

### Post by koleoptero on 2010-10-27
> **juancarlospaco said:**
> **[http://www.giuspen.com/cherrytree/](http://www.giuspen.com/cherrytree/)**

*See the screenshots, its really nice, save the file to U1 and ready to go...*

That looks nice indeed. I'll give it a go tomorrow.

---

### Post by baumgarr on 2010-10-27
> **timbo-lino said:**
> Hi, I just installed NeverNote using the 64bit deb package:
[http://sourceforge.net/projects/nevernote/files/Current/nevernote-0.92.1_amd64.deb/download](http://sourceforge.net/projects/nevernote/files/Current/nevernote-0.92.1_amd64.deb/download)

When I start NeverNote I just get some error messages
```

user@machine:~$ /usr/share/nevernote/nevernote.sh
Exception in thread "main" java.lang.ExceptionInInitializerError
    at com.trolltech.qt.QtJambiObject.<clinit>(QtJambiObject.java:60)
Caused by: java.lang.RuntimeException: Loading library failed, progress so far:
Unpacking .jar file: 'qtjambi-linux64-gcc-4.5.2_01.jar'
Checking Archive 'qtjambi-linux64-gcc-4.5.2_01.jar'
 - skipping because of wrong system: trying to load: 'linux64', expected: 'linux32'
Loading library: 'libQtCore.so.4'...
 - using 'java.library.path'

    at com.trolltech.qt.internal.NativeLibraryManager.loadNativeLibrary(NativeLibraryManager.java:431)
    at com.trolltech.qt.internal.NativeLibraryManager.loadQtLibrary(NativeLibraryManager.java:355)
    at com.trolltech.qt.Utilities.loadQtLibrary(Utilities.java:140)
    at com.trolltech.qt.Utilities.loadQtLibrary(Utilities.java:136)
    at com.trolltech.qt.QtJambi_LibraryInitializer.<clinit>(QtJambi_LibraryInitializer.java:56)
    ... 1 more
Caused by: java.lang.UnsatisfiedLinkError: /usr/lib/libQtCore.so.4.6.2: /usr/lib/libQtCore.so.4.6.2: wrong ELF class: ELFCLASS64 (Possible cause: architecture word width mismatch)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1803)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1699)
    at java.lang.Runtime.load0(Runtime.java:770)
    at java.lang.Runtime.load(Runtime.java:758)
    at com.trolltech.qt.internal.NativeLibraryManager.loadLibrary_helper(NativeLibraryManager.java:478)
    at com.trolltech.qt.internal.NativeLibraryManager.loadNativeLibrary(NativeLibraryManager.java:426)
    ... 5 more
Could not find the main class: cx.fbn.nevernote.NeverNote.  Program will exit.
/home/user

```

Does someone has an idea what is going wrong here?

Thanks!

It acts as if you've installed a 64bit version but it thinks you're on a 32 bit OS or there is some type of mismatch in the jar files..

Can you tell me what version of Linux you're running, if it is 64 or 32 bit?

Also, from within /usr/share/nevernote/lib do an "ls -la" and paste the results.  I'll check the file sizes to make sure I didn't mess something up in building them.

---

### Post by timbo-lino on 2010-10-28
Hi baumgarr,

thanks for you reply. I am on a 64bit Version of Lucid Lynx.

The result I get is:
```

/usr/share/nevernote/lib$ ls -la
insgesamt 31220
drwxr-xr-x 2 root root     4096 2010-10-28 00:06 .
drwxr-xr-x 8 root root     4096 2010-10-28 00:06 ..
-rw-r--r-- 1 root root   258299 2010-10-11 10:22 commons-lang-2.4.jar
-rw-r--r-- 1 root root  2782400 2010-10-11 10:22 evernote.jar
-rw-r--r-- 1 root root  1198447 2010-10-11 10:22 h2-1.2.136.jar
-rw-r--r-- 1 root root   188121 2010-10-11 10:22 jtidy-r938.jar
-rw-r--r-- 1 root root   119740 2010-10-11 10:22 libthrift.jar
-rw-r--r-- 1 root root   367444 2010-10-11 10:22 log4j-1.2.14.jar
-rw-r--r-- 1 root root  2087109 2010-10-11 10:22 PDFRenderer.jar
-rw-r--r-- 1 root root  2759839 2010-10-11 10:22 qtjambi-linux64-4.5.2_01.jar
-rw-r--r-- 1 root root 22179904 2010-10-11 10:22 qtjambi-linux64-gcc-4.5.2_01.ja

```

---

### Post by baumgarr on 2010-10-28
The size matches my 64 bit versions, so I don't think I messed up the package.

The next thing I'd check is to be sure you have a 64 bit Java.  I'm assuming you do since you probably installed it from a deb, so I doubt that is the problem.

You can try downloading the 32 bit tar file and running the install.  It just copies the files into /usr/share/nevernote.  See if that corrects the problem.  If that still doesn't work, you can always get back to the 64 bit version by doing the same with the 64 bit tar or uninstalling & reinstalling the 64 bit deb.

If nothing else, I can try downloading the 64 bit Ubuntu you are using & trying to debug it from there.  I just need to know what JDK you are using to try and match.

---

### Post by timbo-lino on 2010-10-28
> **baumgarr said:**
> 
You can try downloading the 32 bit tar file and running the install.  It just copies the files into /usr/share/nevernote.  See if that corrects the problem. 

That did it for me. :)
I dont know why, but synaptic tellt me that I use 32-bit Java.....

Very nice program! It rocks :guitar:
But a quick question...Do you have synthax highlighting on your ToDo?

---

### Post by baumgarr on 2010-10-28
Cool.  I'm glad that is all that it was.  

I hadn't planned on adding syntax highlighting.  At least not in the short term.  I was toying with the idea of adding things like exit routines to make customizing it easier, but that isn't on the immediate future list.  

If enough people need it, however, I could probably find enough JavaScript examples to hack something together.  I've added things that were more complicated than that based upon requests.

---

### Post by nac.est on 2010-11-02
First of all, thank you so much for this awesome software. I was very happy when I discovered it.

Unfortunately I'm having problems with syncing, like the ones described in [this bug report]("https://sourceforge.net/tracker/?func=detail&aid=3080869&group_id=322872&atid=1356578") (I haven't found a way to post a comment there without creating a new bug report, sorry).

It says "thread has died" and refuses to sync. I'm running 0.92.1 on Ubuntu 10.10, and my EN account contains a lot of notes in Japanese.

Here is the terminal output corresponding to the error:
```
Exception in thread "Synchronization Thread" java.lang.NullPointerException
	at org.apache.thrift.protocol.TBinaryProtocol.writeString(TBinaryProtocol.java:174)
	at com.evernote.edam.type.Note.write(Note.java:1542)
	at com.evernote.edam.notestore.NoteStore$updateNote_args.write(NoteStore.java:29859)
	at com.evernote.edam.notestore.NoteStore$Client.send_updateNote(NoteStore.java:2843)
	at com.evernote.edam.notestore.NoteStore$Client.updateNote(NoteStore.java:2833)
	at cx.fbn.nevernote.threads.SyncRunner.syncLocalNotes(SyncRunner.java:492)
	at cx.fbn.nevernote.threads.SyncRunner.evernoteSync(SyncRunner.java:334)
	at cx.fbn.nevernote.threads.SyncRunner.run(SyncRunner.java:175)
	at java.lang.Thread.run(Thread.java:636)
	at com.trolltech.qt.QThread.run(QThread.java:164)
```

Please note that when I first installed Nevernote it synced normally all my notes. The problem emerged after I had modified some notes locally.


Should I open a new report on the tracker?

---

### Post by baumgarr on 2010-11-02
Under Edit/Preferences set the debugging level to "Extreme" and do a sync again.  When it dies, close the program.  Look in ~/.nevernote/logs at the file syncRunner.log.  That should contain information on the note that is having issue.  Be sure that you can edit & view the note normally.  You might also want to try editing the title or even duplicating the note to see if it clears up the problem.

If you want to use the bug tracker on SourceForge or use the forum that is fine.  I don't mind responding here, but I don't check this thread very often so my responses may be a bit slower.

---

### Post by nac.est on 2010-11-03
Thank you baumgarr, with your instructions I was able to get it to work.

Apparently the problem was a single note. I noticed that the list of tags started with a comma (like ", tag1, tag2"), and I removed it. Perhaps that was the issue.

---

### Post by jaimedavila on 2010-11-03
woohoo! thanks for nevernote, and for the .deb file.

---

### Post by glavepp on 2010-11-12
First of all, many thanks for this application!!!
I've just installed the .deb on a fresh ubuntu 10.04, and it worked without any problems.
I'm a Evernote fan, so I'll keep an eye open on the evolution of your project.

By the way, are you thinking to support encrypted notes?
That's a nice feature of the evernote client, and it's useful for one who wants to store sensible information online.
Nevernote now is able to open encrypted notes, but not to edit them. (It's the same limitation as for the access with a web browser).

Thanks again.
Regards,
--
Pier (Italy)

---

### Post by baumgarr on 2010-11-12
I'm glad you like it.

You should be able to edit decrypted text.  Are you receiving an error or can you provide the steps to reproduce the problem?  The last release (0.94) had a lot of encryption bug fixes so I may have introduced a new one.

In addition, you can also encrypt your local database.  It doesn't help with online encryption but it prevents someone from browsing your database locally.

Thanks.

---

### Post by gatorbrit on 2010-11-15
Wow.  Just wow.  I just installed the new deb version of nevernote.  Awesome.  Thanks so much!!!!

---

### Post by gatorbrit on 2010-11-15
OK, quick question.  How do i create a note of a pdf file.  I think in the windows version of evernote you can drag and drop.  This doesn't seem to work in nevernote, but is there another way to pull in a pdf?

Thks

---

### Post by baumgarr on 2010-11-15
Drag & Drop does work in NeverNote, but it is a bit flaky.  Unless the NeverNote window had focus prior to beginning the drag, the drop isn't propagated to NeverNote.  I've never been able to figure out why or any setting that allows me to change the behavior.

Alternately you should be able to cut & paste a PDF or setup an import folder & drop the PDF into it.

---

### Post by gatorbrit on 2010-11-15
> **baumgarr said:**
> 
Alternately you should be able to cut & paste a PDF or setup an import folder & drop the PDF into it.


OK, cut and paste works great.  I really like the little nav arrows that allow you to read the pdf in line.  Very nice.

I'm an academic, so I have loads of pdf articles collected for various research projects.  I've been wanting a way to organize them.

Have you any word/idea of whether evernote will allow linking from one note to another?  Or sub-notebooks - i.e. notebook within a notebook?

Cheers

Rich

---

### Post by baumgarr on 2010-11-15
I don't know anything special other than what Evernote posts on their forums.  I wish they would give me an early heads up, but they don't.  :-)

Evernote is going to allow "stacks" of notebooks.  Basically they allow you to group multiple notebooks together, but it isn't a traditional hierarchical structure.  You can't assign a note to a stack and you can't have stacks within stacks, but it allows for basic grouping.  The Mac 2.0 alpha supports this now and the next NeverNote will also support it.

I don't know if you'd find it useful, but I added the ability to close notebooks in NeverNote to help me keep things organized.  It just hides a notebook from view, but it still will synchronize that notebook so you can always open it later.  It also has the benefit of speeding up NeverNote since there are less notes to manage.

Evernote has said they plan to do links to other notes, but I don't have any idea when.  It looks like the next main area of focus will be notebook sharing on the client.  They've updated their API to allow for sharing and added it to the Mac alpha but I didn't see any mention of linking in the latest API release.  

Personally, I'd be surprised if they implement linking before they have sharing rolled to every client and I expect that to take a while considering the number of platforms they support.  Changing the note structure is also much more difficult than changing other elements.  This is just an opinion, so I could very easily be wrong.

Other than that the only thing I know that is coming is a "due date" field so you can sort notes based upon that date.  This isn't a big change.  It is just the subject date field from 3.1 renamed.

Also, just a note on the PDFs.  Some PDFs it can't read so if you see one where it is just an icon then that PDF NeverNote can't read directly.  There are not very many, but it does happen.  Just a heads up.

---

### Post by gatorbrit on 2010-11-15
Another way to get pdfs into evernote is to open the evernote web page in chrome and drag the pdfs on to the notebook you want.

---

### Post by mlevin77 on 2010-11-16
Sorry if this is a stupid question but: which file do I download to install Nevernote on my Asus 901 eeePC (Atom processor)?

thank you!

Mike

---

### Post by baumgarr on 2010-11-16
There are no stupid questions, just stupid answers.  

I believe Atom processors use the x86 32 bit instruction set, so (assuming your using an Ubuntu or Debian based distribution) you'd need the nevernote-0.94_i386.deb file.

---

### Post by mlevin77 on 2010-11-16
Thank you!

Mike

---

### Post by berlinblue on 2010-11-27
> **HelloIndustries said:**
> 
I find that using Prism to run the web version of EverNote is good enough for me.

Thanks for the tip - works better for me, then NeverNote. :D

---

### Post by Nisuspi on 2010-12-01
Hi Baumgarr. Just a quick question - for some reason Nevernote has stopped deleting notes for me. I know about the historical problems, but when I delete a note in Nevernote it isn't even getting moved to the trash in the web client any more. I've tried uninstalling and clearing out the database to reload everything, but I'm a little stuck.

---

### Post by baumgarr on 2010-12-01
The first thing I'd try is to empty the trash on both the Web & NeverNote and synchronize.  If that didn't fix anything, change the debug level to extreme and try to delete another note & synchronize.  The log file syncrunner.log might then have more information on the problem.

---

### Post by akshayas1986 on 2010-12-07
Bumped into the same issue as nac.est and removed a note that had empty tags (,,,,). It worked like a charm. Thanks!

> **nac.est said:**
> Thank you baumgarr, with your instructions I was able to get it to work.

Apparently the problem was a single note. I noticed that the list of tags started with a comma (like ", tag1, tag2"), and I removed it. Perhaps that was the issue.

---

### Post by gatorbrit on 2010-12-16
Still really liking nevernote!

Quick question - when I view a note on the web, I have it formatted in courier font - as the note needs to be in a fixed width font to make sense.  But in nevernote, it seems to default to a variable width font.  Anyway to force the font?

Cheers

---

### Post by baumgarr on 2010-12-16
If you formatted the note with a specific font via the web browser then it should display it properly if you have that font available to Linux.

You can change the font for an existing note or text.  If you right click on the editor button bar you should bring up a list of buttons to add or remove.  The font list should be there.  If you have a small screen or have a lot of those editor buttons visible it is possible that the font list isn't visible, so you may need to hide some of the buttons to see it.

I'd be curious if that font is available in the drop down list.

---

### Post by gatorbrit on 2010-12-16
OK - that worked.  In the web app it was displaying courier, but I still went and reformatted it in courier and then it showed up with the correct font in Nevernote.


Another question - does Nevernote support stacks?   I don't have a Mac, so I don't really know what this function entails, but being able to nest notebooks seems like it would be quite useful.

---

### Post by baumgarr on 2010-12-16
Version 0.94 doesn't support stacks.  The API supporting stacks wasn't released to outside developers until after I posted 0.94.

I'm debugging 0.95 now and it supports stacks.  There are a lot of new things in 0.95 and I'm hoping to have it ready soon, but there are still some bugs I need to track down.  Even after I release it, I'd recommend doing a full sync prior to upgrading.  Given the number of changes in the next release it is better safe than sorry.

---

### Post by gatorbrit on 2010-12-16
Thanks for all your hard work!!  I know all the evernote linux users really appreciate it!

---

### Post by gatorbrit on 2010-12-16
What does it mean when I get the error:

```
It appears that the synchronization thread has died..
```


I close nevernote and restart, but i still get the error.  Is there some other action I could take?

---

### Post by baumgarr on 2010-12-16
It has a background thread that does the synchronization with Evernote.  This is reporting that that thread died for some reason.

The first thing I'd try is to run NeverNote in a terminal.  When the thread dies it probably spits out a stack trace where it died. I'd also set the debugging level to Extreme before synchronizing & then see if there is anything useful in the .nevernote/logs/SincRunner.log file.

If you could paste some of the results it would help to debug the problem.

---

### Post by gatorbrit on 2010-12-16
Here is the output from the syncrunner log.  I actually rebooted the computer and restarted Nevernote and still had the same error. 

```
2010-12-16 14:56:32.569 Setting Update Count in sync thread
2010-12-16 14:56:32.570 Starting thread
2010-12-16 14:56:32.570 Entering DatabaseConnection.dbSetup 0
2010-12-16 14:56:32.571 Entering RDatabaseConnection.dbSetup
2010-12-16 14:56:32.576 Leaving DatabaseConnection.dbSetup0
2010-12-16 14:57:00.261 Setting keepRunning=true
2010-12-16 14:57:00.262 Work found: SYNC
2010-12-16 14:57:00.263 SyncNeeded is true
2010-12-16 14:57:00.264 Beginning sync
2010-12-16 14:57:00.264 Entering SyncRunner.evernoteSync
2010-12-16 14:57:00.264 Synchronizing with Evernote
2010-12-16 14:57:00.265 getting user from userstore
2010-12-16 14:57:00.448 Saving user information
2010-12-16 14:57:00.449 Getting sync state
2010-12-16 14:57:00.673 Full Sequence Before: 1224085298000
2010-12-16 14:57:00.674 Last Sequence Date: 1292527288698
2010-12-16 14:57:00.674 Update Count: 6191
2010-12-16 14:57:00.674 Last Update Count: 6191
2010-12-16 14:57:00.674 Uploading changes
2010-12-16 14:57:00.674 Entering SyncRunner.syncExpunged
2010-12-16 14:57:00.675 Entering DeletedTable.getAllDeleted
2010-12-16 14:57:00.675 Leaving DeletedTable.getAllDeleted
2010-12-16 14:57:00.678 Leaving SyncRunner.syncExpunged
2010-12-16 14:57:00.678 Entering SyncRunner.syncLocalTags
2010-12-16 14:57:00.678 Getting remote tags to compare names with the local tags
2010-12-16 14:57:00.879 Entering SyncRunner.findNextTag
2010-12-16 14:57:00.880 Leaving SyncRunner.findNextTag - no tags returned
2010-12-16 14:57:00.881 Leaving SyncRunner.syncLocalTags
2010-12-16 14:57:00.881 Entering SyncRunner.syncLocalNotebooks
2010-12-16 14:57:00.881 Getting remote notebooks to compare with local
2010-12-16 14:57:01.67 Getting local dirty notebooks
2010-12-16 14:57:01.68 Leaving SyncRunner.syncLocalNotebooks
2010-12-16 14:57:01.68 Entering SyncRunner.syncNotes
2010-12-16 14:57:01.140 Active dirty note found - non new
2010-12-16 14:57:01.140 Updating note : 25f3e79e-368e-4810-9b69-0f1bd1cd8e7f <title>the rip - portishead.pdf</title>]
```

---

### Post by baumgarr on 2010-12-16
It is having a problem with note the "rip - portishead.pdf".

Did the terminal output show anything?

---

### Post by gatorbrit on 2010-12-16
I didn't see anything in the terminal - I forgot to run it from there.  Anyhow, I deleted the offending note, but it sort of got really bogged down.   I was worried that some of my online notes might get messed up so I reinstalled the whole thing.


It seems to have the most trouble with pdfs.  I have quite a few in my evernote account.  Regular notes and clipped web pages do fine, its just the pdfs where it will occasionally hang, or fail to display one.

---

### Post by gatorbrit on 2010-12-17
Sorry for the endless comments on Nevernote, but I have another question.

When I sync - for example after I reinstalled, my whole computer becomes almost unusable.  I'm using a Dell T1500 workstation with 8GB ram and an Intel I7 chip, so I can't believe it is my computer.   Is there a way to make Nevernote play a little more nicely and not be such a resource hog?

---

### Post by baumgarr on 2010-12-17
It's never been quick, but I don't have it that bad & the machines I've tested on are lesser machines than that.  Is it just during the initial sync?

You may want to try editing the nevernote.sh script in /usr/share/nevernote & adjusting the heap size.  You've got a ton of memory so I'd increase the maximum heap size.

You may also want to try disabling indexing during a sync & seeing if it makes any difference.  It should be disabling it automatically, but perhaps there is a bug.

To answer your PDF question, the PDF library I'm using to render the pages has problems with some PDFs.  I've never been able to find a pattern to it, but it isn't my code so I can't do much.  If it fails, it should just put the PDF icon.

---

### Post by dasheep on 2010-12-21
Hi Baumgarr,

thanks for this really cool piece of software !!!
Unfortunately 0.95 64 does not run on linux lucid 64bit (tried deb and tars in 64 and 32 bit).
While I'm happy to use 0.94 (which runs fine) I just wanted to tell you for debugging.
Error outpu is the following:

```

Exception in thread "main" java.lang.NoClassDefFoundError: com/trolltech/qt/gui/QMainWindow
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Caused by: java.lang.ClassNotFoundException: com.trolltech.qt.gui.QMainWindow
        at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
        ... 11 more

```

Best and thanks again, Martin

---

### Post by baumgarr on 2010-12-21
Someone else just pointed that out to me today.  I messed up in the 64 bit versions scripts and am pointing to the 32 bit libraries.  I'll fix it tonight and try to have it out by tomorrow.

---

### Post by PresentOmni on 2010-12-27
Wow, I'm new to Evernote, and what a treat to have a native linux app!  Very Good Work Baumgarr!  Merry Christmas and Happy New Year!  You deserve it.  Kudos.

Edited: Yes, and I registered just to say thanks and good work. ;)

---

### Post by kowsik on 2011-01-12
I had been avoiding using Evernote due to the lack of linux support. Thanks a lot Baumgarr for creating NeverNote. It is nice to be able to have synchronized notes on my office and home computers.

---

### Post by baumgarr on 2011-01-12
You're welcome.  I'm glad you find it useful.

---

### Post by kryos on 2011-03-15
Baumgarr;

I'm posting to the forum to gain a wider audience than taking "the direct approach"!
Upgrade from 8.04 to 10.04 breaking Nevernote.  After total removal, fresh download, and reinstall still no luck.  Nothing in Applications menus either.  I may let this rest for awhile.
See attached for possible incomplete install?  Also persistent splash screen and qt jambi msg.

---

### Post by Priswell on 2011-03-16
Thx to all re: this thread. I'm doing a demonstration at my local linux users group re: note taking software and wikis and this might be of interest.

---

### Post by jloveless on 2011-03-30
> **baumgarr said:**
> Someone else just pointed that out to me today.  I messed up in the 64 bit versions scripts and am pointing to the 32 bit libraries.  I'll fix it tonight and try to have it out by tomorrow.

I want to add my kudos. I still can't believe Evernote has left us out to dry for so long. 

I have 2 64bit Ubuntu Maverick PCs at home. I can't install Nevernote to work on a 64bit. Is there a special version or do I just need to change something in the .sh file?

Many thanks again.

Jon

---

### Post by baumgarr on 2011-03-30
Is it failing to install, or just crashing on startup?  There is a 64 bit version that includes 64 bit Jambi libraries, so be sure you download the correct deb.

I've seen some instances where 64 bit Linux distros are using a 32 bit JVM and that causes problems.  The 64 bit deb expects a 64 bit JVM.

If you are running a 32 bit JVM you can try downloading the 32 bit tar file and run the install script.

If nothing else, run it from a terminal and let me know what output you are getting.

Thanks.

---

### Post by jloveless on 2011-03-30
> **baumgarr said:**
> Is it failing to install, or just crashing on startup?  There is a 64 bit version that includes 64 bit Jambi libraries, so be sure you download the correct deb.

I've seen some instances where 64 bit Linux distros are using a 32 bit JVM and that causes problems.  The 64 bit deb expects a 64 bit JVM.

If you are running a 32 bit JVM you can try downloading the 32 bit tar file and run the install script.

If nothing else, run it from a terminal and let me know what output you are getting.



Apparently I dl'd the 32bit version. I tried again and it works fine. MHA. I actually like this better than the real Evernote. Thry just released a new web version and I'm not sure about the interface. It is a big change and seems to be missing something. So, now I will use Nevernote.

Thanks again. Do you have a contribution mechanism set up? I would love to donate something.

Jon
Thanks.

---

### Post by baumgarr on 2011-03-30
> **jloveless said:**
>  Do you have a contribution mechanism set up? I would love to donate something.

Thanks for asking, but I don't have anything. If you want to contribute money there are a few options. 

- Donate to a charity of your choice.  I just ask that you let me know so I can feel good about it.
- Get a premium account & support Evernote directly.  I think if you sign up via my site memory button at [www.nevernote.org]("http://www.nevernote.org") I get a few dollars from your first month too.
- The next release should have the ability to insert LaTeX formulas as images.  That comes via the generosity of CodeCogs ([www.codecogs.com]("http://www.codecogs.com")).  If you use that feature then donate to them via their web site.  It costs them money to maintain the service and they are not getting anything out of the deal.

I'm glad it is working for you.

---

### Post by jloveless on 2011-03-31
> **baumgarr said:**
> Thanks for asking, but I don't have anything. If you want to contribute money there are a few options. 

- Donate to a charity of your choice.  I just ask that you let me know so I can feel good about it.
- Get a premium account & support Evernote directly.  I think if you sign up via my site memory button at [www.nevernote.org]("http://www.nevernote.org") I get a few dollars from your first month too.
- The next release should have the ability to insert LaTeX formulas as images.  That comes via the generosity of CodeCogs ([www.codecogs.com]("http://www.codecogs.com")).  If you use that feature then donate to them via their web site.  It costs them money to maintain the service and they are not getting anything out of the deal.

I'm glad it is working for you.

I am already a Premium account holder of Evernote. I was one of the very early users back when it was all free. I retired and then switched to Linux due to the cost of Windows and Office on a retirement income. I have been bugging them about doing a Linux version all this time but had to finally settle for the web version. 

Thanks again.

---

### Post by schnoogge on 2011-03-31
Hi there, 

I run Evernote on my MacBook and Ipad however at work I have my Ubuntu. Everything seemed to work fine and thought it was so cool to have however I have stumbled across a problem. It seems it is not able to upload sync  to my account. That is I have all the docs that we generated on the Macbook in evernote but those made in Nevernote have a dot next to them as if they aren't in sync and I don't see them on my IPAD or mac. In the logs there are also errors as listed below. 

I would appreciate it when someone would have an idea where it could lie. 

Thanks 


 Synchronizing with Evernote
 Synchronizing shared notebooks.
 Sending local tags.
 Sending local notebooks.
 Synchronizing deleted notes.
 Sending local notes.
 Sending local notes.
 Error sending local note: EDAMNotFoundException(identifier:Note.notebookGuid, key:1301041509913)
 Sending local notes.
 Sending local notes.
 Error sending local note: Note.title
 Sending local notes.
 Cleaning up
 Finalizing Synchronization
 Synchronization completed with errors.  Please check the log for details.
 Error synchronizing - see log for details.

---

### Post by jloveless on 2011-04-01
> **schnoogge said:**
> Hi there, 

I run Evernote on my MacBook and Ipad however at work I have my Ubuntu. Everything seemed to work fine and thought it was so cool to have however I have stumbled across a problem. It seems it is not able to upload sync  to my account. That is I have all the docs that we generated on the Macbook in evernote but those made in Nevernote have a dot next to them as if they aren't in sync and I don't see them on my IPAD or mac. In the logs there are also errors as listed below. 

I would appreciate it when someone would have an idea where it could lie. 

Thanks 


 Synchronizing with Evernote
 Synchronizing shared notebooks.
 Sending local tags.
 Sending local notebooks.
 Synchronizing deleted notes.
 Sending local notes.
 Sending local notes.
 Error sending local note: EDAMNotFoundException(identifier:Note.notebookGuid, key:1301041509913)
 Sending local notes.
 Sending local notes.
 Error sending local note: Note.title
 Sending local notes.
 Cleaning up
 Finalizing Synchronization
 Synchronization completed with errors.  Please check the log for details.
 Error synchronizing - see log for details.

I am also getting an error when synching with Nevernote. The following is the entry in the log:
2011-04-01 01:57:17.83 Full Sequence Before: 1205865141000
2011-04-01 01:57:17.84 Last Sequence Date: 1301647316097
2011-04-01 01:57:17.84 Update Count: 12302
2011-04-01 01:57:17.84 Last Update Count: 12302
2011-04-01 01:57:17.516 *** EDAM Not Found Excepton syncLocalNotes EDAMNotFoundException(identifier:Note.notebookGuid, key:1301611369538)
2011-04-01 01:57:17.517 EDAMNotFoundException(identifier:Note.notebookGuid, key:1301611369538)

Any ideas?

---

### Post by jloveless on 2011-04-01
> **jloveless said:**
> I am also getting an error when synching with Nevernote. The following is the entry in the log:
2011-04-01 01:57:17.83 Full Sequence Before: 1205865141000
2011-04-01 01:57:17.84 Last Sequence Date: 1301647316097
2011-04-01 01:57:17.84 Update Count: 12302
2011-04-01 01:57:17.84 Last Update Count: 12302
2011-04-01 01:57:17.516 *** EDAM Not Found Excepton syncLocalNotes EDAMNotFoundException(identifier:Note.notebookGuid, key:1301611369538)
2011-04-01 01:57:17.517 EDAMNotFoundException(identifier:Note.notebookGuid, key:1301611369538)

Any ideas?

Well, I emptied the trash and I deleted a single note that had the dot indicator in the Synch column (far right) and then synched. All went well this time. Maybe it was a corrupted note?

---

### Post by schnoogge on 2011-04-04
Well to be honest I didn't think this would solve it but it did :-) 
Thanks for the tip I had to that hadn't synced I deleted them both and all in the trash made a new one and wow it worked. Thanks 

Take care
Mick

---

### Post by baumgarr on 2011-04-04
Sorry for not replying.  I used to get notified for this topic but I must have unsubscribed accidentally.

Given the GUID that the error message is spitting out, this is what happened.

- You created a note in NeverNote.  Somehow this note was given an update sequence number > 0.  The update sequence number is increased each time you synchronize with Evernote.  Until you upload the note for the first time it should be 0.
- When you synchronized it thought that this note had already been uploaded to Evernote in the past, so rather than creating a new note on their servers it tried to update an existing note (which obviously didn't exist).  Evernote then kicked it back.

When you deleted it and emptied the trash NeverNote had the same problem of not being able to find it, but deleting a note that doesn't exist is something NeverNote doesn't care about.

Why it happened I don't know, but that is the cause.

---

### Post by stecz on 2011-08-23
I have a new install of 11.04 on a dell mini 10v with 2 gig of ram... nevernote is hitting 120% of cpu. I just installed nevernote on my 10.x system at work and it seems to be working fine.

Any ideas?

Thanks

---

### Post by baumgarr on 2011-08-24
The first thing I'd want to do is to turn up debugging to the highest level (in Edit/Preferences).  That should give you an idea of what is happening.  If it is a new download, then it can take a while to do the initial indexing.  If it isn't inedxing, then I'd look at nevernote.log or syncRunner.log.  If it is indexing you can look at indexRunner.log.  

Other than that you can open a SourceForge ticket and attach any logs in ~/.nevernote/logs.  That will give me an idea of what is going on.  If you have sensitive data they may appear in the logs when debugging is high, so you may want to scrub them first.

Thanks.

---

### Post by stecz on 2011-08-24
I was thinking about the indexing... that might be it. I'll get the logs and also let it run overnight or something (can't do it tonight since I didn't bring my stinking power supply home)...

Thanks for the ideas.

---

### Post by stecz on 2011-08-30
I've decided it's not Nevernote. It's java. Nevernote kicks off java, but even after I quit out of Nevernote, java continues to use all of my CPU.

---

### Post by dirtyblanket on 2012-06-30
nevernote is crapware... it's absolute garbage and a sorry excuse for a program. I tried to install it several times and it failed to ever get working at all.

BEWARE of nevernote... DON'T INSTALL IT. Just my 2 cents here.. by the way, I'm still looking for alternatives.

---

### Post by dirtyblanket on 2012-06-30
I would say, just use Tomboy if you're on linux... until someone can get Evernote working with wine, or until Nixnote / Nevernote (linux clones that use the Evernote API, but currently are pure failware / crapware / non-working software distros).

[https://help.ubuntu.com/community/Tomboy](https://help.ubuntu.com/community/Tomboy)

---

### Post by cariboo on 2012-06-30
Old thread closed.

---

