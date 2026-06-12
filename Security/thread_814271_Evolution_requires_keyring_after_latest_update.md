---
title: "Evolution requires keyring after latest update"
date: 2008-05-31
forum: Security
---

### Post by timzak on 2008-05-31
It seems that after the most recent update to Evolution, it now requires to type in the keyring password the first time you try to open Evolution after booting the computer.  I've seen a few other posts on this topic, but no reasonable explanation as to why this new "feature suddenly appeared.

I don't mind having to do this once per boot up as an added layer of security, but I'd like to be able to disable it if I want to.  

Was this intentional or is it a bug in the latest Evolution update?

---

### Post by wbrothman on 2008-05-31
I cannot answer your questions about why, but I will tender an observation: when I disabled auto login, and was, therefore, obliged to log onto the system after boot-up with my username/password, Evolution no longer pestered me for a keyring password.

---

### Post by timzak on 2008-05-31
> **wbrothman said:**
> I cannot answer your questions about why, but I will tender an observation: when I disabled auto login, and was, therefore, obliged to log onto the system after boot-up with my username/password, Evolution no longer pestered me for a keyring password.

Hmmm...you're right.  I did have auto login enabled (I'm the sole user of my computer), but once I turned that off, I no longer needed the pword to start Evolution.  Does anyone else know if this was an intentional change in Evolution to require a keyring pword if auto login is enabled?

---

### Post by The Cog on 2008-06-01
I don't use auto-login and I got the same question this morning.

I don't have a keyring either. If it refuses to start without the keyring password then I may simply have to abandon using Evolution as my email client. I'll find out when I'm back at work tomorrow.

---

### Post by Nicademus on 2008-06-01
I used auto-login and Evolution repeatedly asked for keyring password. Changed to manual login and Evolution still asks for keyring password on a repeated basis. Entering keyring password does not stop the window from re-appearing. It appears to prevent the sending of email, not receipt. All worked fine until latest software upgrade on Sat 31st May.

---

### Post by Jovaro on 2008-06-02
I have the same issue, without auto-login. It is quite irritating I think. If someone has more information on this that please let us know.

---

### Post by Gourgi on 2008-06-03
the procedure below worked for me, i hope it helps : 

