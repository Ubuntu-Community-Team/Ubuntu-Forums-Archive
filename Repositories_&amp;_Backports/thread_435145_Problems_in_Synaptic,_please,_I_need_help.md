---
title: "Problems in Synaptic, please, I need help"
date: 2007-05-06
forum: Repositories &amp; Backports
---

### Post by franz1789 on 2007-05-06
I'm an italian user of Ubuntu, and I'm looking for help here, because it seems that no one can help in italian forum. After I added the 3v1n0 repo, which contains loads of updated software. I made an update, and i.e. aMsn and aMule now works better. But soon I began to have problems. First of all, I'm not able anymore to install compiz.manager. It was removed (I don't know why) during the update, and now the new version has problem of dependences. I search the old, but it seems there is not anymore. And when I try to make an update of all packages, to make compiz-manager return in the software, I've got this error:
```
E: Dynamic MMap ran out of room
E: Errore nell'analisi di libglib2.0-doc (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
E: Impossibile analizzare o aprire l'elenco dei pacchetti o il file di stato.
E: _cache->open() failed, please report.
```

It seems there are problem with the reading of the repository list. And I don't know how I could reset the synaptic, because now I can't even open it... Please, please, help me...

---

### Post by paparucino on 2007-05-07
> **franz1789 said:**
> 
It seems there are problem with the reading of the repository list. And I don't know how I could reset the synaptic, because now I can't even open it... Please, please, help me...
I don't know if someone already told you:

```

Remove the two .bin files from /var/cache/apt then rerun apt-get update

Cancella i due file .bin in /var/cache/apt poi rilancia apt-get update e incrocia le dita. :lolflag: 

```





UAResolved

---

