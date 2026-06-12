---
title: "How to &gt;&gt; log a bash script?"
date: 2016-01-07
forum: Server Platforms
---

### Post by Higgins909 on 2016-01-07
Basically I have a script, that runs a program, while logging it, but it don't seem to work though the script.

```

#!/bin/bash
# Test is the process is running using the if statement.
if ! ps -ef | grep [a]rma3server ;
then
      echo "program arma3server is not running - run the program"
      cd /home/admin-ben/Steam/steamapps/common/Arma3Server
      screen -dmS arma-auto ./arma3server >>/home/admin-ben/gameserver/logs/log.rpt 2>&1 -mod=@Exile\;@mas\;@NATO_Rus_Vehicle -servermod=@ExileServer -config=@ExileServer/config.cfg -port=2302 -profiles=SC -cfg=@ExileServer/basic.cfg -name=SC -autoinit -filePatching
else
      echo "program arma3server is running - nothing to do"
      exit
fi
```

I used to manually make a screen and cd, then sudo ./arma3server >>/and so on.
It seems to be making the log.rpt but is not writing anything to it.

How come the logging has stopped working?
What is a way to fix or a alternative?

Thanks,
Higgins909

---