1) Go to ~/.gnome2/keyrings and make backup copies of the files elsewhere
2) Go System--> Preferences --> Encryption and keyrings
or if you can't find it type in terminal ```
seahorse-preferences
```
3) At first tab (Password Keyrings) select login and click Remove Keyring
4) logout and login again
5) open evolution and ... pray it works :lolflag:

---

### Post by twl on 2008-06-03
Gourgi's solution didn't work for me.  When I logged back in, it not only prompted me to set a keyring password, it also asked for passwords for both of my POP3 servers before retrieving mail from them.  On subsequent logins, it's back to prompting me for just the keyring password.

Anybody have any other ideas?  Failing that, what are some good alternatives to Evolution to try?

---

### Post by twl on 2008-06-03
Here's how I fixed it (in 8.04):

System>Preferences>Encryption and Keyrings
In the Password Keyrings tab, select "default".
Click on Change Unlock Password.
Enter the old password (the one you've been prompted for when you start Evolution), but leave the new password fields blank.
It will prompt you with: Store Passwords Unencrypted?.  Click on Use Unsafe Storage.

FYI, this is apparently "unsafe".  Whatever.  Now it no longer asks me for a default keyring password the first time I start Evolution after booting.

I still don't understand why this became a problem with the latest update to Evolution.  I thought the point of having the libpam-gnome-keyring package installed was to make GDM automatically unlock your gnome keyrings when you login.  Anyway, this worked for me.

---

### Post by timzak on 2008-06-03
This fixed it for me too, thanks.  Although I had a little scare after applying the changes the first time I rebooted I ended up at a command prompt (no GUI).  After jumping through a couple of hoops, I got it to load up and since then the system has worked normally.

One difference from your instructions:  I don't have "default" on the Password Keyrings tab.  Instead, I have:

login *Automatically unlocked when user logs in*

I selected this in place of default and followed the rest of your instructions.


> **twl said:**
> Here's how I fixed it (in 8.04):

System>Preferences>Encryption and Keyrings
In the Password Keyrings tab, select "default".
Click on Change Unlock Password.
Enter the old password (the one you've been prompted for when you start Evolution), but leave the new password fields blank.
It will prompt you with: Store Passwords Unencrypted?.  Click on Use Unsafe Storage.

FYI, this is apparently "unsafe".  Whatever.  Now it no longer asks me for a default keyring password the first time I start Evolution after booting.

I still don't understand why this became a problem with the latest update to Evolution.  I thought the point of having the libpam-gnome-keyring package installed was to make GDM automatically unlock your gnome keyrings when you login.  Anyway, this worked for me.

---

### Post by wangvs80 on 2008-06-03
This worked for me!  Thanks

---

### Post by forestpixie on 2008-06-04
Found this in search of answer for someone else - perhaps it will help others

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264)

---

### Post by timzak on 2008-06-04
> **forestpixie said:**
> Found this in search of answer for someone else - perhaps it will help others

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264)

Interesting, this sounds like it was an intentional feature addition for added security.  I wish they would have made this clear during the update process.  For example: "In this update to Evolution we have added an additional security layer to prompt for keyring password on machines where auto-login is enabled."  That would have prevented a lot of confusion for Evolution users.

Thanks for posting that link!

---

### Post by forestpixie on 2008-06-04
Appears that way - if I'd found the link when I was losing patience I might still be using evolution :)

---

### Post by sum1cross on 2008-06-05
See my post at the following location also:

[http://ubuntuforums.org/showthread.php?t=813201&highlight=keyring](http://ubuntuforums.org/showthread.php?t=813201&highlight=keyring)

As long as you know your install password (the one you used to install Ubuntu) this seems to work.

Have fun!

---

### Post by ayova on 2008-06-05
[QUOTE=twl;5105310]
I followed twl's way...But i didnt see any "default" selection
So,here is how I did:
System>Preferences>Encryption and Keyrings
Click " Password Keyrings " tab,
 and then
Click "Remove Keyring" tab

it worked for me, thanks.
(ubuntu 8.04)

---

### Post by zephyrus17 on 2008-06-20
Frankly, this keyring thing reminds of vista's activation thing. Which isn't a good sign.

---

### Post by The Cog on 2008-06-21
Is there a way to tell evolution not to use the f***ing keyring?

Every morning when I boot my laptop, the very forst thing that happens when I log in is that a popup appears saying evolution wants access to the keyring.
So I click Deny
The popup disappears.
Another popup appears saying Evolution wants access to the keyring.
So I click Deny
The popup disappears.
Another popup appears saying Evolution wants access to the keyring.
So I click Deny
The popup disappears.
Another popup appears saying Evolution wants access to the keyring.
So I click Deny
The popup disappears.

Every time I click compose mail in Evolution, the CPU usage shoots to 100%. When I kill the gnome-keyring-daemon process, two things happen: 
1 - the CPU usage returns to normal
2 - A popup appears saying Evolution wants access to the keyring.
So I click Deny
The popup disappears.
Another popup appears saying Evolution wants access to the keyring.
So I click Deny
The popup disappears.
Another popup appears saying Evolution wants access to the keyring.
So I click Deny
The popup disappears.
Another popup appears saying Evolution wants access to the keyring.
So I click Deny
The popup disappears.
Then I can write my email.

If this is Ubuntus finest release, one shoud perhaps give up hope and look for a distro where the devs don't insist it's not a bug it's a feature. This feature is slowly begining to really piss me off. 

Is there any other email client that can talk to an exchange server? The idiots won't enable POP3 or IMAP so it has to use MS proprietary secret sauce.

Alternatively, is evolution this poor on KDE? Maybe it's just gnome that's all messed up.

---

### Post by Tridion2000 on 2008-06-21
What is a keyring password?

---

### Post by rkosby on 2008-06-24
I just fixed my problem too.  I didn't follow twl's instructions exactly though.  I entered entered a new password for default (it appears the old one was my login password).  I set the location for application passwords combo box at the bottom to default.  This did the trick.  It asked for my pop password once and has been fine since.  Thanks twl.

---

### Post by TheRingmaster on 2009-04-25
> **Gourgi said:**
> the procedure below worked for me, i hope it helps : 

1) Go to ~/.gnome2/keyrings and make backup copies of the files elsewhere
2) Go System--> Preferences --> Encryption and keyrings
or if you can't find it type in terminal ```
seahorse-preferences
```3) At first tab (Password Keyrings) select login and click Remove Keyring
4) logout and login again
5) open evolution and ... pray it works :lolflag:

it seems as though the jaunty jackalope has seen some changes in this area, because I no longer see any of these options and I am therefore stuck with entering my (being my grandfather's) password every boot.

---

### Post by Victormd on 2009-04-25
You're right, I'm trying to figure out the same thing...

---

### Post by Victormd on 2009-04-25
The Ringmaster, are you trying to remove the password or just pointing it out? I'm asking because I just removed it in Jaunty so just let me know if you need the steps.

---

### Post by TheRingmaster on 2009-04-26
> **Victormd said:**
> The Ringmaster, are you trying to remove the password or just pointing it out? I'm asking because I just removed it in Jaunty so just let me know if you need the steps.



that would be helpful!

---

### Post by Victormd on 2009-04-27
Sorry, just saw your post. When I get home I'll post the steps.

---

### Post by Victormd on 2009-04-27
The way I removed it was by going to **Applications>Accessories>Passwords and Encryption Keys** then click on the **Passwords** tab and you should find a list or at least 1 entry, i.e., "Passwords: login".

If you click on the **>** before the item it will expand and you will see what it's for - this is good so you don't open your system any more than you have to.

Simply click on the passwords item you want and select "Change Password" and enter a blank password. This will remove the password for that specific item in the keyring.

---

### Post by yuki86 on 2009-05-08
in 9.04 this worked for me:

1. application > Accessories > Passwords and Encryption Keys > Passwords, right click on login passwords and remove

2. start evolution, it asks for mail passwords just type, than it asks for keyring pass, just type nothing and click ok, it says to store passwords unsafely so click on it

thats all

---

### Post by vb1022 on 2009-05-08
Thanks

:KS [COLOR=White][.]("http://www.sanabes.net/vb/")[/COLOR]

---

### Post by kahunals on 2009-06-03
Warning:  Totally New Ubuntu/Linux user!

When I go to Passwords and Encryption Keys I do not see a tab for changing the password.  There is a line indicating that there is no password set.  However, I still have the Evolution keyring request "bug" or whatever it is.

PS  I'm using Ubuntu Jaunty Jackalope to reinvigorate an old PC with a 500MHz CPU.  I'm impressed overall except for this keyring business.

---

### Post by boddhisatva on 2009-06-11
This is what worked for me:
Applications>Accessories>Passwords and Keyrings
Select 'Passwords' tab
Right-click on default password, select 'Change password'
Type in old password, and leave the new password fields blank.
When there's a warning, just confirm.

---

### Post by FrankP1 on 2009-08-16
I don't know if this is the 'correct' way to solve this but I found that the following worked:

System -> Preferences -> Encryption and Keyrings
In the 'Password Keyrings' tab

There I found that only the 'login' keyring existed. I created a new one as follows:

'Add Keyring'
Gave it a name
Gave my usual password as the password  (not sure if it would be better to use a different one).

I then selected this new keyring in the drop down list 'Location for Application Passwords'

After that Evolution worked and stopped asking for keyrings.

---

### Post by wygee on 2009-11-01
> **yuki86 said:**
> in 9.04 this worked for me:

1. application > Accessories > Passwords and Encryption Keys > Passwords, right click on login passwords and remove

2. start evolution, it asks for mail passwords just type, than it asks for keyring pass, just type nothing and click ok, it says to store passwords unsafely so click on it

thats all

thanks yuki86, that worked for me!:D

---

