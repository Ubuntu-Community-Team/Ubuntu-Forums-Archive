---
title: "Dedicated server"
date: 2010-07-22
forum: Server Platforms
---

### Post by ash369 on 2010-07-22
Hey, i have just recently purchased a dedicated server to be used to run a srcds (Counter-Strike Source). But i am having problems. I am trying to run hldsupdatetool. I have done the following ...

These 3 commands worked fine.

```
mkdir srcds_l
cd srcds_l
wget http://www.steampowered.com/download/hldsupdatetool.bin
```

This command didn't seem to do anything.

```
chmod +x hldsupdatetool.bin
```

When i try to run hldsupdatetool it says -bash: ./hldsupdatetool.bin: No such file or directory. 

```
./hldsupdatetool.bin
```

I've looked around the internet and some people said installing lib32gcc1 would fix my problem. But when i try to install that it says:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package lib32gcc1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lib32gcc1 has no installation candidate
```

Running Ubuntu 9 64-bit. Can anyone help?

---

### Post by kaelspencer on 2010-07-22
wget downloads a file from the internet. Can you post the output from that command? If it does fail to download hldsupdatetool.bin, you won't be able to do anything with it.

chmod +x is making that file executable. You need to do this in order to run the .bin.

Also note, you'll need to be inside the same directory as the .bin for ./hldsupdatetool.bin to execute it.

Just in case, can you list that directory? Inside srcds_l, run

```
ls -la
```

---

### Post by ash369 on 2010-07-22
Thanks for your quick reply!

```
total 3444
drwxr-xr-x 2 root root    4096 2010-07-22 16:04 .
drwx------ 5 root root    4096 2010-07-22 17:11 ..
-rwxr-xr-x 1 root root 3513408 2005-09-02 03:27 hldsupdatetool.bin
```

---

### Post by kaelspencer on 2010-07-22
Interesting. It exists and is executable. Are you sure you're in the correct directory when you execute it?

It's possible the file is corrupt, but I doubt that would cause it to "not exist". You could try redownloading. Is there an MD5 checksum available for that download? That would confirm you have a proper file.

---

### Post by Bachstelze on 2010-07-22
Install ia32-libs.

@kaelspencer: "No such file or directory" when trying to run a binary usually indicates a binary compiles for another architecture (in this case, probbly an IA32 binary).  Since most 64-bit processors today are backwards-compatible with IA32 processors, it is possible to run an IA32 binary on them, just install the compatibility libraries (ia32-libs).

---

### Post by kaelspencer on 2010-07-22
> **Bachstelze said:**
> @kaelspencer: "No such file or directory" when trying to run a binary usually indicates a binary compiles for another architecture (in this case, probbly an IA32 binary).  Since most 64-bit processors today are backwards-compatible with IA32 processors, it is possible to run an IA32 binary on them, just install the compatibility libraries (ia32-libs).

Thanks for the info! Why is the error message so... misleading? Is something legitimately missing from the system (32bit libraries), or is this just the error messages it gives?

If the first, what is the reason that is says the binary is missing and not a particular library?

If the second, why is there not a slightly more descriptive error message?

Thanks for sharing!

---

### Post by ash369 on 2010-07-22
I tried

```
apt-get install ia32-libs
```

and got ...

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ia32-libs has no installation candidate
```

Am i using the right command? I'm pretty new to this, thanks for the help so far.

Here are the dedicated server specs, if needed.

```
    * 2.8GHz 3MB Intel® Dual Core processor
    * 2GB RAM and 500GB hard disk space
    * Ubuntu 9.04
    * 100Mbps connectivity &#8211; unlimited bandwidth
```

---

### Post by Bachstelze on 2010-07-22
> **ash369 said:**
> I tried

```
apt-get install ia32-libs
```

and got ...

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ia32-libs has no installation candidate
```

Am i using the right command? I'm pretty new to this, thanks for the help so far.

Yes, this is the right command.  Make sure you have the Universe repositories enabled.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by dfreer on 2010-07-22
Also make sure you run an apt-get update.

---

### Post by ash369 on 2010-07-22
Awesome. Thanks for for all your help. As i'm using the console with putty and SSH i had to edit the sources.list file using nano, i made a backup before editing. I uncommented one of the universe repositories and then ran:

```
apt-get update
```

Then tried installing ia32-libs again, and it worked!

```
apt-get install ia32-libs
```

Thanks a bunch! I was able to make the hldsupdatetool.bin file executable, i'm now downloading the server files for CS:S!

---

### Post by Bachstelze on 2010-07-22
> **kaelspencer said:**
> Thanks for the info! Why is the error message so... misleading? Is something legitimately missing from the system (32bit libraries), or is this just the error messages it gives?

If the first, what is the reason that is says the binary is missing and not a particular library?

If the second, why is there not a slightly more descriptive error message?

Thanks for sharing!

Actually, never mind what I said earlier.  Normally, when you try to execute a binary compiled for the wrong arcitecture, you get:

```
zsh: exec format error: ./hello/usr/bin/hello
```

Or, if you use a bad shell:

```
bash: ./hello/usr/bin/hello: cannot execute binary file
```

The reason you get a different message when you're trying to run an IA32 binary on an amd64 processor is that the executable is *not* in the wrong format (i.e. it is in a format the processor understands).  Why you get "No such file or directory", though, I must admit I do not know.  What happens behind the scenes when you execute a binary is far from trivial.

---

