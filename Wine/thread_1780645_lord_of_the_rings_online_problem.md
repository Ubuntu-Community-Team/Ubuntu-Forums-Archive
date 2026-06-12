---
title: "lord of the rings online problem"
date: 2011-06-12
forum: Wine
---

### Post by cheesedog31 on 2011-06-12
ok so i downloaded the lord of the rings online from their website, and the install worked perfectly with wine, i also downloaded pylotro by adding the ppa on that guys website that runs it. and i use pylotro to go on the lord of the rings online and it starts to load up then says "connection failed: you do not have the current version of the client installed." but i dont understand how thats possible because i just got it off the website.. what do i do?

this is what i get when i try to patch on pylotro

rundll32.exe lotrpatch.dll,Patch patch.lotro.com:80 --language English --productcode LOTRO --filesonly
wine: Call from 0x7b835cc2 to unimplemented function msvcr71.dll._set_purecall_handler, aborting

fixme:faultrep:ReportFault 0x32f658 0x0 stub

wine: Call from 0x7b835cc2 to unimplemented function msvcr71.dll._set_purecall_handler, aborting

fixme:faultrep:ReportFault 0x32f658 0x0 stub

wine: Call from 0x7b835cc2 to unimplemented function msvcr71.dll._set_purecall_handler, aborting

fixme:faultrep:ReportFault 0x32f658 0x0 stub

*** Finished ***

---

### Post by cheesedog31 on 2011-06-12
bump.

---

### Post by ajackson on 2011-06-13
You need to either stick a copy of msvcr71.dll in the game directory or use winetricks to install vcrun2003.

---

### Post by The Contractor on 2011-06-13
To be on the safer side I would use Winetricks to install vcrun.

---

### Post by cheesedog31 on 2011-06-13
> **ajackson said:**
> You need to either stick a copy of msvcr71.dll in the game directory or use winetricks to install vcrun2003.

how exactly do i do that? i gotta admit i have linux mint 11 katya, not ubuntu :p its basically the same, but when i click on winetricks it pops up a gui asking if i want to install, for instance, an app, game, benchmark (what is that) and a few other options. how do i use it to install vcrun2003?

i picked install a wine prefix, and clicked on vcrun2003, and while installing it disconnected me from the internet and gave me this error message...

sha1sum mismatch! Rename /home/evan/.cache/winetricks/vcrun2003/BZEditW32_1.6.5_Installer.exe and try again.

ok so i just ran "winetricks vcrun2003" in the terminal and it downloaded some stuff. opened up an installer.. i just clicked next and it installed.. now to test lotro.. will report back if there is any problems, if not thank you

---

