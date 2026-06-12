---
title: "HOWTO: Encrypt /tmp"
date: 2012-12-30
forum: Security
---

### Post by DarkDead on 2012-12-30
EDIT: Please prefer [Paddy Landau's approach]("http://ubuntuforums.org/showpost.php?p=12433861&postcount=9") which solves some problems of my approach.

--------------------------------------------------------------------------

After encrypting my home directory, the swap area and making sure my login password was hashed with a strong hash algorithm on /etc/shadow I realized I still had a loophole on the /tmp directory. Thus here is my approach to encrypt it.

You'll have to run the following commands as root.

1. Create an empty file with 300 MiB where your tmp files will reside.
```
dd if=/dev/zero of=/.crypttmp count=300 bs=1M
```

2. Mount it via loop device.
```
losetup /dev/loop0 /.crypttmp
```

3. Format as a ext2 partition. There is no need for journalling.
```
mkfs.ext2 /dev/loop0
```
Formating as ext4 with journaling disabled would probably be more performant but it gave me an error. It might be worth to try it on your system.
```
mkfs.ext4 -O ^has_journal /dev/loop0
```

4. Edit /etc/crypttab and paste the following line.
```
crypttmp /.crypttmp /dev/urandom precheck=/bin/true,tmp,size=256,hash=sha256,cipher=aes-cbc-essiv:sha256
```

5. Edit /etc/fstab and paste the following line.
```
/dev/mapper/crypttmp /tmp ext2 defaults 0 2
```
Substitute ext2 for ext4 if you were able to format as ext4.

6. Start the encrypted disk.
```
cryptdisks_start crypttmp
```

7. Delete all files in /tmp directory.
```
rm -r /tmp/*
```

8. Mount the new encrypted directory.
```
mount /tmp
```

Problem with this approach:
I don't like the fact of having to allocate a fixed sized file: the allocated space can be either too low or wasteful. Using a LVM partition would solve this as it can be resized while mounted. Another solution would be to use a stacked filesystem encryption like eCryptfs. The issue is you can't use a one-time randomly generated password with eCryptfs because "If you use more than one password, you will have more than one set of data." (from [Ecryptfs - bodhizazen]("http://bodhizazen.net/Tutorials/Ecryptfs/")). Thus in order to use eCryptfs to encrypt /tmp one would have to choose a password and introduce it during boot. This is impractical and would require the password to be shared amongst all users of the machine.

Sources:
[Encrypted loop device on boot]("http://stolowski.blogspot.pt/2008/08/encrypted-loop-device-on-boot.html")
[How do I encrypt my /tmp directory?]("http://askubuntu.com/a/146641")
[ext4 disable journal]("http://fenidik.blogspot.pt/2010/03/ext4-disable-journal.html")

---

### Post by phamhung on 2012-12-31
If mounting it with defaults permission, users can still compile scripts on /tmp, can't they? Why not mount it with "loop,nosuid,noexec,nodev,noatime,noauto,rw" permissions?

Thanks.

---

### Post by sudodus on 2012-12-31
[s]When you use encrypted home, the /tmp directory will be overwritten (made extremely hard to read) at shutdown or reboot.[/s] But it is readable while the computer is running, as is your home directory.

---

### Post by phamhung on 2012-12-31
> **sudodus said:**
> When you use encrypted home, the /tmp directory will be overwritten (made extremely hard to read) at shutdown or reboot. But it is readable while the computer is running, as is your home directory.

That's not my point. If I keep my machine running, and /tmp is mounted with defaults permission, users can still upload script to /tmp and compile it there, is that correct?

---

### Post by samiux on 2012-12-31
> **phamhung said:**
> That's not my point. If I keep my machine running, and /tmp is mounted with defaults permission, users can still upload script to /tmp and compile it there, is that correct?

Even the /tmp is encrypted, the machine is running and the user is logged in, the /tmp is readable and writeable unless you do something else on it.

Samiux

---

### Post by sudodus on 2012-12-31
> **phamhung said:**
> That's not my point. If I keep my machine running, and /tmp is mounted with defaults permission, users can still upload script to /tmp and compile it there, is that correct?
Yes, in a running machine, /tmp is available to anyone logged in. So you need to keep people out, to protect from writing on /tmp.

```
drwxrwxrwt  16 root root  4096 dec 31 17:27 tmp
```

I think it would create problems to change the permissions, because many programs used by the system uses /tmp and 'are used to' the default permissive access.

---

### Post by DarkDead on 2013-01-01
Thanks everyone for the feedback.

So it seems encrypting /tmp is only advantageous to keep it unreadable in case of a energy cut-off shutdown. And if no other user has access to the system.

---

### Post by sudodus on 2013-01-02
.

---

### Post by Paddy Landau on 2013-01-02
> **DarkDead said:**
> So it seems encrypting /tmp is only advantageous to keep it unreadable  in case of a energy cut-off shutdown. And if no other user has access to  the system.
No, I wouldn't say that. If you shut down normally, the [FONT=Lucida Console]/tmp[/FONT] files are deleted, but the data is still available on the hard drive, accessible to anyone has physical access to your machine. If confidentiality is important, you should indeed encrypt your [FONT=Lucida Console]/tmp[/FONT] folder.

@DarkDead, I took a different approach, which eliminates the problems both of other users reading your temporary files and of having a fixed size. Why not put the temporary folder into your home folder?

It requires your home folder to be encrypted; mine is encrypted using the [FONT=Lucida Console]ecryptfs[/FONT] method that comes standard with Ubuntu. If your home folder is not already encrypted, you can encrypt it using the [Post Installation Encryption instructions]("https://help.ubuntu.com/community/PostInstallationEncryption").

Here is how I did it.


[LIST]
[*]```
mkdir ~/.tmp                [COLOR=Blue]# Create a hidden folder for temporary files.[/COLOR]
chmod u+rwx,go-rwx ~/.tmp   [COLOR=Blue]# Restrict access to only the user.[/COLOR]
```
[/LIST]

[LIST]
[*]Add the following code to [FONT=Lucida Console]/etc/profile[/FONT]: this caters for multiple users, not all of whom might have created the folder.
```
[COLOR=Blue]# Set the user's private temprary folder if it exists.[/COLOR]
if [ -d "${HOME}"/.tmp ]
then
        export TMP="${HOME}"/.tmp
        export TEMP="${HOME}"/.tmp
        export TMPDIR="${HOME}"/.tmp
fi
```
[/LIST]

[LIST]
[*]The standard folder [FONT=Lucida Console]/tmp[/FONT] is cleaned at shutdown. However, the user's folder must be cleaned at logout before the encryption is closed.
[LIST=1]
[*]Create a script — let's call it [FONT=Lucida Console]/opt/lightdmlogout[/FONT] — make it executable and fill it with the following code.
```
[COLOR=Blue]# Clean the user's private temprary folder if it exists.[/COLOR]
if [ -d "${HOME}"/.tmp ]
then
        [COLOR=Blue]# Delete all contents of ~/.tmp including hidden files and folders.[/COLOR]
        rm --force --recursive --one-file-system "${HOME}"/.tmp/* "${HOME}"/.tmp/.*[^.]*
fi
```
[*]Run the logout script at logout. Edit [FONT=Lucida Console]/etc/lightdm/lightdm.conf[/FONT]. Under the [FONT=Lucida Console][SeatDefaults][/FONT] section, add the following line.
```
session-cleanup-script=/opt/lightdmlogout
```
[/LIST]
 
[/LIST]
Pro:

[LIST]
[*]Avoids the fixed-size limitation.
[/LIST]
Cons:

[LIST]
[*]A few scripts and applications might have been written to use [FONT=Lucida Console]/tmp[/FONT] explicitly and to not examine [FONT=Lucida Console]${TMPDIR}[/FONT].
[*]Needs some adjustment if you are using (say) Lubuntu or Xubuntu, as their start-up and shut-down processes differ from Ubuntu's.
[/LIST]
You will find that the system still uses [FONT=Lucida Console]/tmp[/FONT] for a few items, such as PulseAudio. That is fine, as there is no confidential data there.

---

### Post by sudodus on 2013-01-02
> **Paddy Landau said:**
> No, I wouldn't say that. If you shut down normally, the [FONT=Lucida Console]/tmp[/FONT] files are deleted, but the data is still available on the hard drive, accessible to anyone has physical access to your machine. If confidentiality is important, you should indeed encrypt your [FONT=Lucida Console]/tmp[/FONT] folder.

...

I see. I thought I had read somewhere that /tmp and swap are overwritten/encrypted when you select encrypted home in Ubuntu. But of course, if that is not case, it can be read with a tool like photorec.

I sat down right now and browsed the internet without finding any evidence that /tmp is overwritten. I'm sure about cryptswap, because I have tried that myself. So I guess /tmp is a source of information for anybody getting access to the computer unless you encrypt it, or (faster but not as secure) set up the system to overwrite all files in /tmp before deleting them at shutdown (poweroff or reboot).

Edit: or make a ramdrive for /tmp

---

### Post by Paddy Landau on 2013-01-02
> **sudodus said:**
> I thought I had read somewhere that /tmp and swap are overwritten/encrypted when you select encrypted home in Ubuntu.
Swap is encrypted if you choose encryption.

[FONT=Lucida Console]/tmp[/FONT] is not overwritten; rather, the files are deleted on shut-down. Deleting files does not get rid of the data!

> **sudodus said:**
> … set up the system to overwrite all files before deleting them at shutdown (poweroff or reboot).
Overwriting files is a crazy way to go; you have to overwrite several times with random codes to be reasonably sure of the data disappearing. Besides, it would not delete the data on power failure, nor would it hide the data from other users on the system.

> **sudodus said:**
> … or make a ramdrive for /tmp
Yes, if you have sufficient RAM. If you were editing large video files, for example, you would need a massive amount of RAM!

---

### Post by sudodus on 2013-01-02
> **Paddy Landau said:**
> ...
Overwriting files is a crazy way to go; you have to overwrite several times with random codes to be reasonably sure of the data disappearing. Besides, it would not delete the data on power failure, nor would it hide the data from other users on the system.
...
I know, I read about it here: ```
info shred
```
:-)
But how is ecrypt doing? I guess your home folder will be stored temporarily without encryption while you are logged in?

