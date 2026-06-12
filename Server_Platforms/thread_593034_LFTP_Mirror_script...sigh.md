---
title: "LFTP Mirror script...sigh"
date: 2007-10-26
forum: Server Platforms
---

### Post by meighty on 2007-10-26
Below is my short script i wrote for lftp. It will be used to keep a backup copy of various files (pictures, etc) on a remote server. For some reason when i run it it won't get past the login. Doesn't put the mirror command out there. I'm a scripting noob so feel free to flame (especially if this is in the wrong section). It all works if  I do it manually.  


lftp -p  PORT -u username,password ftp.address.com/folder	
mirror -R -c -v --log=/home/username/lftp.log /home/username/folder .
quit

:guitar:
Metal

---

### Post by meighty on 2007-10-26
so i get the "cd ok, cwd=/directory"

then just sits at the lftp prompt.

---

### Post by nix4me on 2007-10-26
im having some issues with lftp too.  my queue mirror commands are not working correctly.

---

### Post by jpkotta on 2007-10-27
Did you put all three of those commands in a script?  If so, it won't work.  Once you start lftp, it listens for input, not the shell that was originally executing the script.  Therefore everything after the lftp line isn't executed until after lftp exits.

lftp is scriptable though.  Have a look at the "-f" or "-c" options.

---

### Post by meighty on 2007-10-27
> **jpkotta said:**
> Did you put all three of those commands in a script?  If so, it won't work.  Once you start lftp, it listens for input, not the shell that was originally executing the script.  Therefore everything after the lftp line isn't executed until after lftp exits.

lftp is scriptable though.  Have a look at the "-f" or "-c" options.


Very nice. 2 points for you! Had been trying to figure it out and just over looked the simple things

lftp -f /scriptfile

works like a charm...i think. Have a bit more of testing to do. 

Should be as simple to make a cron job with that command. sweet!


:guitar:
Metal!

---

### Post by jpkotta on 2007-10-27
You may also want to try rsync, because it is made for this kind of thing.

---

### Post by hyper_ch on 2008-05-24
I know this is an old post BUT do I understand correctly:

You can mirror your local files TO your backup server with lftp?

---

