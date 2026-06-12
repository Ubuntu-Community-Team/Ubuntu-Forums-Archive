---
title: "how to add another PC"
date: 2009-11-25
forum: Ubuntu One (CLOSED)
---

### Post by windowsfree on 2009-11-25
I have an established account. My laptop 9.04 is what I used and now I built another PC and installed Ubuntu 9.10.  I went to the Ubuntu One folder - clicked connect and nothing happens.  I went online and tried to see if I can connect this computer but cannot find info.  What do I need to do to add this PC to my account?  I have the latest software installed also
Thank you

Wanted to add that I did the almost Microsoft like thing of rebooting and trying it, but still does not connect or ask me to add the PC.

---

### Post by wrgb2 on 2009-11-26
On the new PC, go to Applications > Internet > Ubuntu One.  Running this will allow you to add the PC.

---

### Post by windowsfree on 2009-11-27
sorry i didn't make it clearer in my post, but nothing happens when I click on Ubuntu one.

---

### Post by wrgb2 on 2009-11-27
There's a serious problem with Ubuntu One -- the way it works is, the first timee you click on the Ubuntu One icon in the program menu, it sets the application to run at startup AND is supposed to take you to a page to validate that PC on Launchpad.  If you closed this browser window, or there was an error with the page (which happens fairly frequently with the Ubuntu One site), the problem is that Ubuntu One thinks the validation has taken place and never offers you the opportunity again.  In short, you only get on chance at it.  Even uninstalling and reinstalling Ubuntu One does not force the validation to take place again on that PC.  The bad news is, I haven't seen a workaround short of a fresh install for this problem - maybe someone else knows of one?

---

### Post by windowsfree on 2009-11-27
Thanks, I kinda figured it was on that end.  I appreciate your input and guess I will stick with DROPBOX.

---

### Post by Newfoundlander on 2009-11-28
> **windowsfree said:**
> sorry i didn't make it clearer in my post, but nothing happens when I click on Ubuntu one.

It should launch an icon in your top panel and open the launchpad service in your browser.  I had to change my default browser from Opera to Firefox to get it to work though.

---

### Post by windowsfree on 2009-11-29
nope- that does not work as stated in above thread

---

### Post by windowsfree on 2009-11-29
I have an established account. My laptop 9.04 is what I used and now I built another PC and installed Ubuntu 9.10. I went to the Ubuntu One folder - clicked connect and nothing happens. I went online and tried to see if I can connect this computer but cannot find info. What do I need to do to add this PC to my account? I have the latest software installed also
Thank you

[B][U]
Tried this........it did not work[/U][/B].

bob@Main:~$ u1sync --authorize

ERROR:dbus.proxies:Introspect error on org.freedesktop.NetworkManager:/org/freedesktop/NetworkManager: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
________________________________________________________________________________________________

[U][B]did this too, still doesn't work.

[/B][/U]                                  
[LIST=1]
[*]Quit the Ubuntu One client
[*]$ sudo rm -rf     ~/.share/local/ubuntuone
[*]$ rm -rf ~/.cache/ubuntuone
[*]$ rm -rf ~/.config/ubuntuone
[*]$ mv ~/Ubuntu\ One/ ~/Ubuntu\     One_old/
[*]Open     Applications->Accessories->Passwords and Encryption Keys, go     to the Passwords tab, delete the Ubuntu One token
[*]$ sudo apt-get purge ubuntuone*
[*]$ sudo apt-get install ubuntuone*
[*]Open     Applications->Internet->Ubuntu One and you should have to add     your computer via the web page that comes up once you login to     Ubuntu One
[*]Put a small text file in the newly     created ~/Ubuntu One/ directory and make sure that syncs correctly,     if not, please report a bug
[*]If all goes well this far, move the files and folders from     ~/Ubuntu One_old/ to ~/Ubuntu One/ and the sync should happen.
[/LIST]
[U][B]
Guess I will stay with DROPBOX[/B][/U]

---

### Post by thebear78 on 2009-11-30
Sorry to hear you're still having issues using Ubuntu One. Have you checked this page [1]. It's a quick way to find some of the common reported bugs that we're seeing with the service. You may find the cause there. Thanks.

[1] [https://wiki.ubuntu.com/UbuntuOne/Bugs#Common%20(Duplicate)%20Bugs](https://wiki.ubuntu.com/UbuntuOne/Bugs#Common%20(Duplicate)%20Bugs)

---

### Post by windowsfree on 2009-11-30
reloaded the OS just to see, clicked on UO and got the message you can see on the attachment.
???

---

### Post by joshuahoover on 2009-11-30
> **windowsfree said:**
> reloaded the OS just to see, clicked on UO and got the message you can see on the attachment.
???

This is an expected message due to bug 462828. If you do a system update via System->Administration->Update Manager and restart the Ubuntu One client, then all should be good. 

Thank you,

Joshua

---

### Post by windowsfree on 2009-12-01
Thanks and it is, just hated reloading the OS to get it to work.  Thanks again.

---

