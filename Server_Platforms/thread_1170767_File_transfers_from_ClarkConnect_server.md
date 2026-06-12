---
title: "File transfers from ClarkConnect server"
date: 2009-05-26
forum: Server Platforms
---

### Post by OllieGab on 2009-05-26
I've got ClarkConnect server up and running and I am now trying to access it from my Ubuntu 9.4
As I am a newbie is this (network) area I seem to have some basic problems, like how to acutally access the file server, upload or download files for instance.
I was expecting to see some sort of directory tree...
I can connect to the FTP server and upload/download web pages but I have no feel for how to go about simple file transfers.
Is there any tweak or setting I need to do in Ubuntu?
I've tried Places --> Connect to server... but whenever I stick my password in the dialogue box comes back after a few seconds and asks for the pw again.

Anyone point me in the right direction, please?

Cheers Ollie

---

### Post by cariboo on 2009-05-26
It looks like clarkconnect leaves out 1 major componenet, ssh. I would install openssh-server on the server and use sftp/scp to manage files on the server. 

Seeing as you have to pay for clarkconnect, wouldn't it be better to contact them for support?

---

### Post by OllieGab on 2009-05-27
There is actually free version of ClarkConnect - the community version, which is the one I've got installed.
I have been able to access the server via ssh and ftp but I was expecting Ubuntu to "give me" some sort of easy interface where I could possibly drag and drop files - or at least highlight local files and press a button.
There's is a Mac in the house, which apparently "saw" the server straight away without any tweaking and I was just wondering whether Ubuntu had something similar - and I've just missed it!

Cheers

---

