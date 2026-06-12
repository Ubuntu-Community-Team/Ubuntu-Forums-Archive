---
title: "Ubuntu One connection problem - Lucid"
date: 2010-10-28
forum: Ubuntu One (CLOSED)
---

### Post by Trevor Burton on 2010-10-28
I have Ubuntu One working for me on my main PC running Karmic Koala.  Files are syncing.

I then tried my laptop which I had upgraded to Lucid Lynx.  I eventually found Ubuntu One client/preferences in its new place in the user menu.

The devices tab shows <LOCAL-MACHINE> as the computer, even though my machine has a name - is this right?  

[IMG]http://i55.tinypic.com/euhds1.png[/IMG]

Then I click "Connect" and get the error below. Any ideas please?

[IMG]http://i55.tinypic.com/2z4w946.png[/IMG]

Thanks,

Trevor

---

### Post by NHclimber on 2010-10-28
from another thread...

> **duanedesign said:**
> If  you see <local machine> it means  you have deleted all your machines from your computer, but there is  still a Token in the keyring. Please try the following.

   1. Quit the Ubuntu One client
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open System-> Preferences-> Ubuntu One (or Me Menu ->
       Ubuntu One)
   9. a web page should open, prompting you to add your computer to
       your Ubuntu One account
  10. Add your computer

Please let us know if this helps.

thank you,
duanedesign

If your browser doesn't open at step 9, following the instructions here [[https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIAddMyComputer](https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIAddMyComputer)].

---

### Post by Trevor Burton on 2010-10-28
Thanks NHClimber, but I did spot that and tried it all with no luck.

At step 4, there is no Ubuntu token, since I have never managed to connect the laptop, nor add it as a machine.  Therefore at step 6, there is no machine to delete, apart from my desktop, which I don't want to delete.

It seems there is some problem with the laptop actually connecting to Ubuntu One as a service, but I can't tell what.

---

### Post by Trevor Burton on 2010-10-29
OK, so I've now upgraded the laptop to the latest release, Maverick, and the problem is slightly different.

I still get no connection - the first screen looks exactly the same, I don't get the error message, but my laptop doesn't connect to Ubuntu One so I can't set it up to sync files.

Just to confirm, all is working fine with my desktop machine (Karmic) and files are syncing with my Ubuntu One account from the desktop.

Any ideas?

---

### Post by NHclimber on 2010-10-29
What about this from the FAQ?

> If the steps above do not solve the problem for you, it's possible your  network connection is managed by something other than Network Manager  (USB modem, WICD, etc.) and Network Manager is still installed and  running on your computer. If this is the case, Network Manager will  either need to be removed or [disabled]("https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager").  The reason for this is because Ubuntu One first checks with Network  Manager to see if there is a connection. If Network Manager is running  but doesn't have a connection it tells Ubuntu One that and Ubuntu One  waits for a connection to be made before moving forward.  

---

### Post by Trevor Burton on 2010-10-29
Didn't spot that one, thanks.

I don't know what network manager is, so I solved it rather brutally, by just reinstalling the whole of ubuntu.

It's not as drastic as it sounds as it is a secondary machine and I had no important data stored on it alone - it's also my "learning" machine for configuration, and I'd already messed up the bootsplash by installing and then uninstalling KDE alongside Gnome.

The reinstall worked, and now I do get a sensible machine name, and it is syncing files.

Thanks for your help anyway NHClimber.

Trevor

---

