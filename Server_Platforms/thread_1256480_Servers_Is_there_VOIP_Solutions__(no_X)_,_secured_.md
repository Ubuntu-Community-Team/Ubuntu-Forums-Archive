---
title: "Servers: Is there VOIP Solutions  (no X) , secured alternative to Skype"
date: 2009-09-02
forum: Server Platforms
---

### Post by frenchn00b on 2009-09-02
Hello,
For machines without keyboard and monitor, is there no x skype solutions for linux?  Would be great also with command line or lirc

I would like that people can voip call me on my box, without any X.

---

### Post by smeerbartje on 2009-09-03
Would be great! Anyone some suggestions?

---

### Post by frenchn00b on 2009-10-18
> **smeerbartje said:**
> Would be great! Anyone some suggestions?

still nothing in that field; but importnat is to say that skype No X has an alternative, now:


[http://www.pjsip.org/pjsua.htm](http://www.pjsip.org/pjsua.htm)

it can do voip command line; no x

---

### Post by frenchn00b on 2010-01-29
nothing solutions but there is skype no X

```

#!/bin/sh

if  [ "`ps aux | grep skype | grep pipelogin`" != "" ]  ; then
        echo "Skype is there"
        beep
else   
        echo "Skype not there"
        killall -e skype Xvfb
        Xvfb :6 &
        DISPLAY=:6 ; export DISPLAY ; cat $HOME/.skyperc | skype --pipelogin
        killall -e skype
        sleep 1s
        # beep
fi


```

---

