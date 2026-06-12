---
title: "Windows LIve Messenger under Wine"
date: 2009-06-30
forum: Wine
---

### Post by timecatcher_3 on 2009-06-30
Hi 

I think there is a slight possibility that the latest WLM might work with Wine 1.1.24 and I need help figuring this out  :


fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\manojhemnani\\.wine\\drive_c\\Program Files\\Windows Live\\Messenger\\msnmsgr.exe" failed, status c0000142


Basically what I did was :

I installed Wine and replaced the program files folder and windows folder with the ones from my windows 7201 installation and when i loaded msnmsgr.exe using wine i got this :


Microsoft Visual C++ Runtime Library

Runtime Error!

R6034
An application has made an attempt to load the C runtime library incorrectly.

Please contact the application's support team for more information.


So please can someone help me out i really wish this could work Windows Live Messenger on Ubuntu!

---

### Post by Blood//Stain//Child on 2009-06-30
You may just want to use aMSN or emesene from Add/Remove. They are both very good MSN clients.

---

### Post by andrea000 on 2009-06-30
you can also use the msn service with pidgin and i think the Microsoft Visual C++ Runtime Library can be installed using wine tricks

---

### Post by Wiggles707 on 2009-06-30
Personally I wouldnt even bother trying to install WLM I dont really like it and when I uses XP I instantly got rid of it bc it was annoying.
Try using Pigeon its very user friendly and I like the fact that you can have more then one screen name signed in with out opening another messenger program 
but good luck any how :)

---

### Post by timecatcher_3 on 2009-07-02
The fact that none of the messengers mentioned have the proper video calling support which i really need. So please can someone help me figure out the solution to this problem.

---

### Post by cogadh on 2009-07-02
andrea000 already offered you a solution: install the Visual C++ Runtime using [winetricks]("http://wiki.winehq.org/winetricks"). However, that being said, WLM does not have a good history with Wine, so I wouldn't expect too much if I were you:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=127](http://appdb.winehq.org/objectManager.php?sClass=application&iId=127)

EDIT - And now that I have re-read your original post, I have a feeling that you are not going to be able to get it to work at all with the method you used. By replacing the entire Wine Program Files and Windows directories with Windows native ones, you have essentially broken Wine completely. You should only replace Wine's files with native ones if and when an application complains about a missing function in Wine and you should only replace the exact file that is being complained about, not everything. If you want to do this right, you will need to delete your .wine directory, create a new one, then run the actual installation of WLM within Wine.

---

### Post by edmondt on 2010-01-24
Thanks for trying guys, but why not just give the man a real answer instead of showing him the alternative?

Running Live Messenger has been done, check out this HOWTO at: [http://www.wine-reviews.net/wine-reviews/microsoft/msn-messenger-2008-and-2009-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/msn-messenger-2008-and-2009-on-linux-with-wine.html)

---

### Post by AllRadioisDead on 2010-01-24
Try emesene, video calling works fine for me.

---

