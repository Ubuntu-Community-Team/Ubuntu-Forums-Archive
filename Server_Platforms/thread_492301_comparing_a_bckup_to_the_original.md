---
title: "comparing a bckup to the original"
date: 2007-07-04
forum: Server Platforms
---

### Post by neill on 2007-07-04
hi

i back up my desktop /home to a LAN server using rdiff-backup

periodically a little voice in my head says - "how do you know the backups are good ??"

so what i want to do is compare /home with the backup of /home on the server

i can ssh into that server in the usual way or use a VNC desktop if needs be

all i want to do is compare file listings and date/time attributes

is there a util that does this across the LAN or how else might i do it ??

thanks

/neill

---

### Post by MJN on 2007-07-05
I don't use rdiff-backup but I do use rsync which I believe rdiff-backup may be based on?

Assuming so, I do know that rsync automatically compares the hashes of source and (temporary) destination file at the end of a sync/backup and only then does it overwrite the destination if they match so you need not be concerned as far as that side of things is concerned.

However, if you want to check the validity of the backup at a later date you could just use rsync to identify any differences in the files - basically perform a full backup as a dry-run so nothing is changed but you are notified of any differences. At the most basic (default) level it would compare filenames and attributes however you can also make it check full file hashes to satisfy the more paranoid amongst us!

This would be extremely fast, not least given you've got an instance of rsync running at either end of the link with only the filelists passing between the two.

Remember your wish is already a fundamental job of rsync/rdiff-backup i.e. to identify changes in files (on source and destination) and subsequently sync the two where they differ. In your case you just want to do the former hence the dry-run attribute.

Mathew

---

### Post by Mr. C. on 2007-07-05
> **neill said:**
> periodically a little voice in my head says - "how do you know the backups are good ??"

That little voice you are hearing is the voice of wisdom.

A backup is *only* as good as your ability to *reliably* restore from it.  Too much effort is spent on the backup side, and never on the restore side.

Test periodic restores, full and partial.  Rely on the tools to make the backup / restore faster and more efficient, but it is not wise to place all trust in one form of automated verification; verify data periodically using an alternate strategy, so that errors in the first strategy are more likely to be discovered.

MrC

---

### Post by MJN on 2007-07-06
What Mr C said is spot on, but do also realise that a restore is usually insufficient at verifying that the data is correct. For example, you might have 5,000 photos backed up and whilst a restore may apparently have worked there's no guarantee that each file is as per the original. Hence some form of verification that the backup is the same as the original is worthwhile (and the point about using a different mechanism is a good one but I can only advise on the tools I know).

As an example to what I discussed earlier the following would compare the files on source and destination and output (not change) any files that differed (and detail how - see the -i description in the man page for what's displayed):
[B]
rsync -aivn --delete /source/files/ <username>@<remote IP>:/path/to/backup/files/[/B]

This will compare the files on filesize and modification time. To cover all bases, and use checksums instead, then add the -c flag (it'll take longer though). The --delete flag is important to highlight any files that exist at the destination but not the source.

One of the key benefits of this rsync approach is the fact that as your source and destination is over a network you don't want the files to traverse that link hence you need something to operate at each end and then compare the results.

I run rsync over the Internet and can compare my 100GB backups bit-for-bit in a matter of minutes. To echo what Mr C says this isn't the end though, you also need to know you can successfully restore that backup and the only way is to do it (on a representative test system preferably!).

Mathew

---

### Post by neill on 2007-07-06
thanks very much guys

the 'voice of wisdom' you note actually comes from experience - not mine thankfully - but a friend who lost >10gb of music and photos when he found out his meticulously performed backups were duff !!

i'll try the rsync commands as that seems *exactly *what i'm after

i had tried doing ls commands on both trees and running diff on the output - but this failed of course because of the incremental nature of rdiff/rsync :rolleyes:

cheers !

/neill

---

### Post by MJN on 2007-07-06
Ah... As mentioned I'm not familiar with rdiff but I'm guessing, from the name at least, that perhaps it's just storing differences at the destination and hence my rsync method will likely fail in the same way as your simple ls trick. Rsync stores full copies at the destination hence the aforementioned comparison method works fine for me.
 
Mathew

---

### Post by neill on 2007-07-06
rsync is indeed very similar to rdiff-backup and you're right - it fails !!

by that i mean it outputs
<f+++++++
for every file

meaning, i think, that it would copy it on a real run - this despite the file being there and the checksums matching when i do them manually

this must be, i guess, because the mechanism by which rdiff and rsync do their incremental thang is sufficiently different

so what i need to do now is find the equivalent rdiff command to your rsync command

/neill

---

### Post by neill on 2007-07-06
you know what they say ..........

RTFM

.... there's a --compare flag in rdiff-backup which looks like it'll do what i need :D

sorry for wasting your time and thanks for the help

/neill

:oops:

---

### Post by MJN on 2007-07-06
Not a problem - I'm sure it'll be useful for someone else in the same boat!
 
Mathew

---

