---
title: "Ubuntu One Broken after update"
date: 2010-03-09
forum: Ubuntu One (CLOSED)
---

### Post by iansyngin on 2010-03-09
Jaunty Jack - 9.04
Ran update manager last night and ubuntu-one client failed as part of the upgrade.
At a loss as to figure out how to fix this. I have removed the ubuntuone-gnome-client and re-installed from the website but now luck.

Has anyone else had this issue and how did you resolve?

Thanks,
Ian

---

### Post by jvecht on 2010-03-09
> **iansyngin said:**
> Jaunty Jack - 9.04
 Has anyone else had this issue and how did you resolve?

I have the same problem. I guess we have to roll back this update?

---

### Post by iansyngin on 2010-03-09
i've gone throught the procedure for uninstalling and re-installing ubuntuone and that doesn't work either. very frustrating.
Not sure if i've gone past the point of doing a roll back on the update

when trying to install ubuntu one client from the website, i now see the following error

[IMG]http://img83.imageshack.us/img83/9587/uoneerror.png[/IMG]

---

### Post by AlexanderDGreat on 2010-03-09
YES! This is killing me, as usual with Ubuntu! This same **** happens to me, and I got all my notes in Ubuntu One. I sync with 5 pcs, work and home.

Why would you give us a hard time? Huhuhu... :(

---

### Post by iansyngin on 2010-03-09
> **AlexanderDGreat said:**
> YES! This is killing me, as usual with Ubuntu! This same **** happens to me, and I got all my notes in Ubuntu One. I sync with 5 pcs, work and home.

Why would you give us a hard time? Huhuhu... :(

Well the files should be still in  ~/.share/ubuntuone  if I'm not mistaken.

---

### Post by jvecht on 2010-03-09
> **iansyngin said:**
> 
Not sure if i've gone past the point of doing a roll back on the update
Some time ago another update broke the local network access in Nautilus.

In that case the problem was with the libglib package.

The command to roll back the update to the previous package of libglib was (do **[COLOR=Red]NOT[/COLOR]** use it in our case) :

[B][FONT=courier]sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1

[/FONT][/B]I guess we first need to know which package is causing our current problem and then next we have to execute a similar command to get the roll back done. 

The command should not be that hard. But I am not going to experiment with my system to locate the trouble.

---

### Post by joshuahoover on 2010-03-09
My apologies for some of the issues caused by this latest update. We've been heads down on Lucid development and I didn't realize what this would mean for those using our PPA version on Jaunty and Karmic. Right now, there are a couple of issues:

1) We've removed the ubuntuone-client-applet and replaced it with ubuntuone-preferences, which can be accessed from System->Preferences->Ubuntu One. Unfortunately, this means you'll need to uninstall and reinstall. You can do this from a terminal session:

sudo apt-get remove ubuntuone-client* python-ubuntuone-storage*

sudo apt-get install ubuntuone-client* python-ubuntuone-storage* python-httplib2


2) There is currently a missing dependency that we are fixing right now (see [https://launchpad.net/bugs/535207](https://launchpad.net/bugs/535207) for more info). Until we get a fix out, you'll need to make sure you include python-httplib2 when you install. I've included it in the instructions above.

While we fix issue #2, I'm going to make sure our documentation and tutorials are updated appropriately to reflect the fact that there is no longer an ubuntuone-client-applet.

Thank you,

Joshua

---

### Post by jvecht on 2010-03-09
> **joshuahoover said:**
> You can do this from a terminal session:

sudo apt-get remove ubuntuone-client* python-ubuntuone-storage*

sudo apt-get install ubuntuone-client* python-ubuntuone-storage* python-httplib2


I did that (copy and paste) and it worked just fine on my machine. I uploaded two files and it synced too. I saw no pop-up confirming sync was completed (yet). No taskbar icon as well.

Thanks Joshua! Great job. I appreciate your quick response!

---

### Post by iansyngin on 2010-03-09
apt-get install ubuntuone-client* and python-ubuntuone-storage* are not being found. I think i'm missing the dependency settings in synaptic. Can someone post the dependency settings and i'll try to add them and see.

Thanks,
Ian

---

### Post by iansyngin on 2010-03-09
Got it sorted.

Thanks

---

### Post by AlexanderDGreat on 2010-03-10
> My apologies for some of the issues caused by this latest update. We've been heads down on Lucid development and I didn't realize what this would mean for those using our PPA version on Jaunty and Karmic. Right now, there are a couple of issues:

1) We've removed the ubuntuone-client-applet and replaced it with ubuntuone-preferences, which can be accessed from System->Preferences->Ubuntu One. Unfortunately, this means you'll need to uninstall and reinstall. You can do this from a terminal session:

sudo apt-get remove ubuntuone-client* python-ubuntuone-storage*

sudo apt-get install ubuntuone-client* python-ubuntuone-storage* python-httplib2


2) There is currently a missing dependency that we are fixing right now (see [https://launchpad.net/bugs/535207](https://launchpad.net/bugs/535207) for more info). Until we get a fix out, you'll need to make sure you include python-httplib2 when you install. I've included it in the instructions above.

While we fix issue #2, I'm going to make sure our documentation and tutorials are updated appropriately to reflect the fact that there is no longer an ubuntuone-client-applet.

Thank you,

Joshua - I'm sorry for ranting, I'm so ashamed. Thank you for your time and effort.

---

### Post by jvecht on 2010-03-11
> **joshuahoover said:**
> there is no longer an ubuntuone-client-applet.

Small question if I may, Joshua. I am missing some functionality probably due to the absence of that applet. 

Now I need to go to Preferences each time I start up my laptop to connect to Ubuntu One. I would like to have Ubuntu One be connected automatically if possible. I am using Jaunty.

*Good thing this cloud! I really missed it that one day it was not "there"...*

---

### Post by iansyngin on 2010-03-11
> **jvecht said:**
> Small question if I may, Joshua. I am missing some functionality probably due to the absence of that applet. 

Now I need to go to Preferences each time I start up my laptop to connect to Ubuntu One. I would like to have Ubuntu One be connected automatically if possible. I am using Jaunty.

*Good thing this cloud! I really missed it that one day it was not "there"...*

thought you might be able to put **ubuntuone-preferences** as one of the startup applications but don't think this launches the program

---

### Post by iansyngin on 2010-03-11
i'm not sure ubuntu one is working for me on Jaunty Jackalope still?
How do we launch the program after it's been installed.
I can launch ubuntuone-preferences from system-preferences, that brings up a screen saying it's connected but that's it.
I don't have an icon in the task bar any more that shows the app running.
I have copied a file into the ubuntu one directory but checking the website i don't see that this file has copied over. This used to be instant.

How can i confirm what should be running and should there still be an icon in the taskbar for JJ. Not happy with the Jack been left in the dark like this :(

---

### Post by AlexanderDGreat on 2010-03-11
Yeah, used to be much easier and friendlier to use for simple folks like me.

---

### Post by iansyngin on 2010-03-11
uninstalled and re-installed for the 5 or 6th time.
Now when i try to add my machine from the website it just freezes, eventaully times out and brings me to my files. Machine is not being added as it stuck on this page

[IMG]http://img121.imageshack.us/img121/1209/addingcomputer.png[/IMG]

---

### Post by joshuahoover on 2010-03-11
> **jvecht said:**
> Small question if I may, Joshua. I am missing some functionality probably due to the absence of that applet. 

Now I need to go to Preferences each time I start up my laptop to connect to Ubuntu One. I would like to have Ubuntu One be connected automatically if possible. I am using Jaunty.

*Good thing this cloud! I really missed it that one day it was not "there"...*

Yes, you and many others are missing this functionality right now. There are two main things we're adding back that we (unintentionally) removed from the client package:

[https://launchpad.net/bugs/534707]("https://launchpad.net/bugs/534707https://launchpad.net/bugs/526084")

[https://launchpad.net/bugs/526084]("https://launchpad.net/bugs/534707https://launchpad.net/bugs/526084")

Thank you,

Joshua

---

### Post by joshuahoover on 2010-03-11
> **iansyngin said:**
> uninstalled and re-installed for the 5 or 6th time.
Now when i try to add my machine from the website it just freezes, eventaully times out and brings me to my files. Machine is not being added as it stuck on this page

[IMG]http://img121.imageshack.us/img121/1209/addingcomputer.png[/IMG]

When it rains, it pours. We're furiously trying to figure out what is causing the OAuth process (which is what you're in the middle of when you add your computer to your Ubuntu One account) to timeout/fail most of the time right now and get it fixed ASAP. My apologies for the inconvenience this is causing you and others.

Joshua

---

### Post by iansyngin on 2010-03-12
no problem, take your time.
Just as long as everyone on JJ has the issue and not just me :)

---

### Post by jvecht on 2010-03-12
> **joshuahoover said:**
> Yes, you and many others are missing this functionality right now. There are two main things we're adding back that we (unintentionally) removed from the client package
Thanks Joshua. It is workable in my case. I will wait patiently.

Good luck with the job!

---

### Post by joshuahoover on 2010-03-12
> **joshuahoover said:**
> When it rains, it pours. We're furiously trying to figure out what is causing the OAuth process (which is what you're in the middle of when you add your computer to your Ubuntu One account) to timeout/fail most of the time right now and get it fixed ASAP. My apologies for the inconvenience this is causing you and others.

Joshua

Good news! This OAuth issue should no longer be a problem. We're still working on a longer term fix but have a workaround that will suffice for the time being.

Thank you all for your patience and support!

Joshua

---

### Post by iansyngin on 2010-03-12
:popcorn: Good work Josh @ the ubuntuone team

on a slde note. can you let us know if you guys are planning on re-introducing the ubuntuone task bar icon showing connectivity status, link to web site and link to nautilus folder?

Ian

---

### Post by AlexanderDGreat on 2010-03-13
> Thank you all for your patience and support! - More power to your team! I love UbuntuOne!

> on a slde note. can you let us know if you guys are planning on re-introducing the ubuntuone task bar icon showing connectivity status, link to web site and link to nautilus folder?

Yeah!

---

### Post by iansyngin on 2010-03-13
Ubuntuone is still not syncing my files that are held on the uone servers.
Been connected for about 2-3 hours and still nothing has synced..Is this still related to the database issues?

ian

[IMG]http://img715.imageshack.us/img715/614/ubuntuone.png[/IMG]

---

### Post by iansyngin on 2010-03-15
Any chance of a status report on the ubuntuone issues for Jaunty or overall?

Ian

---

### Post by duanedesign on 2010-03-15
> Ubuntuone is still not syncing my files that are held on the uone servers.
Been connected for about 2-3 hours and still nothing has synced..Is this still related to the database issues?

iansyngin,
I have a script you can run that will check for known issues in Ubuntu One. You can run it by issuing the following commands in a Terminal (Applications > Accessories > Terminal).

```
wget http://people.ubuntu.com/~duanedesign/ubuntuone-client-diagnose.py
```
After it downloads, run.
```
python ubuntuone-client-diagnose.py
```

If that finds a known issue it should tell you which bug tracks that issue. If it doesnt find anything i would suggest filing a bug report. That is the best way to get your issue looked at. You can do that by right-clicking on the applet and selecting report a problem. Apport will automatically attach some extra information to the report. Two files you will want to make sure are attached are:

```
~/.cache/ubuntuone/log/oauth-login.log
~/.cache/ubuntuone/log/syncdaemon-exceptions.log
```

Something you can do to gather a little extra info before attaching those logs to your report is to start Ubuntu one in debug mode and then try an connect.

Applications->Accessories->Terminal, and run:

```
 sudo killall ubuntuone-client-applet ubuntuone-syncdaemon
```

```
 /usr/lib/ubuntuone-client/ubuntuone-syncdaemon --debug > ~/syncdaemon-debug.log
``` 

Start the Ubuntu One client from the menu as you normally would and try and connect to the service and any other issues you might be having reproduce them as well. This log file will be in your home folder.

~/syncdaemon-debug.log

---

### Post by iansyngin on 2010-03-15
Here is the termianl output i receive after running your python script.

```

python ubuntuone-client-diagnose.py
Checking your Ubuntu One client...
Traceback (most recent call last):
  File "ubuntuone-client-diagnose.py", line 583, in <module>
    main()
  File "ubuntuone-client-diagnose.py", line 546, in main
    bug_found = bug.detect()
  File "ubuntuone-client-diagnose.py", line 262, in detect
    connect = int(appcfg.get("ubuntuone", "connect"))
TypeError: int() argument must be a string or a number, not 'NoneType'


```

---

### Post by jlh68 on 2010-03-15
After upgrading today, I no longer can find ubuntuone.  I can find it listed in Synaptic Package Manager, but no where else on my computer.

Where did it go?  Why is ubuntuone giving us broken updates?  It was working just fine and then they fiddle with it and break it or make it disappear from my computer (laptop).

---

### Post by joshuahoover on 2010-03-15
> **jlh68 said:**
> After upgrading today, I no longer can find ubuntuone.  I can find it listed in Synaptic Package Manager, but no where else on my computer.

Where did it go?  Why is ubuntuone giving us broken updates?  It was working just fine and then they fiddle with it and break it or make it disappear from my computer (laptop).

My apologies for the hassle. I'm in the process of updating all our documentation as we're changing quite a bit for Lucid (and, as a result, beta PPA users). I updated our installation docs for the beta PPA: [https://one.ubuntu.com/support/installation/](https://one.ubuntu.com/support/installation/) You'll notice that you now access Ubuntu One through System->Preferences->Ubuntu One and there is a new control panel that is nearing completion in terms of functionality.

Question for you and others: How would you like to see these types of changes documented? I'm curious to know where people look for information, as I'd hate to be updating docs/info that is rarely used while ignoring other more useful channels.

Thanks!

Joshua

---

### Post by iansyngin on 2010-03-15
When you say new control panel..Is this a new GUI compared to the one in place?
On the documentation side of things, speaking from my point of view and looking at the issue i am having. 
ubuntuone is saying it's connected but my files are not being synced with ~/Ubunto \One Folder. Some docs and commands to run to confirm where the issue lies, whether it's incompatibility with my client or some other issue with the sync
Might be helpful on the new control panel itself to remind users to look in /usr/share..i for one always forget to look in here.

As mentioned earlier, this has been connected for about 4-5 days and still nothing, not giving up hope yet though

---

### Post by joshuahoover on 2010-03-15
> **iansyngin said:**
> When you say new control panel..Is this a new GUI compared to the one in place?
On the documentation side of things, speaking from my point of view and looking at the issue i am having. 
ubuntuone is saying it's connected but my files are not being synced with ~/Ubunto \One Folder. 
As mentioned earlier, this has been connected for about 4-5 days and still nothing.

If you are accessing Ubuntu One through System->Preferences->Ubuntu One then you have a newer version of Ubuntu One that no longer includes the ubuntuone-client-applet which was in the taskbar. 

If you are still having the problem, please file a new bug by doing the following:

Open Applications->Accessories->Terminal and run: apport -p ubuntuone-client

Thank you,

Joshua

---

### Post by iansyngin on 2010-03-15
Probably different in Karmic but in Jaunty i receive "command not found" when trying to run apport -p ubuntuone-client

---

### Post by iansyngin on 2010-03-16
Update:
This morning i removed ~/.cache/ubuntuone & ~/.config/ubuntuone
lunched ubuntuone from system - preferences

The files on remote ubuntu server are now appearing locally.
There still appears to be some sort of sync issue though. There is a little red x icon on each of my folders. Also copied a file into the local directory and nothing shows up remotely after checking the web server.
I don't seem to be able to use apport to log this.
How else should i officially log this issue?

---

### Post by iansyngin on 2010-03-16
just want to mention that this is now syncing properly.

---

### Post by jlh68 on 2010-03-17
UbuntuOne continues NOT to work.  I tried the System > Preferences > UbuntuOne and I get an icon on my left panel and the little circle turns for awhile and then the circle goes away and the UbuntuOne icon disappears.  The result is that UbuntuOne did not start.

So I still have the problem

---

### Post by jlh68 on 2010-03-17
I can get the UbuntuOne applet on my Left panel.  When I click on it, I get the icon on the right panel and then the same result as my previous post, it does not start.  The applet icon remains on my Left panel.

BTW, I have my panels on the sides as I have a wide screen display and putting the panels on the side gives me more screen top and bottom.  Top panel relocated to the Left side, bottom panel relocated to right side.

---

### Post by jlh68 on 2010-03-17
OK, I completely Un-Installed all of UbuntuOne and then re-installed it following the UbuntuOne web page for installation.

I still have the same results as I did before.  

So what is happening with UbuntuOne in that it will not load?
I am using Ubuntu 9.04 Jaunty and Firefox 3.6

---

### Post by jlh68 on 2010-03-17
I tried again to completely Un-Install UbuntuOne using the following directions:
[https://answers.edge.launchpad.net/ubuntuone-client/+faq/778](https://answers.edge.launchpad.net/ubuntuone-client/+faq/778)

Step 5. $ mv ~/Ubuntu\ One/ ~/Ubuntu\ One_old/  did not work as I had no One old directory.

I used the above instructions to Re-Install, again having no success.

How about a goo "How-to" on getting this situation corrected?
Thanks

---

### Post by jlh68 on 2010-03-17
Did it again using "cut-n-paste", because I saw an error in my removal commands (did not see the underscore the first time).

I still cannot get UbuntuOne to actually open and let me set up the application.

I get the following on clicking > Install ubuntuone-client-gnome  see screen shot

---

### Post by joshuahoover on 2010-03-17
> **jlh68 said:**
> Did it again using "cut-n-paste", because I saw an error in my removal commands (did not see the underscore the first time).

I still cannot get UbuntuOne to actually open and let me set up the application.

I get the following on clicking   see screen shot

Sorry to hear Ubuntu One isn't installing or starting up properly for you. I think you may be getting bit by a missing dependency bug. Please install the software as detailed on the web site but then follow up with running the following command in a terminal session: sudo apt-get install python-httplib2

If you still cannot get System->Preferences->Ubuntu One to open, then please try launching it from a terminal session and see if you get any errors: ubuntuone-preferences

Thank you,

Joshua

---

### Post by jlh68 on 2010-03-18
**joshuahoover**  You hit the nail smack dab on the head.  I added the following *sudo apt-get install python-httplib2* using the terminal, then went to System > Preferences > UbuntuOne and it opened a web site.  

I believe now I have UbuntuOne in operation, but I do not get the upper right corner message about putting a file on UbuntuOne like I used to in the earlier versions.  How do I know that a file is on UbuntuONe?

Thanks for the help and for sticking with me on finding the solution.

---

### Post by iansyngin on 2010-03-18
> **jlh68 said:**
> **joshuahoover**  
I believe now I have UbuntuOne in operation, but I do not get the upper right corner message about putting a file on UbuntuOne like I used to in the earlier versions.  How do I know that a file is on UbuntuONe?
.
That ubuntuOne Notification icon no longer works as far as i can see.
You can view the files you transfer into the folder from that ubuntuone website. There is a files tab that shows the files.
Does ubuntuone launch at startup now or do i have to manually hit connect each time. How is it possible to start this automatically?

Ian

---

### Post by iansyngin on 2010-03-18
well i guess i can answer my own questioon as i found out

simply create an executle bash file or whatever and have the following line

u1sdtool --connect

Stick the file is startup applications and that should do it

---

### Post by joshuahoover on 2010-03-19
> **iansyngin said:**
> That ubuntuOne Notification icon no longer works as far as i can see.
You can view the files you transfer into the folder from that ubuntuone website. There is a files tab that shows the files.
Does ubuntuone launch at startup now or do i have to manually hit connect each time. How is it possible to start this automatically?

Ian

We're fixing both issues (status of syncing and automatic connection). For now, you need to manually connect and depend on either u1sdtool --current-transfers or the Nautilus file emblems to see the status of syncing. If you're interested in tracking progress on these two fixes, please see:

[https://bugs.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/526084](https://bugs.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/526084)

[https://bugs.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/534707](https://bugs.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/534707)

Thank you,

Joshua

---

### Post by jlh68 on 2010-03-20
I still cannot confirm if any files are being put on UbuntuOne, even though I have UbuntuOne on this computer.  I get no notification in the upper right corner like I did before the UbuntuOne upgrade and it became broken.

What is the indication that a file has been put online?

---

### Post by chicken159 on 2010-03-20
>>Update

In case this is of help to anyone, I have had some success getting Ubuntuone working again - not a very structured testing process, but here's what seemed to work:
Having initially removed/reinstalled ubuntuone (and couchdb) a few times using Synaptic, then numerous times in terminal mode...last time I went one step further and after purging all ubuntuone packages, did a system-wide search for any file containing 'ubuntuone'. Ignoring icons and messages, this threw up the .debs in the archives, and a number of python files which I manually removed. 
Then reinstalled, now I have a functioning Ubuntuone (at least as far as file sync goes...contacts are another matter).

So I'm guessing that some update may have left some old files lying around causing problems?

Anyway - thanks all concerned for the work thats gone into this!



>> Original stressed rantings...

Apologies, but I'm in need of a rant:

I hate to be defeatest here, but after having Ubuntu One working for months, it is now completely broken on 3 machines. No file sync, no Evolution contacts. Nothing. I have crashes, and when it doesn't crash it just does absolutely nothing.I've been through all the bug reports, but no solutions. I've tried removing all traces of ubuntuone/couch, cancelling my subscription and starting again - must have unistalled and reinstalled 20 times. But nothing works. Just when it was becoming an invaluable tool it has cost me days of hair-pulling and now I'm afraid I will not trust it again. Whats happened? It just stopped working.

---

### Post by joshuahoover on 2010-03-22
> **chicken159 said:**
> >>Update
>> Original stressed rantings...

Apologies, but I'm in need of a rant:

I hate to be defeatest here, but after having Ubuntu One working for months, it is now completely broken on 3 machines. No file sync, no Evolution contacts. Nothing. I have crashes, and when it doesn't crash it just does absolutely nothing.I've been through all the bug reports, but no solutions. I've tried removing all traces of ubuntuone/couch, cancelling my subscription and starting again - must have unistalled and reinstalled 20 times. But nothing works. Just when it was becoming an invaluable tool it has cost me days of hair-pulling and now I'm afraid I will not trust it again. Whats happened? It just stopped working.

No apologies necessary on your part. I'm sorry our latest updates have caused you so many problems. Have you filed a bug for this? If so, let me know the number and I'll make sure we have someone look into it. Even better would be if you could jump on the #ubuntuone channel on Freenode IRC and ask for joshuahoover. I'm normally on Monday-Friday, 13:00 UTC to 21:00 UTC.

Thank you,

Joshua

---

### Post by chicken159 on 2010-03-26
Hi - thanks for the reply - I've been away for the last week so not been able to follow-up. Current state of affairs is file sync working fine, but clicking on the contacts in evolution results in the pop-up:

Error loading address book.

This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: Address Book does not exist

I seem to remember this being reported on some bug or other, so I'll go look again when I get home. Just happy for now that file sync was working for my travels!

---

### Post by joshuahoover on 2010-03-26
> **chicken159 said:**
> Hi - thanks for the reply - I've been away for the last week so not been able to follow-up. Current state of affairs is file sync working fine, but clicking on the contacts in evolution results in the pop-up:

Error loading address book.

This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: Address Book does not exist

I seem to remember this being reported on some bug or other, so I'll go look again when I get home. Just happy for now that file sync was working for my travels!

OK, good to hear file sync is working for you now. :-)

For the contacts problem, can you try the following:

[LIST=1]
[*]Quit Evolution
[*]Start a terminal session (Applications->Accessories->Terminal) and then run:
evolution --force-shutdown
killall beam.smp
rm ~/.config/desktop-couch/desktop-couchdb.ini
dbus-send --session --dest=org.desktopcouch.CouchDB --print-reply --type=method_call / org.desktopcouch.CouchDB.getPort
[*]Start Evolution back up
[/LIST]
If that doesn't fix the problem, you may either be affected by an issue we're working on fixing right now related to the CouchDB tokens not being created for all users or your affected by something else. You can file a bug report and provide some debug info:

[LIST=1]
[*]File a bug at: [https://bugs.edge.launchpad.net/evolution-couchdb/+filebug](https://bugs.edge.launchpad.net/evolution-couchdb/+filebug)
[LIST=1]
[*]Be sure to include the steps you're taking and the problem you're seeing
[/LIST]
[*]From a terminal session run:
evolution --force-shutdown
/usr/lib/evolution/evolution-data-server-2.28 > ~/evolution_debug.log
[*]Open Evolution and try to reproduce the problem
[*]Attach ~/evolution_debug.log to the bug report
[*]Attach ~/.cache/desktop-couch/log/desktop-couch-replication.log
[/LIST]
Thank you,

Joshua

---

