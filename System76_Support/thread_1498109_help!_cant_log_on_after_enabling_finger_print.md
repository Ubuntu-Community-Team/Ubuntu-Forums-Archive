---
title: "help! cant log on after enabling finger print"
date: 2010-05-31
forum: System76 Support
---

### Post by dysonsphere23 on 2010-05-31
Hi,

I did the following as outlined on [http://knowledge76.com/index.php/Main_Page:](http://knowledge76.com/index.php/Main_Page:)

Instructions for Ubuntu 9.04
Configure PAM
Cut and paste the following commands into your terminal (Applications > Accessories > Terminal).
sudo cp /etc/pam.d/common-auth /etc/pam.d/common-auth_orig
gksudo gedit /etc/pam.d/common-auth
Change only this portion of the file from:
# here are the per-package modules (the "Primary" block)
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
to:
# here are the per-package modules (the "Primary" block)
auth    sufficient      pam_fprint.so
auth	[success=1 default=ignore]	pam_unix.so nullok_secure

Leave the rest of the file as is.

Save and close the file. This configuration will first try to read your fingerprint before asking your password. Go to Applications > Accessories > fprint project demo to register and verify your fingerprint. It takes some practice but works well once you get it. You can use your fingerprint reader to log in and for sudo commands.

I have Fingerprint GUI in accessories, but it would not register any finger swipes.  

Upon reboot, the login page will not accept my password anymore and there are no finger prints registered.

How may i log in to fix this mess?

Thanks

---

### Post by thomasaaron on 2010-06-01
Are you running 9.04?

Try swiping your finger four or five times. It should default to the password field.

If that doesn't work, we'll try to boot into recovery mode and undo the changes.

---

### Post by 29732 on 2010-06-04
I tried that as well for installing the fingerprint device but it just doesnt find the fingerprint reader 
I didn't do the exact same as you did (or I think i didn't) and I've never had any problems
I've read somewhere that if you type in or paste the line in the gedit document
auth required pam_fprint.so
and you have no fingerprints enrolled it'll just completely lock you out
But other than that, I didn't have problems I just type my password in and I'm logged on......
So that is sort of strange for that to do it.

---

### Post by Mendel314 on 2010-06-04
I have the same problem...
I can't access Common-auth to change it back either, since now that requires a fingerprint that doesn't exist

---

### Post by Mendel314 on 2010-06-04
Reboot and hold shift (this will bring up the GRUB menu)
it will say GRUB loading.  wait a minute, then you will see the choices. Choose the one that says recovery mode

you will see another menu, navigate down using arrow keys to the root option. You will now be logged in as root, and automatically have root privileges.

 You will have a command line at the bottom of the screen.

Write all of this down, you will need to enter this command, and make these changes, but won't be able to cut and paste them from the GRUB screen.
first enter this:

nano /etc/pam.d/common-auth

you will have loaded the file, which you can now edit with root privileges.  Be extremely careful now, do not change anything but the following.  

(if you want help in nano, ^ means press the ctrl key. There are commands listed at the bottom, help will bring up further options.  You shouldn't need them for this, however.)

Delete the line that says:
auth     sufficient     pam_fprint.so

immediately below that, you should see 2 lines that read
auth    [success=1 default=ignore]    pam_unix.so nullok_secure
auth    [success=1 default=ignore]    pam_winbind.so krb5_auth
change the first [success=1 default=ignore] to [success=2 default=ignore]
but not the second
this worked for me. I found the GRUB recovery mode info here, but had to make the other changes after examining the common-auth_orig file that I made to change it back.

[http://ubuntuforums.org/showthread.php?t=860681&highlight=fprint&page=4](http://ubuntuforums.org/showthread.php?t=860681&highlight=fprint&page=4)

someone there misspoke and said to press esc instead of shift.  It took me a little trial and error to figure this out, so I figured I'd just put all the steps up that I used. 

I'm assuming that you, like I did, just made changes in 10.04 assuming it would work out even though the instructions were for 9.04.  The thread I posted above should have better instructions for getting the fingerprint reader to work in 10.04.  I am going to try that now.

There is probably an easier way to do this by just deleting the common-auth file you have and changing the name of common-auth_orig to common-auth, but I figure I'm going to be messing with this file to get the finger print reader to work, so I might as well just keep the common-auth_orig file saved for future reference

---

### Post by isantop on 2010-06-07
Also note that the fingerprint reader on our laptops are all in beta, and are not yet suitable for day-to-day use. On some systems, the fingerprint reader does not work at all, and following the instructions to enable it may lock you out of your account, requiring you to use recovery mode as detailed above.

The best way to prevent this kind of situation is to open Fingerprint GUI *before* editing the file, and make sure you can register fingerprints at all. If you can't, avoid using the fingerprint reader for the time being.

---