Edit: Or is everything decrypted, whenever you ask for it?

---

### Post by Paddy Landau on 2013-01-02
> **sudodus said:**
> But how is ecrypt doing?
With ecryptfs, your home folder is encrypted and decrypted on-the-fly. The files are stored encrypted, but *appear* to be decrypted while you access them.

If your home folder is encrypted, you can see what it really looks like by looking at the following folder (substitute "sudodus" with your real user name):
```
/home/.ecryptfs/sudodus/.Private
```

---

### Post by samiux on 2013-01-02
I wonder if your Ubuntu box, where the /tmp is encrypted, is a multi-user system, what will it be happened.

Why not try to see?

Samiux

---

### Post by sudodus on 2013-01-02
> **Paddy Landau said:**
> With ecryptfs, your home folder is encrypted and decrypted on-the-fly. The files are stored encrypted, but *appear* to be decrypted while you access them.

If your home folder is encrypted, you can see what it really looks like by looking at the following folder (substitute "sudodus" with your real user name):
```
/home/.ecryptfs/sudodus/.Private
```
It is quite efficient even on an old slow laptop :-)

---

### Post by Paddy Landau on 2013-01-02
> **samiux said:**
> I wonder if your Ubuntu box, where the /tmp is encrypted, is a multi-user system, what will it be happened.
What do you mean?

