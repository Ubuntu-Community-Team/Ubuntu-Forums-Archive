---
title: "How do I leave a command running after quitting SSH"
date: 2006-02-16
forum: Server Platforms
---

### Post by endy on 2006-02-16
I was wondering what the correct way to log into a server via SSH, run a command and make sure it will complete because I then need to quit the connection whilst it's still running.

Is there a proper method to doing this?

--endy

---

### Post by siefkencp on 2006-02-16
Check out how to run this as a background process here: [http://linux.about.com/od/glossary/l/bldef_bgprocess.htm](http://linux.about.com/od/glossary/l/bldef_bgprocess.htm)

I believe that should set you up.

---

### Post by heimo on 2006-02-16
For example, by running it prefixed by *nohup, *and backgrounding it using & or ctrl+z. Also you may be interested to learn using [screen]("http://www.linuxjournal.com/article/6340").

---

### Post by endy on 2006-02-16
Thanks for the ideas, I can't believe I forgot about & and nohup :)

Well as this is going to be part of a script I'm just going to see how backgrounding it works, I guess as long as nothing kills it should complete. Thanks again.

---

