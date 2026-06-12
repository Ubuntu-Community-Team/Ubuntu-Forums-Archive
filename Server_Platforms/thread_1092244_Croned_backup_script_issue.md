---
title: "Croned backup script issue"
date: 2009-03-10
forum: Server Platforms
---

### Post by _sami_ on 2009-03-10
Hi
I have made a backup script which connects trough ssh to the remote host, tar's a directory and sends the stream back so that i can redirect the stream to a file on my local host. The script works fine when I run it in the terminal, but when I cron the script it stops working. It hangs on the following line:

	ssh user@server "tar cvzf - $remote_files">$full/$today.tar.gz

I know its working because the file is being created and is fully extractable too. But its like the ssh-session just wont exit so my script hangs and dont continues its execution.

Does any one have an idea of why this is?
Thankful for any help  :)

---

### Post by hyper_ch on 2009-03-10
maybe not a nice solution but why not make a cron on the remote computer that creates the tgz file and puts it in a webfolder and then like an hour later or so run the cron on your computer and use wget to pull the tgz down.

---

### Post by shizzy-t on 2009-03-10
I think it would work if you used rsh and not ssh

rsh user@server "tar cvzf - $remote_files">$full/$today.tar.gz

---

### Post by Dr Small on 2009-03-10
I don't know why you just don't tar it on the server with one command, then use scp and download the file with another command in your script.

---

