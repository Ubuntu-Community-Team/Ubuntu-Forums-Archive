---
title: "Server - unable to use ppa"
date: 2010-04-22
forum: Server Platforms
---

### Post by quimkaos on 2010-04-22
I'm trying to add an repository using the "add-apt-repository ppa:name"  but i'm unable to do so. I'm using sudo!

first i got an error that i needed python-software-properties
so i made [FONT=monospace]"[/FONT]sudo apt-get install python-software-properties"

now i get a command not found error when i use [FONT=monospace]"[/FONT]sudo add-apt-repository ppa:<repository-name>"

How can i add a ppa repository in ubuntu 9.10 server?

---

### Post by wojox on 2010-04-24
Do it the old fashion way and edit the /etc/apt/sources.list

---

### Post by quimkaos on 2010-04-26
done! ty

---

