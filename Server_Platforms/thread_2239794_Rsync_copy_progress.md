---
title: "Rsync copy progress"
date: 2014-08-15
forum: Server Platforms
---

### Post by brent1975 on 2014-08-15
Hello - We have a couple servers that are being decommissioned. We have the new servers in place and working flawless. I am using Rsync to transfer data between the servers. 

  The command below seems to be copying the files over nicely. However, Is there an option that gives a status or amount of time left on the copy? 

sudo rsync -av -e ssh /home/shares/data/ brent@10.123.153.129: /home/shares/data


Thanks in advance.

---

### Post by papibe on 2014-08-15
Hi brent1975.

Try the '--progress' option:
```
rsync -av --progress /home/shares/data/ brent@10.123.153.129: /home/shares/data
```
Let us know if that helps.
Regards.

EDIT: this works as progress 'per file'.

---

### Post by brent1975 on 2014-08-15
That is nice. However, I am looking for something more on the lines of total copy time remaining as a hole. Looks like there is an option for this but in beta stages or at least that is what is said in some of the forums. This will do just fine. Thank you!!!

---

### Post by papibe on 2014-08-15
Are you syncing files, and directories? or are you using it to just transfer the content to an empty server?

In syncing mode, using the rsync delta algorithm, rynsc stars transferring while is scanning the directory tree so it does not know how much is going to transfer until the very the end.

An idea: if it is a transfer (nothing on the destination), and displaying the progress is very important to you, you may tar the content first, and then rsync the tar file with the progress option.

Just some thoughts.
Regards.

---

### Post by brent1975 on 2014-08-15
I am just copying data to a clean server. files and folders. I will have to remember next time to tar the folders. It would be a good idea to back up some* of the folders mainly user home folders to another server. Is there a script that I can use that I set specific folders to copy over daily incrementally if there are changes or new files?  In search*** 


Thanks,

---

### Post by nerdtron on 2014-08-17
> **brent1975 said:**
> I am just copying data to a clean server. files and folders. I will have to remember next time to tar the folders. It would be a good idea to back up some* of the folders mainly user home folders to another server. Is there a script that I can use that I set specific folders to copy over daily incrementally if there are changes or new files?  In search*** 


Thanks,

rsync by default will not transfer all files but rather update the files on the destination only if the source files are changed or new files are created.

---

