---
title: "Adding shred to Nautilus"
date: 2009-03-16
forum: Security
---

### Post by zaphodbblx on 2009-03-16
found this neat shred utility here:
[http://www.ubuntugeek.com/tag/shred-ubuntu](http://www.ubuntugeek.com/tag/shred-ubuntu)
it uses Nautilus and you can shred a file with a right click
this is the info it tells you to input:

Label: Shred
Tooltip: shred utility to securely erase files
Icon: gtk-dialog-warning
Path: shred
Parameters: -f -u -v -z %M

what do the parameters mean?
 how secure is the shred utility that is built into ubuntu?
 I like to understand what I'm doing to my computer and how its being done and face it security often gets overlooked

---

### Post by kestrel1 on 2009-03-16
If you type```
shred --help
```
in a terminal it tells you what the parameters mean.

---

### Post by zaphodbblx on 2009-03-16
> **kestrel1 said:**
> If you type```
shred --help
```
in a terminal it tells you what the parameters mean.

thanks! I was a bit scared to type shred into the terminal

---

### Post by HermanAB on 2009-03-17
Just remember that shred doesn't really work.  It isn't really any better than rm.

Cheers,

Herman

---

### Post by hyper_ch on 2009-03-17
> **HermanAB said:**
> Just remember that shred doesn't really work.  It isn't really any better than rm.

because of the beauty of journaling filesystems.

---

### Post by kestrel1 on 2009-03-17
> **hyper_ch said:**
> because of the beauty of journaling filesystems.
For anyone interested a little more info o the above: [http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

---

### Post by cdenley on 2009-03-17
Except by default, the actual file is not journaled, so overwriting with random data multiple times on a default configuration would protect it from being recovered by physically analyzing the disk platters with special tools.

```

man shred

```
> 
In the case of ext3 file systems, the  above  disclaimer  applies  (and shred  is  thus  of  limited  effectiveness) only in data=journal mode, which journals file data in addition to just  metadata.   In  both  the data=ordered  (default) and data=writeback modes, shred works as usual. Ext3 journaling modes can  be  changed  by  adding  the  data=something option  to  the  mount  options  for  a  particular  file system in the /etc/fstab file, as documented in the mount man page (man mount).


---

### Post by hyper_ch on 2009-03-17
you don't know for sure what state the file is in.

---

### Post by HermanAB on 2009-03-17
The problem is the uncertainty.  

Assuming you are not an exhibitionist - If you had a personal cloaking device that worked some of the time, would you walk around naked in public?

If you are going through a divorce and you had a paper shredder that sometimes shredded your bank statements and sometimes not, would you hand your office trash to your spouse's lawyer?

So, since shred cannot be relied upon, there is no point in using it.  If you need control over your data, encrypt it with LUKS.  Then you will have certainty.

Cheers,

Herman

---

### Post by cdenley on 2009-03-17
I am certain that my system mounts ext3 filesystem in ordered write mode. If I had files which already exist, and I wanted to erase the files securely without destroying the entire filesystem, I would certainly use shred or another similar utility. Of course encryption is a better method of protecting data, but if the data is already written without encryption, saying tools like shred are completely useless is absurd.

Even IF shred is "unreliable" on ext3 with ordered write mode, as you claim, it is still better than doing nothing.

---

### Post by HermanAB on 2009-03-17
Well, if you can entrust your deleted data to an unreliable tool, then you need to wonder whether you needed that tool in the first place.  

That is why I am saying that shred is no better than rm.  In fact, rm is better, since it doesn't leave you with a false sense of security.

If you are worried about data security, use LUKS.  If not, don't bother.

Cheers,

Herman

---

### Post by cdenley on 2009-03-17
> **HermanAB said:**
> That is why I am saying that shred is no better than rm.  In fact, rm is better, since it doesn't leave you with a false sense of security.

Well I certainly disagree. Using shred would prevent me from recovering your data. The rm command wouldn't.

---

### Post by hyper_ch on 2009-03-18
if shred would delete the actual data in question... which is to be disputed.

---

### Post by cdenley on 2009-03-18
> **hyper_ch said:**
> if shred would delete the actual data in question... which is to be disputed.

Show me something which contradicts shred's documentation and indicates the actual data wouldn't be deleted when the default mount options for ext3 are used.

---

### Post by kestrel1 on 2009-03-18
Would wipe be any better than shred?
```
sudo apt-get install wipe
```

---

### Post by cdenley on 2009-03-18
> **kestrel1 said:**
> Would wipe be any better than shred?
```
sudo apt-get install wipe
```

I'm sure that uses the same method of simply overwriting a file.

---

### Post by HermanAB on 2009-03-19
Format a new file system (on a large USB memory stick for example):
mkfs.ext3 /dev/sdb
mkdir /mnt/test
mount /dev/sdb /mnt/test

Save some large text files.
cp -r ~/Documents /mnt/test 
Run shred on all the files.

Dump the file system using dd and look for strings:
dd if=/dev/sdb | strings

Cheers,

Herman

---

### Post by cdenley on 2009-03-19
```

mkdir shred
dd if=/dev/zero of=shred.ext3 bs=1024 count=40960
mkfs.ext3 -F shred.ext3
sudo mount shred.ext3 ./shred -o loop
sudo chown $USER shred
for ((i=0;i<1000000;i+=1)); do echo this is a large text file;done>shred/test.txt
shred -n 1 -z -u shred/test.txt
sudo umount ./shred
strings shred.ext3

```
No strings were found from the file itself. The file's name was found, probably because the meta-data was journaled, but not the actual data. The same thing could have been accomplished by simply zeroing out the file.

---

### Post by hyper_ch on 2009-03-19
> **cdenley said:**
> Show me something which contradicts shred's documentation and indicates the actual data wouldn't be deleted when the default mount options for ext3 are used.

did you test that it really does delete that data? what are the default mount options?

---

### Post by cdenley on 2009-03-19
> **hyper_ch said:**
> did you test that it really does delete that data? what are the default mount options?

I just posted every command I used which shows that not a single byte was recoverable from the filesystem. For default mount options, try
```

man mount

```
Specifically, the relevant default mount option is data=ordered.

---

