---
title: "can't login acer laptop;how to do bios bypass to overcome failed ACER login and do te"
date: 2014-08-24
forum: Ubuntu Studio
---

### Post by ken78724 on 2014-08-24
from pdmKen post on kubuntu forum "Cannot open screen upon login" my subject is clearly discussed beginning with this concise title: &#8220;Unable to get past sign in screen&#8221;
i.e., After you log in, can you get to a TTY (old command prompt)?

Try*Ctrl Alt F1, and remember if you have other functions on your F keys this may be*Fn Ctrl Alt F1.
Then type the*startx*and see what happens..."

My revised original post says: "Ubuntu studio 12.04, fails as I cannot find a way to unlock the login keyring. I would like to gain benefit of your wisdom.   
 Note: I wish it were feasible to re-title this thread as   "Cannot open screen upon login". 

for the time being, I cannot follow up for about 9 days....

---

### Post by jejeman on 2014-08-25
I don't think anyone will understand what you are saying here.
BIOS does not have terminal, a specially one with Linux commands. BIOS is not a part of OS.

It is not clear where and why you can't log in. Can't log in to user of an OS, or to BIOS? Can't pass BIOS password or user password?

---

### Post by ken78724 on 2014-08-25
12.04 Studio with special PPA fails to login.  Cannot open screen upon login -- unlock the keyring. Comes up saying "cannot unlock the key ring"

please leap forth past my posts and responses about hardware

---

### Post by jejeman on 2014-08-25
What is a boot up password?

What about a recovery mod from GRUB? Dropping to root shell?

---

### Post by MartyBuntu on 2014-08-25
Are you sure you're typing in the correct password?

Is caps lock on, by any chance?

---

### Post by ken78724 on 2014-08-25
this thread is about  "Cannot open screen upon login" not about hardware...

---

### Post by ken78724 on 2014-08-25
replace thread title with concise  "Cannot open screen upon login"

---

### Post by ken78724 on 2014-08-26
correct title to thread  "Cannot open screen upon login"

---

### Post by jejeman on 2014-08-28
Well, I just do not understand is it a hardware problem or OS problem?
Why is mentioning ACER so important? It guides me to think that it is a hardware problem.

---

### Post by ken78724 on 2014-09-03
if you are having a similar problem see pdmken on Kubuntu Forum "Cannot open login screen."  &#8220;Your unlock login keyring is not recognized.&#8221;

 In 9 or so days, I'll be back to my Ubuntu studio 12.04 OS so I can save the PPA by getting past the "unlocked login keyring" problem. 

if I can finally log in, I'll upgrade to 14.04 studio. :popcorn:

---

### Post by ken78724 on 2014-09-21
hi, am back from overwhelming 14 days and found great help from persons who understand English. Hope to apply guidance once am rested. Here's what has worked... Helps below [kubuntu]automatically unlock keyring
"automatically unlock this keyring whenever i'm logged in" doesn't work
Hi All,
I want to share a solution to a problem I had with my new install of ubuntu 10.10
The problem was every time I logged into ubuntu, a dialog box would pop up asking me to enter my password for the default keyring, so that the network manager applet could connect to my encrypted wireless network. Despite checking the box "automatically unlock this keyring whenever i'm logged in", every time i did log in it would still ask me for the password! A quick google came up with no real solutions except for setting the password for the 'Default' keyring to blank.

My solution was:
uninstall network manager applet from Ubuntu Software Centre
immediately reinstall network manager applet
(^^^^^ not sure if these steps are really needed ^^^^^^)

Open System -> Preferences -> Passwords and Encryption Keys
In the Passwords tab, delete the 'passwords: Default' keyring
Right-click the 'passwords: login' key and select 'Set as default'

This fixed the problem for me. I think the cause was the login keyring was not set to be the default keyring. So even though logging in unlocked this keyring, the wifi keys were stored in another keyring that was the default, meaning I had to type the password again.

Hope this helps someone!
Ross

Re: "automatically unlock this keyring whenever i'm logged in" doesn't work
 *Originally Posted by*wxuyec* 
Hi, my system is 10.04. why can I not find what he said.
In password tab of my dialog for the password and encryption there is just
one option asking me to input password.
Hi,
In seahorse, I clicked right on my keyring "login" and chosen "default", and I removed my other keyring that was named "default".

However, I don't remember when, (before or after changing default keyring, or before or after removing old default), but I also clicked right on my login keyring, chosen "Lock", and after chosen "Unlock". In the dialog appearing, there was option about unlocking it when I log in.

---

