---
title: "Removing gnome after apt-get install gnome"
date: 2011-10-20
forum: Server Platforms
---

### Post by jooiiee on 2011-10-20
I have used ubuntu server for a while not and am currently using ubuntu server 32bit 11.04 and wanted to experiment with gnome so i installed gnome with the comand 
[I]sudo apt-get install gnome
[/I]and that installed about 350 packages. 
since gnome autostarted after the installation i removed it with 
[I]sudo apt-get remove gnome

[/I]That removed 2 packages. 

After that i ran 
[I]sudo apt-get remove gnome*

[/I]and that removed about 200 packages. 
Now the system still boots up in tty7 and starts lots of programs that i dont need. 

And to the question: Can i remove the other 150 packages in a simple way or should i do a full reinstall? 

Thx in advance for the help ;)

---

