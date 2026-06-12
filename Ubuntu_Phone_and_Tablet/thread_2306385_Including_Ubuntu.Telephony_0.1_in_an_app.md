---
title: "Including Ubuntu.Telephony 0.1 in an app"
date: 2015-12-15
forum: Ubuntu Phone and Tablet
---

### Post by moma on 2015-12-15
Hello,
I want to create a small app that includes phone-call capabilities.
And I have already installed qtdeclarative5-ubuntu-telephony0.1 package.
 $ ```
sudo apt install qtdeclarative5-ubuntu-telephony0.1 qtdeclarative5-ubuntu-telephony-phonenumber0.1
```

And the code does 
import Ubuntu.Telephony 0.1

But the IDE says it cannot find the Ubuntu.Telephony module.
[COLOR="#FF0000"]Starting /usr/ubuntu-sdk-dev/bin/qmlscene...
file:///home/moma/QT/Test7/Test7/Main.qml:4 [COLOR="#FF0000"]module "Ubuntu.Telephony" is not installed[/COLOR]
[/COLOR]
```
import QtQuick 2.0
import Ubuntu.Components 1.1
import Ubuntu.Telephony 0.1

MainView {
    objectName: "mainView"
....
}
```

Should I add additional PATHs or libraries to the project?
Please educate me.

I cannot find documentation for the Ubuntu.Telephony module? 
I did find the phone-dialer app on the Launchpad.
See also: [http://askubuntu.com/questions/689349/how-to-perform-a-dial-call-using-ubuntu-api](http://askubuntu.com/questions/689349/how-to-perform-a-dial-call-using-ubuntu-api)

---

### Post by moma on 2015-12-15
Re-hi,
Ok, I got it to compile and run.

During the test, I"ve seen these messages.

[COLOR="#B22222"]Starting /usr/ubuntu-sdk-dev/bin/qmlscene...
This application failed to start because it could not find or load the Qt platform plugin "xcb".
Reinstalling the application may fix this problem.[/COLOR]
and
[COLOR="#B22222"]:-1: error: security:policy_groups_safe:Test7:debug: (REJECT) reserved policy group 'debug': not for production use.[/COLOR]
and
[COLOR="#B22222"]Starting /usr/bin/autopilot3-sandbox-run... E: Xephyr executable not found. Please install Xephyr.
/usr/bin/autopilot3-sandbox-run exited with code 1[/COLOR]

I am running:

$ lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

---

