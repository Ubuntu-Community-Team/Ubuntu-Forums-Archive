---
title: "Is there a way to cp files from Ubuntu server to a Windows Server WITHOUT Samba?"
date: 2013-04-08
forum: Server Platforms
---

### Post by saande on 2013-04-08
Hi,

I've got the task to create a sh file in Ubuntu Server 10.04.02 and have different files copied to a Windows Server share without using Samba?

IMPORTANT POINTS
1.The Ubuntu server is a server I do not manage directly; as he owners created me a profile with full access on the required folders from which I need those files.
2. I'm not allowed to install or upgrade anything on the Ubuntu server, otherwise the warranty and support are lost.
3. SSH or FTP is not & will not be present/active and on the Windows server share.

SITUATION 1
When copying any file from the Ubuntu server to another folder within the Ubuntu server there is no problem.

SITUATION 2
When copying any file from the Ubuntu server to another ("external) windows server, I always get the message: "cp: target `@19.168.0.174:/pgm' is not a directory".

When reading most forums and surfing through the web, I see that Samba is needed to copy/move files across a Linux/Windows server. Can someone confirm this?

---

### Post by darkod on 2013-04-08
Samba as in samba server installation is not needed in my opinion. But a samba client might be needed to communicate with the windows share.

But, you can't simply use the cp command with IP address, it doesn't work like that. You will have to mount the windows share either temporarily (but do it every time you want to copy), or permanently (the better option). If they gave you a user with permissions only on the folders you need, that user probably doesn't have rights to mount shares. They will need to help you with that. It's sufficient that they make an entry in fstab only once which will mount the share every time on boot. Then you can use it.

The windows share would use cifs to mount as far as I remember. It also depends whether you need to suppy credentials or not. If you don't need credentials mounting it with guest option should be fine. I think there was also an option called _netdev or similar which tells it the share is over a network, and to wait a little if there is a delay reaching it. They will also need to create a folder to use as mount point, for example /windows_share.

The line in fstab would look something like:
```
//19.168.0.174/share-name   /windows_share   cifs   _netdev,guest   0   2
```

That will mount the share each time on boot. After that you can use it to copy like:
```
cp whatever /windows_share/
```

Everything you copy into that mount point will end up on the windows server in the shared folder.

---

### Post by egpetrich on 2013-04-09
Does the Ubuntu server have the "smbclient" program installed? If so, you can use this to transfer files to and from the Windows server without requiring a directory mount.

---

### Post by cerealcable on 2013-04-10
You could always install an FTP server on the Ubuntu server and access it via Internet Explorer on the Windows Server if that would work for you.  Could always do HTTP even if you really wanted.  Depends on what you want to really do in the long term.  Looking for a short fast fix, then hell installing apache and putting your file /var/www/, of course my suggestion assumes you could retrieve the file via the Windows server instead of pushing the file to the Windows server.

---

### Post by saande on 2013-04-11
smb client is not installed and I cannot install anything on the ubuntu server. I've made a try from the windows server: Make an SFTP connection with Putty and type, in command line, cp for a particular file. It worked. The problem comes when we work with multi-level directories cause it does not work with cp but that's for another topic.

---

### Post by koenn on 2013-04-11
try winscp
it's a windows program that understands ssh and looks like a file browser

---

### Post by saande on 2013-04-12
I've tried winscp and can navigate through the entire root directory of the linux server. But when I make a search and specify the files everything is OK. It finds all the files I need and that's great. Now I need to try to transfer this to a directory from the server I'm working cause when trying and I click on start, nothing happens. Still researching.

---

### Post by koenn on 2013-04-14
it shouldn't be all that difficult.

Run WinSCP in "Explorer" mode (meaning : like Windows. The laternative is "Midnight Commander mode" but that's a 1980's approach)
You should be able to drag and drop between a  WinSCP window and a  MS Explorer window. 
Alternatively, you can browse the linux file tree, right-click a file, and copy it to the windows machine where you're running winscp.
Piece of cake, really

---

### Post by HermanAB on 2013-04-15
Hmm, lemme see how many boring ways can we use to move files beween two computers...
smbclient
scp
ftp
webdav
email attachments
nc

Bingo! Netcat is the most fun way!

On one machine set up a listener and send its output to a file:
nc -l 1234 > filename

On the other machine run a client session and send a file:
nc ip.add.re.ss 1234 < filename

La voila.

Now that ain't bad is it?

---

### Post by saande on 2013-04-18
Lots of options. Something I did not mention is that the Ubuntu server cannot be modified in nothing, which means no config, no setup or no installation and/or update. There is a samba server/client installed but I cannot configure it.
I also tried scp and cp but it does not work because when the nested sub-folders are to deep in the tree, I get an error/alert stating multi-level scp is not supported.
I will give it a try with webdav or nc and keep you updated if it works.

---

### Post by saande on 2013-04-18
I managed to setup everything, as mention don the winscp website, but when I press synchronize nothing happens. With Filezilla, I manage to search for specific files in very deep in the tree but when I want to transfer the same structure it says it cannot copy more than 1 folder at a time.

NC works on the Ubuntu side but failes to make the link with Windows server. If I haven't got so many restructions on the Ubuntu server, I could finished this long time ago.

---

### Post by saande on 2013-04-18
I managed to setup everything, as mention don the winscp website, but when I press synchronize nothing happens. 

Concerning FTP, I gave a try with Filezilla. I managed to search for specific files in very deep in the tree but when I want to transfer the same structure it says it cannot copy more than 1 folder at a time.

NC works on the Ubuntu side but failes to make the link with Windows server. If I haven't got so many restructions on the Ubuntu server, I could finished this long time ago.

WebDav cannot be implemented on the Windows server as IIS is not configured. The Windows server in question is a virtual server, where I created a share. All file should go to that share. That's why webdav is not an option here.

One of my colleagues is trying to create a bat files, declare some variable (rem ...) and copy all we need and have this bat file executed with psftp and putty. It works but it's a lot of work with all the variables. Furthermore, if something changes in the structure, it will certainly give a headache.

---

### Post by kgatan on 2013-04-18
> **saande said:**
> I managed to setup everything, as mention don the winscp website, but when I press synchronize nothing happens.  

I use scripted WinSCP to backup windows machines to a linux server over ssh. Ill include my bat and synch files in case it helps.
Please note my setup requiers WinSCP to have a saved password to the host.

I have better files using Windows enviroment variables etc but i cant find it at the moment. Hopefully you get the idee from this.

bat file,

```
"C:\Program Files\WinSCP\winscp.exe" "/console" "/script=C:\Program Files\WinSCP\files.txt"
```


files.txt,

```
open change_to_winscp_saved_host
synchronize remote -delete "Source directory" "target directory"
exit
```

"Synchronize remote -delete" means it mirrors the target directory with the source.

---

### Post by markbl on 2013-04-18
> **HermanAB said:**
> 
Now that ain't bad is it?
Here's another neat little trick you can add to your list. Not many people know this but it is **very** handy.

On your linux-box where you want to copy files from, just:
```

cd <where the files are>
python -m SimpleHTTPServer

```

Then on your client machine just point your browser to http://<linux-box>:8000/ and click on the files you want.

---

