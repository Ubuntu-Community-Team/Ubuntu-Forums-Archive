---
title: "Archiving millions of files into a managable size"
date: 2019-02-08
forum: Server Platforms
---

### Post by LHammonds on 2019-02-08
I have a Windows server that processes a ton of HL7 messages and they get dumped into a single folder.  I did not realize this data was there and continuing to grow until Nagios told me the drive was starting to fill up.

It is impossible to use Windows File explorer to manage the folder due to there being millions of files in it.  It can take 30 minutes just for Explorer to show me the contents of the folder...even longer if I perform a single action in that folder (due to a refresh)

I got the idea to use Linux to mount the folder and use a "find" command to start breaking the files into sub-folders based on date to have a more manageable-sized folder but I get this error:

```

# find /mnt/windowsserver/* -type f -newermt 20180101 -not -newermt 20190101 -exec mv {} /mnt/windowsserver/2018/. \;
-su: /usr/bin/find: Argument list too long

```

My idea was to move all files in a specific year into a year folder.  Then move all files in January to an 01 folder under that.  Then I could run the archive commands against just those files rather than on the huge mess that it is now....each time.

Any ideas on how to handle a folder that has millions of little files in it?

Ideally, I'd like to compress the files into archives like 2018-01.zip, 2018-02.zip, etc. and then schedule a job to keep doing this maintenance on a regular basis.

Oh, and no, the file names are useless in this endeavor...just the date of the file.

**EDIT #1** - Rather than create a "neat" set of archives, I am going to try and create a single archive with all of those files.  If this works, I can just have the massive archive as the 1st and the ones in the future can be automated to be just a month's worth of files per archive.  Hopefully the following command will work.  If so, hopefully the "rm" command after that will work to remove the files.

```
tar -czf /tmp/hl7-all.tar.gz /mnt/windowsserver/.
```

**EDIT #2** - The tar command above worked and now I have a single compressed archive of all those files.  Now I'm just trying to delete everything and then move the archive into that folder.

**EDIT #3** - Because new files are being added all the time, I was not able to use "rm *" but luckily, Windows Explorer did allow me to "shift delete" the files that were archived...but it took a LONG time to finish and I had to babysit all the various this-or-that prompts that cropped up.  I have another huge directory and will try the find command again with xargs to see if that does better just for giggles now that the emergency is over.  I will post my results and close the thread after that.  Thanks TheFu.

LHammonds

---

### Post by TheFu on 2019-02-08
Use **xargs** for the exec part.
Use -delete for the clean up in the 'find' command.  It isn't have the shell limitation of 4K characters.

---

