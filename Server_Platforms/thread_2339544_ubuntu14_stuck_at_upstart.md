---
title: "ubuntu14 stuck at upstart"
date: 2016-10-10
forum: Server Platforms
---

### Post by sacy on 2016-10-10
Hi 

i got a problem with 2 of my Server. My local console will not load to login screen. It got stuck on Upstart. But i can SSH to the server.  Anyone has encounter this before?
Server hardware: 
Dell R730

[IMG]http://forumspp.vr-zone.net/500/medium/stuck.PNG[/IMG]

---

### Post by Vegan on 2016-10-12
logon with SSH
then run

[COLOR="#FF0000"]sudo apt update
sudo apt full-upgrade[/COLOR]

---