If [FONT=Lucida Console]/tmp[/FONT] is not encrypted, all users will be able to read and write (but not modify someone else's files).

If [FONT=Lucida Console]/tmp[/FONT] is encrypted as per [post=12429731]DarkDead's instructions[/post], that is still the case, but once the machine has been turned off, all files will be gone.

If using [post=12433861]my instructions[/post], files will be completely private to each user (although visible to root while the user is logged on).

---

### Post by zika on 2013-01-02
Silly question: Why not just put /tmp in RA memory (tmpfs) as I do?

---

### Post by Paddy Landau on 2013-01-02
> **zika said:**
> Silly question: Why not just put /tmp in RA memory (tmpfs) as I do?
Yes, as [post=12434059]sudodus mentioned[/post], you can do that. It does require sufficient RAM. If you have (say) 4Gb RAM and only use browsing, email and documents, that's fine. But if you use the computer for heavy use such as editing large videos, that may not work. It depends on both your hardware and how you use it.

---

### Post by samiux on 2013-01-02
Silly answer :

In my opinion, the /tmp and swap are encrypted is for single user system and it is limited to be a desktop computer only.  For a multi-user system or server, this approach is impractical.

Samiux

---

### Post by zika on 2013-01-02
> **Paddy Landau said:**
> Yes, as [post=12434059]sudodus mentioned[/post], you can do that. It does require sufficient RAM. If you have (say) 4Gb RAM and only use browsing, email and documents, that's fine. But if you use the computer for heavy use such as editing large videos, that may not work. It depends on both your hardware and how you use it.Sorry I've missed that edit by @sudodus...
I was judging by the size of file in post #1...
> Create an empty file with 300 MiB where your tmp files will reside.

---

### Post by zika on 2013-01-02
> **samiux said:**
> Silly answer :

In my opinion, the /tmp and swap are encrypted is for single user system and it is limited to be a desktop computer only.  For a multi-user system or server, this approach is impractical.

SamiuxNothing silly about that... ;)

