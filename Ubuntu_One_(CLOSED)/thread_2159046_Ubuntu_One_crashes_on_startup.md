---
title: "Ubuntu One crashes on startup"
date: 2013-07-01
forum: Ubuntu One (CLOSED)
---

### Post by Scooby-2 on 2013-07-01
*** UPDATE 5th July 2013*** Thanks to Ubuntu One support the crashing on startup is resolved but I was unable to add more than one device at a time - each time I tried to add a second machine it removed the first one from the device list. Support sent me a link to a page of suggestions for this but nothing there helped me. The "fix" in the end was to use DropBox instead. *** End of update ***

I have an old laptop running Xubu 12.04 lts and it syncs files without problem. I used to share the same files with a PC which was running 10.04 but it stopped connecting with Ubuntu One some while ago. I have just upgraded it to 12.04 and it now crashes as soon as I try to start it. It says fle sync error, auth fail and if I try to click anything else I get a box which says "Ubuntu One experienced an error. Sorry, an error has occurred and Ubuntu One needs to close." I have noticed that there is no notification icon in the menu bar and I am trying to start it from the Settings menu.

I have tried [this]("https://answers.launchpad.net/ubuntuone-client/+faq/778") procedure to try to remove the software and reinstall it but I cannot complete step 6 as there is no "Passwords and Encryption Keys" menu item under Accessories. This is the same for both the laptop and the PC, and both 10.04 and 12.04 and both Gnome and Xfce desktops.

[ATTACH=CONFIG]244302[/ATTACH]


I already have a post to ask if the missing menu item can be added, but this post is to ask if there is an alternative way of reinstalling or overwriting Ubuntu One...? (I don't really want to install from CD as it would take so long to put everything else back onto the machine.)

---

### Post by Irihapeti on 2013-07-01
See your other thread.

---

### Post by Scooby-2 on 2013-07-02
With thanks yet again to [**Irihapeti**]("http://ubuntuforums.org/member.php?u=346442") who seems to be single-handedly getting me through this. I ran:

```
sudo apt-get install seahorse
```

which now gives me a "Passwords & Keys" in the Gnome "Settings" menu. After deleting the Ubuntu One key (and removing and reinstalling the Ubuntu One software as per [this]("https://answers.launchpad.net/ubuntuone-client/+faq/778") link) and running it again, I get to the initial screen where  can open a new account or use an existing one. When I choose "Sign me in with an existing account"  I get "The authentication failed" after I enter my credentials. If I then click "I've forgotten my password (which isn't really the case) I get "Sorry, we did not recognise the email address."

I am stumped, because my laptop syncs files OK with Ubuntu One using the exact same credentials.

I don't know if I should close this thread as Ubuntu One no longer crashes. However, now it does not authenticate with known good credentials. I can log in to the Ubuntu One website and view the files I am syncing from my laptop, btw.

---

### Post by Irihapeti on 2013-07-02
Log into the web interface of Ubuntu One. Go to "My Account" and scroll down to the bottom of the page. You'll see a listing called "Devices".

Remove the offending machine from the list. Also go through the "remove Ubuntu One from your machine" routine again including removing the key. That leaves you with a completely clean slate &#8211; neither the server nor the local computer knows anything about each other.

You should now be able to set up a new account on the computer.

If for some reason this doesn't work, you'd need to talk to the devs or support.

---

### Post by Scooby-2 on 2013-07-04
Thanks again to **[Irihapeti]("http://ubuntuforums.org/member.php?u=346442") **for the advice, which I followed. From the web interace of Ubuntu One I checked the devices listed but only my laptop was listed. I removed the software from the PC yet again, including the key, and tried to set up an account on it again - but I got the same result.


I contacted Ubuntu One support and explained the problem. With lightening speed I got a reply with a list of steps to try. The first one was to run
```
sudo apt-get install --reinstall ca-certificates
```
which seemed to work. I reinstalled the software and this time it accepted my credentials. I was then offered the same folders to sync as those which I sync with on my laptop. Everything seemed fine and it synced immediately. Great, I thought, cooking with gas. However the problem then was that the laptop then gave the auth_fail message when I tried to connect, yet I had changed nothing on it.


I emailed Ubu One again and got a reply stating, "[FONT=arial]For more information, please take a look at [/FONT][https://one.ubuntu.com/help/faq/what-should-i-]("https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/")
[do-if-authentication-fails-auth_failed-state/]("https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/")." None of the three reasons listed there for getting this problem applied to me so I ended up freelancing. I am pleased to report that I did eventually get the laptop to sync again - but then I got auth_fail again on the PC.


After spending all afternoon trying to get both machines to work simultaneously I have found I just get CredentialsError in the ~/.cache/ubuntuone/log/credentials.log on whichever machine stops working. Adding a machine removes the one which was previously working. I found a post which suggested the following:
```
[B]sudo apt-get install ubuntuone-client-tools
[/B]**u1sync --authorize**
```
but I received "E: Unable to locate package ubuntuone-client-tools" on running the first command.


As Ubuntu One is so difficult to set up file sync with more than one machine - even with the help of the developers - I decided to look for an alternative. I decided against Google drive as it is still in beta - but in less than 10 minutes (with only 3 lines to copy and paste into the terminal on each machine) I was up and running with DropBox, syncing files on both machines. Less space - 2GB vs 5GB - less versatile, as it only allows one folder to be synced (~/Dropbox) whereas Ubuntu One allows any directories/files in the home directory to be individually selected for syncing) - but installing DropBox is totally hassle free.

Ubu One developers take note!

Thanks again to [B][Irihapeti]("http://ubuntuforums.org/member.php?u=346442")[COLOR=#000000].


[/COLOR][/B]

---

### Post by Irihapeti on 2013-07-04
The U1 developers rarely come here nowadays. Would you be able to file a bug on Launchpad?

---

### Post by Scooby-2 on 2013-07-05
Hi **[Irihapeti]("http://ubuntuforums.org/member.php?u=346442") **

Thanks again for your guidance I've had a look [here]("https://wiki.ubuntu.com/UbuntuOne/Bugs") at how to report a bug and it's all too technical for me. I haven't heard of most of what this page talks about and I regret to admit that even after reading it I don't know how to proceed! [This link]("http://askubuntu.com/questions/159999/adding-another-device-to-my-ubuntu-one-account") is the only reference that seems relevant to my situation, and it's all I've been doing on each machine. If this only affected me then at least I got around it with DropBox.

I'm going to try to chnge the title of the first post to something like "Unable to add second PC" as it's now more relevant to the problem and it may help someone else. I don't know if I'll be able to do it, though...

---

