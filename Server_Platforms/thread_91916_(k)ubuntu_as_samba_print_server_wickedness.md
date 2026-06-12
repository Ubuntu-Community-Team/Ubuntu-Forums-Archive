---
title: "(k)ubuntu as samba print server wickedness"
date: 2005-11-18
forum: Server Platforms
---

### Post by QmQ on 2005-11-18
Hello everyone, this be my first post ;)

I know that's there are LOTS of ubuntu + samba + printer topics, but this one will be different I hope (I've read the majority of the existing ones, and no else seemed to be having similar problems).

Mine is a bit odd I'm afraid. I've spent ages trying to setup my samba server in such a way to enable a win2k computer from my LAN to use my printer. And I have actually succeded! :)

But nothing lasts forever I'm afraid, and it turned out that when I add this printer on the win2k computer everything works like a charm, everyone can print and be happy and all. But when I reboot things get messed up. Samba and CUPS working fine, printer is available via samba (I can see it from win2k) but I can't print until I remove the printer and install it again (on the win2k computer that is). I have not the slightest idea why this be...

Any ideas? What may be wrong?


And, quite apart from this, there is more... ;)
The printer status is always: ACCES DENIDED, but I actually can print (untill I reboot kubuntu that is). I somehow don't find this normal - maybe this is the problem?

Could someone write me a short n' simple list of required thing to do to make a working samba printer share? (don't write how, I'll manage that, I just need to know what I may be missing).


This is my smb.conf, if it's relevant:

```

# global
workgroup = MORDOR
netbios name = kuba(kubuntu)
encrypt passwords = yes

load printers = yes
printing = cups
printcap name = cups

[printers]
comment = HP LaserJet 1020
browseable = yes
path = /tmp
printable = yes
public = yes
writable = no
#guest ok = yes
create mode = 0700

```

(just don't ask about the workgroup :rolleyes: )

There's no [$printer] section cause I've installed the original printer drivers on the win2k computer - I hope I can do that this way..?


The printer is a HP LaserJet 1020 installed with the patched foo driver working VERY WELL locally. CUPS seems to be working fine too, though I'm not that sure - I find it evil... :evil: 


That's it. Thanks for help :)

---