---

### Post by DarkDead on 2013-01-02
Nice idea Paddy Landau. Working like a charm. I didn't know that the tmp directory was set through an environment variable.

Just a note for those using gdm: place the log out ~/.tmp cleaning code in /etc/gdm/PostSession/Default

@zika The 300 MiB size was a value based on my system's setup. As Paddy Landau mentioned, the space needed for the tmp directory varies a lot. Thus I didn't like my approach of allocating a fixed space for it.

---

### Post by Paddy Landau on 2013-01-02
> **samiux said:**
>  For a multi-user system or server, this approach is impractical.
In what way would encrypted swap or [FONT=Lucida Console]/tmp[/FONT] be impractical on a multi-user system?

---

### Post by samiux on 2013-01-02
> **Paddy Landau said:**
> In what way would encrypted swap or [FONT=Lucida Console]/tmp[/FONT] be impractical on a multi-user system?

Silly answer :

Consider if every user has his/her cron job running in the background of a multi-user system where the /tmp and swap as well as their /home directory are encrypted.

Samiux

---

### Post by Paddy Landau on 2013-01-02
> **samiux said:**
> Consider if every user has his/her cron job running in the background of a multi-user system where the /tmp and swap as well as their /home directory are encrypted.
If that's a silly answer, then I'm a bit silly :shock:

Seriously, though, I don't understand. What would be the problem with that?

---

### Post by samiux on 2013-01-02
> **Paddy Landau said:**
> If that's a silly answer, then I'm a bit silly :shock:

Seriously, though, I don't understand. What would be the problem with that?

More silly answer :

Consider if the users' home directories, /tmp and swap are encrypted in a multi-user system or server.  That mean the encrypted home directories and other encrypted directories are required to decrypt before further process.  This process is to login in order to decrypt it.

Scripts are stored in the encrypted user home directories and they will be ran by cron job hourly/daily/weekly/monthly or what so ever.  Since the scripts are encrypted and they are required to decrypt in order to run but the users are already logout, how can the scripts be ran? 

Samiux

---

### Post by Paddy Landau on 2013-01-02
> **samiux said:**
> … cron job hourly/daily/weekly/monthly or what so ever.
Thanks, I understand now (feeling less silly).

