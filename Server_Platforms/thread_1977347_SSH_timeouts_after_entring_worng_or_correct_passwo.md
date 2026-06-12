---
title: "SSH timeouts after entring worng or correct password"
date: 2012-05-10
forum: Server Platforms
---

### Post by gaurang171 on 2012-05-10
the issue is already posted in other section. but i think its belongs to here
 
[http://ubuntuforums.org/showthread.php?t=1975003](http://ubuntuforums.org/showthread.php?t=1975003)

My server was working fine and suddenly without doing any configuration changes ssh stopped working. 
I am able to login via KVM or direcly on server but ssh is not working in weird way

i have Ubuntu Lucid and when i try to connect via ssh it prompts for the password and after entering password it waits till connection time out and i get connection closed by server. 

The same thing happen when i try to do SSH on the same machine. so its not firewall issue to related DNS. i tried disabling use dns but no luck.

I also tried to update OS and now its 10.04.4 will all the latest  update.

---

### Post by gaurang171 on 2012-05-10
Bumped.

---

### Post by SeijiSensei on 2012-05-11
What do you see in the logs, particularly /var/log/auth.log?

---

### Post by gaurang171 on 2012-05-12
Now i am able to connect.


It was again surprise for me. 
SSH started working the same way it stopped. means. all of a sudden i  found that SSH is not working and after 3-4 days again all of a sudden i  found that its working. 
Now i dont know what did i do wrong? no settings changed. nothing done dusing these days and its started .

Thanks SeijiSensei, i am not able to provide auth.log as i have access to it but side is around 400KB so dont know what to post. if you need i can attach full log.

---

### Post by SeijiSensei on 2012-05-12
No, please don't post a whole log!

First, you can extract just the sshd related errors with 

```
sudo grep sshd /var/log/auth.log
```

However what I meant was to try to connect and look at the most recent entries in the log that pertain to that attempt.  Usually this is just a few lines.

However since it's working now, you hopefully won't need to do anything, but if so, you'll have a place to start.

One useful trick is to open a terminal and use "tail" to watch the log while you try to connect like this:

```
sudo tail -f /var/log/auth.log
```

That will echo the last dozen or so lines to the screen, then "follow" (-f) the log as more lines are written during your attempted connection.

---

