---
title: "Unable to Load Page/Cannot connect to destination"
date: 2010-04-02
forum: Ubuntu One (CLOSED)
---

### Post by platz on 2010-04-02
I haven't been able to add any computers to my account. After launching Ubuntu One from the preferences, I am asked in my browser (Epiphany 2.29.92) to confirm computer access. The following is the screen I'm given after clicking "add this computer"

[IMG]http://soundcircle.org/Screenshot.png[/IMG]

I haven't found this exact issue mentioned in the threads here yet. I apologize if I've overlooked something.

OS: 10.04

---

### Post by joshuahoover on 2010-04-05
> **platz said:**
> I haven't been able to add any computers to my account. After launching Ubuntu One from the preferences, I am asked in my browser (Epiphany 2.29.92) to confirm computer access. The following is the screen I'm given after clicking "add this computer"

[IMG]http://soundcircle.org/Screenshot.png[/IMG]

I haven't found this exact issue mentioned in the threads here yet. I apologize if I've overlooked something.

OS: 10.04

This error normally occurs if there your web browser is setup to use a proxy server for 127.0.0.1/localhost. See the following FAQ for more on this: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/633](https://answers.edge.launchpad.net/ubuntuone-client/+faq/633)

This problem can also occur if there is a long period of time between when you see the "Add your computer" web page and when you actually submit the form. In this case, the local web server may time out (normally after 10 minutes).

If neither of the points above seems to help, please file a bug ([https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)) and be sure to attach the following log files:

~/.cache/ubuntuone/log/oauth-login.log
~/.cache/ubuntuone/log/u1-prefs.log

Thank you,

Joshua

---

