---
title: "Backups to external hardrive thru samba"
date: 2008-11-01
forum: Server Platforms
---

### Post by rgotten on 2008-11-01
I have an ubuntu server, the box has e-sata conector for an external hard drive. My client computers are all windows, i would like to have the data of information that the windows use and store on the server and is being seen with samba(word documents, pdf , etc) to be able to backup on an external hard dirve in a way that if the server has a crash, at least i can take the external hardrive and pluget into any of the windows computer and see and use the data.is this possible...or i have to get a network ready hard dirve..in this case i am assuming that the bakup process will be much slower

Thanks

---

### Post by mitchroberts on 2008-11-20
> **rgotten said:**
> I have an ubuntu server, the box has e-sata conector for an external hard drive. My client computers are all windows, i would like to have the data of information that the windows use and store on the server and is being seen with samba(word documents, pdf , etc) to be able to backup on an external hard dirve in a way that if the server has a crash, at least i can take the external hardrive and pluget into any of the windows computer and see and use the data.is this possible...or i have to get a network ready hard dirve..in this case i am assuming that the bakup process will be much slower

Thanks

yes the back up will be some slower but back ups are already slow so format external hardrive in **ntfs** **linux can read ntfs format **then set back up to that drive external hardrive should mount when pluged in to windows and linux windows can only read a linux drive when you use samba.

xp use samba 
vista is different it uses something different You need to configure Samba to accept NTLMV login encryption

---

### Post by rgotten on 2009-04-05
> **mitchroberts said:**
> yes the back up will be some slower but back ups are already slow so format external hardrive in **ntfs** **linux can read ntfs format **then set back up to that drive external hardrive should mount when pluged in to windows and linux windows can only read a linux drive when you use samba.

xp use samba 
vista is different it uses something different You need to configure Samba to accept NTLMV login encryption
i would like to get some help if i should have the hard drive connected to the server or as a network attach storage...like i mention before in order to be able to do daily backups into it and also if the server crashes to be able to connect the hrd drive to one of the windows computers and access the files...which option is recomended and were should i start???

---

