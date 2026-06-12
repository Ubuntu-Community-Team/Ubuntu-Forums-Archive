---
title: "FTP Upload from Server"
date: 2009-04-20
forum: Server Platforms
---

### Post by GodsDead on 2009-04-20
hey there, i have a working Ubuntu home server, and im guessing its got ProFTPD Server running, since thats the name of the FTP server running from webmin, and it works, which is great, but since i have this homeserver running most of the time, i wondered if i can use it to upload like 6gb of data from this server to another server which is always on :)

I think i tryed the built in ftp commands from shell before, but it just hung, i think it party worked, but i have/had no progress etc going on.. i do have screen installed, so i could do this but that would just suck waiting and hoping :/

I mean as ProFTPD Server is installed can i use this as a client with some stats? for uploading to my proper web server? Cheers.

Also a web gui would be ausom for checking stats on the upload etc =D

---

### Post by John Cheng on 2009-04-20
> I mean as ProFTPD Server is installed can i use this as a client with some stats? for uploading to my proper web server? 

Unfortunately, no. Use a client like ncftp or lftp for uploading files. The ncftp client supports a progress meter.

> The purpose of ncftp is to provide a powerful and flexible interface to the Internet standard File Transfer Protocol. It is intended to replace the stock ftp program that comes with the system.

Although the program appears to be rather spartan, you'll find that ncftp has a wealth of valuable performance and usage features. The program was designed with an emphasis on usability, and it does as much as it can for you automatically so you can do what you expect to do with a file transfer program, which is transfer files between two interconnected systems.

Some of the cooler features include progress meters, filename completion, command-line editing, background processing, auto-resume downloads, bookmarking, cached directory listings, host redialing, working with firewalls and proxies, downloading entire directory trees, etc., etc.

The ncftp distribution comes with the useful utility programs ncftpget(1) and ncftpput(1) which were designed to do command-line FTP. In particular, they are very handy for shell scripts. This version of ncftp no longer does command-line FTP, since the main ncftp program is more of a browser-type program.

---

### Post by GodsDead on 2009-04-21
Oh wow, that sounds perfect, cheers John Cheng!!

---

