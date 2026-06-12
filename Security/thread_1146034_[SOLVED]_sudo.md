---
title: "[SOLVED] sudo"
date: 2009-05-02
forum: Security
---

### Post by pek007 on 2009-05-02
hi,

i am new in linux. i was trying to make skype work (problems with mic) and i did it by one how to. now skype works ok, but it seems i did something wrong, since i take off all my ability to use sudo or any install programs or synaptic manager... i am trying to make it back to work, but i cant. now i looking here if someone of you can tell me, how do i make it work? in terminal it says:

ziga@ziga-laptop:~$ sudo apt-get install screenlets
[sudo] password for ziga: 
ziga is not in the sudoers file.  This incident will be reported.
ziga@ziga-laptop:~$ 

for visudo:

ziga@ziga-laptop:~$ visudo
visudo: /etc/sudoers: Permission denied
ziga@ziga-laptop:~$ sudo visudo
[sudo] password for ziga: 
ziga is not in the sudoers file.  This incident will be reported.
ziga@ziga-laptop:~$ 


i cant even change my cpu freq since it was required password... 

what can i do?

ty and bye
ziga

---

### Post by aysiu on 2009-05-02
This should help:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by pek007 on 2009-05-02
ty m8. i managed to fix it.

bye

---

