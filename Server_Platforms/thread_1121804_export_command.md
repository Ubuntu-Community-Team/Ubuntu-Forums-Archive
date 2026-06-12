---
title: "export command"
date: 2009-04-10
forum: Server Platforms
---

### Post by snorkytheweasel on 2009-04-10
I just installed xubuntu server 8.10.

To use apt -or any other update/install tool, I have to configure the system to use my proxy server.

The commands I would normally use are
sudo export http_proxy="192.168.1.10:3128"
sudo export ftp_proxy="192.168.1.10:3128" 

However, the export command is not found.

I did a find on export:
sudo find / -name export

It returned /sys/class/gpio/export

That is not the export command. I know this because when I attempt
sudo /sys/class/gpio/export http_proxy="192.168.1.10:3128"

the system returns
sudo: /sys/class/gpio/export command not found

Yes, everything is in lower case.

[LIST=1]
[*]If export is not the correct command, then what is the correct command to tell the system how to find my proxy server?
[*]If export is not the correct command, where do I find it?[/LIST]

I have a server down, several hundred people unhappy, and a growing sense of urgency.

---

### Post by iponeverything on 2009-04-10
export is a bash internal (builtin) command.

do "sudo -i" and then run the export command.

---

### Post by sighk on 2009-04-10
you could also add the lines without sudo into /etc/profile

or add the lines into ~/.profile

this way you will next have to type it again

---

### Post by snorkytheweasel on 2009-04-10
That worked. Thank you.

---

### Post by snorkytheweasel on 2009-04-10
That worked (also). Thank you.

---

