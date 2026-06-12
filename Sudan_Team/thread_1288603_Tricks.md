---
title: "Tricks"
date: 2009-10-11
forum: Sudan Team
---

### Post by zero-n on 2009-10-11
[B][SIZE="2"]Run Num Lock key on startup:
[/SIZE][/B]
1- First you need to download the script that will run num lock.
```
sudo apt-get install numlockx  
```

2-
```
gksu gedit /etc/gdm/Init/Default
```

3- add this statment to the file beginning.
```
 if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on
fi  
```

4- done do a restart to check it.



[B][SIZE="2"]Add time & date to [COLOR="Red"]history[/COLOR] command :
[/SIZE][/B]
1- open the bashrc file:
```
gedit $HOME/.bashrc
```

2- in the eof add this line
```
export HISTTIMEFORMAT="%h/%d - %H:%M:%S " 
```

3- done (but to may need to logout & in )


[**[COLOR="Red"]Source[/COLOR]**]("http://www.linuxac.org/forum/linuxac43/thread25345.html")

---

