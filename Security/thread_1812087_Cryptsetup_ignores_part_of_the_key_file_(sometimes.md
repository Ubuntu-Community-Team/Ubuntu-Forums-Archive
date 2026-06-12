---
title: "Cryptsetup ignores part of the key file (sometimes)"
date: 2011-07-25
forum: Security
---

### Post by u-slayer on 2011-07-25
I was attempting to mount a volume with cryptsetup, but I couldn't get it to work. After some experimentation I found out the ***way*** you mount volumes changes what password cryptsetup uses. It has very inconsistent (and therefore dangerous behavior) when reading keyfiles. 

When you cat a keyfile into cryptsetup it behaves normally:

**cat /ram/key | cryptsetup create test1 /dev/ram0 --hash sha256 --cipher aes-cbc-plain --key-size 256 --key-file=-; sleep 0.5; xxd test1 | head -n 1; cryptsetup remove test1**

I can open up the keyfile file with ghex2, go to the end, change one bit and run the above command again and I will get a completely different output.

However! When I redo the command like this:

**cryptsetup create test1 /dev/ram0 --hash sha256 --cipher aes-cbc-plain --key-size 256 --key-file=/ram/key; sleep 0.5; xxd test1 | head -n 1; cryptsetup remove test1**

It only reads the first 256 bits of the keyfile! I can monkey around the end of the keyfile all day long, adding random data to make it more secure and so forth, but cryptsetup will completely ignore me! This is horribly insecure. What is the point of --hash=sha256 if it's only hashing the first 256 bits? Futhermore this is very confusing if you create a volume using "cat | cryptsetup" but later on try to mount it with "--key-file=" and it won't work.

---

### Post by u-slayer on 2011-08-02
Who marked my thread as solved? I never got any responses.

---

