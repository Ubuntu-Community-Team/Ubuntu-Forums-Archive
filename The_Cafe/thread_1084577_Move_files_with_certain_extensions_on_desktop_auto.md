---
title: "Move files with certain extensions on desktop automatically to folder after download"
date: 2009-03-02
forum: The Cafe
---

### Post by billgoldberg on 2009-03-02
Is it possible (nautilus script?) to automatically move a file from your desktop to a specified folder after it's done downloading?

What I'm asking here, couldn't someone with more scripting skills than me try to make this and share?

---

### Post by Ozor Mox on 2009-03-02
Are you using Firefox? You can change the location of downloaded files or set it to ask you each time.

---

### Post by notwen on 2009-03-02
Maybe set up a cron job to run a shellscript every X minutes moving *.extension to /target/folder ?  However if you're specifying for a script that monitors downloads and runs after each download finishes, then that is a bit beyond my simple thinking.  =]

---

### Post by billgoldberg on 2009-03-02
> **Ozor Mox said:**
> Are you using Firefox? You can change the location of downloaded files or set it to ask you each time.

That's not what I'm looking for.

---

### Post by billgoldberg on 2009-03-02
> **notwen said:**
> Maybe set up a cron job to run a shellscript every X minutes moving *.extension to /target/folder ?  However if you're specifying for a script that monitors downloads and runs after each download finishes, then that is a bit beyond my simple thinking.  =]

That would be good, but I don't know how I would only make completely downloaded files move and not those that are still downloading.

---

### Post by Skripka on 2009-03-02
> **billgoldberg said:**
> That would be good, but I don't know how I would only make completely downloaded files move and not those that are still downloading.

That is the sticky problem....

---

### Post by Ozor Mox on 2009-03-02
Do files that are downloading have the extension .part, or is that only a Firefox thing?

Otherwise I don't know. It would have to somehow compare the local file size with the remote file size I suppose...

---

### Post by init1 on 2009-03-02
> **billgoldberg said:**
> That would be good, but I don't know how I would only make completely downloaded files move and not those that are still downloading.
Would you be using Firefox? If so, the fact that incomplete files have another file with a .part extension would be useful. 
The pseudocode might be something like this:
```

for i=*.ext in downloadfolder
{
if i.part does not exist then copy to Desktop

}

```
I know that its possible to do in bash, but I'm not sure exactly how.

---

### Post by notwen on 2009-03-02
> **billgoldberg said:**
> That would be good, but I don't know how I would only make completely downloaded files move and not those that are still downloading.

Very true, got me stumped.  This is probably above basic shellscripting but if you could somehow copy the **original** to /target/folder/**copiedfile** and once **copiedfile** is the same size as **original**, then delete **original** leaving **copiedfile** in the desired folder.  I don't think shellscripting could do this alone, so an additional language may have to be used, but it seems feasible.

This is all under the assumption that all downloads would be constantly downloading(file size growing) and not paused, etc.  It may also cause temporary size limitations depending on the size of your downloads and the size of your HDDs.

---

### Post by billgoldberg on 2009-03-02
The .part files a firefox only thing (as far as I know).

It would have to be, basically all files downloaded to the desktop.

Files downloaded using transmission, firefox, thunderbird, nautilus, ...

---

### Post by Ozor Mox on 2009-03-02
notwen's idea seems fairly sensible. Perhaps take a snapshot of the size every minute and compare it with the previous snapshot. If the size has not changed in a minute, you can probably assume the download is complete and copy it. It may have failed, in which case you'll end up with a broken file copied. I don't know how much of a problem that would be.

---

### Post by Hells_Dark on 2009-03-02
This is what you want :

[http://doc.ubuntu-fr.org/dossier_magique](http://doc.ubuntu-fr.org/dossier_magique)

It's in french.. but not the commands ;)

---

### Post by billgoldberg on 2009-03-02
> **Hells_Dark said:**
> This is what you want :

[http://doc.ubuntu-fr.org/dossier_magique](http://doc.ubuntu-fr.org/dossier_magique)

It's in french.. but not the commands ;)

Thanks.

It seems that what I'm looking for is called a "magic folder".

I'll try to get this up and running.

I hope that download problem is addressed in the script, I assume it will be.

---

### Post by billgoldberg on 2009-03-02
Well that french script didn't work and another one I found online also didn't work.

I'll guess I'll make one myself this weekend.

--

I'll just create a hotkey for the script and use it after downloading is finished, problem solved.

---

### Post by VCoolio on 2009-03-02
Nice idea. Plz inform us when you managed to write a working script.
Look what I found around these fora: fsniper, lets you monitor specified directories and execute scripts on any new files that are created in them.
[http://www.linux.com/feature/150200](http://www.linux.com/feature/150200) 
Maybe this helps.

---

