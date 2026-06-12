---
title: "Authentication Failing..."
date: 2009-12-08
forum: Security
---

### Post by animalhouse100 on 2009-12-08
I am a new user to Ubuntu.  I recently had a custom build with Ubuntu on 50% partition.   The builders loaded Ubuntu, set up my user id and password.   I have had no problem with authentication  until this weekend.   When I try to download any new programs or allow any new upgrades, the authentication is failing.   These activities ask for a password.  I have tried entering the supplied password and then the userid when that did not work. 

If I go to system/preferences/about me, it shows the userid they set for me.  When I select "change password" and enter the password they provided, it just sits with the round circle (would be hour glass in windows) spinning indefinitely.

I did call the custom builder and they had me enter the bios.  Under "Boot" the supervisor and user password showed "not installed".   They didn't know what else to do and stated they do not support Ubunti, only Windows.  They load Ubuntu as courtesy, so they would not try to help me further.   Not sure what to do now....     Any ideas?

Any help would be greatly appreciated as my goal was to become as familiar w/ Ubuntu as possible and eventually make it my primary OS.  Rignt now I am very stuck!! ](*,)

Thank you
Alane

---

### Post by cariboo on 2009-12-08
When you see the grub prompt press esc and select to boot in recovery mode, at the menu use the arrow keys to select drop to root prompt and press enter. Once at the prompt type: 

```
passwd <username>
```

where <username> = your user name. Just enter a new password, it won't be echoed back to you. Once you have created a new password type:

```
exit
```

Then select resume to get to your desktop.

---

### Post by animalhouse100 on 2009-12-13
I tried to follow your instructions.  Did boot in recovery mode, used the arrow keys to select "drop to root directory" and hit enter.  At the prompt, I typed "Code:".  It did not recoginze it.   So I tried "passwd".   Probably should not have done that but it did prompt me.  So I entered my new password.   Hit exit and booted up normally.  

Tried to update software and it is still failing authentication.   When back thru the boot up in recovery mode, but now it is asking for "Give root pswd for maintenance" which it did not do 1st time in.  I entered the password I had updated earlier.  It then gave me "root@(computer name):    I must have set a password for root maintenance.

I then entered exit to select normal login but it is prompting me for Login.   I entered the pswd I entered earlier but then I get a prompt for Pswd.  So I entered the pswd I added earlier again.   I get "incorrect pswd".   Since I didn't set a login id earlier, I don't know what it should be.    

I tried the orignal login id and pswd the builders had set for me.  Didn't expect it to work and it didn't.    Tried a couple of other combinations.  Nothing is working.  

So I evidentally only set a pswd for root maint and skrewed that up.     I can boot up ok but I still can't update or download software.   And really don't understand why it didn't [COLOR=#2D4038]recognize[/COLOR] "Code:"  at root prompt.   

I sure need some additional help if someone can please assist.  I would be most grateful.  :confused:

Thank you
Alane

---

### Post by animalhouse100 on 2009-12-13
Well, I feel pretty stupid.  I was to enter "passwd <my username>.  

passwd <username>
So....   now how do I undo creating a root login/pswd??   

So new to this.   I think I'm catching on now....  #-o:oops:

---

### Post by cariboo on 2009-12-14
Run the following command in a terminal:

```
sudo usermod -p '!' root
```

To disable the root account. For more info on setting passwords and more, have a look [here]("https://help.ubuntu.com/community/RootSudo#Re-disabling your root account").

---

### Post by animalhouse100 on 2009-12-14
Ok...   I was able to finally change my password.  I can now update/download software=D>

Thank you!

I then entered this command in terminal mode:

sudo usermod -p '!' root 

rebooted, came up in root prompt, then entered exit to see if it would not prompt for login.    

It still prompted for login to exit:   

computer name user id: 
Password:

Nothing I tried works so I just do a hard shut down and reboot.  I read through your link you provided on disabling root acct, but it looked like another method was not reccommended by Ubuntu:

**Remove Password Prompt For sudo**

**Edit the sudoers file** 
Open a Terminal window. Type in **sudo visudo**. Add the following line to the END of the file (if not at the end it can be nullified by later entries): 

<username> ALL=NOPASSWD: ALL


Do you think I should try this? 

Thank you for your help!!   
Alane

---

### Post by cariboo on 2009-12-14
When you start in recovery mode it always comes up at a root prompt. When you start normally, open a terminal, and you should see your username.

---

