---
title: "Ubuntu One problem"
date: 2010-03-31
forum: Ubuntu One (CLOSED)
---

### Post by churfsan on 2010-03-31
I installed Lucid (Beta 1) on my home machine. 
UbuntuOne connected alright

However, in the dialog which shows the connected computers to the account, I found that there are a lot of old computers (previously linked from my home computer, office computer, Virtual Box installations. Hence, I wanted to delete all these computer links and only add my home computer and office computer afresh. Hence I deleted all the computer links and in the end, it shows one "LOCAL MACHINE" entry which does not go away. 

Now, from my office computer (again Lucid Beta1) I am able to access the Ubuntu One account and registered my office computer. But in my home computer I am unable to access Ubuntu One. I tried un-installing and then re-installing the Ubuntu One, but still does not work, and stubbornly displays only one entry as "LOCAL MACHINE" and I cannot figure out anyway how to add my home computer to Ubuntu One and access the same

Is there some way to completely uninstall Ubuntu One (along with all settings) and then re-install? Will this help? Any other solutions?

Please help.

---

### Post by joshuahoover on 2010-03-31
> **churfsan said:**
> I installed Lucid (Beta 1) on my home machine. 
UbuntuOne connected alright

However, in the dialog which shows the connected computers to the account, I found that there are a lot of old computers (previously linked from my home computer, office computer, Virtual Box installations. Hence, I wanted to delete all these computer links and only add my home computer and office computer afresh. Hence I deleted all the computer links and in the end, it shows one "LOCAL MACHINE" entry which does not go away. 

Now, from my office computer (again Lucid Beta1) I am able to access the Ubuntu One account and registered my office computer. But in my home computer I am unable to access Ubuntu One. I tried un-installing and then re-installing the Ubuntu One, but still does not work, and stubbornly displays only one entry as "LOCAL MACHINE" and I cannot figure out anyway how to add my home computer to Ubuntu One and access the same

Is there some way to completely uninstall Ubuntu One (along with all settings) and then re-install? Will this help? Any other solutions?

Please help.

This is a bug we're fixing with Beta2. Until then, please do the following to work around this problem:

1. Open Applications->Accessories->Passwords and Encryption Keys
2. Right-click on the ubuntuone token and select "Delete"
3. Open System->Preferences->Ubuntu One

You should be prompted to re-add your computer to your Ubuntu One account via your web browser. The problem is when you removed your local machine from your account the client never deleted the token on the computer. With a token on your computer but the computer not authorized on your account, authorization fails. Again, we've got a fix for this problem which will be released with Beta2 which comes out in about a week from tomorrow.

[https://launchpad.net/bugs/545506](https://launchpad.net/bugs/545506) 

Thank you,

Joshua

---

### Post by churfsan on 2010-04-03
> **joshuahoover said:**
> This is a bug we're fixing with Beta2. Until then, please do the following to work around this problem:

1. Open Applications->Accessories->Passwords and Encryption Keys
2. Right-click on the ubuntuone token and select "Delete"
3. Open System->Preferences->Ubuntu One

You should be prompted to re-add your computer to your Ubuntu One account via your web browser. The problem is when you removed your local machine from your account the client never deleted the token on the computer. With a token on your computer but the computer not authorized on your account, authorization fails. Again, we've got a fix for this problem which will be released with Beta2 which comes out in about a week from tomorrow.

[https://launchpad.net/bugs/545506](https://launchpad.net/bugs/545506) 

Thank you,

Joshua

Thanks Joshua,

I followed your directions and it solved the problem.

Another small issue (may be a noob type):

I can see the Ubuntu One folder in my home directory. This is now there in both my home computer and my office computer. But how to initiate the synchronization? 

I know that there are several files in my Ubuntu One account (from previous Karmic installation), but none of the files show up in my /home/UbuntuOne folder now. This was done automatically in previous Karmic installations, and largely worked most of the times, whenever a file is dropped in this folder.

Is this problem a lucid beta1 regression? Or is  there something wrong in my setup? 

I would really like to use Ubuntu One. At present I am also using dropbox, and it is much more streamlined and trouble-free. I would really like to see Ubuntu One work at that level, and I am sure it will be, by the time Lucid is released.

Please help

Churfsan

---

### Post by joshuahoover on 2010-04-05
> **churfsan said:**
> Thanks Joshua,

I followed your directions and it solved the problem.

Another small issue (may be a noob type):

I can see the Ubuntu One folder in my home directory. This is now there in both my home computer and my office computer. But how to initiate the synchronization? 

I know that there are several files in my Ubuntu One account (from previous Karmic installation), but none of the files show up in my /home/UbuntuOne folder now. This was done automatically in previous Karmic installations, and largely worked most of the times, whenever a file is dropped in this folder.

Is this problem a lucid beta1 regression? Or is  there something wrong in my setup? 

I would really like to use Ubuntu One. At present I am also using dropbox, and it is much more streamlined and trouble-free. I would really like to see Ubuntu One work at that level, and I am sure it will be, by the time Lucid is released.

Please help

Churfsan

Hi Churfsan,

Our latest update in Lucid (ubuntuone-client 1.1.91-0ubuntu1) should fix this. Prior to this release in Lucid, the client would not auto connect. So, you may need to open System->Preferences->Ubuntu One, click on the "Devices" tab and click the "Connect" button there on both computers. That should get any files that are in queue to be synchronized. If that doesn't work, you'll likely need to file a bug and/or hop on #ubuntuone on Freenode IRC and ask for help there. I'm on there from 13:00-21:00 UTC as joshuahoover.

Thank you,

Joshua

---

### Post by Jacob111 on 2010-10-28
I'm currently running maverick and I'm having this problem. I removed my machine because I wanted to reset what was syncing.  So now I'm stuck with <LOCAL MACHINE> under clients with no way to connect to my existing U1 account.  There is no entry under "Password and Encryption Keys" to delete.

I have tried all the instructions for uninstalling all the software, removing the config files ~/.cache, and reinstalling, but it remains stuck on <LOCAL MACHINE>.  Why is this so hard to fix?  Where is Ubuntu One storing its configuration files, and why can't we just delete them and get the prompt again to connect to an account?

---

### Post by Jacob111 on 2010-10-30
Hey guys, after fiddling with this for waaaayyyy too long, I finally found a solution.  I was having the same symptoms as so many others: You are told to open "password and encryption keys" and "delete the Ubuntu One entry", but there is no "Ubuntu One" entry to delete.

Sooooo, I found a folder called ~/.gnome2/keyrings.  Deleting that folder resets ALL saved passwords on programs associated with the gnome desktop.  For instance, after deleting, I had to re-enter my passwords in evolution mail, BUT it also made it so launching Ubuntu One prompted me to add an account.

I think there's a bug with U1 such that it's saved password doesn't show up in the keyring, even though an entry exists.  Deleting the keyring deletes it.  Hope this helps.

---

### Post by 9170 on 2010-10-31
hi everyone, 

I still have a kind of a simple problem. It doesn't matter what I do, erasing passwords, stopping ubuntuone in the whole system, re-install it on the computer, open the web page while retyping my password, nothing works on both machines.  ](*,)  
It can't "see" my computers. 

Christian

---

### Post by 9170 on 2010-11-01
hi again

it just works fine, Ubuntu one. 
for some reasons, that I don't understand so far, have I not received all updates and by fixing this problem, Ubuntu one works as it should be. :)

Thank you!

Christian

---

### Post by 9170 on 2010-11-01
ok, the problem was that I have excluded some updates in my software sources and there was the place they vanished. 

hope that this will help someone! 

christian

---

