---
title: "Problem"
date: 2009-04-24
forum: Wine
---

### Post by hamamshady on 2009-04-24
_I downloaded Wine ( I have ubuntu 8.10 ) entered terminal and wrote that :- _[html]wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - [/html]   then [html]sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list [/html]   then
[html]sudo apt-get  update[/html]then
 _entered add/remove checked on wine and it started downloading after that it started installing in the middle of installing the power went off when It came back I dont know if its working or not I went to add/remove and saw it was inchecked I started download ing again but it gave me this message _[html]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/html]_I don't know wut to do should I write that in the terminal ?? becuz when I do that nth happens and it gives me that _[html]dpkg: requested operation requires superuser privilege[/html]_I tried to install a new language ( arabic) it gave me the same dpkg was interrupted error what should I do _

---

### Post by =^,^= on 2009-04-24
> **hamamshady said:**
> _I downloaded Wine ( I have ubuntu 8.10 ) entered terminal and wrote that :- _[html]wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - [/html]   then [html]sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list [/html]   then
[html]sudo apt-get  update[/html]then
 _entered add/remove checked on wine and it started downloading after that it started installing in the middle of installing the power went off when It came back I dont know if its working or not I went to add/remove and saw it was inchecked I started download ing again but it gave me this message _[html]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/html]_I don't know wut to do should I write that in the terminal ?? becuz when I do that nth happens and it gives me that _[html]dpkg: requested operation requires superuser privilege[/html]_I tried to install a new language ( arabic) it gave me the same dpkg was interrupted error what should I do _

Copy and paste this into terminal;

sudo dpkg --configure -a

It will ask you for your password. Just type it and hit enter!

---

### Post by hamamshady on 2009-04-24
Wow thx for this help I was told that ubuntu has the fastest active forums I never thought it was to this extent !! thx very much for the fast reply I entered and wine is now installed I think, and now is downloading arabic package thx very much for this.. 
It seems like its was really easy its me and the terminal we aint that good with eachother I still have to learn alot about it thx again

---

### Post by =^,^= on 2009-04-24
> **hamamshady said:**
> Wow thx for this help I was told that ubuntu has the fastest active forums I never thought it was to this extent !! thx very much for the fast reply I entered and wine is now installed I think, and now is downloading arabic package thx very much for this.. 
It seems like its was really easy its me and the terminal we aint that good with eachother I still have to learn alot about it thx again

No problem! ^,^

Dont be scared of the terminal, i was when i started using ubuntu, but it makes fixing and doing things so easy!

---

