---
title: "Rsync &quot;Error in rsync protocol data stream&quot;"
date: 2017-10-21
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2017-10-21
Hi

Running Windows 10 Enterprise with 'C:\cygdrive' folder containing 4 required rsync files.

```
C:\cygdrive\rsync -avz /cygdrive/c/testsite/public_html/ /cygdrive/c/Test2/
```

works as expected.

```
C:\cygdrive\rsync -avz -e ssh /cygdrive/c/testsite/public_html/ chris@nnn.nnn.nnn.nnn:/var/www/testsite.com/public_html/
```

fails with error code 12, > Error in rsync protocol data stream

The server is accessible with PUTTY, (SSH), and  Filezilla, (SFTP), and permissions for target folder are 775, owner chris.

Would appreciate guidance as to resolving the issue, please

TIA

Chris

---

### Post by darkod on 2017-10-21
Have you tried it without the '-e ssh'? I don't know about cygwin requirements but on linux you don't need the -e ssh option, it should work just fine without it. It is designed to use ssh by default unless I'm mistaken.

---

### Post by ChrisRChamberlain on 2017-10-21
darkod

Thanks for your reply - unfortunately same error message.

---

### Post by darkod on 2017-10-21
In such case it looks like cygwin issue, not rsync issue. Maybe you are missing some files that it depends on? Or simply they are not in that folder and it doesn't have the PATH to use them?

It looks to me like a problem related to use rsync/cygwin on windows, not specifically rsync problem.

PS. That destination path does exist on the remote server, right?

---

### Post by ChrisRChamberlain on 2017-10-22
darkod

The problem seems to lie with the server file ~/.ssh/authorized_keys.

Have regenerated the public key without password and appended the string to 'authorized_keys'

Running ```
rsync -avz /cygdrive/c/test/ [email]chris@nnn.nnn.nnn.nnn[/email]:/home/chris/documents/
``` in a cwrsync .cmd file, the rsync path being set in the .cmd file, prompts for a password. 

Enter the password and the task completes.

The application under development would call 'rsync' from a Windows shell. That is currently returning error no 12, "Error in rsync protocol data stream" because it can't handle the request for a password.

So resolve the password issue, hopefully resolve all.

Something obvious still missing, methinks

---

### Post by ChrisRChamberlain on 2017-10-22
Finally resolved the issue - calling rsync in a .bat or .cmd file is the problem, not the server file ~/.ssh/authorized_keys.

Running the rsync command, .bat or .cmd file in a Cygwin64 terminal works. 

Calling the same code in a Windows shell fails so it's  back to resolving those issues as opposed to any rsync issues.

Many thanks to darkod for your input.

---

### Post by ChrisRChamberlain on 2017-10-23
Finally a solution ```
rsync -avz -e "\"/cygdrive/c/cygwin64/bin/ssh.exe\"" /cygdrive/c/......
```found here [http://ycsoftware.net/rsync-failed-to-exec-ssh-no-such-file-or-directory2-on-windows/]("http://ycsoftware.net/rsync-failed-to-exec-ssh-no-such-file-or-directory2-on-windows/")

Running the testrsync.cmd through the Windows WinAPI call shellexecute() with working folder set to C:\cygwin64 enables rsync to function as expected.

---

