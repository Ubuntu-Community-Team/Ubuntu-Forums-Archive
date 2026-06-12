---
title: "Not Sycing Tomboy Notes"
date: 2010-04-24
forum: Ubuntu One (CLOSED)
---

### Post by belkinsa on 2010-04-24
When I try to syc my notes via Tomeboy Notes, it gives me a "Sychronization Failed" error.  And when I look at the details, I see none of my notes synced.  Can I have some suggestion of how to fix this.

Thanks

---

### Post by joshuahoover on 2010-04-27
> **Mechafish said:**
> When I try to syc my notes via Tomeboy Notes, it gives me a "Sychronization Failed" error.  And when I look at the details, I see none of my notes synced.  Can I have some suggestion of how to fix this.

Thanks

I'm sorry to hear notes are not syncing for you. In order to help determine what the cause of the problem is, you'll need to do the following:

[LIST=1]
[*]Quit Tomboy 
[*]Applications->Accessories->Terminal, and run: 

[LIST]
[*]tomboy --debug > ~/tomboy_debug.log 
[/LIST]
[*]Try to  reproduce the bug
[*]File a bug at: [https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug](https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug)
[*]Attach ~/tomboy_debug.log to the bug report
[/LIST]
You can also hop on #ubuntuone on Freenode IRC and ask for joshuahoover there. I'm normally available Monday-Friday, 13:00-21:00 UTC. I can try to help troubleshoot things in real time with you there.

Thank you,

Joshua

---

### Post by belkinsa on 2010-04-27
Doesn't work for me (newbie here!)

I have Ubuntu 10.04 

Error:

> 
bash: /home/svetlana/tomeboy_debug.log: Permission denied
svetlana@svetlana-desktop:~$ sudo ~/tomeboy_debug.log
sudo: /home/svetlana/tomeboy_debug.log: command not found


---

### Post by duanedesign on 2010-04-27
After quitting Tomboy open a Terminal (Applications > Accessories > Terminal) and cut/paste or type the following code.

```
tomboy --debug > ~/tomboy_debug.log 
```

This will launch Tomboy in debug mode. Try and reproduce your issue. The errors are being saved to a file tomboy_debug.log located in  your Home directory. That is the folder with your name. The file name is:

tomboy_debug.log