[LIST]
[*]Swap and [FONT=Lucida Console]/tmp[/FONT]: Handled at the system level, so not a problem even if no one is logged in.
[/LIST]

[LIST]
[*]System-level cron: Root is not encrypted, so not a problem provided it does not attempt to manipulate users' home folders.
[/LIST]

[LIST]
[*]User-level cron: will always be a problem if the user's home folder is encrypted but the user is not logged in.
[/LIST]
**Conclusion:**

If a script run by a cron job (whoever owns it) attempts to access any user's home folder, it should always check that the folder is not encrypted. How? I'm not sure; I think (but I stand to correction) that the easiest method is to see if the following folder exists:
```
/home/${USER}/Desktop
```If it exists, assume that the folder is either unencrypted or decrypted.

---

### Post by fakeyyy on 2013-01-03
Quote:
                                                                      Originally Posted by **phamhung**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12430987#post12430987")                 
                 *That's not my point. If I keep my  machine running, and /tmp is mounted with defaults permission, users can  still upload script to /tmp and compile it there, is that correct?*
                                 
Even the tmp is encrypted, the computer is operating and the user is  logged in, the tmp is readable unless you do something  else on it.




---------------------------------------------
I discovered this site while searching for [URL="http://www.senacaeu.com"]security services
[/URL]

---

### Post by phamhung on 2013-01-03
> **fakeyyy said:**
> Even the tmp is encrypted, the computer is operating and the user is  logged in, the tmp is readable unless you do something  else on it.


It seems still someone don't recognize the difference between read and execute permissions?

---

### Post by samiux on 2013-01-03
> **phamhung said:**
> It seems still someone don't recognize the difference between read and execute permissions?

Attackers may not need to execute the script/exploit at /tmp.

Samiux

---

### Post by phamhung on 2013-01-03
Of course, but if you mount it without execute permission (as the OP mounted /tmp with default permissions), attackers cannot compile their script there on /tmp.

---

### Post by samiux on 2013-01-03
> **phamhung said:**
> Of course, but if you mount it without execute permission (as the OP mounted /tmp with default permissions), attackers cannot compile their script there on /tmp.


Agreed.  But the main point is that attackers are not required to execute or compile the script at /tmp.  There are some areas can do this job and /tmp is not the only area to do the job.

By the way, some applications may need to execute something at /tmp.

Samiux

---

### Post by phamhung on 2013-01-03
/tmp is still the first area, and the default area, that script kidders try to use. By that way, mounting /tmp with default permission will be a big security hole, unless I am wrong with encrypted partition in Ubuntu? That's why I raised question with the OP, if you read my posts again.

---

### Post by Paddy Landau on 2013-01-03
> **phamhung said:**
> /tmp is still the first area, and the default area, that script kidders try to use. By that way, mounting /tmp with default permission will be a big security hole, unless I am wrong with encrypted partition in Ubuntu? That's why I raised question with the OP, if you read my posts again.
I don't know the answer to your question, but I do know that the default mount of [FONT=Lucida Console]/tmp[/FONT] in a fresh installation is read-write-execute access to everyone, with the caveat that the restricted deletion flag is set. In other words, the equivalent of:
```
chmod a+rwx,+t /tmp
```

---

### Post by samiux on 2013-01-03
> **phamhung said:**
> /tmp is still the first area, and the default area, that script kidders try to use. By that way, mounting /tmp with default permission will be a big security hole, unless I am wrong with encrypted partition in Ubuntu? That's why I raised question with the OP, if you read my posts again.

If the attacker knows to use /tmp for his operation, he is no longer a script kiddy anymore.  If the /tmp cannot be used for execute scripts, he will use other area in the system.  

There may be some other applications will use /tmp to execute something.  Therefore, the /tmp mounted without execute bit may cause problem unless you make sure no application that you are installed will use /tmp to execute something.

