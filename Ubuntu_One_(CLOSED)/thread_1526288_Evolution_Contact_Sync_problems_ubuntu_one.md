---
title: "Evolution Contact Sync problems ubuntu one"
date: 2010-07-07
forum: Ubuntu One (CLOSED)
---

### Post by AJExtreme on 2010-07-07
I setup my ubuntu one free account today, and downloaded the ubuntu one app for my Iphone 3G.  I registered my computer and Iphone with ubuntu one.  I was able to sync 196 Iphone contacts perfectly with ubuntu one; no problems. :p  

I opened evolution on my ubuntu 10.04 and I had no contacts.  I created one "test" contact in evolution to see if it would show up in ubuntu one.  When I created it, it disappeared in evolution and did not show up in ubuntu one.  I clicked on contacts on the top panel bar, and it showed my "test contact".  Then when I opened evolution from the applications it didn't show and Then I also got the following error message. 

"This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: Address Book does not exist".

Also everything else works great, Tommyboy notes, and file share.

I tried to use the fix on the following thread.

[http://swiss.ubuntuforums.org/showthread.php?t=1277470&page=9](http://swiss.ubuntuforums.org/showthread.php?t=1277470&page=9)

I pull up a web page, but I don't understand anything in it also before it redirects me it gives me a message that I am about to connect to a user, but it doesn't say aaron.  Then when the page opens I don't understand anything in there and it doesn't show any contacts when I click that link.  

Someone please help I am really lost on this.  I don't want to modify anything in that page as I am not sure what I am looking at let alone what to modify.

I also removed and reinstalled the evolution-couchdb through synaptic.
I would really like to have all my contact in evolution without having to manually enter them.

I figured I would have problems with syncing the Iphone side not the ubuntu side. 

Thank you for any help in advance.

Aaron

---

### Post by AJExtreme on 2010-07-08
I ran the following command.
```
u1sdtool -s
```

I got the following output,
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

Everything is working such as file transfer, and Tomboy notes.  Ubuntu One even syncs flawlessly with my Iphone.  The only problem I am having is my contacts are not showing up in Evolution.

Ok now I am really confused.  I pressed restart for my machine, it says syncing in progress then I ran the above command again and now I get the following output.

```
aaron@aaron-desktop:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

aaron@aaron-desktop:~$ u1sdtool -s
State: READY
    connection: Not User Not Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE
```


Could someone please help.

Aaron

Here is a copy of all the all that I put in Terminal and it's response
```
aaron@aaron-desktop:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

aaron@aaron-desktop:~$ u1sdtool -s
State: READY
    connection: Not User Not Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE

aaron@aaron-desktop:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

aaron@aaron-desktop:~$ killall beam.smp; killall beam
beam: no process found
aaron@aaron-desktop:~$ rm ~/.config/desktop-couch/desktop-couchdb.ini
aaron@aaron-desktop:~$ dbus-send --session --dest=org.desktopcouch.CouchDB --print-reply --type=method_call / org.desktopcouch.CouchDB.getPort
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
aaron@aaron-desktop:~$ xdg-open file:///home/aaron/.local/share/desktop-couch/couchdb.html
aaron@aaron-desktop:~$ evolution --force-shutdown
Shutting down evolution-alarm-notify (Evolution Calendar alarm notification service)
aaron@aaron-desktop:~$ /usr/lib/evolution/evolution-data-server-2.28
evolution-data-server-Message: Starting server
e-data-server-Message: adding type `ECalBackendGoogleTodosFactory'
e-data-server-Message: adding type `ECalBackendGoogleEventsFactory'
e-data-server-Message: adding type `EBookBackendFileFactory'
e-data-server-Message: adding type `ECalBackendWeatherEventsFactory'
e-data-server-Message: adding type `EBookBackendCouchDBFactory'
e-data-server-Message: adding type `EBookBackendVCFFactory'
e-data-server-Message: adding type `ECalBackendFileTodosFactory'
e-data-server-Message: adding type `ECalBackendFileEventsFactory'
e-data-server-Message: adding type `ECalBackendFileJournalFactory'
e-data-server-Message: adding type `EBookBackendGoogleFactory'
e-data-server-Message: adding type `EBookBackendWebdavFactory'
e-data-server-Message: adding type `ECalBackendContactsEventsFactory'
e-data-server-Message: adding type `EBookBackendGroupwiseFactory'
e-data-server-Message: adding type `ECalBackendGroupwiseTodosFactory'
e-data-server-Message: adding type `ECalBackendGroupwiseEventsFactory'
e-data-server-Message: adding type `ECalBackendGroupwiseJournalFactory'
e-data-server-Message: adding type `ECalBackendCalDAVEventsFactory'
e-data-server-Message: adding type `ECalBackendCalDAVTodosFactory'
e-data-server-Message: adding type `ECalBackendCalDAVMemosFactory'
e-data-server-Message: adding type `ECalBackendHttpTodosFactory'
e-data-server-Message: adding type `ECalBackendHttpEventsFactory'
e-data-server-Message: adding type `ECalBackendHttpMemosFactory'
e-data-server-Message: adding type `EBookBackendLDAPFactory'
in server_log_handler
evolution-data-server-Message: Server up and running
impl_GNOME_Evolution_Addressbook_BookFactory_getBook
 + couchdb://127.0.0.1
 => 0xe3e180
impl_GNOME_Evolution_Addressbook_Book_open (0xe3e180)
impl_GNOME_Evolution_Addressbook_BookFactory_getBook
 + file:///home/aaron/.evolution/addressbook/local/system
 => 0xea7640
impl_GNOME_Evolution_Addressbook_Book_open (0xea7640)

(process:4376): libedata-book-WARNING **: impl_GNOME_Evolution_Addressbook_Book_getBookView ((contains "x-evolution-any-field" ""))

e_data_book_respond_get_book_view
book_view file uref 
in server_log_handler

** (process:4376): WARNING **: Couldn't get port for desktopcouch: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
in server_log_handler

** (process:4376): WARNING **: Could not create DesktopcouchSession object


```

---

### Post by duanedesign on 2010-07-08
Contact and Bookmark syncing is turned off right now. Last I heard it is being turned back on a little at a time so it does not overwhelm the service. You can get the latest Status information [here]("https://wiki.ubuntu.com/UbuntuOne/Status").

Your u1sdtool -s looks good. A couple of things to look for when using u1sdtool -s:

[COLOR="Green"]GOOD:[/COLOR] connection: With User With Network
[COLOR="Red"]NOT GOOD:[/COLOR] connection: Not User Not Network
[COLOR="Red"]NOT GOOD:[/COLOR] connection: With User Not Network
[COLOR="Red"]NOT GOOD:[/COLOR] connection: Not User With Network

[COLOR="Green"]GOOD:[/COLOR] is_connected: True
[COLOR="Red"]NOT GOOD:[/COLOR] is_connected: False

[COLOR="Green"]GOOD:[/COLOR] is_online: True
[COLOR="Green"]GOOD:[/COLOR] is_online: False
is_online will be False for the first couple minutes or so while Ubuntu One does its Authenticating and Local_Rescan.

queues: IDLE
This is normal, **if** you are not waiting on something to sync. IDLE means there is nothing for Ubuntu One to do. So if Ubuntu One should be busy syncing you do not want IDLE.

A couple of good commands for troubleshooting are:

```
u1sdtool --waiting-metadata
u1sdtool --waiting content
```

I use these like so:

```
u1sdtool --waiting-metadata | wc -l
u1sdtool --waiting content | wc -l
```

This will return a number that should get smaller over time. A good way to see if the syncdaemon is stuck.

Here is a good page with more info on u1sdtool
[Ubuntu One Client Control]("https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/ClientControl")

---

### Post by AJExtreme on 2010-07-08
Thank you for the information and links, I hope they turn the service on soon.  

I was worried that something was wrong on my end.  

Aaron

---