[click here]("https://bugs.edge.launchpad.net/ubun...rvers/+filebug") to file a bug report. Attach the file you created to your report. You should be able to add an attachment when you file the bug (can't remember off the top of my head). however if you can not, you will be able to add an attachment after you make the bug using the 'Add Attachment or patch' button at the bottom of the bug report.

---

### Post by belkinsa on 2010-04-28
Got it, but that link is wrong.

I got this when I tried to sync the notes:

> Tomboy is already running.  Exiting...

---

### Post by joshuahoover on 2010-04-29
> **Mechafish said:**
> Got it, but that link is wrong.

I got this when I tried to sync the notes:

Based on that, it sounds like Tomboy is still running. Tomboy needs to be quit by either right-clicking on the Tomboy icon in the task bar and selecting "Quit" or from a terminal session (Applications->Accessories->Terminal) run: killall tomboy

Thank you,

Joshua

---

### Post by belkinsa on 2010-04-29
Still no error.

---

### Post by joshuahoover on 2010-04-30
> **Mechafish said:**
> Still no error.

Still no error? I'm not sure I understand, sorry.

After you quit Tomboy, did you try to run these steps so we can get a debug log to tell us why you are not able to synchronize notes?

[LIST=1]
[*]Applications->Accessories->Terminal, and run:
[LIST]
[*]tomboy --debug > ~/tomboy_debug.log
[/LIST]
[*]Try to synchronize your notes
[*]File a bug at: [https://bugs.edge.launchpad.net/ubun...rvers/+filebug]("https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug")
[*]Attach ~/tomboy_debug.log to the bug report
[/LIST]
Thank you,

Joshua

---

### Post by belkinsa on 2010-04-30
I tried that but gives me no error. Maybe I should try again or just give up and just wait.

---

### Post by Mal Bridgeman on 2010-05-14
[https://bugs.launchpad.net/ubuntuone-servers/+bug/580368](https://bugs.launchpad.net/ubuntuone-servers/+bug/580368)
[COLOR=DarkRed]
I posted a bug here - it's the first time I have reported a bug so please be gentle with me ;)

Thanks
Mal[/COLOR]

---

### Post by joshuahoover on 2010-05-14
> **Mal Bridgeman said:**
> [https://bugs.launchpad.net/ubuntuone-servers/+bug/580368](https://bugs.launchpad.net/ubuntuone-servers/+bug/580368)
[COLOR=DarkRed]
I posted a bug here - it's the first time I have reported a bug so please be gentle with me ;)

Thanks
Mal[/COLOR]

Thank you Mal! I repllied in the bug comments with a potential workaround. I'll have to follow up with one of the devs when they're back from UDS next week.

Joshua

---

### Post by Mal Bridgeman on 2010-05-17
> **joshuahoover said:**
> Thank you Mal! I repllied in the bug comments with a potential workaround. I'll have to follow up with one of the devs when they're back from UDS next week.

Joshua
[COLOR=DarkRed]
Hi Joshua

Thanks for your advice - it has helped a bit but I am way off having properly synced notes still.

I deleted the keys you advised and re-syned - no change, although Ubuntuone wanted me to add my computer ...again!.

I noticed other keys mentioning Ubuntuone specifically so I deleted them and tried to re-sync.

This got about 6 notes synced but there's about another 9 which aren't sync'd.

I desperation I deleted all keys from that file, removed all computers from Ubuntu one, de-installed ubuntuone, changed tomboy syncing back to local.

I reinstalled ubuntuone and reintroduced this machine.

Then tried Tomboy sync and got another fail :(

```

[DEBUG 18:52:38.772] SyncThread using SyncServiceAddin: Tomboy Web
[DEBUG 18:52:38.819] Building web request for URL: https://one.ubuntu.com/notes//api/1.0/
[DEBUG 18:52:39.969] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/user/
[DEBUG 18:52:40.190] 8
[DEBUG 18:52:40.196] Sync: GetNoteUpdatesSince rev -1
[DEBUG 18:52:40.206] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/op/?include_notes=true
[DEBUG 18:52:40.507] Sync: 5 updates since rev -1
[DEBUG 18:52:40.674] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/op/
[DEBUG 18:52:40.865] Sync: Uploading 9 note updates
[DEBUG 18:52:40.889] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/op/
[DEBUG 18:52:41.103] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/op/
[ERROR 18:52:41.518] Caught exception. Message: The remote server returned an error: (500) INTERNAL SERVER ERROR.
[ERROR 18:52:41.525] Stack trace for previous exception:   at System.Net.HttpWebRequest.CheckFinalStatus (System.Net.WebAsyncResult result) [0x00000] 
  at System.Net.HttpWebRequest.SetResponseData (System.Net.WebConnectionData data) [0x00000] 
[ERROR 18:52:41.533] Rest of stack trace for above exception:    at System.Environment.get_StackTrace()
   at Tomboy.WebSync.Api.OAuth.MakeWebRequest(RequestMethod method, System.String url, System.Collections.Generic.List`1 parameters, System.String postData)
   at Tomboy.WebSync.Api.OAuth.WebRequest(RequestMethod method, System.String url, System.String postData)
   at Tomboy.WebSync.Api.OAuth.Put(System.String uri, IDictionary`2 queryParameters, System.String putValue)
   at Tomboy.WebSync.Api.UserInfo.UpdateNotes(IList`1 noteUpdates, Int32 expectedNewRevision)
   at Tomboy.WebSync.WebSyncServer.CommitSyncTransaction()
   at Tomboy.Sync.SyncManager.SynchronizationThread()
[ERROR 18:52:41.534] Synchronization failed with the following exception: The remote server returned an error: (500) INTERNAL SERVER ERROR.
  at System.Net.HttpWebRequest.CheckFinalStatus (System.Net.WebAsyncResult result) [0x00000] 
  at System.Net.HttpWebRequest.SetResponseData (System.Net.WebConnectionData data) [0x00000] 

```

Any further help would be gratefully received.
Mal[/COLOR]

---

### Post by Mal Bridgeman on 2010-05-17
[COLOR=DarkRed]OK - really not having fun here .... :(

I decided to clear down everything and start again.

turned off synch in Tomboy
deleted all machines in ubuntuone
marked for complete removal everything I could find related to ubuntuone and libubuntuone 
Restarted
Installed the Ubutnuone bits
REstarted
synched the Ubuntuone client .... all good (if a little slow)
I then updated all the tomboy notes
then enabled Tomboy synch
**it asked me to add the computer again so I chose a different name**
it synched the notes with those already on the server
but failed to synch the ones that were not on the server in the failed synch "details" it does say that the old notes were "Updated" and the new ones were "Uploaded new note to server" - but it did not.

Why did it need to know about the computer again? IS this the source of my issue?

I now have two named computers on my ubuntu One account but they are the same physical machine

Advice gratefully received.
Mal[/COLOR]

---

### Post by rogerdean on 2010-06-07
Similar problems here. I've quit synching altogether as I was losing access to my notes... Maybe by the next release things will be ironed out.

---

### Post by Surachinen on 2011-03-20
okay, found a workaround for me. i was getting the failed to sync thing, with no details. the debug specified a 404 error though the urls were working fine. then a poster said that if you had created any notes from the ubuntu one web ui then you need to delete one or more notes. well i created another new note on the web ui (i had made several from it prior) calling it placeholder (with some gibberish text in it), then proceded to delete that one note. sync is now working perfectly again. don't know why it worked. but it did, so in short:

1) make a note on the website (nothing important)
2) delete said note
3) attempt to sync notes
4) ????
5) PROFIT!!!

---

### Post by Throne777 on 2011-03-21
> **joshuahoover said:**
> I'm sorry to hear notes are not syncing for you. In order to help determine what the cause of the problem is, you'll need to do the following:

[LIST=1]
[*]Quit Tomboy 
[*]Applications->Accessories->Terminal, and run: 

[LIST]
[*]tomboy --debug > ~/tomboy_debug.log 
[/LIST]
[*]Try to  reproduce the bug
[*]File a bug at: [https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug](https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug)
[*]Attach ~/tomboy_debug.log to the bug report
[/LIST]
You can also hop on #ubuntuone on Freenode IRC and ask for joshuahoover there. I'm normally available Monday-Friday, 13:00-21:00 UTC. I can try to help troubleshoot things in real time with you there.

Thank you,

Joshua

Filed a bug report for a similar issue (and attached a log file).
Terminal said the error was (I mentioned this in the report):
```

(Tomboy:6521): GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed
```
Hope that's helpful

---

### Post by xsist10 on 2011-07-27
I followed the following instructions:
[https://wiki.ubuntu.com/UbuntuOne/Bugs](https://wiki.ubuntu.com/UbuntuOne/Bugs)

I also tried removing the UbuntuOne key from the seahorse keychain and reconfiguring UbuntuOne on my computer.

Here is my output for tomboy --debug

```

$ tomboy --debug
** Running Mono with --debug    **
[DEBUG 08:17:54.214] NoteManager created with note path "/home/xxxx/.local/share/tomboy".
[INFO 08:17:54.760] Initializing Mono.Addins
[DEBUG 08:17:54.915] AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG 08:17:54.919] 	       Name: Tomboy.Tomboy,0.10
[DEBUG 08:17:54.919] 	Description: 
[DEBUG 08:17:54.919] 	  Namespace: Tomboy
[DEBUG 08:17:54.919] 	    Enabled: True
[DEBUG 08:17:54.919] 	       File: /usr/lib/tomboy/Tomboy.exe
[DEBUG 08:17:55.858] AddinManager.OnAddinLoaded: Tomboy.WebSyncServiceAddin
[DEBUG 08:17:55.859] 	       Name: Web Sync Service Add-in
[DEBUG 08:17:55.859] 	Description: Synchronize Tomboy Notes with Tomboy Online and other compatible web services
[DEBUG 08:17:55.859] 	  Namespace: Tomboy
[DEBUG 08:17:55.859] 	    Enabled: True
[DEBUG 08:17:55.859] 	       File: /usr/lib/tomboy/addins/WebSyncServiceAddin.dll
[DEBUG 08:17:55.860] AddinManager.OnAddinLoaded: Tomboy.WebDavSyncServiceAddin
[DEBUG 08:17:55.861] 	       Name: WebDav Sync Service Add-in
[DEBUG 08:17:55.861] 	Description: Synchronize Tomboy Notes to a WebDav URL
[DEBUG 08:17:55.861] 	  Namespace: Tomboy
[DEBUG 08:17:55.861] 	    Enabled: True
[DEBUG 08:17:55.861] 	       File: /usr/lib/tomboy/addins/WebDavSyncService.dll
[DEBUG 08:17:55.866] Unable to locate 'gnomesu' in your PATH
[DEBUG 08:17:55.866] Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG 08:17:55.867] Successfully found all system tools
[DEBUG 08:17:55.867] Unable to locate 'wdfs' in your PATH
[DEBUG 08:17:55.868] AddinManager.OnAddinLoaded: Tomboy.FileSystemSyncServiceAddin
[DEBUG 08:17:55.868] 	       Name: Local Directory Sync Service Add-in
[DEBUG 08:17:55.868] 	Description: Synchronize Tomboy Notes to a local file system path
[DEBUG 08:17:55.868] 	  Namespace: Tomboy
[DEBUG 08:17:55.868] 	    Enabled: True
[DEBUG 08:17:55.868] 	       File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
[DEBUG 08:17:56.156] AddinManager.OnAddinLoaded: Tomboy.ExportToHtmlAddin
[DEBUG 08:17:56.157] 	       Name: Export to HTML
[DEBUG 08:17:56.157] 	Description: Exports individual notes to HTML.
[DEBUG 08:17:56.157] 	  Namespace: Tomboy
[DEBUG 08:17:56.157] 	    Enabled: True
[DEBUG 08:17:56.157] 	       File: /usr/lib/tomboy/addins/ExportToHtml.dll
[DEBUG 08:17:56.158] AddinManager.OnAddinLoaded: Tomboy.PrintNotesAddin
[DEBUG 08:17:56.158] 	       Name: Printing Support
[DEBUG 08:17:56.158] 	Description: Allows you to print a note.
[DEBUG 08:17:56.159] 	  Namespace: Tomboy
[DEBUG 08:17:56.159] 	    Enabled: True
[DEBUG 08:17:56.159] 	       File: /usr/lib/tomboy/addins/PrintNotes.dll
[DEBUG 08:17:56.160] AddinManager.OnAddinLoaded: Tomboy.BacklinksAddin
[DEBUG 08:17:56.160] 	       Name: Backlinks
[DEBUG 08:17:56.160] 	Description: See which notes link to the one you're currently viewing.
[DEBUG 08:17:56.160] 	  Namespace: Tomboy
[DEBUG 08:17:56.160] 	    Enabled: True
[DEBUG 08:17:56.160] 	       File: /usr/lib/tomboy/addins/Backlinks.dll
[DEBUG 08:17:56.162] AddinManager.OnAddinLoaded: Tomboy.EvolutionAddin
[DEBUG 08:17:56.163] 	       Name: Evolution Mail Integration
[DEBUG 08:17:56.163] 	Description: Allows you to drag an email from Evolution into a Tomboy note.  The message subject is added as a link in the note with an envelope icon next to it.
[DEBUG 08:17:56.163] 	  Namespace: Tomboy
[DEBUG 08:17:56.163] 	    Enabled: True
[DEBUG 08:17:56.163] 	       File: /usr/lib/tomboy/addins/Evolution.dll
[DEBUG 08:17:56.167] AddinManager.OnAddinLoaded: Tomboy.FixedWidthAddin
[DEBUG 08:17:56.167] 	       Name: Fixed Width
[DEBUG 08:17:56.168] 	Description: Adds fixed-width font style.
[DEBUG 08:17:56.168] 	  Namespace: Tomboy
[DEBUG 08:17:56.168] 	    Enabled: True
[DEBUG 08:17:56.168] 	       File: /usr/lib/tomboy/addins/FixedWidth.dll
[DEBUG 08:17:56.170] AddinManager.OnAddinLoaded: Tomboy.StickyNoteImportAddin
[DEBUG 08:17:56.170] 	       Name: Sticky Notes Importer
[DEBUG 08:17:56.170] 	Description: Import your notes from the Sticky Notes applet.
[DEBUG 08:17:56.171] 	  Namespace: Tomboy
[DEBUG 08:17:56.171] 	    Enabled: True
[DEBUG 08:17:56.171] 	       File: /usr/lib/tomboy/addins/StickyNoteImport.dll
[DEBUG 08:17:56.172] StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!
[DEBUG 08:17:56.271] Unable to locate 'wdfs' in your PATH
[DEBUG 08:17:56.295] Tomboy remote control active.
** (Tomboy:3952): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object
[DEBUG 08:18:12.992] SyncThread using SyncServiceAddin: Ubuntu One
[DEBUG 08:18:13.008] Building web request for URL: https://one.ubuntu.com/notes//api/1.0/
[DEBUG 08:18:14.751] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/user/
[DEBUG 08:18:15.159] 8
[DEBUG 08:18:15.161] Sync: GetNoteUpdatesSince rev -1
[DEBUG 08:18:15.166] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/op/?include_notes=true
[DEBUG 08:18:15.576] Sync: 0 updates since rev -1
[DEBUG 08:18:15.580] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/op/
[DEBUG 08:18:15.979] Sync: Uploading 4 note updates
[DEBUG 08:18:16.027] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/op/
[DEBUG 08:18:16.469] Building web request for URL: https://one.ubuntu.com/notes/api/1.0/op/
[ERROR 08:18:26.827] Caught exception. Message: The remote server returned an error: (400) Bad Request.
[ERROR 08:18:26.835] Stack trace for previous exception:   at System.Net.HttpWebRequest.CheckFinalStatus (System.Net.WebAsyncResult result) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.SetResponseData (System.Net.WebConnectionData data) [0x00000] in <filename unknown>:0 
[ERROR 08:18:26.840] Rest of stack trace for above exception:    at System.Environment.get_StackTrace()
   at Tomboy.WebSync.Api.OAuth.MakeWebRequest(RequestMethod method, System.String url, System.Collections.Generic.List`1 parameters, System.String postData)
   at Tomboy.WebSync.Api.OAuth.WebRequest(RequestMethod method, System.String url, System.String postData)
   at Tomboy.WebSync.Api.OAuth.Put(System.String uri, IDictionary`2 queryParameters, System.String putValue)
   at Tomboy.WebSync.Api.UserInfo.UpdateNotes(IList`1 noteUpdates, Int32 expectedNewRevision)
   at Tomboy.WebSync.WebSyncServer.CommitSyncTransaction()
   at Tomboy.Sync.SyncManager.SynchronizationThread()
[ERROR 08:18:26.841] Synchronization failed with the following exception: The remote server returned an error: (400) Bad Request.
  at System.Net.HttpWebRequest.CheckFinalStatus (System.Net.WebAsyncResult result) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.SetResponseData (System.Net.WebConnectionData data) [0x00000] in <filename unknown>:0 

(Tomboy:3952): GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed

```

I also created a new note on UbuntuOne's web interface and it downloaded to my notes when I sync'd. When I deleted it on my interface, it removed it when I sync'd. I'm going to try creating all my notes in UbuntuOne and see if that solves the syncing problem.

---

### Post by xsist10 on 2011-07-27
Interestingly enough, new notes created on the website download, but I'm unable to sync new changes up (asks me to rename or overwrite the local copy when I update the local copy).

---

### Post by affert on 2012-01-31
> **Surachinen said:**
> okay, found a workaround for me. i was getting the failed to sync thing, with no details. the debug specified a 404 error though the urls were working fine. then a poster said that if you had created any notes from the ubuntu one web ui then you need to delete one or more notes. well i created another new note on the web ui (i had made several from it prior) calling it placeholder (with some gibberish text in it), then proceded to delete that one note. sync is now working perfectly again. don't know why it worked. but it did, so in short:

1) make a note on the website (nothing important)
2) delete said note
3) attempt to sync notes
4) ????
5) PROFIT!!!

