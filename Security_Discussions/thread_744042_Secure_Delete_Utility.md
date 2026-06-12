---
title: "Secure Delete Utility?"
date: 2008-04-03
forum: Security Discussions
---

### Post by MarkH01 on 2008-04-03
I use sysinternals sdelete for windows to nuke the slack space... that drive space that is scheduled to be overwritten after you empty your trash bin.

Whats the equivalent for ubuntu?

---

### Post by 505 on 2008-04-03
If you use ext3 as your file system you don't need anything. ext3 really deletes files when you delete them. This also means you cannot do a 'restore deleted files' on ext3. If you delete from the GUI, make sure you shift-delete, otherwise the files are copied to the recycle bin. To be sure, use the 'rm' command from the shell.

---

### Post by cdenley on 2008-04-03
I don't think the actual file is actually zeroed out, just the data about the file. In other words, the data will be there, but any recovery tool wouldn't know where to find it, where a file begins and ends, how it may be fragmented, or if a block of data used to be part of a file unless there is an observable pattern like plain text.

If you want to overwrite the contents of a file before you delete it, use the shred command. If you want to overwrite the unused data on your hard drive, I think you can use the sfill command after installing the secure-delete package. These take much longer than a normal delete, and aren't really necessary for ext3 filesystems unless you are paranoid.

---

### Post by HermanAB on 2008-04-03
This comes up all the time.  The problem is that it is not possible to delete data from magnetic media using ordinary tools. Read that again.

The military zeroes out files and then re-use the media on the same or higher classification level.  When media needs to be recycled, it is burned, melted or shredded.  

Multiple overwrites of data doesn't help - just a waste of time.

So in general, you have three solutions.  To provide protection against your little kid sister, just delete the file.  To provide protection against people with special equipment - destroy the media thoroughly.  For all other uses, encrypt the whole file system, then to delete it, forget the key.  

Note that simply encrypting individual files is useless too - you have to decrypt it to use it and this decrypted copy will hang around forever even if you delete it. So encrypting individual files is just a waste of time as well, but it does provide protection against your little kid sister.

So in summary, most of the things people commonly do to protect their data, is a waste of time.  The only thing that works, is to encrypt the whole filesystem, specifically /tmp, /swap and /home.  Encrypting more than those three, is also a waste of time and only serves to slow down the system.

Cheers,

Herman

---

### Post by cdenley on 2008-04-03
> 
So in general, you have three solutions. To provide protection against your little kid sister, just delete the file. To provide protection against people with special equipment - destroy the media thoroughly. For all other uses, encrypt the whole file system, then to delete it, forget the key.

A single pass overwrite would prevent me from reading it. Of course I wouldn't be able to tell what data belongs to which file, but if you delete a text file, I might be able to recover it. More than one pass would be a waste of time, but would make it more difficult to read the erased data from the track edges (in theory). I don't think recovering actual data which has been erased from modern drives is a proven possibility, though. I agree that encrypting entire filesystems is the way to go.

---

### Post by netlogic on 2008-04-03
1. Thc
2. Sfill
3.bcwipe
4. Shred
5. Srm

---

### Post by FakeOutdoorsman on 2008-04-03
```
shred -z -u file.ext
```

From 'man shred':
> shred - overwrite a file to hide its contents, and optionally delete it
-z, add a final overwrite with zeros to hide shredding
-u, truncate and remove file after overwriting

---

### Post by kevdog on 2008-04-03
How is encrypting individual files worthless??  How much different is this if you encrypt the file and then forget the password compared to whole system encryption and forgetting the password??

Who cares if the encrypted file is around forever -- its encrypted.  If its decrypted to RAM -- it doesnt hang around forever!

---

### Post by netlogic on 2008-04-03
i think what he meant was if you use the pgp file encryption, you will have to expand your file to somewhere. if you kept the original file and deleted expanded file, you can   always umount ext3 partition and mount as ext2 and start greping for your files.

Can I please have my $2, kevdog?

---

### Post by kevdog on 2008-04-03
Here is where you can find your $2:
[http://www.youtube.com/watch?v=S2C07yRCdT8&feature=related](http://www.youtube.com/watch?v=S2C07yRCdT8&feature=related)

---

### Post by netlogic on 2008-04-03
damn brother... that is some cold ****.
i will comb your hair to your baldness.

---

### Post by /etc/init.d/ on 2008-04-04
> **kevdog said:**
> How is encrypting individual files worthless??  
This has already been explained.  If you encrypt and invidual file, the original unencrypted copy is stil there.  If you delete it, you still face the age-old issue of magnetic remanence.  The only solution is to encrypt everything from the beginning.  Having unencrypted copies lying around (even if "deleted") can also open you up to a known-plaintext attack, which can considerably weaken some less-secure ciphers.

> **kevdog said:**
> Who cares if the encrypted file is around forever -- its encrypted.  If its decrypted to RAM -- it doesnt hang around forever!
Files encrypted with DES in only the 1990s are now trivially breakable with brute-force.  The lasting security of encryption is not a given.

---

### Post by kevdog on 2008-04-05
It would be hard to find an available file encryption utility today that encrypts through straight DES.  3DES is still used, but to everyone's knowledge although this is extremely slow, there has been no reported breaks with this algorithm.

Yes security algorithms will fail as time goes on and new methods are discovered, however I guess the same could be said of whole disk encryption also.

---

### Post by netlogic on 2008-04-05
> **kevdog said:**
> It would be hard to find an available file encryption utility today that encrypts through straight DES.  3DES is still used, but to everyone's knowledge although this is extremely slow, there has been no reported breaks with this algorithm.

Yes security algorithms will fail as time goes on and new methods are discovered, however I guess the same could be said of whole disk encryption also.

I think you are still missing the point. If you extract the data to a non-encrypted volume, a single file encryption is pointless...

I still want my $2! DAMN YOU!!!!
just kidding.

---

### Post by notebooktessler on 2008-06-03
> **HermanAB said:**
> 
Multiple overwrites of data doesn't help - just a waste of time.

So in summary, most of the things people commonly do to protect their data, is a waste of time.  The only thing that works, is to encrypt the whole filesystem, specifically /tmp, /swap and /home.  Encrypting more than those three, is also a waste of time and only serves to slow down the system.


Interesting. Thanks, I wasn't aware of that. 

Does anyone know a good guide to encrypting the whole filesystem? What encryption tools/programs would you recommend? EncFS?

---

### Post by stream303 on 2008-06-03
Another possibility for a kid-sister that is really smart, would be to partition a non-journaling filesystem with ext2 rather than ext3.  On those, you could use the secure deletion tools mentioned. :)

But unless you keep on top of things, you are likely to leave something hanging around in plaintext somewhere... :)

---

