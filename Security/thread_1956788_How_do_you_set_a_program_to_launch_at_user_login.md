---
title: "How do you set a program to launch at user login?"
date: 2012-04-11
forum: Security
---

### Post by Kvothe on 2012-04-11
I want to set a program or command to listen for an SSH login and start when the user logs in over SSH. A script that will listen for and detect a user's login status and then start when the user appears is what I am looking for. Any help would be greatly appreciated.

---

### Post by Kvothe on 2012-04-12
Never mind, I figured it out. I wrote this script to take care of the problem...

```
#!/bin/bash
# get username
bold=`tput bold`
normal=`tput sgr0`
# username="ssh"
echo -n "Please enter a username to track: "; read username
echo " "
echo -n "Listening for login of user ${bold}$username${normal}..."
until [ "$(who -a | grep -c "$username")" -ge 1 ]; do
        sleep 1
done
echo " "
echo -n "${bold}$username has logged in!${normal}"
echo " "
echo -n "Loading watcher program..."
zenity --warning --text "SHH has logged in! Close this window to check it's movements." &
whowatch
echo " "
echo -n "Tracker has been terminated. Exiting . . ."
while [ "$(who -a | grep -c "$username")" -ge 1 ]; do
        zenity --warning --text "SHH is still logged in! Close this window to check it's movements.\n\n(Press CTRL+C to quit.)" &
        echo " "
        echo -n "${bold}$username is still logged in! Tracking again.${normal}"
	whowatch
        echo " "
        echo -n "Tracker has been terminated. Exiting . . ."
done
echo " "
echo -n "Done tracking. Enter 'whowatch' to continue tracking this computer."
```

---

