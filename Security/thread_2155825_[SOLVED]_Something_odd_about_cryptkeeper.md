---
title: "[SOLVED] Something odd about cryptkeeper"
date: 2013-06-19
forum: Security
---

### Post by s1baker on 2013-06-19
hello,

Why does cryptkeeper open an encrypted folder so fast?
I have an encrypted folder that is 2 gigs in size, and when I use cryptkeeper
to open it, the folder and files therewithin are available immediately.

This indicates to me that the files themselves are not encrypted or it
would take a little while to decrypt them.

What gives?

Thanks

---

### Post by unspawn on 2013-06-19
> **s1baker said:**
> This indicates to me that the files themselves are not encrypted or it would take a little while to decrypt them.Easy. If you umount the volume, then list the source and target directories and if the target directory is empty and the source directory contains only illegible files ('file /path/to/source' only returning files of type "data") then it's encrypted.

---

### Post by s1baker on 2013-06-19
I'm sorry, I don't understand. The files are not in an external volume.
The files are in an encrypted folder ( called ".files_encfs" ) on the HD with the OS.
You can go into this directory and see that all the sub folders and files
are indeed encrypted. When cryptkeeper is called up and the password is inserted, the
decrypted folder ( "files" ) appears immediately and all of the sub folders
and files are immediately available for view. It would seem that each of these files would
have to be run through the decryption math to make them available. With a 
cryptkeeper folder that is over 2 gigs large, that should at least take a minute
or two, same as if one would copy 2 gigs of data from one place to another.

---

### Post by unspawn on 2013-06-21
In essence Cryptkeeper doesn't do anything but give you easy access to encfs / fusermount commands. Ten points for trying but you can't really compare efficient kernel / crypto / VFS / FUSE / EncFS ops with copying a tree of files.

---

### Post by s1baker on 2013-06-22
I understand that cryptkeeper is a user shell that uses the underling encfs routines to encrypt files.
So, if I understand you, copying a tree of files that takes 1-1/2 minutes will take 2 seconds using encfs?
Why isn't this techniq used for all copy file maneuvers?

Again, when cryptkeeper is run, another folder is created on the HD that is openly viewable. So you would 
have 2 folders on the HD. One would be ".files_encfs" and the other would be "files".
The open files would still have to be wrote to the HD. And you say that a copy/paste that takes 90 seconds
will take 2 seconds to do this with encfs?

---

### Post by unspawn on 2013-06-22
> **s1baker said:**
> So, if I understand you, No. **What I said is that [COLOR=red]you should not choose to compare apples with oranges.[/COLOR]** FUSE is the "File system in USEr land". (User land, as opposed to in-kernel ops, means any operations come with a performance penalty: compare for example "true" ZFS with FUSE ZFS.) EncFS builds a representation of whatever "~/.files_encfs/" holds in "~/files/". To truly understand it you should read up on FUSE developer documentation and EncFS internals or maybe ask the EncFS developer.

---

### Post by s1baker on 2013-06-22
[HTML]EncFS builds a representation of whatever "~/.files_encfs/" holds in "~/files/[/HTML]

Ok, I will ask this one more time.
1)  The encrypted files that encfs makes ( ".files_encfs" ) are stored on the HD.... True?
2)  The un-encrypted files are not stored anywhere ( or you don't have security whatsoever )...True?
3)  When encfs is called, the encrypted files ( ".files_encfs" ) are put in a viewable folder ( "files" ) on the HD ...True?
4)  The viewable files ( "files" ) would have to be run through the de-encryption math so that they are viewable...True?
5)  This decryption should take longer than 2 seconds if the files were large, say 2 to 4 gigs...True?

---

### Post by Ranko Kohime on 2013-06-24
> **s1baker said:**
> [HTML]EncFS builds a representation of whatever "~/.files_encfs/" holds in "~/files/[/HTML]

Ok, I will ask this one more time.
1)  The encrypted files that encfs makes ( ".files_encfs" ) are stored on the HD.... True?
2)  The un-encrypted files are not stored anywhere ( or you don't have security whatsoever )...True?
3)  When encfs is called, the encrypted files ( ".files_encfs" ) are put in a viewable folder ( "files" ) on the HD ...True?
4)  The viewable files ( "files" ) would have to be run through the de-encryption math so that they are viewable...True?
5)  This decryption should take longer than 2 seconds if the files were large, say 2 to 4 gigs...True?
1. True
2. True
3. Sort've.  See below.
4. True
5. Sort've.  Again, see below.

Decryption does take time, and the slower the processor the longer it takes.  I cannot max out my hard drive, even with a second generation Intel i3.  What EncFS does is just provide a folder where the files appear decrypted to any program that accesses them.  What happens is that when a program requests a file, EncFS decrypts the file as it is being accessed, and places the decrypted data into RAM for the program to access.

---

### Post by s1baker on 2013-06-25
> **Ranko Kohime said:**
>  What EncFS does is just provide a folder where the files appear decrypted to any program that accesses them.  What happens is that when a program requests a file, EncFS decrypts the file as it is being accessed, and places the decrypted data into RAM for the program to access.

So, is this basically what is happening?:

 When an encrypted folder ( ".files_encfs" ) is decrypted ( "files" ), and one goes into this decrypted folder with a file browser, the only thing one is seeing in this decrypted folder is the name labels of the folders and files that are under "files". 
 If one navigates to a sub-folder ( "files/subfolder" ), then at that time, all the folder and file label names for "subfolder" would be decrypted and listed. If one was to mouse-click a text file in folder "files/subfolder" ( "files/subfolder/textfile" ), then at that time, and only at that time, "textfile" would be decrypted and displayed to the user. If any changes were made to "textfile" by the user, and then "textfile" were closed out and saved, then "textfile" would be run through the encryption math routine and stored back in ".files_encfs/subfolder/textfile".

---

### Post by Ranko Kohime on 2013-06-25
> **s1baker said:**
> So, is this basically what is happening?
That is correct.

ETA: If you'd like to see this in action, then open up System Monitor, or the program "top" in a terminal window, then save a large file that will take several seconds to save, to the encrypted folder.  then issue the command "sync" in a terminal window, and watch what goes on with the CPU.  Lots of work for it when is starts writing the file, as it' s encrypting it while writing.

---

### Post by Hungry Man on 2013-06-26
Because encryption isn't slow, and neither is decryption. It's actually incredibly fast. The slow part is key generation, but even that isn't noticeable to a regular user.

On a modern CPU you can use AES 256bit at something like 80GB/s.

The decryption process is doing almost nothing to performance, you can decrypt 2GB of encrypted data just as fast as your HDD can read 2GB of data, assuming a somewhat decent CPU, and AES128bit (I think it uses 192-bit, which is something like 15% slower than 128bit).

---

