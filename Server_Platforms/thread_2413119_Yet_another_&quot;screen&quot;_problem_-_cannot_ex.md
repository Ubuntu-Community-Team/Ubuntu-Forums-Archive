---
title: "Yet another &quot;screen&quot; problem - cannot execute command on screen multiuser"
date: 2019-02-21
forum: Server Platforms
---

### Post by elmarciano18 on 2019-02-21
Hello!

 I have wasted hours on this now, but it won't work, and after searching the web and finding like hundreds of similar, but no matching problems, I have to try it here.

I start a screen session with a normal user 'foobar':
```
/usr/bin/screen -dmS server /usr/lib/jvm/java-8-openjdk-amd64/bin/java -jar server.jar -Xms2000M -Xmx6000M /home/foobar/server
```

Then I try to connect to this session from root. The multiuser part is actually working.
For example I can connect  into the screen session using ```
screen -Rd foobar/server
``` with no  problem. I can also type commands there.

But I need to send commands from a script there, and as soon as I insert an "-X" into the screen command like this:
```
screen -S foobar/server -X stuff "command"
```

all I get is:
```
No screen session found.
```


Why?

---

