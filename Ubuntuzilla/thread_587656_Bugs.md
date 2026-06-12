---
title: "Bugs"
date: 2007-10-22
forum: Ubuntuzilla
---

### Post by bbukh on 2007-10-22
I ran the ubuntuzilla and encountered the following bugs:

1) The text that the script prints in the terminal window does not respect the width of the terminal window. Thus the long lines get cut. Since some of the lines are very long, even at full screen terminal some lines are cut (I like big fonts; in case you wonder).

2) The script apparently does not check whether firefox is currently running (using "ps" command) nor it instructs the user to close the firefox. Trying to install the new version firefox while the old one is running lead to errors in my attempt.

3) The last remark is not about a bug, but a suggestion. The script should print some kind of prompt before invoking "sudo", so that the user knows what kind of "Password:" is expected of her.

Boris

---

### Post by nanotube on 2007-10-23
> **bbukh said:**
> I ran the ubuntuzilla and encountered the following bugs:


thanks for your report! :)
> 
1) The text that the script prints in the terminal window does not respect the width of the terminal window. Thus the long lines get cut. Since some of the lines are very long, even at full screen terminal some lines are cut (I like big fonts; in case you wonder).

i have never seen that behavior before - lines wrap just fine on my terminal, and nobody has ever reported otherwise. so... i just don't know how to address this. what terminal software are you using? have you changed any settings?

> 2) The script apparently does not check whether firefox is currently running (using "ps" command) nor it instructs the user to close the firefox. Trying to install the new version firefox while the old one is running lead to errors in my attempt.

what kind of errors? could you post them here? i wouldn't have thought it would cause errors (though i haven't tried myself...) but generally you are right, we should either check to see if it's running, or prompt user to close - it's generally a decent idea to close a program before upgrading it, after all.

> 3) The last remark is not about a bug, but a suggestion. The script should print some kind of prompt before invoking "sudo", so that the user knows what kind of "Password:" is expected of her.

hm, good point. :)

---

### Post by bbukh on 2007-10-23
> **nanotube said:**
> thanks for your report! :)
what terminal software are you using? have you changed any settings?

The program is Konsole, and I never changed any of its settings.

> **nanotube said:**
> 
what kind of errors? could you post them here?
 

Linking plugins

ln: target `/opt/firefox/plugins' is not a directory
sudo ln -s -f Sorry, try again. /opt/firefox/plugins
Previous command has failed to complete successfully. Exiting.

Boris

---

### Post by nanotube on 2007-10-24
> **bbukh said:**
> The program is Konsole, and I never changed any of its settings.

i can't reproduce this problem - runs fine on my konsole. since nobody else has ever mentioned this before, i am suspecting it is something specific to your setup...
 
> 
Linking plugins

ln: target `/opt/firefox/plugins' is not a directory
sudo ln -s -f Sorry, try again. /opt/firefox/plugins
Previous command has failed to complete successfully. Exiting.


hm, very peculiar... it appears that it failed to determine the plugin path correctly... which should not depend at all on whether ff is running or not. but you say that after you closed the existing running ff process and installed again, it worked?

---

