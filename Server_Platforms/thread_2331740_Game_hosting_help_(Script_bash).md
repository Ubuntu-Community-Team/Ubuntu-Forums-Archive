---
title: "Game hosting help (Script bash)"
date: 2016-07-25
forum: Server Platforms
---

### Post by itseternity on 2016-07-25
Hey, so I'm trying to setup a Minecraft server. I've created a new folder called "mc" in my root directory and have both "spigot.jar" and "start.sh". My script.sh file looks like this
```
#!/bin/sh

java -Xms512M -Xmx1500M -XX:+UseConcMarkSweepGC -jar /root/mc/spigot.jar -o true
```

When I do: ```
chmod +x start.sh
```…and then ```
./start.sh
```…I receive  this error:```
-bash: ./start.sh: /bin/sh^M: bad interpreter: No such file or directory
```Could anyone help?

---

### Post by steeldriver on 2016-07-25
Looks like you have DOS-style line endings in your script - usually a sign of editing it in a Windows text editor

Either re-type it in a different editor, or run the script through dos2unix, or use sed / tr / whatever to remove the carriage returns

```

sed -i 's/\r$//' start.sh

```

---

### Post by itseternity on 2016-07-25
I'm currently using Notepad++ and select the language to shell. Where do I use the sed / tr / code?

---

### Post by steeldriver on 2016-07-25
As you're using notepad++, you should be able to do it right there - see [http://stackoverflow.com/a/8195860/4440445](http://stackoverflow.com/a/8195860/4440445)

If you want to use sed, you'd need to do it in a terminal after changing to the directory where the file lives

---

### Post by DuckHook on 2016-07-25
*Thread moved to **Server Platforms** as the more appropriate forum.*

---

