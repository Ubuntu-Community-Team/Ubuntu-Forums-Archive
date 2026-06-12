---
title: "Too many levels of symbolic links, Problem"
date: 2010-10-23
forum: Server Platforms
---

### Post by ScriptingPenguin on 2010-10-23
Hello, I do not understand why I am getting this error, it should be a very simple thing, I am just trying to decompress tftpd.
The file is named, tftpd.8.gz

So I typed whereis tftpd.8.gz to find where ubuntu wanted to download it to, and found it here:
/usr/share/man/man8

so here are the steps i typed;;

cd /usr/share/man/man8
/usr/share/man/man8$ gunzip tftp.8.gz > /home/MyRoot/Downloads/Net_Tools
bash: /home/jMyRoot/Downloads/Net_Tools: Is a directory

it failed, (idk why) so I tried not redirecting it

gunzip tftpd.8.gz
gzip: tftpd.8.gz: Too many levels of symbolic links

Why can't I decompress this file I just downloaded?
Also, any help on how to redirect or pipe the decompressed output to a certain folder I would like to put my network tools in would be great.

Thanks

---

### Post by BkkBonanza on 2010-10-23
The whereis command is not useful for finding downloaded files. It will only locate executable files and manuals in the path. So it is unlikely that your file was downloaded to that directory. More likely is that it found a man page file and you're trying to unzip a file that isn't suitable.

You can use the **find** command to locate any file. Most likely it was downloaded to wherever your browser is set by default for downloads - somewhere under your home folder. Try, **find ~ -name tftpd***.

Usually a downloaded archive would be a tar archive, like tftpd.tar.gz and you would use the **tar -xzvf filename** command to unarchive it. 

Better yet, tftpd is in the repos so you would be better to install from there because it would get updated as fixes occur. Use Synaptics from desktop or **sudo apt-get install tftpd** from cmd line. The only reason to install a direct download would be if you want a version newer than the repos have.

---

