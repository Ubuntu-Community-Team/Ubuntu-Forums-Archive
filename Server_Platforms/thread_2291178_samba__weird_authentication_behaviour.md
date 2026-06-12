---
title: "samba | weird authentication behaviour"
date: 2015-08-18
forum: Server Platforms
---

### Post by arjan3 on 2015-08-18
Hi

I'm encountering weird behaviour with ubuntu server 15 and samba shares.
I have multiple shares and those shares should have different users assigned to them.
This works, i can access the shares with the designated users, BUT... only 1 every session.. 

Lets say i have share A and share B
with user X (for share A) and Y (for share B)

If i reboot my windows machine and then connect to share A with user X.. that works.. 
When i connect to share B it prompts for the different user/pass of that share.. i enter it and it works.. but i can not return to share A. I get a prompt for the different user/pass. But when i enter the correct credentials, it will still deny me access..
Same goes if i repeat the process in the opposite order... i can only reconnect to the first share if i fully reboot my windows machine.

I have a windows 7 machine and i also tried on a vista machine, same issue..
Does anybody have any clue what is going on?

my smb.conf:

[databases]
    comment = ALLEEN databases plaatsen aub
    path = /home/mvmm/databases
    available = yes
    valid users = vanmunster
    browsable = yes
    public = yes
    writable = yes
    guest ok = no
    read only = no




[overige]
    comment = Alle overige bestanden
    path = /home/mvmm/overige
    valid users = vanmunster
    available = yes
    public = yes
    browsable = yes
    writable = yes
    guest ok = no
    read only = no


[facturatie]
    comment = Facturatie
    path = /home/mvmm/facturatie
    valid users = admini
    available = yes
    public = yes
    browsable = yes
    writable = yes
    guest ok = no
    read only = no

---

### Post by arjan3 on 2015-08-18
solved.. apparently windows can not connect to one server (even if the shares are different) with more than 1 user.. 

[http://superuser.com/questions/95872/sambawindows-allow-multiple-connections-by-different-users](http://superuser.com/questions/95872/sambawindows-allow-multiple-connections-by-different-users)

---

### Post by Morbius1 on 2015-08-18
Which method did you use. Connecting to the server a second time by ip address?

---

