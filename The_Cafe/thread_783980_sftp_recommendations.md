---
title: "sftp recommendations"
date: 2008-05-06
forum: The Cafe
---

### Post by oldskool on 2008-05-06
I'm new here and to ubuntu so hi and i hope this is posted in the right place 

I made the switch at work initially then found it so good i installed it at home too. After about 2 weeks now i'm 95% there in saying goodbye to windows. 


1 issue thats bugging me is sftp under ubuntu - i understand Nautilus 2.22.2 (the one i have) has issues with speed. My work requires me to sftp into servers, up/download files, edit files etc. 

I'm using Nautilus 2.22.2 with bookmarks and opening files using gEdit and saving them direct to the server. That bit seems to work well enough so far, v.quick, simple and fast - getting the job done without much effort. 

Transferring files is terrible though. 30-40KB/Sec. We have a 100Mbit connection here; achieving 20Mbit in most cases. 


So is there anything out there where i can browse remote sftp folders as easily, 1 touch edit files as easily and transfer files really quickly all in one program. 

I used to use WinSCP and SSH.COM's tool which worked very well. I think i tried gftp and that wasn't that quick and i couldnt edit files directly on the server. 


Thanks,

---

### Post by freduardo on 2008-05-06
I'm not sure it's exactly what you're looking for, but gftp will connect through sftp.

```
sudo apt-get install gftp
```

and don't forget to select ssh2 as the protocol (default is ftp)

EDIT: You can edit files in gftp, when you've specified an editor in the options, e.g. gedit.

---

### Post by Joeb454 on 2008-05-06
I just use sftp from the command line.

Just thought I'd mention that it existed - though gftp is probably a better choice for most people :)

---

### Post by oldskool on 2008-05-07
found 2 programs i like 

krusader for sftp and geany for editing from krusader 


1 problem - sometimes when i save files in geany and press "upload" it stalls leaving a *.php.part file on the server and looses some of the code. 


It happened in gedit too but in that the program just became unresponsive requiring a forced quit. 


Any ideas on this stalling?

---

