---
title: "Help Needed On Ubuntu Server"
date: 2006-06-09
forum: Server Platforms
---

### Post by zimele on 2006-06-09
HI all

Number one Newbie i need help on "Commenting out" what does this mean,,,
i'm tryna build up an isp server and when installing mysql and need to find a listening port  **"If you do not see this line, edit /etc/mysql/my.cnf and comment out skip-networking:"** now all i need to understand is how to do this comment out..

I've been on the net and it seems like a basic process


Thanks in advance

---

### Post by tribaal on 2006-06-09
Hi there

Well it's indeed a pretty basic proccess, we'll go through it together:

1. First of all, open up a terminal. If you use GNOME, it's "Applications" -> "Accessories" -> "Terminal".

2. Type in the following at the prompt: ```
sudo nano /etc/mysql/my.conf
```
What this command does in details: "sudo" makes it that the following part is run with super-user ("root") privileges. It will ask you for your password.
nano is a simple command-line text editor. Most of it is pretty intuitive.
Then "/etc/mysql/my.conf" is the path to the file you want to open. It's a system file, that's why we used sudo, otherwise it would have been read-only.

3. Find the line that says "skip-networking". The "search" shortcut is Ctrl-w.

4. To comment it out, place a hash ("#") sign in front of it. # is the most common comment sign in Linux. If it's the first char on the line, anything after it will be considered a comment, and thus not interpreted by programs.

5. Once you're done, use ctrl-o (to save), and ctrl-x (to close nano).

You're done!

Hope this helped...

- trib'

---

### Post by Iowan on 2006-06-09
[QUOTE=tribaal] # is the most common comment sign in Linux. If it's the first char on the line, anything after it will be considered a comment, and thus not interpreted by programs.
[/QUOTE]
The semicolon is frequently used as another "comment-er".  Since the "system comments" are usually hashes, sometimes it's handy to use the semicolon to tell the difference. Of course, you could just use double hashes...

---

