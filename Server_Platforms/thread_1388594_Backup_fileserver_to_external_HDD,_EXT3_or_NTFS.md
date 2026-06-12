---
title: "Backup fileserver to external HDD, EXT3 or NTFS?"
date: 2010-01-23
forum: Server Platforms
---

### Post by ajk32 on 2010-01-23
Hi everybody,

After a near miss with my 1.5TB, RAID5 file server, I have decided that I need to backup my data to an external hardrive periodically.

I have been looking at rsync but the question I have is: Do I format the external hard drive in EXT3 (the same as my fileserver) or NTFS?

All my main machines are Windoze, but the file server is Ubuntu with a samba share. If my server ever went belly up, I would like to be able to access my data from the external hard drive. I guess if it's in EXT3 then windows would be clueless... I would either need to fix the server pronto or access it with a live CD or something.

What would I lose if I used NTFS instead of EXT3? I think I would lose permissions and possibly ownerhsip information - are there any other issues??

Many thanks!
Andrew

---

### Post by Revolutionary101 on 2010-01-23
I would suggest that you use NTFS so that your Windows machines would be able to read the HDD if the server fails.

---

### Post by NIT006.5 on 2010-01-23
Provided you're only copying files that "originated" on Windows (and were then backed up to the server), I'd say go with NTFS. 

I have had issues before though, when backing up certain applications running on my servers, because NTFS didn't seem to like some of the file names which resulted in the files just not being transferred. I was using a NAS drive though, but I don't think that was to blame.

---

### Post by ajk32 on 2010-01-23
Yeah - these are mostly only files that "originated" on windows. It's only the samba share as well as I'm not too bothered backing up the server OS (it's on it's own HDD and not part of the raid).

I'll go with NTFS for now and see if I get any problems. I can always reformat in EXT3 and recopy the data if anything gets screwy.

Thanks for the help!
Andrew

---

