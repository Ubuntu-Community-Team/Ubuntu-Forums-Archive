---
title: "Where is UbuntuOne for Windows?"
date: 2010-07-02
forum: Ubuntu One (CLOSED)
---

### Post by NUboon2Age on 2010-07-02
Update: 8/5/10: Here's the twitter feed for updates on U1 Windows client.  Should get more active soon, since testing has begun.  [http://twitpic.com/296inf](http://twitpic.com/296inf)

There was an a[rticle from January 2010]("http://www.geek.com/articles/news/ubuntu-one-cloud-storage-coming-to-windows-20100125/") saying that at PyCon there would be a 'sprint' porting effort to get UbuntuOne working on Windoze.  Did that happen?  Where's the project at now?  This'd be one more hook to get Windoze users exposed/drawn to Ubuntu.

Here's a 3 month old answer on Launchpad from Joshua Hoover about this.
[https://answers.launchpad.net/ubuntuone-servers/+question/107268](https://answers.launchpad.net/ubuntuone-servers/+question/107268)

in #ubuntuone irc channel **<Chipaca> (John Lenton) wrote July 2, 2010:** : 
> T**here is no Ubuntu one for windows yet. There will be soon.**  Lucio Torres (__lucio__)'s work was awesome, but it was proof-of-concept, not something we can ship. Its most lasting contribution was a branch that separates out the unix-specific pieces of code, which is a branch which we'll be merging this coming week (I hope). Testers are not needed yet, because we have just finished hiring a person that will do it, but I expect it to come together rapidly over the next few months.

Here's a wishlist/bug report for it.  Everyone please add yourself to the 'affects you', subscribe and add comments.
**[https://bugs.launchpad.net/ubuntuone-client/+bug/601218](https://bugs.launchpad.net/ubuntuone-client/+bug/601218)**

Update 7/18/2010:  
[SIZE="3"]I confirmed Tomboy Notes on Windows (Vista) synchronization is working with Ubuntu One[/SIZE]
I got Tomboy note syncing working on Windows (Vista) using Ubuntu One to sync, but without any specific Windows Client-side U1 software. 
1) Tomboy (right click)->Preferences->Synchronization->  
a) Service:  Tomboy Web
b) Server: [https://one.ubuntu.com/notes;](https://one.ubuntu.com/notes;) 
c) 'Connected'  
d) The Web browser prompted to add the computer to Ubuntu One account; Add computer.
e) Save

After that it 'just worked! :)  Synchronizes with no problems.[SIZE="2"][/SIZE]

---

### Post by NUboon2Age on 2010-07-02
On Vista (Home Premium, Service Pack 2) I just downloaded Portable Ubuntu 'Tres' and installed ubuntuone-client-gnome.  

At least some functions seem to be working.  

[LIST=1]
[*]I was able to add the computer to my Ubuntu One account.  
[*]The "Ubuntu One" folder and its child folder "Shared With Me" showed up on the Vista computer in my user's folder automagically, and i added a test file to the folder which promptly showed up on the Ubuntu One account.  
[*]When I created the test file a notification pops up saying "Updating Files... Ubuntu One is now updating your files" and then "Updating Finished n/ Ubuntu One is finished updating 1 file"  

[/LIST]

However: 

[LIST=1]
[*] See the UDFs Problem below...
[/LIST]

Update 7/4/2010
**The UDFs problem: **
UDFs = User Defined Folders any folders you've designated to be synced in Ubuntu One other than the default "Ubuntu One" folder and its default "Shared With Me" Folder within.
 
If you run into a situation your UDFs are not propagating to your desktop it could be because UDFs are not supported on your system.  I am with Portable Ubuntu 'tres' which is based on Karmic.  

Here's what Canonical's U1 developer of ubuntu-client-gnome, John Lenton (Chipaca on #ubuntuone irc channel) explained about UDF support:> 
<Chipaca> Karmic didn't have UDFs :) so, you could use a backport of ubuntuone (from the ubuntuone-hackers ppa) on Karmic, and get the UDFs or, not use UDFs at all -- your choice.

Update: Now I understand that the "Shared With Me" folder is for when other people drop files in folders that they have designated to share with me.  I haven't tried doing that yet.  Before I understood what the "Shared With Me" folder was I experimented with it by changing the permissions on the "Shared With Me" folder and when i changed it from 'access' to 'read and write' the lock symbol went away and was replaced by a circular arrow.  But even though i dropped a file in there, it did not show up on the U1 web site.

Update: I tried to make a symlink to a windoze file, but i get an error from cygwin that says 'feature not implemented yet'

---

### Post by Ellipsis on 2010-07-02
[https://launchpad.net/ubuntuone-windows-installer](https://launchpad.net/ubuntuone-windows-installer)

---

### Post by Pifilatakanemu on 2010-07-04
If inter-OS-syncing is important to you check [Dropbox]("https://www.dropbox.com/referrals/NTIxNTQxNzg5") out. I use it with several OSs and it works like a charm.


IMHO U1 still needs a lot of improvements to reach the performance of Dropbox...

[Wuala]("http://www.wuala.com/referral/KC6FMCNNMBGNAJPKP4MC") seems quite promising, too.

---

### Post by JohnDMcClane on 2010-07-09
It's probably behind your couch

---

### Post by kyleabaker on 2010-07-12
> **Pifilatakanemu said:**
> If inter-OS-syncing is important to you check [Dropbox]("https://www.dropbox.com/referrals/NTIxNTQxNzg5") out. I use it with several OSs and it works like a charm.

IMHO U1 still needs a lot of improvements to reach the performance of Dropbox...

Exactly. I hope they hold off on porting Ubuntu One to Windows for a while. I'd rather see performance and features become something impressive first. Porting it now or in the near future just seems like a complete waste of Canonical resources to me.

---

### Post by NUboon2Age on 2010-07-18
Update: 8/5/10: Here's the twitter feed for updates on U1 Windows client.  Should get more active soon, since testing has begun.  [http://twitpic.com/296inf](http://twitpic.com/296inf)

> **NUboon2Age said:**
> 
Here's a wishlist/bug report for it.  Everyone please add yourself to the 'affects you', subscribe and add comments.
**[https://bugs.launchpad.net/ubuntuone-client/+bug/601218](https://bugs.launchpad.net/ubuntuone-client/+bug/601218)**



Chipaca (Canonical U1 developer John Lenton) wrote in the #ubuntuone irc channel (which is also accessible via [http://java.freenode.net](http://java.freenode.net) or [http://webchat.freenode.net](http://webchat.freenode.net) and simply provide a nickname and enter #ubuntuone for the channel)
 <Chipaca>  if you could come online tomorrow between 8z and 16z (ie. GMT time), approx, and talk to mandel, he's **[SIZE="2"]working on the windows client and has an installer you might want to try[/SIZE]**  and also said FWIW, the windows port of the file syncing part of Ubuntu One will be windows native, i.e. you wouldn't need to install dbus on windows :)

---

### Post by NUboon2Age on 2010-07-18
> **JohnDMcClane said:**
> It's probably behind your couch

:) Might be in my [CouchDB]("http://arstechnica.com/open-source/guides/2009/12/code-tutorial-make-your-application-sync-with-ubuntu-one.ars").

---

### Post by NUboon2Age on 2010-08-05
I understand testing has begun.  We're getting closer.

Update: 8/5/10: Here's the twitter feed for updates on U1 Windows client.  Should get more active soon, since testing has begun.  [http://twitpic.com/296inf](http://twitpic.com/296inf)

---

