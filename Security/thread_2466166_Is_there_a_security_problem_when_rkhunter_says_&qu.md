---
title: "Is there a security problem when rkhunter says &quot;the file properties have changed&quot;?"
date: 2021-08-21
forum: Security
---

### Post by johnjones1234 on 2021-08-21
I recently ran Rkhunter 1.4.6 and recieved many &#8220;Warning&#8221; messages. I realize that Rkhunter has a hash for various executables and provides the &#8220;Warning&#8221; if the hashes of the current files are different. There were 24 occasions where the file properties had changed.

 
 
 However, how serious is this? For example, in the hashes below, the hash of the programs have clearly changed. Why would so many programs have been altered?  
 
 
 ```
Warning: The file properties have changed:
          File: /usr/bin/ssh
          Current hash: e875b1185577ff872fbaabde481cc196af03745c530403c8303f00fe35859bf7
          Stored hash : 240970e65242586bf8160f3cebc4a7e8c7074a5fc203219af153fa858490f81c
          Current inode: 1051539    Stored inode: 1049714
          Current file modification time: 1627044912 (23-Jul-2021 13:55:12)
          Stored file modification time : 1590737829 (29-May-2020 08:37:09)
 Warning: The file properties have changed:
          File: /usr/bin/ps
          Current hash: 701d30ed7055d688aad76e94f43f6da71bf6ca58caa961cee5f38d0c45c0aa52
          Stored hash : 6e1be2ff79adf6a05ad09b6df87618a5f9857378a2978beb1dec12e20fd34844
          Current inode: 1050911    Stored inode: 1049547
          Current file modification time: 1622222850 (28-May-2021 18:27:30)
          Stored file modification time : 1582782727 (27-Feb-2020 05:52:07)
 Warning: The file properties have changed:
          File: /usr/sbin/groupadd
          Current hash: c4a51fd9348b4981d8cd5a4d9115e25dd1b7647129d01f31b962936d96c33b8d
          Stored hash : 05b11bc4a81adda19d9e899ee05faa79553fd9bfd088911ec6ec9b31f358beb2
          Current inode: 1050480    Stored inode: 1057423
          Current file modification time: 1626300498 (14-Jul-2021 23:08:18)
          Stored file modification time : 1590647867 (28-May-2020 07:37:47)
```

---

### Post by TheFu on 2021-08-21
When you patch, you should keep track of what changed and allow rkhunter to update the DB for those programs.  If you don't, then the signatures will be out of date and look like someone swapped in bad versions of important programs.  If I saw those programs in a rkhunter output, I'd wipe the system, nuke it from orbit, that's the only way to be certain.   And next time, be more aware of which programs are updated so you can allow rkhunter's DB to update them too.

Or you could have been cracked.

Or rkhunter could be announcing false positives.

---

