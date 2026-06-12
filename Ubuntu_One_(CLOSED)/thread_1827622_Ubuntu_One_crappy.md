---
title: "Ubuntu One crappy"
date: 2011-08-18
forum: Ubuntu One (CLOSED)
---

### Post by stallinux on 2011-08-18
The ***only*** important thing of a cloud file server such as Ubuntu One is that ***if*** it tells you that the files are synchronised they ***are*** in fact synchronised.
I don't mind if it tells me
  "I don't feel like uploading your stupid files today, punk"
or
  "Hey, no Internet available, dude!"
or not say anything at all and let you figure it out yourself. Annoying, but acceptable.

But if it says "files synced", they should be synchronised and if I work on a file I want to be 100% sure I am working on the latest version of the file.

Not so for Ubuntu One. See image attached. First of all, it cost me several attempts to actually make the files upload from one computer in the first place. Disconnect, connect, disconnect, connect, until the message was "synced" ***and*** all the files were there. Downloading on the other side remains impossible. It stays at 1.3 GB locally on the computer of the 3.6 GB uploaded. Many files I know should be there are still missing. Yet, no more network activity, and the status is "File Sync is up-to-date"

This is unacceptable. Product tested and failed.

Better to stick to Dropbox, which is integrated into Ubuntu seamlessly, never fails and is reliable in its messages. It actually has messages on the notification area, something that is very usefull (green means your files are synced, blue means it is syncing. Wonderfully simple).

That said, I would really like to switch to (that is, use one, namely) Ubuntu One and drop Dropbox. However, for the moment Ubuntu One is a failure.

([Ubuntu 11.04, 32 bit, classic desktop, Gnome] on both computers. On both computers it runs flawed)

---

### Post by duanedesign on 2011-08-23
The 11.10 version has notifications. You should get a message bubble when the sync starts and when it is done. The file emblems telling you the sync status of a file work a lot better in Natty as well.

Their is also a thread I stuck about getting more information from Ubuntu One.

From the command line you can get the number of items in the metadata and content queue with the following command:

```
u1sdtool --waiting | wc -l
```

Their is also a GUI for the u1sdtool called Magicicada. It will show you items waiting to sync and offers a toolbar where you can connect/disconnect Ubuntu One.  You can install it with the command:

```
sudo apt-get update; sudo apt-get install magicicada
```

If you determine the queue is stuck contact[ Ubuntu One Support]("https://one.ubuntu.com/help/contact/") for help.

Respectfully,
duanedesign

---