YOU'RE MY HERO!   

That worked for me.  Thanks a bunch!

---

### Post by markMDW on 2012-05-08
I have the same problem as [Mechafish]("http://ubuntuforums.org/member.php?u=1044117") on my Ubuntu 10.04 desktop

"Failed to synchronize notes. Check the details below and try again.
      > Details
                         [there is nothing in the Details]




I've tried uninstalling reinstalling clearing settings, removing computers from UbuntuOne, all of this repeatedly.


I wonder if this could be a UbuntuOne problem instead?

---

### Post by David Crockett on 2012-05-09
Hi,

I too cannot sync tomboy.   It does not work with Ubuntu or with my windows machine.   It worked just fine until yesterday. PM (5/8/12).

My gues it is either a problem with Tomboy or the server.    

Cheers,

David

---

### Post by markMDW on 2012-05-09
The Tomboy version I'm using with Ubuntu 10.04 is 1.2.2

I checked the Tomboy homepage and found that a new version had been released on April 16, 2012, "Stable version 1.10.1", and that it fixes the following and more:  "
-Support for latest Firefox versions
-Updated 256x256 icon for GNOME 3
-Sync improvements and fixes "

The download is a file "tomboy-1.10.1.tar.xz"  There aren't any instructions on exactly how to install it.  

