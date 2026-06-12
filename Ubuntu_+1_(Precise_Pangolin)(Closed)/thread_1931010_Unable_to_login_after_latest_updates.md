---
title: "Unable to login after latest updates"
date: 2012-02-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rajeev1204 on 2012-02-24
System upgraded fully. welcome screen as usual, when i enter password it restarts the display manager (or so it seems ) and brings me back to the login screen again.'



Edit: i installed the gnome-session package and all is fine now. Seems like it was uninstalled during an upgrade.

---

### Post by Hazzabin on 2012-02-24
Mate mine did that too, I don't know how long you waited but mine eventually seem to 'remember' what it was suppose to do.....did start 12.04 ok

regards
hazz

---

### Post by effenberg0x0 on 2012-02-24
If this is a .Xauthority issue again, the solution would be to do this:
Press Ctrl+Alt+F6 and login to VT with username and password
```

mv $HOME/.Xauthority $HOME/.Xauthority.backup
HOST=$(hostname)
key=$(perl -e 'srand; printf int(rand(100000000000000000))')
key=$key$key
xauth add ${HOST}/unix:0 . $key
sudo chown $USER:$USER $HOME/.Xauthority
sudo chmod 600 $HOME/.XAuthority
sudo service lightdm restart

```Otherwise, it would be nice to see some logs. If you want to automate that, you can run this to automatically search your logs for possible problem-related keywords and create a file named MyLog.log at your home directory with a summary of it.
```

MYLOG=$HOME/MyLog$(date +%d.%m.%y).log; echo '['"code"']' >> ${MYLOG} && uname -a >> ${MYLOG} && lsb_release -a >> ${MYLOG} && for LOGFILE in $(ls /var/log/*.log); do sudo grep -iHw 'segfault\|warning\|error\|critical\|lightdm\|\(WW\)\|\(EE\)' $LOGFILE | tee -a ${MYLOG}; done && echo '['"code"']' >> ${MYLOG}

```Then you can use your favorite text editor to read MyLog.log and see if you can pinpoint something interesting, which may relate to the problem you're having. Or just paste whatever log message you want here for others to have a look at it.

Regards,
Effenberg

---