Please refer to [#26]("http://ubuntuforums.org/showpost.php?p=12434343&postcount=26") which stated that /home, /tmp and swap encryption is impractical in a multi-users and server environment.

Samiux

---

### Post by Paddy Landau on 2013-01-03
> **samiux said:**
> Please refer to [#26]("http://ubuntuforums.org/showpost.php?p=12434343&postcount=26") which stated that /home, /tmp and swap encryption is impractical in a multi-users and server environment.
Well, for many people, [FONT=Lucida Console]/home[/FONT] and swap are already encrypted anyway, so why not [FONT=Lucida Console]/tmp[/FONT]?

Besides, as already mentioned in [post=12434433]post #27[/post], swap and [FONT=Lucida Console]/tmp[/FONT] are mounted at boot, so they are not impractical (except for hibernate, which is addressed in a [community help page]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap")).

It is only a problem with an encrypted [FONT=Lucida Console]/home[/FONT], and even then only for servers, and for cron jobs while the cron's owner is not logged in (unless you have further examples).

Conclusion:

[LIST]
[*]Whether or not you are on a server environment, encrypted [FONT=Lucida Console]/tmp[/FONT] and swap are perfectly fine, because they are mounted as soon as the system is booted.
[/LIST]

[LIST]
[*]If you are on a desktop (not server) environment, and you do not run cron jobs for users who are not logged in, encrypted [FONT=Lucida Console]/home[/FONT] folder is perfectly fine. Even with cron jobs for non-root users, a little care will generally (not always) eliminate the problem.
[/LIST]

---

### Post by samiux on 2013-01-03
> **Paddy Landau said:**
> Well, for many people, [FONT=Lucida Console]/home[/FONT] and swap are already encrypted anyway, so why not [FONT=Lucida Console]/tmp[/FONT]?

Besides, as already mentioned in [post=12434433]post #27[/post], swap and [FONT=Lucida Console]/tmp[/FONT] are mounted at boot, so they are not impractical (except for hibernate, which is addressed in a [community help page]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap")).

It is only a problem with an encrypted [FONT=Lucida Console]/home[/FONT], and even then only for servers, and for cron jobs while the cron's owner is not logged in (unless you have further examples).

Conclusion:

[LIST]
[*]Whether or not you are on a server environment, encrypted [FONT=Lucida Console]/tmp[/FONT] and swap are perfectly fine, because they are mounted as soon as the system is booted.
[/LIST]

[LIST]
[*]If you are on a desktop (not server) environment, and you do not run cron jobs for users who are not logged in, encrypted [FONT=Lucida Console]/home[/FONT] folder is perfectly fine. Even with cron jobs for non-root users, a little care will generally (not always) eliminate the problem.
[/LIST]

For server environment, just up to you.  I just point it out.  If anyone use this encryption matter on his remote server, you have been warned.

Samiux

---

### Post by Paddy Landau on 2013-01-03
> **samiux said:**
> If anyone use this encryption matter on his remote server, you have been warned.
Con for using encryption with swap and [FONT=Lucida Console]/tmp[/FONT] on a server: slows down the server.

I actually don't see any point whatsoever in using encryption on a server. But, from an academic point of view, I still do not understand how encrypting swap and [FONT=Lucida Console]/tmp[/FONT] could cause a problem.

But you are right about encrypting [FONT=Lucida Console]/home[/FONT] on a server (unless the home folder in question is not used to serve web pages or cron jobs — for example, the administrator's personal account).

---

### Post by samiux on 2013-01-03
> **Paddy Landau said:**
> Con for using encryption with swap and [FONT=Lucida Console]/tmp[/FONT] on a server: slows down the server.

I actually don't see any point whatsoever in using encryption on a server. But, from an academic point of view, I still do not understand how encrypting swap and [FONT=Lucida Console]/tmp[/FONT] could cause a problem.

But you are right about encrypting [FONT=Lucida Console]/home[/FONT] on a server (unless the home folder in question is not used to serve web pages or cron jobs — for example, the administrator's personal account).


Why not setup a lab to try and see?

Samiux

---

