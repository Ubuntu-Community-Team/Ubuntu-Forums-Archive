---
title: "Ubuntu One - Maverick"
date: 2010-09-03
forum: Ubuntu One (CLOSED)
---

### Post by altor on 2010-09-03
I've just read the following 3d:
[http://ubuntuforums.org/showthread.php?t=1554953](http://ubuntuforums.org/showthread.php?t=1554953)

I'd like to do the same (U1 on Ubuntu 10.04 and 10.10) but I can't find the way. 

In particular, I do not have in the upper bar - under the name I use to login in my machine - the possibility to connect to ubuntu one I used with 10.04 as per instructions. 
If I log in my U1 account from a web page I do not find the way to add my new machine.

Before reading this forum I thought that I had to wait for the Maverick final release but now I  am asking for your help....

Thanks in advance

---

### Post by afrowildo on 2010-09-06
To connect a machine to Ubuntu One, you navigate to 

**System** -> **Preference** -> **Ubuntu One**

and select manage account. From there, you will be taken to a web page that will give you the option to add your current computer.

---

### Post by MrKaiser on 2010-09-07
I do not see that option on the account page. I can remove machines but I have no idea where to go to add machines on that page. I tried executing

```
 killall ubuntuone-login ubuntuone-syncdaemon 
``` and the output was
```
 ubuntuone-login: no process found
```

---

### Post by dr.peters12 on 2010-09-07
I too don't get any Ubuntu One drop-down under my Me applet.

Selecting 'Manage Account' from System -> Preferences, and logging in, doesn't seem to trigger anything either.  I can click "Connect" under the Ubuntu One Preference's Devices Tab, but nothing ever happens.

Attached is a picture of my Me Menu.

---

### Post by dsfitzpat on 2010-09-07
No luck here either.  Chances are this is a bug - has anyone found a report filed on Launchpad?

---

### Post by dr.peters12 on 2010-09-07
> **dsfitzpat said:**
> No luck here either.  Chances are this is a bug - has anyone found a report filed on Launchpad?
Looks like someone did post it.  Please subscribe:
[https://bugs.launchpad.net/ubuntuone-client/+bug/626659](https://bugs.launchpad.net/ubuntuone-client/+bug/626659)

---

### Post by duanedesign on 2010-09-08
Yes their was an Ubuntu-sso-client bug. From what I have heard the new package with the fix should be available late today/ early tomorrow.


As far as the Me Menu not having Ubuntu One, you can access Ubuntu One under:

System -> Preference -> Ubuntu One


To add machines all you have to do is open the Ubuntu One client. That is the System -> Preference -> Ubuntu One. When you run this for the first time it will prompt you to add your computer. If it does not their is either a bug or their is a Token leftover in your keyring. So if opening the client does not open a browser I would follow these steps to make sure their is not a token that is left over from a previous install, or failed install.

   1. Quit the Ubuntu One client (if it is open)
   2. Open System->Preferences->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open System->Preferences->Ubuntu One
   9. a web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer 

**UPDATE:** the new ubuntu-sso-client package has been uploaded. this should fix the authentication issues Maverick users were having.


thank you,
duanedesign

---

### Post by linux.alucard on 2010-10-20
Unfortunately for me the authentication failed :( I've tried everything

Ubuntu 10.10

---

