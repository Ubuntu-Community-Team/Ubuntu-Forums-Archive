---
title: "Ubuntu One in 10.04"
date: 2010-04-17
forum: Ubuntu One (CLOSED)
---

### Post by cogier on 2010-04-17
The instructions for setting up Ubuntu One in 10.04 says go to **System>Preferences>Ubuntu One** and a dialogue box will appear asking if you want to add this computer to Ubuntu One.

I don't see that, all I get is the **Ubuntu One Preferences.**

How do I log on with 10.04?

Thanks for your help.

---

### Post by jaco223 on 2010-04-17
> **cogier said:**
> The instructions for setting up Ubuntu One in 10.04 says go to **System>Preferences>Ubuntu One** and a dialogue box will appear asking if you want to add this computer to Ubuntu One.

I don't see that, all I get is the **Ubuntu One Preferences.**

How do I log on with 10.04?

Thanks for your help.

Do you get the Ubuntu One client after selecting system>Preferences>Ubuntu One?
If not you can try going to Applications>Accessories>Passwords and Encryption Keys
and removing Desktop Couch user authentication and or Ubuntu One token.
Then relaunch the Ubuntu One client from System>Preferences>Ubuntu One
That should launch the client and open a webrowser so you can add the computer
to the Ubuntu Cloud.
See if that helps.

Jaco

---

### Post by cogier on 2010-04-17
Jaco,

Thanks for the reply but all I have in the Password area is attached. I am doing this on a Dell Mini 9 if that helps.

---

### Post by jaco223 on 2010-04-17
> **cogier said:**
> Jaco,

Thanks for the reply but all I have in the Password area is attached. I am doing this on a Dell Mini 9 if that helps.

Cogier, have you tried relaunching Ubuntu one since your original post?
And if I understand correctly you go to System>Preferences>Ubuntu One
to launch, but it just kind of tries to open the Ubuntu One client and fails?
If that's the case I had the same problem a while back. I was able to launch
Ubuntu One from the MeMenu, but that's not a viable option when it should start
from Sys>Pref...

You can try this link 

[http://ubuntuforums.org/showthread.p...rrerid=1042836]("http://ubuntuforums.org/showthread.php?t=1297076&referrerid=1042836")

Or you can try:

 by deleting the following config file:  ~/.config/ubuntuone/syncdaemon.conf

See if one of these gets you up and running. If worse comes to worse, you can follow
the instructions in the link to purge and reinstall Ubuntu One. It's not as painful as it looks.
Hope this helps.

Jaco

---

### Post by duanedesign on 2010-04-17
cogier,
If you were not prompted to add your computer on first run please try the following.

*System > Preferences > Preferred Applications* make sure Firefox is the default browser.

Also do you have any script blocking software like NoScript? If you are running NoScript [look at this FAQ]("https://answers.launchpad.net/ubuntuone-client/+faq/957").  Are you behind a Proxy?

Make sure there are no lingering authentications from other installs.

   1. Quit the Ubuntu One Preferences. Then run the following command in a Terminal *(Applications > Accessories > Terminal)*:
```
u1sdtool -q; killall ubuntuone-login
```
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button and then close the page.
   8. *Open System -> Preferences -> Ubuntu One* or *MeMenu -> Ubuntu One*
   9. a web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer 

You should be connected after you follow these steps. If not there is one last thing I would try before filing a bug.

Open a Terminal and run the following:

```
sudo apt-get install ubuntuone-client-tools
```

After that installs run the following in the Terminal:

```
u1sync --authorize
```

The webpage will come up asking you to login then it should ask you to add your computer.

If you have had no success this far I would file a bug. If you file a bug can you please attach your logs to a bug report. The report will have a 'Add Attachment or Patch' button. Just zip your *$HOME/.cache/ubuntuone/log/* folder and attach the zip to the report. You can zip the folder by right-clicking on it and selecting compress. To file a bug run the following in a Terminal:

```
ubuntu-bug ubuntuone-client
```

Apport is preferred, however you can also file a bug manually at: 

[https://bugs.launchpad.net/ubuntuone-client/+filebug](https://bugs.launchpad.net/ubuntuone-client/+filebug)


-
-

---

### Post by cogier on 2010-04-18
Thank you all for your help. Jaco's advice to delete the file worked, I was taken straight to the right place.

You are all stars!

---

### Post by rudihawk on 2010-04-18
> **cogier said:**
> Thank you all for your help. Jaco's advice to delete the file worked, I was taken straight to the right place.

You are all stars!

Glad you got it working!

You can mark the thread as solved :)

---