I'm hoping it will fix the sync problem.  Does anyone know what to do with this file?

---

### Post by the.scarecrow on 2012-05-09
I'm having the same problem after just installing 12.04. Tomboy fails to Sync my notes and there is nothing in the Details box. It was working prior to my 12.04 fresh install.

---

### Post by pmunly on 2012-05-09
Same problem here on Windows, Ubuntu 12.04 and Ubuntu 11.10.  I've got Tomboy 1.6.0 installed on Windows, Tomboy 1.10.1 installed on Ubuntu 12.04 and I'm not sure about what version I've got on Ubuntu 11.10, though I think it's 1.8.3.  Either way, I don't think it's a Tomboy issue as I ran Tomboy from the command line and am getting an "error: (500) INTERNAL SERVER ERROR," which is a standard web server error.  I did this for each system/version I'm using and received basically the same error.  Hopefully it gets fixed relatively soon as I use it pretty extensively for school.

markMDW - that file is a compressed archive containing the source code for Tomboy.  I tried compiling it in Windows (uhg) and it compiled (had to do the sync add-on as well), but the results were the same.  If you want to compile it, I suggest heading here: [http://live.gnome.org/Tomboy/Developers]("http://live.gnome.org/Tomboy/Developers")

---

### Post by David Crockett on 2012-05-10
good morning,

Well a miricle has occurred.  Tomboy now syncs. Server problem?    

I have run into thisproblem before and it gets resolved eventually.    it is too bad because I use this for many of my experimental note taking.    I export all of my notes (important ones anyway) to html format frequently as a backup.

Cheers,
D

---

### Post by markMDW on 2012-05-10
It's also syncing for me again.  I guess it was the server causing all the fuss.   Thanks for everyone posting messages

---

### Post by the.scarecrow on 2012-05-10
YAY! its working for me to. So wasn't anything to do with me installing 12.04.

---

