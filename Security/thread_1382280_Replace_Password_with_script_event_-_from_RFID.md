---
title: "Replace Password with script event - from RFID"
date: 2010-01-15
forum: Security
---

### Post by charliehorse55 on 2010-01-15
[SIZE="5"]EDIT: I am now just looking for a way to multi-task in PAM, if at all possible.[/SIZE]


Basically I would like to supplement replace my password based logon with and RFID scanner. The output of the RFID scanner looks like this:



Tag Read: 0a006f4757
Tag Lost: 0a006f4757
Tag Read: 2800c48994
Tag Lost: 2800c48994

As you can see I scanned some different RFIDs. 

Basically I would like for my logon screen to wait until my script gives the message "Tag Read XXXXX where xxx is the RFID unique ID.

In case I lose my RFID, I would like to also allow me to type my password in. 

Is this possible?

---

### Post by vivanjones on 2010-01-15
this is just a stab in the dark, probably not the most sensible or straightforward way, and its rather messy, but you could call your script from /etc/gdm/Init/Default, and use it to stop gdm and directly start the x session for the user e.g. ```
/etc/init.d/gdm stop
su *username* -c gnome-session
``` which will start a session for a given user without a password, but you'd be circumventing pam so the default gnome keyring wouldnt be unlocked, plus you'd want to restart gdm when they log out, which might involve creating a fake panel button to replace the logout button and execute a script to kill the session and restart gdm.
do you have a way of matching the id's with usernames?
also does your script poll periodically for the rfid or does it just check once at run-time?

---

### Post by vivanjones on 2010-01-15
acutally, thinking about it, its much easier to use pam-script to execute your script, return 0 if its finds a valid rfid, and have it set as sufficient in /etc/pam.d/common-auth and set the use_first_pass option on the pam_unix.so line so that it will use the typed password if the pam-script does not return success

ive used pam-script to do similar things on hardy but i don't have time to test it on jaunty today, but ill try it out and explain more clearly tomorrow

---

### Post by charliehorse55 on 2010-01-16
> **vivanjones said:**
> acutally, thinking about it, its much easier to use pam-script to execute your script, return 0 if its finds a valid rfid, and have it set as sufficient in /etc/pam.d/common-auth and set the use_first_pass option on the pam_unix.so line so that it will use the typed password if the pam-script does not return success

ive used pam-script to do similar things on hardy but i don't have time to test it on jaunty today, but ill try it out and explain more clearly tomorrow

So it will sit at a fully functional GNOME log-in until an RFID is scanned?

My script doesn't return a negative, it only waits until it hits positive. Would the script need to complete before I could type my password?

---

### Post by vivanjones on 2010-01-16
heres a rough outline of how you might use the pam-script method,
bear in mind it is very easy to lock yourself out of your installation with an incorrect pam configuration

a deb package for version 1.1.3 of pam-script can be downloaded [[COLOR="Blue"]here[/COLOR]]("http://sourceforge.net/projects/pam-script/files/")

after installation, modify your /etc/pam.d/common-auth to process the pam-script module by adding another auth line before the pam_unix line, to which you should append the use_first_pass option e.g.
```

...
auth    sufficient                    pam_script.so pam_script_auth
auth    [success=1 default=ignore]    pam_unix.so use_first_pass
...

```

next create an /etc/pam-script/pam-script.d/pam_script_auth script to execute your scanner script e.g.

```

#!/bin/bash

RFID_SCRIPT_RESULT=`sh /path/to/your/script`;

#add code here to parse result/match UID with username
#and then set RFID_AUTH_SUCCESS=0 or 1 depending

exit RFID_AUTH_SUCCESS;

```

this method will require the user to insert their username and the rfid card before attempting to log in,
if the rfid match succeeds, the contents of the password field will be ignored and can be left empty,
if the rfid match fails e.g. the card is not present then the contents of the password field will be validated in the usual manner

note that if the password is not used the default password keyring cannot be unlocked, unless the keyring is locked with the card UID instead, which would cause it to be unable to be unlocked with regular password login.
whatever you decide to do with keyrings (e.g. dont encrypt them/dont use them at all) depends on what your users will be doing with the client.

---

### Post by vivanjones on 2010-01-16
> **charliehorse55 said:**
> So it will sit at a fully functional GNOME log-in until an RFID is scanned?

My script doesn't return a negative, it only waits until it hits positive. Would the script need to complete before I could type my password?

in that case you may have to run the script with an & subshell, which should allow gdm to continue to a login prompt while the script runs in the background, i havent tried this out yet

you could then get the script to terminate gdm on rfid success and start the user session, as well as a post-login script to terminate the rfid scan after a sucessful password-login, and a post-session/logout script to restart the rfid scan and gdm on logout depending on how the session was logged in to, but i would need to try this out first

---

### Post by charliehorse55 on 2010-01-16
Sounds good. Is there a way to make this work for multiple users (Require different RFIDs?) It can happen the same script, if needed.

This is just the computer that mainly me (But other memebers of my family) use for web surfing/email and some light games. 

I'd like the keychain to remain function even if that means leaving it unencypted. How would I go about doing this?

---

### Post by vivanjones on 2010-01-16
> **charliehorse55 said:**
> Sounds good. Is there a way to make this work for multiple users (Require different RFIDs?) It can happen the same script, if needed.

This is just the computer that mainly me (But other memebers of my family) use for web surfing/email and some light games. 

I'd like the keychain to remain function even if that means leaving it unencypted. How would I go about doing this?

i had already assumed that you were going to use multiple users, matching RFID's with usernames, for which you could just store a list in a text file of each user and their rfid and grep it with your script to discover the username when a card is inserted

as for the keyrings, heres a quote from [http://ubuntuforums.org/archive/index.php/t-1063623.html](http://ubuntuforums.org/archive/index.php/t-1063623.html)
> 
Go to the ~/.gnome2/keyrings folder. Delete any files you see there. Then logout and log back in. If you are prompted to enter a password for the keyring, leave the textboxes blank and click the Ok button (or the equivalent if it's not actually "Ok"). If you are then prompted to confirm that you want to use an unencrypted keyring, do so.

you will have to do  this once as each user

---

### Post by charliehorse55 on 2010-01-19
So what folder would I want to put that script into? Would I still need to install pam-script?

If I was to start the process in a sub shell like you recommended.

Is there really no way to get GDM to recognize the RFID as a replacement for the password? Maybe modifying PAM in some way could allow GDM to use the RFID in lieu of the password.

For example, you get to GDM prompt, type username, scan RFID, log in without ever having to kill gdm/manually start an x-session.

EDIT: For Fedora, not sure if you could get this to work in Ubuntu
[http://fedoraproject.org/wiki/Features/MultiplePAMStacksInGDM](http://fedoraproject.org/wiki/Features/MultiplePAMStacksInGDM)

It's basically just a way to multi-task pam-modules... perfect for what I want to do.

---

