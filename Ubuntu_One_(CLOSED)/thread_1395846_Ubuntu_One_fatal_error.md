---
title: "Ubuntu One fatal error"
date: 2010-02-01
forum: Ubuntu One (CLOSED)
---

### Post by PaulNL on 2010-02-01
Hello all,

I use Ubuntu 9.04 and have reinstalled Ubuntu One, now the problem when i start Ubuntu One i get a fatel eror end a red ! in the Ubuntu One icon. after that Ubuntu One stops working

Can someone tell me what to do ??


Paul

---

### Post by duanedesign on 2010-02-01
paulNL,
sorry to hear you are having problems with Ubuntu One. There are a couple of things that might be an issue here. First i would make sure that if you have 'Limit Bandwidth Usage' enabled that you make sure the Maximum Upload and Maximum Download are not set to zero(0). If that is the case  delete the ~/.config/ubuntuone/syncdaemon.conf file and restart the Ubuntu One client.

Also, make sure you are running at least ubuntuone-client 1.0.3. You can check this by opening a Terminal (Applications > Accesories > Terminal) and running the following:
```
dpkg -l ubuntuone-client
```
if you are using 1.0.2 or earlier you can find directions for upgrading here. [FAQ #930]("https://answers.launchpad.net/ubuntuone-client/+faq/930")

Those are two simple things you can check right away. If neither of these help i would recommend setting Ubuntu to log in [DEBUG] Mode and submit a bug by Right -clicking the applet and selecting 'Report a Problem'. Here is how you can provide the best information to help quickly solve your problem.

1) Quit the Ubuntu One client. R-click on the Ubuntu One applet and select 'Quit'

2) Open Applications->Accessories->Terminal, then run the command:
```
  mv ~/.cache/ubuntuone/log ~/.cache/ubuntuone/log_old && mkdir ~/.cache/ubuntuone/log
```

3) Run the following in a Terminal to open/create this file:
 ```
gedit  ~/.config/ubuntuone/syncdaemon.conf
```

    #Add the following 2 lines to this file and save:
```
    [__main__]
    log_level = DEBUG
```

4) Open Ubuntu One Applications->Internet->Ubuntu One

5) Let Ubuntu One run for a bit, copy some files into your Ubuntu One Folder. Then attach the following logs to a bug report (R-click the applet and select Report Problem):

~/.cache/ubuntuone/log/syncdaemon.log
~/.cache/ubuntuone/log/syncdaemon-exceptions.log

---

